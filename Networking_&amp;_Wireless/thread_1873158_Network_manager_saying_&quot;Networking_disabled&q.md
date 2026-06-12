---
title: "Network manager saying &quot;Networking disabled&quot;"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by cha0s619 on 2011-10-31
Hi,

So today I start up my ubuntu 10.04 box after having changed monitors. The screen just goes black and doesn't show the log in screen so I simply restart and I log in fine. Then I notice there is no Internet and when I click on the network manager icon it says "networking disabled." Where it says that, it isn't clickable. How do I fix this? I'm sure it's not a hardware issue because Windows & my 11.04 partition are working fine.

Thanks.

---

### Post by mikewhatever on 2011-11-01
You should post the output of **dmesg | grep eth**.

---

### Post by cha0s619 on 2011-11-01
output of [B]dmesg | grep eth:

[    0.859836] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.860253] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    0.860258] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.381024] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1a:4d:7b:68:b0
[    1.381028] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3


By the way, I use both a wire connection and a usb wifi adapter
[/B]

---

### Post by mikewhatever on 2011-11-01
Odd. I was hoping to see meaningful error messages, but there were none. How about the outputs of the following:

lspci

rfkill list all

---

### Post by cha0s619 on 2011-11-01
lspci:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)


Nothing happens when I enter "rfkill list all" in terminal.

---

### Post by mikewhatever on 2011-11-01
I've been searching for "forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.", and apparently, there is a lot of info, but no clear answer.

Here is a fairly recent thread:
[http://ubuntuforums.org/showthread.php?t=1811914](http://ubuntuforums.org/showthread.php?t=1811914)

---

### Post by cha0s619 on 2011-11-01
> **mikewhatever said:**
> I've been searching for "forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.", and apparently, there is a lot of info, but no clear answer.

Here is a fairly recent thread:
[http://ubuntuforums.org/showthread.php?t=1811914](http://ubuntuforums.org/showthread.php?t=1811914)

So what would you suggest I should do? Can this be fixed or is that installation done for? Would doing something like updating the installation to 10.10?

---

### Post by cha0s619 on 2011-11-01
I think I've found the solution here: [http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

I haven't tried it yet because now my resolution is out of range so I need to fix that first. Hopefully it will though.

---

### Post by mikewhatever on 2011-11-01
> **cha0s619 said:**
> So what would you suggest I should do? Can this be fixed or is that installation done for? Would doing something like updating the installation to 10.10?

Really don't know. Hope the solution you found works.

---

### Post by praseodym on 2011-11-01
Hi,

the forcedeth module often needs 2 module parameters:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

---

### Post by cha0s619 on 2011-11-02
> **cha0s619 said:**
> I think I've found the solution here: [http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

I haven't tried it yet because now my resolution is out of range so I need to fix that first. Hopefully it will though.

It worked! Turns out Network Manager disables networking whenever you go into suspend/hibernate mode and if recovery from suspend doesn't go correctly Network Manager never gets the chance to reenable it, you you have to do that manually.

Thank you all for trying to help.

---

