---
title: "How to play music through the microphone jack?"
date: 2011-01-19
forum: Multimedia Software
---

### Post by ttarvai on 2011-01-19
Hello, absolute noob here.

My green audio output jack is broken, under Windows 7 I used to reroute my audio to the red microphone jack, so I could listen to music with headphones through the microphone jack. It took me some simple mouse clicks.

How to do this in Ubuntu 10.10? I haven't find anything useful for days for this particular problem. :?

---

### Post by ttarvai on 2011-01-20
No idea, anyone?

---

### Post by ttarvai on 2011-01-20
No idea, anyone?

---

### Post by ttarvai on 2011-01-20
No ideas, anyone?

---

### Post by ttarvai on 2011-01-20
No ideas, anyone?

---

### Post by ttarvai on 2011-01-20
Any idea?

---

### Post by ttarvai on 2011-01-21
Sorry for the multiple posts, I got some weird error every time I wanted to post something, and I kept trying, well, it didn't go too well obviously.

But I still don't have the answer for my question, so it would be appreciated if anyone could tell me anything.

---

### Post by Shaggin Shea on 2011-03-24
I was wondering the same thing myself. I will see what I can find.

---

### Post by Shaggin Shea on 2011-03-24
I'm a noob so there might be better options then this but this worked for me.

```
pacat -r --latency-msec=1 -d  alsa_input.pci-0000_00_1b.0.analog-stereo | pacat -p --latency-msec=1 -d  alsa_output.pci-0000_00_1b.0.analog-stereo
```
  

where 'alsa_input.pci-0000_00_1b.0.analog-stereo' is your input  device and 'alsa_output.pci-0000_00_1b.0.analog-stereo' is your output  device. Use paman to find these device names.

I had to turn down my mic in volume prefrences because it was pretty loud/muffeled.

Did this help you?

---

