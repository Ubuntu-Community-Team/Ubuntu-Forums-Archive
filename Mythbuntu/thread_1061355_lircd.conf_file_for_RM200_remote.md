---
title: "lircd.conf file for RM200 remote?"
date: 2009-02-05
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-05
Hi All,

Just wondering if anyone had an up to date lircd.conf file for the RM200 remote that comes with the Antec Fusion Remote HTPC case? I have lirc working and can see the output on screen when running irw, however using the iMon pad conf file from lirc.org I can only get the d-pad (and surrounding buttons apart from mouse/keyboard) and the numerical buttons to work. Just hoping someone has a conf file so I don't have to record a new conf file from scratch.

---

### Post by fatmonk on 2009-02-06
Hi,

Are you sure you have lirc working correctly?

Your symptoms sound exactly like mine, and I've yet to get completely to the bpttom of my problem - at the moment I suspect I have a problem with HAL grabbing the data from the in-built IR receiver, and treating the remote as a keyboard (hence mouse/d-pad, mouse clicks and numbers working). However I've tried to stop HAL from grabbing the receiver (via instructions on this forum) and have failed to get much further so far.

One way to test if your remote is being seen as a keyboard is to open something like a text editor and check to see if you can type numbers from your remote and navigate around in the document with the d-pad. If so then your remote is probably being seen as a keyboard and you could have the HAL issue.

When you try irw you are probably just seeing the remote being received as keyboard key-presses, this is exactly what I saw and it fooled me for a long while into thinking I was getting somewhere with lirc - it turned out I wasn't as I could still 'type' on the command line when irw had been exitted!

Hope this helps, and if you get anywhere please do post back as I'm interested in how to solve this one myself. It's the last thing I need to get working on my box, and has been for a couple of months now!

-FM

---

### Post by the_plumber on 2009-02-17
Hi Monk!
I too have the RM200, coupled with the iMON-LCD on a Fusion Max remote case. I have got to the stage where the power button powers the case on, the volume knob gives readings in irw, and all the numbers and other buttons work with irw, except the "joystick" pad and the ring of buttons immediately surrpounding the joystick. Interestingly, the "enter" key below the pad works occasionally.
I'm running a clean install of Ubuntu 8.10, patched to the max, and have installed LIRC by downloading 0.8.4a, setup/configure, make, make install, and then used Jean-Yves Avenard's solution on 
[http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452](http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452) (the bottom half of his post, not the bit about installing LIRC) to create two lirc.conf files, the hardware fies, etc.

This may be where I'm going wrong, he has the MX200, I have the RM200, and maybe something is different in the hardware or codes...Also when I try to create a conf file that includes the Pad and the surrounding buttons, I don't get any output from irrecord for those buttons, though all the others work fine. I even tried putting the codes documented here> [http://brakemeier.de/electronics/vdr/lirc-imon.html](http://brakemeier.de/electronics/vdr/lirc-imon.html)
into the conf file, but that didn't do anything..

Finally, I know its a software/config issue, because it works fine under windows with the manufacturer's drivers...

I have a suspicion that it's something to do with the invocation of a patch called "pad2keys", which I think has to be done at compile time, but Google has not been my friend on this and has stayed silent:(

---

