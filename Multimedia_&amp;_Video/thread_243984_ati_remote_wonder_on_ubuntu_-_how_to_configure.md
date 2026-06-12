---
title: "ati remote wonder on ubuntu - how to configure?"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by pulper on 2006-08-25
i just installed ubuntu after a long hiatis from Linux.  I have to say that i'm very impressed with how far linux has come (the x-server fiasco aside) <g>.

i would like to be able to configure my ati remote wonder on ubuntu.  i currently like using the rhythmbox player and would like to skip songs and adjust the volume (perhaps these are two separate things for the remote - i'll describe in a bit).

the remote can actually move the mouse so i know it is recognized.  i just don't know if there is a plug-in for the rhythmbox player.  if there isn't, then i should be able to adjust the remote keys to simulate keyboard strokes to advance songs if i know how to configure the remote.  any help?

also, the remote changes the master volume but doesn't adjust the volume of the player.  for some reason, the master volume does not change the volume of the player (only the computer).  i'm using a sblive card and it is connected to my denon receiver via ac3.  is this a sound card issue?  if so/not, any advice on this?

any help on either would be greatly appreciated.  Thanks!

Paul

---

### Post by capran on 2006-12-05
BUMP!

I've been using my Shuttle XPC as a HTPC with Kubuntu 6.06 and now Ubuntu 6.10 for several months. I had originally bought an ATI Remote Wonder to use with it, but I've only been using it as a remote mouse, basically. And it's a poor one at that since the thumb directional doesn't work quite right for me.

I've looked into setting up the buttons for applications, but there is no easy way to do it. It requires making a config file for every application you want to control, and I can't find anything that's specific to my remote and the applications I want to use (mostly Mplayer, VLC, Democracy Player, MythTV, some emulators)

---

### Post by superm1 on 2006-12-07
Guys, 

If you are using the kernel driver (ati_usb if my memory serves me right), then your remote is a standard hid device.  Each of the keys will produce a keystroke or a mouse movement.

If you want certain keys to always perform actions like launching a program, xbindkeys will do this.

If you want to remap certain keys to be different keys, xmodmap will do this.

If you want application specifc things, you will need to use lirc instead.

---

### Post by cracker on 2006-12-19
Hello, I got my remote wonder working thanks to this thread (and a few other sources). However, I am having problems with keystrokes being repeated--for example, when I press the play/pause key I have set, it sometimes presses two, three, or even four times, leaving undependable playback results. Is there any way to correct this? I'm using xbindkeys and XMMS.

---

### Post by superm1 on 2006-12-19
> **cracker said:**
> Hello, I got my remote wonder working thanks to this thread (and a few other sources). However, I am having problems with keystrokes being repeated--for example, when I press the play/pause key I have set, it sometimes presses two, three, or even four times, leaving undependable playback results. Is there any way to correct this? I'm using xbindkeys and XMMS.
If your using the kernel ati_remote or ati_remot2 driver, AFAIK, no.  Are you sure that you just dont accidentally have multiple instances of xbindkeys running?

---

### Post by cracker on 2006-12-20
I'm sure. I used 'killall xbindkeys' a few times while setting it up. It autodetected the hardware when I plugged it in, and it's using ati_remote. I had this problem when I was using it in windows too, so it wasn't that unexpected, just a tad annoying.

---

### Post by superm1 on 2006-12-20
> **cracker said:**
> I'm sure. I used 'killall xbindkeys' a few times while setting it up. It autodetected the hardware when I plugged it in, and it's using ati_remote. I had this problem when I was using it in windows too, so it wasn't that unexpected, just a tad annoying.

Well the only thing I could think to possibly help the situation is to modify the source and ignore every other keypress for this driver or something to that nature, but thats probably a tad bit overkill to overcome this problem.  Sorry couldn't help you out :(

---

