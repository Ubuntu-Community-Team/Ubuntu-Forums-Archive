---
title: "nokia-evolution sync w/ USB - Help plz."
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by benbenny on 2008-12-20
Hi,

Ive been searching for a while now how to synchronize my Nokia 6230 phone with Evolution via USB cable. Does anyone know if this is possible?
Ive treid the following tutorial: 
[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
without success.

First thing I dont understand is when your told to run the command
```
syncml-obex-client
```
to find the interface number. The result from typing in that command is:
```
ben@ben-laptop:~$ syncml-obex-client -u
Superuser privileges are required to access complete USB information.
Found 3 USB OBEX interfaces
Interface 0:
	Manufacturer: Nokia
	Product: Nokia 6230
	Interface description: (null)
Interface 1:
	Manufacturer: Nokia
	Product: Nokia 6230
	Interface description: (null)
Interface 2:
	Manufacturer: Nokia
	Product: Nokia 6230
	Interface description: (null)
Use '-u interface_number' to connect
ben@ben-laptop:~$ 
```

then the tutorial says "type 5". - what does this mean?

If I ignore this and continue in trying the sync the phone I get :
```
ben@ben-laptop:~$ msynctool --sync nokia-evo
Synchronizing group "nokia-evo" 
Error while synchronizing: Bluetooth selected but no bluetooth address given
ben@ben-laptop:~$ 
```

Why is bluetooth selected? How do I deselect it? (my comp does not suopport bluetooth).
Can someone help me with this? its seriously inhibiting my ability to move away from windows :(:confused:

Thanks,

Ben

---

### Post by benbenny on 2008-12-21
what is the reason no one is replying?
what have I done wrong? is this topic discussed elsewhere or has it been resolved in another post? if so a little direction would be very appreciated.

---

### Post by rieschiek on 2008-12-22
I want to do the exact same thing, but don't even know where to start.  Any help would be greatly appreciated by me, too.

---

### Post by benbenny on 2008-12-22
> **rieschiek said:**
> I want to do the exact same thing, but don't even know where to start.  Any help would be greatly appreciated by me, too.

hey man, post here if you find a solution. Have you treid following through on the link I posted in my first post? maybe that will work for you.

---

### Post by rieschiek on 2009-01-04
OK, the interface (probably 0) and connection type (that's what the 5 is for) need to go into that xml file we edited earlier.  It's set to bluetooth (2) by default, hence the bluetooth error.

Now, when I attempt to sync, my phone 'blacks out' and I get this error:

```
Member 2 of type syncml-obex-client had an error while getting changes: Link Error: 0x0
Member 2 of type syncml-obex-client just disconnected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members
```

---

### Post by ucoder on 2009-01-05
No real solution here either, got this far with usb and 5800 Xpress Music

Found 2 USB OBEX interfaces
Interface 0:
	Manufacturer: Nokia
	Product: Nokia 5800 XpressMusic
	Interface description: SYNCML-SYNC
Interface 1:
	Manufacturer: Nokia
	Product: Nokia 5800 XpressMusic
	Interface description: PC Suite Services

(used 1)



Member 2 of type evo2-sync just connected
Member 1 of type syncml-obex-client had an error while connecting: Unable to connect to the interface
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members

I think I tried all versions for SyncML (0, 1, 2) and 0 and 1 for wbxml, but I keep getting the same error. Also, I tried to make a new sync profile in the phone UI, but it doesn't even offer USB as a choice for connection!

---

### Post by vipseixas on 2009-01-30
Anyone got lucky here? I've tried everything to sync my Nokia 5700 and nothing worked...

---

### Post by bbldox on 2009-02-12
> **ucoder said:**
> No real solution here either, got this far with usb and 5800 Xpress Music

Found 2 USB OBEX interfaces
Interface 0:
	Manufacturer: Nokia
	Product: Nokia 5800 XpressMusic
	Interface description: SYNCML-SYNC
Interface 1:
	Manufacturer: Nokia
	Product: Nokia 5800 XpressMusic
	Interface description: PC Suite Services

(used 1)


Member 2 of type evo2-sync just connected
Member 1 of type syncml-obex-client had an error while connecting: Unable to connect to the interface
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members

I think I tried all versions for SyncML (0, 1, 2) and 0 and 1 for wbxml, but I keep getting the same error. Also, I tried to make a new sync profile in the phone UI, but it doesn't even offer USB as a choice for connection!

Hi 
I was able to COPY the address book from the Nokia 5800 to evolution using this guide:
[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)
It has copied all the contact information, even the pictures.

The main thing about it: run multisync from the command line. I don't understand yet why it doesn't work from GUI.

Later I'll try to sync the contacts back (from Evolution) as well as calendar events

---

### Post by schrill on 2009-04-15
> **bbldox said:**
> Hi 
I was able to COPY the address book from the Nokia 5800 to evolution using this guide:
[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)
It has copied all the contact information, even the pictures.

The main thing about it: run multisync from the command line. I don't understand yet why it doesn't work from GUI.

Later I'll try to sync the contacts back (from Evolution) as well as calendar events

Hi
I was able also able to sync all data between my nokia 5800 (address book,notes,calendar) and evolution using the same tutorial.
[http://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync]("http://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync") 
Even the Multisync 0.90 gui util. works perfectly! But you'll have to install it...
sudo apt-get install multisync0.90
not multisync it's a different util.

---

### Post by bikenerd on 2009-09-28
schrill - I'm also using a Nokia 5800 and am successfully syncing contacts between the phone and Evolution using multisync. I can create and update contacts on either phone, sync and have them appear on the other

I couldn't get it to work with bluetooth_channel set to 10 (Nokia OBEX PC Suite Services) as recommended in Nailor's tutorial.
Similarly I couldn't get it to work with bluetooth_channel 11 (Nokia SyncML Server) as recommended in the NokiaEvolutionSyncingOpensync documentation

To get Evolution Contacts to sync properly I had to
 - Set bluetooth_channel to 8 (SyncMLClient)
 - Leave calender_db and note_db blank

After I got it working once, using command line 
 msynctool --sync Evolution-Nokia

I was able to use the GUI and add the Calender sync.
 
At this stage I've only got Calendar sync working in one direction (from Evolution Calendar to Phone Calendar) and (from Evolution Calendar to Google Calendar) -- but that's an issue for another evening's hacking.

---

### Post by howardW on 2009-09-28
Hi BikeNerd, 
Thanks for this, it's useful to know that it can be done, even if I cannot yet do it. Can you post your full output for the configure for the opex "Member" without the bluetooth address of course. I must be doing something wrong as I cannot get my nokia 5800 to sync at all. 

I have also been attempting to use the sync software on  the phone itself to connect to the ubuntu host. Can you confirm what I suspect that this is not the way to do it. I'm now suspecting that I should be doing nothing on the phone other than the bluetooth pairing and allowing of trust. 

Also, have you found the bluetooth connection flaky? I've had obex errors when I try to "connect"  from the bluetooth icon. Of course, now I try to repeat this to put the error in here it all works perfectly :-)

I have the following opex config, comments and bluetooth addr removed.
<?xml version="1.0"?>
<config>
  <bluetooth_address>xx:xx:xx:xx</bluetooth_address>
  <bluetooth_channel>8</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>1</usestringtable>
  <onlyreplace>0</onlyreplace>
  <onlyLocaltime>0</onlyLocaltime>
  <recvLimit>10000</recvLimit>
  <maxObjSize>10000</maxObjSize>
  <contact_db>contacts</contact_db>
  <calendar_db></calendar_db>
  <note_db></note_db>
</config>

For both bluetooth channels 8 and 10, the ubuntu end prints out nothing after the 
Member 1 of type evo2-sync just connected
The bluetooth icon on the phone has the double arrows next to it. It's trying to do something.

For channel 8, the phone even had a message that it was connected to the ubuntu machine and disconnected when I stopped the process.

---

