---
title: "Can't enable 3d acceleration on XP over VMware"
date: 2010-04-06
forum: Multimedia Software
---

### Post by varunendra on 2010-04-06
I'm using Ubuntu 9.10 (Karmic Koala) & recently added Ubuntu Studio to it.
For quite some time, I'm trying to enable direct 3d acceleration on a virtual XP SP3 machine running over VMware Workststion 7.0.1.

As per VMware forums & many other sites, **3d hardware acceleration is supported for XP** as guest **provided that host Linux version is supported by the VMware product** running that VM.

The forum also says that **Ubuntu 9.10 is now supported by Workstation 7.0.1**.

So:

[LIST]
[*]I have a supported version of host (Ubuntu 9.10)
[*]XPSP3 as guest.
[*]Latest version of VMware tools installed.
[/LIST]
Still I don't get hardware acceleration for the guest XP VM. Where am I going wrong?

I didn't ask at VMware forums 'cause it doesn't seem to me as helpful as this one.

Thanx in advance for any response.

---

### Post by varunendra on 2010-05-06
It's now 4 weeks & 186 views so far to this thread.
Anybody?

Oh... well.... there's an update:
I also tried Virtualbox a while ago & followed the instructions given in its manual to enable 3d acceleration. Then in WinXP(SP3) virtual machine's DirectX diagnostics, 'Direct3d' appears enabled, but all its tests fail.
The system is 2.8GHz Intel DualCore with 512MB RAM, and the onboard graphic adapter supports DirectX9c !

I only need this for gaming. Can go with any solution- be it VMware, Virtualbox or something else.

---

### Post by splicerr on 2010-05-06
Intel  onboard graphics adapter?

---

### Post by varunendra on 2010-05-06
Yes. It's Intel 865G Chipset. Those games & everything runs fine when XPSP3 is run natively.

---

