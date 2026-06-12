---
title: "Connecting 2 PCs with a crossover cable issue"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by lulacLilla on 2010-04-12
I'm trying to connect two PCs with a crossover cable to transfer some large files.

I've got Ubuntu 10.4beta on one PC and Ubuntu 9.10 on the other.

I've followed the howto from [http://ubuntuforums.org/showthread.php?t=1374953](http://ubuntuforums.org/showthread.php?t=1374953) (see below) however I keep receiving an error message "read: Connection reset by peer" when trying to connect with
sshfs myusername@192.168.2.2:/home/ machine2

Any help please?




> **iponeverything said:**
> Do it the easy way:

Machine 1:

open a terminal and run:

```
sudo nano /etc/network/interfaces

```
Add the following section:

```

iface eth0 inet static
  address 192.168.2.1
  netmask 255.255.255.0

auto eth0

```

Machine 2:

open a terminal and run:

```
sudo nano /etc/network/interfaces

```
Add the following section:

```

iface eth0 inet static
  address 192.168.2.2
  netmask 255.255.255.0

auto eth0

```

The two machines should now be able to ping each other.

now install openssh-server, and sshfs on both machines.

from the prompt of machine one:

```

mkdir machine2
sshfs yourusername@192.168.2.2:/home/ machine2

```

You should now see a folder with other machine show up on your desktop..

---

### Post by 98cwitr on 2010-04-12
can you ping the other machine? ssh installed on both?

---

### Post by lulacLilla on 2010-04-12
> **98cwitr said:**
> can you ping the other machine? ssh installed on both?

openssh-server and sshfs are installed on both machines.

However, I can't ping the machines.

Here's the output:
ping 192.168.2.2
connect: Network is unreachable

---

### Post by 98cwitr on 2010-04-12
but you can ping 192.168.2.1? (ie: local IP) Your link lights flashing?

---

### Post by Iowan on 2010-04-12
It *might* be necessary to use Network Manager to configure a static address - or disable NM. Seems like the newer versions don't play as nicely with */etc/network/interfaces* as the older versions did.
 My Karmic machine had a file (*/etc/NetworkManager/system-connections* that could be edited. That machine got upgraded to Lucid, and now it and the machine I (re)loaded with Karmic have a directory named */etc/NetworkManager/system-connections*, but no file.:confused:

---

### Post by NichoTL on 2010-04-25
> **Iowan said:**
> It *might* be necessary to use Network Manager to configure a static address - or disable NM. Seems like the newer versions don't play as nicely with */etc/network/interfaces* as the older versions did.
 My Karmic machine had a file (*/etc/NetworkManager/system-connections* that could be edited. That machine got upgraded to Lucid, and now it and the machine I (re)loaded with Karmic have a directory named */etc/NetworkManager/system-connections*, but no file.:confused:

In theory setting up the  IP addresses via NM should work. No need to go through the command line (unless you really want to). And you are right it's usually not advised to mess up with the config files AND use NM.

For the original poster: type ifconfig -a on both machines and tell us the output.

---

