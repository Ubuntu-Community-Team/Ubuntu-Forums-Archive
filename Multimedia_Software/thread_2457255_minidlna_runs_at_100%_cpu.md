---
title: "minidlna runs at 100% cpu"
date: 2021-01-28
forum: Multimedia Software
---

### Post by MickSulley on 2021-01-28
On a fresh install of Ubuntu Server 20.04.1, LTS   I have installed minidlna and it seems to be working OK, however it runs at 100% cpu, occasionally drops to 98% or so but mostly 100%
Is there something wrong or is that normal?

Thanks
Mick

---

### Post by TheFu on 2021-01-29
Well, it does need to index the content in order to serve it.  That can take hours, but is dependent on the amount and type of content being indexed.
After that finishes, streaming shouldn't take much CPU at all.  I don't think miniDLNA supports transcoding like plex or jellyfin or emby do for each client device.

Are you certain it is minidlna eating the CPU and not something else?  What does top show?
Could it be a poorly sized swap problem?

And the CPU would matter.  If it is a 10th-gen Core i7, then yes, it is definitely a problem, but if it is an Atom from 2011, perhaps this would be normal.

---

### Post by TheFu on 2021-01-29
I would disable minidlna and see if the CPU abuse continues too.

---

### Post by MickSulley on 2021-01-29
This is what I see in top
  
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                          
34129 minidlna  35  15  182760   7848   4400 R 100.0   0.0   1687:34 minidlnad 
```                                                                                       
  
If I stop the minidlna service then that line disappears from top
The processor is an Intel E5-2420 Xeon Six-Core 1.9GHz CPU, so should have plenty of power.  Swap usage shows 1%

---

### Post by SeijiSensei on 2021-01-30
How big are the libraries it needs to index? Once the indexing is finished, my instance of minidlnad uses hardly any CPU.
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                
 3945 phl       20   0  266m 7820 1236 S  0.0  0.2   0:06.14 minidlnad

```

---

### Post by ajgreeny on 2021-01-30
Let's see the content of your ***/etc/minidlna.conf*** file; that may immediately give us more of a clue than we have at the moment and the CPU use you mention is certainly not normal.

