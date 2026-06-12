---
title: "aircrack 1.1 does not work on Ubuntu 11.04 (using Edimax 7318USg or ALFA AWUD036NH)"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by N3tMast3r on 2011-04-30
Hi everyone,

As soon as I installed Ubuntu 11.04 64-bit (kernel 2.6.38.8 ) I noticed that aircrack does not work with my 2 wireless adapters Edimax 7318USg and ALFA AWUS036NH (fixed channel 1 error).
I used to get the same error since aircrack 1.0 but I fixed it installing the kernel 2.6.34. Unfortunately this kernel does not work on Ubuntu 11.04.

I tried to go back to aircrack 0.93 and it only works if I use my laptop integrate wireless card (only for WPA since the card is not able to inject). Edimax 7318USg and ALFA AWUS036NH are not compatible out of the box with aircrack 0.93. I remember I used to install drivers and play around with ubuntu 8.10 and 9.04 to make aircrack work with my Edimax 7318USg, but now I do not remember how to do it.

I have tried many patches and workaround posted on the internet but none of them has worked so far.

I hope some one will help me out because I have never had a problem making the edimax adapter work with aircrack since ubuntu 8.10.

This fixed channel 1 error is driving me crazy! ](*,)](*,)](*,)

---

### Post by vladchalapco on 2011-04-30
I'm getting the same error(fixed channel). (Configuration: Patched Intel Wireless Pro 3945 ABG; Ubuntu 11.04 32-bit; Aircrack-ng vs. 1.1).
I was using 10.10 with the same configuration and it worked just fine. Please help.

---

### Post by N3tMast3r on 2011-04-30
I can suggest you to try aircrack 0.93. It should work for you

---

### Post by N3tMast3r on 2011-04-30
I was able to make my Edimax adapter work by installing this kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.2-maverick/)

On Ubuntu 10.10 I used  an other 2.6.34 kernel that did not work on Ubuntu 11.04. Fortunately I tried different 2.6.34 kernels and this one was the right one for ubuntu 11.04.

Unfortunately I am still unable to make my ALFA adapter work (it used to work on ubuntu 10.10). I do not have the fix channel error anymore, it just seems to be a driver problem. When I try to put it into monitor mode it gives me a message like
¨monitor mode on usb¨. and it does not work.
on ubuntu 10.10 used to give me something like ¨monitor mode on mon0¨ and then it worked!
I really believe it is a driver related problem, I just do not know how to fix it!

Any help would be appreciate.

thanks

---

### Post by steveone on 2011-05-02
This 11.04 is really pissing me off!! :mad: Can't find anything anymore. aircrack doesn't work on my ALFA AWUS036H. arrgh!!!!](*,)Stupid "mon0 is on channel -1, but the AP uses channel 11". Has anyone found a fix? I've been at this all day. My eyes hurt and my girlfriend is pissed.

---

### Post by N3tMast3r on 2011-05-02
eh eh... I know how you feel!
It has a lot of bugs! 
Skype icon disappears from the notification area. 
The x button used to  close the windows does not work if the window is near the up left edge of the monitor
Compiz fusion must be set properly in order to work
Some skydomes in compiz fusion stop working after a reboot

and I bet there are a lot of other bugs!

Anyway, try to install this kernel [http://kernel.ubuntu.com/~kernel-ppa...34.2-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34.2-maverick/")
it made my edimax adapter work!
Still no luck with my alfa AWUS036NH though, which used to work on the previous releases of ubuntu.

Please let me know if you find a solution

---

### Post by steveone on 2011-05-11
Thanks for the suggestion N3tMast3r, but unfortunately it didn't work. Still search for a solution. :confused:

---

### Post by huevo5050 on 2011-05-23
Same problem here.

with an Intel 3945BG

---

### Post by N3tMast3r on 2011-05-23
It looks like they have made a big mess this time :(
A lot of things do not work in 11.04 :(

---

### Post by josephmills on 2011-05-23
sounds lioke you need to change the channel that the card is on they are colliding this is assuming that the network that you are trying to crack is on channel 6 ```
iwconfig wlan channel 6 
``` see if aireplay is working now? Have you also looked to see if your card is compadivle with the aircrack suite [http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)  
[http://board.blackbuntu.com/showthread.php?tid=450](http://board.blackbuntu.com/showthread.php?tid=450)
[http://board.blackbuntu.com/showthread.php?tid=388](http://board.blackbuntu.com/showthread.php?tid=388)

---

### Post by splifftor on 2011-05-24
I don't know if any one else is having the same problem but as of 11.04 I can not even compile the aircrack source anymore. functionality is down to about 50% on both my cards (alfa 36h and 36nh). also trying to compile from compat source is equally useless. seriously considering going back to 10.04 or even back to debian pure. if any1 has a breakthrough would be good to hear it

---

### Post by N3tMast3r on 2011-05-24
I am thinking to go back to 9.10 and aircrack 1.0 or 0.93.
I had no problems at all with ubuntu 9.10 and everything used to work out of the box. Problems started with ubuntu 10.04. And now in ubuntu 11.04 every little thing is a problem :(

---

### Post by Azrael Nightwalker on 2012-01-02
This is a known, long outstanding bug in the Linux kernel.
[https://bugs.launchpad.net/ubuntu/+source/aircrack-ng/+bug/643788](https://bugs.launchpad.net/ubuntu/+source/aircrack-ng/+bug/643788)
Monitor mode worked correctly in Ubuntu 10.04, and it stopped working in all later versions.

---

