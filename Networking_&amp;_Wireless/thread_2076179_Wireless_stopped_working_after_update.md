---
title: "Wireless stopped working after update"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by Cancellator on 2012-10-25
Hi, I'm running Ubuntu 12.04 LTS on my Vaio with an Atheros AR9285 wireless adapter. Yesterday I installed the updates from the Update Manager, and everything seemed to work fine... until the first reboot. Now my wireless is disabled, and my card doesn't show up in settings at all.

As I don't have access to a wired connection, I'm posting this from Windows, where everything works fine. 

Also, I've tried the "rfkill unblock all" solution, nothing happened, and in rfkill list all switches are OFF.

Anyone have any info on why this might happen? It's probably driver related but I don't know how to fix it. And it's a bit of a pain since I did most of my university work on my laptop... Thanks!

---

### Post by maniandram on 2012-10-25
Start the "Additional Drivers" application and if there are drivers which you can install, install it.

---

### Post by danielbauwens on 2012-10-25
If you have Fn, it might be:
```
Fn-F2
```

Or go to the Internet Icon on the top of the screen and "Enable Wireless" and "Enable Networking" 
Both must be on.

Daniel

---

### Post by Cancellator on 2012-10-25
> **maniandram said:**
> Start the "Additional Drivers" application and if there are drivers which you can install, install it.

The "Additional Drivers" application only shows Nvidia graphics drivers as available.

> **danielbauwens said:**
> If you have Fn, it might be:
```
Fn-F2
```Or go to the Internet Icon on the top of the screen and "Enable Wireless" and "Enable Networking" 
Both must be on.

Daniel

Thanks, but I already tried all this, and "Enable Wireless" doesn't even show up in the Internet menu! Also, before you ask, I did check the hardware switch.

---

### Post by maniandram on 2012-10-25
Run
```

sudo iwconfig

```
and post the output.
-
I am a 11-year old (really)

---

### Post by Cancellator on 2012-10-25
> **maniandram said:**
> Run
```

sudo iwconfig

```
and post the output.
-
I am a 11-year old (really)


lo no wireless extensions
eth0 no wireless extensions

---

### Post by Cancellator on 2012-10-25
No one else has any ideas? :(

---

