---
title: "Problem with Ubuntu Networking...."
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by mardinn on 2009-01-04
Well I have a HP Pavilion dv6000 and I've got Vista instaled too... and Ubuntu.. the newest one... So I install it log into ubuntu and i can't connect to the internet.. I don't know what to do because this is my first time experience with Ubuntu...

---

### Post by Sprut1 on 2009-01-04
First use:
```
ifconfig
```
in terminal to check if there are any interfaces up, print the output.

---

### Post by mardinn on 2009-01-04
Just asking where's the terminal because I have no idea

---

### Post by Sprut1 on 2009-01-04
Are you using Kubuntu? Then it will be called Konsole. Try the menu where all your applications are, look for Terminal or Konsole.

---

### Post by mardinn on 2009-01-04
kurdistan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:46:4e:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)




This is the log...

---

### Post by Sprut1 on 2009-01-04
Okay, eth0 is the wired network, are you trying to connect wired? If you are trying wireless it won't work because there are no wireless interfaces.

---

### Post by mardinn on 2009-01-04
Well I don't know because I am using now in Vista Wireless name is the   Martins and in Ubuntu is eth0 ... and I can't connect in Ubuntu to any network... and I asked somewhere else and they said that I need some drivers or what...

---

### Post by Natovr on 2009-01-04
What is the type of wireless and wired adapters you have? do you know?
the command "lspci" lists some devices connected... I had the same problem, but with wireless only. My adapter was Atheros 5003 or something. Ubuntu reported it as 
"02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"
My wired network controller is another brand. If your wireless controller is the same brand, then it's the same problem I had.

---

### Post by mardinn on 2009-01-04
kurdistan@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I don't know which ones are which lol

---

### Post by rjmatthews62 on 2009-01-04
> **mardinn said:**
> kurdistan@ubuntu:~$ lspci
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I don't know which ones are which lol
That would be the one.

When you say you can't connect... there is an icon on the top right of the screen, typically 2-3 icons to the left of the OFF button, which controls network access.

If you right click on that, it should give you some options on connecting to wireless.

