---
title: "SMPlayer gives error &quot;MPlayer/mpv has finished unexpectedly. Exit code: 2&quot;"
date: 2022-05-24
forum: Multimedia Software
---

### Post by peyre on 2022-05-24
I recently reinstalled Xubuntu 22.04 from scratch on my desktop.  It has an SSD for the system and a mechanical for data.  I use SMPlayer for most video files and it's always worked great.  It was working fine tonight too, until I decided to move the location to install the mechanical drive to in fstab.  Ever since that time, opening SMPlayer has given the error above.  The log shows:

```
/snap/smplayer/58/usr/bin/mpv --no-quiet --terminal --no-msg-color --input-ipc-server=/tmp/smplayer-mpv-c44 --msg-level=ffmpeg/demuxer=error --video-rotate=no --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-vo-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=83886118 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --osd-bar-align-y=0.6 --sub-ass --embeddedfonts --sub-ass-line-spacing=0 --sub-scale=1 --sub-font=Arial --sub-color=#ffffffff --sub-shadow-color=#ff000000 --sub-border-color=#ff000000 --sub-border-size=0.75 --sub-shadow-offset=2.5 --sub-font-size=50 --sub-bold=no --sub-italic=no --sub-margin-y=8 --sub-margin-x=20 --sub-codepage=ISO-8859-1 --sub-pos=100 --volume=55 --cache=auto --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --screenshot-directory=/home/leon/Pictures/smplayer_screenshots --audio-pitch-correction=yes --volume-max=110 --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-params/aspect}
INFO_VIDEO_FPS=${=container-fps:${=fps}}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_DEMUX_ROTATION=${=track-list/0/demux-rotation}
INFO_AUDIO_FORMAT=${=audio-codec-name}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate}
INFO_AUDIO_NCH=${=audio-params/channel-count}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=current-demuxer:${=demuxer}}
INFO_SEEKABLE=${=seekable}
INFO_TITLES=${=disc-titles}
INFO_CHAPTERS=${=chapters}
INFO_TRACKS_COUNT=${=track-list/count}
METADATA_TITLE=${metadata/by-key/title:}
METADATA_ARTIST=${metadata/by-key/artist:}
METADATA_ALBUM=${metadata/by-key/album:}
METADATA_GENRE=${metadata/by-key/genre:}
METADATA_DATE=${metadata/by-key/date:}
METADATA_TRACK=${metadata/by-key/track:}
METADATA_COPYRIGHT=${metadata/by-key/copyright:}
INFO_MEDIA_TITLE=${=media-title:}
INFO_STREAM_PATH=${stream-path}
 --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} /media/leon/Storage/Graphics/Movies/Lord of the Rings/Sharkey Purist Mods/2 - TTT2.1.mp4

[file] Cannot open file '/media/leon/Storage/Graphics/Movies/Lord of the Rings/Sharkey Purist Mods/2 - TTT2.1.mp4': Permission denied
Failed to open /media/leon/Storage/Graphics/Movies/Lord of the Rings/Sharkey Purist Mods/2 - TTT2.1.mp4.
Exiting... (Errors when loading file)

```

I've tried changing it back, but it still insists on doing the same thing.  I've had a few twists and turns, so I'm not sure this is what I had before, but this is what I tried to revert to:

# mount sdc1 on /data
UUID="002e92c4-784a-4cb3-9d52-4171af4804c8"  /media/storage             ext4    defaults  0       2

---

### Post by ajgreeny on 2022-05-24
Your mount point in fstab looks wrong to me meaning the files etc on that disk/partition will possibly be owned by root.

Normally I let USB drives automount to /media/username/partition-label but also change ownership of the mountpoint to my user with command 
***sudo chown -R username:username /mountpoint***

I do not have any permanently attached USB drives in fstab.

Try that to see if it helps as an ext4 partition will otherwise be root owned by default.

---

### Post by peyre on 2022-05-24
It's not a USB drive.  It's a SATA drive mounted inside the case.  It is formatted ext4.

If I don't have fstab mount it, it appears (and even appears in Start, which it hasn't been since I reinstalled Xubuntu)--which is great, except it doesn't *mount* automatically.  I have to manually tell it to mount the drive every time I boot up, which is unnecessarily tedious.

