---
title: "Where is the bottleneck?  CPU or network?"
date: 2009-11-06
forum: Mythbuntu
---

### Post by B34N on 2009-11-06
I have successfully setup Mythbuntu 9.10 as a backend/frontend on an old P4 (2.?Ghz).  I also setup Ubuntu 9.10 and MythTV frontend on another P4 (3Ghz).  I'm able to watch TV and recorded content on the 2.?Ghz backend through the frontend on the 3.0Ghz machine.  Unfortunately the content is choppy...especially when the content is higher resolution.  I seem to be fine at 720P but when I go beyond that it's pretty bad.  Both machines are on a wireless G network with little to no other traffic.  Is the network the bottleneck or is it the machines?  If it's the machines then which one?

Thank you!

---

### Post by B34N on 2009-11-07
I did some further testing of the frontend machine using System Monitor.  On a 720p recording (little to no choppiness) the network was running under 1.0MiB/s. The CPUs were averaging around 80% but would range from 50-100%. For 1080i the network ran at 1.4MiB/s and the CPUs actually seemed to be less utilized. (weird?)

My understanding ([http://www.pixelbeat.org/speeds.html](http://www.pixelbeat.org/speeds.html)) is that 802.11G can do 2.9MiB/s, which I believe is twice what 1080i requires. I understand that wireless speeds can be highly variable but considering the conditions that I'm testing under, I would expect to be able to maintain at least 1/2 the max speed. Could this be a latency issue rather than a throughput issue?

I'm doing the testing with the frontend, backend and router all within 8' of each other.  After I'm done testing the frontends will be about 40' from the router with two walls in between.  I could break down and wire a few locations ([http://www.instructables.com/id/How_to_Wire_Your_House_With_Cat_5_or_6_For_Ether/](http://www.instructables.com/id/How_to_Wire_Your_House_With_Cat_5_or_6_For_Ether/)) but that wouldn't help me much with watching content on the netbook or notebook wirelessly.

Any thoughts?

---

### Post by ian dobson on 2009-11-07
Hi,

Maybe try copying a file to the local harddisk of the frontend and then play it with mplayer and have a look at the CPU load.

I have a 54Mbit wireless connection to my laptop and sometimes the throughput drops to less than 1Mbit every so often for no real reason (Microwave or DCT telephone active). If normal internet surfing thats not a problem, but for streaming it's a pain/can cause stuffering.

If the problem is CPU and you have a new enough NVIDIA graphic card then have a look at using VDPAU for video playback.

Regards
Ian Dobson

---

### Post by nickrout on 2009-11-07
i don't think you'll have much luck with 1080i on those machines, cpu not grunty enough. but it could also be the network. 802.11g really doesn't cut it in real life for HD.

Eliminate variables one at a time, run a cable (its only 8  feet, trip over it for a day or two). If that doesn't fix it try fitting a vdpau capable card.

---

### Post by B34N on 2009-11-08
It was the network.  I cabled the two machines and the problem was resolved.  1080i wasn't using more than 2.0MiB/s which I had hoped the 802.11G could have handled under close to ideal circumstances.  I will hardwire my main machines but I would still like to be able to use the netbook and laptop on 802.11G.  Could I do something like increase a buffer to make them more manageable?  Or is it possible to down convert a recording or broadcast from 1080i to 720p while viewing over the wireless?

---

### Post by B34N on 2009-11-08
I just installed and ran iperf.  
95Mbits/sec!

Then I unplugged the network cables.  With both the backend and frontend on wireless, I averaged about 10Mbits/sec. With just the frontend on wireless I averaged just over 20Mbits/sec.  It looks like I may be able to get my wish and be able to do some occasional wireless if I can optimize some settings and conditions.

---

