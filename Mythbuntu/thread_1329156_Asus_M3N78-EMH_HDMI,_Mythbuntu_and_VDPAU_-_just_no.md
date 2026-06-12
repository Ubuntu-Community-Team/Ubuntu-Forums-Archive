---
title: "Asus M3N78-EMH HDMI, Mythbuntu and VDPAU - just not there yet..."
date: 2009-11-17
forum: Mythbuntu
---

### Post by flecki on 2009-11-17
Hi All,

i am currently running this board with mythbuntu 9.10 and everything is going well for me on my DVB-C cable network but...

I can´t get VDPAU to work without jumping frames/sound regardless of the VDPAU-profile chosen in mythtv.

The BIOS is set to the maximum memory for the onboard 8200 (512 MB).

VDPAU only works when i deactivate the decoding via VDPAU and remove all interlacers. If i only activate one of those pictures start jumping again.

Anyone any ideas what to change or test ? 

The 8200 with 512 MB aloocated should be able to do SD without problems and HD too with low power interlacers - no idea what goes wrong. Since i run a dual core Athlon it works like a charm via processor only in SD and even in HD most of the time so i am in no hurry - i just want VDPAU to do what it was made for on my 8200.

Thanks for your suggestions guys !!

---

### Post by jstew on 2009-11-17
I too, had the same problem until I turned off composite and turned off laptop-mode and ondemand. Frequency scaling, for some reason makes VDPAU unusable for HD. 

Others have had good results by increasing the minimum CPU frequency.

---

### Post by flecki on 2009-11-17
Got it under control now - here come my findings:

My CPU(max 2800 MHz) runs ondemand on only 1000 MHz.

Changing the up_threshold(set on 95 % cpu load under mythbuntu) wouldn´t help even if i knew how to do it permanently since by running VDPAU the CPU always stays quite idle.

Unfortunately the 1000 MHz Setting of the CPU is also reducing the bus-speed thus slowing down the GPU....

So while your GPU is totally overloaded at this speed the CPU is happily running at between 8 and 14 %. It would take some kind of tool to watch the GPU load and then ramp up the CPU speed - and thus the GPU with it - on boards like mine.

Solution for now - manually switch to performance mode if needed when watching HD content -  if bored by manually switching, permanently run in performance mode.

Not elegant but it works.

---

### Post by scottcrawford on 2009-11-17
Frequency scaling slows down the memory clock too, so the GPU gets throttled back. I have my CPU set to a minimum 1.8GHz and HD plays fine with the 8200.

The other issue that gave me stuttering playback was having the extra audio buffers enabled in myth. When I unchecked that option, playback became smooth (I was getting a bunch of prebuffering pause errors with the extra audio buffers enabled).

---

### Post by flecki on 2009-11-17
Would be cool to have a function im mythtv to ramp up cpu speed to performance mode when playing demanding content.

After all - most of the time you don´t watch...

I don´t have that audio problem on this board at all.

How did you set the minimum to 1800 ?

---

### Post by Dewey_Oxberger on 2009-11-17
You must have installed cpufreq-utils - is that true?

Try installing cpufreqd.  Then edit the cpufreqd.conf (It should be /etc I think).

Odds are you are using some profile that has ac = on.

Find that profile and change the min freq to 1.8G.

I suppose Myth should really ask for a higher cpu freq during playback...

---

### Post by flecki on 2009-11-18
I now use the Applet Gnome provides for CPU-Freqency changes.

When playing TV HD-Content i switch to performance manually because franky i still watch mostly SD since the network here only offers little HD i would want to watch ;-)

For file playing i got a seperate Sigma-based Box that handles all i need in HD with 12 Watts power.

Thanks for your suggestions guys - really appreciated !

---

