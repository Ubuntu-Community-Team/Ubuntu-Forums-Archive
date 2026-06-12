---
title: "Suspend backfired, can't login"
date: 2011-03-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vaskark on 2011-03-15
I tried the suspend feature in natty and my machine wouldn't wake back up. I rebooted and now the screen seems to freeze after booting past grub but before it gets to gdm. I'm at a loss as to what to do. I made a maverick install cd and am currently running on that. I can see my natty systems' partitions in nautilus but am lost as how to proceed. I was hoping to run fsck.

Can someone help, or point me to a resource that will instruct me how to proceed? I've had great luck in the past with early dist upgrades but this one seems to have bitten me in the **** :(

Thanks.

---

### Post by zika on 2011-03-15
Did You try to boot with &#8222;text&#8220; as kernel option. That would get You to tty1 and, after that, You could explore the reason why GDM (i.e. X) is not starting properly... Check locks...
To run forced fsck do```
sudo touch /forcefsck
``` and reboot...

---

### Post by vaskark on 2011-03-15
Fixed! Bravo, sir.

---

### Post by zika on 2011-03-15
> **vaskark said:**
> Fixed! Bravo, sir.
I'm glad that it worked...

---

### Post by vaskark on 2011-03-15
I encountered a similar problem after applying some updates. I tried your 'sudo touch /forcefsck' solution again and rebooted. It appeared to be working and checking the disks, but then it went to a text screen and just stopped (see attachment). I waited a few minutes but nothing happened. Any ideas? Sorry to bother you again ;)

---

### Post by dinamic1 on 2011-03-15
> **vaskark said:**
> I encountered a similar problem after applying some updates. I tried your 'sudo touch /forcefsck' solution again and rebooted. It appeared to be working and checking the disks, but then it went to a text screen and just stopped (see attachment). I waited a few minutes but nothing happened. Any ideas? Sorry to bother you again ;)

try booting with <Previous linux version> (from grub)

---

### Post by Starks on 2011-03-15
getting a similar problem after today's updates.

x won't load. older kernel doesn't help.

---

