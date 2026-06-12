---
title: "ATI Radeon x850 XT Platinum Edition driver questions"
date: 2010-05-12
forum: Multimedia Software
---

### Post by teejay17 on 2010-05-12
I am running Lucid Lynx x86 and I have an ATI Radeon x850 XT Platinum Edition card. It seems to be working well out of the box. I have not yet tried any gaming though. 
However, I'm just wondering if I should install the driver found [here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.16&lang=English")? Would this make things better? Would it make things worse? Also, what sort of installer is this...would it automatically start in Lucid Lynx? 
I look forward to hearing what others think about these questions.

---

### Post by Yellow Pasque on 2010-05-12
No, don't install the proprietary driver (aka fglrx/Catalyst). The older version required for your card does not work with Lucid.

---

### Post by teejay17 on 2010-05-12
> **Temüjin said:**
> No, don't install the proprietary driver (aka fglrx/Catalyst). The older version required for your card does not work with Lucid.
Great, thanks for the heads-up. I'm sure glad I asked in advance--saved a lot of headache. 
So gaming should work fairly decent then? I'm not expecting jaw dropping goodness, but adequately smooth graphics will suffice.

---

### Post by teejay17 on 2010-05-13
> **Temüjin said:**
> No, don't install the proprietary driver (aka fglrx/Catalyst). The older version required for your card does not work with Lucid.
What doesn't work, anyway?

---

### Post by Yellow Pasque on 2010-05-13
> **teejay17 said:**
> What doesn't work, anyway?

The legacy Catalyst driver does not work with newer Xservers.

---

### Post by teejay17 on 2010-05-15
> **Temüjin said:**
> The legacy Catalyst driver does not work with newer Xservers.
Does any new ATI driver work for this particular card? Or should I just leave it as-is, with whatever Ubuntu is currently using?

---

### Post by teejay17 on 2010-11-20
> **Temüjin said:**
> The legacy Catalyst driver does not work with newer Xservers.

How about now? Any updates for my particular card since the last time I checked in? Or should I sill leave everything as-is?
I'm still using Ubuntu 10.04 64-bit, and still loving it!

---

### Post by Decatf on 2010-11-20
The Catalyst (fglrx) driver does not work anymore for Ubuntu 9.10 and onwards. It will not in the future since AMD does not support this graphics card anymore.

You can leave it as is. Currently your graphics card is using the open source driver. There has been alot of work by the open source developers on this driver. Updates can be obtained from the xorg-edgers ppa: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Be sure to read the description before you decide to upgrade to the packages from this repository.

---

### Post by teejay17 on 2010-11-20
> **Decatf said:**
> The Catalyst (fglrx) driver does not work anymore for Ubuntu 9.10 and onwards. It will not in the future since AMD does not support this graphics card anymore.

You can leave it as is. Currently your graphics card is using the open source driver. There has been alot of work by the open source developers on this driver. Updates can be obtained from the xorg-edgers ppa: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Be sure to read the description before you decide to upgrade to the packages from this repository.

Thanks for the link and the update.

---

