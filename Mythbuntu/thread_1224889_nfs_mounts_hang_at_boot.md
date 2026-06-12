---
title: "nfs mounts hang at boot"
date: 2009-07-27
forum: Mythbuntu
---

### Post by mark467 on 2009-07-27
This is on a remote front end
Here are the lines in my /etc/fstab

192.168.1.25:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,bg,timeo=14,intr
192.168.1.25:/var/lib/mythtv/pictures /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,bg,timeo=14,intr
192.168.1.25:/var/lib/mythtv/posters /var/lib/mythtv/posters nfs rsize=8192,wsize=8192,bg,timeo=14,intr
192.168.1.25:/var/lib/mythtv/music /var/lib/mythtv/music nfs rsize=8192,wsize=8192,bg,timeo=14,intr

with that they hang at boot for a long time but when it eventualy comes up they are functional.
I tried adding ,noauto to the end of the lines and adding mount -a to /etc/rc.local and they dont hang but dont mount at all.
they wont even mount with sudo mount -a in terminal
this seems like a common and obvious problem but I have searched and found nothing to correct it.

---

### Post by ian dobson on 2009-07-28
Hi,

Are you using a static IP address or an IP address through DHCP?

If you using DHCP I would recommend going over to a static one, configured in /etc/networks/interfaces and that you remove network-manager.

It looks as if your mounts are waiting for your network interface to get a IP address before even attempting to bind.


Regards
Ian Dobson

---

### Post by SiHa on 2009-07-28
Ah!
I have the same problem on my 'spare' machine that spends most of it's time as a windows PC. I've never got round to setting a static IP address for this one.
Sorry to hijack the thread, but I think you've just fixed an annoying problem. Thanks.

---

### Post by stevanbt on 2009-07-28
Hi,
I don't think the network interface is running when rc.local is run (I have a wake on lan in the rc.local on my remote frontend and it never fires correctly).

I use autofs for the frontend's network shares - works a treat.

Thanks, Steve.

---

### Post by mark467 on 2009-07-30
Ok, I do have all my ip's set static but it is in network manager (which seems to be the problem I guess) I see network manager connection does start or bind until the gui is up. So that to me is the problem. There is no network connection available when fstab runs.

What does "I use autofs for the frontend's network shares - works a treat" mean. I am not familiar with autofs.

---

### Post by stevanbt on 2009-07-30
Hi,
I followed a detailed ubuntu autofs guide, which I can't find now.  However there is a guide here that will give you a good start point.

[https://help.ubuntu.com/community/Autofs]("https://help.ubuntu.com/community/Autofs")

Then on your remote frontend's mythtv setup you reference the autofs mountpoint.  The remote file system isn't mounted until you reference it for the first time.

Hope this helps, Steve.

---

