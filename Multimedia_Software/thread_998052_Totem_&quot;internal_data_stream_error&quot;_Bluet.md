---
title: "Totem &quot;internal data stream error&quot; Bluetooth Headset"
date: 2008-11-30
forum: Multimedia Software
---

### Post by perrya on 2008-11-30
Totem will play a paticular video but not sound. So I get to see what the video is but there is no sound. When I configure my Bluetooth headset to hear the sound I get an internal data stream error. It only happens on paticular video formats. 

```
perry@perry-m1530:~/Desktop$ totem 96FFF3ECd01.flv
** (totem:7476): DEBUG: Init of Python module
** (totem:7476): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7476): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7476): DEBUG: Creating Python plugin instance
** (totem:7476): DEBUG: Init of Python module
** (totem:7476): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7476): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7476): DEBUG: Creating Python plugin instance
** Message: Error: Internal data stream error.
gstflvdemux.c(538): gst_flv_demux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstFLVDemux:flvdemux0:
stream stopped, reason not-negotiated

** (totem:7476): DEBUG: Finalizing Python plugin instance
** (totem:7476): DEBUG: Finalizing Python plugin instance
perry@perry-m1530:~/Desktop$ 
```

Funniest thing. If I'm not using my Bluetooth Headset I don't get this error. However, video plays but no sound.  I WANT to be able to use my headset with this. The video I used was [Let it Rock on Youtube]("http://www.youtube.com/watch?v=dh3gGQfyVyw").

To play this format, an additional package was required. 

Any help would be greatly appreciated.

---

