---
title: "MediaTomb shuts down when trying to view on TV"
date: 2011-09-06
forum: Multimedia Software
---

### Post by Jonners59 on 2011-09-06
I have an LG Infinia 42LE8900 Tv connected to my LAN.  I have a PC running 11.04 with a hard drive that I share content on the LAN.  The PC uses MediaTomb for the DNLA that the Tv requires..

I have it set up and it worked fine for about 24hrs.  Now, every time I try and view the media from the Tv the MediaTomb shuts down and has to be re-launched from the PC.

Any ideas, please?

---

### Post by BicyclerBoy on 2011-09-06
It's crashing..
I would launch the program from terminal so you can observe stdout.
You can likely raise the verbosity with cmdline options.
Check for log files for the program or general stuff in /var/log/ etc

Could be crashing when transcoding..

Can you try another DLNA client or different media formats ?

---

### Post by Jonners59 on 2011-09-07
> **BicyclerBoy said:**
> It's crashing..
I would launch the program from terminal so you can observe stdout.
You can likely raise the verbosity with cmdline options.
Check for log files for the program or general stuff in /var/log/ etc

Could be crashing when transcoding..

Can you try another DLNA client or different media formats ?

BicyclerBoy
many thanks for the reply....  Sorry, but can you give me the text I need to put in cmd line to run these tests.  I'm not a techie, so I don't know what to do.

---

### Post by BicyclerBoy on 2011-09-07
Your mediatomb normally runs as a demonised process (background no GUI).

After mediatomb has crashed:
open a terminal (X server screen terminal)
& run
mediatomb --debug

it may have a --help cmdline option..

---

