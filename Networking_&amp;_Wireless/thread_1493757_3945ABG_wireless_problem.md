---
title: "3945ABG wireless problem"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by Yeeha on 2010-05-26
i have Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) that worked before karmic and still not working in Kubuntu Lucid Lynx.I can see networks but cant connect... I found some topic while ago where person had same problem with exact same card and problem. Topic concluded with guess that its network on/off switch problem as one person supposedly got it to work by setting card from bios on auto activate or something like that. But my bios had no such option. So if this could be the problem, how to solve it and if not what could be? :S

---

### Post by chili555 on 2010-05-26
Let's see what's going on under the hood. Please open a terminal and do:```
dmesg | grep iwl
rfkill list all
```Thanks.

---

### Post by Yeeha on 2010-05-26
dmesg | grep iwl:

[   12.413686] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 2.6.32-22-generic-ks
[   12.413690] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   12.413845] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.413868] iwl3945 0000:0c:00.0: setting latency timer to 64
[   12.474092] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.474095] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.474387] iwl3945 0000:0c:00.0: irq 32 for MSI/MSI-X
[   13.387199] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.723055] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   14.139967] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9

rfkill list all:

0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: compal-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: compal-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

Thx for trying to help! :)

---

### Post by chili555 on 2010-05-26
Everything looks fine. What happens when you try to connect? Does it try? What kind of encryption is on your network? Are you asked for a key?

---

### Post by Yeeha on 2010-05-26
Preparing to connect... Forever. But it doesnt ask password again. Tryed wep and wpa2 both, year ago i think i tryed without encryption too, still didnt work.

---

### Post by chili555 on 2010-05-26
Do you have an active ethernet connection? If so, detach the ethernet cable and try to connect the wireless. Let it try and then do:> sudo cat /var/log/syslog | grep -i networkPaste the last 20 lines or so into a text document (Applications > Accessories > gedit) and transfer it on a USB key and post it here. Let's see what's happening.

---

### Post by Yeeha on 2010-05-27
Heres syslog when i try to connect with wpa2. I was wrong before about preparing to connect going on forever, it eventually asks password again.

---

### Post by chili555 on 2010-05-27
> NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedI am Googling this and I suggest you do the same.

---

### Post by Yeeha on 2010-05-27
Hmm... So far it seems this error is quite generic, but i think bug raport about same problem is here [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/384493](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/384493) . Same card, started with karmic aswell and same description. Sadly there doesnt seem to be any useful information except one person thinks that problem started with new kernel. If i recall correctly wireless stopped functioning before alpha4. I dont know if this is viable plan but if there is easy way to compare karmic alpha3 - alpha4 changes regarding wireless that could still exist in Lucid Lynx then in theory problem could be narrowed down?

---

### Post by chili555 on 2010-05-27
I am sure there are change reports around somewhere.

I have several kernel versions on my laptop, back to 2.6.28-16 and the version of every iwl3945 is 1.2.26ks.

You might see if you have linux-backports-modules-lucid-generic installed. If it is not, install it. If it is, remove it. Perhaps it will make a difference.

What is maddening is that I bought a Thinkpad T60 in mid-2007. It has an Intel 3945ABG and it has run perfectly in every version of Ubuntu including Lucid today. I am answering this post using it. I do not use Network Manager.> [COLOR="Red"]NetworkManager:[/COLOR] nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed Perhaps we should be more interested in versions of NM.

---

### Post by Yeeha on 2010-05-28
Same with or without wireless-backports. I dont think it can be network-manager problem, since wicd seems to be completely independent program, not nm gui and that wont work either. Although i installed wicd without removing nm, dunno if it can cause conflicts? So it still has to be driver or wpasupplicant problem i think. But what i know about that, i am just ordinary kubuntu user... :D

---

