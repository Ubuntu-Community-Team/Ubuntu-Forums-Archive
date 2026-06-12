---
title: "Lenovo z575 on 12.04, Wired Connection works, but Wireless isn't with Ralink RT3090"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by grimslider75 on 2012-08-10
Here is my Laptop Info:

**Machine Brand and Model**

```
Lenovo ideapad Z575 Laptop, AMD-A6
```**lspci|grep Network**

```
Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
```**iwconfig**

 ```
lo        no wireless extensions.

eth0      no wireless extensions.
```
**iwlist scan**

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```**lsb_release -d**

```
Description:    Ubuntu 12.04 LTS
```**uname -mr**

```
3.2.0-29-generic-pae i686
```What Happened:

My wireless internet connection **worked** before the latest software and kernal updates, about 12 hours ago. After I woke up in the morning, my wireless connection disappeared, even though _*my wired connection works just fine*_. Any suggestions? :confused:  I would appreciate any guidance in the right direction :D

---

### Post by grimslider75 on 2012-08-13
> **grimslider75 said:**
> 
My wireless internet connection **worked** before the latest software and kernal updates, about 12 hours ago. After I woke up in the morning, my wireless connection disappeared, even though _*my wired connection works just fine*_. Any suggestions? :confused:  I would appreciate any guidance in the right direction :D

Is there possibly any way to reverse or recover the previous state of the computer before the upgrade? I have a feeling that something about the update caused something to stop working, because my wireless connection was needed for the update in the first place, so it was surely working just fine before the update.

---

### Post by chili555 on 2012-08-13
Are there any interesting messages here?```
sudo modprobe rt2800pci
dmesg | grep -i rt2
```Thanks.

---

### Post by grimslider75 on 2012-08-13
> **chili555 said:**
> Are there any interesting messages here?```
sudo modprobe rt2800pci
dmesg | grep -i rt2
```Thanks.

Well, I have no clue if the messages were interesting; it spit out this:

```

kurt@kurt-Ideapad-Z575:~$ sudo modprobe rt2800pci
[sudo] password for kurt: 

kurt@kurt-Ideapad-Z575:~$ dmesg | grep -i rt2
[  100.253473] rt2800pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  100.253494] rt2800pci 0000:02:00.0: setting latency timer to 64
[  100.330979] Registered led device: rt2800pci-phy0::radio
[  100.331031] Registered led device: rt2800pci-phy0::assoc
[  100.331083] Registered led device: rt2800pci-phy0::quality

```But whatever happened, my wireless connection suddenly sprung back to life! :D

What in the world did that command do, if you don't mind educating my dull mind? :P

---

### Post by chili555 on 2012-08-13
> But whatever happened, my wireless connection suddenly sprung back to life!

What in the world did that command do, if you don't mind educating my dull mind? It simply reloaded the lazy driver which evidently fell asleep for no reason I can think of. Let's amend one file and make it load automagically on boot:```
sudo su
echo rt2800pci >> /etc/modules
exit
```You should be all set.

---

