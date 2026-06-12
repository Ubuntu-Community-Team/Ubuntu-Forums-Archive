---
title: "Console dead, nvidia stac in dmesg. Hardware? or Software? 12.04 LTS 3.2.0-63-generic"
date: 2014-06-26
forum: Multimedia Software
---

### Post by ArlieS on 2014-06-26
This morning, my monitors went dead. I ssh'd to the box, found no sign of X running, and tried to reboot "sudo shutdown -r now". The reboot hung, and I resorted to the power switch. I forget the exact sequence of events, but in the course of debugging I had an incident where the system came up, with monitors, then lost them, and another incident where it simply didn't come up properly. 

Checking dmesg and /var/log/kern.log got me sof tlockup and NMI messages from the kernel. Symbols beginning with _nv are prominent in the stack traces. The whole things smells as if the nvidia graphics driver is in difficulties, and in particular, is hanging in kernel space. I've attached samples of each as txt files; the rcu_sched message is in 2 parts due to limitations on upload size.
My problem is to try to figure out whether I'm dealing with:

- malfunctioning hardware, combined with a stupid driver that doesn't handle this failure mode nicely
- an out and out driver bug 

For added confusion, if it's hardware, it would be useful to know which hardware is broken. Obvious candidates include my graphics card, but also the kvm that connects monitors to computer. I've pretty well excluded loose cables, even though someone was in my office yesterday dusting, and could easily have moved something - I pretty much reseated everything after problems started appearing. 

This is a system 76 desktop with Ubuntu 12.04 LTS. It has never given me problems of this kind - all my Ubuntu graphics issues have been with laptops.  I've installed updates fairly regularly, with the result that the kernel I'm running claims (in uname -a) to be  3.2.0-63 generic #95-Ubuntu SMP. The system has 2 monitors connected to it via a DVI KVM. A Windows system is on the same KVM sharing the same monitors.

The windows system is not behaving 100% normally either. It was fine at first, but then it stopped displaying on one of its monitors, and when rebooted appears not to have detected that monitor's presence. It can, however, see the second monitor. Resetting (power cycling) the kvm doesn't seem to have helped it, though it did seem to help the Ubuntu system - which then worked just long enough for me to get my hopes up ;-) [However, I also rebooted the Ubuntu system at the same time, so no proof it was the KVM reset.]

The logical bet seems to be the KVM, given that the windows box is also complaining - but the kernel messages are making me hesitate. Just how stupid is that driver?  (Dealing with failing hardware by wedging the system isn't generally regarded as sane behaviour.) Also, the windows box has a history of graphics issues - I believe its graphics cards are somewhat flaky. 

Any ideas, beyond the obvious - disconnecting the KVM to see what happens? (I'll try that tonight - presently posting from work.)

---

### Post by ArlieS on 2014-06-27
It does not appear to be the KVM. There have been no farther incidents involving the windows box, and I replicated the problem with the main monitor, keyboard etc. directly connected to the Ubuntu box. (However, IIRC, the connector from computer to 2nd monitor was still plugged into the kvm, after I discovered I didn't have a suitable cable to go direct from that monitor to the computer. Again IIRC, that monitor was not connected to the KVM at the time.) 

After I applied all pending updates (From Jun 1-Jun 26) to the Ubuntu box, the symptoms changed - now I get compiz crashes, with the main monitor coming back with VGA-ish resolution, and various keyboard shortcuts (e.g. to change workspace) no longer working. Those can be cleared up by logging out, without rebooting. This included a kernel upgrade, to 3.2.0-65-generic #98.

The system had been up too many days since my last software update for me to be happy blaming a software bug - and the timing of the change may be coincidental. So I'm baffled. Any ideas about debugging this kind of thing? If I had a spare graphics card, I'd replace it just to see what happens, but I don't. The other option that occurs to me is to get rid of the proprietary nvidia driver. Or to contact my hardware vendor, but I'm pretty sure the system is long out of warrantee.

---

### Post by tfurfaro on 2014-08-11
I don't know if it's quite related or not, but I had an issue with X and the related bits that had to do with display/resolution detection. I haven't had confirmation yet that it's a EDID decoding problem, but long story short, I was able to revert to a normal working state by booting with 3.2.0-61 instead of *65. For me the direct implication was messed up auto-detected resolution, but X also handles some shortcuts, so it could be similar thing.

---

