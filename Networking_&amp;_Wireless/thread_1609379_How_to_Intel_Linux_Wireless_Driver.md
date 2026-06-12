---
title: "How to Intel Linux Wireless Driver?"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by FreakShow! on 2010-10-30
Hi,

I've just installed Mint 10 (based on Maverick) and am very pleased with it so far. However the one annoying thing that seems to be present in every Linux distro I have tried, it's got terrible speeds on WiFi.

It works fine in Windows so it's definitely a software issue.

Does anyone fancy writing a quick guide on how to install [this]("http://intellinuxwireless.org/?n=Downloads")?

My WiFi card is the 3945ABG. Thanks for any help.

---

### Post by s_raiguel on 2010-10-31
As a matter of fact, I just installed an updated Intel driver (but for a wired NIC) a couple of days ago. If you open the tar file with the archive manager, isn't there a readme file in it? When I got my new driver, the accompanying readme explained step-by-step how to install the driver. Basically, you un-archive it, then go into the newly-created directory with the terminal, and type "make install" at the command line. This will put the new driver into the kernel modules directory. You can then either simply reboot, or you can use the modprobe command, to remove the old module and fire up the new one.

---

