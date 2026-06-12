---
title: "Yet another &quot;Best Graphics Card?&quot; post"
date: 2008-07-14
forum: Mythbuntu
---

### Post by yonkiman on 2008-07-14
I'm building a new backend (my current one's a bit underpowered whenever it has to do more than one thing at once).  After a lot of looking, I'm pretty happy with my MB and CPU choices:
[LIST]
[*]DFI BloodIron P35-T2RL LGA 775 Intel P35 ATX Intel Motherboard
[*]Intel Core 2 Duo E7200 Wolfdale 2.53GHz
[/LIST]
But I need a new PCIx graphics card since my AGP Nvidia 6200 won't fit.

Out of habit based on the last several years of recommendations, I was going to go nvidia, either the 7x00 or 8x00 series (8400GS 512MB is only $32 at newegg), but two things are making me reconsider:
[LIST=1]
[*]I've never been able to get the overscan adjusted using my nvidia card and the proprietary nvidia driver.  I use the component output (720p), and "TVOverScan" option has never done a thing.  I think perhaps it's for svideo and composite only.  The driver doesn't seem to accept custom modelines either.  The hardware's fine - it was no trouble creating a custom resolution in WinXP with Powerstrip - but there doesn't seem to be any way to do it with the proprietary nvidia driver.  So I don't really want to build a new system, buy a new card, and be stuck in this same irritating place.
[*]I read about how AMD/ATI is finally going to properly support linux with decent drivers ([http://tinyurl.com/5uwp4c](http://tinyurl.com/5uwp4c)).  I know that's not a lot to go on, but what are the odds that nvidia ***and ***ATI are both ignoring custom modelines?
[/LIST]

So what do you people think?  

Should I give more money to nvidia because their drivers are "better" (even though their drivers don't allow me to see the linux taskbar or anything else on the outer 5% of my screen?)?

Or should I roll the dice and give AMTID a chance?  

How bad are the ATI drivers currently - will they be adequate given the reasonably high horsepower of my new CPU?

Along those same lines, if I have the CPU power, could I use the open-source nvidia (or ATI) drivers (which presumably don't ignore custom modelines) and get excellent 720p playback?

---

### Post by silkstone on 2008-07-14
I can tell you that the 8400GS works out of the box on Hardy - that's what I'm on right now (mine also has 512MB).

The screen resolution etc was fine right after a clean install of Hardy, and I then let it automatically install the restricted drivers. Desktop effects seem to work although I didn't try them all, but I'm not an eye-candy fan so I have them turned off. I've also installed nvidia-settings.

I'm on a 22" widescreen at 1680x1050 and 2-D graphics are good. The 8400GS is a fairly basic card and is not up to 3-D games at this resolution. You might consider something like a 7600GT which has better performance.

I can't answer either of your specific queries since that's not something I've tried, and I've no experience of ATI on Ubuntu.

---

### Post by yonkiman on 2008-07-14
> **silkstone said:**
> I can tell you that the 8400GS works out of the box on Hardy - that's what I'm on right now (mine also has 512MB).

Thanks.  It sounds like your experience was similar to mine (it all works great out of the box), but I'm guessing you aren't using the component output and having to deal with the overscan.  I wouldn't have a problem if I had a flat panel TV/monitor with an HDMI/DVI input...

---

### Post by jaakan on 2008-07-14
I just got the 8400GS 512MB from newegg last week. it's currently connected via VGA but It'll soon be connecting it via DVI. HDTV and DVDs looks great so I'm happy with it. I'm only running at 720p with my Flat Panel.

---

### Post by silkstone on 2008-07-15
> **yonkiman said:**
> Thanks.  It sounds like your experience was similar to mine (it all works great out of the box), but I'm guessing you aren't using the component output and having to deal with the overscan.  I wouldn't have a problem if I had a flat panel TV/monitor with an HDMI/DVI input...

That's right - I'm using an LG L226WTQ with DVI input.

---

### Post by ian dobson on 2008-07-15
Hi,

On my main "live" frontend I'm using a Nvidia7300 over S-VIDEO to an analog TV and everything works quite well. 

On a test box that I use to tryout various SW hacks I have an ATI X1600 connected to a LCD monitor and the picture quality is really bad for live/recorded programs (Bad horizontal lines, movement artifacts and generally bad play back.)

So I'd say a Nvidia card 7000 series is a good bet. You don't need a really high spec. card. Even though ATI/AMD talk alot about their "open source" drivers/documentation I've not seen much progress in the real world when it comes to Linux drivers.

Maybe one day things will be different, but at the moment I'd stick with Nvidia on Linux.

Regards
Ian Dobson

ps I'll be trying out a 8600gs in my frontend sometime soon, I don't really need it but it's an interesting experiment for me.

---

