---
title: "Wi-Fi Setup"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by laxcoach on 2010-12-29
I have taken a very slow moving Avertec 5100 series laptop (Windows XP), wiped it clean, and installed Ubuntu 10.10.  Everything works fine except for the fact that I am unable to connect to my wi-fi network.  The network adapter for the laptop is a Realtek RTL8139/810X Family Fast Ethernet NIC, if this helps with defining the problem.  As well, I guess that I should probably ask if Ubuntu 10.10 will even work on this laptop.  Do I need another variant? I am excited about my first foray into Linux.  Please advise.  Thanks.[URL="http://members.driverguide.com/driver/device_for_make_model.php?modelId=4783&deviceDescriptionId=23788&manufacturerId=12816&providerId=12816&hwid=PCI%5CVEN_10EC%26DEV_8139%26SUBSYS_24201509%26REV_10"]
[/URL]

---

### Post by bkratz on 2010-12-29
> **laxcoach said:**
> I have taken a very slow moving Avertec 5100 series laptop (Windows XP), wiped it clean, and installed Ubuntu 10.10.  Everything works fine except for the fact that I am unable to connect to my wi-fi network.  The network adapter for the laptop is a Realtek RTL8139/810X Family Fast Ethernet NIC, if this helps with defining the problem.  As well, I guess that I should probably ask if Ubuntu 10.10 will even work on this laptop.  Do I need another variant? I am excited about my first foray into Linux.  Please advise.  Thanks.

That is your ethernet controller not the network controller used for wireless. You might go to the terminal and type in

lspci -nn

(that is LSPCI in lowercase) and copy/paste the results back here or look for an entry labeled Network.

---

### Post by laxcoach on 2010-12-29
Intel Corporation POR/wireless LAN 2100 3B Mini PCI adapter

---

### Post by gordintoronto on 2010-12-29
"I am unable to connect to my wi-fi network."

Could you be more specific, please? Do you get an icon near the top-right of the screen? Can you right-click on it and select "edit connections"?

I think your wireless adapter is 802.11b, which means it might slow down all users of your router. Or perhaps your router is set to not allow a "b" connection.

You asked if you could run Ubuntu on this computer, but you didn't tell us any specs. The most important one is memory; if it has 512 MB, it should be OK. With 256 MB of memory, I've found that Lubuntu is a better choice.

---

### Post by laxcoach on 2010-12-29
I do have a wireless icon in the upper right but it has an exclamation point over the top.  I can, and have, tried to edit the wireless connections unsuccessfully.  This is most likely due to a message that I got during installation that said:  "Your network is probably not using the DHCP protocol.  ALternatively, the DHCP server may be slow or some network hardware is not working properly."  I logged into my router and it does say that it is compatible with DHCP client and the website says that it works with 802.11 b - g.  Finally, if the memory is indeed just 256MB, couldn't I just upgrade to 512 for about $20?  Please let me know what you think.  Thanks.

---

### Post by PatchesTheCaveman on 2010-12-29
> Finally, if the memory is indeed just 256MB, couldn't I just upgrade to 512 for about $20?

That won't fix this problem, but might help you greatly still.

---

### Post by laxcoach on 2010-12-30
Patches, do you have an idea on how I might successfully connect to my wireless?  If it is the memory, then I will try Lubuntu as suggested.  If not, how do I connect to wi-fi using what I have installed?
Thanks for the help

---

### Post by grahammechanical on 2010-12-30
laxcoach

You asked two questions. Please do not confuse the answers. 

1) Will Ubuntu run effectively on my computer? Answer - yes if you have sufficient memory. The more memory you have the better.

2) Why can I not get a wireless connection? This is not caused by a lack of memory. Buying more memory will allow Ubuntu to run better on your machine. It will not give you a working wireless connection.

The icon with the red exclamation mark is telling you that networking is switched off or that you are not connected. Right click the icon. You will see two lines. The first says Enable Networking. The second says Enable Wireless. Is there a tick mark against both of them. If not, then select each of them and click to put the tick mark there.

You can also choose Edit Connections from right clicking the icon. Select the Wireless tab. Select your wireless connection and click Edit. Make sure there is a tick mark against the box labeled Connect automatically. Select the IPV4 settings tab and make sure that Method is set to Automatic (DCHP).

