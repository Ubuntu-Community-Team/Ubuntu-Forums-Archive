---
title: "HOW TO  Install Fuppes on Ubuntu 8.10"
date: 2008-11-16
forum: Multimedia Software
---

### Post by PorchSong on 2008-11-16
********THIS WORKS ON JUANTY 9.04 AS WELL********

I got caught in a weird loop of not being able to install.  But, I finally got fuppes to install and work with no problems.  This is for an XBOX360 but will work on PS3 as well.  Do this: (I like to run these lines individually rather than all at once to watch what is going on--just cut and paste all code after and not including the "$").

First, open up a terminal "Applications->Accessories->Terminal" and clean your system of old programs fuppes uses:

```

$ sudo apt-get remove autoconf
$ sudo apt-get remove automake
$ sudo apt-get remove gettext

```

Open up a file browser and go to your /home/**your user name**/ directory and delete your /fuppes directory if you see it in there.  NOT the hidden .fuppes directory (use Ctrl+h to toggle hidden folders while in gnome to see) as this only contains your fuppes.cfg and vfolder.cfg files. (no need to nuke those).  

So, you are now "clean."

Now start over (again while in console).

```
$ sudo apt-get update
```

Install your codecs (cut and paste the whole thing rather than line by line): 

```
$ sudo apt-get install ffmpeg build-essential \
libavutil-dev libavformat-dev libavcodec-dev \
subversion libtool automake autoconf \
libsqlite3-dev libpcre3-dev libxml2-dev
```

Reinstall your conf programs:

```

$ sudo apt-get install autoconf
$ sudo apt-get install automake
$ sudo apt-get install gettext

```

Now get the latest release of fuppes v646 (Again, I run these one line at a time)

For some reason, I HAD to "--enable-video-transcoding" for this to work, even though I DISABLE TRANSCODING in my fuppes.cfg file.  So, I am NOT transcoding at all.

```
$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ ldconfig
```

This should do it.  

The tricky part is getting a proper fuppes.cfg file in order.  You can find a fuppes.cfg in the forums, but I modified mine so that I am NOT transcoding vids to my Xbox 360--again, no need to.

Here is my fuppes.cfg file.  You will have to change to direct to your personal folders up top, and in network section set up to your ip addy and port.  Just cut and paste my whole file over your whole file (after making a backup copy of yours in case it does not work), make changes in folder area and network area, and save it.  Also, place this in your home/**your user name**/.fuppes directory (the hidden one again, Ctrl+h to toggle hidden folders). You will need admin rights to do this.

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
      <!--<ip>192.168.0.1</ip>-->
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

$ sudo fuppes
```

Once you have it running, type "r" (no quotes) and wait as your directories get built. After you get back to prompt, hit "v" to rebuild your virtual directories.

And you know all is well if you can go to your browser and type in your computer's ip addy and get the fuppes config screen.  With my fuppes.cfg this would be:

```
http://192.168.0.10:9137
```

This does work on 8.10, 9.04, and earlier.  I just got it all working.  Furthermore, I am running the AMD64 version.

******PEOPLE ARE HAVING ISSUES WITH THE XBOX SEEING FUPPES, BUT HAVING NO VIDEO FILES OR DIRECTORY STRUCTURE.  This is an issue with the fuppes.db (database).  If your Xbox sees fuppes server, then it WILL see your vids.  First, make sure you do "sudo fuppes" in terminal.  Second, after fuppes loads up, type 'r' to rebuild your database.  AFTER it completes, type 'v' to rebuild your folder structure.  This WILL work, though it might take a few attempts.  If still having problems, then goto your /.fuppes and delete your fuppes.db file (you will need admin rights to do so), wash and repeat (load fuppes, 'r', then 'v'.  Hang in there, it WILL work.******

Lastly, if you are having install/upgrade issues with latest fuppes version v636 or newer, AND you followed the guide for "Installing the latest FFMPEG & V264 guide," 

[http://ubuntuforums.org/showthread.php?t=786095&highlight=fuppes]("http://ubuntuforums.org/showthread.php?t=786095&highlight=fuppes")

there is a solution.  You first have to go back the "FFMPEG guide" and uninstall/purge the install and delete the directories as directed.  AFTER this, follow this guide again to get fuppes installed and running, THEN you can go back to the FFMPEG Guide and reinstall.  Apparently, fuppes install and the latest ffmpeg codecs don't play well.

PM me if you have any additional questions.

---

### Post by mr_skater99 on 2008-12-29
Hi,

Followed your guide to the letter.  Fuppes is installed and the web interface is up - it went through and built all the directories.  But my xbox doesn't see anything at all.

Any suggestions?  Turned my firewall off.  not to sure what else to try.

Using 8.10 AMD64 (same as you).

Cheers.

---

### Post by PorchSong on 2008-12-29
> **mr_skater99 said:**
> Hi,

Followed your guide to the letter.  Fuppes is installed and the web interface is up - it went through and built all the directories.  But my xbox doesn't see anything at all.

Any suggestions?  Turned my firewall off.  not to sure what else to try.

Using 8.10 AMD64 (same as you).

Cheers.

Xbox doesn't see fuppes, or Xbox doesn't see the directories within fuppes once you click on it?

PM me and I can walk you through it.  Make sure you have your Xbox on a static addy and that you have that addy in your fuppes.cfg file.  If your Xbox is not seeing the folders, but is seeing fuppes under video, then redo your "r" and "v" commands in fuppes terminal.

This is an easy fix, but I need to know exactly what is not being seen.

---

### Post by mr_skater99 on 2008-12-29
Thanks for the quick reply!

My xbox is not seeing fupes at all.

On the fupes end I get a few entries for my router with different uuid's and an entry for vuze upnp media server.

I have my xbox set to a static ip and have it in my fupes config file.

Cheers.

---

### Post by il-luzhin on 2009-01-03
I'm in a similar boat to mr_skater99.  

I've got the fuppe dir on my 360, but all the folders are empty.  When I rebuilt the collection on fuppe I saw the files being processed so I believe fuppe sees them.  Yet still, all the folders are empty on the xbox.

UPDATE: Oh! So close...  So my Video folder is A OK, almost.  All my audio folders are listed under video for some reason but I can't do anything with them.  All my Videos are just fine (thnx PorchSong!).  Under Music it says I have no artists, no albums, no playlists, but under songs it seems to have almost everything.  This has got to be a vfolder.cfg issue.  ANy help is much appreciated

---

### Post by il-luzhin on 2009-01-04
Well I installed this patch

[http://sourceforge.net/tracker2/?func=detail&aid=2212188&group_id=141999&atid=751215](http://sourceforge.net/tracker2/?func=detail&aid=2212188&group_id=141999&atid=751215)

But all it managed to do was break my Video Folder.  Now it's no video, no music hierarchy

---

### Post by PorchSong on 2009-01-15
> **mr_skater99 said:**
> Thanks for the quick reply!

My xbox is not seeing fupes at all.

On the fupes end I get a few entries for my router with different uuid's and an entry for vuze upnp media server.

I have my xbox set to a static ip and have it in my fupes config file.

Cheers.

Make sure your have the right tags on your ip within fuppes.cfg.  Post your fuppes.cfg and I'll look it over.

Also, check your port setting in your fuppes.cfg and make sure your router is port forwarding to your computers static ip.  In my .cfg I have it set to port 9137 and in my router, I have 9137 forwarded to 192.168.0.10 (my linux box).

---

### Post by Skooj on 2009-01-15
I pasted this in the earlier thread as well. It's not completely relevant here either since I am running 7.10 and not 8.10, but might still be of use to someone and this thread is newer. here's a paste:

I am currently running the most up-to-date version of fuppes (rev 627) from the subversion repository on ubuntu 7.10. I started with 576 or something like that and removed it to try the most up to date. I have not been able to get my 360 to see the fuppes server. I have used the cfg file from the wiki, the cfg file posted in the OP, and also tried the fix from this post: [http://ubuntuforums.org/showthread.php?p=3888138](http://ubuntuforums.org/showthread.php?p=3888138) but all to no avail on either version.

when I start up fuppes, I see this:
```
            FUPPES - 0.UNKNOWN
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/Plugins/Plugin.cpp (139) :: Wed Jan 14 10:17:17 2009 ==
registered transcoder plugin "ffmpeg"

