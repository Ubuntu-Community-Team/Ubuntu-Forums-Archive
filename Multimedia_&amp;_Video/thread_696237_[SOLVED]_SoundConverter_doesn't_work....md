---
title: "[SOLVED] SoundConverter doesn't work...?"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by chazdraves on 2008-02-13
So, I'm giving this Linux business a bit longer mostly because I can't find my PS/2 keyboard to install XP. I just bought a new iPod, and I want to get it working, but when I enter the files into SoundConverter and click "Convert" it doesn't do anything. The bar comes up on the bottom, but it doesn't even move... This kind of seems like everything else that has happened for me in Linux, so I apologize if I sound like I'm at my wit's end.

Thanks for your time!
- Chaz

---

### Post by cozmicharlie on 2008-02-14
What is the format of the files you trying to convert and to what format are you trying to convert them too?  

Have you installed all the packages you need for multimedia such as the Ubuntu Restricted Extras?  This should help [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by chazdraves on 2008-02-14
I installed the restricted extras and the one for MP3's. I have .ogg and lossless .flac files. I'd like to convert them to Apple Lossless, but right now I don't have an option for that, so I'm just trying to convert them to MP3 at 256 kbps. No matter if I click one file or a whole stack of them, the bar comes up on the bottom as if it was trying, but it just hangs. I can leave it there for an hour and it won't do a darn thing. My only success with the iPod (which was a bugger because it's a 6th Gen) was to rip the CD's as MP3. It seems too time-consuming to rip every CD twice, however :)

- Chaz

EDIT: Now that I look, I see that SoundJuicer now has the option for AAC, but I still don't have it in SoundConverter. Which is kind of null and void anyway since Converter won't convert...

---

### Post by cozmicharlie on 2008-02-14
Soundconverter does not support Apple Lossless (m4a or aac).  You need Sound_K_onverter.  Let me walk you through it.

First lets install all the codecs you need.

Open Synaptic (you can also do this in the command line but since you are new Synaptic is the easiest method).  Install these codecs (if not already installed)

