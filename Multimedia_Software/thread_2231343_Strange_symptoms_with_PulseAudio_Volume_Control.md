---
title: "Strange symptoms with PulseAudio Volume Control"
date: 2014-06-25
forum: Multimedia Software
---

### Post by cscj01 on 2014-06-25
I have an 87 year old Ubuntu Precise user with a strange problem.  Here is what is happening.  A few days ago, he could use PulseAudio Volume Control to set Audacity to record "What You Hear" or to record from an external source via Line In.  Now he can't.  When he launches PulseAudio Volume Control with an input active on Line In and goes to the Input Devices tab and sets Show to All video devices, the Line In volume indicator initially shows a signal.  This lasts for approximately 2 seconds.  Then the volume indicator becomes static at the last volume before it stopped being active.  If he launches Audacity and starts recording and sets the device on the Recording tab to the Line In device, he gets a signal indication that varies correctly on both the Recording tab and the Input Devices tab.  However, Audacity shows no signal at all and records nothing.  He can still record "What You Hear" by setting the recording device to Monitor.

Does anyone have any ideas here?

---

### Post by lidex on 2014-07-01
Check troubleshooting section here:
[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

And a lot of info here:
[https://wiki.archlinux.org/index.php/PulseAudio]("https://wiki.archlinux.org/index.php/PulseAudio")

---

### Post by cscj01 on 2014-07-22
Well, we solved this issue by finding the System Volume settings were set to Mic In as opposed to Line In.  So although the PulseAudio Volume Control settings were correct, the System Volume settings were incorrect.

---

