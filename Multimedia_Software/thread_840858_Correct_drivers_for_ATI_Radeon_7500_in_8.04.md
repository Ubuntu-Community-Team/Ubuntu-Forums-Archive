---
title: "Correct drivers for ATI Radeon 7500 in 8.04?"
date: 2008-06-25
forum: Multimedia Software
---

### Post by mikeescott on 2008-06-25
What are the correct drivers for ATI Radeon 7500 in Ubuntu 8.04 and where do I find them?

---

### Post by Yuki_Nagato on 2008-06-25
I wouldn't know, but ...

Have you tried installing this hardware using the "Envy" program?

It is designed to install graphics cards.

---

### Post by mikeescott on 2008-06-25
> **Yuki_Nagato said:**
> I wouldn't know, but ...

Have you tried installing this hardware using the "Envy" program?

It is designed to install graphics cards.


I did and got the following:

"EnvyNG Error: Envy does not recognise your card as compatible with any version of the driver. This might happen because either your card is not supported by the driver or Envy's hardware detections failed."

---

### Post by Hayesio on 2008-06-28
I have exactly the same problem! Envy is not fixing this problem. The card is working fine with what ever module ubuntu is running by default, except for tv out -can't get it to work.  I really need tv-out!!!

I second that question, "what driver is best for this card"?

---

### Post by Melcar on 2008-06-28
You need to use the "[radeon]("http://www.x.org/wiki/radeon")" module.  Hardy should load it by default for your card.

---

### Post by Hayesio on 2008-06-29
Brilliant!  Thanks for that link. Tv-out is working now.  The card is working perfectly!

Steps taken;

1. Use "Radeon" module
2. install the xorg-dev, mesa-dev, libdrm-dev and xserver-dev packages for your distro. The usual build tools are needed too (autoconf, automake, libtool, gcc and others) 
3. Run in terminal
```
git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati
```
4.```
cd xf86-video-ati
./autogen.sh --prefix=/usr
make
sudo make install
```

Then,
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard ntsc 
```

The image should now be on the tv screen.

---

### Post by Hayesio on 2008-07-03
Ok, I have another problem now.  To make tv-out work i use the following commands:
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard pal
```

But i have to run these commands every time i boot up, which means i have to have a monitor beside my tv to see what i'm doing. 
Is there any way to make the system automatically load tv-out on start-up so i can get rid of the monitor?  This is a Mythbuntu box, so i want s-vidio as the default output on the card.

Thanks

---

### Post by linuxter on 2008-07-07
Hi guyes. I have Dell Inspiron 5100, with Ati Mobility Radeon 7500, too. I would like to ask you is it possible to explain all the way to make my video card work properly- tv out, to have better performace. Please explain that step-by-step. with links and commands in terminal (if there are) please. Where is that radeon module, from where to download it, how ot use it? I am using ubuntu 8.04. please specify which packages exactly to install via the synaptic package manager. I will be very thankful to you, guys.

---

### Post by CarpKing on 2008-07-07
> **linuxter said:**
> Hi guyes. I have Dell Inspiron 5100, with Ati Mobility Radeon 7500, too. I would like to ask you is it possible to explain all the way to make my video card work properly- tv out, to have better performace. Please explain that step-by-step. with links and commands in terminal (if there are) please. Where is that radeon module, from where to download it, how ot use it? I am using ubuntu 8.04. please specify which packages exactly to install via the synaptic package manager. I will be very thankful to you, guys.

The radeon module is installed by default, so if you have an Ati card and you don't get just a blank screen when you boot up, you are using it.  There are extra options you can set in xorg.conf that might increase performance, but I don't have them at hand.  For TV-out, enter the following commands (assuming you're using an S-video cable):

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard pal
```

As for Hayesio's question about running that command on startup, create a text file called "tv.sh" (or whatever name you like.sh) containing the following:

```
#!/bin/sh
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard pal
```

You should then be able to select that file from Sessions--> Startup Programs.

---

### Post by linuxter on 2008-07-07
Thank you for your quick reply. I will try it and then I will post the results. I hope there will be positive results :wink:

---

### Post by linuxter on 2008-07-07
Hi. guys. There is no effect when i type those thing in the console:
```
linix@cybers:~$ xrandr --addmode S-video 800x600
linix@cybers:~$ xrandr --output S-video --mode 800x600
linix@cybers:~$ xrandr --output S-video --set tv_standard pal
linix@cybers:~$ 

```

After that there is nothing happening in the TV display. I have turn it to AV ...
My graphics card is ATI Mobility Radeon 7500 64MB Ram, on Dell Inspiron 5100. Please help.

---

### Post by CarpKing on 2008-07-08
What sort of cable are you using to connect the TV to the computer?

---

### Post by linuxter on 2008-07-08
I am using the S-video cable. On the one side it has about 6 or 10  metal pin-like thins and ot the other side(which is for the tv) it has onle bigger metal pin-like thing and in round form metal surrounding that bigger pin-like thing. The sold it to me for a S-Video cable for Ati cards. And it enters perfectly in the laptop port, and on the other hand, it enters perfectly, too, in the port of the TV set. Please help.

P.S. Maybe i do not have the right module.. for my card, because it cannot run the desktop effects as it run them in the previous release of ubuntu. now i cannot run effects.

---

### Post by taromsn on 2008-08-12
I got my S-video to work like hayesio did, but videos in VLC or Totem won't play on my TV, has anyone else figured out how to do this?

---

### Post by Aikimox on 2008-09-24
Well, I give up... I've messed up trying to improve this video card performance (it was not too bad by default, had compiz running and video files played ok) And now after my messing with it - all is wrong. Video files can't be played anymore (just a blue/green screen, and sound on any player), and general visual quality is poor, every time I scroll or drag a window there's a strange sound coming out of the ... probably video card.

Is there a way to restore to the defaults without reinstalling the OS?
It's pretty hard to backtrack all the changes done so this far, and I'm desperate... Please help!?

Thanx in advance and have a good one!

---

