---
title: "Can hear myself from mic, cant record"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by h2z on 2007-11-04
[color="red"]EDIT 2: Partially solved but, my problem now is that I cant seem to make capture (from the mic) work with AOSS :@[/color]



Sound works great and with multiple sound output programs (Rythmbox, XMMS and totem all working at same time, all 3 are able to play sounds simultaneously). I have my mic enabled and all options are on (capture, boost, front input) and I can hear myself on both the speakers and the headset I use (at the same time; speakers are connected to the back panel, headset+mic on the front panel) when speaking. When I run the sound input test from the "Multimedia Systems Selector" it sounds ok (abit choppy but still works) with the option being set to "ALSA". Setting it to "OSS" makes the output way too fast and it makes me sound like a chipmonk lol 
When trying to start Sound Recorder (application->sound & video) I get the following error:

```

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

```

Also when starting TeamSpeak (both the normal way and with "aoss") it displays my mic as being muted but I can still hear myself when speaking :confused:

I have tried some of the solutions on the forums but nothing seems to work.


Output of aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Relevant section of lspci
```

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```



EDIT: Eventho the test with OSS sounds bad and too fast, it seems to work just fine with TeamSpeak and the sounds recorder which refuses to run when the input is set to ALSA...

---

### Post by akwatve on 2008-04-08
Even I was unable to record from alsa. I switched to OSS and everything is working fine. I didn't have to do anything. You may consider trying it. The only issue is it is not in Ubuntu repo. I had to download deb file from its website ([http://www.4front-tech.com/oss.html](http://www.4front-tech.com/oss.html)) and install it using dpkg -i <deb file>

---

