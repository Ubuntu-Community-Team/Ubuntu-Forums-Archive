---
title: "No image in Cheese/Skype webcam issue"
date: 2013-02-22
forum: Multimedia Software
---

### Post by alexmoon on 2013-02-22
Hi,

After the latest update, the image from my webcam is displaying as just black (I've tried in Cheese, Skype, and guvcview and got the same result). I've double-checked that I didn't accidentally turn off my webcam, but I haven't. 

I've been looking around some other threads, and I've included the outputs of some of the common requests for information here: 

The output of lsusb is:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 005: ID 5149:13d3  

```

The output of ls /dev/v* is:
```
/dev/vcs   /dev/vcs2  /dev/vcs4  /dev/vcs6   /dev/vcsa   /dev/vcsa2  /dev/vcsa4  /dev/vcsa6   /dev/vga_arbiter
/dev/vcs1  /dev/vcs3  /dev/vcs5  /dev/vcs63  /dev/vcsa1  /dev/vcsa3  /dev/vcsa5  /dev/vcsa63  /dev/video0

```

Running Cheese through the terminal gets this:
```
(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:6713): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (totem-video-thumbnailer:6721): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:6721): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:6721): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:6721): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:6721): WARNING **: Could not take screenshot: no last video frame
totem-video-thumbnailer couldn't get a picture from 'file:///home/sky/Videos/Webcam/2011-12-20-174120.ogv'

** (cheese:6713): WARNING **: could not generate thumbnail for /home/sky/Videos/Webcam/2011-12-20-174120.ogv (video/ogg)


** (cheese:6713): WARNING **: could not generate thumbnail for /home/sky/Pictures/Webcam/2012-11-30-154257.jpg (image/jpeg)

