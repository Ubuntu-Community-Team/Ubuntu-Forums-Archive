---
title: "am i getting hacked?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by RastaManPower on 2010-11-16
hello guys strange things happening to my pc lately i post here some info 
sudo netstat -tlp --numeric-ports
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      1277/polipo     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1346/cupsd      
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      2099/tor        
tcp        0      0 127.0.0.1:9051          0.0.0.0:*               LISTEN      2099/tor        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1346/cupsd
----------------------------------------------------------------------------------------------------------------
netstat -antp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      2099/tor        
tcp        0      0 127.0.0.1:9051          0.0.0.0:*               LISTEN      2099/tor        
tcp        1      1 192.168.0.2:35620       64.34.119.12:80         LAST_ACK    -               
tcp        0      1 192.168.0.2:59224       195.22.200.144:80       FIN_WAIT1   -               
tcp        0      1 192.168.0.2:57828       209.85.229.102:80       FIN_WAIT1   -               
tcp        0   1610 192.168.0.4:35006       69.93.127.176:9001      ESTABLISHED 2099/tor        
tcp        0      1 192.168.0.2:47062       216.137.61.192:80       FIN_WAIT1   -               
tcp        0      0 192.168.0.2:43851       195.22.200.208:80       ESTABLISHED 1847/clock-applet
tcp        0      1 192.168.0.2:48499       74.125.77.95:80         FIN_WAIT1   -               
tcp        0      0 127.0.0.1:36080         127.0.0.1:9051          ESTABLISHED 2095/vidalia    
tcp   315264      0 127.0.0.1:9050          127.0.0.1:49342         ESTABLISHED 2099/tor        
tcp        0      1 192.168.0.2:44526       64.34.80.176:80         FIN_WAIT1   -               
tcp        0      1 192.168.0.2:57255       72.233.61.123:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:47063       216.137.61.192:80       FIN_WAIT1   -               
tcp        1      1 192.168.0.2:35636       64.34.119.12:80         LAST_ACK    -               
tcp        0 110721 127.0.0.1:49342         127.0.0.1:9050          FIN_WAIT1   -               
tcp        0   1610 192.168.0.4:53828       24.117.147.148:9001     ESTABLISHED 2099/tor        
tcp        0      1 192.168.0.2:57250       72.233.61.123:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:47064       216.137.61.192:80       FIN_WAIT1   -               
tcp        1      1 192.168.0.2:35623       64.34.119.12:80         LAST_ACK    -               
tcp        0      1 192.168.0.2:57251       72.233.61.123:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:57252       72.233.61.123:80        FIN_WAIT1   -               
tcp        0   2122 192.168.0.4:54834       149.9.0.59:9001         ESTABLISHED 2099/tor        
tcp        0      1 192.168.0.2:53467       74.125.77.100:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:36000       184.73.247.134:80       FIN_WAIT1   -               
tcp        1      1 192.168.0.2:35624       64.34.119.12:80         LAST_ACK    -               
tcp        1      1 192.168.0.2:45670       72.167.239.239:80       LAST_ACK    -               
tcp        1      0 192.168.0.4:57643       91.189.89.31:80         CLOSE_WAIT  2573/gvfsd-http 
tcp        0      1 192.168.0.2:57829       209.85.229.102:80       FIN_WAIT1   -               
tcp        0    586 192.168.0.4:44584       188.72.203.252:9001     ESTABLISHED 2099/tor        
tcp        0      1 192.168.0.2:57827       209.85.229.102:80       FIN_WAIT1   -               
tcp        0      0 192.168.0.2:38386       74.84.130.182:80        TIME_WAIT   -               
tcp        0      1 192.168.0.2:45195       72.14.255.104:80        FIN_WAIT1   -               
tcp       38      0 192.168.0.4:37728       91.189.89.105:443       CLOSE_WAIT  2573/gvfsd-http 
tcp        1      1 192.168.0.2:35625       64.34.119.12:80         LAST_ACK    -               
tcp        1      1 192.168.0.2:35622       64.34.119.12:80         LAST_ACK    -               
tcp        0      0 192.168.0.4:53859       95.91.205.164:443       ESTABLISHED 2099/tor        
tcp        0      0 127.0.0.1:9051          127.0.0.1:36080         ESTABLISHED 2099/tor        
tcp        1      1 192.168.0.4:58222       195.22.200.208:80       LAST_ACK    -               
tcp        0      1 192.168.0.2:57254       72.233.61.123:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:45197       72.14.255.104:80        FIN_WAIT1   -               
tcp        0      1 192.168.0.2:57253       72.233.61.123:80        FIN_WAIT1   -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -
____________________________________________________________________________________________________________
netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      1 nico-linux:35620        stackoverflow.com:www   LAST_ACK   
tcp        0   1611 192.168.0.4:35006       server1.digitalrha:9001 FIN_WAIT1  
tcp        1      1 nico-linux:35636        stackoverflow.com:www   LAST_ACK   
tcp        0   1611 192.168.0.4:53828       24-117-147-148.cpe:9001 FIN_WAIT1  
tcp        0      0 nico-linux:50747        ww-in-f100.1e100.ne:www ESTABLISHED
tcp        1      1 nico-linux:35623        stackoverflow.com:www   LAST_ACK   
tcp        0   2123 192.168.0.4:54834       149.9.0.59:9001         FIN_WAIT1  
tcp        1      1 nico-linux:35624        stackoverflow.com:www   LAST_ACK   
^C
_______________________________________________________________________________________________________________________
netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 nico-linux:48492        feijoa.canonical.co:www ESTABLISHED
tcp        0      0 nico-linux:50747        ww-in-f100.1e100.ne:www ESTABLISHED
tcp        1      1 nico-linux:35623        stackoverflow.com:www   LAST_ACK   
tcp        1      1 nico-linux:35624        stackoverflow.com:www   LAST_ACK   
tcp        1      0 nico-linux:43881        195.22.200.208:www      CLOSE_WAIT 
tcp        1      0 192.168.0.4:57643       barbadine.canonical:www CLOSE_WAIT 
tcp        0      0 nico-linux:39879        ew-in-f102.1e100.ne:www ESTABLISHED
tcp        0    587 192.168.0.4:44584       jund.leptoquark.ne:9001 FIN_WAIT1  
tcp       38      0 192.168.0.4:37728       sumac.canonical.c:https CLOSE_WAIT 
tcp        0      1 192.168.0.4:53859       95-91-205-164-dyn:https FIN_WAIT1

