---
title: "360 can't see fuppes"
date: 2009-09-09
forum: Multimedia Software
---

### Post by burntresistor on 2009-09-09
When I complied it the only command i was able to find was to get about half the codecs enabled in ./configure not sure how to get all of them enabled  when I add --enable-faad it bashes the command but some others are working fine.  Not sure what to put under the IP in fuppes.cfg because my address is dynamic 

 config.cfg
```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
<dir>/media/My Book/mkv and psp</dir>  
</shared_objects>
  <network>
<interface>eth1</interface>
<http_port>0</http_port>
<allowed_ips>
<ip>192.168.1.100</ip>
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
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
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
          <mime_type>video/x-msvideo</mime_type>
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
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
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

<description_values>
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values> 
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
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

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10" />
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21"> 
  <folders filter="contains(videoItem)" /> 
</vfolder>

      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```
This is the error I received in ./configure but I cant seem to find a solution for it 

```

format.so.0 -o .libs/libmetadata_libavformat.so.0.0.0
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libmetadata_libavformat.la] Error 1
make[1]: Leaving directory `/home/burntresistor/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```

---

### Post by burntresistor on 2009-09-11
BUMP I compied fuppes the way it says pressing  r  then v  and its not showing up in the output at all 
```

burntresistor@pandora-box:~$ fuppes
            FUPPES - 0.646
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://127.0.1.1:9000

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

[ContentDatabase] create database at Fri Sep 11 17:54:40 2009
read shared directories
[NULL @ 0x7913e0]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x7913e0]frame skip 8
    Last message repeated 1 times
[wmv3 @ 0x795d20]Extra data: 8 bits left, value: 0
[NULL @ 0x7913e0]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 24 times
[mpeg @ 0x77e6a0]pes_ext 5A is invalid
[mpeg @ 0x77e6a0]Could not find codec parameters (Audio: mp3, 0 channels, s16)
    Last message repeated 1 times
[mpeg @ 0x77e6a0]Could not find codec parameters (Video: 0x0000)
[mpeg @ 0x77e6a0]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x77e6a0]Could not find codec parameters (Video: h264)
[mpeg @ 0x77e6a0]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x77e6a0]pes_ext 5A is invalid
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases


``` 

I really want to get this working so I can stop relying on my windows os to run traveristy

---

### Post by burntresistor on 2009-09-12
Bump 

This is my check install. I got it off svn is there a older version I can get? I'm using jaunty

```

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

```

---

### Post by burntresistor on 2009-09-14
> **burntresistor said:**
> Bump 

This is my check install. I got it off svn is there a older version I can get? I'm using jaunty

```

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640
0.640" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

```

Bump

---

