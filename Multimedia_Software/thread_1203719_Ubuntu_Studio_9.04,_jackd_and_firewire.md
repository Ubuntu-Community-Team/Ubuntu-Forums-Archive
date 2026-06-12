---
title: "Ubuntu Studio 9.04, jackd and firewire"
date: 2009-07-03
forum: Multimedia Software
---

### Post by carricre on 2009-07-03
A strange problem has reared it's head in Ubuntu Studio 9.04.  When running jack with my firewire audio interface (ESI Quatafire 610) the device works great for an average of about 3 mins and then suddenly stops working with the following message:
```

cannot continue execution of the processing graph (Broken pipe)
```
The same thing happens with both RT and not-RT, runs great for a bit, I'm able to start all my apps and connect them and use them for a few minutes and them BAM! jack commits suicide.

Someone suggested that I try the 64bit version, so I did and the problem became worse.  Jack starts and crashes nearly instantly with the same error.

Jack gives no further explanation of what is going wrong so I've no idea where to even start.  Is this a bug with ffado or something else?  Any ideas?

---

### Post by DigitalRazor on 2009-10-09
> **carricre said:**
> A strange problem has reared it's head in Ubuntu Studio 9.04.  When running jack with my firewire audio interface (ESI Quatafire 610) the device works great for an average of about 3 mins and then suddenly stops working with the following message:
```

cannot continue execution of the processing graph (Broken pipe)
```The same thing happens with both RT and not-RT, runs great for a bit, I'm able to start all my apps and connect them and use them for a few minutes and them BAM! jack commits suicide.

Someone suggested that I try the 64bit version, so I did and the problem became worse.  Jack starts and crashes nearly instantly with the same error.

Jack gives no further explanation of what is going wrong so I've no idea where to even start.  Is this a bug with ffado or something else?  Any ideas?

Its a long shot: But check your Jackd Setup. I just read your post as I was setting up two FA-101s on my old 32 bit system... 

Check your "Priority Level" and your "Frames/Period" settings bump them up a bit. pending on how you have it set up .. I really wouldnt worry about the latency. I am reading 32 at jackd and 10.7 at Ardour. that may seem high .. but considering I am using the FAs to monitor as I do individual tracks I am not having any issues at all ..
(FYI I am using "Priority 25" and "Frames/Buffer:512" I read somewhere that the Frames Buffers for FA-101s should be no lower than 256 ... I have played with 128 with good results ..but depending on your system and what all else is done... your milage may vary. Hope this helps.. Good luck.

---

