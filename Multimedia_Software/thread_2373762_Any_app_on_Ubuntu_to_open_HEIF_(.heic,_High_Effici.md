---
title: "Any app on Ubuntu to open HEIF (.heic, High Efficiency Image File Format) pictures?"
date: 2017-10-09
forum: Multimedia Software
---

### Post by tellapu on 2017-10-09
A certain cellphone maker has changed the default format of taking  pictures to HEIF (.heic, High Efficiency Image File Format), without  asking the users (although there is still the option to use jpeg/jpg).  
Is there an **app**/program on Ubuntu that can **open HEIF-pictures and even let them be edited**? 
There are options to [convert HEIF to JPEG ]("https://stackoverflow.com/questions/45460611/convert-heif-heic-to-jpeg") or [even bulk convert]("https://github.com/pushd/heif"), but I am looking for a **picture viewer/editor that can handle HEIF-pictures**. Any hint?

---

### Post by linuxissuperawesome on 2017-10-09
Try gThumb. I Had A Similar Problem When I Tried To Open WEBP Format But Gthumb Helped me Out.

---

### Post by tellapu on 2017-10-09
Thanks,[**[COLOR=#000000] linuxissuperawesome[/COLOR]**]("https://ubuntuforums.org/member.php?u=2076297&"), for your reply. But at least gThumb 3.4.3, the version I have (Ubuntu 16.04), does not open it. I also tried Shotwell, GIMP, Okular, XnView Multi Platform with no success.

---

### Post by ajgreeny on 2017-10-09
It looks as if you may have to compile your own app to convert them.
See [https://github.com/pushd/heif](https://github.com/pushd/heif)

I have no knowledge of that application, how well it works or anything at all about it, so this will have to be a "suck it and see" situation, I'm afraid.

---

### Post by oldfred on 2017-10-09
Some more links. But I have not found anything that works for me.
 iOS 11 new photo format HEIF
[https://github.com/pushd/heif](https://github.com/pushd/heif)
[https://github.com/nokiatech/heif](https://github.com/nokiatech/heif)
[https://nokiatech.github.io/heif/technical.html](https://nokiatech.github.io/heif/technical.html)
[https://github.com/ImageMagick/ImageMagick/issues/507#issuecomment-330418013](https://github.com/ImageMagick/ImageMagick/issues/507#issuecomment-330418013) 

But I can still pair iOS11, but not now see files. This patch not yet updated, unless you compile yourself.

 iOS 11 patch
[https://github.com/libimobiledevice/libimobiledevice/commit/5a85432719fb3d18027d528f87d2a44b76fd3e12](https://github.com/libimobiledevice/libimobiledevice/commit/5a85432719fb3d18027d528f87d2a44b76fd3e12)
[https://github.com/libimobiledevice/libimobiledevice](https://github.com/libimobiledevice/libimobiledevice)

---

### Post by Barry_Luijten on 2018-04-09
I came across this project, which also comes with a pre-compiled static binary:
[https://github.com/monostream/tifig](https://github.com/monostream/tifig)

---

### Post by kathyjohnson320 on 2018-04-11
[COLOR=#000000] gThumb is useful in this kind of situation.[/COLOR]

---

### Post by tellapu on 2018-05-02
Thanks for the replies, but latest gThumb 3.6.1 (Ubuntu 18.04) still does not open the HEIF-pictures. I prefer to be able to open them than to covert them. Thaks.

---

### Post by Yellow Pasque on 2018-05-02
A program called "MP4client" (found in gpac package) supposedly supports HEIF. I tried it here on Debian sid and didn't have any luck (blank window). Maybe the version isn't new enough?
[https://gpac.wp.imt.fr/2017/06/09/gpac-support-for-heif/](https://gpac.wp.imt.fr/2017/06/09/gpac-support-for-heif/)

---

### Post by aldridge2 on 2018-05-05
"MP4client" should work for u.

---

### Post by monkeybrain20122 on 2018-05-06
Gimp does, libheif is in the repo for Ubuntu 17.10 or 18.04, for 16.04 and 14.04 there is a [ppa]("https://launchpad.net/~strukturag/+archive/ubuntu/libheif").
[https://github.com/strukturag/heif-gimp-plugin](https://github.com/strukturag/heif-gimp-plugin)

---

### Post by tellapu on 2018-05-23
@Temüjin Thanks for the hint regarding **mp4client**. I have not found time to try this.

As monkeybrain20122 mentioned there is a plugin for **GIMP** and the most recent GIMP version automatically comes with this plugin:
**GIMP 2.10.2** with support for HEIF image format ([https://www.gimp.org/news/2018/05/20/gimp-2-10-2-released/):](https://www.gimp.org/news/2018/05/20/gimp-2-10-2-released/):)  
You can install/upgrade to [GIMP 2.10.2 on Ubuntu via Flatpak]("https://flathub.org/apps/details/org.gimp.GIMP") or wait for [Otto’s GIMP PPA]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp") for Ubuntu 18.04 LTS to be updated with the new build ([https://www.omgubuntu.co.uk/2018/05/linux-release-roundup-gnome-twitch-app](https://www.omgubuntu.co.uk/2018/05/linux-release-roundup-gnome-twitch-app)).

---

### Post by dreamcarrior on 2018-08-07
I am using Fedora 28 and came across XnView. I tried XnView MP, but no plugins for the HEIC file type. I then tried the XnView windows version (using wine) and install the HEIC plugin, which then works perfectly. Has anyone found a better way?

---

### Post by w_barath on 2018-12-08
On ubuntu 18.04:

```
sudo apt install libheif-examples
```

then:

```
heif-convert IMG_1605.HEIC IMG_1605.jpg
```

NOTE: you must use lowercase '.jpg' or it will complain that it doesn't know the format.

---

