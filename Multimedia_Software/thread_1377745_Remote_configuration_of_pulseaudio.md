---
title: "Remote configuration of pulseaudio"
date: 2010-01-10
forum: Multimedia Software
---

### Post by pstickar on 2010-01-10
I'm trying to get pulseaudio to work (Ubuntu 9.10, following Part-A of the Howto in [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) on a remote machine and I have two questions.

Is it possible to remotely config pulseaudio in 9.10? (that is, a remote way of using pavucontrol). I tried "ssh -X me@remote_server pavucontrol" but it did not work ("Connection failed: Connection refused").

After each change in pavucontrol and/or alsamixer, do I have to logout/login to "hear" the change?

A little background, just in case:

I'm trying to fix the audio on a remote machine (in my parents home, some 13000 Km away). Sound was working with Ubuntu-8.10, but stop working with the automatic upgrade a few days ago.
I have the feeling that just selecting the right choices in pavucontrol and in System/Preferences/Audio will do the trick.
I tried to follow the Howto, ssh'ing the commands, asking the clicks on "pavucontrol" over the phone, but it turns out to be pretty messy (my parents have good humor, their Linux skills are modest, and they are asking if Linux is actually a good choice ... you get the picture), and it does not produce any sound at all. Only the telephone company is getting something out of this.

Any tip will be highly appretiated. Thanks!

---

