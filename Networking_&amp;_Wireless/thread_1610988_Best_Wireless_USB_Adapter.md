---
title: "Best Wireless USB Adapter"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Data 1 on 2010-11-01
Can anyone recommend a wireless USB adapter known to work well with Ubuntu.

Currently running 10.04, KDE.

Thanks- 
Jim

---

### Post by mikewhatever on 2010-11-01
I don't know about the best. Best for who? Best for what? Best for how much? Is it vague or what? I think the link below is much better then any of the best.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#Wireless%20USB%20Adapters)

---

### Post by Data 1 on 2010-11-01
I stand corrected. Or scolded.

Just one that several people use and have success with. I tried my wusb54gc I had laying around, seemed impossible to get it to work.

I'll read the thread, 

thank you-

Jim

---

### Post by MooPi on 2010-11-01
I find that list to be dated and woefully in need of current adapters. I read reviews from online vendors to determine if the ones I've chosen will function with Ubuntu. It always a good idea to go to the manufactures web site to see if they list Linux as a compatible OS. I personally have had very good success with Rosewill adapters both usb and pci. These are listings from newegg in the US
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166023]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166023")

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166027]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166027")

---

### Post by mikewhatever on 2010-11-01
> **Data 1 said:**
> I stand corrected. Or scolded.

Just one that several people use and have success with. I tried my wusb54gc I had laying around, seemed impossible to get it to work.

I'll read the thread, 

thank you-

Jim

In no way scolded, just an opinion. ;)

---

### Post by walt.smith1960 on 2010-11-01
I'm quite happy with this adapter in Lucid. It is not recognized out of the box. There are 2 ways to get it to work. 


[LIST]
[*]There are directions on this board to download various files and compile. I'm not that confident in my skills. I found reference to a file on Sourceforge--http://sourceforge.net/projects/ath9k-htc/  I downloaded and installed it, it's a two stage process.  There was a problem with resuming from suspend, the adapter didn't want to wake up. I found this fix and so far so good. This apparently fixes a problem in network-manager that is known but the updated applet hasn't found its way to Ubuntu yet.   Prefix sudo before each line
[/LIST]

[LIST=1]
[*]service network-manager stop
[*]rm /var/lib/NetworkManager/NetworkManager.state
[*]service network-manager start
[/LIST]
I did a restart and so far so good in Lucid after several suspend/resume cycles over a week. I'm getting better than G speed but I don't know if I'm getting full 150 speed. I have no way to measure network throughput but it's significantly faster than other G adapters.



[LIST]
[*]NDIS wrapper.  I did this in Meerkat because at the time the Meerkat fix was not yet published.  NDISwrapper installed smoothly but I think I'm getting G speed.  Definitely seems slower than using the native driver in Lucid.  I haven't tried installing the latest version of the .deb file.  I used the .inf & .sys files from a 32 bit winXP install.
[/LIST]
I hope this is of some use to you and others.

---

