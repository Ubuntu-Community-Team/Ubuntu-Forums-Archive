---
title: "Converting Audio CDs to format for iPod Nano"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2006-12-20
I'm not a big iPod person, but my daughter wanted one and so my wife bought one for her. She will receive it on Christmas. Since I expected that my daughter will want to use a computer to download songs on to it, and since I only permit Ubuntu in my household, I tried to set the thing up.

After trying every known iPod app on Ubuntu, spending hours surfing Google, looking also in apt (with Universe option on briefly), I found that the thing that worked best for me and most reliably was **gtkpod**.

So the next thing I'll need to learn how to do is download and install some kind of GUI application on Ubuntu that reads an audio CD and converts it into a format of files that can be transferred to the iPod, whether that's Ogg, MP3, or whatever. 

On Ubuntu, what are the top 2 recommended GUI apps for transferring audio CD data to iPod?

---

### Post by SuperMike on 2006-12-20
Also, a couple other things I need to figure out are:

* How to download video from websites and put it on it. She likes YouTube a lot.

* How to install an image that is displayed with the song when it is playing.

* When I plugged it in for the first time, I let it charge up for 4 hours. It said, "Do not disconnect" and refused to stop saying that. After 4 hours passed, it still said "Do not disconnect". I had already transferred some songs with gtkpod to it and so I disconnected. The songs played just fine. I then reconnected and it still said "Do not disconnect". What gives?

---

### Post by SuperMike on 2006-12-20
Is this the right forum for this question? I hope I can answer these questions before Wednesday Dec 27th when we return home with this iPod after spending time with our relatives.

---

### Post by lister171254 on 2006-12-20
Try this link

