# hostingraja.in-SSL-Installation-Setup-Guide
This script helpsyou to install SSL on Linux VPS server provided by HostingRaja.  This scripts lets  you install the " Let’s Encrypt", Let’s Encrypt is an open source tool for SSL installation.

SSL installation script 

#!/bin/sh
domain="example.com"
mail="mail@example.com"
wwwoption="with"
dir="/var/log/letsencrypt/"
if [ ! -d "$dir" ]
then
        mkdir /var/log/letsencrypt/
fi
chmod 755 /var/log/letsencrypt/
file="/var/log/letsencrypt/$domain.log"
if [ ! -f "$file" ]
then
        touch /var/log/letsencrypt/$domain.log
fi
echo "started" > /var/log/letsencrypt/$domain.log
chmod 777 /var/log/letsencrypt/$domain.log
chown apache:apache /var/log/letsencrypt/$domain.log
yum -y install python-certbot-apache
if  [[ "$wwwoption" = "with" ]]; then
/usr/local/letsencrypt/./certbot-auto certonly --apache --agree-tos --non-interactive --verbose --no-self-upgrade -d $domain -d www.$domain --email $mail
else
/usr/local/letsencrypt/./certbot-auto certonly --apache --agree-tos --non-interactive --verbose --no-self-upgrade -d $domain --email $mail
fi
chmod 755 /var/log/letsencrypt/
chmod 777 /var/log/letsencrypt/$domain.log
chown apache:apache /var/log/letsencrypt/$domain.log
echo "completed" > /var/log/letsencrypt/$domain.log
/usr/bin/php /etc/sentora/panel/bin/daemon.php

The above script was used to install SSL on Linux VPS server.  This script uses Let’s Encrypt to achieve this. Let’s Encrypt is an open source tool for SSL installation.

Before to use Let’s Encrypt,  We need to install python for apache. And also we have the option to install SSL for a domain with or without www. Once we complete installation, SSL pem file are created in path /etc/letsencrypt/live/example.com/.

In Apache configuration file update the pem file path and check document root and domain name are correct.  once everything is  correct restart the httpd service.

SSL uses:

SSL is the backbone of our secure Internet and it protects your sensitive information as it travels across the world's computer networks. SSL is essential for protecting your website, even if it doesn't handle sensitive information like credit cards. It provides privacy, critical security and data integrity for both your websites and your users' personal information.

when you install SSL for your domain it will have the impact on the reputaion.HopstingRaja servers builted with world class components that assures you the reliable services.

Visit HostingRaja.in for buying VPS, We provide FREE ssl with every VPS plan chosen.
