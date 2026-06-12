---
title: "Updating Plex on Ubuntu"
date: 2022-07-01
forum: Multimedia Software
---

### Post by laspo on 2022-07-01
Hi, I'm an Ubuntu noob but I managed to install Plex and it's working well. However, when I try updating plexmediaserver with "sudo apt upgrade plexmediaserver -y", I get several errors in the Pre-installation Validation which I think is the cause why it fails (log below). What am I doing wrong and how can I fix it?

```
laspo@nas:~$ sudo apt upgrade plexmediaserver -y
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 shim
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  distro-info libatasmart4 libblockdev-crypto2 libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 libblockdev-part2 libblockdev-swap2 libblockdev-utils2 libblockdev2 libevdev2 libfwupdplugin5 libimobiledevice6 libjcat1
  libmbim-glib4 libmbim-proxy libmm-glib0 libnspr4 libnss3 libparted-fs-resize0 libplist3 libqmi-glib5 libqmi-proxy libudisks2-0 libupower-glib3 libusbmuxd6 libvolume-key1 modemmanager udisks2 upower usb-modeswitch usb-modeswitch-data
  usbmuxd
The following packages will be upgraded:
  alsa-ucm-conf apt apt-utils base-files bolt cloud-initramfs-copymods cloud-initramfs-dyn-netconf command-not-found fwupd fwupd-signed grub-common grub2-common initramfs-tools initramfs-tools-bin initramfs-tools-core kmod
  landscape-common libapt-pkg6.0 libasound2 libasound2-data libc-bin libcephfs2 libfwupd2 libfwupdplugin1 libglib2.0-0 libglib2.0-bin libglib2.0-data libkeyutils1 libkmod2 libnetplan0 libnss-systemd libnvpair1linux libpam-modules
  libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpci3 libprocps8 librados2 libsystemd0 libudev1 libuutil1linux libwbclient0 libxmlb1 libzfs2linux libzpool2linux linux-base linux-firmware locales login netplan.io
  open-iscsi open-vm-tools openssh-client openssh-server openssh-sftp-server overlayroot passwd pciutils plexmediaserver pollinate procps python-apt-common python3-apt python3-commandnotfound python3-distupgrade python3-samba
  python3-software-properties python3-update-manager samba samba-common samba-common-bin samba-dsdb-modules samba-libs samba-vfs-modules sbsigntool shim shim-signed snapd software-properties-common sosreport systemd systemd-sysv
  systemd-timesyncd thermald tmux ubuntu-advantage-tools ubuntu-keyring ubuntu-release-upgrader-core udev ufw update-manager-core update-notifier-common wget zfs-zed zfsutils-linux
97 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/292 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up libc6:amd64 (2.31-0ubuntu9.9) ...
(Reading database ... 149605 files and directories currently installed.)
Preparing to unpack .../plexmediaserver_1.27.1.5916-6b0e31a64_amd64.deb ...
PlexMediaServer install: Pre-installation Validation.
PlexMediaServer install: Error: Unknown username " laspo" used in "/etc/systemd/system/plexmediaserver.service.d/override.conf".
PlexMediaServer install: Error: Unknown group " laspo" used in "/etc/systemd/system/plexmediaserver.service.d/override.conf".
PlexMediaServer install: Warning:  "/media/PLEX_DATA/Library/Application Support" isn't owned by "plex", UID: 997.  Found "laspo", UID: 1000 instead. Continuing.
PlexMediaServer install:
PlexMediaServer install: Pre-installation Validation failed.
PlexMediaServer install: Configuration information discovered:
PlexMediaServer install:   Installation Type:   Update
PlexMediaServer install:   Process Control:     systemd
PlexMediaServer install:   Plex User:           plex
PlexMediaServer install:   Plex Group:          plex
PlexMediaServer install:   Video Group:         video
PlexMediaServer install:   Metadata Dir:        /media/PLEX_DATA/Library/Application Support
PlexMediaServer install:   Temp Directory:      /tmp
PlexMediaServer install:   Lang Encoding:       en_US.UTF-8
PlexMediaServer install:   Config file used:   /etc/systemd/system/plexmediaserver.service.d/override.conf
PlexMediaServer install:   Intel i915 Hardware: Not found
PlexMediaServer install:   Nvidia GPU card:     Not Found
PlexMediaServer install:
PlexMediaServer install: Pre-installation Validation complete.  Errors: 2, Warnings: 1
dpkg: error processing archive /var/cache/apt/archives/plexmediaserver_1.27.1.5916-6b0e31a64_amd64.deb (--unpack):
 new plexmediaserver package pre-installation script subprocess returned error exit status 1
Preparing to unpack .../base-files_11ubuntu5.5_amd64.deb ...
Warning: Stopping motd-news.service, but it can still be activated by:
  motd-news.timer
Unpacking base-files (11ubuntu5.5) over (11ubuntu5.3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/plexmediaserver_1.27.1.5916-6b0e31a64_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by TheFu on 2022-07-01
How did you install plex?  If using a repo, then updates happen automatically, if you downloaded a .deb file, you'll need to periodically check for a newer .deb file to be pulled down manually and perform an "install" of that. No need to remove the old version.  Just set a calendar reminder to check for a newer .deb file each month.  If you don't allow external access to your Plex server, you can easily go longer between checks.  I don't allow any outside access and block Plex from phoning home, so running an older version has little risks (only if you don't allow outside access).

I have plex running here for a few years, but decided that the plex clients and lack of privacy for everything plex-y is worth switching to a different option - Jellyfin.  Jellyfin doesn't phone home every time you click anywhere and integrates with live TV and recording HDHomerun devices really well.  Jellyfin is free and F/LOSS, so are the clients or you can use any DLNA renderer/controller that you like with it.  It will transcode for different clients as needed. If your GPU supports hardware-based transcoding, that can be enabled too.

Jellyfin isn't perfect. In some ways it isn't as easy as plex, but how much is our privacy worth?  That's a question for each individual.

---

### Post by ajgreeny on 2022-07-01
I would also recommend jellyfin for many users even though I do not currently use it myself.

My main use of a mediaserver is to stream music, video and photographs to my LG smart TV but regrettably jellyfin does not yet have a client app for LG TVs so I can not easily use it.  In theory it is possible using the webclient in the TV's web-browser but in practice that is just too difficult and long winded so not really a sensible alternative.

I currently use Emby-mediaserver which used to be open-source but is now closed-source and is becoming almost as intrusive as Plex in terms of wanting users to pay for many of its uses, eg live TV.  Jellyfin is a fork of Emby from when Emby was open-source so has many similarities with Emby and as soon as jellyfin has a client for my TV I shall remove Emby and use jellyfin in its place.

---

### Post by TheFu on 2022-07-01
Jellyfin has a DLNA server build-in, so any DLNA controller and/or renderer can be used.  On android, I use VLC.  On my raspberry pi v2/3 devices, I use Kodi (in DLNA mode).
I use the webapp client to manage the library. That can be done from any browser in the network here. I've played with the android Jellyfin client application and it is fine, but I much prefer to use VLC.

There is a huge negative with jellyfin, at least to me. It uses mono/dotNet.  There are many bugs I'd love to fix, but I refuse to learn and setup a dotNet environment. I just can't do it.  Long time linux users understand why.  For me, which of the options does enough of what I need and doesn't make me feel 'dirty' too much is the question. As much as I dislike mono/dotNet, I like privacy more, so I can hold my nose and use Jellyfin.  

Emby is one of those open-Core programs, which I dislike even more after being burned by a few others over the decades.  Free isn't always free.  Jellyfin has a clear statement on their project website that they will never add tracking of their users and that the only tracking performed is by metadata scrapers web-sites ... obviously, TheTVDB and OpenMoviesDB will see the queries and data returned from those requests, so that tracking will happen, but it is a 2-way street. We get good access to the kewl media metadata we all like in exchange for them knowing a bit about our libraries.  The Jellyfin team knows nothing about this, unlike Plex corporate.

But many people don't care if they are tracked and don't know about other options, so plex is fine. It is their choice to make.

---

### Post by ajgreeny on 2022-07-02
I did try the built in DLNA server of  jellyfin but found it too clunky for general use and it did not manage to find or play any any of thr .ts files that are produced when I record TV programs to a USB disk on an old TV that still works here.

I could encode them to .mkv or .mp4 videos but just can't be bothered so still use Emby which will play those .ts videos.

---

### Post by TheFu on 2022-07-02
recorded OTA TV in the USA is mpeg2 video. At hidef resolutions, most cheap streaming sticks don't have the power to decode and play that content. Initially, those devices didn't even include mpeg2 codec support at all.

So, what is necessary is to disable directplay in Jellyfin and setup transcoding to h.264 (vp8) video. For me, making that the mandated default was easiest.  None of my player devices can handle h.265 (vp9).  If the transcoding can't be setup, there is a post-recording script capability in jellyfin that is worth checking out.  [https://www.reddit.com/r/jellyfin/comments/sz8tnq/a_much_more_detailed_guide_on_how_to_use_post/](https://www.reddit.com/r/jellyfin/comments/sz8tnq/a_much_more_detailed_guide_on_how_to_use_post/) It does require some javascript changes to the dotNet interface, but adding the javascript is build-into the existing webapp GUI.  Scripting which actions are to be taken can use any shell script language.  For recorded TV, just running the recorded files through a comskip processor can mark where the commercial blocks are. Why watch 62 minutes when only 40-42 are needed?

OTOH, I find it easier to just run a cron-task every 30 minutes that finds newly static files in the recording directories and perform simple transcoding. This is fine, since 99% of recorded TV isn't going to be archived.  The update to ffmpeg5 in recent jellyfin packages helps with all sorts of prior issues. The changelog: [https://github.com/FFmpeg/FFmpeg/blob/ce4d459db186a7d8ac842685cd6256c9ac1b7f25/Changelog](https://github.com/FFmpeg/FFmpeg/blob/ce4d459db186a7d8ac842685cd6256c9ac1b7f25/Changelog)  Sadly, they haven't included a fix for multi-part m3u8 recordings for internet streams.  Sigh.  That's an ffmpeg issue, not Jellyfin, though I'd love to easily record IPTV channels through jellyfin - schedule data has been working for a long time, but having 500 channels and nothing to watch currently is still the same issue today as it was in 1985. ;)

Clunky is subjective for DLNA. There are great things about it and bad things.  The Jellyfin DLNA doesn't get/receive current playback location information from clients, which can be a hassle for many people.  Plex handles this better, most definitely.

---

