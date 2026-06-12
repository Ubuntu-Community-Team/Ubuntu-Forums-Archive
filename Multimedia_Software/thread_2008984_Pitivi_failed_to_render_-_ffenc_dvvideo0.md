---
title: "Pitivi failed to render - ffenc_dvvideo0"
date: 2012-06-23
forum: Multimedia Software
---

### Post by Lars Pensjö on 2012-06-23
When I do, I get the following error message. I am using version 0.15.2-0ubuntu0.1. Anyone knows how to fix this?

```
Traceback (most recent call last):
  File "/usr/lib/pitivi/python/pitivi/ui/encodingdialog.py", line 692, in _renderButtonClickedCb
    self.startAction()
  File "/usr/lib/pitivi/python/pitivi/actioner.py", line 151, in startAction
    self.addAction()
  File "/usr/lib/pitivi/python/pitivi/actioner.py", line 107, in addAction
    self._activateAction()
  File "/usr/lib/pitivi/python/pitivi/actioner.py", line 248, in _activateAction
    Actioner._activateAction(self)
  File "/usr/lib/pitivi/python/pitivi/actioner.py", line 130, in _activateAction
    self.action.activate()
  File "/usr/lib/pitivi/python/pitivi/action.py", line 121, in activate
    self._ensurePipelineObjects()
  File "/usr/lib/pitivi/python/pitivi/action.py", line 567, in _ensurePipelineObjects
    self.pipeline.getBinForFactoryStream(producer, automake=True)
  File "/usr/lib/pitivi/python/pitivi/pipeline.py", line 545, in getBinForFactoryStream
    bin = stream_entry.bin = factory.makeBin(stream)
  File "/usr/lib/pitivi/python/pitivi/factories/base.py", line 599, in makeBin
    bin = self._makeBin(input_stream)
  File "/usr/lib/pitivi/python/pitivi/encode.py", line 189, in _makeBin
    rb = self.renderfactory.makeBin()
  File "/usr/lib/pitivi/python/pitivi/factories/base.py", line 691, in makeBin
    bin = self._makeBin(input_stream)
  File "/usr/lib/pitivi/python/pitivi/encode.py", line 129, in _makeBin
    b2 = EncoderFactory(setting).makeBin()
  File "/usr/lib/pitivi/python/pitivi/factories/base.py", line 691, in makeBin
    bin = self._makeBin(input_stream)
  File "/usr/lib/pitivi/python/pitivi/encode.py", line 64, in _makeBin
    mod.link(enc)
gst.LinkError: failed to link bin12 with ffenc_dvvideo0

```

---

### Post by 98cwitr on 2012-09-17
I have the same problem :(

---

### Post by kiddo on 2012-09-17
Hi, don't use the ffmpeg DV encoder, it won't work. That plugin is broken, there's nothing pitivi can do about it, you should probably report a bug in gstreamer.

---

