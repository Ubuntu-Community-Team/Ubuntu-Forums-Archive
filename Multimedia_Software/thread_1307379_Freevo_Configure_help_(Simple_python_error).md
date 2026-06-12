---
title: "Freevo Configure help (Simple python error)"
date: 2009-10-31
forum: Multimedia Software
---

### Post by hansoffate on 2009-10-31
Since this seems to be a simple python error, this may be better off posted in the programming forum?

Anyways, my weekend project is to try out freevo instead of mythtv, since mythtv just doesn't seem to work all the time (audio/video sync delay, randomly dropping scheduled recordings, etc).  I have compiled my own firewire changer script to record tv from my STB following this ([http://www.dseifert.net/code/dct6200/](http://www.dseifert.net/code/dct6200/)) tutorial.  I was able to compile the source and get the channel changing working.  I moved the python wrapper script to the place indicated in the instructions (/usr/lib/python2.5/site-packages/freevo/tv/plugins); however, I have a feeling ubuntu doesn't use this directory but I'd like someone to confirm this. 

The reason why I think this is because when I launch freevo and try to change to a channel on my EPG, it crashes.  I checked the logs, and there only seems to be two relevant problems.  Freevo can't find the wrapper script I played in the folder (I made sure it was executable), and there is an audio issue which I no clue what it means.

Does anyone have any suggestions?

Thanks,
-Hans

```
failed to load plugin tv.dct6200wrapper
start 'freevo plugins -l' to get a list of plugins
Traceback (most recent call last):
  File "/usr/share/pyshared/freevo/plugin.py", line 557, in __load_plugin__
    p = eval(object)()
  File "<string>", line 1, in <module>
AttributeError: 'module' object has no attribute 'dct6200wrapper'
2009-10-30 23:23:49,064 WARNING  xml_skin.py (202): can't find image ""

Freevo 1.8.1 ready
2009-10-30 23:23:49,128 INFO     create thread notifier pipe
2009-10-30 23:23:51,411 INFO     record_client.py (98): ('localhost', 18001) is up
2009-10-30 23:23:53,003 INFO     epg_xmltv.py (110): XMLTV, got cached guide (version 6).
2009-10-30 23:23:55,446 WARNING  v4l2.py (768): control "Audio Encoding Layer" does not exists
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/freevo/main.py", line 297, in eventhandler
    app.eventhandler(event)
  File "/usr/share/pyshared/freevo/menu.py", line 764, in eventhandler
    if not isinstance(menu, Menu) and menu.eventhandler(event):
  File "/usr/share/pyshared/freevo/util/benchmark.py", line 68, in origfunc
    func(*args, **kwargs)
  File "/usr/share/pyshared/freevo/tv/tvguide.py", line 234, in eventhandler
    pi.actions()[0][0](menuw=self.menuw)
  File "/usr/share/pyshared/freevo/tv/programitem.py", line 172, in play
    self.parent.player('tv', self.prog.channel_id)
  File "/usr/share/pyshared/freevo/tv/tvmenu.py", line 82, in start_tv
    p.Play(mode, tuner_id)
  File "/usr/share/pyshared/freevo/tv/plugins/mplayer.py", line 100, in Play
    ivtv_dev.init_settings()
  File "/usr/share/pyshared/freevo/tv/ivtv.py", line 360, in init_settings
    codec = self.getCodecInfo()
  File "/usr/share/pyshared/freevo/tv/ivtv.py", line 144, in getCodecInfo
    audio_bitmask |= (tv.v4l2.Videodev.getcontrol(self, 'Audio Encoding Layer') << 6)
TypeError: unsupported operand type(s) for <<: 'NoneType' and 'int'

```

---

