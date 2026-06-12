---
title: "Another firewire issue - SA4250HD intermittently working?"
date: 2009-02-03
forum: Mythbuntu
---

### Post by Calmor on 2009-02-03
I have the SA4250HD (according to the front of the device), and have it connected via firewire.  Priming and channel changing functions always work, but the ability to watch video via firewire comes and goes, sometimes for no particular reason.  Sometimes a restart of the PC and/or STB causes it to work again, sometimes a restart of mythtv-backend seems to help, sometimes it just fixes itself automagically.  

I tried upgrading from 8.04 to 8.10 (x64) with no change.

What could possibly cause the firewire to only work sometimes and go dark for long periods of time (weeks/months/until I start playing with settings)?  Is it a STB issue?  Perhaps a PC firewire issue or cable issue?  I do have a PCI add-on firewire card, is it worth a try?

I have tried using different channels, thinking that perhaps one was flagged with the encryption bit, but none of the channels work (SD or HD), and I get the timeout message in the logs.  (I don't have that computer nearby or I would post them).

Thanks for your help - this issue is quite frustrating.  I do have an analog capture card (PVR-150) but the video quality is terrible (video noise), so the HTPC sits mostly useless until I can get firewire working.

---

### Post by rschapman on 2009-02-03
I am having the exact same issues. My firewire seems to work in the same way. It's considerablly more stable now with my new setup but still hit or miss. The last system I tried had an addon card. This one uses an integrated firewire. 

I am running: 
Mythbuntu 64bit
Time Warner Cable SA4240HD
Point to Point
200MBPS

---

### Post by Calmor on 2009-02-03
I think I'm running the recommended transfer rate (don't remember if it's 400MBS or 800MBS) for the 4250HD, but again, it works flawlessly sometimes, so I'm assuming the transfer rate is acceptable.  Maybe this assumption is incorrect?

---

### Post by Calmor on 2009-02-03
rschapman - what procedure do you take to try to remedy the situation, and are there any specific things that seem to cause it to break?

For a while, I was convinced that shutting off the box was causing issues.  Since the firewire support is sketchy, we typically just watch it like a normal STB through the TV, and turn it off when done.  I found that often, leaving it on reduced the problem, but didn't solve it completely.

---

### Post by Calmor on 2009-03-15
I just tried changing the motherboard (due to other unrelated issues with the onboard video causing a system crash).  It has the same Firewire chipset, and still seems to be about the same, only this time I didn't even get it to connect initially.  Mythprime fails completely (mythprime -v shows everything, even broadcast, fails).

---

### Post by halseyb007 on 2009-03-31
I have a SA4250HDC plugged in via firewire.  I just downloaded the most recent 8.1 release of mythbuntu.  At first, some of the channels were working.  Then the channels stopped getting a lock and showed a partial lock even though I had 100% signal.  I've tried P2P and Broadcast and I've tried all the speeds, 100/200/400/800.  Nothing seems to allow me to get a full lock anymore.  I found another forum that said to press the select button for a few seconds followed by the info button.  Then scroll to a page for IEEE 1394 (firewire) to see if it is set to free (i.e. no C5 encryption)  See this url: [http://www.gossamer-threads.com/lists/mythtv/users/330469](http://www.gossamer-threads.com/lists/mythtv/users/330469)

I confirmed the channel I'm trying to tune is not encrypted.  I've seen code snippets to try rebuilding certain parts and I've seen recommendations for updating ieee modules.  Anyone have any direction for me?  Should I try the 9.x release instead?

---

### Post by bml137 on 2009-04-02
This might be a recently introduced problem.  I also have an SA4250HDC and it has been working from August until I did an update in the afternoon of 3/31.  On 4/1, in hopes of fixing, I updated from 8.10 to 9.04 without success (with respect to resolving the issue).  'mythprime' does not work but my channel changer does.

---

### Post by mlp68 on 2010-01-01
I just wanted to give you guys a heads-up that I made a long-ish post on mythtvtalk about the same problem. Maybe there is a solution meanwhile, and in general it would be good if we out all the info together.

[http://www.mythtvtalk.com/forum/installation-issues/12564-sciatlanta-firewire-recording-woes.html#post49764](http://www.mythtvtalk.com/forum/installation-issues/12564-sciatlanta-firewire-recording-woes.html#post49764)

From what I can tell, this issue is not specific to Ubuntu (my mythtv runs Gentoo), that's why I took it to mythtvtalk.

Let's see if there's some progress.

Thanks,
Martin

---

### Post by lank23 on 2010-02-28
mlp68 
I read your post on mythtvtalk and I have Verison Fios, it is sorta hit and miss also, though I have not tried very hard to see what is really going on with it due I have a PVR-150 and not much free time.

But If I try to watch an open channel "PBS-HD" it will work with some jumping in the picture "maybe my firewire card and or video card", then if I change it to a new channel "HBO" I get the partial lock but 100% signal, then if I change it back to the previous channel it now does not work giving me a partial lock but signal 100%.  I can do this once or twice then I get an error that kicks me out of watching tv back to mythtv menu

This is my setup.

Hardware:
QIP 7100 HD
VIA Technologies, Inc. VT6306

Mythtv FireWire setup.
Mythbuntu 10.04a Mythtv 0.23
Model = DCT-6200  "seems to be the closest model to my QIP-7100"
100Mbps
Point to Point
allow FireWire reset
RingBuffer 14100

As a note I have to use a channel changing script "mythchanger -f 6 -c " for the PVR-150 so not sure if Mythtv built in changer works.

I figure that I am going to try little harder at getting this to work and pass my findings on.

---

### Post by lank23 on 2010-03-23
Been playing with the firewire and Fios for couple weeks now and seems that if the QIP-7100 cable box is unplugged for a couple minutes and then powered back up I can get a LAM lock on the firewire for a couple days, but then it starts only giving a (L__) 100%.....then I have to power off the box.

Also this is my revised set-up.

This is my set-up.

Hardware:
QIP 7100 HD
VIA Technologies, Inc. VT6306

Mythtv FireWire setup.
Mythbuntu 10.04a Mythtv 0.23
Model = DCT-6200 "seems to be the closest model to my QIP-7100"
100Mbps
Broadcast
allow FireWire reset
RingBuffer 14100

---

