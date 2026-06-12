---
title: "Is there anything wrong with my mimeapps.list?"
date: 2021-10-13
forum: Multimedia Software
---

### Post by hari-seldon2 on 2021-10-13
Is there anything wrong with my mimeapps.list?  I have posted it below.

I had a bug mentioned here:
_**Rhythmbox cannot be set as music default player **_
[https://ubuntuforums.org/showthread.php?t=2461501&p=14035564#post14035564](https://ubuntuforums.org/showthread.php?t=2461501&p=14035564#post14035564)

_**My Settings -> Default Applications has Video to play videos and  Rhythmbox to play music, but when I double-click on m4a and mp3 for example it didn't work.  My fix was:**_
SOLUTION: take out the big hammer on mimeapps.list
CHANGE:
audio/m4a=org.gnome.Totem.desktop
audio/mp3=org.gnome.Totem.desktop
TO:
audio/m4a=rhythmbox.desktop
audio/mp3=rhythmbox.desktop
[U][B]
Is there a better way to do that?  I tried this but double-clicking stopped opening Rhythmbox and opened Videos again so there seems to be something wrong with GNOME:[/B][/U]
audio/m4a=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/mp3=org.gnome.Totem.desktop;rhythmbox.desktop;

The Nautilus File  Manager when I right-click a music file the File Manager says that Video  is the default music player and when I click "Set as default" Rhythmbox  nothing happens.  When I click "Reset to system defaults" it keeps  Video as the default music player and does not sync up with Settings  -> Default Applications that has Video to play videos and Rhythmbox  to play music.

When I use the GNOME File Manager (replacement to Nautilus) and  right-click on the music file I can right click the Video and can  sometimes make it forget to use Video to play that music file type and  when I double-click the music file it still opens in Video.  I can get  GNOME File Manager to play Rhythmbox by right-clicking and selecting  Rhythmbox but it does not remember that choice when I double-click.

_**/home/user/.config/mimeapps.list**_
[Added Associations]
application/octet-stream=org.gnome.gedit.desktop;org.gnome.Totem.desktop;vlc_vlc.desktop;keepassxc_keepassxc.desktop;
video/mpeg=vlc_vlc.desktop;org.gnome.Totem.desktop;
video/mp4=vlc_vlc.desktop;org.gnome.Totem.desktop;
application/x-desktop=firefox.desktop;
application/vnd.debian.binary-package=snap-store_snap-store.desktop;snap-store_ubuntu-software-local-file.desktop;
image/png=shotwell-viewer.desktop;
text/x-apt-sources-list=org.gnome.gedit.desktop;
text/plain=sublime-text_subl.desktop;notepad-plus-plus_notepad-plus-plus.desktop;
text/x-r-markdown=org.gnome.gedit.desktop;rstudio.desktop;
text/x-r-source=org.gnome.gedit.desktop;rstudio.desktop;
application/epub+zip=calibre-ebook-viewer.desktop;calibre-gui.desktop;
audio/x-flac=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-it=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-mod=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-mp3=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-mpeg=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-mpegurl=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-s3m=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-scpls=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-stm=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-vorbis=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/x-xm=org.gnome.Totem.desktop;rhythmbox.desktop;
text/calendar=firefox.desktop;
application/x-shellscript=org.gnome.gedit.desktop;
text/x-python=org.thonny.Thonny.desktop;
text/csv=org.gnome.gedit.desktop;
application/mxf=org.gnome.Totem.desktop;
application/ogg=org.gnome.Totem.desktop;
application/ram=org.gnome.Totem.desktop;
application/sdp=org.gnome.Totem.desktop;
application/smil+xml=org.gnome.Totem.desktop;
application/vnd.apple.mpegurl=org.gnome.Totem.desktop;
application/vnd.ms-asf=org.gnome.Totem.desktop;
application/vnd.ms-wpl=org.gnome.Totem.desktop;
application/vnd.rn-realmedia=org.gnome.Totem.desktop;
application/x-extension-m4a=org.gnome.Totem.desktop;
application/x-extension-mp4=org.gnome.Totem.desktop;
application/x-flac=org.gnome.Totem.desktop;
video/x-flv=org.gnome.Totem.desktop;
application/x-matroska=org.gnome.Totem.desktop;
application/x-netshow-channel=org.gnome.Totem.desktop;
application/x-quicktime-media-link=org.gnome.Totem.desktop;
application/x-shorten=org.gnome.Totem.desktop;
application/x-smil=org.gnome.Totem.desktop;
application/xspf+xml=org.gnome.Totem.desktop;
video/3gpp=org.gnome.Totem.desktop;
video/3gpp2=org.gnome.Totem.desktop;
image/vnd.rn-realpix=org.gnome.Totem.desktop;
image/x-pict=org.gnome.Totem.desktop;
misc/ultravox=org.gnome.Totem.desktop;
text/x-google-video-pointer=org.gnome.Totem.desktop;
video/dv=org.gnome.Totem.desktop;
video/x-msvideo=org.gnome.Totem.desktop;
video/x-flic=org.gnome.Totem.desktop;
video/mp2t=org.gnome.Totem.desktop;
video/ogg=org.gnome.Totem.desktop;
video/quicktime=org.gnome.Totem.desktop;
video/vnd.vivo=org.gnome.Totem.desktop;
video/vnd.mpegurl=org.gnome.Totem.desktop;
video/vnd.rn-realvideo=org.gnome.Totem.desktop;
video/webm=org.gnome.Totem.desktop;
video/x-anim=org.gnome.Totem.desktop;
video/x-flc=org.gnome.Totem.desktop;
video/x-matroska=org.gnome.Totem.desktop;
video/x-mjpeg=org.gnome.Totem.desktop;
video/x-ms-asx=org.gnome.Totem.desktop;
video/x-ms-wmv=org.gnome.Totem.desktop;
video/x-nsv=org.gnome.Totem.desktop;
video/x-ogm+ogg=org.gnome.Totem.desktop;
video/x-theora+ogg=org.gnome.Totem.desktop;
video/x-totem-stream=org.gnome.Totem.desktop;
x-content/video-dvd=org.gnome.Totem.desktop;
x-scheme-handler/pnm=org.gnome.Totem.desktop;
x-scheme-handler/mms=org.gnome.Totem.desktop;
x-scheme-handler/net=org.gnome.Totem.desktop;
x-scheme-handler/rtp=org.gnome.Totem.desktop;
x-scheme-handler/rtmp=org.gnome.Totem.desktop;
x-scheme-handler/rtsp=org.gnome.Totem.desktop;
x-scheme-handler/mmsh=org.gnome.Totem.desktop;
x-scheme-handler/uvox=org.gnome.Totem.desktop;
x-scheme-handler/icy=org.gnome.Totem.desktop;
x-scheme-handler/icyx=org.gnome.Totem.desktop;
audio/mp4=org.gnome.Totem.desktop;
audio/mpeg=rhythmbox.desktop;
application/json=org.gnome.gedit.desktop;

[Removed Associations]
application/x-mswinurl=firefox.desktop;
audio/mpeg=org.gnome.Totem.desktop;

[Default Applications]
application/octet-stream=keepassxc_keepassxc.desktop
application/x-desktop=firefox.desktop
audio/x-vorbis+ogg=rhythmbox.desktop
audio/3gpp=org.gnome.Totem.desktop
audio/3gpp2=org.gnome.Totem.desktop
audio/aac=org.gnome.Totem.desktop
audio/ac3=org.gnome.Totem.desktop
audio/AMR=org.gnome.Totem.desktop
audio/AMR-WB=org.gnome.Totem.desktop
audio/basic=org.gnome.Totem.desktop
audio/dv=org.gnome.Totem.desktop
audio/eac3=org.gnome.Totem.desktop
audio/flac=org.gnome.Totem.desktop
audio/m4a=rhythmbox.desktop
audio/midi=org.gnome.Totem.desktop
audio/mp1=org.gnome.Totem.desktop
audio/mp2=org.gnome.Totem.desktop
audio/mp3=rhythmbox.desktop
audio/mpegurl=org.gnome.Totem.desktop
audio/mpg=org.gnome.Totem.desktop
audio/ogg=org.gnome.Totem.desktop
audio/opus=org.gnome.Totem.desktop
audio/prs.sid=org.gnome.Totem.desktop
audio/scpls=org.gnome.Totem.desktop
audio/vnd.rn-realaudio=org.gnome.Totem.desktop
audio/wav=org.gnome.Totem.desktop
audio/webm=org.gnome.Totem.desktop
audio/x-aac=org.gnome.Totem.desktop
audio/x-aiff=org.gnome.Totem.desktop
audio/x-ape=org.gnome.Totem.desktop
audio/x-flac=rhythmbox.desktop
audio/x-gsm=org.gnome.Totem.desktop
audio/x-it=rhythmbox.desktop
audio/x-m4a=rhythmbox.desktop
audio/x-m4b=org.gnome.Totem.desktop
audio/x-matroska=org.gnome.Totem.desktop
audio/x-mod=rhythmbox.desktop
audio/x-mp1=org.gnome.Totem.desktop
audio/x-mp2=org.gnome.Totem.desktop
audio/x-mp3=rhythmbox.desktop
audio/x-mpg=org.gnome.Totem.desktop
audio/x-mpeg=rhythmbox.desktop
audio/x-mpegurl=rhythmbox.desktop
audio/x-ms-asf=org.gnome.Totem.desktop
audio/x-ms-asx=org.gnome.Totem.desktop
audio/x-ms-wax=org.gnome.Totem.desktop
audio/x-ms-wma=org.gnome.Totem.desktop
audio/x-musepack=org.gnome.Totem.desktop
audio/x-opus+ogg=org.gnome.Totem.desktop
audio/x-pn-aiff=org.gnome.Totem.desktop
audio/x-pn-au=org.gnome.Totem.desktop
audio/x-pn-realaudio=org.gnome.Totem.desktop
audio/x-pn-realaudio-plugin=org.gnome.Totem.desktop
audio/x-pn-wav=org.gnome.Totem.desktop
audio/x-pn-windows-acm=org.gnome.Totem.desktop
audio/x-realaudio=org.gnome.Totem.desktop
audio/x-real-audio=org.gnome.Totem.desktop
audio/x-s3m=rhythmbox.desktop
audio/x-sbc=org.gnome.Totem.desktop
audio/x-scpls=rhythmbox.desktop
audio/x-shorten=org.gnome.Totem.desktop
audio/x-speex=org.gnome.Totem.desktop
audio/x-stm=rhythmbox.desktop
audio/x-tta=org.gnome.Totem.desktop
audio/x-wav=org.gnome.Totem.desktop
audio/x-wavpack=org.gnome.Totem.desktop
audio/x-vorbis=rhythmbox.desktop
audio/x-xm=rhythmbox.desktop
audio/vorbis=rhythmbox.desktop
audio/mpeg=rhythmbox.desktop
audio/mp4=rhythmbox.desktop

---

