---
title: "PS3 Media Centre - MediaTomb vs Fuppes"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Fajman on 2008-08-02
Well I've finally set up a media center (Fuppes) on Ubuntu 8.04 that seems as good as (if not better) than TVersity (on windows). I should point out that DivX is the main purpose for my media center. I'm an Ubuntu noob so I may have put a few steps wrong... but it was all fun.

I tried pretty much every linux media center option available except for Twonky (because you have to fork out cash)

Me experiences are below
1. GMediaServer - Doesn't even seem to do DivX...waste of time for me. Might be ok for audio though.

2. UShare - Kept getting 'Unsupported Data' for DivX files and after a lot of searching/playing I finally gave up.

3. MediaTomb - This seems to be the one everyone is raving about for the PS3. I got it working after a few minor problems. 
[INDENT]First Prob - 2 configuration files, basically it loads up ~\.mediatomb\config.xml instead of \etc\mediatomb\config.xml as i was expecting. [/INDENT]
[INDENT]Second Prob - Unsupported Data comes up for divX files so I needed to tweak my config.xml (see below) and got it working[/INDENT]

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlnssi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
<server>
<ui enabled="yes">
<accounts enabled="no" session-timeout="30">
<account user="mediatomb" password="mediatomb"/>
</accounts>
</ui>
<name>MediaTomb</name>
<udn>uuid:c4425c07-a131-403b-88a6-e1e2dc163b7f</udn>
<home>/var/lib/mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
<storage>
<sqlite3 enabled="yes">
<database-file>sqlite3.db</database-file>
</sqlite3>
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>
</mysql>
</storage>
<protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
<!--
Uncomment the lines below to get rid of jerky avi playback on the
DSM320 or to enable subtitles support on the DSM units
-->
<!--
<custom-http-headers>
<add header="X-User-Agent: redsonic"/>
</custom-http-headers>

