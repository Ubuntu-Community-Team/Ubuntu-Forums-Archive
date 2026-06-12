---
title: "Samsung TV with mediatomb DLNA server for Sopcast LiveTV..."
date: 2011-04-11
forum: Multimedia Software
---

### Post by Markus72 on 2011-04-11
Dear all,

now I read a lot and tried even more but I didn't find a solution.

I use Mediatomb 0.12.1 with Kubuntu 10.10, 64 Bit and my Samsung UE46C7700 with firmware 2011/01/06_003006.

What works perfectly is to stream MPEG films directly from file but what does not is to stream Sopcast with transcoding.

Ok, I've got Sopcast running, I can stream it with Mediatomb and it works perfectly fine with VLC as client as well as with my PS3 as streaming client.

But of course I would like to stream it directly to my Samsung.

Mediatomb server is visible and I also don't get any "inknown file format"-like error. Instead of this, the TV seems to buffer data which I at least can deduce from the mediatomb output.
But finally, after about 30 seconds, it just returns to the content directory just as if I hadn't started playback at all - without any message.

I have no idea what's happening - do you?


Thx
Markus

PS: please find my Mediatomb config attached

```

<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd\"><!--
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
<udn>uuid:0170e7d7-4e49-48f6-97d6-673093d96ee8</udn>
<home>/home/mark/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
<storage>
<sqlite3 enabled="yes">
<database-file>mediatomb.db</database-file>
</sqlite3>
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>lavcresample
</mysql>
</storage>
<protocolInfo extend="yes"/>
<!--
Uncomment the lines below to get rid of jerky avi playback on the
DSM320 or to enable subtitles support on the DSM units
-->
<custom-http-headers>
<!-- Samsung needs it -->
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01500000000000000000000000000000"/>
</custom-http-headers>


<manufacturerURL>redsonic.com</manufacturerURL>
<modelNumber>105</modelNumber>
<extended-runtime-options>
<ffmpegthumbnailer enabled="no">
<thumbnail-size>128</thumbnail-size>
<seek-percentage>5</seek-percentage>
<filmstrip-overlay>yes</filmstrip-overlay>
<workaround-bugs>no</workaround-bugs>
</ffmpegthumbnailer>
<mark-played-items enabled="no" suppress-cds-updates="yes">
<string mode="prepend">*</string>
</mark-played-items>
</extended-runtime-options></server>
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
<map from="mkv" to="video/x-matroska"/>
<map from="mka" to="audio/x-matroska"/>
<map from="mpg" to="video/mpeg"/>
<map from="m2v" to="video/mpeg"/>
<map from="gif" to="image/gif"/>
<map from="jpg" to="image/jpeg"/>
<map from="png" to="image/png"/>
<map from="mkv" to="video/x-matroska"/>
<map from="mts" to="video/mpeg"/>
<map from="ts" to="video/mpeg"/>
<map from="m2ts" to="video/mpeg"/>
<map from="mov" to="video/x-quicktime"/>
<map from="vob" to="video/mpeg"/>
<map from="m4v" to="video/mp4"/>
<map from="avi" to="video/divx"/><!-- Uncomment the line below for PS3 divx support --><!-- <map from="avi" to="video/divx"/> --><!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 --><!-- <map from="avi" to="video/avi"/> -->
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
<treat mimetype="video/x-mkv" as="mkv"/>
<treat mimetype="audio/mp4" as="mp4"/>
<treat mimetype="application/x-iso9660" as="dvd"/>
<treat mimetype="application/x-iso9660-image" as="dvd"/>
<treat mimetype="video/quicktime" as="mov"/>
<treat mimetype="video/x-quicktime" as="mov"/>
</mimetype-contenttype>
</mappings>
<online-content><!-- Make sure to setup a transcoding profile for flv -->
<YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
<favorites user="mediatomb"/>
<standardfeed feed="most_viewed" time-range="today"/>
<playlists user="mediatomb"/>
<uploads user="mediatomb"/>
<standardfeed feed="recently_featured" time-range="today"/>
</YouTube>
<Weborama enabled="no" refresh="28800" update-at-start="no">
<playlist name="Active" type="playlist" mood="active"/>
<playlist name="Metal" type="playlist">
<filter>
<genres>metal</genres>
</filter>
</playlist>
</Weborama>
<AppleTrailers enabled="yes" refresh="43200" update-at-start="no" resolution="640"/>
<SopCast enabled="yes" refresh="43200" purge-after="50000" update-at-start="yes"/>
</online-content>
</import>
<transcoding enabled="yes">
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="mencodermpeg"/>
<transcode mimetype="application/ogg" using="mencodermpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="oggflac2raw"/>
<transcode mimetype="application/ogg" using="audio-generic"/>
<transcode mimetype="audio/x-flac" using="audio-generic"/>
<transcode mimetype="video/x-ms-asf" using="video-generic"/>
<transcode mimetype="video/x-flv" using="video-generic"/>
<transcode mimetype="video/x-matroska" using="video-generic"/>
<transcode mimetype="video/x-quicktime" using="video-generic"/>
<transcode mimetype="video/quicktime" using="video-generic"/>
<transcode mimetype="video/sopcast-x-ms-wmv" using="mencodermpeg"/>
</mimetype-profile-mappings>
<profiles>
<profile name="audio-generic" enabled="yes" type="external">
<mimetype>audio/L16</mimetype>
<first-resource>yes</first-resource>
<accept-url>yes</accept-url>
<sample-frequency>44100</sample-frequency>
<audio-channels>2</audio-channels>
<hide-original-resource>yes</hide-original-resource>
<agent command="ffmpeg" arguments="-ac 2 -ar 44100 -y -i %in -f s16be %out"/>
<buffer size="1048576" chunk-size="4096" fill-size="1024"/>
</profile>
<profile name="video-generic" enabled="yes" type="external">
<avi-fourcc-list mode="ignore">
<fourcc>DX50</fourcc>
<fourcc>DM4V</fourcc>
<fourcc>M4S2</fourcc>
</avi-fourcc-list>
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<hide-original-resource>yes</hide-original-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="/usr/local/bin/mediatomb-video-generic" arguments="%in %out"/>
<buffer size="1048576" chunk-size="26214" fill-size="52428"/>
</profile>
<profile name="oggflac2raw" enabled="yes" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="mencodermpeg" enabled="yes" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="mencoder" arguments="%in -oac lavc -ovc lavc -fps 25 -srate 48000 -af lavcresample=48000 -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=9800:vrc_buf_size=1835 -mpegopts muxrate=12000 -vf harddup -o %out"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>

</profiles>
</transcoding>
</config>

```

---

### Post by Markus72 on 2011-04-12
was confused somehow and mixed it up with some other changes I made.
The following works:

```
<custom-http-headers>
<add header="transferMode.dlna.org: Streaming"/>
<add header="contentFeatures.dlna.org: DLNA.ORG_OP=00"/>
</custom-http-headers>
```

---

