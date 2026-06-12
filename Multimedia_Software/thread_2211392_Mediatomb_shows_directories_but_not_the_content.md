---
title: "Mediatomb shows directories but not the content"
date: 2014-03-15
forum: Multimedia Software
---

### Post by uwe-bungto on 2014-03-15
I have been tiring to get mediatomb work without much luck.
I have a D-link dns321 & mediatomb running as DNLA servers, The TV I am using a sharp which can connect to the D-link or mediatomb servers. I can play videos from the D-link how ever the mediatomb server only shows the directory structure and no content. If I can get it to work I will need transcoding to work also since the Sharp can only handle AVI and MPEG file
Here is the config file AM I missing something.

```

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
    <udn>uuid:277202e5-5343-42f1-9ca2-0c49e67a4836</udn>
    <home>/home/jpb/.mediatomb</home>
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
        <map from="mkv" to="video/x-matroska"/>
        <map from="mka" to="audio/x-matroska"/>
        <!-- Uncomment the line below for PS3 divx support -->
        <!-- <map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <map from="avi" to="video/avi"/>
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
    </profiles>
  </transcoding>
</config>
```

---

### Post by Lei_Jiang on 2014-03-16
Hi,

I would suggest you try other DLNA/UPNP servers since Mediatomb is not quite up to your request. Apart form the transcoding issue it's lacking unicode support, too. And it's also missing a lot of features you will find yourself need sooner or later. Personally I recommend serviio. You can find an installation tutorial at [http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu](http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu)

One suggestion is to  create a non-privileged user and use the setuid stanza of upstart. Below is my config.

start on started networking
setuid serviio
script
   alias ffmpeg=avconv
   LANG=zh_CN.utf8 /home/serviio/serviio-1.4/bin/serviio.sh
end script

Serviio comes with a nice GUI console, and it does support transcoding on-the-fly. But what I found is it will transcode and cache the whole file at least by default. That's not what I want but I bet some people like it.

---

### Post by uwe-bungto on 2014-03-16
update.
Mediatomb does show the video directory content if the video is either .vob or .mpg

---

### Post by uwe-bungto on 2014-03-16
> **Lei_Jiang said:**
> Hi,

I would suggest you try other DLNA/UPNP servers since Mediatomb is not quite up to your request. Apart form the transcoding issue it's lacking unicode support, too. And it's also missing a lot of features you will find yourself need sooner or later. Personally I recommend serviio. You can find an installation tutorial at [http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu](http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu)

One suggestion is to  create a non-privileged user and use the setuid stanza of upstart. Below is my config.

start on started networking
setuid serviio
script
   alias ffmpeg=avconv
   LANG=zh_CN.utf8 /home/serviio/serviio-1.4/bin/serviio.sh
end script

Serviio comes with a nice GUI console, and it does support transcoding on-the-fly. But what I found is it will transcode and cache the whole file at least by default. That's not what I want but I bet some people like it.

Thanks
I'll give it a try

---

### Post by uwe-bungto on 2014-03-17
@[**[COLOR=#000000]Lei_Jiang[/COLOR]**]("http://ubuntuforums.org/member.php?u=1868603")
Do I install this package in my home dir or in root?

---

### Post by keratos2 on 2014-04-24
> **Lei_Jiang said:**
> Hi,

I would suggest you try other DLNA/UPNP servers since Mediatomb is not quite up to your request. Apart form the transcoding issue it's lacking unicode support, too. And it's also missing a lot of features you will find yourself need sooner or later. Personally I recommend serviio. You can find an installation tutorial at [http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu](http://wiki.serviio.org/doku.php?id=howto:linux:install:ubuntu)

One suggestion is to create a non-privileged user and use the setuid stanza of upstart. Below is my config.

start on started networking
setuid serviio
script
alias ffmpeg=avconv
LANG=zh_CN.utf8 /home/serviio/serviio-1.4/bin/serviio.sh
end script

Serviio comes with a nice GUI console, and it does support transcoding on-the-fly. But what I found is it will transcode and cache the whole file at least by default. That's not what I want but I bet some people like it.

What utter rubbish.

The problem is that his files and/or mimetime are being filtered out or remapped , as per the config.xml file or that the header information is not quite right for the render, in which case the HTTP header info can be amended in the import.js file.

---

