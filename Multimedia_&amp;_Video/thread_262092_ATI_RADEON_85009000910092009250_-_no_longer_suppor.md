---
title: "ATI RADEON 8500/9000/9100/9200/9250 - no longer support"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by Pawel on 2006-09-21
> As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver [version 8.28.8]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=23096")

I just want to say for people who have one of these cards, and have  problems with (eg. TV-Out + too high gamma on primary monitor,3D doesn't work or sth. else)   - there is a very good alternative for ATI Proprietary Linux Display Drivers.

It's called open source :)

In my case:
Radeon 9200SE - works 3D.
TV-OUT works with this path:
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)


Best regards.
P.S. If you want some help with apply this path - just post on this thread.

---

### Post by sbjaved on 2006-09-26
I have the same card...How did you get it working with 8.28.8? I'm a newbie so detailed tutorial required...

---

### Post by blackpaw on 2006-11-13
> 8500/9000/9100/9200/9250
> **sbjaved said:**
> I have the same card...

Well, you are not really giving a lot of information ;)

Following this guide:
[http://megahurts.dk/rune/tv_output.html]("http://megahurts.dk/rune/tv_output.html")
is very helpful if you need working TV-out and don't care for 3D-accelleration.

On the other hand, this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") 
seems to be very effective when it comes to enabling 3D accelleration but it seems to have some trouble with dual screens (too high gamma, etc.)

If you want both, it might be the wisest to use the proprietary driver that ATI suggests for this card (if you go to their website and select the driver for Linux > Radeon > [your card here], they will point you to a driver that is somewhat older than the current one) as - as Pawel pointed out - with the current one the 8500/9200 are no longer supported.
In this case, just follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") and use method 2, but replace the driver they suggest with the one you downloaded. 

<irony>
Then, if it works, count all the hours you spent on making it work and compare this with how many hours you have to work overtime to get an nvidia card equivalent to a 9200.. let's say, FX5200, ~40$, I have to work 4-5 hours for this one. 
</irony>

---

### Post by kharl on 2007-02-05
> **blackpaw said:**
> 
<irony>
Then, if it works, count all the hours you spent on making it work and compare this with how many hours you have to work overtime to get an nvidia card equivalent to a 9200.. let's say, FX5200, ~40$, I have to work 4-5 hours for this one. 
</irony>

It's good idea... My next computer will be linux-support-optimized. And I am considering replacing my ATI Radeon 9100 (r200) seriously... Because, in my case, it still doesn't work. Now I understand people who start flame wars.

---

### Post by barney_1 on 2007-02-05
So, here's a question for you.  I have an ATI 9000 running fglrx version 8.28.8 on Ubuntu 6.10 Edgy Eft.  I am using this box for mythtv and therefor am only using the TV out port; I don't have a monitor hooked up to it.

I am having trouble getting the overscan settings to work because I have the driver setup in mirror mode (I couldn't get everything to work otherwise).  This leaves a black bar at the top and bottom of the screen that I can't seem to adjust.  

Would switching to the gatos drivers allow the same setup, but add the ability to make adjustments with tv overscan?

---

### Post by Steve H on 2007-02-11
I am seriously starting to consider turning my back on ATi. I have always preferred them for various reason, and that have always worked beautifully for me under XP. I was hoping to be able to turn my back on Mr.Gates's evil empire but it does not look like it will be the case anytime soon unless i fork out for Nvidia. I have been trying for a week or two now to get my ATI 9000 pro to get along with Edgy, as everytime i plug in my s-video cable (which is hooked up to my TV) i get brightness/gamma problems which no-one seems to be able to resolve. I watch alot of downloaded media on my TV which is piped from my PC, yet i still have to dive into Windows to be able to watch anything on my TV.

I am looking at Nvidia prices online as i write this........

---

### Post by barney_1 on 2007-02-11
I'm in the same boat with you Steve H.  I get a washed out picture on my monitor if I am using the tv out on my ATI 9000.  I think the cards work ok, but ATI has never had adequate support when it comes to linux drives.  How unfortunate.

---

### Post by dracomordag on 2007-02-11
alright, i'm trying to install ubuntu (edgy eft) on my desktop computer. specs: 2.7 GHz, 512 MB RAM, Radeon 9200 PRO

i boot up, the LiveCD ish opens. i select "start or install ubuntu"

it goes through the loading sequence (checking file systems, fsk 1.39, etc.), then these errors pop up:


[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0044.jpg[/IMG]
[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0045.jpg[/IMG]
[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0047.jpg[/IMG]




what the hell do i do?

---

### Post by kittyhawk63 on 2007-02-11
dracomordag  
As a novice to Ubuntu, I have found the easiest way to eliminate this is to do a new install.

---

### Post by dracomordag on 2007-02-11
that was from the live cd

i've gotten ubuntu working without the livecd now, but i havent yet been able to use the radeon 9200. right now i'm just using the shitty default card. you can check my posts in the stickied thread about ATI cards to see whats up

( [http://www.ubuntuforums.org/showthread.php?p=2142396#post2142396](http://www.ubuntuforums.org/showthread.php?p=2142396#post2142396) )

---

### Post by Steve H on 2007-02-16
I have now given up on my ancient Radeon 9000 card, and have opted for a nice new(ish) GeForce 6200. It is definitley more compatible than ATi straight out of the box. On my old card i kept having the primary monitor view being squashed and with washed out gamma when the TV s-video was plugged in, not so with the Nvidia card. 
It took some jiggery pokery to get the driver installed and now it works fine. Now i just need to decide how to use multiple monitors, TwinView etc.:lolflag:

---

### Post by barney_1 on 2007-02-22
I am also struggling with an ATI 9000 because I want to use the tv out (an only tv out, no crt monitor) with MythTV.  I've been able to get it to work but haven't been able to use the overscan options that should work for this card.  I have about a half inch black bar at the top and the bottom of the screen that I can't seem to adjust at all.

No scavenging ebay for a cheap nvidia card that will work better.  I guess I should commend ATI for working to improve their Linux drivers but since this card has been dropped from current support they're basically saying a big screw you if there are still bugs in the old builds.  Bah!

---

### Post by mimmo.marozzi on 2007-02-24
do the following after a recovery start:

sudo dpkg-reconfigure xserver-xorg

and then when it's time to set option for acceleration and other stuff disable everithing: you'll get back at your desktop though without 3d acceleration

---

### Post by elnegrito on 2007-06-22
Has anyone got lucky running the TV-Out on a Radeon 9250 with Feisty? All I want to do is to watch   my downloaded media on my TV.

---

### Post by Elvis1985 on 2007-06-29
I am also using an ATI Radeon 9250 with Feisty, and am having the same problem.
My TV will display everything during boot, and when the graphical interface starts all i have is white and grey stripes with some blurriness.

I have tried about every solution I could find through google, and none of them have worked.

If anyone has had ANY success, or knows where to get an open source driver that might work, please let us know...

---

### Post by soul_motor on 2007-06-29
I have a 9250, and it took me a month and a half or so to realize that my video card was the source of all my problems.  At least as it related to Ubuntu...  I had to switch my BIOS to the integrated card to get it up and relatively running.  I found the guide at [http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon) really useful.  I'm actually using my 9250 now, and the beryl is kinda neat too, just eye candy.  My only problem is I dual boot with XP, with XP as the default.  It doesn't load at all when I tell BIOS to use the ATI card, it stops.  So now I have to give it a couple of seconds, hit the arrow key, and enter.  It works, but I can't see the GRUB loader...  If anyone knows how to fix that, it would be awesome, otherwise it's a small price to pay to be able to use my ATI card.

---

