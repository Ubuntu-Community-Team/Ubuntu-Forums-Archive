---
title: "Mediatomb sync issues"
date: 2008-09-20
forum: Multimedia Software
---

### Post by enigma8706 on 2008-09-20
For some reason, my ubuntu server setup with mediatomb is having sync issues I installed ffmpeg and mediatomb both recently through the repos. It's transcoding all of the avi's currently to my PS3. What could be the problem for my syncing issues? Here's my config just in case:

```

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>Media Center</name>
    <udn>uuid:9bbeb414-9aa8-45e7-a03c-98a5ee70c516</udn>
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
<!--      <avi-fourcc-list mode="ignore"> -->
<!--      <fourcc>DX50</fourcc> -->
<!--    </avi-fourcc-list> -->

        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=24,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>

    </profiles>

  </transcoding>


</config>

```

Also the <avi-fourcc-list> is detecting the wrong files, that's why I commented it out of the config. It's only detecting very few of the videos that PS3 should be able to natively play without transcoding. Thanks for reading guys :) Hopefully someone has already gone through this and can lend a helping hand. Thanks again!

---

### Post by theluddite on 2009-04-04
I'd be interested in an answer for this too.  I'm using mediatomb for a D-link DSM-750 and the audio lags on almost every file I've played recently.  Anyone?

---

### Post by Gunder_ on 2009-04-08
```
<agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,acodec=mpga,ab=192,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>

```

Change the arguments like I've done. This let's the program sort out the right sampelrate for the sound on it's own, so you don't force it into something other than the source file.

But I have another problem, even if I have this in my config.xml:

```

      <avi-fourcc-list mode="ignore">
        <fourcc>DIVX</fourcc>
        <fourcc>DX50</fourcc>
        <fourcc>DM4V</fourcc>
        <fourcc>M4S2</fourcc>
      </avi-fourcc-list>

```

Mediatomb still transcodes "new" avi files, not a big problem, but then I can't pause the movies.

---

### Post by theluddite on 2009-04-10
> **Gunder_ said:**
> 
Change the arguments like I've done. This let's the program sort out the right sampelrate for the sound on it's own, so you don't force it into something other than the source file.


I figured out that it's really only .avi files that aren't synced buy my wireless media player should play them without being transcoded.  As a workaround I'm transcoding .avi files to .mpg with ffpeg.  This is less than ideal because of the picture quality so I'm still trying to find a better solution ...

---

