---
title: "Virtual Serial Port? Do they exist?"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by MK1ITS on 2011-08-10
Hi all
 
I'll start by saying that this forum is an excellent source of knowledge and I thank all those that have shared their experience and will continue to do so.
 
OK, down to business.
 
System: Ubuntu 10.04.3 LTS
 
Aim: create a virtual com port
 
Issue: havent goto a clue how to! lol :p
 
I need to get an windows automotive application running through Wine to pick up data from a bluetooth serial device.
 
Linux works a treat when one of the extra com ports (pcie card) are used to pick up the information (serial cable connected straight to the device), but when the bluetooth device is inserted into the machine, and the bluetooth manager pairs the two systems (PC uses a belkin F8T017 bluetooth adapter), I dont know how to check to see if a virtual comport is created. I'm guessing not, as the command:
 
dmesg | grep tty
 
doesnt show any virtual com ports, just the three that the system has physically.
 
In a windows XP environment, the Belkin software seems to handle the creation of the 'virtual com port' which is visible within device manager (a config change has to be made to the automotive application to pick up the new com port), and pairing takes place once the application is ran through bluetooth, so the concept works, in Windows that is!
 
However, I would like to reduce the license costs by utitlising Ubuntu and get this virtual port created.
 
I'm going to contact Belkin to see if they can provide any support for linux, as perhaps I just need to get some software that will do the same as the belkin software does for windows? I dont know....plucking at straws here....
 
Any help with the above at all guys would be appreciated.
 
On another note, when I installed a different serial port card into the linux system and ran through the installation notes, it created ttyD ports? Are these different to ttyS ports?
 
As you can probably guess I'm relatively new to Linux but I am finding the system far more enjoyable than the plug and play environment of Windows.
 
Some will think I'm crazy but there is a certain level of satisfcation in getting something to work.....and a feeling of worth when a technical resolution is needed.....it'd seem that anyone can be a Windows engineer within reason...
 
Thanks again guys....any help at all would be great....:)

---

