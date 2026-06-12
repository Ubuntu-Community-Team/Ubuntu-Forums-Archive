---
title: "$500 to burn on new frontend - best bang for buck?"
date: 2014-02-02
forum: Mythbuntu
---

### Post by sidesh0w on 2014-02-02
After 6years I'm putting my current setup out to stud.

Backends seems simple enough to spec, but whats best frontend to be had these days?

Prefer:

- small / quiet
- low power consumption
- 1080 / HD playback (VDPAU?)

---

### Post by blm-ubunet on 2014-02-03
Intel NUC & using drivers from
[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)
This limits your linux distro choice a bit..

Haswell i5 or i7 with HD4600 or iris pro. (that's the $500 gone!)

The haswell i7 is upto 3x power efficiency of sandybridge i3. (some Phoronix tests)
The intel graphics drivers are almost alright..VAAPI de-interlacing is still broken tho.
There would be nothing that could compare to idle power consumption & still has same potential.
And the VAAPI problems will be sorted in time.

AFAIK
Very good results are now possible with AMD & FOSS driver & VDPAU (yes VDPAU the open std) just not on the latest AMD h/w.

Don't get a GT210/520/610..
The latest version of GT630 is a kepler (not the initial version) & been reports that it is okay.

---

### Post by alien878 on 2014-02-03
A cheap ATOM should work fine and has low power consumption.  You should be able to get an ATOM barebone PC with everything you need for < $300.  I have an ASUS AT3N7A-I (Atom 330)  that I use for a combined FE/BE.  HD (via VDPAU) works out of the box.

Just make sure you do a search on the MB and mythtv to make sure the work together.  Sometimes newer HW doesn't play well with mythtv.

---

### Post by blm-ubunet on 2014-02-03
The atom/ION (ION2) might just work & only because of nVidia GPU but you get a very slow inefficient 1st gen atom.

Replacing a 6 yr old system with another 6 yr old system is likely to be a disappointing experience.

The Haswell HD4600 graphics benchmarks for openGL at about a match for GT220 (& likely at lower power) so shader post-processing is adequate for video playback.
Decoding is not a problem (for any of the current h/w offerings).

The HD4600 system (with mobo) can probably idle lower than atom330 & ION2 mobo.
And the CPU has performance to play anything using CPU & openGL if required.

If support (thru FOSS radeon) improves for the latest AMD CPU-GPU then a similar argument can be made for that..

---

### Post by sidesh0w on 2014-02-03
Thanks Guys

Wow, Intel NUC looks perfect, didnt know about VAAPI stuff.

Is there a guide to running mythbuntu on these or is it a plug and play affair?

I cant seem to find an i7 version, but I did find i5 with HD5000 (I'm assuming would be same or better than HD4600).

Can you tell me what Intel NUC Model # I should go for for around $500?

Thanks!

---

### Post by oldfred on 2014-02-03
Some discussion of different versions of the NUC. But better one's are more expensive.

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)

Also on low cost smaller cases.
[http://www.phoronix.com/scan.php?page=article&item=silverstone_low_cost&num=1](http://www.phoronix.com/scan.php?page=article&item=silverstone_low_cost&num=1)

---

### Post by blm-ubunet on 2014-02-03
Plug-n-Play mythbuntu is only available for LTS versions..

The Intel NUC needs the later kernel &
[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)
to really shine & 01.org only has builds for the latest versions of distros..

There will be some convergence with *buntu 14.04 LTS / mythbuntu 14.04 (mythtv0.27+fixes) which is available in 3+ months.
Ubuntu releases do not typically have the absolute latest versions of everything.

Could always just make do with CPU decode & openGL rendering until then..

There is the mythtv frontend only minimyth2
[http://minimyth2.linuxd.org/](http://minimyth2.linuxd.org/)

---

### Post by z7APXKm on 2014-02-04
I find my i3 does the job quite nicely.  Low power and quiet too.

---

### Post by khPWXxF on 2014-02-05
Hi z7APKm,
  That's interesting - would you expand on your i3 setup and your environment please?
Ta
Phil

---

### Post by blm-ubunet on 2014-02-06
Other h/w options:
[http://www.anandtech.com/show/7735/asus-chromebox-fanless-haswell-in-a-nuclike-form-factor-starting-at-179](http://www.anandtech.com/show/7735/asus-chromebox-fanless-haswell-in-a-nuclike-form-factor-starting-at-179)

cheaper than equivalent NUC
avoid the bottom end "atom" powered versions of this (same for NUC)
Lack of built-in IR Rx could be annoying.

Hopefully this can replace the atom/ION box.
[http://www.maximumpc.com/asus_launches_eee_box_eb1037_bay_trail_processor_nvidia_820m_graphics](http://www.maximumpc.com/asus_launches_eee_box_eb1037_bay_trail_processor_nvidia_820m_graphics)
The 820m laptop graphics is completely unbenchmarked w.r.t. video playback requiring de-interlacing.
It could be worse than the ION..

Almost none of the video playback tests include broadcast interlaced video playback.

---

### Post by philip7 on 2014-02-13
Definitely interested to hear the advice on this as I'm looking for a new frontend.

At the moment I'm leaning towards a Zotac Zbox I42 instead of the NUC.

The zbox is fairly small so I can mount on the back of my tv.
The zbox includes a remote control and IR Reciever.
At the moment I've only seen other Mythtv users using a Zbox, I haven't seen any for NUC, but that could be because I haven't tried hard enough.
The price isn't great, but compared to any alternative options its pretty cheap.

Hoping to drop in a a small SDD and maybe 4-8GB of memory - this is mainly going to be as a frontend but will also use to stream Steam games to my tv as well.
There doesn't seem to be a great deal of info on mythtv frontend requirements, but it doesn't seem like you need to spend big money.

Interested to get feedback - especially if this helps the OP

---

### Post by uteck on 2014-02-14
I had problems getting hardware decoding to work with my Zbox with an AMD APU.  This was a year or so ago, so try to stick with the Nvidia version until for now.  14.04 should have the latest AMD support and work better, hopefully out of the box without lots of tweaking.

Overall, I like the design of the Zbox since it is ment to be a home theater system.  Built in IR, with a secondary external USB IR receiver for when you mount it out of sight.  Also comes with a USB wireless N reciver and a remote control that works fine in Linux

---

### Post by paulsum2 on 2014-02-23
i think the new zotac id45 is great, it has a gt640 in it!... perfect for the deinterlacing via VDPAU.


otherwise go with a asus h81,g3420,4GB ram, and a gt630v2.(gk208) (384 shaders). the gt630(gk208) only adds 5 watts to the idle power.!(you can spot the gk208 gt630's by the fact they have 384 shaders, and 64bit memory width)

h81 (100$),or h87 (120$),g3420 (75$), 4GB (45$), gt630(gk208)(70$), case (such as inwin bp655) (50$), seasonic ss-300tgw (60$) (needed because in is SILENT, and gold level efficiency) ssd (70) 64GB

approx 470$/(h81)or 500(h87).. but might want to upgrade the motherboard to an h87 for the i217v ethernet. (it seems that the realtek 8168(8111g) , is detected as a 8169, and causes slow downs for the frontend... (need to install realteks 8168 driver)

---

