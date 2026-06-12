---
title: "Ubuntu Studio &amp; Guitar??"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by nosam on 2006-07-31
I'm relatively new to Ubuntu and I just stumbled upon Ubuntu Studio.  For awhile I've been looking for a (cheap/simple) way to hook up my guitar (Strat) to my PC to find a way to record.  I actually had Ubuntu Studio installed the other day and played with it for awhile but couldn't figure out how on earth I got JACK to see my guitar on my Line-In connection to my sound card (SoundBlaster Live 5.1).  Is this even possible or do I have to have a MIDI connection? I have a cable with a standard instrument connection on one end and a stereo mini on the other.  I'm not too knowledgeable when it comes to recording/audio stuff.

I had to reinstall Ubuntu yesterday and haven't put Ubuntu Studio back on here yet.  I wanted to find out a little more and whether or not I could make this work before I installed it again.  From what little time I was able to spend playing around with some of the programs this is a really neat project (Hydrogen is very cool).  Thanks.

---

### Post by dolson on 2006-07-31
I don't know of anyone other than myself who owns a guitar capable of MIDI output because it's not a standard thing that most people want. So more than likely, your guitar is standard audio only, and not MIDI.

You will plug it into the soundcard's Line In port. Then adjust your volume control so you can hear it. The problem is that guitar's output is very small compared to what your sound card is expecting, and so it won't likely be very loud. On top of this, it's going to sound unnatural because it is very clean. You can plug it virtually into Ecamegapedal and mess with that to get a good tone, or you can invest in hardware such as a Line6 POD, which is what I have.

---

### Post by metapundit on 2006-07-31
The POD is very nice (I had 2.0 for a while) but if you want to get into it without spending a couple hundred dollars, Behringer's GDI21 box is very nice. I got one for $29 (from musiciansfriend.com i think). It's has 3 amp models, 3 miking emulations, and very basic tone/drive/eq. No effects (unlike the pod), but if you're just trying to figure out how to get your strat to sound good out of your computer speakers, this will do it. It's also a much smaller package about the size of 1.5 Boss effects pedals.)

I believe this is meant to be a cheaper knockoff of the Tech-21 SansAmp (if you're familiar with that)...

---

### Post by nosam on 2006-07-31
> **dolson said:**
> You can plug it virtually into Ecamegapedal and mess with that to get a good tone

I have my guitar plugged into my line-in port on my soundcard like i've done before and the sound works fine.  But I've played around with Ecamegapedal and nothing I do seems to change the sound.  All I get is the same clean sound.  I'll play around with it some more to see if I can get it to work.  But, I have to run it via the console because I have no icon for it and when I do I get this:

```
matt@matt:~$ ecamegapedal
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Ecamegapedal does actually open but it will close if I close the terminal window.  I don't know if this has anything do with it not working but maybe it does.  

> I believe this is meant to be a cheaper knockoff of the Tech-21 SansAmp

I actually have a Tech 21 Trademark 10 which isn't bad for what I use it for.  I'll look into the Behringer you mentioned, thanks.

---

### Post by izle on 2006-08-01
I have got a stupid question:

I am using a Toshiba Laptop, a cme uf5 usb-midi keyboard, I am using the native sound card and I don't plan on buying a pcmcia sound card. So far I am still learning how to use the different software, jack, the soundfonts, and the keyboard itself! ... And I am dying to plug my guitar in this mess but I am not really sure how to manage to do that, so here comes the question:
 
Is it possible to use one those tools ie Behringer's GDI21 or line pod 6 with usb-midi converters such as "M-Audio Uno - USB MIDI interface cable" or "Edirol UM-2EX 1-in/2-out USB to MIDI Interface"?

---

### Post by metapundit on 2006-08-01
> 
Is it possible to use one those tools ie Behringer's GDI21 or line pod 6 with usb-midi converters such as "M-Audio Uno - USB MIDI interface cable" or "Edirol UM-2EX 1-in/2-out USB to MIDI Interface"

I can't answer as to your keyboard (which may have a MIDI out), but the POD and Behringer GDI don't have anything to do with USB or Midi (disclaimer: the POD has a midi port but if IIRC it is only used to program it by attaching to your computer, no MIDI out is possible). Both devices take a standard 1/4" guitar cable as an input signal from a guitar and provide amplification (+ effects, in the case of the POD). Both devices output via a standard 1/4" jack - you can use a 1/4" to 1/8" converter to plug the output jack into the line-in or mic ports on your sound card.

re nosam: I got those same errors initially and got them to go away by removing the 3 wacom sections in xorg.conf file. There's an example of what lines to comment out [in this thread]("http://ubuntuforums.org/showthread.php?t=212025&highlight=wacom+baddevice"). Hey that Trademark10 of yours has headphone and XLR outs... You could always run from one of those with a 1/4" => 1/8" converter into your computer's line-in... Great little practice amp.

---

### Post by izle on 2006-08-02
Hi,

I think it is worth mentioning the Line 6 usb driver that you can find here :

[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)

it seems to answer my questions, so I think I will go for a Pod xt!

---

### Post by dolson on 2006-08-02
The POD XT driver is already in Ubuntu.. Just modprobe it.

---

### Post by dolson on 2006-08-02
...

---

### Post by izle on 2006-08-02
I am using the 2.6.17-rt7 kernel .deb package available in the discussion page on the UbuntuStudio web site, and it seems there is no line6usb module in it nor podxtpro drivers which I found in the ubuntu source of the 2.6.15-26 kernel...
and to be honnest when it comes to kernel stuff I am completely in the dark, I don't know what makes sense and what doesn't!

---

### Post by dolson on 2006-08-02
Yes, you are correct. If you roll your own kernel, or use someone's unsupported kernel, you will not have all the drivers that Ubuntu includes. I didn't realize you were using a different kernel.

---

### Post by Kpax1 on 2007-09-02
I have a Line 6 Tone Port UX2. Since the Gearbox software, which emulates a recording environment on your desktop, is restricted to Windows and Mac OSX, I was wondering if it would be possible somehow to use a Windows box with Gearbox, and then send the output signal from gearbox to a linux box and record it using audacity or some similar programme. Could this be done with a serial cable connection between the two computers?

---

### Post by Kpax1 on 2007-09-03
I think it might be possible to utilize the spdif output on the TonePort and send this to a linux box--a clean digital signal. I am going to look into this...

---

### Post by Gremlinzzz on 2007-09-03
gtkguitune
a nice tuner 
:guitar:

---

### Post by Zimmer on 2007-09-05
> **dolson said:**
> The POD XT driver is already in Ubuntu.. Just modprobe it.

I have tried that a few times , now.
Without success.  latest Dapper kernel 2.6.15.29   386

I have , however , used my PodXT Live plugged into the Line in  socket to record guitar using Audacity. Reasonable results...

I am still messing about trying to get the line6 driver to modprobe before I try to install an XP or W98 virtualbox in order to attempt to use the Line6 Gearbox and Guitar Workbench software in a virtual machine.

Any clues..anyone?

---

### Post by Zimmer on 2007-09-05
> **Kpax1 said:**
> I have a Line 6 Tone Port UX2. Since the Gearbox software, which emulates a recording environment on your desktop, is restricted to Windows and Mac OSX, I was wondering if it would be possible somehow to use a Windows box with Gearbox, and then send the output signal from gearbox to a linux box and record it using audacity or some similar programme. Could this be done with a serial cable connection between the two computers?

Why not just install the Win version of Audacity on your Windows box?

---

