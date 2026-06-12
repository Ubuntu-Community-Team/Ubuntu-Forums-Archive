---
title: "a small script i use for reconnecting disconnected devices and logging the output"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by oobe-feisty on 2009-04-05
a small script i use for reconnecting disconnected devices and logging the output




version to modify 

```
#!/binbash                                                                                                                                                                                                   
echo "************ start disconnect log *************" | tee -a /var/log/wlan.log
/bin/date | tee -a /var/log/wlan.log
/bin/dmesg | tail | tee -a /var/log/wlan.log
/bin/cat /var/log/kern.log | /usr/bin/tail | tee -a /var/log/wlan.log
/bin/cat /var/log/syslog | /usr/bin/tail | tee -a /var/log/wlan.log
/bin/date | tee -a /var/log/wlan.log
echo "************ end disconnect log ***************" | tee -a /var/log/wlan.log

#put your commands you use to connect here


echo "************ start connect log *****************" | tee -a /var/log/wlan.log
/bin/date | tee -a /var/log/wlan.log
/bin/dmesg | tail | tee -a /var/log/wlan.log
/bin/cat /var/log/syslog | /usr/bin/tail | tee -a /var/log/wlan.log
/bin/cat /var/log/kern.log | /usr/bin/tail | tee -a /var/log/wlan.log
/bin/date | tee -a /var/log/wlan.log
echo "************ end connect log *******************" | tee -a /var/log/wlan.log

```


i wrote this myself and want to share it with people its mostly useful for wireless devices as they are the most comment culprits of disconnecting
the idea is that it logs the end of dmesg after it disconnects and after it reconnects and leaves a time stamp this way you can find out how and 
why you getting problems and how often it happens the above example is configured for my network you need to modify it to suit your needs 

basically change the stuff in between the logging lines with what commands you usually use to configure you network.

to call the script i use the script below i found it on this forum i run it as a cronjob


```

#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the backticks in the next line
if ! `/bin/ping -c3 192.168.1.1 >/dev/null 2>&1` ; then
/usr/local/bin/wlan1
fi
exit 0

```

it calls the script wlan1 ( which is the script i made above) if it cant ping the gateway


for this script to work you need to have a file called /var/log/wlan.log you can change the name be sure to edit all references in the script first. 

also i added this to  /etc/logrotate.conf 

# system-specific logs may be configured here
   /var/log/wlan.log {
      weekly
      size 100k
      rotate 2
 }




this way i dont end up with a 10GB log file :P

---

