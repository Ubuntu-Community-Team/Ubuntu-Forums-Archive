---
title: "Mediatomb on Gutsy - PS3 cannot detect"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by mulerobba on 2008-02-05
Installed Mdiatomb on Gutsy Server Edition using the Feisty package.
Been able to get mediatomb running.  All 3 Windows based PCs (XP and Vista) can detect the mediatomb service but PS3 does not detect any mediatomb server.

PS3 can detect WMP server from one of the PCs and I am stumped.

Having gone through mediatomb instructions and various forums, I still have had no luck.

My setup:

Server connected to LAN side of D-link router with DD-wrt firmware. PS3 connected to client bridged linksys WRT54G router also with DD-wrt firmware.  Both routers have UPnP enabled.

I have tried connecting the PS3 through wireless to the main D-Link router bypassing the bridge but still canot get the PS3 to find the mediatomb service.

In all cases, I have ben able to ping the PS3 from the Gutsy server.

I am not sure if the problem is :
1. Related to the mediatomb installation - I doubt this because Windows Pcs on either side of the bridge can see mediatomb.
2. Related to the Network configuration
3. Related to the mediatomb PS3 interface.
4. Related to te PS3 inernet connectivity - I doubt this also because I get on the internet with the PS3 from either side of he bridge.

If any one has run into this sort of problem can you please help

---

### Post by happymellon on 2008-03-09
Did you change the properties in the ~/.mediatomb/config.xml ?

You need to edit it and add the following tag.

<protocolInfo extend="yes"/>

ALTHOUGH I found it already in there, but set to no so I changed it to yes and that made the PS3 detect it.

A question for anyone else, I can get the PS3 to see it but all my MP3's are set as unsupported data types. Any ideas?

---

### Post by specvthis on 2008-03-09
> <?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>Mark's Stuff</name>
    <udn>uuid:6bd8221e-73ab-4dc3-8b1c-b940fff07947</udn>
    <home>/home/specvthis/.mediatomb</home>
    <webroot>/usr/local/share/mediatomb/web</webroot>
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
      <common-script>/usr/local/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/local/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/local/share/mediatomb/js/import.js</import-script>
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
	<map from="vob" to="video/mpeg"/>
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
  <transcoding enabled="no">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
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

That is what your ~/.mediatomb/config.xml file should look like.  That should fix your problems.   I added the line for vob so that the ps3 can play vob files...

---

### Post by happymellon on 2008-03-10
> **specvthis said:**
> That is what your ~/.mediatomb/config.xml file should look like.  That should fix your problems.   I added the line for vob so that the ps3 can play vob files...

I think that is what I wrote, but I noticed that was wrong for myself. I am starting it as a daemon and after tailing my /var/log/mediatomb.log I noticed this:

INFO: Loading configuration from: /etc/mediatomb/config.xml

So I'm going to try updating that instead.

Cheers though.

---

### Post by nuclearj on 2008-06-24
> **mulerobba said:**
> Installed Mdiatomb on Gutsy Server Edition using the Feisty package.
Been able to get mediatomb running.  All 3 Windows based PCs (XP and Vista) can detect the mediatomb service but PS3 does not detect any mediatomb server.

PS3 can detect WMP server from one of the PCs and I am stumped.

Having gone through mediatomb instructions and various forums, I still have had no luck.

My setup:

Server connected to LAN side of D-link router with DD-wrt firmware. PS3 connected to client bridged linksys WRT54G router also with DD-wrt firmware.  Both routers have UPnP enabled.

I have tried connecting the PS3 through wireless to the main D-Link router bypassing the bridge but still canot get the PS3 to find the mediatomb service.

In all cases, I have ben able to ping the PS3 from the Gutsy server.

I am not sure if the problem is :
1. Related to the mediatomb installation - I doubt this because Windows Pcs on either side of the bridge can see mediatomb.
2. Related to the Network configuration
3. Related to the mediatomb PS3 interface.
4. Related to te PS3 inernet connectivity - I doubt this also because I get on the internet with the PS3 from either side of he bridge.

If any one has run into this sort of problem can you please help

I have this same problem and can't for the life of me figure it out!  I did put the protocolinfo line in and it still did not work.  Any ideas?

---

### Post by happymellon on 2008-07-01
> **nuclearj said:**
> I have this same problem and can't for the life of me figure it out!  I did put the protocolinfo line in and it still did not work.  Any ideas?

Did you try both locations for the protocol info? I found that the /etc/mediatomb/config.xml was the one I was using. What does your /var/log/mediatomb.log say when you start it up?

Personally I've given up on the PS3 as a media player. Each update that Sony does only seems to make the playback worse, to the point that now, no matter what I do, I can't get it to play back from any external source without throwing errors. Gone back to my XBMC Xbox.

---

