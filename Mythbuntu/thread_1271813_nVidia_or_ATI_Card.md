---
title: "nVidia or ATI Card?"
date: 2009-09-21
forum: Mythbuntu
---

### Post by bsntech on 2009-09-21
Hello all,

I am looking to piece together a new MythTV Ubuntu system.

I was curious to know what each of your preferences are for a video card - nVidia or ATI - and what kind of card you have and any troubles you encountered.

The motherboards I'm looking at must have coaxial SPDIF out for connecting to the receiver for digital sound.

I've run across the GeForce 8100 series video cards on several motherboards or the Radeon 4200 series video cards on motherboards.

Me being a little cheap, I am looking to use the built-in video/audio on the motherboard and not have any add-in cards except the two PCI TV tuners.

Reading scary things about the GeForce 8100 series cards with drivers not working/flaking playback even with Firefox and YouTube.

---

### Post by Caps18 on 2009-09-21
How does video play with Xine?  Mplayer?  

As for Firefox/YouTube/Flash videos, my web connection sucks, but when I download them to my hard drive they are fine.

I have a GeForce 5200 and it is fine playing back video, but it or my slower CPU doesn't like the on screen overlay display.  It works well with Linux though I'm not sure what the current status of Linux ATI drivers are.

---

### Post by khelben1979 on 2009-09-21
[AMD ATi Radeon]("http://www.phoronix.com/forums/forumdisplay.php?f=19") and [nVidia]("http://www.phoronix.com/forums/forumdisplay.php?f=20") over at Phoronix forums will give you some information.

I believe nVidia will give you less hassle, although AMD ATi is an attractive choice as well.

Make sure to get one with a great cooler since many of these cards gets really hot.

---

### Post by TyTiger on 2009-09-21
Hey i've successfully set up a Mythbuntu box using a nVidia card, No castle at all, works perfect with the restricted driver installed. composite output works perfect and the nVidia display manager allows you to set 'Overscreen' which basically stretches the picture in case it doesn't fill all the space on your TV (if your using composite/s-video that is)

(Mythbuntu version 8.04)

---

### Post by bsntech on 2009-09-21
I am also leaning more towards the nVidia way - just because I found a cheaper mobo for $50 that has this and the SPDIF.  But, it is the GeForce 8100 series and I've heard that there seems to be some issues with antyhing in the 8xxx and 9xxx range of GeForce cards.

I've also been reading about this VDPAU stuff - I wonder/hope that this will be something built-into either the nVidia drivers or the kernel within the year since it apparently lowers the amount of CPU usage when playing back video.

That and hopefully it will all be included in the media players like mplayer.  I use the internal player for TV recordings and DVDs in MythTV, but I use mplayer for the Videos from MythVideo.

---

### Post by williammanda on 2009-09-21
One thing to consider is the VDPAU capability. The only on board video that would work would be the Nvidia ion which has the 9300 / 9400. Also Nvidia video cards are hands down better in linux. I currently use a 9600 GT with VDPAU and it works great.

---

### Post by klc5555 on 2009-09-21
> **bsntech said:**
> Hello all,

I am looking to piece together a new MythTV Ubuntu system.

I was curious to know what each of your preferences are for a video card - nVidia or ATI - and what kind of card you have and any troubles you encountered.

The motherboards I'm looking at must have coaxial SPDIF out for connecting to the receiver for digital sound.

I've run across the GeForce 8100 series video cards on several motherboards or the Radeon 4200 series video cards on motherboards.

Me being a little cheap, I am looking to use the built-in video/audio on the motherboard and not have any add-in cards except the two PCI TV tuners.

Reading scary things about the GeForce 8100 series cards with drivers not working/flaking playback even with Firefox and YouTube.

You'll note from the "known issues" section of the Mythbuntu release notes for 9.04 that Mythfrontend (on *buntu 9.04) won't currently run on ATI Radeon graphics. Now if you already happened to have an ATI Radeon in hand, there's a workaround which sometimes works and sometimes doesn't, but since you're building from scratch, why voluntarily subject yourself to potentially significant hassles? Go with a good, mainstream NVidia GeForce card of some sort, or a board which imbeds NVidia graphics. Preferably something from the myth wiki's NVidia feature matrix here: [http://www.mythtv.org/wiki/NVidia_Cards](http://www.mythtv.org/wiki/NVidia_Cards) The driver support by NVidia remains much better.

---

### Post by bsntech on 2009-09-21
Good to know - so I'm staying away from ATI and going with the nVidia then.  Just hope I don't need to get another card because the board I'm looking at only has two PCI slots and a PCI-E slot that is blocked by the heatsink over the chipset - so there won't be room to put another card in.

---

### Post by bsntech on 2009-09-21
Ouch - no mention of the GeForce 8100 on that website.  I'm not for certain, but I don't think the VDPAU would be required and a quad-core processor with built-in graphics should be meaty enough for HD and Compiz right?

---

### Post by novellahub on 2009-09-22
> **bsntech said:**
> Ouch - no mention of the GeForce 8100 on that website.  I'm not for certain, but I don't think the VDPAU would be required and a quad-core processor with built-in graphics should be meaty enough for HD and Compiz right?

Yes. Even a Dual core Athlon 64 would be sufficent (3800x2). I have have that in my Master Backend / Frontend machine.  I have a Frontend only AMD Phenom Quad Core machine that handles any playback profile with ease.

---

### Post by bsntech on 2009-09-22
Got it.

I setup a front end last night and put a MX4000 64 MB card in it that has composite and S-VIDEO out - and it works very well.

Took several hours last night from start to finish to set the box up - including the lirc remote that works with MythTV and Boxee.

It would be nice if there was a fairly inexpensive motherboard that had both SPDIF and composite out on it.  Either way, I'll have to get another video card in the motherboard I'm looking at with the GeForce 8100 series graphics - since I need the composite or SVIDEO out.  Otherwise, I'd have to buy a brand new TV as well with a VGA input (some point in the future).

---

### Post by klc5555 on 2009-09-22
> **bsntech said:**
> Got it.

I setup a front end last night and put a MX4000 64 MB card in it that has composite and S-VIDEO out - and it works very well.

Took several hours last night from start to finish to set the box up - including the lirc remote that works with MythTV and Boxee.

It would be nice if there was a fairly inexpensive motherboard that had both SPDIF and composite out on it.  Either way, I'll have to get another video card in the motherboard I'm looking at with the GeForce 8100 series graphics - since I need the composite or SVIDEO out.  Otherwise, I'd have to buy a brand new TV as well with a VGA input (some point in the future).

LCD monitors (widescreen or otherwise) also work very well with Myth. As well in most respects as an LCD TV, including HD content.

---

