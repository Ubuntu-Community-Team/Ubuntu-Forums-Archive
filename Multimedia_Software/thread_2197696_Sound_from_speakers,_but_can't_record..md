---
title: "Sound from speakers, but can't record."
date: 2014-01-05
forum: Multimedia Software
---

### Post by mikewate on 2014-01-05
I was playing with the XFCE Mixer, trying to add/remove controls, and all of a sudden I have no input to Sound Recorder (and other application that require sound input, such as Fldigi and Qsstv).  I have no idea what happened, and I am at a loss to fix this.

I was trying to find the setting in the mixer that would let me adjust  the signal level to running applications. In the process, I managed to  "kill" the audio the signal to any running applications, including  fldigi and qsstv.

The sound from my rig still comes out the computer speakers, as it always has. But that's all. There's no longer any input to any running application that takes sound input.

I ran alsamixer and turned everything on. 

I've looked through many threads here and Googled this problem. No luck. I am stuck.

I  restored the old  /home/mike/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-mixer.xml but  it didn't fix it, even after a reboot. (/home/ is the only backup I  have.)

Any suggestions?  I'm using Xubuntu 12.04.3 LTS (Precise), which is Ubuntu with the XFCE 4.8 GUI.

Any help would be greatly appreciated! Let me know what else I should post

---

### Post by mikewate on 2014-01-05
Problem at least partially solved. But I'm not sure how.

Someone on another forum suggested installing pavucontrol. I installed it and played with it, but nothing happened.

 I ran alsamixer and turned everything on. No fix.

Then I shut the computer down and powered everything off. When I rebooted just now, everything is working except Sound Recorder, which I was just using as a test. The other apps which I was really interested in worked fine. Perhaps a reboot will enable Recorder, as it has in the past.

I still would like to understand what happened and how to get Sound Recorder working right. Thanks for looking.

---

