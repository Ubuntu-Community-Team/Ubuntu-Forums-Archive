---
title: "How TO: Install the latest Rhythmbox with MTP"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by bsalt on 2007-06-18
Hey guys, I made a new How To blog for installing the latest version of Rhythmbox with MTP support. You'll find the blog here:

[http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html](http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html)


Thanks to ntetreau for his knowledge:
[http://ubuntuforums.org/showthread.php?t=385371&highlight=rhythmbox+mtp](http://ubuntuforums.org/showthread.php?t=385371&highlight=rhythmbox+mtp)

---

### Post by kevinlyfellow on 2007-06-19
Thanks!  I don't need MTP (almost did, but I don't) but I wanted to use the latest Rhythmbox (looks exciting!).  I'm trying it out right now.

Edit: It worked!  Thanks again.  Just to mention, your howto says you need to 
```
 sudo make
```
but actually sudo isn't required.

---

### Post by bsalt on 2007-06-21
yeah i just prefer to keep it "sudo make" to play it safe

---

### Post by scott_g on 2007-06-24
Hi,

Thanks for the tutorial, I managed to successfully install the new Rhythmbox.  However, it doesn't seem to work, when I plug in my MTP device (a SANSA E250 MP3 Player).  The output is below.

```

scott@scott-ubuntu:~$ rhythmbox
Autodetected device "SanDisk Sansa e200" (VID=0781,PID=7420) is known.
PTP: Opening session
Connected to MTP device.
flush_handles(): LIBMTP panic: Could not get object handles...
Return code: 0x02fe (look this up in ptp.h for an explanation).
Segmentation fault (core dumped)

```

Does anyone know how to fix this?  

If I try plugging the device in after rhythmbox has already started, this is displayed:

```

scott@scott-ubuntu:~$ rhythmbox
Found non-autodetected device "SanDisk Sansa e200" on USB bus...
PTP: Opening session
Connected to MTP device.
flush_handles(): LIBMTP panic: Could not get object handles...
Return code: 0x02fe (look this up in ptp.h for an explanation).
Segmentation fault (core dumped)

```

Rythmbox will work when the device is not plugged in.

Any suggestions are more than appreciated.

Thanks a lot,
Scott

---

### Post by bsalt on 2007-06-25
Scott, try this.

Plug in your Sansa, open up a terminal and type in

```
mtp-detect
```

When I type that, this is my output:

```
Autodetected device "Creative Zen Xtra (MTP mode)" (VID=041e,PID=4128) is known.
PTP: Opening session
Connected to MTP device.

```

If your error is here, then our problem is with libmtp and not Rhythmbox.

---

### Post by scott_g on 2007-06-25
When I tried that before, I would get a "Connected to MTP device", then a lot of information about the device.   However, after trying to access the device through Rhythmbox, then entering mtp-detect, it would give me an error.  However, after more searching, I tried reformatting the drive when booted in windows, and then tried plugging it in in Ubuntu again; the error disappeared; looks like there was something on the drive that was corrupted.  It likely gave me an error as it tried to access the device (using Rhythmbox), instead of just locating it (mtp-detect).

On a side note, does anyone know if the drive is mounted?  Is there anyway to view the files on the device?  The player has a few folders on it; one for music, one for playlists, one for photos, one for video etc, etc..., yet Rhythmbox puts songs in the / directory.  It would be nice to be able to move the songs to the Music folder.

Thanks a lot for your help,
Scott

---

### Post by bsalt on 2007-06-25
> **scott_g said:**
> On a side note, does anyone know if the drive is mounted?  Is there anyway to view the files on the device?  The player has a few folders on it; one for music, one for playlists, one for photos, one for video etc, etc..., yet Rhythmbox puts songs in the / directory.  It would be nice to be able to move the songs to the Music folder.

Thanks a lot for your help,
Scott

