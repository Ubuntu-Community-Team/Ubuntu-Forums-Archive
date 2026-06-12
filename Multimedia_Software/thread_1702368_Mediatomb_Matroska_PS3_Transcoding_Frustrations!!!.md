---
title: "Mediatomb Matroska PS3 Transcoding Frustrations!!!!"
date: 2011-03-07
forum: Multimedia Software
---

### Post by ffixcollector on 2011-03-07
I finally got .flac transcoding to work, but I cant get .mkv files to transcode. I keep getting a network error (000000) when trying to play .mkv's. Here is my config and mkv.sh
```
<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd"><!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="user" password="admin"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:fa142025-46b9-43c2-b4de-dd0e10a7bba6</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage caching="yes">
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" --><!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    --><!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    --><!-- Uncomment the line below if you have a Telegent TG100 --><!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="yes">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>100</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>yes</workaround-bugs>
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
        <map from="mkv" to="video/x-matroska"/>
        <map from="mka" to="audio/x-matroska"/>
    <map from="avi" to="video/divx"/>
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
      <AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
    </online-content>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="audio-flac"/>
      <transcode mimetype="video/x-matroska" using="transcode-matroska"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="audio-flac" enabled="yes" type="external">
      <mimetype>audio/L16</mimetype>
      <accept-url>no</accept-url>
      <first-resource>yes</first-resource>
      <hide-original-resource>yes</hide-original-resource>
      <accept-ogg-theora>no</accept-ogg-theora>
      <sample-frequency>44100</sample-frequency>
      <audio-channels>2</audio-channels>
      <agent command="flac" arguments="-dfs --force-raw-format --endian=big --sign=signed -o %out %in"/>
      <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="oggflac2raw" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
    <profile name="transcode-matroska" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/etc/mediatomb/mkv.sh" arguments="%in %out"/>
        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile> 
      <profile name="vlcmpeg" enabled="yes" type="external">
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
```
#!/bin/bash
#
# General all-covering MediaTomb transcoding script.
#
#############################################################################
# Edit the parameters below to suit your needs.
#############################################################################

# Subtitles imply transcoding; set to 1 to disable subtitle rendering.
# For divx this doesn't matter much but for mp4, mkv and DVD it does.
DISABLESUBS=1

# Change this to enable different DVD subtitle languages.
SUBS="nl,en"

# Change this line to set the average bitrate.
# Use something like 8000 for wired connections; lower to 2000 for wireless.
AVBIT=8000

# Change this line to set the maximum bitrate.
# Use something like 12000 for wired connections; lower to 5000 for wireless.
MVBIT=12000

# Change this line to set the MPEG audio bitrate in kbps. AC3 is fixed to 384.
AABIT=256

# Change this line to set your favourite subtitle font.
SFONT="/etc/mediatomb/DejaVuSans.ttf"

# Change this line to set the size of subtitles. 20-25 is okay.
SUBSIZE=20

# Enable downscaling of transcoded content to 720 pixels wide (DVD format)?
DOWNSCALE=1

# If downscaling is enabled, anything over this width (pixels) will be downscaled.
MAXSIZE=900

# Enable logging to file?
LOGGING=1

# If logging is enabled, log to which file?
LOGFILE="/var/log/mediatomb-transcode.log"

#############################################################################
# Do not change anything below this line.
#############################################################################
# Variables
#############################################################################

FILE=$1
VERSION="0.12"

MENCODER=$(which mencoder)
MEDIAINFO=$(which mediainfo)
FFMPEG=$(which ffmpeg)
LSDVD=$(which lsdvd)
XML=$(which xmlstarlet)

M_TR_M="-oac lavc -ovc lavc -of mpeg -lavcopts \
    abitrate=${AABIT}:vcodec=mpeg2video:keyint=1:vbitrate=${AVBIT}:\
    vrc_maxrate=${MVBIT}:vrc_buf_size=1835 \
    -mpegopts muxrate=12000 -af lavcresample=44100 "
M_TR_A="-oac lavc -ovc copy -of mpeg -lavcopts \
    abitrate=${AABIT} -af lavcresample=44100 "
M_RE_M="-oac copy -ovc copy -of mpeg -mpegopts format=dvd -noskip -mc 0 "
F_TR_M="-acodec ac3 -ab 384k -vcodec copy -vbsf h264_mp4toannexb -f mpegts -y "
F_RE_M="-acodec copy -vcodec copy -vbsf h264_mp4toannexb -f mpegts -y "
SUBOPTS="-slang ${SUBS} "
SRTOPTS="-font ${SFONT} -subfont-autoscale 0 \
    -subfont-text-scale ${SUBSIZE} -subpos 100 "
