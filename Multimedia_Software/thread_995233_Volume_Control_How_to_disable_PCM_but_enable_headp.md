---
title: "Volume Control: How to disable PCM but enable headphone???"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Piraja on 2008-11-27
Dear all,

I'm trying to listen to music via headphones while working at my low-fi desktop computer (Compaq Evo D 510 SFF with integrated Intel soundcard; see screenshots for further details) late at night, but I just cannot figure out how to mute the box's loudspeaker but keep the headphone sound on. I feel rather stupid asking this, because this is the first PC with which I have encountered such a puzzle and it really confuses me. Could this be a hardware issue, or maybe an Alsa bug? Or am I just missing something?

I mean, if I uncheck the "mute" box of PCM, the loudspeaker sound turns on, and this is obviously not what I want late at night when even the keyboard noise is too much racket. But if PCM's muted, no sound in the headphones.

Thanks in advance,

Piraja

---

### Post by Piraja on 2008-11-28
Anyone any idea? For such a stupid problem it would seem overkill to install Alsa from source, which is what solved the problem for [wetbrainirishsage]("http://dreamlinuxforums.org/index.php?topic=1697.0") (a nice nick, isn't it?) at the Dreamlinux forums. So I'm not the only one with this problem, maybe I should file a bug against &#8212; what? Not Alsa, anyway?

And I'm not sure if the Dreamlinux forums solution works on Ubuntu Intrepid, either. Maybe I'll try it anyway, so wish me luck if you will.

---

### Post by Piraja on 2008-11-28
I solved the issue without having to compile from source or anything like that. I went to Synaptic, searched for alsa and found, among a few other things my Intrepid install still missed, GNOME Alsa Mixer. It's actually funny that GNOME Volume Control shipped with Ubuntu is so stripped-down it does not allow for even such simple functionalities that would have solved my "issue" in the first place. Well, the "issue" at hand might just be related to older hardware, with which one has to do one's googling and the usual forums and package searching, I guess.

---

### Post by damatta on 2008-11-30
Same problem here, but that didnt do it for me.
I plug the headphones but the speakers are not muted.

---