== lib/Plugins/Plugin.cpp (110) :: Wed Jan 14 10:17:17 2009 ==
registered dlna profile plugin

== lib/Plugins/Plugin.cpp (117) :: Wed Jan 14 10:17:17 2009 ==
registered metadata plugin "libavformat"

== lib/Plugins/Plugin.cpp (124) :: Wed Jan 14 10:17:17 2009 ==
registered audio decoder plugin "vorbis"

== lib/Plugins/Plugin.cpp (117) :: Wed Jan 14 10:17:17 2009 ==
registered metadata plugin "taglib"

<insert watch listing crap>

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (346) :: Wed Jan 14 10:17:50 2009 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
```

so it obviously sees my 360, but my 360 will not find it in the system settings or anywhere. 

here's my fuppes.cfg:
```
<?xml version="1.0" encoding="UTF-8"?>

<fuppes_config version="0.7.2.3">

 <shared_objects>

   <dir>/home/leech/downloads</dir>

 </shared_objects>



<network>

   <!--empty = automatic detection-->

   <interface>eth0</interface>

   <!--empty or 0 = random port-->

   <http_port>9137</http_port>

   <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->

   <allowed_ips>

     <!--<ip>192.168.0.1</ip>-->

     <ip>192.168.1.8</ip>
     <ip>192.168.1.4</ip>
     <ip>192.168.1.7</ip>

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

and my vfolder.cfg:
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

I have no idea what's going wrong or where, but nothing wants to work.

thanks in advance.

---

### Post by il-luzhin on 2009-01-19
Thnx PorchSong

```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/"Media and BU"/Music</dir>
    <dir>/media/"Media and BU"/Videos</dir>
    <dir>/home/luzhin/Music</dir>
    <dir>/home/luzhin/Videos</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth25</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.1.1</ip>-->
      <ip>192.168.1.45</ip>
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

---

### Post by adobrakic on 2009-01-19
my xbox detects the fuppes folder, but it detects my music only under Videos on the xbox, and not under Music.
Is there a way to fix this?

---

### Post by wolf4914 on 2009-01-25
I am trying to compile it on jaunty 64 bit and get this error :

autoreconf -vfi
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 186.
Use of uninitialized value $libtoolize in pattern match (m//) at /usr/bin/autoreconf line 186.
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
configure.in:10: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:12: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1

---

### Post by wolf4914 on 2009-01-25
I figured out the error and compiled ok. Now I have it messed up within folders. There are videos Pics and Music showing as shared folders in my video section but only videos will play. The pics will not show up in Pictures folder of Xbox360 at all and Musix folder is just one long list of songs - no Folders albums genres etc. I believe somebody posted on the same behavior so I tend to think it is a bug. Compiled on Jaunty Alpha 3 64 bit v 0.638

---

### Post by Skooj on 2009-01-26
figured out my problem. I'm running a wds wireless network and forgot to put my routers on my allow list. moving over to a wired connection made this clear to me.

after getting it to show up, I am having the same problem as wolf4914. While my video and pictures and everything sorts fine, the music is just one huge list of songs. I have all of the dev taglib (libtag in the apt repos) builds, andalso have the create_references="true" tag in my vfolder.cfg.

not sure what's going on here.

thanks in advance for any help!

---

### Post by AfterShock6783 on 2009-01-28
I seem to be just unable to install at this point - wondering if anyone had any pointers on what I may be missing.
First - my system (in case it makes a difference) is:
    * GOAL3+ 754 SiS 761 GX Micro ATX Motherboard
    * AMD Sempron 1.6GHZ 64 Bit
    * New system - Ubuntu 8.10 AMD_64 (2.6.27-11-server) just did my update/upgrade/dist-upgrade today

I followed each step in the 1st post and I'm erroring out during
```
./configure --enable-video-transcoding
```
here's the ending bit that's making me go crazy:
```
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking whether byte ordering is bigendian... no
./configure: line 15948: PKG_PROG_PKG_CONFIG: command not found
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
./configure: line 16974: syntax error near unexpected token `PCRE,'
./configure: line 16974: `PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'
```
any help would be greatly appreciated :D
------------
EDIT:
just as an update I found I'm apparently missing pcre...
Thank you both for the advice!

I reinstalled pkjg-configit after I saw the error, thinking it wasnt there.
ran pkg-config --version. returned 0.22
ran pkg-configure --cflags libpcre. returned a blank line. I can only assume I don't have the library - which is crazy since one of the instructions is to install libpcre3-dev and when I tried it just now it told me it's already installed....


so I went and got it manually. now I'm still getting the same issue, but when I do pkg-configure --cflags libpcre I get
Code:

```
pkg-config --cflags pcre
Package pcre was not found in the pkg-config search path.
Perhaps you should add the directory containing `pcre.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pcre' found
```

