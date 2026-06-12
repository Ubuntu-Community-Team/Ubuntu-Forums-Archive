---
title: "HOWTO:  Install Fuppes on Ubuntu 9.10"
date: 2009-11-01
forum: Multimedia Software
---

### Post by PorchSong on 2009-11-01
I have updated and cleaned up my fuppes guide to help you install Fuppes on your linux box.  If you follow the guide exactly, it will work.  

This is for an XBOX360 but will work on PS3 as well.  

First, open up a terminal "Applications->Accessories->Terminal" and clean your system of old programs fuppes uses:

```

$ sudo apt-get remove autoconf automake gettext


```

Open up a file browser and go to your ./home/**your user name**/ directory and delete your /fuppes directory if you see it in there.  NOT the hidden /.fuppes directory (use Ctrl+h to toggle hidden folders while in gnome to see) as this only contains your fuppes.cfg and vfolder.cfg files. (no need to nuke those).  

So, you are now "clean."

Now start over (again while in console).

```
$ sudo apt-get update
```

Install your codecs (cut and paste the whole thing rather than line by line): 

```
$ sudo apt-get install ffmpeg build-essential \
libavutil-dev libavformat-dev libavcodec-dev \
subversion libtool \
libsqlite3-dev libpcre3-dev libxml2-dev libpcre3-dev pkg-config
```

Reinstall your autoconf, automake, and gettext programs:

```

$ sudo apt-get install autoconf automake gettext

```

Now get the latest release of fuppes v664 (Again, I run these one line at a time)


```
$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --prefix=/usr 
$ sudo make
$ sudo make install
$ sudo ldconfig
```

This should do it.  

The tricky part is getting a proper fuppes.cfg file in order.  You can find a fuppes.cfg in the forums, but I modified mine so that I am NOT transcoding vids to my Xbox 360--again, no need to.

Below in the coded box is my fuppes.cfg file.  You will have to change this config file to direct to your personal folders in this section:

  <shared_objects>
    <dir>[COLOR="Red"]/media/truecrypt8/Movies[/COLOR]</dir>       [COLOR="Red"]Here is where you path to your media directories.[/COLOR]
    <dir>[COLOR="Red"]/media/truecrypt9/Movies[/COLOR]</dir>
    <dir>[COLOR="Red"]/media/truecrypt10/Movies[/COLOR]</dir>
  </shared_objects>

And in network section set up to your ip addy and port (These are both located at top of fuppes.cfg file:

 <!--empty or 0 = random port-->
    <http_port>[COLOR="Red"]9137[/COLOR]</http_port>      [COLOR="Red"]This is the port # I assigned to fuppes[/COLOR]
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>[COLOR="Red"]192.168.0.1[/COLOR]</ip>   [COLOR="Red"]Threw in my gateway addy[/COLOR] 
      <ip>[COLOR="Red"]192.168.0.20[/COLOR]</ip>         [COLOR="Red"]This is the static addy for my Xbox[/COLOR]
      <ip>[COLOR="Red"]192.168.0.10[/COLOR]</ip>         [COLOR="Red"]This is the static addy for my 'puter[/COLOR]
    </allowed_ips>

Just cut and paste my whole file over your whole file, make changes in directory area and network area to match your setup, and save it.  Also, place this in your home/**your user name**/.fuppes directory (the hidden one again, Ctrl+h to toggle hidden folders). You will need admin rights to do this.

My fuppes.cfg file:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/truecrypt8/Movies</dir>
    <dir>/media/truecrypt9/Movies</dir>
    <dir>/media/truecrypt10/Movies</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.0.1</ip>
      <ip>192.168.0.20</ip>
      <ip>192.168.0.10</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
        </file_settings>
	<description_values>
	<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
	<model_name>Windows Media Connect compatible (%s)</model_name>
	<model_number>2.0</model_number>
	</description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>

```



Also, grab someone's vfolder.cfg file or just use mine and drop in same directory (the hidden fuppes directory in your home directory.  Also where you put your fuppes.cfg file).

Here is mine:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21" />
      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```

Open terminal and type

```

$ fuppes
```

Once you have fuppes up and running in terminal, type "r" (no quotes) and wait as your database gets built. After you get back to prompt, hit "v" to build your virtual directories.

And you know all is well if you can go to your browser and type in your computer's ip addy and get the fuppes config screen.  With my fuppes.cfg this would be:

```
http://192.168.0.10:9137
```

Lastly, I am running the AMD64 version.

******PEOPLE ARE HAVING ISSUES WITH THE XBOX SEEING FUPPES, BUT NOT BEING ABLE TO SEE VIDEO FILES OR DIRECTORY STRUCTURE.  This is an issue with the fuppes.db (database).  If your Xbox sees the fuppes server, then it WILL see your vids (we just need to fix it).  First, make sure you do "fuppes" in terminal.  Second, after fuppes loads up, type 'r' to rebuild your database.  AFTER it completes, type 'v' to rebuild your folder structure.  This WILL work eventually, though it might take a few attempts.  If still having problems, then goto your /.fuppes and delete your fuppes.db file (you will need admin rights to do so), wash and repeat (load fuppes, 'r', then 'v'.  Hang in there, it WILL work.******

Lastly, if you are having install/upgrade issues with latest fuppes version v636 or newer, AND you followed the guide for "Installing the latest FFMPEG & V264 guide," 

[http://ubuntuforums.org/showthread.php?t=786095&highlight=fuppes]("http://ubuntuforums.org/showthread.php?t=786095&highlight=fuppes")

there is a solution.  You first have to go back the "FFMPEG guide" and uninstall/purge the install and delete the directories as directed.  AFTER this, follow this guide again to get fuppes installed and running, THEN you can go back to the FFMPEG Guide and reinstall.  Apparently, this fuppes install and the latest ffmpeg codecs don't play well together.

PM me if you have any additional questions.

---

### Post by sdowney717 on 2009-11-02
good guide.

do you know if fuppes can be configured to pull internet video content and transcode it ?

---

### Post by sdowney717 on 2009-11-02
it appears to start and i would expect to see it as an available media server in my dsm 320 but i dont

i do see ushare as an available media server in my dsm 320 screen. so what am i missing?



> scott@scott-desktop:~/fuppes$ sudo fuppes
            FUPPES - 0.646
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ContentDatabase] create database at Mon Nov  2 17:25:50 2009
== lib/ContentDirectory/VirtualContainerMgr.cpp (56) :: Mon Nov  2 17:25:50 2009 ==
no vfolder.cfg file available

read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Mon Nov  2 17:25:50 2009
webinterface: [http://127.0.1.1:39445](http://127.0.1.1:39445)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (352) :: Mon Nov  2 17:25:56 2009 ==
new device: uShare775: 1 :: MediaServer

new UPnP device:
uShare775: 1 (MediaServer)
r
[ContentDatabase] create database at Mon Nov  2 17:40:32 2009
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Mon Nov  2 17:40:32 2009
q
[FUPPES] shutting down
[FUPPES] exit
scott@scott-desktop:~/fuppes$ sudo fuppes
[sudo] password for scott: 
            FUPPES - 0.646
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

== lib/ContentDirectory/VirtualContainerMgr.cpp (56) :: Mon Nov  2 17:51:19 2009 ==
no vfolder.cfg file available

webinterface: [http://127.0.1.1:54420](http://127.0.1.1:54420)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (352) :: Mon Nov  2 17:51:24 2009 ==
new device: uShare775: 1 :: MediaServer

new UPnP device:
uShare775: 1 (MediaServer)



---

### Post by zacnotes on 2009-11-02
agreed with sdowney. My output looks about the same after running fuppes, and from the "no vfolder.cfg" and the interface being at loopback, it looks like fuppes is looking for the cfg files somewhere else, and when it doesn't find it,  creates a base fuppes.cfg file. i just don't know where it is looking for the files, or how to change where it looks.

---

### Post by Shhnap on 2009-11-03
Hi, I'm planning on doing a little development work on fuppes to get it back upto scratch so here are a couple of things that you should upgrade your guide to include (please take this constructively):

1) The source is out of date and needs to be patched. See this svn diff that fixes the compile problems on the latest gcc with 9.10, with these changes you will not need to do the CC hacks to gcc-4.3:

```
--- src/plugins/transcoder_ffmpeg.cpp   (revision 646)
+++ src/plugins/transcoder_ffmpeg.cpp   (working copy)
@@ -35,7 +35,7 @@
   char*   sChar = NULL;
   std::string  sArg;

-  while((sChar = strchr(sParams.c_str(), nChar)) || !sParams.empty()) {
+  while((sChar = (char*)strchr(sParams.c_str(), nChar)) || !sParams.empty()) {

     if(sChar) {
       sArg = sParams.substr(0, sChar - sParams.c_str());
===================================================================
--- src/lib/Common/Exception.cpp        (revision 646)
+++ src/lib/Common/Exception.cpp        (working copy)
@@ -26,6 +26,7 @@
 #include "Exception.h"
 #include <sstream>
 #include <stdarg.h>
+#include <cstdio>

 using namespace fuppes;

Index: src/lib/ContentDirectory/inotify-cxx-0.7.2/inotify-cxx.cpp
===================================================================
--- src/lib/ContentDirectory/inotify-cxx-0.7.2/inotify-cxx.cpp  (revision 646)
+++ src/lib/ContentDirectory/inotify-cxx-0.7.2/inotify-cxx.cpp  (working copy)
@@ -23,6 +23,7 @@
 #include <errno.h>
 #include <unistd.h>
 #include <fcntl.h>
+#include <cstdio>

 #include "inotify-cxx.h"
===================================================================
--- Makefile.am (revision 646)
+++ Makefile.am (working copy)
@@ -31,7 +31,7 @@
        src/Makefile.am \
        src/plugins/Makefile.am \
        src/windows/Makefile.am \
-       src/windows/fuppes.exe.Manifest \
-       src/windows/fuppes.ico \
+       src/windows/fuppes.exe.Manifest \
+       src/windows/fuppes.ico  \
   vfolder.cfg \
   crosscompile_win32.sh
```


2) VERY IMPORTANT: Do not try and compile fuppes with libsimage-dev. There is currently a bug in it where it tries to look for libogg.la but that file was removed, on purpose and for good reason, by debian. libsimage-dev needs to be fixed.

3) Run a sudo make install before trying to run fuppes or you will likely run into a sqlite error. (Working on this now)

4) Keep the --prefix=/usr/ tag. (Working on this too)

5) The configure I run, for maximum settings, is:
./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad
That means that you must install every dev library except libsimage-dev (until it is fixed)

6) Consider using the following directories for the init.d "startup script" version of fuppes:
/etc/fuppes
/var/lib/fuppes
As is specified in this tutorial: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

I hope this helps everyone when they go to debug problems with fuppes. I have spent the last week getting this information.

---

### Post by PorchSong on 2009-11-04
I completely appreciate your work on this.  I still think fuppes is the best media server and the simplest.  I will be happy to update my guide as needed to reflect your work.

---

### Post by zacnotes on 2009-11-04
excited to see advancements! note to sdowney: created a directory /etc/fuppes and placed my .cfg files there. it appears that fuppes got past the hurdle we were having with that, but then i get a few I/O errors instead and it wont run at all. I am planning on re-installing it when porchsong updates his tutorial.

---

### Post by sdowney717 on 2009-11-04
the one big advantage of fuppes over ushare is realtime transcoding.
otherwise, ushare just works very simply.

I would love to see fuppes downloading and transcoding rss internet feeds like a 'playon' or a 'tversity' style.
[http://www.themediamall.com/playon/](http://www.themediamall.com/playon/)
then it could be playing hulu videos and streaming them to a media player hardware device like dsm 320 or xbox etc... right on your tv.
Linux has no native program to do this.

---

### Post by Zombear on 2009-11-04
Im in the middle of setting up Fuppes with this guide. Sadly, Im getting a buffer overflow error trying to make a database. Can anyone help? thanks!

```

[ContentDatabase] create database at Wed Nov  4 13:59:41 2009
read shared directories
*** buffer overflow detected ***: fuppes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x307de8]
/lib/tls/i686/cmov/libc.so.6[0x306e20]
/lib/tls/i686/cmov/libc.so.6[0x306558]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x29059e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x60a)[0x26414a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x30660d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x30654d]
/usr/lib/fuppes/libmetadata_libavformat.so(fuppes_metadata_read+0x125)[0x371b75]
/usr/lib/libfuppes.so.0(_ZN15CMetadataPlugin8readDataEP10metadata_t+0x24)[0x3cfd34]
/usr/lib/libfuppes.so.0(_ZN12CFileDetails15GetVideoDetailsESsP10SVideoItem+0x25f)[0x3a2e6f]
/usr/lib/libfuppes.so.0(_Z15InsertVideoFileP16CContentDatabaseSs+0x95)[0x3af405]
/usr/lib/libfuppes.so.0(_Z10InsertFileP16CContentDatabasejSsb+0xcba)[0x3b261a]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0xb3f)[0x3b356f]
/usr/lib/libfuppes.so.0(_ZN13RebuildThread3runEv+0x956)[0x3b76c6]
/usr/lib/libfuppes.so.0(_ZN6fuppes6Thread10threadFuncEPv+0x21)[0x3cdff1]
/lib/tls/i686/cmov/libpthread.so.0[0x6ad80e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0x2f37ee]
======= Memory map: ========
00110000-0012c000 r-xp 00000000 08:01 672        /lib/libgcc_s.so.1
0012c000-0012d000 r--p 0001b000 08:01 672        /lib/libgcc_s.so.1
0012d000-0012e000 rw-p 0001c000 08:01 672        /lib/libgcc_s.so.1
0012e000-00130000 r-xp 00000000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
00130000-00131000 r--p 00001000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
00131000-00132000 rw-p 00002000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
00132000-0013c000 r-xp 00000000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0013c000-0013d000 r--p 00009000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0013d000-0013e000 rw-p 0000a000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0013e000-0014b000 r-xp 00000000 08:01 15604      /usr/lib/libsimage.so.20.6.1
0014b000-0014c000 rw-p 0000d000 08:01 15604      /usr/lib/libsimage.so.20.6.1
0014c000-00151000 r-xp 00000000 08:01 4642       /usr/lib/libogg.so.0.6.0
00151000-00152000 r--p 00004000 08:01 4642       /usr/lib/libogg.so.0.6.0
00152000-00153000 rw-p 00005000 08:01 4642       /usr/lib/libogg.so.0.6.0
00153000-0015a000 r-xp 00000000 08:01 4875       /usr/lib/libvorbisfile.so.3.2.0
0015a000-0015b000 r--p 00007000 08:01 4875       /usr/lib/libvorbisfile.so.3.2.0
0015b000-0015c000 rw-p 00008000 08:01 4875       /usr/lib/libvorbisfile.so.3.2.0
0015c000-001b2000 r-xp 00000000 08:01 4845       /usr/lib/libtiff.so.4.2.1
001b2000-001b4000 r--p 00055000 08:01 4845       /usr/lib/libtiff.so.4.2.1
001b4000-001b5000 rw-p 00057000 08:01 4845       /usr/lib/libtiff.so.4.2.1
001b5000-0021b000 r-xp 00000000 08:01 4788       /usr/lib/libsndfile.so.1.0.20
0021b000-0021c000 r--p 00065000 08:01 4788       /usr/lib/libsndfile.so.1.0.20
0021c000-0021d000 rw-p 00066000 08:01 4788       /usr/lib/libsndfile.so.1.0.20
0021d000-00221000 rw-p 00000000 00:00 0 
00222000-00225000 r-xp 00000000 08:01 769        /lib/libuuid.so.1.3.0
00225000-00226000 r--p 00002000 08:01 769        /lib/libuuid.so.1.3.0
00226000-00227000 rw-p 00003000 08:01 769        /lib/libuuid.so.1.3.0
00227000-00365000 r-xp 00000000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
00365000-00367000 r--p 0013e000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
00367000-00368000 rw-p 00140000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
00368000-0036b000 rw-p 00000000 00:00 0 
0036b000-0036f000 r-xp 00000000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
0036f000-00370000 r--p 00003000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
00370000-00371000 rw-p 00004000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
00371000-00373000 r-xp 00000000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00373000-00374000 r--p 00001000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00374000-00375000 rw-p 00002000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00375000-0037c000 r-xp 00000000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
0037c000-0037d000 r--p 00006000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
0037d000-0037e000 rw-p 00007000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
00381000-00484000 r-xp 00000000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00484000-00485000 r--p 00103000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00485000-00486000 rw-p 00104000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00486000-00487000 rw-p 00000000 00:00 0 
00487000-00497000 r-xp 00000000 08:01 645        /lib/libbz2.so.1.0.4
00497000-00498000 r--p 0000f000 08:01 645        /lib/libbz2.so.1.0.4
00498000-00499000 rw-p 00010000 08:01 645        /lib/libbz2.so.1.0.4
00499000-004a5000 r-xp 00000000 08:01 1254       /usr/lib/libgsm.so.1.0.12
004a5000-004a6000 r--p 0000c000 08:01 1254       /usr/lib/libgsm.so.1.0.12
004a6000-004a7000 rw-p 0000d000 08:01 1254       /usr/lib/libgsm.so.1.0.12
004a7000-004bc000 r-xp 00000000 08:01 4800       /usr/lib/libspeex.so.1.5.0
004bc000-004bd000 r--p 00014000 08:01 4800       /usr/lib/libspeex.so.1.5.0
004bd000-004be000 rw-p 00015000 08:01 4800       /usr/lib/libspeex.so.1.5.0
004c1000-005e3000 r-xp 00000000 08:01 4939       /usr/lib/libxml2.so.2.7.5
005e3000-005e4000 ---p 00122000 08:01 4939       /usr/lib/libxml2.so.2.7.5
005e4000-005e8000 r--p 00122000 08:01 4939       /usr/lib/libxml2.so.2.7.5
005e8000-005e9000 rw-p 00126000 08:01 4939       /usr/lib/libxml2.so.2.7.5
005e9000-005ea000 rw-p 00000000 00:00 0 
005ea000-005ee000 r-xp 00000000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
005ee000-005ef000 r--p 00003000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
005ef000-005f0000 rw-p 00004000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
0060d000-0065b000 r-xp 00000000 08:01 3915       /usr/lib/libFLAC.so.8.2.0
0065b000-0065c000 r--p 0004d000 08:01 3915       /usr/lib/libFLAC.so.8.2.0
0065c000-0065d000 rw-p 0004e000 08:01 3915       /usr/lib/libFLAC.so.8.2.0
0065d000-0065e000 r-xp 00000000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
0065e000-0065f000 r--p 00000000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
0065f000-00660000 rw-p 00001000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
006a8000-006bd000 r-xp 00000000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
006bd000-006be000 r--p 00014000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
006be000-006bf000 rw-p 00015000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
006bf000-006c1000 rw-p 00000000 00:00 0 
006fb000-00717000 r-xp 00000000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
00717000-00718000 r--p 0001b000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
00718000-00726000 rw-p 0001c000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
00726000-0077a000 r-xp 00000000 08:01 4834       /usr/lib/libtheora.so.0.3.4Aborted

```

---

### Post by Shhnap on 2009-11-04
EDIT: Welcome to the Forums!! Sorry if this post contains too much information. If you need more help just send me a Personal Message (PM).

Firstly you are using simage:

```
0065d000-0065e000 r-xp 00000000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
0065e000-0065f000 r--p 00000000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
0065f000-00660000 rw-p 00001000 08:01 16995      /usr/lib/fuppes/libmetadata_simage.so.0.0.0
```

Could you please run the following code and tell us the output:

```
dpkg -p libsimage-dev
```

You should not make fuppes with the simage package in karmic because it currently has it's dependencies wrong. If you get this result when simage is still installed then you have a broken simage package:

```
$ grep "libogg.la" /usr/lib/*.la
/usr/lib/libsimage.la:dependency_libs=' /usr/lib/libsndfile.la
/usr/lib/libFLAC.la -L/usr/lib /usr/lib/libvorbisfile.la
/usr/lib/libvorbis.la /usr/lib/libogg.la /usr/lib/libtiff.la -lc -lpng
-lz /usr/lib/libjpeg.la /usr/lib/libgif.la -lm'
$
```

So try uninstalling libsimage-dev and ./configure --some-options && make again. And if you don't have libsimage-dev installed then please post the result of your ./configure.

---

### Post by Zombear on 2009-11-04
from the output:
> 
Package: libsimage-dev
Priority: optional
Section: libdevel
Installed-Size: 216
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: simage
Version: 1.6.1-3ubuntu1
Depends: libgif-dev, libjpeg62-dev, libpng12-dev, libsimage20 (= 1.6.1-3ubuntu1), libsndfile1-dev, libtiff4-dev, libvorbis-dev, zlib1g-dev
Size: 41782
Description: generic interface to various image file format libraries
 The simage library provides a simplified and uniform interface to many
 image file format libraries, and it includes internal support for some
 image file formats too.
Homepage: [http://www.coin3d.org/lib/simage](http://www.coin3d.org/lib/simage)
Original-Maintainer: Steve M. Robbins <smr@debian.org>



Ill try removing simage in the meantime and see what happens.

---

### Post by Shhnap on 2009-11-04
That is the version of simage that I had problems with. When you try again let us know what the results are.

---

### Post by Zombear on 2009-11-04
removed simage.. I think..

rebuilding the database makes it a bit further before quitting.

> 
r
[ContentDatabase] create database at Wed Nov  4 21:05:45 2009
read shared directories
*** buffer overflow detected ***: fuppes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x731de8]
/lib/tls/i686/cmov/libc.so.6[0x730e20]
/lib/tls/i686/cmov/libc.so.6[0x730558]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x6ba59e]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x60a)[0x68e14a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x73060d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x73054d]
/usr/lib/fuppes/libmetadata_libavformat.so(fuppes_metadata_read+0x125)[0x315b75]
/usr/lib/libfuppes.so.0(_ZN15CMetadataPlugin8readDataEP10metadata_t+0x24)[0xf3cd34]
/usr/lib/libfuppes.so.0(_ZN12CFileDetails15GetVideoDetailsESsP10SVideoItem+0x25f)[0xf0fe6f]
/usr/lib/libfuppes.so.0(_Z15InsertVideoFileP16CContentDatabaseSs+0x95)[0xf1c405]
/usr/lib/libfuppes.so.0(_Z10InsertFileP16CContentDatabasejSsb+0xcba)[0xf1f61a]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0xb3f)[0xf2056f]
/usr/lib/libfuppes.so.0(_ZN13RebuildThread3runEv+0x956)[0xf246c6]
/usr/lib/libfuppes.so.0(_ZN6fuppes6Thread10threadFuncEPv+0x21)[0xf3aff1]
/lib/tls/i686/cmov/libpthread.so.0[0x46c80e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0x71d7ee]
======= Memory map: ========
00110000-0011a000 r-xp 00000000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0011a000-0011b000 r--p 00009000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0011b000-0011c000 rw-p 0000a000 08:01 1455       /lib/tls/i686/cmov/libnss_files-2.10.1.so
0011c000-001a2000 r-xp 00000000 08:01 4806       /usr/lib/libsqlite3.so.0.8.6
001a2000-001a3000 r--p 00086000 08:01 4806       /usr/lib/libsqlite3.so.0.8.6
001a3000-001a4000 rw-p 00087000 08:01 4806       /usr/lib/libsqlite3.so.0.8.6
001a4000-001b0000 r-xp 00000000 08:01 1242       /usr/lib/i686/cmov/libavutil.so.49.15.0
001b0000-001b1000 r--p 0000b000 08:01 1242       /usr/lib/i686/cmov/libavutil.so.49.15.0
001b1000-001b2000 rw-p 0000c000 08:01 1242       /usr/lib/i686/cmov/libavutil.so.49.15.0
001b2000-001b5000 rw-p 00000000 00:00 0 
001b5000-001ca000 r-xp 00000000 08:01 4800       /usr/lib/libspeex.so.1.5.0
001ca000-001cb000 r--p 00014000 08:01 4800       /usr/lib/libspeex.so.1.5.0
001cb000-001cc000 rw-p 00015000 08:01 4800       /usr/lib/libspeex.so.1.5.0
001d1000-001ec000 r-xp 00000000 08:01 622        /lib/ld-2.10.1.so
001ec000-001ed000 r--p 0001a000 08:01 622        /lib/ld-2.10.1.so
001ed000-001ee000 rw-p 0001b000 08:01 622        /lib/ld-2.10.1.so
001ef000-001f1000 r-xp 00000000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
001f1000-001f2000 r--p 00001000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
001f2000-001f3000 rw-p 00002000 08:01 1444       /lib/tls/i686/cmov/libdl-2.10.1.so
001f3000-001f7000 r-xp 00000000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
001f7000-001f8000 r--p 00003000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
001f8000-001f9000 rw-p 00004000 08:01 16991      /usr/lib/fuppes/libmetadata_taglib.so.0.0.0
00219000-0022d000 r-xp 00000000 08:01 776        /lib/libz.so.1.2.3.3
0022d000-0022e000 r--p 00013000 08:01 776        /lib/libz.so.1.2.3.3
0022e000-0022f000 rw-p 00014000 08:01 776        /lib/libz.so.1.2.3.3
0022f000-002ae000 r-xp 00000000 08:01 1266       /usr/lib/libschroedinger-1.0.so.0.2.0
002ae000-002af000 r--p 0007f000 08:01 1266       /usr/lib/libschroedinger-1.0.so.0.2.0
002af000-002b0000 rw-p 00080000 08:01 1266       /usr/lib/libschroedinger-1.0.so.0.2.0
002b0000-00304000 r-xp 00000000 08:01 4834       /usr/lib/libtheora.so.0.3.4
00304000-00305000 r--p 00053000 08:01 4834       /usr/lib/libtheora.so.0.3.4
00305000-00306000 rw-p 00054000 08:01 4834       /usr/lib/libtheora.so.0.3.4
00315000-00317000 r-xp 00000000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00317000-00318000 r--p 00001000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00318000-00319000 rw-p 00002000 08:01 16987      /usr/lib/fuppes/libmetadata_libavformat.so.0.0.0
00324000-00446000 r-xp 00000000 08:01 4939       /usr/lib/libxml2.so.2.7.5
00446000-00447000 ---p 00122000 08:01 4939       /usr/lib/libxml2.so.2.7.5
00447000-0044b000 r--p 00122000 08:01 4939       /usr/lib/libxml2.so.2.7.5
0044b000-0044c000 rw-p 00126000 08:01 4939       /usr/lib/libxml2.so.2.7.5
0044c000-0044d000 rw-p 00000000 00:00 0 
00467000-0047c000 r-xp 00000000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
0047c000-0047d000 r--p 00014000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
0047d000-0047e000 rw-p 00015000 08:01 1464       /lib/tls/i686/cmov/libpthread-2.10.1.so
0047e000-00480000 rw-p 00000000 00:00 0 
00480000-0049c000 r-xp 00000000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
0049c000-0049d000 r--p 0001b000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
0049d000-004ab000 rw-p 0001c000 08:01 4871       /usr/lib/libvorbis.so.0.4.0
004d6000-004f2000 r-xp 00000000 08:01 672        /lib/libgcc_s.so.1
004f2000-004f3000 r--p 0001b000 08:01 672        /lib/libgcc_s.so.1
004f3000-004f4000 rw-p 0001c000 08:01 672        /lib/libgcc_s.so.1
004f4000-0059c000 r-xp 00000000 08:01 1281       /usr/lib/i686/cmov/libavformat.so.52.31.0
0059c000-0059d000 r--p 000a7000 08:01 1281       /usr/lib/i686/cmov/libavformat.so.52.31.0
0059d000-005a3000 rw-p 000a8000 08:01 1281       /usr/lib/i686/cmov/libavformat.so.52.31.0
005a3000-005ef000 rw-p 00000000 00:00 0 
0062b000-0064f000 r-xp 00000000 08:01 1446       /lib/tls/i686/cmov/libm-2.10.1.so
0064f000-00650000 r--p 00023000 08:01 1446       /lib/tls/i686/cmov/libm-2.10.1.so
00650000-00651000 rw-p 00024000 08:01 1446       /lib/tls/i686/cmov/libm-2.10.1.so
00651000-0078f000 r-xp 00000000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
0078f000-00791000 r--p 0013e000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
00791000-00792000 rw-p 00140000 08:01 1438       /lib/tls/i686/cmov/libc-2.10.1.so
00792000-00795000 rw-p 00000000 00:00 0 
00795000-007f6000 r-xp 00000000 08:01 4644       /usr/lib/liboil-0.3.so.0.3.0
007f6000-007f7000 r--p 00060000 08:01 4644       /usr/lib/liboil-0.3.so.0.3.0
007f7000-0080e000 rw-p 00061000 08:01 4644       /usr/lib/liboil-0.3.so.0.3.0
0080e000-00810000 rw-p 00000000 00:00 0 
00838000-0083b000 r-xp 00000000 08:01 769        /lib/libuuid.so.1.3.0
0083b000-0083c000 r--p 00002000 08:01 769        /lib/libuuid.so.1.3.0
0083c000-0083d000 rw-p 00003000 08:01 769        /lib/libuuid.so.1.3.0
00871000-00875000 r-xp 00000000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
00875000-00876000 r--p 00003000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
00876000-00877000 rw-p 00004000 08:01 16979      /usr/lib/fuppes/libcore_presentation.so.0.0.0
00877000-00882000 r-xp 00000000 08:01 4873       /usr/lib/libvorbisenc.so.2.0.3
00882000-00883000 r--p 0000a000 08:01 4873       /usr/lib/libvorbisenc.so.2.0.3
00883000-00971000 rw-p 0000b000 08:01 4873       /usr/lib/libvorbisenc.so.2.0.3
00987000-00997000 r-xp 00000000 08:01 645        /lib/libbz2.so.1.0.4
00997000-00998000 r--p 0000f000 08:01 645        /lib/libbz2.so.1.0.4
00998000-00999000 rw-p 00010000 08:01 645        /lib/libbz2.so.1.0.4
009a6000-00a8c000 r-xp 00000000 08:01 4813       /usr/lib/libstdc++.so.6.0.13
00a8c000-00a90000 r--p 000e6000 08:01 4813       /usr/lib/libstdc++.so.6.0.13
00a90000-00a91000 rw-p 000ea000 08:01 4813       /usr/lib/libstdc++.so.6.0.13
00a91000-00a98000 rw-p 00000000 00:00 0 
00ac4000-00aca000 r-xp 00000000 08:01 16983      /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
00aca000-00acb000 r--p 00005000 08:01 16983      /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
00acb000-00acc000 rw-p 00006000 08:01 16983      /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
00b3c000-00b43000 r-xp 00000000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
00b43000-00b44000 r--p 00006000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
00b44000-00b45000 rw-p 00007000 08:01 1468       /lib/tls/i686/cmov/librt-2.10.1.so
00b45000-00bd2000 r-xp 00000000 08:01 4819       /usr/lib/libtag.so.1.6.0
00bd2000-00bd4000 r--p 0008c000 08:01 4819       /usr/lib/libtag.so.1.6.0
00bd4000-00bd5000 rw-p 0008e000 08:01 4819       /usr/lib/libtag.so.1.6.0
00c19000-00c48000 r-xp 00000000 08:01 728        /lib/libpcre.so.3.12.1
00c48000-00c49000 r--p 0002e000 08:01 728        /lib/libpcre.so.3.12.1
00c49000-00c4a000 rw-p 0002f000 08:01 728        /lib/libpcre.so.3.12.1
00d15000-00d21000 r-xp 00000000 08:01 1254       /usr/lib/libgsm.so.1.0.12
00d21000-00d22000 r--p 0000c000 08:01 1254       /usr/lib/libgsm.so.1.0.12
00d22000-00d23000 rw-p 0000d000 08:01 1254       /usr/lib/libgsm.so.1.0.12
00d79000-00d7a000 r-xp 00000000 00:00 0          [vdso]
00df0000-00df5000 r-xp 00000000 08:01 4642       /usr/lib/libogg.so.0.6.0
00df5000-00df6000 r--p 00004000 08:01 4642       /usr/lib/libogg.so.0.6.0
00df6000-00df7000 rw-p 00005000 08:01 4642       /usr/lib/libogg.so.0.6.0
00eee000-00ff1000 r-xp 00000000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00ff1000-00ff2000 r--p 00103000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00ff2000-00ff3000 rw-p 00104000 08:01 16968      /usr/lib/libfuppes.so.0.0.0
00ff3000-00ff4000 rw-p 00000000 00:00 0 
00ff4000-01514000 r-xp 00000000 08:01 1269       /usr/lib/i686/cmov/libavcodec.so.52.20.0
01514000-01515000 r--p 0051f000 08:01 1269       /usr/lib/i686/cmov/libavcodec.so.52.20.0
01515000-0151e000 rw-p 00520000 08:01 1269       /usr/lib/i686/cmov/libavcodec.so.52.20.0
0151e000-0182c000 rw-p 00000000 00:00 0 
08048000-0804b000 r-xp 00000000 08:01 16973      /usr/bin/fuppes
0804b000-0804c000 r--p 00002000 08:01 16973      /usr/bin/fuppes
0804c000-0804d000 rw-p 00003000 08:01 16973      /usr/bin/fuppes
095d4000-096c1000 rw-p 00000000 00:00 0          [heap]
b2804000-b282f000 rw-p 00000000 00:00 0 
b284a000-b284b000 ---p 00000000 00:00 0 
b284b000-b304b000 rw-p 00000000 00:00 0 
b304b000-b304c000 ---p 00000000 00:00 0 
b304c000-b384c000 rw-p 00000000 00:00 0 
b384c000-b384d000 ---p 00000000 00:00 0 
b384d000-b404d000 rw-p 00000000 00:00 0 
b404d000-b404e000 ---p 00000000 00:00 0 
b404e000-b484e000 rw-p 00000000 00:00 0 
b484e000-b484f000 ---p 00000000 00:00 0 
b484f000-b504f000 rw-p 00000000 00:00 0 
b504f000-b5050000 ---p 00000000 00:00 0 
b5050000-b5850000 rw-p 00000000 00:00 0 
b5850000-b5851000 ---p 00000000 00:00 0 
b5851000-b6051000 rw-p 00000000 00:00 0 
b6051000-b6052000 ---p 00000000 00:00 0 
b6052000-b6852000 rw-p 00000000 00:00 0 
b6852000-b6853000 ---p 00000000 00:00 0 
b6853000-b7053000 rw-p 00000000 00:00 0 
b7053000-b7054000 ---p 00000000 00:00 0 
b7054000-b7858000 rw-p 00000000 00:00 0 
b7867000-b7869000 rw-p 00000000 00:00 0 
bfd8e000-bfda3000 rw-p 00000000 00:00 0          [stack]
Aborted



---

### Post by Shhnap on 2009-11-04
A 'sudo apt-get remove libsimage-dev' would have done the trick.

And looking at your stack track again I think your system might be in an interesting position. Can you please look at the svn diffs that I posted on the first page and make sure that you add all of the lines that say:

```
+ #include <cstdio>
```

to the files that the diff is for and then try again. Except don't write the plus (+) symbol because plus means "add this line". So you would just write:

```
#include <cstdio>
```

Let me know if that helps. Make sure you do a:

```
$ autoreconf -vfi
$ ./configure --with-you-options-here
$ make
```

