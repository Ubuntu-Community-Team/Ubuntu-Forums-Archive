---
title: "Help - 'resolv.conf' being overwritten on startup with DNS from my old VPN settings"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by MonkeyMagic23 on 2009-01-10
I took me a while to get this far. After setting up VPNC to connect to my University network I found that I could only access the internet when the VPN was connected.

Eventually worked out it was a DNS server problem.

The Uni DNS server was at the top of the list in my 'resolv.conf' file. I have now removed the VPNC package and the config files for my Uni connection. I can manually edit the 'resolv.conf' file to remove that DNS server. This works as long as the computer is left on, but every time I restart my computer the Uni DNS server is written back into my 'resolv.conf' file.

I am using a wired network with 'Automatic (DHCP)'.

Help me Ubuntu-Forum, you're my only hope.

---

### Post by tpurch on 2009-01-12
> **MonkeyMagic23 said:**
> I took me a while to get this far. After setting up VPNC to connect to my University network I found that I could only access the internet when the VPN was connected.

Eventually worked out it was a DNS server problem.

The Uni DNS server was at the top of the list in my 'resolv.conf' file. I have now removed the VPNC package and the config files for my Uni connection. I can manually edit the 'resolv.conf' file to remove that DNS server. This works as long as the computer is left on, but every time I restart my computer the Uni DNS server is written back into my 'resolv.conf' file.

I am using a wired network with 'Automatic (DHCP)'.

Help me Ubuntu-Forum, you're my only hope.

You need to check a couple of things: 

Firstly, I am assuming that you are have the resolvconf package installed.  If that's the case, check that the /etc/resolv.conf file is a symbolic link to /etc/resolvconf/run/resolv.conf. if not symbolic link then type the following:

cd /etc;rm resolv.conf ;ln -s /etc/resolvconf/run/resolv.conf .

secondly, check the /etc/resolvconf/run/interfaces/ directory for the vpn interface and delete it.  so if your vpn interface was on "tun0" then you need to delete the "tun0" file(s).  

reboot and all should be fine again.....

---

### Post by dmizer on 2009-01-12
No, resolve.conf will always get overwritten. This is by design.

Add your DNS servers to /etc/dhcp3/dhclient.conf

Uncomment the line that begins prepend domain-name-servers, and edit it so it looks something like this:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Then your DNS servers will be persistent.

---

### Post by tpurch on 2009-01-16
> **dmizer said:**
> No, resolve.conf will always get overwritten. This is by design.

Add your DNS servers to /etc/dhcp3/dhclient.conf

Uncomment the line that begins prepend domain-name-servers, and edit it so it looks something like this:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Then your DNS servers will be persistent.

thanks dmizer, yes resolv.conf is overwritten when you reboot/re-new dhcp etc, I agree that changing /etc/dhcp3/dhclient.conf will make DNS persistent, however if you want DHCP to provide DNS settings but don't want your old VPNC DNS servers to be set in resolv.conf then following  the steps i suggested could fix the problem.  Of course, it assumes that the DHCP server isn't sending the wrong DNS settings in the first place.

---

### Post by MonkeyMagic23 on 2009-01-18
> **tpurch said:**
> thanks dmizer, yes resolv.conf is overwritten when you reboot/re-new dhcp etc, I agree that changing /etc/dhcp3/dhclient.conf will make DNS persistent, however if you want DHCP to provide DNS settings but don't want your old VPNC DNS servers to be set in resolv.conf then following  the steps i suggested could fix the problem.  Of course, it assumes that the DHCP server isn't sending the wrong DNS settings in the first place.

Thanks so much.

Had tried adding "*prepend domain-name-servers 192.168.1.1*" as suggested here and elsewhere but without success. I did not follow the first step in your instructions but did delete the *tun0 *file (which contained the offending DNS) and then re-edited my *resolv.conf* file.

Fixed.

Now just to see what happens when I try using VPN again....

---

