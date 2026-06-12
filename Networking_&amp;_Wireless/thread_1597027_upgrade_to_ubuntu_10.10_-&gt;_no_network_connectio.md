---
title: "upgrade to ubuntu 10.10 -&gt; no network connection"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by nnymous12 on 2010-10-14
Dear Experts,

My upgrade to Ubuntu 10.10 seemed to have gone smoothly.  But now my  network connection does not work any more.  (wired, DSL).  My wireless  network does not work since a number of upgrades back.  I seem to  remember that I had a similar problem after the last upgrade, but can  not remember how to fix it.
Computer: Dell inspiron 1501 64 bit, run as 32 bit.

Please help, Thanks!

---

### Post by etijing on 2010-10-14
I am experiencing these symptoms as well, please help. Gateway 6850FX. Everything was working fine until the update was applied. I can't even get online thru the ethernet.

---

### Post by nnymous12 on 2010-10-14
just a short FYI: after my original post starting this thread, I discovered this one: [http://ubuntuforums.org/showthread.php?t=1597008](http://ubuntuforums.org/showthread.php?t=1597008)
it did not yet solve my problem, but there is at least a conversation going on.  You may want to keep an eye on both threads...

---

### Post by gibbylinks on 2010-10-17
> **nnymous12 said:**
> Dear Experts,

My upgrade to Ubuntu 10.10 seemed to have gone smoothly.  But now my  network connection does not work any more.  (wired, DSL).  My wireless  network does not work since a number of upgrades back.  I seem to  remember that I had a similar problem after the last upgrade, but can  not remember how to fix it.
Computer: Dell inspiron 1501 64 bit, run as 32 bit.

Please help, Thanks!

I have same laptop. Use a cable to connect to the internet and then download the STA driver under "Additional Drivers"

---

### Post by Quan-Time on 2010-10-17
after upgrading from 10.04 x64 which worked perfectly (except another un-related issue) my wifi drops out CONSTANTLY and after a while just stops and wont even find anything.
My gbit also only runs at 10/100 speeds to my file server with a cable in.

I installed some new drivers from here:
[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

This fixed my gbit issue weirdly, dunno how, and my wifi is "stable" but only does ~35k/s MAX to my file server.  It doesnt seem to disconnect anymore, but i only gave it about 5mins worth of testing.  Seemed "stable" but hugely slow.
I always pulled 2.7 - 2.8mb/s when i used 10.04 x64.

Just thought i would chirp in.  

Oh, asus laptop (k701c) with atheros ath9k wifi chipset.

---

### Post by Quan-Time on 2010-10-18
OK.. one thing ive noticed.. Ive changed from channel 11 on my wifi network to channel 1, and its MUCH better.  Not sure why, could be neighbour hood conflicts, or something else.  Either way im basically sorted now.

---

### Post by migs73 on 2010-10-18
> **gibbylinks said:**
> I have same laptop. Use a cable to connect to the internet and then download the STA driver under "Additional Drivers"
+1 and I am using 32bit, like you.

---

### Post by migs73 on 2010-10-18
> **nnymous12 said:**
> 
I seem to  remember that I had a similar problem after the last upgrade, but can  not remember how to fix it.


here is your old thread and (I assume) the solution
[http://ubuntuforums.org/showthread.php?p=8716709#post8716709](http://ubuntuforums.org/showthread.php?p=8716709#post8716709)

As stated above use the STA driver.

---

### Post by nnymous12 on 2010-10-20
BUMMER! I had enough of the computer not having internet and booted from  the Ubuntu 10.10 disk.  WIred internet worked right away.  (WIreless  not yet, I have a feeling I need to get the SSID right in the network  settings, will look for instructions.)
This is good news since it means the hardware works, but bad new because  if I can not fix the problem, I'll have to re-install the operating  system and I had put a lot of work into customizing that...

---

### Post by eynestyne on 2010-10-20
I switched from 10.10 to 10.04 because of wireless problems. But now I see that there is a new STA driver out - released on 18th/10.
Has anyone tried this? [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")
Documentation says this one supports up to kernel 2.6.36, I think the previous stopped at 2.6.32

---

### Post by migs73 on 2010-10-21
> **migs73 said:**
> +1 and I am using 32bit, like you.

Just checked just now and I am actually using the b43 driver, so it look like either would be fine.

---

### Post by imran_e on 2011-01-02
Goto synaptic manager. The bcmwl drivers is marked as required as update required. Update the bcmwl drivers and it works.

Running on a Dell inspiron 14R. Upgraded from 10.04 to 10.10 via an alternate CD.

---

