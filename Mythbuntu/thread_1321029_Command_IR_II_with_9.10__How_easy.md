---
title: "Command IR II with 9.10?  How easy?"
date: 2009-11-09
forum: Mythbuntu
---

### Post by tegwilym on 2009-11-09
I've been using MythDora 5 for about 2 years now, everything works nearly flawlessly, including the serial IR Blaster to change channels on my DirecTV box. (IR blaster was the biggest pain to set up!).

I've build a new Mythbox and would like to run Mythbuntu on this on.  My new motherboard does have a serial port, but I need to find a cable and connector for it.  
Since serial ports are going out of style, I would like to go with USB on this one if possible.  So my question:

Does anyone have any comments/experience/reviews of the Command IR II box?  That looks like the USB replacement for my serial irblaster.   The web page says its very easy to setup, but I spent weeks working on the IR blaster (only got it working by accident - so I don't touch it now!).  Time to upgrade to .22 Mythtv though.
(This one: [http://www.commandir.com/content/view/32/48/](http://www.commandir.com/content/view/32/48/))

I'm looking for something that is easier and not as archaic as the old serial port to control things. 

Thanks!

Tom 
- Happy MythTV watcher for 2+ years.

---

### Post by tegwilym on 2009-11-18
Nobody has any comments on this?

---

### Post by santhony on 2010-01-10
Yes.. I did get this to work fairly easy...

As Per the Install Instructions from CommandIR's Website.

The steps I followed for Karmic 64 are...

Install as per instructions for Karmic.
I then installed the sh script install-commandir.sh, listed under mythbuntu instructions.
Make sure you have "setserial" installed, ie sudo apt-get install setserial
Make sure you have "lirc-x" installed, ie sudo apt-get install lirc-x

Make sure your hardware.conf and lircd.conf match what they have listed on the CommandIR site, I'll attach mine to this thread...

I first did the setup with all the dafaults, using Hauppauge remote since I had two of them available... I didn't want to dive in too deep and get any other remote working and other blaster yet, except for both Hauppauge.

Make sure your able to get LED "A" on the CommandIR device to green, not red.  If it is green, lirc is loading correctly.

You can then try irw.. If you get no output, the device is unable to match the codes to any in your lircd.conf

Next you can try irsend... For me.. once i get irw working.. irsend works.

If LED "A" Blinks Red Green Red Green.... ... .

Then your USB port is not supplying enough power, connect it to a powered hub,(you plug into an AC outlet to power the hub).

To confirm the problem above, your /var/log/syslog will show a repeated error of "Is CommandIR busy? Error -110".

Attached are also the codes for hauppauge remotes, lircd.conf.hauppauge.
If testing with the Hauppauge remote.. Be sure your lircd.conf references and can access the lircd.conf.hauppauge, or paste them directly into your lircd.conf

Pls remove the .txt from the files, they were added for upload to the thread.

---

### Post by tegwilym on 2010-01-10
Thanks for the response.  I did get it working somewhat easily, not too much pain as the last time I did it with Mythbuntu.  I just had a problem where I needed to send an "enter" command to the DirecTV box.  I posted a question and had the results in a few hours!  Channels change fine now.  I just have to work on picture quality, DVD playing, optical sound output and a few other things.  A pain to set up, but worth the effort.  ;)

Tom

---

### Post by tegwilym on 2010-01-10
> **tegwilym said:**
> Thanks for the response.  I did get it working somewhat easily, not too much pain as the last time I did it with Mythbuntu.  I just had a problem where I needed to send an "enter" command to the DirecTV box.  I posted a question and had the results in a few hours!  Channels change fine now.  I just have to work on picture quality, DVD playing, optical sound output and a few other things.  A pain to set up, but worth the effort.  ;)

Tom

Oh, I should mention that I'm still running at Serial --> Irblaster, works so I won't fix it for now.  Maybe my next revision.

---

