---
title: "Totem install bad plugins source"
date: 2009-08-25
forum: Multimedia Software
---

### Post by mac-duff on 2009-08-25
Hi,

because of the new Pidgin version I crashed my Totem and I now get every time the error that I have to install the codecs.

But when I download the gst-plugins-bad-0.10.13 source and do a ./configure I get this message:

```

configure: *** Plug-ins with dependencies that will NOT be built:
	acm
	amrwb
	assrender
	cdaudio
	celt
	dc1394
	dirac
	directdrawsink
	divx
	dtsdec
	faac
	faad
	gsmenc gsmdec
	ivorbisdec
	jack
	ladspa
	libmms
	metadata
	mimic
	modplug
	mpeg2enc
	mplex
	musepack
	musicbrainz
	mythtvsrc
	neonhttpsrc
	ofa
	osxvideosrc
	qtwrapper
	resindvd
	sdlvideosink sdlaudiosink
	sfsrc sfsink
	soundtouch
	spc
	swfdec
	theoraexpdec
	timidity
	wildmidi
	wininet
	xvid

```

How can I anyway install this codecs?

Thx
Stephan

---

### Post by mac-duff on 2009-08-26
or how can I get the old gestreamer with totem back?

I already reinstalled the packages out of package manager. Any ideas?

---

### Post by mac-duff on 2009-08-26
Ok, solved by "make uninstall"

---

