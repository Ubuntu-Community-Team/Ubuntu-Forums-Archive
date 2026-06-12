---
title: "kvm/iptables port forwarding"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by jbfink on 2011-01-20
Hey folks,

I've got an Ubuntu 10.10 AMD64 machine with a few KVM instances, set up through virt-manager.  The instances have private IPs in the 192.168.122 range. The KVM instances work great as-is -- they can reach the internet fine and do stuff -- but I want to be able to forward IP traffic to them, like ssh. So if you ssh to the KVM host (which has a publicly reachable IP) on a certain port (I'm using 2222), it forwards to the ssh on a guest instance.

I found what looks like really straightforward instructions here ([http://serverfault.com/questions/170079/forwarding-ports-to-guests-in-libvirt-kvm](http://serverfault.com/questions/170079/forwarding-ports-to-guests-in-libvirt-kvm)), ran them (adjusted for 192.168.122.), ran iptables -L and iptables -T nat -L to see the new rules, but try as I might, I still get "connection refused" when trying to ssh to what should be the open port. Does anyone know what I might be missing?

---

### Post by jbfink on 2011-01-21
bump, as I believe the post did not show yesterday at all.

---

### Post by freemant on 2011-10-19
This is because libvirtd is adding some iptables rules preventing any connections through the host virtual NIC (see [https://bugzilla.redhat.com/show_bug.cgi?id=433484](https://bugzilla.redhat.com/show_bug.cgi?id=433484)).

As a poor man's workaround, I've created a simple upstart config (/etc/init/fix-kvm-iptables.conf):
```

description     "Fix KVM iptables"

start on started libvirt-bin
stop on runlevel [!2345]

# delete the rule that prevents forwarding to the VM
post-start script
  # it still takes a few seconds for libvirtd to start the virtual
  # networks and make its (bad) changes to iptables, so wait.
  sleep 5s
  logger "Fixing iptables"
  iptables -D FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable
end script

```

Hope this may help some poor souls out there.

---

