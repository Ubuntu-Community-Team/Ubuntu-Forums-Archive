---
title: "[SOLVED] Nvidia FX5200"
date: 2008-04-30
forum: Multimedia Software
---

### Post by cyclops-user on 2008-04-30
I am having trouble trying to configure my Nvidia card using the restricted modules manager. When I reboot, the computer freezes. I tried using the driver form the Nvidia Webpage, but I got the same result. 

I have uploaded mi xorg.conf.

I welcome all suggestions, thanks!

---

### Post by gsiliceo on 2008-04-30
I have the same card and it wouldnt let me boot i had to add this line
> blacklist intel_agp
at the end of this file using a text editor and sudo
> sudo gedit /etc/modprobe.d/blacklist
It solved all my problem(the only problem i had actually)

---

### Post by cyclops-user on 2008-04-30
Thanks for the advice, I tried that, but nothing.
I am running kubuntu 8.04.
I have uploaded my xorg.log.

I hope someone can help me.

---

### Post by gcranston on 2008-05-03
> **gsiliceo said:**
> I have the same card and it wouldnt let me boot i had to add this line

```
blacklist intel_agp
```

at the end of this file using a text editor and sudo

```
sudo vi /etc/modprobe.d/blacklist
```

It solved all my problem(the only problem i had actually)


Thanks.  This worked for me.  I have a nVidia FX5200 on an ASUS P4P800-VM.  The intel chipset did not like the video card at all.  Either it wouldn't boot, or the NIC wouldn't run when I had it connected, and I couldn't get accelerated graphics to run (or at least run well).

Blacklisting the module got the system to boot in safe graphics.  Removing all entries related to the intel graphics device in xorg.conf (deleting the device1 entry, which was the intel graphics, and the screen1, which referenced it) has solved all my problems.  I am now running at full speed and resolution.

Thanks a lot.

---

### Post by gsiliceo on 2008-05-03
Its a recurrent problem with this model fx5200 i've seen it in lots of motherboards.

---

### Post by gcranston on 2008-05-03
Yeah, I've put together 8 or 10 systems now under ubuntu, and this is BY FAR the most trouble I've ever had with a nVidia card.  Usually they just work.

At least I learned something...

---

### Post by cyclops-user on 2008-05-31
Finally, I got my card working. I add this in my xorg.conf:
Option       "NvAGP" "2"

I got it from here:
[http://en.opensuse.org/NVIDIA](http://en.opensuse.org/NVIDIA)

Thanks!

---

