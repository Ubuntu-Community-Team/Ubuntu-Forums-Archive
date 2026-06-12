---
title: "Cant play Blu Ray Dvds through Front end"
date: 2010-12-11
forum: Mythbuntu
---

### Post by intelquadcore on 2010-12-11
Title says it all ><

So after finally getting my audio working lol I wanted to test it out with some DVDs... the thing is that when I insert a Blu Ray DVD into my internal (sata) Lite-On Blu Ray player nothing happens. 

Start up the HTPC, insert the Blu Ray into the reader, scroll down to Optical Drive, then choose play DVD and nothing happens

Running Mythbuntu 10.10
Have a zotac geforce 210 which is hdcp compliant
Tried installing medibuntu from terminal: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Checked off libdcdvss from Medica Control Center
Updated mythtv to .24 from: [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)
Made sure Mythvideo was checked off 

I took a look at this page too:[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)
But I want to be able to play the Blu Ray from the Front End and not rip them, so I do not know whether that page will be of any use to me?


Any suggestions greatly appreciated, I'll continue to research the topic meanwhile

---

### Post by deanjm1963 on 2010-12-11
Do you mean a Blu-Ray disk? Currently there is no way to play Blu-Ray movies on linux without going through a heap of steps. DVD's should work fine.

---

### Post by intelquadcore on 2010-12-11
Yea I meant Blu Ray discs.
Sorry for not mentioning it ealier.

I thought mythtv .24 has blu ray playback?

[http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)

---

### Post by deanjm1963 on 2010-12-11
> **intelquadcore said:**
> [http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)

Did you read the notes? You need to rip the blu-ray disk to a hard drive - there are instructions on playing the files once ripped.

---

### Post by intelquadcore on 2010-12-11
"With TrueHD/MLP, DTS-HD MA, and E-AC-3 support in ffmpeg, Myth has  gained full out-of-the-box support of playback for these files as of  version 0.22.  As of MythTV .24, the internal player is capable of  playing Blu-ray disc structures both directly from the disc and from the  folder structure on a hard drive."

[http://www.mythtv.org/wiki/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/High_Definition_Disk_Formats)

I read that from the notes, I thought that discs meant the actual discs and the folder structure meant the ripped versions?

I guess youre right then, I tried a DVD and it works. It's too much of a hassle to rip a blu ray to watch it

---

### Post by deanjm1963 on 2010-12-11
Again - did you read the notes? 

> With TrueHD/MLP, DTS-HD MA, and E-AC-3 support in ffmpeg, Myth has gained full out-of-the-box support of playback for these files as of version 0.22. As of MythTV .24, the internal player is capable of playing Blu-ray disc structures both directly from the disc and from the folder structure on a hard drive.

The minimum requirements are:

    * MythTV .24 or later
    * A Blu-ray drive
    * A disc protected by AACS MKB version 10 or lower, and not protected by BD+
    * libAACS compiled, installed, and functional. It does not need to be present at MythTV compile time.
    * A properly configured KEYDB.cfg located at ~/.mythtv/KEYDB.cfg (see the libAACS thread above for instructions on how to properly edit the file)
    * Entries in the KEYDB.cfg file for each disc in your collection (you can retrieve the keys with aacskeys) 

Straight from the disc playback is only possible from the command line, simply because nobody has added a menu entry to launch BD playback (having multiple menu items to launch each type of disc is messy and the desire is to unify them all under a single menu item). However, if all of the above is met, you can insert a disk and launch it by pointing mythavtest at its mount point, eg: 

;-)

---

### Post by ooboontwo on 2011-05-18
I would like to resurrect this thread, because I am planning on building a Media Center PC, powered by Mythbuntu, and I want to know whether or not I should spend $100 on a Lite-On Blu-Ray drive or not.

Is there a simple way to play Bluray discs, without ripping, without getting keys, etc on Mythbuntu? Will I have all the menus, etc, or just the movie itself?

Yes, I've tried reading the documentation, but nothing seems to be in simple English.

I don't know what BD+ is... I don't even own any Bluray discs yet... because I don't have a player... so... how do I know if the discs I want to buy are protected or not... oh and one last thing...

REALLY, DRM? Why make it so difficult for me to simply plop a blu-ray disc that I bought into a player that I bought, and watch the stinkin' thing on a TV that I bought? [/rant]

I don't blame Ubuntu for any of this. It is just very frustrating. I hate to sell out and use Windows, but if it works... it works. :(

I'm not afraid of the terminal, but I'd rather do stuff in the GUI on a Media Center PC.

Thoughts?

Cheers,
Cody

---

### Post by LowSky on 2011-05-18
> **ooboontwo said:**
> I would like to resurrect this thread, because I am planning on building a Media Center PC, powered by Mythbuntu, and I want to know whether or not I should spend $100 on a Lite-On Blu-Ray drive or not.

Is there a simple way to play Bluray discs, without ripping, without getting keys, etc on Mythbuntu? Will I have all the menus, etc, or just the movie itself?

Yes, I've tried reading the documentation, but nothing seems to be in simple English.

I don't know what BD+ is... I don't even own any Bluray discs yet... because I don't have a player... so... how do I know if the discs I want to buy are protected or not... oh and one last thing...

REALLY, DRM? Why make it so difficult for me to simply plop a blu-ray disc that I bought into a player that I bought, and watch the stinkin' thing on a TV that I bought? [/rant]

I don't blame Ubuntu for any of this. It is just very frustrating. I hate to sell out and use Windows, but if it works... it works. :(

I'm not afraid of the terminal, but I'd rather do stuff in the GUI on a Media Center PC.

Thoughts?

Cheers,
Cody

No.

Blu-Ray's "amazing" DRM is a release key system. Every once in a while a new bunch of keys come out and a blu-ray player need to download them, if it doesn't new disks might not be playable. Its why all the stand alone players have wifi and ethernet connections.

My suggestion.. skip Blu-ray. I own a PS3 and a BR drive in my PC, and both get little use of the blu-ray. I own only two blu0ray movies and the quality is good but unless you are a snob for high def, I really have to say skip blu-ray. DVD is good enough in every case.

Just so you know Windows 7 can't play Blu-ray directly either. You will need software for it to run as well.
[quote=http://windows.microsoft.com/en-US/windows7/MPEG-and-DVD-video-frequently-asked-questions]	Can I play a Blu&#8209;ray Disc?

To play a Blu&#8209;ray Disc, you need to use a non-Microsoft program that supports Blu&#8209;ray playback and a device capable of reading Blu&#8209;ray Discs.
[/quote]


If you wanna watch hi def movies i suggest on demand providors. Amazon's video rental system works great from Firefox (in HD). 

Don't forget BR cost more than DVD and do the math on how many times you may ever watch your "favorite" movie. If a brand new movie cost $20... on demand is usually under $5, so you get 4 watches  for the price of the physical media. That's How I've started living. No need to hoard a DVD if I might only watch it 2-3 times.

---