Once you're done (although the first step should not be required I just want to be safe).

---

### Post by Zombear on 2009-11-05
Yes I am a n00b.. you just lost me.  This is the first time in 8 years Ive gotten linux working to my liking. After I got SAMBA working.. I am very close to having a dedicated file/media/print server.

That being said I have the code ready but no clue where to drop it to compile it.

---

### Post by Shhnap on 2009-11-05
If you can wait maybe a day or two I have cloned the svn repository and converted it to git, to continue fuppes development. I am planning on getting in contact with Ulrich and after tuesday next week I will be free for a few months to give some time to fuppes. If you cannot apply that manually then your best move is to wait a few days and get the git repository.

I hope nobody minds waiting a few days. Keep your eyes open and if anybody wants to join me in developing fuppes once more, and you think you have the required skills, just let me know. I welcome all help.

---

### Post by Zombear on 2009-11-06
that will work fine.

Thanks for all the help!

> **Shhnap said:**
> If you can wait maybe a day or two I have cloned the svn repository and converted it to git, to continue fuppes development. I am planning on getting in contact with Ulrich and after tuesday next week I will be free for a few months to give some time to fuppes. If you cannot apply that manually then your best move is to wait a few days and get the git repository.

I hope nobody minds waiting a few days. Keep your eyes open and if anybody wants to join me in developing fuppes once more, and you think you have the required skills, just let me know. I welcome all help.

---

### Post by jojeaux22 on 2009-11-06
Not sure if this will help anyone else but...
 
Fuppes was not reading either of my .cfg files. When starting fuppes i noticed there was a different port number listed then the one i set up. I want to that page and noticed under the configuration section:
 
Please edit the file: /root/.fuppes/fuppes.cfg 
 
I copied over the two cfg files to here and ran fuppes again. It correctly read the cfg files now. I dont know if this had anything to do with me signing in as su or not (still new to the whole linux thing) but in case it helps anyone else.
 
GREAT GUIDE!
 
*edit*
it appears that it will not display the current web interface and port until you build the database for the first time. then when you launch fuppes again, it will be display towards the top

---

### Post by Shhnap on 2009-11-06
No problems Zombear. Though I have recently noticed that the last time that Ulrich did something for fuppes was aproximately one month ago, so understandably I've sent him a few emails. If he is still working on it then I will drop mine and work with him if I can.

And, on a more important note, you should never ever be running ```
sudo fuppes
```

That makes fuppes run with all of the permissions of the root user. A really big security no-no. What you should be doing instead is setting up a user account like this guide says: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

Do that and DONT ever run fuppes as root, and you should not run it as yourself. It does compromise your system if you run fuppes as root.

---

### Post by jojeaux22 on 2009-11-06
> **Shhnap said:**
> 
And, on a more important note, you should never ever be running ```
sudo fuppes
```That makes fuppes run with all of the permissions of the root user. A really big security no-no. What you should be doing instead is setting up a user account like this guide says: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

Do that and DONT ever run fuppes as root, and you should not run it as yourself. It does compromise your system if you run fuppes as root.

I will change this. Thanks for the heads up on that.

---

### Post by s1500 on 2009-11-08
This seemed to do the trick. Of course, it's always needing the plugin dir specified. 

I did a recompile from this  thread I was directed to(and replied to). After recompiling, I ran fuppes again and got the same error. Then I realized I was running the old, broken copy of fuppes. Tried another copy of the executable I found on my system(which I assume is the recompiled one), and it worked.

I still haven't fired up the xbox to test it, but it's actually running. It segfaults when I try the web interface, but I shall just not use that then.

---

### Post by Shhnap on 2009-11-11
I'm wondering if anybody can get in contact with Ulrich? I've tried all three of his email addresses and I have gotten no response yet. I just want to speak to him to help him develop fuppes but If i get no response within the next week then I will spawn my own unofficial repository and keep on developing there; that will be a temporary measure but atleast it will let fuppes development continue until Ulrich pops back in.

Just letting everybody know what's going on. If your interested in helping out with fuppes in some way don't hesitate to send me a PM.

---

### Post by s1500 on 2009-11-11
The official fuppes site shows the last build as being over 2 years ago, but sourceforge shows a bit more recently. 

As someone who owns an Xbox 360 + Ubuntu server downstairs, I would like to see development of this continue. It was rather disheartening to do the Ubunutu upgrade, only to have less functionality than before. 

I have tried other attempts to unite the game console + server, only to find badly made software that doesn't function, and has zero documentation. One such UPNP server showed my mp3 files  in "movies", and my videos in my Music folder(wow, double fail). 

While I cannot contribute any development help(otherwise I would), all I could offer as a contribution would be QA testing on server + Xbox 360. Surely there's some PS3 owners that could help that side.

I would like to see this work better, a lot better. Tell non-Linux users they can stream content to their gaming console w/o Windows, and that just might turn some heads.

---

### Post by Zombear on 2009-11-16
any news on the update?

eagerly waiting for it.

---

### Post by s1500 on 2009-11-16
I had good success last weekend.

First off, I must remind myself to run fuppesd, not fuppes. Fuppes is the interactive app. You will never be able to toss the process in the background. No way, no how. Impossible. It will never start as a bootable service via tinkering in webmin. Never. 

I swore many moons ago I was able to get fuppes(not fuppesd) to be shoved into the background. Not anymore. So I do the same thing by running fuppesd, and it works.

So far, MP3s play.

So far, the only pictures I can view are the JPEG album artwork files. I swore I added a folder for just images, but it doesn't show in "my pictures".

Videos work okay. When I mean okay, I mean about only 40% of them work, and the remaining 60% use some codec the Xbox can't.

What GUI designer thought it would be a good idea to mix the randomize & orderly button around? To play tracks in shuffle mode, the icon must be showing 2 straight lines. I thought it would be the other way around.

So I'm going to shut down x360mediaserve & maybe just use that only for streaming station if I can get that to work.

---

### Post by Shhnap on 2009-11-16
I heard back from Ulrich the other day and learned a few things.

[LIST=1]
[*]Ulrich does not have much time to develop fuppes
[*]There is a fair amount of cleanup to be performed
[*]I'm going to start working on fuppes with Ulrich and a complete move from git to svn is being considered. To ease development.
[/LIST]

In response to these changes and interest in the project I might just start a blog that lets people know what is going on in the fuppes project. So far I have only:

[LIST]
[*]Made a list of bugs that need to be solved
[*]Gone over the todo list with Ulrich and picked an area of the project to improve. I have chosen to improve the configuration and presentation (web interface) of fuppes first. Easy configuration leads to ease of use and should get me familiar with the project. Then I plan on making it so that as many different types of digital media can play on the xbox (or any other device) as possible.
[*]All the while bugs will be solved and documentation written.
[/LIST]

There is alot to do and only two people to do it so we could obviously use all of the help that we can get but I'll post about that elsewhere. Things are slowly picking up pace and we'll get something happening. I'll post the link to the blog here soon and then I'll post there instead.

[s]P.S. If you google around you might find my git repository for fuppes.[/s]
P.S. I used to have a git repository that I took down because I am now working on the main branch. Don't click on it from google because I took it down.

---

### Post by twisted_steel on 2009-11-16
Shhnap, thanks for getting things moving again.  I had fuppes somewhat working in the past and have been meaning to get it set up on my desktop and server in the near future.  I would be happy to help out with some testing.

---

### Post by Zeikcied on 2009-11-18
I can't get past the ./configure line.

It keeps ending with this:

```
check minimum dependencies

./configure: line 16311: syntax error near unexpected token `PCRE,'
./configure: line 16311: `PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'
```

I'm lost. :(

---

### Post by Shhnap on 2009-11-18
Two things may solve this problem.

1) Before trying ./configure did you remember to type in the following:

```
autoreconf -vfi
```

2) Do you have pkg-config installed?

```
sudo apt-get install pkg-config
```

If the problem still persists after that then let me know.

P.S. Also make sure that you have all of the required dependencies specified here: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux)

---

### Post by Zeikcied on 2009-11-18
> **Shhnap said:**
> 2) Do you have pkg-config installed?

```
sudo apt-get install pkg-config
```

Ah.  That was it.

I rarely ever compile programs, so I don't always know what's needed or what the various errors mean.  Thanks. :)

EDIT: I have it working now.  But when I browse the Fuppes server with my 360, all the music is lumped in one giant list.  I did notice in the ./configure output that the metadata plugins weren't enabled and such.  So the 360 isn't getting Artist or Album tags.  It makes it a lot more difficult to create playlists (especially since I can't save the playlists, because the music isn't on the 360 itself).  Of course, not all my music has proper tags, but it would be a great help if I could get that enabled.  Is it possible to enable it after installation, or do I have to configure and install it again?

---

### Post by Shhnap on 2009-11-18
I'm happy that I could help you get it to compile. My configure script is:

```
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --plugin=/usr/
```

And it's summary is: (notice how everything but simage is enabled; for Ubuntu Karmic Koala)

```
  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : yes
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : enabled
    ImageMagick   : enabled  (Wand C-API)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : enabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled
    inotify    : enabled

```

And I think it works for me. Please try and install all of the required dev libraries (as I gave you a link to before) and try and recompile again and tell me if the problem persists. The important ones for what you want are taglib and mpeg4ip.

---

### Post by s1500 on 2009-11-18
As soon as I have fuppes set up nice & neat, that one thing just HAS to happen to screw it up.

I come home from work to see all my clocks blinking. Yep, the power went out...again. Oh well, at least now I can test my init.d thing I made in webmin for fuppes.

Now at least twice any time I set up fuppes, the power goes out. Typically it just needs a reboot due to updates.

---

### Post by Shhnap on 2009-11-18
> **s1500 said:**
> I come home from work to see all my clocks blinking. Yep, the power went out...again. Oh well, at least now I can test my init.d thing I made in webmin for fuppes.

You could always just use the fuppes init.d script provided on the wiki, it works great for me: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

But good to hear that is is working well for you.

---

### Post by KillaB7 on 2009-11-20
Hi Shhnap,

Thanks for the gcc-4.4 patch and your commitment to helping Ulrich develop fuppes!!  After the latest set of Karmic updates I was faced with a Bus IO error when running fuppes and ended up recompiling.

No offence, but I'm not sure what needs work on the WebUI.  As a Linux user I don't use it. I'm not saying it's not useful, just that IMHO there are more important issues to resolve, such as fixing build bugs.

Also, after recently configuring a Deluge init script I prefer it to the code on the wiki since it doesn't involve creating a new user.

Starting at step 6 of the following howto I just edited every deluge instance to fuppes and trimmed it to use one set of variables.
[http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)

My hack of the original script is probably far from perfect, but it seems to work:

/etc/default/fuppes-daemon 
```

# Configuration for /etc/init.d/fuppes-daemon

# The init.d script will only run if this variable non-empty.
FUPPESD_USER="<username>"             # !!!CHANGE THIS!!!!

# Should we run at startup?
RUN_AT_STARTUP="YES"

```

/etc/init.d/fuppes-daemon
```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          fuppes-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of fuppes.
# Description:       Starts the fuppes daemon with the user specified in
#                    /etc/default/fuppes-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Fuppes Daemon"
NAME="fuppesd"
DAEMON=/usr/bin/fuppesd
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
PKGNAME=fuppes-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$FUPPESD_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, FUPPESD_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE --exec $DAEMON \
      --chuid $FUPPESD_USER --user $FUPPESD_USER --test > /dev/null
   RETVAL="$?"
   [ "$RETVAL" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE --make-pidfile --exec $DAEMON \
      --chuid $FUPPESD_USER --user $FUPPESD_USER -- $DAEMON_ARGS
   RETVAL="$?"
        sleep 2
   [ "$RETVAL" = "0" ] || return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
   # Return
   #   0 if daemon has been stopped
   #   1 if daemon was already stopped
   #   2 if daemon could not be stopped
   #   other if a failure occurred

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $FUPPESD_USER --pidfile $PIDFILE
   RETVAL="$?"
   [ "$RETVAL" = "2" ] && return 2

   rm -f $PIDFILE

   [ "$RETVAL" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME"
   do_stop
   case "$?" in
     0|1)
      do_start
      case "$?" in
         0) log_end_msg 0 ;;
         1) log_end_msg 1 ;; # Old process is still running
         *) log_end_msg 1 ;; # Failed to start
      esac
      ;;
     *)
        # Failed to stop
      log_end_msg 1
      ;;
   esac
   ;;
  *)
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:

```

---

### Post by s1500 on 2009-11-20
Has anyone done some sort of cronjob/scheduled task to automatically update the libraries so files dropped in the folders get added? That is one nice thing about Windows Media Player sharing. You fire it up & it adds the new files to the shared folders, and the Xbox sees it. 

Hmm, maybe make an environment variable of which folders you want fuppes to share, then have both the fuppes config & your cron job use that as a reference point?

---

### Post by KillaB7 on 2009-11-20
> **s1500 said:**
> Has anyone done some sort of cronjob/scheduled task to automatically update the libraries so files dropped in the folders get added?

I'm not sure what build it was introduced but Fuppes already does this.  I think that's what inotify is for.

---

### Post by s1500 on 2009-11-21
Nope, as expected, it does not like my webmin setting to automatically start up. 

And now I bring it back up manually, it doesn't see ANY media. No videos, pictures, or mp3s, despite looking configured correctly.

It really should not be this complicated & fragile.

---

### Post by s1500 on 2009-11-22
And no more than 1 hour after I left that reply, I'm back up and running again.

I browsed over to my Windows laptop's media shares, played a sample file, then ran back to my fuppes installation. Suddenly everything was working again without a problem.

I heavily scaled back my MP3 archive shares from 6500 to less than a third of that MP3 collection. Suddenly things weren't so slow & wishy-washy. Looks to be some sort of scaling problem when you reach a certain amount of MP3s.

There's still things to be ironed out like no web access, but I'll watch Chuck episodes & play MP3s for now. 

And to boot, I'm now typing this message on a just-installed Ubuntu partition on my Acer Aspire one. That installed flawlessly, as well as my Ubuntu Netbook Remix on my EEE PC.

---

### Post by Shhnap on 2009-11-23
> **s1500 said:**
> I heavily scaled back my MP3 archive shares from 6500 to less than a third of that MP3 collection. Suddenly things weren't so slow & wishy-washy. Looks to be some sort of scaling problem when you reach a certain amount of MP3s.

Yes I have noticed this myself. It is one of the items that will be dealt with in time.

I just thought I would announce that two more revisions have come out that add fuppes support for gcc-4.4 and therefore us users of 9.10 might want to get that instead.

---

### Post by twisted_steel on 2009-11-23
> **Shhnap said:**
> I just thought I would announce that two more revisions have come out that add fuppes support for gcc-4.4 and therefore us users of 9.10 might wand to get that instead.

Where can I find your branch?  I thought I found something on github, but I get 404s from the Google results (some ridiculous octopus/cat creature).

---

### Post by Shhnap on 2009-11-23
> **twisted_steel said:**
> Where can I find your branch?  I thought I found something on github, but I get 404s from the Google results (some ridiculous octopus/cat creature).

It is actually the official link on sourceforge that I was referring to:

```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
```

Since I was able to get in contact with Ulrich and join his development effort we are using git in a private repository and publishing via svn on sourceforge. Therefore the link above is fairly recent (last few days). The github link that you found was indeed my repository that I did initial development on like a week ago but obviously I took it down once I could just develop on the main branch. That is why you can no longer view it, it would be out of date and not maintained anyway. So sorry for the dangling google link but at least you know straight away that there is nothing to be had there.

---

### Post by twisted_steel on 2009-11-23
Ah, that makes sense.  Thanks for the svn location.

---

### Post by dbccos on 2009-11-24
Is it still necessary to compile ffmpeg from source? If so please provide the options used to enable support for video transcoding and such for the xbox 360.

I've tried to compile ffmpeg from source with x264 support as below:

Compile x264:

```
$git clone git://git.videolan.org/x264.git
cd x264
./configure
make
sudo checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`" --backup=no --default
```Compile ffmpeg:

```
$cd ..
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb  --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
make
sudo checkinstall --pkgname=ffmpeg --pkgversion "4:0.5+svn`date +%Y%m%d`" --backup=no --default
```Note the omission of theora as it was complaining.

After that I attempted building fuppes from the latest svn repository (v648 ) presuming all the necessary changes for it to work with the latest GCC compiler and such are resolved.

```
svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
cd fuppes
autoreconf -vfi
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --prefix=/usr
make

```And this is where things blow up:

```
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libmetadata_libavformat.la] Error 1
make[1]: Leaving directory `/tmp/fuppes/src/plugins'
make: *** [all-recursive] Error 1
```So there is still no joy in getting a clean build of fuppes in Ubuntu 9.10 :(

---

### Post by s1500 on 2009-11-24
What is the stance on distributing binaries of the fuppes daemon on sourceforge, etc? Or would compiled binaries not work on every system due to library dependencies?

---

### Post by Shhnap on 2009-11-24
> **dbccos said:**
> Is it still necessary to compile ffmpeg from source? If so please provide the options used to enable support for video transcoding and such for the xbox 360.

I've tried to compile ffmpeg from source with x264 support as below:

Compile x264:

```
$git clone git://git.videolan.org/x264.git
cd x264
./configure
make
sudo checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`" --backup=no --default
```Compile ffmpeg:

```
$cd ..
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb  --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
make
sudo checkinstall --pkgname=ffmpeg --pkgversion "4:0.5+svn`date +%Y%m%d`" --backup=no --default
```Note the omission of theora as it was complaining.

After that I attempted building fuppes from the latest svn repository (v648 ) presuming all the necessary changes for it to work with the latest GCC compiler and such are resolved.

```
svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
cd fuppes
autoreconf -vfi
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --prefix=/usr
make

```And this is where things blow up:

```
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libmetadata_libavformat.la] Error 1
make[1]: Leaving directory `/tmp/fuppes/src/plugins'
make: *** [all-recursive] Error 1
```So there is still no joy in getting a clean build of fuppes in Ubuntu 9.10 :(

The problem that you are running into are interesting. Just to let you know I have two different versions of ffmpeg running on Ubuntu 9.10 and both are currently working with fuppes so your problem with libavformat surprised me to say the least. You should add this to the sourceforge bugs list and clearly state how we can reproduce this problem (like detailed steps for how you compiled ffmpeg; what options etc.).

Don't despair, there is a way to make it work, I am sure.

> **s1500 said:**
> What is the stance on distributing binaries of the fuppes daemon on sourceforge, etc? Or would compiled binaries not work on every system due to library dependencies?

Yes, it is dependent on certain libraries being present, therefore it would be wrong of us to just release binaries. I believe that the decision is to wait until fuppes can be made into a clean and stable debian package before we will provide it on the sourceforge site. (Though this question would have been better placed on the sourceforge forums)

---

### Post by twisted_steel on 2009-11-24
> **dbccos said:**
> Is it still necessary to compile ffmpeg from source? If so please provide the options used to enable support for video transcoding and such for the xbox 360.

I don't think it is still necessary to build x264 and ffmpeg from scratch.  I know it was in one of the earlier Ubuntu versions because support was not part of the default packages.

I managed to get fuppes from svn (rev. 648 to compile) with the following configure line:
```
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --prefix=/usr
```I have not tested it yet, but it does compile and I was able to install it via checkinstall.  I never compiled any other package from source and installed a ton of other packages.  I basically used the list from [the wiki page]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux"), but searched through Synaptic because the list was outdated.  I probably should have written it down, but I did not.  I don't have time tonight to try to figure it out again.

This is what my configure output looks like:
```
  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : no
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : disabled
    ImageMagick   : disabled (Wand C-API)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : enabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled
    inotify    : enabled
```

EDIT:
I have the following avformat packages installed: libavformat52, libavformat-dev.  I am running 64-bit.

---

### Post by PorchSong on 2009-11-25
> **twisted_steel said:**
> I don't think it is still necessary to build x264 and ffmpeg from scratch.  I know it was in one of the earlier Ubuntu versions because support was not part of the default packages.

I managed to get fuppes from svn (rev. 648 to compile) with the following configure line:
```
./configure --enable-lame --enable-twolame --enable-mad --enable-faad --prefix=/usr
```I have not tested it yet, but it does compile and I was able to install it via checkinstall.  I never compiled any other package from source and installed a ton of other packages.  I basically used the list from [the wiki page]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux"), but searched through Synaptic because the list was outdated.  I probably should have written it down, but I did not.  I don't have time tonight to try to figure it out again.

This is what my configure output looks like:
```
  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : no
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : disabled
    ImageMagick   : disabled (Wand C-API)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : enabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled
    inotify    : enabled
```

EDIT:
I have the following avformat packages installed: libavformat52, libavformat-dev.  I am running 64-bit.

Here is my quick two cents:  

Are you trying to install fuppes *after* you installed ffmpeg from this thread?

**HOWTO: Install and use the latest FFmpeg and x264**

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If so, fuppes and the latest ffmpeg/x264 codecs don't play well with regard to fuppes installs.

Go back to that thread and purge/delete per instructions, then reinstall fuppes.  After you have fuppes installed, then you can go back to that thread and reinstall ffmep/x264.

I seem to remember running into your problem in the past, and hunted down to the "latest ffmpeg/x264" install thread.

I am also on x64 and everything is running fine.

---

### Post by graabein on 2009-11-27
I have a PS3 and I'm using [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/"). It leaves me wanting more as I plan to get a NAS with GNU/Linux on it and I'd rather not install too many libs. Besides the ps3mediaserver can't transcode everything I throw at it (or maybe it's my codecs, the network or the PS3's fault, either way I can't see everything). So I was thinking I'd give Fuppes a shot. I'll be watching this spot. Go Shhnap! :)

---

### Post by Shhnap on 2009-12-03
Thanks graabein; I'm happy to help. I just hope and many people as possible can enjoy it.

Also letting people know that revisions are going to start coming out more regularly so you might want to check it out once every week or two. All ffmpeg issues should have been solved by the latest patch.

---

### Post by reddevil2064 on 2009-12-05
> **Shhnap said:**
> Thanks graabein; I'm happy to help. I just hope and many people as possible can enjoy it.

Also letting people know that revisions are going to start coming out more regularly so you might want to check it out once every week or two. All ffmpeg issues should have been solved by the latest patch.

This is great to hear! After coming off of FreeNAS and using Fuppes for quite a while, I'm glad to hear development is finally picking back up!! I was tempted into purchasing Twonky but would rather stick with a true free and open program on my home server. Thanks!

---

### Post by finni100100 on 2009-12-07
im having issues using the make file fowling the steps in the tutorial on this [website]("http://server-servers.com/ubuntu-9-10-karmic-compile-fuppes-media-server-from-source/") wy out put is as follows 

```
jason@SRV01:~/fuppes$ make
Making all in m4
make[1]: Entering directory `/home/jason/fuppes/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jason/fuppes/m4'
Making all in include
make[1]: Entering directory `/home/jason/fuppes/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jason/fuppes/include'
Making all in src
make[1]: Entering directory `/home/jason/fuppes/src'
if test -e "../version.sh"; then \
        ../version.sh; \
    fi
make  all-am
make[2]: Entering directory `/home/jason/fuppes/src'
make[2]: Leaving directory `/home/jason/fuppes/src'
make[1]: Leaving directory `/home/jason/fuppes/src'
Making all in src/plugins
make[1]: Entering directory `/home/jason/fuppes/src/plugins'
make[1]: *** No rule to make target `encoder_lame.c', needed by `libencoder_lame_la-encoder_lame.lo'.  Stop.
make[1]: Leaving directory `/home/jason/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```

n00b at compileing software and any help would be appreciated. my enviroment is Ubuntu 9.10 server AMD64 with ubuntu desktop added kernal linux 2.6.31-16 GNOME 2.28.1  2.0 GiB ram AMD Athlon 64 Processor 3200+

---

### Post by Shhnap on 2009-12-07
That looks like a nicely written tutorial but it is not as recent as it could be. For example, the latest svn revision no longer requires the gcc hacks. More importantly, the guide wants you to run the entire install as root which I would not recommend. Could I suggest that you try the instructions on the very first post of this thread. They are pretty good.

But when it comes down to it all you should really need to do for Ubuntu Karmic (it works on all my machines) is what the first page of the wiki ([http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux)) says:

```
$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes/
$ autoreconf -vfi
$ ./configure --with-your-options-here --help
$ make
$ sudo make install
```

And in those steps the only thing you have to do is choose your configure options. Though a minimal ./configure should just work.

Let me know if that is successful. (Please note that the only step to run as root is the make install) 

I hope this helps.

---

### Post by finni100100 on 2009-12-08
thanks for the reply i had tried doing it the way you had it posted and i was having problems the first time it was working for my ps3 i streamed one video to it and then went to watch another and it went heywire and wouldnt work any more so i tried reinstalling again and it just spiraled down hill from there then i installed 9.10 server to see if that helped with it any and this is were i am now. and i was also wondering once i get it working if anyone has the setting needed to get it to stream to a Directv HDDVR if i remember correctly they require the stream to be as a MPEG2 file 

Thanks finni

---

### Post by Shhnap on 2009-12-08
Can I know what you were having problems with? And have you considered sending in a [Bug Report]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Reporting_Bugs")?

So,
[LIST=1]
[*]What file type were you trying to send to your PS3?
[*]Can you describe what you mean by Haywire?
[/LIST]

Thanks, and to can change your transcoding settings in the fuppes.cfg file (only if you configured with the --enable-transcoder-ffmpeg flag) in order to transcode on the fly to MPEG2. That is described on the fuppes wiki (but could probably be made more clear).

---

### Post by reddevil2064 on 2009-12-10
Shhnap,

Are your updates getting pushed out to the BSD version of Fuppes as well? I'm just wondering as I'm a freenas user, and don't mind doing some manual updates as well...

---

### Post by Shhnap on 2009-12-10
Were just working on the source ATM. Minor fixes and improvements, but the beginnings of bigger changes to come. It's all in the TODO list I believe. Continuing to make it compatible with all operating systems is obviously a major priority to fuppes. We will put effort into making sure that it works from source on BSD and I am looking at packaging now for Debian distributions; the others will come after that. 

I hope this makes things clearer.

---

### Post by reddevil2064 on 2009-12-10
> **Shhnap said:**
> Were just working on the source ATM. Minor fixes and improvements, but the beginnings of bigger changes to come. It's all in the TODO list I believe. Continuing to make it compatible with all operating systems is obviously a major priority to fuppes. We will put effort into making sure that it works from source on BSD and I am looking at packaging now for Debian distributions; the others will come after that. 

I hope this makes things clearer.

Excellent! I'm working on compiling for 'buntu karmic now, and will report back with bugs hopefully. What are you exactly changing with the development? Just wondering, Fuppes has been great for me in its current form even with no transcoding.

---

### Post by Shhnap on 2009-12-10
> Excellent! I'm working on compiling for 'buntu karmic now, and will report back with bugs hopefully.

Yeah if you do check out revision 650 and not 651. I think 651 is missing a file that will make your compile fail (encoder_lame.c i think). So yeah, I've got it but I won't distribute it like this, I've asked Ulrich to add it back in which I am sure he will do very soon.

Also, it's all in the TODO list, but I'm planning on:

 - Adding an interface for config utils to connect to, so you don't just have to use the web interface to configure fuppes.
 - Adding more playlist support
 - Crossing off more bugs and refactoring code.
 - Looking into making the database more efficient.

The list goes on. :) I'm about to get some time to work on it but for now it just depends on what Ulrich and I have time to do.

---

### Post by reddevil2064 on 2009-12-10
> **Shhnap said:**
> Yeah if you do check out revision 650 and not 651. I think 651 is missing a file that will make your compile fail (encoder_lame.c i think). So yeah, I've got it but I won't distribute it like this, I've asked Ulrich to add it back in which I am sure he will do very soon.

Also, it's all in the TODO list, but I'm planning on:

 - Adding an interface for config utils to connect to, so you don't just have to use the web interface to configure fuppes.
 - Adding more playlist support
 - Crossing off more bugs and refactoring code.
 - Looking into making the database more efficient.

The list goes on. :) I'm about to get some time to work on it but for now it just depends on what Ulrich and I have time to do.

Good to hear! Nice to see the project active again. I've got an error with minimum dependencies apparently (This is running in a clean karmic  64bit VM that has been following the guide in this thread to the letter). My libpcre seems to be out of date.
Says:
```
line 16311: syntax error near unexpected token 'PCRE,'
line 16311: 'PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'
```

It's not allowing me to configure for a makefile. Seems strange since I've installed everything fresh. Thoughts? Or is this some simple mistake I've made?

EDIT: I checked out svn 650 and still am encountering this error except the line it occurs on changes to 16314. I'll go back and clear my install once again and retry.

EDIT:EDIT: Found my problem forgot to apt-get install pkg-config. Simple googling solved my problem.

---

### Post by Shhnap on 2009-12-10
I'm really happy to hear that fuppes is working well for you. :D 

As for the error, I believe that [you are missing pkg-config]("http://ubuntuforums.org/showpost.php?p=4284740&postcount=8"). Try,

```
sudo apt-get install pkg-config
```

Please let me know if that works. I hope it helps.

P.S. After that try another:

```
autoreconf -vfi
./configure --with-options
make
sudo make install
```

---

### Post by reddevil2064 on 2009-12-11
> **Shhnap said:**
> I'm really happy to hear that fuppes is working well for you. :D 

As for the error, I believe that [you are missing pkg-config]("http://ubuntuforums.org/showpost.php?p=4284740&postcount=8"). Try,

```
sudo apt-get install pkg-config
```

Please let me know if that works. I hope it helps.

P.S. After that try another:

```
autoreconf -vfi
./configure --with-options
make
sudo make install
```

Worked great! Now if I can just get my xbox and PS3 to see the darn thing. Living 80 miles (around 129 km) away from my home server with my working FreeNAS and Fuppes makes it a pain to get the cfg files. (SSH works, but we are on a very crappy wireless connection out there so file transfer is iffy). I'll do what I can tomorrow, maybe throw a new config on this VM and see if that works. fuppes.cfg and the vfolder.cfg from my freenas install (svn 640) should do the trick! 

I'm really excited about this, I'm moving from a crappy dell desktop with 1gig of ram and 3ghz cpu to a Dual 3.4ghz Xeon with 6gb of ram and several tb's of storage. Has 4 Gigabit NICs and I plan on using it for backups and streaming media. FreeNAS was great, but just couldn't meet my hardware support needs. Hopefully with the respin of that project they catch back up.

---

### Post by Shhnap on 2009-12-11
Hi, that's really good, it's now working for you. Let me know if you have any further problems. Also, I recommend that you compile with the latest source possible. At the time of writing that would be svn 653 and it is he most upto date.

---

### Post by reddevil2064 on 2009-12-11
> **Shhnap said:**
> Hi, that's really good, it's now working for you. Let me know if you have any further problems. Also, I recommend that you compile with the latest source possible. At the time of writing that would be svn 653 and it is he most upto date.

I'll start compiling and testing at work. Do you want me to enable transcoding or just stick with the basics. And as far as the ./configure goes, do you want me to throw any specific switches?

UPDATE: SVN 653 compiled with no issues and works great default out of the box. Have it streaming to 2 PCs and 1 Mac right now.

UPDATE2: It's been a while since I've read the UPnP spec, what defines a UPnP friendly name? I remember something about it requiring a colon (which is why the xbox 360 section is so crazy looking) but can't remember specifically what was required. I've got a single name (Intrepid) right now and it seems to work on two Windows 7 machines.

---

### Post by Shhnap on 2009-12-11
> **reddevil2064 said:**
> 
UPDATE: SVN 653 compiled with no issues and works great default out of the box. Have it streaming to 2 PCs and 1 Mac right now.

Excellent. :) Too easy.

> **reddevil2064 said:**
> UPDATE2: It's been a while since I've read the UPnP spec, what defines a UPnP friendly name? I remember something about it requiring a colon (which is why the xbox 360 section is so crazy looking) but can't remember specifically what was required. I've got a single name (Intrepid) right now and it seems to work on two Windows 7 machines.

The friendly name is just supposed to be a human readable description of your UPnP server. You should be allowed to change it to be anything you want. If the XBox config setting are showing anything crazy and it's required then it's probably because XBox made a mistake or did not follow spec. (However, in this case, I believe that you can change that friendly name for Xbox. I seem to rememeber that it caused no problems for me.) So using just 'Intrepid' should be fine. :)

---

### Post by reddevil2064 on 2009-12-11
> **Shhnap said:**
> Excellent. :) Too easy.



The friendly name is just supposed to be a human readable description of your UPnP server. You should be allowed to change it to be anything you want. If the XBox config setting are showing anything crazy and it's required then it's probably because XBox made a mistake or did not follow spec. (However, in this case, I believe that you can change that friendly name for Xbox. I seem to rememeber that it caused no problems for me.) So using just 'Intrepid' should be fine. :)
Ah, excellent. For some reason I thought the 360 wasn't following the spec completely (which it still may not). I haven't had a chance to stop by my place (2 360's and 2 ps3's to stream to) to give it a test, but every software player I can throw at it has worked great. Keep 'em coming! I don't mind testing at all, might be getting my hands on some other renderers soon.

---

### Post by rizman on 2009-12-12
Hi there,
First, thanks for continuing the development of fuppes. Great piece of software.

I managed to get fuppes working under Ubuntu Server 9.10 and my Xbox 360 sees and plays videos and music just fine.

However, I have my TV_Shows organised like this:
Show1
    Season 1
        Episode files
Show2
    Season 1
        Episode files
    Season 2
        Episode files
Show 3
    Season 1
        Episode files
    Season 2
....

What I see on the Xbox is this:

Season 1
    Episode files of Show 1
Season 1
    Episode files of Show 2
Season 1
    Episode files of Show 3
Season 2
    Episode files of Show 2
Seaons 2
    Episode files of Show 3
...

So, it looks like fuppes does not show the whole directory structure, but only the last level of folders or is there somethin I can change in the cfg files to enable this?

I have them organised this way because I also use XBMC which out of the box expects this folder structure for its scraper to work.

Does anyone have an advice on this?

---

### Post by reddevil2064 on 2009-12-12
> **rizman said:**
> Hi there,
First, thanks for continuing the development of fuppes. Great piece of software.

I managed to get fuppes working under Ubuntu Server 9.10 and my Xbox 360 sees and plays videos and music just fine.

However, I have my TV_Shows organised like this:
Show1
    Season 1
        Episode files
Show2
    Season 1
        Episode files
    Season 2
        Episode files
Show 3
    Season 1
        Episode files
    Season 2
....

What I see on the Xbox is this:

Season 1
    Episode files of Show 1
Season 1
    Episode files of Show 2
Season 1
    Episode files of Show 3
Season 2
    Episode files of Show 2
Seaons 2
    Episode files of Show 3
...

So, it looks like fuppes does not show the whole directory structure, but only the last level of folders or is there somethin I can change in the cfg files to enable this?

I have them organised this way because I also use XBMC which out of the box expects this folder structure for its scraper to work.

Does anyone have an advice on this?

Yes, it is related to your virtual folder configuration. The fuppes wiki explains how you can tweak it to display things differently but I believe there needs to be a folder titled TV Shows. 

