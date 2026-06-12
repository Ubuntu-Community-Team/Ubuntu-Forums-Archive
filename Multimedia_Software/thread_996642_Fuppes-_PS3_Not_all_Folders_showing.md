---
title: "Fuppes- PS3 Not all Folders showing"
date: 2008-11-29
forum: Multimedia Software
---

### Post by timcee42 on 2008-11-29
Have been trying to fix my fuppes for about a week now and have read every post on here and on the fuppes site but am stuck. 
Problem is that only one of my folders shows up, movies folder. IT works fine with no problems. All other folders just dont show up. 
have posted fuppes.cfg file. 
as a side note i did reinstall it at one point and to be honest am unsure if it uninstall correctly before install.
Also i have confirmed all the permissions on the folder and they all seem fine. Can link to the web interface and when i rebuild the database only my 1 movie folder with 37 movies show up.
Installed on ubuntu 8.4.

Bit of a beginner, 2 months Ubuntu... config file below (etc/fuppes/fuppes.cfg)

<fuppes_config version="0.7.2.3">
      <shared_objects>
        <dir>/media/music1/music</dir>
	<dir>/media/music1/pictures</dir>
	<dir>/media/sda1/hd</dir>
	<dir>/media/sdc1/movies</dir>
	<dir>/media/sdd1/tv</dir>
	<dir>/media/sdg1/kids video/kids movies</dir>
	<dir>/media/sdg1/kids video/kids other vids</dir>
      </shared_objects>

      <network>
        <interface>192.168.2.2</interface>
        <http_port>2222</http_port>
        <allowed_ips>
          <!--<ip>192.168.0.1</ip>-->
        </allowed_ips>
      </network>
      <content_directory>
        <local_charset>UTF-16</local_charset>
      </content_directory>
      <global_settings>
        <temp_dir></temp_dir>
        <use_fixed_uuid>false</use_fixed_uuid>
      </global_settings>
      <device_settings>
        <device name="default">
            <description_values>
              <friendly_name>TroubleBox %v</friendly_name>
              <manufacturer>Ulrich Voelkel</manufacturer>
              <manufacturer_url>http://fuppes.ulrich-voelkel.de</manufacturer_url>
              <model_name>Media Service</model_name>
              <model_number>%v</model_number>
              <model_url>http://fuppes.ulrich-voelkel.de</model_url>
              <model_description enabled="true">Media Service</model_description>
              <upc enabled="true"/>
              <serial_number enabled="true">2534134</serial_number>
            </description_values>
          <max_file_name_length>0</max_file_name_length>
          <playlist_style>file</playlist_style>
          <show_childcount_in_title>false</show_childcount_in_title>
          <enable_dlna>false</enable_dlna>
          <transcoding_release_delay>4</transcoding_release_delay>
          <file_settings>
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
    <ext>wav</ext>
    <mime_type>audio/wav</mime_type>
    <dlna>WAV</dlna>
    <http_encoding>stream</http_encoding>
    <decoder>flac</decoder>
    <encoder>wav</encoder>
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
                <ext>png</ext>
                <mime_type>image/png</mime_type>
                <height>0</height>
                <width>0</width>
                <greater>false</greater>
                <less>false</less>
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
              <transcode enabled="true">
                <ext>mpg</ext>
                <mime_type>video/mpeg</mime_type>
                <transcoder>ffmpeg</transcoder>
                <video_codec>mpeg1video</video_codec>
                <audio_codec>mp2</audio_codec>
                <audio_samplerate>44100</audio_samplerate>
                <video_bitrate>1800000</video_bitrate>
              </transcode>
            </file>
            <file ext="asf">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-ms-asf</mime_type>
            </file>
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
        <device name="PS3" enabled="true">
          <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
          <user_agent>PLAYSTATION3</user_agent>
          <ip>192.168.2.4</ip>
          <enable_dlna>true</enable_dlna>
          <transcoding_release_delay>50</transcoding_release_delay>
          <file_settings>
           <file ext="avi">
             <type>VIDEO_ITEM</type>
             <mime_type>video/x-divx</mime_type>
           </file>
           <file ext="mpg">
            <ext>mpeg</ext>
             <type>VIDEO_ITEM</type>
              <mime_type>video/mpeg</mime_type>
           </file>
            <file ext="wmv">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-ms-wmv</mime_type>
            </file>
          <file ext="vob">
              <ext>mpeg</ext>
              <type>VIDEO_ITEM</type>
              <mime_type>video/mpeg</mime_type>
          </file>
	<file ext="mkv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-matroska</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
          </file_settings>
        </device>
      </device_settings>
    </fuppes_config>

---

### Post by timcee42 on 2008-12-03
Never mind, if you having any trouble with fuppes follow this guide. 
[http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes]("http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes")

Worked for me on 8.4

---

