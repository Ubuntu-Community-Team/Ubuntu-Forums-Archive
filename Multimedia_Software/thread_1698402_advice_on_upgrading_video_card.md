---
title: "advice on upgrading video card"
date: 2011-03-02
forum: Multimedia Software
---

### Post by Criminel on 2011-03-02
Hi,
I'm running 10.04 in a Sempron desktop PC with this motherboard: [http://reviews.cnet.com/motherboards/asrock-alivenf6p-vsta-motherboard/1707-3049_7-33353683.html](http://reviews.cnet.com/motherboards/asrock-alivenf6p-vsta-motherboard/1707-3049_7-33353683.html)  and a Samsung 2032NW monitor.

So far I can't use the native resolution of 1680x1050 (I've used it with 8.04 but 10.04 doesn't work)

Which video card do you guys recommend to upgrade on this machine?

many thanks.

---

### Post by nickleboyblue on 2011-03-02
First off, most likely there is still a way to get your current card working.  In order to find out if you can, run "lspci" in a terminal and look for your graphics card, and post back with the results that deal with your graphics card.  Second, find your exact monitor specs, including the refresh rates, etc.  If your graphics controller is an older one, you might need to manually define the screen's refresh rate, etc. in your xorg.conf file.  Judging by the fact that the motherboard you named has a geforce 6150SE,  you can probably get it to work.

But... if you want to get a new graphics card just for the heck of it, that all depends on what your board is compatible with.  Make sure you read your motherboard's manual and see what it's graphics ports are capable of supporting.  You'll find the manual in a link on the left bar on this site:

[http://www.asrock.com/mb/overview.asp?Model=ALIVENF6P-VSTA]("http://www.asrock.com/mb/overview.asp?Model=ALIVENF6P-VSTA")

Again, even when looking for a new video card, I suggest you look for one from Nvidia, as they tend to work well with Ubuntu.  You've got a 16x pci express slot, so make sure that a new graphics card will fit there.

---

### Post by Criminel on 2011-03-02
Hi, thanks for the reply.

lspci result is as follows:

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
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

Monitor specs as follows:
    * 20 Display
    * 1680 x 1050 Native Resolution
    * 300 cd/m Brightness
    * 3000 - 1 Dynamic Contrast Ratio; 1000 - 1 Contrast Ratio
    * 5 ms Response Time
refresh rate: 60

Now, how do I go from here?

Thanks

---

### Post by Yellow Pasque on 2011-03-02
Post your /var/log/Xorg.0.log file (either as an attachment or use [ code ][ /code ] tags.

---

### Post by Criminel on 2011-03-02
There you go.

Thanks.

Next?

---

### Post by Yellow Pasque on 2011-03-02
The log indicates you haven't tried to install the nvidia proprietary driver, in which case you should.

---

### Post by Criminel on 2011-03-03
Hi,
I'm not familiar with logs and stuff. But Let me clear it up for you:
What happened is that after many attempts to install and run the nVidia drivers available in the repositories(with no results other than resolutions of 320 and 480) I was urged to work with the machine anyway and so I compromised and stayed with the nouveau driver until I find some other solution. That's why you see no NVidia in the logs.

Thanks anyway for your time and attention.

---

### Post by nickleboyblue on 2011-03-03
If you're still interested in the idea of keeping your video card, and if you haven't tried it yet, you should try to install the drivers from System->administration->additional drivers.  Before you do that though, make sure your system is updated.

---

### Post by Criminel on 2011-03-06
Hi,
I've just installed de NVidia driver (the current recommended one from repositories) and still can't get 1680x1050. I've got a lost of resolutions but not that one.

Does somebody knows what happens and what can I do next?
lspci reads as follows:

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
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)

Thanks

---

### Post by Criminel on 2011-03-06
Here attached the xorg.0.log after installing the nVidia drivers.

---

### Post by Criminel on 2011-03-09
Ok, I've finally found a compromised solution here:
[http://skounis.blogspot.com/2010/08/ubuntu-10041-resolution-up-to-1680x1050.html](http://skounis.blogspot.com/2010/08/ubuntu-10041-resolution-up-to-1680x1050.html)

The trick is to edit the xorg.conf after opening a new nautilus navigator in root mode, and only THEN edit the file (otherwise I accessed a xorg.conf that was empty).

Thanks to the guy in the link and to the rest who took the time to answer.

Next...

---

