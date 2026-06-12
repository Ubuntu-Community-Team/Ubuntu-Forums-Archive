---
title: "Hardy 8.04 snd-via82xx audio comes and go's"
date: 2008-04-27
forum: Mythbuntu
---

### Post by batman01 on 2008-04-27
Hi all,

I'm running Hardy based mythbuntu, which has been updated to within a week or so ago. Its running on a Jetway j7f2, which has the via CN700 chipset. After a long (and succesfull) battle to get XVMC working on this chipset I have run into an audio problem.

My sounds works for a period of up to a day, and then begins to cut in and out. The sound will briefly go crackly and then disappear altogether. sometimes it will never come back at all, other times it comes and goes for 2 or three seconds at a time.

I can sometimes provoke it to come back for a short while by fiddling with the DXS channel volume in alsamixer.

/etc/init.d/alsa-utils restart also seems to bring it back for a while, but then it will misbehave again.

I ran speaker-test to see if I got a similar problem, which I did, so I exited speaker test after it went silent. About 4econds after I had exited the speaker test utility I got about 3 seconds of pink-noise output. I think something is going seriously wrong with buffering somewhere.

dmesg shows nothing
/var/log/messages shows nothing
I can't find a log specifically for alsa anywhere

Can anyone suggest how I can proceed to diagnose this problem?

Thanks all,

Pete

---

### Post by batman01 on 2008-04-28
no one?

---

### Post by jonhewer on 2008-05-09
i've not yet upgraded from gutsy to hardy, but i have the same board and had been experiencing problems with sound cutting out all together as a result of what i can only think to be some kind of buffer overflow.

the solution i found was to install and use OSS instead of alsa.  sound has been great so far.

---

### Post by gatewayasteroid on 2008-08-25
> **batman01 said:**
> Hi all,

I'm running Hardy based mythbuntu, which has been updated to within a week or so ago. Its running on a Jetway j7f2, which has the via CN700 chipset. After a long (and succesfull) battle to get XVMC working on this chipset I have run into an audio problem.

My sounds works for a period of up to a day, and then begins to cut in and out. The sound will briefly go crackly and then disappear altogether. sometimes it will never come back at all, other times it comes and goes for 2 or three seconds at a time.

I can sometimes provoke it to come back for a short while by fiddling with the DXS channel volume in alsamixer.

/etc/init.d/alsa-utils restart also seems to bring it back for a while, but then it will misbehave again.

I ran speaker-test to see if I got a similar problem, which I did, so I exited speaker test after it went silent. About 4econds after I had exited the speaker test utility I got about 3 seconds of pink-noise output. I think something is going seriously wrong with buffering somewhere.

dmesg shows nothing
/var/log/messages shows nothing
I can't find a log specifically for alsa anywhere

Can anyone suggest how I can proceed to diagnose this problem?

Thanks all,

Pete

Try lowering your volume with alsamixer, say 70% for Master and PCM, and 90% for the four VIA DXS Controls. It worked for me.

---

### Post by forest_atq on 2008-10-29
batman01,

Were you able to get sound functioning correctly?  I'm seeing the same issue.

Thanks,
Forest

---

### Post by Flecko on 2008-11-02
I have the same motherboard and have the 'sound cut out' issue with every release of any Myth distro I have tried. The only reliable way to get sound to stay on is to leave your PCM/master volume at a max of 85-90%. 

Of course, as you all probably realize this sucks because the audio output is very quiet, which means you have to crank your receiver which then introduces all the noise and chatter that come out of the motherboard. Its really annoying, but these mini-itx boards just don't put out good sound and the hardware appears to be a bit dodgy.

My solution that I'm currently trying is using a teeny usb soundcard. I got it here from newegg: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812186035&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-N82E16812186035](http://www.newegg.com/Product/Product.aspx?Item=N82E16812186035&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-N82E16812186035)

It works on my desktop, but so far on my DVR, I can only get sound output out of xine.

I'll try to post back with some more results if anyone is interested.

---

### Post by forest_atq on 2008-11-02
Hi Flecko,

Yes, I'm very interested in what ever you find.

Thanks,
Forest

---

### Post by Flecko on 2008-11-02
Well, after some mucking around, I found that mplayer doesn't play nice with this USB sound card. So what I did was set Myth to use the internal player for video, and to have MythMusic use alsa:/dev/dsp1 for music and all seems to be well.

The volume is much, much better on this card than with the built-in VIA sound hardware. And while the noise and chatter aren't completely gone, its nearly un-noticeable due to the increased volume.

So if you're looking to a low cost alternative to rebooting your DVR whenever the sound craps out, this card will work.

Best of luck all, and feel free to respond with specific questions if you have any.

---

### Post by gatecrasher on 2008-12-25
Sound in Linux has always been, still is, and always will be a complete and utter failure and tragic comedy at the very least.

Devs can rip bad imitations of the Windows desktop, but they can't seem to get sound even in the same parking lot of the ballfield as windows.

---

### Post by kostkon on 2008-12-25
> **gatecrasher said:**
> Sound in Linux has always been, still is, and always will be a complete and utter failure and tragic comedy at the very least.

Devs can rip bad imitations of the Windows desktop, but they can't seem to get sound even in the same parking lot of the ballfield as windows.
WIth all respect, but I believe you should better complain to the manufacturer of your card for not providing a driver for Linux. An email will suffice, for example.

ALSA developers try their best to make drivers for every one of the myriad of sound cars (on-board or not) that exist. It's not an easy task, when in most cases not only they don't have the slightest help from the OEMs but the opposite: no documentation, no help from them, and thus have to reverse engineer everything.

---

### Post by gatecrasher on 2008-12-25
> **kostkon said:**
> WIth all respect, but I believe you should better complain to the manufacturer of your card for not providing a driver for Linux. An email will suffice, for example.

ALSA developers try their best to make drivers for every one of the myriad of sound cars (on-board or not) that exist. It's not an easy task, when in most cases not only they don't have the slightest help from the OEMs but the opposite: no documentation, no help from them, and thus have to reverse engineer everything.

I totally agree with the above statement. 

There are probably 2 or 3 major sound card producers in the industry. Perhaps the Linux Foundation should invest in sending some sales consultants or sales engineers to those vendors and get some sort of deal worked out. Hell, get them to join some standards board or certification board (if one even exists) and then request (or better yet, make them certify) that their hardware works with the latest kernels. The MS developers provide frameworks and references that they should adhere to for the hardware to get the stamp of certification. When does that happen for Linux? Just some rants and thoughts.

/gc

---

### Post by gatecrasher on 2008-12-25
Also, I  might add, a lot of companies are formulating open source strategies. I wonder if the ALSA team has approached the main vendors of soundcard/chipsets and requested membership into the ALSA team? This would be a great long term strategy in getting proper support for hardware. Perhaps Creative and some of the others are actively pursuing these open source strategies, so I have to wonder if the ALSA team leads have made any progress here.

/gC

---

