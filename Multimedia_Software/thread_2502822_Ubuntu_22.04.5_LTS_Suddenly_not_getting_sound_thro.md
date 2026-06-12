---
title: "Ubuntu 22.04.5 LTS: Suddenly not getting sound through the HDMI cable"
date: 2024-12-01
forum: Multimedia Software
---

### Post by AbleTassie on 2024-12-01
Hello everybody,

I am using Ubuntu 22.04.5 LTS, specifically Lubuntu. I have been connecting to a flat screen TV for about 1.5 years using an HDMI cable and getting good screen and sound sharing on the TV for all that time. I have had to change the settings to get sound for those 1.5 years by going to the Launcher Button then Sound & Video> PulseAudio Volume Control>Configuration>and then choosing a selection on the drop down menu of Digital Stereo (HDMI) Output. Now that procedure no longer works for some reason. I can get the picture on the TV, but not the sound. It must have something to do with this particular install, because I can get sound with the same PC/HDMI cable/TV with a USB thumb drive live boot of another earlier version of Ubuntu. And I can also get sound with the same PC/HDMI cable/TV using Windows 11 -- I can dual boot Windows on this PC.

I have looked around to see if there are any settings (other than Sound & Video> PulseAudio Volume Control>Configuration) I could change, but I have not found any. Perhaps it is from an update that has a bug.

QUESTION(S): Does anybody have any idea what I can do to fix the problem?

Thank you,

A.

---

### Post by AbleTassie on 2024-12-02
I figured it out: go to Sound & Video> PulseAudio Volume Control>Output devices. In this tab, there are two lines under Port (HDMI/Display Port).The bottom line has a slider. If the slider is slid to the right, the volume increases. If the slider is slid too far to the left, there is no volume. Somehow the slider had been slid too far to the left and the volume was zero.

Thanks,

A.

---

