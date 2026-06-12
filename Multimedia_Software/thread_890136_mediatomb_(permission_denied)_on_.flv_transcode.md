---
title: "mediatomb (permission denied) on *.flv transcode"
date: 2008-08-14
forum: Multimedia Software
---

### Post by ailijic on 2008-08-14
*noob warning*
Hi all, I've been a long time reader first time poster. 

running Hardy on an AMD 2400

Been using mediatomb to play movies and music on my PS3. I added the transcode ability and no when I try to play *.flv I get this error:

> 
2008-08-14 18:58:43    INFO: MediaTomb Web UI can be reached by following this link:
2008-08-14 18:58:43    INFO: [http://192.168.0.107:49152/](http://192.168.0.107:49152/)
2008-08-14 18:59:15    INFO: Arguments: -I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (ailijic)
[00000289] dummy interface: using the dummy interface module...
[COLOR="Red"][00000306] access_output_file private error: cannot open `/tmp//mt_transcode_OVGUFU' (Permission denied)[/COLOR]
[00000304] stream_out_standard private error: no suitable sout access module for `file/ps:///tmp//mt_transcode_OVGUFU'
[00000301] stream_out_transcode private error: cannot create chain
[00000300] main stream output error: stream chain failed for `transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=/tmp//mt_transcode_OVGUFU}'
[00000298] main input error: cannot start stream output instance, aborting
[00000312] dummy demuxer: command `quit'
[00000283] main playlist: stopping playback
2008-08-14 18:59:17    INFO: Arguments: -I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (ailijic)
[00000289] dummy interface: using the dummy interface module...
[00000306] access_output_file private error: cannot open `/tmp//mt_transcode_J9R6FU' (Permission denied)
[00000304] stream_out_standard private error: no suitable sout access module for `file/ps:///tmp//mt_transcode_J9R6FU'
[00000301] stream_out_transcode private error: cannot create chain
[00000300] main stream output error: stream chain failed for `transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=/tmp//mt_transcode_J9R6FU}'
[00000298] main input error: cannot start stream output instance, aborting
[00000312] dummy demuxer: command `quit'
[00000283] main playlist: stopping playback


It seems like I am having trouble writing to /tmp
to fix this I entered:

> 
sudo chmod -R 777 /tmp


it did not fix the problem
related issue [http://ubuntuforums.org/showthread.php?t=830268]("http://ubuntuforums.org/showthread.php?t=830268")
Anyone have any ideas on how to fix this?

here is my config.xml
> 
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <protocolInfo extend="yes"/>	
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:0429935f-0122-4aca-b119-9baa1624c4bf</udn>
    <home>/home/ailijic/.mediatomb</home>
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

<!-- Only show PC Directory -->
      <virtual-layout type="disabled">

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
	<avi-fourcc-list mode="ignore">
          <fourcc>DX50</fourcc>
        </avi-fourcc-list>

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

---

### Post by strizzi on 2008-08-20
Hi,

I had the same problem and it was not a Permission Problem of the tmp directory.
I ran mediatomb with "sudo" - so root-rights. But I installed and configured mediatomb in another users home directory.
I just started the mediatomb-deamon in the home directory of this user and with this user's rights and it worked!
strange but mediatomb is now straming perfectly to my ps3.

greetings,
strizzi

---

