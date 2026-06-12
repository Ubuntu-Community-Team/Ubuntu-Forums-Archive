---
title: "Need help connecting"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by brelice on 2009-05-04
:confused:  I have just loaded Ubuntu 9.04 onto a dedicated machine in addition to my XP machine.  I have them both networked through a Netgear ethernet router.  My XP machine is connecting to the internet just fine but the Ubuntu machine still won't go.  It is recognizing the wired network connection.  I don't have a linux driver for my modem which is a Scientific-Atlantic DPC 2100.  My internet provider told me that all I need is a router for both machines to connect.  Idk..... :mad:    Also....I did "Ispci"  and it came up command not found.

---

### Post by RedSingularity on 2009-05-04
The command is "lspci"

Try that and post the output.

---

### Post by brelice on 2009-05-04
brelice@brelice-desktop:~$ |spci  
 bash: syntax error near unexpected token `|'  
 brelice@brelice-desktop:~$ lspci  
 00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)  
 00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)  
 00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)  
 00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)  
 00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)  
 00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)  
 00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)  
 00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)  
 00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)  
 00:09.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller 2 (rev a2)  
 00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)  
 00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)  
 00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 02:06.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)  
 02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)  
 02:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)  
 02:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)  
 02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)  
 02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)  
 03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)  
 brelice@brelice-desktop:~$

---

### Post by brelice on 2009-05-04
...also ....should I have installed the amd64 version of Ubuntu?  Does it matter?:redface:

---

### Post by RedSingularity on 2009-05-04
I doesnt matter.  So this is a wired connection you are having problems with?  And the network manager recognizes the network?  Look in System>admin>hardware drivers, for some drivers.

---

### Post by brelice on 2009-05-04
"No proprietary drivers are in use on this system."

---

### Post by brelice on 2009-05-04
....and yes it is a wired connection.

---

### Post by brelice on 2009-05-04
On connection settings I have "IPv4 Settings" at "Automatic (DHCP)" for Auto eth1

and for Auto eth0 I have IPv4 Settings at Manual and I put in my IP address from my XP machine.  Should I do something different there?

---

### Post by RedSingularity on 2009-05-04
Try setting it all to automatic.

---

### Post by brelice on 2009-05-05
nuthin.  What about changing browser settings?  Would that make a difference?  How should I check connectivity to internet?.....    "ping Google.com" ....navigate in Firefox?

---

### Post by RedSingularity on 2009-05-05
Just to clarify.......you are connected to your network?

---

### Post by RedSingularity on 2009-05-05
Go to system>admin>network tools.

Choose the ping tab.  Type in [www.google.com](www.google.com)

You should get pings if your settings are correct.

---

### Post by brelice on 2009-05-05
Didn't get anything.  To verify .....I have the network icon at the top right of my desktop....the two little computers......I assume that means I have some kind of network connection.  I set each connection to automatic.  Didn't get a ping.  

I appreciate the help.

---

### Post by RedSingularity on 2009-05-05
No problem.  :)  Click the network connection icon?  Does it give option to connect to anything?

---

### Post by brelice on 2009-05-05
"Wired connection 1" or "Auto eth1"

---

### Post by RedSingularity on 2009-05-05
Can you choose any of those?

---

### Post by brelice on 2009-05-05
switched to Auto eth1 and now no connection

---

### Post by RedSingularity on 2009-05-05
Oh so i guess you were connected before?  We just were not getting any pings.

---

### Post by brelice on 2009-05-05
When I went to "Shared to other computers" in IPv4 Settings it did a connection.  But I still don't get a ping.  Then when I switch back to Automatic (DHCP) and try to switch from Wired connection 1 to Auto eth1 it loses connection.  Does that mean anything?  What is Shared to other computers?

---

### Post by RedSingularity on 2009-05-05
That allows your internet to be shared with other computers networked to that one.....thats not necessary.  It should be "Automatic DHCP"

---

