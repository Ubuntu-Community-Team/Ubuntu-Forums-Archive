---
title: "transcoding-on-the-fly"
date: 2009-10-13
forum: Multimedia Software
---

### Post by Msingh on 2009-10-13
I'm trying to transcode mkv's to my ps3 I've tried so many things, I couldn't get the ps3 media server to work, I tried running tversity in vmware, and I tried fuppes, nothing has worked so far. Now, on to my problems, every time I try to transcode something the ps3 just says its either unsupported or corrupted.

Here is my config:
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
    <udn>uuid:aa8ba7dd-5533-4ec1-b32c-b3b807677f9a</udn>
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
    <extension-mimetype ignore-unknown="yes">
    <map from="mp3" to="audio/mpeg"/>
    <map from="ogg" to="application/ogg"/>
    <map from="ogv" to="video/oggtheora"/>
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
    <map from="avi" to="video/x-divx"/>
    <map from="divx" to="video/x-divx"/>
    <map from="mkv" to="video/x-matroska"/>
    <map from="mov" to="video/quicktime"/>
    <map from="qt" to="video/quicktime"/>
    <map from="mpg" to="video/mpeg"/>
    <map from="mpeg" to="video/mpeg"/>
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
    <treat mimetype="video/mp4" as="mp4"/>
    <treat mimetype="audio/mp4" as="mp4"/>
    <treat mimetype="video/x-divx" as="avi"/>
    </mimetype-contenttype>
    </mappings>
    </import>
    <transcoding enabled="yes">
    <mimetype-profile-mappings>
    <transcode mimetype="video/x-flv" using="vlcmpeg"/>
    <transcode mimetype="application/ogg" using="vlcmpeg"/>
    <transcode mimetype="application/ogg" using="oggflac2raw"/>
    <transcode mimetype="audio/x-flac" using="audio-common"/>
    <transcode mimetype="video/x-divx" using="video-thumbnail"/>
    <transcode mimetype="video/x-matroska" using="video-common"/>
    <transcode mimetype="video/quicktime" using="video-common"/>
    <transcode mimetype="video/oggtheora" using="video-common"/>
    </mimetype-profile-mappings>
    <profiles>
    <profile name="oggflac2raw" enabled="yes" type="external">
    <mimetype>audio/L16</mimetype>
    <accept-url>no</accept-url>
    <first-resource>yes</first-resource>
    <accept-ogg-theora>no</accept-ogg-theora>
    <agent command="ogg123" arguments="-d raw -f %out %in"/>
    <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
    </profile>

    <profile name="vlcmpeg" enabled="yes" type="external">
    <mimetype>video/mpeg</mimetype>
    <accept-url>yes</accept-url>
    <first-resource>yes</first-resource>
    <accept-ogg-theora>yes</accept-ogg-theora>
    <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
    <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
    </profile>

    <profile name="video-thumbnail" enabled="yes" type="external">
    <mimetype>image/jpeg</mimetype>
    <accept-url>yes</accept-url>
    <thumbnail>yes</thumbnail>
    <resolution>128x128</resolution>
    <agent command="ffmpegthumbnailer" arguments="-i %in -o %out -s 128"/>
    <buffer size="524288" chunk-size="512" fill-size="1024"/>
    </profile>

    <profile name="audio-common" enabled="yes" type="external">
    <mimetype>audio/x-wav</mimetype>
    <accept-url>yes</accept-url>
    <first-resource>yes</first-resource>
    <accept-ogg-theora>no</accept-ogg-theora>
    <agent command="/etc/mediatomb/mediatomb-transcode-audio" arguments="%in %out"/>
    <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
    </profile>

    <profile name="video-common" enabled="yes" type="external">
    <mimetype>video/mpeg</mimetype>
    <accept-url>yes</accept-url>
    <first-resource>yes</first-resource>
    <accept-ogg-theora>yes</accept-ogg-theora>
    <agent command="/etc/mediatomb/mediatomb-transcode-video-ffmpeg" arguments="%in %out"/>
    <buffer size="52428800" chunk-size="524288" fill-size="1048576"/>
    <!-- <buffer size="26214400" chunk-size="524288" fill-size="1048576"/> -->
    <!-- <buffer size="14400000" chunk-size="512000" fill-size="120000"/> -->
    </profile>

    <profile name="ffmpeg" enabled="yes" type="external">
    <mimetype>video/mpeg</mimetype>
    <accept-url>no</accept-url>
    <first-resource>yes</first-resource>
    <hide-original-resource>yes</hide-original-resource>
    <agent command="/usr/local/bin/mkv2mpeg" arguments="%in %out"/>
    <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
    </profile>
    </profiles>
    </transcoding>
    </config>
```

can't figure anything out. I can explore the server, and view all files the ps3 supports, and I want to be able to watch mkv's.

Also, mediatomb is 0.11.0

---

### Post by Msingh on 2009-10-13
bump, can anyone help please? I am willing to try other methods, it doesn't have to be mediatomb, I will try any methods that have worked for anyone here.

---

### Post by Msingh on 2009-10-13
can someone help me here?

---

### Post by Msingh on 2009-10-14
this is just ridiculous, I really need help, is there any other way to do this? PLEASE HELP

---

### Post by MrWES on 2009-10-14
> **Msingh said:**
> this is just ridiculous, I really need help, is there any other way to do this? PLEASE HELP

Personally, I don't transcode mkv files, and unless you have a top notch system -- they're going to be choppy, at best.

There are two ways around it. PS3's will play either vob or m2ts files via mediatomb without issue.

1.) Install Wine and Mkv2vob. Works like a charm and is very fast in remuxing mkv to vob; you can either transcode the DTS source, or if your AV receiver has DTS you can maintain that.
[http://www.videohelp.com/tools/mkv2vob]("http://www.videohelp.com/tools/mkv2vob")

2.) Install the necessary tools to run either mkv2mp4 or the mkv2m2ts scripts located at this site. 
[http://blog.flexion.org/index.php/2009/08/27/mkv-to-mp4-conversion-script/]("http://blog.flexion.org/index.php/2009/08/27/mkv-to-mp4-conversion-script/")

I think you'll be happy with the quality with either method. I currently run the mkv2vob in Wine, but if you don't want the overhead of the Wine install run the scripts from the command line.

~Bill


P.S. It's a general rule not to bump less than 24 hours, and multiple bumps tends to turn people off.

---

### Post by Msingh on 2009-10-14
oh wasn't really sure about that other forums I usually end up getting responses really quick, but thanks, it worked!

---

### Post by MrWES on 2009-10-14
> **Msingh said:**
> oh wasn't really sure about that other forums I usually end up getting responses really quick, but thanks, it worked!

Which method did you end up using?

This forum is generally pretty speedy too, but this wasn't along the lines of a 'common' question; not everyone owns a PS3 :)

Bill

---

