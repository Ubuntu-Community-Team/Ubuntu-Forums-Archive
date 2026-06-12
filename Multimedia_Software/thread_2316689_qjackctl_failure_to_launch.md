---
title: "qjackctl failure to launch"
date: 2016-03-10
forum: Multimedia Software
---

### Post by cmcglath on 2016-03-10
I am having trouble with qjackctl working properly. There is much information about how to use jack, but not much on how to get to that point. I have searched threads & the internet, but can't find any information on this topic. At present once I start jack no other audio will work until i stop it. i don't know where to go from here. If there is a website or another forum, could someone please point me in the right direction. I don't even know where to begin. 

This is the output I am receiving now.

 [COLOR=#999999]22:38:16.363 Patchbay activated.[/COLOR]
 [COLOR=#999999]22:38:16.469 Statistics reset.[/COLOR]
 [COLOR=#cccc99]22:38:16.512 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:38:16.814 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#99cc66]22:38:17.021 ALSA active patchbay scan...[/COLOR]
 [COLOR=#ff0000]22:38:19.590 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Sat Mar 12 22:38:19 2016: Starting jack server...
 Sat Mar 12 22:38:19 2016: JACK server starting in realtime mode with priority 10
 Sat Mar 12 22:38:19 2016: Acquired audio card Audio0
 Sat Mar 12 22:38:19 2016: creating alsa driver ... hw:0|hw:0|256|2|48000|0|0|nomon|swmeter|-|32bit
 Sat Mar 12 22:38:19 2016: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Sat Mar 12 22:38:19 2016: ERROR: Cannot initialize driver
 Sat Mar 12 22:38:19 2016: ERROR: JackServer::Open failed with -1
 Sat Mar 12 22:38:19 2016: ERROR: Failed to open server
 Sat Mar 12 22:38:21 2016: Saving settings to "/home/charles/.config/jack/conf.xml" ...

---

### Post by QIII on 2016-03-12
Bump

---

### Post by marseille2 on 2016-03-15
[FONT=arial]Let's see your cards. Please post the output of:

```
$ cat /proc/asound/cards
```

[/FONT][COLOR=#111111][FONT=Consolas][FONT=arial]Especially if you're using Pulseaudio (PA), check out this [thread]("http://ubuntuforums.org/showthread.php?t=2269785&p=13248150#post13248150") for more on trouble-shooting. It's also good to see which files and directories to delete, just in case a reset is needed. (Note: PA's modules for jack-sink and jack-source have to be installed if you want to use PA and Jackd at the same time. If they're not, and you are using PA, you have to suspend PA before starting Jack.)


[/FONT]
[/FONT][/COLOR]

---

