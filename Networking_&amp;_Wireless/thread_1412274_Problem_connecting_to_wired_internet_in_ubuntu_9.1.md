---
title: "Problem connecting to wired internet in ubuntu 9.10"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by subhashishdolai on 2010-02-21
I have a problem connecting to the internet using Ubuntu 9.10  .
But the same works fine in Ubuntu 9.04.. First I thought it was my hardware problem and asked my friend(also was using ubuntu 9.04) to try ubuntu 9.10 but he too failed to connect....:confused:

I have an wired ADSL Modem given by my Service Provider.
When I switch on my modem the router gets connected but it cannot connect me to internet...
Please help me out of this problem.
Thanks in advance:)

---

### Post by coffeeaddict22 on 2010-02-21
Hi,
Can you post back the output of the following commands in a terminal (Applications/Accessories/Terminal):
```
nm-tool
lshw
ifconfig

```
It might help to localise the problem.

---

### Post by subhashishdolai on 2010-02-21
abir@abir-desktop:~$ nm-tool


NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:18:F3:8A:37:3A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


abir@abir-desktop:~$ lshw
WARNING: you should run this program as super-user.
abir-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 2013MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: 15.11.1
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP61 SMU
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:fec80000-fecfffff
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:dbfff000-dbffffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:dbffec00-dbffecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:dbff8000-dbffbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE


