---
title: "change-channel.py isn't working in hardy"
date: 2008-04-29
forum: Mythbuntu
---

### Post by immensewok on 2008-04-29
I did a reinstall of Mythbuntu when Hardy came out and am piecing things back together. I have to say playback looks much nicer out of the box than it did on Gutsy. The problem is, I can watch TV through a Comcast box but MythTV won't change channels. I got this [script]("https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script?highlight=(dct700)") working under Gutsy but I can't with Hardy.
I'm using a CommandIR blaster that is functioning (ie I can change the channels from the command line with "irsend send_once DCT700 ch+") but it isn't automated. I changed the owner of change-channel.py to mythtv and have restarted lirc/myth/system with no luck.
Also I don't understand Python.
Anybody else observe or fix this?

SOLVED: when copying and pasting, its important to grab "#!/usr/bin/python" file this under a lack of attention to detail.

---

