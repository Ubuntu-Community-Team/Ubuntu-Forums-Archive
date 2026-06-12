---
title: "DVDs and Frustration!"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by funkycaper on 2008-01-03
Alright... so I've been trying EVERYTHING I could find in the forums about getting encrypted (commercial) DVDs to play on my Acer Aspire 5100 (running Gusty).  I installed libdvdcss2, w32codecs, etc. and Totem still says the following:

"The source seems encrypted, and canot be read. Are you trying to play an encrypted DVD without libdvdcss?"

Wow... I just noticed the poor spelling in that error... hmmm... moving on...
I've tried reinstalling all this stuff time and time again but I still can't play DVDs.  I also tried VLC but that doesn't work either.

Any further suggestions/recommendations for getting this to work?

---

### Post by Dive4Life on 2008-01-03
I have noticed a similar problem with newer dvd's.  I do believe that there is a new encryption out.  I am unable to either watch or burn the newer dvd's as well.  It should just take a while until someone posts an update.

---

### Post by crazyfish666 on 2008-01-03
> **Dive4Life said:**
> I have noticed a similar problem with newer dvd's.  I do believe that there is a new encryption out.  I am unable to either watch or burn the newer dvd's as well.  It should just take a while until someone posts an update.

I can't seem to play any dvds, old or new.

---

### Post by funkycaper on 2008-01-03
Oh, here's an update!  VLC will now play the menu for the DVD with both video and sound, but when I click to play the movie, I hear the audio for the DVD but the video doesn't play.  I might have changed something somehow, but I really have no idea how I did it.

---

### Post by funkycaper on 2008-01-03
Oh, and my "home-made" DVDs work fine in VLC now as well.  Before they weren't working, but now they seem to be fine, but only in VLC.  These home-made DVDs are of course unencrypted.

---

### Post by theacoustician on 2008-01-03
> **funkycaper said:**
> Alright... so I've been trying EVERYTHING I could find in the forums about getting encrypted (commercial) DVDs to play on my Acer Aspire 5100 (running Gusty).  I installed libdvdcss2, w32codecs, etc. and Totem still says the following:

"The source seems encrypted, and canot be read. Are you trying to play an encrypted DVD without libdvdcss?"

Wow... I just noticed the poor spelling in that error... hmmm... moving on...
I've tried reinstalling all this stuff time and time again but I still can't play DVDs.  I also tried VLC but that doesn't work either.

Any further suggestions/recommendations for getting this to work?How did you install the codecs, per chance?

Also, have you tried using MPlayer?

---

