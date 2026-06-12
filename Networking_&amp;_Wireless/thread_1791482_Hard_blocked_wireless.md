---
title: "Hard blocked wireless"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by newb85 on 2011-06-26
I can't seem to enable the my wireless card.  If I check "Enable Wireless" on the menu, the menu section that shows available networks still says "wireless is disabled".

rfkill is showing two Wireless LANs (even though there's only one card) hp-wifi and phy0.  Pressing the wireless button on my machine toggles the hard-blocked status of hp-wifi.  However, I can't seem to hard-unblock phy0, which apparently is preventing my use of the card.

Any suggestions?

---

### Post by garvinrick4 on 2011-06-26
Is it a kernel driver or one you installed?
Can you activate radio signal? (below is code)
```
sudo ifconfig wlan0 up
```What is your card and driver?
```
sudo lshw -C network
```
```
lspci -k
``` Above Just copy and paste the network cards with drivers if having trouble finding kernel drivers.
#Below code one at a time will stop and restart network manager (kind of a reboot for network manager)
Copy and paste one at a time.
```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```

---

### Post by newb85 on 2011-06-27
I don't believe I installed any drivers when I fresh-installed natty.  The wireless worked out-of-box.

Attempting to activate the radio signal resulted in the message "iwconfig: unknown command 'up'".

The card is an Atheros AR5001 Wireless Network Adaptor.  "driver=ath5k driverversion=2.6.38-8-generic firmware=N/A".

The behavior has me baffled.  This morning it worked again, and according to rfkill, neither hp-wifi nor phy0 were hard-blocked.  The only thing I did was reboot, which I had done several times with no success.  So, I tried "sudo rfkill block all", which resulted in both being soft-blocked, but not hard-blocked.  That I expected, but then "sudo rfkill unblock all" resulted in phy0 being hard-blocked again.  Upon rebooting again, neither were blocked at all.

Even though the problem seems to be gone, I would like to know why rfkill lists 2 wlans, which apparently both have to be unblocked for my wireless to work.  Also, why did "rfkill unblock" trigger a hard-block?

Thanks!

---

### Post by garvinrick4 on 2011-06-27
> "iwconfig: unknown command 'up'"should be ifconfig:
> Even though the problem seems to be gone, I would like to know why rfkill lists 2 wlans
rick@rick-HP:~$ rfkill list all
This is normal below. 0 and 1 are indentifier numbers
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
> I would like to know why rfkill lists 2 wlansIt you run 'iwconfig' it is most likely wlan0 is your wireless:
as below:
rick@rick-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:C6:0A:EC   
          Bit Rate=72.2 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:543  Invalid misc:163   Missed beacon:0

---

### Post by chili555 on 2011-06-27
> Even though the problem seems to be gone, I would like to know why rfkill lists 2 wlans
rick@rick-HP:~$ rfkill list all
This is normal below. 0 and 1 are indentifier numbers
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noIf I may assist here, there are two mechanisms that enable or disable wireless. There is the physical hardware itself phy0; in many laptops, there a physical switch or slider that electrically turns off the wireless radio, including my Lenovo T60.

In just about every laptop, there is a little module, in your case hp-wmi; in my case, thinkpad_acpi, that translates key presses into useful commands, such as "Turn on the wireless, please" when I press Fn+F5. So the rfkill system also looks to see if hp-wmi, i.e., the Fn keys, have the wireless radio enabled or disabled. Therefor, there are two listings.

---