Check these things out and get information that will help other help you.

Regards.

---

### Post by laxcoach on 2010-12-30
Thanks for the assistance.

> The icon with the red exclamation mark is telling you that networking is switched off or that you are not connected. Right click the icon. You will see two lines. The first says Enable Networking. The second says Enable Wireless. Is there a tick mark against both of them. If not, then select each of them and click to put the tick mark there.

At this time, Enable Networking is checked.  However, Enable Wireless was grayed out.  So, I did as you said below...

> You can also choose Edit Connections from right clicking the icon. Select the Wireless tab. Select your wireless connection and click Edit. Make sure there is a tick mark against the box labeled Connect automatically. Select the IPV4 settings tab and make sure that Method is set to Automatic (DCHP).

When I bring up the wireless tab, I do not see available wireless networks.  One thing I did notice is that I am unable to switch on my wireless radio, using the button on my laptop.  I have tried adding a new wireless network before but have not been successful in getting all the right settings.  Do you think that I may be missing some internal setting to have the wireless radio working?

Please let me know what you think.  Thanks for your help.

---

### Post by PatchesTheCaveman on 2010-12-30
I'm sorry.  I meant to come back and get to the other part of your question yesterday and I got distracted.  I'm going to have you run a few things to pull some diagnostic information that might be able to help us out.

Go to Applications > Accessories > Terminal on your top panel.  In the terminal, enter the following and press Enter:
```
lspci -v
```

I know someone had your run lspci -nn but that omits information about what driver you have installed and whether it's working.  Copy and paste what appears into a reply to this thread.

Then type this and press Enter:
```
sudo iwconfig
```
Copy and paste what appears from that also.

Finally, type this last command and hit Enter:
```
dmesg | grep -i ipw2100
```
and copy and paste what that shows, if anything.

With all that we'll hopefully be able to figure out exactly what's going on!

---

