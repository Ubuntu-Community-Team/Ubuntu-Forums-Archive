---
title: "Upgraded from 10.10 to 11.04B1: Plymouth failed"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-04-02
Hello,
Just upgraded from Ubuntu 10.10 to 11.04 Beta1 on an AMD 64-bit system with GeForce 7300 GT video card using proprietary Nvidia driver.  The command I used to upgrade was ALT F2 > update-manager -d, etc.

Now after rebooting I got just a glimpse of Plymouth, then:

```
Mountall: Plymouth command failed
Mountall: disconnected from Plymouth
```.

The screen then shows only a bunch of text.

Then I tried "sudo gdm start" but got: 

```
"WARNING: failed to acquire gnome.org.DisplayManager".

```

Please help me get the normal login screen and Gnome desktop as in Maverick.

Thanks in advance!

:confused:

---

### Post by iClouseau88 on 2011-04-03
Problem solved as I did a clean install of 11.04 on the root partition of 10.10.

---

### Post by bjarkih on 2011-04-03
> **iClouseau88 said:**
> Problem solved as I did a clean install of 11.04 on the root partition of 10.10.


I'm also having problems after upgrading using update manager.  How do I do a clean install without loosing the data in /home?

---

### Post by rykel on 2011-04-03
Hi, I am also facing a challenging situation with Natty too.

I upgraded using "update-manager -d" but at the end of the upgrade (completed), the system did NOT reboot itself. I rebooted it manually.

Unfortunately, now when I boot into Natty, it goes into a Black screen in seconds, and nothing will change it except a Hard Reset using the power button. Not even the Recovery Mode works.

The only thing I can do is to select "Previous Versions" and use the Recovery Mode there (not even the normal boot) and failsafe graphics.

Please advise? Thanks!

---

### Post by cariboo on 2011-04-03
> **bjarkih said:**
> I'm also having problems after upgrading using update manager.  How do I do a clean install without loosing the data in /home?

You can do an inplace install, by using the manual partitioning option, don't mark the partitions to be formatted. You should always backup your important data before making any major changes to your installation, accidents can happen.

---

### Post by bjarkih on 2011-04-04
> **cariboo907 said:**
> You can do an inplace install, by using the manual partitioning option, don't mark the partitions to be formatted. You should always backup your important data before making any major changes to your installation, accidents can happen.

Thanks, I have a backup, problem is that just lasst weekend I managed to kill the motherboard on my desktop machine :evil: so getting the data back from the backup would involve some trouble I'd rather avoid.

---

### Post by caish5 on 2011-04-04
I have the black screen problem as well. My only solution at this stage was to go into grub and add a nomodeset to the boot options. This will get me some video out but with the wrong resolution, and my display not detected in monitors. 
Can anyone shed any more light on this?
i'm using 00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)

---

