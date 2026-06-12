---
title: "Custom volume knob..."
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Culito on 2006-08-08
Hi,
I googled around a bit and didn't find anything conclusive on this.
I'm doing a case mod and want a big spinable volume knob on the front of the case.  I plan to use an optical encoder.  Is there any way to easily interface this to linux via serial port?  I'd rather not use usb, because I usually have those ports used up.

This seems like it would be relatively easy, no?

-C

---

### Post by IanW on 2006-08-09
Since you're modding your case anyway (HTPC?)...

Why not mod a USB hub to fit _inside_ the case,powered from a spare Molex connector?

That's the cunning plan for my own case mod. ;)

---

### Post by Culito on 2006-08-09
Right on.  But...Is a usb volume control any easier?

---

### Post by mpvano on 2006-08-09
How knowledgable are you?

I think if I had to do it here, I'd use a parallel port. If you're using the existing one for printing, it's easy to add another on a card.

The subject's way too big to cover here, but if you google a bit, I think you'll find a lot of information about how to write user-space software to talk to a parallel printer port.

I usually try to read/write the pins that are already interfaced to the system for high level functions, so that I don't need to horse around with the port directly. It's surprising how much you can do by simulating a line printer....

If you need finer control, you can do direct IO easily to and from the port pins in C, but the program will need to be run suid root. (A simple user space daemon can be an easy way to write a "driver").

Serial IO works well, also, but your device may have to be a lot smarter to generate a useful signal.

The usual algorithm for most encoders is well documented by the vendors and involves a simple state machine that runs at regular intervals to detect quadrature outputs. It's pretty easy to do in C. Again, you'll find a lot of examples on the net or in textbooks.

If all that sounds too complicated, you might explore midi IO, however the hardware usually is expensive and you still have to come up with some "glue" to make it work because vendors almost never support linux directly.

Hope this gives you some ideas. I can attest to the fact that LPT IO is usable under Linux easily,  I use it all the time for writing diagnostic software to test cables, stimulate systems, and control simple external hardware for data acquisition.  As with everything else in life, there are a few "gotcha"s, but nothing you can't work around with a little help from google...

Mario

---

### Post by Culito on 2006-08-09
Wow, thanks for the insight.  I'm good with the hardware side, i.e. optical encoders and such, but I don't have much useful programming experience, aside from programming a few atmel devices.  I better stick to something simpler.  Hell, my ps2 keyboard has a volume knob on it, I might see how it's wired in and piggyback with that or something.

But I do have a free parallel port, and I'm pretty tech handy.  I might see what I can Google up.

---

### Post by Culito on 2006-08-09
Looks like all I have to do is set a few data pins for inputs, and pulse one of them for volume up, and one for volume down.  But how to interface with ALSA.....?

---

### Post by mpvano on 2006-08-09
You'll probably have to use a script that's triggered at regular intervals by the "cron" daemon, or from your program that's handling  the knob. The program will need to execute at regular intervals anyway. It's easy to do this using the system call named "nanosleep" to pause the program thread.

Once you have the value, you can scale it and execute the program called "amixer", which is a batch mode mixer interface for alsa, to set the volume you want.

Use "man amixer" to find out more. You can experiment with this from the command line. Depending on how you write your script or program, it can almost certainly execute shell commands with one line of code. Don't worry about the program loading overhad for the "amixer" program. It'll end up cached and will run very quickly...

consider it a learning experience....

Mario

---

