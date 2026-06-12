---
title: "Cannot Load Ndiswrapper Module..."
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by icanfly0307 on 2008-12-18
Hi. I recently installed a secondary kernel alongside the stock kernel and I'm trying to get my wireless working in it. I can connect flawlessly with the stock kernel but whenever I do [FONT="Courier New"]"sudo modprobe ndiswrapper"[/FONT] in the secondary kernel, I keep getting: [FONT="Courier New"]"FATAL: Module ndiswrapper not found"[/FONT] Can anyone help? I would really appreciate it.

Thanks

---

### Post by kevdog on 2008-12-18
Probably in the stock kernel you had downloaded ndiswrapper from repository.  Did you compile ndiswrapper for your new kernel?  Custom kernel modules are just that -- they are custom for one particular kernel version.  ndiswrapper -- which is a custom kernel module -- must always be reinstalled (either via compilation/installation or via repository) for every new kernel version.

---

### Post by icanfly0307 on 2008-12-18
Thank you. I'll try it out. However, whenever I try to install NDISwrapper, I keep getting an error that it's already installed. I also tried ndiswrapper -m to install the module for my kernel. It keeps telling me "Update-Modules is Deprecated". Any suggestions? Thanks.

---

### Post by Ayuthia on 2008-12-18
You cannot install ndiswrapper from the repositories.  It will not work with your custom kernel (ndiswrapper is a kernel module and the repository version is built specifically for the Ubuntu kernels only).  You will need to uninstall the repository version and compile the ndiswrapper source.

---

### Post by icanfly0307 on 2008-12-19
Thanks. Luckily I've done this before on my Fedora installation so I know pretty much what to do. Thanks again.

---

