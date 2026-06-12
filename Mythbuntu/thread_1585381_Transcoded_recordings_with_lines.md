---
title: "Transcoded recordings with lines"
date: 2010-09-30
forum: Mythbuntu
---

### Post by lviperz on 2010-09-30
I decided to try using the transcoding option on some recorded shows. Normally I do not transcode anything. I have 3 tuners, all standard def. They are Hauppauge PVR-150, 250 and 350. The recording profile is 720x480 with everything at it's defaults.

I set the transcode to mpeg4 with all the defaults. My file sizes went from 2.2g for 1 hour to 1.1g. But when I watch the recordings back there are faint diagonal lines throughout the picture and artifacts during fast screen changes and fast action as well as changes between bright and dark scenes.

I don't have much hoursepower in this system so I'm wondering if I need more power or should try some better settings. I just don't know what settings I should try. Anyone use the Hauppauge PVR-X50 series of tuners want to share their settings?

The pc is an old Dell Dimension 8300, P4 2.6 hyperthread, 2.5g ram. The video is an old nvidia mx series with 64m ram.

Would a newer video card help the picture?

---

### Post by LowSky on 2010-09-30
A newer video card would help watching the encoded files if it has VDPAU, I'm not so sure about the encoding prcess though. That is were more CPU speed and cores comes in handy.

That old of a system might not be capable of using a PCIe video card. So your kinda stuck... sorry

---

### Post by nickrout on 2010-10-01
> **LowSky said:**
> A newer video card would help watching the encoded files if it has VDPAU, I'm not so sure about the encoding prcess though. That is were more CPU speed and cores comes in handy.

well yes and no. It needs feature set C to accelerate mpeg4, so not every vdpau card will help.
> 
That old of a system might not be capable of using a PCIe video card. So your kinda stuck... sorry

---