### Post by Yeeha on 2010-05-28
And it seems this error comes only with encryption and probably is caused by true error then, heres syslog when connecting without password, no similar error like we googled. Any more ideas? :(

---

### Post by chili555 on 2010-05-28
> Although i installed wicd without removing nm, dunno if it can cause conflicts?And from your log:> [COLOR="Red"]**NetworkManager: **[/COLOR]<info>  (wlan0): device state change: 3 -> 4 (reason 0)So, do you still think Network Manager is not a factor? Would you like to remove it entirely and see if Wicd can connect?

---

### Post by Yeeha on 2010-05-28
that log was produced by connecting usually not through wicd as wicd doesnt seem to leave any trace when doing cat /var/log/syslog | grep -i network. Right now network-manager is unistalled and i am connected with wired connection through wicd so it has nothing to do with nm, but wireless connection still fails. Thx for having patience to help. Only idea that i have right now is to try newest kernels and hope for the best but are there ppas out there where are kernels that are reasonably safe to use and include restricted drivers? Do you have anymore ideas?

---

### Post by chili555 on 2010-05-28
Please post:```
sudo cat /var/log/wicd/wicd.log | tail -n20
```Thanks.

---

### Post by Yeeha on 2010-05-28
2010/05/28 23:39:36 :: using dhcpcd or another supported client may work better
2010/05/28 23:39:37 :: Putting interface down
2010/05/28 23:39:37 :: Releasing DHCP leases...
2010/05/28 23:39:37 :: attempting to set hostname with dhclient
2010/05/28 23:39:37 :: using dhcpcd or another supported client may work better
2010/05/28 23:39:37 :: Setting false IP...
2010/05/28 23:39:37 :: Stopping wpa_supplicant
2010/05/28 23:39:37 :: Flushing the routing table...
2010/05/28 23:39:37 :: Putting interface up...
2010/05/28 23:39:39 :: Generating psk...
2010/05/28 23:39:39 :: Attempting to authenticate...
2010/05/28 23:39:42 :: wpa_supplicant rescan forced...
2010/05/28 23:40:19 :: wpa_supplicant authentication may have failed.
2010/05/28 23:40:19 :: connect result is Failed
2010/05/28 23:40:19 :: exiting connection thread
2010/05/28 23:40:20 :: Sending connection attempt result bad_pass
2010/05/28 23:40:20 :: attempting to set hostname with dhclient
2010/05/28 23:40:20 :: using dhcpcd or another supported client may work better
2010/05/28 23:40:20 :: attempting to set hostname with dhclient
2010/05/28 23:40:20 :: using dhcpcd or another supported client may work better

---

### Post by chili555 on 2010-05-28
> using dhcpcd or another supported client may work betterPlease open Applications > Internet > Wicd. Select Preferences and change to Automatic if not already selected. Then restart Wicd:```
sudo /etc/init.d/wicd restart
```Please see attached.

Any improvement?

---

### Post by Yeeha on 2010-05-28
Everything is already automatic but since other options were greyed out i think only one dhcp client only was installed so not much choice for automatic anyway. I installed dhcpcd and picked that from settings, still the same... But from logs can you read that contakt is made with router? Maybe for some reason wifi hardware can only receive signals and not send due to driver bug.

---

### Post by Yeeha on 2010-05-29
just tryed .34rc7 kernel from ppa and still problem exists :S

---

### Post by chili555 on 2010-05-29
> Sending connection attempt result bad_passHave you carefully checked the encryption key?

---

### Post by Yeeha on 2010-05-29
Disabled encryption: 

2010/05/29 15:48:37 :: Listening on LPF/wlan0/00:1c:bf:62:a6:55
2010/05/29 15:48:37 :: Sending on   LPF/wlan0/00:1c:bf:62:a6:55
2010/05/29 15:48:37 :: Sending on   Socket/fallback
2010/05/29 15:48:38 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2010/05/29 15:48:45 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2010/05/29 15:48:59 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
2010/05/29 15:49:17 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2010/05/29 15:49:31 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2010/05/29 15:49:39 :: No DHCPOFFERS received.
2010/05/29 15:49:39 :: No working leases in persistent database - sleeping.
2010/05/29 15:49:48 :: DHCP connection failed
2010/05/29 15:49:48 :: exiting connection thread
2010/05/29 15:49:48 :: Sending connection attempt result dhcp_failed
2010/05/29 15:49:48 :: attempting to set hostname with dhclient
2010/05/29 15:49:48 :: using dhcpcd or another supported client may work better
2010/05/29 15:49:48 :: attempting to set hostname with dhclient
2010/05/29 15:49:48 :: using dhcpcd or another supported client may work better

This time wicd told that it even tryed to get ip, i guess thats progress :D - with encryption it was stuck on authenticating
That log2.txt was also without password.
Edit: hmm... Shouldnt DHCPDISCOVER check 192.168.1.254 or 192.168.1.1 instead of 255.255.255.255?

---

### Post by chili555 on 2010-05-29
Nope, 255.x is correct. Here is a correct stanza:```
Listening on LPF/eth1/00:16:6f:9a:5f:df
Sending on   LPF/eth1/00:16:6f:9a:5f:df
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to [COLOR="Red"]255.255.255.255[/COLOR] port 67 interval 8
DHCPOFFER of 192.168.1.105 from 192.168.1.254
DHCPREQUEST of 192.168.1.105 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.105 from 192.168.1.254
bound to 192.168.1.105 -- renewal in 39623 seconds.
```Let's try a few tricks. Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Now will it associate?

If it works, we can create one file to make it permanent.

---

### Post by Yeeha on 2010-05-29
Sadly it doesnt change anything... That must be very well hidden bug, survivor. :D

---

### Post by Yeeha on 2010-05-29
But what about that older driver ipw3945 is this still supported? Maybe i could switch from iwl3945? Maybe that driver works for me...

---

### Post by alexelprogramador on 2010-05-29
> **Yeeha said:**
> Preparing to connect... Forever. But it doesnt ask password again. Tryed wep and wpa2 both, year ago i think i tryed without encryption too, still didnt work.


hello

I have the same card.

In my case, its a mini-pciexpress card inside the laptop.

Happend with me, the same. But i solved it replacing the main wireless program called NETWORKMANAGER by wicd

only open synaptic, and install wicd

if you have a repositories downloaded like ubuntu in dvd version, it will caught it by this dvd

if not, dont know really how to do it on spite to use the command lines to connect over wireless a.p.

I report this thread to canonical, but still deploying the same program "the networkmanager part of gnome"

wicd is the vest one.

replace it, and solved all your problemas

---

### Post by chili555 on 2010-05-29
Please see posts 14 and 15. He's already using Wicd. Thanks for the suggestion.

---

### Post by chili555 on 2010-05-29
> **Yeeha said:**
> But what about that older driver ipw3945 is this still supported? Maybe i could switch from iwl3945? Maybe that driver works for me...I doubt it. It stopped being developed when iwl3945 was folded into the mainline kernel.

I am out of tricks. Sorry.

---

### Post by Yeeha on 2010-05-30
> **alexelprogramador said:**
> hello

I have the same card.

In my case, its a mini-pciexpress card inside the laptop.

Happend with me, the same. But i solved it replacing the main wireless program called NETWORKMANAGER by wicd

only open synaptic, and install wicd...

 

In karmic alpha time i used wicd to connect but around alpha 4 i couldnt connect through that anymore too. Are you using Lucid?
I tryed even opensuse livecd to see if it exists there aswell and it did so i guess i have no hope to get it working... :(

---

### Post by Yeeha on 2010-05-31
Yeaaa! After countless hours i found the bug, i installed ubuntu instead of kubuntu, wicd instead of network manager, backport-wireless all for nothing :D. It was very simple conflict between bluetooth program and network-manager it seems, i am right now using gnome and when i turn bluetooth off i can connect, if i turn it on i cant...
Since i have no experience about bug raporting could someone do it for me please.

---

### Post by Yeeha on 2010-05-31
Just a bump to make sure that information gets seen, so this bug would get fixed. Switching between bluetooth and internet is kind of inconvinient :D

---

### Post by chili555 on 2010-05-31
I don't use bluetooth at all in my laptop. I have a line in /etc/rc.local that turns it off on boot. Maybe it will help you:```
# By default this script does nothing.

echo "disabled" > /proc/acpi/ibm/bluetooth

exit 0

```You might have to look around a bit to see the correct place if your laptop is not an IBM/Lenovo.

---