```

I've tried this:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

and also

LD_PRELOAD=/usr/lib/libv4l2/v4l2compat.so cheese

neither of which had any affect.

Any ideas on what to try next?

Thanks,
sky.

---

### Post by alexmoon on 2013-02-24
Ray suggested that I post the results of /var/log/dpkg.log, trimmed to more or less the date the problem emerged, in order to try to work out which bit is the problematic bit and downgrade it:

```
2013-02-22 11:52:49 startup archives unpack
2013-02-22 11:53:05 upgrade libssl1.0.0 1.0.1-4ubuntu5.5 1.0.1-4ubuntu5.6
2013-02-22 11:53:05 status half-configured libssl1.0.0 1.0.1-4ubuntu5.5
2013-02-22 11:53:05 status unpacked libssl1.0.0 1.0.1-4ubuntu5.5
2013-02-22 11:53:06 status half-configured libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-22 11:53:06 status half-installed libssl1.0.0 1.0.1-4ubuntu5.5
2013-02-22 11:53:06 status half-installed libssl1.0.0 1.0.1-4ubuntu5.5
2013-02-22 11:53:06 status unpacked libssl1.0.0 1.0.1-4ubuntu5.6
2013-02-22 11:53:06 status unpacked libssl1.0.0 1.0.1-4ubuntu5.6
2013-02-22 11:53:07 upgrade libssl1.0.0:i386 1.0.1-4ubuntu5.5 1.0.1-4ubuntu5.6
2013-02-22 11:53:07 status half-configured libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-22 11:53:07 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-22 11:53:07 status half-installed libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-22 11:53:07 status half-installed libssl1.0.0:i386 1.0.1-4ubuntu5.5
2013-02-22 11:53:08 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.6
2013-02-22 11:53:08 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.6
2013-02-22 11:53:09 startup packages configure
2013-02-22 11:53:09 configure libssl1.0.0 1.0.1-4ubuntu5.6 <none>
2013-02-22 11:53:09 status unpacked libssl1.0.0 1.0.1-4ubuntu5.6
2013-02-22 11:53:09 status half-configured libssl1.0.0 1.0.1-4ubuntu5.6
2013-02-22 11:53:10 status installed libssl1.0.0 1.0.1-4ubuntu5.6
2013-02-22 11:53:10 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-02-22 11:53:10 configure libssl1.0.0:i386 1.0.1-4ubuntu5.6 <none>
2013-02-22 11:53:10 status unpacked libssl1.0.0:i386 1.0.1-4ubuntu5.6
2013-02-22 11:53:11 status half-configured libssl1.0.0:i386 1.0.1-4ubuntu5.6
2013-02-22 11:53:11 status installed libssl1.0.0:i386 1.0.1-4ubuntu5.6
2013-02-22 11:53:11 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-02-22 11:53:11 status half-configured libc-bin 2.15-0ubuntu10.3
2013-02-22 11:53:13 status installed libc-bin 2.15-0ubuntu10.3
2013-02-22 11:53:14 startup archives unpack
2013-02-22 11:53:15 upgrade linux-image-3.2.0-38-generic 3.2.0-38.60 3.2.0-38.61
2013-02-22 11:53:15 status half-configured linux-image-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:15 status unpacked linux-image-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:15 status half-installed linux-image-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:24 status half-installed linux-image-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:25 status unpacked linux-image-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:53:25 status unpacked linux-image-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:53:25 upgrade icedtea-6-jre-cacao 6b27-1.12.1-2ubuntu0.12.04.2 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:25 status half-configured icedtea-6-jre-cacao 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:25 status unpacked icedtea-6-jre-cacao 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:25 status half-installed icedtea-6-jre-cacao 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:26 status half-installed icedtea-6-jre-cacao 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:26 status unpacked icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:26 status unpacked icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:26 upgrade openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.04.2 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:26 status half-configured openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:26 status unpacked openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:26 status half-installed openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:27 status half-installed openjdk-6-jre-lib 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:27 status unpacked openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:27 status unpacked openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:28 upgrade icedtea-6-jre-jamvm 6b27-1.12.1-2ubuntu0.12.04.2 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:28 status half-configured icedtea-6-jre-jamvm 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:28 status unpacked icedtea-6-jre-jamvm 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:28 status half-installed icedtea-6-jre-jamvm 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:28 status half-installed icedtea-6-jre-jamvm 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:28 status unpacked icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:28 status unpacked icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:29 upgrade openjdk-6-jre-headless 6b27-1.12.1-2ubuntu0.12.04.2 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:29 status half-configured openjdk-6-jre-headless 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:29 status unpacked openjdk-6-jre-headless 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:29 status half-installed openjdk-6-jre-headless 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:32 status half-installed openjdk-6-jre-headless 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:32 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:32 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:32 upgrade openssl 1.0.1-4ubuntu5.5 1.0.1-4ubuntu5.6
2013-02-22 11:53:32 status half-configured openssl 1.0.1-4ubuntu5.5
2013-02-22 11:53:32 status unpacked openssl 1.0.1-4ubuntu5.5
2013-02-22 11:53:33 status half-installed openssl 1.0.1-4ubuntu5.5
2013-02-22 11:53:33 status triggers-pending man-db 2.6.1-2ubuntu1
2013-02-22 11:53:33 status half-installed openssl 1.0.1-4ubuntu5.5
2013-02-22 11:53:33 status half-installed openssl 1.0.1-4ubuntu5.5
2013-02-22 11:53:33 status unpacked openssl 1.0.1-4ubuntu5.6
2013-02-22 11:53:33 status unpacked openssl 1.0.1-4ubuntu5.6
2013-02-22 11:53:34 upgrade linux-headers-3.2.0-38 3.2.0-38.60 3.2.0-38.61
2013-02-22 11:53:34 status half-configured linux-headers-3.2.0-38 3.2.0-38.60
2013-02-22 11:53:34 status unpacked linux-headers-3.2.0-38 3.2.0-38.60
2013-02-22 11:53:34 status half-installed linux-headers-3.2.0-38 3.2.0-38.60
2013-02-22 11:53:38 status half-installed linux-headers-3.2.0-38 3.2.0-38.60
2013-02-22 11:53:39 status unpacked linux-headers-3.2.0-38 3.2.0-38.61
2013-02-22 11:53:39 status unpacked linux-headers-3.2.0-38 3.2.0-38.61
2013-02-22 11:53:39 upgrade linux-headers-3.2.0-38-generic 3.2.0-38.60 3.2.0-38.61
2013-02-22 11:53:39 status half-configured linux-headers-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:39 status unpacked linux-headers-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:39 status half-installed linux-headers-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:41 status half-installed linux-headers-3.2.0-38-generic 3.2.0-38.60
2013-02-22 11:53:41 status unpacked linux-headers-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:53:41 status unpacked linux-headers-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:53:42 upgrade linux-libc-dev 3.2.0-38.60 3.2.0-38.61
2013-02-22 11:53:42 status half-configured linux-libc-dev 3.2.0-38.60
2013-02-22 11:53:42 status unpacked linux-libc-dev 3.2.0-38.60
2013-02-22 11:53:42 status half-installed linux-libc-dev 3.2.0-38.60
2013-02-22 11:53:45 status half-installed linux-libc-dev 3.2.0-38.60
2013-02-22 11:53:45 status unpacked linux-libc-dev 3.2.0-38.61
2013-02-22 11:53:45 status unpacked linux-libc-dev 3.2.0-38.61
2013-02-22 11:53:45 upgrade openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:45 status half-configured openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status unpacked openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-22 11:53:46 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-22 11:53:46 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-22 11:53:46 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:46 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-02-22 11:53:46 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:47 status half-installed openjdk-6-jre 6b27-1.12.1-2ubuntu0.12.04.2
2013-02-22 11:53:47 status unpacked openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:47 status unpacked openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:53:47 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-02-22 11:53:47 status half-configured man-db 2.6.1-2ubuntu1
2013-02-22 11:53:50 status installed man-db 2.6.1-2ubuntu1
2013-02-22 11:53:50 trigproc bamfdaemon 0.2.124.2-0ubuntu1 0.2.124.2-0ubuntu1
2013-02-22 11:53:50 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-22 11:53:50 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-22 11:53:50 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-02-22 11:53:50 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-22 11:53:50 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-22 11:53:51 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-02-22 11:53:51 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-22 11:53:51 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-22 11:53:51 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-02-22 11:53:51 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-02-22 11:53:59 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-02-22 11:54:00 startup packages configure
2013-02-22 11:54:00 configure linux-image-3.2.0-38-generic 3.2.0-38.61 <none>
2013-02-22 11:54:00 status unpacked linux-image-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:00 status half-configured linux-image-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:17 status installed linux-image-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:17 configure openssl 1.0.1-4ubuntu5.6 <none>
2013-02-22 11:54:17 status unpacked openssl 1.0.1-4ubuntu5.6
2013-02-22 11:54:17 status unpacked openssl 1.0.1-4ubuntu5.6
2013-02-22 11:54:17 status half-configured openssl 1.0.1-4ubuntu5.6
2013-02-22 11:54:17 status installed openssl 1.0.1-4ubuntu5.6
2013-02-22 11:54:17 configure linux-headers-3.2.0-38 3.2.0-38.61 <none>
2013-02-22 11:54:17 status unpacked linux-headers-3.2.0-38 3.2.0-38.61
2013-02-22 11:54:18 status half-configured linux-headers-3.2.0-38 3.2.0-38.61
2013-02-22 11:54:18 status installed linux-headers-3.2.0-38 3.2.0-38.61
2013-02-22 11:54:18 configure linux-headers-3.2.0-38-generic 3.2.0-38.61 <none>
2013-02-22 11:54:18 status unpacked linux-headers-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:18 status half-configured linux-headers-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:18 status installed linux-headers-3.2.0-38-generic 3.2.0-38.61
2013-02-22 11:54:18 configure linux-libc-dev 3.2.0-38.61 <none>
2013-02-22 11:54:18 status unpacked linux-libc-dev 3.2.0-38.61
2013-02-22 11:54:18 status half-configured linux-libc-dev 3.2.0-38.61
2013-02-22 11:54:18 status installed linux-libc-dev 3.2.0-38.61
2013-02-22 11:54:18 configure openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04 <none>
2013-02-22 11:54:18 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:18 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:18 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:19 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:20 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:20 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:21 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:21 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:21 status unpacked openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:21 status half-configured openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 status installed openjdk-6-jre-headless 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 configure openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04 <none>
2013-02-22 11:54:22 status unpacked openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 status half-configured openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 status installed openjdk-6-jre-lib 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 configure icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04 <none>
2013-02-22 11:54:22 status unpacked icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 status half-configured icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 status installed icedtea-6-jre-cacao 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:22 configure icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04 <none>
2013-02-22 11:54:22 status unpacked icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:23 status half-configured icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:23 status installed icedtea-6-jre-jamvm 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:23 configure openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04 <none>
2013-02-22 11:54:23 status unpacked openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:23 status half-configured openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04
2013-02-22 11:54:23 status installed openjdk-6-jre 6b27-1.12.3-0ubuntu1~12.04
2013-02-23 07:59:55 startup packages remove
2013-02-23 07:59:55 status installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:01 remove cheese 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:00:01 status half-configured cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:01 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:01 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:00:01 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:02 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:00:02 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:02 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:00:02 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:02 status triggers-pending man-db 2.6.1-2ubuntu1
2013-02-23 08:00:02 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:02 status config-files cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:02 status config-files cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 status config-files cheese 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 status not-installed cheese <none>
2013-02-23 08:00:03 status installed libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 remove libcheese-gtk21 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:00:03 status half-configured libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 status half-installed libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-02-23 08:00:03 status config-files libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:00:03 status config-files libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status installed libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 remove libcheese3 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:00:04 status half-configured libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status half-installed libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status config-files libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status config-files libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 remove cheese-common 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:00:04 status half-configured cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:04 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:05 status triggers-pending libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:00:05 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:05 status triggers-pending libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:00:05 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:05 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:00:05 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:06 status config-files cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:06 status config-files cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:06 status config-files cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:00:06 status not-installed cheese-common <none>
2013-02-23 08:00:06 status installed gnome-video-effects 0.4.0-1
2013-02-23 08:00:06 remove gnome-video-effects 0.4.0-1 <none>
2013-02-23 08:00:06 status half-configured gnome-video-effects 0.4.0-1
2013-02-23 08:00:06 status half-installed gnome-video-effects 0.4.0-1
2013-02-23 08:00:06 status config-files gnome-video-effects 0.4.0-1
2013-02-23 08:00:06 status config-files gnome-video-effects 0.4.0-1
2013-02-23 08:00:07 status config-files gnome-video-effects 0.4.0-1
2013-02-23 08:00:07 status not-installed gnome-video-effects <none>
2013-02-23 08:00:07 status installed libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:00:07 remove libclutter-gst-1.0-0 1.5.4-0ubuntu2 <none>
2013-02-23 08:00:07 status half-configured libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:00:07 status half-installed libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:00:07 status config-files libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:00:07 status config-files libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:00:07 status installed libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:00:07 remove libclutter-gtk-1.0-0 1.2.0-0ubuntu1 <none>
2013-02-23 08:00:07 status half-configured libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:00:08 status half-installed libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:00:08 status config-files libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:00:08 status config-files libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:00:08 status installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:08 remove libmx-1.0-2 1.4.3-0ubuntu1 <none>
2013-02-23 08:00:08 status half-configured libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:08 status half-installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:08 status half-installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:09 status config-files libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:09 status config-files libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:00:09 status installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:09 remove libclutter-imcontext-0.1-0 0.1.4-2build1 <none>
2013-02-23 08:00:09 status half-configured libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:09 status half-installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:09 status half-installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:10 status config-files libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:10 status config-files libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:00:10 status installed libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:00:10 remove libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3 <none>
2013-02-23 08:00:10 status half-configured libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:00:10 status half-installed libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:00:10 status config-files libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:00:10 status config-files libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:00:10 trigproc bamfdaemon 0.2.124.2-0ubuntu1 <none>
2013-02-23 08:00:10 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:00:10 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:00:10 trigproc desktop-file-utils 0.20-0ubuntu3 <none>
2013-02-23 08:00:10 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:00:11 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:00:11 trigproc gnome-menus 3.4.0-0ubuntu1 <none>
2013-02-23 08:00:11 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:00:11 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:00:11 trigproc man-db 2.6.1-2ubuntu1 <none>
2013-02-23 08:00:11 status half-configured man-db 2.6.1-2ubuntu1
2013-02-23 08:00:13 status installed man-db 2.6.1-2ubuntu1
2013-02-23 08:00:13 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-02-23 08:00:13 status half-configured libc-bin 2.15-0ubuntu10.3
2013-02-23 08:00:14 status installed libc-bin 2.15-0ubuntu10.3
2013-02-23 08:00:14 trigproc libglib2.0-0:i386 2.32.3-0ubuntu1 <none>
2013-02-23 08:00:14 status half-configured libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:00:15 status installed libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:00:16 trigproc libglib2.0-0 2.32.3-0ubuntu1 <none>
2013-02-23 08:00:16 status half-configured libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:00:16 status installed libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:00:16 trigproc hicolor-icon-theme 0.12-1ubuntu2 <none>
2013-02-23 08:00:16 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:00:24 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:01:50 startup archives unpack
2013-02-23 08:01:51 install libclutter-gst-1.0-0 1.5.4-0ubuntu2 1.5.4-0ubuntu2
2013-02-23 08:01:51 status half-installed libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:01:52 status unpacked libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:01:52 status unpacked libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:01:52 install cheese-common <none> 3.4.1-0ubuntu2.1
2013-02-23 08:01:52 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:52 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:01:52 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:52 status triggers-pending libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:01:52 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:52 status triggers-pending libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:01:53 status half-installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:53 status unpacked cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:53 status unpacked cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:01:54 install libcheese3 3.4.1-0ubuntu2.1 3.4.1-0ubuntu2.1
2013-02-23 08:01:54 status half-installed libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:01:54 status unpacked libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:01:54 status unpacked libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:01:54 install libclutter-gtk-1.0-0 1.2.0-0ubuntu1 1.2.0-0ubuntu1
2013-02-23 08:01:54 status half-installed libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:01:55 status unpacked libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:01:55 status unpacked libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:01:55 install libclutter-imcontext-0.1-0 0.1.4-2build1 0.1.4-2build1
2013-02-23 08:01:55 status half-installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:01:55 status triggers-pending man-db 2.6.1-2ubuntu1
2013-02-23 08:01:55 status half-installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:01:56 status unpacked libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:01:56 status unpacked libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:01:56 install libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3 0.0.2.1-2ubuntu3
2013-02-23 08:01:56 status half-installed libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:01:56 status unpacked libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:01:57 status unpacked libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:01:57 install libmx-1.0-2 1.4.3-0ubuntu1 1.4.3-0ubuntu1
2013-02-23 08:01:57 status half-installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:01:57 status half-installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:01:57 status unpacked libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:01:57 status unpacked libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:01:58 install libcheese-gtk21 3.4.1-0ubuntu2.1 3.4.1-0ubuntu2.1
2013-02-23 08:01:58 status half-installed libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:01:58 status unpacked libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:01:58 status unpacked libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:01:58 install gnome-video-effects <none> 0.4.0-1
2013-02-23 08:01:58 status half-installed gnome-video-effects 0.4.0-1
2013-02-23 08:01:59 status unpacked gnome-video-effects 0.4.0-1
2013-02-23 08:01:59 status unpacked gnome-video-effects 0.4.0-1
2013-02-23 08:01:59 install cheese <none> 3.4.1-0ubuntu2.1
2013-02-23 08:01:59 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:01:59 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:01:59 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:01:59 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:01:59 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:01:59 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:01:59 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:02:00 status half-installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:00 status unpacked cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:00 status unpacked cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:00 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-02-23 08:02:00 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:02:01 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-02-23 08:02:01 trigproc libglib2.0-0:i386 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2013-02-23 08:02:01 status half-configured libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:02:01 status installed libglib2.0-0:i386 2.32.3-0ubuntu1
2013-02-23 08:02:02 trigproc libglib2.0-0 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2013-02-23 08:02:02 status half-configured libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:02:02 status installed libglib2.0-0 2.32.3-0ubuntu1
2013-02-23 08:02:02 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-02-23 08:02:02 status half-configured man-db 2.6.1-2ubuntu1
2013-02-23 08:02:03 status installed man-db 2.6.1-2ubuntu1
2013-02-23 08:02:03 trigproc bamfdaemon 0.2.124.2-0ubuntu1 0.2.124.2-0ubuntu1
2013-02-23 08:02:03 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:02:03 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:02:03 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-02-23 08:02:03 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:02:03 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:02:03 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-02-23 08:02:03 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:02:03 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:02:04 startup packages configure
2013-02-23 08:02:04 configure libclutter-gst-1.0-0 1.5.4-0ubuntu2 <none>
2013-02-23 08:02:04 status unpacked libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:02:04 status half-configured libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:02:04 status installed libclutter-gst-1.0-0 1.5.4-0ubuntu2
2013-02-23 08:02:05 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-02-23 08:02:05 configure cheese-common 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:02:05 status unpacked cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 status half-configured cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 status installed cheese-common 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 configure libcheese3 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:02:05 status unpacked libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 status half-configured libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 status installed libcheese3 3.4.1-0ubuntu2.1
2013-02-23 08:02:05 configure libclutter-gtk-1.0-0 1.2.0-0ubuntu1 <none>
2013-02-23 08:02:05 status unpacked libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:02:05 status half-configured libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:02:05 status installed libclutter-gtk-1.0-0 1.2.0-0ubuntu1
2013-02-23 08:02:06 configure libclutter-imcontext-0.1-0 0.1.4-2build1 <none>
2013-02-23 08:02:06 status unpacked libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:02:06 status half-configured libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:02:06 status installed libclutter-imcontext-0.1-0 0.1.4-2build1
2013-02-23 08:02:06 configure libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3 <none>
2013-02-23 08:02:06 status unpacked libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:02:06 status half-configured libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:02:06 status installed libcluttergesture-0.0.2-0 0.0.2.1-2ubuntu3
2013-02-23 08:02:06 configure libmx-1.0-2 1.4.3-0ubuntu1 <none>
2013-02-23 08:02:06 status unpacked libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:02:06 status half-configured libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:02:06 status installed libmx-1.0-2 1.4.3-0ubuntu1
2013-02-23 08:02:06 configure libcheese-gtk21 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:02:06 status unpacked libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 status half-configured libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 status installed libcheese-gtk21 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 configure gnome-video-effects 0.4.0-1 <none>
2013-02-23 08:02:07 status unpacked gnome-video-effects 0.4.0-1
2013-02-23 08:02:07 status half-configured gnome-video-effects 0.4.0-1
2013-02-23 08:02:07 status installed gnome-video-effects 0.4.0-1
2013-02-23 08:02:07 configure cheese 3.4.1-0ubuntu2.1 <none>
2013-02-23 08:02:07 status unpacked cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 status half-configured cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 status installed cheese 3.4.1-0ubuntu2.1
2013-02-23 08:02:07 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-02-23 08:02:07 status half-configured libc-bin 2.15-0ubuntu10.3
2013-02-23 08:02:07 status installed libc-bin 2.15-0ubuntu10.3
2013-02-23 08:10:22 startup archives unpack
2013-02-23 08:10:23 install guvcview <none> 1.5.3-0ubuntu1
2013-02-23 08:10:23 status half-installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:23 status triggers-pending man-db 2.6.1-2ubuntu1
2013-02-23 08:10:23 status half-installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:23 status triggers-pending bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:10:23 status half-installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:24 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:10:24 status half-installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:24 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:10:24 status half-installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:24 status unpacked guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:24 status unpacked guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:25 install libwebcam0 <none> 0.2.1-1build1
2013-02-23 08:10:25 status half-installed libwebcam0 0.2.1-1build1
2013-02-23 08:10:25 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:25 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:25 install uvcdynctrl-data <none> 0.2.1-1build1
2013-02-23 08:10:25 status half-installed uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:26 status unpacked uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:26 status unpacked uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:26 install uvcdynctrl <none> 0.2.1-1build1
2013-02-23 08:10:26 status half-installed uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:26 status half-installed uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:26 status unpacked uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:26 status unpacked uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:26 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-02-23 08:10:26 status half-configured man-db 2.6.1-2ubuntu1
2013-02-23 08:10:28 status installed man-db 2.6.1-2ubuntu1
2013-02-23 08:10:28 trigproc bamfdaemon 0.2.124.2-0ubuntu1 0.2.124.2-0ubuntu1
2013-02-23 08:10:28 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:10:28 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-02-23 08:10:28 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-02-23 08:10:28 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:10:28 status installed desktop-file-utils 0.20-0ubuntu3
2013-02-23 08:10:28 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-02-23 08:10:28 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:10:28 status installed gnome-menus 3.4.0-0ubuntu1
2013-02-23 08:10:29 startup packages configure
2013-02-23 08:10:29 configure guvcview 1.5.3-0ubuntu1 <none>
2013-02-23 08:10:29 status unpacked guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:29 status half-configured guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:29 status installed guvcview 1.5.3-0ubuntu1
2013-02-23 08:10:29 configure libwebcam0 0.2.1-1build1 <none>
2013-02-23 08:10:29 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 status half-configured libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 status installed libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-02-23 08:10:30 configure uvcdynctrl-data 0.2.1-1build1 <none>
2013-02-23 08:10:30 status unpacked uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:30 status half-configured uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:30 status installed uvcdynctrl-data 0.2.1-1build1
2013-02-23 08:10:30 configure uvcdynctrl 0.2.1-1build1 <none>
2013-02-23 08:10:30 status unpacked uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:30 status half-configured uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:30 status installed uvcdynctrl 0.2.1-1build1
2013-02-23 08:10:30 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-02-23 08:10:30 status half-configured libc-bin 2.15-0ubuntu10.3
2013-02-23 08:10:30 status installed libc-bin 2.15-0ubuntu10.3
```

My only guess is that the problem is related to the shift from video for linux 1 to v4l2, maybe this is the gnome-video-effects bit? Or maybe not?

---

### Post by madrabbit on 2013-02-24
Thanks for posting that! Seems there are several packages related to webcams that got upgraded. Listing them in order of likelihood (SWAG):

gnome-video-effects

libwebcam0

uvcdynctrl
uvcdynctrl-data

cheese
cheese-common
libcheese3
libcheese-gtk21

libcluttergesture-0.0.2-0
libclutter-gst-1.0-0
libclutter-gtk-1.0-0
libclutter-imcontext-0.1-0

....aaaaaand then all the rest. Cuz you never know. (That's why they're bugs -- they're surprising.)

As for downgrading, you may have previous versions of these packages in your /var/cache/apt/archives/ directory. cd there, and do an ls -ltr *<package_name_here>* to see if there is something older you can downgrade to via sudo dpkg -i <filename>

---

### Post by madrabbit on 2013-02-24
If you can't find an older version on your local apt archives, you can download them from your local mirror (probably [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/) ?). Go to the mirror's 'ubuntu/pool/main' (mine is [http://us.archive.ubuntu.com/ubuntu/pool/main/](http://us.archive.ubuntu.com/ubuntu/pool/main/)), and there'll be a bunch of subdirectories containing older versions of packages you can download and install.

There's one other step, though. You'll want to downgrade the packages in sets. That's why I broke them up in stanzas up above. Downgrade all or none for a more trustworthy test.

---

### Post by alexmoon on 2013-02-24
As far as I can tell there don't seem to be older versions of any of these in my archives - the versions here all have the same numbers as the ones installed in the dpkg.log.

---

### Post by alexmoon on 2013-02-24
Okay, I'm looking through the index now...I can't seem to find gnome-video-effects or libwebcam at all, though. Sorry, I feel like there's something silly I'm missing here, but I'm not sure what it is!

---

### Post by madrabbit on 2013-02-24
Sorry, my mistake. It appears libwebcam0 is in pool/universe/libw/libwebcam/libwebcam0_0.2.2-1_i386.deb

In general, you can do an 'apt-cache show <package_name>' | grep Filename to show the pool (universe in this case, not main; sorry), the path (which is the first part of the filename), and the files themselves. For example, 

[http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/](http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/)

---

### Post by alexmoon on 2013-02-24
Okay, because my life is a bit crazy at the moment and accidentally breaking everything would suck, I'm going to ask for a little more help. When it comes to replacing the upgraded version of libwebcam with the older version, what commands would I use? (Sorry, I know I'm being a n00b but I can't afford too much disaster! reinsall! right now)

---

### Post by madrabbit on 2013-02-24
(You are allowed to ask for as much help as you like. This stuff should be easier, and it's the fault of the techie side of the community that we don't have a simple rollback UI, not yours.)

So here's the plan. Find the current version number installed on your system, then we're going to go to the archive and find the URL of the one previous. Then we install it. I'll show the process on my system:

```