Scott, I believe that when the Sansa is in MSC mode, it should appear as a removable drive, with your folder structure and everything browseable. I found that information from this thread here:

[http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196)

I hope it helps.

---

### Post by DiaperJe|\|i3 on 2007-06-26
Just wanted to say thanks from the other thread. It works infinately better with MTP for my Iriver H20 than Amarok does right  now. However it absolutely core dumps on some albums (or any songs and said albums). For example my Muse - Hubaloo double disks. The first album transfers fine. The second core dumps Rhythmbox no mater which song or list of songs. Same with Live - Selling the Drama. Very odd. Especially since the other 40 or so albums I fransfered work fine with no crashing. 

Also, every song I transfer gets listed on my device twice. However, when I play any album it seems to show both songs played at once (two arrows on the current song being played). The net result is all albums appear to be double normal lenght but play fine. 

Thoughts?

---

### Post by scott_g on 2007-06-26
> **bsalt said:**
> Scott, I believe that when the Sansa is in MSC mode, it should appear as a removable drive, with your folder structure and everything browseable. I found that information from this thread here:

[http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196)

I hope it helps.

Very true, I can see the folders when it is mounted in MSC mode, however, I was wondering if there was a way of seeing the folders when mounted in MTP mode.  Any ideas?

Thanks again, you've been a big help,
Scott

---

### Post by bsalt on 2007-06-26
> **DiaperJe|\|i3 said:**
> Just wanted to say thanks from the other thread. It works infinately better with MTP for my Iriver H20 than Amarok does right  now. However it absolutely core dumps on some albums (or any songs and said albums). For example my Muse - Hubaloo double disks. The first album transfers fine. The second core dumps Rhythmbox no mater which song or list of songs. Same with Live - Selling the Drama. Very odd. Especially since the other 40 or so albums I fransfered work fine with no crashing. 

Also, every song I transfer gets listed on my device twice. However, when I play any album it seems to show both songs played at once (two arrows on the current song being played). The net result is all albums appear to be double normal lenght but play fine. 

Thoughts?

I do not know just why. I know that here at this mail archive, a Peter Grundstrom is the one who wrote the MTP plugin for Rhythmbox. ([http://mail.gnome.org/archives/rhythmbox-devel/2007-April/msg00064.html](http://mail.gnome.org/archives/rhythmbox-devel/2007-April/msg00064.html))

At the moment, I am no programmer - I want to learn some basic programming and be able to help with writing software, but I only know how to install stuff and get it running. You might want to email him with questions, but he appears busy at the moment with school.

---

### Post by bsalt on 2007-06-26
Scott, right now, I do not think Rhythmbox or any other application (like Amarok) has the functionality with MTP to work with pictures and videos.

EDIT: It appears the MTP in Rhythmbox only filters out audio files, as Rhythmbox is currently only an audio program.

---

### Post by Jaxilian on 2007-06-30
> **bsalt said:**
> Scott, I believe MTP is only for music purposes. Right now, I do not think Rhythmbox or any other application has the functionality with MTP to work with pictures and videos.

so true....tried this thing with Rhytmbox and it does not work.

---

### Post by scott_g on 2007-07-03
> **bsalt said:**
> Scott, I believe MTP is only for music purposes. Right now, I do not think Rhythmbox or any other application has the functionality with MTP to work with pictures and videos.

Ok,  thanks for all of your help, it is very much appreciated.  Now that I wiped the drive (and a corrupted file, I believe), it mounts in a writable mode when mounted in MSC.  So, I'll just use that from now on.  Thanks a lot for your help.

Scott G.

---

### Post by haelen on 2007-07-04
I got to the following error near the end of the install:

[I]Makefile.am: installing `./INSTALL'
configure.ac:927: required file `plugins/coherence/upnp_coherence/Makefile.in' not found[/I]

---

### Post by cewallace on 2007-07-07
i keep getting this in the terminal

(rhythmbox:21968): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed

and also this

WARNING: LIBMTP_Get_Tracklisting() is deprecated.
WARNING: please update your code to use LIBMTP_Get_Tracklisting_With_Callback()

is there a way to fix it.

I am new to all this so be gentle.

Charles

---

### Post by bsalt on 2007-07-10
> **haelen said:**
> I got to the following error near the end of the install:

[I]Makefile.am: installing `./INSTALL'
configure.ac:927: required file `plugins/coherence/upnp_coherence/Makefile.in' not found[/I]


haelen, try doing this:

1) Delete the path Rhythmbox downloaded to if you still have it there
```
sudo rm -r /path/to/rhythmbox
```

2) Go back through the step to install it. Subversion is straight from the developers, and is the latest *developer* release, as it is not the final version yet. 


