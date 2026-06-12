---
title: "Fuppes - Xbox 360 Won't Find"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by Amyn on 2007-11-20
I've searched to the best of my ability and tried to best of my ability, but I have not been able to get Fuppes working.  I used uShare, and it worked great, but what I'm really after is the on-the-fly transcoding Fuppes has.  I'm not sure what the problem is, but my Xbox 360 will not pick up Fuppes.

```
amyn@AMYN-PC:~$ fuppes
            FUPPES - SVN-r558
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

new device: Residential Gateway :: unknown
new device: Residential Gateway :: unknown
new device: Residential Gateway :: unknown
webinterface: http://192.168.1.5:33325

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
new device: Xbox 360 :: MediaRenderer
r
[ContentDatabase] create database at Tue Nov 20 18:56:15 2007
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Tue Nov 20 18:56:16 2007
v
[VirtualContainer] create virtual container layout started at Tue Nov 20 18:56:17 2007
[VirtualContainer] virtual container layout created at Tue Nov 20 18:56:17 2007


```

I really don't know what the problem is, I've attached my fuppes.cfg and vfolder.cfg files.

Thanks in advance,
Amyn

---

### Post by Amyn on 2007-11-22
bump

---

### Post by Amyn on 2007-11-30
Bump

---

### Post by lmellor on 2007-12-02
bump, same probs here on gutsy amd64

---

### Post by Amyn on 2007-12-02
It works.

I don't know what it was, interferace from uShare or that I just needed to restart the comp. and Xbox, but it works...

At least with Divx/Xvid, any idea on mkv?

---

### Post by lmellor on 2007-12-03
I've no idea what's going off with mine, I've got the exact same setup as yourself and still the xbox can't see the computer, the computer can tell me when the 360 is turned on though.

I'm not running ushare though I'm beginning to wonder if my web server or ftp server are getting in the way, though they play well with eachother and run on totally different ports to fuppes, all suggestions on a postcard for me I'm afraid, I do hope somebody can help.

---

### Post by dent_a on 2007-12-03
Just as a suggestion... is your firewall settings getting in the way?

I would like to install a server for dishing out content to my XBOX but have not taken the task on yet. I really just have AVI/DIVX files I want to view on my XBOX. Can i do this through SAMBA? Anyone know?

Does anyone now how the new update Dec 4, 2007 (it adds AVI and MPEG-4) will effect setting up?

---

### Post by lmellor on 2007-12-03
If you're talking xbox 360 then welcome to the nightmare that is FUPPES, if you're talking the good old xbox then so long as you've modded it and have xbmc running on it then just use samba, I got a program from the add/remove bit off the applications menu called gsambad, makes for much lighter work of setting up samba than doing it the old fashioned way.

I do hope I've helped you in some way with this info.

If you do get FUPPES running then I'd love to find out how you did it, I'm running gutsy 64 without any firewall and I'm REALLY struggling to get them to play nice, FUPPES sees the 360, shame the 360 is blind to what's good for it!

---