I run minidlna on my laptop with the following hardware and my system uses perhaps 10%cpu when indexing the media folders but then reduces to such an extent that it is no longer shown in my top 4 processes as shown in conky's output (See screenshot) 
```
Processor (CPU)		Intel® Core™i3 Dual Core Mobile Processor i3-4100M (2.50GHz) 3MB
Memory (RAM)		        4GB KINGSTON SODIMM DDR3 1600MHz (1 x 4GB)
Graphics Card		        INTEL® HD GRAPHICS MEDIA ACCELERATOR 4600
Memory - Hard Disk	        500GB SERIAL ATA II 2.5" HARD DRIVE WITH 8MB CACHE (5,400rpm)
```
and with minidlna running all the time alongside firefox with 3 tabs open I see the following CPU % usage as shown in the screenshot
My minidlna.conf file is shown below; it will be interesting to see the differences apart from the folders used.
NB: I have removed my name and replaced with xxxxxx
```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media
# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.
#
# Specify the user name or uid to run as.
#user=minidlna
#
#
# Path to the directory you want scanned for media files.
#
# This option can be specified more than once if you want multiple directories
# scanned.
#
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#media_dir=A,/path/to/folder
#media_dir=P,/path/to/folder
#media_dir=V,/path/to/folder
#media_dir=B,/path/to/folder #to browse all file types
#
media_dir=/home/xxxxxx/Music
media_dir=/home/xxxxxx/Music2
media_dir=/home/xxxxxx/Videos
media_dir=/home/xxxxxx/abcde
#
media_dir=/home/xxxxxx/Pictures
media_dir=/home/xxxxxx/Pics
#
media_dir=/home/xxxxxx/Videos/BBC_iPlayer
media_dir=/home/xxxxxx/Videos/BBC_iPlayer/Undercover
media_dir=/home/xxxxxx/Videos/Les_Miserables
media_dir=/home/xxxxxx/Videos/War_and_Peace
media_dir=/home/xxxxxx/Pictures/Holidays/Botswana_&_Hermanus/Hermanus_Videos
media_dir=/home/xxxxxx/Pictures/Holidays/Galapagos/Galapagos_Videos
#
#media_dir=/var/lib/minidlna
#
# Path to the directory that should hold the database and album art cache.
#db_dir=/var/cache/minidlna
#
# Path to the directory that should hold the log file.
#log_dir=/var/log
#
# Type and minimum level of importance of messages to be logged.
#
# The types are "artwork", "database", "general", "http", "inotify",
# "metadata", "scanner", "ssdp" and "tivo".
#
# The levels are "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
log_level=fatal
#
# The types are comma-separated, followed by an equal sign ("="), followed by a
# level that applies to the preceding types. This can be repeated, separating
# each of these constructs with a comma.
#
# The default is to log all types of messages at the "warn" level.
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn
#
# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
# If you specify "B" and the client device is audio-only then "Music/Folders"
# will be used as root.
#root_container=.
#
# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=
#
# IPv4 address to listen on (e.g. 192.0.2.1/24).
# If omitted, the mask defaults to 24. The IPs are added to those determined
# from the network_interface option above.
# This option can be specified more than once.
#listening_ip=
#
# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200
#
# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/
#
# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
#friendly_name=
#
# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110
#
# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)
#
# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=
#
# Automatic discovery of new files in the media_dir directory.
inotify=yes
#
# List of file names to look for when searching for album art.
# Names should be delimited with a forward slash ("/").
# This option can be specified more than once.
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg
album_art_names=AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg
album_art_names=Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
#
# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
#strict_dlna=no
#
# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
#enable_tivo=no
#
# Notify interval, in seconds.
notify_interval=900
#
# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

---

### Post by MickSulley on 2021-01-30
ajgreeny,  I've just compared my config file with yours -
I have 4 media_dir=  entries, you have 12
you have log_level=fatal,  I have nothing for that
I have notify_interval=900,  you have that line commented out

SeijiSensei,  library sizes
Pictures - 20k items  130GB
Music - 25k items  143GB
Video - 2 libraries -  20 items  16.7 GB   and   6k items  105 GB

It has been running for a few days now, could it still be indexing?
Thanks
Mick

---

### Post by SeijiSensei on 2021-01-30
Hmm. I have one directory with 2.2 terabytes of content, and three others that total a little over 100 GB.

Something certainly seems wrong. 

Try setting "log_level=debug" in /etc/minidlna.conf then rerun the indexer with
```

sudo minidlnad -R