### Post by laxcoach on 2010-12-30
Patches,  here are the results of terminal inquires:

 **Results of lspci -v:**
   
  00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2930
            Flags: bus master, fast devsel, latency 0
            Memory at <unassigned> (32-bit, prefetchable)
            Capabilities: <access denied>
            Kernel driver in use: agpgart-intel
            Kernel modules: intel-agp
    00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2930
            Flags: bus master, fast devsel, latency 0
    00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2930
            Flags: bus master, fast devsel, latency 0
    00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2930
            Flags: bus master, fast devsel, latency 0, IRQ 11
            Memory at e8000000 (32-bit, prefetchable) [size=128M]
            Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
            I/O ports at 1800 [size=8]
            Expansion ROM at <unassigned> [disabled]
            Capabilities: <access denied>
            Kernel driver in use: i915
            Kernel modules: i915
    00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2930
            Flags: fast devsel
            Memory at f0000000 (32-bit, prefetchable) [size=128M]
            Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
            Capabilities: <access denied>
    00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
              Subsystem: FIRST INTERNATIONAL Computer Inc Averatec 5110H laptop
            Flags: bus master, medium devsel, latency 0, IRQ 11
            I/O ports at 1820 [size=32]
            Kernel driver in use: uhci_hcd
    00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
              Subsystem: FIRST INTERNATIONAL Computer Inc Averatec 5110H
            Flags: bus master, medium devsel, latency 0, IRQ 11
            I/O ports at 1840 [size=32]
            Kernel driver in use: uhci_hcd
    00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
              Subsystem: FIRST INTERNATIONAL Computer Inc Averatec 5110H
            Flags: bus master, medium devsel, latency 0, IRQ 10
            I/O ports at 1860 [size=32]
            Kernel driver in use: uhci_hcd
    00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
              Subsystem: FIRST INTERNATIONAL Computer Inc Averatec 5110H
            Flags: bus master, medium devsel, latency 0, IRQ 11
            Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
            Capabilities: <access denied>
            Kernel driver in use: ehci_hcd
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
              Flags: bus master, fast devsel, latency 0
            Bus: primary=00, secondary=02, subordinate=0a, sec-latency=64
            I/O behind bridge: 00002000-00002fff
            Memory behind bridge: e0200000-e02fffff
            Prefetchable memory behind bridge: 20000000-27ffffff
            Kernel modules: shpchp
    00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
              Flags: bus master, medium devsel, latency 0
            Kernel modules: iTCO_wdt, intel-rng
    00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2990
            Flags: bus master, medium devsel, latency 0, IRQ 10
            I/O ports at 01f0 [size=8]
            I/O ports at 03f4 [size=1]
            I/O ports at 0170 [size=8]
            I/O ports at 0374 [size=1]
            I/O ports at 1810 [size=16]
            Memory at 28000000 (32-bit, non-prefetchable) [size=1K]
            Kernel driver in use: ata_piix
    00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2990
            Flags: medium devsel, IRQ 10
            I/O ports at 1100 [size=32]
            Kernel modules: i2c-i801
    00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2942
            Flags: bus master, medium devsel, latency 0, IRQ 10
            I/O ports at 1c00 [size=256]
            I/O ports at 18c0 [size=64]
            Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
            Memory at e0100800 (32-bit, non-prefetchable) [size=256]
            Capabilities: <access denied>
            Kernel driver in use: Intel ICH
            Kernel modules: snd-intel8x0
    02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
            Subsystem: Intel Corporation MIM2000/Centrino
            Flags: bus master, medium devsel, latency 64, IRQ 10
            Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
            Capabilities: <access denied>
            Kernel driver in use: ipw2100
            Kernel modules: ipw2100
    02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2950
            Flags: bus master, medium devsel, latency 168, IRQ 11
            Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
            Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
            Memory window 0: 20000000-23fff000 (prefetchable)
            Memory window 1: 2c000000-2ffff000
            I/O window 0: 00002400-000024ff
            I/O window 1: 00002800-000028ff
            16-bit legacy interface ports at 0001
            Kernel driver in use: yenta_cardbus
            Kernel modules: yenta_socket
    02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2950
            Flags: bus master, medium devsel, latency 168, IRQ 10
            Memory at e0203000 (32-bit, non-prefetchable) [size=4K]
            Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
            Memory window 0: 24000000-27fff000 (prefetchable)
            Memory window 1: 30000000-33fff000
            I/O window 0: 00002c00-00002cff
            I/O window 1: 00001400-000014ff
            16-bit legacy interface ports at 0001
            Kernel driver in use: yenta_cardbus
            Kernel modules: yenta_socket
    02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02) (prog-if 10 [OHCI])
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2980
            Flags: bus master, medium devsel, latency 64, IRQ 10
            Memory at e0201000 (32-bit, non-prefetchable) [size=2K]
            Capabilities: <access denied>
            Kernel driver in use: firewire_ohci
            Kernel modules: firewire-ohci, ohci1394
    02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
              Subsystem: FIRST INTERNATIONAL Computer Inc Device 2420
            Flags: bus master, medium devsel, latency 64, IRQ 10
            I/O ports at 2000 [size=256]
            Memory at e0201800 (32-bit, non-prefetchable) [size=256]
            Capabilities: <access denied>
            Kernel driver in use: 8139too
            Kernel modules: 8139too, 8139cp
    **results of sudo iwconfig:**
   
  lo        no wireless extensions.
    eth0      no wireless extensions.
    eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
              Mode:Managed  Channel=0  Access Point: Not-Associated   
            Bit Rate:0 kb/s   Tx-Power:off   
            Retry short limit:7   RTS thr:off   Fragment thr:off
            Encryption key:off
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
     
  **results of dmesg | grep -i ipw2100:**
  
  [   19.203902] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
  [   19.203908] ipw2100: Copyright(c) 2003-2006 Intel Corporation
  [   19.254884] ipw2100 0000:02:01.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
  [   19.255573] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
    
Please let me know what you think.  Thanks.

---

### Post by PatchesTheCaveman on 2010-12-30
Everything appears to be in working order.  Try this one:
```
sudo iwconfig eth1 scan
```

That should list all the wireless networks your card can pick up.  Does it pick up any?  If so, can you access them from the wireless network icon?

---

### Post by laxcoach on 2010-12-30
> **PatchesTheCaveman said:**
> Everything appears to be in working order.  Try this one:
```
sudo iwconfig eth1 scan
```

When I type this in, I get: iwconfig: unknown command "scan"

---

### Post by PatchesTheCaveman on 2010-12-30
My bad.  The correct command is:
```
sudo iwlist eth1 scan
```

I have no idea why I can't seem give you the right commands today. 8-[