ray@phoenix:/tmp$ apt-cache show libwebcam0 | grep Version
Version: 0.2.2-1

```

So the one previous to that is probably 0.2.1-1 (but not for sure). So I go to [http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/]("http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/") click 'last modified' and scroll down to the bottom.

Hmm. That's odd. The us archive hasn't updated those in a long time.

What version of Ubuntu are you on again? Your log says you updated to libwebcam0 0.2.1-1build1, which is old:

2013-02-23 08:10:25 install libwebcam0 <none> 0.2.1-1build1
2013-02-23 08:10:25 status half-installed libwebcam0 0.2.1-1build1
2013-02-23 08:10:25 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:25 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 configure libwebcam0 0.2.1-1build1 <none>
2013-02-23 08:10:29 status unpacked libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 status half-configured libwebcam0 0.2.1-1build1
2013-02-23 08:10:29 status installed libwebcam0 0.2.1-1build1

What is the major version number of your install, 12.10? 12.04?

---

### Post by alexmoon on 2013-02-24
Okay, the result of: apt-cache show libwebcam0 | grep Version
0.2.1-1build1

I'm currently on 12.04. 

I wonder if updating to 12.10 is likely to fix this?

---

### Post by madrabbit on 2013-02-24
(Well, let's assume what your log says isn't crazy, so you're on an older version. I guess that's all I really need to know!)

wget [http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb)
or
wget [http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_amd64.deb)
if you're on 64 bit.

I'm on 32 bit, so:
```

