---
title: "Hardware for recording?"
date: 2007-10-04
forum: Multimedia Production
---

### Post by twistedbydesign on 2007-10-04
I've been scrolling through these forums for a while now, reading up as much as i can on  Rosegarden, Ardour, VST, all that stuff...I have learned a lot but i still don't have what I need.
What I want to know is, what exactly do i need to be able to record and produce music. I have Ubuntu studio in my possession, but i haven't installed it. What do i have to do to get to the point where i can plug in my guitar, bass, whatever, and record songs.
1.What hardware do i need?
     -In all the threads i looked at there has been countless information on great software (which i am very excited to test out) but before i can do that I need something to plug my guitar into my computer, if VST is out of the question (i have a us-428 and i have no idea how to compile software or anything like that) then what do i need to make that possible? Is there a mixer out there that isn't VST that i could invest in?
Any help would be amazing, Or if this has already been discussed and i missed it i apologize and would be grateful if you pointed me in the right direction.
Also, i read someone say something about Jacklab, by suse, apparently it has VST support... I think it was an OS, but i couldnt find anything about it online, any info on where to get this would appreciated as well.
Thanks!

---

### Post by tgalati4 on 2007-10-04
A good-quality sound card is vital.  I use an older M-Audio Delta-66 and it works fine with Dynebolic using the envy24control.  It records in 24-bit, 96 kHz.  

Built-in sound cards are OK for casual use, but tend to be noisey for studio work.

---

### Post by twistedbydesign on 2007-10-04
I cant plug my guitar into soundcards though can i?...or is there some adapter that enables you to?...that was really my main concern was what exactly do i plug my guitar into...(i'm not a pro at recording, i can record decent quality with few resources...but when it comes to the technical stuff im still quite new)

---

### Post by tgalati4 on 2007-10-04
The Delta 66 has a 2-channel preamp as a separate box.  It's a firewire-style interface using a pci card inside the machine and a preamp breakout box that you plug your instruments and microphones into.  It's capable of 6 channels of input and 6 channels of output with appropriate adapters.

There's lots of decent, used hardware out there.  Check craigslist.org

A cheaper alternative is to buy a guitar stomp pedal and use that as a preamp and plug the output of the stomp pedal into the line-in of the PC's built-in sound card.  


In a terminal:

>lspci -vv

will enumerate your hardware.

---

### Post by twistedbydesign on 2007-10-04
I'll look into it.
Thank you very much!

---

