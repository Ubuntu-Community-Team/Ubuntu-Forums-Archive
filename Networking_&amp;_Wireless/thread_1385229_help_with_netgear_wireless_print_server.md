---
title: "help with netgear wireless print server"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by cdog2800 on 2010-01-19
Hi, I have a Netgear wgps606 wireless print server with a 4 port switch. My question is how do I configure my ubuntu 9.1 laptop to vwork with this device.Any help will be greatly appreciated.

---

### Post by ethanay on 2010-01-23
are you able to log into the setup screen through your web browser?  this is the part that stumped me the most, as the default IP address for the WGPS606 is 192.168._0_.102 and the default gateway for my router is 192.168._1_.1

for some reason, it did not play nice with DHCP.  to get around this, i had to connect to the print server directly via my computer

steps should be:
1. connect via ethernet directly to computer
2. setup a new wired connection:  right click on network manager > edit connections > wired tab > add > name it XX > IPv4 settings tab > method: manual > address:  192.168.0.112; netmask 255.255.255.0; gateway 192.168.0.1
3. click "apply"
4. exit all the network manager windows
5. left click on network manager, and click on the new XX connection you just set up.

you should now be configured to access the print server setup by typing 192.168.0.102 as the address in your browser

that's as far as i've gotten...it works great as a wireless access point extender.  hopefully it will work great as a wireless print server for our old (but still working!) HP DeskJet 810C.  

will post more results as i have them.

---

### Post by ethanay on 2010-01-23
I am trying to get my printer working via the directions here:

[http://ubuntuforums.org/showthread.php?t=815851](http://ubuntuforums.org/showthread.php?t=815851)

---

### Post by ethanay on 2010-01-23
Am unable to get past the spooling process to actually print something. DOH!

LPD printing worked fine with our old wireless print server, a TRENDNet with a single parallel port.  I have been unsuccessful so far with anything connected to my printer via USB.

USB direct connection to the computer works perfectly, so it's not the printer or the cable.

---

### Post by ewan86 on 2010-06-24
> **ethanay said:**
> are you able to log into the setup screen through your web browser?  this is the part that stumped me the most, as the default IP address for the WGPS606 is 192.168._0_.102 and the default gateway for my router is 192.168._1_.1

for some reason, it did not play nice with DHCP.  to get around this, i had to connect to the print server directly via my computer

steps should be:
1. connect via ethernet directly to computer
2. setup a new wired connection:  right click on network manager > edit connections > wired tab > add > name it XX > IPv4 settings tab > method: manual > address:  192.168.0.112; netmask 255.255.255.0; gateway 192.168.0.1
3. click "apply"
4. exit all the network manager windows
5. left click on network manager, and click on the new XX connection you just set up.

you should now be configured to access the print server setup by typing 192.168.0.102 as the address in your browser

that's as far as i've gotten...it works great as a wireless access point extender.  hopefully it will work great as a wireless print server for our old (but still working!) HP DeskJet 810C.  

will post more results as i have them.

> **ethanay said:**
> I am trying to get my printer working via the directions here:

[http://ubuntuforums.org/showthread.php?t=815851](http://ubuntuforums.org/showthread.php?t=815851)


Thank you these worked perfectly for me... sorry I am not very technical and I can't tell you why it's not working for you on your WGPS606. I have a canon mp180 and have 10.04 installed.

Why when doing that network connection did you use the ip address with the 0.112 rather than 0.102 which is what the print server's address!! I don't get it all but worked superbly!

Thanks

---

### Post by ethanay on 2010-06-26
hi ewan,

i don't know!  maybe i meant to type *.102 and didn't proof read well enough? :confused:

glad it worked for you, though!

ethan

---

### Post by Euphorion on 2010-06-28
Hallo ethanay

As the author of the instructions quoted, the only things that spring to my mind are the following:

Have you checked the firmware version, it is essential that you have firmware greater than V1.0_020 and if not obtain the latest firmware, at best from the Netgear US Site. Then update the firmware, may require that you use a PC with windows to do this if you are having difficulty connecting to the Print Server via Ubuntu.

Do Set the Print Server to a fixed ip address it is essential that it does not use dynamic ip addressing for they can change every time it starts up. If you are accessing it via Router then do this in the Router Setup.

I have recently updated to Lucid 64 bit and have reinstalled the Print Server using my "old" instructions and it works a treat no matter if I use Wireless via router, cable via router or direct via Ethernet cable (computer to server).

Many Netgear print servers do have old firmware, mine had the old firmware all though it is really not that old. The firmware update solved many problems associated with the Print Server.

Also note after submitting the print job it takes several seconds before the leds on the print server flash and the printer starts printing, but you can follow the progress in the Ubuntu spool icon.

My Printers are a good old HP Deskjet 950C and a HP Officejet 4500 both connected via USB to the print server. In the case of the HP Officejet 4500 only printing works, scanning and fax does not because the Netgear Print Server is unidirectional, that is also the reason why you cannot see the ink levels on the corresponding properties tab.

I fax using the remote fax printer  on my wifes windows computer which is part of the network in our house. Scanning can only be done by connecting the computer via usb directly to the officejet.

I hope the above will help.

---

