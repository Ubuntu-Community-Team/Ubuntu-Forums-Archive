---
title: "Trying to get diskless frontend working...and failing"
date: 2011-11-05
forum: Mythbuntu
---

### Post by myth01 on 2011-11-05
Please help!  This is driving me nuts and have spent about 7 hours today working on this.

Rebuilt my myth server today using Ubuntu Server 11.10 (which in itself was an ordeal: installed mythbuntu-desktop for a temporary GUI, it wouldn't boot properly, removed lightdm, installed gdm and it seemed to work.  Wish I'd just tried ssh and x forwarding sooner).

Using a combination of these sites:
[http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless]("http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless")
[http://www.wentztech.com/radio/Linux/files/mythbuntu-netboot.html]("http://www.wentztech.com/radio/Linux/files/mythbuntu-netboot.html")
[https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless")

I have tried to get a diskless frontend to boot.  The initial stages seem to be ok, DHCP works, it loads vmlinuz and initrd and then begins the boot sequence (quiet and splash removed from kernel options) but after a few seconds it displays something like:
```

filename: /pxelinux.0

Error: Socket failed: Connection Refused

Begin: Retrying nbd mount: Connection Refused
End
Begin: Retrying nbd mount: Connection Refused
End
Begin: Retrying nbd mount: Connection Refused
End
Begin: Retrying nbd mount: Connection Refused
End
Begin: Retrying nbd mount: Connection Refused
End
Begin: Retrying nbd mount: Connection Refused
End

```

(recreated from my memory - it scrolls quickly)

and this continues until I power it down manually.  Believing it to be an nbd issue I have Googled as much as I can but all that seems to happen with any change is the error message changes.

ltsp image created with
```
ltsp-build-client --mythbuntu --mythbuntu-credentials="matt:xxxxx"
```


/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default:
```
default ltsp


label ltsp
kernel vmlinuz
append ro initrd=initrd.img nbdname=ltsp_i386 
```

/etc/nbd-server/config:
```
[generic]
user = nobody
group = nogroup
oldstyle = false

[ltsp_i386]
exportname = /opt/ltsp/images/i386.img
readonly = true
```

I really want to get this working as we have 3 frontends and to be able to update them (and my custom theme), with the single PXE image, in one go will make life much easier.

Any other files/information that's helpful let me know.

---

### Post by tebrown on 2011-11-09
I had a similar problem, and I am not sure if it's with NBD server or the kernel. Regardless, I fixed it by using the following configuration:

/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default:

```
default ltsp


label ltsp
kernel vmlinuz
append ro initrd=initrd.img quiet splash nbdport=2000
``` 

/etc/nbd-server/config:
```
[generic]
user = nobody
group = nogroup
oldstyle = true

[export]
exportname = /opt/ltsp/images/i386.img
readonly = true
port = 2000
```

---

### Post by myth01 on 2011-11-09
Hi tebrown,

Not really sure how to proceed, the other day I tried

```
sudo dpkg-reconfigure nbd-server
```

and answered the questions I don't remember being asked (at all) when it first installed.  It added the line to inetd.conf for nbd and port 2000.  Previously

```
sudo netstat -tlnp
```

has shown nbd-server listening only on port 10809, not sure if that made the difference?

Now my files look like this:
/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default:

```
default ltsp


label ltsp
kernel vmlinuz
append ro initrd=initrd.img nbdname=mythtv
```

/etc/nbd-server/config
```

[generic]
# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
        user = nbd
        group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
        oldstyle = true
[mythtv]
        exportname = /opt/ltsp/images/i386.img
        port = 2000

```

Interestingly it doesn't seem to matter what the export section name is compared to the nbdname in the default file.

It seems to be working now though....

---

### Post by myth01 on 2011-11-09
Actually, something else I'm still struggling with is getting the diskless frontend to take the hostname given it in /etc/ltsp/dhcpd.conf.  It gets the correct IP address but its hostname remains as it's MAC address.

I've tried putting a hostname in /opt/ltsp/i386/etc/hostname but no joy...

Any ideas?

---

### Post by santhony on 2011-11-15
Thanks for the Posts.. between the two instructions, I was able to get everything working again...

It appears that the default settings of NBD have changed.. That is instead of defining ports in numbers, it now allows you to define a port using a name..

I would try the dpkg-reconfigure nbd-server first...

---

