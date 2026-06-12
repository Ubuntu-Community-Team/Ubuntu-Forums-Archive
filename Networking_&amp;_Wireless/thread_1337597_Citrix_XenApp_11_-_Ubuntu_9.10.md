---
title: "Citrix XenApp 11 - Ubuntu 9.10"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by idlemind324 on 2009-11-25
Hello,

I have succesfully gotten the Citrix XenApp 11 client to work in Ubuntu 9.10 32-bit. It was pretty straight forward and there are many guides available for completing it.

My problem is that when I run my system with dual monitors in a shared desktop (twinview) and try to open an application in Citrix as seamless I get an error saying it cannot create a display that size and it opens with a "desktop" like window behind my application and my application is then caged in that windowed "desktop".

Is there anything I can do to make seamless mode work while on dual monitors? Even if it would only have the limited functionality of the MS Windows client which is caging the application to the monitor that Citrix is configured for. I would be happy using my Citrix applications on only my extra monitor instead of directly on my notebooks display.

If it's worth noting Citrix runs perfect on my machine with just one monitor. True seamless mode and all. I feel the root cause of this issue is my desktop is being presented to the client at it's combined resolution which is required for seamless to work. I would think there is a setting on the server I can change to allow it to see the entire desktop so it doesn't fallback on caging it into a smaller desktop.

Thanks in advance.

---

### Post by Virtual Desktop on 2009-11-30
I had this problem in Windows, changing to the XenDesktop plugin instead sorted it. I don't have a Linux machine with 2 monitors and they don't do a XenDesktop plugin for Linux for some reason. So unfortunately i don't think there is solution for this.

Sorry

---

### Post by dretep on 2011-04-20
An old thread but I've got the same problem.  Thought it was perhaps because I was running 64-bit but 64-bit with a single monitor is fine.  Wish Citrix would really support Ubuntu/Linux.

---