My vfolder.cfg file looks like:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">
 <vfolder_layout device="default" enabled="false">
    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem"/>
      </vfolders>
    </vfolder>
    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem"/>
        </vfolders>
      </vfolders>
    </vfolder>
    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem"/>
        </vfolders>
      </vfolders>
    </vfolder> 
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem"/>
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem"/>
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)"/>
      </vfolder>      
    </vfolder>
    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem"/>
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)"/>
      </vfolder>
    </vfolder>
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true"/>
    </vfolder>
  </vfolder_layout>
  <vfolder_layout device="Microsoft_XBox360" enabled="true" create_references="true" create_container_details="true">
    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album">
          <items type="audioItem"/>
        </vfolders>
      </vfolder>
      <vfolder name="All Music" id="4">
        <items type="audioItem"/>
      </vfolder>
      <vfolder name="Artist" id="6">
        <vfolders property="artist">
          <items type="audioItem"/>
        </vfolders>
      </vfolder>
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)"/>
      </vfolder>
      <vfolder name="Genre" id="5">
        <vfolders property="genre">
          <items type="audioItem"/>
        </vfolders>
      </vfolder>
      <vfolder name="Playlist" id="15"/>
    </vfolder>
    <vfolder name="Pictures" id="3">
      <!--
      <vfolder name="Album" id="13" />
      -->
      <vfolder name="All Pictures" id="22">
        <items type="imageItem"/>
      </vfolder>
      <vfolder name="Date Taken" id="12"/>
      <!--
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
      -->
    </vfolder>
    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19"/>
      <vfolder name="Folders" id="23"/>
    </vfolder>
    <vfolder name="Video" id="2">
      <!--
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      -->
      <vfolder name="All Video" id="21">
        <!--
        <items type="videoItem" />
        -->
        <shared_dirs full_extend="true"/>
      </vfolder>
      <!--
      <vfolder name="Folders" id="21">
         <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
      -->
    </vfolder>
  </vfolder_layout>
  <vfolder_layout device="Yamaha_RXN600" enabled="false" create_references="true">
    <vfolder name="Playlists"/>
    <vfolder name="Artists">
      <vfolders property="artist">
        <items type="audioItem"/>
      </vfolders>
    </vfolder>
    <vfolder name="Albums">
      <vfolders property="album">
        <items type="audioItem"/>
      </vfolders>
    </vfolder>
    <vfolder name="Songs">
      <items type="audioItem"/>
    </vfolder>
    <vfolder name="Genres">
      <vfolders property="genre">
        <items type="audioItem"/>
      </vfolders>
    </vfolder>
  </vfolder_layout>
  <vfolder_layout device="Loewe_Connect" enabled="false">
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem"/>
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem"/>
        </vfolders>
      </vfolders>
    </vfolder>
    <vfolder name="Photo">
      <vfolder name="Alle">
        <items type="imageItem"/>
      </vfolder>
      <vfolder name="Folder">
        <folders filter="contains(imageItem)"/>
      </vfolder>
    </vfolder>
    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem"/>
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)"/>
      </vfolder>
    </vfolder>
  </vfolder_layout>
</fuppes_vfolder_config>

```

The xbox 360 section I believe is the one you will want to look at.
EDIT: I have my server folder layout configured the exact same way as you, so hopefully you have the same results as myself.

---

### Post by Cas07 on 2009-12-13
Thanks for the guide, really helped me along with [Server-servers]("http://server-servers.com/ubuntu-9-10-karmic-compile-fuppes-media-server-from-source/?utm_source=rss&utm_medium=rss&utm_campaign=ubuntu-9-10-karmic-compile-fuppes-media-server-from-source") guide to get Fuppes up and running. 

For reference I encountered an error "cannot find -lswscale" upon building which was related to libffmpegthumbnailer so disabled that feature in the configure options. I'm guessing that if upgraded to the latest FFMPEG it would resolve the issue.

I noticed that a lot of configure options are true by default so my command was shortened to this:
```
./configure --enable-transcoder-ffmpeg --enable-lame --enable-twolame --enable-mad -
-enable-faad --prefix=/usr/ --disable-ffmpegthumbnailer
```

In the Fuppes config I added device specific settings for my Nokia N900 and found the build-in media player has this user agent string:
```
<user_agent>GUPnP/0.12.8 DLNADOC/1.50</user_agent>
```

---

### Post by rizman on 2009-12-14
@reddevil2064: Thanks for the info. I'll try that later on as currently I'm facing another, more concerning problem.

I have about 500 single files in the TV Shows folder. When I just add that folder to fuppes, the database rebuild and virtual container rebuild work flawlessly. However, when I add my MP3 folder to it, which has about 2000 MP3 files (which I consider not very much compared to other people), at some point, fuppes crashes with a segmentation fault when rebuilding the database. The console doesn't tell me anything else, no stacktrace whatsoever. Is there some log file whith details of the error maybe?

Anyway, after restarting fuppes, I checked the status page on the webUI and it looks like around 1600 files in the database, the seg fault happens. 

FYI: Before switching to Ubuntu server a week ago, I had FreeNas 0.7 installed, and the fuppes version which came with that used up all the system's memory when building the virtual container. So I checked "top" when I ran the database rebuild, but couldn't notice a huge memory usage.

I'm using the latest svn revision as of this writing (I'm currently not at home so I can't check which on exactly it is)

---

### Post by reddevil2064 on 2009-12-14
> **rizman said:**
> @reddevil2064: Thanks for the info. I'll try that later on as currently I'm facing another, more concerning problem.

I have about 500 single files in the TV Shows folder. When I just add that folder to fuppes, the database rebuild and virtual container rebuild work flawlessly. However, when I add my MP3 folder to it, which has about 2000 MP3 files (which I consider not very much compared to other people), at some point, fuppes crashes with a segmentation fault when rebuilding the database. The console doesn't tell me anything else, no stacktrace whatsoever. Is there some log file whith details of the error maybe?

Anyway, after restarting fuppes, I checked the status page on the webUI and it looks like around 1600 files in the database, the seg fault happens. 

FYI: Before switching to Ubuntu server a week ago, I had FreeNas 0.7 installed, and the fuppes version which came with that used up all the system's memory when building the virtual container. So I checked "top" when I ran the database rebuild, but couldn't notice a huge memory usage.

I'm using the latest svn revision as of this writing (I'm currently not at home so I can't check which on exactly it is)
Have you set the permissions on the folder that contains your database? As a test I set mine to 777 then slowly cranked them down to a safe level. My music database is well over 2000 files and I had no issues with my fuppes seg faulting. Hopefully that helps!

---

### Post by rizman on 2009-12-14
> **reddevil2064 said:**
> Have you set the permissions on the folder that contains your database? As a test I set mine to 777 then slowly cranked them down to a safe level. My music database is well over 2000 files and I had no issues with my fuppes seg faulting. Hopefully that helps!

I have no clue how my persmissions are currently set on the database (still @work). I'll check it later this evening. However, as it runs for a certain time and adds about 1600 files, I doubt that it's a permission issue. If permissions were wrong, then it should already get stuck at the first item to add, shouldn't it?

---

### Post by reddevil2064 on 2009-12-14
> **rizman said:**
> I have no clue how my persmissions are currently set on the database (still @work). I'll check it later this evening. However, as it runs for a certain time and adds about 1600 files, I doubt that it's a permission issue. If permissions were wrong, then it should already get stuck at the first item to add, shouldn't it?

Possibly, all issues I had with adding large numbers of files were cleared up with a change in permissions on the folder holding my database though. Not sure if there are some other forces at work here. Maybe shnap can shed some light on this.

---

### Post by Shhnap on 2009-12-14
I agree that permissions should not be an issue. Al that should matter is that there is +rw access for the fuppes user all the way down the directory tree to (and including) the fuppes.db file.

As for having database issues, we recently had an issue with the recreation of the database causing a segfault, it happened on my machine too on svn653. I believe that Ulrich fixed it in svn654 but nothing beats testing it out (though the problem is not occurring for me anymore).

As for the size of the database becoming an issue, that usually happens at around 7000+ items and I'm looking at ways to fix that (it's an the TODO list already). But for 3000 items the database should handle that just fine, maybe it'll be a little slow rebuilding, it but it should not segfault.

If the problem persists once you are on the latest svn then please let me know. :) I'll be happy to help.
(Even better, if you know how to use gdb you could try and pinpoint it for us, but maybe I'm getting ahead of myself)

---

### Post by rizman on 2009-12-15
Unfortunately, I didn't have the time to test your suggestions yesterday evening. I'll have to wait until tonight.

@Shhnap: If memory serves me well, I believe I'm running SVN 654, and still the rebuild is segfaulting. I haven't used gdb as I never developed anything on Linux/Unix. However, I've been a profesionnal .NET developer for about 4 years and currently I'm still doing some things here and there. So I'm not unfamiliar with debugging. I guess that I should be able (after a quick gdb tutorial) to figure out how to use it. 
I'm running Ubuntu server, so no GUI for me, but I can handle the console :-)

Speaking of Ubuntu server: That wouldn't be an issue for fuppes? I mean, fuppes being picky because it ain't running on a desktop edition? Again, I'm not that familiar with Linux architecture, but if I get it right, the base OS (like kernel etc...) is the same for all Ubuntu versions, it's just the installed packages which change, right? 

Well anyway, I'll report back if I get any results. In the meantime, maybe someone can give me some hints on how to start with gdb? Maybe there is a fuppes log which I could send th you Shhnap?

---

### Post by Shhnap on 2009-12-15
> **rizman said:**
> If memory serves me well, I believe I'm running SVN 654, and still the rebuild is segfaulting. I haven't used gdb as I never developed anything on Linux/Unix. However, I've been a profesionnal .NET developer for about 4 years and currently I'm still doing some things here and there. So I'm not unfamiliar with debugging. I guess that I should be able (after a quick gdb tutorial) to figure out how to use it. 
I'm running Ubuntu server, so no GUI for me, but I can handle the console :-)

I have confidence that you can learn gdb fairly quickly. It's an awesome tool and there are plenty of tutorials around. Since your problem is a segfault why not try this tutorial: [http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html](http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html)

> **rizman said:**
> Speaking of Ubuntu server: That wouldn't be an issue for fuppes? I mean, fuppes being picky because it ain't running on a desktop edition? Again, I'm not that familiar with Linux architecture, but if I get it right, the base OS (like kernel etc...) is the same for all Ubuntu versions, it's just the installed packages which change, right?

I have a few points saying why this should not be an issue:
[LIST=1]
[*]You are correct as far as I know, the only differences bettween the Server and Desktop editions of Ubuntu are the packages installed.
[*]I am running Ubuntu Server and fuppes works very well on it.
[*]Fuppes also works on gentoo, bsd, fedora and even windows. Compared to those differences the difference bettween Ubuntu Server and Desktop editions would be minimal.
[/LIST] 
In conclusion I believe that you are very Unlikely to come across a bug caused by the difference.

> **rizman said:**
> Well anyway, I'll report back if I get any results. In the meantime, maybe someone can give me some hints on how to start with gdb? Maybe there is a fuppes log which I could send th you Shhnap?

My suggestion would be to:
[LIST]
[*]Follow that gdb link that I sent you above.
[*]Debug the problem.
[*]Make a bug report according to the <[Reporting Bugs page on the wiki]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Reporting_Bugs")>.
[/LIST]

The Reporting Bugs is really the instructions that anybody with a fuppes bug should follow; it will even show you how to make a fuppes log file. :)

I hope that helps you and anyone with a bug with fuppes, and I'd be interested to see any gdb output. :D

---

### Post by ask21900 on 2009-12-15
Can anyone give me instructions on how to remove everything that has to do with fuppes (all installations).  I am quite the n00b, and tried installing using a tutorial I found.  That didn't work, so I used another, etc.  When I finally found this one, I got it to work for a few hours, but when I tried using the wiki tutorial to switch over to init.d it stopped reading the db (http and upnp works, but no files show up).

I am thinking that the various "fuppes" and ".fuppes" folders I have on my machine are creating conflicts and not updating the proper db files.  I think it would be easier to take everything out, and start from scratch rather than track down what is actually happening (unless someone could give me instructions on where to go from here).

Thanks in advance!

Regards,

David

---

### Post by Shhnap on 2009-12-15
I'll give you some help in private chat but my essential message is that everything to do with fuppes should contain fuppes. Therefore, in order to remove it all, all you need to do is run:

```

sudo make uninstall
find ~/ -name "fuppes" -exec rm -f {} \;
```
**WARNING: Be really careful with the above command because it will delete stuff since it contains an 'rm'**

Maybe do this first to see what you will delete:
```
find ~/ -name "fuppes"
```

---

### Post by yester64 on 2009-12-16
Hi,

i installed fuppes like it was shown here.
Still, i have some questions.

1) i got this in the terminal. Not sure what to make of it.
```
:1: namespace error : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
```

2) this shows up also in the terminal
```
[NULL @ 0x2aa14e0]Invalid and inefficient vfw-avi packed B frames detected

```
and
```
TagLib: MPEG::Header::parse() -- Invalid sample rate.

```

and last, the content will be available once i make the virtual container. Because it does not show up so far.

Ok, other than that it runs already and i watch the status :)

---

### Post by ask21900 on 2009-12-16
> **yester64 said:**
> 
1) i got this in the terminal. Not sure what to make of it.
```
:1: namespace error : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
```


I am getting this same error.  Shhnap is helping me track this down in private chat, but I believe that everything worked fine, even with this error.

> **yester64 said:**
> 
2) this shows up also in the terminal
```
[NULL @ 0x2aa14e0]Invalid and inefficient vfw-avi packed B frames detected

```
and
```
TagLib: MPEG::Header::parse() -- Invalid sample rate.

```



This is also the message I get as my db was populated.  I do specifically remember these same occurrences on a prior install which DID work, so I am sure this is nothing to worry about.


David

---

### Post by rizman on 2009-12-16
@Shhnap:
I followed your link for gdb and was able to figure out where the error is happening. Though I haven't had the time to check the source. Currently, my internet connection is broken at home, so I can't post a bug on sourceforge from there and somehow at work I'm not able to log into sourceforge. Therefore, I'll have to post the gdb output screenshots here.
I hope they'll be usefull.

Here is the gdb output just after the segfault.
[http://i765.photobucket.com/albums/xx296/muppusch/Segfault1.jpg](http://i765.photobucket.com/albums/xx296/muppusch/Segfault1.jpg)

Here is the output of all the available frames after a backtrace
[http://i765.photobucket.com/albums/xx296/muppusch/Segfault2.jpg](http://i765.photobucket.com/albums/xx296/muppusch/Segfault2.jpg)

As a reminder: The segfault occurs when I rebuild/update the database. What I noticed yesterday is that it actually finishes (at least I think) the database population. Before the segfault there is always a message which gets output to the console: "[DONE] read shared directories" So my guess is that it actually does finish the process and segfaults afterwards. 

@yester64: I also get A LOT of those messages. No idea if that is related to my other problem.

---

### Post by Shhnap on 2009-12-16
> **rizman said:**
> @Shhnap:
I followed your link for gdb and was able to figure out where the error is happening. Though I haven't had the time to check the source. Currently, my internet connection is broken at home, so I can't post a bug on sourceforge from there and somehow at work I'm not able to log into sourceforge. Therefore, I'll have to post the gdb output screenshots here.
I hope they'll be usefull.

Here is the gdb output just after the segfault.
[http://i765.photobucket.com/albums/xx296/muppusch/Segfault1.jpg](http://i765.photobucket.com/albums/xx296/muppusch/Segfault1.jpg)

Here is the output of all the available frames after a backtrace
[http://i765.photobucket.com/albums/xx296/muppusch/Segfault2.jpg](http://i765.photobucket.com/albums/xx296/muppusch/Segfault2.jpg)

As a reminder: The segfault occurs when I rebuild/update the database. What I noticed yesterday is that it actually finishes (at least I think) the database population. Before the segfault there is always a message which gets output to the console: "[DONE] read shared directories" So my guess is that it actually does finish the process and segfaults afterwards.

Lol whoops, so the part of the code that is segfaulting is a part that I recently rewrote. The segfault is occurring for you when your playlists are parsed. So can I ask for two things:

[LIST=1]
[*]Are you using .wpl playlists? (They are what I recently added support for)
[*]Can you send me your playlist files? My email can be found on the fuppes wiki [(Robert Massaioli)]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=User:Robertmassaioli").
[/LIST]

Thanks a million for doing that GDB stuff though, that was more helpful than you could imagine. I was able to pinpoint exactly what variable was segfaulting from the information you provided. Now I just need to see which playlist file type caused it.

And as for "I hope they'll be usefull." Yes!!! So useful, really I wish that every bug came with a backtrace like the one you provided, if everybody did that then the time it took to solve bugs would be halved.

Thanks again,
Robert

---

### Post by rizman on 2009-12-17
Unfortunately, I wasn't at my computer yesterday evening, so I couldn't check which playlists I have and I don't really know because I never use them. I just shuffle on about every song I have in my library :-) Though I know that some playlists are present. 

After I debugged, I figured that the playlists where causing problems as the error happened in PlaylistParser.cpp, so for the sake of testing, I removed all the *.m3u playlists from my mp3 library (i.e. physically moved them to a different location on the file system). However, that didn't help. The rebuild did still segfault. I haven't thought of trying different playlist formats.

> 
Are you using .wpl playlists? (They are what I recently added support for)

I'll have to check. As I said, I usually don't use playlists, but some actually DO hang around :-)

> 
Can you send me your playlist files? My email can be found on the fuppes wiki [(Robert Massaioli)]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=User:Robertmassaioli").

Will do

> 
Thanks a million for doing that GDB stuff though, that was more helpful than you could imagine. I was able to pinpoint exactly what variable was segfaulting from the information you provided. Now I just need to see which playlist file type caused it.

And as for "I hope they'll be usefull." Yes!!! So useful, really I wish that every bug came with a backtrace like the one you provided, if everybody did that then the time it took to solve bugs would be halved.


You're welcome. As I said earlier, I've been a developer for a few years, so I know how painful it can be to track down bugs when someone just tells you that "It doesn't work" :-)

And thanks to you too for taking on the challenge to develop (or rather continue developing) fuppes.

---

### Post by Shhnap on 2009-12-17
Just incase anybody else is having the same problem it has been fixed as of now and will be present in the next release svn655.

---

### Post by Zeikcied on 2009-12-17
Okay, now I'm having problems.

A week or so ago, I bought and downloaded some music from the Amazon.com MP3 store.  Since my Amazon MP3 folder is included in the Fuppes database, I wanted to make sure that it had the new stuff.  So after I started Fuppes via the terminal, I typed "u" (without quotes) and hit Enter, as that's supposed to update the database.

When I then connected via my Xbox 360, it doesn't show any files.  I tried looking at it via my PS3 (the IP of which is also allowed, same as my 360) and it wasn't even showing a Fuppes share on the Music or Video tab.

I tried to Rebuild the database, but that didn't help, either.  The 360 does show the Fuppes service, but when it connects it doesn't list anything.  The PS3 doesn't even show Fuppes.

Somehow I broke things.  I tried stopping Fuppes, deleting the database, and restarting it again, but that didn't work.  Before all this, I was able to shut down Fuppes and restart it a day later without any trouble.  But ever since I tried getting it to recognize and list new additions, it's not listing anything.  I did nothing to the config files or anything.

I'm lost.

---

### Post by Jochem2911 on 2009-12-18
Oké, I got fuppes working on my Ubuntu Server 9.10.
Well, it works, but i get a bunch of parser errors.

like this :
```

:25: parser error : Premature end of data in tag root line 2
		<serviceId>urn:
		               ^

```

The line number is different every time an error comes up.

Any1 know what this means or how I can prevent this ?

---

### Post by TurboZinc on 2009-12-19
Not sure what i'm doing wrong here.
I did
```
$ sudo apt-get install autoconf automake gettext
```which seemed to work, but when i try to autoreconf -vfi i get this

```
$ autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4
aclocal: configure.ac:4: file `m4/version.m4' does not exist
autoreconf: aclocal failed with exit status: 1
```

---

### Post by jimmij01 on 2009-12-19
Bump

---

### Post by chanman on 2009-12-19
> **TurboZinc said:**
> Not sure what i'm doing wrong here.
I did
```
$ sudo apt-get install autoconf automake gettext
```which seemed to work, but when i try to autoreconf -vfi i get this

```
$ autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4
aclocal: configure.ac:4: file `m4/version.m4' does not exist
autoreconf: aclocal failed with exit status: 1
```

I commented out line 4 in the configure.ac file
```
#m4_include([m4/version.m4])
```

This let it compile

---

### Post by jimmij01 on 2009-12-19
I now get this error:

lib/HTTP/HTTPServer.cpp:35:47: error: ../DeviceSettings/MacAddressTable.h: No such file or directory
lib/HTTP/HTTPServer.cpp:400:2: warning: #warning todo: clear unfinished sessions
lib/HTTP/HTTPServer.cpp: In constructor ‘CHTTPServer::CHTTPServer(std::string)’:
lib/HTTP/HTTPServer.cpp:153: error: ‘MacAddressTable’ has not been declared
lib/HTTP/HTTPServer.cpp: In destructor ‘virtual CHTTPServer::~CHTTPServer()’:
lib/HTTP/HTTPServer.cpp:161: error: ‘MacAddressTable’ has not been declared
make[2]: *** [HTTPServer.lo] Error 1

---

### Post by TurboZinc on 2009-12-19
> **jimmij01 said:**
> I now get this error:

lib/HTTP/HTTPServer.cpp:35:47: error: ../DeviceSettings/MacAddressTable.h: No such file or directory
lib/HTTP/HTTPServer.cpp:400:2: warning: #warning todo: clear unfinished sessions
lib/HTTP/HTTPServer.cpp: In constructor ‘CHTTPServer::CHTTPServer(std::string)’:
lib/HTTP/HTTPServer.cpp:153: error: ‘MacAddressTable’ has not been declared
lib/HTTP/HTTPServer.cpp: In destructor ‘virtual CHTTPServer::~CHTTPServer()’:
lib/HTTP/HTTPServer.cpp:161: error: ‘MacAddressTable’ has not been declared
make[2]: *** [HTTPServer.lo] Error 1
Getting the same thing

---

### Post by Shhnap on 2009-12-20
Sorry about that. There were a few files that should have been added to the svn656 but are now present in svn657. Revert and changes you have made via 'svn revert' and then do a 'svn up' and you should have no more problems.

Sorry for the delayed response. Things are getting busy around Christmas, I'm sure you understand. :)

---

### Post by akutz on 2009-12-20
Just FYI - this works on Ubuntu Server 9.10 as well, but I had to install quite a few libraries and headers. The bug that I've found is that you cannot configure a prefix other than /usr. I would prefer to install it at /opt/fuppes, but the configure script won't find the taglib-config and mpeg4ip-config commands. If I set the prefix to /usr then the configure script finds everything less the simage plug-in since I read it has issues and did not install it.

---

### Post by Cas07 on 2009-12-20
> **akutz said:**
> The bug that I've found is that you cannot configure a prefix other than /usr.

I noticed that too but forgot to mention it.

[QUOTE=Shhnap]
--plugin=/usr/
[/QUOTE]

I saw the above option included as an example configure line but when i tried it, configure complained that it wasn't valid. I guess if this worked it would be the solution to the above bug.

---

### Post by akutz on 2009-12-20
FYI - you can fix the ffmpegthumbnailer / swscale compile bug with this symlink:

ln -s /usr/lib/libswscale.so.0 /usr/lib/libswscale.so

Then swscale is detected during compilation.

---

### Post by akutz on 2009-12-20
This is a hack to fix the prefix problem where you cannot specify a prefix other than /usr. Simply edit the configure.ac file and look for the lines:

AC_PATH_PROG(TAGLIB_CONFIG, taglib-config, no, $prefix/bin/)

and

AC_PATH_PROG(MPEG4IP_CONFIG, mpeg4ip-config, no, $prefix/bin/)

Change them to

AC_PATH_PROG(MPEG4IP_CONFIG, mpeg4ip-config, no, /usr/bin/)

and 

AC_PATH_PROG(TAGLIB_CONFIG, taglib-config, no, /usr/bin/)

(/usr/bin is the default path for those commands in Ubuntu)

Now re-run your autoconf script per the first post on this thread and the next time you run configure you can specify any prefix you wish.

---

### Post by yester64 on 2009-12-20
How long does Fuppes build a database? I have it run for one day and its still building.
Have a lot of files (over 40000).

---

### Post by Shhnap on 2009-12-20
> **akutz said:**
> Just FYI - this works on Ubuntu Server 9.10 as well, but I had to install quite a few libraries and headers. The bug that I've found is that you cannot configure a prefix other than /usr. I would prefer to install it at /opt/fuppes, but the configure script won't find the taglib-config and mpeg4ip-config commands. If I set the prefix to /usr then the configure script finds everything less the simage plug-in since I read it has issues and did not install it.

I run ubuntu server and I found the install almost the same as the desktop edition. The /usr issue is a bug and I think i'll be looking to fix it for the next release. Maybe by looking in /usr/bin first and then around for taglib and mpeg4ip. Thanks for reminding me.

> **akutz said:**
> FYI - you can fix the ffmpegthumbnailer / swscale compile bug with this symlink:

ln -s /usr/lib/libswscale.so.0 /usr/lib/libswscale.so

Then swscale is detected during compilation.

That's interesting, I'll pass that on to Ulrich because he is dealing with ffmpegthumbnailer atm. Thanks.

> **yester64 said:**
> How long does Fuppes build a database? I have it run for one day and its still building.
Have a lot of files (over 40000).

Yeah, the database is known to be slow for more than 7000 items. Sorry. It is on my todo list but it will not make it out before the next for-windows-as-well release. It will be a rather large change that will require some testing.

---

### Post by TurboZinc on 2009-12-21
I can get my xbox to see fuppes, but i'm having some problems with some of the details.

My mp3's only show up under all songs. The artist, album, genre, etc tabs are empty. I'm thinking the metadata isn't being read.

Also, under the video tab, my music and pictures folders show up. All the files have video listed under them, but obviously won't play. Is this normal or the same as above.

The is what i get when typing i at the command line when running fuppes
```
plugin dir: 
/usr/lib/fuppes/

registered plugins
database:
  "sqlite3"    library version: 3.6.16

misc:
  dlna-profiles

metadata:
  libavformat

transcoder:

audio decoder:

audio encoder:
  pcm
  wav


iconv: enabled
inotify: enabled
uuid: disabled

```

---

### Post by yester64 on 2009-12-21
It took fuppes around a 1 day to build my database. I have a lot of files.
My problem now is, that my xbox does not see fuppes, but fuppes sees the xbox.
Have to check my firewall, but ushare always worked. Strange.

---

### Post by Zeikcied on 2009-12-22
> **Zeikcied said:**
> Okay, now I'm having problems.

A week or so ago, I bought and downloaded some music from the Amazon.com MP3 store.  Since my Amazon MP3 folder is included in the Fuppes database, I wanted to make sure that it had the new stuff.  So after I started Fuppes via the terminal, I typed "u" (without quotes) and hit Enter, as that's supposed to update the database.

When I then connected via my Xbox 360, it doesn't show any files.  I tried looking at it via my PS3 (the IP of which is also allowed, same as my 360) and it wasn't even showing a Fuppes share on the Music or Video tab.

I tried to Rebuild the database, but that didn't help, either.  The 360 does show the Fuppes service, but when it connects it doesn't list anything.  The PS3 doesn't even show Fuppes.

Somehow I broke things.  I tried stopping Fuppes, deleting the database, and restarting it again, but that didn't work.  Before all this, I was able to shut down Fuppes and restart it a day later without any trouble.  But ever since I tried getting it to recognize and list new additions, it's not listing anything.  I did nothing to the config files or anything.

I'm lost.

I reinstalled Fuppes (maybe a newer version even), and I'm still having this issue.

I figured out why my PS3 wasn't seeing Fuppes.  In the Network Settings, I didn't have it set to look for media servers.  So I changed that setting, and my PS3 sees Fuppes and can play stuff off of my computer (though it sometimes gives an error saying that the content may have been deleted, even though it still plays the song).

My 360, though, still doesn't list any songs, albums, artists, etc.  It used to.  Back when I posted for help on Page 3 or 4, I got it to work perfectly with my 360.  But somehow last week it stopped working properly.

I don't get any error messages on the 360.  It seems to connect just fine.  I haven't done anything to the config file.  I did the network test on my 360, and it connected to my PC via the Fuppes listing.  But it doesn't list any of my media anymore. :confused:

---

### Post by PaulStat on 2009-12-22
Hi All,

Nice guide! I'm having some issues with Xbox 360 "seeing" Fuppes, when I try testing the "PC Connection" or the "Windows media center" connection, the 360 fails to detect the fuppes server.

Fuppes however can "see" the 360 as it's listed on the remote devices. Does anyone have any ideas why this might be? Here is my fuppes.cfg

```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/paul/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--These are examples of what data you can put between the ip tags where (* => anything, [x-y] => range)-->
      <!--<ip>192.168.0.1</ip>-->
      <!--<ip>192.168.0.[20-100]</ip>-->
      <!--<ip>192.168.0.*</ip>-->
      <!--<ip>192.*.[0-2].[40-*]</ip>-->
      <ip>192.168.0.4</ip>
      <ip>192.168.0.1</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
        <file ext="wpl">
          <type>PLAYLIST</type>
          <mime_type>application/vnd.ms-wpl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <!--This section is for the mime types that the makers of the XBox changed from standards.-->
      <file_settings>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config> 
```Any help is really really appreciated.

---

### Post by PaulStat on 2009-12-22
Aha! It's working now, although the Xbox sees it listed as "%s %v :1" How do I change that?

---

### Post by TurboZinc on 2009-12-22
> **PaulStat said:**
> Aha! It's working now, although the Xbox sees it listed as "%s %v :1" How do I change that?
What did you change to get it to work?

Change this line
```
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
```

It's the 7th line from the bottom of your fuppes.cfg file

---

### Post by PaulStat on 2009-12-23
> **TurboZinc said:**
> What did you change to get it to work?

Change this line
```
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
```It's the 7th line from the bottom of your fuppes.cfg file

My router has an inbuilt firewall, I needed to change some of the rules

---

### Post by TurboZinc on 2009-12-23
> **PaulStat said:**
> My router has an inbuilt firewall, I needed to change some of the rules
So are you getting songs showing up under the album, artist, genre sections in the music tab?

If so, what did your ./configure line look like?

---

### Post by ricardo81 on 2009-12-25
Hi everyone!

I'm trying to configure Fuppes to work as a Upnp server for a Revo Blik Wi-fi radio. This player is able to play Mp3, WAV, Wma among a few other formats.

I would like for Fuppes to transcode  other formats (FLAC, m4a, MPC and ogg) to WAV.

So this is how far I got:

Following this guide. I downloaded the latest version 0.657. Installed the dependencies (the dev versions), and ran the configure command. Which in summary reported that everything I wanted was enabled:

```

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : enabled
    inotify            : enabled
```

...then the problems start. During the make command there were some errors. Mad, faad and lame were not included. But in the end Fuppes got compiled and I executed it. The player connected to it. But it is only able to see mp3 files. Not the non-native formats(mpc, ogg etc)
This is what I get from the status webpage:


```
plugin dir: 
/usr/lib/fuppes/

database:
  "sqlite3"    library version: 3.6.16

misc:
  dlna-profiles

metadata:
  libavformat
  mp4v2
  taglib

transcoder:
  
audio decoder:
  FLAC
  musepack
  vorbis

audio encoder:
  pcm
  wav
```

So no transcoder plugins. Did anyone run in the same problems, or does anyone know what I may be doing wrong? Thanks for any help or information in advance.

---

### Post by Coollie on 2010-01-03
Hi all,

First of all, thanks to everyone who contributed on this post. After reading a lot of howto's and re-installing fuppes a bunch of times, I finally got Fuppes working quite well and I can access almost all of my files. Virtual containers are also properly set so that I can see my music catagorized. 
The only issue I'm struggling with is that I still can't stream mpg, vob or flv (xvid or divx are no problem) to my XBox 360 console. After the configuration step, the summary shows that video transcoding is configured.  Also transcoding is configured in my fuppes.cfg for the above file types. Can anybody help me out with the transcoding section or point me in the right direction? Thanks in advance.

Edit: When I browse with XBOX to my movies, de folder where mpg, vob or flv movies resides is empty. The XBOX doesn't see te files.

Edit 2: Did some searching and found the answer for this question: Which parameter must ./configure have to enable ffmpeg transcoding? Answer ./configure --enable-transcoder-ffmpeg. This used to be --enable-video-transcoding. Everywhere you look this parameter is still being used but this has changed. Also found what seems to be the right configuration for transcoding video.

System info: See server info in my Signature. Fuppes version 0.660. Here are my  fuppes.cfg, vfolder.cfg and configure summary files.

---

### Post by khadland on 2010-01-04
Hoping someone can help.

I've got fuppes up and running and it works really well serving to an Xbox 360.  Its actually very fast and responsive, noticeably over any other solution including windows.

The problem I do have though is with starting the server on restart.  I've set it up to startup with init.d by following this guide [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d).  On reboot is does start the daemon but it doesnt seem to work, almost like it started too early or something.  If I kill it and manually start it via init.d it works fine.

Also, should fuppes automatically update the database when files are modified?

Appreciate any help!
Thanks,
Kyle

---

### Post by Coollie on 2010-01-04
> **khadland said:**
> Hoping someone can help.

I've got fuppes up and running and it works really well serving to an Xbox 360.  Its actually very fast and responsive, noticeably over any other solution including windows.

The problem I do have though is with starting the server on restart.  I've set it up to startup with init.d by following this guide [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d).  On reboot is does start the daemon but it doesnt seem to work, almost like it started too early or something.  If I kill it and manually start it via init.d it works fine.

Also, should fuppes automatically update the database when files are modified?

Appreciate any help!
Thanks,
Kyle

Hi Kyle, I don't have that problem and yet i followed the same guide. Here's my fuppesd file. Compare it and see if it's the same. As for your second question you can create a cron job that can update the database every hour or so. Didn't configure that yet, maybe in the near future. Hopes this helps. Bytheway can you stream your vob, mpg of flv files? See my post (above).
GreeTz

---

### Post by khadland on 2010-01-04
> **Coollie said:**
> Hi Kyle, I don't have that problem and yet i followed the same guide. Here's my fuppesd file. Compare it and see if it's the same. As for your second question you can create a cron job that can update the database every hour or so. Didn't configure that yet, maybe in the near future. Hopes this helps. Bytheway can you stream your vob, mpg of flv files? See my post (above).
GreeTz

Thanks!

Interesting... I'll triple check my setup against your files and the guide again.

I might have to setup a cron job to update, its just that I thought that the inotify support was there to allow fuppes to be aware of changes to the filesystem so it could auto update.

I havent tried to stream anything other than avi files, sorry, that all I need it for at this stage.

---

### Post by illumeo on 2010-01-05
Hi, Help
I had an older ver of fuppes working and then it broke so I thought i would follow the the howto to upgrade.  It did not work so i rm the fuppes dir
and tried again still no joy. when i run sudo fuppes i get
            
FUPPES - 0.643
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] failed to bind socket to : 192.168.1.14:9137
[exiting]

i think the ver of fuppes i checked out was 660. 

very confused, pls help.
thanks

---

### Post by Coollie on 2010-01-05
> **illumeo said:**
> Hi, Help
I had an older ver of fuppes working and then it broke so I thought i would follow the the howto to upgrade.  It did not work so i rm the fuppes dir
and tried again still no joy. when i run sudo fuppes i get
            
FUPPES - 0.643
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] failed to bind socket to : 192.168.1.14:9137
[exiting]

i think the ver of fuppes i checked out was 660. 

very confused, pls help.
thanks

Hi Ilumeo,

What is your current ubuntu version? I installed mine from svn on my Hardy server. Which fuppes directory did you remove? If you want I can give you my own guide on what to remove and how to reinstall using the latest svn. Let me know.

GreeTz

---

### Post by illumeo on 2010-01-05
Yes pls do. I am running 9.10 I had the fuppes dir in / and i removed it, i still have my .fuppes in my home dir

---

### Post by caffeineme on 2010-01-07
> **khadland said:**
> Thanks!

Interesting... I'll triple check my setup against your files and the guide again.

I might have to setup a cron job to update, its just that I thought that the inotify support was there to allow fuppes to be aware of changes to the filesystem so it could auto update.

I havent tried to stream anything other than avi files, sorry, that all I need it for at this stage.

If someone has created a cron job that auto-updates the Fuppes DB, I'd very much appreciate a peek at how they did it. The Fuppes wiki has inst. for Gentoo...I tried that, and wasn't successful. I'm only slightly past n00b, and CRON is a bit out of my depth. Thank you. 

Do have fuppes running on 9.10 Server/PS3, and really enjoying it.

---

### Post by Langan on 2010-01-07
Thank you for the guide and everyone for volunteering such diligent help!

I'm using a Netgear MR814v2 to connect my Dell Inspiron 6000 wirelessly to my xbox 360 l33t (ethernet wired for the l33test gaming performance :D).

I followed the guide and everything worked beautifully. I'm fairly new to linux and setting up home servers, so this made me giddy excited. I'm not ashamed to say my pants indeed got a little bit shorter.

Superfluous exposition aside, after a few restarts later, connecting to my laptop no longer works for me. If I open "My Videos" on the 360, it'll say "FUPPES 0.659:1" but it wont actually let me connect when I select it. If I run the network test it says it can't detect any computers, and "FUPPES 0.659:1" disappears from the "My Games" "Select Source" list. While still in the "Select Source" list, if I go back to my Ubuntu 9.10 terminal and type:

tyler@tyler-laptop:~$ sudo fuppes
[sudo] password for tyler: 
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.659
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

webinterface: [http://192.168.0.4:9137](http://192.168.0.4:9137)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

r
[ContentDatabase] create database at Thu Jan  7 04:00:24 2010
read shared directories
[NULL @ 0x924b9e0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x920d970]Invalid and inefficient vfw-avi packed B frames detected
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Thu Jan  7 04:00:34 2010
v
[VirtualContainer] create virtual container layout started at Thu Jan  7 04:00:37 2010
[VirtualContainer] virtual container layout created at Thu Jan  7 04:00:38 2010

I get this output. I got the Null @ 0x924b9e0 errors before and it didn't prevent my stream from working.

The router has been assigning new ip addresses, so I went to the Fuppes config and added the 192.168.0.1 through 8 to the allowed IP list.

Please, ubuntu forum experts, help me get this media server working again. You're my only hope!

---

### Post by Coollie on 2010-01-07
> **illumeo said:**
> Yes pls do. I am running 9.10 I had the fuppes dir in / and i removed it, i still have my .fuppes in my home dir

Hi Illumeo,
Sorry for the delay. Here's what you have to do to completely remove Fuppes and re-install it.

[LIST]
[*] First change to root user and remove all fuppes directories and files. You can use the following command:
```

