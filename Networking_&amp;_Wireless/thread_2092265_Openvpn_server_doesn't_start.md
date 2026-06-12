---
title: "Openvpn server doesn't start"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by ksylian on 2012-12-07
Hi,

I'm not an expert user but trying to run a vpn server on Ubuntu.
I followed this tutorial [https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)
and installation went well but the openvpn server doesn't start. I get this error:

# /etc/init.d/openvpn start

 * Starting virtual private network daemon(s)...
*   Autostarting VPN 'server'                                                  S
IOCSIFADDR: No such device
: ERROR while getting interface flags: No such device
SIOCSIFDSTADDR: No such device
: ERROR while getting interface flags: No such device
SIOCSIFMTU: No such device

# /etc/init.d/openvpn status
 * VPN 'server' is not running

It seems that tun interface isn't created but I'm not sure.
Can anyone help, please?

Thanks

---

### Post by SeijiSensei on 2012-12-07
Add "dev tun" to the top of the OpenVPN configuration file and see if it helps.

---

### Post by ksylian on 2012-12-07
dev tun was uncommented

---

### Post by SeijiSensei on 2012-12-07
What do you seen in /var/log/syslog?  For instance in [this discussion](https://forums.openvpn.net/topic8664.html), the problem was that it wanted to create the tun device in /dev/net/tun, but there was no such directory or device.  However, I just installed OpenVPN from the repositories (with "sudo apt-get install openvpn"), and see this:

```

root@vid:/# ls /dev/net -l
total 0
crw-rw-rwT 1 root root 10, 200 Nov 26 13:27 tun

```

Did you install the repository version or install it some other way?  The repository version has always worked for me.

---

### Post by ksylian on 2012-12-08
# ls /dev/net -l
ls: cannot access /dev/net: No such file or directory

I re-installed openvpn from the repositories and it didn't help.

Apparently, there isn't a tun device on my OS. 
I just found out that this is due to kernel not installed properly.

---

### Post by sulliwane on 2013-06-20
Here what solved my problem :
```
[COLOR=#000000][FONT=Consolas]# mkdir /dev/net [/FONT][/COLOR]
# mknod /dev/net/tun c 10 200  
[COLOR=#000000][FONT=Consolas]# chmod 666 /dev/net/tun[/FONT][/COLOR]
```

And here is the problem I had (syslog also complained about directory net that doesn't exist)
```
service openvpn start
 * Starting virtual private network daemon(s)...                                         *   Autostarting VPN 'server'                                                          SIOCSIFADDR: No such device
: ERROR while getting interface flags: No such device
SIOCSIFDSTADDR: No such device
: ERROR while getting interface flags: No such device
SIOCSIFMTU: No such device



```

---