abir@abir-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:8a:37:3a  
          inet6 addr: fe80::218:f3ff:fe8a:373a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1335 (1.3 KB)  TX bytes:940 (940.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15593 (15.5 KB)  TX bytes:15593 (15.5 KB)

virbr0    Link encap:Ethernet  HWaddr 2e:07:fc:fa:b2:4a  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:3966 (3.9 KB)

---

### Post by x33a on 2010-02-21
Try
```
sudo pppoeconf
```

---

### Post by subhashishdolai on 2010-02-21
I have entered the command [COLOR="orange"]pppoeconf[/COLOR] 




&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; ALL DEVICES FOUND? &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; I found 3 ethernet devices:                              &#9474; 
          &#9474; eth0                                                     &#9474; 
          &#9474; pan0                                                     &#9474; 
          &#9474; virbr0                                                   &#9474; 
          &#9474;                                                          &#9474; 
          &#9474; Are all your ethernet interfaces listed above?           &#9474; 
          &#9474; (If No, modconf will be started so you can load the      &#9474; 
          &#9474; card drivers manually).                                  &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 

yes

          &#9474;               <Yes>                  <No>    



yes

     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; OKAY TO MODIFY &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                    &#9474; 
     &#9474; If you continue with this program, the configuration file          &#9474; 
     &#9474; /etc/ppp/peers/dsl-provider will be modified. Please make sure     &#9474; 
     &#9474; that you have a backup copy before saying Yes.                     &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474; Continue with configuration?                                       &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                  <Yes>                     <No>                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 



     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; POPULAR OPTIONS &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                    &#9474; 
     &#9474; Most people using popular dialup providers prefer the options      &#9474; 
     &#9474; 'noauth' and 'defaultroute' in their configuration and remove      &#9474; 
     &#9474; the 'nodetach' option. Should I check your configuration file      &#9474; 
     &#9474; and change these settings where neccessary?                        &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                  <Yes>                     <No>                    &#9474; 
     &#9474;                                                                    &#9474; 






          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; ENTER USERNAME &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474; Please enter the username which you usually need for     &#9474; 
          &#9474; the PPP login to your provider in the input box below.   &#9474; 
          &#9474; If you wish to see the help screen, delete the           &#9474; 
          &#9474; username and press OK.                                   &#9474; 
          &#9474;                                                          &#9474; 
          &#9474; username________________________________________________ &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                          <Ok>                            &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                       



          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; USE PEER DNS &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; You need at least one DNS IP address to resolve the      &#9474; 
          &#9474; normal host names. Normally your provider sends you      &#9474; 
          &#9474; addresses of useable servers when the connection is      &#9474; 
          &#9474; established. Would you like to add these addresses       &#9474; 
          &#9474; automatically to the list of nameservers in your local   &#9474; 
          &#9474; /etc/resolv.conf file? (recommended)                     &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; LIMITED MSS PROBLEM &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                    &#9474; 
     &#9474; Many providers have routers that do not support TCP packets with   &#9474; 
     &#9474; a MSS higher than 1460. Usually, outgoing packets have this MSS    &#9474; 
     &#9474; when they go through one real Ethernet link with the default MTU   &#9474; 
     &#9474; size (1500). Unfortunately, if you are forwarding packets from     &#9474; 
     &#9474; other hosts (i.e. doing masquerading) the MSS may be increased     &#9474; 
     &#9474; depending on the packet size and the route to the client hosts,    &#9474; 
     &#9474; so your client machines won't be able to connect to some sites.    &#9474; 
     &#9474; There is a solution: the maximum MSS can be limited by pppoe.      &#9474; 
     &#9474; You can find more details about this issue in the pppoe            &#9474; 
     &#9474; documentation.                                                     &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474; Should pppoe clamp MSS at 1452 bytes?                              &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474; If unsure, say yes.                                                &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474; (If you still get problems described above, try setting to 1412    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9474;                  <Yes>                     <No>                    &#9474; 
     &#9474;                                                                    &#9474; 
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                            

          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;               <Yes>                  <No>                      &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; DONE &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; Your PPPD is configured now. Would you like to start     &#9474; 
          &#9474; the connection at boot time?                             &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;               <Yes>                  <No>                &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; ESTABLISH A CONNECTION &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; Now, you can make a DSL connection with "pon             &#9474; 
          &#9474; dsl-provider" and terminate it with "poff". Would you    &#9474; 
          &#9474; like to start the connection now?                        &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;               <Yes>                  <No>                &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                       


          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; CONNECTION INITIATED &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
          &#9474;                                                          &#9474; 
          &#9474; The DSL connection has been triggered. You can use the   &#9474; 
          &#9474; "plog" command to see the status or "ifconfig ppp0"      &#9474; 
          &#9474; for general interface info.                              &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                                                          &#9474; 
          &#9474;                          <Ok>                            &#9474; 
          &#9474;                                                          &#9474; 
          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                       

&#9472;&#9496; 
                                                                       
     
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 




Now what to do??
There is still no internet connection...

---

### Post by northd_tech on 2010-02-21
I actually didn't find anything ethernet/network card-specific in that lshw output.  Can you post the output of these terminal commands:

```
lspci

lsmod

sudo lshw -C network
```

This part makes it look like you are seeing a tiny bit of ethernet traffic (but that might just be talking to the network switch:

> **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:18:f3:8a:37:3a  
          inet6 addr: fe80::218:f3ff:fe8a:373a/64 Scope:Link
          **UP BROADCAST RUNNING** MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:**1335 (1.3 KB)**  TX bytes:**940 (940.0 B)**
          Interrupt:27 Base address:0x2000 

---

### Post by x33a on 2010-02-21
> **subhashishdolai said:**
> I have entered the command [COLOR=orange]pppoeconf[/COLOR] 

....

Now what to do??
There is still no internet connection...

Did you enter everything correctly (the default, yes is sufficient most of the times), but you do have to enter your broadband account info correctly. 

for connecting
```
sudo pon dsl-provider
```

for disconnecting
```
sudo poff
```

---

### Post by Villiam on 2010-02-21
As it looks like it was working before on ubuntu 9.04, and was a wired connection. Previously did you need to install drivers in 9.04? Do you have another NIC available or you swaped it? Are your core network settings are properly configured, ie. dhcp, dns, gateway, firewall etc. Connection is lit up and powered, packets transmitting etc.

Try this: $ dmesg | grep eth
$ ifconfig -a

---

### Post by northd_tech on 2010-02-21
> **subhashishdolai said:**
> abir@abir-desktop:~$ nm-tool
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver: **           forcedeth**
  State:             **disconnected**
  Default:           no
  HW Address:        00:18:F3:8A:37:3A

  Capabilities:
    **Carrier Detect:  yes**
    Speed:           100 Mb/s

  Wired Properties
    **Carrier:         on**

Actually I missed that "forcedeth" driver before in the **nm-tool** command- that looks like the same one that my NVIVIA nForce ethernet uses in my HP DV98xx laptop running Jaunty 9.04 ubuntu.  That has actually worked "out of the box" with every version of Linux (dozens) that I have tried for about 2 years now.

Have you checked with a different internet cable?  I've seen many of those RJ45 ends/connections get messed up.

I'm still not seeing what type (or if) you have any wireless stuff that might be interfering.

Unfortunately, I'm stuck in Vi$ta for a while hosting some file transfers (much better speed still than ubuntu WiFi for whatever reasons).  If I get a chance, I'll dig out a cable and see what my "forcedeth" nForce settings show when I've got an active ethernet link running under ubuntu.

---

### Post by northd_tech on 2010-02-22
OK- I'm currently running off an ethernet cable under ubuntu Jaunty 9.04 with that working nForce ethernet.  **lspci **reports it as:

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

This is portion of the output that looks related to internet or "forcedeth" from **lsmod**:
Module                  Size  Used by
ipt_MASQUERADE         11520  1 
iptable_nat            14724  1 
nf_nat                 30100  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      24216  4 iptable_nat,nf_nat
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
xt_state               10624  1 
nf_conntrack           84752  5 *ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state*
ipt_REJECT             11776  2 
xt_tcpudp              11776  4 
iptable_filter         11392  1 
ip_tables              28304  2 iptable_nat,iptable_filter
x_tables               31624  6 *ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables*

forcedeth              68368  0 

Here is the interesting part from** ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:11:6c:3b:53:81  
          inet addr:192.xx.xx.xx  Bcast:192.xx.xx.xx  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9822288 (9.8 MB)  TX bytes:1553625 (1.5 MB)
          Interrupt:252 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:01:00:10:20:b4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2122 errors:0 dropped:0 overruns:0 frame:11644
          TX packets:1920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1689198 (1.6 MB)  TX bytes:313646 (313.6 KB)
          Interrupt:19 

eth0 is my nForce "forcedeth" interface, and eth1 is a wireless Broadcom 4321 series (that works quite well, but I'm cabled in right now).

Hopefully this might help you compare to what a working version looks like.

@[subhashishdolai]("http://ubuntuforums.org/member.php?u=1022427"):

Maybe you should post the results of this terminal command:

```
lsmod | grep ip

lsmod | grep force

```P.S.  I have disabled IPv6 for speed reasons, so you won't see the ipv6 lines (but they used to be there).

edit:  Also, I am using wicd instead of [Gnome] Network Manager and **nm-tool** gives this:

> The program 'nm-tool' is currently not installed.  You can install it by typing:
sudo apt-get install network-manager
bash: nm-tool: command not found
I prefer to keep wicd though.

---

### Post by northd_tech on 2010-02-22
Whoops- I forgot one:

> **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: **eth0**
       version: a2
       serial: 00:04:4c:2b:22:71
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=forcedeth driverversion=0.61** latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes **port=MII**
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:16:00:43:b4:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.xx.xx.xx latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: b2:e2:b2:b2:b2:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.xx.xx.xx link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 11:24:d0:03:f1:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by subhashishdolai on 2010-02-22
I have entered [COLOR="DarkOrange"]pon dsl-provider[/COLOR]

abir@abir-desktop:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.

what is this 'members' of the 'dip'???

Please note::I can connect to the internet in Windows Xp and also ubuntu 9.04....

---

### Post by subhashishdolai on 2010-02-22
How will I get wicd??
Will wicd work for me??

---

### Post by subhashishdolai on 2010-02-22
> **Villiam said:**
> As it looks like it was working before on ubuntu 9.04, and was a wired connection. Previously did you need to install drivers in 9.04? Do you have another NIC available or you swaped it? Are your core network settings are properly configured, ie. dhcp, dns, gateway, firewall etc. Connection is lit up and powered, packets transmitting etc.

Try this: $ dmesg | grep eth
$ ifconfig -a

No I didn't used any driver. I have no other NIC available..
Yes everything is up and I even get response from [COLOR="DarkOrange"]ping[/COLOR]..

---

### Post by chili555 on 2010-02-22
I don't mean to hijack or step on toes, but I saw this:> sudo lshw -C network
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
--- snip ---
driver=forcedeth driverversion=0.61 latency=0 [COLOR="Red"]link=no[/COLOR] maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MIIAnd I saw this: [http://www.nvnews.net/vbulletin/showthread.php?t=130438](http://www.nvnews.net/vbulletin/showthread.php?t=130438)

And especially this:> I have a DHCP server running for the home LAN here, and as of kernel release 2.6.29 there were some changes to the forcedeth driver code, which powered down the NIC during reboots/power off. It caused havoc for many, because the NIC did not power up at next boot. I couldn't get an IP address without repeatedly restarting the network a bunch of times, and never got an IP during boot, it just hung.

The driver regression was reverted in 2.6.29.3 or .4 but still the default behavior seemed to be to remain powered off.

What I posted above is from my 'forcedeth' file in /etc/modprobe.d folder.
Notice the option "phy_power_down" option! It makes the NIC stay powered up during reboots etc.. Voila! Now it works perfect again, getting its IP from DHCP in a blink of an eye during boot.

You can use either the 'modinfo' command, or look at the bottom of the forcedeth.c sourcecode, for all the parameters you can pass to the driver.
I wonder if the link comes up, you get an IP address and connect if you try:```
sudo rmmod -f forcedeth
sudo modprobe forcedeth phy_power_down=0
```It may take a .conf file and a reboot, if it doesn't work right away. Perhaps creating a file: /etc/modprobe.d/forcedeth.conf with the following:```
alias eth0 forcedeth
options forcedeth phy_power_down=0
```

---

### Post by x33a on 2010-02-22
Afaik, wicd doesn't support pppoe.

[http://wicd.sourceforge.net/moinmoin/FAQ](http://wicd.sourceforge.net/moinmoin/FAQ)

---

### Post by northd_tech on 2010-02-22
Hi chili.

> [http://www.nvnews.net/vbulletin/showthread.php?t=130438](http://www.nvnews.net/vbulletin/showthread.php?t=130438)

And especially this: 	Quote:
 	 	 		 			 				I have a DHCP server running for the home LAN here, and **as of kernel  release 2.6.29 **there were some changes to the forcedeth driver code,  which powered down the NIC during reboots/power off. It caused havoc for  many, because the NIC did not power up at next boot. I couldn't get an  IP address without repeatedly restarting the network a bunch of times,  and never got an IP during boot, it just hung.

The driver regression was reverted in 2.6.29.3 or .4 but still the  default behavior seemed to be to remain powered off.

I think the page break caused a little confusion above.  I have a working NVIDIA nForce ethernet connection in my HP DV98xx laptop that uses that same "forcedeth" module that I noticed above.  I was posting from my working ethernet connection so that we had a working configuration of that to compare to.  I think you read that part of my **lshw** output that was from my working ethernet connection.

On the kernel thing- I'm running an older Jaunty 9.04 2.6.28-18-generic and -17 and -14 kernel(s) , and I've never even had so much as a hiccough using a cable connection with any (of dozens) of Linux versions that I've tried on this HP laptop.

It's good to have a heads-up about a possible "forcedeth" pitfall though (as well as yet more confirmation why I stayed with the older ubuntu ;) ).

Thanks,

NDT

---

### Post by chili555 on 2010-02-22
Gotcha. Sorry I misread.

---