I believe/hope if you try it over again, you will have more success. Tell me how it goes!


cewallace - try this as well, I'm hoping it works for ya!

---

### Post by Wokm4n on 2007-07-12
I managed to install it succesfully but afterwards, audio in Rhythmbox _only_ was messed up :(

---

### Post by dada1958 on 2007-07-22
Tnx for this how to, now my Zen V is showing up in Rhythmbox :cool:

---

### Post by GumbyX on 2007-08-26
> **cewallace said:**
> i keep getting this in the terminal

(rhythmbox:21968): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed

and also this

WARNING: LIBMTP_Get_Tracklisting() is deprecated.
WARNING: please update your code to use LIBMTP_Get_Tracklisting_With_Callback()

is there a way to fix it.

I am new to all this so be gentle.

Charles

Having the same problem for some reason. I got around it bey running rhythbox as root using gksudo. I still get the error, but it still allows for transfers. If I run it as a normal user, rhythmbox crashes about 50% through the transfer.

bsalt, I am left a post at your blog with all the info I got from my problem. Hope you can help me out. I don't like running anything from root because it just makes me uneasy. Hopefully you or someone else can help us out. Thanks for posting this how-to. It got the support working for my player. :) I am not longer attached to windows anymore (unless I need to download more songs.)

edit:
For some reasons, the file permissions were locked to root. Recopied to get them under my own and tried again. I now have problems copying certain songs. Each time I copy them, Rhythmbox crashes/"freezes". Anyone think they can help?

---

### Post by peterson2k4 on 2007-09-04
I Installed everything fine and I clicked the plugin MTP thingy.  though It doesn't let me press the configure button in the plugin area.  also I am unable to add/remove/view my mp3 player.  I have a phillips GoGear 6330

---

### Post by scru on 2007-09-04
OMG thank you. I was just wondering how i was going to start synching my mp3 player from here!

---

### Post by bsalt on 2007-09-13
I'm glad I could help! I know the lack of support for MP3 players is a major setback to people that switch to Ubuntu or other forms of Linux. Hopefully this will help get rid of that problem.

---

### Post by ArtInvent on 2008-02-03
I think it should be mentioned that in Ubuntu Gutsy, MTP just works. You have to make sure you have libmtp installed but I don't believe I installed that separately, perhaps Rhythmbox installs that automatically. 

Anyway, I got a new iRiver Clix (Clix2) 8GB and plugged it in. Rhythmbox started automatically and the Clix was sitting at the bottom of the lefthand pane. Drag an album over and the transfer starts. Very slick. At the moment it seems a little balky. I transferred one album over fairly well. Then attempted to start another transfer, seems to lock up. 

The album art seems to transfersomething over but didn't look right at all.

Anyway, some progress but not quite there yet it seems.

---

### Post by mrbryan on 2008-04-16
I know this thread is a little dead -- but wanted to know if anyone figured out a workaround for rhythmbox's behaviour of putting all music to MTP devices in the ROOT folder rather than /MUSIC  where the device can find the files.

I'm using a different MTP device that doesn't have an alternate access to MTP.

Thanks!

---

