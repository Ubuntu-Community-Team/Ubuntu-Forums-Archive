---
title: "wireless networks disconnected??"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by melinda on 2010-12-29
HELP

I tuned on my netbook and my wireless signal had a red exclamation.  

Wireless is enabled.
Wireless Networks shows disconnected

I dont get it.  Can't seem to get it to connect?  How?  

If I open the connection information I can see the wifi networks around me.  And edit/add/delete.  But when I go back to the signal and click.  it just shows wireless network  disconnected.  and no option to connect.  

What to do?  I have restarted the computer, router, cable modem, etc etc.  done the updates.  HELP?

---

### Post by PatchesTheCaveman on 2010-12-29
Hi melinda!  I'm sorry you're having trouble getting hooked up to your wireless network.

To figure out what's going on, go to Applications > Accessories > Terminal on your top panel.  In the purple box that appears, type in the following and press Enter:
```
lspci -v
```

It will spit out a bunch of info about your hardware that we can use to see what's going on.  Just copy and paste it into a reply to this thread and we'll see what we can do.

---

### Post by melinda on 2010-12-29
Hey PatchesTheCaveman.

Here is what I got:  

heather@heather-U-100:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfe80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e0f0 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dff00000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, fast devsel, latency 0
	Memory at dfe00000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at ffe00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 00000000ffd00000-00000000ffdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: dfc00000-dfcfffff
	Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dff40000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at e0a0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Flags: medium devsel, IRQ 3
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Physical Slot: 0
	Flags: bus master, fast devsel, latency 0, IRQ 40
	I/O ports at d000 [size=256]
	Memory at ffd10000 (64-bit, prefetchable) [size=4K]
	Memory at ffd00000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at dfd00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
	Physical Slot: 0-1
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at dfc00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

---

### Post by PatchesTheCaveman on 2010-12-29
Okay, you're wireless card is configured properly.

You should be able to **left**-click on the wireless icon and see a list of wireless networks around you.  You can just click on them to connect to them.  They may ask you for a WPA password or WEP key if the networks require them.

If you don't see any networks, and you know the name and password of the network you want, you can try clicking on *Connect to Hidden Wireless Network...* and typing in the network name (SSID), choosing the type of security, and entering the password.  Then hit Connect to connect to them.

---

### Post by melinda on 2010-12-29
ok so that is my problem.

I click and see NO networks around me
  and I KNOW there are several.....or 10.

I have mine, my neighbors across the street and kiddy corner and right next to me.
I do have their SSID name and type of encryption and code/key/passphrase. 

BUT they do not appear.   when I click it says "Wireless Networks"  in sort of a greyish white color, and then underneath in black it says "disconnected."

---

### Post by melinda on 2010-12-29
ps.  When I click on the Connect to Hidden Network, then scroll down to the one broadcasted from my basement....it just closes the window (connect to hidden network)  then a little window pops up states Wireless network  Disconnected - you are now offline.  

Don't get it?

---

### Post by PatchesTheCaveman on 2010-12-30
You might have gotten bit by a faulty update from Canonical.  Many of us have had a problem.  There's an easy way to check.

Go back to Applications > Accessories > Terminal and type in the following and press Enter:
```
uname -r
```

It'll print out one line.  If it says *2.6.35-24-generic* you have the faulty update.  To work around this, you'll need to restart your computer.

If you dual boot with Windows, you get a menu when you start your computer.  If you don't, you'll need to hold down the SHIFT key before Ubuntu starts to get that menu.  

In that menu, there will be several listings for Ubuntu.  One will say 2.6.35-24-generic and should be highlighted.  Another will say 2.6.35-23-generic.  Go down to that one and press Enter.  Your wireless card should now work properly.

If it says 2.6.35-23-generic or anything else when you run uname -r, let us know so we can try and figure out what else might be going on.

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ uname -r
2.6.35-24-generic


I am rebooting holding the shift key...brb

---

### Post by melinda on 2010-12-30
ok so I did that.  and I still have the same problem.  yikes!  

any other clues?

---

### Post by PatchesTheCaveman on 2010-12-30
Run *uname -r* now and make sure it changed.

---

### Post by melinda on 2010-12-30
Yes it did change.  I even tried the one below it too (2.6.35-22-generic).  same deal.  
I went back to this one:

heather@heather-U-100:~$ uname -r
2.6.35-23-generic

I really am puzzled.  I mean even restarting my router...I should still be able to connect to my neighbors.

---

