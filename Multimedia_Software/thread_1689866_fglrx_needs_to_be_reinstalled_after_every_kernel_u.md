---
title: "fglrx needs to be reinstalled after every kernel upgrade"
date: 2011-02-17
forum: Multimedia Software
---

### Post by erikla2002 on 2011-02-17
I had this problem for a while now. Every time the update-manager decides to upgrade the kernel my graphics driver is ****** up. I have had this problem in 10.04 and now in 10.10. Now I get dropped to the command prompt after an upgrade (I can also log in with fail-safe/low graphics mode). The problem is solved if I reinstall the package fglrx so nog big issue but it is rather annoying. 

What could be wrong? I am using ATI HD4770. I haven't tried open drivers yet.

---

### Post by lukeiamyourfather on 2011-02-17
Are you using the binary drivers in the Ubuntu repositories that come with Ubuntu or are you using the binary drivers downloaded from the AMD website? If you are using the drivers from the repository then they should automatically handle new kernel upgrades. The driver from the AMD website will break if the kernel changes.

---

### Post by erikla2002 on 2011-02-18
> **lukeiamyourfather said:**
> Are you using the binary drivers in the Ubuntu repositories that come with Ubuntu or are you using the binary drivers downloaded from the AMD website? If you are using the drivers from the repository then they should automatically handle new kernel upgrades. The driver from the AMD website will break if the kernel changes.

I installed the drivers from AMD:s website from the beginning and then changed to Ubuntus repository. When I reinstall I always do a sudo-apt get reinstall fglrx from Ubuntus repository.

---

### Post by lukeiamyourfather on 2011-02-18
There might be another package that goes with the fglrx package which handles the kernel changes. I usually use the "Hardware Drivers" utility in the administration menu of GNOME. I'm not on Ubuntu right now otherwise I'd check that out.

---

### Post by johntaylor1887 on 2011-02-18
> **lukeiamyourfather said:**
> There might be another package that goes with the fglrx package which handles the kernel changes.

That package would be DKMS. It is necessary so that you do not need to reload the video drivers.

---

### Post by erikla2002 on 2011-02-18
> **johntaylor1887 said:**
> That package would be DKMS. It is necessary so that you do not need to reload the video drivers.


I have the DKMS package installed according to Synaptic.

---

### Post by johntaylor1887 on 2011-02-18
Why did you install the Ati drivers from the website instead of the ones offered from system>administration>additional drivers?

---

### Post by erikla2002 on 2011-02-21
> **johntaylor1887 said:**
> Why did you install the Ati drivers from the website instead of the ones offered from system>administration>additional drivers?

There was a new version released and I was stupid enough to upgrade...I can't uninstall the drivers properly. Is there a force flag or something I could use?

---

