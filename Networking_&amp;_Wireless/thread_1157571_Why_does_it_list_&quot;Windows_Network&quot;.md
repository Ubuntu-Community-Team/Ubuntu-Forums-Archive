---
title: "Why does it list &quot;Windows Network&quot;"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by jsast21 on 2009-05-12
I googled the heck out of this and cannot seem to find an answer:

I have Ubuntu 9.04 on one laptop and 8.04 on another. I have a linksys wireless router connected to a cable modem. In either version of Ubuntu, when I click Places, Network all I see is an icon with the label "Windows Network". Windows? I would expect to see the other laptop. But I am not sure where the Windows Network is coming from. And when I click on it, there is nothing there.

Could someone please tell me what's up and also how I can make the laptops visible to eachother?

Thanks.

---

### Post by SunnyRabbiera on 2009-05-12
You might be picking up another network in the area, happens all the time.
Its the drawback to people going wireless, as if you have a strong wireless network others can easily leach on.

---

### Post by jsast21 on 2009-05-12
But shouldn't it also list my own network? Or at least the other Ubuntu laptop?

---

### Post by doas777 on 2009-05-12
well, do you have samba set up on either of the hosts? the Places -> Network app shows samba/windows servers and shares (and perhaps nfs as well. never tried.)  the node you are seeing, is likely a default for the "network:///" uri. my guess is that it's just a default root node, not an actual network. samba networks emulate the MS smb protocol for file sharing, so it's natural that it would identify itself as a windows network.

as for your situation, can the hosts ping each other? do you know the ip addresses of each host?

---

### Post by jsast21 on 2009-05-12
So it might be seeing the windows partition on each machine? (both are dual boot).

And yes, I can ping each one from the other.

---

### Post by doas777 on 2009-05-12
ok, now I'm kinda getting ya.

no i don't think that it is seeing a windows partition, or anything else, but I think you would see "Windows Network" wether there was one or not. if it detects a workgroup, it will display the workgroup name.

what protocol do you want to use for these pcs to see eachother? if you want to isntall and config samba, you can use places -> network. if you wanna use sftp, you can install ssh on each pc, and just put 'ssh://<IP of machine>' into a nautilus address bar, to browse the hdds of each Pc. theres also nfs and a host of others, but i can't help ya there.

---

### Post by doas777 on 2009-05-12
> **jsast21 said:**
> But shouldn't it also list my own network? Or at least the other Ubuntu laptop?
he's implying that you may be connected to the wrong wireless network by accident (a neighbors or whatever.) easy to check, and since you can ping them, then you know that they're both on the same net.

---

