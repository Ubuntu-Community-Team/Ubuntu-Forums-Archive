---
title: "Intermittent wireless issue - cannot find my wireless network."
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by Tricycle on 2009-03-27
Hi all,

I'm hoping this is going to prove to be something really obvious I am missing, but here goes.

I am using Ubuntu 8.10 AMD64 with the proprietary Broadcom STA drivers for my BCM4312 802.11b/g (rev 01), and my router is the BT2700HGV transmitting on channel 8 with wpa encryption. I have used this combination for some time with no issue at all - gnome network manager detected the network on startup and connected just fine. However, in the past few weeks (and potentially starting concurrently with an OTA BT firmware update for the router, though I can't be sure) my machine hasn't been able to see my wireless network. It can see plenty of other networks in the area, just not my one. I have tried telling it to connect to a hidden wireless network and put in the details manually - no joy. I tried switching from network manager to WICD and back - still no resolution. The oddest thing is that occasionally it will wake up and find the network (usually after some hours of me trying different things, prompting me to think 'aha! I've fixed it' only to reboot and find out that I haven't at all.) Once it has found it, it doesn't disappear, and if I hibernate the machine rather than shutting down it will find the connection again when i wake it up. This has been my interim solution, but is not very elegant, and I'd love to hear some ideas as to what might be causing this? If i can provide any dumps or logs, let me know. Other Windows machines are not having any issues. Looking forward to your ideas!

Many thanks...

---

### Post by Tricycle on 2009-03-27
lshw -C network for the wireless:

 *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
 vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:25:6c:28
       width: 64 bits
       clock: 33MHz vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:25:6c:28
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by Tricycle on 2009-03-27
FYI: If I plug in a netgear WG111v2 USB wifi dongle, it also picks up the local networks without picking up mine. And I am sitting right next to the AP. In case that helps...

---

### Post by Tricycle on 2009-03-28
Bumpity?

---

### Post by iponeverything on 2009-03-28
Are you seeing this in your /var/log/wpa_supplicant.log

"No network configuration found for the current AP"

If so:

right click on network manager icon go to edit, then the wireless tab. Re-add your key for your connection on the list.  Every time that prompts about access to the key ring -- choose "always remember"

-- see if it solves your problem.  For some reason this issue poped up with me today..

---

### Post by superprash2003 on 2009-03-28
does this wifi network have a weak signal? is it located far away?

---

### Post by Tricycle on 2009-03-28
iponeverything: Sadly, that is not showing up in the log - all I'm getting is many lines of "CTRL-EVENT-SCAN-RESULTS " and then occasionally "CTRL-EVENT-TERMINATING - signal 15 received"...

superprash2003: It's as strong a signal as I can get - I've tried sitting the laptop next to the AP and doing it, and still no joy...

A puzzler!

---

### Post by Tricycle on 2009-04-23
Resurrecting this thread as I've just done a clean install of Jaunty RC1 (not imported any user config or settings) and still I can see all other networks, but at the moment not my own. Does this suggest some issue between the laptop's hardware and the router, some general ubuntu dislike of BT Business (and who can blame it?) or what? More thoughts are very much welcomed as I'm very bored of this problem now!

---

