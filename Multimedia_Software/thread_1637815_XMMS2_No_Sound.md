---
title: "XMMS2 No Sound"
date: 2010-12-05
forum: Multimedia Software
---

### Post by haxwithaxe on 2010-12-05
I have spent the past day and a half trying to get sound out of xmms2. Does anyone have a working config I could look at? Google hasn't been at all helpful on this :/

/var/www/.config/xmms2/clients/cli.conf 
```

ipcpath=tcp://localhost:5555
statusformat=${artist} - ${title}
listformat=${artist} - ${title} (${minutes}:${seconds})
autostart=true
runnycli=true
iknowoldcliisdeprecatedandwillgoaway=false

```

/var/www/.config/xmms2/clients/nycli.conf
```

[main]

PROMPT=xmms2> 
SERVER_AUTOSTART=true
AUTO_UNIQUE_COMPLETE=true
SHELL_START_MESSAGE=true
PLAYLIST_MARKER=->
GUESS_PLS=false
CLASSIC_LIST=true
CLASSIC_LIST_FORMAT=${artist} - ${title}
HISTORY_FILE=
STATUS_FORMAT=${playback_status}: ${artist} - ${title}: ${playtime} of ${duration}

[alias]

ls = list
clear = playlist clear
quit = server shutdown
repeat = seek 0
mute = server volume 0
scap = stop ; playlist clear ; add $@ ; play
current = status -f $1
addpls = add -f -P $@

```