SIZEOPTS="-vf harddup,scale=720:-2 "
NOSIZEOPTS="-vf harddup "
S24FPS="23.976"
S24OPT="-ofps 24000/1001 "
S30FPS="29.970"
S30OPT="-ofps 30000/1001 "

VCODEC=""
ACODEC=""
VWIDTH=""
VFPS=""
QPEL=""
AVCPROF=""

OPTS=("")

declare -i MODE=0

#############################################################################
# Functions
#############################################################################

function log {
        if [ "${LOGGING}" == "1" ] ; then
                echo -e "$(date +'%Y/%m/%d %H:%m:%S') \t $1" >> ${LOGFILE}
        fi
}

function mediainfo {
        MIOUT=$(mktemp /tmp/tmp.mediainfo.XXXXXX)
        log "Logging mediainfo XML to ${MIOUT}."
        ${MEDIAINFO} --output=xml "${FILE}" > ${MIOUT}
        VCODEC=$(${XML} sel -t -m ".//track[@type='Video']" -v "Format" ${MIOUT} )
        ACODEC=$(${XML} sel -t -m ".//track[@type='Audio']" -v "Format" ${MIOUT} )
        VWIDTH=$(${XML} sel -t -m ".//track[@type='Video']" -v "Width" \
            ${MIOUT} | sed 's/ pixels//' )
        VFPS=$(${XML} sel -t -m ".//track[@type='Video']" -v "Frame_rate" \
            ${MIOUT} | sed 's/ fps//' )
        AVCPROF=$(${XML} sel -t -m ".//track[@type='Video']" -v "Format_profile" \
            ${MIOUT} | sed 's/[^0-9]//g' )
        QPEL=$(${XML} sel -t -m ".//track[@type='Video']" -v "Format_settings__QPel" \
            ${MIOUT} )
        log "Variables found: \
            ${VCODEC} | ${ACODEC} | ${VWIDTH} | ${VFPS} | ${AVCPROF} | ${QPEL} "
        rm -f ${MIOUT}
}

function tropts {
        if [ "${DOWNSCALE}" == "1" -a ${VWIDTH} -gt ${MAXSIZE} ] ; then
                log "Rescaling to 720 pixels wide."
                OPTS+=(${SIZEOPTS})
        else
                log "Rescaling disabled or file within limits."
                OPTS+=(${NOSIZEOPTS})
        fi
        if [ "${VFPS}" == "${S24FPS}" ] ; then
                log "Framerate adjusted for mencoder."
                OPTS+=(${S24OPT})
        else if [ "${VFPS}" == "${S30FPS}" ] ; then
                log "Framerate adjusted for mencoder."
                OPTS+=(${S30OPT})
        else
                log "Framerate acceptable for mencoder."
        fi
        fi
}

function getmode {
        # Fixed case: DVD ISO.
        if [ "${FEXT}" == "ISO" ] ; then
                CHAPTER=$(${LSDVD} "${FILE}" | grep Longest | sed 's/.* //')
                log "DVD iso image found: Longest chapter is ${CHAPTER}."
                MODE+=${DISABLESUBS}1000000
                return 0
        fi
        # Fixed case: subtitle found: transcode by default.
        if [ "${DISABLESUBS}" == "0" -a -e "$(echo $FILE | sed 's/...$/sub/')" ] ; then
                log "SRT subtitle found."
                SUB=$(echo $FILE | sed 's/...$/sub/')
                MODE+=100000
                return 0
        elif [ "${DISABLESUBS}" == "0" -a -e "$(echo $FILE | sed 's/...$/srt/')" ] ; then
                log "SUB subtitle found."
                SUB=$(echo $FILE | sed 's/...$/srt/')
                MODE+=100000
                return 0
        fi

        log "No subtitles found, or subtitle rendering disabled."
        mediainfo

        case ${VCODEC} in
        "AVC")
                if [ "${AVCPROF}" -gt "41" ] ; then
                        # Cannot handle h.264 4.1+
                        MODE+=10000    
                else         
                        # We can handle the rest                         
                        MODE+=1        
                fi ;;
        "MPEG-4 Visual")
                if [ "${QPEL}" == "No" ] ; then
                        # No QPEL: we could remux the video        
                        MODE+=100      
                else           
                        # QPEL: just transcode it all                       
                        MODE+=10000    
                fi ;;
        * )
                        # Transcode everything we don't know
                        MODE+=10000 ;; 
        esac

        case ${ACODEC} in
        "AC-3" | "MPEG Audio" )     
                        # These should be wellknown                  
                        MODE+=1 ;;     
        * )
                if [ "${MODE}" -lt "100" ] ; then   
                        # If video is AVC, transcode audio in m2ts  
                        MODE+=10       
                else    
                        # Otherwise in other container                      
                        MODE+=1000     
                fi ;;
        esac

}

