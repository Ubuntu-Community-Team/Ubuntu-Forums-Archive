---
title: "Mediatomb and Subtitles"
date: 2010-01-20
forum: Multimedia Software
---

### Post by Spacecowboy2005 on 2010-01-20
Hi i've looked at serveral post all over the net but still can't get subtitles (.str files) to bind with the stream on mediatomb.

Mediatomb works fine with out the subtitle transcoding profile, but when added and mediatomb is restarted using **sudo /etc/init.d/mediatomb restart **I get the response "Fail" and Mediatomb will not start. If I change **<transcoding enabled="yes">** to "no" then mediatomb works fine

Below is my config.xml


> 
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:bc6ea4a4-9bcc-465d-b44e-74817cd484ac</udn>
    <home>/var/lib/mediatomb</home>
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
     <extended-runtime-options>
      <ffmpegthumbnailer enabled="yes">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
        <dvd-script>/usr/share/mediatomb/js/import-dvd.js</dvd-script>
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
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/divx" as="avi"/>
      </mimetype-contenttype>
    </mappings>
      </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="application/ogg" using="video-common"/>
      <transcode mimetype="video/divx" using="video-common" />
      <transcode mimetype="video/x-divx" using="video-common" />
    </mimetype-profile-mappings>
<profiles>          
 <profile name="video-common" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/usr/bin/mediatomb-transcode-video" arguments="%in %out"/>
        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile>
    </profiles>
  </transcoding>
</config>


---

### Post by blaze7810 on 2011-06-03
have the same problem any help please

---

### Post by negatifo on 2012-10-01
Hello Folks

I have the same issue. After I enable transcoding Mediatomb fails to start.

---

