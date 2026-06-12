---
title: "fuppes trouble"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by linux newb on 2009-07-21
hey man, im havin some trouble with fuppes, but i will make it easy to help.
first off, my xbox and ps3 see fuppes, but i cant seem to get fuppes to recognize my wannabe shared folders (/home/ron/Music, and /home/ron/Videos)
and broadcast them over the network.
Can anyone tell me what to do to get this to work? I've been searching for painful hours for a cure.
here are my vfolder.cfg and fuppes.cfg files

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/ron/Videos</dir>
    <dir>/home/ron/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.64</interface>
    <!--empty or 0 = random port-->
    <http_port>5080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
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
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>true</use_fixed_uuid>
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
            <bitrate>140</bitrate>
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
          <convert enabled="true">
            <!--<dcraw enabled="false">-q 0</dcraw>-->
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
    <device name="PS3" enabled="true">
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
      <show_empty_resolution>true</show_empty_resolution>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>
```

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="true">

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
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolder>

      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>

      <vfolder name="Artist" id="6">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>

      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>

      <vfolder name="Genre" id="5">
        <vfolders property="genre">
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

  </vfolder_layout>

  <vfolder_layout device="Yamaha" enabled="true" create_references="true" >


    <vfolder name="Playlists" />

    <vfolder name="Artists">
      <vfolders property="artist">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Albums">
      <vfolders property="album">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Songs">
      <items type="audioItem" />
    </vfolder>

    <vfolder name="Genres">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```

Edit: I just noticed that some things dont look right when i accessed the server from my browser; and every single ext. has no transcoding, which is why i only copy/pasted one of them as well, it also says this like 20 million times when i rebuild the database:
ibfaad.so.0: cannot open shared object file: No such file or directory
[mpeg4aac @ 0xb79282f0]FAAD library: libfaad.so.0 could not be opened!
```
database status
Type	Count
object.container.storageFolder 	64
object.container.album.musicAlbum 	1
object.item.imageItem 	21
object.item.audioItem 	340
object.item.videoItem 	70
transcoding

Neither LAME nor TwoLame found. Transcoding disabled!
build options
option	enabled
iconv	true
uuid	false
taglib	false
imageMagick	false
libavformat (ffmpeg)	true
video transcoding (experimental)	false
lame	false
twolame	false
ogg/vorbis	false
musepack	false
flac	false
flac	false
system status

UUID: 35479649-aabb-dead-beef-1234eeff0000
device settings
device: default
release delay	4
file settings
ext: asf
dlna	
mime/type	video/x-ms-asf
upnp type	object.item.videoItem
no transcoding/resizing
```

---

### Post by linux newb on 2009-07-23
570 views and no one has anything to say about my problem? that's peculiar, cmon theres gotta be someone out here that knows about fuppes, Right?

---

### Post by fuzzman54 on 2009-09-03
I felt bad for viewing and not having an answer, because it pisses me off when a lot of people look at my threads and nobody even says anything. So as a temporary solution until someone helps you, I recommend Twonkymedia Server. You download the manual package and run the .sh and then the twonkymedia executable and you'll be up and running.

---