function processmode {
        log "Mode is ${MODE}."
        if [ ! "${MODE}" -lt "10000000" ] ; then
                EXEC="${MENCODER} -dvd-device"
                OPTS+=(dvd://${CHAPTER} ${M_RE_M} -o )
        elif [ ! "${MODE}" -lt "1000000" ] ; then
                EXEC="${MENCODER} -dvd-device"
                OPTS+=(dvd://${CHAPTER} ${SUBOPTS} ${M_TR_M} -o )
        elif [ ! "${MODE}" -lt "100000" ] ; then
                EXEC=${MENCODER}
                tropts
                OPTS+=(${M_TR_M} -sub ${SUB} ${SRTOPTS} -o )
        elif [ ! "${MODE}" -lt "10000" ] ; then
                EXEC=${MENCODER}
                tropts
                OPTS+=(${M_TR_M} -o )
        elif [ ! "${MODE}" -lt "1000" ] ; then
                EXEC=${MENCODER}
                tropts
                OPTS+=(${M_TR_M} -o)
        elif [ ! "${MODE}" -lt "100" ] ; then
                EXEC=${MENCODER}
                OPTS+=(${M_TR_M} -o)
        elif [ ! "${MODE}" -lt "10" ] ; then
                EXEC="${FFMPEG} -i"
                OPTS+=(${F_TR_M})
        elif [ ! "${MODE}" -lt "1" ] ; then
                EXEC="${FFMPEG} -i"
                OPTS+=(${F_RE_M})
        else
                log "I'm sorry Dave, I'm afraid I can't do mode=0."
        fi
}

#############################################################################
# Main method
#############################################################################

log "Starting MediaTomb Multifunctional Transcoder (version ${VERSION})."
FEXT=$(echo $FILE | sed 's/.*\.//' | tr [a-z] [A-Z])
log "${FEXT} file specified: \"${FILE}\""

getmode
processmode

log "Starting exec:"
log "${EXEC} \"${FILE}\" ${OPTS[@]} ${2} &>/dev/null"
exec ${EXEC} "${FILE}" ${OPTS[@]} "${2}" &>/dev/null
```



What am I doing wrong? How do I transcode .mkv files for the PS3? Can I test the mkv.sh script to see if it works? Do I need additional packages? Do I need a different script? 

Any help would be much appreciated.

---

### Post by chrisjames59 on 2011-03-14
I have also been unable to get mkv to properly transcode to the PS3 using mediatomb.  I have tried at least 3 different config+agent command/script combinations found online.  If anyone could post a working config with script to get mkv, subtitle, and flac working.  It would be greatly appreciated.

---

### Post by adduds on 2011-03-28
don't know if you've tried this or simply want to use mediatomb for the webUI

but i greatly suggest you try pms-linux

[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589)


it owns media tomb all to hell lol IMHOP

you won't have to tinker ;)

need help just holler MAYBE i can :P

---

### Post by ffixcollector on 2011-04-17
PS3mediaserver is the way to go, Thank  you. It can trancode anything thing, play flac and mkv files and even read .iso or .rar files. I love it, zero config, and it uses mencoder :) Awesome

---

### Post by Arminius on 2011-09-19
> **ffixcollector said:**
> PS3mediaserver is the way to go, Thank  you. It can trancode anything thing, play flac and mkv files and even read .iso or .rar files. I love it, zero config, and it uses mencoder :) Awesome

it's not the way to go, it's extremely unstable, when I tried it every 5 mins it would stop what I'm watching and complain of a network error, even though there was no network problem.

Media tomb is much more stable, in spite of it's limited trans coding ability's.

---

### Post by ffixcollector on 2013-04-28
To each their own

---

