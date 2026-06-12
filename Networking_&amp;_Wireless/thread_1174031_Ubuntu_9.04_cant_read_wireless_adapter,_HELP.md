---
title: "Ubuntu 9.04 cant read wireless adapter, HELP"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by babzlightyear on 2009-05-30
Just recently switch from vista to Ubuntu 9.04. My Vista had a virus and was getting sick of windows. So i made the switch and so far been learning a  playing with the OS and the forums. But my issue is my labtop's wireless card kicked the bucket before i had Ubuntu, I had it hardlined off the router. But Ubuntu has opened up a new found love for my labtop again and i want to go wireless, again. I purchased a Linksys Compact  Wireless G USB adapter Model No. WUSB54GC but cant get it to link up. I been reading forums for the past 2 days and trying different things in but it doesnt seem to work for my problem. If anyone can help or let me know what kind of infomation i need to post to help you help me would be great. I'm a Ubuntu noob but not that stupid w/ computers any help is appricated. 

p.s. I also noticed other forums stateing the black USB adapter doesnt work with 9.04
      or doesnt work with on a 64bit system. 

Some of the forums i been reading so far are. 
[http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc)
   (yes it is a ver3)

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB54GC](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB54GC)

---

### Post by babzlightyear on 2009-05-30
Random question. The install cd is for Vista. If i run Wine and install the wireless adapter will it still work on Ubuntu?

---

### Post by Chris_no on 2009-05-30
These would go a long way.

> iwconfig

> ifconfig -a

> lshw -C network 

> cat /etc/network/interfaces

---

### Post by Chris_no on 2009-05-30
I cannot imagine that wine would help you enable any network devices.

---

### Post by babzlightyear on 2009-05-31
I tired your recent code you just posted and got this massage
> 
~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.




and if i follow the instructions off this link 
[http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=1155941&highlight=wusb54gc)

I get stuck at step 4, stating this file cant be find please use apt-get <*******>

---

### Post by babzlightyear on 2009-06-01
I been trying day after day to get this to work and after i follow step 4 off the forum, bump into a problem with one of the codes. Here is a copy of my terminal. Hopefully someone can help me figure this out. 

```

root@babz-laptop:~#  wget http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
--2009-06-01 20:53:07--  http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
Resolving www.ralink.com.tw... 192.72.83.242
Connecting to www.ralink.com.tw|192.72.83.242|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 538777 (526K) [application/octet-stream]
Saving to: `2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2.3'

100%[======================================>] 538,777     64.8K/s   in 8.4s    

2009-06-01 20:53:19 (62.6 KB/s) - `2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2.3' saved [538777/538777]

root@babz-laptop:~#  tar xjf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
root@babz-laptop:~#  cd 2008_0925_RT2870_Linux_STA_v1.4.0.0
root@babz-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0#  replace include/rt2870.h with the attached rt2870.h
The program 'replace' can be found in the following packages:
 * mysql-server-5.0
 * mysql-server-5.1
Try: apt-get install <selected package>
-bash: replace: command not found
root@babz-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0# 

```

---

### Post by Ayuthia on 2009-06-01
> **babzlightyear said:**
> I been trying day after day to get this to work and after i follow step 4 off the forum, bump into a problem with one of the codes. Here is a copy of my terminal. Hopefully someone can help me figure this out. 

```

root@babz-laptop:~#  wget http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
--2009-06-01 20:53:07--  http://www.ralink.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
Resolving www.ralink.com.tw... 192.72.83.242
Connecting to www.ralink.com.tw|192.72.83.242|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 538777 (526K) [application/octet-stream]
Saving to: `2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2.3'

100%[======================================>] 538,777     64.8K/s   in 8.4s    

2009-06-01 20:53:19 (62.6 KB/s) - `2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2.3' saved [538777/538777]

root@babz-laptop:~#  tar xjf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
root@babz-laptop:~#  cd 2008_0925_RT2870_Linux_STA_v1.4.0.0
root@babz-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0#  replace include/rt2870.h with the attached rt2870.h
The program 'replace' can be found in the following packages:
 * mysql-server-5.0
 * mysql-server-5.1
Try: apt-get install <selected package>
-bash: replace: command not found
root@babz-laptop:~/2008_0925_RT2870_Linux_STA_v1.4.0.0# 

```

Step 4 is a statement not a command.  It is telling you to replace the file include/rt2870.h with his attached version of rt2870.h in his post.  So don't copy and paste step 4, but instead copy his rt2870.h over the file include/rt2870.h.

EDIT: I am sure that you are aware that there are different chips inside that Linksys USB adapter.  You might want to check lsusb to make sure that you have the right chipset number.

---

### Post by billyfd on 2009-06-01
Have you tried the ndiswrapper? It uses windows driver for wireless devices, I think that is what you was trying to do with the wine program

---

### Post by babzlightyear on 2009-06-01
Thanks for the help it makes sence now that its not a command. But how do i replace the old file w/ the one in the post.

---

