---
title: "mpd + ncmpcpp dont work"
date: 2011-12-08
forum: Multimedia Software
---

### Post by kerasi on 2011-12-08
Hello and Merry Christmas

I had to install Lubuntu new it works all perfect but when i try to setup mpd + ncmcpp it wont work :-( :-( i'am so sad

this are the steps that i have done 
all my music are stored in another partiton called music

/media/music #if you look from Linux a ntfs partition

i will setup mpd system wide not as user

here my fstab (i hope i'have done it right)

```
sudo blkid

/dev/sda5: LABEL="music" UUID="464C96747AFB6EB9" TYPE="ntfs" 
```
```
shaft@shaft:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=2b42ec22-4d7b-4163-bdd8-78c7a151f6e7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=1cb9690d-5fb1-44e9-ba88-86e04ba924f0 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=8a7e5f02-73bc-44a7-a114-97cfa446176c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# eingehängte music partition
UUID=464C96747AFB6EB9 /media/music ntfs rw,auto,users,nls=utf8,umask=007,gid=46  0  0
```
```
sudo mkdir -p /media/music
```
```
sudo mount -a
```
```
shaft@shaft:~$ cat /var/lib/mpd/tag_cache
info_begin
format: 1
mpd_version: 0.16.1
fs_charset: UTF-8
tag: Artist
tag: ArtistSort
tag: Album
tag: AlbumArtist
tag: AlbumArtistSort
tag: Title
tag: Track
tag: Name
tag: Genre
tag: Date
tag: Composer
tag: Performer
tag: Disc
tag: MUSICBRAINZ_ARTISTID
tag: MUSICBRAINZ_ALBUMID
tag: MUSICBRAINZ_ALBUMARTISTID
tag: MUSICBRAINZ_TRACKID
info_end
```
```
shaft@shaft:~$ sudo service mpd restart
 * Stopping Music Player Daemon mpd                                                                           [ OK ] 
 * Starting Music Player Daemon mpd
```
```
shaft@shaft:~$ sudo sed '/^#\|^$/d' /etc/mpd.conf
music_directory		"/media/music/"
playlist_directory		"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file			"/var/log/mpd/mpd.log"
pid_file			"/var/run/mpd/pid"
state_file			"/var/lib/mpd/state"
user				"mpd"
bind_to_address		"localhost"
input {
        plugin "curl"
}
        #type    "pulse"
        #name    "MPD PulseAudio Ausgabe"
        #server  "pulseaudio"   # optional
        #sink    "alsa_output" # optional
audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}
filesystem_charset		"UTF-8"
id3v1_encoding			"UTF-8"
```
```
shaft@shaft:~$ ls -l /etc/mpd.conf
-rw-r----- 1 mpd audio 12616 2011-12-07 18:27 /etc/mpd.conf
```
```
shaft@shaft:/var/lib/mpd$ ls -la
insgesamt 36
drwxr-xr-x  5 mpd  audio 4096 2011-12-07 18:00 .
drwxr-xr-x 55 root root  4096 2011-12-07 16:49 ..
-rw-------  1 mpd  audio   16 2011-12-07 18:00 .esd_auth
drwxr-xr-x  2 mpd  audio 4096 2011-02-02 12:50 music
drwxr-xr-x  2 mpd  audio 4096 2011-02-02 12:50 playlists
drwx------  2 mpd  audio 4096 2011-12-07 18:35 .pulse
-rw-------  1 mpd  audio  256 2011-12-07 17:41 .pulse-cookie
-rw-r--r--  1 mpd  audio  183 2011-12-07 18:46 state
-rw-r--r--  1 mpd  audio  344 2011-12-07 16:50 tag_cache
```
```
shaft@shaft:~$ ls -la /media/music/80\'/80\'s_Night_DJCollections/01
insgesamt 27320
drwxrwx--- 1 root plugdev   12288 2011-11-22 12:54 .
drwxrwx--- 1 root plugdev    4096 2011-02-27 21:13 ..
-rwxrwx--- 2 root plugdev 4950144 2007-03-08 11:30 16_Steve_Arrington_Feel_So_Real.mp3
-rwxrwx--- 2 root plugdev 3442816 2007-03-08 11:33 17_Rick_Astley_Never_Gonna_Give_You_Up.mp3
-rwxrwx--- 2 root plugdev 3289216 2007-03-08 12:15 18_Rick_Astley_Together_For_Ever.mp3
-rwxrwx--- 1 root plugdev 4031215 2011-11-20 18:42 ABBA_Super_Trouper.mp3
-rwxrwx--- 1 root plugdev 4538496 2011-11-20 19:27 Alphaville_Big_in_Japan.mp3
-rwxrwx--- 1 root plugdev 3796206 2011-11-21 10:32 Aneka_Japanese_Boy.mp3
```
```
sudo usermod -aG plugdev mpd
```

here my ncmpcpp config
```
shaft@shaft:/var/lib/mpd$ cat /home/shaft/.ncmpcpp/config 
####################################################
## this is example configuration file, copy it to ##
## ~/.ncmpcpp/config and set up your preferences  ##
####################################################
#
##### connection settings #####
#
## set it in order to make tag editor and renaming files work properly
#
mpd_host = "localhost"
#
mpd_port = "6600"
#
mpd_music_dir = "/media/music"
#
mpd_connection_timeout = "5"
#
mpd_crossfade_time = "5"
#
mpd_communication_mode = "notifications" (polling/notifications)
#
##### music visualizer #####
##
## Note: In order to make music visualizer work you'll
## need to use mpd fifo output, whose format parameter
## has to be set to 44100:16:1. Example configuration:
## (it has to be put into mpd.conf)
##
## audio_output {
##        type            "fifo"
##        name            "My FIFO"
##        path            "/tmp/mpd.fifo"
##        format          "44100:16:1"
## }
##
#
```
```
shaft@shaft:~/Arbeitsfläche/christmas$ sudo cat /var/log/mpd/mpd.log
Dec 08 10:50 : state_file: failed to open /var/lib/mpd/state: No such file or directory
Dec 08 10:58 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:03 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:04 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:09 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:26 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:27 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:38 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:38 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused
Dec 08 11:41 : output: Failed to enable "MPD PulseAudio Ausgabe" [pulse]: pa_context_connect() has failed: Connection refused

```
```
shaft@shaft:/var/lib/mpd$ id mpd
uid=107(mpd) gid=29(audio) Gruppen=29(audio),46(plugdev)
```

I hope someone could find the mistake and help me
when i start ncmpcpp i could not find when i press 3 my music files

:-(

---

### Post by marinara on 2011-12-08
you said this is a new Lubuntu install.  Did you install pulseaudio?

---

### Post by kerasi on 2011-12-08
i dont't install pulsaudio i thought it was per dafault installed

pulsaudio is installed

---

### Post by kerasi on 2011-12-08
cool i fix it :-) :-)

i forgot to type

u

in ncmpcpp then it startet the database update oh :-)

thanks 

and merry Christmas

---

