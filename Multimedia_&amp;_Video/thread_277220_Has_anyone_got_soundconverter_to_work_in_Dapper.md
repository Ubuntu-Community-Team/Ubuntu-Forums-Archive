---
title: "Has anyone got soundconverter to work in Dapper?"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by rthompson0926 on 2006-10-14
I have tried using soundconveter 0.8.3 from packages to convert a .mp3 file to a .ogg file. I keep getting the following message :

/usr/bin/soundconverter-0.8.3 -b audio_01.mp3
Traceback (most recent call last):
  File "/usr/bin/soundconverter-0.8.3", line 1935, in ?
    main()
  File "/usr/bin/soundconverter-0.8.3", line 1931, in main
    cli_convert_main(args)
  File "/usr/bin/soundconverter-0.8.3", line 1839, in cli_convert_main
    while queue.do_work():
  File "/usr/bin/soundconverter-0.8.3", line 389, in do_work
    if self.paused:
AttributeError: TaskQueue instance has no attribute 'paused'

I downloaded soundconverter 0.9.1 from 

[http://developer.berlios.de/project/showfiles.php?group_id=3213](http://developer.berlios.de/project/showfiles.php?group_id=3213)

and I get the following message :

soundconverter -b audio_01.mp3
SoundConverter 0.9.1
  using Gstreamer version: 0.10.6, Python binding version: 0.10.4
  using gnomevfssrc
audio_01.mp3: -error:GStreamer encountered a general stream error. (audio_01.mp3)
Queue done in 0s

and an empty .ogg file is generated.

Has anyone got soundconverter to work in Dapper?

---

### Post by johnbl on 2006-11-18
Am attempting to get 0.9.3 ver working but without any luck.
install ' seems ' to have worked however soundconverter is not available from within any menu I can find (a) and (b) when I fire it up from a command line it appears to start a conversion and freezes. Only out put is a 0 length file - properly titled but containing zip!

Did you have any more luck?

---

