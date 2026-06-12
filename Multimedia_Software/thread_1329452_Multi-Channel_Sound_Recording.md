---
title: "Multi-Channel Sound Recording"
date: 2009-11-17
forum: Multimedia Software
---

### Post by sailing1nH2O on 2009-11-17
I am looking to switch to Ubuntu, but I'm still using one piece of software on my computer that's keeping me tied to Windows. The software is called [Abyssmedia MCRS](http://www.abyssmedia.com/), and it is a multi-channel, voice activated sound recording program. I use this to record selected telephone calls for my small business, along with the related radio traffic from the trucks. All of these inputs are connected to 4 standard sound cards installed in the computer. I don't have a multi-channel sound card, since they're pretty expensive, and consumer level cards work fine for me. 

Is there any alternative that exists on Linux? I'm really attracted to open source, so that would be greatly preferred, but I'd settle for anything at this point, provided that it is reasonably affordable for a small business like mine. I haven't found any software using queries like Multi-Channel Recording, so even if no one knows of any other software, I'd appreciate any advice on how to better search for it in the repositories.

---

### Post by sailing1nH2O on 2009-11-28
* Bump *

---

### Post by sailing1nH2O on 2009-12-07
*Bump*

Seriously, is this something that's just not possible with Linux?

---

### Post by sailing1nH2O on 2010-01-21
*Bump* Is this just something that's not possible on Linux? It seems like such a simple program - my Windows recording program is only 2 MB.

---

### Post by ricardisimo on 2010-08-18
I'm curious about this as well, but for a different reason. We had a bit of a skirmish with a contractor about who called whom and said what, and I'd like to be able to avoid that.

I'd also like nothing more than to cause trouble for the telemarketers who continue calling even after we've added our number (numerous times) to the *Do Not Call* list.

Voice recording might be optional, for some of my purposes. I'd just like a record of what number called in and who we called out on our landline. Any way to do that with any of the SIP, VoIP or Bluetooth, etc. apps? Thanks.

---

### Post by jabeavers on 2010-08-19
I'm no expert. Check out audacity. You can record many channels at the same time and it can start recording when it senses an input above a certain level. You would need to setup alsa to combine your sound cards into a single, virtual device, or use tha Jack sound server. It's certainly possible.

Hope this helps.
John

---

### Post by jmfal on 2010-08-19
Google: Ubuntu howto,  there is a few howto`s for phone recording

also ubuntu howto: voip

haven`t messed with it just read about it, not sure about multi-channel
have to check it out yourself

---

### Post by ricardisimo on 2010-09-13
The plot thickens...

Without getting into too much detail, I got an inline recorder, it works fine, but now I've discovered some weird things. I have a number dialed out from my line that I can simply play into the phone receiver to dial, but I would like to know what the actual number is.

So that's the new conundrum: how do I "translate" phone dial tones into their text equivalent? Seven beeps of different frequencies magically transformed into seven digits. Can it be done? Thanks.

---

