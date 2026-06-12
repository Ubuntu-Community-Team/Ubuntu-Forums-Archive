---
title: "Xvidcap Disappears?"
date: 2009-04-20
forum: Multimedia Software
---

### Post by gaalaaant on 2009-04-20
Whenever I try to record in xvidcap it disappears? Now I understand that's what it SHOULD DO, but how do I get it to come back and let me stop recording >= ?

---

### Post by rajeeja on 2009-04-28
Just installed Jaunty...there is no sound codec for XVIDCAP....


Xvidcap complains about not having audio support build in:

xvidcap --fps 15 --quality 100 --gui yes --format avi --audio yes
[B][SIZE="6"]
Audio support not present in this binary.[/SIZE][/B]



Reproducible: Always

Steps to Reproduce:
1. emerge xvidcap
2. start xvidcap with --audio yes

Actual Results:  
Audio support not present in this binary.

Expected Results:  
Audio support should be build in

emerge --info

Portage 2.1.6.7 (default/linux/amd64/2008.0/desktop, gcc-4.3.3,
glibc-2.8_p20080602-r1, 2.6.27.6 x86_64)
=================================================================
System uname:
Linux-2.6.27.6-x86_64-AMD_Athlon-tm-_64_X2_Dual_Core_Processor_4200+-with-glibc2.2.5
Timestamp of tree: Fri, 06 Feb 2009 19:45:02 +0000
ccache version 2.4 [disabled]
app-shells/bash:     3.2_p48
dev-java/java-config: 1.3.7-r1, 2.1.7
dev-lang/python:     2.5.4-r2
dev-util/ccache:     2.4-r8
dev-util/cmake:      2.6.2-r1
sys-apps/baselayout: 2.0.0
sys-apps/openrc:     0.4.2
sys-apps/sandbox:    1.3.2
sys-devel/autoconf:  2.13, 2.63
sys-devel/automake:  1.5, 1.7.9-r1, 1.8.5-r3, 1.9.6-r2, 1.10.2
sys-devel/binutils:  2.19.1
sys-devel/gcc-config: 1.4.1
sys-devel/libtool:   2.2.6a
virtual/os-headers:  2.6.28-r1
ACCEPT_KEYWORDS="amd64 ~amd64"
CBUILD="x86_64-pc-linux-gnu"
CFLAGS="-O2 -march=athlon64 -fomit-frame-pointer -pipe"
CHOST="x86_64-pc-linux-gnu"
CONFIG_PROTECT="/etc /usr/kde/3.5/env /usr/kde/3.5/share/config
/usr/kde/3.5/shutdown /usr/share/config"
CONFIG_PROTECT_MASK="/etc/ca-certificates.conf /etc/env.d /etc/env.d/java/
/etc/fonts/fonts.conf /etc/gconf /etc/gentoo-release
/etc/php/apache2-php5/ext-active/ /etc/php/cgi-php5/ext-active/
/etc/php/cli-php5/ext-active/ /etc/revdep-rebuild /etc/sandbox.d /etc/terminfo
/etc/texmf/language.dat.d /etc/texmf/language.def.d /etc/texmf/updmap.d
/etc/texmf/web2c /etc/udev/rules.d"
CXXFLAGS="-O2 -march=athlon64 -fomit-frame-pointer -pipe"
DISTDIR="/usr/portage/distfiles"
FEATURES="distlocks fixpackages parallel-fetch protect-owned sandbox sfperms
strict unmerge-orphans userfetch"
GENTOO_MIRRORS="ftp:///ftp-stud.fht-esslingen.de/pub/Mirrors/gentoo/
[ftp://ftp.uni-erlangen.de/pub/mirrors/gentoo](ftp://ftp.uni-erlangen.de/pub/mirrors/gentoo)
[http://ftp-stud.fht-esslingen.de/pub/Mirrors/gentoo/](http://ftp-stud.fht-esslingen.de/pub/Mirrors/gentoo/)
[ftp://distro.ibiblio.org/pub/Linux/distributions/gentoo/](ftp://distro.ibiblio.org/pub/Linux/distributions/gentoo/)
ftp://ftp2.tnc.edu.tw/pub1/Gentoo/"
LANG="en_US.utf8"
LC_ALL="en_US.utf8"
LDFLAGS="-Wl,-O1"
LINGUAS="de en"
MAKEOPTS="-j6"
PKGDIR="/usr/portage/packages"
PORTAGE_RSYNC_OPTS="--recursive --links --safe-links --perms --times --compress
--force --whole-file --delete --stats --timeout=180 --exclude=/distfiles
--exclude=/local --exclude=/packages"
PORTAGE_TMPDIR="/var/tmp"
PORTDIR="/usr/portage"
PORTDIR_OVERLAY="/usr/local/portage/layman/science /usr/local/overlays/local"
SYNC="rsync://rsync.europe.gentoo.org/gentoo-portage"
USE="3dnow X acl acpi aim alsa amd64 apache2 apm audiofile avi bash-completion
bcmath berkdb bidi bindist bluetooth branding bzip2 bzlib calendar caps cdr cli
cracklib crypt cups dbus divx4linux dri dts dvd dvdr dvdread emboss emerald
encode ethereal evo exif fastcgi fbcon firefox foomaticdb fortran ftp gdbm gif
gnutls gphoto2 gpm gps gstreamer gtk2 hal iconv icq imagemagick imap imlib
innodb ipv6 isdnlog jabber java jpeg kde libg++ libnotify lirc mad maildir mcal
midi mikmod mmx mmx2 mp3 mpeg msn mudflap multilib ncurses network nls nptl
nptlonly nvidia ogg oggvorbis opengl openmp oss pam pcre pda pdf pdflib perl
png pnp ppds pppd prelude python qt qt3 qt3support qt4 quicktime readline
reflection samba sapdb sasl scanner sdl session sockets spell spl sse sse2 ssl
startup-notification svg sysfs tcpd tiff truetype unicode usb v4l v4l2 vorbis
xinerama xml xml2 xorg xsl xulrunner xv xvid zlib" ALSA_CARDS="ali5451 als4000
atiixp atiixp-modem bt87x ca0106 cmipci emu10k1x ens1370 ens1371 es1938 es1968
fm801 hda-intel intel8x0 intel8x0m maestro3 trident usb-audio via82xx
via82xx-modem ymfpci" ALSA_PCM_PLUGINS="adpcm alaw asym copy dmix dshare dsnoop
empty extplug file hooks iec958 ioplug ladspa lfloat linear meter mmap_emul
mulaw multi null plug rate route share shm softvol" APACHE2_MODULES="actions
alias auth_basic auth_digest authn_anon authn_dbd authn_dbm authn_default
authn_file authz_dbm authz_default authz_groupfile authz_host authz_owner
authz_user autoindex cache dav dav_fs dav_lock dbd deflate dir disk_cache env
expires ext_filter file_cache filter headers ident imagemap include info
log_config logio mem_cache mime mime_magic negotiation proxy proxy_ajp
proxy_balancer proxy_connect proxy_http rewrite setenvif so speling status
unique_id userdir usertrack vhost_alias" ELIBC="glibc" INPUT_DEVICES="mouse
keyboard joystick evdev" KERNEL="linux" LCD_DEVICES="bayrad cfontz cfontz633
glk hd44780 lb216 lcdm001 mtxorb ncurses text" LINGUAS="de en" USERLAND="GNU"
VIDEO_CARDS="nvidia nv v4l vesa vga"
Unset:  CPPFLAGS, CTARGET, EMERGE_DEFAULT_OPTS, FFLAGS, INSTALL_MASK,
PORTAGE_COMPRESS, PORTAGE_COMPRESS_FLAGS, PORTAGE_RSYNC_EXTRA_OPTS

---

### Post by ana.sord on 2009-05-02
my XvidCap also disappeared when I pressed "record". I started the program from the terminal and got this error:
xtoffmpeg.c add_video_stream(): video codec not found

I found a solution in a french ubuntu forum, Ii was to install: libavcodec-unstripped-52
(I did it with synaptics and it uninstalled another library)

Now I'm able to use Xvidcap and make screen recordings... (I have some rendering problems, but that's another story)

---

### Post by Braedon on 2009-05-11
Yes, but my audio STILL doesn't work! So frustrating!

---

### Post by gnowak on 2009-06-05
Hey, I have the exact same problem. Do you think compiling from scratch could help?

Does anyone have xvidcap working with sound?

---

### Post by worksofcraft on 2009-06-07
I installed the latest XVidCap from teh software channel using Synapitic Package Manager and had same problem.

The version I had before works fine and you can get it from [http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=613295](http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=613295)

take the one named xvidcap_1.1.7intrepid_i386.deb

Good Luck ):P

---

### Post by gnowak on 2009-06-07
Thanks.

That's no option if you are running 64bit though..

I use Jaunty 64 bit.

---

### Post by worksofcraft on 2009-06-07
oh soz...I didn't know. I thought 64 bit processors could run 32 bit apps... Omg this is messy :redface:

---

### Post by gnowak on 2009-06-07
64 bit processors can run 32 bit apps, but 64 bit can't or.. they can with some tweaking but that's another story...

---

### Post by gnowak on 2009-06-07
Hey. I tried the xvidcap_1.1.7intrepid_i386.deb on Jaunty 32 bit, it works very well!

The only problem is, how can we get xvidcap in 62 bit?... with sound/audio.

---

### Post by worksofcraft on 2009-06-10
> **gnowak said:**
> Hey. I tried the xvidcap_1.1.7intrepid_i386.deb on Jaunty 32 bit, it works very well!

The only problem is, how can we get xvidcap in 62 bit?... with sound/audio.

I was hoping someone would give you an answer. I too have an AMD quad core 64 bit processor, but I eventually gave up on 64 bit... just too many problems and all the 64 bit addresses cause huge code bloat and reduced performance and basically on my single user computer with 4 GB ram I just don't see a need for any programs that can't make do with 32 bits. However that's not really on topic for this thread I suppose.

So what is.... well besides XVidCap there is a video editing system called LiVES that provides capture from another Window... might be worth trying ?

---

### Post by gnowak on 2009-06-10
Hey, I haven't tried LiVES but I have tried Kdenlive but it does not work very well.. clipping sound etc.

---

### Post by worksofcraft on 2009-06-12
It sounds like we have similar objectives. I'm trying to capture on screen activity and turn it into tutorial videos using free software tools on Linux. It's taken me a while just to get sound recorder going... well actually I gave up on Ubuntu 8.04 (Hardy Heron) and started again with 9.04 (Jaunty Jackalope). Have been running into one problem after another but determined to get there eventually.

Would anyone be interested in my progress reports on this thread... or elsewhere? I can tell you all about my discoveries with Cinelerra, LiVES and Kino... might have a go at Kdenlive and PiTiVi and finally document how I think it best is done and we can perhaps share ideas when we get stuck ;)

