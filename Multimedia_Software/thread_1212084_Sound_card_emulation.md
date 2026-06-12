---
title: "Sound card emulation?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by catechu on 2009-07-13
Hi everyone,

I have a remote server which has no sound card. I'd like to use it to run Skype in order to make a call and play from an existing wave file. 

So far, I've got Skype running, and I've installed PulseAudio with the following configuration in ~/.asoundrc:

```

pcm.pulse { type pulse }
ctl.pulse { type pulse }

```The command `[FONT=Courier New]aplay -l[/FONT]` yields "no soundcards found...", as expected. I have the pulse daemon running, and I'm able to select "pulse" under Skype's Sound Options for Input/Output/Ringing. But when I actually try to make a call, pulse fails:

> 
skype: pcm_pulse.c:115: pulse_stop: Assertion 'pcm->stream' failed.
I understand that the immediate reaction is to suggest that I grab the machine and install a sound card, but because it is remote, I'm looking for a way to emulate the functionality of a sound card without actually having one installed. I've searched for existing solutions, but the closest thing I've found is sound card virtualization.

How can I do this?

---

### Post by igorzwx on 2009-07-13
Is it a secure thing?
And what about exploits?

---

### Post by catechu on 2009-07-13
Thank you for pointing out security -- although usually I would think about the potential for exploits, it's not a concern for this particular machine.

---

### Post by igorzwx on 2009-07-13
I would not be happy if my Linux server would be integrated into a botnet.
There were such stories on The Register and Security Now!
Google "Frenzy LiveCD" and try it with your server.
ask Ubuntu security team for a help

---

### Post by catechu on 2009-07-13
Once again, I appreciate your pointers, but security is not a concern in this particular application.

---