su <and enter your root password>
cd /
find / -maxdepth 5 -name *fuppes* 

``` and then manually remove every directory and file in which fuppes shows up. Or, you can use the following command:
```
rm -r /usr/local/bin/*fuppes* |rm -r /usr/local/share/*fuppes* |rm -r /usr/local/lib/*fuppes* |rm -r /usr/local/include/*fuppes* |rm -r /root/.*fuppes* |rm -r /tmp/*fuppes* |rm -r /usr/src/*fuppes*
``` which on **Hardy** removes all fuppes directories and files.

[*]Remove the folowing packages:
```

aptitude remove subversion build-essential automake ffmpeg libtool libpcre3-dev pkg-config libxml2-dev libsqlite3-dev libavformat-dev libtwolame-dev libmpcdec-dev libfaad-dev libflac-dev libtag1-dev libsimage-dev uuid-dev liblame-dev libmagick++9-dev libmad0-dev libmpeg4ip-dev libmp4v2-dev libavutil-dev libavcodec-dev autoconf gettext

```
[*]After this your system is clean. Let's update the repositories and install the packages needed.
```

apt-get update

aptitude install subversion build-essential automake ffmpeg libtool libpcre3-dev pkg-config libxml2-dev libsqlite3-dev libavformat-dev libtwolame-dev libmpcdec-dev libfaad-dev libflac-dev libtag1-dev libsimage-dev uuid-dev liblame-dev libmagick++9-dev libmad0-dev libmpeg4ip-dev libmp4v2-dev libavutil-dev libavcodec-dev autoconf gettext libxml-dev checkinstall

```
[*]Remove the package that causes problems, see the [this]("http://ubuntuforums.org/showpost.php?p=8237466&postcount=5") thread
```
aptitude remove libsimage-dev
```


[*]Get fuppes, compile and install
```

cd /usr/src

svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes

cd fuppes

ACLOCAL_FLAGS="-I /usr/bin/aclocal" autoreconf -vfi

./configure --enable-transcoder-ffmpeg --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad

checkinstall --pkgname=fuppes --pkgversion "3:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --default

```

[*]Finally you can run fuppes by 
```
sudo fuppes
```
[/LIST]

If you want to you can use my volfer.cfg and fuppes.cfg which I [posted]("http://ubuntuforums.org/showpost.php?p=8602859&postcount=107") earlier. I've also posted my fuppesd script and can be found [here]("http://ubuntuforums.org/showpost.php?p=8610720&postcount=109"). [COLOR="Red"]**Word of caution: This guide works on my Hardy server. Use at own risk.**[/COLOR]

---

### Post by Coollie on 2010-01-07
> **Langan said:**
> 
I followed the guide and everything worked beautifully. I'm fairly new to linux and setting up home servers, so this made me giddy excited. I'm not ashamed to say my pants indeed got a little bit shorter.


Can you recall what you changed before the restarts? If everything worked ok before then something must have changed. Try starting fuppes in a terminal and afterwards streaming your content. What do you see in your terminal window?
Post your configs so we can take a look at them.
GreeTza

---

### Post by illumeo on 2010-01-07
Thanks very much for that i will let you know how i get on

---

### Post by illumeo on 2010-01-07
ok all good until

checkinstall --pkgname=fuppes --pkgversion "3:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --default

sudo checkinstall --pkgname=fuppes --pkgversion "3:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --default
sudo: checkinstall: command not found

any idea how to do this bit?

---

### Post by illumeo on 2010-01-07
so i did

sudo make
sudo make install
and ldconfig

then i get

sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.660
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] no database version information found. remove the fuppes.db and restart fuppes
[ERROR] unable to create database file
[exiting]

---

### Post by Coollie on 2010-01-07
> **illumeo said:**
> so i did

sudo make
sudo make install
and ldconfig

then i get

sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.660
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] no database version information found. remove the fuppes.db and restart fuppes
[ERROR] unable to create database file
[exiting]

How did you install fuppes? As user of as root? Try running fuppes as user. Any luck?
Check in your /root/.fuppes or /user/.fuppes if you see any fuppes.db

What i did is dropdown to root and installed everything. Forgot to mention that, my bad. Are you able to drop down to root? 
Thus:
```
 su
password: your root password

```

If you can't do this, first lookup how to change your root password. Afterwards remove fuppes and install as root user. When you start fuppes (sudo fuppes) your fuppes.db should be created in /root/.fuppes.
GreeTza

PS: In order to use checkinstall you have to install it first if you get this error.
```
apt-get install checkinstall
```

---

### Post by illumeo on 2010-01-07
thanks for the help
installed checkinstall
and ran the checkinstall line
rm the fuppes.db from ~/.fuppes
and sudo fuppes

:~$ sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.660
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ContentDatabase] create database at Thu Jan  7 14:22:22 2010
read shared directories
[ERROR] failed to bind socket to : 192.168.1.14:9137
[exiting]

hmmm. any ideas?

---

### Post by Coollie on 2010-01-07
> **illumeo said:**
> thanks for the help
installed checkinstall
and ran the checkinstall line
rm the fuppes.db from ~/.fuppes
and sudo fuppes

:~$ sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.660
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ContentDatabase] create database at Thu Jan  7 14:22:22 2010
read shared directories
[ERROR] failed to bind socket to : 192.168.1.14:9137
[exiting]

hmmm. any ideas?

I've seen that error before but can't remember where. I think i saw it in the ubuntu forum's but can't remember which thread. Try [googling]("http://www.google.nl/search?hl=nl&client=firefox-a&rls=com.ubuntu%3Anl%3Aofficial&hs=aBZ&q=ubuntu+fuppes+failed+to+bind+socket+to+&btnG=Zoeken&meta=&aq=f&oq=") it. Here's [one]("http://forums.overclockers.co.uk/showthread.php?p=12485746") that may be of intrest.

---

### Post by illumeo on 2010-01-07
on it.

Thanks very much for your help Coollie.

---

### Post by Coollie on 2010-01-07
> **illumeo said:**
> on it.

Thanks very much for your help Coollie.

If it's working, enjoy. And if you came accross people who can transcode mpg, vob and flv video formats let me know please.

GreeTz

---

### Post by illumeo on 2010-01-07
yes working now!

noticed the web interface was still up even though i had rebooted and not run fuppes and it had the old ver number.

did a ps -A|less and found the proc number and killed it, ran fuppes and it works.  :)

Thamks

---

### Post by Coollie on 2010-01-07
> **illumeo said:**
> yes working now!

noticed the web interface was still up even though i had rebooted and not run fuppes and it had the old ver number.

did a ps -A|less and found the proc number and killed it, ran fuppes and it works.  :)

Thamks

Great to hear Illumeo. Enjoy! :D  And once again Ubuntu rocks :D
A happy ending

---

### Post by Siderian on 2010-01-07
Greetings!

After following numerous tutorials I've gotten Fuppes and ffmpeg installed for streaming/transcoding to my 360. I've been mostly successful but I'm having a problem that has me completely lost.

My xbox sees fuppes content but will only play WMV's. My fuppes.cfg is standard except for this part:
> <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="mkv">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
            <file ext="avi">
             <type>VIDEO_ITEM</type>
             <mime_type>video/x-msvideo</mime_type>
             <transcode enabled="true">
             <transcoder>ffmpeg</transcoder>
             <ext>wmv</ext>
             <mime_type>video/x-ms-wmv</mime_type>
             <video_codec>wmv2</video_codec>
             <audio_codec>wmav1</audio_codec>
             <video_bitrate>180000</video_bitrate>
             <audio_bitrate>128000</audio_bitrate>
             </transcode>
            </file>
        </file_settings>
    </device>Following another thread I found the above allowed my xbox to see .MKV's and .AVI's, but trying to play one of these files produces a 53-c00DF238 xbox error which seems to be some type of stream/connectivity error. For the sake of testing, i've disabled my firewall and set the media server on DMZ, though I suspect the issue is one of transcoding. Does anyone have any ideas at all? Or a current, working solution for transcoding to the 360? Thanks!!

---

### Post by Coollie on 2010-01-07
> **Siderian said:**
> Greetings!

After following numerous tutorials I've gotten Fuppes and ffmpeg installed for streaming/transcoding to my 360. I've been mostly successful but I'm having a problem that has me completely lost.

My xbox sees fuppes content but will only play WMV's. My fuppes.cfg is standard except for this part:
Following another thread I found the above allowed my xbox to see .MKV's and .AVI's, but trying to play one of these files produces a 53-c00DF238 xbox error which seems to be some type of stream/connectivity error. For the sake of testing, i've disabled my firewall and set the media server on DMZ, though I suspect the issue is one of transcoding. Does anyone have any ideas at all? Or a current, working solution for transcoding to the 360? Thanks!!

Hi Siderian,

That's exactly the same problem I'm having. I think I'm going to ask the fuppes guru's and creators directly cuz seems that no one has the need to transcode mkv, flv, vob, mpg or avi's.
I'm starting to think that transcoding no longer is supported in fuppes. I still want to have one more go at compiling and installing ffmpeg to see if I can get transcoding going.

Cheers and if you have any luck with finding someone that has transcoding actually working, let me know.

GreeTz

---

### Post by Langan on 2010-01-08
> **Coollie said:**
> Can you recall what you changed before the restarts? If everything worked ok before then something must have changed. Try starting fuppes in a terminal and afterwards streaming your content. What do you see in your terminal window?
Post your configs so we can take a look at them.
GreeTza

Thanks for your prompt response!

I cannot recall any changes to either system. I'm assuming something happened with the network? The laptop and xbox have new ip addresses on [http://192.168.0.1](http://192.168.0.1) (my router config page, "attached devices").

What would prevent the xbox from seeing all my movies, but still allow it to see FUPPES on the "My Videos" tab?

---

### Post by 55021 on 2010-01-08
Hello All

I am getting big problems to install Fuppes on Ubuntu 9.10 Desktop I386.
And after ready with more attention all coments here posted. I need one simple information
How can I remove completly the Fuppes and re-install it ?

Chears

---

### Post by Coollie on 2010-01-08
> **Siderian said:**
> Greetings!

After following numerous tutorials I've gotten Fuppes and ffmpeg installed for streaming/transcoding to my 360. I've been mostly successful but I'm having a problem that has me completely lost.

My xbox sees fuppes content but will only play WMV's. My fuppes.cfg is standard except for this part:
Following another thread I found the above allowed my xbox to see .MKV's and .AVI's, but trying to play one of these files produces a 53-c00DF238 xbox error which seems to be some type of stream/connectivity error. For the sake of testing, i've disabled my firewall and set the media server on DMZ, though I suspect the issue is one of transcoding. Does anyone have any ideas at all? Or a current, working solution for transcoding to the 360? Thanks!!

PS: Did you download the XBox 360 fall update? [This]("http://www.360-hq.com/posts2628-highlightsupported.html+codec") is what de XBox curently supports.
GreeTz

---

### Post by Coollie on 2010-01-08
> **55021 said:**
> Hello All

I am getting big problems to install Fuppes on Ubuntu 9.10 Desktop I386.
And after ready with more attention all coments here posted. I need one 
simple information
How can I remove completly the Fuppes and re-install it ?

Chears

Hi, check out [my post]("http://ubuntuforums.org/showpost.php?p=8624368&postcount=116"). Good luck! GreeTz

---

### Post by Coollie on 2010-01-08
> **Langan said:**
> Thanks for your prompt response!

I cannot recall any changes to either system. I'm assuming something happened with the network? The laptop and xbox have new ip addresses on [http://192.168.0.1](http://192.168.0.1) (my router config page, "attached devices").

What would prevent the xbox from seeing all my movies, but still allow it to see FUPPES on the "My Videos" tab?

Hi Langan,

Post your fuppes.cfg and vfolder.cfg so I can take a look at them. Or, you could download mine and compare them with yours.
GreeTz

---

### Post by Langan on 2010-01-09
> **Coollie said:**
> Hi Langan,

Post your fuppes.cfg and vfolder.cfg so I can take a look at them. Or, you could download mine and compare them with yours.
GreeTz


```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/tyler/Downloads</dir>
    <dir>/media/cdrom0</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth1</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.1</ip>
      <ip>192.168.0.2</ip>
      <ip>192.168.0.3</ip>
      <ip>192.168.0.4</ip>
      <ip>192.168.0.5</ip>
      <ip>192.168.0.6</ip>
      <ip>192.168.0.7</ip>
      <ip>192.168.0.8</ip> 
   </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <file_settings>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>

``````

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

 <vfolder_layout device="Xbox 360" enabled="true" create_references="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
                <items type="videoItem" />
            </vfolder>
      <vfolder name="Folders" id="21">
               <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```sudo fuppes
tried
```

sudo -s
cd ./.fuppes
rm fuppes.db
sudo fuppes

```
firewall is down
192.168.0.4:9137 gives me the config page
my xbox says its 192.168.0.2

Worked previously. Dell inspiron 6000 to xbox 360 elite.

Thanks! :)

---

### Post by Coollie on 2010-01-09
> 
firewall is down
192.168.0.4:9137 gives me the config page
my xbox says its 192.168.0.2

Worked previously. Dell inspiron 6000 to xbox 360 elite.

Thanks! :)

Your config's looks just fine. Because the setup worked before "something happened" I'm guessing that maybe you had some libraries updated which broke fuppes down. This is just a guess of course. Did you try re-installing fuppes before? Otherwise try re-installing fuppes (use my guide). It work's on Hardy and Karmic. That's as far that I can help you with this problem, sorry and good luck!:confused:](*,)

---

### Post by Siderian on 2010-01-09
> **Coollie said:**
> PS: Did you download the XBox 360 fall update? [This]("http://www.360-hq.com/posts2628-highlightsupported.html+codec") is what de XBox curently supports.
GreeTz

I think my xbox is current on all updates. Then again, I'm on a satellite connection in the middle of a desert so checking for new updates would require alignment of the planets, spontaneous world peace, and an authorization memo signed by Jesus himself. -_-

I'll keep looking for answers to this and post if I find anything

---

### Post by reddevil2064 on 2010-01-10
> **Shhnap said:**
> 
Yeah, the database is known to be slow for more than 7000 items. Sorry. It is on my todo list but it will not make it out before the next for-windows-as-well release. It will be a rather large change that will require some testing.

Shhnap what is the status of the slow database issue? And is there anything that can be done to aid in improving/fixing the issue?

---

### Post by sven.jambor on 2010-01-13
Hmm, I got the latest release of Fuppes to compile without errors and with support for ffmpeg (which I didn't re-compile) on 9.04. Everyting seems to be running fine, including transcoding flac to mp3. However, transcoding movies is simply not working. Not mpeg2 to mpeg4, avi to anything etc. The error I get is:
> == lib/HTTP/HTTPMessage.cpp (750) :: Wed Jan 13 21:51:24 2010 ==
init transcoding failed :: /storage/movies/New Stuff/Amadeus/Amadeus.avi


When I do the transcode manually using ffmpeg then it works well...  ANyone got any ideas?

---

### Post by sven.jambor on 2010-01-13
Also wondering: I saw a site with various "module" for fuppes (?!) - and some of them seemed to refer to mysql.... would it make sense to grab some of that code and get the db moved over to mysql? Just my 2c worth...

---

### Post by finni100100 on 2010-01-14
ok so im tring to install tonight and i keep getting this error message on sudo make after everything but simage is enabled in configure
```
libtool: link: g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtbeginS.o  .libs/libmetadata_ffmpegthumbnailer_la-metadata_ffmpegthumbnailer.o   -lffmpegthumbnailer -lavutil -lavformat -lavcodec -lswscale -lpng12 /usr/lib/libjpeg.so -L/usr/lib/gcc/x86_64-linux-gnu/4.4.1 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../.. -L/usr/lib/x86_64-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.4.1/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crtn.o    -Wl,-soname -Wl,libmetadata_ffmpegthumbnailer.so.0 -o .libs/libmetadata_ffmpegthumbnailer.so.0.0.0
/usr/bin/ld: cannot find -lswscale
collect2: ld returned 1 exit status
make[1]: *** [libmetadata_ffmpegthumbnailer.la] Error 1
make[1]: Leaving directory `/home/finni/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```

anyone have any ideas  
```
CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : yes
      pcm/wav    : yes
    decoder:
      vorbis     : no
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : enabled

  image conversion/rescaling plugins
    ImageMagick        : enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib             : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : enabled
    ImageMagick        : enabled  (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : enabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : enabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

```

---

### Post by KillaB7 on 2010-01-16
I have a theory. Lately there have been folks talking about setting up cron jobs to update fuppes.db.

It's already been pointed out that fuppes uses inotify to update the database automatically.

What might be throwing some people off is that you should only be adding COMPLETED files to folders that fuppes serves from.

For example: If your torrent download directory is the same as the folder you're trying to serve from, then fuppes will detect the file as soon as it's added and will have a very hard time analyzing it's contents (container type, etc.) based on just a few bytes.

Of course, on my PS3, you still need to perform a "Search for Media Servers" to refresh the local PS3 database. I would imagine this is true for Xbox 360 users as well.


@Shhnap
I know it's not necessary, but older versions of fuppes used to report on the CLI when a new file was detected. Can this be added back in?

---

### Post by Shhnap on 2010-01-17
> **KillaB7 said:**
> I have a theory. Lately there have been folks talking about setting up cron jobs to update fuppes.db.

It's already been pointed out that fuppes uses inotify to update the database automatically.

Actually that's been around for quite some time. I think it was suggested in the wiki as a workaround in 2007

> **KillaB7 said:**
> What might be throwing some people off is that you should only be adding COMPLETED files to folders that fuppes serves from.

Agreed, don't make a torrent directory a fuppes directory. That could cause some issues and (off the top of my head) I don't really see a good workaround other than removing inotify from the code and doing manual updates of fuppes.db.

> **KillaB7 said:**
> @Shhnap
I know it's not necessary, but older versions of fuppes used to report on the CLI when a new file was detected. Can this be added back in?

Actually it never really left, it was really only for 'printf debugging' and so was just commented out. To get it back just uncomment the required lines. For one of those lines look in 'src/lib/ContentDirectory/FileAlterationMonitor.cpp' on line 245. Uncomment that and you get one of the create events back.


Now as a little announcement to the community, you may not have heard from me recently and that is because I have been working on packaging fuppes. Right now I have a package that works for me on Ubuntu Karmic and it should be easy to upgrade it for Lucid now that I have read through the debian policy and debian maintainers guide a few times. This is good news because it means that when it is released either everybody will have an install problem or nobody will have install issues and everyone on Ubuntu and Debian will be in the same boat. I mention this not to set a date or even to say it is coming out now but to alert you so that you know to keep an eye out.

The fuppes package will not be released until all lintian bugs are resolved (there are only two left) and until I have a talk with Ulrich and he agrees that it is ready for release.

Just in case anyone here can help me, the two lintian bugs that are left are:
```
W: fuppes: package-name-doesnt-match-sonames libfuppes0
W: fuppes: non-dev-pkg-with-shlib-symlink usr/lib/libfuppes.so.0.0.0 usr/lib/libfuppes.so
```
So if anybody has seen that before it will save me having to search (I have already looked at the documentation for those errors and it didn't really help me).

I hope everybody on Ubuntu is enjoying fuppes and I'll make some sort of announcement here when a fuppes package has been released. (Then i'll ask PorchSong to edit the initial thread to just say: download and double click on the package)

---

### Post by TurboZinc on 2010-01-18
I was finally able to get fuppes set up correctly, but now i can't get it to load automatically at logon.

I followed the instructions at [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d) and i get nothing. The process isn't running when i log on. It will start when i type fuppesd start in the terminal though.

Anyone get it to work?

---

### Post by Shhnap on 2010-01-21
> **TurboZinc said:**
> I was finally able to get fuppes set up correctly, but now i can't get it to load automatically at logon.

I followed the instructions at [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d) and i get nothing. The process isn't running when i log on. It will start when i type fuppesd start in the terminal though.

Anyone get it to work?

All you should have to do is set the right runlevels at the top of the script and make sure that you installed it in the right manner using update-rc.d. Make sure that you have specified the right runlevel (en.wikipedia.org/wiki/Runlevel) so that it loads up on boot. But I think that the debian/init.d script in the fuppes-svn should work for you. It had the correct runlevels when I checked it today.


On another note I would like to announce that I have started a new blog that posts on various computing things that I am doing but a whole category is about fuppes stuff; it has a few fuppes posts already. If you want to hear a little about the fuppes dev I am doing or some of the decisions made then visit: [http://massaioli.homelinux.com/wordpress](http://massaioli.homelinux.com/wordpress)

And leave a comment if you feel like it too. :)

---

### Post by bumbot on 2010-01-23
> **TurboZinc said:**
> I was finally able to get fuppes set up correctly...

Does this mean you got your music to show up in the Artists and Albums listings on the Xbox, instead of just songs? I'm having the same problem, how did you solve it?

---

### Post by Sload on 2010-01-23
> **bumbot said:**
> Does this mean you got your music to show up in the Artists and Albums listings on the Xbox, instead of just songs? I'm having the same problem, how did you solve it?

 If you haven't already tried it, then use the vfolder.cfg from this post: [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107)  Working great for me, using Fuppes rev.661.

---

### Post by bumbot on 2010-01-23
> **Sload said:**
> If you haven't already tried it, then use the vfolder.cfg from this post: [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107)  Working great for me, using Fuppes rev.661.

Thanks, I hadn't seen that one yet.

At first I used the vfolder.cfg from the beginning of this thread. Everything plays just fine, but all my music is listed alphabetically by filename (not title from the id3 tag) under Songs, and under Albums it says "No Albums Found", same for Artist and Genre (also, my playlists aren't showing up, which I have saved as m3u's). Then I tried installing taglib from the link in this post:

[http://ubuntuforums.org/showpost.php?p=6696805&postcount=48](http://ubuntuforums.org/showpost.php?p=6696805&postcount=48)

I followed the instructions on installation included with the download, then I tried using the vfolder.cfg from this post:

[http://ubuntuforums.org/showpost.php?p=5375602&postcount=38](http://ubuntuforums.org/showpost.php?p=5375602&postcount=38)

Didn't work, so I deleted my fuppes folder, and reinstalled it using the instructions at the beginning of this thread. Again, everything plays, but only the filenames show up on the Xbox. I installed Songbird and Amarok in the hopes that taglib would be installed correctly if I'd done something wrong, and re-started my computer, but again, only filenames showing up.

I just tried the vfolder.cfg that I'm quoting in this post, but again, only filenames showing up. I'm using Karmic Koala, I have v0.661 of Fuppes, and none of the three vfolder.cfg files I'm trying are making the id3 tags show up. I'm pretty sure I've got taglib installed, and again, all the media plays no problem, I can see and play all my videos, pictures and music, and I've even got fuppesd running automatically when I log in, just no tags on my mp3's.

Upon closer inspection, all three are exactly the same untill the very bottom, where the setup for pictures and video is different. In other words, how they handle music is the same, so maybe that needs to be changed?

---

### Post by bumbot on 2010-01-23
Okay, I just tried swapping out the code in the vfolder.cfg files on the forums for the code from the fuppes wiki:

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Xbox_vfolders](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Xbox_vfolders)

Again, I can get everything to play, but everything's still listed by filename under Songs.

---

### Post by Shhnap on 2010-01-23
Edit: Rewrote it all.

Actually according to Ulrich this capability should be in fuppes as of svn659: [https://sourceforge.net/tracker/?func=detail&aid=2898475&group_id=141999&atid=751216](https://sourceforge.net/tracker/?func=detail&aid=2898475&group_id=141999&atid=751216)

I'm not sure how to set it up though. Music is not the reason I use fuppes but I may look a this soon.

---

### Post by Shhnap on 2010-01-24
> **sven.jambor said:**
> Also wondering: I saw a site with various "module" for fuppes (?!) - and some of them seemed to refer to mysql.... would it make sense to grab some of that code and get the db moved over to mysql? Just my 2c worth...

Hi Sven,

I just thought I would let you know that even though there is a mysql plugin for fuppes it does not actually currently work with fuppes. Just look inside the src/lib/libmain.cpp file and you see that while sqlite is loaded no attempt is made to load mysql.

I actually tried to see what would happen if I loaded mysql instead and a few bugs occur. Also there are some parts of the code that are very sqlite specific. I think a little bit of work needs to be done to add mysql support.

I actually go into this in more detail in a post that will come out at 2PM (my time) tomorrow. I live in GMT+10. Go to [massaioli.homelinux.com/wordpress/]("http://massaioli.homelinux.com/wordpress/") to see it.

---

### Post by Sload on 2010-01-24
> **bumbot said:**
> Okay, I just tried swapping out the code in the vfolder.cfg files on the forums for the code from the fuppes wiki:

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Xbox_vfolders](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Xbox_vfolders)

Again, I can get everything to play, but everything's still listed by filename under Songs.

 Sounds weird, is taglib enabled in fuppes.cfg? If fuppes was compiled with taglib and you have tried every vfolder.cfg here, then I don't know what's wrong.

---

### Post by RetianFes on 2010-01-24
I've read through the whole thread and followed all the steps but I can't seem to get this to work. It's unknown to me whether fuppes isn't working, or if it's just that my xbox can't see it. Right now I'm making a gradual switch from Windows XP to Ubuntu 9.10, but I'd really like to stream my videos rather than keep loading up USB flash drives.

These are my cfg files that are in the .fuppes folder.

fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/My Book/Media</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>22222</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.1.0</ip>-->
      <ip>192.168.1.50</ip>
      <ip>192.168.1.51</ip>
      <ip>192.168.1.52</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <show_empty_resolution>true</show_empty_resolution>
        <file_settings>
           <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
           <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
           <file ext="avi"><type>VIDEO_ITEM</type>
              <mime_type>video/avi</mime_type>
           </file>
        </file_settings>
	<description_values>
	    <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
	    <model_name>Windows Media Connect compatible (%s)</model_name>
	    <model_number>2.0</model_number>
	</description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```


vfolder.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
     <vfolder name="Folders" id="21"> 
       <folders filter="contains(videoItem)" /> 
     </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```

I port forwarded the port 22222 on the IP 192.168.1.52 for my modem and wireless router and the web interface is at [http://192.168.1.52:22222/](http://192.168.1.52:22222/) 

I really appreciate it! Thanks.

---

### Post by bumbot on 2010-01-24
> **Sload said:**
> Sounds weird, is taglib enabled in fuppes.cfg? If fuppes was compiled with taglib and you have tried every vfolder.cfg here, then I don't know what's wrong.

Here's a copy and paste from my fuppes.cfg file:

```
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
```

That's as it should be, yes? Is there a way to check if I've got taglib installed correctly? All the song information is showing up automatically in Rythmbox, Songbird and Amarok, so I know something's reading the tags.

There is one thing I'm doing that's a little odd. I'm using a different user's Music folder as a source of my music. Should that make a difference?

---

### Post by Sload on 2010-01-24
> **bumbot said:**
> Here's a copy and paste from my fuppes.cfg file:

```
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
```That's as it should be, yes? Is there a way to check if I've got taglib installed correctly? All the song information is showing up automatically in Rythmbox, Songbird and Amarok, so I know something's reading the tags.

There is one thing I'm doing that's a little odd. I'm using a different user's Music folder as a source of my music. Should that make a difference?

 You can see what plugins are installed by going to the web interface and look on the status page. If taglib isn't listed there then you need to reinstall. The config looks right, and no, if your xbox can play the music then it doesn't make a difference.

---

### Post by Sload on 2010-01-24
> **RetianFes said:**
> I've read through the whole thread and followed all the steps but I can't seem to get this to work. It's unknown to me whether fuppes isn't working, or if it's just that my xbox can't see it. Right now I'm making a gradual switch from Windows XP to Ubuntu 9.10, but I'd really like to stream my videos rather than keep loading up USB flash drives.
 I port forwarded the port 22222 on the IP 192.168.1.52 for my modem and wireless router and the web interface is at [http://192.168.1.52:22222/](http://192.168.1.52:22222/) 

I really appreciate it! Thanks.

 So I take it that your xbox doesn't show up in the konsole when you run fuppes? If that's the case then I'd suggest trying out a differenet fuppes.cfg file, since even the smallest error will result in fuppes not seeing the xbox.

---

### Post by RetianFes on 2010-01-24
> **Sload said:**
> So I take it that your xbox doesn't show up in the konsole when you run fuppes? If that's the case then I'd suggest trying out a differenet fuppes.cfg file, since even the smallest error will result in fuppes not seeing the xbox.

Where would I look to find out if fuppes can see the xbox?

---

### Post by emma_peel on 2010-01-24
Thank you for this howto, it has been very usefull.

---

### Post by KillaB7 on 2010-01-24
@Shhnap

Much thanks for your efforts on the packaging front!

I'm not sure if this bug is documented, but I've noticed that the IP range parameter doesn't appear to work.

The following code doesn't work for me:
```
<ip>192.168.1.*</ip>
```

When I change it to the IP of my PS3 and restart, it works:
```
<ip>192.168.1.205</ip>
```

---

### Post by Sload on 2010-01-24
> **RetianFes said:**
> Where would I look to find out if fuppes can see the xbox?

 On the start page in the web interface.

---

### Post by bumbot on 2010-01-24
> **Sload said:**
> You can see what plugins are installed by going to the web interface and look on the status page. If taglib isn't listed there then you need to reinstall. The config looks right, and no, if your xbox can play the music then it doesn't make a difference.

There we go! Sure enough, taglib isn't listed on the status page. I'll try reinstalling a little later and see what happens. By the way, there's nothing fancy I have to do to install taglib, is there? I just open the terminal, go into the directory where the taglib download was extracted to, type ./configure, then type make, then sudo make install. That's it, right? I did that, but I don't see any files called taglib in /usr/local/bin, although there are a few files called libtag.

---

### Post by RetianFes on 2010-01-24
> **Sload said:**
> On the start page in the web interface.

Okay, it has WRT160N on the list four times (it's my router), and then a WFADevice, which I'm not quite sure what that is.

---

### Post by Sload on 2010-01-24
> **bumbot said:**
> There we go! Sure enough, taglib isn't listed on the status page. I'll try reinstalling a little later and see what happens. By the way, there's nothing fancy I have to do to install taglib, is there? I just open the terminal, go into the directory where the taglib download was extracted to, type ./configure, then type make, then sudo make install. That's it, right? Yep > **bumbot said:**
> I did that, but I don't see any files called taglib in /usr/local/bin, although there are a few files called libtag.

Check in /usr/bin. Otherwise do a search for taglib-config in your computer. > **RetianFes said:**
> Okay, it has WRT160N on the list four times (it's my router), and then a WFADevice, which I'm not quite sure what that is.

  Ok, the WFADevice belongs to your router as well I believe. Have you tried any fuppes.cfg file from this thread? The one on the first page should work, otherwise this one will definitely work: [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107) I had problem with fuppes not finding my xbox before as well and that file did the trick.

---

### Post by RetianFes on 2010-01-24
> **Sload said:**
> Ok, the WFADevice belongs to your router as well I believe. Have you tried any fuppes.cfg file from this thread? The one on the first page should work, otherwise this one will definitely work: [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107) I had problem with fuppes not finding my xbox before as well and that file did the trick.

Thanks! I can now see my Xbox, I used the one you linked me to. The one I was originally using was from the front page, so I may have just messed up something when putting in the IP addresses and whatnot.

But another brick wall, the xbox can't see fuppes. I ran the rebuild database and virtual container commands again after I changed the fuppes.cfg file, but it did naught.

---

### Post by Sload on 2010-01-24
> **RetianFes said:**
> Thanks! I can now see my Xbox, I used the one you linked me to. The one I was originally using was from the front page, so I may have just messed up something when putting in the IP addresses and whatnot.

But another brick wall, the xbox can't see fuppes. I ran the rebuild database and virtual container commands again after I changed the fuppes.cfg file, but it did naught.

Use the vfolder.cfg from the same post and it should work.

---

### Post by RetianFes on 2010-01-24
> **Sload said:**
> Use the vfolder.cfg from the same post and it should work.

Unfortunately, it didn't work. Do I need to reboot after rebuilding the database and virtual container or do something else special?

---

### Post by Shhnap on 2010-01-24
Wow, so many replies, I love it. :D I'll try and put in what I think quickly.

> **RetianFes said:**
> I've read through the whole thread and followed all the steps but I can't seem to get this to work. It's unknown to me whether fuppes isn't working, or if it's just that my xbox can't see it. Right now I'm making a gradual switch from Windows XP to Ubuntu 9.10, but I'd really like to stream my videos rather than keep loading up USB flash drives.

These are my cfg files that are in the .fuppes folder.

(Removed code for the sake of brevity)

I port forwarded the port 22222 on the IP 192.168.1.52 for my modem and wireless router and the web interface is at [http://192.168.1.52:22222/](http://192.168.1.52:22222/) 

I really appreciate it! Thanks.

I would suggest using a port >= 49200. I don't really remember why I am suggesting that but I think there was  good reason too but what that reason is evades me; either way give it a try and see it it works for you. It sure works for me. Also eth0 is not required but it should not matter that it is there. Other than that I'm not sure; let me know.

> **RetianFes said:**
> Where would I look to find out if fuppes can see the xbox?

You could make a log file and see the connections occurring (or not ocurring) or you could look at the stats page of the webinterface.

> **emma_peel said:**
> Thank you for this howto, it has been very usefull.

I'm glad it has helped you. I'm not taking any credit though, PorchSong wrote the guide and the credit is all his. :) I just love seeing people enjoy fuppes.

> **KillaB7 said:**
> @Shhnap

Much thanks for your efforts on the packaging front!

I'm not sure if this bug is documented, but I've noticed that the IP range parameter doesn't appear to work.

The following code doesn't work for me:
```
<ip>192.168.1.*</ip>
```

When I change it to the IP of my PS3 and restart, it works:
```
<ip>192.168.1.205</ip>
```

No problems on the packaging front, just happy to get it done. :) However I have to ask Uli a question and talk to a few more people before it gets packages properly.

Also that screams bug so I was wondering if you could raise a bug request on sourceforge for it? Sounds to me like the regex that handles that didn't work as hoped. Sorry for the inconvinience.

And I think that almost wraps it up, oh and fuppes should never require a computer reboot to work. It should not even require a program restart unless you change the config file.

---

### Post by RetianFes on 2010-01-24
Yay. Okay, I think I've nearly got it down. Fuppes sees the Xbox, the Xbox sees Fuppes, just it says that no videos are found. I'm going to guess its because of the vfolder.cfg, but I'm not sure. I'm using the one here: [http://ubuntuforums.org/showpost.php...&postcount=107](http://ubuntuforums.org/showpost.php...&postcount=107)

Thanks for all the help so far by the way!

---

### Post by Shhnap on 2010-01-24
What media files are you trying to get the XBox to see? All avi's will have to have their mime type changed in the way you saw in the xbox device settings of the first fuppes.cfg you showed us.

---

### Post by RetianFes on 2010-01-24
> **Shhnap said:**
> What media files are you trying to get the XBox to see? All avi's will have to have their mime type changed in the way you saw in the xbox device settings of the first fuppes.cfg you showed us.

avi and mp3, [s]although now, after restarting Ubuntu, fuppes won't recognize the xbox 360 anymore.[/s]

EDIT: Okay, so now the Xbox will only recognize my itunes folder and not my videos folder.

---

### Post by emoguitarist06 on 2010-01-25
I can't get Fuppes to run!
I follow the guide exactly but I get an error when I run fuppes in the terminal

```
$ fuppes
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

failed to initialize sqlite database plugin.
```

And according to fuppes wiki:
[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Troubleshooting](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Troubleshooting)
I tried runnning this with no results either:

```
$ fuppes --plugin-dir src/plugins/.libs/ 
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

failed to initialize sqlite database plugin.
```

Please help

EDIT: I just recompiling Fuppes and this time I followed Shhnap's advice of running
> ./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad
But still no luck. And Shhnap also says don't try and install with "libsimage-dev" and I'm not doing that because I don't even have "libsimage-dev" installed.

---

### Post by Shhnap on 2010-01-25
@Retian: That is very odd indeed. Can I reccommend removing your database and trying to rebuild. If that fails and you are still having problems maybe consider making a post on the sourceforge help page.

@emoguitarist06 That is quite confusing. It looks like you have run a 'sudo make install' on svn661 and that fuppes is supposed to be installed on your machine. You should just be able to just type in 'fuppes' and have it work. It is my suspicion right now that you have not installed 'libsqlite3-dev' so please ensure a 'sudo apt-get install libsqlite3-dev' and recompile again.

However if that still does not fix the problem then I need you to run these commands and give me their output:
```

ldd `which fuppes`
ls -la /usr/lib/fuppes/
```

(Please note that these commands assume you have done a 'sudo make install'. Otherwise they will do nothing.)

I hope that helps.

---

### Post by emoguitarist06 on 2010-01-25
> **Shhnap said:**
> 
@emoguitarist06 That is quite confusing. It looks like you have run a 'sudo make install' on svn661 and that fuppes is supposed to be installed on your machine. You should just be able to just type in 'fuppes' and have it work. It is my suspicion right now that you have not installed 'libsqlite3-dev' so please ensure a 'sudo apt-get install libsqlite3-dev' and recompile again.

However if that still does not fix the problem then I need you to run these commands and give me their output:
```

ldd `which fuppes`
ls -la /usr/lib/fuppes/
```

(Please note that these commands assume you have done a 'sudo make install'. Otherwise they will do nothing.)

I hope that helps.

THANKS FOR THE QUICK REPLY!!

Here are my results
```
$ sudo apt-get install libsqlite3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsqlite3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ ldd `which fuppes`
	linux-gate.so.1 =>  (0x00190000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x0078d000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x009cc000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x004fc000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00fb0000)
	libfuppes.so.0 => /usr/lib/libfuppes.so.0 (0x002f5000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00851000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00110000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00136000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00191000)
	/lib/ld-linux.so.2 (0x00666000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00736000)
	libz.so.1 => /lib/libz.so.1 (0x00154000)
$ ls -la /usr/lib/fuppes/
ls: cannot access /usr/lib/fuppes/: No such file or directory
$ 


```

---

### Post by Shhnap on 2010-01-25
> **emoguitarist06 said:**
> THANKS FOR THE QUICK REPLY!!

```

$ ls -la /usr/lib/fuppes/
ls: cannot access /usr/lib/fuppes/: No such file or directory
$ 

```

No problems but there we go. That directory should not be empty and that is your problem. It should be full of all of your plugin code, including the sqlite plugin .so file. I don't know why it is missing but my guess is that the option '--prefix=/usr/' was not used on the first configure and therefore the .so files might be located in '/usr/local/lib/fuppes' instead:

Try a:

```
ls -la /usr/local/lib/fuppes/
```

And if that has the sqlite file in it try:

```
fuppes --plugin-dir /usr/local/lib/fuppes/
```

Otherwise if that fails then please perform all the steps to give you an identical install to myself:
```

sudo make uninstall
autoreconf -vfi 
./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad 
make clean && make
sudo make install
fuppes
```

I'm hoping that the first step works but If not then maybe a complete recompile will.

---

### Post by emoguitarist06 on 2010-01-25
> **Shhnap said:**
> No problems but there we go. That directory should not be empty and that is your problem. It should be full of all of your plugin code, including the sqlite plugin .so file. I don't know why it is missing but my guess is that the option '--prefix=/usr/' was not used on the first configure and therefore the .so files might be located in '/usr/local/lib/fuppes' instead:

Try a:

```
ls -la /usr/local/lib/fuppes/
```

And if that has the sqlite file in it try:

```
fuppes --plugin-dir /usr/local/lib/fuppes/
```

Otherwise if that fails then please perform all the steps to give you an identical install to myself:
```

sudo make uninstall
autoreconf -vfi 
./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad 
make clean && make
sudo make install
fuppes
```

I'm hoping that the first step works but If not then maybe a complete recompile will.

First option didn't work, apparently that directory didn't exist either :/
So I'm going to give you the results of each command you gave me

```
~$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
lunchables@andrea-laptop:~$ cd fuppes
lunchables@andrea-laptop:~/fuppes$ cd fuppes
bash: cd: fuppes: No such file or directory
~/fuppes$
```

the next line

```
:~/fuppes$ autoreconf -vfi autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: serial numbers `2006.12.25.00' or `2009.04.28.21; # UTC' contain non-digit chars
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
autoreconf: Leaving directory `.'
~/fuppes$ 
```

the next line

```
~/fuppes$ ./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faa
configure: WARNING: unrecognized options: --enable-faa
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we are building with mingw... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for select... yes
checking size of off_t... 8
checking size of long long int... 8
checking size of unsigned long long int... 8
checking size of long int... 4
checking size of unsigned long int... 4
checking size of int... 4
checking size of unsigned int... 4
checking size of short... 2
checking size of unsigned short... 2

check minimum dependencies

checking for PCRE... yes
checking for LIBXML... yes
checking for SQLITE3... yes
checking for pthread_create in -lpthread... yes
checking for clock_gettime in -lrt... yes

check recommended dependencies

checking for UUID... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);

check optional stuff

checking for taglib-config... no
checking for FFMPEGTHUMBNAILER... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... yes
checking libavformat/avformat.h usability... no
checking libavformat/avformat.h presence... no
checking for libavformat/avformat.h... no
checking for LIBSWSCALE... no
checking ffmpeg/avstring.h usability... no
checking ffmpeg/avstring.h presence... no
checking for ffmpeg/avstring.h... no
checking for LIBAVCODEC... yes
checking for LIBAVUTIL... yes
checking for mpeg4ip-config... no
configure: *** mpeg4ip/libmp4v2 support disabled ***
checking lame/lame.h usability... yes
checking lame/lame.h presence... yes
checking for lame/lame.h... yes
checking for TWOLAME... no
checking for VORBISFILE... yes
checking mpcdec/config_types.h usability... no
checking mpcdec/config_types.h presence... no
checking for mpcdec/config_types.h... no
checking FLAC/file_decoder.h usability... no
checking FLAC/file_decoder.h presence... no
checking for FLAC/file_decoder.h... no
checking FLAC/stream_decoder.h usability... no
checking FLAC/stream_decoder.h presence... no
checking for FLAC/stream_decoder.h... no
checking for MAD... no
checking for simage-config... no
checking for mysql_config... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating src/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/windows/Makefile
config.status: creating include/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands
configure: WARNING: unrecognized options: --enable-faa

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

lunchables@andrea-laptop:~/fuppes$ 
```

Unfortunately I could not copy all of the results of > make clean && make because it was far too long. But at the end there was an error
```
metadata_libavformat.c:36:22: error: avformat.h: No such file or directory
metadata_libavformat.c:37:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function ‘register_fuppes_plugin’:
metadata_libavformat.c:55: error: ‘AV_LOG_QUIET’ undeclared (first use in this function)
metadata_libavformat.c:55: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:55: error: for each function it appears in.)
metadata_libavformat.c: In function ‘fuppes_metadata_file_open’:
metadata_libavformat.c:67: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:67: error: expected expression before ‘)’ token
metadata_libavformat.c:68: error: expected expression before ‘)’ token
metadata_libavformat.c: In function ‘fuppes_metadata_read’:
metadata_libavformat.c:78: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:78: error: expected expression before ‘)’ token
metadata_libavformat.c:78: error: ‘AV_NOPTS_VALUE’ undeclared (first use in this function)
metadata_libavformat.c:81: error: expected expression before ‘)’ token
metadata_libavformat.c:81: error: ‘AV_TIME_BASE’ undeclared (first use in this function)
metadata_libavformat.c:82: error: expected expression before ‘)’ token
metadata_libavformat.c:96: error: expected expression before ‘)’ token
metadata_libavformat.c:97: error: expected expression before ‘)’ token
metadata_libavformat.c:105: error: expected expression before ‘)’ token
metadata_libavformat.c:107: error: ‘AVStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: ‘pStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: expected expression before ‘)’ token
metadata_libavformat.c:108: error: ‘AVCodec’ undeclared (first use in this function)
metadata_libavformat.c:108: error: ‘pCodec’ undeclared (first use in this function)
metadata_libavformat.c:152: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
metadata_libavformat.c:158: error: ‘CODEC_TYPE_AUDIO’ undeclared (first use in this function)
metadata_libavformat.c:164: error: ‘CODEC_TYPE_DATA’ undeclared (first use in this function)
metadata_libavformat.c:166: error: ‘CODEC_TYPE_SUBTITLE’ undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/lunchables/fuppes/src/plugins'
make: *** [all-recursive] Error 1
lunchables@andrea-laptop:~/fuppes$ make clean && make

```
and again more errors after > sudo make install
```
unchables@andrea-laptop:~/fuppes$ sudo make install
Making install in m4
make[1]: Entering directory `/home/lunchables/fuppes/m4'
make[2]: Entering directory `/home/lunchables/fuppes/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/lunchables/fuppes/m4'
make[1]: Leaving directory `/home/lunchables/fuppes/m4'
Making install in include
make[1]: Entering directory `/home/lunchables/fuppes/include'
make[2]: Entering directory `/home/lunchables/fuppes/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include" || /bin/mkdir -p "/usr/include"
 /usr/bin/install -c -m 644 fuppes_plugin.h fuppes_plugin_types.h fuppes_db_connection_plugin.h '/usr/include'
test -z "/usr/include" || /bin/mkdir -p "/usr/include"
 /usr/bin/install -c -m 644 fuppes_types.h '/usr/include'
make[2]: Leaving directory `/home/lunchables/fuppes/include'
make[1]: Leaving directory `/home/lunchables/fuppes/include'
Making install in src
make[1]: Entering directory `/home/lunchables/fuppes/src'
make  install-am
make[2]: Entering directory `/home/lunchables/fuppes/src'
make[3]: Entering directory `/home/lunchables/fuppes/src'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libfuppes.la '/usr/lib'
libtool: install: /usr/bin/install -c .libs/libfuppes.so.0.0.0 /usr/lib/libfuppes.so.0.0.0
libtool: install: (cd /usr/lib && { ln -s -f libfuppes.so.0.0.0 libfuppes.so.0 || { rm -f libfuppes.so.0 && ln -s libfuppes.so.0.0.0 libfuppes.so.0; }; })
libtool: install: (cd /usr/lib && { ln -s -f libfuppes.so.0.0.0 libfuppes.so || { rm -f libfuppes.so && ln -s libfuppes.so.0.0.0 libfuppes.so; }; })
libtool: install: /usr/bin/install -c .libs/libfuppes.lai /usr/lib/libfuppes.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c fuppes fuppesd '/usr/bin'
libtool: install: /usr/bin/install -c .libs/fuppes /usr/bin/fuppes
libtool: install: /usr/bin/install -c .libs/fuppesd /usr/bin/fuppesd
test -z "/usr/share/fuppes" || /bin/mkdir -p "/usr/share/fuppes"
 /usr/bin/install -c -m 644 lib/Presentation/style.css lib/Presentation/fuppes-small.png lib/Presentation/header-gradient.png lib/Presentation/header-gradient-small.png '/usr/share/fuppes'
make[3]: Leaving directory `/home/lunchables/fuppes/src'
make[2]: Leaving directory `/home/lunchables/fuppes/src'
make[1]: Leaving directory `/home/lunchables/fuppes/src'
Making install in src/plugins
make[1]: Entering directory `/home/lunchables/fuppes/src/plugins'
/bin/bash ../../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src    -I/usr/include/ffmpeg   -DOLD_INCLUDES_PATH -DFFMPEG_VERSION=52 -I/usr/include/ffmpeg   -I/usr/include/ffmpeg   -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c -o libmetadata_libavformat_la-metadata_libavformat.lo `test -f 'metadata_libavformat.c' || echo './'`metadata_libavformat.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../src -I/usr/include/ffmpeg -DOLD_INCLUDES_PATH -DFFMPEG_VERSION=52 -I/usr/include/ffmpeg -I/usr/include/ffmpeg -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c metadata_libavformat.c  -fPIC -DPIC -o .libs/libmetadata_libavformat_la-metadata_libavformat.o
metadata_libavformat.c:36:22: error: avformat.h: No such file or directory
metadata_libavformat.c:37:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function ‘register_fuppes_plugin’:
metadata_libavformat.c:55: error: ‘AV_LOG_QUIET’ undeclared (first use in this function)
metadata_libavformat.c:55: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:55: error: for each function it appears in.)
metadata_libavformat.c: In function ‘fuppes_metadata_file_open’:
metadata_libavformat.c:67: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:67: error: expected expression before ‘)’ token
metadata_libavformat.c:68: error: expected expression before ‘)’ token
metadata_libavformat.c: In function ‘fuppes_metadata_read’:
metadata_libavformat.c:78: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:78: error: expected expression before ‘)’ token
metadata_libavformat.c:78: error: ‘AV_NOPTS_VALUE’ undeclared (first use in this function)
metadata_libavformat.c:81: error: expected expression before ‘)’ token
metadata_libavformat.c:81: error: ‘AV_TIME_BASE’ undeclared (first use in this function)
metadata_libavformat.c:82: error: expected expression before ‘)’ token
metadata_libavformat.c:96: error: expected expression before ‘)’ token
metadata_libavformat.c:97: error: expected expression before ‘)’ token
metadata_libavformat.c:105: error: expected expression before ‘)’ token
metadata_libavformat.c:107: error: ‘AVStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: ‘pStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: expected expression before ‘)’ token
metadata_libavformat.c:108: error: ‘AVCodec’ undeclared (first use in this function)
metadata_libavformat.c:108: error: ‘pCodec’ undeclared (first use in this function)
metadata_libavformat.c:152: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
metadata_libavformat.c:158: error: ‘CODEC_TYPE_AUDIO’ undeclared (first use in this function)
metadata_libavformat.c:164: error: ‘CODEC_TYPE_DATA’ undeclared (first use in this function)
metadata_libavformat.c:166: error: ‘CODEC_TYPE_SUBTITLE’ undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/lunchables/fuppes/src/plugins'
make: *** [install-recursive] Error 1
:~/fuppes$ 
```

and finally 

```

$ fuppes
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

failed to initialize sqlite database plugin.
$ 
```

---

### Post by Shhnap on 2010-01-25
Hmmm, I think you may have discovered a bug in the configure script. Which version of Ubuntu are you running?

And can you try 'sudo apt-get install libavformat-dev' and then try again from the ./configure step? If the make fails then there is no need for further instructions. You see, the configure thinks you have libavformat enabled but the files also seem to be missing which is confusing. So my guess is that libavformat-dev is not installed and that the configure script needs an update.

Other than that everything else seemed reasonable; it should compile atleast even if you do not have full functionality. :)

This time, just give me the result of the configure (don't do the sudo make uninstall) and the result of any make errors along with the output of this command:

```
head -n30 /usr/include/libavformat/avformat.h
```

(Make sure that libavformat-dev is installed before running the above command.)

---

### Post by emoguitarist06 on 2010-01-25
> **Shhnap said:**
> Hmmm, I think you may have discovered a bug in the configure script. Which version of Ubuntu are you running?

And can you try 'sudo apt-get install libavformat-dev' and then try again from the ./configure step? If the make fails then there is no need for further instructions. You see, the configure thinks you have libavformat enabled but the files also seem to be missing which is confusing. So my guess is that libavformat-dev is not installed and that the configure script needs an update.

Other than that everything else seemed reasonable; it should compile atleast even if you do not have full functionality. :)

This time, just give me the result of the configure (don't do the sudo make uninstall) and the result of any make errors along with the output of this command:

```
head -n30 /usr/include/libavformat/avformat.h
```

(Make sure that libavformat-dev is installed before running the above command.)

I'm running Ubuntu 9.10 32bit

```
$ sudo apt-get install libavformat-dev: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavformat-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$ cd fuppes
~/fuppes$ ./configure --prefix=/usr/ --enable-lame --enable-twolame --enable-mad --enable-faad 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we are building with mingw... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for select... yes
checking size of off_t... 8
checking size of long long int... 8
checking size of unsigned long long int... 8
checking size of long int... 4
checking size of unsigned long int... 4
checking size of int... 4
checking size of unsigned int... 4
checking size of short... 2
checking size of unsigned short... 2

check minimum dependencies

checking for PCRE... yes
checking for LIBXML... yes
checking for SQLITE3... yes
checking for pthread_create in -lpthread... yes
checking for clock_gettime in -lrt... yes

check recommended dependencies

checking for UUID... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);

check optional stuff

checking for taglib-config... no
checking for FFMPEGTHUMBNAILER... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... yes
checking libavformat/avformat.h usability... no
checking libavformat/avformat.h presence... no
checking for libavformat/avformat.h... no
checking for LIBSWSCALE... no
checking ffmpeg/avstring.h usability... no
checking ffmpeg/avstring.h presence... no
checking for ffmpeg/avstring.h... no
checking for LIBAVCODEC... yes
checking for LIBAVUTIL... yes
checking for mpeg4ip-config... no
configure: *** mpeg4ip/libmp4v2 support disabled ***
checking lame/lame.h usability... yes
checking lame/lame.h presence... yes
checking for lame/lame.h... yes
checking for TWOLAME... no
checking for VORBISFILE... yes
checking mpcdec/config_types.h usability... no
checking mpcdec/config_types.h presence... no
checking for mpcdec/config_types.h... no
checking FLAC/file_decoder.h usability... no
checking FLAC/file_decoder.h presence... no
checking for FLAC/file_decoder.h... no
checking FLAC/stream_decoder.h usability... no
checking FLAC/stream_decoder.h presence... no
checking for FLAC/stream_decoder.h... no
checking for MAD... no
checking faad.h usability... yes
checking faad.h presence... yes
checking for faad.h... yes
checking mp4ff.h usability... yes
checking mp4ff.h presence... yes
checking for mp4ff.h... yes
checking for simage-config... no
checking for mysql_config... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating src/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/windows/Makefile
config.status: creating include/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : yes (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

Thanks for using fuppes
please report bugs

~/fuppes$ 

```

Again it looks like the same errors after > make clean && make
```
 metadata_libavformat.c:36:22: error: avformat.h: No such file or directory
metadata_libavformat.c:37:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function ‘register_fuppes_plugin’:
metadata_libavformat.c:55: error: ‘AV_LOG_QUIET’ undeclared (first use in this function)
metadata_libavformat.c:55: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:55: error: for each function it appears in.)
metadata_libavformat.c: In function ‘fuppes_metadata_file_open’:
metadata_libavformat.c:67: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:67: error: expected expression before ‘)’ token
metadata_libavformat.c:68: error: expected expression before ‘)’ token
metadata_libavformat.c: In function ‘fuppes_metadata_read’:
metadata_libavformat.c:78: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:78: error: expected expression before ‘)’ token
metadata_libavformat.c:78: error: ‘AV_NOPTS_VALUE’ undeclared (first use in this function)
metadata_libavformat.c:81: error: expected expression before ‘)’ token
metadata_libavformat.c:81: error: ‘AV_TIME_BASE’ undeclared (first use in this function)
metadata_libavformat.c:82: error: expected expression before ‘)’ token
metadata_libavformat.c:96: error: expected expression before ‘)’ token
metadata_libavformat.c:97: error: expected expression before ‘)’ token
metadata_libavformat.c:105: error: expected expression before ‘)’ token
metadata_libavformat.c:107: error: ‘AVStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: ‘pStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: expected expression before ‘)’ token
metadata_libavformat.c:108: error: ‘AVCodec’ undeclared (first use in this function)
metadata_libavformat.c:108: error: ‘pCodec’ undeclared (first use in this function)
metadata_libavformat.c:152: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
metadata_libavformat.c:158: error: ‘CODEC_TYPE_AUDIO’ undeclared (first use in this function)
metadata_libavformat.c:164: error: ‘CODEC_TYPE_DATA’ undeclared (first use in this function)
metadata_libavformat.c:166: error: ‘CODEC_TYPE_SUBTITLE’ undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/lunchables/fuppes/src/plugins'
make: *** [all-recursive] Error 1
~/fuppes$ 

```

and errors in > sudo make install
```
metadata_libavformat.c:36:22: error: avformat.h: No such file or directory
metadata_libavformat.c:37:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function ‘register_fuppes_plugin’:
metadata_libavformat.c:55: error: ‘AV_LOG_QUIET’ undeclared (first use in this function)
metadata_libavformat.c:55: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:55: error: for each function it appears in.)
metadata_libavformat.c: In function ‘fuppes_metadata_file_open’:
metadata_libavformat.c:67: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:67: error: expected expression before ‘)’ token
metadata_libavformat.c:68: error: expected expression before ‘)’ token
metadata_libavformat.c: In function ‘fuppes_metadata_read’:
metadata_libavformat.c:78: error: ‘AVFormatContext’ undeclared (first use in this function)
metadata_libavformat.c:78: error: expected expression before ‘)’ token
metadata_libavformat.c:78: error: ‘AV_NOPTS_VALUE’ undeclared (first use in this function)
metadata_libavformat.c:81: error: expected expression before ‘)’ token
metadata_libavformat.c:81: error: ‘AV_TIME_BASE’ undeclared (first use in this function)
metadata_libavformat.c:82: error: expected expression before ‘)’ token
metadata_libavformat.c:96: error: expected expression before ‘)’ token
metadata_libavformat.c:97: error: expected expression before ‘)’ token
metadata_libavformat.c:105: error: expected expression before ‘)’ token
metadata_libavformat.c:107: error: ‘AVStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: ‘pStream’ undeclared (first use in this function)
metadata_libavformat.c:107: error: expected expression before ‘)’ token
metadata_libavformat.c:108: error: ‘AVCodec’ undeclared (first use in this function)
metadata_libavformat.c:108: error: ‘pCodec’ undeclared (first use in this function)
metadata_libavformat.c:152: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
metadata_libavformat.c:158: error: ‘CODEC_TYPE_AUDIO’ undeclared (first use in this function)
metadata_libavformat.c:164: error: ‘CODEC_TYPE_DATA’ undeclared (first use in this function)
metadata_libavformat.c:166: error: ‘CODEC_TYPE_SUBTITLE’ undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/lunchables/fuppes/src/plugins'
make: *** [install-recursive] Error 1
~/fuppes$ 

```

and finally the failed to initialize sqlite database plugin error after attempting to run fuppes

and here's the list code you gave me
```
~$ head -n30 /usr/include/libavformat/avformat.h
head: cannot open `/usr/include/libavformat/avformat.h' for reading: No such file or directory
$
```

:(

---

### Post by Shhnap on 2010-01-25
...Wow. Now I'm confused as hell. You have libavformat-dev but you don't have the header files it is supposed to install. That's a big WTF in my books...It's like the package installed but did not install anything...and I'm running the same version of Ubuntu as you so I have no clue what is wrong. Your packages should install the same as my packages; identically. I don't even think this will work but try:
```

sudo apt-get purge libavformat-dev
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install libavformat-dev
```

And then check if you have that file now using the 'head' command from the previous post. If that fails then there is a bug with your installation of libavformat-dev and I don't know what it is; it'll be time to start a new thread on these forums about that. (Let me know what the result of the head command is)

---

### Post by emoguitarist06 on 2010-01-25
> **Shhnap said:**
> ...Wow. Now I'm confused as hell. You have libavformat-dev but you don't have the header files it is supposed to install. That's a big WTF in my books...It's like the package installed but did not install anything...and I'm running the same version of Ubuntu as you so I have no clue what is wrong. Your packages should install the same as my packages; identically. I don't even think this will work but try:
```

sudo apt-get purge libavformat-dev
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install libavformat-dev
```

And then check if you have that file now using the 'head' command from the previous post. If that fails then there is a bug with your installation of libavformat-dev and I don't know what it is; it'll be time to start a new thread on these forums about that. (Let me know what the result of the head command is)

This crap makes me want to just do a clean install of Karmic LOL

but ya no results from the head command.
But what if I just place the avformat.h file there?
is this the file [http://cekirdek.pardus.org.tr/~ismail/ffmpeg-docs/avformat_8h-source.html](http://cekirdek.pardus.org.tr/~ismail/ffmpeg-docs/avformat_8h-source.html) ??

---

### Post by Shhnap on 2010-01-26
Just placing the file there is a bad idea because it is just one of many, and not just header files, shared libraries too. So if you wanted to put it in manually then I would suggest downloading the sources and building it yourself.

But I don't really recommend that either because we have a package manager and it should just work. I would start a forum post about it and then if that fails either contact the Ubuntu packager of libavformat-dev or create a lintian bug for it.

Sorry I couldn't be of more help. I'm just confused that a header file that should be there is not. (Infact at this point I would seriously consider a clean install of Karmic too)

---

### Post by emoguitarist06 on 2010-01-26
> **Shhnap said:**
> Just placing the file there is a bad idea because it is just one of many, and not just header files, shared libraries too. So if you wanted to put it in manually then I would suggest downloading the sources and building it yourself.

But I don't really recommend that either because we have a package manager and it should just work. I would start a forum post about it and then if that fails either contact the Ubuntu packager of libavformat-dev or create a lintian bug for it.

Sorry I couldn't be of more help. I'm just confused that a header file that should be there is not. (Infact at this point I would seriously consider a clean install of Karmic too)

Alright I'll research as much as I can and let you know if I come up with anything. 
I plan to do a clean install of 10.04

Thanks for all your help!

---

### Post by bumbot on 2010-01-27
> **Sload said:**
> Yep 

Check in /usr/bin. Otherwise do a search for taglib-config in your computer. 

Okay, it was actually in a different folder, but I did have it installed. So after about three hours of copying the file around and deleting and re-installing fuppes, I finally clued into this part of the fuppes status screen:

plugin dir:
/usr/lib/fuppes/

Copied taglib-config to that location, and now the Albums, Artist, and Song Titles all show up! Thanks for the help Sload, it's greatly appreciated.

---

### Post by Shhnap on 2010-01-27
> **bumbot said:**
> Okay, it was actually in a different folder, but I did have it installed. So after about three hours of copying the file around and deleting and re-installing fuppes, I finally clued into this part of the fuppes status screen:

plugin dir:
/usr/lib/fuppes/

Copied taglib-config to that location, and now the Albums, Artist, and Song Titles all show up! Thanks for the help Sload, it's greatly appreciated.

Oh, I did not know that...it's definitely something I should look into. But when you say 'copyied taglib-config' you mean symbolic link right ('man ln' with the -s option)?

If not then the way I would recommend 'copying' taglib-config, for now, is to create a symbolic link, like this:

```
cd /usr/lib/fuppes/
sudo ln -s /usr/bin/taglib-config 
```

That will achieve the same thing but if new versions of taglib-config come through the package manager (apt-get) then you don't have to re-copy taglib; which is useful.

---

### Post by Shhnap on 2010-01-28
[SIZE="6"][COLOR="Red"]NEWS UPDATE: Christoph Korn packaged FUPPES for the GetDeb project.[/COLOR][/SIZE]

[COLOR="Red"]Get it while it's hot: [http://www.getdeb.net/updates/Ubuntu/9.10/?q=fuppes](http://www.getdeb.net/updates/Ubuntu/9.10/?q=fuppes)[/COLOR]

I should note that GetDeb makes non-official packages that should work but are not tested as much as official ones. I am still working on packaging fuppes for Debian and will then stream down an official one for Ubuntu.

---

### Post by emoguitarist06 on 2010-01-31
> **Shhnap said:**
> [SIZE="6"][COLOR="Red"]NEWS UPDATE: Christoph Korn packaged FUPPES for the GetDeb project.[/COLOR][/SIZE]

[COLOR="Red"]Get it while it's hot: [http://www.getdeb.net/updates/Ubuntu/9.10/?q=fuppes](http://www.getdeb.net/updates/Ubuntu/9.10/?q=fuppes)[/COLOR]

I should note that GetDeb makes non-official packages that should work but are not tested as much as official ones. I am still working on packaging fuppes for Debian and will then stream down an official one for Ubuntu.

Shhnap that getdeb package works great on my system!! Finally I have fuppes up and running! Now I only have one little problem :( my xbox says there is no videos in my video folder :(

Here is my fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/pumpkinfeet/Videos/</dir>
    <dir>/home/pumpkinfeet/Music/</dir>
    <dir>/home/pumpkinfeet/Pictures/</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>wlan1</interface>
    <!--empty or 0 = random port-->
    <http_port>0</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
        </file_settings>
	<description_values>
	<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
	<model_name>Windows Media Connect compatible (%s)</model_name>
	<model_number>2.0</model_number>
	</description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```

any ideas?

---

### Post by foolsgold7 on 2010-01-31
Hi im brand new to ubuntu just installed today, have managed to get my avi files and mp3 files working but im a little lost with fuppes ive managed to the bit that says 'this should do it' is there any way you can break the next part down into complete beginners talk, step by step, im a little out my depth, thanks in advance

---

### Post by emoguitarist06 on 2010-01-31
> **foolsgold7 said:**
> Hi im brand new to ubuntu just installed today, have managed to get my avi files and mp3 files working but im a little lost with fuppes ive managed to the bit that says 'this should do it' is there any way you can break the next part down into complete beginners talk, step by step, im a little out my depth, thanks in advance

Go to your home folder and make a new folder called ".fuppes" without the quotes. And then open Applications>Accessories>Gedit and make the fuppes.cfg file & the vfolder.cfg file. You can copy them from the first post. And then just change the settings in those files to match your desired settings. And save those files and place them in your .fuppes folder.

Note: when you make the folder .fuppes the "." makes the folder HIDDEN so to see the folder you have to press ctrl+h

---

### Post by Shhnap on 2010-01-31
> **foolsgold7 said:**
> Hi im brand new to ubuntu just installed today, have managed to get my avi files and mp3 files working but im a little lost with fuppes ive managed to the bit that says 'this should do it' is there any way you can break the next part down into complete beginners talk, step by step, im a little out my depth, thanks in advance

About two post above I have pointed out a package that you can use to install fuppes on your machine (if you are running Karmic Koala). If you can I would recommend trying that if you can and then if you need step by step instructions on how to install fuppes then you can find them on the main page of the fuppes wiki. If you still have problems then post them on the fuppes sourceforge forums and we'll be happy to help.

> **emoguitarist06 said:**
> Shhnap that getdeb package works great on my system!! Finally I have fuppes up and running! Now I only have one little problem :( my xbox says there is no videos in my video folder :(

Here is my fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/pumpkinfeet/Videos/</dir>
    <dir>/home/pumpkinfeet/Music/</dir>
    <dir>/home/pumpkinfeet/Pictures/</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>wlan1</interface>
    <!--empty or 0 = random port-->
    <http_port>0</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
        </file_settings>
	<description_values>
	<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
	<model_name>Windows Media Connect compatible (%s)</model_name>
	<model_number>2.0</model_number>
	</description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```

any ideas?

Well, on a glance your config file seems fine so my question to you is what types of files (mp3, avi ect.) are you trying to send to your XBox and have to rebuilt the database? 

And try sending a .wmv file to the XBox via fuppes; that is my sanity check to make sure that the basics are working. The XBox will always be able to play a .wmv file so if it cannot do that then something in the fuppes install is wrong.

---

### Post by foolsgold7 on 2010-02-01
hi again managed most of it, i have configured the fuppes.cfg but it is not letting me save it in my hidden .fuppes folder, it says i have not got admin rights :o any ideas?
sorry for being such a noob




> **Shhnap said:**
> About two post above I have pointed out a package that you can use to install fuppes on your machine (if you are running Karmic Koala). If you can I would recommend trying that if you can and then if you need step by step instructions on how to install fuppes then you can find them on the main page of the fuppes wiki. If you still have problems then post them on the fuppes sourceforge forums and we'll be happy to help.



Well, on a glance your config file seems fine so my question to you is what types of files (mp3, avi ect.) are you trying to send to your XBox and have to rebuilt the database? 

And try sending a .wmv file to the XBox via fuppes; that is my sanity check to make sure that the basics are working. The XBox will always be able to play a .wmv file so if it cannot do that then something in the fuppes install is wrong.

---

### Post by foolsgold7 on 2010-02-01
cool sorted it :D


> **foolsgold7 said:**
> hi again managed most of it, i have configured the fuppes.cfg but it is not letting me save it in my hidden .fuppes folder, it says i have not got admin rights :o any ideas?
sorry for being such a noob

---

### Post by foolsgold7 on 2010-02-01
still struggling now getting this message

foolsgold@foolsgold-laptop:~$ sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] can't resolve ip from interface "eth0".
foolsgold@foolsgold-laptop:~$ 

any help greatly appreciated

---

### Post by emoguitarist06 on 2010-02-01
> **foolsgold7 said:**
> still struggling now getting this message

foolsgold@foolsgold-laptop:~$ sudo fuppes
WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

[ERROR] can't resolve ip from interface "eth0".
foolsgold@foolsgold-laptop:~$ 

any help greatly appreciated

First never run fuppes as sudo. Just run "fuppes"

Are you on wifi? if so in the fuppes.cfg you need to change the networking device. It's saying that eth0 isn't connected. So if you're using wifi it'll probably be wlan0 or wlan1

If you don't know then right click your connection symbol on the top right of your panel and choose "connection information" and under interface it'll tell you

---

### Post by foolsgold7 on 2010-02-01
> **emoguitarist06 said:**
> First never run fuppes as sudo. Just run "fuppes"

Are you on wifi? if so in the fuppes.cfg you need to change the networking device. It's saying that eth0 isn't connected. So if you're using wifi it'll probably be wlan0 or wlan1

If you don't know then right click your connection symbol on the top right of your panel and choose "connection information" and under interface it'll tell you

hi totally new at this do i change etho to wlano in fuppes.cfg, cheers

---

### Post by foolsgold7 on 2010-02-01
thanks for your help much appreciated and seems to be working now, thanks again

---

### Post by zacnotes on 2010-02-02
beginners question here:
   i have a headless 9.10 system i would like to run fuppes on, but i don't know how to get that package onto my server to install. anybody got a hint for me?

---

### Post by emma_peel on 2010-02-03
> **zacnotes said:**
> beginners question here:
   i have a headless 9.10 system i would like to run fuppes on, but i don't know how to get that package onto my server to install. anybody got a hint for me?

Hello.

I'm in the same configuration and follow the howto described on the first page, without any issues.

Did you try it ?

There is currently no package.

---

### Post by Cerox Rex on 2010-02-04
Great guide...

Works fine on my PS3 but i have troubble getting matroska support. I'v tried the config options from Fuppes wiki with no luck. 

posting my config and system output:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/srv/media/Filmer/</dir>
    <dir>/srv/media/Serier</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>
      <ip>192.168.0.20</ip>
      <ip>192.168.0.10</ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.50</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
            
               <file ext="avi">
               <type>VIDEO_ITEM</type>
               <mime_type>video/x-divx</mime_type>
               </file>
               
               <file ext="avi">
               <type>VIDEO_ITEM</type>
               <mime_type>video/x-divx</mime_type>
               <transcode enabled="true">
               <transcoder>ffmpeg</transcoder>
               <ext>mpg</ext>
               <mime_type>video/mpeg</mime_type>
               <video_codec vcodec="msmpeg4">mpeg1video</video_codec>
               <video_bitrate>1800000</video_bitrate>
               <audio_codec acodec="wmav2">mp2</audio_codec>
               <audio_samplerate>44100</audio_samplerate>
               <audio_bitrate>192000</audio_bitrate>
               </transcode>
               </file>

               <file ext="mkv">
               <type>VIDEO_ITEM</type>
               <mime_type>video/x-matroska</mime_type>
               <transcode enabled="true">
               <transcoder>ffmpeg</transcoder>
               <ext>mpg</ext>
               <mime_type>video/mpeg</mime_type>
               <video_codec>mpeg2video</video_codec>
               <video_bitrate>1800000</video_bitrate>
               <audio_codec>mp2</audio_codec>
               <audio_samplerate>44100</audio_samplerate>
               <audio_bitrate>192000</audio_bitrate>
               </transcode>
               </file>




      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
        </file_settings>
	<description_values>
	<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
	<model_name>Windows Media Connect compatible (%s)</model_name>
	<model_number>2.0</model_number>
	</description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```

```
$ fuppes
            FUPPES - 0.661
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.1.10:9137

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

i
general information:
  version     : 0.661
  hostname    : master
  OS          : Linux 2.6.31-17-server
  build at    : Feb  4 2010 13:44:12
  build with  : 4.4.1
  address     : 192.168.1.10
  log-level   : 1 (normal)
  webinterface: http://192.168.1.10:9137/

configuration file:
  /home/hallvar/.fuppes/fuppes.cfg


plugin dir: 
/usr/lib/fuppes/

registered plugins
database:
  "mysql"	library version: 
  "sqlite3"	library version: 3.6.16

misc:
  dlna-profiles

metadata:
  libavformat

transcoder:

audio decoder:

audio encoder:
  pcm
  wav


iconv: enabled
inotify: enabled
uuid: disabled


```

I notice that ffmpeg is missing from transcoding. 

Also is there a way to make fuppes start at boot?

---

### Post by Shhnap on 2010-02-04
@Cerox Rex: I am going to respond to this in the thread that you created for it ([http://ubuntuforums.org/showthread.php?p=8772819#post8772819](http://ubuntuforums.org/showthread.php?p=8772819#post8772819))

---

### Post by DoctorLard on 2010-02-05
See the Debian [_[COLOR="Blue"]Fuppes ITP bug[/COLOR]_]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=426048") for more info.

I've got this going by doing the following:

```
sudo apt-get install build-essential git-buildpackage libexiv2-dev \
     pkg-config libxml2-dev libsqlite3-dev libavformat-dev ffmpeg \
     libtwolame-dev libmpcdec-dev libfaad-dev libtag1-dev uuid-dev \
     libmp3lame-dev libmagick++-dev libmad0-dev libmpeg4ip-dev \
     libmp4v2-dev libflac-dev devtodo autoconf automake gettext
sudo apt-get remove libsimage-dev
git clone git://git.debian.org/collab-maint/fuppes.git
cd fuppes/
git-buildpackage --git-ignore-new
sudo dpkg -i ../fuppes*.deb ../libfuppes*.deb
```

Note that the package build step will NOT currently succeed with libsimage-dev installed, hence the remove step.

Once the packages have been installed, the config is in /etc/fuppes/fuppes.cfg and you can start and stop it as a normal service:

```
sudo service fuppes start
sudo service fuppes stop
```

I hope this gets added to Debian/Ubuntu soon!

---

### Post by derfnerd on 2010-02-05
Hi All,

  I've been following these threads for quite a while, and am getting tired of not being able to solve my issue! It is the same issue others have had, w/o a solution being posted yet. I have followed the guide on page one for .657 (along with numerous other guides at various points), and am unable to view the Genre/Album/Artist info- all the songs get lumped into the "songs" category. So, here are the data points I have:

- I am able to see my music folders under the  "My Videos" xbox console, but all the songs are unable to be played (no error, they just dont play and have a "null" icon for a picture)
- When I go to My Music, all the songs are lumped under the songs category, and are not broken out by Artist/Genre/Album like I would expect. 

When I view the status tab from the web GUI, I get this:

```

plugin dir: 
/usr/local/lib/fuppes/

database:
  "sqlite3"	library version: 3.6.16

misc:
  dlna-profiles

metadata:
  libavformat
  magickWand

transcoder:
  magickWand

audio decoder:
  FLAC
  musepack
  vorbis

audio encoder:
  pcm
```

Note that there is no mention of libtag in there anywhere, but it was compiled initially. The libtag .so files are both in /usr/lib/fuppes and /usr/local/lib/fuppes
I'm not sure what else I can do! I am using the vfolder and fuppes.cfg from [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107) 

Thanks

---

### Post by meerola on 2010-02-07
Hi! I'm running a headless 9.10 server machine. I got fuppes to work using the GetDeb package, but can't get it to start at boot with init.d. I followed [Ulrich's instructions]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d") carefully but it still won't start.

When I did the update-rc.d, I got the following message:

```
sudo update-rc.d fuppesd defaults 60
update-rc.d: warning: fuppesd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
 Adding system startup for /etc/init.d/fuppesd ...
   /etc/rc0.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc1.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc6.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc2.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc3.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc4.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc5.d/S60fuppesd -> ../init.d/fuppesd
```

The only way I get fuppes to run is by logging in and running
```
sudo /etc/init.d/fuppesd start
```

I'm a bit confused here. Any help is appreciated. :)

---

### Post by Shhnap on 2010-02-07
> **DoctorLard said:**
> See the Debian [_[COLOR="Blue"]Fuppes ITP bug[/COLOR]_]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=426048") for more info.

I've got this going by doing the following:

```
sudo apt-get install build-essential git-buildpackage libexiv2-dev \
     pkg-config libxml2-dev libsqlite3-dev libavformat-dev ffmpeg \
     libtwolame-dev libmpcdec-dev libfaad-dev libtag1-dev uuid-dev \
     libmp3lame-dev libmagick++-dev libmad0-dev libmpeg4ip-dev \
     libmp4v2-dev libflac-dev devtodo autoconf automake gettext
sudo apt-get remove libsimage-dev
git clone git://git.debian.org/collab-maint/fuppes.git
cd fuppes/
git-buildpackage --git-ignore-new
sudo dpkg -i ../fuppes*.deb ../libfuppes*.deb
```

Note that the package build step will NOT currently succeed with libsimage-dev installed, hence the remove step.

Once the packages have been installed, the config is in /etc/fuppes/fuppes.cfg and you can start and stop it as a normal service:

```
sudo service fuppes start
sudo service fuppes stop
```

I hope this gets added to Debian/Ubuntu soon!

Woot! Somebody actually used the package that I have been making. :) Yay. I too hope that I get into Debian / Ubuntu soon. :)

> **derfnerd said:**
> Hi All,

  I've been following these threads for quite a while, and am getting tired of not being able to solve my issue! It is the same issue others have had, w/o a solution being posted yet. I have followed the guide on page one for .657 (along with numerous other guides at various points), and am unable to view the Genre/Album/Artist info- all the songs get lumped into the "songs" category. So, here are the data points I have:

- I am able to see my music folders under the  "My Videos" xbox console, but all the songs are unable to be played (no error, they just dont play and have a "null" icon for a picture)
- When I go to My Music, all the songs are lumped under the songs category, and are not broken out by Artist/Genre/Album like I would expect. 

When I view the status tab from the web GUI, I get this:

```

plugin dir: 
/usr/local/lib/fuppes/

database:
  "sqlite3"	library version: 3.6.16

misc:
  dlna-profiles

metadata:
  libavformat
  magickWand

transcoder:
  magickWand

audio decoder:
  FLAC
  musepack
  vorbis

audio encoder:
  pcm
```

Note that there is no mention of libtag in there anywhere, but it was compiled initially. The libtag .so files are both in /usr/lib/fuppes and /usr/local/lib/fuppes
I'm not sure what else I can do! I am using the vfolder and fuppes.cfg from [http://ubuntuforums.org/showpost.php?p=8602859&postcount=107](http://ubuntuforums.org/showpost.php?p=8602859&postcount=107) 

Thanks

You don't seem to have added the --enable-transcoder-ffmpeg line to the configure. Once you do that try and remake fuppes and run it. Let me know if that is successful.

> **meerola said:**
> Hi! I'm running a headless 9.10 server machine. I got fuppes to work using the GetDeb package, but can't get it to start at boot with init.d. I followed [Ulrich's instructions]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d") carefully but it still won't start.

When I did the update-rc.d, I got the following message:

```
sudo update-rc.d fuppesd defaults 60
update-rc.d: warning: fuppesd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
 Adding system startup for /etc/init.d/fuppesd ...
   /etc/rc0.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc1.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc6.d/K60fuppesd -> ../init.d/fuppesd
   /etc/rc2.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc3.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc4.d/S60fuppesd -> ../init.d/fuppesd
   /etc/rc5.d/S60fuppesd -> ../init.d/fuppesd
```

The only way I get fuppes to run is by logging in and running
```
sudo /etc/init.d/fuppesd start
```

I'm a bit confused here. Any help is appreciated. :)

I'm not sure what the problem is but it is really odd and, as you may have guessed, fuppes should not be working like that. To the best of my knowledge it does not make sense. Make sure that in the fuppes.cfg you have set the port the presentation plugin runs on to something steady so that it is not random every time. That way you can find it when you run fuppesd.

The update-rc.d went perfectly. The error about the S run level is to be expected on Debian based systems. Debian does not have the S run level so you could remove it from the init.d script if you chose to; it would not hurt anything.

---

### Post by derfnerd on 2010-02-07
> **Shhnap said:**
> 
 
 
You don't seem to have added the --enable-transcoder-ffmpeg line to the configure. Once you do that try and remake fuppes and run it. Let me know if that is successful.
 
 
Thanks for the reply; isnt that a video thing though? I redid it, here is my configuration summary: 
 
```

ONFIGURATION SUMMARY
audio transcoding plugins
encoder:
lame : yes
twolame : yes
pcm/wav : yes
decoder:
vorbis : yes (libvorbisfile)
mpc : yes
flac : yes
faad : yes (aac/mp4/m4a)
mad : yes (mpeg Layer I, II & III)
video transcoding plugins
ffmpeg : enabled
image conversion/rescaling plugins
ImageMagick : enabled (Wand C-API)
audio metadata extraction plugins
taglib : enabled (mp3, ogg, flac & mpc)
mpeg4ip/mp4v2 : enabled (mp4/m4a)
image metadata extraction plugins
Exiv2 : disabled
ImageMagick : enabled (Wand C-API)
simage : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)
video metadata extraction plugins
libavformat : enabled
ffmpegthumbnailer : disabled
miscellaneous
iconv : enabled (charset conversion)
uuid : enabled
inotify : enabled

```
 
So there's that- and nothing has changed as a result. Music cannot be played from the "My Videos" console box, and all songs are listed, but not sorted (but can be played) from within the "My Music" console box. 
 
Thanks

---

### Post by Shhnap on 2010-02-07
@defnerd:

I don't know why I suggested that, I completely said the wrong thing. And as for your actual problem, some people have told me that putting taglib-config in the lib directory enabled them to sort audio...I don't really know how that works but it's worth a try:

```
ln -s `which taglib-config` /usr/lib/fuppes/
```

Then try and run fuppes again. This should be done after the 'make install'.

---

### Post by meerola on 2010-02-07
Thanks for the huge effort you're putting into this!

> **Shhnap said:**
> I'm not sure what the problem is but it is really odd and, as you may have guessed, fuppes should not be working like that. To the best of my knowledge it does not make sense. Make sure that in the fuppes.cfg you have set the port the presentation plugin runs on to something steady so that it is not random every time. That way you can find it when you run fuppesd.

I have set the port to 9137.

This is quite odd. I don't know whether I should remove everything (I've messed around with the fuppes install a fair bit, first trying the make route, then installing the GetDeb package and finally getting it to work) and reinstall from scratch.

Another unrelated question: music plays well on PS3 via fuppes but video streaming is so jerky it's unwatchable. When I stream to Apple TV (Boxee), the video plays nicely. Do you think enabling transcoding might make it easier for the PS3?

---

### Post by Shhnap on 2010-02-07
> **meerola said:**
> Thanks for the huge effort you're putting into this!

I have set the port to 9137.

This is quite odd. I don't know whether I should remove everything (I've messed around with the fuppes install a fair bit, first trying the make route, then installing the GetDeb package and finally getting it to work) and reinstall from scratch.

Another unrelated question: music plays well on PS3 via fuppes but video streaming is so jerky it's unwatchable. When I stream to Apple TV (Boxee), the video plays nicely. Do you think enabling transcoding might make it easier for the PS3?

The port is good; did it fix the presentation issue. (BTW I personally use ports over 49200 because I think that is the beginning of the unspecified range; but it really does not matter)

And any number of things could slow down video playback but the two most important ones are, what type of file are you trying to play and how is the PS3 connected to fuppes, wires / wireless? etc.

And no problem about the effort, I like Fuppes and I like helping people who like using Fuppes. :) And having people say thanks like that is the best bit so thankyou.

EDIT: Oh and if you're planning on installing fuppes from scratch then I would recommend installing the debian ITP one that somebody mentioned on the last page.

---

### Post by meerola on 2010-02-07
> **Shhnap said:**
> The port is good; did it fix the presentation issue. (BTW I personally use prots over 49200 because I think that is the beginning of the unspecified range but it really does not matter)

The port has been set to 9137 all along. Still struggling with the original problem: fuppesd won't start at bootup without me logging in and manually starting the service.

> **Shhnap said:**
> And any number of things could slow down video playback but the two most important ones are, what type of file are you trying to play and how is the PS3 connected to fuppes, wires / wireless? etc.

I've been testing with a divx avi file and an MP4 file. Both get stuck for 1-2 seconds every 3-4 seconds or so. All connections are wireless: the media server on which fuppes is running, the PS3 and the AppleTV. And I have read that PS3's wireless connectivity is not really all that spectacular so I might just be I'm aiming at something impossible here.

> **Shhnap said:**
> And no problem about the effort, I like Fuppes and I like helping people who like using Fuppes. :) And having people say thanks like that is the best bit so thankyou.

:)

---

### Post by derfnerd on 2010-02-07
> **Shhnap said:**
> @defnerd:
 
I don't know why I suggested that, I completely said the wrong thing. And as for your actual problem, some people have told me that putting taglib-config in the lib directory enabled them to sort audio...I don't really know how that works but it's worth a try:
 
```
ln -s `which taglib-config` /usr/lib/fuppes/
```
 
Then try and run fuppes again. This should be done after the 'make install'.
 
I already have that in there as well... root owns those lib files, that shouldn't be a problem, right?
 
It sounds like I'm running out of things to try. I had installed taglib via apt-get, could that be a problem?
 
(Note: I also have all the taglib-config/taglib.so files in /usr/local/lib/fuppes as well)
 
This may be a stupid question, but I don't need a hacked 360 to do this, correct? Mine is just the regular vanilla version, with the latest console version.

---

### Post by Shhnap on 2010-02-07
> **meerola said:**
> The port has been set to 9137 all along. Still struggling with the original problem: fuppesd won't start at bootup without me logging in and manually starting the service.


Um, to be honest I don't really know what's going on there. I don't think I've heard of that problem before. Can I recommend the ITP package?

> **derfnerd said:**
> I already have that in there as well... root owns those lib files, that shouldn't be a problem, right?
 
It sounds like I'm running out of things to try. I had installed taglib via apt-get, could that be a problem?
 
(Note: I also have all the taglib-config/taglib.so files in /usr/local/lib/fuppes as well)
 
This may be a stupid question, but I don't need a hacked 360 to do this, correct? Mine is just the regular vanilla version, with the latest console version.

None of the above issues should be a problem: root should own those files and I installed taglib via apt-get. And Fuppes will work with any XBox360, cracked or not, that should not be an issue. Once I have finished my database work then I think I will check out the problems that people have been having sorting audio.

---

### Post by meerola on 2010-02-07
> **Shhnap said:**
> Um, to be honest I don't really know what's going on there. I don't think I've heard of that problem before. Can I recommend the ITP package?
Tried it, got the following error when running  git-buildpackage --git-ignore-new

```

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp
# Add here commands to clean up after the build process.
[ ! -f Makefile ] || /usr/bin/make distclean
rm -f config.sub config.guess
dh_clean
fatal: Not a valid object name upstream/0.660
fuppes_0.660.orig.tar.gz does not exist, creating from 'upstream'
fatal: Not a valid object name upstream

```

---

### Post by Shhnap on 2010-02-07
> **meerola said:**
> Tried it, got the following error when running  git-buildpackage --git-ignore-new

```

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp
# Add here commands to clean up after the build process.
[ ! -f Makefile ] || /usr/bin/make distclean
rm -f config.sub config.guess
dh_clean
fatal: Not a valid object name upstream/0.660
fuppes_0.660.orig.tar.gz does not exist, creating from 'upstream'
fatal: Not a valid object name upstream

```

```
git br upstream
```

And then try again. :)

---

### Post by meerola on 2010-02-07
> **Shhnap said:**
> ```
git br upstream
```

And then try again. :)

I'm totally new with this git stuff. Tried that, got this:

```
git: 'br' is not a git-command. See 'git --help'.

```

---

### Post by Shhnap on 2010-02-07
Oh, lol, :) sorry about that one. I have git-config'd branch => br

Therefore write it out fully as:

```
git branch upstream
```

We are creating the upstream branch just incase you want to make local modifications so that the diff in the build has some base to diff too. The base that was used in dh_make. That probably made no sense to you but just try the above command and you'll be right.

---

### Post by meerola on 2010-02-07
> **Shhnap said:**
> Oh, lol, :) sorry about that one. I have git-config'd branch => br

Therefore write it out fully as:

```
git branch upstream
```

Ok, thanks. :) Now I got this:
```

dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp
# Add here commands to clean up after the build process.
[ ! -f Makefile ] || /usr/bin/make distclean
rm -f config.sub config.guess
dh_clean
fatal: Not a valid object name upstream/0.660
fuppes_0.660.orig.tar.gz does not exist, creating from 'upstream'
 dpkg-buildpackage -rfakeroot -D -us -uc -i.git/ -I.git
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fuppes
dpkg-buildpackage: source version 0.660-1
dpkg-buildpackage: source changed by Robert Massaioli <robertmassaioli@gmail.com>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: libtwolame-dev libmpcdec-dev libfaad-dev libflac-dev libtag1-dev uuid-dev libmp3lame-dev libmagick++-dev libmad0-dev libmpeg4ip-dev libmp4v2-dev libexiv2-dev devtodo
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc -i.git/ -I.git failed
debuild -i\.git/ -I.git returned 29
Couldn't run 'debuild -i\.git/ -I.git'

```

---

### Post by Shhnap on 2010-02-07
> **meerola said:**
> Ok, thanks. :) Now I got this:
```

dpkg-checkbuilddeps: Unmet build dependencies: libtwolame-dev libmpcdec-dev libfaad-dev libflac-dev libtag1-dev uuid-dev libmp3lame-dev libmagick++-dev libmad0-dev libmpeg4ip-dev libmp4v2-dev libexiv2-dev devtodo

```

That line explains the entire problem. In English it says "you have not installed these packages and the program you are trying to make really needs them, please install them." So just install them with a:

```
sudo apt-get install libtwolame-dev libmpcdec-dev libfaad-dev libflac-dev libtag1-dev uuid-dev libmp3lame-dev libmagick++-dev libmad0-dev libmpeg4ip-dev libmp4v2-dev libexiv2-dev devtodo
```

And you're done.

---

### Post by Cerox Rex on 2010-02-08
Tried to build fuppes from git.

got the following

```
$ git-buildpackage --git-ignore-newdh_testdir
make: dh_testdir: Command not found
make: *** [clean] Error 127
debuild: fatal error at line 1316:
couldn't exec fakeroot debian/rules: 
debuild -d clean returned 2
Couldn't run 'debuild -d clean'

```

---

### Post by Shhnap on 2010-02-08
I'm not sure, make sure that you have 'debhelper' and 'fakeroot' installed.

---

### Post by meerola on 2010-02-08
> **Shhnap said:**
> That line explains the entire problem. In English it says "you have not installed these packages and the program you are trying to make really needs them, please install them."

Thanks! Really stupid of me not figuring that out from the error.

I installed the packages and tried git-buildpackage again. This time it ended after lintian with the following:

```
Finished running lintian.
Now signing changes and any dsc files...
 signfile fuppes_0.660-1.dsc Robert Massaioli 
gpg: directory `/home/user/.gnupg' created
gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/user/.gnupg/secring.gpg' created
gpg: keyring `/home/user/.gnupg/pubring.gpg' created
gpg: skipped "Robert Massaioli <@gmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
WARNING: Can't find the right public key-- can't check signature integrity.
debuild: fatal error at line 1255:
running debsign failed
debuild -i\.git/ -I.git returned 29
Couldn't run 'debuild -i\.git/ -I.git'
```

Can you please help again? :)

---

### Post by Shhnap on 2010-02-08
> **meerola said:**
> Thanks! Really stupid of me not figuring that out from the error.

I installed the packages and tried git-buildpackage again. This time it ended after lintian with the following:

```
Finished running lintian.
Now signing changes and any dsc files...
 signfile fuppes_0.660-1.dsc Robert Massaioli 
gpg: directory `/home/user/.gnupg' created
gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/user/.gnupg/secring.gpg' created
gpg: keyring `/home/user/.gnupg/pubring.gpg' created
gpg: skipped "Robert Massaioli <@gmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
WARNING: Can't find the right public key-- can't check signature integrity.
debuild: fatal error at line 1255:
running debsign failed
debuild -i\.git/ -I.git returned 29
Couldn't run 'debuild -i\.git/ -I.git'
```

Can you please help again? :)

No problems. The good news is that it should be just about done; everything compiled on your machine. The error is telling you what you do not have the secret key to my gpg identity; I'm happy that you do not or I would be in trouble lol. ;)

All you have to do (I think) is add the following option to the git-buildpackage: --git-no-sign-tags

Then it should just work and all of the .deb files should exist in the parent directory.

---

### Post by zacnotes on 2010-02-08
i seem to be making some headway on  my system, as i can see fuppes on my ps3 now, but i only have 2 music files on my server, and my shared objects are only listed as <dir>/Media/Music</dir> but the rebuild has now taken over 10 minutes. is this normal, or have i made a mistake somewhere?

---

### Post by therikoxide on 2010-02-10
I am brand new to this sort of thing and I dont know what to do since my 360 wont recognize fuppes. I followed your tut word for word.

vfolder.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21" />
      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```

fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/seamarshall/Pictures</dir>
    <dir>/home/seamarshall/Videos</dir>
    <dir>/home/seamarshall/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>wlan0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.1.2</ip>
      <ip>192.168.1.4</ip>
      <ip>192.168.1.1</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <file_settings>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```

---

### Post by PorchSong on 2010-02-14
> **therikoxide said:**
> I am brand new to this sort of thing and I dont know what to do since my 360 wont recognize fuppes. I followed your tut word for word.

fuppes.cfg
[CODE]<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/seamarshall/Pictures</dir>
    <dir>/home/seamarshall/Videos</dir>
    <dir>/home/seamarshall/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>wlan0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.1.2</ip>
      <ip>192.168.1.4</ip>
      <ip>192.168.1.1</ip>
    </allowed_ips>
 

What is the gateway address of your router?  It looks like you might be running two subnets:  xxx.xxx.0.1 and xxx.xxx.1.1  


Also check your xbox, are you manual or automatic.  If automatic network setup, you need to put that ip into your fuppes.cfg.

---

### Post by tjegou on 2010-02-17
I am new to Ubuntu.  I installed Fuppes a few days ago and I am having some trouble with the setup.  I can see fuppes on my PS3 but it says there are no tracks, no pictures and no video files found.  what am I doing wrong? Please help.

Here are my fuppes.cfg and vfolder.cfg from my ** /home/tjegou/.fuppes/ folder **tjegou is my username.

Thanks for your help,
Tom

fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <dir>/home/tjegou/music/music_share</dir>
    <dir>/home/tjegou/pictures/picture_share</dir>
    <dir>/home/tjegou/videos/video_share</dir>
    <dir>/tjegou/music/music_share</dir>
    <dir>/home/tjegou/music</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.109</interface>
    <!--empty or 0 = random port-->
    <http_port>4242</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--These are examples of what data you can put between the ip tags where (* => anything, [x-y] => range)-->
      <!--<ip>192.168.0.1</ip>-->
      <!--<ip>192.168.0.[20-100]</ip>-->
      <!--<ip>192.168.0.*</ip>-->
      <!--<ip>192.*.[0-2].[40-*]</ip>-->
      <ip>192.168.1.100</ip>
      <ip>192.168.1.101</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="true">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
        <file ext="wpl">
          <type>PLAYLIST</type>
          <mime_type>application/vnd.ms-wpl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <!--This section is for the mime types that the makers of the XBox changed from standards.-->
      <file_settings>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>
``` vfolder.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
                <items type="videoItem" />
            </vfolder>
      <vfolder name="Folders" id="21" />
      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```

---

### Post by zacnotes on 2010-02-18
Audio files in mp3 format now play on my ps3, (i posted a few days ago about getting it to even see files, but it seems i have that worked out.) but the .ogg files will not play. on the ps3 they are claimed as "unsupported data, and on my fuppes terminal, it says about 10 times - "error initializing audio decoder". 
my .cfg file:
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/zac/Media/Music</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
   <interface>10.20.1.150</interface>
    <!--empty or 0 = random port-->
   <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
```

any help would be appreciated!

---

### Post by simbloke on 2010-02-21
**Can't get get PS3 to recognise FLAC or OGG.**

Hi, I am building a system using Lucid and have compiled fuppes from svn 662. I have installed all the possible libraries to build against (except mp4ff which doesn't seem to be available). I configured like this:

```
./configure --prefix=/usr --enable-lame --enable-twolame --enable-mad --enable-faad --enable-transcoder-ffmpeg --enable-ffmpegthumbnailer
```

```
CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : yes
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/NO mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : enabled

  image conversion/rescaling plugins
    ImageMagick        : enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib             : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : enabled  (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : enabled
    ImageMagick        : enabled  (Wand C-API)
    simage             : enabled  (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : enabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : enabled
    inotify            : enabled

```

I am testing with a minimal library of one flac, one ogg and one wav. Only the wav will play. The others show up as Unsupported Data
This is my config file:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
	<shared_objects>
		<!-- <dir>/shares/videos</dir>
		<dir>/shares/photos</dir>
		<dir>/shares/music</dir> -->
		<dir>/shares/test</dir>
	</shared_objects>
	<network>
		<interface>eth0</interface>
		<http_port>9137</http_port>
		<!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
		<allowed_ips>
			<!--These are examples of what data you can put between the ip tags where (* => anything, [x-y] => range)-->
			<!--<ip>192.168.0.1</ip>-->
			<!--<ip>192.168.0.[20-100]</ip>-->
			<!--<ip>192.168.0.*</ip>-->
			<!--<ip>192.*.[0-2].[40-*]</ip>-->
		</allowed_ips>
	</network>
	<content_directory>
		<!--a list of possible charsets can be found under: http://www.gnu.org/software/libiconv/-->
		<local_charset>UTF-8</local_charset>
		<!--libs used for metadata extraction when building the database. [true|false]-->
		<use_imagemagick>true</use_imagemagick>
		<use_taglib>true</use_taglib>
		<use_libavformat>true</use_libavformat>
	</content_directory>
	<global_settings>
		<temp_dir>/var/lib/fuppes</temp_dir>
		<!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
		<use_fixed_uuid>true</use_fixed_uuid>
	</global_settings>
	<device_settings>
		<!--"default" settings are inhertied by specific devices and can be overwritten-->
		<!--do NOT remove the "default" device settings-->
		<!--all new file types have to be added to the default settings-->
		<!--adding new file types just to a specific device will have no affect-->
		<device name="default">
			<!--specify the maximum length for file names (0 or empty = unlimited)-->
			<max_file_name_length>0</max_file_name_length>
			<!--[file|container]-->
			<playlist_style>file</playlist_style>
			<show_childcount_in_title>false</show_childcount_in_title>
			<enable_dlna>false</enable_dlna>
			<transcoding_release_delay>4</transcoding_release_delay>
			<file_settings>
				<!--audio files-->
				<file ext="mp3">
					<type>AUDIO_ITEM</type>
					<mime_type>audio/mpeg</mime_type>
					<dlna>MP3</dlna>
				</file>
				<file ext="ogg">
					<type>AUDIO_ITEM</type>
					<mime_type>application/octet-stream</mime_type>
					<transcode enabled="true">
						<ext>mp3</ext>
						<mime_type>audio/mpeg</mime_type>
						<dlna>MP3</dlna>
						<http_encoding>chunked</http_encoding>
						<decoder>vorbis</decoder>
						<encoder>lame</encoder>
						<bitrate>192</bitrate>
						<samplerate>44100</samplerate>
					</transcode>
				</file>
				<file ext="mpc">
					<type>AUDIO_ITEM</type>
					<mime_type>application/octet-stream</mime_type>
					<transcode enabled="true">
						<ext>mp3</ext>
						<mime_type>audio/mpeg</mime_type>
						<dlna>MP3</dlna>
						<http_encoding>chunked</http_encoding>
						<decoder>musepack</decoder>
						<encoder>lame</encoder>
						<bitrate>192</bitrate>
						<samplerate>44100</samplerate>
					</transcode>
				</file>
				<file ext="wav">
					<type>AUDIO_ITEM</type>
					<mime_type>audio/x-wav</mime_type>
					<!-- <dlna>L16</dlna> -->
				</file>
				<file ext="flac">
					<type>AUDIO_ITEM</type>
					<mime_type>audio/x-flac</mime_type>
					<transcode enabled="true">
						<ext>wav</ext>
						<mime_type>audio/x-wav</mime_type>
						<dlna>WAV</dlna>
						<http_encoding>stream</http_encoding>
						<decoder>flac</decoder>
						<encoder>wav</encoder>
					</transcode>
				</file>
				<file ext="wma">
					<type>AUDIO_ITEM</type>
					<mime_type>audio/x-ms-wma</mime_type>
					<dlna>WMAFULL</dlna>
				</file>
				<!--image files-->
				<file ext="jpg">
					<ext>jpeg</ext>
					<type>IMAGE_ITEM</type>
					<mime_type>image/jpeg</mime_type>
					<convert enabled="false">
						<!--<dcraw enabled="true">-q 0</dcraw>-->
						<ext>png</ext>
						<mime_type>image/png</mime_type>
						<height>0</height>
						<width>0</width>
						<!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
						<greater>false</greater>
						<!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
						<less>false</less>
						<!--set "less" and "greater" to "false" if you always want to resize-->
					</convert>
				</file>
				<file ext="bmp">
					<type>IMAGE_ITEM</type>
					<mime_type>image/bmp</mime_type>
				</file>
				<file ext="png">
					<type>IMAGE_ITEM</type>
					<mime_type>image/png</mime_type>
				</file>
				<file ext="gif">
					<type>IMAGE_ITEM</type>
					<mime_type>image/gif</mime_type>
				</file>
				<!--video files-->
				<file ext="mpg">
					<ext>mpeg</ext>
					<type>VIDEO_ITEM</type>
					<mime_type>video/mpeg</mime_type>
				</file>
				<file ext="mp4">
					<type>VIDEO_ITEM</type>
					<mime_type>video/mp4</mime_type>
				</file>
				<file ext="avi">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-msvideo</mime_type>
				</file>
				<file ext="wmv">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-ms-wmv</mime_type>
				</file>
				<file ext="vob">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-ms-vob</mime_type>
				</file>
				<file ext="mkv">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-matroska</mime_type>
				</file>
				<file ext="vdr">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-extension-vdr</mime_type>
					<transcode enabled="true">
						<ext>vob</ext>
						<mime_type>video/x-ms-vob</mime_type>
					</transcode>
				</file>
				<file ext="flv">
					<type>VIDEO_ITEM</type>
					<mime_type>application/x-flash-video</mime_type>
				</file>
				<file ext="asf">
					<type>VIDEO_ITEM</type>
					<mime_type>video/x-ms-asf</mime_type>
				</file>
				<!--playlists-->
				<file ext="pls">
					<type>PLAYLIST</type>
					<mime_type>audio/x-scpls</mime_type>
				</file>
				<file ext="m3u">
					<type>PLAYLIST</type>
					<mime_type>audio/x-mpegurl</mime_type>
				</file>
				<file ext="wpl">
					<type>PLAYLIST</type>
					<mime_type>application/vnd.ms-wpl</mime_type>
				</file>
			</file_settings>
		</device>
		<!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
		<!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
		<!--It is safe to remove unneeded devices-->
		<device name="PS3" enabled="true">
			<user_agent>UPnP/1.0 DLNADOC/1.50</user_agent>
			<user_agent>PLAYSTATION 3</user_agent>
			<!--<ip></ip>-->
			<enable_dlna>true</enable_dlna>
			<transcoding_release_delay>50</transcoding_release_delay>
			<file_settings>
				<file ext="ogg">
					<type>AUDIO_ITEM_MUSIC_TRACK</type>
					<transcode enabled="true">
						<http_encoding>stream</http_encoding>
					</transcode>
				</file>
				<file ext="flac">
					<type>AUDIO_ITEM_MUSIC_TRACK</type>
					<transcode enabled="true">
						<http_encoding>stream</http_encoding>
					</transcode>
				</file>
			</file_settings>
		</device>
	</device_settings>
</fuppes_config>
```

Note that based on observing the logs I changed the PS3 useragent lines (1.00 to 1.50 and a space between PLAYSTATION and 3) but it made no difference. Mine is a PS3 Slim in case it matters.

As far as I can see transcoding is not even attempted. There are no messages at log level 3 about transcoding. I'm guessing that the wrong metadata is being sent so the PS3 doesn't bother trying to play the file.

Has anyone got a definitive config to transcode for the PS3?

Thanks

---

### Post by Canto39 on 2010-02-22
I don't seem to have a hidden .fuppes folder in my home directory or a fuppes.cfg file. Can someone help me?

---

### Post by Canto39 on 2010-02-22
I got it to work! this is great, thanks for the guide

---

### Post by Xavier de Salaberry on 2010-02-23
when i get to the ldconfig step, i get this.  Ideas?

> 
xavier@Xavier-Laptop:~/fuppes$ ldconfig
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied


---

### Post by endlessracingz on 2010-02-23
Something is very wrong for me at the moment. I have a system that has not had fuppes previously installed.

When trying to follow the guide (first post by [PorchSong]("http://ubuntuforums.org/member.php?u=448485")) I receive the following

```
$ sudo apt-get install ffmpeg build-essential \
> libavutil-dev libavformat-dev libavcodec-dev \
> subversion libtool \
> libsqlite3-dev libpcre3-dev libxml2-dev libpcre3-dev pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavcodec-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavcodec52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavcodec-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavdevice52 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavdevice52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavfilter0 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavfilter0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavfilter-extra-0 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavformat52 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavformat-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavformat52 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavformat-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libavutil49 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libavutil49 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libavutil-extra-49 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libpostproc51 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libpostproc-extra-51 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libpostproc51 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libpostproc-extra-51 (< 4:0.5+svn20090706-99) but it is not going to be installed
          Depends: libsdl1.2debian (>= 1.2.10-1) but it is not going to be installed
          Depends: libswscale0 (>= 4:0.5+svn20090706) but it is not going to be installed or
                   libswscale-extra-0 (>= 4:0.5+svn20090706) but it is not going to be installed
          Depends: libswscale0 (< 4:0.5+svn20090706-99) but it is not going to be installed or
                   libswscale-extra-0 (< 4:0.5+svn20090706-99) but it is not going to be installed
  fuppes: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libgif4 (>= 4.1.6) but it is not going to be installed
          Depends: libjpeg62 but it is not going to be installed
          Depends: libmad0 (>= 0.15.1b) but it is not going to be installed
          Depends: libmagick++10 but it is not installable
          Depends: libmagick10 but it is not installable
          Depends: libogg0 but it is not going to be installed
          Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
          Depends: libraw1394-8 but it is not installable
          Depends: libsimage20 but it is not going to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not installable
          Depends: libtag1c2a (>= 1.4) but it is not going to be installed
          Depends: libtheora0 but it is not going to be installed
          Depends: libtiff4 but it is not going to be installed
          Depends: libvorbis0a (>= 1.2.0) but it is not going to be installed
          Depends: libvorbisenc2 (>= 1.1.2) but it is not going to be installed
          Depends: libvorbisfile3 (>= 1.2.0) but it is not going to be installed
  libavcodec-dev: Depends: libavcodec52 (>= 4:0.5+svn20090706-2ubuntu2) but it is not going to be installed or
                           libavcodec-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
                  Depends: libavcodec52 (<= 4:0.5+svn20090706-99) but it is not going to be installed or
                           libavcodec-extra-52 (<= 4:0.5+svn20090706-99) but it is not going to be installed
  libavformat-dev: Depends: libavformat52 (>= 4:0.5+svn20090706-2ubuntu2) but it is not going to be installed or
                            libavformat-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
                   Depends: libavformat52 (<= 4:0.5+svn20090706-99) but it is not going to be installed or
                            libavformat-extra-52 (<= 4:0.5+svn20090706-99) but it is not going to be installed
  libavutil-dev: Depends: libavutil49 (>= 4:0.5+svn20090706-2ubuntu2) but it is not going to be installed or
                          libavutil-extra-49 (>= 4:0.5+svn20090706) but it is not going to be installed
                 Depends: libavutil49 (<= 4:0.5+svn20090706-99) but it is not going to be installed or
                          libavutil-extra-49 (<= 4:0.5+svn20090706-99) but it is not going to be installed
  libpcre3-dev: Depends: libpcrecpp0 (= 7.8-3) but it is not going to be installed
  libtool: Depends: autotools-dev but it is not going to be installed
           Recommends: libltdl-dev but it is not going to be installed
  libxml2-dev: Depends: zlib1g-dev but it is not going to be installed or
                        libz-dev
  subversion: Depends: libsvn1 (= 1.6.5dfsg-1ubuntu1) but it is not going to be installed
              Depends: libapr1 (>= 1.2.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```It is obvious that there are missing dependencies but when i attempt to run ```
sudo apt-get -f install
``` for any or all of the packages i receive the same errors...

I am absolutely lost on what the problem is... this is probably a complete newbie issue. Please help.

---

### Post by Canto39 on 2010-02-24
If I am downloading something on the PC that I am streaming from, will it affect the stream?

---

### Post by PorchSong on 2010-02-25
> **Canto39 said:**
> If I am downloading something on the PC that I am streaming from, will it affect the stream?

I do it all the time with no problems.

---

### Post by Coinneach on 2010-02-25
> **Xavier de Salaberry said:**
> when i get to the ldconfig step, i get this.  Ideas?
Quote:
xavier@Xavier-Laptop:~/fuppes$ ldconfig
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied 
I got the same thing so I just did "sudo ldconfig" and all was fine. I have successfully installed Fuppes and have it running AVIs, MP3s, and pictures. Everyting I download is pretty much AVI format so I don't really care if the other video work or not.

Btw, I followed the guide exactly on a fresh install of 9.10.

---

### Post by adenewton on 2010-02-26
I installed fuppes via the getdeb site sas i had major problems compiling it. Now I get this problem,

I ran it as
/usr/bin/fuppes --plugin-dir /usr/lib/fuppes/

as it gives me a failed to initialize sqlite database plugin. message if i just type fuppes.

which did launch it, however if i then go to the web browser to view the setup it says page cannot be displayed and when i look in the terminal the app has closed.

any ideas? here is the output from my terminal:

ade@ade-ubuntu:~$ /usr/bin/fuppes
FUPPES - 0.662
the Free UPnP Entertainment Service
[http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

failed to initialize sqlite database plugin.
ade@ade-ubuntu:~$ /usr/bin/fuppes --plugin-dir /usr/lib/fuppes/
FUPPES - 0.662
the Free UPnP Entertainment Service
[http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

error load symbol 'fuppes_encoder_set_audio_settings'
webinterface: [http://192.168.1.67:5001](http://192.168.1.67:5001)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

Segmentation fault

---

### Post by adenewton on 2010-03-03
I've reinstalled my system at the weekend in order to try and get fuppes working on a clean install. Sods law, getdeb has now been down for 5 days!

I don't suppose anyone has a copy of the deb they could upload somewhere so that I could grab it as I would really like to ensure I can get this working before I start re-installing everything else onto my system.

---

### Post by sensory on 2010-03-04
> **adenewton said:**
> I've reinstalled my system at the weekend in order to try and get fuppes working on a clean install. Sods law, getdeb has now been down for 5 days!

I don't suppose anyone has a copy of the deb they could upload somewhere so that I could grab it as I would really like to ensure I can get this working before I start re-installing everything else onto my system.

I'm in the same boat but doubly as annoying because I somehow succeeded in compiling fuppes from source but couldn't reproduce it after a clean install of karmic. :(

If any one has that .deb it'd be great. I'd hate to go back to uShare..

edit: FOUND IT.[http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/apps/f/fuppes/]("http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/apps/f/fuppes/") :D

---

### Post by scmior on 2010-03-05
Hello I am attempting the guide but when I am at the 
ldconfig 


section it tells me 

/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied

and I can not find the fuppies.cnfig file.

anyone have nay ideas to help?

Thank a bunch

---

### Post by adenewton on 2010-03-05
> **sensory said:**
> I'm in the same boat but doubly as annoying because I somehow succeeded in compiling fuppes from source but couldn't reproduce it after a clean install of karmic. :(

If any one has that .deb it'd be great. I'd hate to go back to uShare..

edit: FOUND IT.[http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/apps/f/fuppes/]("http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/apps/f/fuppes/") :D

Every getdeb mirror I could find was out of date, dunno how you found that one, but you are the main man! :D

---

### Post by sensory on 2010-03-05
> **adenewton said:**
> Every getdeb mirror I could find was out of date, dunno how you found that one, but you are the main man! :D
I can't take all the credit; Google helped a lot. :D

---

### Post by twisted_steel on 2010-03-06
> **scmior said:**
> Hello I am attempting the guide but when I am at the 
ldconfig 


section it tells me 

/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied

and I can not find the fuppies.cnfig file.

anyone have nay ideas to help?

Thank a bunch

For the first issue, try doing "sudo ldconfig".  For the second, I believe you have to create the config file yourself.  It should be located at /home/youruser/.fuppes/fuppes.cfg.

---

### Post by vtnerd on 2010-03-07
I pretty much registered on these forums because of the interest I have in this project. I am a Gentoo user, but my comments here should help some people. For starters this project seems like it has some bugs - I had to track down a buffer overflow just to get her working ... but let me hopefully solve a problem that I think has not yet been fixed.

> 
I've been following these threads for quite a while, and am getting  tired of not being able to solve my issue! It is the same issue others  have had, w/o a solution being posted yet. I have followed the guide on  page one for .657 (along with numerous other guides at various points),  and am unable to view the Genre/Album/Artist info- all the songs get  lumped into the "songs" category. So, here are the data points I have:

- I am able to see my music folders under the  "My Videos" xbox console,  but all the songs are unable to be played (no error, they just dont  play and have a "null" icon for a picture)
- When I go to My Music, all the songs are lumped under the songs  category, and are not broken out by Artist/Genre/Album like I would  expect. 
For those having this problem ... I *may* have solution. One issue with this project is that by default it is configured to install stuff in "/usr/local". There is nothing wrong with this, except that it looks for some of the dependencies in that folder taglib-config being one of them. Of course any distro installed this in "/usr/bin/", so its never found. The solution is to run "--prefix=/usr", which enables fuppes to find the taglib dependency. But a new problem is created, because this also installs fuppes into "/usr" now. Anyone who did not do a "make uninstall" before running such a thing will have the "old" plugins still in /usr/local, and this is what fuppes is most likely picking up. Your other posts suggest this too.

In summary, based on your posts you should run fuppes with the command "--plugin-dir /usr/lib/fuppes". In fact anyone that did a "./configure" with "--prefix=/usr" should run fuppes in this fashion. I don't like the plugin method that this program uses, but hopefully the original author had a good reason for doing this.

And to whomever has control of this project I may be able to help out with some bug control (which I suspect there still may be some). Just PM if you think you could use the help.

Oh and about that buffer overflow, I think its a problem someone else was having too. The problem is with a sprintf call - it was used incorrectly. In fact I didn't even notice it at passing glance, but width is clearly stated as "not being truncated if the value is longer". Gotta love C format functions.

---

### Post by neoroses on 2010-03-09
> **Canto39 said:**
> I don't seem to have a hidden .fuppes folder in my home directory or a fuppes.cfg file. Can someone help me?

i had the same issue, just run fuppes in the terminal then quit and it should be there

---

### Post by illy123 on 2010-03-09
Thanks for the guide.

I've connected to my linux server with SSH (SOCKS proxy browser) - how would I stream files from my server to my laptop?

When I go to the web interface it is a configuration file rather than something like tversity's one where you can stream the videos

---

### Post by derfnerd on 2010-03-13
> **vtnerd said:**
> I pretty much registered on these forums because of the interest I have in this project. I am a Gentoo user, but my comments here should help some people. For starters this project seems like it has some bugs - I had to track down a buffer overflow just to get her working ... but let me hopefully solve a problem that I think has not yet been fixed.

For those having this problem ... I *may* have solution. One issue with this project is that by default it is configured to install stuff in "/usr/local". There is nothing wrong with this, except that it looks for some of the dependencies in that folder taglib-config being one of them. Of course any distro installed this in "/usr/bin/", so its never found. The solution is to run "--prefix=/usr", which enables fuppes to find the taglib dependency. But a new problem is created, because this also installs fuppes into "/usr" now. Anyone who did not do a "make uninstall" before running such a thing will have the "old" plugins still in /usr/local, and this is what fuppes is most likely picking up. Your other posts suggest this too.

In summary, based on your posts you should run fuppes with the command "--plugin-dir /usr/lib/fuppes". In fact anyone that did a "./configure" with "--prefix=/usr" should run fuppes in this fashion. I don't like the plugin method that this program uses, but hopefully the original author had a good reason for doing this.


OK! I just logged back on to post MY solution, and it looks like you have a very similar one as well. I noticed that in my web interface, it still had an old version number being displayed, despite having compiled a more recent version. It looks like indeed the old plugins were never updated/removed/whatever. My solution (not trusting anything else from the install scripts) was to go through, do a 'whereis fuppes' and delete *everything* that it listed (keeping my cfg file, of course). I then recompiled from the most recent version, using the tutorial instructions on the front of this post, and everything worked! Hopefully the maintains can take this into account and look for old, "improperly" installed versions in the next install script. So for the others having this problem (and you have installed stuff "incorrectly previously", that's your answer!

---

### Post by Adrian Challinor on 2010-03-15
Like others, I am trying to run Fuppes from a **Ubuntu 9.10 headless-Server**. It all compiles and runs fine. I can see the audio files and the fuppes db builds correctly. 

I turn on debug level messages by "l <cr> l". I can see devices connecting, but no device finds any data. Connecting from a Ubuntu workstation using firefox gives me a totally blank screen. 

I recompiled on the 9.10 workstation and all worked as expected. 

So what do I need to add to the server to make it generate HTML output? 

Adrian

---

### Post by bladerunner6 on 2010-03-15
anyone know how to get the applet panel feature working? doesnt seem to work i checked all the dependancies dev files for gnome applet etc

---

### Post by mattjones124 on 2010-03-15
Is there a way to stop Fuppes from showing hidden files?

---

### Post by Drain on 2010-03-21
That's a very thorough How-To, and it seems like a lot of people have had some success with installing FUPPES.  Just out of curiosity, though, is there any reason why the instructions don't involve something like:

```

$ ./configure --prefix=/usr
$ sudo make
$ sudo checkinstall
```

Creating and installing the program via a package seems a little more "refined," and easier to clean up should things go wrong.  Which is kind of what happened to me.  I've got it running using the Get-Deb source now, but mainly because I couldn't compile the latest version, svn-664.   Everything seems to go alright, but I get a "Segmentation Fault" error when I run Fuppes.  Is this a problem with the build?  Anyone else run into it?

My minor nitpicking about the .deb version (.640) is that it doesn't seem to like when I add my 10,000 mp3s or 10,000 pictures to the mix.  It will stream my couple-100 movies alright, but if I try and update the database or the virtual containers, it appears to be overwhelmed.  My .cfg files don't appear to be the problem.  Any thoughts about how to trouble-shoot this?

---

### Post by vtnerd on 2010-03-24
> **Drain said:**
> That's a very thorough How-To, and it seems like a lot of people have had some success with installing FUPPES.  Just out of curiosity, though, is there any reason why the instructions don't involve something like:

```

$ ./configure --prefix=/usr
$ sudo make
$ sudo checkinstall
```Creating and installing the program via a package seems a little more "refined," and easier to clean up should things go wrong.  Which is kind of what happened to me.  I've got it running using the Get-Deb source now, but mainly because I couldn't compile the latest version, svn-664.   Everything seems to go alright, but I get a "Segmentation Fault" error when I run Fuppes.  Is this a problem with the build?  Anyone else run into it?

My minor nitpicking about the .deb version (.640) is that it doesn't seem to like when I add my 10,000 mp3s or 10,000 pictures to the mix.  It will stream my couple-100 movies alright, but if I try and update the database or the virtual containers, it appears to be overwhelmed.  My .cfg files don't appear to be the problem.  Any thoughts about how to trouble-shoot this?

I have a patch that probably works, I found a buffer overflow that occurred while database building. Since I don't feel like trying to figure out how to upload files on this forum:

```

Index: src/plugins/metadata_libavformat.c
===================================================================
--- src/plugins/metadata_libavformat.c  (revision 662)
+++ src/plugins/metadata_libavformat.c  (working copy)
@@ -86,7 +86,7 @@
                mins %= 60;
        
                char szDuration[12];
-         sprintf(szDuration, "%02d:%02d:%02d.%02d", hours, mins, secs, (10 * us) / AV_TIME_BASE);
+         snprintf(szDuration, 12, "%02d:%02d:%02d.%02d", hours, mins, secs, (10 * us) / AV_TIME_BASE);
          szDuration[11] = '\0';
                
                set_value(&metadata->duration, szDuration);

```Copy-paste that and save it to a file. Then run this command from your local fuppes folder:
```

patch -p0 -i [path to file]
```The make again, install, etc. To my knowledge this should only overflow when hours > 99 since the other values should always be guaranteed to be less than 100. This is possible if AV_TIME_BASE is some really small value. I think this value represents FPS in videos, but who knows. I just hope by (sometimes) forcefully truncating the string, I am not destroying any functions that rely on that string.

---

### Post by Shanawa on 2010-03-25
So I am at this part of the install:

$ sudo make install
$ sudo ldconfig

When I entered sudo ldconfig I didn't see anything happen. I went to look for the /.fuppes folder and didn't see anything. It should be between /.evolution and /.gconf right? I entered sudo ldconfig again and it asked for a password but nothing happened again after that.

I'm new to linux so be gentle :)

***Update: I ended up just creating the /.fuppes directory and ended up making the 2 files and then starting fuppes too make the fuppes.db file .***

---

### Post by Shanawa on 2010-03-25
I got my xbox 360 to see the 2 folders that are on the linux box but I also have some windows boxes that have shared folders that I can't seem to see. I tried putting in the filemanager address in there but its not working. I can access the folder through file manager just fine.

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>smb://shan-pc/movies%20hd%20xbox/</dir>
    <dir>/media/B6909DBA909D8213/Movies</dir>
    <dir>/media/Temp/Movies3</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>10.0.0.1</ip>-->
      <ip>10.0.0.9</ip>
      <ip>10.0.0.4</ip>
      <ip>10.0.0.7</ip>
    </allowed_ips>
```

---

### Post by timwight on 2010-03-26
Very helpful thread, thanks.  

I have successfully installed Fuppes and can see it from my Xbox -- all seems to be working fine.  I would also like to serve media at home to my smartphone, an HTC Touch HD.  I have adjusted fuppes.sfg so that the phone upnp app (Pocket Player) finds Fuppes on the network, but it finds no media.  Meanwhile Fuppes returns the following message:

unhandled sort order
your device requested a sort order that is currently not supported by FUPPES. This is not a bug as FUPPES correctly specifies it's sorting capabilities but your device seems to ignore it.
please file a feature request containing the following lines: 

=== CUT ===
+dc:creator,+upnp:album,+upnp:originalTrackNumber,+dc:title
=== CUT ===


I guess I have to adjust vfolder.cfg, and would welcome any hints/advice

Rgds

Tim

---

### Post by TurboZinc on 2010-03-28
Figured it out. Thanks

---

### Post by ortayus on 2010-03-30
PorchSong,

Thanks for the guide, it worked without any issues.

---

### Post by KillaB7 on 2010-04-04
@Shhnap

I totally forgot about that ACL bug until my PS3 was assigned a new IP Address.

Here's that bug ticket you requested awhile back:
[http://sourceforge.net/tracker/?func=detail&aid=2981963&group_id=141999&atid=751213](http://sourceforge.net/tracker/?func=detail&aid=2981963&group_id=141999&atid=751213)

---

### Post by KillaB7 on 2010-04-05
> **KillaB7 said:**
> @Shhnap

I totally forgot about that ACL bug until my PS3 was assigned a new IP Address.

Here's that bug ticket you requested awhile back:
[http://sourceforge.net/tracker/?func=detail&aid=2981963&group_id=141999&atid=751213](http://sourceforge.net/tracker/?func=detail&aid=2981963&group_id=141999&atid=751213)


Fixed and lightly tested. 192.168.**255**.0/24 is a valid subnet, correct?

```

diff -Nur fuppes664/trunk/src/lib/SharedConfig.cpp fuppes664_mod/trunk/src/lib/SharedConfig.cpp
--- fuppes664/trunk/src/lib/SharedConfig.cpp	2010-04-04 23:51:50.084583156 -0700
+++ fuppes664_mod/trunk/src/lib/SharedConfig.cpp	2010-04-05 00:01:30.168582498 -0700
@@ -365,8 +365,8 @@
   for(unsigned int i = 0; i < AllowedIPCount(); i++) { 
 
 		string pattern = GetAllowedIP(i);
-		pattern = StringReplace(pattern, ".*.", "[255]");
-		pattern = StringReplace(pattern, "*", "255");
+		pattern = StringReplace(pattern, ".*.", ".[0-255].");
+		pattern = StringReplace(pattern, "*", "[1-254]");
 
 		RegEx rxIp(pattern.c_str());
 		if(rxIp.Search(p_sIPAddress.c_str()))

```

---

### Post by CapnCaveman on 2010-05-05
I've just done a fresh install of Lucid, but now my Fuppes  (664 from the svn) is crashing on me, I get the following message on console



```
scott@greytower:~/fuppes$ :2: namespace error : xmlns:u: Empty XML namespace is not allowed
as.xmlsoap.org/soap/encoding/"><s:Body><u:GetSpecificPortMappingEntry xmlns:u=""
                                                                               ^
:2: namespace error : Namespace prefix u on GetSpecificPortMappingEntry is not defined
as.xmlsoap.org/soap/encoding/"><s:Body><u:GetSpecificPortMappingEntry xmlns:u=""
                                                                               ^
malformed xml
fuppesd: lib/HTTP/HTTPMessage.cpp:160: std::string CHTTPMessage::GetHeaderAsString(): Assertion `0' failed.
```

Is anyone else having this problem.  Streaming avi to an XBOX360 works great until it borks, although it craps out even when idle

---

### Post by Shhnap on 2010-05-05
Um, that is the weirdest thing that I have ever seen and I'll explain why:

```
malformed xml
fuppesd: lib/HTTP/HTTPMessage.cpp:160: std::string CHTTPMessage::GetHeaderAsString(): Assertion `0'
```

That points to the following segment of code:

```
/* Version */
switch(m_nHTTPVersion)
{
  case HTTP_VERSION_1_0: sVersion = "HTTP/1.0"; break;
  case HTTP_VERSION_1_1: sVersion = "HTTP/1.1"; break;
  default:               ASSERT(0);             break;
}

