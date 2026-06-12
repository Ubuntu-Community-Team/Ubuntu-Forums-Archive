---
title: "How to get to work with mpd icecast2"
date: 2010-04-14
forum: Multimedia Software
---

### Post by farhadsoft on 2010-04-14
Hello

Install icecast2 on Ubuntu  Server (on VPS) works fine with the SAM Broadcaster and others too. wanted to broadcast using mpd, but here's  the rub!
Runs without errors but  does not work.

```
root@radio:/# /etc/init.d/mpd restart
 * Stopping Music Player Daemon mpd
   ...done.
 * Starting Music Player Daemon mpd
   ...done.
``````
root@radio:/# netstat -na | grep -i listen | grep 6600
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN
``````
root@radio:/# ps -A|grep mpd
17651 ?        00:00:00 mpd
```But does not  broadcast in icecast2 and
```
root@radio:/# ncmpc --host=127.0.0.1 --port=6600 --password=*********
error [15]: timeout in attempting to get a response from "127.0.0.1" on port 6600
```[B]cat /etc/mpd.conf
[/B]```
# An example configuration file for MPD
# See the mpd.conf man page  for a more detailed description of each parameter.


# Files  and directories #######################################################
#
#  This setting controls the top directory which MPD will search to  discover the
# available audio files and add them to the daemon's  online database. This 
# setting defaults to the XDG directory,  otherwise the music directory will be
# be disabled and audio files  will only be accepted over ipc socket (using
# file:// protocol) or  streaming files over an accepted protocol.
#
music_directory          "/home/radio/audio"
#
# This setting sets the MPD internal  playlist directory. The purpose of this
# directory is storage for  playlists created by MPD. The server will use 
# playlist files not  created by the server but only if they are in the MPD
# format. This  setting defaults to playlist saving being disabled.
#
playlist_directory               "/home/radio/playlists"
#
# This setting sets the  location of the MPD database. This file is used to
# load the  database at server start up and store the database while the 
#  server is not up. This setting defaults to disabled which will allow
#  MPD to accept files over ipc socket (using file:// protocol) or  streaming
# files over an accepted protocol.
#
db_file                  "/var/lib/mpd/tag_cache"
# 
# These settings are the  locations for the daemon log files for the daemon.
# These logs are  great for troubleshooting, depending on your log_level
# settings.
#
#  The special value "syslog" makes MPD use the local syslog daemon. This
#  setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file                         "/var/log/mpd/mpd.log"
#
# This setting  sets the location of the file which stores the process ID
# for use  of mpd --kill and some init scripts. This setting is disabled by
#  default and the pid file will not be stored.
#
pid_file                         "/var/run/mpd/pid"
#
# This setting sets the location  of the file which contains information about
# most variables to get  MPD back into the same general shape it was in before
# it was  brought down. This setting is disabled by default and the server 
#  state will be reset on server start up.
#
state_file                       "/var/lib/mpd/state"
#
# The location of the sticker  database.  This is a database which
# manages dynamic information  attached to songs.
#
sticker_file             "/var/lib/mpd/sticker.sqlite"
#
###############################################################################


#  General music daemon options  ################################################
#
# This setting  specifies the user that MPD will run as. MPD should never run as
#  root and you may use this setting to make MPD change its user ID after
#  initialization. This setting is disabled by default and MPD is run as  the
# current user.
#
user                            "mpd"
#
#  This setting specifies the group that MPD will run as. If not specified
#  primary group of user specified with "user" setting will be used (if  set).
# This is useful if MPD needs to be a member of group such as  "audio" to
# have permission to use sound card.
#
#group                           "audio"
#
# This setting sets the address for  the daemon to listen on. Careful attention
# should be paid if this  is assigned to anything other then the default, any.
# This setting  can deny access to control of the daemon.
#
# For network
bind_to_address          "127.0.0.1"
#
# And for Unix Socket
#bind_to_address                 "/var/run/mpd/socket"
#
# This setting is the TCP  port that is desired for the daemon to get assigned
# to.
#
port                             "6600"
#
# This setting controls the  type of information which is logged. Available 
# setting arguments  are "default", "secure" or "verbose". The "verbose" setting
#  argument is recommended for troubleshooting, though can quickly stretch
#  available resources on limited hardware storage.
#
#log_level                       "default"
#
# If you have a problem with your  MP3s ending abruptly it is recommended that 
# you set this argument  to "no" to attempt to fix the problem. If this solves
# the problem,  it is highly recommended to fix the MP3 files with vbrfix
#  (available from <http://www.willwap.co.uk/Programs/vbrfix.php>),  at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback                    "yes"
#
# This setting enables MPD to create  playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists        "no"
#
# This setting defines a list of tag types that will  be extracted during the 
# audio file discovery process. Optionally,  'comment' can be added to this
# list.
#
#metadata_to_use         "artist,album,title,track,name,genre,date,composer,performer,disc"
#
#  This setting enables automatic update of MPD's database when files in 
#  music_directory are changed.
#
#auto_update    "yes"
###############################################################################


#  Symbolic link behavior  ######################################################
#
# If this  setting is set to "yes", MPD will discover audio files by following 
#  symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks         "yes"
#
# If this setting is set to "yes", MPD will  discover audio files by following
# symbolic links inside of the  configured music_directory.
#
#follow_inside_symlinks          "yes"
#
###############################################################################


#  Zeroconf / Avahi Service Discovery  ##########################################
#
# If this setting is  set to "yes", service information will be published with
# Zeroconf /  Avahi.
#
#zeroconf_enabled               "yes"
#
# The  argument to this setting will be the Zeroconf / Avahi unique name for
#  this MPD server on the network.
#
#zeroconf_name                   "Music Player"
#
###############################################################################


#  Permissions  #################################################################
#
#  If this setting is set, MPD will require password authorization. The  password
# can setting can be specified multiple times for different  password profiles.
#
password                         "**********@read,add,control,admin"
#
# This setting specifies the  permissions a user has who has not yet logged in. 
#
#default_permissions              "read,add,control,admin"
#
###############################################################################


#  Input  #######################################################################
#
#
#input  {
#        plugin "curl"
#       proxy "proxy.isp.com:8080"
#        proxy_user "user"
#       proxy_password "password"
#}
#
#
###############################################################################

#  Audio Output  ################################################################
#
#  MPD supports various audio output types, as well as playing through  multiple 
# audio outputs at the same time, through multiple  audio_output settings 
# blocks. Setting this block is optional,  though the server will only attempt
# autodetection for one sound  card.
#
# See  <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for  examples of 
# other audio outputs.
#
# An example of an ALSA  output:
#
#audio_output {
#       type            "alsa"
#        name            "My ALSA Device"
#       device           "hw:0,0"        # optional
#       format          "44100:16:2"    #  optional
#       mixer_type      "hardware"      # optional
#        mixer_device    "default"       # optional
#       mixer_control    "PCM"           # optional
#       mixer_index     "0"             #  optional
#}
#
# An example of an OSS output:
#
#audio_output  {
#       type            "oss"
#       name            "My OSS  Device"
##      device          "/dev/dsp"      # optional
##       format          "44100:16:2"    # optional
##      mixer_type       "hardware"      # optional
##      mixer_device    "/dev/mixer"    #  optional
##      mixer_control   "PCM"           # optional
#}
#
#  An example of a shout output (for streaming to Icecast):
#
audio_output  {
        type            "shout"
        encoding        "ogg"                    # optional
        name            "My Shout Stream"
         host            "127.0.0.1"
        port            "8000"
         mount           "/live.ogg"
        password         "***********"
        quality         "5.0"
#       bitrate          "128"
        format          "44100:16:1"
        protocol         "icecast2"              # optional
#       user             "source"                # optional
        description     "My Stream  Description" # optional
        genre           "jazz"                   # optional
        public          "no"                    #  optional
        timeout         "2"                     # optional
         mixer_type      "software"              # optional
}
#
#  An example of a recorder output:
#
#audio_output {
#        type            "recorder"
#       name            "My recorder"
#        encoder         "vorbis"                # optional, vorbis or lame
#        path            "/var/lib/mpd/recorder/mpd.ogg"
##       quality         "5.0"                   # do not define if bitrate is  defined
#       bitrate         "128"                   # do not  define if quality is defined
#       format          "44100:16:1"
#}
#
#  An example of a httpd output (built-in HTTP streaming server):
#
#audio_output  {
#       type            "httpd"
#       name            "My  HTTP Stream"
#       encoder         "vorbis"                #  optional, vorbis or lame
#       port            "8000"
##       quality         "5.0"                   # do not define if bitrate is  defined
#       bitrate         "128"                   # do not  define if quality is defined
#       format          "44100:16:1"
#        max_clients     "0"                     # optional 0=no limit
#}
#
#  An example of a pulseaudio output (streaming to a remote pulseaudio  server)
#
#audio_output {
#       type            "pulse"
#        name            "My Pulse Output"
##      server           "remote_server"         # optional
##      sink             "remote_server_sink"    # optional
#}
#
## Example "pipe"  output:
#
#audio_output {
#       type            "pipe"
#        name            "my pipe"
#       command         "aplay -f cd  2>/dev/null"
## Or if you're want to use AudioCompress
#        command         "AudioCompress -m | aplay -f cd 2>/dev/null"
##  Or to send raw PCM stream through PCM:
#       command         "nc  example.org 8765"
#       format          "44100:16:2"
#}
#
##  An example of a null output (for no audio output):
#
#audio_output  {
#       type            "null"
#       name            "My Null  Output"
#       mixer_type      "none"                  # optional
#}
#
#  This setting will change all decoded audio to be converted to the  specified
# format before being passed to the audio outputs. By  default, this setting is
# disabled.
#
#audio_output_format             "44100:16:2"
#
# If MPD has been compiled with  libsamplerate support, this setting specifies 
# the sample rate  converter to use.  Possible values can be found in the 
# mpd.conf  man page or the libsamplerate documentation. By default, this is
#  setting is disabled.
#
#samplerate_converter           "Fastest  Sinc Interpolator"
#
###############################################################################


#  Normalization automatic volume adjustments  ##################################
#
# This setting specifies the  type of ReplayGain to use. This setting can have
# the argument  "off", "album" or "track". See <http://www.replaygain.org>
#  for more details. This setting is off by default.
#
#replaygain                      "album"
#
# This setting sets the pre-amp used  for files that have ReplayGain tags. By
# default this setting is  disabled.
#
#replaygain_preamp              "0"
#
# This  setting enables on-the-fly normalization volume adjustment. This will
#  result in the volume of all playing audio to be adjusted so the output  has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization            "no"
#
###############################################################################


#  MPD Internal Buffering  ######################################################
#
# This  setting adjusts the size of internal decoded audio buffering. Changing
#  this may have undesired effects. Don't change this if you don't know  what you
# are doing.
#
#audio_buffer_size              "2048"
#
#  This setting controls the percentage of the buffer which is filled  before 
# beginning to play. Increasing this reduces the chance of  audio file skipping, 
# at the cost of increased time prior to audio  playback.
#
#buffer_before_play             "10%"
#
###############################################################################


#  Resource Limitations  ########################################################
#
# These  settings are various limitations to prevent MPD from using too many
#  resources. Generally, these settings should be minimized to prevent  security
# risks, depending on the operating resources.
#
#connection_timeout              "60"
#max_connections                "10"
#max_playlist_length             "16384"
#max_command_list_size          "2048"
#max_output_buffer_size          "8192"
#
###############################################################################


#  Character Encoding  ##########################################################
#
# If  file or directory names do not display correctly for your locale then  you 
# may need to modify this setting.
#
filesystem_charset               "UTF-8"
#
# This setting controls the encoding that  ID3v1 tags should be converted from.
#
id3v1_encoding                   "UTF-8"
#
###############################################################################
```**cat /etc/icecast2/icecast.xml**
```
<icecast>
    <limits>
         <clients>100</clients>
         <sources>2</sources>
         <threadpool>5</threadpool>
         <queue-size>524288</queue-size>
         <client-timeout>30</client-timeout>
         <header-timeout>15</header-timeout>
         <source-timeout>10</source-timeout>
        <!-- If  enabled, this will provide a burst of data when a client 
              first connects, thereby significantly reducing the startup 
              time for listeners that do substantial buffering. However,
              it also significantly increases latency between the source
              client and listening client.  For low-latency setups, you
              might want to disable this. -->
         <burst-on-connect>1</burst-on-connect>
        <!--  same as burst-on-connect, but this allows for being more
              specific on how much to burst. Most people won't need to
              change from the default 64k. Applies to all mountpoints  -->
         <burst-size>65535</burst-size>
    </limits>

     <authentication>
        <!-- Sources log in with  username 'source' -->
         <source-password>**********</source-password>
         <!-- Relays log in username 'relay' -->
         <relay-password>**********</relay-password>

         <!-- Admin logs in with the username given below -->
         <admin-user>*******</admin-user>
         <admin-password>**********</admin-password>
     </authentication>

    <!-- set the mountpoint for a  shoutcast source to use, the default if not
         specified is  /stream but you can change it here if an alternative is
          wanted or an extension is required
     <shoutcast-mount>/live</shoutcast-mount>
    -->

     <!-- Uncomment this if you want directory listings -->
     <!--
    <directory>
         <yp-url-timeout>15</yp-url-timeout>
         <yp-url>[http://dir.xiph.org/cgi-bin/yp-cgi](http://dir.xiph.org/cgi-bin/yp-cgi)</yp-url>
     </directory>
     -->

    <!-- This is the  hostname other people will use to connect to your server.
    It  affects mainly the urls generated by Icecast for playlists and yp
     listings. -->
     <hostname>radio.******.com</hostname>

    <!-- You  may have multiple <listener> elements -->
     <listen-socket>
        <port>8000</port>
         <!-- <bind-address>127.0.0.1</bind-address> -->
         <!-- <shoutcast-mount>/stream</shoutcast-mount>  -->
    </listen-socket>
    <!--
     <listen-socket>
        <port>8001</port>
     </listen-socket>
    -->

     <!--<master-server>127.0.0.1</master-server>-->
     <!--<master-server-port>8001</master-server-port>-->
      <!--<master-update-interval>120</master-update-interval>-->
     <!--<master-password>hackme</master-password>-->

     <!-- setting this makes all relays on-demand unless overridden,  this is
         useful for master relays which do not have  <relay> definitions here.
         The default is 0 -->
     <!--<relays-on-demand>1</relays-on-demand>-->

     <!--
    <relay>
         <server>127.0.0.1</server>
         <port>8001</port>
         <mount>/live.ogg</mount>
         <local-mount>/live.ogg</local-mount>
         <on-demand>0</on-demand>

         <relay-shoutcast-metadata>0</relay-shoutcast-metadata>
     </relay>
    -->

    <!-- Only define a  <mount> section if you want to use advanced options,
          like alternative usernames or passwords
    <mount>
         <mount-name>/example-complex.ogg</mount-name>

         <username>admin</username>
         <password>**********</password>

         <max-listeners>1</max-listeners>
         <dump-file>/tmp/dump-example1.ogg</dump-file>
         <burst-size>65536</burst-size>
         <fallback-mount>/example2.ogg</fallback-mount>
         <fallback-override>1</fallback-override>
         <fallback-when-full>1</fallback-when-full>
         <intro>/example_intro.ogg</intro>
         <hidden>1</hidden>
        <no-yp>1</no-yp>
         <authentication type="htpasswd">
                 <option name="filename" value="myauth"/>
                 <option name="allow_duplicate_users" value="0"/>
         </authentication>
         <on-connect>/home/icecast/bin/stream-start</on-connect>
          <on-disconnect>/home/icecast/bin/stream-stop</on-disconnect>
     </mount>

    <mount>
         <mount-name>/auth_example.ogg</mount-name>
         <authentication type="url">
            <option  name="mount_add"       value="[http://myauthserver.net/notify_mount.php](http://myauthserver.net/notify_mount.php)"/>
             <option name="mount_remove"    value="[http://myauthserver.net/notify_mount.php](http://myauthserver.net/notify_mount.php)"/>
             <option name="listener_add"    value="[http://myauthserver.net/notify_listener.php](http://myauthserver.net/notify_listener.php)"/>
             <option name="listener_remove" value="[http://myauthserver.net/notify_listener.php](http://myauthserver.net/notify_listener.php)"/>
         </authentication>
    </mount>

    -->

     <fileserve>1</fileserve>

    <paths>
                 <!-- basedir is only used if chroot is enabled -->
         <basedir>/usr/share/icecast2</basedir>

         <!-- Note that if <chroot> is turned on below, these paths  must both
             be relative to the new root, not the original  root -->
        <logdir>/var/log/icecast2</logdir>
         <webroot>/usr/share/icecast2/web</webroot>
         <adminroot>/usr/share/icecast2/admin</adminroot>
         <!-- <pidfile>/usr/share/icecast2/icecast.pid</pidfile>  -->

        <!-- Aliases: treat requests for 'source' path  as being for 'dest' path
             May be made specific to a port  or bound address using the "port"
             and "bind-address"  attributes.
          -->
        <!--
        <alias  source="/foo" dest="/bar"/>
          -->
        <!--  Aliases: can also be used for simple redirections as well,
              this example will redirect all requests for [http://server:port/](http://server:port/) to
              the status page
          -->
        <alias  source="/" dest="/status.xsl"/>
    </paths>

     <logging>
        <accesslog>access.log</accesslog>
         <errorlog>error.log</errorlog>
        <!--  <playlistlog>playlist.log</playlistlog> -->
         <loglevel>3</loglevel> <!-- 4 Debug, 3 Info, 2 Warn, 1  Error -->
        <logsize>10000</logsize> <!-- Max  size of a logfile -->
        <!-- If logarchive is enabled  (1), then when logsize is reached
             the logfile will be  moved to [error|access|playlist].log.DATESTAMP,
              otherwise it will be moved to [error|access|playlist].log.old.
              Default is non-archive mode (i.e. overwrite)
        -->
         <!-- <logarchive>1</logarchive> -->
     </logging>

    <security>
         <chroot>0</chroot>
        <!--
         <changeowner>
            <user>nobody</user>
             <group>nogroup</group>
         </changeowner>
        -->
    </security>
</icecast>
```

---

