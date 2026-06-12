---
title: "DisplayPort =&gt; DVI ?"
date: 2010-01-27
forum: Multimedia Software
---

### Post by tincup on 2010-01-27
Hi.

I have a Dell Latitude E6400 with Karmic (Intel graphics chip). Currently, I am trying to connect a 22'' TFT using a DisplayPort to DVI adaptor plug. Unfortunately, it doesn't even seem to find the screen.

xrandr does not list it:
```

VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 189mm
   1440x900       60.1*+   59.9     40.4
   1360x768       59.8
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0
   1024x768       85.0     75.0     70.1     60.0
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

```

I know from another guy who connected an HDMI TV over DisplayPort, and this devices is listed unter "HDMI1", and not "DP1". So I am not quite sure where it would be listed even if it found the screen.

Any ideas?

Cheers,
tin

---

### Post by cb951303 on 2010-01-27
converter adapters work only if your monitor supports it.
does your monitor support both displayport and dvi?

---

### Post by tincup on 2010-01-27
Ooh ok, I did not know that.

Most probably it does not support DisplayPort, because the screen is at least 2 years old, I think. It has both DVI and VGA inputs.

I thought that due to the ingoing DVI cable the screen does not care about DisplayPort.

Need to search for another solution then, thanks.

tin


edit: why are there DisplayPort to DVI adaptors anyway, if screens with DVI cables do not support DisplayPort?

---

### Post by efflandt on 2010-01-28
Since your computer appears to have HDMI, why not try HDMI to DVI cable.  The digital signals on those are the same, just that DVI is missing audio (sound from TV speakers would need separate audio cable).  I have done that the other way from DVI up converting DVD player to HDMI TV.

If you use VGA instead, you may have to use **xrandr** and **cvt** in terminal to find/set a modeline for native resolution of external display, since it may be a mismatch from your laptop screen.

I do not think you have to mess with that for HDMI/DVI, unless the multiple displays default to a different common resolution.  My desktop with only one display connected (by DVI) defaults to the native resolution of the HDTV.

---

