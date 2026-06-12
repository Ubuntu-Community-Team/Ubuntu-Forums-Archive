---
title: "NDIS Wrapper/Hawking HWP54G -Works."
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by BLH on 2006-05-18
Just finished up a fresh install of 5.10 on my kid's computer.. I had a bit of a fight to make the wireless card work and wanted to share my solution in hopes that it might save some time for others.. 
As stated this is a Hawking Tech card with the TI-ACX111 chip-set. The drivers in Ubuntu found the card but I could not get it and the router to connect with one another. As per several of the threads here in the forums, the ACX project page and the House of Craig page (let me know if you need the link and I'll post it) I tried to update the driver for the ACX driver with the proper image...No Luck.
Next move was to try NDIS Wrapper. Again per the How-To and instructions from NDIS I uploaded my driver with the -i command and the software reported back that both the driver and card were present. But again no luck.iwconfig would the card but no association was being made with the router.. After some additional reading I found that the both the NDIS driver and ACX driver can't be run at the same time..The ACX driver kept loading even after being added to : /etc/hotplug/blacklist. After a little more research I found that the ACX driver was being called from : /etc/modules. I commented out the offending line (acx_pci) and re installed the drivers with  NDISWRAPPER (from the directory containing your M$ drivers for your card enter : ndiswrapper -i <filename.inf>). The card showed up as soon as I turned it back on in the Networking tool (also remember to enter your ESSID and WEP key in this tool if needed) under System > Administration. I also took the machine off of my hardwired network and then re-booted (just to be safe).. The network came right up with out any issues. It has been up for about 96 hours w/o issues..Again I hope that this helps and makes some kind of sense.. Let me know if you need clarification on any of this. Also please forgive me for not throwing all of the commands on here, I'm still a bit of a noob when it comes to trying to post...

---

