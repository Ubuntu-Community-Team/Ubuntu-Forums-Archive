---
title: "Lost VNC ability"
date: 2008-01-28
forum: Mythbuntu
---

### Post by uncle hammy on 2008-01-28
I wrapped up my first backend server on the weekend, and everything seems great.  Then last night, while exiting out of live tv, the screen just went blank, and never recovered.  Can anyone shed any light on what may have caused that?

Also, after a hard power cycle to bring it all back, I can no longer connect to the box via VNC from my windows vista machine (which I had been able to do up until last night).  When I try to connect an error comes up "No password configured for VNC auth".

I went to the physical box, loaded up the Myth Control center, selected Reconfigure for the VNC service, and entered the password again, then rebooted.  Still no luck.

Thanks for any answers to both problems.

---

### Post by superm1 on 2008-01-28
> **uncle hammy said:**
> I wrapped up my first backend server on the weekend, and everything seems great.  Then last night, while exiting out of live tv, the screen just went blank, and never recovered.  Can anyone shed any light on what may have caused that?

Also, after a hard power cycle to bring it all back, I can no longer connect to the box via VNC from my windows vista machine (which I had been able to do up until last night).  When I try to connect an error comes up "No password configured for VNC auth".

I went to the physical box, loaded up the Myth Control center, selected Reconfigure for the VNC service, and entered the password again, then rebooted.  Still no luck.

Thanks for any answers to both problems.
Try setting a password exactly the minimum number of characters and reboot.  You might be toying with and odd bug here. (If that's the case, be sure to file it :))

---

### Post by JGJones on 2008-01-28
I have something similar to you here - except that mine was caused by me swapping a Nvidia card for a ATI Radeon 7000 card (as that had S-video output).

After installing, obviously I wasn't getting X to start up (I could see the Xfailsafe executable showing in process list (Xfailsafe is not the name, I can't remember the exact name).

So after manually tweaking xorg.conf so that the system use the S-video for output however I no longer had VNC access and even after using mythbuntu control center to reconfigure (including the extra number of letters for the password) - I don't have VNC starting (port 5900 remain closed).

I notice that it use vnc4server for VNC? If so I will attempt this:

```
sudo apt-get --purge remove vnc4server
```

The --purge switch also remove any configuration files associated with that so hopefully that will help. I will report back if any success here.

Cheers

---

### Post by uncle hammy on 2008-01-28
Setting the password to the minimum did not resolve the issue.  I will se what happens with the above post.

---

### Post by JGJones on 2008-01-29
OK I did that command and I checked in my user account (which autologon) and removed the .vnc directory.

I then reinstalled vnc4server and reconfigured it in mythbuntu control center but it did not work.

This morning, I had a power cut, so I powered up the server (aka a reboot if you like).

It now works(!) So after doing that command I'll suggest restarting gdm/xserver (reboot if you like) and see if it works for you.

---

### Post by uncle hammy on 2008-01-30
Seems to have worked, thanks!

---

