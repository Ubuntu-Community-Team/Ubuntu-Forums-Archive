---
title: "Suddenly a video playback problem"
date: 2015-02-28
forum: Multimedia Software
---

### Post by TerryT on 2015-02-28
I hope someone can point me in the right direction. I'm running Kubuntu 14.04 and for months I have had no problems whatsoever with media file playback using [ks]mplayer, vlc, pepper flash, etc.

However, after what seemed to be a minor package update in the last few days, mplayer and pepper flash will no longer properly play video, e.g., flv, mp4. VLC still works fine though.

Mplayer (with -vo xv) will play the video but at what seems about half speed. The pepper flash plugin (firefox) will no longer properly play video either. It will play for a second or two, then pause, then play again, over and over.

Any advice on how to track down this problem would be much appreciated.

Terry

---

### Post by SeijiSensei on 2015-02-28
What version of mplayer?  Is it mplayer2 with version 2.0-701-gd4c5b7f-2ubuntu2 (use "dpkg -s mplayer2" to see)?

What graphic output device were you using before xv?  Something that works with a proprietary video driver like vdpau for NVIDIA or gl (fast) for AMD/ATI adapters?  Perhaps your system isn't using the proprietary drivers after the update?

I'm using Kubuntu 14.04 with smplayer installed (has mplayer2 as a dependency) and haven't seen any of the problems you report on machines with Intel, NVIDIA, and ATI graphics.

---

### Post by TerryT on 2015-02-28
Greetings ... thanks for responding.

Yes, I'm using mplayer 2.0-701-gd4c5b7f-2ubuntu2. When the problem occurred I upgraded to this version, hoping that it would help. No luck with that.

I don't really know if it was using vdpau originally, it just worked out of the box.

I'm running GeForce GTX 750 Ti and using an nvidia binary driver (I tried upgrading to a newer version of the driver, with no luck). According to vdpauinfo, GPU vdpau decoding is available. However, when I try using it with vlc, is tells me "vdpau_avcodec generic error: decoder profile not supported".  When I run mplayer with vdpau, I get "Failed creating VDPAU decoder". But I may not have ever been using vdpau.

Not sure why xv would not be working?

---

### Post by SeijiSensei on 2015-02-28
xv is limited by your CPU speed.  vdpau lets the player offload H.264 decoding to dedicated hardware in the video adapter.

If you installed the NVIDIA proprietary driver from the Ubuntu repositories, it would have installed vdpau as a dependency.  Try "sudo apt-get install libvdpau1" to make sure the libraries were installed.  If so, try running mplayer with "-xv vdpau" and see what happens.  

If you installed the driver from some other source, I strongly recommend removing it and using the one in the repositories.  I usually just use "sudo apt-get install nvidia-current", but you can specify a particular version of the driver like "nvidia-331".  If you have problems with the driver, try removing it and installing the older "nvidia-304" package instead.

---

### Post by Yellow Pasque on 2015-02-28
The logical question is - What packages got updated recently? Look at /var/log/dpkg.log

@SS: nvidia-304 is too old for a GTX750.

---

### Post by TerryT on 2015-02-28
Temujin, you are correct about nvidia-304. This was the reason I had installed from the nvidia website, originally. But I've now installed nvidia-331 (113) from the repo which seems to be working fine, giving glx. It hasn't fixed my problem though.

It is odd, when I run mplayer, it seems that it is reading the media parameters incorrectly. The video looks ok but running at maybe half speed, with the sound messed up accordingly. It doesn't seem to matter what type of media file I open with mplayer, it gives the same result.

Here is my recent /var/log/dpkg.log, I don't know if there are any clues there.

