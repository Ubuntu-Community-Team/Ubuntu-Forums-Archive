---
title: "gtkpod and ubuntu 7.10"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by stevecoh1 on 2008-02-24
I installed gtkpod via apt-get onto my Ubuntu 7.10 system. 

It seems to read my IPOD just fine and play music from it okay except it always starts with a spurious warning message about being sure that my sound card isn't being used by something else.

But the helper apps - those referred to on the preferences/tools tab - are missing.  I got xmms via apt-get, as well as lame,

But one tool does not appear to be available via aptget: that is oggdec, which is required by the /usr/share/gtkpod/scripts/convert-ogg2mp3.sh for converting ogg to mp3.  The Sound  Juicer app extracts CD tracks to ogg files, and they need to be converted to mp3.  The gtkpod script for doing this requires oggdec which isn't available from apt-get and thus I can't load these tracks onto IPOD

Can someone provide a HOWTO on configuring GTKPOD for ubuntu or other info for using gtkpod successfully under Ubuntu?

---

### Post by cozmicharlie on 2008-02-24
First, install the medibuntu repository and the Ubuntu restricted extras.
[https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067)

In Soundjuicer you do not have to code to ogg - open Soundjuicer>edit>preferences and at the bottom of the dialog is "format output" scroll to mp3 if that is what you want.

This should get everything you need.

Enjoy

---

