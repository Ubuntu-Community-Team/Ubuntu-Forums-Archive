---
title: "No sound on Shuttle SD11G5"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by QuantumCaffeine on 2006-01-20
Hi all,

Having splashed out on a Shuttle SD11G5 barebones, got everything together and installed Ubuntu on it, I can't get the sound to work! (Everything else is fine though, and it's a beautifully quiet machine, after the banshee I had before.)

The install detected the onboard sound (SoundBlaster Live! 24bit 7.1) as an Audigy LS, and gave me the ca0106 driver. Everything seems fine (mp3s will play, etc.) apart from the fact that no sound comes out. (Yes, I've unmuted the volume.) I can't even get any system sounds.

Googling around, I found a post on a Gentoo forum ([http://forums.gentoo.org/viewtopic-t-417290-highlight-analog.html](http://forums.gentoo.org/viewtopic-t-417290-highlight-analog.html)) which seemed to indicate that I need a patched version of alsa. That's a bit beyond my level of expertise, but I have upgraded alsa to 1.0.11rc2 by following the instructions on the alsa website ([http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106))
to no avail.

Any ideas?

Cheers, and thanks in advance,

Peter

---

### Post by ngms27 on 2006-01-20
Have you tried this guide?

[http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)

Just make sure you use the right kernel and driver in this line:
 
./configure --with-oss=yes --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-2.6.12-10-386/

For example my older Shuttle uses intel8x0 as the card and I use the 2.6.12-10-K7 kernel

i.e. ./configure --with-oss=yes --with-cards=intel8x0 --with-kernel=/usr/src/linux-headers-2.6.12-10-K7/

HTH

JonnyT

---

### Post by QuantumCaffeine on 2006-01-21
[QUOTE=ngms27]Have you tried this guide?

[http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy](http://system76.com/knowledge/index.php/ALSA_1.0.10_Setup_on_Ubuntu_Breezy)

[snip]

HTH

JonnyT[/QUOTE]

Thanks for the info, but the guide says much the same thing as the page on the ALSA website that I used. Just in case, I tried again following the guide (but specifying the ca0106 card rather than the Intel chipset, and installing version 1.0.11rc2 rather than 1.0.10) but no joy. As before, everything seems fine apart from the fact that no sound comes out!

Does anybody know what's going on here? The manual says I have a "Creative P17 (7.1-channel)" chipset, and the ALSA website seems to say that this is supported (with the exception of sound capture) by the ca0106 driver, so I must still be doing something wrong (sigh).

Cheers,

Peter

---

### Post by K0LO on 2006-01-30
Peter:

I too have the Shuttle SD11G5, and I just wanted you to know that it **is **possible to get the sound working. Mine is working just fine, both the playback and the record side of the sound card. However, you're going to have to do some compiling from source.

I'm at work now, so when I get home later tonight, I'll let you know how I did it.

---

### Post by K0LO on 2006-01-30
Peter:

You were really close to having sound working! The problem is that the SoundBlaster Live!24 audio system in the Shuttle SD11G5 is nonstandard; it won't work with the standard CA0106 driver. There was a bug report tracking this; it's ALSA bug 1675, and the issue has now been fixed.

The ALSA version that will work with the Shuttle sound system is 1.0.11.rc3 or later. It was just released yesterday and is available on the ALSA web site. So if you have already compiled and installed 1.0.11.rc2, I think that all you'll have to do is recompile alsa-driver and your sound should work.

However, if you are using the latest Kubuntu version of alsa, which is 1.09, then there's a relatively painless way to get the playback side of your soundcard working quickly that does not require compiling all four alsa modules, only alsa-driver. This is what I did at first, then I later worked on getting the recording side (inputs) working. If you want to try the quick fix, then do the following:

1. Make sure that you have installed the packages alsa-source, libasound2, libasound2-dev, and libasound-doc using the Adept installer. These will all be version 1.09 (as of today's date).
2. Find the file ca0106_main.c  --> in my system it was located at /usr/src/modules/alsa-driver/alsa-kernel/pci/ca0106
3. Make a backup copy of the file:
cd /usr/src/modules/alsa-driver/alsa-kernel/pci/ca0106
cp ca0106_main.c ca0106_main.c.bak
4. Open the file in a text editor and scroll down to the ca0106_chip_details section. You'll see a bunch of sound card definitions. You can add the definitions for the Shuttle's sound card by adding the following lines. (Just match the format of the other sound card definitions):
	 /* Shuttle SD11G5 with onboard SB Live 24bit without AC97 */
	 { .serial = 0x30411297,
	   .name   = "Shuttle XPC SD11G5 [SD11G5]",
	   .gpio_type = 1 } ,
5. Save the file
6. Now you'll want to compile the file and install it:
sudo su
cd /usr/src/modules/alsa-driver
./configure
7. When configure completes successfully, then
make
8. When the compiler finishes successfully, then
make install
9. Restart the computer and you should now have sound playback

Let me know if you have any luck,

Mark

---

### Post by ways on 2006-02-08
[QUOTE=K0LO]Peter:

You were really close to having sound working! The problem is that the SoundBlaster Live!24 audio system in the Shuttle SD11G5 is nonstandard; it won't work with the standard CA0106 driver. There was a bug report tracking this; it's ALSA bug 1675, and the issue has now been fixed.

The ALSA version that will work with the Shuttle sound system is 1.0.11.rc3 or later. It was just released yesterday and is available on the ALSA web site. So if you have already compiled and installed 1.0.11.rc2, I think that all you'll have to do is recompile alsa-driver and your sound should work.

However, if you are using the latest Kubuntu version of alsa, which is 1.09, then there's a relatively painless way to get the playback side of your soundcard working quickly that does not require compiling all four alsa modules, only alsa-driver. This is what I did at first, then I later worked on getting the recording side (inputs) working. If you want to try the quick fix, then do the following:

1. Make sure that you have installed the packages alsa-source, libasound2, libasound2-dev, and libasound-doc using the Adept installer. These will all be version 1.09 (as of today's date).
2. Find the file ca0106_main.c  --> in my system it was located at /usr/src/modules/alsa-driver/alsa-kernel/pci/ca0106
Mark[/QUOTE]

hi

i have the same problem. my new tvbox is worthless without sound. but i only got as far as this, cause i have no modules folder in /usr/src

checked the kernel-source folder as well..

what am i missing?

---

### Post by K0LO on 2006-02-08
ways:

Make sure that you have installed the four packages listed in step 1) above. If the Adept installer does not put things in the same place as it did on my system, then do a search for the file "ca0106_main.c" as follows:

locate ca0106_main.c

If you find the file in a different location, then modify the instructions to fit the path on your system.

If you still have problems you could always go to the ALSA web site and download all four updated packages (alsa-driver, alsa-lib, alsa-utils, and alsa-oss). Make sure that you download version 1.0.11.rc3 or later. Then compile each package separately by following the instructions on ALSA here [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106").

If you use the latest packages from ALSA, your sound system should work for both playback and capture.

---

### Post by ways on 2006-02-08
[QUOTE=K0LO]ways:

Make sure that you have installed the four packages listed in step 1) above. If the Adept installer does not put things in the same place as it did on my system, then do a search for the file "ca0106_main.c" as follows:

locate ca0106_main.c

If you find the file in a different location, then modify the instructions to fit the path on your system.

If you still have problems you could always go to the ALSA web site and download all four updated packages (alsa-driver, alsa-lib, alsa-utils, and alsa-oss). Make sure that you download version 1.0.11.rc3 or later. Then compile each package separately by following the instructions on ALSA here [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106").

If you use the latest packages from ALSA, your sound system should work for both playback and capture.[/QUOTE]

i could kiss you right now :mrgreen: 
it works!

---

### Post by K0LO on 2006-02-08
Fantastic! I'm glad that it worked out for you. My machine was silent for 3 months until I figured this out, so I'm glad to share the solution with other Shuttle owners.

Isn't the SD11G5 a nice little machine? It's so quiet, and plenty fast for what I do with it. I built mine with a Seagate 7200.1 notebook hard drive that is also completely silent. I really like it.

Mark

---

### Post by ways on 2006-02-09
[QUOTE=K0LO]Fantastic! I'm glad that it worked out for you. My machine was silent for 3 months until I figured this out, so I'm glad to share the solution with other Shuttle owners.

Isn't the SD11G5 a nice little machine? It's so quiet, and plenty fast for what I do with it. I built mine with a Seagate 7200.1 notebook hard drive that is also completely silent. I really like it.

Mark[/QUOTE]

hehe. i dont think i could have gone 3 months. i was about to crack on the third day. i bought a sata disk, which did not prove to be quiet. but those problems later. i have one more before it can proudly take on the task of being my tvbox. tv-out! i need the signal to be pal-b. do you have a suggestion for that as well? i've tried using the nvidia-options (which of course doesnt work on a intel card:rolleyes: ). man i810 tells me there is no option for this.

so.. do i have to go for DRI?

btw: you should send your path to ALSA if you haven't already. other people are anoyed with this error as well..

Edit: forget it. color works =) now to watch some videos!

---

### Post by K0LO on 2006-02-09
[QUOTE=ways]hehe. i dont think i could have gone 3 months. i was about to crack on the third day. i bought a sata disk, which did not prove to be quiet. but those problems later. i have one more before it can proudly take on the task of being my tvbox. tv-out! i need the signal to be pal-b. do you have a suggestion for that as well? i've tried using the nvidia-options (which of course doesnt work on a intel card:rolleyes: ). man i810 tells me there is no option for this.

so.. do i have to go for DRI?

btw: you should send your path to ALSA if you haven't already. other people are anoyed with this error as well..[/QUOTE]

I haven't tried using the tv-out, so I'm afraid that I can't be much help. I suspect that there are a lot of people using the Intel Integrated Graphics Controller who have faced this issue, so I'd check Intel's web site and Google for information. {I've found the Gentoo forums to be a rich source of technical information too. They've almost convinced me to change distibutions! Perhaps some day, but Kubuntu works well for me now and I'm too much of a noob to attempt a Gentoo installation.}

I too am looking for help with a different issue with Intel 915 video. My machine locks up occasionally and I suspect that it's video related. My post describing this is here: [http://ubuntuforums.org/showthread.php?t=125771]("http://ubuntuforums.org/showthread.php?t=125771") I'd be interested in hearing if yours behaves similarly.

---