```
My logs have lots of warnings, but I don't have problems watching those files. Maybe just include one of the smaller directories to see what happens.

---

### Post by MickSulley on 2021-01-31
Sorry for the delay in replying, I have been testing out many scenarios.  Now I am totally confused!!  

Following your advice I set the log level and just enabled the smallest directory, restarted etc, and could not see it in top as it was so low.  I then added the others in one by one and checked top, showed 100% for a few seconds then dropped.  I now have them all enabled again and have just taken out the log_level=debug, so I believe exactly as it was before, and minidlnad shows in top occasionally at around 0.3% CPU.

That was the good news.

However-  on my TV I can't see any of them.  I can see the server but if I select anything it cannot open the folder to see the actual media.  I have tried just enabling a single directory, I did get it to work with just pictures but then tried videos, that didn't work and now pictures won't work either.  I removed and purged minidlna and then reinstalled, then edited the config to point to my directories and still it doesn't work.  The really odd thing is that on TV I can see my second video directory and the files within but non of them play, and bizarrely I didn't actually enter that directory in the config - how can that happen?

Any ideas?  I think I must be missing something really obvious.

Mick

---

### Post by ajgreeny on 2021-01-31
If you look carefully you will see that I have the notify interval 900 the same as you, ie,  ***notify_interval=900***, though in may case the line has become separated from the 
[B][I]# Automatic discovery of new files in the media_dir directory.
inotify=yes[/I][/B]
lines in the file, probably by my editing.
That should make no difference nor have anything to do with your problem.

Can you check that you are in the **minidlna** user group and also that user **minidlna** is in your usergroup; I made that change to make sure no permissions problems followed but I'm not sure if such potential problems would affect the CPU usage as you're seeing.

Finally can you check permissions and file-types for the contents of the folder that will not play, and if necessary change them to:
[B]Owner rw
Group r
Others r[/B]
In octal permissions language that is 644 for files, 755 for folders.

---

### Post by CelticWarrior on 2021-01-31
Do the same files play locally (TV)? If not then there's your answer, miniDLNA doesn't do transcoding as mentioned above.

---

### Post by TheFu on 2021-01-31
> In octal permissions language that is 655 for files, 755 for folders. 
Think you mean 644 for files and 755 for directories.

Best to learn Unix permissions sooner than later.  Only native Linux file systems allow control over the owner, group, and permissions while the file system is mounted. NTFS and all FAT-whatever file systems allow control only through mount options and all files, all directories in that mount get the same owner, group, and permissions.
There are lots of 15-30 minute permissions tutorials. Any are fine - Unix, OSX, Android, iOS, and all Linuxen use the same permissions. Learn one and you know them all.  Here's the Ubuntu tutorial: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  
and a beginner Linux book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) if you need more details.

TVs usually support very few video file codecs, so if your video files don't use those codecs in the container the TV understands, then it won't see or play the files.

---

### Post by MickSulley on 2021-01-31
No still not working, and my second video directory still shows on TV as a list of files but cannot be opened, even though it is not in the config file.  Is that information cached anywhere?  The log file has a few warnings but nothing to indicate what the problem may be.

On the plus side the CPU usage is down around 0.3% :)

Mick

---

### Post by MickSulley on 2021-01-31
All of the files did play on TV before I started trying to fix the 100% CPU problem

---

### Post by TheFu on 2021-01-31
If you change any config file, restart the service using that config file.

[https://www.linuxtrainingacademy.com/systemd-cheat-sheet/](https://www.linuxtrainingacademy.com/systemd-cheat-sheet/)
**Working with Services**
```
sudo systemctl stop service : Stop a running service
sudo systemctl start service : Start a service
sudo systemctl restart service : Restart a running service
sudo systemctl reload service : Reload all config files in service
sudo systemctl status service : See if service is running/enabled
sudo systemctl enable service : Enable a service to start on boot
sudo systemctl disable service : Disable service–won’t start at boot
sudo systemctl show service : Show properties of a service (or other unit)
```

Not all services/daemons support the "reload", so "restart" is what I use.

---

### Post by MickSulley on 2021-01-31
Yes each time I change anything in config I run
sudo service minidlna stop
sudo minidlnad -R
sudo service minidlna start

---

### Post by MickSulley on 2021-01-31
I have just installed it on my Desktop running Mint 20 as a test and it works fine.  It must be permissions or something.  Tomorrow I will remove all traces and start again.  I'll let you know how it goes......

---

### Post by MickSulley on 2021-02-02
All fixed!!
The original problem of 100% CPU usage went away, I don't know why.
The second problem of not seeing anything on TV was a problem with directory ownership, corrected that, restarted and all is fine now.
Thanks to everyone who assisted, mush appreciated.

Mick

---

### Post by ajgreeny on 2021-02-02
Great news! I'm glad you now have minidlna working for you.

For the record, what exactly were the permissions problems that you have now solved? Several of us were suggesting incorrect permissions were behind your difficulties and you said you were sure that was not the case.
The more info you give in this thread the more useful this will be for others searching for similar problems.

However, please now mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