---

### Post by worksofcraft on 2009-06-13
Oh well here goes anyway:

Kino was easy to install with...
sudo apt-get install kino

Had no problem importing my mpeg files but could not find any menu option for adding or modifying the sound tracks.

Conclusion: Kino does not appear to be an appropriate tool for adding narration to video I captured with XVidCap :(

---

### Post by worksofcraft on 2009-06-13
Just out of interest, submitted my mpeg video files to Windows Movie Maker... and got the error message "...cannot be imported because required codec is not installed..." the required mpeg codec is allegedly available from a Microsoft site but that requires validation of my windows installation. Even though I have a perfectly legitimate holographed product key Microsoft decree I installed it once too often. No doubt over the years I was just unlucky with viruses and irrecoverable system crashes but either way, having coughed up my hard earned cash for every one of their OS'es since DOS 3.1 I'm not paying them for yet another license :P

Conclusion: The cost of Windows Movie Maker would be prohibitive... so best persevere with Linux tyvm.

---

### Post by gnowak on 2009-06-14
Hey.

Nice to hear from someone else.

I actually don't think there is anything wrong with recordmydesktop or xvidcap. The error is with the soundcard. I have a Lenovo T400 and I have issues with sound, where soundcapture obviously is one of them.

Wake up Lenovo and or Intel and get us some nix support here ;-)

