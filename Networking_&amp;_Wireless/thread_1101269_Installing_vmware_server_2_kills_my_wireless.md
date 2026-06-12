---
title: "Installing vmware server 2 kills my wireless"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by Sooper-Gooner on 2009-03-20
[I'm not sure if this is the right place for this thread, so please move it if necessary.]

I'm running Ubuntu 8.10 on a Compaq CQ50-110EM. Until I installed vmware server 2 everything, including wireless networking, was working perfectly.

I followed this guide to install vmware server 2 ([http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/]("http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/")). 

So, I follow the installation steps as per the guide and vmware server installs successfully. All the services start and I can log into the web admin site.

Then, I copy AN EXISTING XP VM to my machine and add it to the VM inventory. The VM was created using the VM Ware Converter tool. The VM successfully starts, and here's where the problems start...

First, the VM machine has no networking. When I type 'ipconfig' on the XP machine I get 'media not connected'. The VM machine also shows that no netwokring is active through the admin console.

Then, if I restart my host, when it comes back up I don't have any wireless networking anymore. Normally I'm prompted for a password to unlock the keyring, but even this stops happening. Only by completely removing vmware server and re-installing my wireless drivers do I get my wireless networking back.

Can anyone offer any advice on how I can sort this out. I really need to be able to run an XP guest VM.

Thanks.

---

### Post by albandy on 2009-03-20
vmware compile some kernel modules, this could be the matter, install vmware and then recompile your wifi drivers.

Also you can use virtualbox wich works very well and have vt-x/amd-V hw virtualization options.

---

### Post by Sooper-Gooner on 2009-03-25
Thanks for the reply. After much "testing" I found that configuring my VM to use NAT instead of Bridged networking solved the problem.

:P

---

