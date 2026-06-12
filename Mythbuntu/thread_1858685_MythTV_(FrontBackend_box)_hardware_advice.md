---
title: "MythTV (Front/Backend box) hardware advice"
date: 2011-10-12
forum: Mythbuntu
---

### Post by shad0w_walker on 2011-10-12
I've been looking into replacing my rather power hungry motherboard with something a little more power friendly. My current board of choice is the ASUS E35M1-M. AMD Fusion based.

I've been reading into it and there seems to be conflicting opinions about it's worthyness as a mythtv machine. I will be using an Nvidia GT210 for the graphics decoding on all videos so CPU shouldn't be an issue, but I have seen talk about schedulers and loads from tuner management and the like.

If anyone has any advice on the board (Preferably using it with positive results :P ) I'd appreciate hearing it.

I've also seen some reports of issues with hangups and slow SATA performance under high load, along with some NIC issues.

If I can get a good answer about this all, I'll be very happy. On paper it looks to be a perfect board for me but my research has shown otherwise.

---

### Post by BicyclerBoy on 2011-10-12
The GT210 is not recommended because the shader performance is too slow for VA deinterlacing (same with GT520)..get a GT430 (best) or GT220.

The AMD E350 fusion graphics is too slow for VA de-interlacing as well..
Unless you use the fusion GPU, it is a bit pointless.
The AMD A8 fusion could be okay.

If you are using a discrete GPU why bother with AMD fusion..just get the bottom end i3 or i5.

The intel CPUs are expensive but are unmatched by AMD.

---

### Post by shad0w_walker on 2011-10-13
I am looking at the AMD fusion option because I can pick up the board (Including CPU obviously) for £70 total. An i3 on the cheap would be far more expensive.

---

### Post by BicyclerBoy on 2011-10-13
Yes intel is expensive..but you get what you buy for sometimes..

The E350 GPU is not good enough for HTPC.
The E350 CPU is marginal to take up the slack.

The AMD A8 fusion may be okay..

This is the best ITX format mobo I have seen.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500070](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500070)

Still need to fork out for a bottom end i3 CPU..

---

### Post by ian dobson on 2011-10-13
Hi,

If you have hardware acceleration for video playback enabled (NVidia vdpau) you don't need much cpu power to playback video. My frontend box is an underclocked e5200 (running at 1200MHz) with a NVidia 9600 (also underclocked with a BIOS hack) only uses 5-15% cpu playing back any file (including 1080i mkv's).

Regards
Ian Dobson

---

### Post by shad0w_walker on 2011-10-14
Thank you Ian. As stated in my earlier post I am using VDPAU on a GT210, which contrary to prior claims works perfectly well with my de-interlacer settings. I was mostly looking for info on what sort of power is realistically needed when the heavy lifting is done by the graphics card. You say that's your front end machine, what is your backend running on? It's going to be a front+backend machine so I am considering something with some more power, but not sure how much mythtv backend would really need.

---

### Post by BicyclerBoy on 2011-10-14
You were/are asking for h/w advice..sorry you do not like it.

It is not just my claims..do some web searching on de-interlace performance of the GT210. This card is simply not good enough.

If you did a side-by-side comparison of the GT210 & any of [GT430,GT220,240] & experimented with hqscaling, VA de-I etc, you would change your opinion of the GT210.

---

### Post by shad0w_walker on 2011-10-14
Looking on the mythtv wiki, which I will take as a good source on this, the only thing it has a problem with is advanced 2x and it also states maybe fine at PAL frame rates. Having spent 2 weeks now watching HD recordings being de-interlaced by it, it's doing just fine for me. I am not asking for advice on my graphics card. I was seeking an opinion on a motherboard.

---

### Post by nickrout on 2011-10-14
> **shad0w_walker said:**
> Looking on the mythtv wiki, which I will take as a good source on this, the only thing it has a problem with is advanced 2x and it also states maybe fine at PAL frame rates. Having spent 2 weeks now watching HD recordings being de-interlaced by it, it's doing just fine for me. I am not asking for advice on my graphics card. I was seeking an opinion on a motherboard.

Yes, back on topic :) If you are not transcoding or commflagging then almost any cpu will do. If you want to do heavy transcoding and/or commflaging then the more powerful the better.

Most people recommend intel i3/i5 processors for processing power and low power consumption.

---

### Post by shad0w_walker on 2011-10-14
Ok. Thanks for the advice. Looking around, a cheap i3 bundle wouldn't be too massively expensive. I didn't originally look into it as I tend to associate the higher spec stuff with higher power drain, but I guess the designs have improved since I last looked in to it. The whole thing is mostly a planning phase at the moment, can't afford any upgrade right now. Good to know that though. Had a feeling the requirements for the backend wouldn't be too great, but nice to get some confirmation.

---

### Post by BicyclerBoy on 2011-10-14
You were asking for advice on an APU (CPU/GPU) frontend mobo.
How can you possibly exclude advice about the video card/GPU from any discussion about a front end machine ?...

I have a fair idea why..

---

### Post by nickrout on 2011-10-15
> **BicyclerBoy said:**
> You were asking for advice on an APU (CPU/GPU) frontend mobo.
How can you possibly exclude advice about the video card/GPU from any discussion about a front end machine ?...

I have a fair idea why..

possibly because he already has the gpu and is happy with it.

---

### Post by shad0w_walker on 2011-10-15
I was asking about advice on a MOTHERBOARD that contains a given CPU, specifically stating I already have a graphics card that is quite fine for MY NEEDS. I am excluding advice on the card because that's not what I damn well want. I do not feel the need for advanced 2x, I cannot see any difference between it and 1x on my display, so it DOES NOT MATTER. That it maybe unsuitable for someone who cares about advanced 2x is completely irrelevant to this thread. You are just trying to cram the one piece of advice you can down my throat. I don't recall even saying in this thread it would be doing HD decoding, so you are throwing advice at me that has absolutely no need to be here.

While we are at it, why don't I give you excellent advice about getting new, more expensive tires for your car when you ask for engine advice. I'm sure that will help plenty. Please just stop harping on about a graphics card. If I notice a problem, I will put my 9600GTX in there.

Nickrout - Thank you for the advice
Bicyclerboy - Will you stop talking about my graphics card. I never wanted to discuss graphics capabilities. If you actually read my post, you'd know I was seeking advice on MOTHERBOARD STABILITY AND SUITABILITY. Not graphics card prowess.

I am looking into the advice about an i3 machine as if the power drain does work out to be similar to the fusion, it would be the best of both worlds (low power and good performance) but that once again has nothing to do with a graphics card. I just want to find options for a motherboard.

---

