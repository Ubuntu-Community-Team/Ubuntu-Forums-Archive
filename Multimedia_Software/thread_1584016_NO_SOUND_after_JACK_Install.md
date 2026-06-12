---
title: "NO SOUND after JACK Install"
date: 2010-09-28
forum: Multimedia Software
---

### Post by Jakeotron on 2010-09-28
Ok, so I am way new to this.  I am trying to set my computer up to do sound sequencing.  I want to plug my MIDI keyboard in and record with a sequencer.  Running 10.04, was following a tutorial on installing JACK, and my audio stopped working.

Since then, I've gone through all guides I can find, some advising an upgrade of ALSA, some saying to use OCC.  I've tried both, but nothing seems to work.

I suspect it may have something to do with libjack0.  I could not install jackd because it claimed libjack0 to be the wrong version, and for some reason I couldn't upgrade.  So I uninstalled libjack0, then installed jackd, which automatically included the version of libjack0 it wanted.  After that, I could get the JACK server running, but the computer had no sound.

I will post whatever logs or information necessary to troubleshoot, but I don't know exactly how or what to post.  If you need logs, please tell me how to get them.

Any help is GREATLY appreciated.  I didn't realize how much it sucks to have no sound.

---

### Post by cchhrriiss121212 on 2010-09-28
I don't know what guides you looked at, but upgrading ALSA or switching to OSS is not necessary or advisable in this situation. You might be better off just doing a fresh install, unless you kept a record of exactly what you have done then this will be hard to troubleshoot. 

You should not have any issues installing jack as long as you do so from either synaptic or the software center, do not start compiling things yourself, even if you think you need the newest version.

---

### Post by Jakeotron on 2010-09-28
First I followed this guide for an ALSA update script:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Failing that, I went to a guide on installing OSS:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Followed by these instructions for post-install:
[http://ubuntuforums.org/showpost.php?p=9872284&postcount=4](http://ubuntuforums.org/showpost.php?p=9872284&postcount=4)

I'm not totally against a fresh install, but would like to troubleshoot first, if anyone's got any ideas.

---

