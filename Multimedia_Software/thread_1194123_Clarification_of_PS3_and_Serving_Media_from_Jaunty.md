---
title: "Clarification of PS3 and Serving Media from Jaunty Desktop"
date: 2009-06-22
forum: Multimedia Software
---

### Post by renzokuken on 2009-06-22
Firstly, apologies if i picked the wrong sub-forum for this.

I've finally got my grubby little mits on a shiny new Playstation 3 and was wondering what the situation is with accessing the videos/music/pictures stored on my jaunty desktop is?

I'm guessing its not as simple as using samba or NFS? what reading i have done seems to come back to Mediatomb and Fuppes, which are new to me and so i'm not entirely sure what the deal is. 

when using mediatomb or fuppes, does my desktop need to have its own wireless card or can it work through my router? (my current set-up is :- broadband connected to linksys router, to which my desktop is connected by ethernet, and my ps3 connects to it wirelessly).

any help explaining the situation and any clarification on the differences/pros/cons of mediatomb and fuppes would be massively appreciated.

thanks

---

### Post by hibliss on 2009-06-27
Install FUPPES and edit the fuppes.cfg file in your /home/user/.fuppes directory.

Here is mine:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
  <dir>/home/chris/Desktop/Unpacked</dir>
  <dir>/media/Backup2/Music</dir>
  <dir>/home/chris/Music</dir>
  </shared_objects>
  <network>
    <interface>192.168.2.2</interface>
    <http_port>33566</http_port>
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
    <device name="Xbox 360" virtual="Xbox 360" enabled="false"><description_values> 
      <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name> 
      <model_name>Windows Media Connect compatible (%s)</model_name> 
      <model_number>2.0</model_number> 
	  </description_values> 
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
    </device>
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
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

You have to fill in the local IP of your desktop under 
```

<interface>your IP</interface>
```

You can pick any port for 

```
<http_port>pick a high port to avoid conflicts</http_port>
```

You can add as many directories as you like under:
```

 <dir>whatever you want to share here</dir>
```

You don't need to fill in the <allowed_IPs></allowed_IPs> unless you are on a network where there may be people you do not want to share your content with.

Note also that my FUPPES.cfg file is setup to transcode files that the PS3 cannot play natively. It works for all files I have tried except for MKV containers.

You also need a vfolder.cfg file in the .fuppes directory. If it is not there, you can create it. Just use mine:

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
      <vfolder name="Folders" id="21" />
      <vfolder name="Genre" id="9" />
    </vfolder>
    <vfolder name="Browse Folders" id="21">  
<shared_dirs full_extend="true" />  
</vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```

After you have finished the setup, open terminal and type:

```
sudo fuppes
```

Now you are all set to stream music/pictures/movies to your PS3. You will get much better performance if you could plug your PS3 in to your router with an ethernet cable.

---

### Post by dragon99 on 2009-07-01
Only had mine a few days, wanted to do the same, and found the ps3 media server - java based s/w. Installed this server on Jaunty, & work pretty good. Very easy to install and use. It enables the ps3 to access all my network drives (ext3, fat32, & ntfs), including any usb external, and esata docks. Been testing only since yesterday, but plays just about any format I've thrown at it except matroska.

The server s/w can be downloaded from:
code.google.com/p/ps3mediaserver/

There's also a version of the server for windows available.

There's a couple of other linux based media servers for the ps3, but this one appealed to me as a new user of ps3 with limited knowledge of linux.

dragon

---

### Post by renzokuken on 2009-07-02
thanks for you replies both of you. in the end i just went ahead and tried MediaTomb which is running without any problems whatsoever.

should i not like it or it proves unreliable, i shall try both your suggestions

cheers

---

### Post by hibliss on 2009-07-02
I tried Mediatomb, but did not like the way it butchered the folder structure. Other than that it did a decent job and was exactly the same performance wise as FUPPES.

I have to say that having also tried PS3 Media Server, I was not impressed with it, and it chomped down about half my ram while streaming a movie, making my PC nearly unusable. Java makes it cross-platform compatible, but is otherwise not the best way to code something like this.

---

### Post by renzokuken on 2009-07-02
what do you mean when you say "butchered the folder structure".

on mine it lists all the videos/music/pics in a single endless list for each category (which is a stupid idea for lots of files), but there is also an option "PC Directory" which allows you to browse through the folder tree as you would normally on the actual pc

---

### Post by hibliss on 2009-07-02
> **renzokuken said:**
> what do you mean when you say "butchered the folder structure".

on mine it lists all the videos/music/pics in a single endless list for each category (which is a stupid idea for lots of files), 

This was the only option in the last version I tried. They must have implemented the regular folder tree in the newer version. Does it sort alphabetically?

---

### Post by renzokuken on 2009-07-02
i'm not in front of it now so couldnt say 100% but yes, i'm pretty sure it sorts alphabetically.

---

### Post by Mugwug on 2009-07-03
> **hibliss said:**
> This was the only option in the last version I tried. They must have implemented the regular folder tree in the newer version. Does it sort alphabetically?

Yep, sorts alphabetically and you can modify the config.xml file to eliminate the mangled directory stuff altogether, I believe it's as simple as adding the line;

```
<virtual-layout type="disabled">
```

More documentation here;

[http://mediatomb.cc/pages/documentation#id2537759](http://mediatomb.cc/pages/documentation#id2537759)
[]("http://mediatomb.cc/pages/documentation#id2537759")

---

### Post by chrisbloe on 2009-07-04
Check out this bad boy... it sorted out what I need in under 5 min with minimal config tweaks.

Not sure if it does everything yet, but well worth a look at:

[http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty](http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty)

---

### Post by hibliss on 2009-07-04
> **chrisbloe said:**
> Check out this bad boy... it sorted out what I need in under 5 min with minimal config tweaks.

Not sure if it does everything yet, but well worth a look at:

[http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty](http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty)

ushare is decent for native formats, but it's weakness is in transcoding.

---

### Post by QuePsiPhi on 2009-08-05
I just wanted to say THANK YOU!

---

### Post by leo5111 on 2009-08-06
have fun with fuppes or mediatomb. ill NEVER go back to em, install ubuntu tweak install, then XBMC with it and NEVER look back... :P:popcorn:.. once its installed run XBMC, go to settings tab, click on network tab and click on Upnp tab,click on autostart Upnp client,enable Upnp renderer and enable Upnp server, then to add youre videos, click manage Upnp shares,click add media shares, browse to youre videos, example cheers, then add another one airwolf etc, and yes you get folder seperation, cheers episodes are in cheers folder and airwolf episodes are in airwolf folder on ps3 no hair pulling to get program to install works great ....:popcorn:

---

