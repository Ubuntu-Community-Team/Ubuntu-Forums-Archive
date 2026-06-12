---
title: "Rosegarden Errors"
date: 2007-11-07
forum: Multimedia Production
---

### Post by enkoan on 2007-11-07
I would really like to use my midi controller and do some recording in Ubuntu, but whenever I start up Rosegarden, I get the following two (2) errors:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

&

Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.

Can anyone advise me on how to fix this or at least point me in the right direction?
BTW I am running Ubuntu 7.10.

---

### Post by enkoan on 2007-11-07
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

Can anyone tell me how to increase the kernel timer resolution?  Is that something thats even possible?

---

### Post by aouie on 2007-11-07
Ubuntu Studio likely uses a real time kernel that will satisfy the timing concerns. I am uncertain as to whether this is easy to tweak in the regular distribution. But, you may want to search to find out if the low latency package (in 7.04 Fiesty I have "linux-image-2.6.20-16-lowlatency") is all you need to resolve the timing issue.
Sincerely,
Aouie

---

### Post by jagwah on 2007-11-07
> System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

Using ubuntu studio would solve this problem, but to fix it in Ubuntu you would have to use another kernel that used a Timer resolution of 1000 (*eg, a multimedia kernel, or low-latency kerne*l), I think that by default the ubuntu's kernel is set at 250, or . . . , you could recompile your existing kernel, just changing the timer resolution to 1000, leaving everything else as is, there would be more involved, like you would likely have to recompile your restricted modules and video drivers perhaps. 

In Mandriva and Debian, I found it very easy to recompile the kernel and change the timing to 1000, however reading the process for Ubuntu has put me off, it seems to be needlessly complicated compared to Mandi and Debian, (*in practice it may not be, but reading about the process it seems that way*)

By far the easiest would be to install the ubuntu studio stuff, you can do that from within Ubuntu/Synaptic, just search for Ubuntu Studio.

> Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.


You need to either install jack, or start the jack server if you already have it installed. Just search for **jack** in Synaptic, I think it's called jackd, anyway, just search jack, read the descriptions, you'll find it. Also find and install qjackctl, it is like a front end for the jack server, and will make things a bit easier for you. Then just start jack through qjackctl before you start Rosegarden, and you should be ok. You can set Rosegarden to start the jack server automatically when it starts if you like, just have a look through the options in Rosegarden and you'll find it

---

