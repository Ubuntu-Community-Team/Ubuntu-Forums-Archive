---
title: "MediaTomb help, please :)"
date: 2010-06-18
forum: Multimedia Software
---

### Post by Buying_Some_Time on 2010-06-18
I'm fairly new to Ubuntu (I'm running Lucid), and I want to stream media to my PS3 from Ubuntu I hear MediaTomb is great for doing that and I just have one problem with it, it won't play my MKV files. I found a tutorial online that showed you how to enable MKV play but it still doesn't work, and I was wondering if any of you guys could take a look at my "/etc/mediatomb/config.xml" file and tell me whats wrong. :) 

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://mediatomb.cc/config/1
http://mediatomb.cc/config/1.xsd">
  <server>
    <interface>eth0</interface>
    <port>50000</port>
    <pc-directory upnp-hide="yes"/>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MyMediatomb</name>
    <udn>uuid:4105837b-0437-4848-9bea-xxxxxxxxxxxx</udn>
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
    <protocolInfo extend="yes"/>
  </server>
  <import hidden-files="no">
    <filesystem-charset>UTF-8</filesystem-charset>
    <metadata-charset>ISO-8859-15</metadata-charset>
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="js">
        <import-script>/etc/mediatomb/import-custom.js</import-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogm" to="video/oggmedia"/>
        <map from="mkv" to="video/matroska"/>
        <map from="iso" to="video/dvdiso"/>
        <map from="wmv" to="video/x-ms-wmv"/>
        <map from="flv" to="video/x-flv"/>
        <map from="avi" to="video/avi"/>
        <map from="rm" to="video/realmedia"/>
        <map from="srt" to="video/subtitle"/>
        <map from="sub" to="video/subtitle"/>
        <map from="mpg" to="video/mpeg"/>
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="video/avi" as="avi"/>
      </mimetype-contenttype>
    </mappings>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/transcode" using="mencoder-int"/>
      <transcode mimetype="video/realmedia" using="mencoder-int"/>
      <transcode mimetype="video/oggmedia" using="mencoder-720"/>
      <transcode mimetype="video/matroska" using="mencoder-720"/>
      <transcode mimetype="video/dvdiso" using="mencoder-iso"/>
      <transcode mimetype="video/subtitle" using="mencoder-sub"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="mencoder-sub" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/usr/local/bin/mediatomb-mencoder-sub" arguments="%in %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>
      <profile name="mencoder-int" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=9000:vrc_buf_size=1835 -ofps 25 -mpegopts muxrate=12000 -af lavcresample=44100 -vf harddup -o %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>
      <profile name="mencoder-720" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -aid 0 -sid 0 -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=12000:vrc_buf_size=1835 -mpegopts muxrate=12000 -vf harddup,scale -zoom -xy 720 -font /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf -subfont-autoscale 0 -subfont-text-scale 20 -slang nl,en -noautosub -ofps 24000/1001 -o %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>
      <profile name="mencoder-iso" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/usr/local/bin/mediatomb-mencoder-iso" arguments="%in %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
      </profile>
    </profiles>
  </transcoding>
</config>

---

### Post by Buying_Some_Time on 2010-06-19
Anyoine?

---

