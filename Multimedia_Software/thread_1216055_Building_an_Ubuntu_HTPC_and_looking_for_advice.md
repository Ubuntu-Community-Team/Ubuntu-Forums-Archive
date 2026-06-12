---
title: "Building an Ubuntu HTPC and looking for advice"
date: 2009-07-17
forum: Multimedia Software
---

### Post by djbon2112 on 2009-07-17
Hello everyone. I'm working on an HTPC that will use Ubuntu as its operating system, and I'm trying to do as much research as possible before buying the parts to minimize my frustration!

First, the purpose. It will be used to stream 720p HD movies and TV shows (as well as a bit of SD content) via Wireless-N from my Fileserver, and display it on my 720p HDTV. I'm looking to make this playback as smooth as possible, while keeping the future possibility of moving to a full 1080p TV open. At first I will not have a discrete video card, though that possibility is there.

The hardware I've chosen so far is a run-of-the-mill Intel midrange system.

Motherboard: ZOTAC N73USupreme
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500006](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500006)

CPU: Intel Pentium E6300 Wolfdale 2.8GHz
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16819116091](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819116091)

All other parts are pretty much generic (RAM, disk). A discrete video card is NOT part of my purchase plans (the motherboard has both HDMI and a D-Sub connection and an integrated nVidia 7150).

**Question 1: Do you think this hardware is sufficient for 720p on Ubuntu, ignoring things like VDPAU?**

**Question 2: Can anyone recomend a good IR receiver that has few problems with Linux?**

Now, on to the software. The OS will obviously be Ubuntu 9.04. My main concern is looking for a video player that will do what I want. I'm leaning heavily towards XBMC but I'm wondering if that's the right choice. I need something that will actually play 720p decently on the hardware (or let me use something like CoreAVC), while also allowing me to use a Harmony remote for control. It needs to have some sort of media library function for browsing. Something full screen and skinnability is also a benefit but I can live without it if it looks good.

**Question 3: What media player would you recommend for such an HTPC?**

With these initial questions, I hope to lay out my plan. Thanks in advance for any responses!

---

### Post by zeronothing on 2009-07-17
I too am looking to build a HTPC. I'm really trying to keep the forum factor small with little heat. I'm looking to build a Nvidia Ion based setup. Their aren't to many but their are a few on newegg.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028)

Zotac makes a intel dual core atom motherboard with the nvidia Ion graphics chip on the motherboard. The motherboard is a mini-ITX size which is nice and small. The Nvidia Ion chip that is built on the motherboard is really just a Nvidia 9400 graphics card (really nice for HD). The only other pieces you need are memory, case, and a remote. One of the best remotes to get are the older Windows Media Center controllers if you can find one. 

[http://www.amazon.com/Microsoft-Control-Receiver-Windows-A9O-00007/dp/B00066FIO6/ref=sr_1_1?ie=UTF8&s=electronics&qid=1247882262&sr=8-1](http://www.amazon.com/Microsoft-Control-Receiver-Windows-A9O-00007/dp/B00066FIO6/ref=sr_1_1?ie=UTF8&s=electronics&qid=1247882262&sr=8-1)

I was going to build a boxee media center setup for my TV.

---

### Post by zeronothing on 2009-07-17
Oh and one more thing, their aren't to many wireless-N solutions right now for linux. That will be the hardest part of your task. I ran Ethernet outlets around my place. I specifically had one run right behind where my TV set is.

---

### Post by zeronothing on 2009-07-17
Sorry in my post about the Zotac motherboard I believe I posted the wrong one. Here is the one I want

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500030](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500030)

---

### Post by gordintoronto on 2009-07-17
> **djbon2112 said:**
> 
Motherboard: ZOTAC N73USupreme
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500006](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500006)



Did you notice that 55% of the reviews are one or two eggs?  Quite a contrast to the Atom 330 board, which will go in a smaller case and require a smaller power supply.

---

### Post by steefjeqv on 2009-07-18
Hi,

