---
title: "transcoding ps3 firmware 2.35 mediatomb"
date: 2008-06-15
forum: Multimedia Software
---

### Post by graveson on 2008-06-15
does anyone have transcoding working flawlessly with the ps3 and mediatomb?

---

### Post by Rever75 on 2008-06-19
Bump....

<I believe I have it working but not sure if I have it optimized>

---

### Post by Dies on 2008-06-20
Works very well here. Aside from not being able to seek during playback. :(

But not much that can be done about that, except converting everything to a supported format permanently.

Anyways here's my config.xml in case it helps anyone, this of course is specific to my needs and may not work so well for others.

This is set up to transcode all flash files and any avi files which are not compatible with the PS3, avi's which are compatible are ignored, also provides thumbnails for all videos and ignores any files which have an extension that isn't listed. I have no need for ogg or flac transcoding but also no reason to believe that just uncommenting the relevant entry and enabling the profile under it wouldn't work.


```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">

  <server>

	<port>?</port>

    <ui enabled="yes">
      <accounts enabled="yes" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>

    <name>MediaTomb</name>
    <udn>?</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>

    <storage>
      <sqlite3 enabled="no">
        <database-file>sqlite3.db</database-file>
      </sqlite3>
      <mysql enabled="yes">
        <host>?</host>
	<port>?</port>
        <username>?</username>
	<password>?</password>
        <database>?</database>
      </mysql>
    </storage>

<!-- PS3 requires "yes" -->
    <protocolInfo extend="yes"/>

  </server>


  <import hidden-files="no">

	<autoscan use-inotify="auto">
		<directory location="/Videos" mode="inotify" recursive="yes" hidden-files="no" />
		<directory location="/Music" mode="inotify" recursive="yes" hidden-files="no" />
		<directory location="/Pictures" mode="inotify" recursive="yes" hidden-files="no" />
	</autoscan>

    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>

<!-- Only show PC Directory -->
      <virtual-layout type="disabled">

        <import-script>/usr/share/mediatomb/js/import.js</import-script>
      </virtual-layout>
    </scripting>


    <mappings>

<!-- Don't import anything not listed here since it's pointless -->
      <extension-mimetype ignore-unknown="yes">

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

<!-- List images so they get imported -->
	<map from="jpg" to="image/jpeg" />
	<map from="jpeg" to="image/jpeg" />
	<map from="png" to="image/png" />
	<map from="svg" to="image/svg" />

<!-- Added for PS3 DiVX support -->
        <map from="divx" to="video/x-divx"/>
	<map from="avi" to="video/x-divx"/> 
      </extension-mimetype>

      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>

      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/x-divx" as="avi"/>
      </mimetype-contenttype>

    </mappings>

  </import>

  <transcoding enabled="yes">

    <mimetype-profile-mappings>

<!-- Transcode flash and avi files -->
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="video/x-ms-asf" using="vlcmpeg"/>	
      <transcode mimetype="video/x-divx" using="vlcmpeg"/>

<!--  <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>  -->

<!-- Added for PS3 thumbnail support -->
      <transcode mimetype="video/x-divx" using="video-thumbnail"/>
      <transcode mimetype="video/x-avi" using="video-thumbnail"/>
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

<!-- Added for PS3 thumbnail support -->
      <profile name="video-thumbnail" enabled="yes" type="external">
        <mimetype>image/jpeg</mimetype>
        <accept-url>yes</accept-url>
        <thumbnail>yes</thumbnail>
        <resolution>128x128</resolution>
        <agent command="ffmpegthumbnailer" arguments="-i %in -o %out -s 128"/>
        <buffer size="524288" chunk-size="512" fill-size="1024"/>
      </profile>

      <profile name="vlcmpeg" enabled="yes" type="external">

<!-- Don't transcode newer avi's which are supported -->
	<avi-fourcc-list mode="ignore">
          <fourcc>DX50</fourcc>
        </avi-fourcc-list>

        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>

    </profiles>

  </transcoding>

</config>
```

BTW after editing make sure this file is correct/valid, in my experience if it's not mediatomb will still run but will use up all available RAM and most available swap.  :shock:

---

### Post by csk on 2008-06-28
hey guys
everytime i try to transcode i get this message
> 
2008-06-28 19:26:48    INFO: Arguments: -I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (csk)
[00000289] dummy interface: using the dummy interface module...
[00000306] access_output_file private error: cannot open `/tmp//mt_transcode_EQAMDU' (Permission denied)
[00000304] stream_out_standard private error: no suitable sout access module for `file/ps:///tmp//mt_transcode_EQAMDU'
[00000301] stream_out_transcode private error: cannot create chain
[00000300] main stream output error: stream chain failed for `transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=/tmp//mt_transcode_EQAMDU}'
[00000298] main input error: cannot start stream output instance, aborting
[00000312] dummy demuxer: command `quit'
[00000283] main playlist: stopping playback


this happens regardless of whether i use the code above or the one which originally came with mediatomb. I think the error seems to be here 
[00000306] access_output_file private error: cannot open `/tmp//mt_transcode_EQAMDU' (Permission denied)
I tried doing things like changing the permissions for vlc to 'read and write' but to no avail. Help!!

---

### Post by Ardrias on 2008-06-29
I can't even get my .ogg files to show up, much less try to transcode them. Anyone got any ideas about that?

---

### Post by amak79 on 2008-06-29
Ardrias,

I suspect the reason why your Ogg files aren't showing up is that MT has assigned the wrong UPnP class to them. You can check the UPnP class via the MT interface. It should be set to "object.item.audioItem.musicTrack", but instead it's set to "object.item". This is a bug in MT that can be fixed by adding <map from="application/ogg" to="object.item.audioItem.musicTrack"/> to the <mimetype-upnpclass> section of config.xml.

However even if you did this you still would not be able to transcode them, as the current version of MT can't stream transcoded audio to the PS3. This has been fixed in the SVN version of MT.

---

### Post by amak79 on 2008-06-29
csk,

The permission denied message means the user that is running MediaTomb doesn't not have sufficient permissions to access /tmp. MediaTomb must be able to write to /tmp for transcoding to work. You need to check the permissions of /tmp, it is usually world writeable.

---

### Post by Ardrias on 2008-06-29
Alright, I've just checked out and built the latest Mediatomb. I also did the mentioned fix for the PS3 to recognize OGG files. I had tried that before, but I think I might have forgot to rescan the directories. 

Anyhow, I still cant figure out how to make it transcode OGG audio to the PS3. I've followed the Mediatomb wiki about transcoding, to transcode using VLC, but it just refuses to work. 

What am I doing wrong?

---

### Post by Keare on 2008-06-29
Just wanted to thank Dies for his config.xml, I've been playing around with this for a few weeks with very little luck, but now it is working :D

Thanks!

---

### Post by amak79 on 2008-06-29
Ardrias,

Do the Ogg files show up in your PS3 after you added the fix to the config? If you added the fix after you imported your Ogg files, then you will need to remove and re-import the Ogg files for the fix to take effect.

If you still can't get it to work, then please post your config.xml. Can you also post any useful info from the MT log file or messages printed to the console.

---

### Post by Ardrias on 2008-06-30
I'm at work now (Yes, I have time to be on forums, it's summertime :p) so cant watch the logs. The OGG files however do appear on the PS3. If I set it to transcode using oggflac2wav(?) it shows as being playable RAW Pcm, but errors on playing. 

I tried other various settings from the wiki, but nothing works. I've got vorbis-tools, ffmpeg and VLC installed, so any solution is fine by me, I just want to play my OGG music.

---

### Post by amak79 on 2008-06-30
Ardrias,

I forgot to mention that the PS3 expects the byte order of the Raw PCM stream to be big endian. If your using ogg123 then the agent tag for oggflac2raw should be: <agent command="ogg123" arguments="-d raw **-o byteorder:big** -f %out %in"/>

---

### Post by Ardrias on 2008-06-30
This is the content of my /etc/mediatomb/config.xml 

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:ff857b6b-b68a-41a7-b700-17992b00015d</udn>
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
        <!-- <map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
	<map from="application/ogg" to="object.item.audioItem.musicTrack"/>        
	<map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
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
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>
```

If I try to play an ogg file, /var/log/mediatomb.log spits out
```
2008-06-30 22:56:08    INFO: Arguments: -d raw byteorder:big -f %out %in
```
and the PS3 refuses to play it. Is it supposed to be this difficult? Cheers for helping tho amak79 :D

---

### Post by amak79 on 2008-06-30
Ardrias,

This time the error is my fault :oops:. I forgot the **-o** in front of **byteorder:big**. I've update the my previous post with the correct line. Sorry about that.

---

### Post by Ardrias on 2008-07-04
And along came firmware 2.4.... Now I cant see any files at all. This is quite ridiculous :|

---

### Post by amak79 on 2008-07-04
[QUOTE=Ardrias]And along came firmware 2.4.... Now I cant see any files at all. This is quite ridiculous :|[/QUOTE]
That is ridiculous indeed and very frustrating. Most people have reported that 2.40 fixed the transcoding issue the PS3 had with certain types of files. I've personally had no issues with 2.40. I can only suggest you try the MediaTomb IRC channel or forum for help.

---

### Post by Ardrias on 2008-07-04
Alright, I'll give that a try. Thanks for being helpful :)

---

### Post by amak79 on 2008-07-05
Ardrias,

There is an issue with the current MT SVN version which affects the PS3 2.40 firmware from seeing more than 10 items. The developers are aware of this issue and have advised SVN users to disable the new storage cache feature. You will need to add an attribute to the storage tag so it looks like this: **<storage caching="no">**. I don't know if this will solve your problem but it's worth a shot.

---

### Post by Ardrias on 2008-07-06
I just checked out the latest build, and now I can browse files just fine, without adding that tag too. Transcoding is still a no-go tho.

---

### Post by luxor on 2008-07-10
> **amak79 said:**
> Ardrias,

I forgot to mention that the PS3 expects the byte order of the Raw PCM stream to be big endian. If your using ogg123 then the agent tag for oggflac2raw should be: <agent command="ogg123" arguments="-d raw **-o byteorder:big** -f %out %in"/>

:guitar:  This piece of information was key to getting my install working after wrestling with it for about a week.  I can finally play my flac encoded music.
Thank you!!

---

### Post by SpEnTBoY on 2008-08-16
Ok I'm probably beating a dead horse but I figured I'd try here anyway :) ... do people still have this working? For some reason I just can not get flac and ogg files to transcode :(

I see the old "format not supported" and in my MT log I see the "2008-08-16 21:19:54    INFO: Arguments: -d raw -o byteorder:big -f %out %in" but nothing goes through. I have the latest firmware and the arguments look ok but for some reason I just can't get this working.

I have tried on both Kubuntu and MacOSX (running Fink deb packages for both ogg123 and ffmpeg). When I tried the ffmpeg solution it immediately went to "unrecognized format". With ogg123 it at least tries to run, even starts the visual like its about to play, and the I see the "arguments" line in my log and the format issue on my PS3.

I've verified pathes, tried writing a wrapper script ... anyone have any other ideas _or_ know of a way to get more detailed logging from MT? I realy want to get all my transcoding working!!!

I know that flv works because I tested it AND watched my poc list on my Mac to verify that ffmpeg was in fact transcoding the content. Next for video stuff is matroska files but first I need my flac and ogg stuff working :D

help? :confused: :)

