---
title: "JACK/Guitarix question"
date: 2014-03-26
forum: Multimedia Software
---

### Post by Sworkma2 on 2014-03-26
Installed JACK and guitarix and I'm trying to run my guitar through a rocksmith usb cable to use my laptop as an amp.

I received an error code in guitarix

```
  [COLOR=#999999]20:22:50.126 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:22:50.138 Statistics reset.[/COLOR]
 [COLOR=#cccc99]20:22:50.362 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:22:50.564 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]20:22:52.061 D-BUS: JACK server is starting...[/COLOR]
 Wed Mar 26 20:22:50 2014: Starting jack server...
 Wed Mar 26 20:22:50 2014: JACK server starting in realtime mode with priority 10
 Wed Mar 26 20:22:51 2014: control device hw:0
 Wed Mar 26 20:22:51 2014: control device hw:0
 Wed Mar 26 20:22:51 2014: Acquired audio card Audio0
 Wed Mar 26 20:22:51 2014: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Wed Mar 26 20:22:51 2014: control device hw:0
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]20:22:52.219 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]20:22:52.497 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Wed Mar 26 20:22:51 2014: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Wed Mar 26 20:22:51 2014: ALSA: final selected sample format for capture: 32bit integer little-endian
 Wed Mar 26 20:22:51 2014: ALSA: use 2 periods for capture
 Wed Mar 26 20:22:51 2014: ALSA: final selected sample format for playback: 32bit integer little-endian
 Wed Mar 26 20:22:51 2014: ALSA: use 2 periods for playback
 Wed Mar 26 20:22:52 2014: graph reorder: new port 'system:capture_1'
 Wed Mar 26 20:22:52 2014: New client 'system' with PID 0
 Wed Mar 26 20:22:52 2014: graph reorder: new port 'system:capture_2'
 Wed Mar 26 20:22:52 2014: graph reorder: new port 'system:playback_1'
 Wed Mar 26 20:22:52 2014: graph reorder: new port 'system:playback_2'
 Wed Mar 26 20:22:52 2014: New client 'PulseAudio JACK Sink' with PID 1768
 Wed Mar 26 20:22:52 2014: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
 Wed Mar 26 20:22:52 2014: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
 Wed Mar 26 20:22:52 2014: New client 'PulseAudio JACK Source' with PID 1768
 Wed Mar 26 20:22:52 2014: Saving settings to "/home/owner/.config/jack/conf.xml" ...
 Wed Mar 26 20:22:52 2014: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
 Wed Mar 26 20:22:52 2014: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
 Wed Mar 26 20:22:54 2014: New client 'gx_head_amp' with PID 3228
 Wed Mar 26 20:22:54 2014: New client 'gx_head_fx' with PID 3228
 [COLOR=#9999cc]20:22:54.810 JACK connection change.[/COLOR]
 [COLOR=#999933]20:22:54.824 Server configuration saved to "/home/owner/.jackdrc".[/COLOR]
 [COLOR=#999999]20:22:54.827 Statistics reset.[/COLOR]
 [COLOR=#999999]20:22:54.873 Client activated.[/COLOR]
 [COLOR=#cc9966]20:22:54.966 JACK connection graph change.[/COLOR]
 Wed Mar 26 20:22:54 2014: Connecting 'gx_head_amp:out_0' to 'gx_head_fx:in_0'
 Wed Mar 26 20:22:54 2014: New client 'qjackctl' with PID 3389

```

Any help would be greatly appreciated

---

### Post by jejeman on 2014-03-27
Did you enabled RT priority?
Are you in Audio group?
Have you install lowlatency kernel?
I gues this Rocksmith cable is USB audio card, so did you choose rigth card in JACK?

What is your problem?

---

