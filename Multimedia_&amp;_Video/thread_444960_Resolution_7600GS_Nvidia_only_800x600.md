---
title: "Resolution 7600GS Nvidia only 800x600"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by agkbill on 2007-05-15
I am unable to set the proper resolution for my MSI NX7600GS video card. Connected to my  monitor (Nokia 920C) with a DVI-->HDMI cable, but the only resolution settings that I am getting from Ubuntu are 800x600. That is also the only one I can se in the Nvidia server setting tool. What do I need to do to remedy this situation?

Best regards,
/Christer

---

### Post by heimo on 2007-05-15
I think I've seen this couple times before on these forums. I'd probably start here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://ubuntuforums.org/showpost.php?p=454217&postcount=1")

---

### Post by agkbill on 2007-05-16
:lolflag: 


I got it working!

Added

Option "ModeValidation" "AllowNon60HzDFPModes, NoVertRefreshCheck, NoEdidMaxPClkCheck, NoHorizSyncCheck"

Under device section in the xorg.conf

---

