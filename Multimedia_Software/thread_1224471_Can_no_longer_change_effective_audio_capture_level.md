---
title: "Can no longer change effective audio capture level"
date: 2009-07-27
forum: Multimedia Software
---

### Post by ireneshusband on 2009-07-27
Not too long ago I bought an audio headset and was able to do successful skype test calls with good quality both ways.

Today I find that the mic capture is at an extremely high level and the sound is very distorted. I just don't seem to be able to adjust the level any more.

The computer is a Thinkpad R61i with a Conexant Venice sound card. One anomaly is that the internal mic controls actually control the external mic, while the external mic is redundant. However Skype, when set to automatically control the capture level, tries to adjust the external capture level. However this did not cause a problem before, so why is it doing so now?

Kmix definitely says that it is the Venice card that it is using, while in Skype I have tried using all the sound-in devices offered (hw:intel,0 pulse etc).

If I use kmix to set the levels I get the following behaviours. If I have the capture toggle set to internal, the sound level is very high and distorted. Adjusting the capture level for the internal mic makes absolutely no difference, nor does the capture on/off button. However the mic output level slider does control the level of the sound I hear while recording. If I have the toggle set to external, I hear the same sound as through the internal mic, but muffled. It is reasonably loud, but not loud enough to be useful for capture. Again, the controls make no difference.

Has anyone a clue as to what is going on here?

---

### Post by igorzwx on 2009-07-27
Skype works well with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

and Ekiga too

---

### Post by ireneshusband on 2009-07-27
> **igorzwx said:**
> Skype works well with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

and Ekiga too

If it had never worked then that might be an option, albeit a little drastic, but the thing is that it *did* work properly last week. I know this because I did a Skype test call before I Skyped some people. This means that it did work with the currently installed kernel and also, unless one of them was replaced in an automated security update, the currently installed userspace applications. Something has changed, but I really can't figure out what it is.

---

### Post by igorzwx on 2009-07-27
Ubuntu 9.04 in dual boot and make all kind of experiments there

check if your hardware is supported by OSS4
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by ireneshusband on 2009-07-27
> **igorzwx said:**
> Ubuntu 9.04 in dual boot and make all kind of experiments there

check if your hardware is supported by OSS4
**Does OSS Support My Hardware?**

But I don't want to switch to OSS. I want to find out what has changed in the last week on my machine and to un-change it.

---

### Post by igorzwx on 2009-07-27
In this case, you should, perhaps,
read similar stories in this forum

---

### Post by igorzwx on 2009-07-27
this story, for example.
**[[*ubuntu*] Pulse Sound in *Skype Keeps Dying* - *Ubuntu* Forums]("http://ubuntuforums.org/showthread.php?t=1139404")**

10 posts - 6 authors - Last post: 2 May
[*ubuntu*] Pulse Sound in *Skype Keeps Dying* Multimedia & Video.
**ubuntu**forums.org/showthread.php?t=1139404 - [Cached]("http://209.85.129.132/search?q=cache:l84keYj6wGAJ:ubuntuforums.org/showthread.php%3Ft%3D1139404+ubuntu+skype+keep+diing&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:ubuntuforums.org/showthread.php%3Ft%3D1139404")

---

