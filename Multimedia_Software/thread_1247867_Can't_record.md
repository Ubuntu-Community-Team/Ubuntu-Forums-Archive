---
title: "Can't record"
date: 2009-08-23
forum: Multimedia Software
---

### Post by drndrw on 2009-08-23
Hey everyone. I'm trying to record music in my Ubuntu machine, but it doesn't appear to be working. I have my instrument in the Line-in on my machine, and it must be picking it up because I can hear my instrument playing through my computer speakers, but it will not record on any recording program. If have the input source set to line and the line in is turned all the way up, but still nothing. What can I do?

---

### Post by lavadisco on 2009-08-23
I'm with you. I am trying to record in both Sound Recorder and Audacity, and nothing is working. I have tried a million different things. I am so sick of the stupid way that Ubuntu handles audio. So many different audio codecs, so many layers of preferences and hidden crap. Pisses me off. Sorry I can't offer any help, I'm in the same boat.

---

### Post by mztriz on 2009-11-24
I'm also having the same problem. I have my guitar plugged into the line in jack on my computer and I can hear everything just fine, but I can't get any program to record it!

---

### Post by r0n1n0x47 on 2009-11-24
I was experiencing a similar problem with my external microphone. Fortunately my fix was quick and simple. Anyway here's what I did, hope it helps.

1. open a terminal window
2. type in alsamixer
3. arrow over to <digital>
4. toggle the option to Analog I

After doing this I was able to record no problem.

---

### Post by mztriz on 2009-11-24
Hm. I don't seem to have that as an option in my alsamixer. Here's a screen capture:[IMG]http://img257.imageshack.us/img257/8829/screenshotavaavadesktop.png[/IMG]

Here is an image of sound recorder: [IMG]http://img527.imageshack.us/img527/1559/screenshotsoundprefereng.png[/IMG]

As you can see it's set to line-in but there is no sound coming from it. I can hear it just fine though. Any ideas?

---

### Post by mztriz on 2009-11-25
Where would I find the 'digital' setting?

---