---

### Post by #&amp;thj^% on 2022-05-24
Still would be nice to see your fstab, as we all know XFCE4 won't auto mount anything with out it being in fstab first.
show if you will:
```
cat /etc/fstab
```
also 
```
ls -l /mnt
total 4
drwx------ 8 me 1002 4096 Apr  4 10:02 be93f3dc-cd54-4321-9a9f-558c1317fc44

```
EDIT: I'll use this for my switch's, in fstab
```
rw,user,auto    0      1
```

---

### Post by peyre on 2022-05-24
I'll get that tonight and post it.  Incidentally, I've had fstab mount that drive for years now, both on the current installation and the one before, and SMPlayer worked flawlessly.  But make a little change last night and it won't do anything but throw up an error.

Maybe I should set it back to mount in ~/Storage.  I must have deleted what I had in fstab because it's currently set to mount somewhere else.  But it doesn't seem right to mount it under my home folder.

I wonder if maybe I'm trying to do this the hard way--perhaps I should rem out the line in fstab and use the Disks utility to set it the way I want it.  It should let me set it to mount at startup, and I can add nofail so the computer will boot even if there's trouble with the drive.

---

### Post by #&amp;thj^% on 2022-05-24
> **peyre said:**
>  Incidentally, I've had fstab mount that drive for years now, both on the current installation and the one before, and SMPlayer worked flawlessly.  But make a little change last night and it won't do anything but throw up an error.

Maybe I should set it back to mount in ~/Storage.  I must have deleted what I had in fstab because it's currently set to mount somewhere else.  But it doesn't seem right to mount it under my home folder.
I meant no offense peyre, I'm well familiar with you over the years, and know your level of experience. We *all* tend to overlook the small things from time to time. :)

---

### Post by Holger_Gehrke on 2022-05-24
It's probably a configuration problem. smplayer keeps a playlist with the last files you used it for as part of it's configuration. I can get similar results to what you get by renaming the last file I played, although I have to hit play without loading a new file to get it to try to play the last file it (mis-)remembers to provoke the error. The config in question is ~/.config/smplayer/playlist.ini and you can either change the paths for the files in it with an editor or just delete it (it will be recreated with an empty playlist).

Holger

---

### Post by peyre on 2022-05-24
Sorry 1fallen; I wasn't mad at you, just frustrated with Xubuntu not doing what I wanted.

Holger, thanks for the config location!  I'll try that tonight too.  I tried doing a complete removal of SMPlayer in Synaptic, then reinstall, but that didn't seem to clear its memory.  (Should've mentioned that earlier, come to think of it.)

---

### Post by #&amp;thj^% on 2022-05-24
> **peyre said:**
> Sorry 1fallen; I wasn't mad at you, just frustrated with Xubuntu not doing what I wanted.


No apology needed, I had a strong feeling of your frustration. (Gets us all at one point) :)

---

### Post by ajgreeny on 2022-05-24
Have you checked that you are the owner of that disk partition ?

As I said before, an ext4 partition will be root owned by default unless you chown the mountpoint to be owned by you.
PS:
Sorry about my assumption that this was a USB disk, though it will make no difference regarding owner.

---

### Post by peyre on 2022-05-24
> **Holger_Gehrke said:**
> It's probably a configuration problem. smplayer keeps a playlist with the last files you used it for as part of it's configuration. I can get similar results to what you get by renaming the last file I played, although I have to hit play without loading a new file to get it to try to play the last file it (mis-)remembers to provoke the error. The config in question is ~/.config/smplayer/playlist.ini and you can either change the paths for the files in it with an editor or just delete it (it will be recreated with an empty playlist).

Holger

What the?  There's no smplayer folder inside ~/.config.  Should I look somewhere else?

---

### Post by #&amp;thj^% on 2022-05-24
> **peyre said:**
> What the?  There's no smplayer folder inside ~/.config.  Should I look somewhere else?

