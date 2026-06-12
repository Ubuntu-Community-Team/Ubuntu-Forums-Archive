---
title: "Replacement DVD drive won't play movies"
date: 2008-12-27
forum: Multimedia Software
---

### Post by PirateFanAZ on 2008-12-27
I have replaced my computer's original Sony DVD+-RW drive with a Pioneer DVR-116D DVD+-RW drive.  I'm using Ubuntu 8.10 and using my Sony drive movies played fine in my default player, VLC.  Once I switched out the Sony for the Pioneer drive the same movies will not play using VLC or MPlayer.  Both players are configured to use device /dev/dvd1.

When I insert a DVD movie the drive does mount, I get an icon on my desktop for it, and I am able to browse the contents of DVDs using the Pioneer drive.  Additionally I do think the firmware on the drive is the most recent.

The error I'm receiving from VLC is:
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd1'. Check the log for details.

I would post the contents of that log but must sheepishly admit I can't find it.

The error I get from MPlayer is:
No stream found to handle url dvd://1

Output of  sudo lshw -C disk command:

  *-cdrom:0               
       description: DVD writer
       product: DVD-RW  DVR-116D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

Content of my /etc/udev/rules.d/70-persistent-cd.rules file (I did reset this file as suggested in another thread here):

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well. 
#  (pci-0000:00:1f.1-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
#  (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"


Any assistance would be most appreciated by this noob.

---

### Post by mc4man on 2008-12-27
Try 2 things, open vlc -> media -> open disc and give it a device of /dev/scd0

Also run 
 ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Remove the entries, save and then reboot.

Leave it like this
> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well. 


Do the rules first and after reboot try vlc

---

### Post by PirateFanAZ on 2008-12-27
Thanks mc4man.

I edited my 70-persistent-cd.rules file as you suggested then rebooted.  After my machine came back up I went to Tools -> Preferences in VLC and in Inputs and Codecs I changed the default disc device to /dev/scd0.  I then closed VLC and restarted it.  I used Media -> Open Disc and changed disc device to /dev/scd0 and clicked Play.  I received the same error:

Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd0'. Check the log for details.

Any other ideas?  Thanks again.

---

### Post by mc4man on 2008-12-27
Something is obviously amiss.

When you installed the drive what jumper did you set it at?