as opposed to a blank line. looking into it now, but we'll see how that goes. any tips?
------------
I can't believe this...  I'm such a moron.
I forgot to run  autoreconf -vfi
sorry for wasting everyone's time, but thank you for all help
such a noob move

---

### Post by Nodds on 2009-02-06
how do I give myself admin rights to paste into the hidden fuppes folder?

---

### Post by tgilbert328 on 2009-02-08
Hi All,  

I am running kubuntu 8.10 and had some trouble with the this.  During the configure stage, I received an error:

`PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'

I found a solution on another page here:

[HTML]http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux[/HTML]

near the botton they reveal another package you need to have:

```
sudo apt-get install pkg-config
```

Which solved the configure problem.

Tim

---

### Post by kevthepongo on 2009-02-08
Hi
I'm having the same problem as Nodds a couple of posts earlier.....
I'm at the stage where I need to change the config file but for some reason when I try and access the /.fuppes folder I receive a permission denied message and i do not have necessary rights.  I am an administrator - in fact I'm the only user. everything else seems to have worked up to this point.  Any assistance would be greatly appreciated.  Many thanks

---

### Post by kevthepongo on 2009-02-10
> **Nodds said:**
> how do I give myself admin rights to paste into the hidden fuppes folder?

Nodds, a mate of mine came back to me and told me how to solve the snag about ownership of the .fuppes file so that you can edit the cfg file.  
He wrote:
What's probably happened is that the .fuppes folder in your home directory belongs to root and not 'your user'.

the way to check is open a terminal and enter:

ls -al /home/yourusername | grep fuppes

if it looks like this:

drwxr-xr-x  2 root root      4096 2009-01-18 23:57 .fuppes

or similar then the ownership is wrong.

type:

sudo chown -R yourusername:yourusername /home/yourusername/.fuppes

enter you password and you should now 'own' that folder and the files inside it.

It worked

---

### Post by cberger on 2009-02-11
PorchSong,

Great thread!  Thanks!

I've been pulling my hair out for the past week trying to get XBOX to see any video files using FUPPES.  It sees FUPPES and can open music and images.  In fact, prior to loading pictures, it would still open and show the vfolders.  However, when selecting FUPPES under videos, I immediately get 'No videos found'.  Even if it couldn't find files it recognized, I'd assume I'd at least get presented the vfolders which of course it's not.

Most of my files are *.vob's.  However, in troubleshooting I've posted sample AVI and WMV files downloaded directly from MS's website.  Still no luck.  Seems like a vfolder.cfg issue, but using the one you've posted.  I also used your fuppes.cfg file (obviously changing for my environment).  Again, music and images are fine.

Any thoughts you may have would be greatly appreciated.

---

### Post by Nodds on 2009-02-11
cool, 

that seems to do the trick. I'm now stumped by streaming M3U files, it appears that Fuppes does not support this for the Xbox.

Bah....

> **kevthepongo said:**
> Nodds, a mate of mine came back to me and told me how to solve the snag about ownership of the .fuppes file so that you can edit the cfg file.  
He wrote:
What's probably happened is that the .fuppes folder in your home directory belongs to root and not 'your user'.

the way to check is open a terminal and enter:

ls -al /home/yourusername | grep fuppes

if it looks like this:

drwxr-xr-x  2 root root      4096 2009-01-18 23:57 .fuppes

or similar then the ownership is wrong.

type:

sudo chown -R yourusername:yourusername /home/yourusername/.fuppes

enter you password and you should now 'own' that folder and the files inside it.

It worked

---

### Post by suricx on 2009-02-15
First off great guide it worked great for my ps3.  My xbox 360 sees fuppes and fuppes see's my xbox but no folders or files show up on xbox 360.

This is my .cfg file if anyone has any ideas please let me know.


```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/disk/</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.3</interface>
    <!--empty or 0 = random port-->
    <http_port>9000</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.1.2</ip>
      <ip>192.168.1.3</ip>
      <ip>192.168.1.4</ip>
      <ip>192.168.1.5</ip>
      <ip>192.168.1.6</ip>
      <ip>192.168.1.7</ip>
      <ip>192.168.1.8</ip>
      <ip>192.168.1.9</ip>
      <ip>192.168.1.10</ip>
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
    
  </device_settings>
