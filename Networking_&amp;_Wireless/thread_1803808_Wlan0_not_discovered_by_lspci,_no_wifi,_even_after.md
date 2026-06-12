---
title: "Wlan0 not discovered by lspci, no wifi, even after driver install"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by UsedTampon on 2011-07-13
hello the world of Ubuntu.  

so heres the setup, 
I have in my possession someone else's mac book 5.1 (i hate macs so i was resistant to taking it) 
everything along the lines of installation are perfect; everything that is expect the wireless. To kick me in a face a little bit more, the walk through for this machine simply states 
**Wireless (AirPort)**

 To enable wireless you need to install the restricted Broadcom STA driver. 
Open and choose Broadcom STA in: 

[LIST]
[*]**System** -> **Administration** -> **Additional Drivers**
[/LIST]
if you already chose to install restricted software during Ubuntu's installation, the wireless card is automatically working.

if only life was so easy sometimes.....:(

i have run lspci -vvnn only to find that wlan0 doesnt exist. infact the broadcom chip that is in here doesnt even give the slightest bit of read out from any command i try. 

ive installed all variations of the driver through synaptic. compiled my own driver from broadcom, tried ndisweeper.  This whole mac experience for me just reminds me...macs really really suck. I felt like before i took this guys computer i knew a bit about makin **** work in ubuntu. evidently its not enough. 

so i call upon the greatness of the Ubuntu community, help me fix this **** so i can give this kid a working computer and not look like a jackass...:confused:
```
start@start-MacBook:~$ lspci 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M] (rev b1)
```

iw config says
lo -no wireless extensions
eth0 -no wireless extensions

i have tried waking it up with sudo iwconfig wlan0 wake up outputs does not exist.

```
root@start-MacBook:~# lshw | grep net
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
```

---

### Post by varunendra on 2011-07-15
It all suggests that the wireless interface is not even detected. So any software level effort from within Ubuntu is not going to turn it up. I may be wrong though, but that's what my experience tells me.

Make sure it is enabled in BIOS and is physically turned ON if there's some On/Off switch available in the macbook.

Also, the better way to use lshw command to bring up network related hardware details is:
```
sudo lshw -C network
```

Please post back its output.

---

### Post by wildmanne39 on 2011-07-15
Hi, you can also the this command to see if it can find it.
```
sudo lspci -nn
```

---

### Post by UsedTampon on 2011-07-15
Thanks for replying to this post,
       So i went and cheated a little bit, i acquired a external card and give it back to him. I don't like having peoples computers for long times.

Although i did also set the computer up to work under windows too.  Even under there with all the drivers (finally found a mac to intel drivers cd without bootcamp) the internal wireless adapter would just not even register that it was alive. It really is a wonder 

I did run lspci -nn once when i had it, still didn't show it at all.  


As far as switches, i was never able to get into any sorts of BIOS. I think i would need a mac disk (which all the intel drivers are on too..if only if only) to attempt that statement... 

What i think was going on was either in Os X it was turned off, turning the device itself off. so Ubuntu looks at this device like it has nothing at all because it does not have the headers for it turn back on or even detect it needs these headers in the first place at all because its off and doesn't know which one it needs. (2) ok so this is my favorite one, what if the adapter was broken...the computer just came out of a house fire... its a wonder how it survived.  What if something melted something fried anything.... idk im reaching at that point but looking on the brighter side of things 

On a side note i see this kid very often so i will keep this post alive when i get the computer back (duel layer dvds....) so im going to figure this one out. If you fallow this ive be very thankfull. its just gonna be awhille till i can get some money to take me numbers from next to 0.

---

