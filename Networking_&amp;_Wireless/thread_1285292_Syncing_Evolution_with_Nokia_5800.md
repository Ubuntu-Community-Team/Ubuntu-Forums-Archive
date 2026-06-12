---
title: "Syncing Evolution with Nokia 5800"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by howardW on 2009-10-07
I have a Nokia 5800 and am trying to synchronise Evolution databases with the phone but am having no joy.

I have paired the phone with the desktop and can access the phone and card via bluetooth.

I followed all of the instructions at
[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
and have the following config (comments removed for brevity):
Groupname: nokia-evo_again
Member 1: evo2-sync
        Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

Member 2: syncml-obex-client
        Configuration : <?xml version="1.0"?>
<config>
  <bluetooth_address>00:00:00:00:00:00</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
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
  <contact_db>Contacts</contact_db>
  <calendar_db></calendar_db>
  <note_db></note_db>
</config>

blanked the bluetooth address for security.

Result is :
hostname:~$ msynctool --sync nokia-evo_again
Synchronizing group "nokia-evo_again"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
.... it just hangs there

Am I correct in thinking that I don't need to do something on the phone to start the other end of this process?

I have tried connecting to the phone (mounting it) beforehand and I've tried not mounting it first. I reboot the phone between subsequent attempts.
I've run out of ideas as to what could be the problem... Help
:confused:

Final thing, When I do the sync, I get the following output in syslog
Oct  7 21:42:28 hostname bluetoothd[11575]: link_key_request (sba=<hostAddr>, dba=<phoneAddr>)
where <hostAddr> and <phoneAddr> are the bluetooth addresses of my machine and the phone

---

### Post by suyog on 2009-10-29
Try removing calendar , notes from syncml-obex plugin.

Also ensure that you are not having any spaces, unwanted characters. For me 1 space was causing issue.

before starting sync you should we able to to browse mobile over BT. and it is trusted in bt connections in pc , same in mobile.

Also I would suggest that you create new sync profile, by copying existing PC suite config. Rename it as ubuntu , change host address in connection setting also to ubuntu from PC suite.
Now use ubuntu in place of PC suite for identifier field.

In new sync profile ubuntu, in applications disable notes. calendar and for contacts set direction "to server".

Just try , for me it works fine for Contacts, Calendar, Todo

Notes dont work as they not supported by evo2-sync plugin.

Let me know how it goes.

Best Regards,
Suyog





> **howardW said:**
> I have a Nokia 5800 and am trying to synchronise Evolution databases with the phone but am having no joy.

I have paired the phone with the desktop and can access the phone and card via bluetooth.

I followed all of the instructions at
[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
and have the following config (comments removed for brevity):
Groupname: nokia-evo_again
Member 1: evo2-sync
        Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

Member 2: syncml-obex-client
        Configuration : <?xml version="1.0"?>
<config>
  <bluetooth_address>00:00:00:00:00:00</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
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
  <contact_db>Contacts</contact_db>
  <calendar_db></calendar_db>
  <note_db></note_db>
</config>

blanked the bluetooth address for security.

Result is :
hostname:~$ msynctool --sync nokia-evo_again
Synchronizing group "nokia-evo_again"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
.... it just hangs there

Am I correct in thinking that I don't need to do something on the phone to start the other end of this process?

I have tried connecting to the phone (mounting it) beforehand and I've tried not mounting it first. I reboot the phone between subsequent attempts.
I've run out of ideas as to what could be the problem... Help
:confused:

Final thing, When I do the sync, I get the following output in syslog
Oct  7 21:42:28 hostname bluetoothd[11575]: link_key_request (sba=<hostAddr>, dba=<phoneAddr>)
where <hostAddr> and <phoneAddr> are the bluetooth addresses of my machine and the phone

---

### Post by FariAzz on 2009-12-16
Hi, I have a Nokia 5800 in ubuntu 9.10, I get exactly the same message, it gets stucked in "Member 1 of type evo2-sync just connected" and it never leaves from there..

---

### Post by suyog on 2009-12-17
Have you tried sync via datacable?

---

### Post by howardW on 2009-12-30
Hi all, sorry for the delay.
I did eventually get it working but by giving up with bluetooth and using the USB cable. 

I have been playing... and have got... somewhere
I've found out most of the info below by trial and error.

Firstly, go to evolution and back up all your settings. The instructions below seem to duplicate all of the contacts calendar entries etc so make sure you have a sensible start point to go back to. I've restored the whole lot a fair few times in the learning of
this lot

Also, if you get this to work do an 
msynctool --showgroup <groupname> >text_file 
It took me ages to get back to a working version after playing with a few things.

I gave up on bluetooth in the end and went for USB, the bluetooth may work but USB I have actually got working. Ditto I gave up with the GUI and followed the CLI instructions in the link in the original post.

The basic config that worked for me is:

Groupname: nokia-evo_usb2
Member 1: evo2-sync
        Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
  <notes_path>default</notes_path>
</config>

Member 2: syncml-obex-client
        Configuration : <?xml version="1.0"?>
<config>
  <bluetooth_address></bluetooth_address>
  <bluetooth_channel></bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1</wbxml>
  <username></username>
  <password></password>
  <type>5</type>
  <usestringtable>0</usestringtable>
  <onlyreplace>0</onlyreplace>
  <onlyLocaltime>0</onlyLocaltime>
  <recvLimit>10000</recvLimit>
  <maxObjSize>10000</maxObjSize>

  <!--<contact_db></contact_db>-->
  <contact_db>Contacts</contact_db>

  <calendar_db>calendar</calendar_db>
  <!--<calendar_db></calendar_db>-->

  <!-- <note_db>notes</note_db> -->
  <note_db></note_db>
</config>

On the phone go to settings->connectivity->Data transfer->Sync and ensure that Contacts Calendar and Notes are all ticked. The ticked entries need to match the entries above, ie if there is a contacts entry above contacts must be ticked and vice versa.

You will note that the contacts db is capitalised but the calendar one is not, this is not a typo, it's correct. No idea why this is different

With the contacts, the sync is one way only evolution -> phone. It tries sending them back but easily gets totally messed up and duplicates entries or loses attributes. This is why I told you to back up evolution at the top.

Yes I gave up on Notes syncing Suyog. I'm hoping that when opensync 0.40 is released, Notes will be supported. I'm currently doing it via a really ungodly hack.

---

### Post by howardW on 2009-12-31
Some more updates if people are interested:
Addressbook entries syncs both ways... sort of. 
When it asks which entry to choose I always picked "Newer". Note beware of this, It will create some duplicate entries in the evolution addressbook. Keep an eye on the total contacts and if it increases, go looking.

But.. if as someone suggested in another thread, you delete every entry in the phone and resync, you get a different problem. A single resync does not get all of the entries down to the phone (I have about 170). Retrying the sync gets all entries down. I think it's a phone thing where it is just too swamped to take all of the entries in one go and reports an error. 
For the retrys, it still reports errors (see below) but I suspect it errors on entries it already has so this is not a problem. 

Errors seen:
apping Write Error: Unable to commit change. Error 415
Error writing entry 3246 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3381 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3259 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3266 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3279 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3288 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Error writing entry 3143 to member 2 (syncml-obex-client): Unable to commit change. Error 500
Mapping Write Error: Unable to commit change. Error 500

So in summary, yes it does work but it's buggy as hell. 

Anyway, I've spent enough time doing this, it's new years eve and I'm off to a party. Happy new yr folks.

---

### Post by suyog on 2010-01-02
@howardW, Great to see that you have got something working !!!
For me with N82, I am able to so update/delete/add in both directions, evo<->phone.
Do you know when opensync 0.40 is coming out?I dont see any progress there.

---

