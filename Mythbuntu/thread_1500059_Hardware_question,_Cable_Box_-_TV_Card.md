---
title: "Hardware question, Cable Box - TV Card"
date: 2010-06-02
forum: Mythbuntu
---

### Post by seanchayes on 2010-06-02
I'm looking to set up Mythbuntu and want some guidance as to the correct hardware to use as some elements of my configuration will change.

Previously, I've had a Hauppauge PVR 150 working with MythTV connected directly to my cable (WOW - Wide Open West, Chicago) service with no cable box.

Now, however, I now have a digital service (not HD) using a Scientific Atlanta Explorer 4250 cable box and want to know what make / model TV/Tuner/Capture card I should use to get it working with Mythbuntu 10.04 and will I need a channel changer device?

I'm a little stuck and confused as to what to get.

Thoughts / commments ?

Thank you

---

### Post by 4dognight on 2010-06-02
If it has a firewire port , it is your best bet.
 Either way you can still use you pvr150 as is.

---

### Post by ian dobson on 2010-06-03
Hi,

Does your reciever have a firewire or ethernet port? If yes then maybe you can convince MythTV to use it directly.

For example I'm using a DVB_C recorder with an ethernet port, have a simple script that does the channel changing using wget/http and VLC to stream the video into mythtv as mythtv doesn't support the streaming format that the recorder supports.

Regards
Ian Dobson

---

### Post by LowSky on 2010-06-03
By law US cable companies need to have a unlocked firewire port. If the box you were given is not unlocked you may have to request on from your cable operator. They have to comply.

[http://gizmodo.com/009313/fcc-requires-firewire-on-all-cable-boxes](http://gizmodo.com/009313/fcc-requires-firewire-on-all-cable-boxes)
[http://www.mythtv.org/wiki/FireWire](http://www.mythtv.org/wiki/FireWire)

---

### Post by seanchayes on 2010-06-04
Thanks

I've now moved on to the fun of trying to get the channels changed to record the right channel.

I did look at the cable box and saw a port on the front and there's one on the back. They both look like USB ports.

This is what I have:
[http://www.scientificatlanta.com/explorerclubguides/getting_started/4012028.pdf](http://www.scientificatlanta.com/explorerclubguides/getting_started/4012028.pdf)

And curiously port 12 is not labeled. Would that be the firewire port? It looked a little different to the port on a Firewire card I have.

---

### Post by bob.os on 2010-06-05
From that drawing, 12 is also a USB port.

I've also trying to connect this using one of my PVR-150s.  I've got the S-Video connection wired, but am trying to figure out setting up the PVR-150's iR blaster to change channels on it.

I'm stuck trying to figure out getting the channel changer script (/usr/bin/ch_chan.sh) into place to drive this thing, but it looks like the external STB setups are the way to go.

This thread describes which LIRC script to use: [http://www.gossamer-threads.com/lists/mythtv/users/368639](http://www.gossamer-threads.com/lists/mythtv/users/368639)
Here are two MythtTV Wiki pages on using a digital cable STB and an IR blaster for channel changes:
[http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat](http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat)
[http://www.mythtv.org/wiki/Recording_Digital_Cable](http://www.mythtv.org/wiki/Recording_Digital_Cable)

Hope that this helps a bit.

---

