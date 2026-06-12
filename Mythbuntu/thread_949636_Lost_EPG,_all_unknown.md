---
title: "Lost EPG, all unknown"
date: 2008-10-16
forum: Mythbuntu
---

### Post by Andrew U.K. on 2008-10-16
Hi,
In the epg it now shows unknown on every channel. I am using the EIT transmitted guide. 
What would cause this and would using the XMLTV one be better? 
Any ideas on how to restore it?

Cheers 
Andrew

---

### Post by Andrew U.K. on 2008-10-16
when I run mythfilldatabase i get this,

2008-10-16 20:27:57.936 Source 1 configured to use only the broadcasted guide data. Skipping.

How do i get it to stop skippng?

---

### Post by SiHa on 2008-10-17
If it helps, I find my Backend will just stop getting EIT guide data after it's been up for a week or so. I end up with %unknown% for everything, same as you. I find a reboot usually cures it.

Except my backend won't boot since last night, but that's a story for a different thread.

Grrr.

Also, I'm not sure, but the Mythfilldatabase line looks correct. You are only using the broadcasted guide data, so it's skipping the part where the grabber is called.

---

### Post by Andrew U.K. on 2008-10-17
Cheers

I'm going to do a re-install. 
Do you use xmltv? I'm thinking this might cure it.

Andrew

---

### Post by SiHa on 2008-10-20
I did, when first tinkering with Myth, and it worked fine. But when I put together the main system it was simpler initially to just use EIT, no buggering around with 'mythfilldatabase --manual'. I get 8 days worth of guide data which is enough for me, so I've just left it.

---

### Post by Andrew U.K. on 2008-10-20
I have kept it as EIT and maybe have found a fix for getting the epg to show up.
I have been waiting for it to go again, so I can check this actually works, because I can't believe this is how I fixed it.

I went to the programme guide, every channel showed unknown. This time I scrolled down to check to see if all the channels were unknown, they were, but as I went round again programmes started appearing. By the time I had scrolled through the epg three times all the programmes were back.  

Is mythbuntu like a favourite old car that just needs coaxing along? I'm waiting with anticipation for the epg to goto unknown again.

Andrew

---

