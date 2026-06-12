---
title: "phonon/xine and pulseaudio problem"
date: 2010-10-11
forum: Multimedia Software
---

### Post by dillinger417 on 2010-10-11
In an effort to troubleshoot a sound issue, I upgraded to ALSA 1.0.23 and although the upgrade was successful and I have 7.1 pulseaudio sound working, Phonon/Xine greys out the option to use pulseaudio as output bc it thinks it not available.  Rest assured PulseAudio is running, Audacious and the ALSA and Pulseaudio tests all work fine.

I get the sense that this is a timing issue, that Phonon/Xine is checking for available sources before PulseAudio fires off, but I am not sure how to check this, or if this is the issue.

I am not very familiar w/ Ubuntu start-up other than I know that /etc/init.d/pulseaudio exists and is likely fired off in etc/init.d/rc somewhere, but there is no such entry for /etc/init.d/phonon|xine

Can anyone suggest a fix, or a troubleshooting method, or verify that this is a known bug?  Google searches have been not been that helpful so far.

I'm using Ubuntu 10.04x64

TIA,
d417

---

### Post by Yellow Pasque on 2010-10-11
[http://ubuntuforums.org/showpost.php?p=9926862&postcount=1117](http://ubuntuforums.org/showpost.php?p=9926862&postcount=1117)

---

