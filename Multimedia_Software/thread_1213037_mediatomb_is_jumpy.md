---
title: "mediatomb is jumpy"
date: 2009-07-14
forum: Multimedia Software
---

### Post by dopple on 2009-07-14
Hi all. Media tomb is a bit jumpy when streaming avi vids to my ps3. It was a lot worse until I changed the buffer fill size to 0 (you can see the commented out original lines above the current lines in the config.xml file below.)

Can anyone tell me by how much I shold increase the chunk and buffer size to fix this?

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
    <udn>uuid:732ff820-500f-4144-8cfa-c79901b8593b</udn>
    <home>/home/graham/.mediatomb</home>
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
    <protocolInfo extend="yes"/>
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
<map from="vob" to="video/mpeg"/>
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
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
      <transcode mimetype="video/x-msvideo" using="vlcmpeg"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -f %out %in"/>
        <!--<buffer size="1048576" chunk-size="131072" fill-size="262144"/>-->
        <buffer size="1048576" chunk-size="131072" fill-size="0"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <!--<buffer size="14400000" chunk-size="512000" fill-size="120000"/>-->
        <buffer size="14400000" chunk-size="512000" fill-size="0"/>
      </profile>
    </profiles>
  </transcoding>
</config>

```

---

### Post by dopple on 2009-07-14
Actually, it isn't any better. it's just the same.

---

### Post by tgalati4 on 2009-07-14
Probably wireless interference.

---

### Post by dopple on 2009-07-15
Is there a gui that will show traffic streamed by mediatomb so that I can check? Both my laptop and ps3 are on static ip addresses, so perhaps a network monitor showing traffic from one machine to another?

---

### Post by dopple on 2009-07-16
From what I can see the audio is cutting out, then the video stops. It's almost as if the video is only stopping to allow the audio to catch up. Can anyone please post the lines from their transcoding section from their config.xml file so I can maybe see some other configurations?

---

### Post by dopple on 2010-03-13
Sorry for digging up an old post but I thought I'd post my recent findings for this issue. Check post [http://ubuntuforums.org/showthread.php?t=1428112](http://ubuntuforums.org/showthread.php?t=1428112). Although it relates to an xbox 360 it's the same issue and now seems to be solved so I'm marking this as solved too.

---

### Post by forgewire on 2011-11-28
My PS3 has ****** wifi card. I had jumpy video untill I repositoned router untill I'd got a good reception. It is smooth and nice now

---

