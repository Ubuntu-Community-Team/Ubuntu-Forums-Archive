---
title: "skype and pulse (again)"
date: 2008-12-28
forum: Multimedia Software
---

### Post by rossmoore on 2008-12-28
Hi,

I have skype working with Pulse, I think. I have Sound Out and Ringing set to use Pulse, and Sound In set to my microphone. I can successfully make two-way calls.

I also have Rhythmbox and VLC all working successfully with Pulse.

The problem is that when listening to music a a call comes in, the sound stops working altogether. So I have to restart skype if I want to use that, or restart rhythmbox if I want to continue listening to music.

I've read loads about getting skype to work with other applications, but nothing seems to quite solve this problem.

How can I go about debugging this problem?

Ross

P.S. I'm on Hardy.

---

### Post by rossmoore on 2008-12-28
bump!
Is this solvable, or is skype just a bit broken and I need to wait until they fix it?

---

### Post by markbuntu on 2008-12-29
You can try setting your mic as default input device in the pulseaudio volume control and set the sound in to pulse in skype. This should prevent skype from grabbing the sound device. It has been a while since I fooled around with skype so I am not positive that it will work for you but let us know if it does.

Skype has been problematic with pulseaudio in ubuntu. This is due to problems on both sides but they are working on it.

EDIT: you also may need to change the audioconference setting to pulse in System/Preferences/Sound.

---

### Post by blackgr on 2008-12-29
Where did you install skype from. I had also some sound issues with the officual site version. Then i used the medibuntu skype and it worked like charm.

---

### Post by rossmoore on 2008-12-29
Thanks for the help. I installed skype from the repository. I'm now in Intrepid, by the way - but it's no better. Thanks for the tip about trying setting the Sound In to Pulse. Unfortunately when I do that the sound isn't captured correctly - it's bitty, very delayed and too quiet (regardless of how I set pavucontrol). To get the mic working I have to set it directly to the mic device itself.

Unless I can fix how pulse deals with my microphone (either of them), then I think I'm stuck. Fingers crossed they can work it out soon.

---

### Post by markbuntu on 2008-12-29
If you find the sound stuttering and crackling etc on skype you can edit the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
Code:

;default-fragments = 5
;default-fragment-size-msec = 25

Change them to look like this :
Code:

default-fragments = 8
default-fragment-size-msec = 5

---

