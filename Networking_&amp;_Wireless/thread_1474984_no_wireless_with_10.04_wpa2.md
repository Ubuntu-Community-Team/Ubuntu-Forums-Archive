---
title: "no wireless with 10.04 wpa2"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by dreamquartz on 2010-05-06
After updating to 10.04, I was able to connect easily to my network.

However after getting a new router "Linksys WRT610Nv2", I was initially able to set up my wireless "WPA & WPA2 Personal"-encrypted network, but for whatever reason it stopped working completely.

My Asus EeePC 1000H does recognize my network, but its does not want to connect anymore, whatever I try. If I use no encryption, or go wired, everything works well.
If I go on other networks everything is ok.
I even reinstalled Passwords and Encryption Keys.
Other computers (Windows-bad XP and Vista, laptop and desktop [sorry, but working on it to get rid of them!]) have no problems, either wired or wireless connecting with my network.
Booting under 9.10, everything works ok as well.

In Ubuntu 10.04, going into Network Connections and Edit my network, this is what I see:

ticked: Connect automatically
Did not tick: Available for all users

Under tab **Wireless**:
_S_SID: *my network name*
M_o_de: Infrastructure
_B_SSID:
_M_AC Address:
MT_U_: automatic

Under tab **Wireless Security**:
_S_ecurity: WPA & WPA2 Personal
_P_assword: *63 characters long*
 
Under tab **IPv4 Settings**:
_M_ethod: Automatic (DHCP)
Addresses: greyed out
_D_NS servers: greyed out
_S_earch domains: greyed out
D_H_CP client ID:
When _R_outes... are checked, everything is empty

Under tab **IPv6 Settings**:
Method: Ignore
Addresses: greyed out
_D_NS servers: greyed out
_S_earch domains: greyed out
_R_outes...: greyed out

Any suggestions?

---

### Post by dreamquartz on 2010-05-06
> **dreamquartz said:**
> After updating to 10.04, I was able to connect easily to my network.

However after getting a new router "Linksys WRT610Nv2", I was initially able to set up my wireless "WPA & WPA2 Personal"-encrypted network, but for whatever reason it stopped working completely.

My Asus EeePC 1000H does recognize my network, but its does not want to connect anymore, whatever I try. If I use no encryption, or go wired, everything works well.
If I go on other networks everything is ok.
I even reinstalled Passwords and Encryption Keys.
Other computers (Windows-bad XP and Vista, laptop and desktop [sorry, but working on it to get rid of them!]) have no problems, either wired or wireless connecting with my network.
Booting under 9.10, everything works ok as well.

In Ubuntu 10.04, going into Network Connections and Edit my network, this is what I see:

ticked: Connect automatically
Did not tick: Available for all users

Under tab **Wireless**:
_S_SID: *my network name*
M_o_de: Infrastructure
_B_SSID:
_M_AC Address:
MT_U_: automatic

Under tab **Wireless Security**:
_S_ecurity: WPA & WPA2 Personal
_P_assword: *63 characters long*
 
Under tab **IPv4 Settings**:
_M_ethod: Automatic (DHCP)
Addresses: greyed out
_D_NS servers: greyed out
_S_earch domains: greyed out
D_H_CP client ID:
When _R_outes... are checked, everything is empty

Under tab **IPv6 Settings**:
Method: Ignore
Addresses: greyed out
_D_NS servers: greyed out
_S_earch domains: greyed out
_R_outes...: greyed out

Any suggestions?

[SIZE=6]This is what helped me[/SIZE]

see [http://ubuntuforums.org/showthread.php?p=9203922#post9250969](http://ubuntuforums.org/showthread.php?p=9203922#post9250969)

---

### Post by dreamquartz on 2010-05-07
> **dreamquartz said:**
> [SIZE=6]This is what helped me[/SIZE]

see [http://ubuntuforums.org/showthread.php?p=9203922#post9250969](http://ubuntuforums.org/showthread.php?p=9203922#post9250969)


[SIZE=6]Spoke too soon.[/SIZE]
update:
I reinstalled 10.04 from an ISO, and had also the updates from ubuntu lucid partner (System -> Administration -> Software Sources -> tab Other Software) installed.
I took a leap of faith and I changed my security settings for the internet from WPA & WPA2 Personal to WEP 40/128-bit Key, and used a 26 bit key. I connected instantly.
I went back to WPA with the same 26 characters, and nothing.
Went back to WEP, and no problem.

Tried a smaller, totally different 16 character, key under WPA, and to no avail.

At this point I am wondering if the WPA key is not transmitted properly.

Any Thoughts?

---

### Post by dreamquartz on 2010-05-07
[SIZE=6]Spoke too soon.[/SIZE]
I already posted information about my quest to connect my EeePC 1000H via WPA & WPA2 Personal wireless to the internet, but I do not know how to properly link it all.

So, as a result of it, I am repeating myself a little.
In a nutshell: no success to connect from a new install, but my status is the following:

update:
I reinstalled 10.04 from an ISO, and had also the updates from ubuntu  lucid partner (System -> Administration -> Software Sources ->  tab Other Software) installed.
I took a leap of faith and I changed my security settings for the  internet from WPA & WPA2 Personal to WEP 40/128-bit Key, and used a  26 bit key. I connected instantly.
I went back to WPA with the same 26 characters, and nothing. Went back to WEP, and no problem.
Tried a smaller, totally different 16 character, key under WPA, and to  no avail.
Went back to WEP, and YES a 100% strong connection.

I rebooted every time in between to make sure that everything was reset.

Again, not to repeat myself, but other laptops on the same network, working under either Windows XP or Windows Vista, never experienced any problems, and could connect instantly.

At this point I am wondering if the WPA & WPA2 Personal-key is not transmitted properly.

Any Thoughts?

---

### Post by PhilGil on 2010-05-07
Did you install the custom kernel and then upgrade the kernel using the Update Manager?  This will break the driver fix which was compiled into the custom kernel.  You may want to review the bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)

The inability to log in to a mixed-mode wireless connection seems to be caused by a problem with the Ralink 2860 drivers incorporated into the Lucid kernel.

Until the Ubuntu devs patch the kernel there are 3 work-arounds:

1) Install the custom kernel as described in the post you linked to above.  Do not upgrade your kernel using the Update Manager.

