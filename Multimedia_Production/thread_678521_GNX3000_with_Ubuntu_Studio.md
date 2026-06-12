---
title: "GNX3000 with Ubuntu Studio"
date: 2008-01-25
forum: Multimedia Production
---

### Post by vikarama on 2008-01-25
Hi,

I have just installed the latest Ubuntu-Studio and I am trying connect my GNX3000 to record with Ardour with Jack.

Unfortunately there is no signal from my GNX3000 and I am not able to see how my GNX3000 is recognised by Ubuntu. Someone please help!

Thank you.

Regards,
vikarama

---

### Post by mcstrum on 2008-02-08
I am also using a gnx3000 and the one thing holding me to my current setup running that other os is the fact I can not connect the gnx via the usb connection built in. I could however buy a middle unit but I think it should be a fairly easy mod/config to make it work. 

I however am a guitard and not at a Linux level to work this one out.

Peace, 
McStrum

---

### Post by vikarama on 2008-02-18
Hi,

I figured out the solution for the problem. Now I am able to connect my GNX3000 through the USB and use JACK to record noise-free.

For those who have trouble doing it, here's how you do it.

1. When you connect the GNX3000 through USB, you will see that GNX3K is identified as an external sound card. To verify this just see under /proc/asound you would see new files created for GNX3K.

2. Now all you have to do is select hw:1 in the Interface under qjackctl's 'Setup' window. Alternatively you can type this command in the terminal
'jackd -d alsa -d hw:1'.

3. Now start JACK and you can see 4 capture ports and 2 playback ports under alsa_pcm.

Now go ahead and do the thing you do best....

regards,
vikarama

---

