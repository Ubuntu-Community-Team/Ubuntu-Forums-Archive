---
title: "Unable to connect/ping Ubuntu server from Windows computer"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by czecks on 2013-03-02
Hey everybody,

I am new to the forums and Ubuntu, but thanks for having me.  I am having trouble connecting and pinging Ubuntu server from separate physical machine in my network that happens to be wirelessly connecting to the Internet.  My Ubuntu server is installed on a virtual machine on one of my windows 7 dektops.  I am able to remote desktop and ping the Ubuntu server from the Windows 7 operating system that sits on the same physical hardware.

I know I am missing something here, but I just can figure it out.  I also did several hours of searching before posting this as well, but any help is greatly appreciated.

Thanks.

Here are my Ubuntu server specs:

Ubuntu server 12.10 with Ubuntu desktop 12.04 installed on a Virtual Machine.
Virtual machine sits on Windows 7 desktop computer connected via ethernet cable to router
Installed Apache2, xrdp for remote desktop and web server
static IP setup

ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:03:33:f3
          inet addr:192.168.86.128  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe03:33f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78077827 (78.0 MB)  TX bytes:185467111 (185.4 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:283992103 (283.9 MB)  TX bytes:283992103 (283.9 MB)

---

### Post by Mr. Shannon on 2013-03-02
What VM software are you using?  How is your network connection setup in the VM software?   Bridged is probably the easiest way to get your server to be seen by the network.  If you are using NAT you probably need port forwarding (not sure).  And if it is host only then that definitely explains the problem.

---

### Post by czecks on 2013-03-02
Hey Mr. Shannon.

I am using VMware player as my virtual box.  When I open up my network settings on my Windows 7 machine hosting the virtual machine, see no internet access to the VMware network.  I am currently looking into the bridged solution, but currently no luck.

---

### Post by Mr. Shannon on 2013-03-02
I am not familiar with VMware but the settings you are looking for are for the VM not your Windows 7 host.  So I would look in the network settings for your VM inside VMware player.  At least that is where they are in VirtualBox.

---

### Post by czecks on 2013-03-02
I was able to find where to change vmware player network settings.  I changed it to use bridged, but then I lost internet within my vm and still could not ping within or outside of the vm.

---

### Post by Mr. Shannon on 2013-03-02
Did you do:
```
sudo service networking restart
```
inside the VM after changing the network settings.

---

### Post by czecks on 2013-03-02
Yes, I just tried that as well as rebooting my Ubuntu server.  Is there anything on the host machine that I need to configure at all for for the VMware Network Adapters?  "Access type" still says No Internet Access, but I am not sure if I need to configure anything on that end.

Right now my VMware Player is in bridged network mode and I cannot access the ubuntu server via ICMP putty, or remote desktop.  I also cannot access the Internet within Ubuntu or ping any hosts.

---

### Post by Mr. Shannon on 2013-03-02
If it says "No Internet Access" in VMware then that is probably the problem.  I suggest that you read up on how to properly setup a bridged network adapter for a VM in VMware.  What it should do is give your VM direct access to the network hardware on your host machine.  Sorry I could not be of more help.  Hopefully someone will come along who knows VMware.

---

### Post by Doug S on 2013-03-02
I have an Ubuntu server under vmware on a windows vista LapTop. I rarely use this setup, but tried again for this thread.
When I set "bridged" instead of "NAT" under the vmware settings, then nothing worked, until I re-booted the virtual machine.
Then, I noticed that it had gotten a proper IP address from the guest pool of my main DHCP server (also a real Ubutnu server) and I could then access it from other computers on my network.
I noticed in the OP that static IP address was mentioned. That would be a difference between us, as my virtual machine is using DCHP and when using "NAT" it gets some IP address that only the vmware host knows about, and when "BRIDGED" is used it does as I mentioned.

Hope this helps.

---