2) Install the newer 2.6.33 kernel, which already has the repaired driver.  Again, do not upgrade your kernel using the Update Manager.

3) Download the driver from the Ralink website, then compile and install it yourself.  The Launchpad bug report has instructions.  Be aware that this method appears to have met with mixed success, and that if you choose to upgrade the kernel you will have to compile and and install the driver again.

---

### Post by dreamquartz on 2010-05-07
Thx for your response, but the following is occurring:

the tar described in the link has been replaced by: 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2, and this is what is happening:

/home$ tar -xvjf 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2
tar: 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Any thoughts?

---

### Post by Iowan on 2010-05-07
I've merged your threads. 
Also, you can use Thread Tools to mark you thread as Unsolved (if it has been marked SOLVED).

---

### Post by chili555 on 2010-05-07
> /home$ tar -xvjf 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2
tar: 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Any thoughts?Where did you download the file? To your desktop? If so, please change directories to where the file is located:```
cd Desktop
tar -xvjf 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2
etc., etc.
```

---

### Post by dreamquartz on 2010-05-07
> **Iowan said:**
> I've merged your threads. 
Also, you can use Thread Tools to mark you thread as Unsolved (if it has been marked SOLVED).

Thx, but how to do that?

---

### Post by dreamquartz on 2010-05-07
> **chili555 said:**
> Where did you download the file? To your desktop? If so, please change directories to where the file is located:```
cd Desktop
tar -xvjf 2010_01_29_RT2860_Linux_STA_v2.3.0.0.tar.bz2
etc., etc.
```

Done everything, but the last step shows:
~/Desktop/2010_01_29_RT2860_Linux_STA_v2.3.0.0$ sudo echo rt2860sta >> /etc/modules
bash: /etc/modules: Permission denied

I am at a loss

---

### Post by chili555 on 2010-05-07
> **dreamquartz said:**
> Done everything, but the last step shows:
~/Desktop/2010_01_29_RT2860_Linux_STA_v2.3.0.0$ sudo echo rt2860sta >> /etc/modules
bash: /etc/modules: Permission denied

I am at a lossPlease try:```
sudo su
echo rt2860sta >> /etc/modules
exit
```

---

### Post by dreamquartz on 2010-05-07
Thx, but that did not do the trick as well. I did everything, but nothing comes out of it.
I would like to be able to download and install the 2.6.33 kernel. Any instructions available? The forum does not help me that much.

---

### Post by chili555 on 2010-05-07
> Password: 63 characters longThe actual password in the router is really 63 characters? Or has it been passed through some magic converter? If you set the password in the router as chilirocks and set the password in Network Manager as chilirocks, does your connection rock?

---

### Post by dreamquartz on 2010-05-13
> **chili555 said:**
> The actual password in the router is really 63 characters? Or has it been passed through some magic converter? If you set the password in the router as chilirocks and set the password in Network Manager as chilirocks, does your connection rock?

yes it is:)

---

### Post by chili555 on 2010-05-13
> **dreamquartz said:**
> Thx, but that did not do the trick as well. I did everything, but nothing comes out of it.
I would like to be able to download and install the 2.6.33 kernel. Any instructions available? The forum does not help me that much.Please check here. The actual version numbers may be newer. Be sure to get the correct architecture, 32-bit or 64-bit, for your system.

[http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/](http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/)

---

### Post by Rean on 2010-07-31
I am also having this problem. 

I do not understand what updating the kernal meens, or not sure if I trust myself enough to do it. 
I would google it but... I am not really that sure what to google.

Could someone link me to something simple that could explain what I am suppose to be doing, and how to do it

(I am totally new to Ubuntu, it took me about 3 hours before I could set the OS up to pick the wireless signals up, so yeah...)

---

