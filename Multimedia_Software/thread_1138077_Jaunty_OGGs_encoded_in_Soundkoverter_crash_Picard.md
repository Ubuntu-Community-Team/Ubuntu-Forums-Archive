---
title: "Jaunty: OGGs encoded in Soundkoverter crash Picard"
date: 2009-04-26
forum: Multimedia Software
---

### Post by shayguitarra on 2009-04-26
Since I upgraded to Jaunty on Friday, MusicBrainz Picard (v0.11) is crashing each time I try to tag ogg files created in Soundkonverter.

mp3 files are fine, as are flac. But each time I try to tag ogg files Picard just closes.

The ogg files themselves are fine and play, accept replaygain tags etc. normally. I've also checked the tags and there is no difference between these files and previously encoded ones.

I've had a look at the list of issues and regressions on the download page and can see nothing that could be causing this. Does anyone know if there have been any changes made to soundkonverter or any dependencies that might be causing this? I've tried it in SoundConverter (Gnome) and it's a bit better. It crashes on certain files but not all.:confused:

---

### Post by kostkon on 2009-04-26
You could run Picard from the terminal, then give it an Ogg file to make it to crash and check for any error messages that it may output.

---

### Post by shayguitarra on 2009-04-27
OK, I ran it from terminal just by typing in 'picard'. Hope that's right. I'm still a little dodgy with terminal commands. This is what I got:

sheamus@sheamus-desktop:~/Documents$ picard
/var/lib/python-support/python2.6/picard/webservice.py:25: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/var/lib/python-support/python2.6/picard/webservice.py:28: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha


When I added an ogg file it gave me this:
Segmentation fault

I'm assuming a deprecation warning is not a good thing and that the problem here is with python 2.6 rather than picard. Any ideas on what to do next? Or is this something I should report at launchpad as a bug? :)

---

### Post by kostkon on 2009-04-27
> **shayguitarra said:**
> OK, I ran it from terminal just by typing in 'picard'. Hope that's right. I'm still a little dodgy with terminal commands. This is what I got:

sheamus@sheamus-desktop:~/Documents$ picard
/var/lib/python-support/python2.6/picard/webservice.py:25: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/var/lib/python-support/python2.6/picard/webservice.py:28: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha


When I added an ogg file it gave me this:
Segmentation fault

I'm assuming a deprecation warning is not a good thing and that the problem here is with python 2.6 rather than picard. Any ideas on what to do next? Or is this something I should report at launchpad as a bug? :)
It seems not, this bug report [here]("https://bugs.launchpad.net/ubuntu/+source/picard/+bug/335914") suggests that Picard should work OK with Python 2.6

Since you have upgraded and didn't do a fresh install, then the thing you could do is to try reinstalling it. Even better, you could do a complete removal of it (although you'll lose any of its configuration files) and then install it again.

I don't believe that the warnings are something important although the seg fault suggests that indeed something is wrong.

---

### Post by shayguitarra on 2009-04-27
I tried uninstalling and a complete removal but no joy. I've raised a bug report on launchpad. Thanks for your help.

---

### Post by ben2talk on 2009-11-02
This never occurred for me with Jaunty - though it started in Karmic after a fresh install. We're missing something here...

I already copied all my music to my extermal drive, and imported everything Picard could handle to a separate 'Music Library' folder - and it's files from that folder that my new installation can't import. Needless to say, if they couldn't be correctly tagged, they didn't go into this folder - they went into a separate folder (inside) entitled 'Music' - so I'm not asking Picard to handle anything it hasn't already handled.

---

