---
title: "Transfer timed out in tftp"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by IAMTubby on 2013-05-17
I'm getting a "Transfer timed out." error when I try to transfer a file using the following command,"tftp -4 10.94.161.170 -c get filename"
These are the contents of my /etc/xinetd.d/tftp
# default: off
# description: The tftp server serves files using the trivial file transfer \
#       protocol.  The tftp protocol is often used to boot diskless \
#       workstations, download configuration files to network-aware printers, \
#       and to start the installation process for some operating systems.
service tftp
{
        disable = no
        socket_type             = dgram
        protocol                = udp
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -c -s /tftpboot
        per_source              = 11
        cps                     = 100 2
        flags                   = IPv4
}

Please advise.
Thanks.

---

