---
title: "temporarily unmanaging a specific interface"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by decoherence on 2011-08-06
As part of my job, I have to configure a lot of network devices that are configured through web pages. This generally means plugging in to them via ethernet, going to their default IP address and reconfiguring them. I set my IP address using ifconfig, which is much faster than plugging numbers in to networkmanager's GUI. The problem is, NetworkManager seems to take the interface down at random.

I could disable NetworkManager but then I don't have a wireless connection.

Is there a way to tell NetworkManager to temporarily ignore what is happening on a specific interface or should I just ditch NM altogether when doing this kind of work and use wpa_supplicant to get on my wireless?

My co-worker with the Windows machine is looking over my shoulder and chuckling. Away! Dirty MS user! You don't even have a proper shell!

---

### Post by decoherence on 2011-08-07
I guess I'll ask the fedora forum. Redhat did most of the work on it anyway, i guess. Seems like it would be a pretty nice feature to have if it doesn't already exist.

---

### Post by cbruce8 on 2011-08-08
Well, I have 20 ip's configured in my Unity desktop network dropdown box - but that seems to be the limit.  I have more configured but they do not show in the dropdown box.

I have similar requirement in that I travel to locations with different subnets and do not want to do dhcp. The drop down box allows me to click on location. -Works pretty well.
-c

---

