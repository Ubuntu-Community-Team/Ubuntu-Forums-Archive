---
title: "Ubuntu 15.04 Audio Glitches"
date: 2015-10-01
forum: Multimedia Software
---

### Post by tehtotalpwnage on 2015-10-01
Ever since I've upgraded to Ubuntu 15.04, my audio problems have gotten progressively worse. On applications like Audacity and LMMS (audio editors), playing through the track causes it to speed through the track while playing a ridiculously annoying glitching sound. At the same time, working with video editing applications like OpenShot and Kdenlive is a pain in the butt since the audio starts in the wrong place when I use the seek. Sometimes when starting the track in either application, the pitch of the song is messed up too. Does anybody know what is the cause of this and how to fix it? I've already tried resetting the PulseAudio configs and downloading the ALSA Daily Intel HDA driver.

Relevant Information:
[LIST]
[*]Running Ubuntu 15.04 Vivid Vervet
[*]Using an integrated Intel HDA ALC1150 chip for onboard audio
[*]Speakers are connected via analog Line Out
[/LIST]

---

### Post by Yellow Pasque on 2015-10-02
Another fix to try: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

If it doesn't help, undo it and get detailed information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