</fuppes_config>
```

---

### Post by PorchSong on 2009-02-17
I occasionally get same error.  Just go to console, fire up fuppes via "sudo fuppes" and then once loaded, do "u" then "v" to update database and rebuild virtual folders. Sometimes you have to do this multiple times "u" "v" "u".

---

### Post by Zikona on 2009-02-18
I am attempting to install Fuppes on 8.10 and getting following errors below after running 'make'. Any ideas?

[COLOR="RoyalBlue"]libtool: compile:  g++ -DHAVE_CONFIG_H -I. -DOLD_DB -I/usr/include/libxml2 -DFUPPES_DATADIR=\"/usr/local/share/fuppes\" -DFUPPES_PLUGINDIR=\"/usr/local/lib/fuppes\" -g -O2 -MT ControlInterface.lo -MD -MP -MF .deps/ControlInterface.Tpo -c lib/ControlInterface/ControlInterface.cpp  -fPIC -DPIC -o .libs/ControlInterface.o
mv -f .deps/ControlInterface.Tpo .deps/ControlInterface.Plo
make[2]: *** No rule to make target `lib/ControlInterface/SoapControl.cpp', needed by `SoapControl.lo'.  Stop.
make[2]: Leaving directory `/home/bobo/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bobo/fuppes/src'
make: *** [all-recursive] Error 1[/COLOR]

---

### Post by s3lekta on 2009-02-22
Well it's my first post... Hello all?

I'm just running into some minor problems you guys could probably decipher in a second, so here goes...

I am able to see my 360 and the 360 can see only my audio files but NOT the video files, they are all avi files btw

Here's a copy of my cfg's

[ATTACH]104218[/ATTACH]

[ATTACH]104219[/ATTACH]

Thanks guys

---

### Post by s3lekta on 2009-02-22
> **s3lekta said:**
> Well it's my first post... Hello all?

I'm just running into some minor problems you guys could probably decipher in a second, so here goes...

I am able to see my 360 and the 360 can see only my audio files but NOT the video files, they are all avi files btw

Here's a copy of my cfg's

[ATTACH]104218[/ATTACH]

[ATTACH]104219[/ATTACH]

Thanks guys

no worries guys, i'm using ushare instead ... works fine!

---

### Post by Coinneach on 2009-02-22
> **s3lekta said:**
> no worries guys, i'm using ushare instead ... works fine!

I used your files and I can now see/play my audio files but can't see my videos

---

### Post by megacrypto on 2009-03-01
i followed the guide on the first page, but i cant see my video files, i can only see the jpg's in the video folders... what am i missing

---

### Post by Kain000 on 2009-03-08
hey everyone, I  am having the same problem that most people here seem to have and that is that my xbox 360 connects but there is no media in any of the folders (music videos and pictures)   

I followed this guide and the one linked to, and it would seem I need to use the vfile.ctf file to correct this but I cannot find the vfile at all.

where is it???  or do I need to create it?  if so do i just put it in the .fuppes folder?

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Microsoft_Xbox_360")

---

### Post by LuvinLinux on 2009-03-09
Well, I seem to be having the same problem as many on here in that my 360 can see the fuppes server and fuppes sees my files but my 360 doesn't see any files.

I have been able to get fuppes 0.629 running perfectly on my laptop but when I got around to installing it on my desktop it had been updated to version 0.634.  This install is the one in which my 360 can't see any files.

It seems to me as though something must have changed between these two versions as the vfolder.cfg and fuppes.cfg files that work on my laptop do not work on my desktop (I obviously changed the network info though).  The only other thing I can think of is that perhaps a package installed on the laptop is not on the desktop or is a different version.  Will be trying to re-install on the desktop later tonight to see if there is a new version out now which might work.

In the meantime though, if anyone knows of a way that I can download and install 0.629 that would be great.

Thanks.

---

### Post by TESFox on 2009-03-18
Confirmed, OP should add this to the guide.  I was getting the same error on Xubuntu, installing pkg-config fixed it.

> **tgilbert328 said:**
> Hi All,  

I am running kubuntu 8.10 and had some trouble with the this.  During the configure stage, I received an error:

`PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'

I found a solution on another page here:

[HTML]http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux[/HTML]

near the botton they reveal another package you need to have:

```
sudo apt-get install pkg-config
```

Which solved the configure problem.

Tim

---

### Post by LuvinLinux on 2009-03-18
Well, after copying the earlier version to the desktop and recompiling, the 360 now sees all my files.  I don't know if this means that something has changed but it seems like there must be something as I did everything exactly the same when installing.
     The only problem I'm having is that my music is not being sorted properly.  Everything seems to show up but only in the Songs section (ie. Artists, Albums, Genres are all empty).  I thought maybe there might be a package installed on the one machine that is not present on the other which allows Fuppes to read ID3 tags, but it seems like they have the same ones installed.
     Any advice would be greatly appreciated.

Thanks.:)

---

### Post by bruceleeroy on 2009-03-25
I have a PS3 and I was using MediaTomb but it kept losing my directory's which in turn caused me to lose my mind a little.

I keep trying to install Fuppes but from the get go I get this output
after I type [COLOR="Red"]sudo apt-get remove autoconf.[/COLOR]
```

chris@otacon:~$ sudo apt-get remove autoconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autoconf is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fuppes: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
          Depends: libavformat1d (>= 0.cvs20070307) but it is not installable
          Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
          Depends: libmagick++10 but it is not going to be installed
          Depends: libsimage20 but it is not going to be installed
          Depends: libswscale1d (>= 0.cvs20070307) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I don't know what any of that means what am I doing wrong?

---

### Post by bruceleeroy on 2009-03-25
I tried writing apt-get f install but that doesn't seem to help either.

---

### Post by bruceleeroy on 2009-03-25
Sorry to belabor this but any have any ideas?

---

### Post by keenish27 on 2009-03-26
Ok...it doesn't matter what I do I can't get my xbox to even see fuppes...

my fuppes sees the xbox...
also I keep gettin this message "no vfolder.cfg file available"  but it lies.  There is a vfolder.cfg in both the .fuppes and fuppes directories.....

here is my config

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/shared/Downloads/Movies</dir>
   </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>35911</http_port>
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

any help is appreciated.

---

### Post by PorchSong on 2009-04-01
In your fuppes.cfg you removed your ip adddresses.  This is supposed to allow all ip's, but I do not think this works properly.  Set your pc as static AS WELL AS your xbox360 then input both adresses into your fuppes.cfg.  Look at page one under my guide and you will see the two addresses I have listed are my xbox360 and my main pc.

---

### Post by PorchSong on 2009-04-01
BTW fuppes is now v634.

---

### Post by keenish27 on 2009-04-06
> **PorchSong said:**
> In your fuppes.cfg you removed your ip adddresses.  This is supposed to allow all ip's, but I do not think this works properly.  Set your pc as static AS WELL AS your xbox360 then input both adresses into your fuppes.cfg.  Look at page one under my guide and you will see the two addresses I have listed are my xbox360 and my main pc.

I added the ips but no deal.  Though I did notice that .fuppes is owned by root.  Should it have a different owner or group?

---

### Post by keenish27 on 2009-04-06
> **keenish27 said:**
> I added the ips but no deal.  Though I did notice that .fuppes is owned by root.  Should it have a different owner or group?

That was exactly the problem.  I just made myself the owner and group for .fuppes and all the files in it and it worked fine.

---

### Post by larrinh on 2009-04-11
I ran though the example and everything went fine. No errors. However; when I was done there is no .fuppes folder and therefore no fuppes.cfg file. I am running Jaunty 9.04 AMD64 build. Any ideas?

Larrin

---

### Post by madhi19 on 2009-04-12
The ps3 firmware update 2.70 messed up fuppes but their a fix. You need to edit the config file. The most up to date info on fuppes I could find is on this forum and on the wiki. 
[http://fuppes.ulrich-voelkel.de/forum/](http://fuppes.ulrich-voelkel.de/forum/)
You will also do well to visit the wiki since the ps3 demand a few more line of editing to work fine

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Sony_Playstation_3](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Sony_Playstation_3)

This is really an app that need to be on synaptic because it a pain to install and maintain. But it sure is the most interesting upnp media server for linux.

---

### Post by snipe6006 on 2009-04-22
I had no problem installing Fuppes on my computer. I ran fuppes using the sudo fuppes and then went to the address and port on my computer. On the site the page is blank not an error. How do I access it on the web?

---

### Post by linuxvacuum on 2009-05-12
This weird, it's not working. It keeps repeating this error
```
**Invalid and inefficient vfw-avi packed B frames detected**
```

```
fuppes
            FUPPES - 0.636
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

