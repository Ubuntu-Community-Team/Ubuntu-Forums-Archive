---
title: "Reliable reboot"
date: 2019-05-15
forum: MINT
---

### Post by arwdcs on 2019-05-15
Hi:

I am considering upgrading from Ubuntu server to Mint, in an attempt to get extra value out of one of my server machines.  One of the things that really worries me is remote rebooting of the machine: I have already suffered a hanging reboot with Ubuntu Desktop that caused me a lot of pain.  My big issue is that I travel sometimes for weeks on end, and although I can remote access and remote update these devices, when I do so, I sometimes need to reboot them to make the changes take effect.  These machines provide services for a small business, so I really need them to work.  For compliance purposes, it's difficult to run a server that has NOT been rebooted if it requires it.  But if I am away, I can't do a power-off/on when it all goes to pot.  My servers are all LUKS encrypted, so I need dropbear to work after a reboot, just to make it more complicated.  And it does...except when the machine hangs.  I have evaluated Mint, and it IS better than regular Ubuntu Desktop, butI have had two failed reboots in two weeks.  I am uncomfortable with that.  I do not use proprietary drvers, but it is still more challenging to use ANY desktop than a straight server insta.  Is that a common experience?

I am aware of 'sudo reboot -f' as an option but it's VERY drastic and potentially bad news for running services.

Does anyone know of something MORE RELIABLE than 'sudo reboot' that is maybe not as drastic as 'sudo reboot -f'?

I know I can go back to a straight server install (which to be honest has never failed to reboot), but I would really like to do more with at least one of my hardware platforms.

Thanks for any replies.

Andrew

---

### Post by TheFu on 2019-05-15
If you need uptime, don't put a GUI onto a server.

If your infrastructure and hosting setup can't support the SLA, then either fix the SLA (lower it) or move to someplace that can and hire people to back you up for those periods when you don't want to work. 'Best effort' is reasonable, but only if the customer understands what that really means.

---

### Post by arwdcs on 2019-05-18
Sadly, that seems to be my conclusion too.  I hate to waste my resources so much, but I do indeed need a reliable server.  Maybe one day I can get the best of both worlds but not today.  Thanks TheFu!

---

### Post by TheFu on 2019-05-18
> **arwdcs said:**
> Sadly, that seems to be my conclusion too.  I hate to waste my resources so much, but I do indeed need a reliable server.  Maybe one day I can get the best of both worlds but not today.  Thanks TheFu!

Pretty much any server today can be a VM host. Then you can run multiple VMs, get the crazy flexiblity that provides, have different services segmented apart, and one of those VMs can contain a lite-desktop, if you like.  

My daily use desktop machine is actually running inside a VM on a headless server and accessed from anywhere in the world using x2go or ssh.  I've been doing this since around 2008.  There are some tradeoffs, but I decided the extra flexibility was worth it to me.  It has been.  YMMV.  VMs don't impact the stability of the server they are running on, at least not if you use KVM.  

I've been burned by Xen and VirtualBox on stability.  Vbox locked up the entire host. That same host was converted to KVM and has been running 24/7/365 since 2010. It is running today, hosting VMs still. No stability issues that weren't hardware (loose SATA cables). I'm about the retire it for a new machine.  Used ESXi for a few years, but it was really, really, really, picky about hardware and refused to run on all but 1 of my systems.  Xen was pretty stable, when it would boot. There were times when it refused to boot. I had 15 production VMs on a system, patched it, it needed rebooting. Refused to come up. Troubleshooting production issues, unexpectedly sucks. Especially when the entire machine is impacted.

---