2015-02-26 17:03:18 startup archives unpack
2015-02-26 17:03:19 upgrade libc-bin:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:19 status half-configured libc-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:19 status unpacked libc-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:19 status half-installed libc-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:19 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:19 status half-installed libc-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:19 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:19 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:19 upgrade libc6:i386 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:19 status half-configured libc6:i386 2.19-0ubuntu6.5
2015-02-26 17:03:20 status unpacked libc6:i386 2.19-0ubuntu6.5
2015-02-26 17:03:20 status half-configured libc6:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:20 status half-installed libc6:i386 2.19-0ubuntu6.5
2015-02-26 17:03:20 status half-installed libc6:i386 2.19-0ubuntu6.5
2015-02-26 17:03:20 status unpacked libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:20 status unpacked libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:21 upgrade libc6:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:21 status half-configured libc6:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:21 status unpacked libc6:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:21 status half-installed libc6:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:21 status half-installed libc6:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:22 status unpacked libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:22 status unpacked libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:22 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-02-26 17:03:22 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:22 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:23 startup packages configure
2015-02-26 17:03:23 configure libc6:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:03:23 status unpacked libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:23 status unpacked libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:23 status half-configured libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:25 status installed libc6:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:25 configure libc6:i386 2.19-0ubuntu6.6 <none>
2015-02-26 17:03:25 status unpacked libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:25 status unpacked libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:25 status half-configured libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:26 status installed libc6:i386 2.19-0ubuntu6.6
2015-02-26 17:03:26 configure libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:03:26 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status unpacked libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:26 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:27 startup archives unpack
2015-02-26 17:03:28 upgrade libc6-i386:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:28 status half-configured libc6-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:28 status unpacked libc6-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:28 status half-installed libc6-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:28 status half-installed libc6-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:28 status unpacked libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:28 status unpacked libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:29 upgrade libc-dev-bin:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:29 status half-configured libc-dev-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status unpacked libc-dev-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status half-installed libc-dev-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:29 status half-installed libc-dev-bin:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status unpacked libc-dev-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:29 status unpacked libc-dev-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:29 upgrade libc6-dev:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:29 status half-configured libc6-dev:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status unpacked libc6-dev:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:29 status half-installed libc6-dev:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:30 status half-installed libc6-dev:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:30 status unpacked libc6-dev:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:30 status unpacked libc6-dev:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:30 upgrade libc6-dev-i386:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:30 status half-configured libc6-dev-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:30 status unpacked libc6-dev-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:30 status half-installed libc6-dev-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:30 status half-installed libc6-dev-i386:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:31 status unpacked libc6-dev-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:31 status unpacked libc6-dev-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:31 upgrade libc6-dev-x32:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:31 status half-configured libc6-dev-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:31 status unpacked libc6-dev-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:31 status half-installed libc6-dev-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:31 status half-installed libc6-dev-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:31 status unpacked libc6-dev-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:31 status unpacked libc6-dev-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:32 upgrade libc6-x32:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:32 status half-configured libc6-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status unpacked libc6-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status half-installed libc6-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status half-installed libc6-x32:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status unpacked libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:32 status unpacked libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:32 upgrade libc6-dbg:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:03:32 status half-configured libc6-dbg:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status unpacked libc6-dbg:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:32 status half-installed libc6-dbg:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:33 status half-installed libc6-dbg:amd64 2.19-0ubuntu6.5
2015-02-26 17:03:33 status unpacked libc6-dbg:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:33 status unpacked libc6-dbg:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:33 upgrade linux-libc-dev:amd64 3.13.0-45.74 3.13.0-46.75
2015-02-26 17:03:33 status half-configured linux-libc-dev:amd64 3.13.0-45.74
2015-02-26 17:03:33 status unpacked linux-libc-dev:amd64 3.13.0-45.74
2015-02-26 17:03:33 status half-installed linux-libc-dev:amd64 3.13.0-45.74
2015-02-26 17:03:33 status half-installed linux-libc-dev:amd64 3.13.0-45.74
2015-02-26 17:03:34 status unpacked linux-libc-dev:amd64 3.13.0-46.75
2015-02-26 17:03:34 status unpacked linux-libc-dev:amd64 3.13.0-46.75
2015-02-26 17:03:34 upgrade e2fslibs:amd64 1.42.9-3ubuntu1 1.42.9-3ubuntu1.2
2015-02-26 17:03:34 status half-configured e2fslibs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:34 status unpacked e2fslibs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:34 status half-installed e2fslibs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:34 status half-installed e2fslibs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:34 status unpacked e2fslibs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:34 status unpacked e2fslibs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:34 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-02-26 17:03:34 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:35 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:35 startup packages configure
2015-02-26 17:03:35 configure e2fslibs:amd64 1.42.9-3ubuntu1.2 <none>
2015-02-26 17:03:35 status unpacked e2fslibs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:35 status half-configured e2fslibs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:35 status installed e2fslibs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:35 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:35 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:03:35 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:36 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:36 startup archives unpack
2015-02-26 17:03:37 upgrade e2fsprogs:amd64 1.42.9-3ubuntu1 1.42.9-3ubuntu1.2
2015-02-26 17:03:37 status half-configured e2fsprogs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:37 status unpacked e2fsprogs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:37 status half-installed e2fsprogs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:37 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:37 status half-installed e2fsprogs:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:37 status unpacked e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:37 status unpacked e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:38 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-02-26 17:03:38 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:38 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:39 startup packages configure
2015-02-26 17:03:39 configure e2fsprogs:amd64 1.42.9-3ubuntu1.2 <none>
2015-02-26 17:03:39 status unpacked e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:39 status unpacked e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:39 status half-configured e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:39 status installed e2fsprogs:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:40 startup archives unpack
2015-02-26 17:03:40 upgrade libcomerr2:amd64 1.42.9-3ubuntu1 1.42.9-3ubuntu1.2
2015-02-26 17:03:40 status half-configured libcomerr2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:40 status unpacked libcomerr2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:40 status half-configured libcomerr2:i386 1.42.9-3ubuntu1
2015-02-26 17:03:40 status half-installed libcomerr2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:40 status half-installed libcomerr2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:40 status unpacked libcomerr2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:40 status unpacked libcomerr2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:41 upgrade libcomerr2:i386 1.42.9-3ubuntu1 1.42.9-3ubuntu1.2
2015-02-26 17:03:41 status half-configured libcomerr2:i386 1.42.9-3ubuntu1
2015-02-26 17:03:41 status unpacked libcomerr2:i386 1.42.9-3ubuntu1
2015-02-26 17:03:41 status half-installed libcomerr2:i386 1.42.9-3ubuntu1
2015-02-26 17:03:41 status half-installed libcomerr2:i386 1.42.9-3ubuntu1
2015-02-26 17:03:41 status unpacked libcomerr2:i386 1.42.9-3ubuntu1.2
2015-02-26 17:03:41 status unpacked libcomerr2:i386 1.42.9-3ubuntu1.2
2015-02-26 17:03:41 upgrade libss2:amd64 1.42.9-3ubuntu1 1.42.9-3ubuntu1.2
2015-02-26 17:03:41 status half-configured libss2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:41 status unpacked libss2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:41 status half-installed libss2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:41 status half-installed libss2:amd64 1.42.9-3ubuntu1
2015-02-26 17:03:42 status unpacked libss2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 status unpacked libss2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 startup packages configure
2015-02-26 17:03:42 configure libcomerr2:amd64 1.42.9-3ubuntu1.2 <none>
2015-02-26 17:03:42 status unpacked libcomerr2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 status half-configured libcomerr2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 status installed libcomerr2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:42 configure libcomerr2:i386 1.42.9-3ubuntu1.2 <none>
2015-02-26 17:03:42 status unpacked libcomerr2:i386 1.42.9-3ubuntu1.2
2015-02-26 17:03:42 status half-configured libcomerr2:i386 1.42.9-3ubuntu1.2
2015-02-26 17:03:43 status installed libcomerr2:i386 1.42.9-3ubuntu1.2
2015-02-26 17:03:43 configure libss2:amd64 1.42.9-3ubuntu1.2 <none>
2015-02-26 17:03:43 status unpacked libss2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:43 status half-configured libss2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:43 status installed libss2:amd64 1.42.9-3ubuntu1.2
2015-02-26 17:03:43 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:03:43 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:43 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:03:44 startup archives unpack
2015-02-26 17:03:44 upgrade cups-daemon:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:44 status half-configured cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:44 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:44 status half-installed cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:44 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:03:45 status triggers-pending ufw:all 0.34~rc-0ubuntu2
2015-02-26 17:03:45 status half-installed cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:45 status triggers-pending ureadahead:amd64 0.100.0-16
2015-02-26 17:03:45 status half-installed cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:45 status triggers-pending ureadahead:amd64 0.100.0-16
2015-02-26 17:03:45 status half-installed cups-daemon:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:45 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:45 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:45 upgrade cups-server-common:all 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:45 status half-configured cups-server-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:45 status unpacked cups-server-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:45 status half-installed cups-server-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status half-installed cups-server-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status unpacked cups-server-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:03:46 status unpacked cups-server-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:03:46 upgrade libcupsmime1:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:46 status half-configured libcupsmime1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status unpacked libcupsmime1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status half-installed libcupsmime1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status half-installed libcupsmime1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:46 status unpacked libcupsmime1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:46 status unpacked libcupsmime1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:47 upgrade cups-core-drivers:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:47 status half-configured cups-core-drivers:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status unpacked cups-core-drivers:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status half-installed cups-core-drivers:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status half-installed cups-core-drivers:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status unpacked cups-core-drivers:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:47 status unpacked cups-core-drivers:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:47 upgrade cups:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:47 status half-configured cups:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status unpacked cups:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:47 status half-installed cups:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status half-installed cups:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status unpacked cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 status unpacked cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 upgrade libcupsimage2:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 status half-configured libcupsimage2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status unpacked libcupsimage2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status half-installed libcupsimage2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status half-installed libcupsimage2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status unpacked libcupsimage2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 status unpacked libcupsimage2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 upgrade libcupsppdc1:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:48 status half-configured libcupsppdc1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:48 status unpacked libcupsppdc1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status half-installed libcupsppdc1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status half-installed libcupsppdc1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status unpacked libcupsppdc1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 status unpacked libcupsppdc1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 upgrade libcupscgi1:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 status half-configured libcupscgi1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status unpacked libcupscgi1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status half-installed libcupscgi1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status half-installed libcupscgi1:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:49 status unpacked libcupscgi1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 status unpacked libcupscgi1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 upgrade cups-bsd:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:49 status half-configured cups-bsd:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status unpacked cups-bsd:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status half-installed cups-bsd:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status half-installed cups-bsd:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status unpacked cups-bsd:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:50 status unpacked cups-bsd:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:50 upgrade cups-client:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:50 status half-configured cups-client:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status unpacked cups-client:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status half-installed cups-client:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:50 status half-installed cups-client:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status unpacked cups-client:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:51 status unpacked cups-client:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:51 upgrade libcups2:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:51 status half-configured libcups2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status unpacked libcups2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status half-configured libcups2:i386 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status half-installed libcups2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status half-installed libcups2:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:51 status unpacked libcups2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:51 status unpacked libcups2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 upgrade libcups2:i386 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 status half-configured libcups2:i386 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status unpacked libcups2:i386 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status half-installed libcups2:i386 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status half-installed libcups2:i386 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status unpacked libcups2:i386 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 status unpacked libcups2:i386 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 upgrade cups-common:all 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 status half-configured cups-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status unpacked cups-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status half-installed cups-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status half-installed cups-common:all 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status unpacked cups-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 status unpacked cups-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 upgrade cups-ppdc:amd64 1.7.2-0ubuntu1.2 1.7.2-0ubuntu1.5
2015-02-26 17:03:52 status half-configured cups-ppdc:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status unpacked cups-ppdc:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:52 status half-installed cups-ppdc:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:53 status half-installed cups-ppdc:amd64 1.7.2-0ubuntu1.2
2015-02-26 17:03:53 status unpacked cups-ppdc:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:53 status unpacked cups-ppdc:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:03:53 upgrade language-pack-en:all 1:14.04+20141110 1:14.04+20150219
2015-02-26 17:03:54 status half-configured language-pack-en:all 1:14.04+20141110
2015-02-26 17:03:54 status unpacked language-pack-en:all 1:14.04+20141110
2015-02-26 17:03:54 status half-installed language-pack-en:all 1:14.04+20141110
2015-02-26 17:03:54 status half-installed language-pack-en:all 1:14.04+20141110
2015-02-26 17:03:54 status unpacked language-pack-en:all 1:14.04+20150219
2015-02-26 17:03:54 status unpacked language-pack-en:all 1:14.04+20150219
2015-02-26 17:03:54 upgrade language-pack-en-base:all 1:14.04+20140707 1:14.04+20150219
2015-02-26 17:03:54 status half-configured language-pack-en-base:all 1:14.04+20140707
2015-02-26 17:03:55 status unpacked language-pack-en-base:all 1:14.04+20140707
2015-02-26 17:03:55 status half-installed language-pack-en-base:all 1:14.04+20140707
2015-02-26 17:03:55 status half-installed language-pack-en-base:all 1:14.04+20140707
2015-02-26 17:03:55 status unpacked language-pack-en-base:all 1:14.04+20150219
2015-02-26 17:03:55 status unpacked language-pack-en-base:all 1:14.04+20150219
2015-02-26 17:03:55 upgrade language-pack-gnome-en:all 1:14.04+20141110 1:14.04+20150219
2015-02-26 17:03:55 status half-configured language-pack-gnome-en:all 1:14.04+20141110
2015-02-26 17:03:55 status unpacked language-pack-gnome-en:all 1:14.04+20141110
2015-02-26 17:03:55 status half-installed language-pack-gnome-en:all 1:14.04+20141110
2015-02-26 17:03:55 status half-installed language-pack-gnome-en:all 1:14.04+20141110
2015-02-26 17:03:56 status unpacked language-pack-gnome-en:all 1:14.04+20150219
2015-02-26 17:03:56 status unpacked language-pack-gnome-en:all 1:14.04+20150219
2015-02-26 17:03:56 upgrade language-pack-gnome-en-base:all 1:14.04+20140707 1:14.04+20150219
2015-02-26 17:03:56 status half-configured language-pack-gnome-en-base:all 1:14.04+20140707
2015-02-26 17:03:56 status unpacked language-pack-gnome-en-base:all 1:14.04+20140707
2015-02-26 17:03:56 status half-installed language-pack-gnome-en-base:all 1:14.04+20140707
2015-02-26 17:03:57 status half-installed language-pack-gnome-en-base:all 1:14.04+20140707
2015-02-26 17:03:57 status unpacked language-pack-gnome-en-base:all 1:14.04+20150219
2015-02-26 17:03:57 status unpacked language-pack-gnome-en-base:all 1:14.04+20150219
2015-02-26 17:03:57 upgrade libfreetype6:i386 2.5.2-1ubuntu2.3 2.5.2-1ubuntu2.4
2015-02-26 17:03:57 status half-configured libfreetype6:i386 2.5.2-1ubuntu2.3
2015-02-26 17:03:57 status unpacked libfreetype6:i386 2.5.2-1ubuntu2.3
2015-02-26 17:03:57 status half-configured libfreetype6:amd64 2.5.2-1ubuntu2.3
2015-02-26 17:03:57 status half-installed libfreetype6:i386 2.5.2-1ubuntu2.3
2015-02-26 17:03:57 status half-installed libfreetype6:i386 2.5.2-1ubuntu2.3
2015-02-26 17:03:57 status unpacked libfreetype6:i386 2.5.2-1ubuntu2.4
2015-02-26 17:03:57 status unpacked libfreetype6:i386 2.5.2-1ubuntu2.4
2015-02-26 17:03:58 upgrade libfreetype6:amd64 2.5.2-1ubuntu2.3 2.5.2-1ubuntu2.4
2015-02-26 17:03:58 status half-configured libfreetype6:amd64 2.5.2-1ubuntu2.3
2015-02-26 17:03:58 status unpacked libfreetype6:amd64 2.5.2-1ubuntu2.3
2015-02-26 17:03:58 status half-installed libfreetype6:amd64 2.5.2-1ubuntu2.3
2015-02-26 17:03:58 status half-installed libfreetype6:amd64 2.5.2-1ubuntu2.3
2015-02-26 17:03:58 status unpacked libfreetype6:amd64 2.5.2-1ubuntu2.4
2015-02-26 17:03:58 status unpacked libfreetype6:amd64 2.5.2-1ubuntu2.4
2015-02-26 17:03:58 upgrade libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:03:58 status half-configured libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:03:58 status unpacked libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:03:58 status half-installed libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:03:58 status half-installed libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:03:58 status unpacked libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:03:58 status unpacked libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:03:59 install linux-image-3.13.0-46-generic:amd64 <none> 3.13.0-46.75
2015-02-26 17:03:59 status half-installed linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:00 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:00 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:00 upgrade libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:00 status half-configured libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:00 status unpacked libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:00 status half-installed libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status half-installed libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status unpacked libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:01 status unpacked libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:01 upgrade smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:01 status half-configured smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status unpacked smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status half-installed smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status half-installed smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:01 status unpacked smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:01 status unpacked smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:02 upgrade samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:02 status half-configured samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status unpacked samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status half-installed samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status half-installed samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status unpacked samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:02 status unpacked samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:02 upgrade python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:02 status half-configured python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status unpacked python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:02 status half-installed python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:03 status half-installed python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:03 status unpacked python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:03 status unpacked python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:03 upgrade samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:03 status half-configured samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:03 status unpacked samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:03 status half-installed samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:03 status half-installed samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:04 status unpacked samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:04 status unpacked samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:04 upgrade samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.5 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:04 status half-configured samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:04 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:04 status half-installed samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:04 status half-installed samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.5
2015-02-26 17:04:04 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:04 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:04 upgrade multiarch-support:amd64 2.19-0ubuntu6.5 2.19-0ubuntu6.6
2015-02-26 17:04:04 status half-configured multiarch-support:amd64 2.19-0ubuntu6.5
2015-02-26 17:04:04 status unpacked multiarch-support:amd64 2.19-0ubuntu6.5
2015-02-26 17:04:04 status half-installed multiarch-support:amd64 2.19-0ubuntu6.5
2015-02-26 17:04:05 status half-installed multiarch-support:amd64 2.19-0ubuntu6.5
2015-02-26 17:04:05 status unpacked multiarch-support:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:05 status unpacked multiarch-support:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:05 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-02-26 17:04:05 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:04:06 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:04:06 trigproc ufw:all 0.34~rc-0ubuntu2 0.34~rc-0ubuntu2
2015-02-26 17:04:06 status half-configured ufw:all 0.34~rc-0ubuntu2
2015-02-26 17:04:06 status installed ufw:all 0.34~rc-0ubuntu2
2015-02-26 17:04:06 trigproc ureadahead:amd64 0.100.0-16 0.100.0-16
2015-02-26 17:04:06 status half-configured ureadahead:amd64 0.100.0-16
2015-02-26 17:04:06 status installed ureadahead:amd64 0.100.0-16
2015-02-26 17:04:07 startup packages configure
2015-02-26 17:04:07 configure multiarch-support:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:07 status unpacked multiarch-support:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:07 status half-configured multiarch-support:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:07 status installed multiarch-support:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:08 startup archives unpack
2015-02-26 17:04:08 upgrade ca-certificates:all 20130906ubuntu2 20141019ubuntu0.14.04.1
2015-02-26 17:04:08 status half-configured ca-certificates:all 20130906ubuntu2
2015-02-26 17:04:08 status unpacked ca-certificates:all 20130906ubuntu2
2015-02-26 17:04:08 status half-installed ca-certificates:all 20130906ubuntu2
2015-02-26 17:04:08 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:04:08 status half-installed ca-certificates:all 20130906ubuntu2
2015-02-26 17:04:09 status unpacked ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:04:09 status unpacked ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:04:09 upgrade firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:09 status half-configured firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:09 status unpacked firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:09 status half-installed firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:11 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-02-26 17:04:12 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-02-26 17:04:12 status half-installed firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status half-installed firefox:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:12 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:12 upgrade firefox-locale-en:amd64 35.0.1+build1-0ubuntu0.14.04.1 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:12 status half-configured firefox-locale-en:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status unpacked firefox-locale-en:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status half-installed firefox-locale-en:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status half-installed firefox-locale-en:amd64 35.0.1+build1-0ubuntu0.14.04.1
2015-02-26 17:04:12 status unpacked firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:12 status unpacked firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:04:13 install linux-image-extra-3.13.0-46-generic:amd64 <none> 3.13.0-46.75
2015-02-26 17:04:13 status half-installed linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:16 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:16 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:17 upgrade linux-generic:amd64 3.13.0.45.52 3.13.0.46.53
2015-02-26 17:04:17 status half-configured linux-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status unpacked linux-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status half-installed linux-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status half-installed linux-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status unpacked linux-generic:amd64 3.13.0.46.53
2015-02-26 17:04:17 status unpacked linux-generic:amd64 3.13.0.46.53
2015-02-26 17:04:17 upgrade linux-image-generic:amd64 3.13.0.45.52 3.13.0.46.53
2015-02-26 17:04:17 status half-configured linux-image-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status unpacked linux-image-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status half-installed linux-image-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status half-installed linux-image-generic:amd64 3.13.0.45.52
2015-02-26 17:04:17 status unpacked linux-image-generic:amd64 3.13.0.46.53
2015-02-26 17:04:17 status unpacked linux-image-generic:amd64 3.13.0.46.53
2015-02-26 17:04:18 install linux-headers-3.13.0-46:all <none> 3.13.0-46.75
2015-02-26 17:04:18 status half-installed linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:04:21 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:04:21 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:04:22 install linux-headers-3.13.0-46-generic:amd64 <none> 3.13.0-46.75
2015-02-26 17:04:22 status half-installed linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:23 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:23 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:23 upgrade linux-headers-generic:amd64 3.13.0.45.52 3.13.0.46.53
2015-02-26 17:04:23 status half-configured linux-headers-generic:amd64 3.13.0.45.52
2015-02-26 17:04:23 status unpacked linux-headers-generic:amd64 3.13.0.45.52
2015-02-26 17:04:23 status half-installed linux-headers-generic:amd64 3.13.0.45.52
2015-02-26 17:04:23 status half-installed linux-headers-generic:amd64 3.13.0.45.52
2015-02-26 17:04:23 status unpacked linux-headers-generic:amd64 3.13.0.46.53
2015-02-26 17:04:23 status unpacked linux-headers-generic:amd64 3.13.0.46.53
2015-02-26 17:04:23 upgrade unattended-upgrades:all 0.82.1ubuntu2 0.82.1ubuntu2.1
2015-02-26 17:04:23 status half-configured unattended-upgrades:all 0.82.1ubuntu2
2015-02-26 17:04:23 status unpacked unattended-upgrades:all 0.82.1ubuntu2
2015-02-26 17:04:23 status half-installed unattended-upgrades:all 0.82.1ubuntu2
2015-02-26 17:04:23 status triggers-pending ureadahead:amd64 0.100.0-16
2015-02-26 17:04:24 status half-installed unattended-upgrades:all 0.82.1ubuntu2
2015-02-26 17:04:25 status half-installed unattended-upgrades:all 0.82.1ubuntu2
2015-02-26 17:04:25 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:04:25 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:04:26 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-02-26 17:04:26 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:04:26 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-02-26 17:04:26 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-02-26 17:04:26 status half-configured mime-support:all 3.54ubuntu1.1
2015-02-26 17:04:26 status installed mime-support:all 3.54ubuntu1.1
2015-02-26 17:04:26 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-02-26 17:04:26 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-02-26 17:04:26 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-02-26 17:04:26 trigproc ureadahead:amd64 0.100.0-16 0.100.0-16
2015-02-26 17:04:26 status half-configured ureadahead:amd64 0.100.0-16
2015-02-26 17:04:26 status installed ureadahead:amd64 0.100.0-16
2015-02-26 17:04:27 startup packages configure
2015-02-26 17:04:27 configure libc6-i386:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:27 status unpacked libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status unpacked libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status half-configured libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status installed libc6-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 configure libc-dev-bin:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:27 status unpacked libc-dev-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status half-configured libc-dev-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status installed libc-dev-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 configure linux-libc-dev:amd64 3.13.0-46.75 <none>
2015-02-26 17:04:27 status unpacked linux-libc-dev:amd64 3.13.0-46.75
2015-02-26 17:04:27 status half-configured linux-libc-dev:amd64 3.13.0-46.75
2015-02-26 17:04:27 status installed linux-libc-dev:amd64 3.13.0-46.75
2015-02-26 17:04:27 configure libc6-dev:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:27 status unpacked libc6-dev:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status half-configured libc6-dev:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status installed libc6-dev:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 configure libc6-dev-i386:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:27 status unpacked libc6-dev-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status half-configured libc6-dev-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:27 status installed libc6-dev-i386:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 configure libc6-x32:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:28 status unpacked libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status unpacked libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status half-configured libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status installed libc6-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 configure libc6-dev-x32:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:28 status unpacked libc6-dev-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status half-configured libc6-dev-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status installed libc6-dev-x32:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 configure libc6-dbg:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:04:28 status unpacked libc6-dbg:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status half-configured libc6-dbg:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 status installed libc6-dbg:amd64 2.19-0ubuntu6.6
2015-02-26 17:04:28 configure libcups2:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:28 status unpacked libcups2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status half-configured libcups2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status installed libcups2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 configure libcups2:i386 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:28 status unpacked libcups2:i386 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status half-configured libcups2:i386 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status installed libcups2:i386 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 configure libcupsmime1:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:28 status unpacked libcupsmime1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status half-configured libcupsmime1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status installed libcupsmime1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 configure cups-daemon:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:28 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:28 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:29 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:29 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:29 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:29 status unpacked cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:29 status half-configured cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed cups-daemon:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure cups-server-common:all 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked cups-server-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured cups-server-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed cups-server-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure cups-core-drivers:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked cups-core-drivers:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured cups-core-drivers:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed cups-core-drivers:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure libcupscgi1:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked libcupscgi1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured libcupscgi1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed libcupscgi1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure libcupsimage2:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked libcupsimage2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured libcupsimage2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed libcupsimage2:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure libcupsppdc1:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked libcupsppdc1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured libcupsppdc1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed libcupsppdc1:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure cups-common:all 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked cups-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured cups-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed cups-common:all 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure cups-client:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked cups-client:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status half-configured cups-client:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 status installed cups-client:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:30 configure cups-ppdc:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:30 status unpacked cups-ppdc:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:31 status half-configured cups-ppdc:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:31 status installed cups-ppdc:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:31 configure cups:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:31 status unpacked cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:31 status unpacked cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:31 status half-configured cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:32 status installed cups:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:32 configure cups-bsd:amd64 1.7.2-0ubuntu1.5 <none>
2015-02-26 17:04:32 status unpacked cups-bsd:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:32 status half-configured cups-bsd:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:32 status installed cups-bsd:amd64 1.7.2-0ubuntu1.5
2015-02-26 17:04:32 configure libfreetype6:amd64 2.5.2-1ubuntu2.4 <none>
2015-02-26 17:04:32 status unpacked libfreetype6:amd64 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 status half-configured libfreetype6:amd64 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 status installed libfreetype6:amd64 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 configure libfreetype6:i386 2.5.2-1ubuntu2.4 <none>
2015-02-26 17:04:32 status unpacked libfreetype6:i386 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 status half-configured libfreetype6:i386 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 status installed libfreetype6:i386 2.5.2-1ubuntu2.4
2015-02-26 17:04:32 configure libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:04:32 status unpacked libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:32 status half-configured libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:32 status installed libwbclient0:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:04:32 configure linux-image-3.13.0-46-generic:amd64 3.13.0-46.75 <none>
2015-02-26 17:04:32 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:04:33 status half-configured linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:08 status installed linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:08 configure samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:08 status unpacked samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:08 status half-configured samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status installed samba-libs:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 configure libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:09 status unpacked libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status half-configured libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status installed libsmbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 configure samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:09 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status unpacked samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status half-configured samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status installed samba-common:all 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 configure smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:09 status unpacked smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status half-configured smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status installed smbclient:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 configure python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:09 status unpacked python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:09 status half-configured python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:10 status installed python-samba:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:10 configure samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7 <none>
2015-02-26 17:05:10 status unpacked samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:10 status half-configured samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:10 status installed samba-common-bin:amd64 2:4.1.6+dfsg-1ubuntu2.14.04.7
2015-02-26 17:05:10 configure ca-certificates:all 20141019ubuntu0.14.04.1 <none>
2015-02-26 17:05:10 status unpacked ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:05:10 status half-configured ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:05:11 status installed ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:05:11 status triggers-pending ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:05:11 configure firefox:amd64 36.0+build2-0ubuntu0.14.04.4 <none>
2015-02-26 17:05:11 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status unpacked firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status half-configured firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status installed firefox:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 configure firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4 <none>
2015-02-26 17:05:11 status unpacked firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status half-configured firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 status installed firefox-locale-en:amd64 36.0+build2-0ubuntu0.14.04.4
2015-02-26 17:05:11 configure linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75 <none>
2015-02-26 17:05:11 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:11 status half-configured linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:18 status installed linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:18 configure linux-image-generic:amd64 3.13.0.46.53 <none>
2015-02-26 17:05:18 status unpacked linux-image-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status half-configured linux-image-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status installed linux-image-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 configure linux-headers-3.13.0-46:all 3.13.0-46.75 <none>
2015-02-26 17:05:18 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:05:18 status half-configured linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:05:18 status installed linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-26 17:05:18 configure linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75 <none>
2015-02-26 17:05:18 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:18 status half-configured linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:18 status installed linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-26 17:05:18 configure linux-headers-generic:amd64 3.13.0.46.53 <none>
2015-02-26 17:05:18 status unpacked linux-headers-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status half-configured linux-headers-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status installed linux-headers-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 configure linux-generic:amd64 3.13.0.46.53 <none>
2015-02-26 17:05:18 status unpacked linux-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status half-configured linux-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 status installed linux-generic:amd64 3.13.0.46.53
2015-02-26 17:05:18 configure unattended-upgrades:all 0.82.1ubuntu2.1 <none>
2015-02-26 17:05:18 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:18 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:18 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:18 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:19 status unpacked unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:19 status half-configured unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:19 status installed unattended-upgrades:all 0.82.1ubuntu2.1
2015-02-26 17:05:19 configure language-pack-en:all 1:14.04+20150219 <none>
2015-02-26 17:05:19 status unpacked language-pack-en:all 1:14.04+20150219
2015-02-26 17:05:19 status half-configured language-pack-en:all 1:14.04+20150219
2015-02-26 17:05:19 status installed language-pack-en:all 1:14.04+20150219
2015-02-26 17:05:19 configure language-pack-en-base:all 1:14.04+20150219 <none>
2015-02-26 17:05:19 status unpacked language-pack-en-base:all 1:14.04+20150219
2015-02-26 17:05:19 status half-configured language-pack-en-base:all 1:14.04+20150219
2015-02-26 17:05:20 status installed language-pack-en-base:all 1:14.04+20150219
2015-02-26 17:05:20 configure language-pack-gnome-en:all 1:14.04+20150219 <none>
2015-02-26 17:05:20 status unpacked language-pack-gnome-en:all 1:14.04+20150219
2015-02-26 17:05:20 status half-configured language-pack-gnome-en:all 1:14.04+20150219
2015-02-26 17:05:20 status installed language-pack-gnome-en:all 1:14.04+20150219
2015-02-26 17:05:20 configure language-pack-gnome-en-base:all 1:14.04+20150219 <none>
2015-02-26 17:05:20 status unpacked language-pack-gnome-en-base:all 1:14.04+20150219
2015-02-26 17:05:20 status half-configured language-pack-gnome-en-base:all 1:14.04+20150219
2015-02-26 17:05:20 status installed language-pack-gnome-en-base:all 1:14.04+20150219
2015-02-26 17:05:20 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-02-26 17:05:20 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:05:20 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-02-26 17:05:20 trigproc ca-certificates:all 20141019ubuntu0.14.04.1 <none>
2015-02-26 17:05:20 status half-configured ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-26 17:05:22 status installed ca-certificates:all 20141019ubuntu0.14.04.1
2015-02-27 08:35:07 startup archives unpack
2015-02-27 08:35:07 upgrade linux-image-3.13.0-46-generic:amd64 3.13.0-46.75 3.13.0-46.76
2015-02-27 08:35:07 status half-configured linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:07 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:07 status half-installed linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:09 status half-installed linux-image-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:09 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:09 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:09 upgrade linux-headers-3.13.0-46:all 3.13.0-46.75 3.13.0-46.76
2015-02-27 08:35:09 status half-configured linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-27 08:35:09 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-27 08:35:09 status half-installed linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-27 08:35:13 status half-installed linux-headers-3.13.0-46:all 3.13.0-46.75
2015-02-27 08:35:13 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.76
2015-02-27 08:35:13 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.76
2015-02-27 08:35:13 upgrade linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75 3.13.0-46.76
2015-02-27 08:35:13 status half-configured linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:13 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:13 status half-installed linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:15 status half-installed linux-headers-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:15 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:15 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:16 upgrade linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75 3.13.0-46.76
2015-02-27 08:35:16 status half-configured linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:16 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:16 status half-installed linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:20 status half-installed linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.75
2015-02-27 08:35:20 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:20 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:21 upgrade linux-libc-dev:amd64 3.13.0-46.75 3.13.0-46.76
2015-02-27 08:35:21 status half-configured linux-libc-dev:amd64 3.13.0-46.75
2015-02-27 08:35:21 status unpacked linux-libc-dev:amd64 3.13.0-46.75
2015-02-27 08:35:21 status half-installed linux-libc-dev:amd64 3.13.0-46.75
2015-02-27 08:35:21 status half-installed linux-libc-dev:amd64 3.13.0-46.75
2015-02-27 08:35:21 status unpacked linux-libc-dev:amd64 3.13.0-46.76
2015-02-27 08:35:21 status unpacked linux-libc-dev:amd64 3.13.0-46.76
2015-02-27 08:35:22 startup packages configure
2015-02-27 08:35:22 configure linux-image-3.13.0-46-generic:amd64 3.13.0-46.76 <none>
2015-02-27 08:35:22 status unpacked linux-image-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:22 status half-configured linux-image-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 status installed linux-image-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 configure linux-headers-3.13.0-46:all 3.13.0-46.76 <none>
2015-02-27 08:35:32 status unpacked linux-headers-3.13.0-46:all 3.13.0-46.76
2015-02-27 08:35:32 status half-configured linux-headers-3.13.0-46:all 3.13.0-46.76
2015-02-27 08:35:32 status installed linux-headers-3.13.0-46:all 3.13.0-46.76
2015-02-27 08:35:32 configure linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76 <none>
2015-02-27 08:35:32 status unpacked linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 status half-configured linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 status installed linux-headers-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 configure linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76 <none>
2015-02-27 08:35:32 status unpacked linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:32 status half-configured linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:42 status installed linux-image-extra-3.13.0-46-generic:amd64 3.13.0-46.76
2015-02-27 08:35:42 configure linux-libc-dev:amd64 3.13.0-46.76 <none>
2015-02-27 08:35:42 status unpacked linux-libc-dev:amd64 3.13.0-46.76
2015-02-27 08:35:42 status half-configured linux-libc-dev:amd64 3.13.0-46.76
2015-02-27 08:35:42 status installed linux-libc-dev:amd64 3.13.0-46.76
2015-02-27 14:32:45 startup archives unpack
2015-02-27 14:32:49 upgrade pepperflashplugin-nonfree:amd64 1.3ubuntu1 1.3ubuntu1
2015-02-27 14:32:49 status half-configured pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:50 status unpacked pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:50 status half-installed pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:50 status half-installed pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:50 status unpacked pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:50 status unpacked pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:51 startup packages configure
2015-02-27 14:32:51 configure pepperflashplugin-nonfree:amd64 1.3ubuntu1 <none>
2015-02-27 14:32:51 status unpacked pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:32:51 status half-configured pepperflashplugin-nonfree:amd64 1.3ubuntu1
2015-02-27 14:33:03 status installed pepperflashplugin-nonfree:amd64 1.3ubuntu1

---

### Post by Yellow Pasque on 2015-02-28
In the future, PLEASE use code tags for large blocks of text.

I don't see anything real suspicious in the updates (it mostly looks like security updates).

If it was me, I'd update to the latest video driver, 346.47 (using a good PPA and NOT Nvidia's website): [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Nvidia doesn't even list the GTX 750 as officially supported by the 331 series driver.

The next thing I'd try is creating another user or using the guest account to see if they have the issue too.

---

### Post by TerryT on 2015-02-28
Thank-you very much for this suggestion. This problem doesn't occur when logged in as another user! Do you have any advice on how to find out where in the user configuration, the problem is occurring?

---

### Post by TerryT on 2015-02-28
I finally found the problem. Long ago I had set an environment variable PULSE_LATENCY_MSEC=30 in .bashrc to fix a problem with skype. Removing this fixed everything.

---

