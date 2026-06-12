---
title: "VSFTP to NFS connection through a firewall - what ports to open?"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by HellesAngel on 2012-07-15
I am trying to set up a VSFTP server that will serve a directory that is on a NFS server that is on the other side of a firewall.  Most things work fine, but there seems to be some service that I cannot identify that insists on using a random port number.

The setup is this:
NFS Server QNAP TS-459 Pro II, static IP 192.168.1.12, on Green subnet.
Exports a /media share.

Connected to:
IPCOP v2.0.4 Firewall 
Ports forwarded between the green and orange subnets: sunrpc 111, nfs 2049, portmap 4000-4003 , vsftp 12000-12010

Connected to:
Host running Ubuntu 12.04 Server, static IP address 192.168.10.2 that acts as a VSFTP server, this is on the Orange (DMZ) subnet.
The /media share is mounted, the data is accessible.  I have followed [this page]("http://bryanw.tk/2012/specify-nfs-ports-ubuntu-linux/") to try to restrict the services that NFS uses to specific ports - statd, lockd, mountd - hence the numbering above.

> 
# nano /etc/fstab
192.168.1.12:/media       /home/guest/media   nfs  ro,soft,intr,rsize=8192,wsize=8192

# showmount -e 192.168.1.12
/media

# rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100021    1   udp   4002  nlockmgr
    100021    3   udp   4002  nlockmgr
    100021    4   udp   4002  nlockmgr
    100021    1   tcp   4002  nlockmgr
    100021    3   tcp   4002  nlockmgr
    100021    4   tcp   4002  nlockmgr
    100024    1   udp   4000  status
    100024    1   tcp   4000  status
 What happens in VSFTP allows me to login, see the directory tree, navigate up and down, but any attempt to access a file causes another login request then nothing.

Sometimes I see this in the logs:

> 
**Time**     **Chain**     **Iface**     **Proto**     **Source**     **Src Port**     **MAC Address**     **Destination**     **Dst [COLOR=Red]Port[/COLOR]**

14:48:17      ORANGE REJECT      **dmz-1**     TCP               [192.168.10.2]("https://192.168.1.1:8443/cgi-bin/ipinfo.cgi?ip=192.168.10.2")               813     :::::               [192.168.1.12]("https://192.168.1.1:8443/cgi-bin/ipinfo.cgi?ip=192.168.1.12") [COLOR=Red]              46629[/COLOR]    The formatting is a bit dodgy but essentially the firewall has rejected a connection attempt from the host to the NFS server on port 46629.  If I open this port then the VSFTP works for a while.

At this point netstat shows this port is in use, but not by which service.
> # netstat -atnp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1036/mysqld     
tcp        0      0 0.0.0.0:6922            0.0.0.0:*               LISTEN      638/sshd        
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      516/rpcbind     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1067/apache2    
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      731/vsftpd      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      638/sshd        
tcp        0      0 0.0.0.0:4000            0.0.0.0:*               LISTEN      689/rpc.statd   
tcp        0      0 0.0.0.0:4002            0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.10.2:21         192.168.1.1:42956       ESTABLISHED 1234/vsftpd     
[COLOR=Red]tcp        0      0 192.168.10.2:813        192.168.1.12:46629      ESTABLISHED [/COLOR]-               
tcp        0      0 192.168.10.2:669        192.168.1.12:2049       ESTABLISHED -               
tcp        0      0 192.168.10.2:21         192.168.1.1:42949       ESTABLISHED 1231/vsftpd     
tcp        0      0 192.168.10.2:6922       192.168.1.84:40905      ESTABLISHED 1239/sshd: toby [pr
tcp6       0      0 :::6922                 :::*                    LISTEN      638/sshd        
tcp6       0      0 :::111                  :::*                    LISTEN      516/rpcbind     
tcp6       0      0 :::443                  :::*                    LISTEN      638/sshd        
tcp6       0      0 :::4000                 :::*                    LISTEN      689/rpc.statd   
tcp6       0      0 :::4002                 :::*                    LISTEN      -               
Any ideas what I missed?

---

### Post by Kirk Schnable on 2012-07-15
You're probably not forwarding the "passive" ports for vsftpd.

In the vsftpd.conf, add directives, like these:

```
pasv_max_port=51000
pasv_min_port=50000
port_enable=YES
```

Now you know what port range (50000-51000) to forward for passive FTP connections to work.

Kirk

---

