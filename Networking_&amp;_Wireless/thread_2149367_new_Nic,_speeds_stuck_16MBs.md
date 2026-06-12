---
title: "new Nic, speeds stuck 16MB/s"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by jhayes on 2013-05-28
what i have, is an 8 drive software raid array, a 2-port nic like this [Dell-Intel-Pro-1000-PT-DUAL-port-NIC]("http://www.ebay.com/itm/Dell-Intel-Pro-1000-PT-DUAL-port-Gb-network-NIC-0X3959-pcie-card-PCI-e-express-/151042699943?pt=US_Internal_Network_Cards&hash=item232ad8b2a7") desktop board, 16gb ram, pretty standard stuff. recently  i changed it from 2 pci NIC's to the one dual-port pcie NIC. in my windows desktop after the switch i put one of the pci nics in. the 2 port nic in the server is assigned 192.168.2.5, 192.168.2.6, the 2nd nic in desktop is 192.168.2.8, and both the onboard nics are dhcp from ISP. there is a generic $50 gigabit 8port switch in between it all. before the nic changes i was able to get speeds of 80-110MB/s coping to the windows box. now it tops out at 16MB/s, almost as if there were a cap ( moving large file like movies). i suppose it is possible the "new" 2-port nic is bad, but i can rx/tx data on both ports. went the intel site to try to upgrade to newest driver for the nic on windows box, but the only thing available was default baked in driver. it does not seem to matter if i am using smb/windows file transfer to copy, or sftp over ssh, same exact speeds.

i don't think it is the raid array, what should i do to test it?
what sort of tests can i run to test what is going on? i have access to a laptop i can use for testing ( old crappy, but gigabit), will us this to try to isolate whether its the windows desktop or the server. are there any networking commands i can run, iftop might be useful.


turns out, it was the NIC drivers on Windows, or the NIC itself or something. it seems windows 7 + Intel PWLA8391GT PRO/1000 GT NIC is a terrible combination. switched to the realtec card talking to server, 110MB/s no big deal.

---

