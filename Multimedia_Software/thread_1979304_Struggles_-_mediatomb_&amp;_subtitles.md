---
title: "Struggles - mediatomb &amp; subtitles"
date: 2012-05-13
forum: Multimedia Software
---

### Post by yashoda on 2012-05-13
Hi, after quite a journey, I've managed to get Mediatomb to work, between my ubuntu computer and samsung tv.  however, no matter what i've tried, I can't get subtitles to work.  I would appreciate any help in this regard.  Please find my config.xml below.

<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd">
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
    <udn>uuid:5b01f9aa-ac0e-4ba1-b07d-85a46594f54c</udn>
    <home>/home/yashik/.mediatomb</home>
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
     <custom-http-headers>
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=017000 00000000000000000000000000"/>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
   
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="no">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
        <image-quality>8</image-quality>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
        <mark>
          <content>video</content>
        </mark>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <virtual-layout type="builtin"/>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogx" to="application/ogg"/>
        <map from="ogv" to="video/ogg"/>
        <map from="oga" to="audio/ogg"/>
        <map from="ogg" to="audio/ogg"/>
        <map from="ogm" to="video/ogg"/>
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
    	<map from="mkv" to="video/mpeg"/>
        <map from="mka" to="audio/x-matroska"/>
        <map from="avi" to="video/divx"/>
	<map from="avi" to="video/mpeg"/>
	<map from="srt" to="video/subtitle"/>

        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
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
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/x-matroska" as="mkv"/>
        <treat mimetype="audio/x-matroska" as="mka"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="mp4" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
    </online-content>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
	<transcode mimetype="video/subtitle" using="mencoder-srt"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
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
<agent command="/usr/local/bin/mediatomb-mencoder-srt" arguments="%in %out"/>
    </profiles>
  </transcoding>
</config>

---

### Post by yashoda on 2012-05-23
Hi,

since I've had no replies, I thought to add some info.

I have had considerable more luck with the ps3 media server.  I hadn't tried it initially, cos I foolishly thought it was only for people with ps3s! 

But it has been a breeze to setup, and quite intuitive to run compared to Mediatomb, ushare, rygel, etc.  

The only app that was easier is tvmobili, which is unfortunately a subscription service if you stream more than 10GB per month.

---

