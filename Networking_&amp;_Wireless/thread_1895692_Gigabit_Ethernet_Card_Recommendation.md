---
title: "Gigabit Ethernet Card Recommendation"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by Steve R. on 2011-12-15
I just bought the Asus RT-N56U Router, works fine.  Now I need to get a Gigabit Ethernet (hardwired) adapter to replace my existing Ethernet card to upgrade my home network to Gigabit Ethernet system.

Any recommendations as to what to get? 
(This is a hardwired Ethernet network) 

One possibility seems to be the Dynex DX-PCIGB, but it's compatibility with LINUX (Ubuntu) is unstated.

FYI Note: Getting the Asus RT-N56U Router fully functional required implementing the solution contained in Problem #3 in [Howto: Fix Windows share browsing issues]("http://ubuntuforums.org/showthread.php?t=1169149").

---

### Post by Steve R. on 2011-12-15
One possibility seemed to be the Dynex DX-PCIGB, but it's compatibility with LINUX (Ubuntu) was unstated. Well Dynex technical support provided the following response.

"*In order to work the DX-PCIGB Dynex Gigabit PCI Desktop Adapter requires oneof the following operating systems: Windows XP or Vista; Windows 7; Mac OS X 10.4 or higher. Unfortunately, it is not Lunix compatible.*"

---

### Post by dBuster on 2011-12-15
Have you done a simple google search?  [gigabit card linux compatible]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=gigabit+card+linux+compatible")

Just picked two responses out of that and read a little, seems like there are plenty of cards out there that would work...

[how to achieve gigabit speeds with Linux]("http://datatag.web.cern.ch/datatag/howto/tcp.html")

[Gigabit NIC & Debian - Recommendations]("http://forums.whirlpool.net.au/archive/531982")

---

### Post by Steve R. on 2011-12-15
Thanks. I had tried an internet search, but it didn't generate any really good hits. Not even on Amazon!
One site listed Linux compatible cards but none were gigabit cards and the site had not been updated for quite a while. 

Looks like the [Intel PRO/1000 GT Desktop Adapter]("http://www.intel.com/Products/Desktop/Adapters/PRO1000GT/PRO1000GT-overview.htm") will work.
Now that I have name, it turns out that this is [available on Amazon.com]("http://www.amazon.com/gp/product/B00030DEQE/ref=s9_simh_gw_p147_d0_g147_i1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=13ZJKS2C3XXQ8KA46SE1&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846").

Thanks again for the information.

---

### Post by bkratz on 2011-12-15
> **Steve R. said:**
> Thanks. I had tried an internet search, but it didn't generate any really good hits. One site listed Linux compatible cards but none were gigabit cards and the site had not been updated for a while.  Obviously, I need to use some different key words.

Please keep in mind that you will also need to make sure your cabling is at least cat5e (cat6 even better) since cat5 is not rated for the speed needed.

---

### Post by Steve R. on 2011-12-15
> **bkratz said:**
> Please keep in mind that you will also need to make sure your cabling is at least cat5e (cat6 even better) since cat5 is not rated for the speed needed.Thanks for bringing this up. I just did an assessment and found that I had two CAT 5 Cables in my spare parts bin, that are now going to be donated. The rest of the cables are a mixture of CAT 5e and Cat 6.

---

### Post by Steve R. on 2011-12-20
For those who may be interested as to what happened. The Intel PRO/1000 GT desktop adapter arrived today. I first configured it in WindowsXP, then re-booted in Ubuntu. It works and I have a Gigabit connection.

---