```

So your problem is being caused by the fact that your XBox is not sending a correct HTTP header. That is just odd. Can you tell me in more detail what you were doing to cause it? 

P.S. And if you know how to use wireshark then could you send me the header that the XBox gives you?

---

### Post by CapnCaveman on 2010-05-06
I had a wide open IP range in my fuppes.cfg so I'm wondering if maybe another of the myriad devices at home was causing the problem.  I restricted it to just the xbox360 and media server IP's so we'll see if that works better.  If not I'll try and setup a sniff tomorrow on Wireshark

---

### Post by Shhnap on 2010-05-06
That would be great and really good if you could do that.

Oh also, even though I like checking these forums, this is not really the right place for fuppes bugs. The better place to get those issues resolved would be: [on Sourceforge]("https://sourceforge.net/tracker/?group_id=141999&atid=751213")

That way we can track it properly and everyone that wants to do work on fuppes, or has the same bug, can see it.

Thanks.

---

### Post by CapnCaveman on 2010-05-07
I've posted on the Bug Tracker, here's the wireshark capture from when the crash happened.  The xbox360 is 192.168.2.8 and packet 6578 is when I got the crash message in my fuppes terminal as above.  

6578    708.738279    192.168.2.9    192.168.2.8    TCP    53149 > cap [FIN, ACK] Seq=148 Ack=1674 Win=11712 Len=0
6579    708.738413    192.168.2.8    192.168.2.9    TCP    cap > 53149 [RST] Seq=1674 Win=0 Len=0

---

### Post by s73v3r on 2010-05-08
I was able to get Fuppes to compile and install correctly without problems. However, the Xbox 360 cannot see Fuppes. Fuppes says it is able to see it from the web interface, and the debug statements show it being discovered. What are some of the solutions you guys have used to fix this? I'm using the latest trunk version from SVN.

---

### Post by KillaB7 on 2010-05-08
> **s73v3r said:**
> I was able to get Fuppes to compile and install correctly without problems. However, the Xbox 360 cannot see Fuppes. Fuppes says it is able to see it from the web interface, and the debug statements show it being discovered. What are some of the solutions you guys have used to fix this? I'm using the latest trunk version from SVN.

Make sure the IP address of your Xbox is listed in the fuppes configuration file, and that the line is uncommented. Restart fuppes if you had to make any changes.

Example:
<ip>192.168.1.25</ip>

---

### Post by Pete420 on 2010-05-14
Hello New user on the forums here but been an ubuntu user for awhile. anyway tring to get fuppes to transcode .flac into pcm/wav so the ps3 will play it but it is not working here is my config file as of now. tried with using wav instead of l16 but did not work either.

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/hd2/music</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.1.4</ip>
<ip>192.168.1.5</ip>  
  </allowed_ips>

  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
   
       <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
<file ext="flac">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-flac</mime_type>
<transcode enabled="true">
<ext>l16</ext>
<mime_type>audio/l16</mime_type>
<dlna>l16</dlna>
<http_encoding>stream</http_encoding>
<decoder>flac</decoder>
<encoder>wav</encoder>
</transcode>
</file>      
</file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
        </file_settings>
    <description_values>
    <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
    <model_name>Windows Media Connect compatible (%s)</model_name>
    <model_number>2.0</model_number>
    </description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>


any help is greatly appreciated

---

### Post by celtic_smith on 2010-05-27
Hi there, I am very NEWB, first post!

I am trying to install FUPPES, I followed the install instructions to the letter(as well as sever others) and I keep getting this error anytime I try to run fuppes from the terminal

Shared (Base) Config File:/home/(my dir)/.fuppes/fuppes.cfg
[config] Warning: The Global settings could not be read.
[config] ERROR: A device mapping could not be found and one is required. Even an empty device mapping will work. (The empty device mapping makes everything use the default device)
[config] The config file failed to load properly.


can't find any help , I would love to get some feedback to wee where I have gone wrong.

many thanks

Graeme

---

### Post by Shhnap on 2010-05-27
> **celtic_smith said:**
> Hi there, I am very NEWB, first post!

I am trying to install FUPPES, I followed the install instructions to the letter(as well as sever others) and I keep getting this error anytime I try to run fuppes from the terminal

Shared (Base) Config File:/home/(my dir)/.fuppes/fuppes.cfg
[config] Warning: The Global settings could not be read.
[config] ERROR: A device mapping could not be found and one is required. Even an empty device mapping will work. (The empty device mapping makes everything use the default device)
[config] The config file failed to load properly.


can't find any help , I would love to get some feedback to wee where I have gone wrong.

many thanks

Graeme

Huh, I think that I can help you because I was the one that wrote those very error messages that you are getting. :D

Very recently Uli and I decided that it was ugly and cumbersome to have one large config file when much of it does not change. As a result I split up the entire config file into many little ones. This will make the config files much easier to deal with in the future. For now though we have to make sure that you get the correct config files for the changes that I made. If you look here ([http://fuppes.svn.sourceforge.net/viewvc/fuppes/trunk/config/](http://fuppes.svn.sourceforge.net/viewvc/fuppes/trunk/config/)) at the latest version of the Fuppes SVN you will see all of the files that you are supposed to use now instead.

The solution is simple:

```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk/config
cd config
rm Makefile.am
cp * ~/.fuppes