== lib/Plugins/Plugin.cpp (131) :: Tue May 12 21:52:20 2009 ==
registered presentation plugin

== lib/Plugins/Plugin.cpp (167) :: Tue May 12 21:52:20 2009 ==
registered database plugin "sqlite3"

== lib/Plugins/Plugin.cpp (145) :: Tue May 12 21:52:20 2009 ==
registered audio decoder plugin "FLAC"

== lib/Plugins/Plugin.cpp (145) :: Tue May 12 21:52:20 2009 ==
registered audio decoder plugin "musepack"

== lib/Plugins/Plugin.cpp (145) :: Tue May 12 21:52:20 2009 ==
registered audio decoder plugin "vorbis"

== lib/Plugins/Plugin.cpp (124) :: Tue May 12 21:52:20 2009 ==
registered dlna profile plugin

== lib/Plugins/Plugin.cpp (138) :: Tue May 12 21:52:20 2009 ==
registered metadata plugin "libavformat"

== lib/Plugins/Plugin.cpp (138) :: Tue May 12 21:52:20 2009 ==
registered metadata plugin "mp4v2"

== lib/Plugins/Plugin.cpp (138) :: Tue May 12 21:52:20 2009 ==
registered metadata plugin "magickWand"

== lib/Plugins/Plugin.cpp (138) :: Tue May 12 21:52:20 2009 ==
registered metadata plugin "taglib"

== lib/Plugins/Plugin.cpp (160) :: Tue May 12 21:52:20 2009 ==
registered transcoder plugin "ffmpeg"

== lib/Plugins/Plugin.cpp (160) :: Tue May 12 21:52:20 2009 ==
registered transcoder plugin "magickWand"

webinterface: [http://192.168.15.4:8080](http://192.168.15.4:8080)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (348) :: Tue May 12 21:52:21 2009 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
r
[ContentDatabase] create database at Tue May 12 21:52:29 2009
read shared directories
[NULL @ 0x103c450]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 1 times
[NULL @ 0x1053020]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0xfda3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x1053020]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x1054f50]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x1053020]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 1 times
[NULL @ 0x106e8e0]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 1 times
[NULL @ 0x104cab0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x106d3a0]frame skip 8
[NULL @ 0x106d3a0]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 2 times
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 1 times
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106edf0]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x106d3a0]Invalid and inefficient vfw-avi packed B frames detected
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Tue May 12 21:52:39 2009
u
[ContentDatabase] create database at Tue May 12 21:52:43 2009
remove missing
[DONE] remove missing
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Tue May 12 21:52:43 2009
v
[VirtualContainer] create virtual container layout started at Tue May 12 21:52:44 2009
[VirtualContainer] virtual container layout created at Tue May 12 21:52:47 2009
```

---

### Post by linuxvacuum on 2009-05-12
Wow it works even with these errors. Looks like the Xbox 360 REQUIRES you to be signed in to Xbox live to access a local computer.
I don't see how that makes sense, but right after login in Xbox Live I could see my fuppes computer with all my files :)

---

### Post by wbzial on 2009-05-15
> **linuxvacuum said:**
> Wow it works even with these errors. Looks like the Xbox 360 REQUIRES you to be signed in to Xbox live to access a local computer.

Are you sure of the need to be logged in live to access your media.?

> **snipe6006 said:**
>  On the site the page is blank not an error. How do I access it on the web?


In your fuppes.cfg you change your network config... default 127.0.0.1: ????

---

### Post by Unislash on 2009-06-08
This guide rocks. I'm lucky enough to have found it before i spent hours trying to get this working. All together, i spent about 50 minutes (!) working on this--waaay less than i did in windows--and it's working thanks to this guide.

I should mention that i did run into the whole "Can't see any videos" problem. I fixed it by using the vfolder.cfg file provided in the tutorial; apparently i did something wrong and didn't end up using it until i recopied it. So, if you're having this problem... consider recopying it--just to make sure :)

Cheers,
Unislash

---

### Post by KB1LQC on 2009-06-12
I've tried the first post as well as the guide from the [FUPPES Website]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux") to no avail.  I can successfully configure (but not all is enabled...) and get this summary:
```
SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : disabled (mp4/m4a)

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

Thanks for using fuppes
please report bugs

```

after 

```

Make
sudo make install (because it would error if not sudo)