### Post by igorzwx on 2009-07-27
**[COLOR=#980101][B]or this one:**[/COLOR]
[/B]**[[*ubuntu*] *Skype* high *cpu* usage *ubuntu* 9.04 64-bit - *Ubuntu Forums*]("http://ubuntuforums.org/showthread.php?t=1127056")**

10 posts - 7 authors - Last post: 22 Apr
[*ubuntu*] *Skype* high *cpu* usage *ubuntu* 9.04 64-bit Multimedia & Video.
**ubuntuforums**.org/showthread.php?t=1127056 - [Cached]("http://209.85.135.132/search?q=cache:jRR4ICAfxI0J:ubuntuforums.org/showthread.php%3Ft%3D1127056+ubuntu+skype+cpu+forum&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:ubuntuforums.org/showthread.php%3Ft%3D1127056")
[More results from ubuntuforums.org »]("http://www.google.com/search?hl=en&q=+site:ubuntuforums.org+ubuntu+skype+cpu+forum")

---

### Post by ireneshusband on 2009-07-27
This is neither a skype issue nor a pulse issue. I have reproduced the issue using jack and qjackctl, so there can be no doubt about this. Please read my original post more carefully.

---

### Post by igorzwx on 2009-07-27
Did you have system updates?

---

### Post by ireneshusband on 2009-07-27
> **igorzwx said:**
> Did you have system updates?

No. I have double-checked in /var/log/apt but the last activity there was a few days before the last time the mic volume seemed to work properly.

---

### Post by igorzwx on 2009-07-27
There was a lot of reports about noise in recording.
They really change frequently everything, fixing this or that.
I had a lot of such problems.
Believe me, it is very reasonable to have another Ubuntu (9.04)
with OSS4.
The problem is that if you remove pulse, it would be difficult to make ALSA
working. You may try this too.
OSS4 is easy to use and it seems to be reliable.
That is why I proposed it.

---

### Post by ireneshusband on 2009-07-27
But Pulse isn't the problem. Pulse works fine, and in any case I don't use it for Skype capture anyway. OSSv4 doesn't support midi (and specifically, midi hardware) so it's completely out of the question. What I want is to get my machine back to how it was last week.

---

### Post by igorzwx on 2009-07-27
Midi is the problem. OSS4 is not an option then, of course.

"the sound is very distorted." - this is artefacts produced by pulse.
I had similar things.
You may try to change settings of Pulse.

perhaps, you may find something here:


[LIST=1]
[*]**[*PulseAudio* - *Ubuntu* Wiki]("https://wiki.ubuntu.com/PulseAudio")**

*PulseAudio* is a sound server for POSIX and Win32 systems. A sound server is basically a proxy for your sound applications. It allows you to do advanced **...**
[https://wiki](https://wiki).**ubuntu**.com/**PulseAudio** - [Cached]("http://209.85.129.132/search?q=cache:-nvQG6ZeytIJ:https://wiki.ubuntu.com/PulseAudio+ubuntu+pulse+audio&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:https://wiki.ubuntu.com/PulseAudio")
[*]**[HOWTO: *PulseAudio* Fixes & System-Wide Equalizer Support - *Ubuntu* [B]...**]("http://ubuntuforums.org/showthread.php?t=789578")[/B]

10 posts - 5 authors - Last post: 12 May 2008
The *Ubuntu* developers have done an excellent job with *PulseAudio* **...** To my surprise when *Ubuntu* adopted *PulseAudio* they moved into one of **...**
**ubuntu**forums.org/showthread.php?t=789578 - [Cached]("http://209.85.129.132/search?q=cache:WZWLgvv0SjAJ:ubuntuforums.org/showthread.php%3Ft%3D789578+ubuntu+pulse+audio&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:ubuntuforums.org/showthread.php%3Ft%3D789578")
[/LIST]

---

### Post by igorzwx on 2009-07-27
One Fedora geek told me this:
"By the way, I don't think it is a 'bug' in pulse, it is the fact that 
pulse is a sound server and runs at a specific frame rate.  It has to 
move all sound streams to that frame rate in order to play through the 
sound device.  It uses on the fly rate conversion, and this introduces 
artifacts into the sound."

---

### Post by ireneshusband on 2009-07-27
This is not a pulse problem. It even occurs when pulse is suspended, as happens automatically when I launch jack via qjackctl. The problem is an alsa problem. It is an alsa problem that must be fixable within my system as it is now without installing a whole load of other stuff, because it worked before.

---

### Post by igorzwx on 2009-07-27
search in the forum "alsa upgrade script"
Some people said it helped them

---

### Post by igorzwx on 2009-07-27
[http://www.google.com/search?q=ubuntu%20forum%20alsa%20upgrade%20script&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=ubuntu%20forum%20alsa%20upgrade%20script&ie=UTF-8&oe=UTF-8)

---

