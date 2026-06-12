---
title: "Problems playing DVD"
date: 2016-03-21
forum: Multimedia Software
---

### Post by Donnie Love on 2016-03-21
Trying to play a DVD in Lubuntu. Tried all the players, none would work for me. VLC gives me this error:  
 [COLOR=#ff0000]
Playback failure:[/COLOR]
[COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
[COLOR=#ff0000]Your input can't be opened:[/COLOR]
[COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

What do I need to do to make it work?[/COLOR]

[COLOR=#000000]
[/COLOR]

---

### Post by ajgreeny on 2016-03-21
[https://www.google.com/url?q=https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs&sa=U&ved=0ahUKEwjNt6Lw69LLAhWCuRQKHcEACUsQFggFMAA&client=internal-uds-cse&usg=AFQjCNHV1qPRGZsDsOO6dFBamgGEVNlDAg](https://www.google.com/url?q=https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs&sa=U&ved=0ahUKEwjNt6Lw69LLAhWCuRQKHcEACUsQFggFMAA&client=internal-uds-cse&usg=AFQjCNHV1qPRGZsDsOO6dFBamgGEVNlDAg) should give you the answer; install libdvdcss2 as instructed.

---

### Post by Donnie Love on 2016-03-22
That didn't work. I'm pretty sure I've already done that. Here are the results:

```

donnie@R103:~$ sudo apt-get install libdvd-pkg
[sudo] password for donnie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdvd-pkg
donnie@R103:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2016-03-22 13:27:31--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-NO92PE/Packages&#8217;

100%[======================================>] 3,520       --.-K/s   in 0.002s  

2016-03-22 13:27:37 (1.72 MB/s) - &#8216;/tmp/dvdcss-NO92PE/Packages&#8217; saved [3520/3520]

--2016-03-22 13:27:37--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-NO92PE/libdvdcss.deb&#8217;

100%[======================================>] 44,316       164KB/s   in 0.3s   

2016-03-22 13:27:37 (164 KB/s) - &#8216;/tmp/dvdcss-NO92PE/libdvdcss.deb&#8217; saved [44316/44316]

(Reading database ... 503310 files and directories currently installed.)
Preparing to unpack .../dvdcss-NO92PE/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
donnie@R103:~$ 

```

---

### Post by ajgreeny on 2016-03-22
Which version of Lubuntu are you using?  The way to add libdvdcss changed from 15.10 onwards to the way you did it; if you have 14.04 you need the instructions lower in the linked page.

---

### Post by Donnie Love on 2016-03-23
It is 14.04. I input the codes. I forgot to copy and paste the results here before I rebooted. No effect.
It acts like the disc drive isn't even there, but I know that drive works because it will play an audio CD.

---

### Post by ajgreeny on 2016-03-23
Which codes did you use; you don't make that clear?

You should only need the two following commands and that should then install libdvdcss for you.
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```
You make no mention of installing libdvdread4.

---

### Post by Donnie Love on 2016-03-24
Sorry. It wanted to reboot and I forgot to paste the codes here. I'll run them again but....

```

donnie@R103:~$ sudo apt-get install libdvdread4
[sudo] password for donnie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  abiword abiword-common apturl apturl-common evolution-data-server-common
  gecko-mediaplayer gnome-mplayer gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers language-selector-gnome libabiword-3.0
  libavfilter3 libcamel-1.2-45 libchamplain-0.12-0 libchamplain-gtk-0.12-0
  libclutter-1.0-0 libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libdiscid0
  libebook-contacts-1.2-0 libedataserver-1.2-18 libfs6 libgbm1 libgda-5.0-4
  libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data
  libgstreamer-plugins-bad1.0-0 libgtkglext1 libical1 libjs-jquery
  libloudmouth1-0 libmusicbrainz3-6 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libots0 libsbc1
  libsdl2-2.0-0 libsrtp0 libtbb2 libtelepathy-glib0 libtidy-0.99-0 libva-glx1
  libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwv-1.2-4 libzeitgeist-2.0-0
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-49 linux-headers-3.19.0-49-generic
  linux-image-3.19.0-25-generic linux-image-3.19.0-49-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-49-generic
  lubuntu-core python-psutil x11-apps x11-session-utils x11-xfs-utils xinit
  xorg zeitgeist-core
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
donnie@R103:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2016-03-24 10:59:12--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-sX429E/Packages&#8217;

100%[======================================>] 3,520       --.-K/s   in 0.002s  

2016-03-24 10:59:13 (1.60 MB/s) - &#8216;/tmp/dvdcss-sX429E/Packages&#8217; saved [3520/3520]

--2016-03-24 10:59:13--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-sX429E/libdvdcss.deb&#8217;

100%[======================================>] 44,316       198KB/s   in 0.2s   

2016-03-24 10:59:13 (198 KB/s) - &#8216;/tmp/dvdcss-sX429E/libdvdcss.deb&#8217; saved [44316/44316]

(Reading database ... 503320 files and directories currently installed.)
Preparing to unpack .../dvdcss-sX429E/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
donnie@R103:~$ 


```

What else could be preventing operation?

---

### Post by ajgreeny on 2016-03-24
Strange, as your terminal output suggests that libdvdcss has been installed and setup without an error.

Sorry but this is beyond me at this point, and I don't know what else to suggest.
I'll keep looking and come back if I find anything else that might help.

EDIT:
Have a look at [http://askubuntu.com/questions/185587/why-does-dvd-playback-still-not-work-after-installing-libdvdcss2](http://askubuntu.com/questions/185587/why-does-dvd-playback-still-not-work-after-installing-libdvdcss2) to see if anything there is of help.

---

### Post by Donnie Love on 2016-03-26
So I'm looking for any solution that will work. I checked the connections, the drive's plugged in and will play an audio CD but won't even recognize a video DVD.

---

### Post by poorguy on 2016-03-26
Hey Donnie Love,

I just ran these two commands one at a time in terminal and did a reboot and they work.
I'm using Ubuntu Mate 14.04 and I am now able to play DVDs in my player.


sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by Donnie Love on 2016-03-26
Here's what I got when I ran those:

```

donnie@R103:~$  sudo apt-get install libdvdread4
[sudo] password for donnie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  abiword abiword-common apturl apturl-common evolution-data-server-common
  gecko-mediaplayer gnome-mplayer gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers language-selector-gnome libabiword-3.0
  libavfilter3 libcamel-1.2-45 libchamplain-0.12-0 libchamplain-gtk-0.12-0
  libclutter-1.0-0 libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libdiscid0
  libebook-contacts-1.2-0 libedataserver-1.2-18 libfs6 libgbm1 libgda-5.0-4
  libgda-5.0-common libgmlib1 libgmtk1 libgmtk1-data
  libgstreamer-plugins-bad1.0-0 libgtkglext1 libical1 libjs-jquery
  libloudmouth1-0 libmusicbrainz3-6 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libots0 libsbc1
  libsdl2-2.0-0 libsrtp0 libtbb2 libtelepathy-glib0 libtidy-0.99-0 libva-glx1
  libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwv-1.2-4 libzeitgeist-2.0-0
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-49 linux-headers-3.19.0-49-generic
  linux-image-3.19.0-25-generic linux-image-3.19.0-49-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-49-generic
  lubuntu-core python-psutil x11-apps x11-session-utils x11-xfs-utils xinit
  xorg zeitgeist-core
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
donnie@R103:~$  sudo /usr/share/doc/libdvdread4/install-css.sh 
--2016-03-27 00:53:45--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-bTLqeJ/Packages&#8217;

100%[======================================>] 3,520       --.-K/s   in 0.02s   

2016-03-27 00:53:46 (185 KB/s) - &#8216;/tmp/dvdcss-bTLqeJ/Packages&#8217; saved [3520/3520]

--2016-03-27 00:53:47--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_i386.deb
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44316 (43K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-bTLqeJ/libdvdcss.deb&#8217;

100%[======================================>] 44,316       156KB/s   in 0.3s   

2016-03-27 00:53:47 (156 KB/s) - &#8216;/tmp/dvdcss-bTLqeJ/libdvdcss.deb&#8217; saved [44316/44316]

(Reading database ... 503320 files and directories currently installed.)
Preparing to unpack .../dvdcss-bTLqeJ/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) over (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...


```

I don't know why it's not working for me, but it's not.

---

### Post by mc4man on 2016-03-26
Open home folder (show hidden files), and _delete the .dvdcss folder_

Then in a terminal

```
export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2

```

```
vlc dvd://  > vlc_output.log 2>&1
```

See what the log in your home folder says

---

### Post by poorguy on 2016-03-26
Hey Donnie Love,

Yeah that is what mine looked like after it installed.

---

### Post by Donnie Love on 2016-03-28
I don't see a folder called .dvdcss even with hidden files shown. Could it be somewhere other than home folder or named something else? I looked around, don't see it anywhere.

No visible output from the codes I entered. VLC opened, but still won't work.

vlc_output.log reads:
```

[0x8862928] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.1
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x8902f00] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb0301b70] main input error: open of `dvd://' failed
libdvdnav: Using dvdnav version 4.2.1
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x892ae50] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb0301b70] main input error: open of `dvd://' failed
libdvdnav: Using dvdnav version 4.2.1
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdcss debug: opening target `/dev/sr0'
libdvdcss debug: using libc for access
libdvdcss debug: cannot open /dev/sr0 (No medium found)
libdvdcss error: failed to open device
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0xb0303ff0] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb0301b70] main input error: open of `dvd:///dev/sr0' failed

```

What's next?

---

### Post by mc4man on 2016-03-28
put a dvd in the drive, let the drive settle & run
```
sudo lshw -c disk
```
Post what's in any *-cdrom section(s)

If the dvd filesystem is not being detected then obviously no player or libdvdcss can work

---

### Post by Donnie Love on 2016-03-28
```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-H663C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: UO00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

It looks like it says "no disc". That's incorrect. There is a disc in there. Apollo 13 with Tom Hanks. I have also tried different discs.

---

### Post by mc4man on 2016-03-28
> **Donnie Love said:**
> ```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-H663C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: UO00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

It looks like it says "no disc". That's incorrect. There is a disc in there. Apollo 13 with Tom Hanks. I have also tried different discs.
It's physically incorrect but  as far as the system there is nothing in the drive so nothing to play, ect.
Do you have any other optical media available to test like a data dvd/cd or an audio cd?

---

### Post by Donnie Love on 2016-03-28
It plays audio CDs just fine. (Not with Rhythmbox of course, but that's a separate thread.)

---

### Post by Donnie Love on 2016-03-29
So, can any conclusion be drawn? Is there any way to get it to work?

---

### Post by mc4man on 2016-03-29
> **Donnie Love said:**
> So, can any conclusion be drawn? Is there any way to get it to work?

You'll need to try some other dvds, preferably a data dvd though some other commercial dvd video discs would be ok I guess. 
dvd drives have separate lens for dvd & cd media. So overall the drive still works & works with cd's. 
You'll need to try other dvd discs to confirm the condition of the dvd lens, ect.

---

### Post by Donnie Love on 2016-03-29
Doesn't work for data disc either. I rarely use discs for data, only videos.
When I play an audio CD, it still doesn't show up in the file manager.
So you think the hardware is shot then?

---

### Post by mc4man on 2016-03-29
> **Donnie Love said:**
> Doesn't work for data disc either. I rarely use discs for data, only videos.
When I play an audio CD, it still doesn't show up in the file manager.
So you think the hardware is shot then?
I would see your options as such,
Try cleaning the dvd device. Assuming a laptop,  if the loading tray comes out, (vs a slot loader) then it should be easy to try.
Get a new dvd device, probably more hassle than it's worth. Especially in regards to the faceplate.
Buy an external dvd device, not very expensive, $20 - 30 at a big box or amazon
Keep trying, maybe every once & a while a disk will play.

---

### Post by Donnie Love on 2016-03-29
It's a desktop. I need the disc to play regularly. I might have another drive, an older one, somewhere. I never had a problem until I "up"graded to this version of Lubuntu.

---

