---
title: "Microphone Problem on EeePc"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by komputes on 2008-02-24
I was wondering if someone could help me diagnose the issue I have recently been having with my microphone. I have used it correctly before without issues, but ever since I started using my external Logitech webcam (with integrated microphone), my computer microphone has stopped working.

I have gone to the volume control panel, and made sure all preferences were selected, none of them are muted and all of them are maxed out to 100%, I'm really not sure what could have happened to cause this. Please let me know what details I can give you to help me diagnose this issue.

---

### Post by komputes on 2008-02-26
I think I figured out what happened.

I think I changed the alsa-base file because I had notes in the file that this was a custom command for the eeepc. This is what I based it on: [https://help.ubuntu.com/community/EeePC#head-d8a1fbb35ee4cebc8fc60ae58ae92e98bb78d41d](https://help.ubuntu.com/community/EeePC#head-d8a1fbb35ee4cebc8fc60ae58ae92e98bb78d41d)

Now somehow, I, or another program commented out that line. The only other audio device connected in between the time when it worked and the time when it didn't was my webcam.

sudo nano /etc/modprobe.d/alsa-base

# Append the following (to end of file)
# Custom eeepc
options snd-hda-intel model=3stack-dig

All of a sudden a new device named "IEC958" shows up in Sound Recorder and my microphone works!

I was asking around and this driver "3stack-dig" may change in hardy to "eeepc-p701", the new driver. but since I'm using Gutsy, I'll just use whats available and stable for now.

---

### Post by komputes on 2008-06-23
I had this problem once again (on the same installation) and ended up going through the instructions again. In Sound Recorder, I was unable to get ANY microphone to record and playback sound. All I got was staccato noise. I tried skype and it worked fine. Here were my alsa levels/settings. I have also attached a copy of this staccato noise picked up by "Sound Recorder" from ALL inputs.

---

