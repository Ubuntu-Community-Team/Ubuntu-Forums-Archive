---
title: "Banshee and Rhythmbox Issues"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by ryanchang on 2008-03-10
Hello,

I'm a relatively new Linux user and I'm having some problems running Banshee and Rhythmbox in GNOME on Gutsy Gibbon. First, Banshee stopped loading and crashed at the "Loading User Interface" part of its load. I uninstalled then reinstalled it--no change. Then, I got frustrated and just opted for Rhythmbox. Now Rhythmbox just loads a fraction of my music library before ceasing to function. Help! I have no idea what to do!


Ryan

---

### Post by 6205 on 2008-03-10
uhm....run banshee or rhythmbox from terminal and report error messages here...

---

### Post by SRGT. DeGreene on 2008-03-10
I recommend the small XMMS player. you can download it in the add remove programs thingy. it has alot of skins to make it pretty and ive never had any problems with it. you can get themes for it and other stuff here: [http://www.gnome-look.org/]("http://www.gnome-look.org/")

---

### Post by ajgreeny on 2008-03-10
Try a "Completely remove" in synaptic or purge with apt-get and see if that helps; it will remove all your settings for the apps but may be what is needed

---

### Post by ryanchang on 2008-03-10
This is what happens when I try to purge banshee...

apt-get --purge remove banshee
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


?

---

### Post by 6205 on 2008-03-10
[COLOR="Red"]sudo[/COLOR] apt-get --purge remove banshee

btw. when you uninstall Banshee and Rhythmbox, delete also hidden folders in your home directory, related to those players with potential old/corrupted config files and then download and re-install Gutsy's Rhythmbox 0.11.3 from GetDeb [http://getdeb.net/search.php?keywords=rhythmbox](http://getdeb.net/search.php?keywords=rhythmbox)

---

### Post by ryanchang on 2008-03-11
Thanks for the help! Did the trick.

On a completely unrelated note, Firefox won't play MySpace music players or display any Flash movies. I've installed the flash player multiple times, but no luck. Any ideas?

---

### Post by 6205 on 2008-03-11
type in the Firefox adress bar [COLOR="Red"]about:plugins[/COLOR] and copy/paste here that text

---

### Post by ryanchang on 2008-03-11
```
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see http://www.gnu.org/software/gnash. Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v
```

---

### Post by 6205 on 2008-03-11
Uhm...well...

I have nothing agains GNASH project, but maybe you should uninstall this open source alternative and instead of that install a real Flash player 9 from Adobe.

Enter in terminal [COLOR="Red"]sudo apt-get remove gnash[/COLOR] and eventually [COLOR="Red"]sudo apt-get autoremove[/COLOR] to clean some potentially unecessarry files from your system.

After that download and install *. deb file with latest flashplugin from this link [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)



Now should all Flash videos work, of course only if you have all necessary codecs installed. If it's still not working, try to install gstreamer codecs (because i see that you use default Totem Mozilla browser plugin, hopefully with Gstreamer backend, not xine :) - you [COLOR="Red"]must[/COLOR] have enabled universe and multiverse for next step, or it will not work [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Also adding medibuntu multimedia repositories is very useful [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f) and after that proceed with >>>

[COLOR="Red"]
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-good[/COLOR]

If you already have some of them installed, system will notify you and install only missing ones anyway, so there is no danger to install them all...

---

