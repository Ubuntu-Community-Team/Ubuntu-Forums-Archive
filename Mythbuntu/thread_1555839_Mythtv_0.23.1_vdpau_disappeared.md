---
title: "Mythtv 0.23.1 vdpau disappeared"
date: 2010-08-18
forum: Mythbuntu
---

### Post by utar on 2010-08-18
I have just upgrade to Myth 0.23.1 on Mythbuntu 9.10 using autobuilds.

However vdpau has totally disappeared.  I cannot select it as a decoder in the playback menus.  The mythfrontend log contains zero entries mentioning vdpau.

My searches have come up with nothing.

Any help would be appreciated as my media centre struggles to play HDTV without vdpau.


Cheers.

---

### Post by utar on 2010-08-18
Hmmm, not sure if everything has upgraded properly.  The themes are still on 0.23, although Myth itself seems to all be on 0.23.1.

---

### Post by LowSky on 2010-08-18
Could it be that it isn't upgrading correctly because oyu are not using 10.04?

Or have you not added the PPA for 0.23.1
[https://edge.launchpad.net/~mythbuntu/+archive/0.23.1](https://edge.launchpad.net/~mythbuntu/+archive/0.23.1)

---

### Post by utar on 2010-08-18
Thanks for the reply.

0.23.1 is mean to work on 9.10, and it does apart from the fact that vdpau is missing on my system.

I have added the ppa for 0.23.1 through enabling autobuilds.  From what I can tell all the myth components (except themes) are at build 25609 which is the latest.

This is stumping me.

---

### Post by utar on 2010-08-18
Sorry to keep replying to my own posts but I have noticed the following in the build log:

[http://launchpadlibrarian.net/53453318/buildlog_ubuntu-karmic-i386.mythtv_0.23.1%2Bfixes25609-0ubuntu0%2Bmythbuntu1_FULLYBUILT.txt.gz](http://launchpadlibrarian.net/53453318/buildlog_ubuntu-karmic-i386.mythtv_0.23.1%2Bfixes25609-0ubuntu0%2Bmythbuntu1_FULLYBUILT.txt.gz)

```
./configure --compile-type=debug --prefix=/usr --runprefix=/usr --enable-lirc --enable-audio-alsa --enable-audio-oss --enable-audio-jack --enable-dvb --enable-ivtv --enable-firewire --enable-joystick-menu --enable-opengl-vsync --enable-libfaad --with-bindings=perl --enable-opengl-video --enable-ffmpeg-pthreads --perl-config-opts="INSTALLDIRS=vendor" --cpu=i686 --enable-mmx --enable-xvmc --enable-xvmc-vld --enable-xvmc-pro --enable-glx-procaddrarb --enable-vdpau
Please upgrade to libvdpau >= 0.2 if you would like vdpau support.
```

I'm not a coder but to me if looks like vdpau support has not been compiled into the Karmic autobuild.  Is this an accident?

---

### Post by tgm4883 on 2010-08-18
> **utar said:**
> Sorry to keep replying to my own posts but I have noticed the following in the build log:

[http://launchpadlibrarian.net/53453318/buildlog_ubuntu-karmic-i386.mythtv_0.23.1%2Bfixes25609-0ubuntu0%2Bmythbuntu1_FULLYBUILT.txt.gz](http://launchpadlibrarian.net/53453318/buildlog_ubuntu-karmic-i386.mythtv_0.23.1%2Bfixes25609-0ubuntu0%2Bmythbuntu1_FULLYBUILT.txt.gz)

```
./configure --compile-type=debug --prefix=/usr --runprefix=/usr --enable-lirc --enable-audio-alsa --enable-audio-oss --enable-audio-jack --enable-dvb --enable-ivtv --enable-firewire --enable-joystick-menu --enable-opengl-vsync --enable-libfaad --with-bindings=perl --enable-opengl-video --enable-ffmpeg-pthreads --perl-config-opts="INSTALLDIRS=vendor" --cpu=i686 --enable-mmx --enable-xvmc --enable-xvmc-vld --enable-xvmc-pro --enable-glx-procaddrarb --enable-vdpau
Please upgrade to libvdpau >= 0.2 if you would like vdpau support.
```

I'm not a coder but to me if looks like vdpau support has not been compiled into the Karmic autobuild.  Is this an accident?

Looks like just a mistake in the PPA, I think i've fixed it. We will see when the next build happens

---

### Post by utar on 2010-08-19
Cheers again for the second time in as many threads!

Hopefully there will be an update soon.

---

### Post by matt06 on 2010-08-19
> **utar said:**
> Thanks for the reply.

0.23.1 is mean to work on 9.10, and it does apart from the fact that vdpau is missing on my system.

I have added the ppa for 0.23.1 through enabling autobuilds.  From what I can tell all the myth components (except themes) are at build 25609 which is the latest.

This is stumping me.

Same issue here with 25609 on Ubuntu 9.10, it broke after I updated to the current build this afternoon.

Thanks for looking into it tgm4883.

---

### Post by tgm4883 on 2010-08-19
yea 26609 is the last build, I was hoping that upstream would make a -fixes change so that the next build would go but they haven't yet. I'm pinging the other dev to see if we can do a build without an upstream change

---

### Post by utar on 2010-08-23
Hi


Was it possible to do a build without an upstream change?



Utar

---

### Post by tgm4883 on 2010-08-23
> **utar said:**
> Hi


Was it possible to do a build without an upstream change?



Utar

Yea, but I ran into some issues with the orig.tar.gz. I should have this worked out later today.

---

### Post by jennifer18 on 2010-08-23
> **matt06 said:**
> Same issue here with 25609 on Ubuntu 9.10, it broke after I updated to the current build this afternoon.

Thanks for looking into it tgm4883.
yea 26609 is the last build, I was hoping that upstream would make a -fixes change so that the next build would go but they haven't yet. I'm pinging the other dev to see if we can do a build without an upstream change

---

### Post by tgm4883 on 2010-08-23
> **jennifer18 said:**
> yea 26609 is the last build, I was hoping that upstream would make a -fixes change so that the next build would go but they haven't yet. I'm pinging the other dev to see if we can do a build without an upstream change

huh?

---

### Post by utar on 2010-08-23
> **tgm4883 said:**
> Yea, but I ran into some issues with the orig.tar.gz. I should have this worked out later today.

Cheers.

---

### Post by tgm4883 on 2010-08-24
This should be fixed in the builds last night. Let me know if they work.

---

### Post by utar on 2010-08-24
Yes, vdpau is now working.  Thanks again.

I did get an error the first time I installed but the second time worked fine.  However since everything is working I assume this isn't an issue:

```
dpkg: error processing /var/cache/apt/archives/mythtv-common_0.23.1+fixes25609-0ubuntu0+mythbuntu4_i386.deb (--unpack):

 trying to overwrite '/usr/share/mythtv/mythconverg_restore.pl', which is also in package mythtv-database 0:0.23.1+fixes25609-0ubuntu0+mythbuntu1

dpkg-deb: subprocess paste killed by signal (Broken pipe)

/var/lib/dpkg/info/mythtv-common.postinst: 118: db_set: not found

dpkg: error while cleaning up:

 subprocess installed post-installation script returned error exit status 127
```

Edit: I notice the themes aren't building for Karmic.  Albeit this isn't a problem as the 0.23 ones work fine.

---

### Post by matt06 on 2010-08-24
> **tgm4883 said:**
> This should be fixed in the builds last night. Let me know if they work.

Thank you tons, VDPAU is functional again!!  Got the same error as utar, but it seems to have fixed itself the second round.

---

