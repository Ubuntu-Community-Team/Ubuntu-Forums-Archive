---
title: "Why Did This Work????"
date: 2009-08-17
forum: Multimedia Software
---

### Post by ttoolin on 2009-08-17
Hi folks-

Yesterday, I installed an inexpensive CMedia CMI8738 soundcard to replace my onboard Yamaha, which I deselected in the BIOS.

I didn't work.  Tried lots of stuff in the help forums.  Nothing was working.  No sound, any time.

Woke up this morning, Decided to try again, and proceeded to uninstall and reinstall the alsa software.  I ran this command in a terminal:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

Before doing anything else, I tested the sound.  It worked.  I clicked on the volume icon.  It worked.  Looked at the mixer options, alsa was there, pulse audio was there.  Okay . . . somehow I got two copies of alsa.  Reran the above code.  The terminal tells me alsa is not installed.

Rebooted the computer and got the login sound.  Tested the sound.  It worked.  Looked at the volume control, and everything is there.  Open a terminal window, and typed in some kind of alsa status inquiry (I forget which one), and get told that alsa is not installed.

Two questions - Why do I have sound?  (I uninstalled alsa)  I see alsa options in the volume control, etc., but the terminal window tells me that alsa is not installed.  Why?

Not to look a gift horse in the mouth, or anything (because I have sound now), but can I set things right?  (sound is there, alsa is there, I see it in terminal, and everything is really like it is supposed to be)?

I am adding this edit, in hopes that someone may benefit by what happened . . .

i got to thinking, as the day went along, and typed in 'alsa' as a search in synaptic package manager.  I had 4 installed items, despite the fact that I could not validate any alsa installation in my system.  I selected them for removal one at a time.  Two of them I marked for removal, and the other two I did not, because it looked like half of my operating system would've been removed along with them.

I then installed alsa-utils.  Success!!!! The sound is up and running, normally.

I wish I had, but I didn't take notes on what I did.  I'm not going to try and duplicate the event.  I hope that others with similar problems can benefit from what I did, and that maybe someone more technically inclined can explain why it worked.

Thanks.

terry

---

