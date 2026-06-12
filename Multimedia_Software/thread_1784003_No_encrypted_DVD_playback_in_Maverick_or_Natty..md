---
title: "No encrypted DVD playback in Maverick or Natty."
date: 2011-06-16
forum: Multimedia Software
---

### Post by TimC340 on 2011-06-16
First, let me say that this is on three separate laptops; an HP Pavilion 4120se, a Sony Vaio VGN-S5XP and a Dell Studio XPS1340. All are showing the same symptoms, though the first two are running 10.10 and the last is dual-boot Win7Pro and Natty 64-bit. All are UK models with a Region 2 restriction. The dual boot machine will run all legal movie DVDs perfectly under Windows 7 Professional. All three installations will run educational and similar DVDs. On all 3, Medibuntu repo is enabled, Ubuntu Restricted Extras are installed, as is libdvdcss2 and libdvdread4 (if those 2 can co-exist!). I'm using Movie Player and VLC.

I have tried UK retail commercial Region 2 movie DVDs, foreign region-free movie DVDs, Chinese pirate movie DVDs. None work. However, Licklibrary guitar instructional DVDs work fine - so the drives are OK! I've tried the oldest movie DVDs I have, and the same result. MP in Maverick tells me, "Could not read from resource" (VLC just does nothing!), and in Natty it says, "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed".

I have read as much as I can of the sticky above, and searched through every 'can't play DVDs' thread - hence the installation of all the above-mentioned software, codecs and libraries, all to no avail. Is it simply that the lack of commercial kick-backs from open-source software means Linux users will not be allowed to view movie content, or is there something fundamental I'm missing? I would be grateful for any suggestions, as this is a game-stopper for me wrt Ubuntu!

---

### Post by BicyclerBoy on 2011-06-17
Did you run the install script as well, (not sure this is necessary) ?
Did you see the ubuntu webpage on the subject ?

I have found VLC on natty to work very well with DVDs.
The very difficult ones get HandBrake set loose on them.

With DVD navigation problems, the fix can be the latest version of programs build with the latest libdvdnav lib.
But your problem seems to suggest the libdvdcss lib is not installed correctly. 

I would check that the medibuntu repos is visible in synaptic manager & re-install libdvdcss2

---

### Post by TimC340 on 2011-06-17
I guess it may be that I've cocked something up in the installation, especially as the same symptoms are presenting in all three computers! But as far as I can tell, I followed the installation procedures given in other threads (there's no way I could work out all that sudo apt-get stuff on my own!), and Medibuntu is visible in Synaptic Manager.

---

### Post by User3k on 2011-06-17
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by jmore9 on 2011-06-17
You could also try the section in the multi media how to on the forum , heres the link :

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

There is a section on dvd plyback if you scroll down the page.

---

### Post by TimC340 on 2011-06-17
Thank you, **User3k**. I thought my OP made it fairly clear that I'd 'been there, done that'. However, I have been there again, removed and reinstalled/re-enabled Medibuntu, VLC (with the appropriate extras) and libdvdcss2. No change. The disc is recognised but will not play - not even menus. For the diagnosis process, I'm using a Disney/Pixar disc of Bugs Life - double sided, with widescreen one side and 4:3 the other, and old enough not to include any new types of encryption that might be beyond open-source software.

---

### Post by TimC340 on 2011-06-17
> **jmore9 said:**
> You could also try the section in the multi media how to on the forum , heres the link :

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

There is a section on dvd plyback if you scroll down the page.

You, sir, are a star! Installing regionset on the Sony Vaio revealed that, somehow, the Ubuntu installation had reset the DVD drive to Region 1 (USA). I, of course, was trying to play a Region 2 (UK/Europe) disc. Having used the program to set the drive back to Region 2 (as it had been under Windows) resolved the problem - at least on this computer - and all is now well.

Now to discover whether on the dual-boot machine, it's on Region 2 under Win7 but Region 1 under Ubuntu!

---

### Post by TimC340 on 2011-06-17
OK. The Sony Vaio is running fine. The dual-boot 64-bit Win7/Natty machine will now play commercial DVDs on VLC. But there is no sound, and the video has a blue tint. It plays fine through Windows. Other, streamed, video plays perfectly. 

The old HP Pavilion is suffering the black screen of death with flashing Caps Lock tell-tale, and it's getting to that point long before I have a chance to change anything or see whether I've fixed the DVD problem! It seems to be an ATI driver issue, as far as I can tell, but I don't have the knowledge to diagnose further.

Edit: a reboot has sorted the sound issue, but not the blue-tinted playback!

---

