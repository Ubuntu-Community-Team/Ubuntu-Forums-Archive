---
title: "Dell Inspiron Wireless Adapter"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Tom Boy on 2011-09-10
I apologize for the redundancy. I am using a Dell Inspiron 6400/E 1505 laptop. Here are my adapter stats (I think):
 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 
I installed ubuntu yesterday, and have been having a heck of a time trying to get my wireless adapter to work. 
 
Broadcom STA wireless driver was activated and currently in use THIS MORNING... HOWEVER, after performing the commands listed at last below, it is now indicated as: activated but *not currently in use*.
 
I have tried a couple of fixes:
 
[http://ubuntuforums.org/showthread.php?t=1795570&highlight=dell+ispirion+6400](http://ubuntuforums.org/showthread.php?t=1795570&highlight=dell+ispirion+6400)
 
and also this:
:~$ sudo modprobe b43
And because that is needed I did:
:~$ gksudo gedit /etc/rc.local
 
at sudo modprobe b43: came up blank...
 
at gksudo gedit/etc/rc.local this:
 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR=#ff0000]modprobe b43[/COLOR]
exit 0
 
where I added the text in red above the exit 0 line.
 
Though the above fix did finally turn on the wireless adapter, the wireless connection would not hold. Further, THIS HAS ALSO KNOCKED OUT MY ETHERNET CONNECTION... (see above: broadcom STA wireless driver is activated, but [NOW] *not in use*) I cannot access the Internet at all after perfoming the above terminal command and edit...
 
Please Help! And thank you so much in advance! I am the consumate newbie also, so I am hoping the above is clear!

---

### Post by Tom Boy on 2011-09-10
My solution is to reinstall ubuntu...  To get back the dirt to fill the hole I have dug for myself...  Lol...

---

### Post by bkratz on 2011-09-10
> **Tom Boy said:**
> I apologize for the redundancy. I am using a Dell Inspiron 6400/E 1505 laptop. Here are my adapter stats (I think):
 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 
I installed ubuntu yesterday, and have been having a heck of a time trying to get my wireless adapter to work. 
 
Broadcom STA wireless driver was activated and currently in use THIS MORNING... HOWEVER, after performing the commands listed at last below, it is now indicated as: activated but *not currently in use*.
 
I have tried a couple of fixes:
 
[http://ubuntuforums.org/showthread.php?t=1795570&highlight=dell+ispirion+6400](http://ubuntuforums.org/showthread.php?t=1795570&highlight=dell+ispirion+6400)
 
and also this:
:~$ sudo modprobe b43
And because that is needed I did:
:~$ gksudo gedit /etc/rc.local
 
at sudo modprobe b43: came up blank...
 
at gksudo gedit/etc/rc.local this:
 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR=#ff0000]modprobe b43[/COLOR]
exit 0
 
where I added the text in red above the exit 0 line.
 
Though the above fix did finally turn on the wireless adapter, the wireless connection would not hold. Further, THIS HAS ALSO KNOCKED OUT MY ETHERNET CONNECTION... (see above: broadcom STA wireless driver is activated, but [NOW] *not in use*) I cannot access the Internet at all after perfoming the above terminal command and edit...
 
Please Help! And thank you so much in advance! I am the consumate newbie also, so I am hoping the above is clear!


The reason you lost wired connection was that the installation of the STA driver blacklisted the b44 and ssb drivers used by the BCM4401. The command 

```
egrep -e b44 -e ssb  /etc/modprobe.d/*
```

should show us the directory. please copy/paste the output back here

---

### Post by Tom Boy on 2011-09-10
> **bkratz said:**
> The reason you lost wired connection was that the installation of the STA driver blacklisted the b44 and ssb drivers used by the BCM4401. The command 
 
```
egrep -e b44 -e ssb  /etc/modprobe.d/*
```
 
should show us the directory. please copy/paste the output back here
 
Thank you so much bkratz!!!  Here is the output:
 
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
anne@anne-MM061:~$

---

### Post by bkratz on 2011-09-10
> **Tom Boy said:**
> Thank you so much bkratz!!!  Here is the output:
 
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
anne@anne-MM061:~$


Since you have apparently reinstalled here is the correct way for your machine

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311)

---

### Post by Tom Boy on 2011-09-10
> **bkratz said:**
> Since you have apparently reinstalled here is the correct way for your machine
 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311)
 
Thanks again! I got scrambled eggs in return for all the code you sent, I haven't reinstalled yet, but think that is, at this point, the only solution to clean up this situation...
 
Appreciate your help and will immediately refer to above doc upon reinstallation... lol...

---

### Post by bkratz on 2011-09-10
> **Tom Boy said:**
> Thanks again! I got scrambled eggs in return for all the code you sent, I haven't reinstalled yet, but think that is, at this point, the only solution to clean up this situation...
 
Appreciate your help and will immediately refer to above doc upon reinstallation... lol...


No problem there are plenty of us here that will be happy to help.  Good Luck!

---

### Post by Tom Boy on 2011-09-12
Your instructions worked to a tee...
 
Dell users should NOT download the Broadcom STA at all, you are given that option after installing ubuntu 11.04.  There is an icon at top that asks you to upgrade additional drivers (this is the Broadcom STA driver)...  Don't do it!  Refer to the link:
 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)
 
and follow it to the letter.  Restart.  You will then have your wireless connection...  If you search for the Broadcom you may not find it, if you didn't download it...  
 
I still found files to purge...  (the second-to-last command/found nothing with last command)
 
Good Luck!  Thanks to a friend who helped me on my end, and to your posts and PMs bkratz.
 
**Please also note that this command**
 
sudo apt-get remove &#8211;purge bcmwl-kernel-source
should actually be entered as 
sudo apt-get remove --purge bcmwl-kernel-source

(note the double dash before 'purge')
 
*I'm a newbie, and that may be well-known around here*  :p  
 
PROBLEM SOLVED!

---

### Post by bkratz on 2011-09-13
> **Tom Boy said:**
> Your instructions worked to a tee...
 
Dell users should NOT download the Broadcom STA at all, you are given that option after installing ubuntu 11.04.  There is an icon at top that asks you to install the Broadcom STA stuff...  Don't do it!  Refer to the link above
 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)
 
and follow it to the letter.  Restart.  You will then have your wireless connection...  If you search for the Broadcom you may not find it, if you didn't download it...  
 
I still found files to purge...  (the last commands)
 
Good Luck!  Thanks to a friend who helped me on my end, and to your posts and PMs bkratz.
 
**Please also note that this command**
 
sudo apt-get remove –purge bcmwl-kernel-source
should actually be entered as 
sudo apt-get remove --purge bcmwl-kernel-source

(note the double dash before 'purge')
 
*I'm a newbie, and that may be well-known around here*  :p  
 
PROBLEM SOLVED!


Sure glad you got it sorted, enjoy!

---

### Post by Tom Boy on 2011-09-14
> **bkratz said:**
> Sure glad you got it sorted, enjoy!

Thanks so much bkratz!  Now, the issue is that I want to upgrade to kubuntu.  Will I have to perform the above all over again?  

*no worries, I will never download additional drivers again...  lol...*

---

### Post by bkratz on 2011-09-14
> **Tom Boy said:**
> Thanks so much bkratz!  Now, the issue is that I want to upgrade to kubuntu.  Will I have to perform the above all over again?  

*no worries, I will never download additional drivers again...  lol...*


Well I have never done that, so I don't really know for sure. My logic tells me that if you just add the Kubuntu desktop along with Ubuntu you would probably be ok. If a fresh install you certainly would have to go through it again.  Like I said I don't really know--would you like to experiment??

---