```

And then try and run fuppes again. That code checks out the config dir and moves all of the required code into the .fuppes directory for you to use.

Please note that if that still does not work then I may have to double check what is going wrong. (Because something odd is happening as I thought that this case was going to be covered by a different error message that was supposed to say something like 'using wrong version of the config file.')

P.S. You have to run that code in the 'gnome-terminal'. Just find the terminal in 'Applications -> Acessories' and copy and paste the code in.

---

### Post by Mikkis on 2010-05-28
Hi,

I'm newbie in all this compiling stuff, but tried to follow the instructions from post#1 to compile the latest fuppes version. It gave me this error:
```

Making install in resources
make[1]: Entering directory `/usr/src/fuppes/resources'
make[1]: *** No rule to make target `header-gradient-small.png', needed by `all-am'.  Stop.
make[1]: Leaving directory `/usr/src/fuppes/resources'
make: *** [install-recursive] Error 1

```Any idea why that happens?

---

### Post by mathfreak on 2010-05-30
> **Mikkis said:**
> Hi,

I'm newbie in all this compiling stuff, but tried to follow the instructions from post#1 to compile the latest fuppes version. It gave me this error:
```

Making install in resources
make[1]: Entering directory `/usr/src/fuppes/resources'
make[1]: *** No rule to make target `header-gradient-small.png', needed by `all-am'.  Stop.
make[1]: Leaving directory `/usr/src/fuppes/resources'
make: *** [install-recursive] Error 1

```Any idea why that happens?

