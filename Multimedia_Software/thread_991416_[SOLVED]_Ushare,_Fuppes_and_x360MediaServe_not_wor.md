---
title: "[SOLVED] Ushare, Fuppes and x360MediaServe not working since new Xbox experience"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Zanian on 2008-11-23
Hey,
I used x360MediaServe to stream music to my Xbox for a while.  However, since the new Xbox experience update, my Xbox won't recognize it.  I tried switching over to Fuppes and then Ushare, same problem.  Currently I'm working on getting Ushare working because it seems to do what I want.  Here is my configs:

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Ushare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/zander/music,/home/zander/movies

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=no




/etc/init.d/ushare
#!/bin/sh -e
#
# uShare init script
#
### BEGIN INIT INFO
# Provides:          ushare
# Required-Start:    $local_fs $syslog $network
# Should-Start:
# Required-Stop:
# Should-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: uShare
# Description:       uShare UPnP (TM) A/V & DLNA Media Server
#                    You should edit configuration in /etc/ushare.conf file
#                    See [http://ushare.geexbox.org](http://ushare.geexbox.org) for details
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/ushare
NAME=ushare
DESC="uShare UPnP A/V & DLNA Media Server"
PIDFILE=/var/run/ushare.pid
CONFIGFILE=/etc/ushare.conf

# abort if no executable exists
[ -x $DAEMON ] || exit 0

# Get lsb functions
. /lib/lsb/init-functions
. /etc/default/rcS

[ -f /etc/default/ushare ] && . /etc/default/ushare

checkpid() {
  [ -e $PIDFILE ] || touch $PIDFILE
}

check_shares() {
  if [ -r "$CONFIGFILE" ]; then
    . $CONFIGFILE
    [ -n "$USHARE_DIR" ] && return 0
  fi
  return 1
}

case "$1" in
  start)
    log_daemon_msg "Starting $DESC: $NAME"
    if ! $(check_shares); then
      log_warning_msg "No shares avalaible ..."
      log_end_msg 0
    else
      checkpid
      start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS --xbox
      log_end_msg $?
    fi
  ;;
  stop)
    log_daemon_msg "Stopping $DESC: $NAME"
    start-stop-daemon --stop --signal 2 --quiet --oknodo --pidfile $PIDFILE
    log_end_msg $?
  ;;
  reload|force-reload)
    log_daemon_msg "Reloading $DESC: $NAME"
    start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile $PIDFILE --exec $DAEMON
    log_end_msg $?
  ;;
  restart)
    $0 stop
    $0 start
  ;;
  *)
    N=/etc/init.d/$NAME
    log_success_msg "Usage: $N {start|stop|restart|reload|force-reload}"
    exit 1
  ;;
esac

exit 0


When I run ushare:

```
ushare -x
```

Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.0.100:49153
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/zander/music
Looking for files in content directory : /home/zander/movies
Found 3225 files and subdirectories.
Stopping UPnP Service ...

I've also tried running it through:

```
sudo /etc/init.d/ushare start
```

Same error

I've opened the port 49153 and I can access the web interface at myip:49153/web/ushare.html.  I thought maybe the problem was "Interface eth0 is down", but I read other threads that said this was not the problem.  If someone has a solution it would be much appreciated.  I really just want to stream music, videos are a bonus.  If you know that Ushare doesn't work with the new xbox experience, but something else that only streams music does, I wouldn't mind switching over.  I have fuppes and x360mediaserve all configured properly and ready to work if someone knows how to fix them instead.
Thanks

---

### Post by Zanian on 2008-11-23
I got ushare working, opening ports in ufw (apparently I use ufw...?).  I have a new problem, Ushare sucks.  it doesn't organize in folders and only displays 1000 files.  Maybe I'm missing something, if not, anyone know how I can fix fuppes?

Here's my fuppes.cfg:

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/zander/music</dir>
    <dir>/home/zander/movies</dir>
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>49153</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.200</ip>
      <ip>192.168.0.1</ip>
      <ip>192.168.0.100</ip>
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
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
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

It's the same deal, I can access the web interface but my Xbox just won't recognize it.
Thanks

---

### Post by PorchSong on 2008-11-24
Fuppes works--I have it up and running on my system with no problems.  rebuild your virtual folders "v"; and then rebuild your database "r".

---

### Post by Zanian on 2008-11-24
Hey Porch,
Funny, I used your Howto.  I tried that, no dice.  When I type v I get this:

[VirtualContainer] create virtual container layout started at Mon Nov 24 17:18:02 2008
CContentDatabase::Execute :: SQL error: attempt to write a readonly database, statement: 
CContentDatabase::Execute :: SQL error: attempt to write a readonly database, statement: 
CContentDatabase::Execute :: SQL error: attempt to write a readonly database, statement: 
CContentDatabase::Execute :: SQL error: attempt to write a readonly database, statement: 
== lib/ContentDirectory/ContentDatabase.cpp (391) :: Mon Nov 24 17:18:02 2008 ==
CContentDatabase::Insert - insert :: SQL error: attempt to write a readonly database
Statement: insert into MAP_OBJECTS (OBJECT_ID, PARENT_ID, DEVICE) values ( 1, 0, 'Xbox 360');

It repeats the == lib/Content etc... for a while and then says

[VirtualContainer] virtual container layout created at Mon Nov 24 17:18:02 2008

Also, here's my vfolder:

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

Would all this effect my Xbox from even recognizing fuppes?
Thanks

---

### Post by PorchSong on 2008-11-24
You are getting write errors.  Are you starting fuppes with console and "sudo fuppes".  You will not be able to update your virtual folders int he hidden directory without admin permissions hence the "sudo fuppes".  If that still does not work then start new.  Completely remove fuppes folder from system--that is your fuppes folder, not your .fuppes folder.  Then clean the system off by using my guide and start over.

[http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes](http://ubuntuforums.org/showthread.php?t=984325&highlight=fuppes)

After you get it all running again, replace your virtual folder with mine again and then update virtual folders "v" and "r" -- rebuild database, see how that goes.

---

### Post by Zanian on 2008-11-25
Thanks Porch, I got fuppes working.  Videos work, the only problem now, is that my music is organized under video library.  Anyway I can change this?

---

### Post by PorchSong on 2008-11-27
> **Zanian said:**
> Thanks Porch, I got fuppes working.  Videos work, the only problem now, is that my music is organized under video library.  Anyway I can change this?

Sorry, I do not stream my music over.

---