### Post by Lampi on 2010-06-21
have a look @ /var/log/mediatomb, if you see:
> 
INFO: MediaTomb Web UI can be reached by following this link:
INFO: [http://YOURMEDIATOMBIP:4915X/](http://YOURMEDIATOMBIP:4915X/)

- then copy this URL to firefox - the MediaTomb web interface should open
- now choose Filesystem
- browse to the folder you like to share files
- use the plus icon to add a folder or a single file
- then you find it in Database

---

### Post by Chocomochino on 2010-06-25
Okay: i just got this running today using this config.xml

```

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="Tabatha" password="d4c4f4"/>
      </accounts>
    </ui>
    <name>Tabatha</name>
    <udn>uuid:48b8dd9e-f2aa-4a9f-a235-d42f69492afd</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>127.0.0.1</host>
        <username>root</username>
        <database>d4c4f484=</database>
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
<filesystem-charset>UTF-8</filesystem-charset>
<scripting script-charset="UTF-8">
<common-script>/usr/share/mediatomb/js/common.js</common-script>
<playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
<virtual-layout type="builtin">
<import-script>/usr/share/mediatomb/js/import.js</import-script>
</virtual-layout>
</scripting>
<autoscan>
    </autoscan>
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
<map from="divx" to="video/x-divx"/>
<map from="mkv" to="video/x-matroska"/>
<map from="mov" to="video/quicktime"/>
<map from="qt" to="video/quicktime"/>
<map from="mpg" to="video/mpeg"/>
<map from="mpeg" to="video/mpeg"/>
<map from="rm" to="video/realmedia"/>
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
<treat mimetype="audio/mp4" as="mp4"/>
<treat mimetype="video/x-divx" as="avi"/>
</mimetype-contenttype>
</mappings>
</import>
<transcoding enabled="yes">
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="audio-common"/>
<transcode mimetype="video/x-divx" using="video-common"/>
<transcode mimetype="video/x-matroska" using="video-common"/>
<transcode mimetype="video/quicktime" using="video-common"/>
<transcode mimetype="video/realmedia" using="mencoder-int"/>
</mimetype-profile-mappings>
<profiles>
<profile name="oggflac2raw" enabled="yes" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -f %out %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="vlcmpeg" enabled="yes" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="vlc" arguments="-I dummy %in -sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
<profile name="audio-common" enabled="yes" type="external">
<mimetype>audio/x-wav</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="mediatomb-transcode-audio" arguments="%in %out"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="video-common" enabled="yes" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="mediatomb-transcode-video-ffmpeg" arguments="%in %out"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
<profile name="mencoder-int" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=9000:vrc_buf_size=1835 -ofps 25 -mpegopts muxrate=12000 -af lavcresample=44100 -vf harddup -o %out"/>
<buffer size="1000000" chunk-size="512000" fill-size="20480"/>
</profile>
</profile>
</profiles>
</transcoding>
</config>



```



But what really did it, was changing the file /usr/bin/mediatomb-transcode-video and /usr/bin/mediatomb-transcode-video-ffmpeg (which mkv uses to  stream in this config)

to these:


/usr/bin/mediatomb-transcode-video
```


#!/bin/bash

VLC_PATH="/usr/bin/vlc"
INPUT="$1"
OUTPUT="$2"
VIDEO_CODEC="mp2v"
VIDEO_BITRATE="4096"
VIDEO_FRAMERATE="25"
AUDIO_CODEC="mpga"
AUDIO_BITRATE="192"
AUDIO_SAMPLERATE="44100"
AUDIO_CHANNELS="2"
FORMAT="ps"
SUBTITLE_LANGUAGE="eng"

exec "${VLC_PATH}" "${INPUT}" -I dummy --sout "#transcode{vcodec=${VIDEO_CODEC},\
vb=${VIDEO_BITRATE},fps=${VIDEO_FRAMERATE},acodec=${AUDIO_CODEC},ab=${AUDIO_BITRATE},\
samplerate=${AUDIO_SAMPLERATE},channels=${AUDIO_CHANNELS},soverlay,audio-sync}:\
standard{mux=${FORMAT},access=file,dst=${OUTPUT}}" --sub-language=${SUBTITLE_LANGUAGE} \
vlc:quit >/dev/null 2>&1



```

/usr/bin/mediatomb-transcode-video-ffmpeg
```

#!/bin/bash
INPUT=$1
OUTPUT=$2
VIDEO_CODEC="mpeg2video"
VIDEO_BITRATE="4096k"
AUDIO_CODEC="mp2"
AUDIO_BITRATE="192k"
AUDIO_SAMPLERATE="48000"
AUDIO_CHANNELS="2"
FORMAT="dvd"

exec /usr/bin/ffmpeg -threads 2 -i "${INPUT}" -vcodec ${VIDEO_CODEC} -b ${VIDEO_BITRATE} \
-acodec ${AUDIO_CODEC} -ab ${AUDIO_BITRATE} -ar ${AUDIO_SAMPLERATE} -ac ${AUDIO_CHANNELS} \
-f ${FORMAT} -copyts - > "${OUTPUT}" #2>/dev/null


```


Also i needed to install these:


```


sudo apt-get install vlc ffmpeg ffmpegthumbnailer transcode vorbis-tools

```

Hope this helps :)

---

