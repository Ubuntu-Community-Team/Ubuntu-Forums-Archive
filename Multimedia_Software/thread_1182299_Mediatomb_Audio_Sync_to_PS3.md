---
title: "Mediatomb Audio Sync to PS3"
date: 2009-06-08
forum: Multimedia Software
---

### Post by kaboosh on 2009-06-08
Hey

I'm having some trouble getting my audio sync'd when streaming to my PS3. I've searched high and low for a solution and just can't seem t get it sync'd. Oh, this is on video/x-msvideo files specifically, other file types seem to be ok.

I'm on Intrepid 64bit

Config.xml as per below;

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:85223379-1a82-4470-b750-b8b91cc4f227</udn>
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
        <map from="ts" to="video/mpeg"/>
        <map from="vob" to="video/mpeg"/>
        <map from="wav" to="audio/wav"/>
        <map from="mpg" to="video/mpeg"/>
        <map from="aac" to="audio/x-aac"/>
        <map from="m4a" to="audio/mp4"/>
           <map from="mkv" to="video/x-matroska"/>
        <map from="mov" to="video/x-quicktime"/>
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
        <map from="x-msvideo" to="video/divx"/>
        <map from="divx" to="video/x-divx"/>
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
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
     <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
      <transcode mimetype="video/x-divx" using="video-common"/>
      <transcode mimetype="video/divx" using="vlcmpeg"/>
      <transcode mimetype="video/x-msvideo" using="vlcmpeg"/>
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
      <profile name="vlcmpeg" enabled="yes" type="external">
      <avi-fourcc-list mode="ignore">
        <fourcc>DIVX</fourcc>
        <fourcc>DX50</fourcc>
        <fourcc>DM4V</fourcc>
        <fourcc>M4S2</fourcc>
      </avi-fourcc-list>
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

---

