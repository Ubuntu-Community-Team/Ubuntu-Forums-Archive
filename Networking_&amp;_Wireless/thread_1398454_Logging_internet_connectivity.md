---
title: "Logging internet connectivity"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by wasutton3 on 2010-02-04
My ISP has had the second outage in a month now for my family's server (which i manage remotely from University). I don't know how often this happens, nor its duration. So i would like to output the time that the server cannot access the internet. I understand that this can be done with logger, but i would like it to save the logs that it is offline for with the datestamp. I.E. if i have an outage on the 16th of this month, i would want the file to be named 2-16-2010 (or some such thing) and the timestamps from 00:00:00 to 23:59:59 (or whatever interval, probably every minute) to have the command, and then the result (online or offline) or the output or something. Thanks i know i am asking a lot

---

### Post by puppywhacker on 2010-02-04
MRTG is a webapplication that is normally used to display bandwidth usage. That should already help, otherwise you have to resort to some script that will ping endlessly to log if it can still reach the other side of the internet.

---

### Post by wasutton3 on 2010-02-04
endlessly pinging isnt too bad, ill just set the inteval to 1 minute or something.

---

### Post by puppywhacker on 2010-02-04
ping -i 60 will endlessly ping, however without timestamp. The little oneline script below will put a date in front of it and has fields separated by comma's so you can load them in openoffice, or just filter through them

```

while [ 1 -eq 1 ];do DATE=`date --rfc-3339='seconds'`;RESULT=`ping -q -c 1 www.google.com | grep received`;echo $DATE,$RESULT >> /tmp/ping.log; sleep 60;done;
```

---

### Post by wasutton3 on 2010-02-04
That works perfectly with a few minor tweaks. would it be possible to do multiple hosts?

---

