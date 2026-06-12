---
title: "Centrino Dual Core (dell 9400) wireless networking"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by Scotland on 2006-02-01
Hi All,

Does anyone have any info on wireless connections for the new core duo chip, Intel Pro WLAN 3945 Internal Wireless (802.11a/b/g 54 Mbps)

The Intel site says Linux driver Q1, 2006 but my new laptop gets delivered tomorrow (top spec Dell Inspiron 9400).

My priorities are in order and the default install will be getting flattened and  back to my current dual boot situation on my Inspiron 4000 with XP, Unbuntu(with kubuntu-desktop) - (vmware will be coming into play as well).

Can I use any of the ip2200 drivers etc in the meantime, anyone have any experience so far with this new 3945 ? I'd rather not use ndiswrapper etc.

Dougie.

---

### Post by mips on 2006-02-01
Did some googling and found zip. You can try the ipw2200 driver as it might work but you will have no 'a' support, wont hurt to try.

If all else fails there is ndiswrapper for the next 2mnths or so.

Maybe someone else has more promising news...

---

### Post by ewjmulder on 2006-02-06
Hi,

I have the Dell inspiron 9400 for 1 week now. I installed Ubuntu a few days ago and I've been struggeling with enabling the wireless network. I too found 'Q1 2006' on the intel site, but the 2 sourceforge projects look very empty at the moment, so it might take some time...

So has anybody been able to get the card to work?
mips: Did you try the ipw2200 drivers yet? Any success?

I personally tried the ndiswrapper option. Installed ndiswrapper, used my winxp drivers, hit 'modprobe ndiswrapper' and boom: kernel panic. Something with IRQ interrupts. Beyond my tech knowlegde anyway.

So any info, experience, howto's are very welcome, thanks!

Erik
- The Netherlands

---

### Post by mips on 2006-02-06
[QUOTE=ewjmulder]
mips: Did you try the ipw2200 drivers yet? Any success?
[/QUOTE]

No, I dont have a Intel Pro WLAN 3945.

---

### Post by flagg on 2006-03-01
Intel released drivers in the last week or so

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Still no 'stable' release but a couple people have posted to the mailing list that it works for them with no or little problem. They think a stable release should be out in a few weeks too if you would prefer to wait.

---

### Post by ewjmulder on 2006-03-01
Hey thanks, I'll be sure to check it out!

---

