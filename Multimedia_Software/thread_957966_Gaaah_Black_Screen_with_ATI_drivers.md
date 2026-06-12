---
title: "Gaaah Black Screen with ATI drivers"
date: 2008-10-24
forum: Multimedia Software
---

### Post by PoopyTheJ on 2008-10-24
Ok, I've gotten this problem with Gutsy, Hardy and Intrepid now. When I install the ATI drivers from 8.6 through 8.10 I get a black screen when booting, monitor goes to sleep and pow nothing works. I can boot to the recovery kernel and try to fix the xorg file, but even then when I try to get into the x session it dies on me until I choose failsafe gnome. This is seriously aggravating me as I have an ATI 3850 on two rigs one is a Intel dual core rig and the other is a AMD rig with an MCP61 based mobo. The intel rig install and runs fine the AMD rig will NOT work with the ATI drivers, and I get no acceleration with the HD drivers which I tried after an upgrade to intrepid. I'm going to try installing Intrepid from scratch and then attempting to use the Radeon HD drivers, however when I tried before it didn;t look like it was actually using the drivers. Installed but not being used. Ok so long story short, does anyone have any ideas on using the RadeonHD drivers or getting the ATI proprietary drivers to work. I'd kinda prefer the proprietary as I can get compiz with them, but I'll take anything at this point. The only major difference is the mobo and processor, and I'm thinking perhaps its something to do with the motherboard drivers, is there anything funny about nvidia motherboards and ubuntu?

One final note when trying to install Intrepid from the LiveCD I get a black screen as well, also get this with 7.10 but 8.04 will work. totally at a loss here...

---

### Post by Yellow Pasque on 2008-10-24
The open-source radeonhd driver in the intrepid repo is seriously outdated. Anyway, even if you build from the git source, it doesn't include R600/R700 acceleration yet because AMD/ATI is taking its sweet time in releasing documentation to the devs.

Your only hope right now is the fglrx driver,

---

### Post by PoopyTheJ on 2008-10-24
hmmm, well either way Intrepid from a clean install boots to a black screen. I'm gona install 8.04 and try to install the newest RadeonHD drivers, have a good source for a howto or documentation on those so I don't screw it up. Btw is there anything special I need for nvidia motherboards and ATI graphics? Seems to me years back they didn't play nice together is that what I'm running into here?

---

### Post by Yellow Pasque on 2008-10-24
I actually started to write documentation on installing the radeonhd driver from source here:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by Yellow Pasque on 2008-10-24
To complete that, I should add these instructions
```
cd /usr/src/xf86-video-radeonhd
gksudo gedit configure.ac Makefile.am
```
In the configure.ac file, paste this into the file: AC_CONFIG_MACRO_DIR([m4])
after the line that reads: AC_CONFIG_AUX_DIR(.) 
In the Makefile.am file, paste this: ACLOCAL_AMFLAGS = -I m4 
after the line that reads: SUBDIRS = src man utils/conntest

Now you can build the radeonhd driver
```
sudo ./autogen.sh --prefix=/usr
sudo make
sudo make install
```

The last step is to configure xorg.conf to use your driver, so:
```
gksudo gedit /etc/X11/xorg.conf
```
Find the Device section and change/add the driver line:
```
Section "Device"
	...
	**Driver	"radeonhd"**
        ...
EndSection
```

---

### Post by PoopyTheJ on 2008-10-25
ok, now this is wierd, now just trying to boot to the live 8.04 CD I get the monitor going to sleep on me. I can CTRL+ALT+BKSPC and restart X but the monitor just goes right back to sleep. Any ideas, I have no clue wtf is going on here

---

### Post by PoopyTheJ on 2008-10-25
ok got the booting issue solved, let you know when I try the drivers

---

### Post by PoopyTheJ on 2008-10-25
Ok started on your walkthrough, however the first area where you have the list of commands to get libraries I get this error...

Couldn't find package libpci-dev

Following is the hole print out...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting x11proto-resource-dev for regex 'x11proto*'
Note, selecting x11proto-xext-dev for regex 'x11proto*'
Note, selecting x11proto-fonts-dev for regex 'x11proto*'
Note, selecting x11proto-xf86dga-dev for regex 'x11proto*'
Note, selecting x11proto-kb-dev for regex 'x11proto*'
Note, selecting x11proto-gl-dev for regex 'x11proto*'
Note, selecting x11proto-xf86misc-dev for regex 'x11proto*'
Note, selecting x11proto-xinerama-dev for regex 'x11proto*'
Note, selecting x11proto-bigreqs-dev for regex 'x11proto*'
Note, selecting x11proto-render-dev for regex 'x11proto*'
Note, selecting x11proto-video-dev for regex 'x11proto*'
Note, selecting x11proto-panoramix-dev for regex 'x11proto*'
Note, selecting x11proto-trap-dev for regex 'x11proto*'
Note, selecting x11proto-record-dev for regex 'x11proto*'
Note, selecting x11proto-composite-dev for regex 'x11proto*'
Note, selecting x11proto-core-dev for regex 'x11proto*'
Note, selecting x11proto-dmx-dev for regex 'x11proto*'
Note, selecting x11proto-scrnsaver-dev for regex 'x11proto*'
Note, selecting x11proto-xf86bigfont-dev for regex 'x11proto*'
Note, selecting x11proto-randr-dev for regex 'x11proto*'
Note, selecting x11proto-damage-dev for regex 'x11proto*'
Note, selecting x11proto-input-dev for regex 'x11proto*'
Note, selecting x11proto-fixes-dev for regex 'x11proto*'
Note, selecting x11proto-print-dev for regex 'x11proto*'
Note, selecting x11proto-evie-dev for regex 'x11proto*'
Note, selecting x11proto-xf86vidmode-dev for regex 'x11proto*'
Note, selecting x11proto-xcmisc-dev for regex 'x11proto*'
Note, selecting x11proto-xf86dri-dev for regex 'x11proto*'
Note, selecting x11proto-fontcache-dev for regex 'x11proto*'
xutils-dev is already the newest version.
E: Couldn't find package libpci-dev

