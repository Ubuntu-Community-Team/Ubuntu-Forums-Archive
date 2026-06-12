---
title: "New to Mythbuntu"
date: 2008-04-16
forum: Mythbuntu
---

### Post by tommie74 on 2008-04-16
I am new to Mythbuntu, and very pleased! My computer starts up automaticly to get the tv-guide daily using mythwelcom, starts up automaticly to do recordings. Very nice!

But I use quite an old computer with a pvr 150 card. When I am recording, and at the same time watching an old recording, my computer can't cope.

My question: is it possible to change a setting so mythbuntu makes it impossible to watch an old recording while live recording to protect the recording process?

---

### Post by laga on 2008-04-16
I don't think such a setting exists. But maybe you can your system specs so we can try to make it work..

---

### Post by tommie74 on 2008-04-16
> **laga said:**
> I don't think such a setting exists. But maybe you can your system specs so we can try to make it work..

I am sorry Laga, I complained too fast. My father was compllaining the computer froze when he tried to watch a recording while another program was being recorded. I have just tested it for myself and it seems to give no problems whatsoever. After questioning my father about what exactly he did, he told me that first he turned on the computer, but that didn´t work (actually he turned it off, because it was already on, recording at the time) So that didn't workt he tried restarting the computer (turned it on after all) and admitted that he then started pushing options more or less wildly, restarting the computer again etc. 
So I think Mythbuntu is not completely dad-proof.. 

But it might be that the system actually froze because the specs of my computer are too low. So I will mention the specs, maybe somebody knows if this is good enough to record and watch an old recording at the same time.

AMD Athlon 900 Mhz, 256 Mb memory, nVidea RIVA TNT2 model 64 Pro (used for tv-out), 74 GB IDE harddisk 7600 rpm (6 GB ext3 Mythbuntu partition, 68 GB ext3 recording partition), Hauppauge pvr 150 tv-card mpeg encoder (used for tv-in)

Thx anyhow Laga.

---

### Post by volkswagner on 2008-04-16
256meg ram is low.  When you go to system status, you can see if your ram maxed out.  How much swap did you allow?

---

### Post by tgm4883 on 2008-04-16
The ram may be low, but you should be able to handle recording and playing back at the same time.

---

### Post by tommie74 on 2008-04-17
As suggested I have checked the system resources, installed xfce4-system-monitor plugin, and it seems that the cpu and memory are only used for 50% when recording and playing a recording at the same time. My swap is 520 Mb, the double of the memory. It seems my dad was the problematic factor after all.
Thx for the tips,
Thomas.

---

### Post by tgm4883 on 2008-04-17
> **tommie74 said:**
> As suggested I have checked the system resources, installed xfce4-system-monitor plugin, and it seems that the cpu and memory are only used for 50% when recording and playing a recording at the same time. My swap is 520 Mb, the double of the memory. It seems my dad was the problematic factor after all.
Thx for the tips,
Thomas.

Disconnect that power button.  Mysql doesn't like being turned off that way.

---

### Post by ian dobson on 2008-04-17
Hi,

Add more memory, 1Gb is the sweet spot.

I had a underclocked C2D @800MHz with 1Gb ram and can record/watch a program at the same time, using a PVR150.

OK the C2D is a dual core but  CPU load isn't a problem.


Regards
Ian Dobson

---

### Post by laga on 2008-04-17
> **ian dobson said:**
> 
Add more memory, 1Gb is the sweet spot.


Sweet spot for what?

Sounds like overkill to me :) Unless you want to use some really big themes..

---

### Post by ian dobson on 2008-04-17
Hi,

My frontend only box uses about 300-400Mb ram (I've not optimised to for ram usage) so and with 512Mb there won't be much left for MySQL/backend.

The MythTV wiki talks about 512Mb ram, the mythbuntu documentation talks about 1Gb ram recommended. The main thing is to have enough ram so the system doesn't need to swap and if possible enough left over for a good sized cache.

For me 1Gb is the "sweet spot" for my configuration. I'd rather spend a little bit more and have more than enough memory rather than spend time trimming the system down so that it runs optimally on sub optimal hardware.

tommie74: Whats the actual PC spec. CPU, Harddisk, Chipset etc.

Regards
Ian Dobson

---

### Post by tommie74 on 2008-04-18
> **tgm4883 said:**
> Disconnect that power button.  Mysql doesn't like being turned off that way.

I have instructed my dad now to check wether mythbuntu is already running before turning the computer on. I think that will do. Also I have made a backup of my mythconverg in case anything happens to the database, so I can restore it in case something happens to it.
thx for the tip, if this doesn't work, I will definitely do that.
Thomas.

---

### Post by tommie74 on 2008-04-18
> **ian dobson said:**
> Hi,

Add more memory, 1Gb is the sweet spot.

I had a underclocked C2D @800MHz with 1Gb ram and can record/watch a program at the same time, using a PVR150.

OK the C2D is a dual core but  CPU load isn't a problem.


Regards
Ian Dobson

Hello Ian,
it seems to me right now that neither the cpu nor the memory is a problem because when I check the system status while watching an old recording and at the same time recording a tv show, both are only used for about 50%. 

Regards,
Thomas.

---

### Post by tommie74 on 2008-04-18
> **ian dobson said:**
> Hi,

My frontend only box uses about 300-400Mb ram (I've not optimised to for ram usage) so and with 512Mb there won't be much left for MySQL/backend.

The MythTV wiki talks about 512Mb ram, the mythbuntu documentation talks about 1Gb ram recommended. The main thing is to have enough ram so the system doesn't need to swap and if possible enough left over for a good sized cache.

For me 1Gb is the "sweet spot" for my configuration. I'd rather spend a little bit more and have more than enough memory rather than spend time trimming the system down so that it runs optimally on sub optimal hardware.

tommie74: Whats the actual PC spec. CPU, Harddisk, Chipset etc.

Regards
Ian Dobson

Hi Ian,
the specs:
AMD Athlon 900 Mhz, 256 Mb memory, nVidea RIVA TNT2 model 64 Pro (used for tv-out), 74 GB IDE harddisk 7600 rpm (6 GB ext3 Mythbuntu partition, 68 GB ext3 recording partition), Hauppauge pvr 150 tv-card mpeg encoder (used for tv-in), and 520 Mb swap.

I think that the 1 Gig memory is recommended when you use mythbuntu with software mpeg encoding. I have a hardware mpeg encoder in the pvr 150 so the systemload is not as much compared to a system that needs software encoding.

regards,
Thomas.

---

