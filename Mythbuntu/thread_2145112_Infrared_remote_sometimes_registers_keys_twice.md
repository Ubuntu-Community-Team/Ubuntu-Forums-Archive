---
title: "Infrared remote sometimes registers keys twice"
date: 2013-05-14
forum: Mythbuntu
---

### Post by EasyRiderOnTheStorm on 2013-05-14
I've recently upgraded my old but flawlessly working 8.04 mythbuntu box (yeah I knew there would be hell to pay the instant I touch it, hence the procrastinating) to 12.04 - basically there's nothing left on it that wasn't broken in some way in the process (pretty much as expected), but currently it's more or less functional (for modest values of "functional"); Myth GUI / video playback / Mythweb etc. seem to be running acceptably well at the moment.

The infrared remote (with a receiver built into the TV tuner card, a Philips compatible Asus "My Cinema" P7131 Hybrid) was a different story, it just stopped working so after a long convoluted process I discovered the built-in kernel lirc driver (which supports this remote) and promptly removed lirc completely. Currently the remote is working mostly fine, except for the "back" and other special buttons, which I learned can be tinkered with / remapped using ir-keytables - a thing I fully intend to do sometime soonish.

However, this bring us to the point: right up front I noticed sometimes keypresses from the remote register twice, as in moving two menu entries instead of one for one button press. Now, to make this as clear as possible and avoid confusion with the countless posts about apparently similar but clearly different problems: I do NOT get every keypress twice all the time. I don't even get SOME of the keys twice all the time. What I get is SOME RANDOM key detected twice, SOME of the time (rather annoyingly often, though). I'd like to note that two different remotes do the exact same thing, and they were both fine before the whole upgrade thing.

The phenomenon is specifically remote-related (it never happens using the keyboard to navigate), it's NOT a keypress-repeat setting issue, and is clearly visible as early as the "ir-keytable -t" level: every time the glitch happens, a second set of "key down" and "key up" events are detected (not a "key continuously pressed" event, those are a different code), the immediate millisecond following the "real" set of events. This is in itself telling - actual keypresses, even fast ones, have a few hundred milliseconds between each other; these "phantom" doubles however occur instantly after the real "key up" - which leads me to suspect this might actually be a bug in the kernel's built-in lirc detector / protocol decoder. Any ideas...?

PS - I'm currently trying to avoid this by activating Bounce Keys with a very small time interval - it does a nice job of preventing the "instant" doubles getting through, but since apparently after such an event BK has a small "stand-off" period in which nothing gets through, it implies having to scroll through things rather sloooooowly; the constantly occurring "bounce hits" triggered by the frequent double detections apparently keep activating that stand-off, so fast-ish scrolling is impossible. It's much nicer than runaway menu navigation, but I'd obviously prefer to get rid of this completely...

---

### Post by JasonEde on 2013-05-21
I had the same problem.... Looking in /etc/lirc and I think the lircd.conf it refers to a code file that is in /usr/share.

I edited this file to make sure it contained just the one remote that I had (used irw to make sure got the right one) and then restarted and problem solved.

---

### Post by EasyRiderOnTheStorm on 2013-05-21
Yes, well: thank you for trying to help. No, that was not the same problem. As I explicitly emphasized, this is not a case of all keypresses being received twice via two different "routes" - it only happens randomly, with random keys. I don't even HAVE lirc installed, nor irw or the other tools. ONLY the built-in kernel driver is handling IR, and by the looks of it, its decoder is seriously shoddy - but I can't prove that: when it comes to serious coding, I can't brain - I have the dumb, unfortunately.

---

### Post by JasonEde on 2013-05-28
Have you checked in [http://www.mythtv.org/wiki/LIRC#Double_presses_for_certain_buttons](http://www.mythtv.org/wiki/LIRC#Double_presses_for_certain_buttons) to see how the kernel is listening?

---

### Post by EasyRiderOnTheStorm on 2013-05-28
Look, no offense, but which part of "I have NO lirc AT ALL, it's UNINSTALLED - and ONLY the kernel is listening" is hard to understand...? I KNOW the net and all the forums are full of people who have SOME keys work twice ALL THE TIME because two different channels receive them - but I definitely only have ONE (which reports repeats happening all by itself on its own channel via irkeytable - not connected to lirc in any way), and even repeated keys are repeated only SOMETIMES, particularly when I start pressing them quicker, which is the hallmark of a decoder-type problem. Out of the 1001 complaints, this is the 1 case, not the other 1000 - which I tried to emphasize, twice now. I can Google too.

PS ...and no, it's not the remotes issuing repeats either - this started only and immediately after the upgrade to the new OS, never happened before with the same (two different) remotes.

---

### Post by JasonEde on 2013-06-03
Yes, but that link above will give you the means to see exactly what is being bound and then can trace it through. If you know what is listening to what device (IR sometimes show up as multiple devices as that link shows) then you can trace it through the system easier.

---

