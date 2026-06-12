---
title: "How to make Midi Maker work in Ubuntu (Karmic)"
date: 2010-03-27
forum: Multimedia Software
---

### Post by Robin-chan on 2010-03-27
Edit:

I have a few things working now, so all I need to know is a good way to record the music you play from Virtual Keyboard. I've tried Audacity to do this, but it never works correctly.

Edit 2: I figured it out! :)

---

### Post by hansdown on 2010-03-27
Hi Robin-chan.

The link you provided leads to an executable file.

In ubuntu, click system> administration> synaptic package manager.

In the search box, enter "midi" to find some good programs for midi.

---

### Post by Robin-chan on 2010-03-27
I know that it's an .exe file. I used to use it in Windows, and I wanted to see if I could make it work through Wine. I've installed a bunch of packages to make midis work, but it still hasn't affected the program. I guess I might just look for something else.

---

### Post by themusicalduck on 2010-03-27
Not sure how well wine and midi work together. Have you install the timidity package? That's the one that usually adds support for midi sounds on Ubuntu.

---

### Post by Robin-chan on 2010-03-27
Timidity didn't help, but I may just give up on making Midi Maker work.

I did download Virtual Keyboard, though, but it doesn't make a sound, either. I'm reading about someone else who had the same problem, but I don't know if I can get it to work.

Edit: My problem now is getting JACK to work. It won't start, and it gives me the following error message:
Could not connect to JACK server as client.

---

### Post by Robin-chan on 2010-03-27
Apologies for the double-post. I now have Virtual Keyboard working... somehow. Is there any way to record the sounds you play?

---

### Post by themusicalduck on 2010-03-28
You'd need to use virtual keyboard with another midi editing program to actually record the midi. The ones I can think of off the top of my head are RoseGarden, Muse, LMMS.

There are a list of midi programs you could try if you type "midi" into the Software Centre.

If you mean record the sounds into a an audio file then it's a bit more difficult with midi. The best way is just to run a line out from your computer into the line in and record with something like Audacity. It might be possible to do it direct with Jack using the patchbay, but I'm not sure how.

As to Jack not running for you. On the Jack control UI, click on Setup and make sure Realtime is unchecked. Bear in mind though, if you really want to do low latency stuff then you'll want to install the realtime kernel, then you can use Jack with Realtime on and hopefully lower the latencies somewhat.

---