```

sudo lshw -C sound
[sudo] password for gnowak:
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


```

Xvidcap and recordmydesktop perform a lot better on my old T40p IBM.. IBM rulez... slash ruled..

---

### Post by worksofcraft on 2009-06-14
> **gnowak said:**
> Hey.

Nice to hear from someone else.

I actually don't think there is anything wrong with recordmydesktop or xvidcap. The error is with the soundcard. I have a Lenovo T400 and I have issues with sound, where soundcapture obviously is one of them.

Wake up Lenovo and or Intel and get us some nix support here ;-)

```

sudo lshw -C sound
[sudo] password for gnowak:
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


```

Xvidcap and recordmydesktop perform a lot better on my old T40p IBM.. IBM rulez... slash ruled..

well mine gives: 
sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32 module=snd_hda_intel


so it's the same driver. I had incredible problems with the audio on Hardy Heron... in fact I just gave up and installed Jaunty Jackalope which works just fine with sound recorder.

---

### Post by worksofcraft on 2009-06-14
Meanwhile I'm still trying to add my own narration to the videos I captured from my desk top.

Had no problem installing PiTiVi using
sudo apt-get install pitivi


...but would you believe, like in Kino I can find no way to put my .wav recorded audio onto the story board with my .mpeg recorded video clips and then export as a new video. Sigh - surely this is fairly elemental I thought... am I missing something here ? :/

---

### Post by gnowak on 2009-06-15
You could do that in Kdenlive.

---

### Post by gobberpooper on 2009-07-12
oh wow thank you very much. I was about to install that one until it told me that it would be better to install the latest version.

---

