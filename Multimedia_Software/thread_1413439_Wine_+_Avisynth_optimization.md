---
title: "Wine + Avisynth optimization?"
date: 2010-02-22
forum: Multimedia Software
---

### Post by Kenjitamura on 2010-02-22
Just came back to ubuntu after losing my own computer system and getting a new one, ubuntu is my flavor of choice.  However, I became pretty addicted to using avisynth for video encoding back in windows, a huge variety of plugins Im afraid I don't think any native linux encoder offers.  Of course if anyone could point me to a denoiser that works the same as fft3dfilter + mvtools combo for motion compensated temporal-spatial denoising I might reconsider that statement. 

I have avisynth up and running through wine just fine the problem is the speed.  Im running a script I've tested through windows vista and where as it used to get 1.8 fps its now running at .76 fps.  I thought there'd be a performance hit but this seems a little unreasonable.  I'm piping the avs script through avsproxy with wine to avidemux and encoding to x264.  I've also tested it with xvid to rule out the x264 build as the problem and to further test it I ran the script through avs2yuv with wine directly to the x264 encoder and was still getting around .7 fps.  I did notice that when I ran it directly to the x264 encoder it put up the message the only instruction sets its using are MMX2 and SSE2Slow if thats of any consequence.

The only difference in the script really between vista and ubuntu is instead of using DirectShowSource Im loading with FFMPEG2, I've read that causes a slow down in comparison as well.  Is there anything I can do to run avisynth through ubuntu and get comparable speeds to windows or am I going to have to dualboot and rely on windows again?

Edit: I forgot to mention I removed all the plugin DLL's from avisynth's autoload folder and am manually loading them from a different folder into the script.  I had heard since wine evaluates the dll's at a slower speed that having the default plugins folder loaded could cause a slowdown.  No difference though.

---

