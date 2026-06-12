---
title: "Check if display device is connected"
date: 2010-02-10
forum: Multimedia Software
---

### Post by jamesdew on 2010-02-10
I am trying to write a script to turn my HTPC off automatically and turn it back on again at a specified interval.

I've got the turn on off bit sorted using /sys/class/rtc/rtc0/wakealarm but I want the script to not turn the machine off if say something is downloading, I am currently watching something etc and i dont think I will have any trouble with that.

But what I would really like to be able to do is tell if my TV is currently on. I dont think anything x11 related would work here and this may not even be possible. Does Ubuntu "know" if it's display device is powered on or not? if so can I interrogate this somehow?

Thanks

---

### Post by efflandt on 2010-02-10
I believe X just checks status and parameters of a display when it starts or when it or xrandr specifically changes something.  You might check **man xrandr** to see (test) what info it can provide.  But that might not indicate whether the monitor itself has been turned off or put into its own standby externally.  That is sort of difficult to test if you cannot see what is going on when the monitor is off, unless you set up a script with sleep pauses that can test and log possibilities while you manually switch the monitor to standby or off.

I just got a 32" LG 1080p HDTV that I am using as a monitor.  It has a serial port that can set various parameters that the remote can do, or check status.  But I have not played around with that yet other than to other than to check that Linux recognizes my USB to serial cable (it does), because I have to find or buy a null modem cable.

---

### Post by jamesdew on 2010-02-10
hi thanks for the reply,

I have an LG too and it also has a serial port. I had not thought of that I guess that could be a possible solution, I have not used serial ports since uni but I guess I could give it a shot.

I will have a read through xrandr aswell

---

### Post by jamesdew on 2010-02-10
I just realised that the TV also has a USB port,

maybe if I plug the USB port from the PC into the TV I can detect it is powered on.

Thanks for giving me this idea!

If this works I will post back.

---

### Post by itsgalway on 2010-05-22
Hey! Did it work?

---

### Post by jamesdew on 2010-10-06
well I tried plugging the LG into the TV and ubuntu did identify the USB device so it probably would have been possible to use this to identify the presence of the TV.

But I decided to just buy a new low powered media centre so I don't have to worry about it being on all the time.

So in theory, yes this will work.

---

