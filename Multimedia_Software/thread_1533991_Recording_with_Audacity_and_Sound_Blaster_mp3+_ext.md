---
title: "Recording with Audacity and Sound Blaster mp3+ external usb audio card"
date: 2010-07-18
forum: Multimedia Software
---

### Post by xroywadex on 2010-07-18
Hello,

I'm trying to record some audio from 4-track cassette tapes using Audacity and a Sound Blaster mp3+ external usb audio card.  I'm using Karmic.

I have fiddled with levels on the sound card using alsamixer, but the only I way I can detect any sound from the tapes when recording is by turning the levels all the way up in alsamixer, and in doing this, I can faintly make out the audio beneath a large wall of static.  If the levels are not maxed out, I only get static when recording in Audacity.

Does anyone have any suggestions for fixing this?  Has anyone had any success in capturing audio with this card?

---

### Post by cchhrriiss121212 on 2010-07-19
What exactly does your recording chain look like?
Are you using the usb card to record or the soundblaster?
To check whether your usb card is recognised put arecord -l into a terminal.

---

### Post by xroywadex on 2010-07-19
I have a 4-track recorder, connected by RCA cables to the Sound Blaster MP3+ sound card.  The sound card is connected by usb to my machine.

The computer recognizes the sound card when I enter arecord -l:

card 1: MP3 [Sound Blaster MP3+], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by xroywadex on 2010-07-19
And I'm trying to record using Audacity.  The audio I'm trying to capture is on the cassettes in the 4 track cassette recorder.  I'm trying to transfer that audio to my computer, by creating ogg or mp3 files of the audio using audacity.

---

