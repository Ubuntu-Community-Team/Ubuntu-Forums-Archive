---
title: "Internet connection unstable"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by datatron on 2009-07-20
[FONT=Tahoma]I am completely new to Linux, so I have no idea what I am doing.

I recently installed Xubuntu 8.04 (Hardy Heron) on my Dell Inspiron 2650 laptop. Everything is running smoothly except that my wireless PC card is barely working. It is a Hawking WE120P 11M wireless card. The red "Activity" light on the card sometimes lights up (although it blinks a lot), while the green "Link" light rarely lights up, and when it does, it only does so for about ten to fifteen seconds. Please help.

Thank you,
datatron[/FONT]

---

### Post by martinbaselier on 2009-07-20
It would be nice to get a bit more info about the card. 

Open a terminal (it's in accessories )

(you can copy the command and paste it in the terminal either by ctrl+shift+v or by choosing paste, in the right mouse button menu - if you use a 3 button mouse, you can use the middle mouse button to paste a selected text)

When you open a terminal and type **lspci**, you will see your card in between. 
next type 
sudo lspci -v -s CARDNUMBER. (replace this with the number you see in the list)

example: 
```

lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
**06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)**
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
...
sudo lspci -v -s 06:03.0

```
Could you please post the output for your card, to show a bit more details. (you can select the text in the terminal with your mouse and then copy with ctrl+shift+c or by selecting copy from the right mouse button menu)

Next thing interesting would be to know a bit more about the wireless connection. For this type:
**iwconfig**
please post the output of that too.

---

### Post by datatron on 2009-07-20
Output for *sudo lspci -v -s CARDNUMBER*:

> 03:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 11)
            Subsystem: ADMtek SMC2635W 802.11b (11 mbps) wireless lan pcmcia (cardbus) card
            Flags: bus master, medium devsel, latency 64, IRQ 10
            I/O ports at 3400 [size=256]
            Memory at 28000000 (32-bit, non-prefetchable) [size=1k]
            [virtual] Expansion ROM at 24000000 [disabled] [size=128k]
            Capabilities: [c0] Power Management version 2Output for *iwconfig*:

> lo         no wireless connection
eth0     no wireless connection
wmaster 0   no wireless connection
wlan0   IEEE 802.11b ESSID: " "
           Mode: Managed Frequency: 2.412 GHz Access Point: Not-Associated
           Tx-Power=0 dBm
           Retry min limit: 7 RTS thr: off Fragment thr=2346 B
           Link Quality: 0 Signal: 0 RX invalid crypt: 0 Rx invalid frag: 0
           Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0
By the way, I had no internet connection on my Xubuntu laptop during the time I copied down the outputs (I am currently using my desktop computer).

---

### Post by martinbaselier on 2009-07-21
You're missing the two lines at the bottom of the first output. It should show the kernel module in use. 

I did a bit of searching and the correct kernel module should be the rt2400pci.

First check if it's loaded.
**lsmod | grep 2400**

If not, then try loading it:

**sudo modprobe rt2400pci**

Now try again:

**sudo lspci -v -s 03:00.0**

Does it show a kernel module loaded now?

if this makes your wireless work, add the name to /etc/modules and it will load automatically

---

### Post by datatron on 2009-07-21
The first time I tried *lsmod | grep 2400*, nothing happened, so I went on to type in *sudo modprobe rt2400pci* and *sudo lspci -v -s 03:00.0*, and I got the same output as before. I decided to type in *lsmod | grep 2400* a second time, and it came up with this:

> rt2400pci 16768 0
rt2x00pci 11264 1 rt2400pci
rt2x00lib 22528 2 rt2400pci, rt2x00pci
mac80211 165652 4 rt2400pci, rt2x00pci, rt2x00lib, adm8211
eeprom_93cx6 3200 2 rt2400pci, adm8211

---

### Post by martinbaselier on 2009-07-21
It just means the kernel modules are loaded, but they are not used by the card. I might not have found the right information regarding it. Well it won't hurt, they're gone when you reboot or enter **sudo modprobe -r rt2400pci**

The only thing in my hardware list, which does not show a kernel module is my cardreader, for which there is no driver. Strange. Maybe it's done in some other way. 

Either **lsmod | grep eee** or **lsmod | grep mac** should show the driver in use, normally. Did you maybe install ndiswrapper or madwifi?

---

### Post by datatron on 2009-07-21
***lsmod | grep eee*** did nothing, but ***lsmod | grep mac** *got this:

> mac80211 165652 1 adm8211
cfg80211 15112 1 mac80211

I did install ndiswrapper earlier, although it didn't help, so I'm not sure whether I installed it wrong or if it wasn't compatible. I do not have madwifi installed.

---

### Post by super gaga on 2010-05-27
have you found a solution? (if so what?)
i have had similar  problem with
lubuntu 10.04 (also mint 9 main)
with similar outputs (i would tell you the difference if that that helps)

---