### Post by Yellow Pasque on 2008-01-03
Here:
[http://ubuntuforums.org/showpost.php?p=4068411&postcount=2](http://ubuntuforums.org/showpost.php?p=4068411&postcount=2)

---

### Post by theacoustician on 2008-01-03
> **Temüjin said:**
> Here:
[http://ubuntuforums.org/showpost.php?p=4068411&postcount=2](http://ubuntuforums.org/showpost.php?p=4068411&postcount=2)

Hmm, yeah, I would think that would be the right way too.  Hmm.  Even though you shouldn't have to do it this way, try> sudo apt-get install liba52-0.7.4 libdvdcss2 libdvdnav4 libdvdread3 and see if that makes a difference.

---

### Post by funkycaper on 2008-01-03
> **theacoustician said:**
> How did you install the codecs, per chance?

Also, have you tried using MPlayer?

here's what I typed in terminal:
sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs

I made sure I added the proper repositories as well.
As for mplayer, I am sad to say that only gives me errors when I try to play any of my DVDs - encrypted or unencrypted.  Back in my mac os x days, it never failed me haha

---

### Post by funkycaper on 2008-01-03
> **Dive4Life said:**
> I have noticed a similar problem with newer dvd's.  I do believe that there is a new encryption out.  I am unable to either watch or burn the newer dvd's as well.  It should just take a while until someone posts an update.

actually, now that I am trying my older DVDs (commercial, not home-burned) with VLC, they are working fine.  I guess it really is a new encryption that is causing the problem.  Guess that means no Batman (1989) for me haha

not that big a deal... I can patiently continue to dual-boot until the needed update arrives.  windows vista seems to be OK with it

---

### Post by fearevilleet on 2008-01-04
I was just about to make a new post about this issue. I just rented resident evil put it in, no go. Below is the output from vlc. 


```
evil@box:~$ vlc
VLC media player 0.8.6c Janus

(.:15962): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(.:15962): Gtk-WARNING **: Error loading theme icon 'gtk-harddisk' for stock: Failed to open file '/home/evil/.icons/LeopardX-Beta2/scalable/devices/gtk-harddisk.png': No such file or directory

(.:15962): Gtk-WARNING **: Error loading theme icon 'gtk-execute' for stock: Failed to open file '/home/evil/.icons/LeopardX-Beta2/scalable/apps/22/gtk-execute.png': No such file or directory
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/evil/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
evil@box:~$ 

```

The messed up thing is im just downloading a dvd rip, but it would be nice to have my legal  dvds work as well. I have the restricted drivers installed.  I tried to rip it also. Any ideas?

On a side note: I thought they could not come up with a new encryption scheme on dvds since all dvds would not be able to play them.

---

### Post by RawMustard on 2008-01-04
It's not really new encryption as such as I understand it.  They purposely put bad blocks/sections on the dvd so computer dvds can't read them, they then do some magic stuff with the ifo files to tell the players to skip these bad sections.  Normal dvd players have no problems with the new discs, but computer dvds do.  I've had problems playing some of the new dvds under windows also, but they work fine in my standalone dvd player. 

The only option at the moment is to rip them with a windows program called DVD fAb which is constantly updated to handle these new anti piracy methods.  But even then some discs like Deja Vu can be a real pain in the *** :(

Anyway, that's kinda how I understand it, there may be a more technical explanation, but that's pretty much the crucks of it all

---

### Post by kiisu on 2008-01-04
My 2 cents:

I started on Kubuntu, had trouble with both Totem and MPlayer.
VlC worked for me, later I had to add the Medibuntu repositories for libdvd and W32.

Now, under Ubuntu, VlC didnt work at all, even with those codecs.

So I gave MPlayer a shot and it worked.

All I've tested it with so far is my commercial copy of Fargo, nothing really new so I can't comment on that. But it works beautifully, so, I am happy for now.

---

### Post by fearevilleet on 2008-01-04
I tried 2 different media players, vlc &  mplayer. I also tried to rip the dvd using acid rip, the dvd rips to a corrupt file. Ohh well xvid rip is done, screw drm.

---

### Post by lisati on 2008-01-04
> **fearevilleet said:**
> I tried 2 different media players, vlc &  mplayer. I also tried to rip the dvd using acid rip, the dvd rips to a corrupt file. Ohh well xvid rip is done, screw drm.

To play DVDs on my machine I installed the recommended libraries @ [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) using "aptitude" instead of "apt-get", and then installed the CSS library with the command shown on the page. Apart from a moan about the libdvdcss2 library not being available (it was downloaded with the CSS installation command)  it was a smooth install.......

No probs.....

---

### Post by caqui on 2008-01-12
tried everything and nothing too....only the older dvds. new ones and not too new didn't work.

follows my vlc output, wich is just a bit different from the above...

caqui@aquitemcaqui:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: THE_RECRUIT
libdvdnav: DVD Serial Number: 2ec3a175
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/caqui/.dvdnav/THE_RECRUIT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007c9
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000007c9)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0002f97b
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003128d5
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003128d5)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00330b54
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x00330b54)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 3
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Afirmação `0' falhou.
Cancelado (core dumped)

---

### Post by csoler on 2008-01-13
Ok, and why not simply rip the dvd content with dd with the no-error option, and then writing it to a clean dvd ? This could do ok.

---

### Post by battlesound on 2008-01-18
> **RawMustard said:**
> It's not really new encryption as such as I understand it.  They purposely put bad blocks/sections on the dvd so computer dvds can't read them, they then do some magic stuff with the ifo files to tell the players to skip these bad sections.  Normal dvd players have no problems with the new discs, but computer dvds do.  I've had problems playing some of the new dvds under windows also, but they work fine in my standalone dvd player. 

The only option at the moment is to rip them with a windows program called DVD fAb which is constantly updated to handle these new anti piracy methods.  But even then some discs like Deja Vu can be a real pain in the *** :(

Anyway, that's kinda how I understand it, there may be a more technical explanation, but that's pretty much the crucks of it all

I noticed a little hitch with playing a newer dvd, res. evil extinction.  I couldn't play it with gxine, but it worked with kaffeine.  Later, the dvd did auto play (the gxine setup shown in the community documents).  It's pretty weird, but I do agree that the bad blocks added in are there to mess up the computer from reading it.  AND, it must be all the newer DVDs that have that copy protected symbol on the back of the box.

---

### Post by Riverside on 2008-01-18
There is something very odd about DVD replay and Gutsy.  I have been running various Ubuntu versions for quite a while now, and have never had any difficulty enabling encrypted commercial DVD replay before now.

However, yesterday I installed (fresh install) Gutsy on my Dell Inspiron 6400 laptop, on which Dapper was previously installed.  All of my commercial DVDs would play on this laptop using Dapper, however only a subset of them will play using Gutsy even though (to the best of my knowledge) all required packages are installed, including libdvdcss2 (I have tried several versions).

Output from an unsuccessful play attempt using xine:

```
user@localhost:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000026ff
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB
(0x000026ff)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002704
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB
(0x00002704)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000276e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0001658e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00366187
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0036618c
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
AFD changed from -2 to -1
AFD changed from -2 to -1
```
i.e. xine is using the installed libdvdcss version 1.2.9 for DVD correctly, however it is unable to decrypt the DVD.  The same DVD plays perfectly well on my Dell Dimension 4600 desktop machine running Dapper (using the same libdvdcss version 1.2.9), and played perfectly well on the same laptop running Dapper (again using the same libdvdcss version 1.2.9).

---

### Post by AlanR8 on 2008-01-18
I always "wimp out" and install Automatix then from there install all the codecs and DVD playing stuff. Am watching/listening to a brand new DVD as I type, (Kubuntu VLC, or Totem, or Xine)

---

### Post by Talon2 on 2008-01-18
The simple fact of the matter is that playing DVD's on Ubuntu does not work well <period>.

I have followed a lot of advice on a lot of different systems and my conclusion is that frustration is all you are going to end up with in the end.

If I had to pick a needed capability that is the SORE THUMB in Ubuntu, this is it.

---

### Post by Riverside on 2008-01-18
> **Riverside said:**
> There is something very odd about DVD replay and Gutsy.  I have been running various Ubuntu versions for quite a while now, and have never had any difficulty enabling encrypted commercial DVD replay before now.

However, yesterday I installed (fresh install) Gutsy on my Dell Inspiron 6400 laptop, on which Dapper was previously installed.  All of my commercial DVDs would play on this laptop using Dapper, however only a subset of them will play using Gutsy even though (to the best of my knowledge) all required packages are installed, including libdvdcss2 (I have tried several versions).

Output from an unsuccessful play attempt using xine:

```
user@localhost:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000026ff
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB
(0x000026ff)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002704
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB
(0x00002704)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000276e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0001658e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00366187
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0036618c
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
AFD changed from -2 to -1
AFD changed from -2 to -1
```
i.e. xine is using the installed libdvdcss version 1.2.9 for DVD correctly, however it is unable to decrypt the DVD.  The same DVD plays perfectly well on my Dell Dimension 4600 desktop machine running Dapper (using the same libdvdcss version 1.2.9), and played perfectly well on the same laptop running Dapper (again using the same libdvdcss version 1.2.9).A friend of mine and I have now worked out what the issue appears to be - it's truly bizarre though.

Mine, and his, machines don't have a DVD region set.  This isn't an issue with Dapper and previous Ubuntu versions - indeed it's a benefit, as a Dapper installation with DVD playing software and libdvdcss2 on a machine with no DVD region code set can play an encrypted DVD from any region.

However, a Gutsy installation with DVD software and libdvdcss2 on a machine with no DVD region code set can play encrypted DVDs as follows:

Region 2: Yes
Regions 2+4 (most, possibly all, BBC DVDs): No

My friend has now set his machine's region code to 2 using regionset - he can now play both Region 2 & Region 2+4 DVDs.  Not an ideal workaround though, as it will (presumably) prevent him from playing Region 1 DVDs on that machine.

---

### Post by Riverside on 2008-01-18
> **Talon2 said:**
> The simple fact of the matter is that playing DVD's on Ubuntu does not work well <period>.No, this is Gutsy (and possibly Feisty, although I haven't used that version) specific.  Enabling encrypted DVD playback on Dapper and previous versions is in my experience extremely simple, and works first time every time.  Put simply, the Ubuntu developers and/or package maintainers responsible for DVD playback in Gutsy appear to have broken something.  See my other postings to this thread.

[QUOTE=Talon2]If I had to pick a needed capability that is the SORE THUMB in Ubuntu, this is it.[/QUOTE]Absolutely, yes.  Almost everyone wants to play DVDs on computers these days, particularly laptops.  If there was ever an issue likely to drive average users back to Windows or to Apple Macs, this is it.

---

### Post by mc4man on 2008-01-19
> Not an ideal workaround though, as it will (presumably) prevent him from playing Region 1 DVDs on that machine.
He'll probably be able to play some region 1's though certainly a fair number will not play / crash player. There is another less than ideal workaround for that though it may fall into a grey area to advise. In any event if I happened to have the drive in my main box set to region 2 with some region 1's that wouldn't play and had access to a region 1 drive then this is what I might do. When vlc (probably other players too) plays a disk for the first time it creates a folder in .dvdcss specific to that title. The next time you open the disc in vlc it will use that folder first to open the title, and if the files inside are kosher then away you go. So what I might do is use vlc to open the region1's with the region 1 drive, copy the folders and insert them in the .dvdcss folder in my region 2 box. Vlc will now have the proper info to play the disk.

---

### Post by BMWolfgang on 2008-02-14
> 
Absolutely, yes.  Almost everyone wants to play DVDs on computers these days, particularly laptops.  If there was ever an issue likely to drive average users back to Windows or to Apple Macs, this is it.

Hello,
now I can not hold back with my comment and frustration.
Since I used to "play" with linux for years and when win came out with the new system, I made a decision to absolutely stay with linux from now on. First came Kubuntu Dapper, an upgrade didn't work on several aux system, I went through Mandriva (too commercial) and Suse (too crowded and different from "ordinary" linux)  and came back to Kubuntu Feisty, great.
Now a new upgrade to Gutsy, everything works fine except to play the DVDs, very annoying.
Especially I want to enjoy legal US DVD during my job time and legal Europe DVD back home.

Actually, for a period of time I thought to re-install my old XP, but then - NO.
But why in the h....  doesn't this work on ubuntu.
Are there any new issues or fixes on this ??

I have the same problem as decribed by others many times before, a libdvdcss2 is installed but NO DVD playing. (Is there is difference when the playing programs actually are expecting libdvdcss versus libdvdcss2 (TWO) ?

Thank you and have fun.

Wolfgang

---

### Post by Leed on 2008-02-15
Had the same frustration with "Resident Evil Extinction", I am very disgusted with what the film industry is doing here, punishing it's own customers by selling them DVD that can't be watched, only because they purposely corrupted the disc as "copy protection measurement". 
I should have bought the film from a Chinese black market for about 2$, at least that film would have worked. 

However I do not blame Ubuntu for the two days I spent looking for a solution, all other dvds run perfectly with libbcss2 installed. I also tried playing it in a Virtualbox window and in a parallel installed Windows XP... same problems, it's the DVD drive that can't read it. Trying it on my parents office PC (Windows) I could play the DVD, but not make a backup, so that I could watch it on mine. 

I think I'll give DVD fab a  chance... but apart from that nothing worked (also tried the newest version of anyDVD)

---

### Post by BMWolfgang on 2008-02-15
Hi Leed and all,
you might like to read "my solution" in
[http://ubuntuforums.org/showthread.php?p=4337488#post4337488](http://ubuntuforums.org/showthread.php?p=4337488#post4337488)

Wolfgang

---

### Post by TheThinker on 2008-02-15
libdvdcss2 has been going through various changes over the years.I currently use a version from this directory:

[http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)

---