I had the same issue. It looks like that file just wasn't included in the latest svn trunk. I just downloaded the tarball [from here]("http://fuppes.ulrich-voelkel.de/download/"), extracted it, and copied the file src/lib/Presentation/header-gradient-small.png into the resources directory.

---

### Post by Mikkis on 2010-05-30
> **mathfreak said:**
> I had the same issue. It looks like that file just wasn't included in the latest svn trunk. I just downloaded the tarball [from here]("http://fuppes.ulrich-voelkel.de/download/"), extracted it, and copied the file src/lib/Presentation/header-gradient-small.png into the resources directory.

Thanks, that helped. Still having problems playing anything on Xbox360 or XBMC.

As I posted over here:
[https://sourceforge.net/projects/fuppes/forums/forum/475749/topic/3712124](https://sourceforge.net/projects/fuppes/forums/forum/475749/topic/3712124)

So fuppes recognizes XBox360, but doesn't seem to use that information.

Error message:
```

SQL select error: near "%": syntax error :: select OBJECT_ID from  
OBJECTS where   PARENT_ID in (7) and   %DEVICE
SQL_VC_HAS_CHILDREN: select count(*) as VALUE from OBJECTS 
where  PARENT_ID = 22 and DEVICE = 'default'

```XBMC doesn't start playiing anything either (xbmc.log):
```

12:48:35 T:1436 M:2603753472   ERROR: 
CDVDPlayer::OpenInputStream -  error opening []
12:48:35 T:1436 M:2603753472  NOTICE: 
CDVDPlayer::OnExit()
12:48:35 T:1436 M:2603749376  NOTICE: 
CDVDPlayer::OnExit() deleting  input stream
12:48:35 T:1740 M:2603749376   ERROR: 
Playlist Player: skipping  unplayable item: 0, path []

```Nokia E72 does seem to work fine with fuppes although a bit slowly.

Any help appreciated.

---

### Post by Mikkis on 2010-05-30
> **Mikkis said:**
> 
```

SQL select error: near "%": syntax error :: select OBJECT_ID from  
OBJECTS where   PARENT_ID in (7) and   %DEVICE

```

Maybe that error is caused by this in /src/plugins/database_sqlite3_sql.h:
```

{
  SQL_SEARCH_GET_CHILDREN_OBJECT_IDS, 
  "select OBJECT_ID from OBJECTS "  "where "  
  "  PARENT_ID in (%OBJECT_ID%) and "  
  "  [COLOR=Red]%DEVICE[/COLOR] "
},

```Maybe should be [COLOR=SeaGreen]%DEVICE%[/COLOR] as in the other places?

Tried changing that, but still my Xbox360 is detected as 'default':
```

FriendlyName: Xbox 360 MAC: 00:XX:YY:ZZ:VV:KK (Real MAC removed)
SQL_VC_HAS_CHILDREN: select count(*) as VALUE from 
OBJECTS where PARENT_ID = 21 and DEVICE = 'default'
SQL_VC_HAS_CHILDREN: select count(*) as VALUE from 
OBJECTS where PARENT_ID = 22 and DEVICE = 'default'

```

---

### Post by fabis94 on 2010-06-01
I did everything correctly, and i can open my folder on my Xbox, but the thing is it says there are no videos. It displays all the folders, but no files :/

Also in the Web interface it says: 

> device settings

device: default

Is it supposed to be default?

---

### Post by Mikkis on 2010-06-02
> **fabis94 said:**
> I did everything correctly, and i can open my folder on my Xbox, but the thing is it says there are no videos. It displays all the folders, but no files :/

Also in the Web interface it says: 



Is it supposed to be default?
I think you should have both default and xbox somewhere when you scroll down.

It doesn't help the actual problem though

---

### Post by Mikkis on 2010-06-07
> **Mikkis said:**
> 
XBMC doesn't start playiing anything either (xbmc.log):
```

12:48:35 T:1436 M:2603753472   ERROR: 
CDVDPlayer::OpenInputStream -  error opening []
12:48:35 T:1436 M:2603753472  NOTICE: 
CDVDPlayer::OnExit()
12:48:35 T:1436 M:2603749376  NOTICE: 
CDVDPlayer::OnExit() deleting  input stream
12:48:35 T:1740 M:2603749376   ERROR: 
Playlist Player: skipping  unplayable item: 0, path []

```

This one seems to work when setting DLNA off in /Devices/default.cfg:
```
<enable_dlna>false</enable_dlna>
```The Xbox360 part should start working again once Ulrich gets the new vfolder and database stuff working as he replied in the bug tracker:
[http://sourceforge.net/tracker/?func=detail&aid=3011821&group_id=141999&atid=751213](http://sourceforge.net/tracker/?func=detail&aid=3011821&group_id=141999&atid=751213)

---

### Post by senseisimple on 2010-06-18
I may be a little late to the party but these instructions seem to be a slightly modified version... had a little trouble getting original to work on reliably on PS3 with transcoding... PS3 kept giving my unreadable errors.

[http://www.chrisnovoa.com/364_install-fuppes-0-661-on-ubuntu-9-10-karmic-x64 ]("http://www.chrisnovoa.com/364_install-fuppes-0-661-on-ubuntu-9-10-karmic-x64")

it's more detailed and updated... was able to get it to work on Lucid, too.

---

### Post by derfnerd on 2010-07-04
Hi all,

  I know there have been issues with large mp3 collections causing slowness with fuppes... has this ever been fixed, or has anyone found a better way to organize collections, perhaps? I have about 2,000 files archived in different locations, and when I do only one path, it works well, but when I add in all my music paths, it takes forever to update the database, and much of the music is missing from the displayed listing. Any thoughts on how to correct this? Thanks

---

### Post by gilligan8 on 2010-07-23
I'm running 10.4 server but I followed your guide anyway.

Well, everything went well but I have this error when I run fuppes.

```
gilligan@Server:~$ fuppes
            FUPPES - 0.675
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

Shared (Base) Config File:/usr/local/etc/fuppes/fuppes.cfg
Can't create/open database: unable to open database file
[unknown] error opening database sqlite3
gilligan@Server:~$

```

---

### Post by dmm1000 on 2010-07-24
Hi Folks
I'm getting the same error as the poster above can ANYONE please help ? - someone must have had this error and been able to resolve ? Please ? :)

---

### Post by davnetuk on 2010-07-24
I too am having exactly the same issue. I've installed the sqlite and sqlite 3 packages too. Followed exactly the steps in the original post, note though the fuppes.cfg conf file is now stored in /usr/etc/fuppes/

Output when I try to run fuppes as a normal user..

fuppes
            FUPPES - 0.675
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

Shared (Base) Config File:/usr/etc/fuppes/fuppes.cfg
Can't create/open database: unable to open database file
[unknown] error opening database sqlite3

Can anyone help/advise?

---

### Post by gilligan8 on 2010-07-24
Hey guys... I have made *SOME* progress but it is really all for naught.

Basically no matter what I put in the config file for the database file it ignores it (maybe my syntax is wrong).

So I started using command line options to specify a db file since it seemed like a permission problem (not having access to wherever fuppes was trying to write to.)

Well, now I can launch fuppes... BUT again, it ignores anything I put in the config (like specifying a port).  I can still log in locally with 127.0.1.1:<some random port>.  BUT when I try to do anything to the config... like specify a port, it seg faults as soon as I hit "submit".  This is using w3m as I'm console only on this system (doubt that matters).

So, basically I got past the permission problem but still can't get anything to work.  Logs don't show anything when it crashes.

---

### Post by dmm1000 on 2010-07-24
Hi All
I too have made progress - basically I hadnt got sqlite3 installed - so have done that now - will continue trying to set this up

---

### Post by rancid1two on 2010-07-24
Manually create the ~/.fuppes directory on 10.4 and it should fix the sqlite error read error.

```
mkdir ~/.fuppes
```

---

### Post by gilligan8 on 2010-07-25
Ok, that is now sort of working.

I have to manually move the config file into that dir for it to read it... but it still can't write to it.  Anytime I change the config and hit "submit" (or even if I don't change anything and just hit "submit") it craps out with a seg fault.

Not a whole lot else I can do from where I am now as I'm working on it remotely... but that doesn't seem very stable to me.

But I can edit the config file manually and it will read those settings at least.

---

### Post by FlekkeN on 2010-07-31
you can also change the database file path in fuppes.cfg to somewhere it can create file. I also had the problem and created the ~./.fuppes folder and changed the path of database in fuppes.cfg to this:
```
<file>/home/username/.fuppes/fuppes.db</file>
```I propably had this problem because my config files are in /usr/etc/fuppes.

---

### Post by PlasticlightS on 2010-08-05
I've been getting this error when trying to run Fuppes on 10.04:

Shared (Base) Config File:/home/john/.fuppes/fuppes.cfg
/home/john/.fuppes/fuppes.cfg:202: parser error : Opening and ending tag mismatch: device line 40 and fuppes_config
</fuppes_config>
                ^
/home/john/.fuppes/fuppes.cfg:203: parser error : Premature end of data in tag device_settings line 38

^
/home/john/.fuppes/fuppes.cfg:203: parser error : Premature end of data in tag fuppes_config line 2

^
[config] The config file failed to load properly.

I've been searching for a few days and can't fix it, this would mean I no longer have any need for windows, so any help would be great. I'm relatively new to the forums/Ubuntu so if I haven't included anything, let me know.

---

### Post by SjLucky on 2010-08-07
So maybe I'm just retarded or not holding my mouth right or something but I cant get this to work. I got it to install. Which wasnt hard from the HOWTO but Jesus Christ I cant figure out this config file. I read the guide and I read the wiki but I guess I'm just thick cause I'm just got getting it. Maybe someone can help me out.

I'm starting out small with only my music collection. (I call it a library) But I really want to get my movies and tv shows that I have made backups of to stream to two 360s. Preferable at the same time. So this is what I get when I open a terminal and type "cd fuppes" then "fuppes"

> Shared (Base) Config File:/usr/etc/fuppes/fuppes.cfg
Can't create/open database: unable to open database file
[unknown] error opening database sqlite3
Aight, So I figure this is an user error on my part and it either has to do with the fuppes.cfg file itself or I do not have it in the location fuppes would like it to be. Since Im currently getting my Linux and software compiling cherry popped (at the same time, I feel so kinky) I really am a little... afraid to be slinging files around. So here is my fuppes.cfg file.

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.8">

  <shared_objects>
    <dir>/media/Music/Mp3</dir>
  </shared_objects>

  <network>
    <!--empty = automatic detection-->
    <interface>eth0<interface/>
    <!--empty or 0 = random port-->
    <http_port>42900<http_port/>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.10.*</ip>
    </allowed_ips>
  </network>

  <database type="sqlite3"> <!-- sqlite3 | mysql -->

    <!-- sqlite3 -->
    <file />  <!-- if empty default path will be used -->

    <!-- mysql -->
    <hostname />
    <username />
    <password />
    <dbname />

    <!-- common -->
    <readonly>false</readonly>
  </database>

  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>

    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>

  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>


  <!--
  enable virtual folder layouts 
  all vfolder layouts enabled here will be created and updated.
  if "default" is enabled all renderers (unless something else is set in the next part)
  will use that layout.
  -->
    <vfolders enabled="false">
        <vfolder name="default" enabled="true" />
        <vfolder name="xbox" enabled="false" />
    </vfolders>


  <!--
  map device settings and virtual folder layouts to a device
  if no vfolder is set "default" will be used (if enabled above).
  if vfolder is set to "none" no virtual layout will be used (even though it is enabled above) 
  -->
  <device_mapping>
   <device name="Xbox 360" virtual="Xbox 360" enabled="true">
  <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
  <user_agent>Xenon</user_agent>
  <xbox360>true</xbox360>
  <show_empty_resolution>true</show_empty_resolution>
  <description_values>
    <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
    <model_name>Windows Media Connect compatible (%s)</model_name>
    <model_number>2.0</model_number>
  </description_values>
  <file_settings>
    <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
    <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
  </file_settings>
</device>

  </device_mapping>

</fuppes_config>

```As you can see all I have is my mp3 dir and I think I have it setup to only stream to my local network. I tried like hell to make this work on my own but I'm now lost and don't know where to turn. If I could get a push in the right direction or better description of how I should set up my config file, I would dance at your wedding or bake you a cake or sacrifice some small animal in your honor. Thank you so much.

---

### Post by Kirix on 2010-08-08
I got past the "error opening database sqlite3" error by making a directory, and now I'm getting an error that says "ERROR: The config file is deprecated." Does anyone know how to fix this?

---

### Post by SjLucky on 2010-08-08
HAHAHA I figured it out!\\:D/

All I did was rename my fuppes folder to .fuppes and boom baby I got it to run! Wooo WHOO!! now I got to see if it works on my 360

---

### Post by Charlietje on 2010-08-21
Hi,

I have fuppes running without problems.
Now, I wanna split my movies in ABC
I changed the vfolder.cfg as following:

```

    <vfolder name="Videos">
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="ABC">
       <vfolders split="ABC">
         <items type="videoItem" />
       </vfolders>
      </vfolder>
    </vfolder>

```

I can see the split, but all abc folders are empty.
Does anyone know the vfolder property for the name of the file?

thanks.

---

### Post by mad_as_toast on 2010-08-22
I've given up. Couldn't get around a Segmentation Fault.

Installed mediatomb through the package manager and it works perfectly.

---

### Post by 7venoh3 on 2010-08-23
> **Kirix said:**
> I got past the "error opening database sqlite3" error by making a directory, and now I'm getting an error that says "ERROR: The config file is deprecated." Does anyone know how to fix this?

im having this same problem. im using 10.04. does anyone out there know what this means?? as far as i can tell the file is perfect

---

### Post by Charlietje on 2010-08-23
> **7venoh3 said:**
> im having this same problem. im using 10.04. does anyone out there know what this means?? as far as i can tell the file is perfect

I think you installed the svn version.
If that is the case, then you need to take the new configuration files from the source files.

---

### Post by 7venoh3 on 2010-08-24
well i figured it all out! not really, i downgraded my desk top to 9.10 and it just worked. however i had to install it without faad installed because it kept getting some error i couldnt figure out. the main point is i have it up and running and it can connect to my xbox :) the problem im having right now is that the xbox isnt showing and videos in any location! :O does someone know what might be the problem or how to fix it?

**edit** haha im a jackass. i had the directory misspelled

after restarting fuppes and pressing v,u and r. it compiled all of my videos for view. and spit out all of the /this/file/adding/now type things. but when connecting to xbox it still shows no videos. which makes me believe that its the vfolder that im having problems with now. could someone post their working vfolder, please?

also just for more reference into my problem. inside /usr/etc/fuppes there was no vfolder.cfg i created one and put it in there with the code from page 1. there was a vfolder FOLDER with inside a default.cfg and an xbox.cfg i also add a vfolder.cfg to this. to clarify which vfolder.cfg is everyone talking about when they mention it and where should it be located

i think i might just have this figured out soon. ive fixed some more of the code and when i press v to build the virtual folders i get this error

```
webinterface: http://192.168.1.2:58878

l = change log-level
    (disabled, normal, extended, debug) default is "normal"
i = print system info
s = print device settings
r = rebuild database
v = rebuild virtual container layout
u = update database
h = print this help

m = send m-search
a = send notify-alive
b = send notify-byebye

ctrl-c or q = quit

v[VirtualContainer] create virtual container layout started at Tue Aug 24 21:17:17 2010

[VirtualContainer] read vfolder layout from 'xbox.cfg'.
[VirtualContainer] load '/usr/etc/fuppes/vfolders/xbox.cfg'
create path for : vfolder*
  path for vfolder node : Music*
   vfolder node parent: vfolder_layout*
  result: folder | 
create path for : vfolder*
  path for vfolder node : Album*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolders*
create path for : vfolder*
  path for vfolder node : All Music*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Artist*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolders*
create path for : vfolder*
  path for vfolder node : Folders*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Genre*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolders*
create path for : vfolder*
  path for vfolder node : Playlist*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Pictures*
   vfolder node parent: vfolder_layout*
  result: folder | 
create path for : vfolder*
  path for vfolder node : Album*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : All Pictures*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Date Taken*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Folders*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Playlists*
   vfolder node parent: vfolder_layout*
  result: folder | 
create path for : vfolder*
  path for vfolder node : All Playlists*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Folders*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Video*
   vfolder node parent: vfolder_layout*
  result: folder | 
create path for : vfolder*
  path for vfolder node : Actor*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Album*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : All Video*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Folders*
   vfolder node parent: vfolder*
  result: folder | folder | 
create path for : vfolder*
  path for vfolder node : Genre*
   vfolder node parent: vfolder*
  result: folder | folder | 
fuppes: lib/ContentDirectory/VirtualContainerMgr.cpp:600: static void VirtualContainerMgr::insertFileForLayout(fuppes::DbObject*, std::string): Assertion `qry.size() == 1' failed.
Aborted
```

it looks like this Assertion `qry.size() == 1' failed. is the problem, but i havent seen that anywhere nor do i know what its talking about. does anyone else know? i tried changing the owner of the folder as it is a problem creating something but that wasnt it. has anyone seen this error before?

here is the code for my fuppes.cfg

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.8">
  <shared_objects>
    <dir>/home/nikolaus/Videos</dir>
  </shared_objects>

  <network>
    <!--empty = automatic detection-->
    <interface>wlan0</interface>
    <!--empty or 0 = random port-->
    <http_port></http_port>
    <allowed_ips>
      <ip>192.168.1.*</ip>
      <ip>225.225.225.0</ip>
      <ip>192.168.1.3</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>

    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
    <vfolders enabled="true">
        <vfolder name="default" enabled="false" />
        <vfolder name="xbox" enabled="true" />
        <vfolder name="vfolder" enabled="false"  />
    </vfolders>
  <device_mapping>
    <ip value="192.168.1.[4-7]" device="default" vfolder="none" />
    <ip value="192.168.1.3" device="xbox" vfolder="xbox" />
    <mac value="78:E4:00:7C:37:CC" device="xbox" vfolder="xbox"/>
  </device_mapping>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
    <vfolders enabled="false">
        <vfolder name="default" enabled="true" />
        <vfolder name="xbox" enabled="true" />
    </vfolders>
  <device_mapping>
    <ip value="192.168.1.[4-7]" device="default" vfolder="none" />
    <ip value="192.168.1.3" device="xbox" vfolder="xbox" />
    <mac value="78:E4:00:7C:37:CC" device="xbox" vfolder="xbox"/>
  </device_mapping>
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>

    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
</fuppes_config>

```and the code for xbox.cfg which fuppes is reading for vfolders

```
<?xml version="1.0" encoding="UTF-8"?>
<vfolder_layout version="0.2">
    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
                <items type="videoItem" />
            </vfolder>
      <vfolder name="Folders" id="21">
               <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>
</vfolder_layout>

```

---

### Post by bbrand on 2010-08-25
Just did this after buying a new TV, (Phillips 46PFL9704H
), set up fuppes on a 10.04 server box.

The config file in the first post DOES NOT WORK if you grab the latest from the source repository. After I followed the build instructions (worked perfectly) the cfg file mentioned on the first post did not work, this was deprecated.

I copied the fuppes.cfg that was built when deploying from /usr/etc/fuppes to HOME/.fuppes and tweaked that.

Btw, I left the interface section empty figuring it would default to the correct interface. Alas, with me it defaulted to the localhost which was useless, I added <interface>eth0<interface/> to fix that.

It works ... kind of, the video play is choppy. 

I had already tried ushare which streamed video flawlessly, but the connection to ushare would close after 30 mins, the TV being the culprit (Phillips support has not answered yet). 

I can now watch 30 mins of perfect video or a complete movie but then choppy. Are we having fun yet ....

Remarks/comments welcome.

---

### Post by 7venoh3 on 2010-08-25
@ bbrand could you put a copy of your vfolder up? im pretty sure the last half of mine where the xbox is containing the video folder setup is bad

---

### Post by Sload on 2010-08-30
[LEFT]Nevermind, was just being stupid.
[/LEFT]

---

### Post by mattlach on 2010-09-01
Can anyone comment on what kind of CPU is needed for real time transcoding?   Are fuppes and its dependencies multithreaded?

I ask because my server has a rather slow dual core Athlon 3250e.  It's 2x1.5Ghz.  Any thoughts on wheter or not this will be able to get the job done?

---

### Post by sjhupp on 2010-12-12
Could someone please share a working setup for the xbox 360? I can get it to see the files, but no virtual folders, so juts a huige ugly dir of files.
I don't understand if I need to use the default.cfg file (which I enabled), or the xbox.cfg (which looks almost empty in the one provided, and different to most I've seen people post).
Bit confused on the whole cfg file structure, and what cfg to put in each cfg file.
Any help appreciated please...

---

### Post by G_u_s on 2010-12-22
> **sjhupp said:**
> Could someone please share a working setup for the xbox 360? I can get it to see the files, but no virtual folders, so juts a huige ugly dir of files.
I don't understand if I need to use the default.cfg file (which I enabled), or the xbox.cfg (which looks almost empty in the one provided, and different to most I've seen people post).
Bit confused on the whole cfg file structure, and what cfg to put in each cfg file.
Any help appreciated please...