---

### Post by Ardrias on 2008-08-23
> **SpEnTBoY said:**
> Ok I'm probably beating a dead horse but I figured I'd try here anyway :) ... do people still have this working? For some reason I just can not get flac and ogg files to transcode :(

I see the old "format not supported" and in my MT log I see the "2008-08-16 21:19:54    INFO: Arguments: -d raw -o byteorder:big -f %out %in" but nothing goes through. I have the latest firmware and the arguments look ok but for some reason I just can't get this working.

I have tried on both Kubuntu and MacOSX (running Fink deb packages for both ogg123 and ffmpeg). When I tried the ffmpeg solution it immediately went to "unrecognized format". With ogg123 it at least tries to run, even starts the visual like its about to play, and the I see the "arguments" line in my log and the format issue on my PS3.

I've verified pathes, tried writing a wrapper script ... anyone have any other ideas _or_ know of a way to get more detailed logging from MT? I realy want to get all my transcoding working!!!

I know that flv works because I tested it AND watched my poc list on my Mac to verify that ffmpeg was in fact transcoding the content. Next for video stuff is matroska files but first I need my flac and ogg stuff working :D

help? :confused: :)

The version in the Ubuntu repos does not work, you need to remove it and build from SVN. The mediatomb IRC channel is a great place to get help... Even tho the devs dont really love PS3 and Ubuntu ;)

