---
title: "qjackctl shows an error that cause guitarix not to work"
date: 2013-12-09
forum: Multimedia Software
---

### Post by jhay2 on 2013-12-09
when i first install this two program , qjackctl and guitarix . they were actually worked , but all of the sudden the qjackctl is showing now an error after i opened guitarix and audaucity at the same time .

and now both qjackctl and guitarix are not working 


heres the log when i start qjackctl
> [COLOR=#999999]19:21:31.150 Patchbay deactivated.[/COLOR][COLOR=#999999]19:21:31.219 Statistics reset.[/COLOR]
[COLOR=#cccc99]19:21:31.966 ALSA connection change.[/COLOR]
[COLOR=#999999]19:21:33.043 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]19:21:33.130 ALSA connection graph change.[/COLOR]
[COLOR=#999999]19:21:41.815 D-BUS: JACK server is starting...[/COLOR]
Mon Dec  9 19:21:40 2013: Starting jack server...
Mon Dec  9 19:21:41 2013: JACK server starting in non-realtime mode
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#999999]19:21:41.850 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
Mon Dec  9 19:21:41 2013: Acquired audio card Audio0
Mon Dec  9 19:21:41 2013: creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
Mon Dec  9 19:21:41 2013: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
Mon Dec  9 19:21:41 2013: ALSA: final selected sample format for capture: 16bit little-endian
Mon Dec  9 19:21:41 2013: ALSA: use 3 periods for capture
Mon Dec  9 19:21:41 2013: ALSA: final selected sample format for playback: 16bit little-endian
Mon Dec  9 19:21:41 2013: ALSA: use 3 periods for playback
Mon Dec  9 19:21:41 2013: graph reorder: new port 'system:capture_1'
Mon Dec  9 19:21:41 2013: New client 'system' with PID 0
Mon Dec  9 19:21:41 2013: graph reorder: new port 'system:capture_2'
Mon Dec  9 19:21:41 2013: graph reorder: new port 'system:playback_1'
Mon Dec  9 19:21:41 2013: graph reorder: new port 'system:playback_2'
Mon Dec  9 19:21:42 2013: Saving settings to "/home/jhay/.config/jack/conf.xml" ...
Mon Dec  9 19:21:42 2013: New client 'PulseAudio JACK Sink' with PID 3170
Mon Dec  9 19:21:42 2013: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Mon Dec  9 19:21:42 2013: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Mon Dec  9 19:21:42 2013: New client 'PulseAudio JACK Source' with PID 3170
Mon Dec  9 19:21:42 2013: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Mon Dec  9 19:21:42 2013: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
[COLOR=#9999cc]19:21:44.318 JACK connection change.[/COLOR]
[COLOR=#999933]19:21:44.341 Server configuration saved to "/home/jhay/.jackdrc".[/COLOR]
[COLOR=#999999]19:21:44.343 Statistics reset.[/COLOR]
[COLOR=#999999]19:21:44.367 Client activated.[/COLOR]
[COLOR=#cc9966]19:21:44.430 JACK connection graph change.[/COLOR]
Mon Dec  9 19:21:44 2013: New client 'qjackctl' with PID 24060



hope someone help me :(

---

### Post by jhay2 on 2013-12-09
heres the log when i start guitarix

> 
[COLOR=#cc9966]12:43:55.849 JACK connection graph change.[/COLOR]
[COLOR=#cc9966]12:43:55.956 JACK connection graph change.[/COLOR]
Tue Dec 10 12:43:55 2013: New client 'gx_head_amp' with PID 4924
Tue Dec 10 12:43:55 2013: New client 'gx_head_fx' with PID 4924
[COLOR=#9999cc]12:43:56.116 JACK connection change.[/COLOR]
[COLOR=#cc9966]12:43:56.443 JACK connection graph change.[/COLOR]
[COLOR=#cc9966]12:43:56.569 JACK connection graph change.[/COLOR]
Tue Dec 10 12:43:56 2013: Connecting 'system:capture_1' to 'gx_head_amp:in_0'
Tue Dec 10 12:43:56 2013: Connecting 'gx_head_fx:out_0' to 'system:playback_1'
Tue Dec 10 12:43:56 2013: Connecting 'gx_head_fx:out_1' to 'system:playback_2'
Tue Dec 10 12:43:56 2013: Connecting 'gx_head_amp:out_0' to 'gx_head_fx:in_0'
[COLOR=#cc66cc]12:44:01.772 XRUN callback (1).[/COLOR]
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackEngine::XRun: client = gx_head_amp was not finished, state = Triggered[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackEngine::XRun: client = gx_head_fx was not finished, state = Triggered[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackEngine::XRun: client = gx_head_amp was not finished, state = Triggered[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackEngine::XRun: client = gx_head_fx was not finished, state = Triggered[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
Tue Dec 10 12:44:01 2013: [1m[31mERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error[0m
[COLOR=#cc99cc]12:44:05.191 XRUN callback (3 skipped).[/COLOR]
[COLOR=#cc9966]12:44:10.318 JACK connection graph change.[/COLOR]
[COLOR=#9999cc]12:44:10.416 JACK connection change.

[/COLOR]

---