Anyone with an answer to this?

I have followed many guides, this one included, and I still only get a bunch of songs but no Album or Artist or Genre founds.

My Music folder structure is as follows:
```

Music
|-Artist 1
  |-Album 1
  |-Album 2

```

Here is my fuppes.cfg file:
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/XXX/Music</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>5080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--These are examples of what data you can put between the ip tags where (* => anything, [x-y] => range)-->
      <!--<ip>192.168.1.6</ip>-->
      <!--<ip>192.168.0.[20-100]</ip>-->
      <!--<ip>192.168.0.*</ip>-->
      <!--<ip>192.*.[0-2].[40-*]</ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
        <file ext="wpl">
          <type>PLAYLIST</type>
          <mime_type>application/vnd.ms-wpl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <!--This section is for the mime types that the makers of the XBox changed from standards.-->
      <file_settings>
	<file ext="mp3">
	  <type>AUDIO_ITEM_MUSIC_TRACK</type>
	</file>
        <file ext="jpg">
	  <type>IMAGE_ITEM_PHOTO</type>
	</file>
        <file ext="avi">
	  <type>VIDEO_ITEM</type>
	</file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>

```

And my vfolder.cfg file:
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

<vfolder_layout device="default" enabled="false">

   <vfolder name="Genre">
     <vfolders property="genre">
       <items type="audioItem" />
     </vfolders>
   </vfolder>

   <vfolder name="Genre/Artists">
     <vfolders property="genre">
       <vfolders property="artist">
         <items type="audioItem" />
       </vfolders>
     </vfolders>
   </vfolder>

   <vfolder name="Artists/Albums">
     <vfolders property="artist">
       <vfolders property="album">
         <items type="audioItem" />
       </vfolders>
     </vfolders>
   </vfolder>
   
   <vfolder name="ABC/Artists/Albums">
     <vfolders split="ABC">
       <vfolders property="artist">
         <vfolders property="album">
           <items type="audioItem" />
         </vfolders>
       </vfolders>
     </vfolders>
   </vfolder>
     
   <vfolder name="Photos">
     <vfolder name="All">
       <items type="imageItem" />
     </vfolder>
     <vfolder name="Folders">
       <folders filter="contains(imageItem)" />
     </vfolder>      
   </vfolder>

   <vfolder name="Videos">
     <vfolder name="All">
       <items type="videoItem" />
     </vfolder>
     <vfolder name="Folders">
       <folders filter="contains(videoItem)" />
     </vfolder>
   </vfolder>
   
   <vfolder name="shared dirs">
     <shared_dirs full_extend="true" />
   </vfolder>
   
 </vfolder_layout>

 <vfolder_layout device="Xbox 360" enabled="true" create_container_details="true">

   <vfolder name="Music" id="1">
     <vfolder name="Album" id="7">
       <vfolders property="album" type="container.album.musicAlbum">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
           
     <vfolder name="All Music" id="4">
       <items type="audioItem" />
     </vfolder>
     
     <vfolder name="Artist" id="6">
       <vfolders property="artist" type="container.person.musicArtist">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
     
     <vfolder name="Folders" id="20">
       <folders filter="contains(audioItem)" />
     </vfolder>
     
     <vfolder name="Genre" id="5">
       <vfolders property="genre" type="container.genre.musicGenre">
         <items type="audioItem" />
       </vfolders>
     </vfolder>
     
     <vfolder name="Playlist" id="15" />
   </vfolder>
 
   <vfolder name="Pictures" id="3">
     <vfolder name="Album" id="13" />
     
     <vfolder name="All Pictures" id="11">
       <items type="imageItem" />
     </vfolder>
     
     <vfolder name="Date Taken" id="12" />
     
     <vfolder name="Folders" id="22">
       <folders filter="contains(imageItem)" />
     </vfolder>
   </vfolder>

   <vfolder name="Playlists" id="18">
     <vfolder name="All Playlists" id="19" />
     <vfolder name="Folders" id="23" />
   </vfolder>

   <vfolder name="Video" id="2">
     <vfolder name="Actor" id="10" />
     <vfolder name="Album" id="14" />
     <vfolder name="All Video" id="8">
<items type="videoItem" />
</vfolder>
     <vfolder name="Folders" id="21" />
     <vfolder name="Genre" id="9" />
   </vfolder>
   <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

 </vfolder_layout>

</fuppes_vfolder_config>

```

And here is the output I had when compiling fuppes:
```

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : enabled  (Wand C-API)

  audio metadata extraction plugins
    taglib             : enabled  (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : enabled  (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  database plugins
    mysql              : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : enabled
    inotify            : enabled

  paths
    localstatedir:      ${prefix}/var/lib/fuppes

Thanks for using fuppes
please report bugs

```

I have gone through the routine of deleting the fuppes.db file, then starting fuppes again, hitting r, and then v, to no avail. I'm all out of ideas. Please help me =)

---

### Post by Legogris on 2011-08-08
I am trying to set up Fuppes 0.660 for streaming to my Xbox 360 on my Ubuntu 11.04 Server.
Install seems to run fine and the HTTP Server runs as expected. It's seen by my 360 (even though the name is "%s: %v", but that's irrelevant for now I guess) but Movies/Pictures/Music are empty.

When I run fuppes (shutting down fuppesd first, so I can get better output) and press r to rebuild my library, the following happens:
```

           FUPPES - 0.660
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.0.12:5080

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

r
[ContentDatabase] create database at Mon Aug  8 14:15:43 2011
read shared directories
*** buffer overflow detected ***: fuppes terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x50)[0xb7422df0]
/lib/i386-linux-gnu/libc.so.6(+0xe4cca)[0xb7421cca]
/lib/i386-linux-gnu/libc.so.6(+0xe43c8)[0xb74213c8]
/lib/i386-linux-gnu/libc.so.6(__overflow+0x4a)[0xb73a635a]
/lib/i386-linux-gnu/libc.so.6(_IO_vfprintf+0x2075)[0xb737c1d5]
/lib/i386-linux-gnu/libc.so.6(__vsprintf_chk+0xad)[0xb742147d]
/lib/i386-linux-gnu/libc.so.6(__sprintf_chk+0x2d)[0xb74213bd]
/usr/lib/fuppes/libmetadata_libavformat.so(fuppes_metadata_read+0x13c)[0xb7878b7c]
/usr/lib/libfuppes.so.0(_ZN15CMetadataPlugin8readDataEP10metadata_t+0x24)[0xb7621e04]
/usr/lib/libfuppes.so.0(_ZN12CFileDetails15GetVideoDetailsESsP10SVideoItem+0x23f)[0xb75ee03f]
/usr/lib/libfuppes.so.0(_Z15InsertVideoFileP16CContentDatabaseSs+0x80)[0xb75faa00]
/usr/lib/libfuppes.so.0(_Z10InsertFileP16CContentDatabasejSsb+0xaca)[0xb75fe2ca]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0xc15)[0xb75fff75]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0x9d5)[0xb75ffd35]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0x9d5)[0xb75ffd35]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0x9d5)[0xb75ffd35]
/usr/lib/libfuppes.so.0(_Z9DbScanDirP16CContentDatabaseSsx+0x9d5)[0xb75ffd35]
/usr/lib/libfuppes.so.0(_ZN13RebuildThread3runEv+0x95e)[0xb7600d3e]
/usr/lib/libfuppes.so.0(_ZN6fuppes6Thread10threadFuncEPv+0x28)[0xb761e3d8]
/lib/i386-linux-gnu/libpthread.so.0(+0x5e99)[0xb7864e99]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0xb740d73e]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 fb:00 5904243    /usr/bin/fuppes
0804b000-0804c000 r--p 00002000 fb:00 5904243    /usr/bin/fuppes
0804c000-0804d000 rw-p 00003000 fb:00 5904243    /usr/bin/fuppes
09926000-09d61000 rw-p 00000000 00:00 0          [heap]
ad9f2000-ad9f3000 ---p 00000000 00:00 0 
ad9f3000-ae1f3000 rw-p 00000000 00:00 0 
ae1f3000-ae1f4000 ---p 00000000 00:00 0 
ae1f4000-ae9f4000 rw-p 00000000 00:00 0 
ae9f4000-ae9f5000 ---p 00000000 00:00 0 
ae9f5000-af1f5000 rw-p 00000000 00:00 0 
af1f5000-af1f6000 ---p 00000000 00:00 0 
af1f6000-af9f6000 rw-p 00000000 00:00 0 
af9f6000-af9f7000 ---p 00000000 00:00 0 
af9f7000-b01f7000 rw-p 00000000 00:00 0 
b01f7000-b01f8000 ---p 00000000 00:00 0 
b01f8000-b09f8000 rw-p 00000000 00:00 0 
b09f8000-b09f9000 ---p 00000000 00:00 0 
b09f9000-b11f9000 rw-p 00000000 00:00 0 
b11f9000-b11fa000 ---p 00000000 00:00 0 
b11fa000-b19fa000 rw-p 00000000 00:00 0 
b19fa000-b19fb000 ---p 00000000 00:00 0 
b19fb000-b21fb000 rw-p 00000000 00:00 0 
b21fb000-b21fc000 ---p 00000000 00:00 0 
b21fc000-b29fc000 rw-p 00000000 00:00 0 
b29fc000-b29fd000 ---p 00000000 00:00 0 
b29fd000-b31fd000 rw-p 00000000 00:00 0 
b31fd000-b31fe000 ---p 00000000 00:00 0 
b31fe000-b39fe000 rw-p 00000000 00:00 0 
b39fe000-b39ff000 ---p 00000000 00:00 0 
b39ff000-b41ff000 rw-p 00000000 00:00 0 
b41ff000-b4200000 ---p 00000000 00:00 0 
b4200000-b4a00000 rw-p 00000000 00:00 0 
b4a00000-b4a21000 rw-p 00000000 00:00 0 
b4a21000-b4b00000 ---p 00000000 00:00 0 
b4b70000-b4b71000 ---p 00000000 00:00 0 
b4b71000-b5371000 rw-p 00000000 00:00 0 
b5371000-b5372000 ---p 00000000 00:00 0 
b5372000-b5b72000 rw-p 00000000 00:00 0 
b5b72000-b5b73000 ---p 00000000 00:00 0 
b5b73000-b6373000 rw-p 00000000 00:00 0 
b6373000-b63fa000 r-xp 00000000 fb:00 5903012    /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
b63fa000-b63fb000 ---p 00087000 fb:00 5903012    /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
b63fb000-b63fc000 r--p 00087000 fb:00 5903012    /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
b63fc000-b63fd000 rw-p 00088000 fb:00 5903012    /usr/lib/i386-linux-gnu/libsqlite3.so.0.8.6
b63fd000-b63fe000 rw-p 00000000 00:00 0 
b6406000-b640d000 r-xp 00000000 fb:00 5912735    /usr/lib/libvorbisfile.so.3.3.4
b640d000-b640e000 r--p 00006000 fb:00 5912735    /usr/lib/libvorbisfile.so.3.3.4
b640e000-b640f000 rw-p 00007000 fb:00 5912735    /usr/lib/libvorbisfile.so.3.3.4
b640f000-b6415000 r-xp 00000000 fb:00 6031127    /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
b6415000-b6416000 r--p 00005000 fb:00 6031127    /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
b6416000-b6417000 rw-p 00006000 fb:00 6031127    /usr/lib/fuppes/libdatabase_sqlite3.so.0.0.0
b6417000-b6418000 r-xp 00000000 fb:00 6034396    /usr/lib/fuppes/libdecoder_vorbis.so.0.0.0
b6418000-b6419000 r--p 00000000 fb:00 6034396    /usr/lib/fuppes/libdecoder_vorbis.so.0.0.0
b6419000-b641a000 rw-p 00001000 fb:00 6034396    /usr/lib/fuppes/libdecoder_vorbis.so.0.0.0
b641a000-b641b000 r-xp 00000000 fb:00 6034686    /usr/lib/fuppes/libencoder_pcm.so.0.0.0
b641b000-b641c000 r--p 00000000 fb:00 6034686    /usr/lib/fuppes/libencoder_pcm.so.0.0.0
b641c000-b641d000 rw-p 00001000 fb:00 6034686    /usr/lib/fuppes/libencoder_pcm.so.0.0.0
b641d000-b648d000 r-xp 00000000 fb:00 5910815    /usr/lib/liborc-0.4.so.0.11.0
b648d000-b648e000 r--p 0006f000 fb:00 5910815    /usr/lib/liborc-0.4.so.0.11.0
b648e000-b6491000 rw-p 00070000 fb:00 5910815    /usr/lib/liborc-0.4.so.0.11.0
b6491000-b6492000 rw-p 00000000 00:00 0 
b6492000-b651f000 r-xp 00000000 fb:00 5910831    /usr/lib/libvpx.so.0.9.6
b651f000-b6520000 ---p 0008d000 fb:00 5910831    /usr/lib/libvpx.so.0.9.6
b6520000-b6521000 r--p 0008d000 fb:00 5910831    /usr/lib/libvpx.so.0.9.6
b6521000-b6522000 rw-p 0008e000 fb:00 5910831    /usr/lib/libvpx.so.0.9.6
b6522000-b652c000 rw-p 00000000 00:00 0 
b652c000-b6551000 r-xp 00000000 fb:00 5908308    /usr/lib/libvorbis.so.0.4.5
b6551000-b6552000 r--p 00025000 fb:00 5908308    /usr/lib/libvorbis.so.0.4.5
b6552000-b6553000 rw-p 00026000 fb:00 5908308    /usr/lib/libvorbis.so.0.4.5
b6553000-b66b8000 r-xp 00000000 fb:00 5908311    /usr/lib/libvorbisenc.so.2.0.8
b66b8000-b66b9000 ---p 00165000 fb:00 5908311    /usr/lib/libvorbisenc.so.2.0.8
b66b9000-b66ca000 r--p 00165000 fb:00 5908311    /usr/lib/libvorbisenc.so.2.0.8
b66ca000-b66cb000 rw-p 00176000 fb:00 5908311    /usr/lib/libvorbisenc.so.2.0.8
b66cb000-b66e3000 r-xp 00000000 fb:00 5910824    /usr/lib/libtheoradec.so.1.1.4
b66e3000-b66e4000 r--p 00017000 fb:00 5910824    /usr/lib/libtheoradec.so.1.1.4
b66e4000-b66e5000 rw-p 00018000 fb:00 5910824    /usr/lib/libtheoradec.so.1.1.4
b66e5000-b6727000 r-xp 00000000 fb:00 5910825    /usr/lib/libtheoraenc.so.1.1.2
b6727000-b6728000 r--p 00041000 fb:00 5910825    /usr/lib/libtheoraenc.so.1.1.2
b6728000-b6729000 rw-p 00042000 fb:00 5910825    /usr/lib/libtheoraenc.so.1.1.2
b6729000-b6744000 r-xp 00000000 fb:00 6949528    /usr/lib/sse2/libspeex.so.1.5.0
b6744000-b6745000 r--p 0001a000 fb:00 6949528    /usr/lib/sse2/libspeex.so.1.5.0
b6745000-b6746000 rw-p 0001b000 fb:00 6949528    /usr/lib/sse2/libspeex.so.1.5.0
b6746000-b67e5000 r-xp 00000000 fb:00 5910819    /usr/lib/libschroedinger-1.0.so.0.10.0
b67e5000-b67e6000 r--p 0009f000 fb:00 5910819    /usr/lib/libschroedinger-1.0.so.0.10.0
b67e6000-b67e7000 rw-p 000a0000 fb:00 5910819    /usr/lib/libschroedinger-1.0.so.0.10.0Aborted

```


Configuration summary:

```

CONFIGURATION SUMMARY

  audio transcoding plugins
    encoder:
      lame       : yes
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : yes
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg             : disabled

  image conversion/rescaling plugins
    ImageMagick        : disabled (Wand C-API)

  audio metadata extraction plugins
    taglib             : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2      : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2              : disabled
    ImageMagick        : disabled (Wand C-API)
    simage             : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat        : enabled
    ffmpegthumbnailer  : disabled

  miscellaneous
    iconv              : enabled (charset conversion)
    uuid               : disabled
    inotify            : enabled

```

(./configure --enable-lame --enable-twolame --enable-mad --enable-faad)

Some codecs seem to be missing. I'm totally clueless on how to progress.

---

### Post by KillaB7 on 2011-09-16
First, since you're running 11.04, I would recommend using a newer revision from SVN. I compiled 0.686 in 11.04 tonight and it worked great. The only thing that didn't seem to work correctly was the ffmpegthumbnailer and likely transcoding (don't like to transcode on the fly anyway).
```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes fuppes 
```

Also, make sure you have all the prerequisites installed. The 10.04 instructions worked ok for me:
[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux#Ubuntu_Lucid_Lynx_.2810.04.29](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux#Ubuntu_Lucid_Lynx_.2810.04.29)

---

### Post by vivekk on 2011-09-17
> **KillaB7 said:**
> First, since you're running 11.04, I would recommend using a newer revision from SVN. I compiled 0.686 in 11.04 tonight and it worked great. The only thing that didn't seem to work correctly was the ffmpegthumbnailer and likely transcoding (don't like to transcode on the fly anyway).
```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes fuppes 
```

Also, make sure you have all the prerequisites installed. The 10.04 instructions worked ok for me:
[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux#Ubuntu_Lucid_Lynx_.2810.04.29](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux#Ubuntu_Lucid_Lynx_.2810.04.29)
I've managed to install 0.686 in 11.04 server & it works well. The only problem is the lack of any usable playlists.

When <playlist_style>file</playlist_style> is set in the devices/default.cfg file, playlists appear as .m3u/.pls files, but VLC is unable to play them. When using <playlist_style>container</playlist_style>, the playlist containers are empty.

Is there any way of creating usable playlists in vfolders? That is what I'd ideally like to do. The playlists themselves work fine with minidlna. It's just a shame it isn't particularly easy to create vfolders with minidlna without modifying source code. :(

Viv

---

