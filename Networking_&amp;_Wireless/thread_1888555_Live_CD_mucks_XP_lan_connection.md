---
title: "Live CD mucks XP lan connection"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by bpmod on 2011-11-29
Hello

I am trying to convince a friend to move to Ubuntu, so I brought over the Live CD v11.10, booted it up, and gave a short demonstration.

But when we went back into Windows XP, the message "network cable is unplugged" pops up and there is no connection.

We have tried every fix that we have been able to find, and nothing works.

I know that **everything works fine in Ubuntu**, so why am I asking the question here?

I need to know: Does Live CD do any modifications to the existing Windows installation? If so, what might they be? And if not, what could cause this? This also happened the very first time I tried the Live CD on my own computer, but that was so long ago, I do not remember how I fixed it. (That computer is now running only ubuntu).

Thanks

Brian

---

### Post by Thad E Ginathom on 2011-11-29
Only half the answer, but it might help.

There is a Realtek LAN chip that causes endless problems like this. Ubuntu misidentifies it, and loads the wrong driver. Somehow, this leaves the chip in a state where it will not start up on a subsequent boot. This can happen with windows or ubuntu. I think the chip is RTL8168d/8111d which gets recognised as RTL8169. Or the other way around. 

The quick fix is *usually* to remove all power from the affected system. Turn off the at the PSU, or even pull the mains cable. Press the machines's power-cycle button to drain that last bit (usually the fans give a quick shiver) as if you were going to swap out some hardware. Give it a minute. Plug back in, power on and boot up. Should work. If not, try again. Try three times before you give up on this idea!

The other "obvious" thing to check is that, somehow, the on-board LAN chip didn't get disabled in the BIOS settings. Shouldn't happen --- but I've seen it.

---

### Post by bpmod on 2011-11-29
Thank you for your help. I will file that away in case this comes up again.

I had shut down the computer and disconnected the power for 30 minutes as advised by somebody elsewhere on the 'net, and upon rebooting XP, we had (only) other problems, which were a) probably caused by the fixes I had tried for the first problem, and b) easy enough to fix with my knowledge and experience. It was probably the shutdown (although I didn't do the hold-the-power-button-and-drain-it step) that fixed the initial problem.

I checked the lan settings in the bios, but concluded that that could not have been the problem, as **every** boot into Ubuntu was good, and **every** boot into XP was bad.

Thanks again

Brian

---

### Post by Thad E Ginathom on 2011-11-30
Ahhh... you were there before me :)

Anyway, this Realtek chip thing continues to be a nuisance, and a mysterious one, for many so at least it has had another mention that might point its sufferers in the right direction.

Glad you fixed your issue.

---

