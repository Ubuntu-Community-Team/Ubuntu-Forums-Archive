---
title: "Can't Resolve Network Client Names"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by lancealbertson on 2011-02-21
(New to Ubuntu, so please be kind.)

Why aren't my network names resolving?

My goal is to set up an Ubuntu server to host multiple virtual machines on my home network. Each of the virtual machines should be reachable by both IP address and name.

Currently IPv4 addresses are pingable, but name resolution is spotty, at best.

Current environment:

  1. Ubuntu 10.10 server. OpenSSH and KVM installed at boot. Ethernet connection to the LAN. Virtual bridge created to enable VMs to reach the LAN.

  1a. Ubuntu 10.10 server VM. OpenSSH, avahi-daemon, vim, acpid, and samba installed. Can ping and be pinged by other computers and ssh accesses it fine both locally and remotely via cygwin.

  2. Windows 7 (home starter) - yes my little netbook. Resolves name of #3 (below), but not of #1 or #1a.

  3. Vista (home premium). Resolves name for #1a and #2, but not #1. (NOTE: this is the behavior I expect in general, ie: I don't expect to see #1).

  3a. Ubuntu 10.4 desktop VM running under VirtualBox on the Vista computer. Can ping everyone, but cannot resolve any names. (ALSO: it doesn't show up for other computers on the network, but that is a much lower priority issue.)

  4. Linksys WRG54G2 - all default network settings. Addresses are handed out via DHCP. Haven't mucked with it at all. It resolves names for #1, #1a, #2, and #3 (how does it do that???).

I'm sure I could assign static address and edit host files and patch things up, and I can just use IP addresses if I have to (that's how I'm ssh-ing into the servers now), but I want the correct solution, not some cheesy, brittle hack.

Also, I would like to keep #1 as thin as possible and push the smarts into the VMs it hosts.

Priority is:
  1: name resolution of #1a by all other computers
  2: name resolution of #2 and #3 by #1a
  3: anything else is cream

Thanks tons in advance, and if you need more specific config details let me know.

---

