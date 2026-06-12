---
title: "iwconfig: cannot set encryption key"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by mringer on 2012-12-30
I am not asking for help in this post but reporting what happened in the
hope that the next person to fall into this booby trap will be able to
climb out sooner than I did.

Dell Inspiron 1525, Broadcom BCM 4312. I installed lubuntu off the live 
CD and the wireless failed, as usual. Previously (several times) I have
got it working by installing wicd and ndiswrapper but not this time.

I Installed wicd and firmware-b43-lpphy-installer and did

```

sudo iwconfig wlan0 key s:password
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

This was reported in 2010:

[http://ubuntuforums.org/showthread.php?t=1552080&highlight=iwconfig+key](http://ubuntuforums.org/showthread.php?t=1552080&highlight=iwconfig+key)

and one of the replies said that you can set the key with wicd. This
means: install wicd and wicd-gtk, and then start > internet > wicd >
channel > properties. I set the key with no visible error, but still
couldnt connect. 

After some hours of misdirected effort I realised that you must not only
set the key but also the style of encryption (in the space just above 
the key). My wireless now works (until the next time). Sorry, I dont 
know any plausible way to find what is the correct style.

---

### Post by ahallubuntu on 2012-12-30
Most people would probably prefer to stick with Network Manager for managing their wireless (or Wicd) using a Gui and not use a command line to change wireless settings.  You are welcome to do it that way, of course, if you choose.  There are also known ways to get the b43 drivers working correctly so you can use the Gui and not worry about it again.  Pity it's still not always simple to do that even with recent versions of Ubuntu.

---

