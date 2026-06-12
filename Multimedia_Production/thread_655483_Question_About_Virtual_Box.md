---
title: "Question About Virtual Box"
date: 2008-01-01
forum: Multimedia Production
---

### Post by xdxoxvx3xrx on 2008-01-01
I just started using Ubuntu and its amazing!

but i have a Zune and i like it a lot 
i have virtual box installed on my computer and it works fine all the music on the virtual machine but when i plug the zune into the USB port it does not show up and neither does anything else i plug into the port. but when i plug the same things into ubuntu it works fine so could some 1 please help me with the USB ports in virtual box?



thanks
dover

---

### Post by philc on 2008-01-01
Sounds like you might need to set up a USB device filter for the Zune.

First, plug your Zune in, but make sure Linux hasn't mounted the device. If it is mounted, unmount it but leave it plugged in.

After launching virtual box, ensure your virtual machine is highlighted then the click "Settings" button. Then highlight "USB" in the list of options. In the right hand box now place a check mark in "Enable USB Controller". Then click the small green plus sign on the right. You should have an option to choose your Zune. This will add a new device filter - ensure there's a tick in the box next to your Zune. Click OK. 

Then start your virtual machine and hopefully the Zune will be recognised.

---

### Post by KOld Iron on 2008-01-01
If you installed the OSE (Open Source Edition) version of Virtualbox, it does not support USB (read  _**[here]("http://www.virtualbox.org/wiki/Editions")**_ at the Virtualbox web site). The USB part of the product is Closed Source. You still can get it free of charge for personal use, you just need to download the full version from their site.

---