```
it seems to complete without errors but there is no /.fuppes folder to be found anywhere near my /home/bryce folder.  Anyone have any ideas?




Bryce

---

### Post by X4320 on 2009-06-16
i followed the guide and also paste the configs.
edited the part of shared folders and the allowed ips. yet i dont get this:

> 
~$ sudo fuppes
            FUPPES - 0.636
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

== lib/Plugins/Plugin.cpp (160) :: Tue Jun 16 21:14:03 2009 ==
registered transcoder plugin "ffmpeg"

== lib/Plugins/Plugin.cpp (167) :: Tue Jun 16 21:14:03 2009 ==
registered database plugin "sqlite3"

== lib/Plugins/Plugin.cpp (131) :: Tue Jun 16 21:14:03 2009 ==
registered presentation plugin

== lib/Plugins/Plugin.cpp (145) :: Tue Jun 16 21:14:03 2009 ==
registered audio decoder plugin "vorbis"

== lib/Plugins/Plugin.cpp (124) :: Tue Jun 16 21:14:03 2009 ==
registered dlna profile plugin

== lib/Plugins/Plugin.cpp (138) :: Tue Jun 16 21:14:03 2009 ==
registered metadata plugin "libavformat"

[ERROR] failed to bind socket to : 62.157.140.133:0
[exiting]


whats up with the 62.157.140.133:0 ???
sometimes its switching between that ip and the 80.156.86.78:0


any ideas ????

---

### Post by PorchSong on 2009-06-16
@KB1LQC

If you are new to Linux, then open up Nautilus point it to your home directory, then hit 'Ctrl-h' to show hidden folders.  Your .fuppes folder should show up now.  If you already know how to show hidden folders (Ctrl-h) and you are not seeing your .fuppes folder, then you have other issues.  Let me know and I will do what I can to help.

---

### Post by PorchSong on 2009-06-16
> **X4320 said:**
> i followed the guide and also paste the configs.
edited the part of shared folders and the allowed ips. yet i dont get this:



whats up with the 62.157.140.133:0 ???
sometimes its switching between that ip and the 80.156.86.78:0


any ideas ????

Goto you fuppes.cfg file and look at the address and port you listed as your ip.  In my fuppes.cfg, I have my computer behind my router thus my addy is 192.168.0.10:9137 -- with the 9137 being the port I assigned fuppes (btw this is section of fuppes.cfg is where you are assigning the port).

Without seeing that section, I am assuming you DO NOT have a static ip addy and it is changing with each modem reboot/powerup AND you are NOT behind a router.  If you are behind a router, then assign yourself an ip (ex. 192.168.0.10 for my setup) and also a port (9137 for me).  Then add that ip to your fuppes.cfg.  I also see that your port keeps coming up as '0' and you should be assigning yourself a static port.

Post your fuppes.cfg file from your .fuppes directory so I can take a peak.

---

### Post by X4320 on 2009-06-17
as said i just changed the share folder and my ips :/
i HAVE satic ip, i have port forwarding , i am BEHIND a router.


here my .cfg


```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/Test/foobar</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>8080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.200.1</ip>-->
      <ip>192.168.200.62</ip>
      <ip>192.168.200.63</ip>
      <ip>192.168.200.64</ip>
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


just as example if i doesnt: DHCP active for a specific ip range and those 2 which are switching from time to time are NOT inside the ip-pool.

---

### Post by PorchSong on 2009-06-17
> **X4320 said:**
> as said i just changed the share folder and my ips :/
i HAVE satic ip, i have port forwarding , i am BEHIND a router.


here my .cfg


```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/Test/foobar</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>8080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.200.1</ip>-->
      <ip>192.168.200.62</ip>
      <ip>192.168.200.63</ip>
      <ip>192.168.200.64</ip>
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


just as example if i doesnt: DHCP active for a specific ip range and those 2 which are switching from time to time are NOT inside the ip-pool.

Config file looks solid.  Going to throw some darts here:  Check your eth0 setup in ubuntu and make sure the ip addy is 192.168.200.1 and not somehow reset to automatically assigned.  Fuppes should be showing 192.168.200.1:8080 as your connected ip.  Why it is pulling from other ip addresses is a mystery.

Hope this helps.

---

### Post by X4320 on 2009-06-18
checked, the connection is fix and ports are forwarded.
checked also router logs if it did something by itself. nothing...:(
thanks anyway for your help and time

---

### Post by Mordlikeafox on 2009-06-28
well, first post here .. I'm having a balls of a time trying to get fuppes 0.636 to work

earlier in the night I could see mp3s i placed in the shared folder, but not jpegs or avis.. the mp3s played fine so I held out some hope for being able to solve this. But then something happened (absolutely no idea what, I changed nothing at the time) and then/now the 360 won't even connect to fuppes. If I open up my video/music/picture library on the dashboard it will say 'harddrive/currentdisc/portable/computer' and then if I start fuppes 'fuppes 0.636:1' appears so the xbox is clearly seeing something. I can't connect though, when I click on the fuppes link in any one of the dashboard libraries i get the 'connecting' screen for a few seconds and then  

"Can't connect to the PC. A firewall may be blocking the connection" and it asks me if i want to test my connection, which always fails.  Now the connection must be there, because it recognises instantly when I turn fuppes on, and xbox live works perfectly (although I do use firestarter for port forwarding for xbox live to get around the moderate nat issue).


My ubuntu machine is connected to the router through wifi and the xbox is connected to my machine using a lan cable. I use firestarter to share the internet connection with the xbox so I can get on xbox live, but i don't need to use it for fuppes, right? because the router isn't involved at all.  

the lan cable is at eth0, which has a static ip of 192.168.0.1 and the xbox has a static ip of 192.168.0.2 , the xbox gatewayis 192.168.0.1 and that must be right because i can get onto xboxlive just fine. I had a few things I thought I should mention before i started this post, but i'm just completely blanked out at this stage so if there's anything else you need to know before you can help me just say so.


I copied my fuppes.cfg and vfolder.cfg from the OP, changed the sharedir to the proper folder and here is my allowed ip's section

  <allowed_ips>
      <ip>192.168.0.2</ip>   
   </allowed_ips>

everything else is as it was in the OP.

I got the xbox a week ago, I've been trying to get this working and I swear I'm this close to dual booting windows but I would really hate to do that as it would involve rebooting every time I wanted to stream media on the xbox and it would be a small victory for everyone who was telling me to 'just install windows' to fix the problem. 

any ideas? thanks in advance

--edit
actually I should mention, I reinstalled fuppes an hour or two ago just to try to get a clean start so whatever magic I did to get my music working earlier in the night is completely gone to the wind now. Probably not the smartest move ever, but there it is.

--edit

oh, and I'm using 8.10


--edit again

ok, after messing around with ushare I think I've come up with something

when i started ushare, i saw an error 

mordeth@asd:~$ /usr/bin/ushare 
Interface eth0 is down.
Recheck uShare's configuration and try again !


so just before I started ushare, I clicked on the networking icon on the top of my screen and selected the 'auto eth0' option. It told me it had connected (even though it was supposedly auto eth0 and was meant to be always connected) and then ushare worked. I was streaming video and streaming music and all was well with the world. Then I stopped ushare, and restarted it.. and nothing. 

Then I tried the same with fuppes.. I selected the auto eth0 in the networking applet and fuppes  opened up just fine on the xbox, played a few mp3s.. it didn't see any videos or jpegs but that is a completely seperate issue. Is the problem with my general networking config instead of with ushare/fuppes? I don't understand why I should have to select the eth0 every time I want to start ushare/fuppes, and even then why it only works some of the time. I googled, and found a few threads here about that particular error message ushare gave me but the only advice given was to make sure the ushare.conf was set up properly re. eth0, and it was. 

At least now I know it can work, I just have to figure out how to make it work consistently.

Progress!


--edit

'sudo ufw disable'


good christ


all working perfectly now

---

### Post by TehSnarf on 2009-07-09
And now, here's my question. Fuppes streams both my videos and my mp3's, but for whatever reason, it's not reading any of my id3 tags on my mp3's... It's just giving me a big list of mp3 filenames... Any clue as to what I may be missing? I'm pretty sure it's probably something simple, like a lib file missing or something, but I'm completely spent on trying to figure this out today.

---

### Post by shreaded_teddy on 2009-07-22
when i run sudo make i get this error: 
[libtranscoder_ffmpeg_la-ffmpeg.lo] Error 1

---

### Post by Saghaulor on 2009-08-03
I have managed to get Fuppes v643 running on Ubuntu 9.04 amd64. 

When I try to browse my shared folders, Fuppes segmentation faults.

I don't know what the problem is, but it stinks. I hope its user error cause we can fix that. 

Please help.

EDIT:
I was running Fuppes as sudo, and that was the problem. Deleted the database file, and recreated it as regular user and all is well now.

---

### Post by ngl984 on 2009-08-19
I am using svn 643 (only version that cleanly compiles, runs) however I keep getting an error message on startup:

:3: parser error : Couldn't find end of Start Tag specVe line 3
  <specVe
         ^
:3: parser error : Premature end of data in tag root line 2
  <specVe
         ^

The cfg files are default and I have double checked, have nothing to do with "<specVe" on any line. 

*Seems to work fine otherwise though...* 

Anyone else have this problem?

---

### Post by burntresistor on 2009-09-19
Well I followed the guide on the first page and I stil can't get the 360 to see fuppes. I don't know what could be causing the errors when I rebuild the database. My ip is dynamic ,so I left that part blank in the cfg. Will it work with a dynamic ip?

fuppes
```

           FUPPES - 0.646
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://127.0.1.1:53641

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

