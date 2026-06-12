---
title: "resume / wake from USB LIRC"
date: 2010-01-04
forum: Multimedia Software
---

### Post by wardy277 on 2010-01-04
Hi,

I have setup a htpc and have the remote working through lirc. i have it to shutdown with the remote but not start up again.

I have a zotac Ion and would really love it if i could turn it on with usb. i have managed to turn on wake on lan, which works great. I had to edit some settings to get it to enable Wake on lan in the shutdown config. Do i have to do the same with wake on USB?

i know there is power in the USB as the Receiver lights up red when i press something on the remote when the pc is off. 

Any ideas?

Chris

---

### Post by wardy277 on 2010-01-06
any one? is this even possible?

---

### Post by stanger192 on 2010-03-04
What kind of ir receiver are you using?

---

### Post by wardy277 on 2010-03-04
Thanx for the reply,

I am using a USB Microsoft [MCE reciever]("http://www.letsautomate.com/images/11992.jpg")

Chris

---

### Post by stanger192 on 2010-03-05
Try this
[http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake#Enable_Wake_on_USB_Activity](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake#Enable_Wake_on_USB_Activity)

How have you found suspend and resume under ubuntu? ive found it a bit hit and miss using the zotac ion itx a board. im currently installing xbmc using the xci script with a minimal ubuntu install. its tailored to ion chipsets, and is supposed to setup suspend and resume via usb remote automatically.

---

### Post by wardy277 on 2010-03-05
I have tried resuming from suspend, and it works great. The problem is, when i do resume, it asks me for my password. (And it makes the speakers pop which is enoying)

I us my HTPC as a pc also, downloading torrents, browsing the web (i am doing it right now lol), so the xci wont do.

I think what i want is more of a hardware thing, setup i nthe bios like old computers could powwer on using the ps2 keyboard. Its a shame that i can get wake on lan working, but i have to have my laptop on for that. kind of defeats the purpose and is easier to simply press the power button. Or i could get a extendable stick lol.

Chris

---

### Post by stanger192 on 2010-03-06
its possible. ive just finished my install of the minimal ubuntu and xbmc with the xci script and resume is working flawlessly. i just suspeneded and work up my system 5 times with no hiccups, all thrugh my usb remote! im amazed! i highly reccomment trying this script, it also adds temp sensors and sorts out audio + video drivers. here is the link
[http://forum.xbmc.org/showthread.php?t=69753](http://forum.xbmc.org/showthread.php?t=69753)

also i had to follow this guide to setup my mceremote

[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes)

i used 0.8.6 instead of 0.4.3pre and lirc_mceusb instead of lirc_mceusb2

now all i need is to get 5.1 optical passthrough audio downmixed and sent over hdmi and im done setting it up!! never thought id get here!!
good luck!

---

