---
title: "Nintendo Wifi Adapter"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by jayjay960 on 2009-04-19
Has anybody managed to get the Nintendo WiFi Adapter completely working with Ubuntu 8.10? I've installed the windows drivers using ndiswrapper, and it appears to recognise it, and when I open up network tools with  the device plugged in the list has an extra network device (wlan0), except there is no information for it. Also, the light doesn't flash, and nothing picks it up. I know you must have to configure it somehow, but I've tried configuring it in Network Configuration, but I don't know a lot about wireless networks, so I don't know what settings to use. Can anyone help?

---

### Post by diablo75 on 2009-04-19
If I'm not mistaken, that little USB adapter is intended to be used for sharing a network the PC is already attached to (namely, the Internet).

I have two ideas, and they both suck:

1.  Try to find a way to put that device into "Master Mode" so you can share your network through it to your DS or whatever else you're trying to use with it.

2.  Install a Windows XP Virtual Machine inside of Virtualbox, mount the USB device, and set everything up through Windows.

I suppose a third option is to resort to booting into Windows somehow and using it for the time being.  It would be the easier than the above two suggestions.

---

### Post by LiamWilson on 2009-04-19
Are you trying to use it so You can broadcast your Internet too your Wii/DS?

I'm not too sure about it, but these might help somewhat:

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)
[http://www.gamefaqs.com/portable/ds/file/925329/40161](http://www.gamefaqs.com/portable/ds/file/925329/40161)

Take a look. The 1st one is a guide to setting it up on linux, but only Recieves, (Like a wireless card in a laptop)

The 2nd one is a quide to setting it up in windows. However, if you use Wine, it may help, but I'm not too sure.

EDIT:// The FAQ does cover Gnu/Linux, section 4.1, it's about 1/4 of the way down.

---

### Post by jayjay960 on 2009-04-20
My  main use for it would be my iPod. I had modified drivers and everything set up under Windows so I could use it as a regular AP, but Windows is kind of inaccessible for me right now.

I found this page:
[http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto)

I followed the steps but it still doesn't work for me. Also I've tried putting it in mater mode and just get this:
```
jay@jay-desktop:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
jay@jay-desktop:~$ 

```

I think I need native linux drivers instead of just Windows ones under ndiswrapper, but I don't know where I could get any

Edit: An update. A while ago I noticed the light on the wifi adapter flashing like crazy, and my ipod picked up the wifi network "enylwnxoaiepnwoky...". i can connect to it, but I can't do anything like access the internet. I tried to ssh to it (My ipod is jailbroken and has openssh installed, which worked fine with Windows), and I get this:
```
jay@jay-desktop:~$ ssh root@169.254.10.42
ssh: connect to host 169.254.10.42 port 22: No route to host
```
I realise that to be able to use the internet I need to somehow enable internet connection sharing (It would be a great help if someone could tell me how to do that, too), but shouldn't it be able to SSH fine?

---

