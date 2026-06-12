---
title: "nfs issues: rpc time out, filesystem not available on running kernel"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by daryl314 on 2006-07-09
hello,

nfs recently stopped working for me after i upgraded to the latest version of kubuntu.  it was patchy several weeks ago, and seems to have died completely now.  when i try to mount the server with:

*sudo mount -t nfs 192.168.254.3:/data /mnt/server*

i get the error:

*mount: RPC: Timed out*

and when I bring up the "Disk and Filesystem" section of the "System Settings" and look at the configuration of the NFS share, I am seeing a message at the bottom of the window that says:

*The filesystem type is currently unavailable on the running kernel*

I'm not sure if the two errors are connected.  I haven't changed any settings on the server between when NFS worked and when it stopped working.  Does anyone have any insight?  None of the prior threads I saw regarding RPC timeouts were helpful.

---

### Post by gborzi on 2006-07-11
I have had the same problem with nfs mounting, but now it is working. I did the following. I have a desktop PC with two ethernet cards, eth0 is connected to my adsl modem, eth1 is used to connect a laptop. The laptop is the nfs server (I use nfs-user-server) and the desktop is the nfs client. Only when I configured the desktop as a router for the laptop, nfs started to work.
I configured the router in this way: first of all I become root > sudo -i
1) set /proc/sys/net/ipv4/ip_forward to 1 to enable ip forwarding, i.e. > echo 1 > /proc/sys/net/ipv4/ip_forward and saved this configuration in /etc/sysctl.conf uncommenting the line > net/ipv4/ip_forward=1;
2) configured iptables with > iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE saved this configuration with
> iptables-save > /etc/iptables-saved and changed /etc/rc.local by adding the following lines > . /lib/lsb/init-functions

if [ -r /etc/iptables-saved ]; then
   log_begin_msg "Setting iptables"
   /bin/cat /etc/iptables-saved | /sbin/iptables-restore
   log_end_msg $?
fi
after 1) nfs didn't worked, but after 2) it worked great! Also, the ssh connections with the laptop improved. Before I had to wait about 10-15 seconds before getting the password request, now I get it immediately.
I think you will have to use a different command for setting iptables, if you use an ethernet (non-dsl) connection, maybe > iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

Regards.

---

