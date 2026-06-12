---
title: "Wireless and energy management"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by Romu on 2012-05-31
Hi there,
I made a fresh install of 12.04 Beta and followed all updates on a new Dell XPS15z, the wireless chipset is an Intel Advanced-N 6230.

I really appreciate the efforts made by Ubuntu regarding the batterie life, it's really amazing. But I'm afraid these efforts were made against the wireless usability because on battery, my wifi connection is unusable. In that case, the connection seems alive but I can really access some servers every 2 mn and this works only for few seconds, and then have to wait for 2 mn and so on.

I have to say I'm running the Wagner Volanin PPA to its modified network-manager, I don't know if this can be the cause of the issue, I'll check this.

Am I the only person in that case, with pretty no working wifi on battery ?

Thanks.

---

### Post by chili555 on 2012-05-31
I'm not sure it's an energy management issue. Let's try a few things. Please open a terminal and do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one file and make it persistent.

---

### Post by Romu on 2012-06-01
Thanks Chili555,
I understand you suggest to shutdown the "N" wifi mode. So, I guess I'll return to 54Mb/s rate, right?

---

### Post by chili555 on 2012-06-01
Correct. I know it's a compromise, but the iwlagn and iwlwifi drivers have a well-known issue with N, usually to the point of not transmitting packets *at all*.

---

### Post by Romu on 2012-06-01
Ok, I'll try this in the following day and post some feedback. Thanks again for your help.

---

### Post by Romu on 2012-06-06
Hi Chili555,
I haven't tested yet, but you pointed a wireless layer bug for N mode. But, to me it works great...as soon as I'm plugged in to my power supply.

I don't have any issue when plugged, only on battery. Does this seem to be the bug you mentioned?

---

### Post by chili555 on 2012-06-06
> **Romu said:**
> Hi Chili555,
I haven't tested yet, but you pointed a wireless layer bug for N mode. But, to me it works great...as soon as I'm plugged in to my power supply.

I don't have any issue when plugged, only on battery. Does this seem to be the bug you mentioned?It's hard to tell. Did you try? Did it fix it or not? It's only two terminal commands that are reversible with two more:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 
```That's certainly not the only thing we can try, but before you discard N, at least try it!

The wonderful thing about Linux is that we can try things quickly and easily and remove them just as quickly and easily. Even if we wrote a configuration file, we can delete it with a very few keystrokes and restore the system to default in a few seconds.

---

### Post by Romu on 2012-06-07
Hi, Yes I know it's easy, it's just I haven't find the time to try it yet. I will, for sure.

Thanks.

---

### Post by Romu on 2012-06-17
Hi Chili555,
Your solution works well indeed. But how can I make it definitive? Because each time I reboot, I'm again in N mode.

---

### Post by wildmanne39 on 2012-06-17
Hi, I am helping my good friend the expert out while he is out of town please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf

```
Add one line:

```
options iwlwifi 11n_disable=1
```

Proofread carefully, save and close gedit. 
then reboot.
Thanks

---

