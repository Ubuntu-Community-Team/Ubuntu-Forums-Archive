---
title: "Ubuntu not connecting to the university's Internet when running as a Virtual Machine."
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by Heero14 on 2011-12-05
Hi, me and other students at my university all have the same problem. We all have Ubuntu installed on our laptops as a Virtual Machine. We use VMWare to do that and we used the "Bridged Connection" setting for the Internet. On Windows, our laptops connect to the wireless Internet without any problem, but when we launch Ubuntu, the connection is not being made.

It's a problem that is only happening at the university. At my house and at a friend's house, my laptop was able to establish the connection under Ubuntu. Also, this problem seems to occur on all versions of Ubuntu.

What could be the problem?

---

### Post by oldtimer7777 on 2011-12-05
> **Heero14 said:**
> Hi, me and other students at my university all have the same problem. We all have Ubuntu installed on our laptops as a Virtual Machine. We use VMWare to do that and we used the "Bridged Connection" setting for the Internet. On Windows, our laptops connect to the wireless Internet without any problem, but when we launch Ubuntu, the connection is not being made.

It's a problem that is only happening at the university. At my house and at a friend's house, my laptop was able to establish the connection under Ubuntu. Also, this problem seems to occur on all versions of Ubuntu.

What could be the problem?

I think what you need to do is refresh the VMWare NAT bridge while you are connected to the internet at school. If you installed VMWare while you were connected to the university network, this problem would probably not exist.  VMWare may not have the right bridged connection configuration while you are at school.. for the virtual Ethernet adapter...  but then again that isn't really a solution to the problem... why?

This is also a Windows issue, not an Ubuntu issue. If you were running Linux instead of Windows as your base-OS, this wouldn't happen. Put your Windows in VMWare and forgetaboutit. Windows is making things harder then they need to be to run your VMWare bridge with your virtualized Ubuntu OS. Call University support and ask them to help configure your windows to reconfigure your VMWare bridge virtual ethernet adapter configuration settings for internet connectivity. If they can't do it, and your instructor doesn't know how to reconfigure VMWare virtual ethernet adapter settings, get over it and simply install Ubuntu to your physical HDD in side-by-side partitioning on your windows computers hard drives (ditch VMWare altogether), and be done with windows issues forever. Or if it is a project that you only need to do for a couple of hours this semester - well you should be using Wubi instead of VMWare. And tell your instructor I said so. If you need to learn about VMWare, then you are going to need to learn how the virtualized "bridged" ethernet adapter settings work in VMWare, and at the very least your instructor will have the answer to that for your university Internet connectivity.  We wouldn't know what that is either.

---

### Post by Heero14 on 2011-12-06
> **oldtimer7777 said:**
> I think what you need to do is refresh the VMWare NAT bridge while you are connected to the internet at school. If you installed VMWare while you were connected to the university network, this problem would probably not exist.  VMWare may not have the right bridged connection configuration while you are at school.. for the virtual Ethernet adapter...  but then again that isn't really a solution to the problem... why?

This is also a Windows issue, not an Ubuntu issue. If you were running Linux instead of Windows as your base-OS, this wouldn't happen. Put your Windows in VMWare and forgetaboutit. Windows is making things harder then they need to be to run your VMWare bridge with your virtualized Ubuntu OS. Call University support and ask them to help configure your windows to reconfigure your VMWare bridge virtual ethernet adapter configuration settings for internet connectivity. If they can't do it, and your instructor doesn't know how to reconfigure VMWare virtual ethernet adapter settings, get over it and simply install Ubuntu to your physical HDD in side-by-side partitioning on your windows computers hard drives (ditch VMWare altogether), and be done with windows issues forever. Or if it is a project that you only need to do for a couple of hours this semester - well you should be using Wubi instead of VMWare. And tell your instructor I said so. If you need to learn about VMWare, then you are going to need to learn how the virtualized "bridged" ethernet adapter settings work in VMWare, and at the very least your instructor will have the answer to that for your university Internet connectivity.  We wouldn't know what that is either.

I found the problem today. I had a feeling it was that but I just needed to make sure. It seems the university doesn't give permission to a single MAC address to have two different IPs simultaneously, hence why a bridged connection doesn't work. I changed the settings to NAT and it fixed the problem, since Windows and Ubuntu are now sharing the same IP.

---

