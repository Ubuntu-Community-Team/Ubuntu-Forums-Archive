---
title: "Having a VM with both a public &amp; private IP?"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Kobalts on 2013-07-19
The VM we are using now has a static IP address assigned to us by the ISP.

/etc/network/interface shows:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 5.x.x.x
        netmask 255.255.255.248
        gateway 5.x.x.x

iface eth0 inet6 static
        address 2a01:xxx:xxx:xxx::3
        netmask 64
        gateway 2a01:xxx:xxx:xxx::2

``` 
 and the KVM XML file has this for the interface
```

    <interface type='bridge'>
      <mac address='00:30:32:00:a3:21'/>
      <source bridge='br0'/>
      <target dev='vnet2'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```
Now, since we need another IP and we can't get anymore external IPs from the ISP, we have no choice but to use private IPs.

So we did the following changes
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``` 
KVM xml file for VM
```

  <name>gorouted</name>
  <uuid>xxx-xxx-xxx-xxx-xxxxxx</uuid>
  <forward mode='route'/>
  <bridge name='virbr1' dev="eth0" />
  <mac address='52:22:00:e4:10:22'/>
  <ip address='192.168.200.1' netmask='255.255.255.0'>
     <dhcp>
      <range start='192.168.200.2' end='192.168.200.254' />
     </dhcp>
  </ip>
</network>

```
Which does assign the static IP to each VM (192.168.200.*), but I don't understand how to assign a public IP to the VM.
Also had to use iptables on HOST machine to do masquerade & forward, so VM could access the outside network.

I have already read [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)  & [http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking) but it just isn't clicking on what I need to do.


Then we tried to add a virtual interface like this
```

# The primary network interface
auto eth0
iface eth0 inet static
        address 5.x.x.x
        netmask 255.255.255.248
        gateway 5.x.x.x

iface eth0 inet6 static
        address 2a01:xxx:xxx:xxx::3
        netmask 64
        gateway 2a01:xxx:xxx:xxx::2
# The primary network interface
auto eth0:1
iface eth0:1 inet dhcp


```
Using the original KVM xml snippet posted above.
While this does work in that it still works from the external IP, but the other VMs can't see it at all.  In fact ifconfig doesn't show anything at all for eth0:1. :confused:

Can anyone give me some hints on how to solve this ?  I must have read about 100 articles, and nothing I have read works out. :(
Basically, all we need is to have each VMs be able to talk to each other and have net access for security updates and backup servers, and then have that one VM with the public IP and a private IP.

Any help is appreciated!

---

