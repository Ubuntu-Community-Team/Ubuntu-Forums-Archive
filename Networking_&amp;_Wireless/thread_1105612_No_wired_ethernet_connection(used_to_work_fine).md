---
title: "No wired ethernet connection(used to work fine)"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by iamthemicrowave on 2009-03-24
Hi.  I just got my laptop fixed by a Dell technician, who installed a new motherboard and fan(old fan burnt out). He also flashed the BIOS to A10, the latest revision for my computer. Since then, the wired internet connection is not working.  It worked fine before.  Wicd simply says that I have no connection.  Wireless works fine.

What are some troubleshooting steps I can take to diagnose the problem?  If you guys can't find anything I will assume it is a hardware problem and get Dell to come fix what they messed up.

Thanks alot!

---

### Post by Iowan on 2009-03-25
Start with **lshw -C network**. That should tell you a lot about your interface.

---

### Post by iamthemicrowave on 2009-03-26
Thanks I got it fixed.  I had to reinstall gnome-network-admin package from a flash drive(downloaded from another computer) because wicd installation had removed it.  I'm back on network-manager, bye bye wicd!

---

