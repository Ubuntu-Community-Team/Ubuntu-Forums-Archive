---
title: "Small NFS Problem"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by youngie on 2012-05-13
Hi everyone, first time Linux user so be kind, please :) The problem I'm having is I have a WD TV Live media player and I have managed (with great, great difficulty) to get NFS shares working. The trouble comes when I shut down my PC, when I next boot up the shares are no longer available on the Live, I have to issue the ```
sudo /etc/init.d/nfs-kernel-server restart

``` then the shares show up again. This is not a massive problem but it is a bit annoying, does anyone know how to prevent this or if I am missing anything? Thank you very much in advance.

---

### Post by youngie on 2012-05-15
Bump. Anyone? Using 12.04 Precise.

---

### Post by SeijiSensei on 2012-05-15
Quick and dirty solution is to edit (as root with sudo) the file /etc/rc.local and add the line

```
/etc/init.d/nfs-kernel-server start
```

Alternatively, you can use update-rc.d to create the necessary symbolic links in /etc/rc[0-6].d/ to start and stop the server as appropriate.  Try running the command

```
sudo update-rc.d nfs-kernel-server defaults
``` 

then rebooting.

---

### Post by youngie on 2012-05-17
Thank you. For the second one I get,
```
System start/stop links for /etc/init.d/nfs-kernel-server already exist.
```
not sure about the first do I put it before "exit 0" or after? The file is basically empty apart from comments and the exit line. Cheers.

---

### Post by SeijiSensei on 2012-05-17
Is this machine connected over Ethernet or via wifi?  What may be happening is that there is no network connection when the machine first boots, so the NFS server cannot start.  If the machine is connected via Ethernet, I'd [configure]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html") /etc/network/interfaces to start the network at boot.  Then it will be available to the NFS server.

You shouldn't need to add any commands to rc.local since the server is already set up to start when booted.  For future reference, you'd put them above "exit 0". 

If you're using wifi, it's possible to configure that to start at boot as well, but I've never tried it. Maybe someone else will chime in here.

---

### Post by youngie on 2012-05-17
My PC and WD are both connected through Ethernet. 
This is what the file has.
```
auto lo
iface lo inet loopback
```should I add this after? 
```

auto eth0
iface eth0 inet dhcp

```Thanks again for the help.

---

### Post by SeijiSensei on 2012-05-18
> **youngie said:**
> My PC and WD are both connected through Ethernet. 
should I add this after? 
```

auto eth0
iface eth0 inet dhcp

```Thanks again for the help.

I'd suggest using a static address if the machine is to be used as an NFS server.  Just make sure the address is outside the range assigned by the router via DHCP.  Something like this:

```

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

---

### Post by youngie on 2012-05-18
I've reserved an ip from DHCP in my router so that will keep the same ip if that's what you intended.

---

