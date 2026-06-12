---
title: "Error found for S3 Savage 4"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by carontis on 2006-07-16
I know it's not the best video card, but it helps. Anyway here is: I launched lshw and with surprise I found that the S3 Savage 4 AGP is on my pc, doesn't have 16 vram but 128!!! This is a bad error and I think should be reported to the Ubuntu's Team. Probably can be some not exact code in checking hardware. Could try someone with same video card, to see what happens running lshw? This is what I see as result (partial)

[COLOR="DarkRed"]display
                description: VGA compatible controller
                product: Savage 4
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 03
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=savage4_smbus
                resources: iomemory:e9000000-e907ffff iomemory:e0000000-e7ffffff irq:11[/COLOR]

Hope it happens only to me... 'cause I have to change this video card!

bye

---

