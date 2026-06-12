---
title: "Distortion in sound volume: above 85%"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by malius on 2006-06-04
As the title states: If I increase the sound volume above 85%, I get cracks and pops in audio playback.  At first I thought I had a bad connection between my speakers and sound card, but after a quick check, they were seated firmly.  I then decreased my volume below the value indicated above, and everything works as expected.

**Specs:**
[LIST]
[*]Sound Card: SoundBlaster Live Value (Gateway OEM).
[*]Sound Mixer: ALSA
[*]Output: Digital
[*]Sound Channel: WAVE
[/LIST]

Anyone else have this issue or know of a fix?

---

### Post by skymt on 2006-06-04
Does this happen in Windows (assuming you have it installed)? Does this happen when you attach your speakers to another sound source like a stereo? Does it go away if you turn the software volume control below 85% and turn the speaker volume up to compensate?

---

### Post by JoWilly on 2006-06-04
[QUOTE=malius]As the title states: If I increase the sound volume above 85%, I get cracks and pops in audio playback.  At first I thought I had a bad connection between my speakers and sound card, but after a quick check, they were seated firmly.  I then decreased my volume below the value indicated above, and everything works as expected.

**Specs:**
[LIST]
[*]Sound Card: SoundBlaster Live Value (Gateway OEM).
[*]Sound Mixer: ALSA
[*]Output: Digital
[*]Sound Channel: WAVE
[/LIST]

Anyone else have this issue or know of a fix?[/QUOTE]


I had this about 4-5 years ago with alsa.

If I remeber well, there is a way to set the max sound in alsa in the alsa config and I think with an alsa config tool... I hope I put you on the right track ;)

EDIT: don't forget to post a bug report on launchpad to inform the developers.

---

### Post by malius on 2006-06-04
The sound worked as expected in Breezy and Windows.

If I use the volume knob on the speakers and the software value is below 85%, I do not have any issues.

Edit: When I get a bit more time, I will post the bug.

---

### Post by JoWilly on 2006-06-04
[QUOTE=malius]The sound worked as expected in Breezy and Windows.

If I use the volume knob on the speakers and the software value is below 85%, I do not have any issues.[/QUOTE]

This confirms my post. The alsa config is somewhere in /etc. Set the max volume there (but there is also some config tool to do this I think).

-> the problem is that alsa is sending a higher volume than your card can handle.

---

### Post by malius on 2006-06-04
Although I'm picking up Linux quite rapidly, I'm still ignorant on where certain configuration files are.  JoWilly, could you lead me to the alsa config file?

Edit:
I think I've found a "solution" to the issue:
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting)

From the sounds of it, I should just get a new sound card.

---

### Post by JoWilly on 2006-06-04
[QUOTE=malius]Although I'm picking up Linux quite rapidly, I'm still ignorant on where certain configuration files are.  JoWilly, could you lead me to the alsa config file?

Edit:
I think I've found a "solution" to the issue:
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting)

From the sounds of it, I should just get a new sound card.[/QUOTE]

Sure no need to get a new sound card ;)

With amixer you can set the playback limits. As I said I did this 4-5 years ago, and don't have much time to go into this now. Do "man amixer" to see what you can do with it, and start "amixer" to see the limits for your controls.

This way you should be able to set the master limit to 0-80 for example, this would keep you within your 85% range.

---

### Post by malius on 2006-06-04
Thanks for the response JoWilly, when I get more time, I will play around with amixer.

---

### Post by LordRaiden on 2006-06-04
In a shell, do the following,

```
alsamixer
```

You will now have a graphical screen with a number of controls. 

The 'left' and 'right' arrow keys will move you left and right.
The 'up' and 'down' keys will raise and lower volume for a given control.
The 'M' key will mute/unmute a given control. 

Navigate to the control that says 'PCM' and look at the value. If it is 100, lower it to around 80. 

Now, navigate to 'Master' and raise it to the maximum (100) and listen for distortion. 

If you have some distortion, lower 'PCM' more. 

If not, raise 'PCM' until you hear distortion. 

Consider all the values above this point as your 'no-go' point (your upper bound) and go back down one. 

Your distortion issue should be resolved.

---

### Post by malius on 2006-06-04
That seems to have solved the problem.  What is wierd is that I use Wave not PCM.  Would you have any idea why PCM would affect the wave device?

---

### Post by JoWilly on 2006-06-04
[quote=malius]That seems to have solved the problem.  What is wierd is that I use Wave not PCM.  Would you have any idea why PCM would affect the wave device?[/quote]

Wave and pcm are the same.

---

### Post by malius on 2006-06-04
Thanks for the clarification!

---

### Post by malius on 2006-06-08
Update:

OK, I've searched the net for countless hours and still cannot figure out how to set the desired upper playback limit using the ALSA utilities (amixer/alsactl/etc).

Does anyone know how to do this?

---

