---
title: "ATI x700 mobility – How I got mine to work"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by zba78 on 2006-07-13
First off I use Kubuntu (dapper) with adept. If you’re using Ubuntu/Synaptic then substitute accordingly.

My graphics card is a 128MB ATI x700 Mobility on an Acer Aspire Laptop.

When I first installed Dapper (beta 2) I downloaded the ATI driver from the ati website and followed the wiki here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) under the section ** Using the drivers from ati.com**. This worked perfectly fine first time.

After the many upgrades/updates to packages the ati drivers broke. Whatever I tried I got the mesa stuff when typing fglrxinfo 

So finally I did this and it worked. 

Launch adept and type fglrx into the search/filter box.
Once the list shows delete all references to fglrx (fglrx-control, fglrx-kernel etc.)
Then type linux-restricted-modules into the search/filter box.
Remove linux-restricted-modules

Then follow the instructions on the above link from the section **Install instructions for Ubuntu 6.06 (Dapper Drake)**

Personally I only had to do the following steps ```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
```
Because I had already edited my xorg.conf from before.

Reboot and all worked fine. Glxgears –printfps gives about 4600 fps

---

