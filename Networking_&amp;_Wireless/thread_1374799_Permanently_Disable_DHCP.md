---
title: "Permanently Disable DHCP"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by FJTim on 2010-01-07
Hello all - I need to permanently disable DHCP on all of my machines I support.  For Windows, this is just disabling the DHCP Client service.  Is there a way to disable the DHCP Client for Ubuntu?  I have found very little online - the most I can think of is deleting /etc/dhcp3 or at least take all permissions away (including root).

All machines are assigned a static address, but since my Linux users still have root access, I cannot have them change any settings - whether through the GUI or CLI.

TIA

---

### Post by chili555 on 2010-01-07
> I cannot have them change any settings - whether through the GUI or CLI.Aren't iwconfig and ifconfig changes privileged, that is, requiring the super user's password? Can you not withdraw priveleges in System -> Administration -> Users and Groups?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SlugSlug on 2010-01-07
> **FJTim said:**
> Hello all - I need to permanently disable DHCP on all of my machines I support.  For Windows, this is just disabling the DHCP Client service.  Is there a way to disable the DHCP Client for Ubuntu?  I have found very little online - the most I can think of is deleting /etc/dhcp3 or at least take all permissions away (including root).

All machines are assigned a static address, but since my Linux users still have root access, I cannot have them change any settings - whether through the GUI or CLI.

TIA

setup  /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.254

or what ever your network settings are
and then sudo chattr +i /etc/network/interfaces

should do the trick

---

### Post by slakkie on 2010-01-07
Removing the dhcp3-client package will make sure DHCP can never be enabled again.

and to prevent people from installing it if they are root:

```

echo -e "Package: dhcp3-client dhcp3-common\nPin: release\nPin-Priority: -10" | sudo tee /etc/apt/preferences
sudo aptitude remove dhcp3-client dhcp3-common

```

After you have done this:

```

sudo aptitude install dhcp3-client
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done
Reading task descriptions... Done
No candidate version found for dhcp3-client
No candidate version found for dhcp3-client
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done
Reading task descriptions... Done

```

Hope this helps.

---

### Post by FJTim on 2010-01-07
SlugSlug & slakkie -

Thanks for these tips.  I combined both of your recommendations and also removed avahi-autoipd.

Thanks again.

---

