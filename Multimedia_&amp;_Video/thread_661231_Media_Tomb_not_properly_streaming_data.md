---
title: "Media Tomb not properly streaming data"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by somuchfortheafter on 2008-01-07
I have been using Ubuntu 7.10 for a while to display media over dvi to my hdtv with mythtv. I recently purchased a ps3 and decided to install mediatomb to stream the files so that the ps3 interface can access them. I first edited the config.xml file and then imported all of my media. the files can be played locally on the machine with no problem so config should not be an issue, but my mp3s, divx movies, and even avi movies do not work on the ps3 what could be the problem.

```

<?xml version="1.0" encoding="UTF-8"?>
<config xmlns="http://mediatomb.cc/0.10.0/config" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/0.10.0/config http://mediatomb.cc/0.10.0/config.xsd">
  <server>
    <protocolInfo extend="yes"/>
	<ui enabled="yes">
      <accounts enabled="no" session-timeout="30"/>
    </ui>
    <name>MediaTomb</name>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage driver="sqlite3">
      <database-file>sqlite3.db</database-file>
    </storage>
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
	<map from="avi" to="video/avi"/>
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
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
      </mimetype-contenttype>
    </mappings>
  </import>
</config>

```

---

### Post by ubtpenguin on 2008-01-21
You need to add this line on your server section 

<protocolInfo extend="yes"/>

Hope this helps you 

Good luck 
:lolflag:

---

