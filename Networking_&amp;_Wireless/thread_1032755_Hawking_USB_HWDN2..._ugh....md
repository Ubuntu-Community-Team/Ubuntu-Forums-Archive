---
title: "Hawking USB HWDN2... ugh..."
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by guitar2007 on 2009-01-06
I've been trying to install my new Hawking hi-gain usb wireless-N network adapter (HWDN2) for a few days now, and  having quite a bit of trouble, as I am new to Linux.  I've followed several forums online and know that it uses a RT2870 chipset.  I get the make file edited like it should be, run sudo make, sudo make install, and that works fine.  I run

modprobe rt2870sta 

and nothing seems to happen.. i've tried running

i tried running insmod for the file instead but it returns:

cody@cody-desktop:~/Desktop/wireless_driver/os/linux$ insmod rt2870sta.ko
insmod: error inserting 'rt2870sta.ko': -1 Operation not permitted
cody@cody-desktop:~/Desktop/wireless_driver/os/linux$ sudo insmod rt2870sta.ko
[sudo] password for cody: 
insmod: error inserting 'rt2870sta.ko': -1 File exists

After the make and make install, my iwlist scan only shows 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

No wlan0 or ra0.  I'm exhausted from trying to figure this out.  It seems a few other people have got these HWDN2's installed.   I've had no responses on the Beginner's Talk forums either. Please help! :confused:

The Confused, 
Guitar2007

---

### Post by kr651129 on 2009-01-06
have you tried using ndiswapper?  I had a similar situation to you on an old distro a year or so back.  Check this out:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


From what I understand it trys to emulate the windows driver for linux

---

### Post by guitar2007 on 2009-01-06
> **kr651129 said:**
> have you tried using ndiswapper?  I had a similar situation to you on an old distro a year or so back.  Check this out:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


From what I understand it trys to emulate the windows driver for linux

I just tried using it again.. still no wireless device found after installing the inf and sys file from windows or the linux chipset rt2870.  :(

---

### Post by kr651129 on 2009-01-06
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

??

---

### Post by guitar2007 on 2009-01-06
yep thats the one.  RT2870.  Is yours working? If so did you only have to use ndiswrapper?

---

### Post by kr651129 on 2009-01-06
I'm running Ubuntu 8.10 Desktop on a Toshiba Sattelite M45 with a built in wireless NIC and it worked out of the box for me.  I had a realtek chipset similar to yours and I did have to use ndiswrapper, but that was with a fedora build.

---

### Post by guitar2007 on 2009-01-06
hmm well maybe i just have the wrong chipset.. i know for the hwdn1, from the forums i've ready anyway, its the rt2870, but maybe it's something totally different for the hwdn2.. but from what i've read it isnt.  i guess i have more research to do...

---

### Post by kr651129 on 2009-01-06
What rev is it?  Sometimes that can screw you up it can be like chipset rt344325 rev b when the driver is for rev a

---

### Post by kr651129 on 2009-01-06
I think i found it for you:

[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)

---

### Post by guitar2007 on 2009-01-06
Thank you.  I've tried something similar to this already, but i'll uninstall everything and start from scratch and see what happens this time.

---

### Post by kr651129 on 2009-01-06
np, let me know if it works out! :D

---

### Post by guitar2007 on 2009-01-06
I got done with make and makeinstall, then i tried to run insmod and got 

cody@cody-desktop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux$ insmod rt2870sta.ko
insmod: error inserting 'rt2870sta.ko': -1 Operation not permitted

Any thoughts or suggestions?

---

### Post by kr651129 on 2009-01-06
chmod it to 777 or did you forget to run as sudo?

---

### Post by guitar2007 on 2009-01-06
yeah i ran as sudo, put in the wrong lines... 

cody@cody-desktop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux$ sudo insmod rt2870sta.ko
[sudo] password for cody: 
insmod: error inserting 'rt2870sta.ko': -1 File exists

---

### Post by kr651129 on 2009-01-06
you could always make a backup of the file, remove it, and then run again

---

### Post by guitar2007 on 2009-01-07
ok i got insmod to work i think... 

cody@cody-desktop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux$ sudo insmod rt2870sta.ko
cody@cody-desktop:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux$ 

it went straight back to the command line, so I assume it did what it needed to do; however, I still have no wireless adapters showing up anywhere.](*,)

---

### Post by kr651129 on 2009-01-07
> 
16. When will all work after my experience, if not follow the next step.
17. Open /etc/network/interfaces (gedit /etc/network/interfaces).
18. Please enter the first sentence
auto ra0
, Also the other

iface ra0 inet dhcp
(dhcp is standard, you need only change to what suits you love.
19. Then all the work, use encryption, you can configure it with the System> Administration> Network, or network-admin in the terminal.
20. Almost forgot that you must install build-essential (apt-get install build-essential).
21. build-essential to be on CD you installed ubuntu with.
22. How to install build-essential CD.
23. Open the Terminal (Applications> Accessories> Terminal)
24. Run apt-cdrom add-d / cdrom (replace / cdrom with the path cdrom is mounted with you)
25. Run apt-get update.
26. And run apt-get install build-essential.


I'm assuming you ran the above steps?

---

### Post by guitar2007 on 2009-01-07
yes i did

---

### Post by kr651129 on 2009-01-08
I'm out of ideas...

:-({|= All aboard the failship :-({|= lol

---