Maybe you haven't started it yet>> if a fresh install nothing will be there until opened:
```
cd .config/smplayer && ls -la
total 36
drwxrwxr-x  2 me me 4096 May 24 21:42 .
drwx------ 26 me me 4096 May 24 21:42 ..
-rw-rw-r--  1 me me    8 May 24 21:42 favorites.m3u8
-rw-rw-r--  1 me me   73 May 24 21:42 hdpi.ini
-rw-rw-r--  1 me me  997 May 24 21:42 playlist.ini
-rw-rw-r--  1 me me    8 May 24 21:42 radio.m3u8
-rw-rw-r--  1 me me 7840 May 24 21:42 smplayer.ini
-rw-rw-r--  1 me me    8 May 24 21:42 tv.m3u8

```
If needed only:
```
stat ~/.config/smplayer 
  File: /home/me/.config/smplayer
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: fc03h/64515d	Inode: 1476705     Links: 2
Access: (0775/drwxrwxr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2022-05-24 21:42:51.991510447 -0400
Modify: 2022-05-24 21:42:39.167567857 -0400
Change: 2022-05-24 21:42:39.167567857 -0400
 Birth: 2022-05-24 21:42:35.455584503 -0400

```

---

### Post by peyre on 2022-05-24
No.  I've opened it many times before since installing again from scratch.  Still, with SMPlayer open, there is no smplayer file or folder.

---

### Post by Yellow Pasque on 2022-05-25
> **peyre said:**
> No.  I've opened it many times before since installing again from scratch.  Still, with SMPlayer open, there is no smplayer file or folder.

Maybe because you're using a Snap version?
```
/snap/smplayer/58/usr/bin/mpv
```

> **Holger_Gehrke said:**
> It's probably a configuration problem. smplayer keeps a playlist with the last files you used it for as part of it's configuration. I can get similar results to what you get by renaming the last file I played, although I have to hit play without loading a new file to get it to try to play the last file it (mis-)remembers to provoke the error. The config in question is ~/.config/smplayer/playlist.ini and you can either change the paths for the files in it with an editor or just delete it (it will be recreated with an empty playlist).

I don't think it's a configuration problem. It's not complaining about 'File not found'. It says it can't open the file because of permissions.

---

### Post by ajgreeny on 2022-05-25
> **Yellow Pasque said:**
> Maybe because you're using a Snap version?
```
/snap/smplayer/58/usr/bin/mpv
```



I don't think it's a configuration problem. It's not complaining about 'File not found'. It says it can't open the file because of permissions.

I refer you back to my post #10.

A permissions problem seems to point in 5his direction but still do not appear to have checked this.

---

### Post by Holger_Gehrke on 2022-05-25
> **Yellow Pasque said:**
> Maybe because you're using a Snap version?
```
/snap/smplayer/58/usr/bin/mpv
```
I don't think it's a configuration problem. It's not complaining about 'File not found'. It says it can't open the file because of permissions.

Good catch. I missed both the exact error and the snap. With a snap the configuration isn't in '~/.config' but somewhere in '~/snap', probably in '~/snap/smplayer/common/'.  And since snaps can't access anything outside $HOME, /media/$user and - I believe - /run/user/$(id) because of an AppArmor profile associated with the program this explains the permission problem. That it tries to access these files is still a problem with the playlist configuration, though. And since the error persisted through a deinstallation / reinstallation it has to be the user specific configuration.

Unless the difference between the snap-version (22.2.0) and the version I installed through apt (21.10.0) is massive, you might want to try removing the snap and installing smplayer through apt, especially if you want to play files that are not in the directories allowed for snaps.

Holger

---

### Post by peyre on 2022-05-25
Um, I formatted it myself, logged in as myself.  But that was under the old installation, so maybe that doesn't count as the same user, if it has a different UserID or something.

---

### Post by #&amp;thj^% on 2022-05-25
Snap SMPlayer runs in a sandbox, with restricted permissions and sometimes you may need to give it more permissions. For example in order to play files from external drives you may need to run this command:
```

sudo snap connect smplayer:removable-media
```
for sound you may need to set that as well, but I'll wait for you to decide first.
I have not seen a confirmation yet if it is a Snap but I'll assume so from the above post's

---

### Post by peyre on 2022-05-25
I installed it using the Software utility.  That isn't using snap yet, is it?

And I never did paste in my fstab.  Have to do that tonight.

---

### Post by #&amp;thj^% on 2022-05-25
> **peyre said:**
> I installed it using the Software utility.  That isn't using snap yet, is it?