### Post by Jonners59 on 2011-09-09
```
3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd">
  <!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes" poll-when-idle="no" poll-interval="2">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    <items-per-page default="25"><option>10</option><option>25</option><option>50</option><option>100</option></items-per-page></ui>
    <name>MediaTomb</name>
    <udn>uuid:2835a0ae-6751-438b-8e0c-e1fc830eefd7</udn>
    <home>/home/server/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage caching="yes">
      <sqlite3 enabled="yes">
        <database-file>/home/server/.mediatomb/mediatomb.db</database-file>
      <synchronous>off</synchronous><on-error>restore</on-error><backup enabled="no" interval="600"/></sqlite3>
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
  <tmpdir>/tmp/</tmpdir><servedir></servedir><pc-directory upnp-hide="no"/><interface></interface><ip></ip><bookmark>mediatomb.html</bookmark><modelName>MediaTomb</modelName><modelDescription>Free UPnP AV MediaServer, GNU GPL</modelDescription><modelNumber>0.12.1</modelNumber><serialNumber>1</serialNumber><manufacturerURL>http://mediatomb.cc/</manufacturerURL><presentationURL append-to="none"></presentationURL><upnp-string-limit>-1</upnp-string-limit><port>0</port><alive>1800</alive></server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <virtual-layout type="builtin"/>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no" case-sensitive="no">
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
  <filesystem-charset>UTF-8</filesystem-charset><metadata-charset>UTF-8</metadata-charset><playlist-charset>UTF-8</playlist-charset><autoscan use-inotify="auto"/><library-options><libexif><auxdata></auxdata></libexif><id3><auxdata></auxdata></id3></library-options><magic-file></magic-file></import>
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
2011-09-09 11:47:44   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 0 -> 1
2011-09-09 11:47:44   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 1 -> 2
2011-09-09 11:47:44   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 2 -> 3
2011-09-09 11:47:44   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 3 -> 4
2011-09-09 11:47:44   DEBUG: [../src/server.cc:118] upnp_init(): start
2011-09-09 11:47:44   DEBUG: [../src/storage/sqlite3/sqlite3_storage.cc:442] waitForTask(): SQLITE3: (1) no such table: mt_internal_setting
Query:SELECT "value" FROM "mt_internal_setting" WHERE "key"='db_version' LIMIT 1
error: no such table: mt_internal_setting
2011-09-09 11:47:44 WARNING: Sqlite3 database seems to be corrupt or doesn't exist yet.
2011-09-09 11:47:44    INFO: no sqlite3 backup is available or backup is corrupt. automatically creating database...
2011-09-09 11:47:44    INFO: database created successfully.
2011-09-09 11:47:44   DEBUG: [../src/storage/sqlite3/sqlite3_storage.cc:190] init(): db_version: 3
2011-09-09 11:47:44   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 4 -> 5
2011-09-09 11:47:44    INFO: Initialized port: 49152
2011-09-09 11:47:44    INFO: Server bound to: 192.168.1.50
2011-09-09 11:47:44   DEBUG: [../src/server.cc:203] upnp_init(): webroot: /usr/share/mediatomb/web
2011-09-09 11:47:44   DEBUG: [../src/upnp_xml.cc:200] UpnpXML_RenderDeviceDescription(): start
2011-09-09 11:47:46   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 5 -> 6
2011-09-09 11:47:46   DEBUG: [../src/update_manager.cc:291] staticThreadProc(): starting update thread... thread: 107570944
2011-09-09 11:47:46   DEBUG: [../src/storage/sql_storage.cc:1815] updateAutoscanPersistentList(): setting persistent autoscans untouched - scanmode: timed;
2011-09-09 11:47:46   DEBUG: [../src/storage/sql_storage.cc:1826] updateAutoscanPersistentList(): updating/adding persistent autoscans (count: 0)
2011-09-09 11:47:46   DEBUG: [../src/storage/sql_storage.cc:1815] updateAutoscanPersistentList(): setting persistent autoscans untouched - scanmode: inotify;
2011-09-09 11:47:46   DEBUG: [../src/storage/sql_storage.cc:1826] updateAutoscanPersistentList(): updating/adding persistent autoscans (count: 0)
2011-09-09 11:47:46   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 6 -> 7
2011-09-09 11:47:46   DEBUG: [../src/singleton.cc:73] registerSingleton(): registering new singleton... - 7 -> 8
2011-09-09 11:47:46   DEBUG: [../src/autoscan_inotify.cc:65] AutoscanInotify(): Max watches on the system: 65536
2011-09-09 11:47:46    INFO: MediaTomb Web UI can be reached by following this link:
2011-09-09 11:47:46    INFO: http://192.168.1.50:49152/
2011-09-09 11:47:46   DEBUG: [../src/server.cc:311] upnp_init(): end
2011-09-09 11:47:46   DEBUG: [../src/timer.cc:67] triggerWait(): triggerWait. - 0 subscriber(s)
2011-09-09 11:47:46   DEBUG: [../src/timer.cc:98] triggerWait(): nothing to do, sleeping...
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_subscriptions.cc:52] process_subscription_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_subscriptions.cc:72] process_subscription_request(): end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 10 OFFSET 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:07   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:07   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:07   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:07   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:07   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_subscriptions.cc:52] process_subscription_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_subscriptions.cc:72] process_subscription_request(): end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 10 OFFSET 0
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-09 12:08:36   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-09 12:08:36   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-09 12:08:36   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-09 12:08:36   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-09 12:08:36   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0

```

No still not working, though it has moved on.  It NOW seems to open the Mediatomb on the Tv, but it is empty.....

---

### Post by BicyclerBoy on 2011-09-09
I have never used mediatomb but maybe you have to run the foreground process or some setup program **once** to create/config the database..

There are database errors in the log file..
What does the webserver interface tell you about database/media collection ?

Did you install from source code or from package management (synaptic) ?
Package management should run install scripts that setup the application..

---

### Post by Jonners59 on 2011-09-11
Bit of an update:
After running debug - When I went in via the Tv the first time, the folders were empty.  I then went in via the browser and the server was empty too.  I then reset the folders in the server via the browsed....  After a day all the pictures appeared when viewing via the Tv. (Caveat - sometimes it shows a folder called PC Directory and no content, but all in all it works).

