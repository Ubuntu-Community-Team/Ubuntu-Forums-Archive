---
title: "Fuppes + 360 = No Playlists?"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Mr.Grim on 2008-05-08
Hey everyone,

I have Fuppes (SVN 611) up and running to stream media to my Xbox 360. Everything about it is working perfectly, except the 360 doesn't see any playlists. I've tried m3u and pls and neither of them work. Fuppes is able to see them because it says stuff like this:

[DONE] read shared directories
parse playlists
playlist id: 95
playlist id: 96
playlist id: 97
[DONE] parse playlists

but they don't show up anywhere in the 360.

Does anyone have experience with this stuff and knows what's going on?

Thanks!

```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/Videos</dir>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/home/grim/music</dir>
  </shared_objects>
  <network>
    <interface>eth0</interface>
    <http_port>8080</http_port>
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
    <!--do NOT remove the "default" device settings-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>true</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
      <enable_dlna>true</enable_dlna>
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
    <!--It is safe to remove unneeded devices-->
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <description_values>
        <friendly_name>Magnolia: The Linux Experiance</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
      <file_settings>
        <file ext="pls">
          <type>PLAYLIST</type>
        </file>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
      </file_settings>
    </device>
  </device_settings>
</fuppes_config>

```

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
      
      <vfolder name="Artists" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
        <vfolders property="album"  type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
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
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```

---

### Post by stewils on 2008-05-09
having similer problems.  can you stream avi to your xbox 360?
I've managed to get it work.  Try the config file here after updating to the latest build by following the instructions on the fuppes wiki.
Config file here:
[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37&p=449#p449](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37&p=449#p449)

---

### Post by Mr.Grim on 2008-05-09
> **stewils said:**
> having similer problems.  can you stream avi to your xbox 360?
I've managed to get it work.  Try the config file here after updating to the latest build by following the instructions on the fuppes wiki.
Config file here:
[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37&p=449#p449](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37&p=449#p449)

Yeah, I can stream just about every file type except mkv. 

Everything seems to be working great except my xbox doesn't read playlists for some reason.

---