Look for a motherboard with Nvidia 8xxx/9xxx graphics onboard.
These chipsets support VDPAU (Nvidia's video accelaration API).

This will allow you to watch high quality HDTV without using too much cpu power.

It works fine here on my Xine based HTPC with VDR (Linux Video Disk Recorder).

Greetings,
Steven

---

### Post by sloggerkhan on 2009-07-18
If you want 720p playback, you will be fine with any CPU + Integrated graphics combo that outclasses an Atom with 945. (Atoms are supposed to be able to play 720P out of the box, but my experience is very mixed, I woudn't rely on it, though maybe the newer atoms perform better.) (I have a netbook and a lot of the time it loses audio sync on 720P and has stuttering video, but with audio turned off plays back the video smoothly.)

If you get an AMD low voltage X2 with integrated nvidia or ati graphics, 720P will be fine. If you get an intel E-Series CPU with modern integrated graphics, 720P will be fine. With nearly anything recent 720P will be fine. However, playing back 1080P will most likely not be fine unless you get a fast CPU or use VDPAU. At least in my experience. 

Myth, XBMC, or Moovida are your best bets for media center software. I lean towards Myth because it gives more control over video playback options.

---

### Post by zehner on 2009-07-18
With a fast cpu it is possible to watch unprotected 720p without vdpau, but it makes a lot more fun with it. 
I've started my htpc with an integrated ati graphic and because of the lack of XvBA I have to watch all 1080p content unaccellerated. Now I switched to a nvidia board and everything looks smoother.

XBMC is a must. My first installation was Mythbuntu with MYTHTV. It took me a few days to get all extensions and configure it for my country. Then I tried XBMC. After installation from PPA and a few minutes of configuration, everything works. And in my oppinion, MYTHTV looks a bit homespun, XBMC has the WOW factor

Try XBMC, install the latest SVN(stable has a bug with vdpau), perhaps you make the same experience and if not, the uninstallation takes also only a few minutes :-)

---

### Post by steefjeqv on 2009-07-18
Hi,

If you like a full blown mediacenter then XBMC is certainly worth it.

It get's even more interesting when you combine with a VDR tv backend.
It isn't fully developed yet, but there are some good ppa repo's available :

[https://launchpad.net/~mirak-mirak/+archive/ppa]("https://launchpad.net/~mirak-mirak/+archive/ppa")

Personally, I do prefer a lean VDR setup combined with VDPAU and some nice plugins (Freesat EPG, Noad, DVD Burn, ....)

Greetings,
Steven

---

### Post by djbon2112 on 2009-07-18
> **gordintoronto said:**
> Did you notice that 55% of the reviews are one or two eggs?  Quite a contrast to the Atom 330 board, which will go in a smaller case and require a smaller power supply.

I did but I was also looking at price. That Atom one looks awesome, for almost the same price as the CPU + mobo.

Since I CAN use VDPAU with this that seems to be my route, with XBMC.

---

### Post by geoffjay on 2009-07-18
I would also recommend trying XBMC, it has a very nice front end and if you've got projectM installed it is able to use that as your audio visualization. One piece of advice I'd offer though is to disable all desktop effects, or do what I did and use openbox as your window manager along with XBMC. I had various problems with XBMC locking up whenever I tried switching it to 1080p while running Gnome + Compiz.

---

### Post by Whiffle on 2009-07-18
I have this receiver:

[http://cgi.ebay.com/Dell-Media-Center-Remote-USB-IR-Receiver-OVU104007_W0QQitemZ370216379684QQcmdZViewItemQQptZPCC_Video_TV_Cards?hash=item56329da524&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|293%3A1|294%3A50](http://cgi.ebay.com/Dell-Media-Center-Remote-USB-IR-Receiver-OVU104007_W0QQitemZ370216379684QQcmdZViewItemQQptZPCC_Video_TV_Cards?hash=item56329da524&_trksid=p3286.c0.m14&_trkparms=65%3A12|66%3A2|39%3A1|72%3A1234|293%3A1|294%3A50)

(got it for $14 + shipping on ebay)

and I'm using a DirecTV remote I got at a garage sale for 50 cents.  Works great.


As far as software, for the moment I'm having GDM autologin to fluxbox, and then I can launch stuff with the remote.  Boxee is my primary media program right now because it does Hulu, Pandora and other fun stuff.

---

### Post by sloggerkhan on 2009-07-20
The major downsides to xbmc: no advanced subtitles, errors on 64bit systems.

---

### Post by djbon2112 on 2009-07-21
> **sloggerkhan said:**
> The major downsides to xbmc: no advanced subtitles, errors on 64bit systems.

I don't really need either (this unit will be 32-bit, 2 GB of RAM tops) and I dislike subtitles.

Now, it seems Newegg has removed (at least for me on newegg.ca) that Zotac combo, but the cheaper one ([http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500029](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500029)) is still around. It seems to be the same, but with the single-core Atom. Will this still be good enough? The reviews seem to say so (with VDPAU) but I want to be sure.

---

### Post by gordintoronto on 2009-07-21
> **djbon2112 said:**
> Now, it seems Newegg has removed (at least for me on newegg.ca) that Zotac combo, but the cheaper one ([http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500029](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813500029)) is still around. It seems to be the same, but with the single-core Atom. Will this still be good enough? The reviews seem to say so (with VDPAU) but I want to be sure.

I've seen a review which suggests the Atom is iffy for playing youtube videos full-screen.  The single-core Atom+Ion was OK for blu-ray playback in the same review.

My six-year-old Athlon (2.0 GHz) is OK with full-screen youtube videos...

---

### Post by sloggerkhan on 2009-07-22
Your flash playback with probably suck (though I think flash may finally have xvideo support if you meet a bunch of idealized conditions), all other video should be fine with nvidia graphics + vdpau (possibly excluding some 1080P).

---

### Post by TomtheWombat on 2009-07-23
> **sloggerkhan said:**
> Your flash playback with probably suck (though I think flash may finally have xvideo support if you meet a bunch of idealized conditions), all other video should be fine with nvidia graphics + vdpau (possibly excluding some 1080P).

I have the single core atom+Zotac board with bundled power supply from Newegg.  It works great for 720p video.  Previously I had a 2.3ghz X2 processor, and there would be noticeable issues in complex sequences (explosions).  With VDPAU on the ion everything is great.  I can even seek through the movie without having to wait!!

I have not tried 1080p or full screen flash.  I think that I played a full screen video from CNN in Boxee, though.  I did have some issues playing Hulu in Boxee, but I think that was do to network issues.

If you have any questions regarding performance, then I can do my best to answer them for you.

---

### Post by xzero1 on 2009-07-23
Full 1080p 1920x1080@24fps video (itunes) plays smoothly with fanless 3300IGP motherboard BIOSTAR TA790GBX a2+ with cpu locked at 800Mhz using ati catalyst 9.6 drivers under Ubuntu 9.04 with compiz. Note: acceleration currently only works full screen.

---

