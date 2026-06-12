---
title: "aircrack-ng issues"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by Riv3r on 2012-02-28
Well, before I go ahead and post the steps I have completed thus far, I am going to get into the problem I'm having. I have a wireless card that supports packet injection (Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]) but the problem is, is that it is a b43/wl. When I go to blacklist the /wl driver it comes back to me with this message; "Permission denied". I've also tried to prefix it with "sudo" to see if that helps at all but no luck. Here is a list of commands I went through in terminal while following the tutorial on aircrack-ng's website:

riv3r@121v312--LT:~$ aireplay-ng -9 wlan0 For information, no action required: Using gettimeofday() instead of /dev/rtc 
socket(PF_PACKET) failed: Operation not permitted This program requires root privileges. 
riv3r@121v312--LT:~$ sudo aireplay-ng -9 wlan0 
[sudo] password for riv3r:  
Interface wlan0:  ioctl(SIOCGIFINDEX) failed: No such device 
riv3r@121v312--LT:~$ lspci -vnn | grep 14e4 02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) riv3r@121v312--LT:~$ uname -vb uname: extra operand `:' Try `uname --help' for more information. 
riv3r@121v312--LT:~$ uname -v 
#28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 
riv3r@121v312--LT:~$ uname -a Linux 
121v312--LT 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux 
riv3r@121v312--LT:~$ lspci -vnn | grep 14e4 02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) riv3r@121v312--LT:~$ sudo apt-get install firmware-b43-installer 
[sudo] password for riv3r:  
Reading package lists... 
Done Building dependency tree        Reading state information... 
Done The following extra packages will be installed: b43-fwcutter 
The following NEW packages will be installed:   b43-fwcutter firmware-b43-installer 0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded. 
Need to get 19.8 kB of archives. After this operation, 139 kB of additional disk space will be used. 
Do you want to continue [Y/n]? y Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main b43-fwcutter i386 1:014-9 [16.5 kB] Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/multiverse firmware-b43-installer all 1:014-9 [3,272 B] Fetched 19.8 kB in 0s (31.4 kB/s)             Selecting previously deselected package b43-fwcutter. (Reading database ... 227929 files and directories currently installed.) Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a014-9_i386.deb) ... Selecting previously deselected package firmware-b43-installer. Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ... Processing triggers for man-db ... Setting up b43-fwcutter (1:014-9) ... Setting up firmware-b43-installer (1:014-9) ... An unsupported BCM4312 Low-Power (LP-PHY) device was found. Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead. Aborting.  
_**[COLOR=#ff0000]This is where things get confusing for me:[/COLOR]**_ 
riv3r@121v312--LT:~$ lspci -vnn | grep 14e4 02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) riv3r@121v312--LT:~$ echo "blacklist wl" >> /etc/modprobe.d/blacklist bash: /etc/modprobe.d/blacklist: Permission denied 
riv3r@121v312--LT:~$ sudo echo "blacklist wl" >> /etc/modprobe.d/blacklist bash: /etc/modprobe.d/blacklist: Permission denied 
riv3r@121v312--LT:~$ modprobe -r wl WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release. FATAL: Error removing wl (/lib/modules/3.0.0-16-generic/updates/dkms/wl.ko): Operation not permitted

^ Sorry for the mess ^ The code fields on this site were much worse looking than what's above.

Any help would be great. I've gone through tutorial after tutorial to solve this. By the way I feel it may be relevant to say that I am running ubuntu 11.10 with kervel version 3+.

Hope this isn't against the rules but here is my [Original Post]("http://www.totse2.com/showthread.php?9250-BCM4312-14e4-4315-Problem") on another forum. Someone there said you guys would know best. Plus the [Original Post]("http://www.totse2.com/showthread.php?9250-BCM4312-14e4-4315-Problem") will be more legible.

---

### Post by Riv3r on 2012-02-29
Bump for relevance

---

### Post by Dangertux on 2012-02-29
Interesting forum they have over there...

Incidentally we dont support howtos on aircrack , you have so many other issues  going on that I will givr you some guidance on those.

big thing is your echo command sudo doesnt work very well with pipes or redirection, so you need to do something like this

```

sudo bash -c "echo  'blacklist wl' > /etc/modprobe.d/blacklist.conf"

```

Second modprobe requires root privs, use sudo.

Third aireplay and airodump require your card to be in monitor mode check out airmon, and dont use wlan0 as your interface use mon0. 

That should be enough to get you going. Are you sure you should be doing this?

---

### Post by Riv3r on 2012-02-29
> **Dangertux said:**
> Interesting forum they have over there...

