---
title: "Bash Script command line find external IP address SFTP file"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by twizler on 2010-02-04
bash script will find your external IP address from the SHELL - then SFTP the IP address to an external site of your choice. Very useful if you have a cable modem or DSL and your ip address changes on you, setup as a cron job so you will always know what your IP address is - > SFTP setup using id_dsa.pub SSH KEY 

must make this executable 
> chmod + x myip.sh

#!/bin/bash
# Script     : myip.sh 
# Version    : 1.0
# Purpose    : from command line find external IP Address- once found send external IP to a webhost/remote host using SFTP
# Author     : Twizler
# Date       : 02-feb-2010
# SubScripts : 
# USE OF     : To auto send the local machine must have SSH keys  RSA or DAS authorized keys enabled
# Notes      : use of weget from [www.findmyip.org](www.findmyip.org), sed and >>casa.html fiel 
# Usage      : run from $SHELL ./myip.sh

T=$(date +%Y%m%d-%H:%M)
D=$(date +%G%m%d)
echo $file
echo Please wait.............IP Address info sent to local file casa.html:
 wget [http://findmyip.org](http://findmyip.org)  -O - -o /dev/null | grep '<span class="title">Your' | sed -r 's/<span class="title">Your IP address is\- //g' > casa.html
cat casa.html
tac casa.html > testfile_temp;
echo "<p> <strong>Time Stamp as of: $T CST </strong></p>" >> testfile_temp;
tac testfile_temp > casa.html;
rm testfile_temp;
echo "Starting SFTP SEND .......sending in progress"
sftp [email]SOMEUSER@SOMESITE.com[/email] <<-EOF
put /home/SOMEUSER/ipdhcp/casa.html /HOME/SOME_USER/SOME_FOLDER/
quit
EOF
echo $D
exit 0

---

### Post by dmizer on 2010-02-04
Dynamicdns updated with ddclient is probably a better way to go about it: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

That way, you never have to look at an email, just type in a url which is automatically updated with your IP.

---

