---
title: "pulseaudio : how to redirect to internal mic"
date: 2019-10-04
forum: Multimedia Software
---

### Post by mauricebis on 2019-10-04
Hello,

I'd like to use the speech to text facility of Google Docs with Chrome on line. It works when dictating to the phone but I'd like to extend that possibility to the playback of a file simulating the mic input. I'm on Ubuntu 18.04.
I successfully loaded the null-sink module as suggested elsewhere:
                   [FONT=courier new]pactl load-module module-null-sink sink_name=virtmic[/FONT]
Although I'm not really sure I understand the effect of this. Now, I guess a command to move sources/sinks is necessary:
                  ?? [FONT=courier new]pacmd move-source-output virtmic analog-input-internal-mic ??[/FONT]
I tried to play around with this but with no success, Chrome saying the mic is not working.

Any help with this much appreciated.

---

### Post by cruzer001 on 2019-10-04
I have not used null-sink, but have used hdajackretask to do similar task.  It has a GUI for ease of use.

[https://askubuntu.com/questions/225017/how-do-i-change-which-audio-jacks-are-used-for-input-and-output](https://askubuntu.com/questions/225017/how-do-i-change-which-audio-jacks-are-used-for-input-and-output)

Just wanted to pass that on.

---

### Post by mauricebis on 2019-10-06
Thanks for that. I installed it and I get the attached screen copy. Now, I'm a bit of a newbie at sound management and don't know how to configure this to achieve the goal I described in my initial message. Steps description would be welcome.

---

