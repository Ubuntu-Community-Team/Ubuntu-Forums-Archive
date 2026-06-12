---
title: "BCM4312 broken after update"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by kbm on 2009-10-01
I running Kubuntu 9.04 and everything had been going just fine.  I ran an update last night and now my wireless network card is not connecting.  It still shows up with an lspci, but when I try to connect to my existing setup, or detect networks, nothing, like it's not even there.

The hardware drivers tool says that I'm using the proprietary Broadcom STA wireless driver.  Says the driver is active.

Items I got with my last update:
[LIST]
[*]libneon27
[*]libneon27-gnutls
[*]libnewt
[*]libpq5
[*]python-newt
[*]whiptail
[/LIST]

My syslog states some stuff about "deactivating device (reason: 2), but I don't know if that was there when it was working or not - or what it means.

If I connect my hardline, networking starts right up.

Anyone else see this recently (my last update was only a few days ago)?  Any advice would be appreciated.

I'm doing another package update on the system now just in case (although I don't see anything new that makes me think it will help).

---

### Post by kevdog on 2009-10-01
Can you post the relevant lines from dmesg?

---

### Post by kbm on 2009-10-01
Ok, went on a short trip on the crazy bus there.  I was running out of ideas, so I decided to boot to Vista to make sure my card didn't just up and die on me.  Vista could not connect either, but said the card was there and running.  I asked it to diagnose the problem and it told to to enable wireless (via switch on laptop or something) so I hit the wireless function key (F2) and boom, it worked!  Rebooted and Kubuntu worked too.

Now, the question is - how did that happen?  My wireless function key does nothing in Kubuntu.  I did change my bios last night to treat those keys as function keys first (F1-12) and then as media/control/whatever keys.  Changed it back as part of my debugging when my wireless died - didn't make a difference so I didn't give it another thought.

I know that this model Dell has an issue where ACPI control dies pretty quickly after startup (i.e. monitor brightness keys and AC power detection stop working).  I can only assume that some combination of issues managed to shut off my wireless card.  I don't remember hitting the F2 key (with or without the Fn key), but that's the only thing that I can think could have done it.

Is there a way to check that sort of thing?

How about a way to turn wireless back on.  I was lucky in the fact that I kept Vista around (now booted up twice :) ) - but what if I had dumped it?

Anyway, I hope this can at least help some other hapless soul that winds up with no wireless :rolleyes:

Don't know that it's relevant, but now every few boots, and it thinks that a TV is attached (starts in 4:3 perspective), fixes itself (with a bit of flashing) as soon as I go to System Settings -> Display.  Just kind of weird.  Maybe it always happened and I just didn't reboot non-stop like I did when testing this card.

P.S. thanks for the post kevdog.  I looked in the logs and the only thing I saw was the "reason 2" thing.  Which may be dmesg speak for "you turned off your card you tool".

---

### Post by Bucky Ball on 2009-10-01
Interesting. I have no idea whether the updates were connected but updated, next time I boot up my laptop the card and drivers are gone completely. Not even in lspci. Nothing. No sign. Boot to windows, same. Nowhere to be seen. 

This is probably a known problem with the HP laptop but strange how updates could possibly be the culprit for a card kill.

Yes, Broadcom card.

---

### Post by kbm on 2009-10-02
Well, it has come to my attention that most laptops have an LED indicator that shows if the wireless adapter is active or not.  My Dell 1555 (studio 15) has been knocked in several reviews for not having any LED indicators (HD, CapLock, etc.).  So it is more a function of my laptop than a general issue that I could not see that my card was deactivated.

Still looking into the 'I think a TV is attached' issue, but I think that it has to do with when the known ACPI issue occurs.  If it is early enough in the boot process, it thinks that a TV is attached.

I'll call this one closed.

---

### Post by Bucky Ball on 2009-10-02
Call it 'solved' and mark from 'Thread Tools' please. :)

---

