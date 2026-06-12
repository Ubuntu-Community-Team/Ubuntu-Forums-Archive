---
title: "Network book/Diskless boot Mythbuntu"
date: 2010-04-26
forum: Mythbuntu
---

### Post by B34N on 2010-04-26
I'm running Mythbuntu 9.10 on a backend and I would like to netboot my Dell Zino. I've been using the Zino as a frontend for a few months but I would like to remove its HD and make the machine a bit quiter while also re-purposing the HD.
I did steps:
```
sudo apt-get install mythbuntu-diskless-server-standalone
```
```
sudo dpkg-reconfigure mythbuntu-diskless-server
```
```
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword" --copy-package-lists --copy-sourceslist --accept-unsigned-packages
```
I even ```
sudo invoke-rc.d dhcp3-server restart
```
When I try to netboot all I get is the Ubuntu logo splash screen (The circle of friends logo) and it hangs there. I have let it stay that way for an hour so I don't think it's me not giving it enough time. How do I check a log file to see where it's stopping?

I'm guessing my dhcp.conf isn't setup correctly. My Mythbunto box only has one NIC and I have my Verizon DSL handling DHCP. My DSL is 192.168.1.1 and my backend is "htpc-backend" and the IP address is dynamic. My /etc/ltsp/dhcpd.conf is:
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.20 192.168.1.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.1.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```


```
sudo invoke-rc.d dhcp3-server restart
```

Thank you!

---

### Post by B34N on 2010-04-27
I got it to boot. The problem I was running into was that I tried to specify my machine in the 2nd question using "sudo dpkg-reconfigure mythbuntu-diskless-server" I just changed it back to * and now I can boot.

The computer's name is the MAC address. Should it be this way? 

I now have my router (192.168.1.1) as the DNS and router in dhcpd.conf. Before I set the router to both I wasn't able to find anything on the network or Internet. Below is my dhcpd.conf
```
authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.2 192.168.1.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.1.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```
Now when I go to start my frontend, the main menu screen comes up and then immediately exits. I was having this same problem trying to run from the LiveCD.

---

### Post by B34N on 2010-04-27
I started up the frontend from the terminal and discovered the problem was that the times did not match on the backend and frontend. I did "date" and "tzselect" and corrected the problem.

---

### Post by santhony on 2010-06-01
> **st8ofmi9d said:**
> I'm running Mythbuntu 9.10 on a backend and I would like to netboot my Dell Zino. I've been using the Zino as a frontend for a few months but I would like to remove its HD and make the machine a bit quiter while also re-purposing the HD.
I did steps:
```
sudo apt-get install mythbuntu-diskless-server-standalone
```
```
sudo dpkg-reconfigure mythbuntu-diskless-server
```
```
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword" --copy-package-lists --copy-sourceslist --accept-unsigned-packages
```
I even ```
sudo invoke-rc.d dhcp3-server restart
```
When I try to netboot all I get is the Ubuntu logo splash screen (The circle of friends logo) and it hangs there. I have let it stay that way for an hour so I don't think it's me not giving it enough time. How do I check a log file to see where it's stopping?

I'm guessing my dhcp.conf isn't setup correctly. My Mythbunto box only has one NIC and I have my Verizon DSL handling DHCP. My DSL is 192.168.1.1 and my backend is "htpc-backend" and the IP address is dynamic. My /etc/ltsp/dhcpd.conf is:
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.20 192.168.1.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.1.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```


```
sudo invoke-rc.d dhcp3-server restart
```

Thank you!
I can follow this no problem up till the point:

sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword"

Do I use the Quotes in my command or no quotes??


Can anyone please confirm?

Thanks

---

### Post by tgm4883 on 2010-06-01
> **santhony said:**
> I can follow this no problem up till the point:

sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword"

Do I use the Quotes in my command or no quotes??


Can anyone please confirm?

Thanks

I can't confirm either way, but I would think that it could be used (and should probably work) either way

---

### Post by matt06 on 2010-06-01
> **santhony said:**
> sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "newuser":"userpassword"

Do I use the Quotes in my command or no quotes??

The [MythTVInstallHardyDiskless]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless#Getting%20started") page shows the syntax as "newuser:userpassword", all in quotes, versus "newuser":"userpassword" which looks 'more correct' to me, but I can't confirm either way.

---

### Post by santhony on 2010-06-12
Thanks guys... I've finally got it working!!

---

