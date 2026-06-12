---
title: "MediaTomb and PS3 - Unsupported Data?"
date: 2008-06-28
forum: Multimedia Software
---

### Post by ChildOfMana on 2008-06-28
Okay here's my problem.

I'm running MediaTomb under Ubuntu Hardy and trying to stream video to my PS3 (firmware version 2.36).

My PS3 can see my MediaTomb Server but it says that all the videos are Unsupported Data.

I know for a fact that the PS3 *will* support the file type (they're all .avi) because if I copy one onto a USB Memory Stick the PS3 will recognise and play the file with no problems whatsoever.

So why does it decide the files are not supported when they're served up by Mediatomb?

Here's my config.xml file:

> <?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:70e6fd25-377c-478b-8a6d-68903a337c7e</udn>
    <home>/home/dave/.mediatomb</home>
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
  </server>
  <protocolInfo extend="yes"/>
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
	<map from="avi" to="video/x-divx"/>
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
        <!-- <map from="avi" to="video/divx"/> -->
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

Can anyone see the problem?

Thanks.

---

### Post by ChildOfMana on 2008-06-28
Oh, I should have mentioned above that after adding the following lines to my config.xml file;

> <protocolInfo extend="yes"/>  and  > <map from="avi" to="video/x-divx"/>

I removed and then re-added all media to the database... so I don't think that's the problem.

---

### Post by ChildOfMana on 2008-06-28
Anyone?

---

### Post by csk on 2008-06-29
i'm having a similar problem. i thought i would try and see if transcoding the avi might solve the problem. I tried referring to this  [http://gentoo-wiki.com/HOWTO_MediaTomb#Introduction](http://gentoo-wiki.com/HOWTO_MediaTomb#Introduction)

it suggested using this script between <profile name="video-common" enabled="yes" type="external"> and </profile> 
        <avi-fourcc-list mode="ignore">
          <fourcc>DX50</fourcc>
        </avi-fourcc-list>


this is supposed to transcode all avi except those with the DX50 FourCC. but still no luck. Everytime the transcode seems to kick in i get this message:

2008-06-29 14:58:28    INFO: Arguments: -i %in -o %out -s 128
2008-06-29 14:58:28    INFO: Arguments: -i %in -o %out -s 128
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
128 12
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
128 12
2008-06-29 15:24:22    INFO: Arguments: -i %in -o %out -s 128
2008-06-29 15:24:22    INFO: Arguments: -i %in -o %out -s 128
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
128 12
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
128 12

and ps3 says media type is not supported. it seems that ps3 firmware 2.35 has issues

---

### Post by amak79 on 2008-06-29
ChildOfMana,

Did you add the <protocolInfo extend="yes"/> line to the config or did you edit the existing <protocolInfo> line. If you added that line, then you might have two conflicting <protocolInfo> tags in your config, which would cause unpredictable results.

If that doesn't help, what mimetype does MT show for you AVI's? it should say, video/divx.

---

### Post by amak79 on 2008-06-29
csk,

Could you please post your config.xml?

---

### Post by jcoddington on 2008-06-29
I am having the same problem since i upgraded my file server to 8.04.  Any help would be greatly appreciated.  Thanks.

---

### Post by ChildOfMana on 2008-06-29
> Did you add the <protocolInfo extend="yes"/> line to the config or did you edit the existing <protocolInfo> line. If you added that line, then you might have two conflicting <protocolInfo> tags in your config, which would cause unpredictable results.

Yes I added it. I'll delete it and uncomment the original one and see if that works. Unfortunately I haven't got time to do it now so will have to do it tomorrow. I'll post back here with the results as soon as I've done it though. Thanks for the advice.

> If that doesn't help, what mimetype does MT show for you AVI's? it should say, video/divx.

I'm not sure. Again, I'll check tomorrow as soon as I get time and let you know.

Thanks.

---

### Post by csk on 2008-06-30
> **amak79 said:**
> csk,

Could you please post your config.xml?

here's my config.xml: 

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:6556ae80-64c9-4054-99d2-cea1b84d6fc9</udn>
    <home>/home/csk/.mediatomb</home>
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
    
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
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
        <map from="avi" to="video/x-divx"/> 
	<map from="divx" to="video/x-divx"/>

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
        <!--<map from="avi" to="video/divx"/> -->
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
	<treat mimetype="video/x-divx" as="avi"/>
       
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
    <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-divx" using="video-thumbnail"/>
      <transcode mimetype="application/ogg" using="audio-common"/>
      <transcode mimetype="application/ogg" using="video-common"/>
      <transcode mimetype="audio/x-flac" using="audio-common"/>
      <transcode mimetype="video/x-flv" using="video-common"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="audio-common" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
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
        <agent command="mediatomb-transcode-video" arguments="%in %out"/>
        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile>

	<profile name="video-thumbnail" enabled="yes" type="external"> 
	<mimetype>image/jpeg</mimetype> 
	<accept-url>yes</accept-url> 
	<thumbnail>yes</thumbnail> 
	<resolution>128x128</resolution> 
	<agent command="ffmpegthumbnailer" arguments="-i %in -o %out -s 128"/> 
	<buffer size="524288" chunk-size="512" fill-size="1024"/> 
	</profile> 

    </profiles>
  </transcoding>
</config>

edit:
my mediatomb-transcode-audio/video script were taken from here:
[http://gentoo-wiki.com/HOWTO_MediaTomb#Using_VLC](http://gentoo-wiki.com/HOWTO_MediaTomb#Using_VLC)

the reason i used this is because it can (allegedly) transcode .srt files as well.

also i tried transcoding with the original script (which comes standard with mediatomb) and got the same message

cheers
csk

---

### Post by amak79 on 2008-06-30
csk,

Your config.xml looks good, except for one thing. You haven't told MT to transcode your DivX files :) You need to add **<transcode mimetype="video/x-divx" using="video-common"/>** to the **<mimetype-profile-mappings>** section in config.xml.

The default MediaTomb and Gentoo Wiki transcoding profiles won't transcode DivX since most UPnP devices can play these files natively. The Gentoo Wiki even states that it will only transcode "FLAC, Flash, Theora and Vorbis" files.

The PS3 is particularly sensitive about which DivX files it will play. If you have a situation where most of your DivX files play but a small number don't, then you can use MediaTomb's FourCC support to selectively transcode DivX based on their FourCC.

The VLC script posted on the Gentoo Wiki is quite good and it supports both internal and external subtitles. You can edit the **SUBTITLE_LANGUAGE** variable in the mediatomb-transcode-video script to select the required subtitle language.

---

### Post by amak79 on 2008-06-30
csk,

I forgot to mention that if you added **<map from="avi" to="video/x-divx"/>** and **<map from="divx" to="video/x-divx"/>** to the config *after* you imported your DivX files, then you will need to re-import you DivX files for the new mimetype to take effect. This could be the reason why your getting the unsupported message and it could also mean that you don't need transcoding. Just make sure that when you remove the DivX files from MediaTomb, you use linked-delete (X icon with the chains) and then re-import.

The messages you see in the MediaTomb log are normal. It is most likely ffmpegthumbnailer producing those messages for your DivX thumbnails.

---

### Post by csk on 2008-06-30
amak79,
worked like a charm. thanks

---

### Post by Famine3h on 2008-06-30
[b][color=indigo]This particular issue is sending me insane - I pretty much only went Linux in order to share media to my PS3.

I've tried every single "fix" I can find out there in internetland - and I'm probably somewhat hindered in that I'm trying to manage interstellar travel before I can crawl - but none, including the one in this thread, have allowed me to view any video files of any flavour on my PS3 from the Linux box. Files I know work. In fact this "fix" has changed matters slightly, in that now all of my audio files are reported as "Unsupported Data" also...


If anyone could provide any assistance - preferably in language one might explain this to your dad or dog, or even with a config.xml file which works for Mediatomb on PS3 v2.35 and Ubuntu 8.04 - I will name a WAP in your honour.

The config.xml file I'm using is identical to the one most recently posted in this thread by csk, with the amendment as suggested by amak79.[/color][/b]

---

### Post by ChildOfMana on 2008-06-30
> Did you add the <protocolInfo extend="yes"/> line to the config or did you edit the existing <protocolInfo> line. If you added that line, then you might have two conflicting <protocolInfo> tags in your config, which would cause unpredictable results.

> Yes I added it. I'll delete it and uncomment the original one and see if that works. Unfortunately I haven't got time to do it now so will have to do it tomorrow. I'll post back here with the results as soon as I've done it though. Thanks for the advice.

Didn't work :(

I'm kind of stumped now :confused:

Thanks for the advice anyway though. :guitar:

---

### Post by amak79 on 2008-06-30
Famine3h,

Exactly what file types do you have? Regarding your audio, if they are in a format that the PS3 doesn't support i.e. Ogg then you will need to transcode them. However, the current version of MediaTomb can't stream transcoded audio to the PS3. This has been fixed in the SVN version of MediaTomb.

You should also re-import all your files into MediaTomb if you made any changes to mimetype settings in config.xml. Just make sure that you remove the existing files with linked-deleted (X icon with the chains), and then re-import your files.

---

### Post by amak79 on 2008-06-30
ChildOfMana,

I can only suggest that you re-import all your AVI files again, but make sure to use linked-delete to remove the files as I mentioned above to Famine3h. What mimetype does MediaTomb show for your AVI files? It should be video/x-divx. If you still can't get it to work, then post your current config.xml and any useful information from the MT log file or console output.

---

### Post by Famine3h on 2008-07-01
> **amak79 said:**
> Famine3h,

Exactly what file types do you have?

**[color=indigo]Almost exclusively .avi - these are files which work on the PS3 or streamed to the PS3 from WindowsXP.[/color]**

> **amak79 said:**
> Regarding your audio, if they are in a format that the PS3 doesn't support i.e. Ogg then you will need to transcode them. However, the current version of MediaTomb can't stream transcoded audio to the PS3.

**[color=indigo]They are almost exclusively .mp3 and worked before I amended my config.xml file to the one most recently posted in this thread by *csk*, with the alteration you made.[/color]**

> **amak79 said:**
> You should also re-import all your files into MediaTomb if you made any changes to mimetype settings in config.xml.

**[color=indigo]I do this every time.[/color]**

---

### Post by amak79 on 2008-07-01
Famine3h,

If your config.xml is the same as csk's then it should work. Are you modifying the correct config.xml? MediaTomb uses ~/.mediatomb/config.xml when started manually in a terminal by your user. If you start MediaTomb via the init script at boot, then it uses /etc/mediatomb/config.xml.

---

### Post by Famine3h on 2008-07-01
> **amak79 said:**
> Are you modifying the correct config.xml?

**[color=indigo]I would certainly assume so, seeing as when I made the modification all of my music files stopped working...[/color]**

---

### Post by ChildOfMana on 2008-07-01
> I can only suggest that you re-import all your AVI files again, but make sure to use linked-delete to remove the files as I mentioned above to Famine3h. What mimetype does MediaTomb show for your AVI files? It should be video/x-divx. If you still can't get it to work, then post your current config.xml and any useful information from the MT log file or console output.

I've re-imported them again twice now and I used the linked-delete too. I also tried deleting the mediatomb.db file and then re-importing them.

How do I find out what mime type MediaTomb is showing?

You think uninstalling and then re-installing MediaTomb might help?

Here's my config.xml again, as it stands now:

> <?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:70e6fd25-377c-478b-8a6d-68903a337c7e</udn>
    <home>/home/dave/.mediatomb</home>
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
  </server>
  <protocolInfo extend="yes"/>
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
        <map from="flv" to="video/x-flv"/>
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
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

Thanks for looking into this.

---

### Post by ChildOfMana on 2008-07-01
Well I uninstalled and then re-installed MediaTomb, checked the database and config.xml were reset to default - they were - edited the config.xml as above and imported all the media again... and still no luck!

Well and truly stumped!

---

### Post by amak79 on 2008-07-01
ChildOfMana,

You still have two **<protocolInfo>** tags in your config.xml. One is set to **yes** and the other is set to **no**. Can you please remove the one that is set to **no** and restart MT. You won't need to re-import your media.

You can check the mimetype of an item via the MT interface. For example, clicking on the Video folder will bring up all your videos that you have added to MT. For each item there is an edit icon right next to the linked-delete icon. Clicking the edit icon will bring a bunch of fields about the item including mimetype. It should say **video/x-divx** or **video/divx**, both will work.

---

### Post by ChildOfMana on 2008-07-02
> You still have two <protocolInfo> tags in your config.xml. One is set to yes and the other is set to no. Can you please remove the one that is set to no and restart MT. You won't need to re-import your media.

Can't believe I didn't notice that. Sorry. I've removed the first instance now but still no joy.

However, the mimetype is showing as video/x-msvideo so I asuume this is the problem then?

I assume this section of config.xml is what I need to be looking at;

> <mappings>
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

But what do I need to change?

---

### Post by amak79 on 2008-07-03
ChildOfMana,

If the mimetype is **video/x-msvideo** then that is the reason why it's not working. However, your config.xml appears to be correct as you have added **<map from="avi" to="video/divx"/>** which tells MT to map all AVI files to the **video/divx** mimetype during import.

Can you manually set the mimetype of one of your AVI's to **video/divx** using the edit icon. You should then restart MT and check if the PS3 can now see that video.

If it can't then I suspect that you may be editing the wrong config.xml. As I explained in a previous post, if MT starts automatically during boot, it will use /etc/mediatomb/config.xml. If you start MT manually in a terminal then it uses ~/.mediatomb/config.xml. Ubuntu will by default start MT at boot, so you should always be editing /etc/mediatomb/config.xml.

I have also tested your config.xml and it correctly sets the mimetype for my AVI's and are seen by the PS3.

---

### Post by ChildOfMana on 2008-07-03
> If it can't then I suspect that you may be editing the wrong config.xml. As I explained in a previous post, if MT starts automatically during boot, it will use /etc/mediatomb/config.xml. If you start MT manually in a terminal then it uses ~/.mediatomb/config.xml. Ubuntu will by default start MT at boot, so you should always be editing /etc/mediatomb/config.xml.

Yeah I've edited both of them.

I removed all the files from the database and re-imported them once more and this time the mimetype for all of them is displaying as video/divx but it's still not working.

---

### Post by amak79 on 2008-07-03
[QUOTE=ChildOfMana]I removed all the files from the database and re-imported them once more and this time the mimetype for all of them is displaying as video/divx but it's still not working.[/QUOTE]
Does the PS3 show a DivX icon next to each video? If it does and it still can't play them, then it would mean that those files are unplayable and need to be transcoded. This is strange as you mentioned in your first post that the files are playable when copied to the PS3.

I don't know what else to try except to enable transcoding and see if that works. You need to set the **<transcoding>** tag to **yes** and add  **<transcode mimetype="video/divx" using=""vlcmpeg"/>** to the **<mimetype-profile-mappings>** section. The default video transcoding profile uses VLC so you need install it: **sudo apt-get install vlc** or **sudo apt-get install vlc-nox** for the CLI version. You won't need to re-import your files, just restart MT with **sudo /etc/init.d/mediatomb restart** if your editing /etc/mediatomb/config.xml.

If you still can't get it to work, I can only suggest you try the MediaTomb IRC channel or forum for help.

---

### Post by ChildOfMana on 2008-07-04
> Does the PS3 show a DivX icon next to each video? If it does and it still can't play them, then it would mean that those files are unplayable and need to be transcoded. This is strange as you mentioned in your first post that the files are playable when copied to the PS3.

No it doesn't. The files are playable when copied to the PS3. I've since copied them all over. I'd still like to get mediatomb working if possible though.
> 
I don't know what else to try except to enable transcoding and see if that works. You need to set the <transcoding> tag to yes and add <transcode mimetype="video/divx" using=""vlcmpeg"/> to the <mimetype-profile-mappings> section. The default video transcoding profile uses VLC so you need install it: sudo apt-get install vlc or sudo apt-get install vlc-nox for the CLI version. You won't need to re-import your files, just restart MT with sudo /etc/init.d/mediatomb restart if your editing /etc/mediatomb/config.xml.

Okay I'll give this a try. Unfortunately I'm away from my PS3 for the weekend so will have to do it Monday. I'll post back here and let you know how I get on though.

Thanks for all your advice so far :cool:

---

### Post by amak79 on 2008-07-04
[QUOTE=ChildOfMana]No it doesn't. The files are playable when copied to the PS3. I've since copied them all over. I'd still like to get mediatomb working if possible though.[/QUOTE]
Well if it's not displaying the DivX icon even after the mimetypes are set correctly, then something is very wrong with your setup. It appears that the changes you make to config.xml don't have any effect, so I doubt enabling transcoding will work either.

---

### Post by ChildOfMana on 2008-07-07
> It appears that the changes you make to config.xml don't have any effect, so I doubt enabling transcoding will work either.

No it doesn't. Ah well, I'll persevere and see if I can come up with anything else. In the mean time at least I've got all my current files copied over to the HDD. It'll do for now.

Thanks for all your help.

---

### Post by Famine3h on 2008-07-08
> **amak79 said:**
> Famine3h,

If your config.xml is the same as csk's then it should work. Are you modifying the correct config.xml? MediaTomb uses ~/.mediatomb/config.xml when started manually in a terminal by your user. If you start MediaTomb via the init script at boot, then it uses /etc/mediatomb/config.xml.

[b][color=indigo]I had a little time last night...

1. Replace config.xml file with csk's, copy and pasted. /etc/mediatomb/config.xml - no problem. ~/.mediatomb/config.xml - no such directory... Oooooookie dokie. Delete all files from Mediatomb.

2. Reset PC. Reset PS3 - search for Media Servers, none found. Good.

3. Start up MediaTomb from Terminal. PS3 finds Mediatomb instantly. No files.

4. Add photos to Mediatomb. PS3 detects photos instantly, displays normally.

5. Add music to Mediatomb. PS3 detects music instantly, displays "Unsupported Data" for all. These music files work on default Mediatomb install *and* when stored locally on PS3 *and* when Windows machines used as media servers.

6. Add videos to Mediatomb. PS3 detects video instantly, displays "Unsupported Data" for all. These video files work when stored locally on PS3 *and* when Windows machines used as media servers.

7. Reset PS3. MediaTomb Music and Video still displayed as Unsupported Data after reset.

8. Delete all files from MediaTomb. Set MediaTomb to run from startup. Reset PC. Reset PS3.

9. Steps 3-6 again, but without manually starting MediaTomb. Same result.


Normally, I'd say this was just me being a stupid - I've never used Linux before. But of the two people in this thread who've tried that config.xml file, all of them have met with a lack of function. And indeed a loss of function - my music files worked just fine before and now they don't.

So, if there's anyone out there with a MediaTomb config.xml *known* to work with 8.04 and PS3 Firmware 2.40 *please*, for the love of granola, post it up in full. I'm going to start hitting the dog soon - and I don't have a dog so I'll have to go and buy one specifically to beat it. That or I'll move back to Windows (which may be worse than premeditated animal abuse).[/color][/b]

---

### Post by amak79 on 2008-07-08
Famine3h,

I recommend you don't use other peoples configs as it just creates even more problems when you don't understand exactly how to set it up. The best way is to start from a clean install, so remove MediaTomb with **sudo apt-get --purge autoremove mediatomb**. Make sure to delete the **/etc/mediatomb** and **~/.mediatomb** directories if they still exist. Now re-install MediaTomb. You will notice that MediaTomb is running and will also start automatically at boot. You can check if it's running with **ps -A | grep mediatomb**. If it isn't running check **/var/log/mediatomb** for any errors or warnings.

I suspect the problem your having when using **/etc/mediatomb/config.xml** and starting at boot is that MediaTomb is binding to the wrong interface. MediaTomb needs to be on the same network as the PS3, so try setting the **INTERFACE** variable in **/etc/default/mediatomb** to the correct interface. Now restart MediaTomb with **sudo /etc/init.d/mediatomb restart**.

Now edit **/etc/mediatomb/config.xml** and set the **protocolInfo** tag **extend** attribute to **yes**. For DivX support add **<map from="avi" to="video/divx"/>** to the **<extension-mimetype>** section and **<treat mimetype="video/divx" as="avi"/>** to the **<mimetype-contenttype>** section. Now restart MediaTomb and import your media files.

If the PS3 fails to play your DivX files then you need to enable transcoding. For this you will need to add **<transcode mimetype="video/divx" using="vlcmpeg"/>** to the **<mimetype-profile-mappings>** section. You also need to set the **transcoding** tag **enabled** attribute to **yes**, and also enable the **vlcmpeg** profile by setting it's **enabled** attribute to **yes**. You will then need to install VLC with **sudo apt-get install vlc**. Now restart MediaTomb  with **sudo /etc/init.d/mediatomb restart**.

You don't need to restart your PS3 all the time. You can just click "Search for Media Servers" in the XMB and after about 2-3 seconds you can press cancel and MediaTomb be "refreshed".

If you still can't get it to work then I suggest you try the MediaTomb IRC channel and ask for help.

---

### Post by Famine3h on 2008-07-08
> **amak79 said:**
> Famine3h,

I recommend you don't use other peoples configs as it just creates even more problems when you don't understand exactly how to set it up.

**[color=indigo]:lol: No arguments there![/color]**

> **amak79 said:**
> **idiotproof instructions**

**[color=indigo]Good stuff. I'll give it a whirl after I've finished moving house next week. Cheers.[/color]**

---

### Post by jowens on 2008-07-17
Hey, this might be too little too late but I just pulled down mediatomb this evening and while setting it up had similar issues as what you are reporting.


I'd bet that if you removed or commented out the line "<treat mimetype="video/x-msvideo" as="avi"/>" from your config you would find the divx files to begin working after one more cleaning of the database.


If that doesn't work out.  From bottom to top here the steps I took to get it installed:

Added the following packages as recommended as requirements by the guys over at the Mediatomb website:
```
sudo apt-get install mediatomb libexpat1 libexpat1-dev zlib1g zlib1g-dev zlibc libmagic-dev libmagic1 spidermonkey-bin libid3-3.8.3-dev libid3-3.8.3c2a libid3tag0 libexif-dev libexif-gtk-dev libexif-gtk5 libexif12 curl ffmpeg libextractor-plugins libextractor-dev libextractor1c2a

```

Changed value for protocolInfo to "yes" in the <server> section:
```
<protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->

```

Added divx line to the <mappings> section (or uncomment if preferred):
```
<map from="avi" to="video/divx"/>

```

Commented msvideo out of the section <mimetype-contenttype>
```
<!-- <treat mimetype="video/x-msvideo" as="avi"/> -->

```

After which, I just headed into the web UI and removed all files and did one last restart of the server.  Voila.

PS: It's worth noting that you most likely don't need all of the packages I installed per the recommendations in the mediatomb documentation, however I'm lazy and don't care to figure out what options the maintainer did or didn't compile into the repository version.

---

### Post by poop rooster on 2008-07-23
> **amak79 said:**
> 
(Step by step instructions)


Thank you so much for this. I followed it verbatim, and it "just worked" - I was very pleased when it was up + working within 10 minutes of finding your post.

There's one thing that's kind of a nuisance, though - it doesn't seem like new files added to my shared directories (adding files through regular system use, cp/mv or a 'net download) are being automatically added to the MediaTomb database. MediaTomb's readme ([http://mediatomb.cc/readme.txt](http://mediatomb.cc/readme.txt)) says that it supports inotify ... but I'm not sure how to determine whether or not this is enabled by default when it's installed via aptitude/dpkg. 

I'm very new to Ubuntu (just installed it on my desktop on Monday), but I've been a Linux user for about 5 years (recent Gentoo convert). So, I know very little about how aptitude/dpkg works, or "the Ubuntu way" of doing things.

Edit:

Figured out how to view the dependencies of packages via aptitude. It doesn't look like inotify is specifically listed as a dependency, but I also saw that inotify doesn't seem to be a package that can be installed via aptitude. I would guess it's already supported by the kernel, since I can install other packages which rely on it (tried 'inotail' as a quick test).

```

$ aptitude show mediatomb
Depends: iceweasel | firefox | www-browser, mediatomb-daemon (>= 0.11.0-1ubuntu1)

$ aptitude show mediatomb-daemon
Depends: adduser (>= 3.34), mediatomb-common (>= 0.11.0-1ubuntu1)

$ aptitude show mediatomb-common
Depends: libavformat1d (>= 0.cvs20070307), libavutil1d (>= 0.cvs20070307), libc6 (>= 2.7-1), libcurl3-gnutls (>= 7.16.2-1), libexif12, libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1-21), libkrb53 (>= 1.6.dfsg.2), libmagic1, libmozjs0d (>= 1.8.1.5), libmysqlclient15off (>= 5.0.27-1), libsqlite3-0 (>= 3.4.2), libstdc++6 (>= 4.1.1-21), libtag1c2a (>= 1.4), zlib1g (>= 1:1.2.3.3.dfsg-1)

```

So, inotify is already running on my setup - I guess the next task is to figure out how to get MediaTomb to actually use it. Didn't see anything in /etc/mediatomb/config.xml which mentions inotify, but I'll keep poking around.

Edit 2:

Reading the readme (fancy that), I found where inotify is explained. Directly below the 
"<import hidden-files="no">" line, I added

```

    <autoscan use-inotify="auto">
      <directory location="/junk" mode="inotify" level="full" recursive="yes" hidden-files="no"/>
    </autoscan>

```

I'm not sure if the autoscan section needs to be added within the 'import' section or not ... still trying to figure it out.

I'm making progress though, since now when I run a 'inotail -f /var/log/mediatomb.log', I see an error message thrown about inotify:

```

2008-07-23 23:09:46   ERROR: Inotify thread caught exception: Permission denied

```

So at least I'm getting closer.

---

### Post by amak79 on 2008-07-24
[QUOTE=poop rooster]I'm not sure if the autoscan section needs to be added within the 'import' section or not ... still trying to figure it out.[/QUOTE]

You don't really need to add an autoscan section this way as you can do it via the MediaTomb interface.

[QUOTE=poop rooster]I'm making progress though, since now when I run a 'inotail -f /var/log/mediatomb.log', I see an error message thrown about inotify:[/QUOTE]

You need to make sure all your files and directories have the correct permissions. You can change the directory permissions by running: **find /path/to/directory -type d -exec chmod 755 {} \;** and to change the permissions of the  files run: **find /path/to/directory -type f -exec chmod 644 {} \;**

---

### Post by amak79 on 2008-07-24
[QUOTE=poop rooster]I'm very new to Ubuntu (just installed it on my desktop on Monday), but I've been a Linux user for about 5 years (recent Gentoo convert).[/QUOTE]

If you ever decide to use Gentoo again, there is a nice MediaTomb [Wiki]("http://en.gentoo-wiki.com/wiki/MediaTomb") to help you get started.

---

### Post by poop rooster on 2008-07-24
> **amak79 said:**
> You don't really need to add an autoscan section this way as you can do it via the MediaTomb interface.


Yeah, I saw that button once I was back in the UI trying to figure out whether or not the files I'd just copied populated into the database. D'oh.


> 
You need to make sure all your files and directories have the correct permissions. You can change the directory permissions by running: **find /path/to/directory -type d -exec chmod 755 {} \;** and to change the permissions of the  files run: **find /path/to/directory -type f -exec chmod 644 {} \;**

I'll look at this when I get home tonight. Thanks for your help!

Edit:

Setting the permissions worked like a charm.  Thanks again!

And the final task is getting MKV and MPG/MPEG format videos streaming properly ... that's a job for the weekend, though.

---

### Post by javaguru on 2008-07-29
after a while of fiddling, I realized that when you run mediatomb, if you don't have a config file in your home dir, it creates a .mediatomb subdirectory, with config and database files in it. 

Unfortunately, the main config file in /etc/mediatomb/config.xml isn't copied to the new user config file, which means that whatever settings you may have done on the main config, are not duplicated in each users config file.

It would seem illogical to have this as wanted behavior. So for you PS3 people out there, that's why you get "Unsupported data" on the TV 

/adrian

---

### Post by illmortal on 2008-08-21
I'm having a similar problem, except this has to do with MP3s. 

I just installed Kubuntu and one of the first things I added was the Kubuntu restricted codecs then installed mediatomb. 

PS3 sees the media server, shows all the folders that were specified but PS3 shows all my files as, "unsupported data". 

Is there anything I need to install onto Kubuntu or modify the conf file for MediaTomb to work properly?

---

### Post by clatter on 2008-08-21
Check the mp3 tags. If your files have V2 tags, the PS3 does not support them. I ran into this, ran the audio tag tool to copy the V2 tags to the V1 tags and all was well.
Hope this helps

---

### Post by illmortal on 2008-08-22
> **clatter said:**
> Check the mp3 tags. If your files have V2 tags, the PS3 does not support them. I ran into this, ran the audio tag tool to copy the V2 tags to the V1 tags and all was well.
Hope this helps

Thanks clatter! Did the trick!

---

### Post by stearic on 2008-12-21
The thing though about transcoding though, is that it does every avi file. Not the ones that aren't "compatible" though. So every file gets transcoded when they don't need to be.

---

### Post by nannus on 2009-01-03
Not quite.
Add this code in the profile-section in config.xml
```
<avi-fourcc-list mode="ignore">
<fourcc>DX50</fourcc>
<fourcc>XVID</fourcc>
</avi-fourcc-list>
```
MT will now transcode only the avi's that's not supported by the PS3.

---

### Post by fastpakr on 2009-04-07
> **amak79 said:**
> You need to make sure all your files and directories have the correct permissions. You can change the directory permissions by running: **find /path/to/directory -type d -exec chmod 755 {} \;** and to change the permissions of the  files run: **find /path/to/directory -type f -exec chmod 644 {} \;**

Sometime between last night and this morning I started getting the same error (ERROR: Inotify thread caught exception: Permission denied).  I've verified that I have 755 permissions on the following:
/usr/bin/mediatomb
/var/run/mediatomb.pid
/var/log/mediatomb.log
/etc/init.d/mediatomb
/etc/default/mediatomb
/etc/mediatomb/config.xml
As well as any monitored data folders.  What am I missing?  I can't figure out what it doesn't have access to.

---

### Post by llimaa on 2009-10-15
Right is...
video/x-divx and not video/divx 

Have Fun!

---

### Post by vladiny on 2009-12-12
Has anyone gotten MKV to stream on PS3. I am still getting unsupported data. I have looked everywhere for this and can't find an answer. If anyone has it working, please let me know. Thanks!

My config:

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
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
    <udn>uuid:c334d802-e148-47b0-b8b1-890e2480e9af</udn>
    <home>/home/vladi/.mediatomb</home>
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
	<map from="avi" to="video/x-divx"/>
	<map from="divx" to="video/x-divx"/>
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
        <!-- Uncomment the line below for PS3 divx support -->
        <!-- <map from="avi" to="video/divx"/> -->
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
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <!-- Make sure to setup a transcoding profile for flv -->
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

---

### Post by encore2097 on 2009-12-16
I got MKV transcoding working, but unfortunately its still slightly out of sync and there are no subtitles since it uses ffmpeg.
[I]
/etc/mediatomb/config.xml[/I]
```

      <extension-mimetype ignore-unknown="no">
       ...
        <map from="mkv" to="video/x-matroska"/>
       ...
      </extension-mimetype>

      <mimetype-contenttype>
       ...
        <treat mimetype="video/x-mkv" as="mkv"/>
       ...
      </mimetype-contenttype>

 <mimetype-profile-mappings>
      ...
      <transcode mimetype="video/x-matroska" using="video-generic"/>
      ...
 </mimetype-profile-mappings>

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
       <agent command="mediatomb-video-generic" arguments="%in %out"/>
       <buffer size="1048576" chunk-size="26214" fill-size="52428"/>
     </profile>

```*/usr/bin/mediatomb-video-generic*
```

#!/bin/bash
INPUT="$1"
OUTPUT="$2"
VIDEO_CODEC="mpeg2video"
VIDEO_BITRATE="4096k"
AUDIO_CODEC="mp2"
AUDIO_BITRATE="192k"
AUDIO_SAMPLERATE="48000"
AUDIO_CHANNELS="2"
FORMAT="dvd"

exec /usr/bin/ffmpeg -threads 2 -i "${INPUT}" -vcodec ${VIDEO_CODEC} -b ${VIDEO_BITRATE} \
-acodec ${AUDIO_CODEC} -ab ${AUDIO_BITRATE} -ar ${AUDIO_SAMPLERATE} -ac ${AUDIO_CHANNELS} \
-f ${FORMAT} - > "${OUTPUT}" 2>/dev/null

```

---

### Post by Morales2k on 2010-01-05
encore2097: Thanks for posting your solution. That also worked for me. It does work for more than just mkv, as I have tried it with flv, avi (unsupported h.264 by dattebayo fansubs) and it transcodes fine.

However, I noticed that some PS3 functions are disabled (probably due to the way transcoding is done?) seek is not working, also if I press circle to exit, and enter again, it starts from the beginning, so there is no semi-permanent file copy being made/stored? I keep reading about multicast... maybe that has something to do with all this? Well, for me, this is better than what I had before (absolutly nothing). This was an interesting way of getting it to work... Now... I can go watch some videos... HD style hehe, I added one more thing to your command file in usr/bin... the attribute aspect, one can set 16:9 if desired... for flv it sucks, however, if we add it from the config.xml with $3 we could make it optional... like, depending on what we are transcoding, we could set an aspect ratio... I don't know much on coding, but heck... one has to learn one way or another huh... 

:popcorn:I'ma watch some anime with my kids now... hehehe they got me hooked with naruto and bleach... >_<

---

### Post by encore2097 on 2010-01-06
> **Morales2k said:**
> encore2097: Thanks for posting your solution. That also worked for me. It does work for more than just mkv, as I have tried it with flv, avi (unsupported h.264 by dattebayo fansubs) and it transcodes fine.

However, I noticed that some PS3 functions are disabled (probably due to the way transcoding is done?) seek is not working, also if I press circle to exit, and enter again, it starts from the beginning, so there is no semi-permanent file copy being made/stored? I keep reading about multicast... maybe that has something to do with all this? Well, for me, this is better than what I had before (absolutly nothing). This was an interesting way of getting it to work... Now... I can go watch some videos... HD style hehe, I added one more thing to your command file in usr/bin... the attribute aspect, one can set 16:9 if desired... for flv it sucks, however, if we add it from the config.xml with $3 we could make it optional... like, depending on what we are transcoding, we could set an aspect ratio... I don't know much on coding, but heck... one has to learn one way or another huh... 

:popcorn:I'ma watch some anime with my kids now... hehehe they got me hooked with naruto and bleach... >_<

You welcome. The PS3 functions won't work because its a live transcode, as far as forcing 16:9 you could do that, this script simply maintains the aspect ratio of the file.

---

### Post by fiction_edge on 2010-10-03
Hi everyone
I've tried all the above and I still get videos that are "unsupported data" or have no sound in my PS3
Here's my config.xml

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
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:dd1385c5-0847-43a2-a1d7-469e2ce3e26a</udn>
    <home>/home/vasco/.mediatomb</home>
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
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
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
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/divx" as="avi"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <!-- Make sure to setup a transcoding profile for flv -->
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

Thanx for your help in advance

---

### Post by leonardox on 2011-01-12
I can see the folders and the names of the mp3 and photos but I cant play mp3 or videos, it says there is no images.

Does anyone can post a config.xml that works and the scripts, please and thank you.

---

### Post by mekulot on 2011-02-19
try this: 
<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd">
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:15d20fb9-4daf-48b2-9520-69dc40ed44e8</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>host</host>
        <database>database</database>
        <username>username</username>
        <password>password</password>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/>
    <pc-directory upnp-hide="no"/>
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="yes">
        <thumbnail-size>160</thumbnail-size>
        <seek-percentage>10</seek-percentage>
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
      <lastfm enabled="no">
        <username>username</username>
        <password>password</password>
      </lastfm>
    </extended-runtime-options>
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
        <map from="avi" to="video/divx"/>
        <map from="mp4" to="video/mp4"/>
    <map from="avi" to="video/x-matroska"/>
        <map from="m2ts" to="video/avc"/>
        <map from="m4a" to="audio/mp4"/>
        <map from="m4v" to="video/mp4"/>
        <map from="cr2" to="image/raw"/>
        <map from="nef" to="image/raw"/>
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="video/ogg" as="ogg"/>
        <treat mimetype="audio/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="video/divx" as="avi"/>
      </mimetype-contenttype>
    </mappings>
    <online-content>
      <YouTube enabled="no" refresh="28800" update-at-start="yes" purge-after="604800" racy-content="exclude" format="mp4" hd="no">
        <favorites user="NationalGeographic"/>
        <playlists user="PlayStation"/>
        <uploads user="Google"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
    </online-content>
  </import>
  <transcoding enabled="yes">
    <mimetype-profile-mappings>
      <transcode mimetype="audio/ogg" using="audio2pcm"/>
      <transcode mimetype="video/mp4" using="video2mpeg"/>
      <transcode mimetype="audio/x-flac" using="audio2pcm"/>
      <transcode mimetype="video/ogg" using="video2mpeg"/>
      <transcode mimetype="video/quicktime" using="video2mpeg"/>
      <transcode mimetype="video/x-flv" using="video2mpeg"/>
      <transcode mimetype="video/x-matroska" using="video2mpeg"/>
      <transcode mimetype="image/raw" using="raw2jpeg"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="audio2pcm" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <sample-frequency>44100</sample-frequency>
        <audio-channels>2</audio-channels>
        <agent command="vlc" arguments="%in -I dummy --sout=#transcode{acodec=s16b,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=raw,dst=%out} vlc://quit"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="video2mpeg" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <sample-frequency>48000</sample-frequency>
        <audio-channels>2</audio-channels>
          <agent command="mencoder" arguments="%in -o %out -ovc lavc -oac lavc -lavcopts vcodec=mpeg2video:vbitrate=4096:vrc_minrate=0:vrc_maxrate=9800:vrc_buf_size=1835:keyint=15:vstrict=0:acodec=mp2:abitrate=192 
-vf harddup -af lavcresample=48000:channels=2 -srate 48000 -ofps 25 -of mpeg -mpegopts format=mpeg2:tsaf"/>

        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile>
      <profile name="raw2jpeg" enabled="no" type="external">
        <mimetype>image/jpeg</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <agent command="/usr/local/bin/mediatomb-raw2jpeg" arguments="%in %out"/>
        <buffer size="524288" chunk-size="512" fill-size="1024"/>
      </profile>
    </profiles>
  </transcoding>
</config>


This works for me except for h264 avi's.. anyone?

---