Video and Music shows no content via the Tv.


> **BicyclerBoy said:**
> I have never used mediatomb but maybe you have to run the foreground process or some setup program **once** to create/config the database..


I can't remember exactly, but it was part of the install process.  It seems to have two directories.  One if a replication of the server directories, the second is the shared director.  During install it craetes the config file and the directories.

> **BicyclerBoy said:**
> 
There are database errors in the log file..
What does the webserver interface tell you about database/media collection ?


Shows the all media folders as captured.

> **BicyclerBoy said:**
> 
Did you install from source code or from package management (synaptic) ?
Package management should run install scripts that setup the application..
It is in Software Centre, but I found it in a search and it was not until after I had installed from source that i found a comment that it was part of the Ubuntu build.

---

### Post by Jonners59 on 2011-09-12
OK...  It has stopped again.

Debug report....

```
2011-09-12 11:51:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:51:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:51:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:51:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:51:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:51:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:51:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:51:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_subscriptions.cc:52] process_subscription_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_subscriptions.cc:72] process_subscription_request(): end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 10 OFFSET 0
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:05   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:05   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:05   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:05   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:05   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_subscriptions.cc:52] process_subscription_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_subscriptions.cc:72] process_subscription_request(): end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 10 OFFSET 0
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:08   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:08   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:08   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:08   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:08   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_subscriptions.cc:52] process_subscription_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_subscriptions.cc:72] process_subscription_request(): end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 10 OFFSET 0
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10    INFO: Exception: Object not found: 23143
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10    INFO: Exception: Object not found: 23143
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=0 LIMIT 1
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:10   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:10   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:10   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:10   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:10   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:11   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:11   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:11   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=0 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 5 OFFSET 0
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:11   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:11   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:11   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:11   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."id"=1 LIMIT 1
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:11   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0
2011-09-12 11:52:11   DEBUG: [../src/server.cc:362] upnp_callback(): start
2011-09-12 11:52:11   DEBUG: [../src/server.cc:444] upnp_actions(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:182] process_action_request(): start
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:45] upnp_action_Browse(): start
2011-09-12 11:52:11   DEBUG: [../src/storage/sql_storage.cc:785] browse(): QUERY: SELECT "f"."id","f"."ref_id","f"."parent_id","f"."object_type","f"."upnp_class","f"."dc_title","f"."location","f"."location_hash","f"."metadata","f"."auxdata","f"."resources","f"."update_id","f"."mime_type","f"."flags","f"."track_number","f"."service_id","rf"."upnp_class","rf"."location","rf"."metadata","rf"."auxdata","rf"."resources","rf"."mime_type","rf"."service_id","as"."persistent" FROM "mt_cds_object" "f" LEFT JOIN "mt_cds_object" "rf" ON "f"."ref_id"="rf"."id" LEFT JOIN "mt_autoscan" "as" ON "as"."obj_id"="f"."id"  WHERE "f"."parent_id"=1 ORDER BY ("f"."object_type"=1) DESC, "f"."dc_title" LIMIT 100 OFFSET 0
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:138] upnp_action_Browse(): end
2011-09-12 11:52:11   DEBUG: [../src/upnp_cds_actions.cc:209] process_action_request(): ContentDirectoryService::process_action_request: end
2011-09-12 11:52:11   DEBUG: [../src/server.cc:423] upnp_callback(): returning 0


```

---

### Post by Jonners59 on 2011-10-10
I discovered that when mediatomb---debug is run, that it creates a new config file! and it is accessed on a different port on the server (one number up from the default).

Once this is identified it is easy to go in to the new config and change the userbname and password and give the server a new name to id it.

Access then has to be done to set up the files and folders to view

That said, on reboot, debug must be run and the folders reset up!  And the old config also runs so needs to be ignored.  This is a pain, unless someone can tell me how to fix this.

Otherwise it works well.

---