---

### Post by windowsh8r on 2010-11-16
I am not sure what all of that means, but if you type 'who', it will list everyone that is logged onto your computer.

---

### Post by RastaManPower on 2010-11-16
$ who
nico     tty7         2010-11-16 19:46 (:0)
nico     pts/0        2010-11-16 20:35 (:0.0)

---

### Post by bitscarre on 2010-11-16
I am no expert in security but try scanning your computer with a rootkit scanner and an antivirus. If still in doubt, probably install a better logs visualisation application.

You can go even further and install a linux firewall application(carefull not to block yourself from the internet) and apply draconic restrictions to your connection.

By architecture, linux operating systems are very secure but not completely.

I hope this helps you.

---

### Post by windowsh8r on 2010-11-16
you are the only one logged into your computer, the netstat screens show what is going on with the network. If you are using a work, or someone else's network, there will likely be some other processes 'listening'.
But as far as your computer goes, it looks like you are good.  Is something weird happening to make you think you were getting hacked?

---

### Post by RastaManPower on 2010-11-16
i was connected to a dc++ hub and a guy started messaging me telling me he was going to hack me bacause i keep connecting to the hub with proxy since i got banned. now my network is slowing down once in a while.. i am not sure but something is going on. now i am installing gufw and ill follow a tutorial to configure it. i tryed firestarter but from what i read around its a little messy

---

### Post by RastaManPower on 2010-11-16
[IMG]http://img593.imageshack.us/img593/9528/screenshote.png[/IMG]
what are those 3 entry

---

### Post by matt_symes on 2010-11-16
Hi

[http://avahi.org/](http://avahi.org/)

dhcp client aquires a dynamic ip address for your pc.

Kind regards

---

### Post by RastaManPower on 2010-11-16
after gufw install emesene is not working... do i have to enable all windows live messenger ports?

---

### Post by windowsh8r on 2010-11-16
the dhclient is how your IP address is assigned, the avahi is for network & computer discovery  [http://avahi.org/](http://avahi.org/)  and it looks like you can disable it [http://en.kioskea.net/faq/739-disabling-the-avahi-daemon](http://en.kioskea.net/faq/739-disabling-the-avahi-daemon)
but even with it running, it would be difficult for someone to get into your system without you letting them.  If your network is running slow, perhaps there is a lot of usage on it, or it is bandwidth-limited.

---

### Post by RastaManPower on 2010-11-16
i dont understand what this thing is

---

### Post by matt_symes on 2010-11-16
Hi

> **Re: am i getting hacked?** 			
 			 			 		   		 		 		i dont understand what this thing is


What thing?

Kind regards

---

### Post by RastaManPower on 2010-11-16
the program posted. i did read the faq but i dont get what it i.. is it supposed to change my ip address^

---

### Post by windowsh8r on 2010-11-16
it should not change your IP address, that is done by the DH client when you connect to the network.  It is quite possible that each time you connect, you will have a different IP, depending on what is available.  
From my understanding, it is a basic firewall, that is essentially a one way communication path that allows you to go out, but prevents others from coming in.  Nothing in the screenshot looked fishy.

---

### Post by marquinos on 2010-11-17
> **RastaManPower said:**
> after gufw install emesene is not working... do i have to enable all windows live messenger ports?

Yes, because you have "Outgoing: Deny", you're dening all traffic FROM your applications ;)
It's safe this combination if you haven't spyware:
Incoming: Deny
Outgoing: Allow 
Or your combination but... you must open all outgoing ports as emesene ;)
Best regards.

---