Are you sure?
```
apt policy smplayer
smplayer:
  Installed: 21.10.0~ds0-1
  Candidate: 21.10.0~ds0-1
  Version table:
 *** 21.10.0~ds0-1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
> **peyre said:**
> And I never did paste in my fstab. Have to do that tonight. 

Possible fstab error? looking forward to seeing that

---

### Post by Holger_Gehrke on 2022-05-25
Well, I am not certain which package the Software utility prefers, it can do both and it can even do flatpak if you've got the plugin for that installed. But finding out is easy from the command line. Either do a 'snap list' or 'apt-cache policy smplayer'.

Holger

---

### Post by peyre on 2022-05-25
Yes, the installation of Xubuntu was just a couple weeks ago, pretty recent.  I used Software for most of my installations; if I didn't use it for SMPlayer, I would've used Synaptic.

---

### Post by peyre on 2022-05-25
Ok, this is my fstab at present:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=a95190c7-e251-49d3-9a36-41090ed350b8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=D5EC-16A5  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/sdj        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# mount sdc1 on /data
UUID="002e92c4-784a-4cb3-9d52-4171af4804c8"  /media/storage             ext4    defaults  0       2

# LABEL=Storage /mnt/Storage auto nosuid,nodev,nofail,x-gvfs-show 0 0
# /dev/disk/by-path/pci-0000:00:1f.2-ata-1-part4 /mnt/pci-0000:00:1f.2-ata-1-part4 auto rw,user,exec,nosuid,nodev,nofail,sync,noauto,x-gvfs-show 0 0

# mount sdc1 on /data
#UUID="ea63af7b-4174-4dfc-956d-fd97da4e63b3"  /home/leon/Storage             ext4    defaults  0       2
#/dev/fd0 /media/floppy0 auto rw,user,exec,utf8,noauto,x-gvfs-show 0 0


Here's snap list:
> Name                             Version                     Rev    Tracking         Publisher   Notes
audacity                         3.1.3                       992    latest/stable    diddledani  -
bare                             1.0                         5      latest/stable    canonical&#10003;  base
chromium                         101.0.4951.64               1993   latest/stable    canonical&#10003;  -
core                             16-2.55.5                   13250  latest/stable    canonical&#10003;  core
core18                           20220428                    2409   latest/stable    canonical&#10003;  base
core20                           20220329                    1434   latest/stable    canonical&#10003;  base
firefox                          100.0.2-1                   1377   latest/stable/&#8230;  mozilla&#10003;    -
gedit                            40.1-14-g0850b4ae32         653    latest/stable    canonical&#10003;  -
gnome-3-28-1804                  3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;  -
gnome-3-38-2004                  0+git.1f9014a               99     latest/stable/&#8230;  canonical&#10003;  -
gnome-system-monitor             41.0-5-g91e67f7982          174    latest/stable    canonical&#10003;  -
gtk-common-themes                0.1-79-ga83e90c             1534   latest/stable/&#8230;  canonical&#10003;  -
gtk2-common-themes               0.1                         13     latest/stable    canonical&#10003;  -
kde-frameworks-5-qt-5-15-core20  5.79.0                      14     latest/stable    kde&#10003;        -
okteta                           0.26.6                      15     latest/stable    kde&#10003;        -
skype                            8.83.0.408                  209    latest/stable    skype&#10003;      -
smplayer                         22.2.0                      58     latest/stable    rvm         -
snapd                            2.55.5                      15904  latest/stable    canonical&#10003;  snapd
solitaire                        1.1                         5      latest/stable    1bsyl       -
supertuxkart                     1.3                         645    latest/stable    diddledani  -
vlc                              3.0.16                      2344   latest/stable    videolan&#10003;   -


And apt-cache policy smplayer:
> smplayer:
  Installed: (none)
  Candidate: 21.10.0~ds0-1
  Version table:
     21.10.0~ds0-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages

---

### Post by peyre on 2022-05-25
Now, the Disks utility does offer me the option to Take Ownership of the drive.  Should I try that?

---

### Post by peyre on 2022-05-26
Well, I set it to mount once again to ~/Storage, and now SMPlayer works.  I guess I'll go with that.

---

### Post by #&amp;thj^% on 2022-05-27
I had faith in you, Good Job!

---