<manufacturerURL>redsonic.com</manufacturerURL>
<modelNumber>105</modelNumber>
-->
<!-- Uncomment the line below if you have a Telegent TG100 -->
<!--
<upnp-string-limit>101</upnp-string-limit>
-->
</server>
<import hidden-files="no">
<scripting script-charset="UTF-8">
<common-script>/usr/share/mediatomb/js/common.js</common-script>
<playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
<virtual-layout type="builtin">
<import-script>/usr/share/mediatomb/js/import.js</import-script>
</virtual-layout>
</scripting>
<mappings>
<extension-mimetype ignore-unknown="no">
<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
<map from="flv" to="video/x-flv"/>
<!-- Uncomment the line below for PS3 divx support -->
<map from="avi" to="video/divx"/>
<map from="divx" to="video/divx"/>
<!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
<!-- <map from="avi" to="video/avi"/> -->
</extension-mimetype>
<mimetype-upnpclass>
<map from="audio/*" to="object.item.audioItem.musicTrack"/>
<map from="video/*" to="object.item.videoItem"/>
<map from="image/*" to="object.item.imageItem"/>
</mimetype-upnpclass>
<mimetype-contenttype>
<treat mimetype="video/x-divx" as="avi"/>
<treat mimetype="audio/mpeg" as="mp3"/>
<treat mimetype="application/ogg" as="ogg"/>
<treat mimetype="audio/x-flac" as="flac"/>
<treat mimetype="image/jpeg" as="jpg"/>
<treat mimetype="audio/x-mpegurl" as="playlist"/>
<treat mimetype="audio/x-scpls" as="playlist"/>
<treat mimetype="audio/x-wav" as="pcm"/>
<treat mimetype="video/x-msvideo" as="avi"/>
</mimetype-contenttype>
</mappings>
</import>
<transcoding enabled="no">
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="oggflac2raw"/>
<transcode mimetype="video/x-divx" using="video-common"/>
</mimetype-profile-mappings>
<profiles>
<profile name="oggflac2raw" enabled="no" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -f %out %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="vlcmpeg" enabled="no" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25, aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,ch annels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
</profiles>
</transcoding>
</config>
```

Why not MediaTomb for me (may be fine for others) -
- I have about 100Gig worth sorted in folders. MediaTomb puts all videos under one 'Video' folder which makes it too difficult to search on the PS3 for what i want to watch. 
- It seems to freeze or lag every few mins when i watch a divX... and i have no idea why. I'm thinking it has something to do with playing a divX on the PS3.

4. Fuppes - This is the one I'm now using
It solves the MediaTomb problems above 
- It keeps my directory structure
- It doesn't freeze up. It seems to work for me when I transcode divX to mpeg2, with no visible loss of quality. If I don't set transcoding on divX files i get the same freeze up's i get on MediaTomb. I've seen forums where people talk about getting similar problems on the PS3 but no solutions... pretty sure the transcoding option did it for me.

There are a few guides to get Fuppes set up, so search away. I used some points from the following link and played with the config file to get it working 

(below)

[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04]("http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04")

Located in ~/.fuppes/config.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/home/pfajou/Video</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.3</interface>
    <!--empty or 0 = random port-->
    <http_port>8765</http_port>
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
    <!--It is safe to remove unneeded devices-->
<device name="PS3" enabled="true">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<ip>192.168.1.2 </ip>
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>80</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
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
<mime_type>video/divx</mime_type>
<!--<mime_type>video/x-divx</mime_type>-->
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec acodec="wmav2">mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
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
<file ext="vob">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>

</file_settings>
</device>    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
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

Let me know if this was a waste of a read or if it actually helped someone.

Update
See my post further down on VLC

---

### Post by mbmonk on 2008-08-15
Thanks for the writeup. I was trying to decided on a media server. I think I am going with Mediatomb for now because I got it working before and the setup was easy due to packages. But I will put Fuppes in the on deck circle if I have problems.

Thanks.
Mike

---

### Post by PlankEyeWilly on 2008-08-20
I kind of went the same route, but mostly with MediaTomb and Fuppes.  I tried Fuppes first, and was pleased, but with all of the posts here that I have seen about MediaTomb I decided to give it a shot.  The HowTo that I used to set up Fuppes was short, simple and to the point.

[http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04]("http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04")

The only issue that I did run into is that at the moment I am transitioning from Windows to Ubuntu so all of my media is on a larger NTFS Partition.  The path to those files was changing depending on which partition on that drive was mounted in what order. I went into fstab and statically set the mount point for that partition to prevent my database in fuppes attempting to access my media from the wrong path. Since that everything has been smoothe sailing!  Hopefully I will soon be completely converted over to Ubunut, and wont have need for my Windows partitions at all!!!

---

### Post by Enufalready on 2008-08-25
I'm a big fan of Fuppes for streaming media to my PS3.  I've found it stable, quick, and easy to use.  What I can't work out how to do is have my PS3 show my playlists.  No one can tell me if this is a PS3 issue or if my Fuppes is set up incorrectly.  Looking at Fajmans config file my appears to be the same.  I would love to hear from anyone who has been able to do this.

My Fuppes server is running on FreeNAS so maybe this is not the right place to ask this question.  But surely if someone has been able to achieve this on Ubnutu then I can make the changes on FreeNAS

---

### Post by saberskunk on 2008-08-26
I use Fuppes with my ubuntu install and it works OK. However the playback controls don't work (pause, rewind etc...). I find this a major pain in the ***. To be fair all I need is pause ;)

---

### Post by PlankEyeWilly on 2008-08-26
I haven't had any problems with my playback controls not working.  I stream everything from my PS3, and I can pause, fast-forward, and rewind.  

Is the firmware on your PS3 or XBOX up-to-date, if that's what you are streaming to?

---

### Post by saberskunk on 2008-08-26
I stream from my Fuppes to my PS3.

Fuppes is version 0.611 which I installed a couple of months ago.

I have seen threads on the fuppes site requesting playback controls in the software so I assumed they were not currently supported by the software?

---

### Post by Fajman on 2008-08-26
saberskunk - most of my streaming is playing tv shows/movies for my kids to keep them occupied... no remote was necessary. I can't remember if i had a problem with it... i'd try it out again to let you know but i'm no longer using Fuppes.

My advice - 

try mediatomb it's easy to set up and it might do the trick. Let us know how you go... it's a serious down point if Fuppes can't handle those basics.
OR
if you have some time see my latest post below and try VLC... that will definitely allow all the pausing, rewind etc.

---

### Post by Fajman on 2008-08-26
After my original post I decided to try one more - VLC... Fuppes isn't perfect and I wanted to play with linux on the ps3

Installing & configuring Yellowdog on a PS3 took me a while, roughly 4 hours. So if you have a bit of time to spend give it a go. I'm also hoping my post may help some people get it down from the 4 hours i went through.

1. The install on Yellewdog6.0 is relatively easy
Follow the official guide on the yellowdog site
[http://www.terrasoftsolutions.com/support/installation/](http://www.terrasoftsolutions.com/support/installation/)

2. Setting up wireless for me was a pain as I was using WPA TKIP. There's no official guide to setup WPA on the yellowdog site, they only give instructions on WEP. I followed this guide to get it working
[http://dachaac.blogspot.com/2007/08/guide-to-get-wpa-psk-working-on-ps3-ydl.html](http://dachaac.blogspot.com/2007/08/guide-to-get-wpa-psk-working-on-ps3-ydl.html)
You may still get some problems so read the reply's to the blog

3. Installing VLC
You need the correct repositories to install
I used this site to setup the repos
[http://www.yellowdog-board.com/viewtopic.php?f=19&t=3017](http://www.yellowdog-board.com/viewtopic.php?f=19&t=3017)
AND 
to configure VLC I used this site (ie to right click a video and play with VLC)
[http://www.ps3forums.com/showthread.php?t=53776](http://www.ps3forums.com/showthread.php?t=53776)

4. Setup a share to your video folder on your Ubuntu (or Windows box)... you'll have to figure this one out for yourself. One piece of advice though... most people will probably use Samba via Nautilus. I was stuck setting that one up for a while then did a "yum update" and it all started working, I noticed there was a Samba client update which probably fixed it. SO MAKE SURE YOU GET ALL AVAILABLE UPDATES before trying to setup your network.

If you don't want to have a keyboard plugged into your PS3 follow these last steps
*I don't have a room for a keybaord in my lounge room right now.*
5. I then wanted to get an onscreen keyboard working so i could use it via my mouse if i needed to
Within YLD
System->Preferences->Accessibility->assistive technology preferences
and select on screen keyboard
Note - I select the Gnome interface rather than Enlightenment when i log in.

6. I wanted to auto login to yellowdog (again because i didn't want to use my keyboard, all i wanted was to stream via VLC). i ran gdmsetup and selected autologin but it didn't let me select a user so i needed to edit

/etc/gdm/custom.conf
to add 
AutomaticLoginEnable=true
AutomaticLogin=[your username]

That was pretty much it, took a while to work out though so i hope it helps.

So is VLC better than Fuppes.... if all your after is playing movies then there's not a huge difference, VLC probably gives you better remote control and VLC will also play just about any media out there. I mostly like the fact I now have a new computer with Linux in the PS3 so I'm gonna stick with VLC for a while. So if you have the time... go YLD with VLC.

---

### Post by kameyou on 2008-08-28
Hi Fajman,

Need a favor on setting up Fuppes transcoding. I followed Andrew's instruction 
([http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04](http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04))
to install Fuppes and copied your setting into /etc/fuppes/fuppes.cfg, however, seems the transcoding for Divx video still doesn't work.

And on the Fuppes's website, it is showing the following lines complaining neither LAME nor TwoLam found. May I know what does that mean?

**transcoding**

Neither LAME nor TwoLame found. Transcoding disabled!

Besides, is that anyway to transcode Realmedia file (i.e. rmvb) so that I can watch it via PS3? Any help would be really appreciated. 

Thanks,
Kameyou

---

### Post by stevoo on 2008-09-21
it seems i am getting the same error.

Neither LAME nor TwoLame found. Transcoding disabled!

have you managed to find a work arround ?

---

### Post by PlankEyeWilly on 2008-09-22
I think that the error just means that you have to install LAME. It's in synaptic under the multiverse repo, not in the Medibuntu repo. Make sure that repo is enabled. Once it is, close and reload Synaptic. Then search for LAME.

Let me know how that goes for you.

---

### Post by unabatedshagie on 2008-09-25
I'm having the same problem.

In the status page it says I don't have lame or twolame but according to synaptic they are.

---

### Post by Conq on 2008-09-28
You need the -dev packages (e.g liblame-dev)

---

### Post by sladetf on 2008-10-02
Thank you for the post, it helped me through a few of my own installation and configuration problems.  Finally I'm at a real dead end.  Transcoding simply will not work, or at least is not working the way I expect.

What works:
-The PS3 finds fuppes.
-PS3 can play any native PS3-compatible format through Fuppes (divx, mp3, wma, etc).

What does not work:
-Anything with an alternative file extension (Ex: FLV or OGG) is still detected by the PS3 as an invalid file or "unsupported data type".

I am using Fajman's config file only modified w/ the proper IP and data file locations.

Can anyone help me out?

Thanks,
sladetf

---

### Post by sladetf on 2008-10-02
Also -- the web interface might tell you that "lame or twolame" is not configured and is disabled, but this could just be a cosmetic error.

The command line interface for fuppes will tell you the truth if lame is installed properly right.  To check, just go to your home folder with some original version of the fuppes.cfg file, and just run fuppes manually.  Hit 'i' after its started and you'll see that lame is enabled.  (Please note that yes my web interface also says my lame/twolame is disabled.  Just a bug.)

i
general information:
  version     : 0.617
  hostname    : libsrv1
  OS          : Linux 2.6.24-19-server
  build at    : Sep 28 2008 14:43:31
  build with  : 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
  address     : 192.168.1.101
  sqlite      : 3.4.2
  log-level   : 1 (normal)
  webinterface: [http://192.168.1.101:5080/](http://192.168.1.101:5080/)

configuration file:
  /home/admin/.fuppes/fuppes.cfg

faad: enabled
flac: enabled
iconv: enabled
ImageMagick++: enabled
ImageMagick Wand: disabled
inotify: enabled
**lame: enabled**
libavformat: enabled
libnotify: disabled
mad: enabled
mp4ff: enabled
mpeg4ip: enabled
musepack: enabled
simage: enabled
inotify: enabled
taglib: enabled
tremor: disabled
**twolame: enabled**
uuid: enabled
vorbis: enabled

---

### Post by iceman600 on 2008-10-30
i cannot make my mkv fifles to work on fuppes nor on mediatomb. 
im now using fuppes because it is easy to setup and more friendly interace when i comes to updating database.

is anybody here transcoding mkv files to ps3 frm fuppes? 
i need help pls...
thanks:lolflag:

---

### Post by PlankEyeWilly on 2008-10-30
I am not real expert, but to my knowledge I dont think that the PS3 supports those media types. Your best bet is to convert them over to a supported codec.

---

### Post by iceman600 on 2008-10-30
i used to be a windows user and tversity works on transcoding mkv files to my ps3. since im an ubuntu user now i find myself lost at some apps. like i have trouble instaling tversity with wine on ubuntu so im on to fuppes now. but i cannot make my mkv files to stream on my ps3 like b4. 

if anyone with any knowledge, pls help. thanks

---

### Post by saberskunk on 2008-10-31
I got completely hacked off with the whole linux and media streaming and reverted back to windows. 

I'm surprised that there is not more Linux software out there for this.

---

### Post by iceman600 on 2008-11-08
i tried both mediatomb and fuppes and i have issues on both... 

they both lag on playing on my ps3. it kinda anoys me when wathing movies... it stops for a while and then resumes. what seems to be the problem? is it my router? 

arg!!! i hope there is a fix for this... 
anyone having the same problem? is there a fix for this?

---

### Post by sony_gamer on 2009-02-28
you might want to try PS3 Media Server
[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)
currently theres no web interface to control it but it seems the developer might be adding it in the future

---

### Post by laluz on 2009-04-15
> **sony_gamer said:**
> you might want to try PS3 Media Server
[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)
currently theres no web interface to control it but it seems the developer might be adding it in the future
I have just downoaded the ps3mediaserver. It worked out of the box. Ubuntu Intrepid. All the the dependencies were already installed on my system.

I have installed and configured FUPPES as well. Most of the stuff works, but I will have to tinker a bit more to get to the ps3mediaserver level. So compared to ps3mediaserver it feels actually awkward.

I'd say go for ps3mediaserver.

---

