---
title: "ATFTPD Mythtv mvpmc startup troubles."
date: 2009-02-15
forum: Multimedia Software
---

### Post by jcoman on 2009-02-15
I started installing a MediaMVP on my Mythbuntu network.  I currently have a backend and a frontend running on separate computers but I am having trouble with the MediaMVP.

When I turn everything on nothing happend on the MediaMVP side.

I think I have the \tftpboot\dongle.bin.config file setup properly but I don't know what triggers this file to download to the MediaMVP.

I don't see anything in the error log but maybe I am looking in the wrong log.

I can ping the address that my DHCP server sends to the MediaMVP but behond that nothing happens.

Any suggestions would be greatly appreciated.

Thanks,
jcoman

---

### Post by sedwards on 2009-10-22
From my /etc/dhcpd.conf file:

        host    mvpmc.example.com
                {
                filename                "dongle.bin.mvpmc";
                option root-path        "/home/mvp,rsize=4096,wsize=4096,nolock";
                fixed-address           mvpmc.example.com;
                hardware ethernet       00:0d:fe:0c:5d:90;
                }

---