Let me know where to go from here and thanks for the help!

---

### Post by PoopyTheJ on 2008-10-25
btw, should that be libpcd-dev? 

Once again thanks a lot for the help!

---

### Post by Yellow Pasque on 2008-10-25
If you're on Hardy, that should be pciutils-dev (I made the change in the doc now). Thank you for the feedback.

---

### Post by Yashiro on 2008-10-25
I think that's a bit over the top there.

Once Ubuntu is installed with default VGA running. 
Don't enable the proprietary driver if the dialog asks you.

Install EnvyNG ([http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A))
Use that to install a working driver.

If that fails, look on the web for more info on installing Ati drivers.
Only as an absolute last resort compile those open source drivers yourself, unless you know what you are doing.

---

### Post by PoopyTheJ on 2008-10-25
ok I get this...

The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  g++-4.2 libc6-dev liberror-perl libice-dev libmailtools-perl libpciaccess0
  libpthread-stubs0 libpthread-stubs0-dev libsm-dev libtimedate-perl
  libx11-dev libxcb-xlib0-dev libxcb1-dev libxdmcp-dev libxt-dev
  linux-libc-dev x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-dmx-dev x11proto-evie-dev x11proto-fixes-dev
  x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-print-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc dh-make
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  cvs gettext-doc git-arch git-cvs git-daemon-run git-doc git-email git-gui
  git-svn gitk gitweb glibc-doc manpages-dev libtool-doc libhtml-format-perl
  libmail-imapclient-perl libmime-perl spamassassin libstdc++6-4.2-doc gcj
  gfortran fortran95-compiler diff-doc procmail graphviz
Recommended packages:
  automaken curl libcompress-zlib-perl
The following NEW packages will be installed:
  autoconf automake autotools-dev build-essential configure-debian debhelper
  diffstat dpkg-dev g++ g++-4.2 gawk gettext git-core html2text
  intltool-debian libc6-dev libdigest-hmac-perl libdigest-sha1-perl libdrm-dev
  liberror-perl libfile-remove-perl libice-dev libio-stringy-perl libltdl3-dev
  libmail-box-perl libmail-sendmail-perl libmailtools-perl libmime-types-perl
  libobject-realize-later-perl libpciaccess-dev libpciaccess0 libpixman-1-dev
  libpthread-stubs0 libpthread-stubs0-dev libsm-dev libstdc++6-4.2-dev
  libsys-hostname-long-perl libtimedate-perl libtool libuser-identity-perl
  libx11-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxdmcp-dev libxt-dev
  linux-libc-dev m4 patch pciutils-dev po-debconf quilt x11proto-bigreqs-dev
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-dmx-dev x11proto-evie-dev x11proto-fixes-dev x11proto-fontcache-dev
  x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev
  x11proto-print-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xserver-xorg-dev xtrans-dev zlib1g-dev
0 upgraded, 83 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.8MB of archives.
After this operation, 79.7MB of additional disk space will be used.
Do you want to continue [Y/n]? 



Should I install the recommended packages as well?

---

### Post by PoopyTheJ on 2008-10-25
Ok sorry for so many questions however now I come to the comiling and I see this command sudo ./autogen.sh --prefix=/usr
I downloaded the package to /home/username/RadeonHD does that matter and does it change the above command in any way? Or does this simply build the package in /usr which is where it should be anyways regardless of where I downloaded the package to? Also minor concern but for dummies like me it would be helpful to mention that if you enter the command gksudo gedit configure.ac Makefile.am without having terminal be in the directory where you downloaded the source files it opens up blank and worthless files.
Thanks again for the help!

---

### Post by PoopyTheJ on 2008-10-25
Yashiro this is my last resort I've already spent hours with the ATI drivers and they give me the same thing every time, using envy, from ATI packages, etc, a monitor in hibernation.

---

### Post by PoopyTheJ on 2008-10-25
Ok now hopefully I'm at the end for convenience sake I copied the xf86-video-radeonhd directory to /usr/src and navigated to it and ran sudo ./autogen.sh --prefix=/usr

I got this returned to me...


autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I m4
aclocal: couldn't open directory `m4': No such file or directory
autoreconf: aclocal failed with exit status: 1

---

### Post by palgan on 2008-10-25
> **PoopyTheJ said:**
> ok got the booting issue solved, let you know when I try the drivers

Hi,

Could you tell me how have you managed to solve this sleeping mode issue during booting?

Thanks in advance!

---

### Post by PoopyTheJ on 2008-10-25
Different revision, I solved the sleep issue on booting from CD not from HDD, that's why I'm trying the Open Source drivers, however I'm getting an error with this last command so I can't move forward.

---

