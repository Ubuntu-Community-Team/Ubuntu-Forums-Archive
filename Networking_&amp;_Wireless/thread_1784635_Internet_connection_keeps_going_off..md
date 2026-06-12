---
title: "Internet connection keeps going off."
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by Sammel on 2011-06-17
OS is Ubuntu 10.04.
I have HomePNA-connection which is converted to Ethernet by Netsys NH-300 HomePNA-Ethernet adapter.

The problems that I have:
Sometimes when I boot I don't get IP from DHCP. If try to ping any address I am told that host is unreachable. 
Sometimes this I can get IP by using command dhlient -r and dhclient to request new ip. Sometimes only way to get my connection to work is booting the computer.

Sometimes the connection works fine from the start but disconnects later for short time. Sometimes this happens every ten minutes, sometimes less often. If I wait for a while the connection might start working again, if not dhclient -r or reboot helps usually. But not always.

I have Windows 7 installed on this machine too, and in it the Internet connection has no problems. 

Any ideas what is the problem and how can I solve it?

---

### Post by ratcheer on 2011-06-17
Check that Ubuntu is using the correct driver for your NIC. I had similar symptoms a few days ago and discovered that my system was using the wrong driver.

Tim

---

### Post by Sammel on 2011-06-17
How do I check that?

System testing shows the name of correct NIC, does this mean drivers are OK?

---

### Post by ratcheer on 2011-06-17
Run: sudo lspci -v

It will show both the name of your NIC and the driver that is being used. Then, research (usually at the company that made the NIC website) what driver that NIC is supposed to use for Linux. In my case, I found that they were different and, after I installed the correct driver, my internet connection became stable.

If the driver in use and the recommended driver are the same, then that is not your problem and you will have to search further for a solution.

Tim

---

### Post by Sammel on 2011-06-17
This is what it tells me about Ethernet controller.
> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8432
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at e800 [size=256]
	Memory at fafff000 (64-bit, prefetchable) [size=4K]
	Memory at faff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=4
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169


Is "Kernel driver in use" about which driver i am using?

---

### Post by ratcheer on 2011-06-17
That is the same NIC my PC has and the same (wrong) driver that Ubuntu chose. So, you need to download driver r8168 for Linux from Realtek Taiwan. Follow the instructions to make the new driver module. Once the new module is built, do the following as root:

1) sudo su (to become root)
2) depmod -a
3) Edit /etc/modprobe.d/blacklist.conf
Add a new line containing: blacklist r8169
Save the file.
4) Edit /etc/initramfs-tools/modules
Add a new line containing: r8168
Save the file.
5) update-initramfs -v -u -k `uname -r`
(Note that in the preceding command, those are NOT quote marks. They are grave accents, on the key to the left of the 1 key above the alpha keyboard.)
6) reboot

Your ethernet will now work. To verify, run "sudo lspci -v" again. It should show module r8168 in use for your NIC.

Tim

PS - It is almost certain that you will have to do this every time a new kernel is released, so keep the driver and instructions handy.

---

### Post by Sammel on 2011-06-17
Thanks. At least yet the connection hasn't disconnected.

> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Kernel driver in use: r8168
	Kernel modules: r8168

Drivers seem to be right ones now?

---

### Post by ratcheer on 2011-06-17
Good work. Sammel. Yes, you are using the correct driver now. Ever since I did that, my connection has been stable.

Tim

---

