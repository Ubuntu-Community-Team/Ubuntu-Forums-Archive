---
title: "Xbox 360 does not see computer"
date: 2011-05-30
forum: Multimedia Software
---

### Post by Super_Kam on 2011-05-30
Hello all!

I am having a problem with Xbox 360 and Ubuntu --- please note, I do NOT need help with uShare, Fuppes, Twonky, PS3 media server or setting up any of that right now. My problem is xbox does not SEE my computer at all. If I go into the media blade (video, music, etc), it does not have my computer listed.

I am connected with ICS - so I can log onto XBOX live fine - it connects to my network fine and I can go off and watch Netflix with no problems!

But when I do the test PC connection - it goes through green on the Network and then asks me to select a source for my computer, but it puts me in the PC NOT LISTED screen.

I have been searching for the forum and everyone else seems to be having problems with specifically connecting to the Internet or using a media server, but my xbox doesn't see the computer at all!

I have restarted my computer, then turned on my XBOX and linked it up, turned off my XBOX then back on again... all of my settings are set to automatic and seem to be coming in with no problems in terms of internet.

Any advice, links would be AMAZINGLY appreciated and I would be forever grateful.

Some background information - Acer Aspire One netbook, wired connection, dual boot with Windows 7 Starter. 

If you need anything else, please let me know! And for any instructions in terminal, please make it's clear as I am still learning. :)

Thank you SO much in advance!

---

### Post by Super_Kam on 2011-05-30
Bump... anyone? :)

---

### Post by cheekymonky2010 on 2011-06-05
Maybe if you try the gateway through the firewall!  

Allowing connections through a firewall
If you are using Ubuntu's UFW, you can easily add a rule to cope with this. Let's say your Xbox 360 uses a static IP address of 192.168.10.3, and your server is 192.168.10.2 with UPnP on port 49200. Use the following command to provide a small hole in your firewall for this:

Change the Ip address to that of your Xbox and PC of course.
 
here's the link: 

//help.ubuntu.com/community/Xbox360Media

---

### Post by blither on 2011-06-05
I just recently got my media server working with the 360.  I had a hard time getting fuppes to work to even display content.  I realize you said you did not need help with fuppes but in order for the 360 to pickup the computer you need to have either windows media center setup a server like fuppes.

Also, I have noticed that unless your files contain details like artist, title, album, etc. vfolders.cfg are relatively useless.  So I have used a small hack to correct it and to keep the files in the file structure of the system.

Along with fuppes you will need sqlite3 installed.

Once the fuppes.db has been built you should stop fuppes and run the following command with the sql script below.

```
cat fuppes_xbox.sql | sqlite3 fuppes.db
```

My recommendation is going with fuppes.  Here are my configurations that seem to be working for fuppes.

fuppes.cfg
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
 <shared_objects>
   <dir>/dir/to/files</dir>
 </shared_objects>

