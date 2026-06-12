---
title: "Cannot connect via Network Manager"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by CkDGTAT on 2013-08-28
Hi,

I am unable to connect via nmcli

```


** (process:7192): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
Error: nmcli (0.9.4.0) and NetworkManager (unknown) versions don't match. Force execution using --nocheck, but the results are unpredictable.
```

Thank you

---

### Post by GwL3eNC on 2013-08-28
Hello,

i hope "nmcli (0.9.4.0) and NetworkManager (unknown) versions don't match" is a clear message.
nmcli is provided by network manager package which version is unknown. I would try to completly remove all network-manager
files using sudo dpkg -P packages. Possibly you need to add the --force-depends option, but
please be careful with it.

Using sudo dpkg -l | grep network-manager you can see the installed packages. After removing
i would do a fresh install of networkmanager.

---

### Post by rstackhouse on 2013-10-15
> **GwL3eNC said:**
>  After removing i would do a fresh install of networkmanager.
After removing network-manager, network-manager-gnome, network-manager-pptp, and network-manager-pptp-gnome and running ```
sudo apt-get install network-manager network-manager-gnome
```

I still get the error mentioned above. 

After running ```
dpkg -l | grep network-man*
```

I see

```
ii  network-manager                  0.9.4.0-0ubuntu4.3                network management framework (daemon and userspace tools)
ii  network-manager-gnome            0.9.4.1-0ubuntu2.3                network management framework (GNOME frontend)
ii  network-manager-pptp             0.9.4.0-0ubuntu1                  network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome       0.9.4.0-0ubuntu1                  network management framework (PPTP plugin GNOME GUI)
```

Is the difference in the revision number between network-manager and network-manager-gnome the problem?

---