ray@phoenix:/tmp$ wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb
--2013-02-24 18:16:27--  http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.15, 91.189.91.14, 91.189.91.13
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23884 (23K) [application/x-debian-package]
Saving to: `libwebcam0_0.2.0-1_i386.deb'

100%[==========================================================================================================================================>] 23,884      --.-K/s   in 0.1s    

2013-02-24 18:16:28 (161 KB/s) - `libwebcam0_0.2.0-1_i386.deb' saved [23884/23884]

ray@phoenix:/tmp$ sudo dpkg -i libwebcam0_0.2.0-1_i386.deb 
[sudo] password for ray: 
Selecting previously unselected package libwebcam0.
(Reading database ... 184568 files and directories currently installed.)
Unpacking libwebcam0 (from libwebcam0_0.2.0-1_i386.deb) ...
Setting up libwebcam0 (0.2.0-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ray@phoenix:/tmp$ 

```

but after playing around, I decide the old version isn't fixing the problem, so:

```

ray@phoenix:/tmp$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
The following packages will be upgraded:
  libwebcam0
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 26.0 kB of archives.
After this operation, 18.4 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

and then I answer 'y', etc.

---

### Post by alexmoon on 2013-02-24
First I tried this:
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb
```
and then 
```
sudo apt-get upgrade
```

Then restarted: no change, Cheese and GUVCVideo are still showing a black screen. 

Then I thought perhaps I'd missed something, and tried:
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_i386.deb
```

followed by:
```
sudo dpkg -i libwebcam0_0.2.0-1_i386.deb
```

Which got this response:
```
dpkg: error processing libwebcam0_0.2.0-1_i386.deb (--install):
 libwebcam0:i386 0.2.0-1 (Multi-Arch: no) is not co-installable with libwebcam0:amd64 0.2.1-1build1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 libwebcam0_0.2.0-1_i386.deb
```

---

### Post by madrabbit on 2013-02-24
The second one is very close. You apparently are on a 64 bit install, not 32 bit, so do the other wget I listed above, and dpkg -i that other filename.

```

wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_amd64.deb
sudo dpkg -i libwebcam0_0.2.0-1_amd64.deb

```

(You're doing great, by the way. This is the hardest it will ever be. Thanks for taking the time to do all the fussy commands!)

---

### Post by alexmoon on 2013-02-24
How embarrassing. I forgot that I have a 64-bit installation (for the first time). 

I did this:
```
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/libwebcam0_0.2.0-1_amd64.deb

```
then:
```
sudo dpkg -i libwebcam0_0.2.0-1_amd64.deb
```

When I ran sudo apt-get upgrade after that, I got this response:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 uvcdynctrl : Depends: libwebcam0 (= 0.2.1-1build1) but 0.2.0-1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by alexmoon on 2013-02-24
Also now that I've restarted I get this error message:

"An error occurred. Please run Package Manager from the right-click menu or run apt-get in a terminal to see what is wrong. The error was: 'BrokenCount > 0'. This usually means that your installed packages have unmet dependencies"

---

### Post by madrabbit on 2013-02-24
Ah, no worries. I haven't mentioned it to you yet explicitly, but this is all harmless and easy to undo. (via sudo apt-get upgrade, at any time.)

Please also do a
```

wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libw/libwebcam/uvcdynctrl_0.2.0-1_amd64.deb

```
and add that file to your sudo dpkg -i line, as such:
```

sudo dpkg -i libwebcam0_0.2.0-1_amd64.deb uvcdynctrl_0.2.0-1_amd64.deb

```

---

### Post by alexmoon on 2013-02-24
Okay, did that and restarted. No more error messages, but also no signs of life from my webcam.

---

### Post by madrabbit on 2013-02-24
Sigh. So it's that same process but for the rest of the packages at the top of the thread as well. Hence my apology that the techie side of the community hasn't written something to make this much easier.

---

### Post by alexmoon on 2013-02-24
ye squids. Okay, I'm not quite up to that today. I think what I'll do is:
1) Upgrade to 12.10 in the vague hope that it somehow fixes things.
2) Check whether that magically fixed things. 
3) If it has not magically fixed things, possibly I will just get an external webcam that is supported or something. Or learn to live without a webcam. 