== lib/Fuppes.cpp (352) :: Fri Sep 18 21:58:17 2009 ==
new device: pandora-box FUPPES : 1 : Windows Media Connect :: MediaServer

new UPnP device:
 FUPPES : 1 : Windows Media Connect (MediaServer)
r
read shared directories
[NULL @ 0x14da5b0]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x14da5b0]frame skip 8
    Last message repeated 1 times
[wmv3 @ 0x14fe4d0]Extra data: 8 bits left, value: 0
[NULL @ 0x14e9660]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 24 times
[mpeg @ 0x158ec00]pes_ext 5A is invalid
[mpeg @ 0x158ec00]Could not find codec parameters (Audio: mp3, 0 channels, s16)
    Last message repeated 1 times
[mpeg @ 0x158ec00]Could not find codec parameters (Video: 0x0000)
[mpeg @ 0x158ec00]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x158ec00]Could not find codec parameters (Video: h264)
[mpeg @ 0x158ec00]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x158ec00]pes_ext 5A is invalid




```

Fuppes.cfg
```

<fuppes_config version="0.7.2.3">
&#8722;
<shared_objects>
<dir>/media/My Book/mkv and psp</dir>
</shared_objects>
&#8722;
<network>
<!--empty = automatic detection-->
<!--empty or 0 = random port-->
<http_port>0</http_port>
&#8722;
<!--
list of ip addresses allowed to access fuppes. if empty all ips are allowed
-->
<allowed_ips>
    </allowed_ips>
</network>
&#8722;
<content_directory>
&#8722;
<!--
a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/
-->
<local_charset>UTF-8</local_charset>
&#8722;
<!--
libs used for metadata extraction when building the database. [true|false]
-->
<use_imagemagick>true</use_imagemagick>
<use_taglib>true</use_taglib>
<use_libavformat>true</use_libavformat>
</content_directory>
&#8722;
<transcoding>
<!--[lame|twolame]-->
<audio_encoder>lame</audio_encoder>
<!--[true|false]-->
<transcode_vorbis>true</transcode_vorbis>
<transcode_musepack>true</transcode_musepack>
<transcode_flac>true</transcode_flac>
</transcoding>
&#8722;
<device_settings>
&#8722;
<!--
"default" settings are inhertied by specific devices and can be overwritten
-->
<!--do NOT remove the "default" device settings-->
&#8722;
<device name="default">
<user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
<user_agent>Xenon</user_agent>
<xbox360>true</xbox360>
<show_empty_resolution>true</show_empty_resolution>
&#8722;
<description_values>
<friendly_name>%h %s : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values>
&#8722;
<!--
specify the maximum length for file names (0 or empty = unlimited)
-->
<max_file_name_length>9999</max_file_name_length>
<!--[file|container]-->
<playlist_style>container</playlist_style>
<show_childcount_in_title>false</show_childcount_in_title>
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>4</transcoding_release_delay>
&#8722;
<file_settings>
<!--audio files-->
&#8722;
<file ext="mp3">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
</file>
&#8722;
<file ext="ogg">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<mime_type>application/octet-stream</mime_type>
&#8722;
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
&#8722;
<file ext="mpc">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<mime_type>application/octet-stream</mime_type>
&#8722;
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
&#8722;
<file ext="wav">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-wav</mime_type>
</file>
&#8722;
<file ext="flac">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<mime_type>audio/x-flac</mime_type>
&#8722;
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
&#8722;
<file ext="wma">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<mime_type>audio/x-ms-wma</mime_type>
<!-- <dlna>WMAFULL</dlna> -->
&#8722;
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>wma</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<!--image files-->
&#8722;
<file ext="jpg">
<ext>jpeg</ext>
<type>IMAGE_ITEM_PHOTO</type>
<mime_type>image/jpeg</mime_type>
</file>
&#8722;
<file ext="bmp">
<type>IMAGE_ITEM_PHOTO</type>
<mime_type>image/bmp</mime_type>
</file>
&#8722;
<file ext="png">
<type>IMAGE_ITEM_PHOTO</type>
<mime_type>image/png</mime_type>
</file>
&#8722;
<file ext="gif">
<type>IMAGE_ITEM_PHOTO</type>
<mime_type>image/gif</mime_type>
</file>
&#8722;
<file ext="tif">
<type>IMAGE_ITEM_PHOTO</type>
<mime_type>image/tiff</mime_type>
</file>
<!--video files-->
&#8722;
<file ext="mpg">
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
&#8722;
<transcode enabled="false">
<transcoder>ffmpeg</transcoder>
<ext>wmv</ext>
<mime_type>video/x-ms-wmv</mime_type>
<video_codec>wmv2</video_codec>
<audio_codec>wmav1</audio_codec>
<video_bitrate>1800000</video_bitrate>
<audio_bitrate>128000</audio_bitrate>
</transcode>
</file>
&#8722;
<file ext="mp4">
<type>VIDEO_ITEM</type>
<mime_type>video/mp4</mime_type>
&#8722;
<transcode enabled="false">
<transcoder>ffmpeg</transcoder>
<ext>wmv</ext>
<mime_type>video/x-ms-wmv</mime_type>
<video_codec>wmv2</video_codec>
<audio_codec>wmav1</audio_codec>
<video_bitrate>1800000</video_bitrate>
<audio_bitrate>128000</audio_bitrate>
</transcode>
</file>
&#8722;
<file ext="vob">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-vob</mime_type>
&#8722;
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
&#8722;
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/avi</mime_type>
&#8722;
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
&#8722;
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>
&#8722;
<file ext="vdr">
<type>VIDEO_ITEM</type>
<mime_type>video/x-extension-vdr</mime_type>
&#8722;
<transcode enabled="true">
<ext>vob</ext>
<mime_type>video/x-ms-vob</mime_type>
</transcode>
</file>
&#8722;
<file ext="flv">
<type>VIDEO_ITEM</type>
<mime_type>application/x-flash-video</mime_type>
</file>
&#8722;
<file ext="asf">
<!-- asf's were working perviously!?! -->
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-mwv</mime_type>
</file>
<!--playlists-->
&#8722;
<file ext="pls">
<type>CONTAINER_PLAYLIST_CONTAINER</type>
<mime_type>audio/x-scpls</mime_type>
</file>
&#8722;
<file ext="m3u">
<type>CONTAINER_PLAYLIST_CONTAINER</type>
<mime_type>audio/x-mpegurl</mime_type>
</file>
&#8722;
<file ext="wpl">
<type>PLAYLIST_CONTAINER</type>
<mime_type>application/vnd.ms-wpl</mime_type>
</file>
</file_settings>
</device>
&#8722;
<device name="Xbox 360" virtual="Xbox 360" enabled="true">
<user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
<user_agent>Xenon</user_agent>
&#8722;
<description_values>
 
        
<friendly_name>Fuppes : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
 
        
<model_number>2.0</model_number>
 
      
</description_values>
         
