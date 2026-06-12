---
title: "wireless setup on Broadcom 802.11b/g WLAN"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by nbharadwaj on 2010-06-03
[FONT=&quot]I use Pavilion dv4 Notebook PC (64 bit operating system) which originally came with Windows Vista and I made a separate partition for Ubuntu on it. The wireless card is Broadcom 802.11b/g WLAN. I can connect to my home (or any) wireless on Vista but can not connect to the same wireless on Ubuntu.[/FONT]
   
  Whenever I start Ubuntu, the wireless card is disabled. There is a touch screen panel on top of my laptop key board to enable or disable the wireless card. This wireless touch screen button works fine on Vista but does not work on Ubuntu. However other touch screen buttons (for volume, etc) on this panel work just as good on Ubuntu. The wireless light is always red (which should be blue when the card is enaabled) whenever I am on Ubuntu.


My Synaptic Package Manager on Ubuntu shows that “Network Manager” is installed but  I do not see the launcher for Network Manager in “System” drop down menu or anywhere else (and I therefore have been unable so far to launch it.)
   
  Following are some of the command prompt results on my terminal to show my current wireless status on Ubuntu. I would appreciate any lead that can help me connect to wireless.
   
  - It seems that Ubuntu can detect the wireless card
  $ lspci | grep Broadcom\ Corporation
  03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
   
  - From internet I downloaded Wireless Lan Driver Broadcom 802.11b+g 3.100.46.0 which (apart from many other files) contains bcmwl5.inf and bcmwl5a.inf.
   
  -I downloaded ndiswrapper from [http://ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net/") and was able to install the wireless driver using ndiswrapper:
    $ sudo ./ndiswrapper -l
  bcmwl5 : driver installed
  bcmwl5a : driver installed
   
  - $sudo ./ndiswrapper -m
  module configuration already contains alias directive
   
  $ sudo lshw -C network
    *-network               
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
           resources: irq:18 memory:d9500000-d9503fff 

  ….more lines for ethernet interface (deleted). 
   
  - $ iwconfig
  lo        no wireless extensions.
  eth0      no wireless extensions.
   
  - $ iwlist scanning
  lo        Interface doesn't support scanning.
  eth0      Interface doesn't support scanning.
   
  - $ sudo iwlist accesspoints
  lo        Interface doesn't have a list of Peers/Access-Points
  eth0      Interface doesn't have a list of Peers/Access-Points
  
   
  - $ lsmod
  Module                  Size       Used by
  ….
  b43                        122776   0 
  mac80211             181140   1 b43
  ….
  

Any suggestion or help is appreciated.

 
  Thanks
  NB

---

### Post by cwig on 2010-06-03
I have a acer aspire one with the same wireless card, and what I found to work was from a 

fresh install, the first thing I did was connect it to ethernet and then went to 

System->administration->Hardware Drivers, and then activated the Broadcom STA 

wireless driver.  I did not install the other b43 driver though, I was never able to get the 

b43-fwcutter to work.

---

### Post by nbharadwaj on 2010-06-05
Thanks for your suggestion. I installed the STA driver but wireless still does not work for me. I do not have much clue what to do now, other than removing the other (probably incorrect) drivers that I have installed so far. I would appreciate if someone could tell me how do I uninstall on Linux.

---

### Post by pingu1 on 2010-07-05
I had a similar problem. I installed the "wicd"-wifi-client instead of the one that was default,
and that solved everything for me ... ...

sudo apt-get install wicd-client

---

