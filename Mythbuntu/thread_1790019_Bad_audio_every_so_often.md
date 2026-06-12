---
title: "Bad audio every so often"
date: 2011-06-24
forum: Mythbuntu
---

### Post by azmyth on 2011-06-24
Every so often I get a recording with crummy audio. I'm using
pulseaudio and a PVR 150 also using mythubuntu 10.04 64 bit just using
the motherboards audio snd_hda_intel I think. I'm also using a STB and
the STB is connected to the PVR 150 through S-video. Only happens
about 1 in 10 recordings. Anyone know what it could be? I've attached
a sample. The first 15 seconds are from a good recording the last from
a bad.

---

### Post by klc5555 on 2011-06-24
Sounds like the standard "tinny audio" problem known to exist with this card when using channel change scripts (as one does when hooked to a settop box). Described (with the solution --resetting the audio input when changing the channel) in the "Issues and Problems" section here: [http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)

The command is very easy to add to the bash shell script version of the channel changer script, if that's the version you use. A bit trickier to do with the perl version of the script.

---

### Post by azmyth on 2011-06-24
Thanks for the info. I'll give this a go.

---

### Post by azmyth on 2011-08-27
I'm still having a problem with the tiny sound. I thought I could solve it by varying the sleep (the sleep 7) but this doesn't help as it doesn't tune until after the sleep command. Can someone look at my script and tell me what I need to change?

```
 #!/bin/sh

#Need this or box will miss channels
irsend --device=/dev/lircd1 SEND_ONCE COXSTB exit
sleep 0.7

for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE COXSTB $digit
  sleep 0.6  # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
  
done
sleep 7; v4l2-ctl --set-audio-input 1 -d /dev/pvr150 > /dev/null 2>&1
exit 0;

```

---

### Post by ck102 on 2011-08-28
Hi.
What happens when you run the command in the terminal?

```
v4l2-ctl --set-audio-input 1 -d /dev/pvr150 
```

I've included the script I use to fix it.  It's very similar to yours.

---

### Post by azmyth on 2011-08-29
It fixes the issue when I do it from the command line.

My command doesn't have the () and I don't have mine run in the background like yours does. I'm starting to think this is my problem as I added this stuff and I noticed it tuned quickly.

---

### Post by azmyth on 2011-09-06
Running the command in the background fixed the problem.

---

