---
title: "New inst' 11.10 .Atheros 5k chipset on Tosh A210 lappy, no wireless"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by dooper on 2011-10-16
Hi all...

I have been using ubuntu for a couple of years now on this Toshiba A210 lappy. Just recently i got the prompt to upgrade to 11.10 so i clicked and set the wheels in motion. Unfortunately for me,i forgot to plug the power lead into the lappy and haf way through the install packages routine, the battery died leaving me with a system that would only boot to a cmd line prompt which was a bit flaky.

I googled and tried various routines but to no avail so burned a new iso of 11.10 and did a complete re-install of 11.10 after retrieving as much useful stuff as i could using the live disk.

In the past i have had the atheros wireless working perfectly with network manager installed but using wicd to manage the wireless.

Windows reports the modem as an AR5700 G or similar.

Now with the new 11.10,i have no wireless though i do have ethernet.


I know the wireless thing with ubuntu and lappys has been a long standing issue but i am unsure as to what the latest fix is for it.

At this stage, i purged the network manager so just have wicd.

Scanning with wi cd produces no networks found.

Having hacked around with the terminal and various commands, i think the ath5k drivers are installed by default ?

lspci produces this bit

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


I re-installed the network manager to see if it would scan but it now doesnt appear in the top right of the tool bar ?


Does anyone know what the latest fix for this wirless issue is please?

---

### Post by dooper on 2011-10-16
OK..i had a flash of inspiration..went to ubuntu software centre...searched for ndiswrapper..saw an installation tool plus some addon source thingies..installed it all.

wicd can now scan and see wireless network...entered passphrase,seems to have issues authenticating....I'm currently using WEP to keep it simple. I think im pointing the right way..:D

---

### Post by dooper on 2011-10-16
Now solved.

I deleted wicd and now find that the network manager is handling wireless just fine :p

So..from the install if i had just gone to the software centre and installed the ndis installer plus add ons,it would probably have worked right from there.

---

### Post by dooper on 2011-10-16
Still having problems...current state,using network manager it will occasionally connect,other times it wont. Also wicd scans but sees no network. I have the ndis wrapper install tool but no inf file for the atheros drivers...does anyone know where they can be had?

---

