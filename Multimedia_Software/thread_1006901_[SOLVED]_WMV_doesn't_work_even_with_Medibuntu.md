---
title: "[SOLVED] WMV doesn't work even with Medibuntu"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Endolith on 2008-12-09
I was messing around with packages the other night, trying to make everything consistent and removing everything I didn't recognize in "local or obsolete", etc.  I remember changing the installation of w32codecs, I think because a newer version was available that it hadn't installed automatically, but now WMV doesn't work.  It's currently at version 20071007-0medibuntu3 and no other version is available.

It's got all the necessary codecs installed in /usr/lib/codecs:

```
 ~> locate "/*wmv*dll*"
/usr/lib/codecs/wmv9dmod.dll
/usr/lib/codecs/wmvadvd.dll
/usr/lib/codecs/wmvdmod.dll

```But Totem is apparently looking in the wrong place:

```

wine/module: Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
Failed creating an audio decoder: could not open DMO filter from DLL wmadmod.dll
wine/module: Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
Failed creating a video decoder: could not open DMO filter from DLL wmvdmod.dll
** Message: Error: Internal data stream error.
gstasfdemux.c(1372): gst_asf_demux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstASFDemux:asfdemux0:
streaming stopped, reason not-negotiated

```What's wrong with my configuration?  And what does Wine have to do with anything?

---

### Post by mc4man on 2008-12-09
Even though w32codecs is installed to /usr/lib/codecs, somes apps still look to /usr/lib/win32. So when you install the package a  folder link named win32 is created in /usr/lib that links to the actual location.

You may have removed or broken the link.

You could check it out or try doing a "complete removal" of w32codecs in synaptic and then reinstalling.

---

### Post by Endolith on 2008-12-09
> **mc4man said:**
> Even though w32codecs is installed to /usr/lib/codecs, somes apps still look to /usr/lib/win32. So when you install the package a  folder link named win32 is created in /usr/lib that links to the actual location.

You may have removed or broken the link.

You could check it out or try doing a "complete removal" of w32codecs in synaptic and then reinstalling.

Hah!  That worked.  I'm guessing I completely removed another package that took those links with it.  I think this would qualify as a bug, but the package management system is so convoluted I would have no idea what's actually at fault...

---

### Post by Ekeluo on 2009-08-23
I try to play some wmv files with totem and they play fine while some others do not. Totem gives the error:

```
** Message: Error: Internal data stream error.
gstasfdemux.c(1303): gst_asf_demux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstASFDemux:asfdemux0:
```

I encoded the non-players with winff on intrepid ibex, while the ones that play were done by SUPER (guess there's a good reason why it's called SUPER then :lolflag: ) on Windows XP. Any help will be well appreciated.

P.S. the files play ok on mplayer and vlc, my beef is nautilus can't thumbnail them since I believe gstreamer has a problem with them.

---

### Post by petehall on 2011-03-21
> **mc4man said:**
> Even though w32codecs is installed to /usr/lib/codecs, somes apps still look to /usr/lib/win32. So when you install the package a  folder link named win32 is created in /usr/lib that links to the actual location.

You may have removed or broken the link.

You could check it out or try doing a "complete removal" of w32codecs in synaptic and then reinstalling.

I got this error on Ubuntu 10.10. Removing and reinstalling w32codecs didn't create the link so I did it myself:

```
sudo ln -s /usr/lib/codecs /usr/lib/win32
```

Pete

---

### Post by p110011 on 2011-03-24
> **petehall said:**
> I got this error on Ubuntu 10.10. Removing and reinstalling w32codecs didn't create the link so I did it myself:

```
sudo ln -s /usr/lib/codecs /usr/lib/win32
```

Pete

That worked for me, thanks!

---

### Post by Talieson on 2011-09-29
Originally Posted by mc4man  
Even though w32codecs is installed to /usr/lib/codecs, somes apps still look to /usr/lib/win32. So when you install the package a folder link named win32 is created in /usr/lib that links to the actual location.

You may have removed or broken the link.

You could check it out or try doing a "complete removal" of w32codecs in synaptic and then reinstalling.

Originally Posted by petehall  
I got this error on Ubuntu 10.10. Removing and reinstalling w32codecs didn't create the link so I did it myself:

Code:
sudo ln -s /usr/lib/codecs /usr/lib/win32
Pete

awsome simple fix it worked for me as well thx pete

---