---

### Post by laxcoach on 2010-12-30
The line came back

eth1 No scan results

I think that my wireless card is not working properly.  How do I check the card out?

---

### Post by PatchesTheCaveman on 2010-12-30
Your card looks like its working fine.  I think the issue might be with your router.  Can you access your router configuration from another computer or via Ethernet?  Look in your wireless settings for something that configures 802.11b or 802.11g and make sure it's in Mixed mode.

I know for a fact you don't have the same router configuration as me because I installed a special Linux firmware on mine, but you should have a screen somewhat similar to the one I attached as an example.

If you know what kind of router you have I can look into exactly how to change it.

---

### Post by laxcoach on 2010-12-30
In the wireless network mode it says:  "up to 54mbps".  See attached screenshot for reference.  The shot will also show you the type of router.

---

### Post by PatchesTheCaveman on 2010-12-30
What are all the options in the drop-down that says "up to 54mbps"?

---

### Post by laxcoach on 2010-12-30
Here you go...

Up to 54 mbps
Up to 72 mbps
Up to 150 mbps

---

### Post by laxcoach on 2010-12-31
I have been doing a little reading.  Do you think that I need ndiswrapper or are my internal settings OK and you think it is the router settings?

---

### Post by PatchesTheCaveman on 2010-12-31
I've done some Googling and might have found a solution to your problem.

Run this on a terminal and copy/paste:
```
dmesg | grep eth1
```

Your card is about ten years old so one would hope they'd have sorted out the native Linux drivers by now...

---

### Post by laxcoach on 2010-12-31
Patches, first off, thank you for investing as much time as you have with my problem.  I really appreciate the help.

Second, the return on the terminal post was: eth1: Radio is disabled by RF switch

What does this mean to you?  My laptop has radio switch button above the keyboard but nothing happens when I hit it.  Is there another way to toggle the radio?

---

### Post by PatchesTheCaveman on 2010-12-31
That's what I thought might be going on.  Download the rfkill package:
```
sudo apt-get install rfkill
```

Then, check to see if it reports your wireless radio as off:
```
rfkill list
```

It probably does.  Run this command to turn it on:
```
rfkill unblock 0
```
Change the 0 if the number shown before your wireless device is different in the list command.

---

### Post by laxcoach on 2010-12-31
Here are the results of the last three commands:

phil@ubuntu:~$ sudo apt-get install rfkill
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rfkill
phil@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
phil@ubuntu:~$ rfkill unblock 0
phil@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

What does this mean?

---

### Post by PatchesTheCaveman on 2010-12-31
That's supposed to mean you need to flip the wireless switch/hit the button.  But you've already tried that several times to no effect.  Try this:
```
sudo bash -c "echo 0 > /sys/bus/pci/drivers/ipw2100/*/rf_kill"
```

If that doesn't work, answer with your laptop's manufacturer and model # and I'll see if the there's a way to force the kernel to switch the RF kill state for your hardware.

