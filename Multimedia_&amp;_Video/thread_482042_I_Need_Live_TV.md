---
title: "I Need Live TV"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by NoVista on 2007-06-23
Currently running  a pvr-350 with MythTV since Feisty was released and all is good.
But I need LIVE TV !

I tried using VLC to see if it would work, but get no video output for tv.

What other progs can I use to watch live TV with?

---

### Post by m47h3us on 2007-06-24
you could try tvtime thats ment to work well with analog singal iv never tried it with dvb tho.

---

### Post by tropicflite on 2007-06-24
Hmm, are you sure you're using VLC correctly.  I have a Hauppauge 150 card running on my Feisty box, and I get live tv by going to 

File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing

sudo apt-get install ivtv-utils

then you can do

ivtv-tune -h

to see the options which control the card.  The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

### Post by wolfen69 on 2007-06-24
thanks for the info. i had been using vlc to watch tv, but didn't know about the other commands. i was just using "ivtv-tune -c"

---

### Post by NoVista on 2007-06-25
Thanks tropicflite.

No, I wasn't using VLC correctly.
What you wrote now gets me the audio/video via VLC.
I didn't realize I needed the IVTV utilities, as for Fiesty as you know the install for MythTV was much simpler.

One thing I noticed right off, was VLC gives me a much better quality picture on my puter screen than MythTV.

Now then, the TV still is not LIVE. It's about 1 second behind.

Is yours in sync with a TV?

---

### Post by Chuckels550 on 2007-07-13
I don't understand your problem - MythTV allows you to watch live tv with a WinPVR 350, assuming all is installed, configured and connected correctly.  The reception isn't quite as good as watching your TV without a PVR.

---

### Post by NoVista on 2007-07-13
The problem is it is not in real-time. It is delayed. Check it .. .. Turn a tv on in the same room on the same channel and it's not in sync.
Well, when you use VLC, you do have to go to the tab labeled PVR.
It's as though the PVR is always on?

---

