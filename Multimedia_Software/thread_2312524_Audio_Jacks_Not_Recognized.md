---
title: "Audio Jacks Not Recognized"
date: 2016-02-05
forum: Multimedia Software
---

### Post by adoyle1215 on 2016-02-05
[FONT=georgia]Hello Everyone,

I'm unable to get headphones to work when using Ubuntu 14.04 LTS.  Notably I can use my monitor's built in speakers (connected to the tower via HDMI).  Pulse audio shows that my only output options are via HDMI.

As a result of Googling around, I've tried:[/FONT]
[LIST]
[*][FONT=georgia][Steps 1-3]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") of the Sound Troubleshooting Procedure (after that, I began to worry that this isn't designed for my problem)
[/FONT]
[*][FONT=georgia]Modifying /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf as shown [here]("http://askubuntu.com/a/147603")
[/FONT]
[/LIST]
[FONT=georgia]
I've seen some people advocating changing the contents of /etc/modprobe.d/alsa-base.conf , but I can't seem to figure out the pattern for their suggestions

Also, a lot of the resources I'm sorting through are a bit dated, so some things may have been updated.  However, if I type 'alsamixer' into the terminal I get "cannot open mixer: No such file or directory"

[Alsa diagnostic output]("http://www.alsa-project.org/db/?f=0df79b89e6b0af692afb77a0c1ca902d8e8c2847") for the system.[/FONT]

Does anyone have any suggestions for how I might be able to convince my computer to play nice with headphones? :(

-Andrew

PS - I'm comfortable navigating the terminal from experiences with other systems in bash.  However, I'm completely new to Ubuntu, so I don't know where things are located.

---

### Post by adoyle1215 on 2016-02-08
Hey Everyone,

This was my first post to this forum, and I'm not entirely sure that I set myself up to succeed.  Is there some additional information I should provide, or some other general resource I could look over?

-Andrew

---

### Post by tea for one on 2016-02-08
> **adoyle1215 said:**
> [FONT=georgia]Hello Everyone,

I'm unable to get headphones to work when using Ubuntu 14.04 LTS.  Notably I can use my monitor's built in speakers (connected to the tower via HDMI).  Pulse audio shows that my only output options are via HDMI.



Sound problems are tricky coves as you can see from the Sticky at the top of this forum.

Anyway, you have sound via HDMI to the speakers on your monitor, do you have a headphone jack on your monitor?

If you do, does it work with your headphones?

Secondly, have you installed pavucontrol (pulse audio volume controller), because this will allow you to select various applications and outputs?

---

### Post by adoyle1215 on 2016-02-08
Heya,At least as a short-term solution, plugging the headphones into an audio jack on the monitor (which had working speakers via HDMI) appears to work.Is pauvcontrol different than the Pulse app that comes installed with Ubuntu 14.04?-Andrew

---

### Post by tea for one on 2016-02-09
Good morning

If I remember correctly, pavucontrol is not included in a normal Ubuntu installation. I installed it separately to learn how to pair a bluetooth speaker.

Now, here is another little experiment.

As far as I understand, HDMI connections transmit both sound and video from your PC to the monitor. I'm not sure if the sound can be separated from the video using HDMI.

I hope that your monitor may include separate inputs for video (only) such as DVI or VGA.

If you have other cables, try the video input via VGA or DVI and the sound via the green jack on your PC to the _sound-in_ jack on your monitor.

Your monitor will probably have two sound jacks - input from PC (or other external device) and output via headphones which you have used successfully.

Best wishes

---

