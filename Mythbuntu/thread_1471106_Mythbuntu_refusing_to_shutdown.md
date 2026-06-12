---
title: "Mythbuntu refusing to shutdown"
date: 2010-05-03
forum: Mythbuntu
---

### Post by Macka01 on 2010-05-03
Hi,

When ever a shut don is initiated via the GUI Log Off>Shutdown command or the MythWelcome automatic shutdown, Mythbuntu refuses to shutdown completely.

The GUI closes off, the mythbuntu logo flickers across the screen very quickly and then I am left with a black screen for a few seconds. Next, a lot of unfamiliar writing appears, the last lines of which is: 
Deconfiguring Network Interfaces
Deactivating swap...

if I press ctrl+alt+del I get more text and then the system reboots (starting from standard bios screens).

This started occurring today, after I tried to activate WOL. I typed:
 sudo ethtool -s eth0 wol g
and modified the halt and reboot files (I followed these instructions [http://ubuntuforums.org/showpost.php?p=4487142&postcount=9](http://ubuntuforums.org/showpost.php?p=4487142&postcount=9))

I have tried a number of things including:
sudo ethtool -s eth0 wol d
undoing all changes to the aforementioned halt and reboot files
disabling the adapter via bios
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8251848&postcount=40](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8251848&postcount=40)


I am getting nowhere, what else can I try?
This system is setup to auto boot for recordings and then shutdown afterwards.

---

