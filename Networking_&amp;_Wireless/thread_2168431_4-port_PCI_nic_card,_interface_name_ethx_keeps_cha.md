---
title: "4-port PCI nic card, interface name ethx keeps changing after reboot"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by huntkey on 2013-08-17
Hi experts,

I have been struggling on this for a while... Basically the NIC works fine but its name keeps changing after every reboot. I have found other posts with the similar problems and I have tried their solutions however I still don't have luck with it... Please help!

Here is my NIC card listed in "lspci"
```
02:00.0 Bridge: Oracle/SUN EBUS (rev 01)
02:00.1 Ethernet controller: Oracle/SUN Happy Meal 10/100 Ethernet [hme] (rev 01)
02:01.0 Bridge: Oracle/SUN EBUS (rev 01)
02:01.1 Ethernet controller: Oracle/SUN Happy Meal 10/100 Ethernet [hme] (rev 01)
02:02.0 Bridge: Oracle/SUN EBUS (rev 01)
02:02.1 Ethernet controller: Oracle/SUN Happy Meal 10/100 Ethernet [hme] (rev 01)
02:03.0 Bridge: Oracle/SUN EBUS (rev 01)
02:03.1 Ethernet controller: Oracle/SUN Happy Meal 10/100 Ethernet [hme] (rev 01)
```

Here is my /etc/udev/rules.d/70-persistent-net.rules for the NIC card. This is after I deleted everything in the file then reboot the PC. So it is kind of system default. Now if I reboot PC again it will add another four lines at the end with eth6-9 and so on for every reboot. 


```
# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:02.1 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:7f:29:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:00.1 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:da:8e:ef", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:03.1 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:5e:43:07", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth5"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:01.1 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:20:f8:57:c6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
```

I am aware that it is issue with OS reading the NIC MAC address so the MAC is different every time and Ubuntu considers that it is a new NIC port. I have found possible solution in this post [http://ubuntuforums.org/showthread.php?t=702116](http://ubuntuforums.org/showthread.php?t=702116) however it doesn't work for me. After I changed my file to look like this my interfaces will become something called "rename1, 2, 3..."

```
# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:02.1 (hme)
SUBSYSTEM=="net", DRIVERS=="hme", NAME="eth3"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:00.1 (hme)
SUBSYSTEM=="net", DRIVERS=="hme", NAME="eth4"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:03.1 (hme)
SUBSYSTEM=="net", DRIVERS=="hme", NAME="eth5"


# PCI device 0x108e:/sys/devices/pci0000:00/0000:00:04.0/0000:01:09.0/0000:02:01.1 (hme)
SUBSYSTEM=="net", DRIVERS=="hme", NAME="eth2"
```

My Ubuntu is brand new install 12.04 32bit on a HP PC.

Help please!! Many thanks!!!

---

### Post by darryn.smith on 2013-11-04
I know your message was posted awhile ago and you may have already found the solution, however for those that haven't here's what I've done to solve the bus based persistent naming requirement on my headless servers. 

Why would you want bus based over MAC based?   udev assigns names to known interfaces based on the mac address, new mac's get a new name.  This is helpful for the average user. Building services that expects an interface name to be persistent but has changed will royally mess up your service configuration.  Sometimes you might have to replace a defective nic card with another one, deploy a static image, or virtual machine.  Some cards don't have a permanent MAC address and generate one on power up. I sometimes have to change mac's to accommodate isp provisioning issues.  I certainly don't want MAC names breaking all my other services. Remember however placing the nic in another slot other than the one defined in your rules will require you to alter your local rules file. 

Here's what I did:

adjust to your needs
 
```
ifconfig -a
```  will list your current devices and the names 

Lets assume eth0 is the one we want to make bus based and persistent. For me this is a onboard nic, but its the same process for all my quad based cards as well.


```
udevadm info -a -p /sys/class/net/eth0
```

Here's the output:  (MAC replaced by XX )

```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:06.0/0000:07:00.0/net/eth0':
    KERNEL=="eth0"
    SUBSYSTEM=="net"
    DRIVER==""
    ATTR{addr_assign_type}=="0"
    ATTR{addr_len}=="6"
    ATTR{dev_id}=="0x0"
    ATTR{ifalias}==""
    ATTR{iflink}=="2"
    ATTR{ifindex}=="2"
    ATTR{type}=="1"
    ATTR{link_mode}=="0"
    ATTR{address}=="XX:XX:XX:XX:XX:XX"
    ATTR{broadcast}=="ff:ff:ff:ff:ff:ff"
    ATTR{carrier}=="1"
    ATTR{speed}=="1000"
    ATTR{duplex}=="full"
    ATTR{dormant}=="0"
    ATTR{operstate}=="up"
    ATTR{mtu}=="1500"
    ATTR{flags}=="0x1003"
    ATTR{tx_queue_len}=="1000"
    ATTR{netdev_group}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:06.0/0000:07:00.0':
    KERNELS=="0000:07:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="tg3"
    ATTRS{vendor}=="0x14e4"
    ATTRS{device}=="0x165b"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x705d"
    ATTRS{class}=="0x020000"
    ATTRS{irq}=="50"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:06.0':
    KERNELS=="0000:00:06.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x1022"
    ATTRS{device}=="0x9606"
    ATTRS{subsystem_vendor}=="0x103c"
    ATTRS{subsystem_device}=="0x1609"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="42"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="2"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```


  This tells us all the information we need. 

Remove reference to eth0 in /etc/udev/rules.d/70-persistent-net.rules  


Now create a new file in /etc/udev/rules.d/99-local-net.rules       (I've named mine 99-local-net.rules)

And based on the information 

```
SUBSYSTEMS=="pci", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:07:00.0", NAME="p1p0"
```

In many how-to's on the net I've noticed they have the wrong key's.     

The keys that work for me are SUBSYSTEMS=="pci"  If we were dealing with MAC address we'd see from the output above it's SUBSYSTEM.  
pci is keyed under SUBSYSTEMS.   I missed this for a day and it drove me nuts trying to figure out why udev was ignoring my rules.   
Also notice it's KERNELS not KERNEL for bus based naming. 

0000:07:00.0  is exact location of the nic.  It's found looking at the KERNELS key (as well as elsewhere)


So for the OP it should read like this in 99-local-net.rules


```
SUBSYSTEMS=="pci", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:02:00.1 ", NAME="net1"
SUBSYSTEMS=="pci", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:02:01.1 ", NAME="net2"
SUBSYSTEMS=="pci", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:02:02.1 ", NAME="net3"
SUBSYSTEMS=="pci", ACTION=="add", DRIVERS=="?*", KERNELS=="0000:02:03.1 ", NAME="net4"
```

Why did I use net1,net2, etc? 

Sometimes there's a issue naming them ethX this is generally used by the kernel.  It's better to use something else net1, etc, or wan, local anything you like except for ethX.  Just from my experience.  


Lets test the rule

```
udevadm test /sys/class/net/eth0
```

We should see lots of output ..  look to see if its parsed your new rule

```
parse_file: reading '/etc/udev/rules.d/99-local-net.rules' as rules file

```

And further down we should see 

```
INTERFACE=net1
INTERFACE_OLD=eth0
```


That should do it.   

Hope that helps someone out.

---

