---
title: "sound error causes program to close"
date: 2011-08-30
forum: Multimedia Software
---

### Post by asarrouy on 2011-08-30
Sorry if this is in the wrong place, but I'm extremely new here. I'm trying to run brainworkshop in Ubuntu 10.04 on my Toshiba NB305 (its a netbook). The program runs fine for a little while, and then suddenly closes. The problem seems to be related to the sound so I posted it here. Here's the error:

 ```
user@user-laptop:~/brainworkshop$ python brainworkshop.pyw 
 ALSA lib pcm_pulse.c:732:(pulse_prepare) PulseAudio: Unable to create stream: Too large 
  
 Traceback (most recent call last): 
   File "brainworkshop.pyw", line 4352, in <module> 
     pyglet.app.run() 
   File "/home/user/brainworkshop/pyglet/app/__init__.py", line 264, in run 
     EventLoop().run() 
   File "/home/user/brainworkshop/pyglet/app/xlib.py", line 93, in run 
     sleep_time = self.idle() 
   File "/home/user/brainworkshop/pyglet/app/__init__.py", line 187, in idle 
     dt = clock.tick(True) 
   File "/home/user/brainworkshop/pyglet/clock.py", line 700, in tick 
     return _default.tick(poll) 
   File "/home/user/brainworkshop/pyglet/clock.py", line 303, in tick 
     item.func(ts - item.last_ts, *item.args, **item.kwargs) 
   File "brainworkshop.pyw", line 4236, in update 
     else: generate_stimulus() 
   File "brainworkshop.pyw", line 3858, in generate_stimulus 
     player.queue(mode.soundlist[mode.current_stim['audio']-1]) 
   File "/home/user/brainworkshop/pyglet/media/__init__.py", line 797, in queue 
     self._begin_source() 
   File "/home/user/brainworkshop/pyglet/media/__init__.py", line 893, in _begin_source 
     self._fill_audio() 
   File "/home/user/brainworkshop/pyglet/media/__init__.py", line 724, in _fill_audio 
     self._audio.write(audio_data) 
   File "/home/user/brainworkshop/pyglet/media/drivers/alsa/__init__.py", line 155, in write 
     raise ALSAException(asound.snd_strerror(samples_out)) 
 pyglet.media.drivers.alsa.ALSAException: File descriptor in bad state 
```I'm new to linux and I was never an expert with windows, so I have no idea what to make of this. Any help at all would be much appreciated.

---

### Post by asarrouy on 2011-08-31
Boy do I feel foolish! I missed the note beneath the installation instructions recommending the installation of the python-opengl package in case of sound trouble. Problem solved!

---

