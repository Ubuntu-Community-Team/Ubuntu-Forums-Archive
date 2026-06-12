---
title: "How to use a Sony Handycam on Ubuntu Feisty"
date: 2007-06-02
forum: Multimedia Production
---

### Post by jellofishy on 2007-06-02
Hi there I'm completely new to Ubuntu and Linux in general.

I got a Sony DCR-TRV280 Digital 8 Handycam as a gift and I own a Clevo D470V.
I have completely reformatted my computer and made the switch from Windows XP to Ubuntu Feisty.
Now, I want to be able to transfer video taken on my MiniDV tape camcorder and transfer it to my laptop.

The camera box comes with an installation CD for Picture Package and the USB drivers.
When I insert the CD, my laptop doesn't seem to recognize it and I can't access the contents of the CD through the file browser.
I don't think I need the Picture Package Software but I might need the driver for my camera.
I've tried googling for the driver alone, but I always seem to get the full package in the results and the camera manual states that the software is only supported on Windows & Mac.

When I plug in my camera, and I type in:
```
lsusb
```
I get:
> Bus 004 Device 003: ID 07c4:a600 Datafab Systems, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 054c:00c0 Sony Corp. Handycam DCR-30
Bus 001 Device 007: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 001: ID 0000:0000
Which should mean that my laptop recognizes that I've plugged in my Sony Handycam.

But when I open Kino, I don't see any indication whatsoever for me to at least view the footage on my computer.
I tried pressing the play button on the camera itself but it doesn't affect my laptop in any way.
[B]
What I would like to be able to do is at least transfer footage from my camera unto my laptop[/B] so that I can get someone else to do the editing for me. But I just don't even know where to start.

If anyone can help me find a way to do this without spending more money on a new camera or switching back to windows, I'd really appreciate it.
I like the quality of tapes better than DVD or Hard-drive cameras, and IT IS possible to digitally transfer the video, I just need to know how to do it on Ubuntu.

Please help me, as I've exhausted myself since day one, trying to customize Ubuntu to suit my needs. I've gone through so much already, constantly reformatting just trying to sort out stuff like my graphics card and touchpad because I keep messing up stuff in the terminal & synaptics package manager, and this is the only other thing I need to sort out before I can truly say that Ubuntu can kick Microsoft's butt!

Cheers.

:D

---

### Post by jellofishy on 2007-06-02
Oh and specifications of my laptop are at:
[http://www.clevo.com.tw/products/D470V.asp](http://www.clevo.com.tw/products/D470V.asp)

and information about my camera can be read here.
[http://www.camcorderinfo.com/content/Sony-DCR-TRV280-Camcorder-Review.htm](http://www.camcorderinfo.com/content/Sony-DCR-TRV280-Camcorder-Review.htm)

---

### Post by firedancer on 2007-06-19
i guess you have to use fire wire with kino 


maybe there's away to work around it, but i ran to the store to get me a fire wire pci card 

but i have a desktop, soyou might be able through a pcmcia fire wire card , that's a possibility 


i use a sony DCR-TRV350 NTSC,

after a few reboots did a sudo kino and was able to capture video, so far i had  problems with  sound after i make changes , i don't hear the sound , i know you don't really have to hear this but...................... i believe you have to think fire wire it's much better anyway

 usb didn't even worked for me in xp , neither for a few folks  i know (M$ bugs they never even worry mentioning)

  AWG 00.02ct

---

### Post by firedancer on 2007-06-19
i see you have one fire wire input, use that jellofishy

you probably figured it out already:popcorn:

---

### Post by timcredible on 2007-06-19
you can use kino with firewire if you have a minidv camcorder.  not sure there's anything in linux for digital 8.

the stuff that came with the camera on the cd is for windows only, you can't use it with linux.

---

### Post by lindykid on 2007-06-19
I have just switched from XP to Ubuntu my self, and was able to use Kino to capture video from my Sony Digital 8 camcorder using the Firewire connection just fine.  (The USB video is very bad, I would recommend using the Firewire.)  It took me ~2 hours to capture 40 mins of video, splice out the unwanted sections, create a DVD iso and burn the DVD all in Ubuntu...  Good-bye Windows!

---

### Post by jellofishy on 2007-06-20
Thanks to everyone who replied!

The camera didn't come with a firewire cable actually, but I'll be getting one soon and hopefully I can start doing some serious filming.

Cheers!

---

### Post by lisati on 2007-07-23
> **timcredible said:**
> you can use kino with firewire if you have a minidv camcorder.  not sure there's anything in linux for digital 8.

the stuff that came with the camera on the cd is for windows only, you can't use it with linux.

I have a MiniDV camera and a Digital-8 camera, Both have firewire

---

