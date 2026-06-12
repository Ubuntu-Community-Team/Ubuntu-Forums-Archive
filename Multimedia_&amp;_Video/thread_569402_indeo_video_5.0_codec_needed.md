---
title: "indeo video 5.0 codec needed"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by Ituxlinux on 2007-10-07
Hi there;

My web cam produces videos .avi using "Indeo  Video 5.0" format, so it is not possible to watch the videos made using that web cam. Does anybody here know a good codec I can use in Xine or mplayer? 
The web cam is Logitech QuickCam Fusion, and the videos where made in WinXp.

Any Idea??

Thanks

You can see a example of this kind of videos here: [[COLOR="RoyalBlue"][SIZE="3"]video IV50[/SIZE][/COLOR]]("http://www.geocities.com/itux_linux/")

---

### Post by adamorjames on 2007-10-07
You can try getting the win32 codecs for mplayer I found an rpm... [http://rpmfind.net/linux/RPM/falsehope/home/rathann/apt/7.3/RPMS.stable/mplayer-codecs-win32-indeo-2.0-1.i386.html](http://rpmfind.net/linux/RPM/falsehope/home/rathann/apt/7.3/RPMS.stable/mplayer-codecs-win32-indeo-2.0-1.i386.html)
That doesn't help much cept it proves that there is a way to play Indeo video in Linux. 
Here is all the codecs for mplayer from mplayer. [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)
Maybe you can try getting the win codecs from there working with your mplayer.
Sorry I'm not of more help.

---

### Post by wolfen69 on 2007-10-07
i believe you could use "alien" to change the rpm to a deb, then install via dpkg. it's in synaptic.

---

### Post by adamorjames on 2007-10-07
I made it into a deb and then installed it but it didn't help any. Maybe you will have better luck.
EDIT: I found the files mplayer wants and I put them in the right directory but now it is complaing about ELF file data.

---

### Post by RomeReactor on 2007-10-07
Hi. Here's a [direct link]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu2_i386.deb") to the Medibuntu w32codecs deb package. Once it downloads, you install it by double click ing the .deb file.

---

### Post by Ituxlinux on 2007-10-07
Actully, I did have installed that codecs already, but they didn't work for that kind of avi. 
Any other Idea?

---

### Post by RomeReactor on 2007-10-07
Perhaps installing **libavifile-0.7c2** can help; from the package's description providedby Synaptic:
> Library that allows programs to read and write compressed
AVI files (Indeo Video, DivX ;-), etc.) under x86 Linux.
(De)Compression is performed with various audio/video plugins
(FFMpeg, MAD, Vorbis, Win32, ...).
Formats like mpeg, mov are partly supported.
For more info about usage of Win32, Lame and OpenDivX plugin
see README.debian.

Do a search in Synaptic for **avifile**. There are other related packages--including an Avi Player.

---

### Post by adamorjames on 2007-10-07
> **RomeReactor said:**
> Perhaps installing **libavifile-0.7c2** can help; from the package's description providedby Synaptic:


Do a search in Synaptic for **avifile**. There are other related packages--including an Avi Player.

Once you get that you need to get the win32 archive from their site and extract it to /usr/lib/win32 and then the vid will play in mplayer but it will still show an error.

EDIT: ok here is the link to the archive - [http://avifile.sourceforge.net/binaries-010122.zip](http://avifile.sourceforge.net/binaries-010122.zip)

---

### Post by Ituxlinux on 2007-10-08
Thank guys!!

I did update Mplayer with all the extra lib, including libavifile-0.7c2 and now it is working pretty well. :popcorn:

---

### Post by adamorjames on 2007-10-08
> **Ituxlinux said:**
> Thank guys!!

I did update Mplayer with all the extra lib, including libavifile-0.7c2 and now it is working pretty well. :popcorn:

Great! Glad to be of help :)

---

### Post by kung fu buntu on 2007-12-16
I already have the latest version of mplayer and libavifile installed. However I can't view the video in any player.
Can you view this video
[http://server.cs.ucf.edu/~vision/projects/triview/collision01.avi](http://server.cs.ucf.edu/~vision/projects/triview/collision01.avi)

There was another thread here that mentioned gstreamer... IIRC there are 2 main "streamers?": mplayer and gstreamer. How can I set one or another in a player, like vlc (in order to see if one of them works)

Thanks

---

### Post by Torqumada286 on 2008-03-11
> **adamorjames said:**
> Once you get that you need to get the win32 archive from their site and extract it to /usr/lib/win32 and then the vid will play in mplayer but it will still show an error.

EDIT: ok here is the link to the archive - [http://avifile.sourceforge.net/binaries-010122.zip](http://avifile.sourceforge.net/binaries-010122.zip)

I am using 64bit gutsy, but I can't seem to get the files to extract to /usr/lib/win32.  Any ideas?

Torqumada

---

### Post by lunnjd on 2008-05-10
Hi, I am having similar problems. I cannot open Indeo 5 videos as well (the one posted above will not play). I am using Xubuntu 8.04 which comes with Totem Movie Player using GStreamer 0.10.18. Have installed medibuntu and codecs to /usr/lib/codecs as suggested. When opening the file Totem asks to search for codecs, it cannot find one and says that there is an error it cannot play indeo files without the codec. VLC player will not open the file either. I'm pretty sure these vids were working in 7.10. Another related thing might be that Thunar no longer makes thumbnails for any of my video files. Any thoughts?

Edit: Totem with Xine backend will open these files.

---

### Post by kung fu buntu on 2008-06-27
> **Torqumada286 said:**
> I am using 64bit gutsy, but I can't seem to get the files to extract to /usr/lib/win32.  Any ideas?

Torqumada

I'm also running a 64 bits system.
That is probably why win32 codecs don't work. If you download both packages win32codecs and win64codecs and compare them... you'll see the difference.

Nonetheless, I have untarballed the win32codecs into /usr/lib/codecs and I can't see the video neither with mplayer nor totem.

Do I have to configure any plugins path?


edit: totem-xine doesn't work for me :(




EDIT2: fixed the problem with my ia32 chroot

---

