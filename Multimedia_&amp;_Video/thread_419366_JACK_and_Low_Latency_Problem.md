---
title: "JACK and Low Latency Problem"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by dahouse on 2007-04-22
Hi,

I recently installed Kubuntu fiesty on my laptop. I installed the Jack Audio Kit with the Jack Gui controller through the gui package manager and the Low Latency Kernel by doing  

sudo aptitude install linux-image-lowlatency

So, basically, I did uname -r and the kernel version is as follows

2.6.20-15-lowlatency


Jack starts up fine, it works great, but there's a problem, the latency is at 43ms... That's unusable.. So I enabled realtime in jack control and try starting the server, but unfortunately, when I start up the jack server with the realtime option enabled in the jack control setup, it crashes. How can I set it up so that it doesn't crash and I get good low latency.

Thanks

---

### Post by jondecker76 on 2007-04-23
The low-latency kernel really still is not good for audio work, though you should be able to easily get around 10ms with it..  Try playing with the frames/period and other settings..

On a side note, UbuntuStudio is being released soon, and they are working on a realtime kernel (they have a link somewhere where you can get it now for testing purposes, but i don't remember where the link is). A real time kernel with its high resolution timers and preemption is the key to linux audio work

So... While the low-latency kernel is better than the normal stock kernel, to do any kind of serious audio work, you need to wait for the realtime kernel..  Looks like its only a couple weeks out!

---

### Post by baltho on 2007-05-06
Hi folks!
I had the same problem, and it seems to be a security issue. You need permissions to "renice" yourself to use the lowlatency kernel, which I figured out from the jack message box, but the solution was elusive until I found a Finnish Ubuntu forum, the only bits of which I understood were the command line extracts!  
Nevertheless, it worked, so here it is. Add the following to the bottom of your /etc/security/limits.conf file:

@audio - rtprio 99 
@audio - memlock 250000 
@audio - nice -10 

(just like that - cut-n-paste and pop it in at the end of the file)

This gives anyone in the audio group low latency permissions. I did a reboot - not sure if just logging out+in would have worked...

Hope this helps, and perhaps the developers could add this step to the lowlatency kernel installation scripts?

---

### Post by MetalMusicAddict on 2007-05-06
The only one you really need is: **sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'**.

The others can be specific to a users system. Ubuntu Studio does set the rtprio.

The link to the RT kernel we are testing is: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

---

