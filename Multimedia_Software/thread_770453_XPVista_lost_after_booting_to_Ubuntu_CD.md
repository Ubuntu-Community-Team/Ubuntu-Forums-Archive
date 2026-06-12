---
title: "XP/Vista lost after booting to Ubuntu CD"
date: 2008-04-27
forum: Multimedia Software
---

### Post by cwharts on 2008-04-27
I have a dual boot/dual display Dimension 8400 with 2 flat panels. Everything was working fine until I booted to the 7.04 Ubuntu CD yesterday. In Ub, both displays were still working fine. However, after shutting down properly, I rebooted to XP, no left/primary display once past boot screens. Rebooted and tried Vista and have the same issue. Reset monitor, unplugged, replugged, reinstalled drivers. Monitor light is Amber (once either OS is fully loaded.)

Why would Ubuntu do this and how do I resolve?

Thanks,
Chris

---

### Post by crossy on 2008-04-27
I'm a little confused here... your title seems to suggest that you've lost your Windows stuff, but the text seems to say that it's only the dual-head stuff that's not working post Ubuntu-ing.
I'm going to assume that it's the latter*, (*if it's the former then I apologise*). :confused:

Right, I've got a Dell (Latitude) in a dual head configuration with XP Pro, and I've got to say that something upsets the dual-screen configuration about once or twice a month. So I've just put it down to "one of those Windows things". :(

You say that the rebooting the monitor just gives a yellow/amber light - this is usually monitor-speak for "I can't find a signal - so I'm on powersave".

What to do next? I'd go into XP/Vista and try setting up your dual-head configuration again (Right-click desktop and then use Display->Properties->Settings?) Actually, maybe try setting up a single-head (different to the normal one) first, then try the dual-head.

Last thing - again assuming that Vista/XP _is_ still viable - I can't think off-hand of something that Ubuntu would do that would change _just_ the Display setting. If something does go badly wrong then - in my experience - it's more likely to totally hose your Windows install than do such a clever selective edit.

Hope this helps, crossy.

(* just had parting thoughts - if the problem is that there's no display at all in Windows, what about trying to booting into XP Safe Mode? Or - like laptops - is there a key combo available that lets you switch displays ... *just a thought*)

---

### Post by cwharts on 2008-04-27
I should have said "XP/Vista Display issue". Sorry, and thank you for figuring it out.
So I did at first try to re-enable the second monitor. It acted weird though. At first, I could click 'extend' but once I clicked 'primary monitor' both lines grayed out and wouldn't come back. If I applied or clicked Ok, it would act normal from a driver perspective, but the monitor stayed in the sleep mode. Now after rebooting, the driver doesn't even see the primary monitor and there is no second monitor to select. Similar behavior was in Vista.

I rebooted to the Ubuntu CD and it has dual monitor display (cloned.) Diagnostics/VGA mode work fine on second monitor. It only stops working in Vista/XP at the Log-on screen or further.

Thanks in adv for any other ideas. Am going to try a restore point to see if that helps.

Chris

---

### Post by crossy on 2008-04-28
Hi Chris (*that's my brother's name too!*)

Nothing comes to mind at the moment (and because laptop and other screen are now separated by about 25m it's a little difficult to test). :-(

One question - you say you're booting to CD - does that mean that this is an XP/Vista+Ubuntu Live CD. Or, have I screwed up again and got you wrong? (*I know, sometimes I'm as dumb as a stick*)

Wierd that it's only Windows that's lost connection to your left monitor - and two separate Windows OS's make's it doubly wierd. I'm wondering if there's something 7.04 is doing to the monitor configuration itself - I'll have to read up on the DDC connection. I was _really_ tempted to suggest swapping over the monitor connections to see if it's something about the particular monitor or it's location in the system - but, on reflection, that's maybe a wee bitty daft.

Regards, crossy.

---

### Post by cwharts on 2008-04-28
Crossy - thanks for the response. Yes, I am using Live CD, but actually the term is new one for me. I didn't install Ubuntu, just booted to the CD. The monitor still works on the smaller (vga?) port if I use the connector from my second monitor. I suspect that my ATI/x1300 card is blown for the DVI output, at least in non-vga mode. (I also assume Ubuntu uses VGA display?) I also notice that the 'white' in vga are more orange in color than they used to be. I tried to find a detailed diag for the card but can not. Any ideas?

---

### Post by cwharts on 2008-04-28
Crossy - thanks for the response. Yes, I am using Live CD, but actually the term is new one for me. I didn't install Ubuntu, just booted to the CD. The monitor still works on the smaller (vga?) port if I use the connector from my second monitor. I suspect that my ATI/x1300 card is blown for the DVI output, at least in non-vga mode. (I also assume Ubuntu uses VGA display?) I also notice that the 'white' in vga are more orange in color than they used to be. I tried to find a detailed diag for the card but can not. Any ideas?

---

### Post by cwharts on 2008-04-29
An update to my situation - I put my old X300 card back in the system and the problem is the same. In the non-VGA mode, left screen switches to sleep mode, amber light. Vista doesn't even see the monitor. Any Master reset for an FP1701? I tried resetting to factory settings. Could it be DDE? Is there any 'reset' for flat panels? Would a Diag for the monitor be available?

Any other ideas? Hate to give up on digital input on that display, especially since I have to find a convertor connector.

Thanks,
Chris

---

### Post by crossy on 2008-05-05
Sorry for the delay - I didn't find the option to subscribe to threads until now, so I was trying to find this thread manually. :oops:

Okay - a "live cd" _should be_ a "zero footprint" install. Which basically means that stuff that would normally come/go-to the HD is either on the CD/DVD or in memory. I'm an ex-Solaris admin and this is the way that this OS has operated for years when you use a "miniroot boot". Anyway, as interesting as this maybe, it's little help to you!

So basically, what I'm trying to say is that the LiveCD doesn't save anything on your machine unless you actually do it yourself explicitly (e.g. mount a filesystem and edit/save stuff)

As to the other matter - sorry I know zip about the FP1701. That sounds suspiciously like a Dell monitor id, in which case have you checked their support site. Not that I claim to be a major league expert (unless you're a paying customer of mine, in which case, I know everything about everything ... LOL), anyway this is beginning to sound like a possible cable fault.

**Anyone out there in Ubuntuland have any other theories??** :guitar:

If it _is_ a cable fault, and it's not a captive cable, (invention of Satan imho), any chance of borrowing another cable and trying it?

I'll try and ask around here at the office, maybe one of the hardware guys will have an inspiration.

All the best, and apologies I can't be more positive at the moment.
crossy.

---

