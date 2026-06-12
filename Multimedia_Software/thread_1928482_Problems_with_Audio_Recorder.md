---
title: "Problems with Audio Recorder"
date: 2012-02-20
forum: Multimedia Software
---

### Post by TedinOz on 2012-02-20
Hi everyone. If anyone is using Audio Recorder 

[http://www.upubuntu.com/2011/10/record-streaming-audio-from-internet.html](http://www.upubuntu.com/2011/10/record-streaming-audio-from-internet.html)

I am hoping they might be able to point me in the right direction to solve my problem. I have had this application installed on Natty (worked fine) and then Oneiric where it has also worked faultlessly until about a week ago when it just ceased to start up. I have checked the stated dependencies and they all seem to be installed. When I select it from Unity dash, just nothing happens, no error message, nothing. I tried to start it in the Terminal and got this message...

```
$ audio-recorder
GLib (gthread-posix.c): Unexpected error from C library during 'Invalid argument': pthread_cond_timedwait.  Aborting.
Aborted

```

Is anyone able to explain what this means or perhaps direct me to the appropriate log file to help locate a solution?

---

### Post by TedinOz on 2012-02-20
A bump for this...anyone?

---

### Post by moma on 2012-03-31
Hello,

Can you start dconf-editor (or gconf-editor in older Ubuntu versions) and browse to "apps" -> "audio-recorder".
$ [COLOR="DarkGreen"]dconf-editor[/COLOR]

Then uncheck the "timer-active" variable. Take also copy of your "timer-text" value and copy&paste it here.

You may need to install dconf-tools first:
[COLOR="DarkGreen"]sudo apt-get install dconf-tools[/COLOR]

Please send error reports to 
[https://bugs.launchpad.net/audio-recorder](https://bugs.launchpad.net/audio-recorder)

---

### Post by TedinOz on 2012-03-31
> **moma said:**
> Hello,

Can you start dconf-editor (or gconf-editor in older Ubuntu versions) and browse to "apps" -> "audio-recorder".
$ [COLOR="DarkGreen"]dconf-editor[/COLOR]

Then uncheck the "timer-active" variable. Take also copy of your "timer-text" value and copy&paste it here.

You may need to install dconf-tools first:
[COLOR="DarkGreen"]sudo apt-get install dconf-tools[/COLOR]

Please send error reports to 
[https://bugs.launchpad.net/audio-recorder](https://bugs.launchpad.net/audio-recorder)

Thank you! Works again! Great app btw.

---

