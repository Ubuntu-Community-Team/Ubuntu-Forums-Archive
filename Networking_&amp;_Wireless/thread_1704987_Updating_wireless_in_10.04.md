---
title: "Updating wireless in 10.04"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by trinitydan on 2011-03-11
I have run into an interesting conundrum trying to install a dual boot on a friends computer.  He has a SATA drive with an adapter that is not detected with the new kernel in 10.10, so I want to use 10.04.  His wireless adapter (TP-Link TL-WN722N/TL) is not supported with the 10.04 kernel but is with 10.10.  Is there some way that I can update just the wireless/networking portion of the kernel?  TIA!

---

### Post by gordintoronto on 2011-03-11
> **trinitydan said:**
> He has a SATA drive with an adapter that is not detected with the new kernel in 10.10

I would focus on this part of the story. Can you give more details?

---

### Post by trinitydan on 2011-03-11
Well, it's not just that.  All around, he isn't the type to want to reinstall again soon probably so I was trying to set him up with the best option for long term support.  The preferred choice was 10.04 anyway, then 10.10 offered wireless support so we were considering installing that.  All we really want though is for his wireless adapter to work in 10.04.

The SATA adapter I was describing looks similar to [this]("http://www.google.com/imgres?imgurl=http://images.highspeedbackbone.net/skuimages/large/ULT40322-vendor-sp.jpg&imgrefurl=http://www.tigerdirect.com/applications/searchtools/item-details.asp%3FEdpNo%3D4143846&usg=__7aq5iuIeB9XEOYYMcvKvlA7dSZk=&h=300&w=300&sz=47&hl=en&start=0&zoom=1&tbnid=cHeYgqEWeMwwLM:&tbnh=113&tbnw=113&ei=Wbp6Tde4L4mesQPp64D_Ag&prev=/images%3Fq%3Dsata%2Bide%2Badapter%26um%3D1%26hl%3Den%26client%3Dubuntu%26sa%3DN%26channel%3Dfs%26biw%3D1360%26bih%3D603%26tbs%3Disch:10%2C74&um=1&itbs=1&iact=hc&vpx=1041&vpy=287&dur=6435&hovh=225&hovw=225&tx=100&ty=146&oei=Wbp6Tde4L4mesQPp64D_Ag&page=1&ndsp=24&ved=1t:429,r:22,s:0&biw=1360&bih=603").  For whatever reason, Ubuntu 10.10, as well as Debian Squeeze based distros like LMDE do not recognize the drive through the adapter. Ubuntu 10.04 does.

---

### Post by gordintoronto on 2011-03-12
A Google search shows that a lot of people were frustrated by that wireless adapter before Ubuntu 10.10. I didn't see any "solved" threads, and even ndiswrapper didn't seem to work.

The problem with the SATA/IDE converter is pretty weird, since the device doesn't rely on a driver of any kind.

Sorry I can't point you to a solution, other than a different wireless adapter. I've got a TP-Link TL-WN321G which "just works." The slower speed would only make a difference if your friend copies large files from computer to computer within his own network.

---

