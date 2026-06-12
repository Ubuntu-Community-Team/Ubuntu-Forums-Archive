---
title: "Intell X4500 and HDMI"
date: 2009-05-19
forum: Mythbuntu
---

### Post by TheGuru23 on 2009-05-19
Hi:

Hope everyone is doing well, and I'll now get straight to the point  :)

I just purchased and installed an Intel DG45FC mini-ITX board (uses the Intel GMA X4500 video chip) using a 2.8 C2D, 2GB RAM, 500GB hard drive.  If you're wondering if the board is any good, I think that it is, yes.  Certainly, the specs are outstanding for an HTPC that is so compact.

Anyway, connected the onboard HDMI to a Panasonic 58 Plasma - TH5800PZ and started to install Jaunty (9.04).  As soon as the GUI comes on screen, I see that the edges are cut off.  So, this makes it so I can't see the menu bar, some of the buttons on the bottom, text on the left, etc.  Screen picture is stunningly clear - just WOW!  But if the edges are cut-off, it's a huge PITA.

I've search the internet for this particular issue, and at least I'm not getting the 'Unsupported video format' issue that some others have seen.  But, clearly things are not all happy-happy.  Adjusting the TV dimensions does no good at all.

Any ideas?  Do I just have to wait for a later build of 9.04?

Thanks for any help at all.

TG23

---

### Post by Dewey_Oxberger on 2009-05-20
I don't use Intel video but I'd guess you are using a driver that doesn't work fully.

What driver are you using?  Is there a better driver you can use?

---

### Post by TheGuru23 on 2009-05-21
Hmm...
 
No special driver, actually.  I just allowed MythBuntu to use it's default driver install.
Thank You for the heads-up, . Dewey.  I'll search for a specific driver and post results.
 
TG23

---

### Post by SiHa on 2009-05-21
That'll be the overscan. Not sure how you correct it from the PC end with an Intel chipset, but you may be able to switch it off on the TV. My Panasonic (a lowly 32"!) has this option in one of the setup menus.

---

### Post by fs3rp4 on 2009-05-21
I know that CRT TVs have a natural overscan, but not plasma and LCD TVs.

This is somenthing related with resolution or frequency.

I have this problem too with my Intel 965 Chipset + HDMI + TV LCD Samsung 40".

---

### Post by TheGuru23 on 2009-06-03
Thank You siHa and fs3rp4.  

Your suggestions led to dig a little bit into the Panasonic HDMI menus, under Advanced Picture, where I found HDMI size 1 vs. size 2.  That did the trick, size2 displays my full MythBuntu desktop.

Again, thanks for pointing me in the right direction.

TG23

---

### Post by hypelightfly on 2009-08-09
I am having the same issue with the same board.  Unfortunately my TV does not support 1:1 pixel mapping so I can't fix it that way.  Does anybody know of a way to fix this on the computer side?  Its either that or not use HDMI which means SPDIF audio and no 7.1 channel LPCM :(

---

### Post by TheGuru23 on 2009-08-09
Hi there:
 
I had some recent success with this board, but with some serious Googling and updating.
 
1.  Make sure you install the latest Intel BIOS - it fixes at least one issue, that being the fan that can't seem to control itself properly...
 
2.  Update to latest ALSA - It's not available from Package Manager yet so I had to get it manually doing yum and other stuff.  Again, Google...
 
3. Used Optical Audio cable from board to receiver.  This gives me my 7.1.  Sorry, have not gotten audio over HDMI yet although everything "looks" OK
 
4. Under MythTV config, changed my screen size to 16:9, default was 4:3.  That got my videos to play properly size.
 
That's all I got for now.  Hope it helps and good luck
 
TG23

---

### Post by carlosrve on 2010-07-24
> **hypelightfly said:**
> I am having the same issue with the same board.  Unfortunately my TV does not support 1:1 pixel mapping so I can't fix it that way.  Does anybody know of a way to fix this on the computer side?  Its either that or not use HDMI which means SPDIF audio and no 7.1 channel LPCM :(

I have an Acer Aspire 4740 with Intel X4500 graphics too. My TV is a Panasonic Plasma, and it doesn't have 1:1 pixel mapping either. I have checked all the format sizes and configs it has. But nothing, I always have borders cutoff from the screen.

Also, I don't find where I can do some X11 config without having to force a xorg.conf into Lucid. I would like to follow the new way of configuring this, since xorg.conf is gone now. Any ideas?

Thank you

---

