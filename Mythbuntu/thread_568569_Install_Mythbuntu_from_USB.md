---
title: "Install Mythbuntu from USB"
date: 2007-10-06
forum: Mythbuntu
---

### Post by packet on 2007-10-06
Has anyone tried to install mythbuntu from a USB drive yet?  I'm assuming I can kind of follow these instructions: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html) and just stick the mythbuntu ISO in instead of the normal one.  

I'm getting ready to do a frontend install on a Zonbu and of course they don't have CD drives.  It will also be a bit more complex as I'm installing onto a 4GB flash drive but apparently that has been supported for a release or two.  

I'll post a step by step if I get it all working...

---

### Post by superm1 on 2007-10-06
> **packet said:**
> Has anyone tried to install mythbuntu from a USB drive yet?  I'm assuming I can kind of follow these instructions: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html) and just stick the mythbuntu ISO in instead of the normal one.  

I'm getting ready to do a frontend install on a Zonbu and of course they don't have CD drives.  It will also be a bit more complex as I'm installing onto a 4GB flash drive but apparently that has been supported for a release or two.  

I'll post a step by step if I get it all working...

Well this appears as though it should feasibly work fine.  I'd be interested to hear your results though :)

---

### Post by packet on 2007-10-09
So while my Zonbu isn't here yet (maybe tomorrow!) I've been working on the mythbuntu USB dongle and wasn't having success with that method above, it kept failing saying it couldn't find the ISO.  So I tried this method:

[http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160)

And that worked perfectly, basically instead of a simple boot with ISO like the first link I posted, this is a full build it up like a live CD copying files from the mythbuntu ISO.  

So it works, it booted up and ran the mythfrontend, I have not been able to test the install from it as I was using my work laptop :) and all my other machines are in use.  I'm toying with the idea of trying to force my vmware to use it instead of a CD to boot using it as a second hard drive in the raw format but at this point I'm pretty happy with the results and I'm willing to wait until tomorrow to actually try it out.

More to come.  I'll probably post a whole separate Zonbu post if all goes well, perhaps even if it doesn't go well.

---

