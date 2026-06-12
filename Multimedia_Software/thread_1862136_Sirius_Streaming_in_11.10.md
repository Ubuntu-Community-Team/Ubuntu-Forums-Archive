---
title: "Sirius Streaming in 11.10"
date: 2011-10-16
forum: Multimedia Software
---

### Post by teejay17 on 2011-10-16
Hi all,
I used to be able to stream Sirius Internet radio no problem using older versions of Ubuntu and Linux Mint, using Mplayer and the Gecko plugin. 
Recently I freshly installed 11.10 and now when I go to Sirius I cannot get Mplayer to open up and play streams.
Does anyone know what I need to turn on/off/download, or otherwise rectify in order to get Sirius working? 
These are my enabled plugins in Firefox: 
```
  **Enabled plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Find updates for installed plugins at  [mozilla.com/plugincheck]("http://www.mozilla.com/plugincheck/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Shockwave Flash**

 File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 11.0 r1   MIME Type Description Suffixes    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl  **IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1))**

 File:  IcedTeaPlugin.soVersion:   The [IcedTea-Web Plugin]("http://icedtea.classpath.org/wiki/IcedTea-Web") executes Java applets.   MIME Type Description Suffixes    application/x-java-vm IcedTea class,jar   application/x-java-applet IcedTea class,jar   application/x-java-applet;version=1.1 IcedTea class,jar   application/x-java-applet;version=1.1.1 IcedTea class,jar   application/x-java-applet;version=1.1.2 IcedTea class,jar   application/x-java-applet;version=1.1.3 IcedTea class,jar   application/x-java-applet;version=1.2 IcedTea class,jar   application/x-java-applet;version=1.2.1 IcedTea class,jar   application/x-java-applet;version=1.2.2 IcedTea class,jar   application/x-java-applet;version=1.3 IcedTea class,jar   application/x-java-applet;version=1.3.1 IcedTea class,jar   application/x-java-applet;version=1.4 IcedTea class,jar   application/x-java-applet;version=1.4.1 IcedTea class,jar   application/x-java-applet;version=1.4.2 IcedTea class,jar   application/x-java-applet;version=1.5 IcedTea class,jar   application/x-java-applet;version=1.6 IcedTea class,jar   application/x-java-applet;jpi-version=1.6.0_50 IcedTea class,jar   application/x-java-bean IcedTea class,jar   application/x-java-bean;version=1.1 IcedTea class,jar   application/x-java-bean;version=1.1.1 IcedTea class,jar   application/x-java-bean;version=1.1.2 IcedTea class,jar   application/x-java-bean;version=1.1.3 IcedTea class,jar   application/x-java-bean;version=1.2 IcedTea class,jar   application/x-java-bean;version=1.2.1 IcedTea class,jar   application/x-java-bean;version=1.2.2 IcedTea class,jar   application/x-java-bean;version=1.3 IcedTea class,jar   application/x-java-bean;version=1.3.1 IcedTea class,jar   application/x-java-bean;version=1.4 IcedTea class,jar   application/x-java-bean;version=1.4.1 IcedTea class,jar   application/x-java-bean;version=1.4.2 IcedTea class,jar   application/x-java-bean;version=1.5 IcedTea class,jar   application/x-java-bean;version=1.6 IcedTea class,jar   application/x-java-bean;jpi-version=1.6.0_50 IcedTea class,jar  **Gnome Shell Integration**

 File:  libgnome-shell-browser-plugin.soVersion:   This plugin provides integration with Gnome Shell for live extension  enabling and disabling. It can be used only by extensions.gnome.org   MIME Type Description Suffixes    application/x-gnome-shell-integration Gnome Shell Integration Dummy Content-Type 
 **RealPlayer 9**

 File:  gecko-mediaplayer-rm.soVersion:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   MIME Type Description Suffixes    audio/x-pn-realaudio RealAudio ram,rm   application/vnd.rn-realmedia RealMedia rm   application/vnd.rn-realaudio RealAudio ra,ram   video/vnd.rn-realvideo RealVideo rv   audio/x-realaudio RealAudio ra   audio/x-pn-realaudio-plugin RealAudio rpm   application/smil SMIL smil  **QuickTime Plug-in 7.6.9**

 File:  gecko-mediaplayer-qt.soVersion:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   MIME Type Description Suffixes    video/quicktime Quicktime mov   video/x-quicktime Quicktime mov   image/x-quicktime Quicktime mov   video/quicktime Quicktime mp4   video/quicktime Quicktime - Session Description Protocol sdp   application/x-quicktimeplayer Quicktime mov  **mplayerplug-in is now gecko-mediaplayer 1.0.4**

 File:  gecko-mediaplayer.soVersion:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   MIME Type Description Suffixes    audio/x-mpegurl MPEG Playlist m3u   video/mpeg MPEG mpg,mpeg   audio/mpeg MPEG mpg,mpeg   video/x-mpeg MPEG mpg,mpeg   video/x-mpeg2 MPEG2 mpv2,mp2ve   audio/mpeg MPEG mpg,mpeg   audio/x-mpeg MPEG mpg,mpeg   audio/mpeg2 MPEG audio mp2   audio/x-mpeg2 MPEG audio mp2   audio/mp4 MPEG 4 audio mp4   audio/x-mp4 MPEG 4 audio mp4   video/mp4 MPEG 4 Video mp4   video/x-m4v MPEG 4 Video m4v   video/3gpp MPEG 4 Video mp4,3gp   audio/mpeg3 MPEG audio mp3   audio/x-mpeg3 MPEG audio mp3   audio/x-mpegurl MPEG url m3u   audio/mp3 MPEG audio mp3   application/x-ogg Ogg Vorbis Media ogg,oga,ogm   application/ogg Ogg Vorbis Media ogg,oga,ogm   audio/x-ogg Ogg Vorbis Audio ogg,oga   audio/ogg Ogg Vorbis Audio ogg,oga   video/x-ogg Ogg Vorbis Video ogg,ogm   video/ogg Ogg Vorbis Video ogg,ogm   application/x-vlc-plugin VLC plug-in vlc   application/x-google-vlc-plugin Google VLC plug-in 
  audio/flac FLAC Audio flac   audio/x-flac FLAC Audio flac   video/fli FLI animation fli,flc   video/x-fli FLI animation fli,flc   video/x-flv Flash Video flv   video/flv Flash Video flv   video/vnd.vivo VivoActive viv,vivo   audio/x-matroska Matroska Audio mka   video/x-matroska Matroska Video mkv   application/x-nsv-vp3-mp3 Nullsoft Streaming Video nsv   audio/x-mod Soundtracker mod   audio/x-aiff AIFF Audio aif   audio/basic Basic Audio File au,snd   audio/x-basic Basic Audio File au,snd   audio/x-scpls Shoutcast Playlist pls   video/x-mng Multiple-Image Network Graphics mng   audio/webm WEBM audio File webm   audio/x-webm WEBM audio File webm   video/webm WEBM video File webm   video/x-webm WEBM video File webm  **Windows Media Player Plug-in**

 File:  gecko-mediaplayer-wmp.soVersion:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   MIME Type Description Suffixes    application/asx Media Files *   video/x-ms-asf-plugin Media Files *   video/x-msvideo AVI avi,*   video/msvideo AVI avi,*   application/x-mplayer2 Media Files *   video/x-mplayer2 Media Files *   application/x-ms-wmv Microsoft WMV video wmv,*   video/x-ms-asf Media Files asf,asx,*   video/x-ms-asx Media Files asx,*   video/x-ms-wm Media Files wm,*   video/x-ms-wmv Microsoft WMV video wmv,*   audio/x-ms-wmv Windows Media wmv,*   video/x-ms-wmp Windows Media wmp,*   application/x-ms-wmp Windows Media wmp,*   video/x-ms-wvx Windows Media wvx,*   audio/x-ms-wax Windows Media wax,*   audio/x-ms-wma Windows Media wma,*   application/x-drm-v2 Windows Media asx,*   audio/wav Microsoft wave file wav,*   audio/x-wav Microsoft wave file wav,*  **DivX Browser Plug-In**

 File:  gecko-mediaplayer-dvx.soVersion:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   MIME Type Description Suffixes    video/divx DivX Media Format divx   video/vnd.divx DivX Media Format divx   
   
```

---

### Post by Pjotr123 on 2011-10-17
Try a switch to Oracle (Sun) Java JRE:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Maybe that'll do the job. :)

---

### Post by teejay17 on 2011-10-17
> **Pjotr123 said:**
> Try a switch to Oracle (Sun) Java JRE:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Maybe that'll do the job. :)

Okay thanks, I will give this a try. 
Am I encountering this problem because Sun Java is no longer included in the repositories/software centre? If I remember correctly, on older installations (the ones that played Sirius), Sun Java was available in the repositories, no?

---

### Post by wolfen69 on 2011-10-17
I stream Sirius no problem. Just enable the Medibuntu and Partners repo and do:
```
sudo apt-get install non-free-codecs
```

---

### Post by darreno1 on 2011-12-15
I got Sirius to stream using Firefox 8 in Ubuntu 11.10 (this is via the online player on the sirius.com website).  At first the player would not work correctly so I uninstalled the adobe mozilla flash plugin and installed the flash 10 player/plugin that can be found in the Ubuntu Software Center. After I installed that plugin, everything worked like a charm!

Additional info:
I'm running a clean Ubuntu 11.10 installation with all the updates installed.
Firefox version is 8 (this was updated by the automated update).

---

