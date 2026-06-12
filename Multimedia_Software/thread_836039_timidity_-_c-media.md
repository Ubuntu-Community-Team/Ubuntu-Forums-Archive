---
title: "timidity - c-media"
date: 2008-06-21
forum: Multimedia Software
---

### Post by Allochtoon on 2008-06-21
Hello,

I'm problems with timidity. Also, previous installations, i was having problems getting sound at all.

Soundcard:
```

marco@kubuntu:~$ lsusb
Bus 003 Device 007: ID 04b8:012d Seiko Epson Corp.
Bus 003 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc.

```



```

(Reading database ... 150590 files and directories currently installed.)
Unpacking python-gtkhtml2 (from .../python-gtkhtml2_2.19.1-0ubuntu7_amd64.deb) ...
Selecting previously deselected package python-imaging-sane.
Unpacking python-imaging-sane (from .../python-imaging-sane_1.1.6-1ubuntu5_amd64.deb) ...
Selecting previously deselected package eikazo.
Unpacking eikazo (from .../eikazo_0.5.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package gimp2.0-quiteinsane.
Unpacking gimp2.0-quiteinsane (from .../gimp2.0-quiteinsane_0.3-8_amd64.deb) ...
Selecting previously deselected package libsane-extras.
Unpacking libsane-extras (from .../libsane-extras_1.0.18.12ubuntu1_amd64.deb) ...
Replaced by files in installed package libsane ...
Selecting previously deselected package sane-utils.
Unpacking sane-utils (from .../sane-utils_1.0.19-1ubuntu3_amd64.deb) ...
Selecting previously deselected package xsane-doc.
Unpacking xsane-doc (from .../xsane-doc_0.995-1ubuntu1_all.deb) ...
Selecting previously deselected package libksane0.
Unpacking libksane0 (from .../libksane0_0.1.0-0ubuntu4_amd64.deb) ...
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                        ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                                                                              [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of songwrite:
 songwrite depends on timidity | playmidi | pmidi; however:
  Package timidity is not configured yet.
  Package playmidi is not installed.
  Package pmidi is not installed.
dpkg: error processing songwrite (--configure):
 dependency problems - leaving unconfigured
Setting up python-gtkhtml2 (2.19.1-0ubuntu7) ...

Setting up python-imaging-sane (1.1.6-1ubuntu5) ...

Setting up eikazo (0.5.2-2ubuntu1) ...

Setting up gimp2.0-quiteinsane (0.3-8) ...
Setting up libsane-extras (1.0.18.12ubuntu1) ...

Setting up sane-utils (1.0.19-1ubuntu3) ...
Adding saned group and user...

Setting up xsane-doc (0.995-1ubuntu1) ...

Setting up libksane0 (0.1.0-0ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 timidity
 songwrite
Selecting previously deselected package timidity-interfaces-extra.
(Reading database ... 150946 files and directories currently installed.)
Unpacking timidity-interfaces-extra (from .../timidity-interfaces-extra_2.13.2-19ubuntu1_amd64.deb) ...
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                        ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                                                                              [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of songwrite:
 songwrite depends on timidity | playmidi | pmidi; however:
  Package timidity is not configured yet.
  Package playmidi is not installed.
  Package pmidi is not installed.
dpkg: error processing songwrite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of timidity-interfaces-extra:
 timidity-interfaces-extra depends on timidity (= 2.13.2-19ubuntu1); however:
  Package timidity is not configured yet.
dpkg: error processing timidity-interfaces-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 songwrite
 timidity-interfaces-extra                                                              

```

Thanks in advance,

---

