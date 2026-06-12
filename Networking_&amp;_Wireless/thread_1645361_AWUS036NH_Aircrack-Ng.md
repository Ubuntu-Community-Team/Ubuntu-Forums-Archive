---
title: "AWUS036NH Aircrack-Ng"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by CiSC0kid on 2010-12-14
I am posting this here for others who are attempting to use their AWUS036NH wireless card with Aircrack-Ng.

**Specifically, this post is for those who cannot get packet injection working. **

Here is the link I used to get it working. I am using the default kernel on Lucid Lynx, but it tells you what to do, step by step, for a few different distros and kernel versions.

[http://forum.aircrack-ng.org/index.php?topic=5755.0]("http://forum.aircrack-ng.org/index.php?topic=5755.0")

Hope this helps. I have ~ 70 - 90% Injection rate now.

---

### Post by stretchtiberius on 2011-01-01
I do not see instructions for the ALFA-AWUS036NH (only ALFA-AWUS036H and ALFA-AWUS050NH). Which instructions did you follow?

---

### Post by rastanomics on 2011-03-14
i have scoped this link and tried the tutorials. like most it offers no fix especially to mine nor probably other users problems. for the life of trying these so called tutorials that claim to be "easy" 
all i get are errors at the end everytime i try to make or make install. here is an example of a so called tutorial...
 
[COLOR=black][FONT=Verdana]1. [/FONT][/COLOR][COLOR=black][FONT=Verdana]1.Copy driver for network card to Desktop[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]2. Open a terminal[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]3. sudo -i[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]4. cd /home/ubuntu/Desktop/rt3070alfa[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]5. tar -xf 036NH_2009_1110_Linux.tar.bz2[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]6. cd 2009_1110_RT3070_Linux_STA_v2.1.2.0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]7. gedit os/linux/config.mk[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]8. Change "HAS_WPA_SUPPLICANT=n" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n" to y[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]9. make && make install[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]10. gedit /etc/modprobe.d/blacklist.conf and add:[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]a. blacklist rt2x00usb[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]b. blacklist rt2x00lib[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]c. blackist rt2800usb[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]11. Reboot[/COLOR][/FONT]
[COLOR=black][FONT=Verdana]This and about another 15 so called tutorials DO NOT WORK. one word="BULL"[/FONT][/COLOR]
 
here is another.....
 
[http://www.microsofttranslator.com/bv.aspx?ref=IE8Activity&from=&to=en&a=http%3a%2f%2fwww.crack-wifi.com%2fforum%2fviewtopic.php%3fid%3d2169]("http://www.microsofttranslator.com/bv.aspx?ref=IE8Activity&from=&to=en&a=http%3a%2f%2fwww.crack-wifi.com%2fforum%2fviewtopic.php%3fid%3d2169")
 
you're suppose arrive in a new menu this doesn't happen because the 3rd command git clone git...... doesn't work either...... what a waste of time.........

---

### Post by khurtsiya on 2011-11-16
who make it work?

---

### Post by CharlesA on 2011-11-16
Thread is ancient. Closed.

---

