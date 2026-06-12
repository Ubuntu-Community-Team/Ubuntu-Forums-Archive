---
title: "Hardware requirements needed to run HULU"
date: 2009-06-27
forum: Multimedia Software
---

### Post by wpshooter on 2009-06-27
I just tried the HULU site where you can watch videos, etc.

Run fairly well, but I am wondering what I can do to make it even better.

I am using Jaunty.

A few questions.

During watching one of the movies, I noticed that occasionally there will be a momentary lag/slow-down in the video and at that same time the hard drive is being accessed (either read or written to).  

What exactly is the cause of this and how can this be overcome ?  Do I possibly need a faster hard drive and also possibly a better/faster video card with more memory ?  And perhaps even a faster processor.

Also, about half way thru the movie, it started doing some pausing while it was doing some type of BUFFERING operation.  What is the exact cause of this and how can this be overcome ?  Do I possibly need more and faster RAM and/or a larger /SWAP partition for Jaunty ?

If you need more stats on my hardware, please let me know.

Thanks.

---

### Post by tgalati4 on 2009-06-27
Run htop in another window and watch cpu load, and swap usage.

sudo apt-get install htop

---

### Post by mgmiller on 2009-06-27
What you are running into is an empty buffer (buffer underrun).  When you try to play the stream, it sends that data to you and begins to fill a buffer on your HDD.  It then plays the movie from that buffer.  Ideally, it can stream to and save to your buffer faster than you can play it.  If the buffer empties out because your internet connection is a little too slow, the movie will pause while the buffer refills.

What I like to do when watching Hulu is to start the move, then hit the pause button.  You will see a graphic for the buffer, wait for it to fill up, then hit the play button.  Hopefully, you will be far enough ahead of the stream to not run into the problems you are having.

In short, it's probably not your hardware, it's the speed of your internet connection.

---

### Post by freechelmi on 2009-06-27
Hulu Use Flash. 

Flash has very poor video performance compared to a Native Player. 

You should play the Hulu content with your favorite media player ( Totem/VLC)

---

### Post by wpshooter on 2009-06-27
> **freechelmi said:**
> Hulu Use Flash. 

Flash has very poor video performance compared to a Native Player. 

You should play the Hulu content with your favorite media player ( Totem/VLC)

If Hulu uses Flash (which I have installed) and you are saying I should use Totem (which Synaptic shows I also have installed) then how do I get HULU to use Totem instead of Flash ?  

Synaptic says that Totem is installed but I do not see it on a menu anywhere.  But it does open when I run it from the terminal.  Why is this not placed on a menu ?

Thanks.

---

### Post by mgmiller on 2009-06-28
> Synaptic says that Totem is installed but I do not see it on a menu anywhere.

It should be in Applications > Sound and Video > Totem Movie Player

If it's not there, right click the Applications drop down and select Edit Menus
On the left side, select Sound and Video and on the right side put a check mark next to Totem Movie Player.

I also would like to know how to get hulu to play with totem or vlc instead of flash.

---

### Post by wpshooter on 2009-06-28
> **mgmiller said:**
> It should be in Applications > Sound and Video > Totem Movie Player

If it's not there, right click the Applications drop down and select Edit Menus
On the left side, select Sound and Video and on the right side put a check mark next to Totem Movie Player.

I also would like to know how to get hulu to play with totem or vlc instead of flash.

Actually, the "movie player" listing was already on the menu, it is just not listed as Totem.

Anyone know how to associate HULU with Totem movie player ?

---

### Post by freechelmi on 2009-07-14
Sorry for late reply. 

We use seom Firefox Extension usually to catch Flash video URL such as VideoDowloadhelper or GreaseMonkey-YoutubeNOFlashAuto But I ve read it does not work with Hulu because they use a special session handling to get sure you use your browser and the flash client.

I live in Europe but if you can advice me a proxy I can give it a try .

---

### Post by FreeOSduh on 2010-10-08
Ok guys,

I'm new to Ubuntu :)

I have the same situation - streaming from Hulu is really slow/laggy. I'm on wifi but I don't think its the issue because on other PCs, they stream perfectly fine. The problem is the CPU spikes up to 100% when I'm streaming on the web. 

On Hulu Desktop, its still slow, but the CPU usage is about 97%. But this is probably because the hardware requirement is at least Intel Core 2 Duo. I'm not sure whether it requires more CPU power (I don't think that is the problem), or better graphics card or more RAM... And yeah I'm running 10.04 I think

Hardware Specs:
Athlon XP 2600+ 2083MHz
1.2 GB RAM
HD Radeon X850 Pro 256MB AGP :(
40 GB SATA Seagate ST340810A

Lastly, I really hate the use of flash on the web. Or flash in general. I tried coding using ActionScript 3 and I hate it.  

Anyways, I hope you guys could help me out.


Thanks

---