Have you tried that yet? (Apologies if that's too obvious... :D)

---

### Post by mardinn on 2009-01-04
Yes I tried that and its like disabled... I can't click it..

---

### Post by rjmatthews62 on 2009-01-04
> **mardinn said:**
> Yes I tried that and its like disabled... I can't click it..

The whole network button, or just the wireless section? 

NB: You get different results if you right or left click.

---

### Post by Guille Damke on 2009-01-04
Hi,

I think your wireless adaptor is not supported. What you can try to do is use backports modules: 
1. Go to "system>asministration>hardware_drivers" and check that any "wireless driver (with the Atheros name)" is *DISABLED*. (NOT enable it).
 
2. Then install backports modules: (I think you have installed Intrepid Ibex i.e. 8.10), go to the terminal and run this command for installing these modules (your password will be asked).

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

3. Finally, restart your system and check if your wireless is working, the Wireless networks should be detected in the icon next to clock in the upper-right if backports worked.

Good luck.

---

### Post by mardinn on 2009-01-04
It says that it could not find the package.... Just so u know that I downloaded ubuntu from their website 32 bit version

---

### Post by Guille Damke on 2009-01-04
> **mardinn said:**
> It says that it could find the package.... Just so u know that I downloaded ubuntu from their website 32 bit version

Hi,
You said the package was found. Was the package installed? Did you reboot the system after? 
If the wireless adaptor is working, the wireless is enabled by checking the "enable networking" and "enable wireless" boxes if you right-click on the Network Manager next to the clock. The networks will be listed (and you'll get connected) if you click on it using the left button and selecting a network.

---

### Post by mardinn on 2009-01-04
> **Guille Damke said:**
> Hi,
You said the package was found. Was the package installed? Did you reboot the system after? 
If the wireless adaptor is working, the wireless is enabled by checking the "enable networking" and "enable wireless" boxes if you right-click on the Network Manager next to the clock. The networks will be listed (and you'll get connected) if you click on it using the left button and selecting a network. 
 I am sorry I forgot to write that it did not find

---

### Post by Guille Damke on 2009-01-04
Hi, I just realized that I missed the edited "not" after I posted my last answer.
Are you running Ubuntu 8.04 or Ubuntu 8.10?
Probably, you can try this command, this will be for your Kernel (which will be replaced by the variable "$(uname -r)", which is the output of running the command "uname -r", to show the kernel version that you have.
```

sudo apt-get install linux-backports-modules-$(uname -r)

```

Follow the same steps I told you before, a friend of mine and I could put an Atheros wireless card to work following these steps.
Good luck!

---

### Post by hooookup on 2009-01-04
Mardinn, I am having the exact same problem as you! I switched over from Vista this afternoon and can't get Ubuntu to recognize the broadcom wireless controller. It picked up my wireless internet card from sprint with no problems at all.

I tried installing backports module and it didn't work.

bill@bill-laptop:~$ sudo apt-get install linux-backports-modules-$(uname -r)
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-2.6.27-7-generic
bill@bill-laptop:~$

---

### Post by Guille Damke on 2009-01-04
By the way, since you just installed Ubuntu, did you update your system after installing? If you did not updated it using the icon that shows up next to the clock after installing Ubuntu, it will be good that you do it first (in System>Administration>Update Manager).

---

### Post by mardinn on 2009-01-04
I am running ubuntu 10 I think but I have vista running to on this of. I wrote that and it did not work it said could not find linux-backports-modules-2.6.27-7-generic

---

### Post by hooookup on 2009-01-04
Guille, I am downloading the updates now via my broadband card. Fingers crossed it works!

---

### Post by Guille Damke on 2009-01-04
First try to update your system. Also, update the package list from the repositories.
```
sudo apt-get update
```

In the worst case, go to the Package Manager in System>Administration>Synatpic_package_manager and reload the packages and look for "linux-backports-modules-intrepid" (look for the intrepic-generic package).

---

### Post by mardinn on 2009-01-04
Well it says that it is up to date but when I press the check button it updates but I don't have Internet so it says that I can't update

---

### Post by Guille Damke on 2009-01-04
Ok, in that case connect your computer using the ethernet (RJ-45 cable), to an internet conection (usually wireless routers also include some conectors). 
Your ethernet card should work out of the box. 
When connected, if it is the first time you are connected to the internet, let ubuntu to update its packages (an icon will shows up). It will take ~20 or 30 minutes. In some cases it also suggests to install a Video drive (nVidia users usually). After that, reboot your system!
Finally, try to install the linux-backports-modules-intrepid-generic package, and follow what I suggested before.
Guille.

---

### Post by mardinn on 2009-01-04
I can't find the packet in synaptic package manager

---

### Post by Guille Damke on 2009-01-04
Mardinn,

I think you need to update your list of packages. It will be done as you connect your computer to the Internet and run the updates. Since you don't have wireless, use a cable (ethernet). I guess you have never connected your laptop to the internet under Ubuntu, and that's why it the system thinks that it is up to date and you don't have all the available packages to download. You must be connected to the internet to download these modules.
Good luck trying the ethernet connection!

---

### Post by hooookup on 2009-01-04
Got it working! Thanks everyone!!! Ubuntu runs flawlessly now on my parents laptop. It actually works!

---

### Post by Guille Damke on 2009-01-04
> **hooookup said:**
> Got it working! Thanks everyone!!! Ubuntu runs flawlessly now on my parents laptop. It actually works!

That's good to hear!
Two more things:

1.- In the synaptic package manager, go to settings>repositories>updates and check "unsupported updates (intrepid-backports)" to avoid problems if the kernel is updated. (Did you install the linux-backports-modules-intrepid-generic package? This is the one to install, instead of one targeted for a given kernel version (which I guess would end in 2.6.27-9-generic for you).

2.- Can you post the output of the command ```
lspci
``` to know what is your wireless card model? It can help other people to realize if these steps can work for them.

Enjoy Ubuntu!

---

### Post by hooookup on 2009-01-04
> **Guille Damke said:**
> That's good to hear!
Two more things:

1.- In the synaptic package manager, go to settings>repositories>updates and check "unsupported updates (intrepid-backports)" to avoid problems if the kernel is updated. (Did you install the linux-backports-modules-intrepid-generic package? This is the one to install, instead of one targeted for a given kernel version (which I guess would end in 2.6.27-9-generic for you).

2.- Can you post the output of the command ```
lspci
``` to know what is your wireless card model? It can help other people to realize if these steps can work for them.

Enjoy Ubuntu!

Im unable to post the output of the command. I left the computer with my parents as it theirs and I was only setting up a new OS for them to use since Vista was running so slow on their machine. 
The wireless card is a Broadcom BCM4311

I followed the steps in the following thread and then combined that with the information Guille provided and voila. It worked.
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

