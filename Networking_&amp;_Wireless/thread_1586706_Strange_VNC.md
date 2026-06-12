---
title: "Strange VNC"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by scottuss on 2010-10-02
Hello all!

OK, I'll try to be quick:

I have a machine (scott-desktop) that has QEMU running on it. I manage VMs through virt-manager.

scott-desktop has VNC running on it, and I can connect to it via a VNC client by connecting to "scott-desktop"

However, today for some odd reason, I was getting connection refused errors. I telneted to the port, the service was running.

I SSH -X to scott-desktop and ran vinagre over X, and tried to connect to localhost. For a BIZZARE reason, it connected to one of the VMs.

It has never done this before, and nothing has changed. I can correctly connect to scott-desktop by using "scott-desktop:1"

So, I'm no expert, but QEMU (or a VM) is bound to scott-desktop:0 ... right? But how has that happened?

Cheers in advance!

---

### Post by scottuss on 2010-10-02
OK so I've disabled loading the VNC server in /etc/rc.local and no VNC server loads (as expected)

However, I specify in the file to load the server on :0 (port 5900) and it still loads on :1 (5901)

I'm very confused. Does this mean :0 isn't available?

Any VNC / Network experts, PLEASE HELP! :)

---

### Post by scottuss on 2010-10-02
Right, I've figured it out. virt-manager had it's VNC server for one of the VMs bound to 5900.

I don't know why the problem only just surfaced, and I'm concerned that this issue could arise, but I'll investigate later. Thought I'd follow up with this post just in case anyone else has the same issue (I know how useful Ubuntu Forum threads can be, especially ones stumbled upon from Google!

:)

---