Also with a dvd in the drive run the sudo lshw again, see it it shows a mounted status. (and double ck. the logical names

If you where to set vlc as the default (autorun player) what happens when you insert a dvd?
( set in nautilus (home folder) -> edit -> preferences -> media or while inserting a dvd hold down the shift button and you'll get a popup




Post your fstab 

```
cat /etc/fstab
```

Right click on the dvd icon -> properties -> volume and ck. the mount point


While vlc 0.9.x isn't very good at opening a directory (video_ts) from vlc, it will from the other 'direction'

Try navigating to /media/cdrom1, right clicking on the video_ts, open with vlc or continue on to 'open with other application' and choose vlc

---

### Post by PirateFanAZ on 2008-12-27
Here are the results you asked for mc4man:

The jumper is set so that the Pioneer DVR-116D is master, just as the Sony DVD+-RW drive was.

The output for the Pioneer drive from teh lshw command run with the movie DVD in the Pioneer drive:

lshw -C disk

  *-cdrom:0               
       description: DVD writer
       product: DVD-RW  DVR-116D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

VLC is set as my default media player for DVD discs.  When I first load the DVD movie disc in the Pioneer drive VLC starts, displays a message on the menu bar (something to do with the VIDEO_TS folder on the DVD drive I think, it goes by pretty quick) then it exits.

Here is the output from the cat /etc/fstab command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=83e04d42-215d-49c8-bc66-b56acecb6350 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2d1cb6aa-df12-49ee-bb5f-58dce61d2bf6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Again, thanks for your help with this.

---

### Post by PirateFanAZ on 2008-12-27
Sorry I missed the last of your inquires:

The mount point is /media/cdrom1 - right clicked on icon on desktop for DVD to get that.

When I try to open the VIDEO_TS folder by right clicking and selecting VLC as the open with application VLC draws itself and then goes away.

Thanks again for you help.

---

### Post by mc4man on 2008-12-27
Sorry I forgot the 1st. thing to address
Did you set a region on the drive? (not all drives and or disks require, should be set though, your R 1

If not 
```
sudo apt-get install regionset
```

Then with a disk in the drive run from the terminal
```

regionset /dev/scd0
```

Otherwise maybe you need to change video and possibly audio output modules.

Ck. on a region first.

Then start vlc from the terminal for error messages when trying to access disk

---

### Post by PirateFanAZ on 2008-12-27
I hadn't checked the region code on the drive.  Here is the output from the regionset command:

regionset /dev/scd0

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

I think region 1 is correct for me as I live in the US.

When I started VLC from the command line and attempt to play the movie DVD I get the previously mentioned error.  Here is the terminal output from VLC:

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FLYBOYS_WS
libdvdnav: DVD Serial Number: 357C78C9
libdvdnav: DVD Title (Alternative): FLYBOYS_WS
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FLYBOYS_WS.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

I looked for these error messages on the web but didn't find anything that looked like the solution, although I could easily have missed it.

The settings for VLC, other than the device settings (/dev/scd0, /dev/dvd1 etc.) are the same as before when I was able to play DVDs, including the one I'm testing with, using the Sony DVD drive I've replaced.  Would those need to change when I swap out a drive?

Thx.

---

### Post by mc4man on 2008-12-27
Well try resetting vlc, go into home folder (edit -> show hidden files) -> .config and delete the vlc folder. (this will set vlc back to default install

While your there delete the .dvdcss folder also

Very curious error, do you have any other dvds to try?

```
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
```

Edit: are you sure you have libdvdcss2 installed?

---

### Post by PirateFanAZ on 2008-12-27
Thanks for the suggestions mc4man.

libdvdread3, libdvdnav4 and libdvdcss2 all show as being installed in Synaptic Package Manager.

I deleted the vlc folder and its contents.  There was no .dvdcss folder in the .config directory though.  I looked in ~/.config for a .dvdcss folder.  None there.  Could that be an issue?

I inserted another DVD and started VLC again.  I got the message you get when VLC first starts up (indicating to me that it was initialized) but when I tried to play the new DVD movie I received the same error message in the original post.

Thanks again for your help.

---

### Post by mc4man on 2008-12-27
The .dvdcss would be in your home folder (not in .config

Delete it, try vlc again, then go look inside the .dvdcss folder and see if there is a folder for your movie and if so are there key files inside.

If there is no .dvdcss folder recreated then post back that info.

Just curious
is the pioneer a new drive or a used drive?

---

### Post by mc4man on 2008-12-27
I've got to run for an hour.
Even though I use a different vlc version this is what you should see from terminal. (red for emphasis

> doug@doug-desktop:~$ vlc
VLC media player 1.0.0-git Goldeneye
[0x8051168] main libvlc debug: VLC media player - version 1.0.0-git Goldeneye - (c) 1996-2008 the VideoLAN team
[0x8051168] main libvlc debug: libvlc was configured with ./configure  '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-caca' '--enable-faad' '--disable-dvb' '--disable-dvbpsi' '--disable-kate' '--disable-mpc' '--enable-x264' '--with-x264-tree=./extras/x264' '--enable-mp4'
[0x8051168] main libvlc debug: translation test: code is "C"
[0x8051168] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
[COLOR="Red"]libdvdread: Using libdvdcss version 1.2.10 for DVD access[/COLOR]
libdvdnav: DVD Title: CHILDREN_OF_MEN
libdvdnav: DVD Serial Number: 363d9f29
libdvdnav: DVD Title (Alternative): WIDESCREEN_R0
libdvdnav: Unable to find map file '/home/doug/.dvdnav/CHILDREN_OF_MEN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

maybe try 
```
sudo aptitude purge libdvdcss2 vlc
```

Then delete the vlc folder in .config, go here and install libdvdcss2 (click on the i386

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

then go 
```
sudo apt-get install vlc
```

---

### Post by PirateFanAZ on 2008-12-27
I deleted the vlc and .dvdcss folders and started VLC to play the DVD movie.  I did receive a different error this time:

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.

The .dvdcss folder was created and now contains a folder called FLAGS_OF_OUR_FATHERS-2007011206571300-6acb11d3bf and a file called CACHEDIR.TAG.  The directory FLAGS_OF_OUR_FATHERS-2007011206571300-6acb11d3bf contains a series of seven text files each containing a single line looking like this:
ca:36:1b:5c:5f
I'm not sure if these are the key files you expected.

I repeated the process (deleting the vlc and .dvdcss folders) and tried to play the movie I was originally testing with and received the same error as posted originally.  The output in the terminal windows is that same as well.

The Pioneer drive I purchased new from NewEgg.com.  I've never received something from them that didn't work, but I suppose there is a first time for everything.

Thanks.

---

### Post by PirateFanAZ on 2008-12-27
I followed your instructions for purging and reinstalling.  I received the orginal error when I ran VLC.  The line in your output in read is not in my output so clearly there is a difference in our setups.  I'm not sure what that is but it is there.

Isn't there a script that needs to be run when installing libdvdcss?  I seem to remember running a script from a HowTo when I had this working before installing the new drive.

Thanks again.

---

### Post by mc4man on 2008-12-27
```
 sudo /usr/share/doc/libdvdread3/install-css.sh
```

That will install either an earlier or same version of libdvdcss2

The keys are being retrieved, that's why they're in .dvdcss

You could try a totally different player that uses some other libs. (with the exception of libdvdcss2

If so try 

```
sudo apt-get install totem-xine libxine1-ffmpeg
```

Look for it in Applications -> sound & video under Movie Player (Xine)

Edit:

The only reason I asked about the drive is that generally new drives don't have a region set, your post implied it was already set ...?

---

### Post by PirateFanAZ on 2008-12-27
No problem with regard to the drive.  I intended to purchase a new drive from NewEgg.com but maybe they sent me a refurbished drive?  It did look like the region had been set to Region 1.

I followed your advice and installed Totem.  I tried to play the same DVD and received the following error:

Totem could not play 'dvd:///dev/scd0'.
The source seems encrypted, and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?

I started Synaptic Package Manager and searched for libdvdcss.  It shows that libdvdcss2 is installed.  Is there a difference, besides version, between libdvdcss and libdvdcss2?  Different purposes?

Thanks for your reply.

---

### Post by mc4man on 2008-12-27
> Is there a difference, besides version, between libdvdcss and libdvdcss2? Different purposes
No libdvdcss2 is what you want.

In rare cases some setups only work with an older version, the script in Intrepid has been updated to retrieve libdvdcss2 from medibuntu so it's the exact same one you have.

In prior releases it would retrieve 1.2.5, if you want to try that version, remove your current and install from here. (try 1.2.5 and or 1.2.9

[http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)


There would be a way if you wish to test the drives ability to read the complete disk, and then the players ability to read and decrypt separately from each other.

We're either missing something simple or there's something about that drive.

Let me know about if you wish to test the drive and players apart from each other.

---

### Post by PirateFanAZ on 2008-12-28
Thanks for the help mc4man.

I feel as though we've done enough to convince me that there is something wrong with that drive.  I removed it from the machine and put the Sony back in.  Movies now play fine.  I only changed out the drive.

I requested and received return authorization from NewEgg.com to exchange the Pioneer drive.  We'll see what happens when I receive the new one.

I really to appreciate your efforts to assist.  I'll repost on this thread after I get the new drive to report success or continuing failure.

Thanks again.

PirateFanAZ.

---

### Post by Dublee on 2009-01-03
I had a similar issue, even after trying the above suggestions on my ThinkPad X61s laptop.  I got it to work by installing regionset (sudo apt-get install regionset) and setting it to region 1.

---

### Post by ignacio69 on 2009-01-03
i have a similar problem, I have searched all ubuntuforums, read the manual of VLC, install all the librairies, but I still get the same error:
"No se puede montar el volumen"
mount: block device dev/scd0 is write protected

I have bought a used DVR-11D Pioneer and installed in my ubuntu 8.10.
I can listen CD music
I can record DVD-R using Brasero
I cannot read DVD at all
I have tried gstreamer in Totem and also VLC. alwys got the same error.
Here is the information that I could find in Linux

**The output of sudo lshw -C disk**
  *-disk:0                
       description: ATA Disk
       product: Maxtor 2R010H1
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: EAH4
       serial: R141SC2C
       size: 9771MiB (10GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=31f94c3c
  *-disk:1
       description: ATA Disk
       product: HDS728080PLAT20
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: PF2O
       serial: PFD815S2DSMSNM
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6d0c844b
  *-cdrom:0
       description: DVD writer
       product: DVD-RW  DVR-111D
       vendor: PIONEER
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.23
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom1
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-W524E
       vendor: TEAC
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.0C
       serial: [TEAC    CD-W524E        1.0C01/07/02
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc

**The VLC log using the terminal:**
 cvlc /media/cdrom1
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "es"
[00000404] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ignacio/.dvdnav/.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
Error en el bus

**The output of cdrecord -scanbus:**
scsibus1:
	1,0,0	100) 'PIONEER ' 'DVD-RW  DVR-111D' '1.23' Removable CD-ROM
	1,1,0	101) 'TEAC    ' 'CD-W524E        ' '1.0C' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

**The output of  cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b5108034-5073-4800-9a60-8d3bf32972f4 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=53b1c518-d178-45cf-a882-3dcae64db66c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

Any suggestions, is there any firmware to flash or do I have to make a manual mount of the media...?

---

### Post by sanitycheck on 2009-01-04
From what I could tell, I could not play DVD movies as a result of my upgrade from Gutsy to Hardy (i386, Kubuntu).  I could access the files on the drive in Dolphin but the movie would not play in VLC, Mplayer, or Kaffeine.  I received similar errors to what have been posted here.

I installed and ran the regionset program (regionset /dev/scd1).  I received an error saying that the region could not be retrieved from the drive.  "This could mean your drive is region free and doesn't need any setting. Would you like to change the region setting of your drive? [y/n]."  I answered no, since the drive worked fine under Gutsy.

From that point, and without even a reboot, I could play unencrypted disks.  I can play encrypted disks, too, but not under Kaffeine (the default, which I never use anyway).

I can't say for sure regionset was the magic fix, but I thought I'd mention it in case it was.

---

### Post by seventyeights on 2009-01-05
Regionset!

That absolutely positively fixed the problem for me.

I wonder if it only occurs on sata drives? I may test that later.

Anyway, thanks for posting the answer.

---

### Post by sanitycheck on 2009-01-06
> **seventyeights said:**
> I wonder if it only occurs on sata drives?

No. My DVD drive is the old style parallel ATA, so that's not it.  It's an old single-layer-only drive.  I can't remember who made it.

Did you set a region, or did you just exit with no changes as I did?

---

### Post by me121 on 2009-01-06
I'm having a similar problem. I can play normal DVD's but not encrypted dvd's. I have installed libdvdread3 0.9.7-11ubuntu2 and then subsequently libdvdcss2 1.2.10-1. I have installed ubuntu restricted extras.

I have run regionset and it says "drive plays discs from region(s): 4, mask=0xF7" which is correct I am trying to play a region 4 disk.

The terminal log I get when I try to play a DVD in VLC is,
```
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: Hancock
libdvdnav: DVD Serial Number: 3938a309
libdvdnav: DVD Title (Alternative): Hancock
libdvdnav: Unable to find map file '/home/user/.dvdnav/Hancock.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdread: Invalid main menu IFO (VIDEO_TS.BUP).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

```

When I try to play it in totem using gstreamer (i don't have xine installed) the terminal log is,
```
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).

(totem:7078): GStreamer-CRITICAL **: 
Trying to dispose element test_dvdsrc, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

```

This is on a fresh Ubuntu 8.10 with relevant updates applied.

Here is some more output,
```
user@mediapc:~$ sudo lshw -C disk
...
  *-cdrom
       description: DVD reader
       product: DVD+RW ND-2100AD
       vendor: _NEC
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 103D
       serial: [_NEC    DVD+RW ND-2100AD103D03093001
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

```

Though the most interesting this is that some encrypted DVD's work... I'm not sure but it looks like newer DVD's don't work but older ones do. But thats just from testing 2 DVD's so its a guess.

Any help? Should I file a bug report? Thanks!

EDIT: It seems to be working fine now. A few restarts must have fixed it, though I swear I had restarted it with no difference noticed.

---

### Post by ignacio69 on 2009-01-07
Dear sanintycheck,
thanks for the tip of the regionset. I risked it anyway and here is the **output:**
 regionset dev/scd0
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "dev/scd0"!
Please ensure there is a readable CD or DVD in the drive.

can you see anything wrong in this log.

I tried it several times, changing dev/scd0 to dev/src0 or to /media/cdrom1 with the same result

Any suggestions?

does anybody has experience with pioneer dvr-111d working under ubuntu without problems?

---

### Post by sanitycheck on 2009-01-07
> **ignacio69 said:**
> regionset dev/scd0

You need an extra slash in front:

   ```
regionset /dev/scd0
```

---

### Post by ignacio69 on 2009-01-09
Dear sanitycheck, thank you for the tip of the slash, you were right, **here is the output of the regionset:**

regionset /dev/scd0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:n

What does it mean regionset 2?
shoudl I change it, since now I am in Slovakia?

**Here is the output of VLC:**
ignacio@ignacio-desktop:~$ cvlc /dev/scd0
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "es"
[00000404] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: MULAN
libdvdnav: DVD Serial Number: c6545035        
libdvdnav: DVD Title (Alternative): MULAN
libdvdnav: Unable to find map file '/home/ignacio/.dvdnav/MULAN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
[00000477] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2

---

### Post by sanitycheck on 2009-01-09
> **ignacio69 said:**
> What does it mean regionset 2?

The purpose of DVD region coding is beyond the scope of this thread.  You should research it further, however, before making any change.  You can only change the region code of some drives a limited number of times.

---

### Post by ignacio69 on 2009-01-09
Dear Sanitycheck,
I apologize for not looking it up the information fo regionset before posting. I am sorry and grateful at the same time.

I have read the README of regionset wich was in /usr/share/doc/regionset/README
and i Understood the following:
1. according to the following output 
[PHP]drive plays discs from region(s): 2, mask=0xFD[/PHP]

right now my drive is in regionset 2, which means Europe, which is OK.
2. acdording to the following output:
[PHP]vendor resets available: 4
user controlled changes resets available: 4[/PHP]
i still have 4 more times to change the regionset

so, now i suspect that the problem is related to the following output:
[PHP]Unable to find map file '/home/ignacio/.dvdnav/MULAN.map'[/PHP]
or:
[PHP][00000477] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
ALSA lib conf.c:3952snd_config_expand) **Unknown parameters** AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2[B]
ALSA lib pcm.c:2196snd_pcm_open_noupdate) Unknown PCM [/B]iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2 
[/PHP]


according to this output:
[PHP]libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
[/PHP]i can see that the vlc can read from all the regions:

am I right?

can you give me more hints, please? or recommend it more reading

---

### Post by mc4man on 2009-01-09
> Unable to find map file '/home/ignacio/.dvdnav/MULAN.map' 
That's irrelevant, always is shown 

> ALSA lib conf.c:3952snd_config_expand) **Unknown parameters** AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2[b]
ALSA lib pcm.c:2196snd_pcm_open_noupdate) Unknown PCM [/b]iec958:AES0=0x2,AES1=0x82,AES2=0x0,AES3=0x2  

That's the real issue, it may be related to the video and or audio output modules your using. Though ...

Is this the disney movie "Mulan"? or something else.
If it is this is suspect
> libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

May be good to see this (looking for dvd drive model

```
sudo lshw -C disk
```

---

### Post by PirateFanAZ on 2009-01-10
Hello all,

I received a replacement drive from NewEgg.com.  I checked its region setting after I installed it and saw that no region was set on this drive, Pioneer DVR-116, as as before.  I set the region to 1.  I uninstalled vlc and libdvdcss2 per previous recommendation from mc4man.  I then rebooted my machine and reinstalled livdvdcss2 from medibuntu and reinstalled vlc.  I attempted to play a dvd and received the same error as before.  Bummer.

Mc4man, you had previously posted VLC output from your system.  I listed using libdvdcss2, or something to that effect.  I do not get that line of output when I run vlc from the command line:

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FLYBOYS_WS
libdvdnav: DVD Serial Number: 357C78C9
libdvdnav: DVD Title (Alternative): FLYBOYS_WS
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FLYBOYS_WS.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

Any other ideas would be most appreciated.

Thanks.

---

### Post by mc4man on 2009-01-10
At least you have a drive that wasn't possibly someones return.

While I don't use 0.9.4 I re installed that version and I always see that line right under the dvdnav line.

But if libdvdcss2 is removed vlc will report "encrypted dvd playback unavailable'

What I'd try
Reboot
Try another player, even the crappy totem-gstreamer
go into home folder (view - show hidden files), find the .dvdcss folder and delete it.
Then try the disk again and see if the .dvdcss folder is recreated and if so is the a folder inside for flyboys with key files inside.

try another dvd if possible

---

### Post by PirateFanAZ on 2009-01-10
Thanks for the reply mc4man.

I did as you suggested.  I rebooted my machine and installed Totem.  I then deleted the .dvdcss folder and tried to play a different DVD using Totem.  I received this error message from Totem:

Totem could not play this media (DVD) although a pluging is present to handle it.
You might want to check that a disc is present in the drive and that it is correctly configured.

Here is the output from Totem (I started it from the command line):

** (totem:7277): DEBUG: Init of Python module
** (totem:7277): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7277): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7277): DEBUG: Creating Python plugin instance
** (totem:7277): DEBUG: Init of Python module
** (totem:7277): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7277): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7277): DEBUG: Creating Python plugin instance

(totem:7277): GStreamer-CRITICAL **: 
Trying to dispose element test_dvdsrc, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

** (totem:7277): DEBUG: Finalizing Python plugin instance
** (totem:7277): DEBUG: Finalizing Python plugin instance

After I ran Totem I checked to see if the .dvdcss folder was recreated.  It was and contained a single text file called 000000014f.

Here is the output from VLC (I tried it after trying Totem):

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: ifoOpenVTSI failed
[00000409] dvdnav demux error: cannot set title (can't decrypt DVD?)
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

Any other ideas or suggestions would be welcome.  I really appreciate your efforts to assist me.

Thanks again.

PirateFanAZ.

---

### Post by mc4man on 2009-01-10
This is got to be so frustrating

Try this with a dvd in the drive
(maybe also try totem-xine

```
export DVDCSS_METHOD=title && vlc dvd://
```

If that doesn't work remove libdvdcss2 and try an older version (1.2.5

[http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)


There should usually be several files per folder in .dvdcss  (at this point delete it before each attempt

---

### Post by PirateFanAZ on 2009-01-10
Thanks for the reply mc4man.

I removed the version of libdvdcss2 I was using and installed version 1.2.5-1 from the location you provided.  I then ran the command you provided with the following results.  None of them good lol!

Output from the DVDCSS command:

~$ export DVDCSS_METHOD=title && vlc dvd://
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdnav: ifoOpenVTSI failed
[00000409] dvdnav demux error: cannot set title (can't decrypt DVD?)

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"

No .dvdcss folder was created.

When I try the same thing with Totem:

Error message is:  An error occurred.  Could not open location; you might not have permission to open the file.

The output:

:~$ export DVDCSS_METHOD=title && totem dvd://
** (totem:6633): DEBUG: Init of Python module
** (totem:6633): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6633): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6633): DEBUG: Creating Python plugin instance
** (totem:6633): DEBUG: Init of Python module
** (totem:6633): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:6633): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:6633): DEBUG: Creating Python plugin instance
** Message: no file info
Device is now /dev/dvd
Device is now /dev/dvd
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(322): rsn_dvdsrc_start (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: No such file or directory

** (totem:6633): DEBUG: Finalizing Python plugin instance
** (totem:6633): DEBUG: Finalizing Python plugin instance

No .dvdcss folder was created.


If I just run VLC from the command line and try to open the DVD I get:

:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdnav: ifoOpenVTSI failed
[00000409] dvdnav demux error: cannot set title (can't decrypt DVD?)

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

No .dvdcss folder was created.

And if I run Totem I get:

Same error message as before.  Command line output is:

:~$ totem
** (totem:6666): DEBUG: Init of Python module
** (totem:6666): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6666): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6666): DEBUG: Creating Python plugin instance
** (totem:6666): DEBUG: Init of Python module
** (totem:6666): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:6666): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:6666): DEBUG: Creating Python plugin instance

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***


(totem:6666): GStreamer-CRITICAL **: 
Trying to dispose element test_dvdsrc, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

** (totem:6666): DEBUG: Finalizing Python plugin instance
** (totem:6666): DEBUG: Finalizing Python plugin instance

The change to version 1.2.5-1 of libdvdcss2 appears to have resulted in no .dvdcss folder creation.  I'm pretty sure that previously that folder was getting created.

This is a little frustrating but not the end of the world.  It's not like the drive was a million dollars or anything but it should work I think.  Incidentally I was able to burn data dvds using the new Pioneer drive.  I used both Brasero and K3B to do that.

Thanks again for your help.  I'll bet this is frustrating for you too :).  You've put a lot of time into this with me.  Thanks.

One thing I noticed in the output was this line:
libdvdnav: DVD disk reports itself with Region [COLOR="Red"]mask 0x00fe0000[/COLOR]. Regions: 1

Here is the output from regionset:
:~$ regionset /dev/scd0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, [COLOR="Red"][COLOR="Black"][COLOR="Red"]mask=0xFE[/COLOR][/COLOR][/COLOR]

Do the masks match?

---

### Post by mc4man on 2009-01-10
The export command should last till you reboot, actually there was a little progress in  vlc, notice it said "error cracking key" (didn't get that far before

Try upgrading libdvdcss2 to the current version (1.2.10

I'd install totem-xine and try that 
(use totem-xine from cli


edit : I really doubt this is a drive issue,the pioneer is fine

---

### Post by PirateFanAZ on 2009-01-10
I installed totem-xine and the latest libdvdcss2.

I received the following error message when I tried to play the Filed of Dreams DVD:

An error occurred.  The source seems encrypted, and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?

A .dvdcss folder was created.  It contained a file called CACHEDIR.TAG and an empty folder called FIELD_OF_DREAMS-2004041915454300-0000000000.

I tried to post the output from the totem-xine command but apparently there are symbols or text in the output that the forum interprets as images and it won't let me post.  Is there a way around that?

Here is the output now when I try to play the same DVD with VLC:

:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdnav: ifoOpenVTSI failed
[00000409] dvdnav demux error: cannot set title (can't decrypt DVD?)
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"

Synaptic Package Manager show libdvdcss2 version 1.2.10-1 is installed.

Looks like progress?

Thanks again.

---

### Post by mc4man on 2009-01-11
> Looks like progress ?
No not really but there does seem to be some attempt by vlc to crack the keys. Before it didn't try. (or didn't report trying ...?

Totem-xine needs libxine1-ffmpeg installed for commercial dvds.


Edit: 
Been awhile since i've seen an issue in this area but why don't you put a dvd in and run these 2 things
```
grep "DMA" /var/log/syslog
```
```
dmesg | tail
```
..........................................................................
 

There would be something interesting to try if you have access to any other Os with vlc installed that can play back your dvds.

To digress
When vlc (and many other players) are asked to open an encrypted dvd the first thing they  do is ck. in the .dvdcss folder (or dvdcss in windows) for a folder matching the volume they're trying to open.

If a matching folder is found they'll use the keys inside to decrypt rather than cracking them from the disk.

You could take the folder from a setup that can play and copy it to your current .dvdcss folder and see what happens.

You know where it is in linux, for xp the location is -
Documents and Settings/[COLOR="Red"]doug[/COLOR]/Application Data/dvdcss

In vista it's -
[COLOR="Red"]Doug[/COLOR]/AppData/Roaming/dvdcss

At this point I'd also re install libdvdread3 and libdvdnav4 (if you don't mind re-installing your players I'd purge them.

If you reboot the export command is no longer in effect, I'd try first without, then with

---

### Post by PirateFanAZ on 2009-01-11
libxine1-ffmpeg is installed.  I checked using Synaptic Package Manager.

The command grep "DMA" /var/log/syslog returned no results.

Here is the output from the dmesg command:
$ dmesg | tail
[63033.247069] end_request: I/O error, dev sr0, sector 1116
[63033.251017] end_request: I/O error, dev sr0, sector 1120
[63033.256889] end_request: I/O error, dev sr0, sector 1120
[63033.504955] end_request: I/O error, dev sr0, sector 1116
[63033.505131] udf: udf_read_inode(ino 279) failed !bh
[63033.559258] end_request: I/O error, dev sr0, sector 1120
[63033.559429] udf: udf_read_inode(ino 280) failed !bh
[63035.091057] end_request: I/O error, dev sr0, sector 12386980
[63035.151678] end_request: I/O error, dev sr0, sector 12387012
[63035.199464] end_request: I/O error, dev sr0, sector 12386996

I do dual boot XP SP3 and Ubuntu.  I installed VLC under my XP instance and it doesn't work either.

Playback failure:

VLC cannot set teh DVD's title.  It possibly cannot decrypt the entire disk.



Then Windows traps an exception and wants to send an error report about the probelm.

I removed libdvdread3 and libdvdnav4.  I also removed VLC, MPlayer and Totem-xine.  I reinstalled them and got the same errors as before.  I executed the export command again then started VLC and totem-xine from the command line.  Here is the output from both:

$ export DVDCSS_METHOD=title && vlc dvd://
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdnav: ifoOpenVTSI failed
[00000409] dvdnav demux error: cannot set title (can't decrypt DVD?)
[00000409] dvdread demux error: fatal error in vts ifo
[00000409] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"


$ export DVDCSS_METHOD=title && totem-xine dvd://
** (totem-xine:7556): DEBUG: Init of Python module
** (totem-xine:7556): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem-xine:7556): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem-xine:7556): DEBUG: Creating Python plugin instance
** (totem-xine:7556): DEBUG: Init of Python module
** (totem-xine:7556): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem-xine:7556): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem-xine:7556): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sda2 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda2 with libdvdcss.
libdvdread: Can't open /dev/sda2 for reading
libdvdread: Device /dev/sda2 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdread: Elapsed time 0
libdvdread: Found 0 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sda2 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda2 with libdvdcss.
libdvdread: Can't open /dev/sda2 for reading
libdvdread: Device /dev/sda2 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: FIELD_OF_DREAMS
libdvdnav: DVD Serial Number: 30939db5
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jbodamer/.dvdnav/FIELD_OF_DREAMS.map'
libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014f
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x0000014f)
libdvdread: Elapsed time 0
libdvdread: Found 0 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
** (totem-xine:7556): DEBUG: Finalizing Python plugin instance
** (totem-xine:7556): DEBUG: Finalizing Python plugin instance

Thanks for your help mc4man.

---

### Post by xc3RnbFO8P on 2009-01-11
Try:
> cat /var/log/syslog* | grep DMA

---

### Post by PirateFanAZ on 2009-01-11
Ringi, here is the output:

$ cat /var/log/syslog* | grep DMA 
Jan 11 11:57:39 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 11 11:57:39 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 11 11:57:39 Lemieux kernel: [    3.279079] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 11 11:57:39 Lemieux kernel: [    3.279087] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 11 11:57:39 Lemieux kernel: [    3.608356] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 11 11:57:39 Lemieux kernel: [    3.608382] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 11 11:57:39 Lemieux kernel: [    3.624311] ata1.00: configured for UDMA/66
Jan 11 11:57:39 Lemieux kernel: [    3.632433] ata1.01: configured for UDMA/33
Jan 11 11:57:39 Lemieux kernel: [    3.836293] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 11 11:57:39 Lemieux kernel: [    3.836301] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 11 11:57:39 Lemieux kernel: [    4.037868] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 11 11:57:39 Lemieux kernel: [    4.104520] ata3.00: configured for UDMA/133
Jan 11 11:57:39 Lemieux kernel: [    4.324432] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 11 11:57:39 Lemieux kernel: [    4.340447] ata4.00: configured for UDMA/133
Jan 11 11:57:39 Lemieux kernel: [   13.531765] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 10 11:37:20 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 10 11:37:20 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 10 11:37:20 Lemieux kernel: [    3.360224] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 10 11:37:20 Lemieux kernel: [    3.360234] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 10 11:37:20 Lemieux kernel: [    3.692357] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 10 11:37:20 Lemieux kernel: [    3.692383] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 10 11:37:20 Lemieux kernel: [    3.708289] ata1.00: configured for UDMA/66
Jan 10 11:37:20 Lemieux kernel: [    3.728294] ata1.01: configured for UDMA/33
Jan 10 11:37:20 Lemieux kernel: [    3.901753] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 10 11:37:20 Lemieux kernel: [    3.901758] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 10 11:37:20 Lemieux kernel: [    4.107425] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 10 11:37:20 Lemieux kernel: [    4.165737] ata3.00: configured for UDMA/133
Jan 10 11:37:20 Lemieux kernel: [    4.384447] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 10 11:37:20 Lemieux kernel: [    4.402230] ata4.00: configured for UDMA/133
Jan 10 11:37:20 Lemieux kernel: [   23.254996] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 10 11:56:58 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 10 11:56:58 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 10 11:56:58 Lemieux kernel: [    3.488860] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 10 11:56:58 Lemieux kernel: [    3.488870] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 10 11:56:58 Lemieux kernel: [    3.820358] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 10 11:56:58 Lemieux kernel: [    3.820383] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 10 11:56:58 Lemieux kernel: [    3.836291] ata1.00: configured for UDMA/66
Jan 10 11:56:58 Lemieux kernel: [    3.844432] ata1.01: configured for UDMA/33
Jan 10 11:56:58 Lemieux kernel: [    4.023407] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 10 11:56:58 Lemieux kernel: [    4.023417] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 10 11:56:58 Lemieux kernel: [    4.223272] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 10 11:56:58 Lemieux kernel: [    4.289888] ata3.00: configured for UDMA/133
Jan 10 11:56:58 Lemieux kernel: [    4.508435] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 10 11:56:58 Lemieux kernel: [    4.524464] ata4.00: configured for UDMA/133
Jan 10 11:56:58 Lemieux kernel: [   23.767476] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 10 13:16:50 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 10 13:16:50 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 10 13:16:50 Lemieux kernel: [    3.408773] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 10 13:16:50 Lemieux kernel: [    3.408781] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 10 13:16:50 Lemieux kernel: [    3.740355] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 10 13:16:50 Lemieux kernel: [    3.740380] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 10 13:16:50 Lemieux kernel: [    3.756289] ata1.00: configured for UDMA/66
Jan 10 13:16:50 Lemieux kernel: [    3.764432] ata1.01: configured for UDMA/33
Jan 10 13:16:50 Lemieux kernel: [    3.969380] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 10 13:16:50 Lemieux kernel: [    3.969386] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 10 13:16:50 Lemieux kernel: [    4.172889] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 10 13:16:50 Lemieux kernel: [    4.239532] ata3.00: configured for UDMA/133
Jan 10 13:16:50 Lemieux kernel: [    4.456426] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 10 13:16:50 Lemieux kernel: [    4.472448] ata4.00: configured for UDMA/133
Jan 10 13:16:50 Lemieux kernel: [   13.707701] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 10 14:20:11 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 10 14:20:11 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 10 14:20:11 Lemieux kernel: [    3.393647] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 10 14:20:11 Lemieux kernel: [    3.393655] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 10 14:20:11 Lemieux kernel: [    3.725357] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 10 14:20:11 Lemieux kernel: [    3.725382] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 10 14:20:11 Lemieux kernel: [    3.740293] ata1.00: configured for UDMA/66
Jan 10 14:20:11 Lemieux kernel: [    3.748435] ata1.01: configured for UDMA/33
Jan 10 14:20:11 Lemieux kernel: [    3.920804] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 10 14:20:11 Lemieux kernel: [    3.920809] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 10 14:20:11 Lemieux kernel: [    4.123662] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 10 14:20:11 Lemieux kernel: [    4.190298] ata3.00: configured for UDMA/133
Jan 10 14:20:11 Lemieux kernel: [    4.408420] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 10 14:20:11 Lemieux kernel: [    4.425463] ata4.00: configured for UDMA/133
Jan 10 14:20:11 Lemieux kernel: [   13.297805] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan 10 18:06:00 Lemieux kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 10 18:06:00 Lemieux kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jan 10 18:06:00 Lemieux kernel: [    3.327251] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 10 18:06:00 Lemieux kernel: [    3.327259] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 10 18:06:00 Lemieux kernel: [    3.656359] ata1.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.09, max UDMA/66
Jan 10 18:06:00 Lemieux kernel: [    3.656385] ata1.01: ATAPI: LTN526S, YS0N, max UDMA/33
Jan 10 18:06:00 Lemieux kernel: [    3.672291] ata1.00: configured for UDMA/66
Jan 10 18:06:00 Lemieux kernel: [    3.680435] ata1.01: configured for UDMA/33
Jan 10 18:06:00 Lemieux kernel: [    3.854049] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe500 bmdma 0xe800 irq 19
Jan 10 18:06:00 Lemieux kernel: [    3.854054] ata4: SATA max UDMA/133 cmd 0xe600 ctl 0xe700 bmdma 0xe808 irq 19
Jan 10 18:06:00 Lemieux kernel: [    4.053614] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
Jan 10 18:06:00 Lemieux kernel: [    4.120258] ata3.00: configured for UDMA/133
Jan 10 18:06:00 Lemieux kernel: [    4.340437] ata4.00: ATA-6: ST3160021AS, 3.05, max UDMA/133
Jan 10 18:06:00 Lemieux kernel: [    4.356434] ata4.00: configured for UDMA/133
Jan 10 18:06:00 Lemieux kernel: [   13.303921] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

Thanks.

PirateFanAZ

---

### Post by mc4man on 2009-01-11
What happens if you open up either player, then right click on the dvd movie icon -> browse. Take the video_ts folder and drag it onto the player.


was that dmesg run after inserting dvd? (showed no udf volume being mounted.

maybe a complete sudo lshw -C disk (with disk in drive

Edit: it's not encouraging that vlc can't play on windows either, do you have powerdvd or similar in win to try with?

What did you set the jumper on the drive to, and what's the other drive?

---

### Post by PirateFanAZ on 2009-01-14
When I drag and drop the VIDEO_TS folder onto:

VLC -> It just dies and goes away.

MPlayer -> Nothing happens at all.

totem-xine -> Wait cursor for about a minute and then it comes back without playing the DVD.

There is a DVD in the drive and here is the ouput of the dmesg command:

$ dmesg | tail
[111484.785074] Buffer I/O error on device sr0, logical block 331
[111484.785081] Buffer I/O error on device sr0, logical block 332
[111484.785089] Buffer I/O error on device sr0, logical block 333
[111484.785098] Buffer I/O error on device sr0, logical block 334
[111484.785107] Buffer I/O error on device sr0, logical block 335
[111485.050450] end_request: I/O error, dev sr0, sector 1120
[111485.050609] udf: udf_read_inode(ino 280) failed !bh
[111486.189274] end_request: I/O error, dev sr0, sector 12386980
[111486.236952] end_request: I/O error, dev sr0, sector 12387016
[111486.285056] end_request: I/O error, dev sr0, sector 12387000

Here is the complete output of the lshw -C disk command:

$ sudo lshw -C disk
[sudo] password for jbodamer: 
  *-cdrom:0               
       description: DVD writer
       product: DVD-RW  DVR-116D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=nodisc
  *-disk:0
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6QF1Z821
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000052e6
  *-disk:1
       description: ATA Disk
       product: ST3160021AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 3.05
       serial: 3JS3GL8R
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e2c8e2c8

As for VLC not working on Windows XP I don't have powerdvd or another player that I know of but I will look around for the orginal discs that came with my PC.  Maybe there is one there.

The jumper on the new Pioneer drive is set to Master just as the jumper on the old Sony were.  The other drive is a Lite-On CD-ROM drive.

Sorry it took so long to get back to you mc4man.  Caught a bit of a cold and was out of commission for a couple of days.  Thanks again for your help.

---

### Post by ignacio69 on 2009-01-15
Sorry for the late answer
the ouput of this  **sudo lshw -C disk** is:
  *-cdrom:0
       description: DVD writer
       product: DVD-RW  DVR-111D
       vendor: PIONEER
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.23
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-W524E
       vendor: TEAC
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.0C
       serial: [TEAC    CD-W524E        1.0C01/07/02
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc

The MULAN film is inspired of the disney one.
Does it have something to do with the fact that I cannot use the webcam because the device dev/video is not found?

---

### Post by mc4man on 2009-01-15
@ PirateFanAZ
Yeah I've been sick too. (as had this forum, though things seem improved

There's nothing I see wrong in all your logs ect. with the slight exception of this one line (may be nothing, just never seen it
> [111485.050609] udf: udf_read_inode(ino 280) failed !bh

I'm going to reread all your posts, see if anything stands out.

Here's a link to free 30 day powerdvd trial for Xp
[http://www.cyberlink.com/multi/download/trials_1_ENU.html](http://www.cyberlink.com/multi/download/trials_1_ENU.html)

Powerdvd uses it's own licensed decryption routine, so this will take libdvdcss out of the loop

Edit; that drive is back to /dev/dvd1., ect. shouldn't really matter though mplayer would be looking to /dev/dvd by default

You could try the deleting of the 70 ....rules again though probably of not any great value.
I'd first see if powerdvd works and if vlc continues to fail in xp

---

### Post by mc4man on 2009-01-15
@ignacio69
You didn't mention if you tried changing your audio out put module.

In vlc 0.9.x
tools -> preferences, click on audio icon and in the audio output box change from 'default' to something specific, try alsa first.

> 
The MULAN film is inspired of the disney one.
Then the disc being 'all region' makes sense, Disney would never release a title that wasn't region specific. A bootleg of a disney title would be all region and the quality could/would be a factor.

---

### Post by PirateFanAZ on 2009-01-15
I downloaded and installed the PowerDVD trial on my XP install and it didn't work either.  It knew it had a DVD in the drive to play, knew the title of the DVD but when I hit play it just stopped.  No error message, just stopped.  VLC (under XP) didn't work either.

I rebooted into Ubuntu and edited the 70 ....rules file again, rebooted one more time but VLC still didn't work.

You know a lot more about this than I.  Do you think that I may need something like a BIOS upgrade to make this newer drive work?  My machine is several years old and I've never upgraded the BIOS.  It just looks to me like a lower level problem maybe?

Thanks again.

---

### Post by ignacio69 on 2009-01-16
dear mc4man,
I am not sure what does it mean "changing your audio out put module"
I can tell you though, that I can use the record program in gnome to record my own voice in wav format, that i can listen to  music using the ryhm musicbox program, that I can watch youtubes videos in mozilla firefox, 
tomororow i am going to change my pioneer dvr-111d for a sony nec.
we will see.
i believe i have all codecs installed, only seems that encripted dvds cannot read.
i am not sure if it is something with the software: vlc, maplayer, xine and totem, neither the 4 of them can read dvds, or wiht the pioneer and the firmware or what?

I am not sure how to do this either:
"tools -> preferences, click on audio icon and in the audio output box change from 'default' to something specific, try alsa first."

however manythanks, 
I have read an archived post with the same topic whre you explain someone else to do all the region set, the preferences, and the rest of thing, for them it worked, not for pirate and me. never mind.

---

### Post by ignacio69 on 2009-01-18
[QUOTE]> **PirateFanAZ said:**
> When I drag and drop the VIDEO_TS folder onto:

VLC -> It just dies and goes away.

MPlayer -> Nothing happens at all.

totem-xine -> Wait cursor for about a minute and then it comes back without playing the DVD.

The same does to me
There is a DVD in the drive and here is the ouput of the dmesg command:

$ dmesg | tail
[   87.856409] lo: Disabled Privacy Extensions
[   98.080087] eth0: no IPv6 routers present
[  265.641314] ppdev0: registered pardevice
[  265.689482] ppdev0: unregistered pardevice
[  268.273500] ppdev0: registered pardevice
[  268.329562] ppdev0: unregistered pardevice
[  268.735585] ppdev0: registered pardevice
[  268.796228] ppdev0: unregistered pardevice
[ 1473.819138] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1473.854122] UDF-fs INFO UDF: Mounting volume 'MULAN', timestamp 2036/02/07 02:58 (103c)

Here is the complete output of the lshw -C disk command:

$ sudo lshw -C disk
  *-cdrom:0
       description: DVD writer
       product: DVD RW AD-5170A
       vendor: Optiarc
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.11
       serial: [Optiarc DVD RW AD-5170A 1.11 Jul19,2006
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

I have changed the drive, just in case the problem is of the drive, before I had a Pioneer DVR-111D and now a Optiarc DVD RW AD-5170A
but the result is the same
any suggestions?

---

### Post by ignacio69 on 2009-01-27
Dear Mc4man,
I apologize for stealing your time.
at the end I figured out how to make it work.
I only was able to make the DVD drive play movies using mplayer.
I had all the codecs but i had to write in the konsole, the following:
[PHP]mplayer -ao oss -vo x11 -nocache -framedrop -autosync 30 dvd://[/PHP]
that means i had to tell mplayer that i wanted to use the oss system for audio and the x11 for video
if you have any doubt just write in the terminal
[PHP]mplayer -vo help[/PHP]or [PHP]maplyer -ao help[/PHP]

the other options [PHP]-nocache -framedrop -autosync 30[/PHP]
are for slow machines as my pentium II PC 433 Celeron.
I hope this can help others.

---

### Post by PirateFanAZ on 2010-02-05
After more than a year I have discovered the problem I had.

I bought yet another DVD drive, a LiteOn, model number iHAP422-989.  I installed it in place of the original Sony drive, which finally died completely, and it didn't work either.  A little better than the Pioneer drive I'd given up on, but not reliable.

I don't know why, but I removed the IDE connector from my CDROM drive and connected it to the DVD drive.  It now works perfectly.  I'm down a CDROM drive, but that doesn't matter to me and a new IDE cable would likely bring both devices online.

Thanks to all for your assistance, mc4man in particular.

---