### Post by jkuhnert on 2007-12-03
Add this to your fuppes.cfg and all should be well (as taken from [http://sourceforge.net/forum/forum.php?thread_id=1871864&forum_id=475749](http://sourceforge.net/forum/forum.php?thread_id=1871864&forum_id=475749) ):

===================

Just add these lines between the <device name="Xbox"> ... </device> nodes. 
 
<description_values> 
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name> 
<model_name>Windows Media Connect compatible (%s)</model_name> 
<model_number>2.0</model_number> 
</description_values> 
===================

---

### Post by lmellor on 2007-12-04
You my friend are a GOD, a true GOD, it's been at least 3 days that I've been playing with this thing now, I cannot thank you enough, really can't, maybe I'll get around to writing a full tutorial for this.  For anybody who's been really struggling then this is the answer.  Now to wait n see what the update brings xvid wise.

Cheers once again dude!

---

### Post by fireport on 2007-12-04
can you post the right fuppes.cfg
I have added the suggested line with no luck
Thanks

---

### Post by Octagonal on 2007-12-04
As of the new update from microsoft the Xbox 360 can now nativley play avi files.  Anybody have any luck listing avi files in the dashboard.  I've tried editing the mime type but still have no luck seeing any avi files listed from fuppes.

---

### Post by stryderjzw on 2007-12-04
OMG.  It WORKS and all the Xvids/DivX works beautifully.  I'll have to go out now, but brief summary:

I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=597650&highlight=xbox+360](http://ubuntuforums.org/showthread.php?t=597650&highlight=xbox+360)

Then used the fix in this thread. 

Thank you jkuhnert!

---

### Post by Octagonal on 2007-12-04
> **stryderjzw said:**
> OMG.  It WORKS and all the Xvids/DivX works beautifully.  I'll have to go out now, but brief summary:

I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=597650&highlight=xbox+360](http://ubuntuforums.org/showthread.php?t=597650&highlight=xbox+360)

Then used the fix in this thread. 

Thank you jkuhnert!

Are you transcoding?
I can get transcoding working but I'd rather not transcode as the xbox 360 now supports avis as of 12/04/07.

---

### Post by Octagonal on 2007-12-04
changing the mimetype to video/avi actually did work for me--I just ended up making a dumb mistake and not putting the movie in the correct forlder for testing ugh.

---

### Post by bartoni on 2007-12-06
Worked, sort of, last night. I could view photos, mp3s and see videos (but no playback).  This morning it isn't seeing any content!

I don't want to transcode, just play Divx/xvid directly if possible.

I've added the fixes listed here but obviously still doing something wrong.  The last comment about mime type as "video/avi" is that instead of video/x-msvideo? And that new "description value" does that go inside the xbox360 device or in a Xbox device as shown in the post?  

Confused.  Could someone please post a working fuppes.cfg?

---

### Post by Octagonal on 2007-12-06
I've attached my working fuppes.cfg file.  This is from ver 571 I think using svn checkout.  This is w/o transcoding--AVI, WMV, MP4 videos play just fine.

---

### Post by bartoni on 2007-12-08
Thanks, still not working for me. I've decided to use ushare... this worked great for about 10 minutes, the next time I rebooted it fails.  *sigh*

---

### Post by Spikextrem on 2007-12-09
Hi,

For those who tough it would be useful to have a startup script, I did one myself. It's REALLY basic since I never wrote such script.

But I thing it's useful :)

```

#!/sbin/runscript

opts="start stop reload"

depend() {
        need net
}


start() {
        ebegin "Starting fuppes"
        start-stop-daemon --start --quiet --background --exec /usr/local/bin/fuppes
        eend $?
}

stop() {
        ebegin "Stopping fuppes"
        start-stop-daemon --stop --quiet --exec /usr/local/bin/fuppes
        eend $?
}


reload() {
        ebegin "Refreshing fuppes' data"
        start-stop-daemon --stop --quiet --exec /usr/local/bin/fuppes -r
        eend $?
}

```

Paste the code as root in something like /etc/init.d/fuppesd
then

```
chmod +x /etc/init.d/fuppesd
rc-update add fuppesd default

```

I hope it will help.

---

### Post by lighty14 on 2007-12-11
After spending a day trying to get my Xbox 360 to see ushare, I decided to give this a try. I followed the (old) how-to, excluding the transcoding parts, used the tidbit in this thread, and... I still can't see my shares on my Xbox 360. I believe the problem is somehow related to my computer also acting as the router for my internet connection, with a switch between other computers and 360 and eth0, eth1 to the internet. I've been able to share in Windows using TVersity, but I really want to avoid booting into Windows whenever I want to watch a movie.

---

### Post by blueorder on 2007-12-11
> **lighty14 said:**
> After spending a day trying to get my Xbox 360 to see ushare, I decided to give this a try. I followed the (old) how-to, excluding the transcoding parts, used the tidbit in this thread, and... I still can't see my shares on my Xbox 360. I believe the problem is somehow related to my computer also acting as the router for my internet connection, with a switch between other computers and 360 and eth0, eth1 to the internet. I've been able to share in Windows using TVersity, but I really want to avoid booting into Windows whenever I want to watch a movie.

I was having an issue with following the tutorial and tried using the --disable-transcoding flag during configure. I was able to compile with that flag since I do not want to transcode. I start fuppes and the Xbox 360 can see the computer but none of the files are there.

I entered the dirctory in the cfg file and used one of the vfolder files provided in one of the posts.

---

### Post by Amyn on 2007-12-25
Glad to hear you got it working.

The dashboard update has brought Divx/Xivd support, so uShare works great.  However, is it possible to transcode .mkv file on the fly with Fuppes?

---

### Post by mkzimms on 2008-01-13
No problems getting the xbox to see fuppes, it nicely shows "FUPPES SVN-r584:1" as a source, but none of my files are there...

heres the fuppes output

```
mikez@twinkie:~/.fuppes$ fuppes
            FUPPES - SVN-r584
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/ContentDirectory/VirtualContainerMgr.cpp (54) :: Sun Jan 13 20:22:04 2008 ==
no vfolder.cfg file available

webinterface: http://192.168.1.50:8080

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
== lib/Fuppes.cpp (336) :: Sun Jan 13 20:22:05 2008 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
== lib/Fuppes.cpp (336) :: Sun Jan 13 20:22:09 2008 ==
new device: WRT54G :: unknown

new UPnP device:
WRT54G (unknown)
== lib/Fuppes.cpp (336) :: Sun Jan 13 20:22:09 2008 ==
new device: WRT54G :: unknown

new UPnP device:
WRT54G (unknown)
== lib/Fuppes.cpp (336) :: Sun Jan 13 20:22:09 2008 ==
new device: WRT54G :: unknown

new UPnP device:
WRT54G (unknown)

```

this line scares me and i through it was taken care of by the description values ```
:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"

```

heres my fuppes.cfg

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/data</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>8080</http_port>
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
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
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

and my vfolder.cfg

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

```

please help!!! thanks guys and gals.

---

### Post by mkzimms on 2008-01-17
bump

---

### Post by mkzimms on 2008-01-23
bump, please help.  im dying over here and ushare is crap, if i have to scroll through a list of 58,000 files to find an mp3 again im going to break my rig.

---

### Post by muzah on 2008-01-28
:KS

I have the same problem. If you find an answer, could you please write it here :)

Thank you :)

---

### Post by EnsignR on 2008-01-31
I think you might be missing the following attribute in your vfolder_layout for the 360 (in ~/.fuppes/vfolder.cfg)

<vfolder_layout device="Xbox 360" enabled="true" **create_references="true"**>

That should hopefully sort your problems (after you rebuild the layout ('v' in fuppes).

Hope that helps.

---

### Post by daodie on 2008-02-07
xbox can see fuppes but shows no files :confused:

---

### Post by m3_del on 2008-02-07
in the fuppes console type "v" (without the quotes) and press enter.

---

### Post by SumnerBoy on 2008-02-26
Hi - I am very keen to try FUPPES so I can stream FLACs to my XBox 360. I have been following the instructions at [http://ubuntuforums.org/showthread.php?t=597650](http://ubuntuforums.org/showthread.php?t=597650) as I am running Ubuntu 7.10 Server Edition.

However I am failing at the very first step! When I run the apt-get install command I get the following message...

```
ben@weka:~$ sudo apt-get install ffmpeg build-essential libavutil-dev libavformat-dev libavcodec-dev subversion libtool automake autoconf libsqlite3-dev libpcre3-dev libxml2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
libavutil-dev is already the newest version.
libavutil-dev set to manual installed.
libavformat-dev is already the newest version.
libavcodec-dev is already the newest version.
libavcodec-dev set to manual installed.
subversion is already the newest version.
libtool is already the newest version.
automake is already the newest version.
autoconf is already the newest version.
autoconf set to manual installed.
libsqlite3-dev is already the newest version.
libpcre3-dev is already the newest version.
libxml2-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodeccvs51 (>= 3:20071206) but it is not going to be installed
          Depends: libavdevicecvs52 (>= 3:20071206) but it is not going to be installed
          Depends: libavformatcvs52 (>= 3:20071206) but it is not going to be installed
          Depends: libavutilcvs49 (>= 3:20071206) but it is not going to be installed
          Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
          Depends: libswscalecvs0 (>= 3:20071206) but it is not going to be installed
E: Broken packages
ben@weka:~$
```

Any one got any ideas as to why these dependencies are broken?

---

### Post by kexodusc on 2008-03-02
I'm having a similar problem to the user above - I've followed the how-to's here on installing and configuring fuppes.

The Xbox 360 can connect to my computer fine, but no files are showing.
Not sure if it's my fuppes.cfg file or my vfolder.cfg file but here's both:

fuppes.cfg:
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/data/Music/mp3</dir>-->
    <!--<dir>/data/Downloads</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>

   <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9452</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.100</ip>
      <ip>192.168.0.101</ip>
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
          <mime_type>application/octet-st<description_values> 
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name> 
<model_name>Windows Media Connect compatible (%s)</model_name> 
<model_number>2.0</model_number> 
</description_values> ream</mime_type>
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
                <audio_bitrate>192000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
   </device_settings>
</fuppes_config>
```

and vfolder.cfg:

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

```

Appreciate any help anyone can provide.  I'm sure I'm overlooking something but have no idea what.

---

### Post by HornedBeast on 2008-03-12
Thanks for this bit of help - but I was wondering if you could point me in the right direction to get Fuppes for Gutsy as a deb? Latest version - or at least the version you were using to get music to stream to 360.

Or just a guide on how to install it and get it working?

Cheers.

Horned

---

### Post by SumnerBoy on 2008-03-12
Anyone else had any success installing and running FUPPES on Ubuntu 7.10 server edition? Please see my earlier post for the errors I get when trying to install using apt-get. Any help would be great. Thanks.

---

### Post by HornedBeast on 2008-03-12
Hello. Yes, ive got it installed on Ubuntu Server 7.10. I followed this: [http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare](http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare)

However, Im having the same problem as a few others.

I can connect to the share, but it doesn't seem to have catalogued it as it should. It hasnt broken it down into artists and things.

Any word on what might be wrong?

I've posted my 2 files here:

Anyone at all?

---

### Post by darkwalt on 2008-05-05
Ok, followed two different threads to this point.  My 360 won't detect fuppes, and my fuppes won't show my 360.  I've been playing around with this for a day and a half now and I still don't know what's wrong.  I'm attaching my vfolder and fuppes cfg's here.  Maybe the answer is so obvious tnat i'm missing it.

---

### Post by Alturos on 2008-05-11
> **EnsignR said:**
> I think you might be missing the following attribute in your vfolder_layout for the 360 (in ~/.fuppes/vfolder.cfg)

<vfolder_layout device="Xbox 360" enabled="true" **create_references="true"**>

That should hopefully sort your problems (after you rebuild the layout ('v' in fuppes).

Hope that helps.

I was having the problem where no files were showing. Turns out the xbox 360 layout was disabled. Updated to match and now it works. thanks.

---

### Post by Octagonal on 2008-05-28
Anyone able to get Fuppes working under Hardy Heron yet?
When I try to run it under hardy I get:

FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!

---

### Post by karlhm76 on 2008-07-13
Hi all, after a lot of research on the net and playing around with the fuppes config and the vfolder config I finally got everything working with one issue.

I'll begin watching a movie or TV show and then it will dump me back to the Xbox OS. When I check fuppes it says "device: Xbox 360 timed out"

I'm using wireless for everything. It works so good apart from that.

Has anyone had any problems like this and solved it?

If anyone has worked out how to organise music into the categories on the xbox that would be good to know as well (I have about 1600 songs and its painful to scroll through them sorted by alpha!).

If anyone wants to see my configs they are here. Nothing worked until I added the extra settings to the device section, and changed the vfolder config file:

fuppes:
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/karl/Music</dir>
    <dir>/home/karl/Videos</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>ath0</interface>
    <!--empty or 0 = random port-->
    <http_port>8080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>10.1.1.2</ip>
      <ip>10.1.1.3</ip>
      <ip>10.1.1.4</ip>
      <ip>10.1.1.5</ip>
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
    <!--do NOT remove the "default" device settings-->
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
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
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
    </device>
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
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


vfolder:
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
```

---

### Post by karlhm76 on 2008-07-20
Hi all,

solved both the above problems if anyone's interested.

the problem of timeout was solved by turning off transcoding of avi. I was unaware that xbox supported avi natively.

the second problem of the music not being categorised was solved by installing the taglib development files and recompiling

---

### Post by lmellor on 2008-07-20
Could you elaborate on this a little further for those of us who are still in our linux infancies?  How exactly did you install the taglib development files?

---

