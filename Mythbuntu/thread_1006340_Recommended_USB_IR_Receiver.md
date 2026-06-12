---
title: "Recommended USB IR Receiver"
date: 2008-12-09
forum: Mythbuntu
---

### Post by SiHa on 2008-12-09
I've got my Frontend working nicely, with a homebrew serial IR receiver. The only minor problem with it is that I have to get off my rear bring it out of standby.

I've read that USB receivers can be used to wake the PC (assuming the mobo supports wake-on-USB), so I'm wondering if anyone has any experience with any cheap receivers?

I've seen the Cyberlink MC remote and receiver for £5.75 [_[COLOR="Blue"]here[/COLOR]_](http://www.ebuyer.com/product/129977/show_product_reviews?offset=10&review_type=both&review_order_by=RUF)

Has anyone used one of these with Myth? Ideally I'd like to use my existing one-for-all learnt as a Hauppauge remote, so I have the same lircrc for both my machines.

Any ideas greatly received

---

### Post by EasyRiderOnTheStorm on 2008-12-09
I'm only scratching the surface myself about this (same boat, the tuner's remote can't wake up the box), but have you considered making one...? :) I've found some interesting stuff about PVR vs. wake-up by remote [[here]("http://gbpvr.com/pmwiki/pmwiki.php/Tips/RemoteWakeUp")]; Also, I think there are some non-usb-based solutions as well - such as the [iMON inside]("http://www.soundgraph.com/Eng_/Products/imon24.aspx?topMenu=2&subMenu=1&leftMenu=24") / VFD - that do not rely on BIOS or powered-during-standby USB ports.

---

### Post by SiHa on 2008-12-09
Thanks - yes, I have considered making one, but I really can't be **** with having to program a uP, even though we've probably got the hardware to do that at work. The homebrew serial is easy, USB is a bit more complicated. As the cyberlink is so cheap I was considering that as the easy option.

Thanks for the links, the German offering looks interesting, as does the imon inside, both are probably on the pricey side though. I'm looking for cheap!
Think I'll probably have a go with the Cyberlink. Will report back when I have anything.

Cheers,

Simon

---

### Post by xyzacct on 2008-12-09
I'd like someone to suggest one also. I already have a remote (logitech 550) so buying a combo would be useless. Just a USB IR receiver is all I need.

---

### Post by anonymousdog on 2008-12-10
The cheap MCE USB remote/receiver/blaster combo is purported to work for this, [http://www.mythtv.org/wiki/index.php/MCE_Remote#S3_.2F_Suspend_To_RAM](http://www.mythtv.org/wiki/index.php/MCE_Remote#S3_.2F_Suspend_To_RAM).  I haven't tested that as the only frontend I have with a remote doesn't support the needed motherboard power options.  I believe that would be one of those solutions where any remote button would wake the machine.

---

### Post by ttabbal on 2008-12-10
I can't help with USB (yet, I'm considering building some for myself. If I do, I might be convinced to sell some to the comunity.). Have you considered using your soundcard? Most motherboards come with one, and it's unlikely you need the mic port for anything anyway. 

[http://ubuntuforums.org/showthread.php?t=477958](http://ubuntuforums.org/showthread.php?t=477958)

---

### Post by jbman on 2008-12-11
i would love to buy one that does not pic up the radiation from my screen. Mine flashes all the time when the TV is on and sometimes interferes with the signal getting to it.

---

### Post by wizgnome on 2008-12-11
When I built my Myth Box a couple of months ago, I got one of the cheap Media Centre compatible remotes advertised on ebay. I found the remote emulated two USB devices, a keyboard and a mouse. It worked ok for some of the buttons which sent single key codes, but a lot of them sent multiple codes, which I was unable to map in mythtv - it only saw the first code. Also I did manage it get it to work partially with lirc, but still did not get enought buttoms to work.

In the end I gave up and purchased a genuine Microsoft RC6 receiver. This worked straight of the box and I was also able to use it with my Logitec Harmony remote that I was using for the normal tv, dvd video etc.

---

### Post by ttabbal on 2008-12-11
> **jbman said:**
> i would love to buy one that does not pic up the radiation from my screen. Mine flashes all the time when the TV is on and sometimes interferes with the signal getting to it.

I've seen sensors that claim to eliminate false signals like those you are seeing. They also shorten range, but I think those with this problem would consider that a valid trade-off. I'll order a couple and experiment. 

I'm shocked that there isn't a reasonably cheap USB IR receiver. It's not like the parts are super expensive. Even a custom PCB isn't bad. Adding blaster capability would be damn near free as well since there are going to be pins available on most any USB capable micro. Of course, I doubt it will be possible to compete on pure price with even the remote/receiver combo packs. Small runs are always more expensive. But once could at least guarantee LIRC compatibility so there's no guessing game involved.

---

### Post by SiHa on 2008-12-11
> **ttabbal said:**
> I can't help with USB (yet, I'm considering building some for myself. If I do, I might be convinced to sell some to the comunity.). Have you considered using your soundcard? Most motherboards come with one, and it's unlikely you need the mic port for anything anyway. 

[http://ubuntuforums.org/showthread.php?t=477958](http://ubuntuforums.org/showthread.php?t=477958)

Thanks, but I'm after a solution that will wake the thing out of standby - this requires a device that can bring the system out of standby - don't think the soundcard will do that. I'm already running a homebrew serial setup.

---

### Post by SiHa on 2008-12-11
> **jbman said:**
> i would love to buy one that does not pic up the radiation from my screen. Mine flashes all the time when the TV is on and sometimes interferes with the signal getting to it.

It is a 'generic' receiver - ie not one that came with a remote, it may have more than one receiver in it, to pick up the widest range of transmitted carrier frequencies.

If you take it apart and find that this is the case, you could try masking off each one in turn, to see if it's one in particular that is causing the problem. If you're lucky it won't be the one you also need for the remote!

---

### Post by EasyRiderOnTheStorm on 2008-12-11
> **jbman said:**
> i would love to buy one that does not pic up the radiation from my screen. Mine flashes all the time when the TV is on and sometimes interferes with the signal getting to it.

This is a bit strange, though. Normally, IR signals use a carrier frequency around 38KHz, which means that unless you have a source of IR vibrating at ~38KHz, receivers never see it. I wouldn't think your screen can produce anything like that. Unless you have some sort of two-way IR remote or IrDA device operating in the area, or the receiver includes some kind of non-modulated IR receiver too. Puzzling...

---

### Post by SiHa on 2008-12-11
You'd be surprised - Flourescent tubes are known to cause interference like this.

Actually, you'll find the allowed frequency for most TV's is roughly 30-60kHz. 720 (for 720p display) x 50 (50hz refresh) = 36,000! Most 38KHz receivers will pick up 36kHz, just at a lower sensitivity.

JBMAN - If you can change your refresh rate or resolution, it might be enough to stop the inteference.

---

### Post by jbman on 2008-12-15
My TV is connected via VGA and there is only on res which is 1368x768x60hz.

I might borrow a friends MS combo and try and see if his gets the same pickup as what I am experiencing from my unit.

---

