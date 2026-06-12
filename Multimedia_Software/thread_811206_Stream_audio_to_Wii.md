---
title: "Stream audio to Wii?"
date: 2008-05-28
forum: Multimedia Software
---

### Post by heartburnkid on 2008-05-28
Hi all.  I'm trying to stream audio from Ubuntu to my Wii, and so far, not having much luck.  I'm trying to use Mediatomb to transcode (since Nintendo, for some reason, decided not to support MP3), but I just can't seem to get transcoding to work; the Wii keeps returning "audio/mpeg not supported", and when I try to access it on a computer browser, it wants to download an MP3.  I've attempted to set up Mediatomb as seen [here](http://gentoo-wiki.com/HOWTO_MediaTomb#Transcoding_Support), using first vlc, then ffmpeg, adding in the line ```
 <transcode mimetype="audio/mpeg" using="audio-common"/> 
``` under <mimetype-profile-mappings>, and it seems to be a no-go.  Running mediatomb in a terminal doesn't return any error messages; it's like it's not even trying to transcode.

Here is my full Mediatomb config.xml:
```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <protocolInfo extend="yes"/>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:17881b11-0f69-4ad7-a0d1-837797389f32</udn>
    <home>/home/calden/.mediatomb</home>
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
        <map from="avi" to="video/x-divx"/>
        <map from="divx" to="video/x-divx"/>
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
      <transcode mimetype="application/ogg" using="audio-common"/>
      <transcode mimetype="application/ogg" using="video-common"/>
      <transcode mimetype="audio/mpeg" using="audio-common"/>
      <transcode mimetype="audio/x-flac" using="audio-common"/>
      <transcode mimetype="video/x-flv" using="video-common"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="audio-common" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="mediatomb-transcode-audio" arguments="%in %out"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="video-common" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mediatomb-transcode-video" arguments="%in %out"/>
        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile>
    </profiles>
  </transcoding>

</config>
```

Can anybody help me set this up?

---

### Post by heartburnkid on 2008-05-30
Does anybody have Wii streaming set up?  I've found ways to set it up using TVersity on Windows, but TVersity doesn't seem to play well with Wine...

---

### Post by amak79 on 2008-05-30
heartburnkid,

If you take a look at the audio-common transcoding profile it will produce a raw PCM audio stream. The Wii must support raw PCM otherwise it will not be able to play the stream. What kind of audio formats does the Wii support? You might to take a look at TVersity and see which audio format they are using and then you can make adjustments to your setup accordingly. Since when did the Wii start supporting UPnP?

I have noticed that you have <protocolInfo extend="yes"/> in your config.xml, that is PS3 specific and should not be enabled. If you see "INFO: Arguments: %in %out" being printed to the terminal or log file, that should indicate then transcoding is enabled for the file your attempting to access. If your trying to access the file through a web browser it will result in a download which is normal.

---

### Post by heartburnkid on 2008-05-31
The Wii doesn't support UPnP; I am trying to use the web interface from the Wii.  I guess that's my problem.

Is there anything that can transcode through a web UI, or uses a Flash or Java player?  As I understand it, TVersity uses a Flash player, which would be why it works.

---

### Post by amak79 on 2008-05-31
Trying to use MediaTomb as you describe will not be possible as transcoding is only offered via UPnP and not the web interface. You should try [Wii Media Center X]("http://www.redkawa.com/mediacenters/wiimediacenterx/") which is a Java based Flash client thats allows you to stream media to your Wii and is supported on Linux.

---

### Post by heartburnkid on 2008-06-01
Thanks for the link... unfortunately, the program's in such an alpha state as to be nearly useless without massive reorganizing of my MP3 collection, and it's apparently discontinued, so it's not going anywhere from here.
*sigh*...

---

### Post by amak79 on 2008-06-01
You could try [Orb]("http://orb.com/en") which is a media streamer that runs on Windows. It is actively developed and supports all the consoles including devices such as PDAs. I have also found a nice [guide]("http://www.lifehacker.com.au/tips/2008/02/20/use_your_wii_as_a_media_center-2.html") for setting it up.

---