[LIST=1]
[*]First install a package from Synaptic called "Build Essential"
[*]Next install these codecs:  faac, faad, flac, lame. ffmpeg, alac-decoder, oggconvert, w32codecs, aacplusenc
[*]If you installed the restricted extras you should have the gstreamer plug-ins already installed but to be sure, check that you have  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdl
[*]If you need shn support follow the tutorial here [http://ubuntuforums.org/showthread.php?t=600781&highlight=shn](http://ubuntuforums.org/showthread.php?t=600781&highlight=shn)
[/LIST]

Next install these packages from Synaptic[INDENT]
Soundjuicer - this is for ripping cd's 
SoundKonverter (with a k) - this is for encoding /decoding
gtkpod-aac - to manage your ipod (with support for aac)
exfalso - for tagging.  This is the only tagger that supports m4a.
You can use Rythmbox as the player (should be already installed)[/INDENT]

Now you have everything you need.  Open SounKonverter and check out the "quality" and "output" boxes and you will see the codecs listed.  When you plug in your ipod gtkpod will open and you can manage the ipod.  If you really want to simplify the process, install Rockbox to your ipod.  With Rockbox you can load flac into your ipod and its just a matter of moving files into a folder.

---

### Post by chazdraves on 2008-02-14
Wow! that's one heck of a post.

Quick question. If I do all that, aren't I going to have to go through an additional bit of hassle because I have a 6th gen iPod? Won't I have to re-download all the Hardy (or whatever) versions of those programs to have support for 6th Gen (because of the checksum issue)? Also, I didn't think SoundKonverter worked in Gnome? Wouldn't shock me to be wrong.

Lastly, what is "tagging"? I don't have to manually enter all the songs/artists/albums/etc, do I?

I appreciate the help!
- Chaz

---

### Post by chazdraves on 2008-02-14
Oh... and I see now that RockBox doesn't work on 6G iPods.

- Chaz

---

### Post by cozmicharlie on 2008-02-14
> **chazdraves said:**
> Wow! that's one heck of a post.

Quick question. If I do all that, aren't I going to have to go through an additional bit of hassle because I have a 6th gen iPod? Won't I have to re-download all the Hardy (or whatever) versions of those programs to have support for 6th Gen (because of the checksum issue)? Also, I didn't think SoundKonverter worked in Gnome? Wouldn't shock me to be wrong.

Lastly, what is "tagging"? I don't have to manually enter all the songs/artists/albums/etc, do I?

I appreciate the help!
- Chaz

No you do not have to re-download.  Ubuntu has an updater that will notify you when there are upgrades to the packages.  When a new verions is released you don't re-install or have to re-downlaod everything.  

SoundKoverter is a kde package but it works fine in gnome.  Many kde packags work fine in gnome.

A tag is metadata attached to an audio file format - a label basically.  It allows information such as the title, artist, album, track number, or other information about the file to be stored in the file itself.   If you are ripping music from cd's the programs will add this info for you.  Sometimes though you may have to add it but it usually can be done once.  This is true no matter what OS you are using (Windows or Linux).

---

### Post by cozmicharlie on 2008-02-14
> **chazdraves said:**
> Oh... and I see now that RockBox doesn't work on 6G iPods.

- Chaz

Then you may not have that option.  I see from there web site that you are correct but it appears they are working on porting it so eventually it will work.  For now then you will have to convert files then add them.

---

### Post by chazdraves on 2008-02-14
What I mean is that I know I went through a tutorial last night where I had to temporarily change my source list to allow updates from the upcoming Ubuntu (Hardy Heron?) and install the Hardy versions of all my programs so that gtkpod/Amarok/RhythmBox/etc could get past the CheckSum issues with the new 6th Gen ipods. I believe if I go through installing what you listed above, I will have the Gutsy Gibbon versions again and not the Hardy Heron versions thusly meaning that I will not be able to transfer again because you need the Hardy versions to get past the checksum issue.

Also, I found a very recent post on their message board (RockBox) stating that there is no one working on RB for Classics/6th Gen and that we should never expect one (the post was from one of the admins). Something to do with the hardware being like the 2G nanos which were impregnable.

- Chaz

Update: Yeah, I was going through Synaptic to try installing gtkpod -aac and it says specifically that it would have to uninstall gtkpod (which is the Hardy version) and install libgpod2 (which is what has the issues with the checksum whereas last night I compiled libgpod3 from Hardy). Basically, it looks like if I take your above suggestions, I'll have to find that guide again to get all of the Hardy versions re-downloaded... Which may be my only option anyway.

---

### Post by chazdraves on 2008-02-14
Here's the guide I'm talking about.

[http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+classic](http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+classic)

- Chaz

---

### Post by cozmicharlie on 2008-02-14
> **chazdraves said:**
> Here's the guide I'm talking about.

[http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+classic](http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+classic)

- Chaz

OK - Isee what you mean.  Apple has not made life for open source easy.  Everyone complains about Micorsoft but Apple is worse. 

The instructions in the link relates only to managing the ipod so you should not have to install SounKonverter or Exfalso as per those instructions.  Install as you normally would using Synaptic.  Install them before you follow the instructions in that thread.  The only change you should do is since you want Apple Lossless, you need the gtkpod-aac.  So where they have gtkpod you will want to install gtkpod-aac.  You will want to install Rythmbox and you may want to try Amarok.  

Do you understand the instructions?

---

### Post by chazdraves on 2008-02-14
Okay, well, I combined your instructions with his. First, I installed all of the codecs in Synaptic, then I installed libgpod3 and all the programs (including gtkpod-aac, SoundKonverter, etc.) using the instructions from the other page to make sure I have the Hardy versions. For some reason, however, SoundKonverter doesn't wan't to give me an option for Apple Lossless... When I select m4a, the highest bitrate I can select is 320, but not lossless... Any ideas? I think that's the last issue. Well, that and the fact that although the songs now transfer just fine, the iPod doesn't read the songs I added after the Ubuntu-update. It still reads that I only have 13 songs. I guess that's not a huge deal, however, so long as they play. Actually... maybe I can just rip them in Apple Lossless and dump 'em with the new gtkpod-aac...? I'll give it a shot.

- Chaz

---

### Post by chazdraves on 2008-02-14
Yeah, ripping to AAC doesn't work either. They still come up being significantly smaller in size than their FLAC counterparts. I really have a hard time believing a 5MB song is lossless...

Well, it seems like other AAC option leaves files about that size, so I guess that's what I'm stuck with, unless you can see what I'm missing? Either way, Led Zepplin still sounds pretty good on the ole HD600's. And, if nothing else, I still have the whole library in FLAC on my computer.

- Chaz

---

### Post by cozmicharlie on 2008-02-14
> **chazdraves said:**
> Yeah, ripping to AAC doesn't work either. They still come up being significantly smaller in size than their FLAC counterparts. I really have a hard time believing a 5MB song is lossless...

Well, it seems like other AAC option leaves files about that size, so I guess that's what I'm stuck with, unless you can see what I'm missing? Either way, Led Zepplin still sounds pretty good on the ole HD600's. And, if nothing else, I still have the whole library in FLAC on my computer.

- Chaz

The Apple Lossless situation in Linux is a bit confusing.  The formats m4a and aac are called Apple Lossless but they really are not.  True Apple Lossless is ALAC.  M4a and aac are really what they call containers

"Apple Lossless data is stored within an MP4 container with the filename extension .m4a. While Apple Lossless has the same file extension as AAC, it is not a variant of AAC, but uses linear prediction similar to other lossless codecs such as FLAC and Shorten"

The m4a and aac in Linux are not really true Apple Lossless because Apple does not release the code.  It has been reverse engineered but what you have now on your computer is as good as it gets for Apple Lossless. You can play true Apple Lossless in Linux but you can't transcode (at least I have not found anything that shows you can).   I do think the m4a or aac in Linux sounds good though- much better than mp3 but not as good as flac.  

There is another option and that is to use dbPoweramp (this is a Windows program and it is not free) under wine but I would not bother.  I think the aac or m4a in Linux is good.  If I were you I would keep checking in the Rockbox web site and as soon as they port the 6g ipods, install Rockbox and load the files as flac.

Glad it is working for you.  if you feel that your problem was answered mark the post "solved".

Enjoy

---

### Post by chazdraves on 2008-02-14
Well, I think it's as resolved as it can be. I certainly appreciate you taking all the time. I guess if I really want Lossless on my iPod I'll have to re-install XP.

- Chaz

---

