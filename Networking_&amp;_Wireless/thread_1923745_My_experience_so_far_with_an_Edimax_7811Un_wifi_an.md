---
title: "My experience so far with an Edimax 7811Un wifi and question"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2012-02-11
This is a review of a new-to-me nano wireless adapter and a question for those more knowledgeable. I've broken two midsized USB Wifi adapters due to physical abuse (Thinkpads are pretty durable). I boubt the Edimax EW-7811Un due to it's barely-there form factor and people have had success getting it to work. Plugged it into Thinkpad running Precise with daily updates.  The light came on steady and the adapter was present in Network Manager. I was connecting to a hidden Wifi network.  It would connect but I got the dreaded repeating &#8220;enter your network key&#8221; message and it wouldn't connect. As far as my limited knowledgeable extended, 'iwconfig' looked fine. 

I was unable to create an open network with Verizon's version of the ActionTec MI424 they supply to FiOS customers so I renamed the SSID and began broadcasting the SSID. Deciding to take the easy road, blacklisted the 'native' drivers and downloaded the latest driver from RealTek's web site. An install script is part of the download and worked perfectly.  A restart and it was there. Speed was good though not as good as the rtl-8192su device it replaced. Stable, no disconnects after a few hours' use. I then tried the device on an 11.10 install. That time it was recognized and did connect. It worked but seemed slow.  I copied the RealTek driver folder, blacklisted, ran the script and download speed was up to snuff.  Upload speed was low in limited testing; I often see 20 mbps up, with this adapter I was seeing less than 8.

I haven't had to re-run the install script due to kernel upgrade yet. The script appears to have provisions to remove previous instances so I guess we'll see soon enough. Executive summary, It seems a nice choice for portable devices. RealTek offers Android drivers along with Linux and it's quite unobtrusive, protruding < 1 cm.. I recommend using the easily installed RealTek driver and blacklisting the drivers that are included in the kernel. Native drivers may 'get there' but they seem to not be there yet. Tested kernel is:
Linux precise 3.2.0-15-generic #24-Ubuntu SMP Tue Feb 7 22:32:19 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Now to my question: Creating a DKMS install seems like it would eliminate the need to rebuild upon kernel upgrade.  Is it possible to create an 'kernel upgrade proof' driver using the existing install script?  Something like ```
sudo dkms bash install.sh
```  This is not hugely important because the included script is quick and easy but :tongue:

---

