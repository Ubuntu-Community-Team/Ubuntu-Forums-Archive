---
title: "How to Enable my Samsung DLP 1080 TV as a display"
date: 2012-05-29
forum: Multimedia Software
---

### Post by cerixon on 2012-05-29
Hello this is my second post.   
 I am unable to watch any movies on my Samsung DLP, since after the reinstall. (before I was able).  Since I has to erase out my previous XP and install my 'genuine' Home Edition XP, thing are not the same. :-(
 
I looked up the “Ubuntu Documentation on 'NvidiaMultiMonitors' and try to follow every instructions, but somewhere I have failed,  at first when it booted up and the Samsung showed the desktop, it was not the right size,  and I tried to correct that and that's when everything fell apart.  I did install the “NVIDIA accelerated graphics driver (post-release updates( (version current-updates)”.   
 When i boot now it says:
 "'Could not appy the stored configuration for monitors'  'Error on line 1 char 1 : Document was empty or contained only white space'”
 
Is there any hope for this??
 
 I am using Nvidia GeForce 8400GS 1024MB DDR3,
 My system as follows:
 DeskTop Self Installed - Abit 52N – AMD Athlon 64X2 6000 Dual Core – Nividia GEForce 8400 GS 1GB – 4GB ram – 300GB(IDE) Seagate Drive and 500GB (SATA) Western Digital Drive as Extra Storage only
Windows HE XP.  Ubuntu 11.10 on the 300GB Drv (partitioned)
 
I have also included the lspci 'command and info here'
 cerixon@claude-rixon:~$ lspci  
 00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)  
 00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)  
 00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)  
 00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)  
 00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)  
 00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)  
 00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)  
 00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)  
 00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)  
 00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)  
 00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)  
 00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)  
 00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)  
 00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)  
 01:09.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)  
 01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)  
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)  
 04:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 8400 GS] (rev a2)  
 04:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by cerixon on 2012-05-29
Can Anyone help me with this,  did I put too much info??  I just read another post where one was asked to copy the lspci report, so i added it there.
Please help if you can.

---

### Post by papibe on 2012-05-29
Hi cerixon.

Try generating a new X configuration file:
```
sudo nvidia-xconfig
```
Then restart your machine.

In order to set resolution, and other settings don't use the standard 'Monitors', but 'Nvidia X Server Settings' instead. If you want changes made here to stick. Run it as admin:
```
sudo nvidia-settings
```
When you have the configuration you desired, press 'Save to X Configuration File'.

I hope that help, and tell us how it goes.
Regards.

---

### Post by cerixon on 2012-05-29
To:  papibe;

Thanks for your reply,  i am at work at the moment, will try this once i am home in 7hrs, and will report.

cer

---

### Post by cerixon on 2012-05-30
> **papibe said:**
> Hi cerixon.

Try generating a new X configuration file:
```
sudo nvidia-xconfig
```Then restart your machine.

In order to set resolution, and other settings don't use the standard 'Monitors', but 'Nvidia X Server Settings' instead. If you want changes made here to stick. Run it as admin:
```
sudo nvidia-settings
```When you have the configuration you desired, press 'Save to X Configuration File'.

I hope that help, and tell us how it goes.
Regards.



papibe;
Firstly thank you for the taking the time to help me.
I tried what you told me and it did not work, Ubuntu take longer to boot up and same message comes abt:
"'Could not appy the stored configuration for monitors'  'Error on line 1  char 1 : Document was empty or contained only white space'”
 Will it be easire to erase my hard drive and start over again??
awaiting your reply,

cer

---

### Post by papibe on 2012-05-30
The problem could be with files called monitors.xml and .nvidia-settings-rc.

Try remove them:
```
rm ~/.config/monitors.xml   ~/.nvidia-settings-rc
```
Tell us how it goes.
Regards.

---

### Post by cerixon on 2012-10-20
Hello Papibe;

Sorry for the absence of this long period;  at first i had erased my hard drive, and reinstalled Win XP and Ubuntu 12.04LTS (32bit).  Today I endeavoured to get my Samsung DLP to get it working but alas, failed.

I followed the above instructions, and come up with a 'white screen' on the Samsung and with a small 'x' for a cursor.

Hope you come online soon and able to guide me.  

Thanks

Claude

---

