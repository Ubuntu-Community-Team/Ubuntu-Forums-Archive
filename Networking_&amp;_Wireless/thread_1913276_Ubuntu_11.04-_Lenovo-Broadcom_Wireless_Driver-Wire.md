---
title: "Ubuntu 11.04- Lenovo-Broadcom Wireless Driver-Wireless is disabled by hardware switch"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by saiganeshb on 2012-01-22
Hello,
I am using a Lenovo G560 Laptop which dual boots windows 7 and ubuntu 11.04. 

Problem: I keep getting a 'wireless disabled by hardware switch' error. (I checked the hardware switch..it apparently only controls bluetooth on/off on ubuntu). I am able to connect/create wi-fi networks without hitches from windows though.

I checked around at a few forum pages. Couldn't find anything relevant to 'blacklist' for my laptop, which looks like the solution. Here's my OS configuration(after turning on the hardware switch):

```

saiganesh@saiganesh-Lenovo-G560:~$ uname -a
Linux saiganesh-Lenovo-G560 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux
saiganesh@saiganesh-Lenovo-G560:~$ lspci | grep -i "wireless"
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
saiganesh@saiganesh-Lenovo-G560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by bkratz on 2012-01-22
> **saiganeshb said:**
> Hello,
I am using a Lenovo G560 Laptop which dual boots windows 7 and ubuntu 11.04. 

Problem: I keep getting a 'wireless disabled by hardware switch' error. (I checked the hardware switch..it apparently only controls bluetooth on/off on ubuntu). I am able to connect/create wi-fi networks without hitches from windows though.

I checked around at a few forum pages. Couldn't find anything relevant to 'blacklist' for my laptop, which looks like the solution. Here's my OS configuration(after turning on the hardware switch):

```




saiganesh@saiganesh-Lenovo-G560:~$ uname -a
Linux saiganesh-Lenovo-G560 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux
saiganesh@saiganesh-Lenovo-G560:~$ lspci | grep -i "wireless"
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
saiganesh@saiganesh-Lenovo-G560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


look at the terminal output of 

```
lsmod
```

and see if there is a module called acer-wmi

---

### Post by saiganeshb on 2012-01-22
> **bkratz said:**
> look at the terminal output of 

```
lsmod
```and see if there is a module called acer-wmi

Hi,
It didn't produce any output when I grepped "acer" from the output of lsmod. Guess it's not there. Do I install it?
```
$ lsmod | grep "acer" 
```

---

### Post by nipunshakya on 2012-01-22
Hi i have similar problems here.... one querry...have you tried to install your driver from the additional drivers??
my thread is also similar to yours..check it.

[http://ubuntuforums.org/showthread.php?t=1912405](http://ubuntuforums.org/showthread.php?t=1912405)

Goodluck.
Regards,WInuxUser

---

### Post by saiganeshb on 2012-01-22
> **WinuxUser said:**
> Hi i have similar problems here.... one querry...have you tried to install your driver from the additional drivers??
my thread is also similar to yours..check it.

[http://ubuntuforums.org/showthread.php?t=1912405](http://ubuntuforums.org/showthread.php?t=1912405)

Goodluck.
Regards,WInuxUser

Hi, I installed it from system-> administration -> additional drivers at about the time of my ubuntu installation, if that's what you mean. It covered "BCM4313-" which I believe is the output of 
```
 lspci | grep -i "wireless" 
```

---

### Post by linuxd00d on 2012-01-22
I just had this problem when playing with aircrack-ng, This was because i was using the bc43 driver. Do what WinuxUser said, this should fix your problem the broadcom driver is supplied with Ubuntu, although you may need to connect your machine via cable to re-download it.

d00d.

---

### Post by saiganeshb on 2012-01-22
Partially Solved: This is what worked for me (I am really not sure why! ... an outdated package perhaps?)

Go to System -> Administration -> Additional Drivers. 

If you find the broadcom STA driver in the list installed and active, remove it and re-install/activate it. (You may have to reboot).

---

### Post by nipunshakya on 2012-01-22
Well i had told u to look for that before hand....see....> **WinuxUser said:**
> have you tried to install your driver from the additional drivers??

Glad to know your wifi is working...its better u mark this thread as [SOLVED]. Thanks.

Regards,WInuxUser

---

### Post by saiganeshb on 2012-01-22
Well, It's not solved 'exactly'. The problem repeats if i reboot the laptop and I have to go through the whole un-install - re-install cycle everytime.

---

### Post by nipunshakya on 2012-01-23
> **saiganeshb said:**
> Solved: This is what worked for me (I am really not sure why! ... an outdated package perhaps?)

Thats what made me think your problem is solved. You could have told earlier that you need to do the re-installation thing everytime.

---