Incidentally we dont support howtos on aircrack , you have so many other issues  going on that I will givr you some guidance on those.

big thing is your echo command sudo doesnt work very well with pipes or redirection, so you need to do something like this

```

sudo bash -c "echo  'blacklist wl' > /etc/modprobe.d/blacklist.conf"

```Second modprobe requires root privs, use sudo.

Third aireplay and airodump require your card to be in monitor mode check out airmon, and dont use wlan0 as your interface use mon0. 

That should be enough to get you going. Are you sure you should be doing this?

Hey thanks, man. I successfully blacklisted the wl driver by entering in to the .conf file manually. Finally. I also checked into some other things and figured out that it is "eth1" that I need to be using, seeing as it is the only one with a valid IP. I'm a little confused as to why it chose eth1 because I'm definitely not wired right now. I'm slowly getting through this by solving one problem after another. Thanks.

Btw, why should I not be doing this?

---

### Post by Dangertux on 2012-02-29
Well depending on what youre doing it could be illegal. Judging from the fact that you think a card in monitor mode should have a valid IP tells me youre in the "knows just enough to be dangerous(usually to themselves)" crowd. You really should look into airmon though,  its not really an optional step.

---

### Post by varunendra on 2012-03-01
Welcome to the forums Riv3r,

Nice avatar of yours there on that forum ;). Thank God you don't have it here yet, otherwise I would have thought twice before posting :P

Anyways-
> **Riv3r said:**
> ```
... An unsupported BCM4312 Low-Power (LP-PHY) device was found. Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead. Aborting.
```Did you notice this^? Did you do what it suggested? That is-
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
``` - while you are connected via ethernet.

I've no idea which interface is eth1 or how it has got a valid IP, but I doubt if your wireless interface is working yet since it has no correct firmware available. The above commands would get it

> **Dangertux said:**
> big thing is your echo command sudo doesnt work very well with pipes or redirection, so you need to do something like this
```

sudo bash -c "echo  'blacklist wl' > /etc/modprobe.d/blacklist.conf"

```
Or simply this:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```But nevermind since it is already sorted out. Just make sure your wireless works first. After that, not only I won't, but also actually I can't help with the aircrack specific issues.

---

### Post by Iowan on 2012-03-02
> **varunendra said:**
> Nice avatar of yours there on that forum ;). Thank God you don't have it here yet, otherwise I would have thought twice before posting :P
 Wouldn't have had it here for long... ;)

> **Riv3r said:**
> I'm a little confused as to why it chose eth1 because I'm definitely not wired right now.I have a couple of laptops that define the wireless interface as eth1.

---

### Post by Riv3r on 2012-03-06
> **Dangertux said:**
> Well depending on what youre doing it could be illegal. Judging from the fact that you think a card in monitor mode should have a valid IP tells me youre in the "knows just enough to be dangerous(usually to themselves)" crowd. You really should look into airmon though,  its not really an optional step.

Ahhh, I see. Well my intentions are purely educational.

> **varunendra said:**
> Welcome to the forums Riv3r,

Nice avatar of yours there on that forum ;). Thank God you don't have it here yet, otherwise I would have thought twice before posting :P

Anyways-
Did you notice this^? Did you do what it suggested? That is-
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
``` - while you are connected via ethernet.

I've no idea which interface is eth1 or how it has got a valid IP, but I doubt if your wireless interface is working yet since it has no correct firmware available. The above commands would get it


Or simply this:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```But nevermind since it is already sorted out. Just make sure your wireless works first. After that, not only I won't, but also actually I can't help with the aircrack specific issues.

Thanks. I've actually been seeking help from other sources as well and just went ahead and blacklisted manually as root user. That, fortunately, is no longer an issue as well as the firmware update. Slowly but surely. I'm still a little confused on blacklisting though. When I blacklist the wl driver and restart, it disables my network connection immediately. Is there a way I can overcome this?

> **Iowan said:**
> Wouldn't have had it here for long... ;)

I have a couple of laptops that define the wireless interface as eth1.

That website is a little different as far as it's topics and type of people who use it, so it works.

---

### Post by varunendra on 2012-03-12
> **Riv3r said:**
> When I blacklist the wl driver and restart, it disables my network connection immediately.
It suggests that the correct b43 driver might not have been installed or loaded correctly. After blacklisting wl, please try:
```
sudo modprobe -v b43
```
and post back the output (although not necessary, it would just be a confirmation that everything went correctly). Also post the outputs of:
```
lsmod
```

---

