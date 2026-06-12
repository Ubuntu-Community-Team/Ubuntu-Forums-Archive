---
title: "Virgin Mobile Broadband on Linux 12.04"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by mariaallen on 2013-02-14
Hi all, I'm a newbie and need someone's help please.  I have Linux 12.04 and bought a Virgin Mobile broadband2go and my computer doesn't recognize the device. I installed the Debian installer package but it still not able to recognize the broadband.  I was told by 2 DBA's that the broadband is compatible with Linux but I haven't been able to figure out how to run the installation wizard. Anyone out there can help me?

---

### Post by mariaallen on 2013-02-17
to all the cyber community, I have not been able to install a Virgin Mobile broadband on my linux 12.04 laptop and I desperately need help. Would anyone outhere be able to help me via skype?):P I want to run my business and I can't move forward. Please help!

---

### Post by waynefoutz on 2013-02-17
Not sure which of the two dongles you're using, the Ovation MC760 is plug and play with Ubuntu, it has been since Ubuntu 8.10 came out. Make sure you have usb-modeswitch installed. It's usually installed by default. That's the only thing I can think of that will keep it from working.

If you have the newer 4G dongle, I'm not sure on that one. If network-manager doesn't work, try installing KPPP. It's a GUI front end for wvdial. That's the old way of doing it. It's pretty good at detecting modems through the GUI, you can edit the connection yourself. Just put in #777 for the phone number, any user name and password should work.

---

### Post by mariaallen on 2013-02-18
I purchased a Virgin Mobile broadband2go and was told that it is compatible with linux 12.04 and when I connect it to my laptop the wizard installer doesn't show up. does anyone know how to get linux to recognize the device? I downloaded the debian package installer and had no luck either. Any professionals outthere with knowledge of how this can be installed?

---

### Post by 3rdalbum on 2013-02-19
> **mariaallen said:**
> I purchased a Virgin Mobile broadband2go and was told that it is compatible with linux 12.04 and when I connect it to my laptop the wizard installer doesn't show up. does anyone know how to get linux to recognize the device? I downloaded the debian package installer and had no luck either. Any professionals outthere with knowledge of how this can be installed?

The wizard doesn't pop up anymore, but you can still set the modem up in Network Manager.

---

### Post by Mark Phelps on 2013-02-19
When I was using wireless on an Ubuntu CD, I found WiCD to work very well ... better than Network Manager ... at the time.

It's worth looking into if Network Manager doesn't do what you want.

---

### Post by arnav803 on 2013-02-19
hi.you can see your modem recognised in network manager or install wvdial.

---

### Post by auxilium on 2013-02-19
Hi,

We might have the same problem, check this out

[http://ubuntuforums.org/showthread.php?t=2099337&highlight=auxilium](http://ubuntuforums.org/showthread.php?t=2099337&highlight=auxilium)

although I may be using different mobile broadband yet it might work for you




Cheers,

---

### Post by mörgæs on 2013-02-19
Please stop multiposting. I have merged your three threads (and moved them to the correct forum).

---

### Post by varunendra on 2013-02-21
> **mariaallen said:**
> I purchased a Virgin Mobile broadband2go and was told that it is compatible with linux 12.04
Let us first see if it is recognized properly.

Plug-in the modem, then open a terminal, run the following commands and post back their results here -
```
lsusb
lsmod
dmesg | tail -20
```

---

