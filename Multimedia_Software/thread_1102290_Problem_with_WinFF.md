---
title: "Problem with WinFF"
date: 2009-03-21
forum: Multimedia Software
---

### Post by bbharatsony on 2009-03-21
Whenever I use WinFF and I click convert, an error in the terminal comes up:

/usr/bin/ffmpeg: symbol lookup error: /usr/bin/ffmpeg: undefined symbol ffm_nopts

I use Intrepid. I have tried reinstalling WinFF. I have also tried uninstalling it fully and installing it again. But it still doesn't work. Can someone please help?

---

### Post by FakeOutdoorsman on 2009-03-21
Do you have any third-party repositories enabled?  Give the full output of:
```
ffmpeg -version
```

---

### Post by paul.gevers on 2009-03-23
> **bbharatsony said:**
> /usr/bin/ffmpeg: symbol lookup error: /usr/bin/ffmpeg: undefined symbol ffm_nopts

This is definitely not a problem with WinFF, but a problem with ffmpeg. As FakeOutdoorsman mentions: what version of ffmpeg are you running.

---

### Post by bbharatsony on 2009-03-28
This is the output:
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: ffm_nopts

---

### Post by BrownieBoy on 2009-04-14
I'm now getting this same error.  Did you find out the cause?

---

### Post by gool7890 on 2009-04-14
thanks 
[COLOR="#FFFFFF"]watch tv online free, 3000+ channel TV sports[/COLOR] [COLOR="#FFFFFF"]http://goonlinetv.com[/COLOR]

---

### Post by FakeOutdoorsman on 2009-04-14
> **BrownieBoy said:**
> I'm now getting this same error.  Did you find out the cause?
Since there isn't much information being provided and I can't duplicate this error, I will make a guess that the error is probably the result of conflicting packages, which may or may not originate from a third-party repository.  Open a terminal and paste the result of:
```
dpkg --get-selections | grep libav
```
Also mention your Ubuntu version and if you are using any third-party repositories.

---

### Post by gizmobay on 2009-04-17
I started getting this error as well. When I initially upgraded to Intrepid I needed to use the unstripped libraries to make ffmpeg work. I've since removed them unstripped versions and they don't show up in Synaptic as installed so I'm not sure why they show up in the command you gave.

Here's my ffmpeg version. Well I just tried this and I can't get the info as I get the ffm_nopts error.

libavahi-client3                                install
libavahi-common-data                            install
libavahi-common3                                install
libavahi-compat-libdnssd1                       install
libavahi-core5                                  install
libavahi-glib1                                  install
libavahi-gobject0                               install
libavahi-qt3-1                                  install
libavahi-ui0                                    install
libavc1394-0                                    install
libavc1394-dev                                  install
libavcodec-dev                                  install
libavcodec-unstripped-51                        deinstall
libavcodec1d                                    deinstall
libavcodec51                                    install
libavcodec52                                    install
libavdevice-unstripped-52                       deinstall
libavdevice52                                   install
libavformat-dev                                 install
libavformat-unstripped-52                       deinstall
libavformat1d                                   deinstall
libavformat52                                   install
libavutil-dev                                   install
libavutil-unstripped-49                         deinstall
libavutil1d                                     deinstall
libavutil49                                     install

---

### Post by gizmobay on 2009-04-17
I figured out my problem. I enabled a repo so I could download kdelive and that caused a different libav* to be installed. I removed the repo backed out the unstripped libavs which also took out ffmpeg and then once done I just reinstalled ffmpeg.

---

