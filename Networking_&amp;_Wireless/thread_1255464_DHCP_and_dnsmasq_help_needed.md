---
title: "DHCP and dnsmasq help needed"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Scubdup on 2009-09-01
I'm trying to set up my Ubuntu machine as a DHCP server on my network (to netboot an old laptop, see [here]("http://ubuntuforums.org/showthread.php?p=7876898#post7876898") - not getting much help there).

I have tried setting up dnsmasq as instructed [here]("http://blog.webworxshop.com/2009/06/24/even-easier-netboot-installation"):-

> And add/uncomment/edit the following lines:

dhcp-range=192.168.1.3,192.168.1.50,12h # sets the ip address range and update frequency for the network
dhcp-boot=pxelinux.0 # set up network booting to boot the pxelinux bootloader
enable-tftp # enable built in tftp server
tftp-root=/var/tftpd # set tftp directory

Basically this sets up dnsmasq to be both the DHCP server for the network and push the PXE boot options out over the network. It also enables the built in TFTP server in dnsmasq and sets the directory to serve files from.

...And then I accessed my router and turned off it's DHCP server setting.

but when I tried restarting dnsmasq, I got an error message:-

```
sam@ubuntudell:~$ sudo /etc/init.d/dnsmasq restart
 * Restarting DNS forwarder and DHCP server dnsmasq                                                                        
dnsmasq: failed to create listening socket: Address already in use
                                                                                                                    [fail]

```

Can anyone help me?

---

### Post by Scubdup on 2009-09-02
Anyone?

I'm wondering if the problem is my router which may not have had its DHCP server setting turned off, and may have been acting as another DHCP server. Is this possible?

I have the option of turning its DHCP setting from "server" to "off" or "relay".

Anyone any ideas?

---

### Post by shredder12 on 2009-09-02
Well, running 2 dhcp servers might be giving rise to some sort of conflict.. 
if the router is acting as a dhcp server then you are probably trying to create a lan inside a lan..
which seems useless but shouldn't give rise to this problem..
anyways...try running this command and identify which daemon is creating a conflict..
since you are trying to create a dns server so try looking for port 53..
```
sudo netstat -nlp | grep -w LISTEN
```

don't try stopping that process jst post the result..

---

### Post by Scubdup on 2009-09-02
> **shredder12 said:**
> Well, running 2 dhcp servers might be giving rise to some sort of conflict.. 
if the router is acting as a dhcp server then you are probably trying to create a lan inside a lan..
which seems useless but shouldn't give rise to this problem..I don't think a lan within a lan is what I need to do, but I do think I need to set up my ubuntu machine as the DHCP server even though the router already does this job. I think this is fundamental for the netbooting I'm attempting.
> **shredder12 said:**
> anyways...try running this command and identify which daemon is creating a conflict..
since you are trying to create a dns server so try looking for port 53..
```
sudo netstat -nlp | grep -w LISTEN
```

don't try stopping that process jst post the result..Right. I will do, once I get home and can try it out. Thanks a lot for taking the time to try and help me. Much appreciated.

---