---

### Post by BillyGlenn on 2008-08-31
hi,

i added a mkv profile to the config.xml and now every time when i want to start mediatomb i get a

> 
MediaTomb UPnP Server version 0.11.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2008-08-31 13:14:50    INFO: Loading configuration from: /home/stefan/.mediatomb/config.xml
2008-08-31 13:14:50    INFO: Checking configuration...
2008-08-31 13:14:50    INFO: Setting filesystem import charset to UTF-8
2008-08-31 13:14:50    INFO: Setting metadata import charset to UTF-8
2008-08-31 13:14:50    INFO: Setting playlist charset to UTF-8
2008-08-31 13:14:50   ERROR: error in configuration, transcoding profile ffmpeg: transcoder /usr/local/bin/mkv2mpegis not executable - Permission denied


how can i change the permission?

config.xml

> <?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:af3b4fc7-3b4a-4b3f-b685-db7f02138484</udn>
    <home>/home/stefan/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->
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
	<map from="mkv" to="video/x-matroska"/>
        <!-- Uncomment the line below for PS3 divx support -->
        <!-- <map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
      </mimetype-contenttype>
    </mappings>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
	<transcode mimetype="video/x-matroska" using="ffmpeg"/>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
<profile name="ffmpeg" enabled="yes" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<hide-original-resource>yes</hide-original-resource>
<agent command="/usr/local/bin/mkv2mpeg" arguments="%in %out"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
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
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>

---

### Post by fej40 on 2008-09-06
BillyGlenn try this: sudo chmod uo+x /usr/local/bin/mkv2mpeg

But can you share your mkv2mpeg file?

---

### Post by ahaslam on 2008-09-20
Deleted - was attempting the impossible...

---

### Post by tkarkache on 2008-12-05
It does work. Just the stock ubuntu ffmpeg is compiled with the needed libraries. Need to download from svn and get wanted encoder libraries.

---

### Post by Memes11 on 2009-01-26
May you explain a bit more?

Which library are you talking about? I am struggling to encode rmvb on the fly (I'll do the mkv after as I have less of them), and I am also facing the problem of :Which vcodec I have to put???

Thanks

---

