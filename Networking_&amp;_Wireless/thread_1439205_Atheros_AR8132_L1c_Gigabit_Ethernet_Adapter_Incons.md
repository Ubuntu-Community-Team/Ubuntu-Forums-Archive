---
title: "Atheros AR8132 L1c Gigabit Ethernet Adapter Inconsistant Device Drivers"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by datajock on 2010-03-25
Hi Everyone,

I have just spent days trying to get this network interface to work on a new Asus Eee PC 1005PEB netbook I just picked up. I have read many posts on issues that contain AR8132 and not one of them seemed to help. Since I am a Unix (Solaris) Systems Administrator and always look for what may be different in my situation, I realized that in most cases I could not tell what distribution of Ubuntu was being talked about.

I have a working install of Ubuntu 9.04 on another Asus Netbook and was having a hard time believing that this one would not have the drivers for the network interface on this one.

Now for the BIG difference! I want to use these small low power consumption systems as a very specialized and dedicated **SERVER**. For a very small application like a DNS server, this is a very low cost solution that doesn't take up much space, need a Monitor or some other sort of KVM setup (although it could be connected to a KVM and the lib left closed) and uses little power with a built in battery backup.

So, am I the only one that has tried installing Ubuntu 9.10 Server (or Ubuntu 9.04 Server) on one of these devices? I even tried the Ubuntu 8.04 LTS Server image.

After all but giving up on being able to run Ubuntu on this netbook I realized that I don't think anyone posting here was using the server ISO image. So I downloaded the Desktop ISO and to my amazement the network interface works just fine. So now it would appear that there is a different set of device drivers included with in the Server ISO image than what is included in the Desktop ISO image.

I am somewhat shocked that the device drivers would not be the same between all these different distros. So can someone closer to the source confirm this to be the case? Was this an oversight on not being updated in the Server ISO, or is this done for a reason?

The next question, is there a way that I can install the Server, and then (since I don't have any network at that point) use the Desktop CD to install the device drivers I really need? I'm actually using a USB attached drive, so it's not a must that this be a thumb drive solution for me but if any others find themselves in this same situation it would be good to know how I might do it via a download to a thumb drive on another computer and the install it on that one.

Am not very familiar with Linux and how the packaging works and would love a quick a easy way to do this.

Thank you in advance.
DJ

---

### Post by datajock on 2010-04-02
Sorry if there was duplication here, but I also posted in the "Server Platforms" Forum with a link back to this, since it appeared that it may be more appropriate to that forum.

The link to that is [http://ubuntuforums.org/showthread.php?t=1439599]("http://ubuntuforums.org/showthread.php?t=1439599") for that thread.

I have since resolved me issue and the results are posted there.

Thanks,
DJ

---

