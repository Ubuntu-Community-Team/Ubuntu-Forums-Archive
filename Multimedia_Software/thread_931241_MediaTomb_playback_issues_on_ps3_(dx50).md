---
title: "MediaTomb playback issues on ps3 (dx50)"
date: 2008-09-27
forum: Multimedia Software
---

### Post by sexyclient on 2008-09-27
OK, so I finally managed to finish setting up my ps3 to accept my divx files, but now I've got another problem.  I have a few (.avi) videos that are (according to vlc) encoded in "DX50" video codec.  I tried to mess around with some configs, but I didn't get anything to play.  Once I load the files in my ps3, I see a "divx" logo in the lower right-hand corner, but nothing plays.  Here's my config.xml file looks like now:

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
    <udn>uuid:0405d323-b146-4dc6-9285-2eb1d269f206</udn>
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
    </mimetype-profile-mappings>
    <profiles>
      <!-- This junk I added -->
      <profile name="video-common" enabled="yes" type="external">
        <avi-fourcc-list mode="ignore">
          <fourcc>DX50</fourcc>
        </avi-fourcc-list>
      </profile>
      <!-- Emd of my junk -->
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
```

Can anyone help me to get these files to play?  It's like 3am here right now, and I've given it all I've got at the moment...

---

### Post by Shininggg on 2008-09-27
googling around...
[http://thefunkcorner.blogspot.com/2008/08/playstation-3-streaming-formats-ick.html]("http://thefunkcorner.blogspot.com/2008/08/playstation-3-streaming-formats-ick.html")

if you want full compatibility just install linux on your ps3 (see yellow dog or psubuntu)

---

### Post by sexyclient on 2008-09-28
Thanks, but installing linux on my ps3 isn't a very practical solution.  I just want to play a few HD (720p) movies encoded in the dx50 codec that are housed in the avi container.  I don't have the HD space, time, nor resources (not to mention a general necessity or desire) to install linux on my ps3 - I have a computer for computing.  I just need my ps3 to play files that are stored remotely on my local network, and served by mediatomb.  I'm planning on getting a WD Mybook 1TB NAS to use as my mediatomb server because it's capable of doing so, and I'd like to iron out all the kinks on my desktop before I make the switch to the big leagues.

---

### Post by sexyclient on 2008-09-28
*bump

---

### Post by sexyclient on 2008-09-30
*double-bump

---

### Post by rustutzman on 2008-10-01
It sounds like you're going to have to enable transcoding. I haven't been able to play any avi's without it on my PS3. I have it working somewhat. I'll post the relevant sections of my config.xml when I'm at my home pc this afternoon.

Russ

---

### Post by sexyclient on 2008-10-02
Russ, my man, you rule!

---

