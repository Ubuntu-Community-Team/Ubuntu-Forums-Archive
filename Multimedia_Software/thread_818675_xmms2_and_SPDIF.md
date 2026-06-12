---
title: "xmms2 and SP/DIF"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Evil Dax on 2008-06-04
I've upgraded a while back to 8.04, and I found that xmms is no longer supported.
So, now I am trying to get the xmms2 to work.
The problem I'm facing is this:
I could always swap very easily from my analogue pc-speakers (hw0,0) to my digital surround speakers on SPDIF (hw0,2).
VLC is still supporting this, so all is installed correctly.

With xmms2d I cannot find the correct options that I need to put in xmms2.conf to get this done, it only seems to support my analogue (formerly hw0,0) option.

Since I'm using Nforce2, I have tried this one:
[http://ubuntuforums.org/showthread.php?t=253725](http://ubuntuforums.org/showthread.php?t=253725)
but this does more bad than good to my system, as it kills all other audio.

So, basically I'm searching for the right code to put here (xmms2.conf)
```

<?xml version="1.0"?>
<xmms version="2">
	<section name="alsa">
		<property name="device">default</property>
		<property name="mixer">PCM</property>
		<property name="mixer_dev">default</property>
	</section>

```

Any help would greatly be appreciated !

---

### Post by Evil Dax on 2008-06-10
*bump*

Nobody ? :confused:

---