<xbox360>true</xbox360>
&#8722;
<file_settings>
&#8722;
<file ext="mp3">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
</file>
&#8722;
<file ext="jpg">
<type>IMAGE_ITEM_PHOTO</type>
</file>
&#8722;
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
&#8722;
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
</device_settings>
</fuppes_config>

```

---

### Post by burntresistor on 2009-09-19
This is what im putting into my ./configure why wouldn't it recognize enabling transcoding 

```

~/fuppes$ ./configure --enable-video-transcoding --enable-lame --enable-twolame --enable-mad \
> --enable-faad --enable-Exiv2 --enable-mpegip --enable-simage \
>   --prefix=/usr
configure: WARNING: unrecognized options: --enable-video-transcoding, --enable-Exiv2, --enable-mpegip, --enable-simage

```






[libmetadata_libavformat.la] Error 1

I reinstalled ffmpeg according to the guide all checkinstalls were fine, I'm still getting this error in the make of my reinstall of fuppes

---

### Post by ruffled on 2009-09-22
I'm willing to bet those who don't have a .fuppes directory in their home share folder have one in /root instead as they made the same mistake as me and installed as root rather than as a user :)

---

### Post by ruffled on 2009-09-22
Any idea what this message means: 

```
lib/Fuppes.cpp (352) :: Tue Sep 22 14:32:47 2009 ==
new device: Netgear DG834 Router :: unknown

new UPnP device:
Netgear DG834 Router (unknown)
== lib/Fuppes.cpp (352) :: Tue Sep 22 14:32:48 2009 ==
new device: Netgear DG834 Router :: unknown

new UPnP device:
Netgear DG834 Router (unknown)
== lib/Fuppes.cpp (352) :: Tue Sep 22 14:32:50 2009 ==
new device: Netgear DG834 Router :: unknown

new UPnP device:
Netgear DG834 Router (unknown)
```Currently I can't view my fuppes media server folders, I've basically followed the instructions step by step.

edit - I can see it on the ps3 actually it's just the web interface on port 9137 which doesn't appear to work.

---

### Post by alcoholman69 on 2009-09-29
Hi, I have the exact same message as ruffled but with a Motorola Corporation SVG2500, I've been stuck at this for days now.  The fuppes server work, I can access the web UI from any other computer on the network but I cant get my PS3 to see it.  Any help is appreciated,

---

### Post by SadaraX on 2009-11-14
Hi guys. I think I found a solution to the error messages about socket binding:

I was frequently getting a message like this:

> 
ERROR] failed to bind socket to : 8.15.7.117:0


And I was always editing the /etc/fuppes/fuppes.cfg

However, I eventually figured out that running fuppes with 'sudo fuppes' was using the config file in /home/username/.fuppes/fuppes.cfg

I edited that file and things started to work. Don't forget to kill prior instances of the fuppes before starting a new one with the modified configuration. Hope that helps.

---

### Post by Shhnap on 2009-11-15
Just don't run 'sudo fuppes' a a general rule. You should run fuppes as yourself and fuppesd as a new 'fuppes' user. There is more information on the fuppes wiki page that you should take a look at. They contain the best practises: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Main_Page](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Main_Page)

---

### Post by adenewton on 2010-02-25
I'm another one with a make error:

make[1]: *** [libmetadata_libavformat.la] Error 1
make[1]: Leaving directory `/home/ade/fuppes/src/plugins'
make: *** [all-recursive] Error 1
ade@ade-ubuntu:~/fuppes$ 

I'm on Ubuntu 9.10 64bit.


two others have had similar errors but no one has posted a fix, so i guess I won't be holding my breath! :(

Is there any other upnp servers that will support both the xbox and PS3?

P.S> just noticed there is a 9.10 guide, you should really put a link to it on the original post, save people wasting some time!

[http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511)

---

