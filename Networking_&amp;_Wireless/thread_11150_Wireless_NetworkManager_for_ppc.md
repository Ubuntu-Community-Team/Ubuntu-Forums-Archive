---
title: "Wireless NetworkManager for ppc?"
date: 2005-01-14
forum: Networking &amp; Wireless
---

### Post by chele on 2005-01-14
I have read about this cool new Network Manager applet that sounds like the cats ass for finding and configuring WiFi networks. [http://people.redhat.com/dcbw/NetworkManager/](http://people.redhat.com/dcbw/NetworkManager/)

There is a Ubuntu/debian build here: [http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/)

However, all I can find to install via apt/synaptic is a network-manager-doc package. I assume that might be because there is no PPC build?

A web search for "networkmanager ppc" shows the existence of a NetworkManager-0.3.2-4.3.cvs20041208.ppc.rpm

So, short of another debian repositry, how can I go about building this from source? Or is there a better way to configure WiFi networks?

---

### Post by hardcandy on 2005-01-14
Will it convert using alien?      "man alien"

---

### Post by chele on 2005-01-14
[QUOTE=hardcandy]Will it convert using alien?      "man alien"[/QUOTE]

Don't know, but I thought it might be better to just build it from scratch. I usually land up in dependency hell converting rpm's. Might be worth a try, though.

---

### Post by chele on 2005-01-14
[QUOTE=chele]Don't know, but I thought it might be better to just build it from scratch. I usually land up in dependency hell converting rpm's. Might be worth a try, though.[/QUOTE]

Tried, no luck ...

:~$ sudo alien NetworkManager-0.3.3-1.cvs20050112.3.ppc.rpm
networkmanager_0.3.3-2_powerpc.deb generated

:~$ sudo dpkg -i networkmanager_0.3.3-2_powerpc.deb
Selecting previously deselected package networkmanager.
(Reading database ... 69332 files and directories currently installed.)
Unpacking networkmanager (from networkmanager_0.3.3-2_powerpc.deb) ...
Setting up networkmanager (0.3.3-2) ...

:~$ sudo NetworkManager
NetworkManager: /lib/libc.so.6: version `GLIBC_2.3.4' not found (required by NetworkManager)

---

### Post by hardcandy on 2005-01-14
I think Ubuntu uses 2.3.2 glibc. Maybe an older version of the package?

---

### Post by chele on 2005-01-24
[QUOTE=chele]

So, short of another debian repositry, how can I go about building this from source? Or is there a better way to configure WiFi networks?[/QUOTE]How does one go about building something like this from source?

[QUOTE=Hubert Figuire]On Wed, 2004-12-15 at 19:15 -0500, Hubert Figuiere wrote:
> Hi,
> 
> I installed NM on my Ubuntu PPC from the Ubuntu source packages
> available at
> 	deb-src [http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/) ./[/QUOTE]There is some sort of dpkg-build-package command, no?

---

### Post by chele on 2005-01-25
[QUOTE=chele]How does one go about building something like this from source?

There is some sort of dpkg-build-package command, no?[/QUOTE]
Yes, there is. First add the appropiate line to /etc/apt/sources.list and run apt-get update:

deb-src [http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/) ./

Away we go!

1] Get any build dependencies:
:~$ sudo apt-get build-dep network-manager

2] build the package the Debian way:
:~$ sudo apt-get -b source network-manager

Oops: "checking for gtk+-2.0... Package gtk+-2.0 was not found..."

1a] A guess at how to get other build dependencies:
:~$ sudo apt-get build-dep  gnome-applets

2] And again: build the package the Debian way:
:~$ sudo apt-get -b source network-manager

3] It Builds! Now install the packages:
:~$ sudo dpkg -i network-manager_0.3.1+cvs20041101-2_powerpc.deb 
:~$ sudo dpkg -i network-manager-gnome_0.3.1+cvs20041101-2_powerpc.deb 

So far so good. We now have Network Manager built and installed on this machine. After rebooting, to make sure that dbus, etc is re-initialized, we logon to Gnome. NetworkManagerInfo shows up in the list of running processes. But no icon shows up in the Notification Area. hmm.

---

