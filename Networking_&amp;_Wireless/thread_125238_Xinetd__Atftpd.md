---
title: "Xinetd / Atftpd"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by sojourner9 on 2006-02-03
Not quite sure where to post this, but hope someone can help.

I'm running atftp started from xinetd.  The service starts up fine and will sit and listen for a tftp connection.  But, after the first tftp connection, atftpd will shutdown with this:

atftpd[8216]: atftpd terminating after 300 seconds
atftpd[8216]: Main thread exiting


Here is the config for it in xinetd.conf:
service tftp
{
        socket_type     = dgram
        protocol        = udp
        wait            = yes
        user            = root
        server          = /usr/sbin/in.tftpd
        server_args     = --no-multicast /ftp
        log_type        = FILE /var/log/tftpd
        log_on_failure  = HOST
}


Any idea why the atftp shuts down and I can no longer tftp to the box without restarting xinetd?

---