(Apparently this is really common on Acer hardware and there's an easy way to fix it, too.)

---

### Post by laxcoach on 2010-12-31
Here's what I got:

phil@ubuntu:~$ sudo bash -c "echo 0 > /sys/bus/pci/drivers/ipw2100/*/rf_kill"
[sudo] password for phil: 
phil@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
phil@ubuntu:~$ rfkill unblock 0
phil@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

The laptop that I am on is an Averatec Model 5110H.

I tried to save you some time by googling the statement you made earlier about the kernal.  I found this on a website about my computer:

+Currently this project provides modules for controlling the software RF kill        59  +switch on the Averatec 5100P and Packard Bell EasyNote E5.  The code may work        60  +on other laptops, but these are the only models on which it has been tested.        61  +        62  +Simply by loading and unloading the av5100/pbe5 module the radio will be toggled        63  +on and off.  In addition, you can turn the driver on and off by writing either        64  +a 1 or 0 to /proc/av5100/radio or /proc/pbe5/radio.  If you automatically load        65  +the av5100/pbe5 module when your system boots, you may wish to use the radio        66  +module parameter to control the state of the radio upon loading:        67  +        68  +       modprobe av5100 radio=0        69  +       modprobe pbe5 radio=0        70  +        71  +results in the module loading with the radio turned off.  You can then turn the        72  +radio on by:        73  +        74  +       echo 1 > /proc/av5100/radio        75  +       echo 1 > /proc/pbe5/radio  
Does this help?  I would try some of the code but thought that it was better left to you to decipher.

This is the website that I found the statement above:  [http://sources.gentoo.org/cgi-bin/viewvc.cgi/linux-patches/genpatches-2.6/historical/2.6.6/2120_ipw2100-0.40-2.6.5.patch?revision=2&view=markup](http://sources.gentoo.org/cgi-bin/viewvc.cgi/linux-patches/genpatches-2.6/historical/2.6.6/2120_ipw2100-0.40-2.6.5.patch?revision=2&view=markup)

---

### Post by t4thfavor on 2010-12-31
Means theres a hardware switch somewhere on the laptop killing the wifi, I hate to say it, but one of my laptops has a weird problem too, if you switch the wifi off with the hardware switch on the side under windows, it won't come back under linux until you boot windows, and switch it on.

It does however work if you switch it off under linux... go figure.

Did you try the wifi button/switch on the laptop itself, and see if it's off, or somehow reversed from when your on Windows.

---

### Post by laxcoach on 2010-12-31
Unfortunately, there is no going back as I wiped the HD clean when I installed ubuntu.  This old machine was running so slowly on Windows that I went scorched earth on it.  Doesn't there have to be a way to force the switch from the linux side?

---

### Post by PatchesTheCaveman on 2010-12-31
That's a slightly different model so that may or may not be useful.  I found a simpler solution I want to try first.

Run this:  ```
sudo modprobe av5100
``` and then run ```
sudo rfkill list
``` again and see if the hard block changed.

---

### Post by laxcoach on 2010-12-31
Yeah, it is unblocked!

phil@ubuntu:~$ sudo modprobe av5100
[sudo] password for phil: 
phil@ubuntu:~$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
phil@ubuntu:~$ 

I am going to unplug the hardwire and try to config the wireless.  If successful, I will post back here in a few minutes.  Thanks.:p

---

### Post by PatchesTheCaveman on 2010-12-31
Awesome!  You're welcome.

To make that fix permanent, run this command:
```
sudo bash -c "echo av5100 >> /etc/modules"
```

---

### Post by laxcoach on 2010-12-31
Thanks.  I ran the above to make this permanent.  Do I need to restart my computer?  It seems that the wireless will work for a short time period and then I will get a message asking me to re-input my security key for the wireless network.  When this happens, I lose the connection the internet.  So, I have had to plug back in to the hardwire.  What do you think?

---

### Post by PatchesTheCaveman on 2010-12-31
We can't win, can we?

Run:
```
sudo iwconfig
```
while you're connected to the wireless and copy/paste the output here.

---

### Post by laxcoach on 2010-12-31
IEEE 802.11b  ESSID:"NETGEAR"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:3F:0E:92:C0:F4   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:B268-2D85-E002-48F6-88F6-E1FA-EA   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

---

### Post by PatchesTheCaveman on 2010-12-31
Try running this:
```
sudo iwconfig wlan0 rate 54M
```

---

### Post by laxcoach on 2010-12-31
phil@ubuntu:~$ sudo iwconfig
[sudo] password for phil: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

phil@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETGEAR"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:3F:0E:92:C0:F4   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:B268-2D85-E002-48F6-88F6-E1FA-EA   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

phil@ubuntu:~$ sudo iwconfig wlan0 rate 54M
[sudo] password for phil: 
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; No such device.

Should it be eth1 vs. wlan0?  Or do I have something not set correctly?

---

### Post by PatchesTheCaveman on 2010-12-31
Yes, it should.  Sorry, you cut off that part in your previous post and I assumed it's wlan0 since most built in kernel drivers are.

---

### Post by laxcoach on 2010-12-31
I tried the last set of commands but it still doesn't hold the wireless signal.  I can get firefox open but then quickly lose the signal:confused:

---

### Post by laxcoach on 2011-01-01
Now that I have the wireless radio on, how do I get the wireless to remain connected to my network?  What could be the issue here?

---

### Post by laxcoach on 2011-01-04
I seem to have come close to a resolution but am not all the way there.  Can someone please help me to figure out how to keep my wireless interface working on a consistent basis?  Thanks.

---

