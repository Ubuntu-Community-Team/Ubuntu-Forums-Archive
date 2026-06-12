---
title: "ATI Firepro v5800, CCC installed what's VESA:FGL JUNIPER?"
date: 2012-05-02
forum: Multimedia Software
---

### Post by silverbullet007 on 2012-05-02
Fresh install of 12.04, running an ATI FirePro V5800 and installed CCC from the repos however checking the All Settings-Details it's showing "VESA:FGL JUNIPER" as the graphics.  How do I know for sure that the ATI driver is pushing my hardware?

---

### Post by silverbullet007 on 2013-01-30
Anyone have any clues?

---

### Post by Mark Phelps on 2013-01-30
There are two very different forms of ATI dri vers (three, if you count the various PPAs) -- open source and restricted.

The VESA indicates you are running the open-source ATI driver -- so ATI, is driving your card.

AMD dropped support for the HD 2x/3x/4xc series cards this last summer -- and yours is older than that.  So, I seriously doubt that there is a restricted driver available for your card.

---

### Post by silverbullet007 on 2013-01-30
I don't think that;'s quite right.. the FirePro V5800 was essentially the same as the HD 58xx series according to:

[http://www.pcper.com/reviews/Graphics-Cards/AMD-FirePro-V5800-and-V3800-Review-Evergreen-completes-sweep]("http://www.pcper.com/reviews/Graphics-Cards/AMD-FirePro-V5800-and-V3800-Review-Evergreen-completes-sweep")

And if this article is correct and the 5800 is running the Juniper XT gpu then the driver being used does make sense.

---

### Post by Mark Phelps on 2013-01-30
> **silverbullet007 said:**
> I don't think that;'s quite right.. the FirePro V5800 was essentially the same as the HD 58xx series according to:

OK thanks ... I stand corrected.

---

### Post by Yellow Pasque on 2013-01-30
Yeah, and the sysinfo program will say "VESA" even when the VESA driver is not being used (confusing/annoying IMO). I guess that indicates a VESA-compliant device?

---

