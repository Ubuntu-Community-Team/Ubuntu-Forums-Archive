---
title: "No DVD sound.  Plays non-DRM DVD's only."
date: 2008-11-29
forum: Multimedia Software
---

### Post by chip616 on 2008-11-29
OK, followed the [Comprehensive Multimedia and Video HowTo.]("http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+mplayer")  I have some success, but no cigar.  I'm using 32-bit Kubuntu 8.04 on a Dell Vostro 1710.

MPlayer and VLC both play non-DRM commercial DVD's, but MPlayer has no sound.  Neither will play a DRM'ed DVD either sound or video.

On a non-DRM DVD, MPlayer complains:

```
Could not open/initialize audio device -> No sound
```

I have enabled the medibuntu repository and installed all the codecs as well as libdvdcss and its associated files using the following commands cut and pasted from the above linked HowTo:

```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree libk3b2-extracodecs liblame0 libtunepimp5-mp3 libxine1-ffmpeg non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
```

I also installed the mozilla mplyaer plugin, and have edited the config file (though that should have no effect on just using VLC or MPlayer alone to play commercial DVD's). 

Where do I go from here?

Thanks.

Frank.

---

### Post by mc4man on 2008-11-29
If your using gmplayer (from applications menu vs. command line) then open it up, right click in video window -> preferences -> audio and choose a driver. (probably alsa.

If from command line specify your audio  
-ao alsa

As far as commercial while it's not 100% necessary some drives, particularly on laptops, require that a region be set on the drive for access to encrypted disks.

To ck.

```
sudo apt-get install regionset
```

In the terminal with a **dvd in the drive**
```
regionset
```

See if it reports the drive as being set. (only needs to be set once, don't change if already set to your region (region 1 n.america, region 2 europe, ck. on the rest in the thread you were following.


In still no good open vlc from a terminal -> file -> open disk and post errors

Sometimes you also need to go into home folder (show hidden files) and delete everything inside of the .dvdcss folder

In 8.04 using vlc 0.8.6 it's good to change vlc's launch command

Right click on applications -> edit menus -> highlight sound and video -> right click on vlc -> properties. Change the command from vlc %U
```
vlc %f
```

---

### Post by chip616 on 2008-11-29
mc4man:

```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

```

I don't see where it is set at all.  Can you offer a further suggestion?  I am in Canada.

I tried to open the DVD with MPlayer using the context menu (open with....) and selected alsa (it was set to pulse).  Now when I try to play the DVD MPlayer complains of a 'seek error'.

MPlayer is not an issue in itself.  Xine and VLC both work on non-DRM DVD's.  That's good enough.

Opened VLC from a terminal and got the following output from a DRM'ed DVD:

```
frank@flaptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 2_BROTHERS
libdvdnav: DVD Serial Number: 31350663
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/frank/.dvdnav/2_BROTHERS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000129e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00016020
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00016020)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002cf7aa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002cf7aa)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002cf7ae
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002cf7ae)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e965d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e9661
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b4a1a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x003b4a1a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b4a1e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003b4a1e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003cea56
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x003cea56)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003cea5a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003cea5a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003ef16b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ef16f
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003ef191
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ef195
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003ef3c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x003ef3c0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003ef3c4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003ef3c4)!!
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 2
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
frank@flaptop:~$    
```

Thanks for the help.

Frank.

PS:

While waiting for a response, I used regionset to set the region to 1.  The reset worked, but vlc still fails.  I no longer get the 'error cracking css key' messages, but the rest of the messages are the same, as follows:

frank@flaptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 2_BROTHERS
libdvdnav: DVD Serial Number: 31350663
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/frank/.dvdnav/2_BROTHERS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000129e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00016020
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002cf7aa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002cf7ae
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e965d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e9661
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b4a1a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b4a1e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003cea56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003cea5a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003ef16b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ef16f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003ef191
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ef195
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003ef3c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003ef3c4
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
frank@flaptop:~$

---

### Post by mc4man on 2008-11-29
Sorry it's late and I didn't notice your using kubuntu. (doesn't matter in general, things are a little different though.

Try finding the .dvdcss folder and deleting it or it's contents, I don't have a kubuntu install atm, but look in your home folder (show hidden files - under view?

What's the name of the dvd (can't find any info on 2 brothers, if it's 2 brothers what studio released it?

edit:
If it's "two brothers" ( the 2 lions) then there wouldn't be any unusual structure protection requiring the latest libdvdnav4

As far as mplayer it defaults to /dev/dvd as the dvd device to access.
run to check your drives /dev links  (
the repo version uses libdvdcss2 so the seek error could be from improper keys rather than not being able to find dvd'

```
sudo lshw -C disk
``` 

If it shows /dev/dvd1 then adjust in mplayers preferences 

Also even though it shouldn't matter try a reboot

---

### Post by chip616 on 2008-11-29
mc4man:

Yeah, it was getting late.  I couldn't sleep last night, so started sleuthing this problem again.  I didn't expect an answer that quickly.  :)

OK, deleted the hidden directory and started vlc again -- no change.  Deleted it yet again, and rebooted.  Now it works.  Weird.

I'm guessing that the problem all along was that the DVD player in my machine did not have a region setting, but that after changing that, one has to reboot.

Now I just need to set up vlc so that it autostarts when a DVD is put in the drive...  I think I'll uninstall mplayer.  I can't be bothered with it.

Thanks for the help.

Frank.

---

### Post by mc4man on 2008-11-29
> Yeah, it was getting late. I couldn't sleep last night, 

You and me too.
You can definitely get it to autoplay thru setting a notification. If you decide to upgrade to 8.10 (Kde 4.x) I don't think it can autoplay anything atm.

---

### Post by chip616 on 2008-11-29
mc4man:

How do I set the notification so that vlc will autoplay when a DVD is in the drive?

Thanks.

Frank.

---

### Post by mc4man on 2008-11-29
> You can definitely get it to autoplay thru setting a notification

I may stand corrected on that, tried every which way, always ends up on a "/media/cdrom0 is a folder but a file was expected"

Can't find a post from back in august where I remember listing all the possible ways to play a dvd video with vlc and kaffeine which would refresh my memory as to whether autoplay was possible with vlc.

Did find one you posted in from late august, but i only said vlc worked fine which is none to helpful in this regard.

I have noticed somethings changed in kubuntu, now the dvd video disk is auto mounted to media/cdrom[COLOR="Red"]x[/COLOR], before it wasn't, and i was able to right click on the icon -> properties -> mounting and make changes. 
Now that's all greyed out.

Will let you know if any 'way' becomes workable.

edit; as back then kaffeine will autoplay, ect.

---

### Post by darksideforge on 2008-11-29
Mc4man,
YOU ARE A GENIUS!!!
I have been fighting a problem for 3 days where I kept getting an error message telling me that my computer "Can Not Mount The UDF Volume"
(please see here: [http://ubuntuforums.org/showthread.php?t=995400]("http://ubuntuforums.org/showthread.php?t=995400") as well as here: [http://ubuntuforums.org/showthread.php?t=978332]("http://ubuntuforums.org/showthread.php?t=978332") and I have been trying EVERYTHING....all to no avail! I've even been told by one moderator, after posting code and screenshots, that absolutely everything in my system looks good, and nobody....I mean NOBODY could figure anything out!!!

I've been so frustrated that I started looking around today at Kubuntu and other variants of ubuntu to see if, since it looked like I was going to have to wipe my HDD and start over with a new install, I might like one of the other DTE's better. After getting on the message board and looking for posts from kubuntu, I saw this post regarding DVD-RW's and thought I'd take a look...even though I'm using Gnome as opposed to KDE.

After reading all the way through the post and seeing where chip616 thought you were probably right about the restart being required after the regionset, I just brought up my terminal and executed your first suggestion on regionset, did a normal restart and.........VOILA!!!!

Again, I can't thank you enough!   I realize that, as a rank beginner I probably don't have any business on this board, but DAMN I'm glad I checked it out anyway!

~darksideforge



> **mc4man said:**
> If your using gmplayer (from applications menu vs. command line) then open it up, right click in video window -> preferences -> audio and choose a driver. (probably alsa.

If from command line specify your audio  
-ao alsa

As far as commercial while it's not 100% necessary some drives, particularly on laptops, require that a region be set on the drive for access to encrypted disks.

To ck.

```
sudo apt-get install regionset
```

In the terminal with a **dvd in the drive**
```
regionset
```

See if it reports the drive as being set. (only needs to be set once, don't change if already set to your region (region 1 n.america, region 2 europe, ck. on the rest in the thread you were following.


In still no good open vlc from a terminal -> file -> open disk and post errors

Sometimes you also need to go into home folder (show hidden files) and delete everything inside of the .dvdcss folder

In 8.04 using vlc 0.8.6 it's good to change vlc's launch command

Right click on applications -> edit menus -> highlight sound and video -> right click on vlc -> properties. Change the command from vlc %U
```
vlc %f
```

---

### Post by chip616 on 2008-11-29
mc4man:

>I may stand corrected on that, tried every which way, always ends up on a "/media/cdrom0 is a folder but a file was expected"<

Not a biggie.  It works well enough for me as it is.  I was just thinking of my daughter who has a similar laptop, but she is capable of starting vlc to play a DVD.

Frank.

---

### Post by mc4man on 2008-11-29
And I'm gathering you don't like kaffeine?, or is it that it didn't work right?
(needs 2 'tweaks' to get going

---

### Post by chip616 on 2008-11-30
mc4man:

>And I'm gathering you don't like kaffeine?, or is it that it didn't work right?<

Both.

However, is there not a way that it can be added to the context menu when a DVD is put into the drive?  I get a list of options in the window:

"An new medium has been detected.  What do you want to do"

Then I can open it in Dolphin, k3b, or do nothing.  There must be a way to edit that to include playing it with vlc, no?

Frank.

---

