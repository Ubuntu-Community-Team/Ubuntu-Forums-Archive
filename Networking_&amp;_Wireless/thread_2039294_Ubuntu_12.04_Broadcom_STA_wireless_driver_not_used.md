---
title: "Ubuntu 12.04 Broadcom STA wireless driver not used"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by pyro.xyz on 2012-08-08
Hello, I have been using Ubuntu 11.04 for a while, and just recently completely uninstalled it (because of many problems that I could not figure out how to fix) and reinstalled Ubuntu 12.04. When I first installed Ubuntu (version 10.04), it automatically detected the correct wireless driver for my wireless card, and installed it, and I had very few problems with it, until now, when I reinstalled Ubuntu. Now, apparently,  I do have a wireless driver that is installed (Broadcom STA wireless driver) and active, but is apparently "currently not in use" according to Additional Drivers. I checked around, and there are no other wireless drivers on my laptop, wireless doesn't work, and the only way I was able to get this posted was to use a wired connection. Can anybody help me with this???

---

### Post by wildmanne39 on 2012-08-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by pyro.xyz on 2012-08-09
here is the result.

---

### Post by pyro.xyz on 2012-08-09
Hey, thanks for your help, but I fixed the entire problem by bumping the wireless switch.

---

### Post by wildmanne39 on 2012-08-09
Hi, glad it is working, what personal information did you find in the file because we made it so it would exclude certain things and if it did not work right I need to know so we can fix it.
Thanks

---

### Post by ts3 on 2012-08-11
> **wildmanne39 said:**
> Hi, glad it is working, what personal information did you find in the file because we made it so it would exclude certain things and if it did not work right I need to know so we can fix it.
Thanks

Hi, wildmanne, I'm not the OP but I downloaded and ran the script out of curiosity.  

The text file shows the name of the wireless network in several places.  Some people may consider this personal information if the name of their network includes a first name or a surname (or both).  The MAC addresses were removed as intended.

Another thought: I've been posting on these forums for a while so I took the chance on running the script (I also took a look at it) but not everyone might be willing or able to do that. 

On one hand it seems like a good idea because it removes human error as much as possible and gives you all the info you need to troubleshoot wireless.  On the other hand, downloading and running scripts sight unseen is not best practice.

Still if it helps get people their wireless back the good probably outweighs the bad :)

HTH & Cheers

P.S. Perhaps adding a sub-forum stickie with the script and a quick explanation about what it does and then link to the explanation from individual threads might help.

---

### Post by wildmanne39 on 2012-08-11
Hi, having the network name included in the information is intended, it would get the same information if you ran the command in the terminal which is the way it is usually done and it is useful to know what network the person is trying to connect too in order to help fix there issue.

True all valid points.
Thanks for your reply and suggestions.

---

