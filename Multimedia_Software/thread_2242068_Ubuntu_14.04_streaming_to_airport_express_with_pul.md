---
title: "Ubuntu 14.04 streaming to airport express with pulseaudio"
date: 2014-08-30
forum: Multimedia Software
---

### Post by ojnbloemen on 2014-08-30
In my last version of Ubuntu 12.04 I was able to stream my audio to my apple airport express with pulseaudio.

In the versions after 12.04 this stopped working. I tried all versions and reverted back to 12.04. Now that 14.04 became available I hoped that the issue would be solved, but after installing this version the problem was still there.

What happens is that after I make Apple airtunes discoverable with paprefs, and then I chose airport in the sound settings my players stop playing. So spotify, VLC, etc all just stop. When I click normal speakers again the players resume playing.

Also the "test audio"  function does not function, or does not produce sound.

Again, when I re-install 12.04, the sound works wonderfully again.

Anyone a suggestion how to get it working in Ubuntu 14.04?

I have an airport 1st generation with a sony VAIO laptop VPCEB4C5E.

---

### Post by ojnbloemen on 2014-09-05
Mmmm... Nobody?

Are there people who have the airport express streaming working under Ubuntu 14.04?

---

### Post by ojnbloemen on 2014-10-09
I hear from private messages that other people have the same issue. Are there people that have a working airport express under 14.04?

---

### Post by sayananbig on 2014-12-19
I ran into the same issue, and it was quite vexing. My prior installation was Ubuntu 12.04, and my preferred sound application was VLC, as this one had worked without any skipping or dropping. When I upgraded to 14.04, I found that this no longer worked. PulseAudio volume control still found my Airport Express, but i heard no sound.

I found two steps that comprised a solution. First, after the upgrade, the volume setting under [PulseAudio Volume Control]->[Output Devices] was set all the way down. After this, I could send audio to the Aiport Express, but it played very choppy with lots of skips and drops. Next, I changed from VLC to Rhythmbox, and now it plays back smoothly using Ubuntu 14.04. i hope this works for others!

---