/var/www/.config/xmms2/xmms2.conf 
```

<?xml version="1.0"?>
<xmms version="2">
	<section name="alsa">
		<property name="device">default</property>
		<property name="mixer">PCM</property>
		<property name="mixer_dev">default</property>
		<property name="mixer_index">0</property>
	</section>
	<section name="asf">
		<section name="priority">
			<property name="video/x-ms-asf">50</property>
		</section>
	</section>
	<section name="asx">
		<section name="priority">
			<property name="application/x-asx-playlist">50</property>
		</section>
	</section>
	<section name="avcodec">
		<section name="priority">
			<property name="audio/x-ffmpeg-*">50</property>
		</section>
	</section>
	<section name="bindata">
		<property name="path">/var/www/.config/xmms2/bindata</property>
	</section>
	<section name="cdda">
		<property name="accessmode">default</property>
		<property name="device"></property>
		<section name="priority">
			<property name="application/x-url:cdda://*">50</property>
		</section>
	</section>
	<section name="converter">
		<section name="priority">
			<property name="generic-pcmdata">100</property>
		</section>
	</section>
	<section name="core">
		<property name="ipcsocket">unix:///tmp/xmms-ipc-www-data;tcp://localhost:5555</property>
		<property name="logtsfmt">%H:%M:%S </property>
		<property name="shutdownpath">/var/www/.config/xmms2/shutdown.d</property>
		<property name="startuppath">/var/www/.config/xmms2/startup.d</property>
	</section>
	<section name="cue">
		<section name="priority">
			<property name="application/x-cue">50</property>
		</section>
	</section>
	<section name="curl">
		<property name="authproxy">0</property>
		<property name="connecttimeout">15</property>
		<section name="priority">
			<property name="application/x-url:http://*">50</property>
			<property name="application/x-url:https://*">50</property>
		</section>
		<property name="proxyaddress">127.0.0.1:8080</property>
		<property name="proxypass">password</property>
		<property name="proxyuser">user</property>
		<property name="readtimeout">10</property>
		<property name="shoutcastinfo">1</property>
		<property name="useproxy">0</property>
		<property name="verbose">0</property>
	</section>
	<section name="daap">
		<section name="priority">
			<property name="application/x-url:daap://*">50</property>
		</section>
	</section>
	<section name="diskwrite">
		<property name="destination_directory">/tmp</property>
	</section>
	<section name="effect">
		<section name="order">
			<property name="0"></property>
		</section>
	</section>
	<section name="equalizer">
		<property name="bands">15</property>
		<property name="extra_filtering">0</property>
		<property name="gain00">0.0</property>
		<property name="gain01">0.0</property>
		<property name="gain02">0.0</property>
		<property name="gain03">0.0</property>
		<property name="gain04">0.0</property>
		<property name="gain05">0.0</property>
		<property name="gain06">0.0</property>
		<property name="gain07">0.0</property>
		<property name="gain08">0.0</property>
		<property name="gain09">0.0</property>
		<property name="gain10">0.0</property>
		<property name="gain11">0.0</property>
		<property name="gain12">0.0</property>
		<property name="gain13">0.0</property>
		<property name="gain14">0.0</property>
		<property name="gain15">0.0</property>
		<property name="gain16">0.0</property>
		<property name="gain17">0.0</property>
		<property name="gain18">0.0</property>
		<property name="gain19">0.0</property>
		<property name="gain20">0.0</property>
		<property name="gain21">0.0</property>
		<property name="gain22">0.0</property>
		<property name="gain23">0.0</property>
		<property name="gain24">0.0</property>
		<property name="gain25">0.0</property>
		<property name="gain26">0.0</property>
		<property name="gain27">0.0</property>
		<property name="gain28">0.0</property>
		<property name="gain29">0.0</property>
		<property name="gain30">0.0</property>
		<property name="legacy0">0.0</property>
		<property name="legacy1">0.0</property>
		<property name="legacy2">0.0</property>
		<property name="legacy3">0.0</property>
		<property name="legacy4">0.0</property>
		<property name="legacy5">0.0</property>
		<property name="legacy6">0.0</property>
		<property name="legacy7">0.0</property>
		<property name="legacy8">0.0</property>
		<property name="legacy9">0.0</property>
		<property name="preamp">0.0</property>
		<section name="priority">
			<property name="audio/pcm">50</property>
		</section>
		<property name="use_legacy">1</property>
	</section>
	<section name="faad">
		<section name="priority">
			<property name="audio/aac">50</property>
		</section>
	</section>
	<section name="file">
		<section name="priority">
			<property name="application/x-url:file://*">50</property>
		</section>
	</section>
	<section name="flac">
		<section name="priority">
			<property name="audio/x-flac">50</property>
		</section>
	</section>
	<section name="flv">
		<section name="priority">
			<property name="video/x-flv">50</property>
		</section>
	</section>
	<section name="gvfs">
		<section name="priority">
			<property name="application/x-url:file://*">50</property>
		</section>
	</section>
	<section name="html">
		<section name="priority">
			<property name="application/x-xmms2-xml+html">50</property>
			<property name="text/html">50</property>
		</section>
	</section>
	<section name="icymetaint">
		<section name="priority">
			<property name="application/x-icy-stream">50</property>
		</section>
	</section>
	<section name="id3v2">
		<section name="priority">
			<property name="application/id3v2">50</property>
		</section>
	</section>
	<section name="m3u">
		<section name="priority">
			<property name="audio/x-mpegurl">50</property>
		</section>
	</section>
	<section name="mad">
		<property name="id3v1_encoding">ISO8859-1</property>
		<section name="priority">
			<property name="audio/mpeg">50</property>
		</section>
	</section>
	<section name="magic">
		<property name="dumpcount">16</property>
		<section name="priority">
			<property name="application/octet-stream">50</property>
		</section>
	</section>
	<section name="medialib">
		<property name="allow_remote_fs">0</property>
		<property name="analyze_on_startup">0</property>
		<property name="path">/var/www/.config/xmms2/medialib.db</property>
	</section>
	<section name="mms">
		<section name="priority">
			<property name="application/x-url:mms://*">50</property>
			<property name="application/x-url:mmsh://*">50</property>
			<property name="application/x-url:mmst://*">50</property>
			<property name="application/x-url:mmsu://*">50</property>
		</section>
	</section>
	<section name="mp4">
		<section name="priority">
			<property name="audio/mp4">50</property>
			<property name="video/mp4">50</property>
		</section>
	</section>
	<section name="normalize">
		<property name="buckets">400</property>
		<property name="max_gain">32</property>
		<section name="priority">
			<property name="audio/pcm">50</property>
		</section>
		<property name="smooth">8</property>
		<property name="target">25000</property>
		<property name="use_anticlip">1</property>
	</section>
	<section name="nulstripper">
		<section name="priority">
			<property name="application/x-nul-padded">50</property>
		</section>
	</section>
	<section name="output">
		<property name="buffersize">32768</property>
		<property name="flush_on_pause">1</property>
		<property name="plugin">pulse</property>
	</section>
	<section name="playlist">
		<property name="repeat_all">0</property>
		<property name="repeat_one">0</property>
	</section>
	<section name="pls">
		<section name="priority">
			<property name="audio/x-scpls">50</property>
		</section>
	</section>
	<section name="pulse">
		<property name="name">XMMS2</property>
		<property name="server"></property>
		<property name="sink"></property>
	</section>
	<section name="replaygain">
		<property name="mode">track</property>
		<property name="preamp">6.0</property>
		<section name="priority">
			<property name="audio/pcm">50</property>
		</section>
		<property name="use_anticlip">1</property>
	</section>
	<section name="rss">
		<section name="priority">
			<property name="application/x-xmms2-xml+rss">50</property>
		</section>
	</section>
	<section name="segment">
		<property name="enabled">0</property>
		<section name="priority">
			<property name="audio/pcm">50</property>
		</section>
	</section>
	<section name="smb">
		<section name="priority">
			<property name="application/x-url:smb://*">50</property>
		</section>
	</section>
	<section name="tta">
		<section name="priority">
			<property name="audio/x-tta">50</property>
		</section>
	</section>
	<section name="visualization">
		<section name="priority">
			<property name="audio/pcm">50</property>
		</section>
	</section>
	<section name="vorbis">
		<section name="priority">
			<property name="application/ogg">50</property>
		</section>
	</section>
	<section name="wave">
		<section name="priority">
			<property name="audio/x-wav">50</property>
		</section>
	</section>
	<section name="wavpack">
		<section name="priority">
			<property name="audio/x-wavpack">50</property>
		</section>
	</section>
	<section name="xml">
		<section name="priority">
			<property name="application/xml">50</property>
		</section>
	</section>
	<section name="xspf">
		<section name="priority">
			<property name="application/x-xmms2-xml+playlist">50</property>
		</section>
	</section>
</xmms>

```

---

### Post by prupert on 2011-04-22
You ever get this working as I have exactly the same problem on a minimal install of Ubuntu, tried with both alsa and pulseaudio and no dice.

MPD works fine, but it has no stats...

---

