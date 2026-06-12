---
title: "[sound] I need a very clear answer: simultaneous sound"
date: 2008-06-18
forum: Multimedia Software
---

### Post by kakyoism on 2008-06-18
I was pretty happy with pulseaudio until
I found that if some application is running sound device, such as firefox, then virtual sound on vmware wouldn't work; i saw sth saying /dev/dsp busy.

Also, there are times that no stream is detected by pulseaudio,
that's when I see nothing on the pavucontrol's output tab.

Can anyone answer a simple question for me?
Is multiple audio streams on ubuntu possible at all?
Sorry if it's a newbie question and I'd appreciate it if I can get a thorough clarification because it's been extremely frustrating to fight over
sound everyday.

---

### Post by tonyric on 2009-04-22
Same problem still exists with 8.10 and 9.04

---

### Post by psyke83 on 2009-04-23
If you're using Hardy or Intrepid, you need to make some configuration changes to your system to ensure that PulseAudio works correctly.

If you're using Jaunty, your system will be configured properly, but certain problematic applications (such as Skype) will need special configuration.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note: if an application is accessing /dev/dsp, then it is trying to use OSS output. If this is the case, you need to use the "padsp" wrapper to remap OSS output to PulseAudio (in your case, you need to use the "padsp" wrapper with the VMWare application). It's all explained in the guide.

---

