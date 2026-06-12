---
title: "kicking network manager out"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-02-04
Configuring a complex network in Ubuntu SERVER is a breeze. Doing so in Ubuntu DESKTOP has been a mess. The obvious culprit is the GUI based network manager.

What I want to accomplish:

DESKTOP boots up with active networking even before anyone logs in. This would be both wired and wireless. When someone logs in (user or administrator or root), the network manager is NOT started and thus can't mess up the networking.

Multiple IP addresses, including static and calculated, both IPv4 and IPv6. Also some static routes to multiple routers (maybe adding RIP or OSPF in the future). I already made script to do this smoothly in Ubuntu SERVER.

Laptop users can still configure their computer for use at home by SOME means, even if command line or a script.  It's OK to have to reboot to switch between office and home network.

I'd prefer to leave network manager installed, and just have it not run. But if uninstalling it is the best way to get it out of the way, let me know.

So far this is all just Ubuntu, but Kubuntu or Xubuntu might also be preferred by future staff.

---

### Post by puppywhacker on 2010-02-04
just edit the file /etc/network/interfaces. It will configure your interfaces early in the boot process and you can add ipv6 addresses, wireless settings, ifup scripts.

---

### Post by doas777 on 2010-02-04
if all your interfaces have config in your interfaces file, network-manager will load at start but immediately close, leaving a message in the syslog indicating that it found no managed interfaces.

someone mentioned the other day that lucid would not use the interfaces file (which would not be a big surprise, after what they did to menu.lst during the grub upgrade in karmic), but other users have refuted that. I guess we'll have to wait and see.

---

### Post by Skaperen on 2010-02-04
I already tried that ... to put the configs in /etc/network/interfaces.  But network manager stays running and changes the live (in the kernel) configuration eventually.  And the default route changed, too (though the other static routes stayed).

---

### Post by doas777 on 2010-02-04
then just go to system -> prefs -> Startup applications and uncheck "network manager"

---

### Post by Skaperen on 2010-02-04
> **doas777 said:**
> then just go to system -> prefs -> Startup applications and uncheck "network manager"Is that system wide, not per-user?

---

### Post by doas777 on 2010-02-04
> **Skaperen said:**
> Is that system wide, not per-user?
well that would be per user. if you can find out wher the config for that setting is, you can probably edit the files in the skell directory, so that new users would get your edits. sorry I can't provide details on how to do that though.

---

### Post by Skaperen on 2010-02-04
OK, thanks!  I'll try it on my home netbook first.  Too many things running at work to logout (to reset) right now (stuff that needs to keep running overnight).

---

### Post by Skaperen on 2010-02-05
I got network manager to NOT run, finally.  But now these problems:

1.  The /etc/resolv.conf file is empty, except for one line that says Network Manager created it.  If I put something in there and reboot, it becomes empty again.  Something besides Network Manager is messing with this.

2.  The IPv6 link-local address is not being established.  I guess Network Manager took care of that and now I need to.  It was done properly in Ubuntu Server.  So maybe whatever set that up in the Server I now need to run in the Desktop.  Or can someone tell me what the ifconfig options to do tha are (I can just script it).

---

