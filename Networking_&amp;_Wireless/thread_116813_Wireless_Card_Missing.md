---
title: "Wireless Card Missing"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by seekyrr on 2006-01-13
Got Breezy going with my Orinoco pcmcia card the other day.  Test and working.

Today when I insert the card, Ubuntu beeps but the card wont light up.

lshw shows it sees the card in the slot..but not all the driver or firware info it used too.

Any ideas?

Thanks

John

---

### Post by Mr_Grieves on 2006-01-13
Tried the standard wireless troubleshooting tips found at the wiki/forum?

For troubleshooting: [http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

And also this one: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
and.. [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wireless&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wireless&titlesearch=Titles)

---

### Post by seekyrr on 2006-01-13
great guide..going through it now..just tryingto figure out what could have changed

The PCMCIA card is reporting 
 
*-network
       description: RoamAbout 802.11 DS
       product: Version 01.01
       vendor: Cabletron
       physical id: 0
       slot: Socket 0

The driver was in there yesterday before the reboot..I have made no changes since then.  

Do you think it is a driver issue or could the card have gone kaput?

The dmesg used to show firmware etc..but now shows

[4295480.265000] orinoco 0.15rc4 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4295480.267000] orinoco_cs: disagrees about version of symbol orinoco_reinit_firmware
[4295480.267000] orinoco_cs: Unknown symbol orinoco_reinit_firmware
[4295480.267000] orinoco_cs: disagrees about version of symbol hermes_struct_init
[4295480.267000] orinoco_cs: Unknown symbol hermes_struct_init
[4295480.267000] orinoco_cs: disagrees about version of symbol __orinoco_up
[4295480.267000] orinoco_cs: Unknown symbol __orinoco_up
[4295480.268000] orinoco_cs: disagrees about version of symbol __orinoco_down
[4295480.268000] orinoco_cs: Unknown symbol __orinoco_down
[4295480.268000] orinoco_cs: disagrees about version of symbol alloc_orinocodev
[4295480.268000] orinoco_cs: Unknown symbol alloc_orinocodev
[4295637.577000] orinoco 0.15rc4 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4295637.579000] orinoco_cs: disagrees about version of symbol orinoco_reinit_firmware
[4295637.579000] orinoco_cs: Unknown symbol orinoco_reinit_firmware
[4295637.579000] orinoco_cs: disagrees about version of symbol hermes_struct_init
[4295637.579000] orinoco_cs: Unknown symbol hermes_struct_init
[4295637.580000] orinoco_cs: disagrees about version of symbol __orinoco_up
[4295637.580000] orinoco_cs: Unknown symbol __orinoco_up
[4295637.580000] orinoco_cs: disagrees about version of symbol __orinoco_down
[4295637.580000] orinoco_cs: Unknown symbol __orinoco_down
[4295637.580000] orinoco_cs: disagrees about version of symbol alloc_orinocodev
[4295637.580000] orinoco_cs: Unknown symbol alloc_orinocodev
[4295844.294000] SCSI subsystem initialized

---

### Post by seekyrr on 2006-01-13
I followed these instructions and after reboot everything seems to be working again.

PCMCIA:

Unfortunally PCMCIA doesnt run out-of-the box. But its easy: In a terminal open /etc/pcmcia/config.opts with sudo gedit /etc/pcmcia/config.opts and add a one line with:

  include port 0x3000-0x7fff, memory 0xe8100000-0xe97fffff

---

### Post by sas on 2007-02-06
Seekyrr: Did you follow the guide located here: [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

Someone has said that you had and added the fix you detailed in this thread to the page, but I'm confused - that's the USB version, it's not intended for usb, you can use the svn trunk for that...

---

