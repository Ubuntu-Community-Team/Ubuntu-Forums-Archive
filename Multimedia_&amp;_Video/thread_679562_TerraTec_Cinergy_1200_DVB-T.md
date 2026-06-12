---
title: "TerraTec Cinergy 1200 DVB-T"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Wild-Storm on 2008-01-27
Hi,
i've got this TV-Card since a lot of time and till i installed the generic driver instead of the -i386 (i think it's since then..i'm not shure..i'm not often watching tv), my tv-card doesn't work. it's tuneable, yes, but it doesn't give me any picture.
kaffeine gives me this error: .FE_READ_STATUS: Input/output error
well, i saw that the firmware was not installed..okay..installed the firmware (with this technotrend script), now the card was not useable (while booting i got the following error msg: unknown header type 7f, ignoring). okay, i removed this firmware and searched on an old dist. for my firmware, found it, installed it. now the card shows up in the systemconfiguration, but i still have no tv.
dmesg shows me this: 
dmesg | tail
[ 3547.487969] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer

so what is going on?

thanks for any help

regards

(excuse my english, not my native language ;) )

---

### Post by Wild-Storm on 2008-01-27
found it..used a diffrent pci slot, works now!

---

