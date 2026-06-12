---
title: "Kaffeine won't play encrypted DVDs"
date: 2008-10-19
forum: Multimedia Software
---

### Post by checho4 on 2008-10-19
When I put in any encrypted DVD, I try to open it with Kaffeine, VLC, KMPlayer, and MPlayer, but nothing happens.  The DVD shows up on the desktop and mounts correctly.  I can't even open the VIDEO_TS folder and play the media through there.

I'm running Kubuntu Hardy 8.04 32-bit.  I used to play DVDs on 7.10, but that is no longer possible after the upgrade.

I have the kubuntu-restricted-extras installed, as well as the ubuntu-restricted-extras.  I've also checked my region settings and ensured the setting to be "North America".

Here is the output from Kaffeine:

```

libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/sda6 mounted on / for CSS authentication
libdvdread: Could not open input: Permission denied
libdvdread: Can't open /dev/sda6 for reading
libdvdread: Device /dev/sda6 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/michelle/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2C2C72B1
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/michelle/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

```

Any help is greatly appreciated.

---

### Post by hansdown on 2008-10-19
Hi checho4.

You should install libdvdcss2 from the synaptic package manager.

---

### Post by Yellow Pasque on 2008-10-19
hansdown, IIRC Ubuntu doesn't provide libdvdcss2 (copyright issues). Medibuntu has the package available: [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

---

### Post by hansdown on 2008-10-20
> **Temüjin said:**
> hansdown, IIRC Ubuntu doesn't provide libdvdcss2 (copyright issues). Medibuntu has the package available: [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

It seems to be in the synaptic package manager.

[http://ubuntuforums.org/attachment.php?attachmentid=88919&stc=1&d=1224477350](http://ubuntuforums.org/attachment.php?attachmentid=88919&stc=1&d=1224477350)

---

### Post by Yellow Pasque on 2008-10-20
> **hansdown said:**
> It seems to be in the synaptic package manager.

[http://ubuntuforums.org/attachment.php?attachmentid=88919&stc=1&d=1224477350](http://ubuntuforums.org/attachment.php?attachmentid=88919&stc=1&d=1224477350)
Synaptic shows that package because you have it installed, but Ubuntu does not provide it in the repositories.

---

### Post by checho4 on 2008-10-20
Yes!  This worked perfectly!  Thank you very much!!!

I feel like I didn't have to do this for earlier versions of Ubuntu.  Is this new to Hardy?  I did a clean install of 7.04 and then upgraded to 7.10 and don't remember ever installing anything more than the kubuntu-restricted-extras.  However, I did a clean install of 8.04 and hadn't been able to view DVDs since then.

---

### Post by AugustinZ on 2009-01-20
My solution to the problem on Kubuntu (Ubuntu) is following:

0.) Open a command-line :)
1.) Add medibuntu repositories into /etc/apt/sources.list
2.) Download and install libdvdcss2 ```
sudo apt-get install libdvdcss2
```
3.) You should also install w32codecs ```
sudo apt-get install w32codecs
``` and (k/x/edu)ubuntu-restricted-extras ```
sudo apt-get install ubuntu-restricted-extras
```
5.) In some cases the error may be also caused by wrong setting in the xine parametres:
 a) Open Kaffeine
 b) Go to Settings --> xine Engine Parametres --> Media --> dvd.device
 c) The default setting is usually /dev/dvd
 d) Change it to /dev/dvd1 or to /dev/dvd2 or /dev/scd0 - you have to try which works for you

---

### Post by valerietheblonde on 2011-10-23
That solution worked for me and Ubuntu 11.10 and movie player. Thank you!

from a new to linux girl

---