### Post by PatchesTheCaveman on 2010-12-30
That's the one I've been using just fine.  Let's see if maybe NetworkManager (the program that drives the wireless icon) is borked.

Go back to the terminal and run this command:
```
sudo iwconfig
```

It'll spit something like this out:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:246  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

teredo    no wireless extensions.

```

All but one say no wireless extensions.  Next to that one it should say something like *eth1* (like mine) or, more commonly, *wlan0*.  Remember what that is.

Then run:
```
sudo iwlist wlan0 scanning
```
Replacing wlan0 with whatever interface name you figured out in the previous step.

That should return all the wireless access points your card can find.  Does it?

---

### Post by melinda on 2010-12-30
ok sorry.  

here is what I got:

heather@heather-U-100:~$ sudo iwconfig
[sudo] password for heather: 
Sorry, try again.
[sudo] password for heather: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
heather@heather-U-100:~$

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ sudo iwconfig
[sudo] password for heather: 
Sorry, try again.
[sudo] password for heather: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
heather@heather-U-100:~$

---

### Post by PatchesTheCaveman on 2010-12-30
Now run
```
sudo iwlist wlan0 scanning
```

---

### Post by melinda on 2010-12-30
ok I dont get where those smiley faces came from.....prob the  colon and then the o right after. sorry.  

so I am not sure what you want me to do after that sudo iwconfig.

---

### Post by PatchesTheCaveman on 2010-12-30
That's okay.  I figured it out.  :-)

Run ```
sudo iwlist wlan0 scanning
``` to scan for any wireless APs in your area.  I just needed the first step cause not all wireless cards are called wlan0.

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ sudo iwlist wlan0 scanning
wlan0     Interface doesn't support scanning : Network is down


so what does this biz mean?

---

### Post by PatchesTheCaveman on 2010-12-30
Try running
```
sudo ifup wlan0
```
then
```
sudo iwlist wlan0 scan
``` again.

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.


heather@heather-U-100:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down


?? 

(ps thanks for helping me.  your the best!)

---

### Post by tad1073 on 2010-12-30
seems to be a bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/581441](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/581441)

---

### Post by PatchesTheCaveman on 2010-12-30
No problem!  I'm sorry this is being such a pain...

Run this:
```
dmesg | grep -i iwl
```
and copy/paste

---

### Post by PatchesTheCaveman on 2010-12-30
And can you by chance plug into a wired Ethernet connection?  If that doesn't turn up anything I'm going to have you download an updated driver for your wireless card.

---

### Post by PatchesTheCaveman on 2010-12-30
If tad1073 is right my grep line will indicate that.  And it's an easy fix.  :-)

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ dmesg | grep -i iwl
[   17.000680] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   17.000690] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   17.000818] iwl3945 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.000841] iwl3945 0000:02:00.0: setting latency timer to 64
[   17.183399] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.183414] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   17.183598] iwl3945 0000:02:00.0: irq 41 for MSI/MSI-X
[   17.406688] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.538449] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   17.538826] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   17.546240] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   53.187029] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[  400.452081] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch


yes I can connect wired.

---

### Post by tad1073 on 2010-12-30
> **melinda said:**
> heather@heather-U-100:~$ dmesg | grep -i iwl
[   17.538826] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   17.546240] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   53.187029] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[  400.452081] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch


yes I can connect wired.


looks like that might be the problem. If the radio transmitter in in the card is disabled then no signals can be sent or received.

---

### Post by PatchesTheCaveman on 2010-12-30
That's saying your wifi switch is off.  Try flipping it, or pressing the wifi button your laptop, or pressing the Fn key and the wireless button on the top of your keyboard.

It's also possible that it is lying but it's better to try the obvious first.

After you do that run
```
sudo iwlist wlan0 scan
```
again and see what it says.

---

### Post by melinda on 2010-12-30
so its odd.  I have had wifi.  no prob. signal strength hasnt been the greatest (in comparison to my macbook)  I was using my little net book for a while and didnt reboot.  then I had to put it down for a couple days....it was sleeping...right into battery drain.  so when I powered on....it rebooted fully.  And the updates that I did took severakl days earlier were installed.   

that is the only thing I can think of that I did.  I did have to restart my router and cable modem.  but that shouldnt have made it so the wireless network was disconnected and couldnt connect to ALL the wifi's around. It doesnt even recognize some. as it shows disco'd.

that is the only thing that has happened.  no dropping, or kicking or throwing the little bugger around either.  

what a pain in the ****.

---

### Post by melinda on 2010-12-30
ok.  so i may be really dumb here.  but I dont have a wifi button that I can see. and I am not sure which button is the wifi button??   im on a MSI wind netbook.  does that matter?

---

### Post by PatchesTheCaveman on 2010-12-30
Run this:
```
sudo bash -c "echo 0 > /sys/bus/pci/driver/ipw3945/*/rf_kill"
```

That will completely override everything and turn your wifi card on no matter what.

[Sorry I completely screwed that up the first time.]

---

### Post by melinda on 2010-12-30
ok i think I figured it out.  i think its f11.  has a sort of satellite thingy looking icon.  

so i did that.  and now when I click on the wireless signal thingy.... it says wired disconnected and the wireless network DEVICE NOT READY  (before it said it was disconnected)

here is what the code in terminal says:
heather@heather-U-100:~$ sudo iwlist wlan0 scan
[sudo] password for heather: 
wlan0     Interface doesn't support scanning : Network is down

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ sudo bash -c "echo 0 > /sys/bus/pci/driver/ipw3945/*/rf_kill"
bash: /sys/bus/pci/driver/ipw3945/*/rf_kill: No such file or directory

---

### Post by PatchesTheCaveman on 2010-12-30
Try this instead (apparently they changed it slightly sometime between 2009 and 2010):
```
sudo bash -c "echo 0 > /sys/bus/pci/drivers/iwl3945/*/rfkill/rfkill0/state"
```

Check the icon again.  If it still says device not ready, hit your wifi button again and look again.

---

### Post by melinda on 2010-12-30
heather@heather-U-100:~$ sudo bash -c "echo 0 > /sys/bus/pci/drivers/iwl3945/*/rfkill/rfkill0/state"
bash: /sys/bus/pci/drivers/iwl3945/*/rfkill/rfkill0/state: No such file or directory


I think it is on.  there is a light that shows the little sattelite icon illuminated.  when I hit fn and f11 that also has that icon the light came on.  and then when I clicked the signal strength thingy on the top menu bar (forgot the name of it -- task bar) the drop down menu shows wired network disconnected and wireless network device not ready.  before it showed both disconnected.

---

### Post by melinda on 2010-12-30
Omg omg omg
its working!

---

### Post by melinda on 2010-12-30
OK so here i am dumb i guess.  the fn and the icon on f11 toggles between bluetooth on and wifi on or blue tooth on only and wifi off, or wifi on and blue tooth off.

I guess I had the bluetooth and wifi on. when I first hit fn and f11. so I turned just the wifi on.  and shazam!  it said configuirng network connection.. CONNECTION TO SUPERGROVER  (my wireless ssid name) ESTABLISHED.  

oh bloody hell.  sorry that took so long.

somehow I musta turned off the wifi radio huh?  


oh you are so cool to hang with me and help me solve this!   PATCH THE CAVEMAN RULES!

---

### Post by PatchesTheCaveman on 2010-12-30
:guitar:

LOL thank you.  Have a good night.

---

### Post by melinda on 2010-12-30
so one last question.  should I boot to the previous update always?  and if I need to... how do I delete that last faulty update?  so I dont have to boot and hold shift to get the menu.  I dont have windows dual boot on here.

---

### Post by PatchesTheCaveman on 2010-12-30
Well next time you reboot it will go back to the broken one but I really don't think that was your problem.  Nobody else with your wireless card reported a problem.

If you wouldn't mind, reboot and don't do anything and see if it still works.  If it does, great.

If not, you can reboot with the fix again and I'll tell you how to get rid of the bad update and I'll report it to the kernel guys so they can fix it in the next one.

Thanks!

---

### Post by melinda on 2010-12-30
cool!   happy holidays!  thanks a gazillion!

---

### Post by Willm004 on 2011-01-02
Hi,

I'm having almost the same problem as her with two exceptions:

willolson@ubuntu:~$ uname -r
2.6.32-24-generic

and

willolson@ubuntu:~$ dmesg | grep -i iwl
[    6.273863] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    6.273867] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    6.273978] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.274015] iwlagn 0000:02:00.0: setting latency timer to 64
[    6.274379] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[    6.296774] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    6.296864] iwlagn 0000:02:00.0: irq 35 for MSI/MSI-X
[    6.480105] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.706905] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   11.740598] iwlagn 0000:02:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   11.740640] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   11.742221] iwlagn 0000:02:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   11.742263] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   11.743834] iwlagn 0000:02:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   11.743878] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   11.745062] iwlagn 0000:02:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   11.745101] iwlagn 0000:02:00.0: Could not read microcode: -2
[   12.000849] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   12.002108] iwlagn 0000:02:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   12.002161] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   12.003322] iwlagn 0000:02:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   12.003371] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   12.004442] iwlagn 0000:02:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   12.004494] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   12.005549] iwlagn 0000:02:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   12.005596] iwlagn 0000:02:00.0: Could not read microcode: -2
[   64.687249] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   64.689009] iwlagn 0000:02:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   64.689014] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   64.690894] iwlagn 0000:02:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   64.690899] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   64.692057] iwlagn 0000:02:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   64.692062] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   64.693436] iwlagn 0000:02:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   64.693441] iwlagn 0000:02:00.0: Could not read microcode: -2
[  419.121215] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-4.ucode
[  419.123805] iwlagn 0000:02:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[  419.123816] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-3.ucode
[  419.127688] iwlagn 0000:02:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[  419.127699] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-2.ucode
[  419.139597] iwlagn 0000:02:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[  419.139604] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6050-1.ucode
[  419.159044] iwlagn 0000:02:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[  419.159049] iwlagn 0000:02:00.0: Could not read microcode: -2

Think you can help me out??

---

### Post by PatchesTheCaveman on 2011-01-02
There is a problem with the version of the Linux kernel you are running that breaks many devices.  Try following the instructions in post #7 to reboot into a known working kernel and see if that helps.

---

### Post by Willm004 on 2011-01-02
my wireless still isn't working

the two options it gives me at the boot menu are:
2.6.32-27 generic
2.6.32-24 generic
and the recovery mode for both of those

neither of the generic options work

is there anything else i can do?

---

### Post by Willm004 on 2011-01-02
and i agree with melinda.. your awesome!! thanks for helping me out with this!!

---

### Post by PatchesTheCaveman on 2011-01-02
Ah, you're using Ubuntu 10.04 Lucid Lynx (LTS).  It doesn't have this bug.

Try updating your wireless drivers.  Run
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by Willm004 on 2011-01-02
this is what it responds with:

willolson@ubuntu:~$ sudo apt-get install linux-backports-modules-wireless-maverick-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-wireless-maverick-generic

---

### Post by PatchesTheCaveman on 2011-01-02
Sorry, I meant:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by Willm004 on 2011-01-02
it works!! thanks a lot!!

so for future reference, what does that code do?? I'm new with linux operating systems and I want to learn about this stuff, that being said is there any place you could suggest to learn about learning this??

thanks so much your the best man!

---

### Post by PatchesTheCaveman on 2011-01-02
That full command installs the backported wireless drivers from newer versions of the Linux kernel.  The *apt-get* command just installs software packages onto your computer.  For instance, if you wanted to install The GIMP, a free alternative to Photoshop, you would run this command:
```
sudo apt-get install gimp
```

As for learning more, the Ubuntu Community Documentation site has more info than anybody could learn in a lifetime:  [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by ianpavlovic on 2011-01-05
Hi I have alienware m11x and eavrything is working fine exept the wireless please some one help me it wont find any wireless networks

-M11x:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0000000-f10fffff
    Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f1604800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f1600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f1100000-f11fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f1200000-f12fffff
    Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=1a, subordinate=1a, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f1300000-f13fffff
    Prefetchable memory behind bridge: 00000000a0400000-00000000a05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f1604c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=26, subordinate=26, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Subsystem: Dell Device 0443
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0443
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 18b0 [size=8]
    I/O ports at 18a4 [size=4]
    I/O ports at 18a8 [size=8]
    I/O ports at 18a0 [size=4]
    I/O ports at 1880 [size=32]
    Memory at f1604000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 0443
    Flags: medium devsel, IRQ 10
    Memory at a0600000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 335M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    [virtual] Expansion ROM at f1080000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1100000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

08:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
    Subsystem: Dell Device 000e
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

1a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10 [OHCI])
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1300800 (32-bit, non-prefetchable) [size=2K]
    Memory at f1301000 (32-bit, non-prefetchable) [size=128]
    Memory at f1300400 (32-bit, non-prefetchable) [size=128]
    Memory at f1300000 (32-bit, non-prefetchable) [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

1a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1301400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

1a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: Dell Device 0443
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1301c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

---

### Post by PatchesTheCaveman on 2011-01-05
You need to install your wireless driver.  Plug into a wired Ethernet Internet connection, and go to System > Administration > Additional Drivers.  Select the *Broadcom STA wireless driver* and click *Install*.

If you continue to have trouble, see this thread:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

