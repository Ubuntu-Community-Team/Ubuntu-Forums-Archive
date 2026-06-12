---
title: "D-Link DWL-AG530"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by thechemist on 2006-06-20
Wireless is the Achille's heel of Linux and a fine distro such as Ubuntu is marred by wireless woes despite its numerous positive sides. The fault, if there is, lies with the hardware vendors. Although in widespread use, wireless is not mature yet. The technology is complex and not standardized. There is a large variety of propriatary hardware and software implementations that are quickly evolving in a fiercly competitive business environment. 

Linux, which relies mostly on volonteers, tend to support older wireless chipsets. The volonteers have a hard time keeping up with the rapid pace of the technology. The vendors, who originate the technology, target the operating system with the largest market share (Windows XP). This makes perfect business sense. Vendors will not invest expensive specialized resources to support 'marginal' operating systems to the detriment of their main business line. At best, some vendors (eg Atheros) will make information available to the Linux community. The situation will not change until wireless becomes more standardized (a likely evolution) or until Linux becomes a dominant operating system (a less likely evolution).

In any event, here is my story.

My wireless card is a D-Link Wireless 108AG, model DWL-AG530, hardware version A3, firmware version 1.00, This is a very popular product in North America, D-Link being a major supplier with a large market share. The chipset is from Atheros in all probability (see below).

Installing Dapper on my plain vanilla 386 with XP dual-boot has bee an interesting experience. I had previously installed Breezy and had no problem, except for the wireless card. I decided to do a clean install of Dapper rather than upgrading.

I first used the live/install CD. It got through the motion, showing various screens but I ended up with a blank (or rather pale brown) screen and a hung system. Repeating the process gave the same result.

I switched to the Alternate CD and used the OEM option. It went through various text screens and stalled at the Network screen. I opened my box, physically removed the wireless card and repeated the process. Success ! Dapper installed without a hiccup and I had a dual boot system that worked fine, but no wireless. 

Putting the wireless card back, rebooting and attempting to use the card lead to "segmentation faults", "kernel panics" and hung systems.

The Atheros chipset is supposedly supported by default in Ubuntu through the Madwifi drivers, or so says the Madwifi Web site.

''Ubuntu ships madwifi in the restricted component, which is enabled in the default install. Madwifi chipsets should therefore ‘just work’.''
      - [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

Well, not so for my particular chipset. Here is how I solved the problem.
 
Doing:
 
     lshw -C network

gives:

       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.

So the chipset appears to be from Atheros and (in theory) should be supported by the Madwifi driver, but not in my flavor. Here is the way out.

Install ndiswrapper-utils from the Synaptic Packge Manager.

Blacklist the Madwifi driver so it will not load in the kernel on future bootups:

      sudo gedit /etc/modprobe.d/blacklist

add the following line at the end of the file and save:

      blacklist ath_pci

You need to download XP (yes, as in Windows) drivers for your card. Do not use the drivers that came bundled on a CD with your card - in all probability it will not work. Rather, go to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D) . Find your card in the list and download and unzip the drivers. In my case they are something like NetA3AB.inf, A3AB.sys, etc.

Make sure the wireless card (ath0 in my case) is not active:

      sudo ifconfig ath0 down

Remove the Madwifi module from memory:

      sudo modprobe -r ath_pci

Install the ndiswrapper drivers:

      ndiswrapper -i  /your windows_drivers_directory/your_widows_driver.inf

Create wlan0 so it will be used whenever the wireless interface is started:

      ndiswrapper -m

Load the new module in the running kernel:

      modprobe ndiswrapper

Check that all is well:

      ndiswrapper -l

you should see:

      Installed ndis drivers
      NetA3B3 driver present
      hardware present

Add the ndiswrapper module to the startup modules so the card will be active whenever Ubuntu boots up:

      sudo gedit /etc/modules

add the following line at the end of the file and save:

      ndiswrapper

Finally, to automatically connect to your wireless network on boot up, edit the network interface cofiguration file:

      sudo gedit /etc/network/interfaces

add the following at the end of the file and save:

      auto wlan0
      iface wlan0 inet dhcp
      wireless-essid YOURNET 

You may have to tune the above for your system (static or dynamic IP, WEP or WPA encryption, wireless channel and so on) by further editing the above file or through the graphical interface (System--> Administration--> Networking--> Wireless Connection--> Properties)

The above works for me... most of the time. Note that on the XP side of this dual boot machine, wireless works... all of the time. Good luck with your system.

---

### Post by stupidkid on 2006-06-21
Interesting...madwifi is possibly the best native Linux driver. I've always had success with several Atheros cards under both Gentoo and Ubuntu. Also, native Linux drivers are superior to ndiswrapper drivers since ndiswrapper is simply a Windows driver emulator.

---

### Post by thechemist on 2006-07-03
I agree Madwifi is superior - in theory. In practice it does not work with my card. That was the case in Breezy and is stil the case in Dapper. It is not an Ubuntu issue but a Madwifi one.

---

### Post by whiteguysamurai on 2006-08-26
I 2nd this, i have the same card, and it doesn not work out of the box. it is a hair pulling shame!

But, ndiswrapped drivers are better then no drivers, so i think i will give this one more shot today.

Thanks for the help!

---

### Post by bgr on 2007-09-19
Forgive me for being a complete noob... I have recently configured (sort of) a feisty distro I downloaded out of frustration with windoze.... After getting up and going (and spending some quality time with the Ubuntu bible) I have had difficulty getting my d-link dwl-ag530 h/w A3 f/w 1 working. I have read your posted message and am still no further ahead. I am not sure exactly where to start..... would you be willing, or anybody for that matter, to explain to me how to configure this card??

thanks,

completly frustrated noob who is already falling for the feisty fawn.

---

