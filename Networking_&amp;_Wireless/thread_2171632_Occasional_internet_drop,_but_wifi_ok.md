---
title: "Occasional internet drop, but wifi ok"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by fizikz on 2013-08-31
I have this puzzling problem where sometime the internet connection drops on my laptop. All programs requiring the internet get disconnected (skype, pidgin, web pages, pinging sites, etc) BUT the wireless connection to the wireless AP is still fine. After a few minutes, the internet connection gets re-established without my intervention. I can also disconnect/reconnect to the wireless network to "solve" this and get the internet connection working again.

I am using an Atheros 9380 wireless adapter with the ath9k drivers.

Some facts:

- internet connection drops, seemingly randomly, but wireless network connection is not affected
- syslog does not reveal any errors or disconnections
- internet connection is re-established after a few minutes on its own
- disconnecting/reconnecting from the wireless network re-establishes the internet connection
- other computers are not affected

---

### Post by alexandari on 2013-08-31
If syslog doesn't show connection drops,does it show when you are connected again? Have you tried running a ping for a few minutes seeing if this happens at an exact time? Does ```
 cat /var/log/syslog | grep ath9k 
``` show any calibration faults? Which kernel are you running? Are you sure it's not from the router?

---

### Post by fizikz on 2013-08-31
Syslog doesn't show anything when the drop occurs or when it reconnects on its own. Pings work fine normally, but when the connection drops, it does not work at all. The internet drop happens rarely; sometimes going for a week without any problems, and then sometimes there will be a cluster of 2-3 drops within a 1 hour period of time. 

There is nothing relating to ath9k in the syslog. The only messages are those expected from Network Manager, when I manually disconnect/reconnect from the wireless network.

I'm not sure it's not from the router. However, these drops only started happening after I upgraded to this wireless adapter. Also, other devices on the network do not experience any such drops. So, I think it's unlikely to be the router.

---

### Post by alexandari on 2013-08-31
I asked about the router because I've experienced such a problem and after a few months (yea....) I figured out the router has been loosing packets at random. So I did a hard reset on it. Another thing you can try is use ndiswrapper instead of your ath9k driver. Basically what it does is load windows drivers (inf files) and uses them on the linux machine. It's only for wireless drivers btw. I haven't had any luck with it but you should give it a try (Atheros AR5007EG here) 

oh yeah and check this out [http://ubuntuforums.org/showthread.php?t=2143660](http://ubuntuforums.org/showthread.php?t=2143660)

---

### Post by wildmanne39 on 2013-08-31
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
let us know if that helps if not it will not hurt, but in many cases it fixes the issue you are having.

If the issue still remains copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by fizikz on 2013-08-31
While I can't say for sure that the router is not part of the problem, the fact that it has been working fine for several years and the fact that other computers, cell phones, etc do not experience connection drops lead me to think that it's probably not the router. 

I suppose it could be something related to the ath9k driver. All I can say is that I have not had any wireless connection drops, just internet drops over a reasonably strong wireless connection. It's unclear to me what kind of drops that post was describing. 

===========

I already had the "nohwcrypt=1" option, and I have attached the results of the wireless script: [ATTACH]245885[/ATTACH]

---

