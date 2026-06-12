---
title: "Syncing evolution with Nokia N85"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by larsemil on 2010-05-04
I have errors trying to sync my evolution with nokia n85 phone.

here are my settings:
```
larsemil@arwen:~/misc/opensync$ msynctool --showgroup emilisking
Groupname: emilisking
Member 2: syncml-obex-client
	Configuration : <?xml version="1.0"?>
<config>
  <bluetooth_address>00:22:FC:CC:1D:C4</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1</version>
	<wbxml>1</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>0</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db>Notes</note_db>

</config>

Member 1: evo2-sync
	Configuration : <?xml version="1.0"?>
<config>
  <address_path>file:///home/larsemil/.evolution/addressbook/local/system</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

and this is the error i get:
```
larsemil@arwen:~/misc/opensync$ msynctool --sync emilisking
Synchronizing group "emilisking" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Not found (0x44)
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members
```

anyone have any ideas on what to do to get it to work?

---

