---
title: "Using mobile broadband"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by octotom on 2009-05-29
Earlier this week, I got internet from Vodafone as the provider.  Until they're able to set up the actual telephone/internet lines in my house, they gave me a mobile broadband stick to use to get on the internet.

Is there a way that I can configure ubuntu/kubuntu to actually use this card?  Or is using Windows going to be my only bet until I'm able to use a landline?

---

### Post by madverb on 2009-05-29
From what I know mobile modems work perfectly in Ubuntu.

---

### Post by lisati on 2009-06-05
Plugging in the stick the first time should make Ubuntu pop up a dialog to select the settings you want.

---

### Post by bluestreek on 2009-06-05
I am guessing you have tried it already before asking this question since you say its already been given to you. If you installed wicd or another network manager you will need to install Vodafone Mobile Connect from beta vine which is similar to the software automatically installed with windows.

---

### Post by Forgetful on 2009-06-05
Hi, 
I've got a Vodafone K3760. I've been trying to get it to connect to Jaunty64 on a HP Parvilion for about three weeks on and off. 

I've got to the point where it recognises that a mobile boardband stick has been pluged in (took about two weeks). 

It will not connect. 

Network manager just says GSM network disconnected every time I try to connect.

Help!

I had to use something called udev to turn off the zero thingamy gidgit.

Tried the betavine software but it wouldn't run because of some kind of snake problem. Didn't like my python version.

What do I do now? Take it back to the shop?

Getting frustrated.

---

### Post by chicken159 on 2009-06-05
I have the same USB modem - for me the solution was to install Vodafone Mobile Connect ([https://forge.betavine.net](https://forge.betavine.net)), uninstall Network Manager and replace it with wicd. Simples...well, after a few days of frustration anyway!

---

### Post by tumescentliposuction on 2009-06-05
Hello...
           I think in mobile you only get dial up connection not broadband because if you use broadband connection with that i think problem with mobile get arises in soon time...

---

### Post by chicken159 on 2009-06-05
...ah, the Python problem has been solved but you need to download the latest svn version for the version of python in jaunty:

[https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb](https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb)

That works OK - but you do need to remove Network Manager and replace it with WICD as NM won't play nicely...

Hope this helps!

---

### Post by Forgetful on 2009-06-05
> **chicken159 said:**
> ...ah, the Python problem has been solved but you need to download the latest svn version for the version of python in jaunty:

[https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb](https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb)

That works OK - but you do need to remove Network Manager and replace it with WICD as NM won't play nicely...

Hope this helps!

The weekend is fast approaching and it looks like rain. I'll give it a go.

WICD? Oh well I expect I'll find out what it is soon enough.

Many thanks to all.

---

### Post by chicken159 on 2009-06-05
I've just posted some slightly more in depth (but by no means exhaustive!) instructions on how I got it to work on another thead ([http://ubuntuforums.org/showthread.php?t=1173350&highlight=vodafone+mobile+connect](http://ubuntuforums.org/showthread.php?t=1173350&highlight=vodafone+mobile+connect)).

You'll find wicd in Synaptic...from memory the thing to do is install that and it will replace Network Manager - don't uninstall NM first or you'll be without a network!

Have a fun weekend!

---

### Post by Forgetful on 2009-06-08
There you go... WICD loaded in nicely the betavine software did its thing but still it does not work.

Can you put pictures on this thing?
See attached. It does not recognise the USB stick and is asking for ports.

I've tried /dev/ttyHS0...HS2 but it does nothing useful.

> twdl@big-hp-laptop:~$ lsusb
Bus 002 Device 012: ID 0af0:7501 Option 
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd 
...
> twdl@big-hp-laptop:~$ ls /dev/tty*
/dev/tty    /dev/tty2   /dev/tty31  /dev/tty43  /dev/tty55  /dev/ttyHS0
/dev/tty0   /dev/tty20  /dev/tty32  /dev/tty44  /dev/tty56  /dev/ttyHS1
/dev/tty1   /dev/tty21  /dev/tty33  /dev/tty45  /dev/tty57  /dev/ttyHS2
/dev/tty10  /dev/tty22  /dev/tty34  /dev/tty46  /dev/tty58  /dev/ttyHS3
/dev/tty11  /dev/tty23  /dev/tty35  /dev/tty47  /dev/tty59  /dev/ttyS0
/dev/tty12  /dev/tty24  /dev/tty36  /dev/tty48  /dev/tty6   /dev/ttyS1
/dev/tty13  /dev/tty25  /dev/tty37  /dev/tty49  /dev/tty60  /dev/ttyS2
/dev/tty14  /dev/tty26  /dev/tty38  /dev/tty5   /dev/tty61  /dev/ttyS3
/dev/tty15  /dev/tty27  /dev/tty39  /dev/tty50  /dev/tty62  /dev/ttySL0
/dev/tty16  /dev/tty28  /dev/tty4   /dev/tty51  /dev/tty63
/dev/tty17  /dev/tty29  /dev/tty40  /dev/tty52  /dev/tty7
/dev/tty18  /dev/tty3   /dev/tty41  /dev/tty53  /dev/tty8
/dev/tty19  /dev/tty30  /dev/tty42  /dev/tty54  /dev/tty9

I shall have a browse around the betavine site to see what I can find.

---

### Post by chicken159 on 2009-07-07
Sorry - not checked back lately - but it only works if you insert the usb modem after you have started up/logged in:

1. Start up, log in.
2. Insert usb modem, wait for red light to come on.
3. Start up Vodafone Mobile Connect.

That should do it...if you restart the machine with the usb modem in, it doesn't recognsie it.

---

