---
title: "Intermittent channel lock problems"
date: 2009-02-20
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-20
Most of the time I can watch TV on my Mythbuntu machine without any problems.

Sometimes, however, I can't, and I get an error message telling me it couldn't get a channel lock. I don't think this is a reception problem, for 3 reasons:

1. I have a reasonably new and good quality TV aerial
2. I can watch TV using my TV as a TV, which gets its reception from the same cable, and the picture quality is perfectly good
3. The problem has so far always been cured by a reboot.

Any idea what the problem could be? I'm using Mythbuntu 8.10 and I have a Hauppauge WinTV-NOVA-T-500 TV tuner card.

Many thanks
NM

---

### Post by scary_jeff on 2009-02-20
Have you enabled the onboard LNA for the NovaT 500? See _[here]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")_, search the page for 'activation'.

What signal strength percentage does it give when changing channels? If it's on the edge of being able to lock, it could end up being pretty random as to whether it manages to lock to a channel or not.

---

### Post by NautiusMaximus on 2009-02-21
Many thanks for that. The signal strength was mainly around 75-80%. I have enabled the LNA as per your instructions, and that didn't have any effect on the signal strength. Should it have done?

It's working OK at the moment, but since the problem was only intermittent anyway it's too early to know whether enabling the LNA has solved it.

---

### Post by NautiusMaximus on 2009-02-22
OK, that hasn't fixed it, I've had exactly the same problem again. I note that the signal strength was showing as 100% at the time.

I don't know if this is relevant, but I've noticed that the problem only seems to occur once the machine has been left running overnight. If it's newly started, I haven't yet had any problems.

Any ideas what to try next?

Thanks
NM

---

### Post by utar on 2009-02-22
The tuners on the Nova T-500 have a habit of crashing unless you tweak a couple of settings in mythbackend:

1) add 150ms tuning delay on both tuners;
2) disable EIT scanning on the second tuner.

---

### Post by NautiusMaximus on 2009-02-23
Many thanks for the suggestions, utar.

I've made the tweaks you suggested, although rather disappointingly the channel lock problem has materialised again. Is it possible that the settings need a reboot before they take effect? I didn't reboot after making the tweaks, but I have done now, so I'll wait with interest to see what happens next.

---

### Post by utar on 2009-02-23
Surprised it didn't work.  A reboot shouldn't be needed, although it certainly wouldn't hurt.  If you type dmesg into a terminal are there any lines mentioning i2c errors?

Try also selecting the option to only open the tuner when required (for both tuners).


utar

---

### Post by NautiusMaximus on 2009-02-27
Well, I think perhaps the reboot was indeed needed. I rebooted after it last failed on Monday, and it's been working just fine since then.

I'm not yet 100% confident it's fixed, but I don't think it's gone this long without failing yet, so that's certainly a good sign.

Thanks again for your splendid help.
NM

---

### Post by lofgren on 2009-03-04
Any updates on this?

I seem to have the same problem, using 8.10 and a nova-td-500.

My issue is one channel only. Signal strength is around 75-80%, BER is high, but other figures look okay.

I've disabled EIT and increased the tuning delay - still no joy on the troublesome channel.

---

### Post by NautiusMaximus on 2009-03-07
My only update is that my system still seems to be working OK. I haven't had the problem recur since following utar's advice and rebooting (thanks utar!).

If that doesn't work for you, I don't know what to suggest, but perhaps some of the Mythbuntu gurus who inhabit this place will be able to help.

NM

---

