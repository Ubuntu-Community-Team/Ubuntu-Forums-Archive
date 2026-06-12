---
title: "rc.local doesn't mount"
date: 2009-08-30
forum: Mythbuntu
---

### Post by Mephi on 2009-08-30
Hi Guys,

I'm working on my mythbuntu frontent (connecting to an ubuntu server backend) and I'm trying to get it to map the varuous conent locations to my server (videos, music, etc)

Originally I had them setup to just mount in fstab, but this caused the box to take ages to boot while the shares timed out (but they worked once the box booted)

The next thing I've tried is to have them listed in fstab with the noauto switch. I then set /etc/rc.local to mount them once booting has finished. But it's not working.

A sample line from fstab:
[INDENT]//192.168.0.1/videos /var/lib/mythtv/videos/ cifs noauto,username=mythtv,password=mythtv[/INDENT]
A sample line from rc.local:
[INDENT]mount /var/lib/mythtv/videos/[/INDENT]

If I run "sudo mount /var/lib/mythtv/videos/" it works fine.

Any idea what I'm doing wrong?

Cheers,

Matt

---

### Post by ian dobson on 2009-08-30
Hi,

How have you got your network setup? If yur using network manager then your network won't be up when rc.local is run.

It would be better to manually configure your network in /etc/networks/interfaces, with something like:-

```

auto lo
iface lo inet loopback

#On board RTL adapter
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.254

```

Regards
Ian Dobson

---

### Post by Mephi on 2009-08-30
It looks like was using Network Manager, as that fixed it, thanks :-)

Matt

---

