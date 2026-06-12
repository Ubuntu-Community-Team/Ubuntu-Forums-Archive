---
title: "Dependency problem with gstreamer0.10-ffmpeg"
date: 2012-05-01
forum: Multimedia Software
---

### Post by Trucoto on 2012-05-01
Hi all, after upgrading to 12.04, I have a problem playing videos. I seem to need gstreamer0.10-ffmpeg, which depends on libavcodec-extra-53 (>=4:0.7.3-1 and < 5:0). Problem is, libavcodec-extra-53 I have installed is 5:0.7.2-1ubuntu1+codecs1~oneiric2, I don't know if it was upgraded or for some reason I had it from some repository. How can I install gstreamer-ffmpeg? Synaptic/apt won't let me because the libavcodec-extra version is too new, as it seems. What can I do?

---

### Post by The Rnegade on 2012-05-01
> **Trucoto said:**
> Hi all, after upgrading to 12.04, I have a problem playing videos. I seem to need gstreamer0.10-ffmpeg, which depends on libavcodec-extra-53 (>=4:0.7.3-1 and < 5:0). Problem is, libavcodec-extra-53 I have installed is 5:0.7.2-1ubuntu1+codecs1~oneiric2, I don't know if it was upgraded or for some reason I had it from some repository. How can I install gstreamer-ffmpeg? Synaptic/apt won't let me because the libavcodec-extra version is too new, as it seems. What can I do?

thats very strange the ubuntu 12.04 repo is libavcodec-extra-53 4:0.8.1

youre gonna have to uninstall youre weird version which i dont even know why you have it.

try to uninstall via synaptic.

in my experience updating instead of a clean install of a new version messes with the libraries

---

### Post by mc4man on 2012-05-01
You were  using the &#8220;KXStudio Team&#8221; team ppa which for some reason named it's libav packages with a 5: for oneiric, -  libav ([COLOR="Red"]5[/COLOR]:0.7.2-1ubuntu1+codecs1~oneiric2)
[https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

So now your libavcodec53*, libavformat53*, ect are versioned higher than the current precise ones & even the ppa's precise libav packages,  - libav ([COLOR="Blue"]4[/COLOR]:0.8.1-0ubuntu1+codecs1) precise;
[https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise](https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise)

So if you want to continue to use the ppa  - 
First make sure that the ppa is sourced to precise
Then you could  - 
Use apt pin (Pin-Priority)  to cause the ppa's precise packages to be an upgrade

Use synaptic to remove all the libav source files, run an update, then re-install them, the gstreamer plugin & anything else removed.

Download all the libav source packages from the ppa for precise, put in a folder & run sudo dpkg -i *.deb on

If you want to return tp precise packages then remove the ppa from your sources, update & do any of the above but obviously for 1 & 3 do from precise perspective

The synaptic way, while you'll temp lose some packages is very straightforward & not hard to figure
(synaptic keeps a history so you'll see anything add. removed

---

### Post by Trucoto on 2012-05-02
> **mc4man said:**
> You were  using the “KXStudio Team” team ppa which for some reason named it's libav packages with a 5: for oneiric, -  libav ([COLOR="Red"]5[/COLOR]:0.7.2-1ubuntu1+codecs1~oneiric2)
[https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

So now your libavcodec53*, libavformat53*, ect are versioned higher than the current precise ones & even the ppa's precise libav packages,  - libav ([COLOR="Blue"]4[/COLOR]:0.8.1-0ubuntu1+codecs1) precise;
[https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise](https://launchpad.net/~kxstudio-team/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise)

So if you want to continue to use the ppa  - 
First make sure that the ppa is sourced to precise
Then you could  - 
Use apt pin (Pin-Priority)  to cause the ppa's precise packages to be an upgrade

Use synaptic to remove all the libav source files, run an update, then re-install them, the gstreamer plugin & anything else removed.

Download all the libav source packages from the ppa for precise, put in a folder & run sudo dpkg -i *.deb on

If you want to return tp precise packages then remove the ppa from your sources, update & do any of the above but obviously for 1 & 3 do from precise perspective

The synaptic way, while you'll temp lose some packages is very straightforward & not hard to figure
(synaptic keeps a history so you'll see anything add. removed

mc4man, you are the man! Thank you very much, it worked like a charm :)

---