<network>
   <interface>eth0</interface>
   <http_port>1080</http_port>
   <allowed_ips>
     <!--<ip>192.168.0.1</ip>-->
   </allowed_ips>
 </network>
 <content_directory>
   <!--a list of possible charsets can be found under:
     http://www.gnu.org/software/libiconv/-->
   <local_charset>UTF-8</local_charset>
   <!--libs used for metadata extraction when building the database. [true|false]-->
   <use_imagemagick>true</use_imagemagick>
   <use_taglib>true</use_taglib>
   <use_libavformat>true</use_libavformat>
 </content_directory>
 <transcoding>
   <!--[lame|twolame]-->
   <audio_encoder>lame</audio_encoder>
   <!--[true|false]-->
   <transcode_vorbis>true</transcode_vorbis>
   <transcode_musepack>true</transcode_musepack>
   <transcode_flac>true</transcode_flac>
 </transcoding>
 <device_settings>
   <!--"default" settings are inhertied by specific devices and can be overwritten-->
   <device name="default">
     <!--specify the maximum length for file names (0 or empty = unlimited)-->
     <max_file_name_length>0</max_file_name_length>
     <!--[file|container]-->
     <playlist_style>file</playlist_style>
     <show_childcount_in_title>false</show_childcount_in_title>
     <enable_dlna>false</enable_dlna>
     <transcoding_release_delay>4</transcoding_release_delay>
     <file_settings>
       <!--audio files-->
       <file ext="mp3">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/mpeg</mime_type>
         <dlna>MP3</dlna>
       </file>
       <file ext="ogg">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>vorbis</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="mpc">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>musepack</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wav">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-wav</mime_type>
       </file>
       <file ext="flac">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-flac</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>flac</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wma">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-ms-wma</mime_type>
         <dlna>WMAFULL</dlna>
       </file>
       <!--image files-->
       <file ext="jpg">
         <ext>jpeg</ext>
         <type>IMAGE_ITEM</type>
         <mime_type>image/jpeg</mime_type>
         <convert enabled="false">
           <!--<dcraw enabled="true">-q 0</dcraw>-->
           <ext>png</ext>
           <mime_type>image/png</mime_type>
           <height>0</height>
           <width>0</width>
           <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
           <greater>false</greater>
           <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
           <less>false</less>
           <!--set "less" and "greater" to "false" if you always want to resize-->
         </convert>
       </file>
       <file ext="bmp">
         <type>IMAGE_ITEM</type>
         <mime_type>image/bmp</mime_type>
       </file>
       <file ext="png">
         <type>IMAGE_ITEM</type>
         <mime_type>image/png</mime_type>
       </file>
       <file ext="gif">
         <type>IMAGE_ITEM</type>
         <mime_type>image/gif</mime_type>
       </file>
       <!--video files-->
       <file ext="mpg">
         <ext>mpeg</ext>
         <type>VIDEO_ITEM</type>
         <mime_type>video/mpeg</mime_type>
       </file>
       <file ext="mp4">
         <type>VIDEO_ITEM</type>
         <mime_type>video/mp4</mime_type>
       </file>
       <file ext="avi">
         <type>VIDEO_ITEM</type>
         <mime_type>video/avi</mime_type>
       </file>
       <file ext="wmv">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-wmv</mime_type>
       </file>
       <file ext="vob">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-vob</mime_type>
       </file>
       <file ext="vdr">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-extension-vdr</mime_type>
         <transcode enabled="true">
           <ext>vob</ext>
           <mime_type>video/x-ms-vob</mime_type>
         </transcode>
       </file>
       <file ext="flv">
         <type>VIDEO_ITEM</type>
         <mime_type>application/x-flash-video</mime_type>
       </file>
       <file ext="asf">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-asf</mime_type>
       </file>
       <!--playlists-->
       <file ext="pls">
         <type>PLAYLIST</type>
         <mime_type>audio/x-scpls</mime_type>
       </file>
       <file ext="m3u">
         <type>PLAYLIST</type>
         <mime_type>audio/x-mpegurl</mime_type>
       </file>
     </file_settings>
   </device>
   <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
   <device name="PS3" enabled="false">
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <user_agent>PLAYSTATION3</user_agent>
     <!--<ip></ip>-->
     <enable_dlna>true</enable_dlna>
     <transcoding_release_delay>50</transcoding_release_delay>
     <file_settings>
       <file ext="ogg">
         <type>AUDIO_ITEM_MUSIC_TRACK</type>
         <transcode enabled="true">
           <http_encoding>stream</http_encoding>
         </transcode>
       </file>
     </file_settings>
   </device>
   <device name="Xbox 360" virtual="Xbox 360" enabled="true">
       <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
       <user_agent>Xenon</user_agent>
       <xbox360>true</xbox360>
       <file_settings>
           <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
           <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
           <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
       </file_settings>
<description_values>
<friendly_name>Our Collection</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values>
   </device>
   <device name="Telegent TG 100" virtual="default" enabled="false">
     <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <playlist_style>file</playlist_style>
     <max_file_name_length>101</max_file_name_length>
   </device>
 </device_settings>
</fuppes_config>

```

vfolder.cfg
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">
    <vfolder name="Video" id="2">
      <vfolder name="Folders" id="21">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
  </vfolder_layout>
</fuppes_vfolder_config>

```

fuppes_xbox.sql
```


DELETE FROM objects WHERE device='Xbox 360';

INSERT INTO objects (object_id,
                     detail_id,
                     type,
                     device,
                     path,
                     file_name,
                     title,
                     hidden)
     SELECT 4293918720 | object_id,
            detail_id,
            type,
            'Xbox 360',
            CASE WHEN type  = 1 THEN 'virtual'
                 WHEN type != 1 THEN path
            END,
            file_name,
            title,
            hidden
       FROM objects
      WHERE object_id<4293918720
        AND device IS NULL;

INSERT INTO objects (object_id,
                     type,
                     device,
                     path,
                     file_name,
                     title,
                     hidden)
     VALUES (2,
             1,
             'Xbox 360',
             'virtual',
             'Video',
             'Video',
             0);
INSERT INTO objects (object_id,
                     type,
                     device,
                     path,
                     file_name,
                     title,
                     hidden)
     VALUES (21,
             1,
             'Xbox 360',
             'virtual',
             'Folders',
             'Folders',
             0);


DELETE FROM map_objects WHERE device='Xbox 360';
INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     SELECT 4293918720 | object_id,
            CASE WHEN parent_id  = 0 THEN 21
                 WHEN parent_id != 0 THEN 4293918720 | parent_id
            END,
            'Xbox 360'
       FROM map_objects
      WHERE object_id<4293918720
        AND object_id NOT IN (0,21)
        AND device IS NULL;
INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     VALUES (2,
             0,
             'Xbox 360');
INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     VALUES (21,
             2,
             'Xbox 360');

```

---

