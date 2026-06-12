---
title: "Guitarists: What guitar hardware will connect to ubuntu pc?"
date: 2008-06-12
forum: Multimedia Software
---

### Post by gatorbrit on 2008-06-12
I posted this over in the community cafe forum, but it was suggested that I post again here. 
 

Hi, I have used line6 products, but I would like to do some basic recording using ubuntu. Previously I have used the line6 guitarport.

What hardware / effects processors/ etc can you plug into a ubuntu pc and then record, say using audacity?

I am looking for a pretty simple solution..

Thanks
:guitar:

---

### Post by sturmvogel on 2008-06-12
I've always done "live" recording with Audacity using an M-Audio Duo (USB connection) and double miked the amp, one at a speaker, the other back to pick up some of the room acoustics.  Ubuntu and Fedora both automatically recognize the hardware and load drivers.  Piece of cake.

---

### Post by aeiah on 2008-06-12
its doubtful that you'll get the guitarport working since its a little unusual, unless it will function as a normal soundcard device. only way to see is to plug it in and see what's reported in the terminal when you type 'lsusb' i guess. maybe there are drivers for it.

if you have a normal line-in id suggest just using that, unless your normal soundcard isn't very good. onboard ones tend to not be very clear for line-in. usually worse than their line-out anyway.

i use a delta 44 for recording stuff. there are quite a lot of options available now though depending on your budget. see how you get on with the hardware you already have though. there are guitar effects software packages in the ubuntu studio repository and elsewhere if you want something that will function like the software side of your guitarport setup. i always prefer recording clean and adding effects afterwards though personally, unless im doing something with a lot of distortion.

---

