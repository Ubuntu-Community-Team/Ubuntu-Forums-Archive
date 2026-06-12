---
title: "Don't understand HD content"
date: 2008-02-26
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-26
I am currently capturing HD channels via QAM on my Kworld 110.  I understand all programs are not broadcast in HD.  I have yet to view any content full screen.  Some shows have large black bars at the top and bottom, and fill the screen horizon.  Oddly the image is not distorted.  Some channels are perfect 16:9, very sharp, but centered about half the size of my screen.  My video out is via DVI on my 8x AGP, Geforce 6200, 256MB.  I am running restricted drivers.  Screen is set to highest setting of 1280x720.  I am pretty sure the card is capable of higher res.  How can I verify what is actually broadcasting?  Are there any tools for this?  Is my video card, or resolution the problem?
I have myth set to deinterlace, and "lib32" gave me the smoothest playback.  
Would the open drivers support HD?  
My display is a Syntax Olevia 26" HDTV.  I think the native resolution is 1366x768 not home now to verify.  It does support higher though.

---

### Post by volkswagner on 2008-02-27
Here is the card I am using

[http://www.newegg.com/product/product.aspx?Item=N82E16814150107]("http://www.newegg.com/product/product.aspx?Item=N82E16814150107")

The specs say it has a max resolution of  	 2048 x 1536.
I check in WinXp and the highest avail is           1280 x 720   same as Mythbuntu.
I have tried running Envy and installing propriatory drivers, but the machine black screened on live tv and vid playback with the same resolution settings.  

My Display is LT26HVX

Well checking through the manual for the tv it appears the highest resolution via VGA or DVI is 1366x 768.  :(

So it appears the only way to get 1080i is via YPbPr.  :(

No specs are given for the svideo.  Since I only have VGA, DVI and svid out from my video card, I will give svid a shot in the dark.

I still would like to know what I am actually capturing If someone can give my a clue.

---

### Post by newlinux on 2008-02-27
Sounds like resolution problems to me... I would play with different resolutions if I were you. Also, I'd skip svid, since it isn't capable of HD resolution and try the VGA and DVI at different resolutions. Also, try using nvidia-settings to change the resolution, if you aren't already.

---

### Post by newlinux on 2008-02-27
Oh, and don't forget to play with your aspect rations ("w" key).

---

### Post by majoridiot on 2008-02-28
> **volkswagner said:**
> I am currently capturing HD channels via QAM on my Kworld 110.  I understand all programs are not broadcast in HD.  I have yet to view any content full screen.  Some shows have large black bars at the top and bottom, and fill the screen horizon.  Oddly the image is not distorted.  Some channels are perfect 16:9, very sharp, but centered about half the size of my screen.  My video out is via DVI on my 8x AGP, Geforce 6200, 256MB.  I am running restricted drivers.  Screen is set to highest setting of 1280x720.  I am pretty sure the card is capable of higher res.  How can I verify what is actually broadcasting?  Are there any tools for this?  Is my video card, or resolution the problem?
I have myth set to deinterlace, and "lib32" gave me the smoothest playback.  
Would the open drivers support HD?  
My display is a Syntax Olevia 26" HDTV.  I think the native resolution is 1366x768 not home now to verify.  It does support higher though.

did you check the capture settings for the card?

you will find them in frontend setup-->playback-->recording profiles.

unless you made changes to the profiles previously, adjusting the settings for "default" is
probably all you will need to modify.

---

