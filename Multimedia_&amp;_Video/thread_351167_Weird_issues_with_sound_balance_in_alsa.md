---
title: "Weird issues with sound balance in alsa"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by Mocker on 2007-02-01
Howdy folks,

I'm running Dapper on an AMD Opteron dual-core, with a Soundblaster Audigy2 soundcard. 

About a month ago, I noticed that my right speaker seemed dead. After unplugging/replugging everything, I finally found the culprit: the settings in alsamixer had the right channel at a greatly reduced volume. I can't imagine why this would have been the case... I hadn't run alsamixer at all up to that point. I fixed this several times manually, assuming that at shutdown, the alsa settings would get saved. They weren't. So, I looked around and found the troubleshooting guide in thsi forum, and ran the command:

```
sudo alsactl store 0
```

I checked the file /var/lib/alsa/asound.state and it had been changed by this operation. Doing a diff between it and an old copy of the file showed that some of the settings for the right channel had been changed. OK, I thought, this should take care of it.

However, it hasn't. Apparently, the old settings are reappearing in the file somewhere between when I shut down the system and when it starts up again. I can't find anything in any logs that indicates something is writing to the asound.state file. I still have to reset the settings in alsamixer by hand everytime I restart the computer.

Anyone have any clues on what could be mucking with the sound settings?

---

### Post by wrethemyr on 2007-02-01
this may or may not be useful but:

When you run alsamixer are you running it as user or root?  I had an issue where if I ran alsamixer as user, the settings would get reset, but if I ran it as root, the settings would stick

---

### Post by Mocker on 2007-02-02
Hi,

Yes, I've been running both alsamixer and the alsactl commands as root. The file does look like it is getting saved, but as I said somewhere along the line the settings get clobbered.

---