Or possibly future-sky will be less daunted by the prospect of this and will manage to get through it for the other packages you suggested.

Thank you for the help! Even if it didn't quite work out I still really appreciate you taking the time to talk me through this.

---

### Post by madrabbit on 2013-02-24
I would suggest postponing the upgrade to 12.10 until after your critical period is over? (Unless not having a webcam is the worst part.) Some programs work a little differently each time, y'know? I'd hate there to be a worse tradeoff in your future (as unlikely as it might be).

You are of course welcome, sorry it wasn't more productive.

---

### Post by alexmoon on 2013-02-24
Yes. This is a problem for future-sky. Present-sky just has to deal with no webcam (and a huge stack of work).

---

### Post by stoneguy on 2013-03-05
As of right now, no image in Skype/Cheese with Raring. Reported via Launchpad #1146829

---

### Post by Mugatu on 2013-03-05
Try this:

[http://askubuntu.com/a/264461/18665](http://askubuntu.com/a/264461/18665)

If it works for you, please contribute to the bug report mentioned in that link, so we can get as much attention from developers as possible to get this resolved soon. Thanks!

---

### Post by ryzaja on 2013-03-09
> **alexmoon said:**
> Hi,

After the latest update, the image from my webcam is displaying as just black (I've tried in Cheese, Skype, and guvcview and got the same result). I've double-checked that I didn't accidentally turn off my webcam, but I haven't. 


I had same problem after kernel upgrade. This solution helped me to fix it:

[http://askubuntu.com/questions/152987/hot-plugging-usb-3-0-drive-not-working-in-ubuntu-12-04/171358#171358](http://askubuntu.com/questions/152987/hot-plugging-usb-3-0-drive-not-working-in-ubuntu-12-04/171358#171358)

---

