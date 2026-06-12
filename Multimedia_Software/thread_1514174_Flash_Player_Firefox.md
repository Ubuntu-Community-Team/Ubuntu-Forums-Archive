---
title: "Flash Player Firefox"
date: 2010-06-20
forum: Multimedia Software
---

### Post by jeffdunn on 2010-06-20
Hi,
After re-installing ubuntu 8.04, I have lost my ability to use the myspace music player (which I use a lot). I was also unable to play flash movies so, I installed the flash plugin like this:
sudo apt-get install flashplugin-nonfree
based on advice I found by googling. Now I can watch movies, but the problem with the myspace player persists. There is a message where the player should be that says
**Get Flash now!**

**In order to listen or view this content you will have to upgrade your version of Flash.**

with a button below that will allow me to download a tarball, but I don't really know what to do with the tarball.
I'm hoping there is a simple fix, because all I did was reinstall the same OS as I had before and 24 hours ago I could watch flash movies as well as listen to my own and other peoples music on myspace. I know that flash works, but I don't know how to install the right plugin, I guess. Please help politely if you can.
Cheers,
Jeff

---

### Post by wojox on 2010-06-20
try this site [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by jeffdunn on 2010-06-21
Thanx for the response.

I tried this

sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so

as recomended on the site you mentioned. Restarted the computer and the same problem still exists.
The strange thing is that all I did initially is to reinstall 8.04. The first time I installed I did something in add/remove programs that worked. Up until a few days ago, before the reinstall, I had no problems with myspace.

Any more suggestions? I'd really like to solve this.
Cheers,
Jeff

---

### Post by andrea000 on 2010-06-21
on 8.04 i had a lot of problems myself.I don't know but
for 9.10 and 10.04 flash from the repo's always crashed
firefox for me i found that downloading flash from adobe's
website stopped it from doing that.That may help you.

---

### Post by jeffdunn on 2010-06-21
If I click on the link on myspace (Get Adobe FlashPlayer) it downloads a file called install_flash_player _10_linux.tar.gz from [http://fpdownload.macromedia.com](http://fpdownload.macromedia.com) and it opens up in the archive manager. I've just done that and the archive manager put a file called libflashplayer.so on my desktop. The problem is I don't know what to do next. What did you do after downloading flash from adobe?

---

### Post by jeffdunn on 2010-06-21
Here is what is currently installed as plugins in firefox on my system

**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 9.0 r277   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  **Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Demo Print Plugin for unix/linux**

 File name:  libunixprintplugin.so The demo print plugin for unix.   MIME Type Description Suffixes Enabled    application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes  **Totem Web Browser Plugin 2.22.1**

 File name:  libtotem-basic-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-ogg - ogg Yes   application/ogg Ogg multimedia ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex - anx Yes   audio/annodex - axa Yes   video/annodex - axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes  **Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)**

 File name:  libtotem-complex-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    audio/x-pn-realaudio-plugin RealAudio document rpm Yes  **VLC Multimedia Plugin (compatible Totem 2.22.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin unknown 
Yes   application/vlc unknown 
Yes   video/x-google-vlc-plugin unknown 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Microsoft ASX playlist wmv Yes   video/x-ms-wm ASF video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.22.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime QuickTime image pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **iTunes Application Detector**

 File name:  librhythmbox-itms-detection-plugin.so This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes
I'm not sure if that will help anyone find an answer for me but I thought it couldn't hurt to supply the info.

---

### Post by andrea000 on 2010-06-21
download flash player for linux it should be a deb file
and click it on 8.04 i think you need to install debconfig
for 8.04 but i could be wrong on that.in the dropdown box
select the .deb for ubuntu 8.04 Here is the adobe [link]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

---

### Post by jeffdunn on 2010-06-21
I solved the problem. What I did was modify the script that was suggested on the link that you originally posted above. I noticed when I looked at it again that the line

sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so

was the same file I had just downloaded from adobe.

so I did this

sudo apt-get purge flashplugin-nonfree
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo cp $HOME/Desktop/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so

When I opened the browser again, everything flash including the player on myspace was working perfectly. Thank you so much for leading me to that site, because I'm no geek and barely understand the command line, but I just really learned something from this experience and your kind assistance. Thanx as well for recommending that I just go ahead and download from adobe.
I couldn't have fixed this without you!!!!
Cheers,
Jeff

---