[http://www.ubuntuforums.org/showthread.php?t=316011&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=316011&highlight=ipod)

also searching the forum for anything related to iPod might help.

Leo

---

### Post by kevinatkins on 2006-12-20
Hi,

You should be able to transfer mp3's to the iPod. I've just checked Soundjuicer, and couldn't see an option for encoding to mp3, but Grip definitely does, and I've used that in the past. You'll need to make sure you've got the correct mp3 libraries installed, too.

---

### Post by SuperMike on 2006-12-26
> **kevinatkins said:**
> You should be able to transfer mp3's to the iPod. I've just checked Soundjuicer, and couldn't see an option for encoding to mp3, but Grip definitely does, and I've used that in the past. You'll need to make sure you've got the correct mp3 libraries installed, too.

These are some notes for what I learned...

I also have to make a correction. It wasn't an iPod nano. It was the new iPod 30GB unit. My wife purchased it for our daughter.

I installed Grip from apt-get and it didn't work by default because the config tab settings for encoding were set to mp3encode instead of lame. I noticed I had /usr/bin/lame but not /usr/bin/mp3encode, and couldn't find mp3encode from apt-get with the Universe option. So, I switched the config settings to lame in Grip and it worked. I then found that you stick a CD in, choose Cancel when GNOME wants to do something with it (but do NOT check Always Do This), and then open Grip. It reads the audio CD. You check off songs you want to convert to MP3. You then click the Rip tab and click the Rip + Encode button. It does 2 passes for each song -- one to create a WAV and/or OGG file, and one to convert that to MP3. It then sticks these in the home directory under "mp3". So, if I am "/home/mike", then it was "/home/mike/mp3". In there, you see an MPU file, which you can ignore. Then, you see an album folder, which you can open. The MP3 files are inside there.

Now, to get these onto the iPod, I used gtkpod, which I got from apt-get. I opened it and it complained about not being in sync -- just click OK and ignore that, I guess. I then see two "tabs" on the left and I chose the one that did not say "Computer". I chose the iPod one. Once I did that, I could see stuff already on the thing. I could then click Add File on the toolbar and select my MP3 file. It added it. I could then click on the list on each cell in the grid and change the titles for song, album, artist, and genre. I think I had to click and hold my cursor over the grid cell a second before it enabled me to edit this. Okay, when done, I clicked some button on the right on the toolbar which essentially meant to push these songs to the iPod. I found on the first try that this doesn't actually write the files to the iPod properly unless you click Update DB from the File Menu. Why? I don't know, but oh well.

Now the iPod, all along, says, "Do Not Disconnect" for some reason. I found no real reason for this and assumed that on Windows or the Mac the iTunes application automatically disconnects the thing, and we don't have that feature in gtkpod. Therefore, I just disconnected it cold. Of course, when I did that, my event log (/var/log/messages and/or dmesg command) started flooding with errors about no connected iPod, but oh well. I found on a reboot at a later time that the errors went away. I really wish there was a more graceful way to disconnect the iPod.

With the disconnected iPod, I found the thing worked great.

Other notes:

* My daughter previously used iTunes to install some songs on the iPod, but not all of these were recognized properly in gtkpod and they were erased from the iPod FOREVER! However, any new songs she added from gtkpod appeared properly and were never lost. I don't understand that one, but oh well.

* Other MP3 players are more easy-going. You just treat them like a mounted USB memory stick or CDR, drag MP3s or WAVs to them, and these recognize and play them automatically. (Some even allow OGG files, I thought I heard.) But not so with the Apple iPod. Personally I can't see why anyone would want one because of the proprietary database on them, but my daughter is a bit stuck on the name brand and my wife gave into her pleading.

* I installed tor/privoxy after I googled on the keyword "tor" and click the first link at the EFF. I then went to PirateBay and tried to download a Foreigner album. That looked a bit ridiculous because not only was tor extremely slow, but the torrent file was massive and not going to be downloaded anytime soon over my DSL connection. Also, the PirateBay site thought I was German (because of onion routing with tor) and I had to switch the language preference. So, anyway, I saw this method of getting MP3s as impractical. This is a good thing, actually, because I'd rather do things the legitimate way when I can.

* We had one problem where gtkpod would open up, throw the "cannot sync" error, and just freeze. I did CTRL+ALT+BACKSPACE, then pulled out the USB cable and replugged it again, logged in again, and all was well again.

* In general the applications were clumsy and I realized I don't really like the iPod. I'd recommend you get some other vendor's product that you simply drag MP3, WAV, or OGG files to and it just plays them.


Anyone have any preferred, Linux-friendly portable music player program, and which plays OGG files? Let me know how the experience was.

The SoundJuicer program, I also noticed, works on some kinds of CDs automatically and permits me to encode songs as WAV or OGG format. However, WAV is too huge on the iPod and OGG doesn't play on the iPod. Therefore, getting another Linux-friendly portable music player program seems to be the best solution.

---

### Post by kevinatkins on 2006-12-27
You can play back certain Apple AAC / M4A music files with XMMS, with the appropriate plugin. I think the same goes for amaroK, but I'm not sure about Rhythmbox. However, music purchased from the iTunes store almost certainly won't play on any Linux player, because it's DRM encrypted. It is possible to install Apple iTunes and run it under Wine / Crossover Office on Linux, incidentally.

---

### Post by Zimmer on 2006-12-27
> **SuperMike said:**
> These are some notes for what I learned...

...
The SoundJuicer program, I also noticed, works on some kinds of CDs automatically and permits me to encode songs as WAV or OGG format. However, WAV is too huge on the iPod and OGG doesn't play on the iPod. Therefore, getting another Linux-friendly portable music player program seems to be the best solution.

Read the Help file in Soundjuicer, the 'Preferences' section , which gives full instructions on how to encode MP3 with Soundjuicer. (You will need the Lame encoder for this).

EDIT: Have you read this info, BTW? Might be useful...
[http://doc.gwos.org/index.php/IPod](http://doc.gwos.org/index.php/IPod)

---

### Post by SuperMike on 2006-12-28
Another thing I had to do...

Some iPods are picky and you're better off with a fresh iTunes database on the thing, if you don't mind losing any existing songs and having to start all over again. You have to rename the iTunes directory to iTunes.OLD on them, then open gtkpod, choose Create iPod's Directories from the File menu, then Synchronize iTunes DB from the File menu, then Quit, then rightclick the icon for the iPod on the desktop, choose Unmount, wait until you get the error on the desktop screen, ignore the error, then unplug the iPod (even if it says "do not disconnect"). That creates a new, empty iTunes database, ready to go.

Now you can upload new songs by plugging it in again, opening gtkpod, click Add Files, select about 5 songs at a time, click the Sync toolbar button, click File menu's Synchronize iTunes DB, then quit, then rightclick desktop icon and choose Unmount Volume, then wait until you see the error message, ignore the error, then unplug iPod, and voila -- songs are on it.

To delete songs, I did the same thing as above but instead of clicking Add Files, I rightclicked a song, chose Remove from iPod, clicked Sync toolbar button, chose Synchronize iTunes DB, then quit, then continue with the last paragraph's steps for the desktop icon and so on.

---

### Post by Mike'sHardLinux on 2006-12-28
Does her iPod show the album covers? I tried to get this to work some time ago and gave up. I can transfer songs, but the iPod doesn't show the album covers any more. (I have them embedded in the mp3s.)

---

### Post by SuperMike on 2006-12-28
I haven't tried this, but I think I read on a website that if you use the CVS technique to install gtkpod, it comes with a feature to install the album covers. I think this was documented on the Ubuntu Document Storage Facility?

---

### Post by 3rdalbum on 2006-12-29
The reason why the iPod says "Do not disconnect" is because otherwise, the typical Windows users would drag their songs to the iPod and then just unplug it, without unmounting first (or without waiting for the songs to transfer :-) . If the iPod has been unmounted, or was not mounted in the first place, then it's perfectly safe to disconnect it.

---

### Post by SuperMike on 2006-12-29
> **3rdalbum said:**
> The reason why the iPod says "Do not disconnect" is because otherwise, the typical Windows users would drag their songs to the iPod and then just unplug it, without unmounting first (or without waiting for the songs to transfer :-) . If the iPod has been unmounted, or was not mounted in the first place, then it's perfectly safe to disconnect it.

Thanks for the tip. Little by little, we're getting somewhere here.

---

### Post by psych-major on 2007-01-07
> **SuperMike said:**
> Anyone have any preferred, Linux-friendly portable music player program, and which plays OGG files? Let me know how the experience was.
Yes, the iPod Nano. It works like a champ in Rhythmbox and I also use GPixPod to transfer photos to it.

---

