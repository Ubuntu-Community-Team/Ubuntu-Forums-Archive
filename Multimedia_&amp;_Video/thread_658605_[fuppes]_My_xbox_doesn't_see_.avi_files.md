---
title: "[fuppes] My xbox doesn't see .avi files"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by Spikextrem on 2008-01-04
Hi all,

my xbox see all folders on my filesystem. It can see and read all .wmv. But when I enter a folder with a .avi file my xbox doesn't see anything in the folder. 

Here is my config file.

```

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/mnt/sda1/Share/Video</dir>
    <dir>/mnt/sda1/Share/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>10001</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
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
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->


    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>

<description_values>
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values>


        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="mkv">
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

---

### Post by Spikextrem on 2008-01-05
*bump*

you can post your fuppes' config file if you can play those avi on your Xbox 360. :)

---

### Post by Spikextrem on 2008-02-25
*bump again*

Please someone, post a working xbox 360 config file

---

### Post by terry_gardener on 2008-02-25
try adding the following to file setting bit. 
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

so it looks like this: 

<file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="mkv">
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

save the cfg file and then restart the fuppes program and it should work. 

i haven't test this on the xbox360 but it is the same method that i used for the ps3. 

hope this helps.

---

### Post by ceaseoleo on 2008-02-27
This solution worked great, thanks.  Remeber to update database, and v container.

---

