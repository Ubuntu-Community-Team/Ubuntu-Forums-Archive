---
title: "How to enable Vaapi?"
date: 2011-03-30
forum: Multimedia Software
---

### Post by MrSparklle on 2011-03-30
Anybody can point me the steps to successful install VAAPI under Ubuntu?

Last week I tried several times diferent drivers, libs, packages and nothing work.

Actually I'm using Ubuntu Lucid under Inter C2D 3.0Ghz, with ATI Radeon HD-3870 graphics card.
I already installed ATI Drivers (Catalyst) latest version (11).

What exactly I need to install? Catalysthacks ([https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)) can solve my problems? 

Sorry for dumb question, I'm almost noob on Linux.

---

### Post by wolfen69 on 2011-03-30
Go to system>administration>synaptic package manager and then settings-repositories-other software. Click the add button and enter **ppa:ikuya-fruitsbasket/vaapi**

Close, then reload when asked. Vaapi will then be available in synaptic to download.

---

### Post by MrSparklle on 2011-03-30
Thanks for help Wolfen.

I don't using X at this moment, I installed a Live Version of XBMC and try to enable hardware acceleration through Vaapi.

Anyway, I try to use this PPA to update with these commands:

```
$ sudo add-apt-repository ppa:ikuya-fruitsbasket/vaapi
```

ok

```
$ sudo apt-get update
```

Errors: 

```
W: Failed to fetch http://ppa.launchpad.net/ikuya-fruitsbasket/vaapi/ubuntu/dists/[COLOR="red"]lucid[/COLOR]/main/binary-i386/Packages.gz 404 Not Found


W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/[COLOR="Red"]lucid[/COLOR]/main/binary-i386/Packages.gz 404 Not Found

```

---

### Post by wolfen69 on 2011-03-31
From [here,]("https://launchpad.net/~ed10vi86/+archive/video/+index?field.series_filter=lucid") "For AMD/ATI VAAPI support, install **xvba-va-driver** package.

---

### Post by Yellow Pasque on 2011-03-31
VA-API is broken for UVD1 (RadeonHD 2k & 3k series) cards in latest Catalyst. You may get it working with Catalyst 10-7.

---

### Post by MrSparklle on 2011-04-01
I finally make it works, but unfortunately the video not plays well.

I installed ATI 10.7 like Temujin recomends, install 0.31.1 versions of Libva, XVBA packges from [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/).

I just can play the video if disable VSYNC, but I get a lof of stuttering. If VSYNC is enable the video plays but with some horizontal targets inside screen.

After several tries to solve the problem, I decide to upgrade Libva, XVBA from the splitted-desktop unsucessfull. I can't remove it, and I can't make it work again. If I install a different version of (0.31.1) it broken Libvainfo:

```
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

---

### Post by Yellow Pasque on 2011-04-01
> I finally make it works, but unfortunately the video not plays well.
You need to rebuild vlc (or mplayer-vaapi) against the new libva to actually get hardware acceleration. This is already done for you with catalysthacks PPA. Maybe this will also fix your libva: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
You may have more success with an older version of xvba-video, since you're using an older version of Catalyst.

---

### Post by MrSparklle on 2011-04-01
> **Temüjin said:**
> You need to rebuild vlc (or mplayer-vaapi) against the new libva to actually get hardware acceleration. 
Yes, I known. I rebuild XBMC with --vappi to enable it. 

> **Temüjin said:**
> 
This is already done for you with catalysthacks PPA. Maybe this will also fix your libva: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
 
Can I install it in Lucid? I think this PPA is just for Maverick.

> **Temüjin said:**
> 
You may have more success with an older version of xvba-video, since you're using an older version of Catalyst.
This weekend I will do some more tests until I change my mind to get a Nvidia Card.

---

### Post by Yellow Pasque on 2011-04-01
> **MrSparklle said:**
> Can I install it in Lucid? I think this PPA is just for Maverick.

Sorry, it's only for Maverick. You're the first person to ask about va-api on Lucid. 

[RANT]This is one of my gripes with non rolling-release distros - if I want to release software, I have to support at least 2 versions, and more likely, 3.
I'm not even sure if the version of VLC in Lucid had VA-API in it, and I'm not interested in backporting an updated version of VLC to Lucid because of all the dependency issues.

Currently, I only have Maverick and Natty VM's, and I will get rid of the Maverick one after Natty's release and turn it into Natty+1/Oneiric[/RANT]

---

