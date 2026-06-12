---
title: "Best practice: use iproute2 or edit 'interfaces' file to set IP info"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by EvertMeirion on 2012-06-13
What I'd like to do is be able to quickly re-configure a machine when I've cloned it.  I built a template ubuntu 12.04 VM, and plan to build and destroy machines at will to test out various stuff.  I would like to write up a bash script to I could run that will prompt me for the hostname, ip addr, etc to reconfigure the machine without having to muck around in config files every time.

So my question is, what might be considered best practice for configuring networking.  Would I just be better off scripting something to edit the /etc/network/interfaces file to change the IP address, using sed or awk? Or should network interfaces be changed using the command 'ip addr add / dev eth0'  

Of course, my experience shows the 'ip' command doesn't change the IP address permanently, so of course that raises the question - why would the command exist if it can't alter the ip address in subsequent sessions? would it be solely to alter it during the current boot, only to revert to what is in the interfaces file when rebooted?

---

### Post by Cheesehead on 2012-06-14
> **EvertMeirion said:**
> ...why would the command exist if it can't alter the ip address in subsequent sessions?

You're right, most 'ip' commands are not persistent. Generally, the config files provide persistence, if desired.

Non-persistent networking commands are useful when the network, and/or the machine's place in the network, or the machine's role may change between sessions. For example, I have one server that also functions as the fallback router for a network. I want the machine to detect primary router failure and reconfigure itself to take on the router role...but upon restart I want it as the secondary again.

One approach for your VM is a first-boot flag file in your template. Upon boot, if the file exists, the new system promptly deletes it and executes whatever setup actions you want, like copying custom /etc/network/interfaces and other settings.

Another approach is to use [FONT="Courier New"]ifup -i /path/to/other/interface.file interface.name[/FONT]. The -i flag allows you to customize which customized interface file you want to use. Handy, so you can leave the original alone, and reconfigure interfaces lots of different crazy ways based on the script's logic.

---

