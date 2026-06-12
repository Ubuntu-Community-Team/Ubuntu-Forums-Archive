---
title: "Sync Contacts with Nokia C6-00"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by gadepall on 2011-01-25
I have been able to sync my Nokia C6-00 using multisync in Ubuntu Lucid 10.04.  Thought of sharing it in Ubuntuforums.  I have borrowed most instructions from one post for Nokia N95 but do not have the link right now.

1.  Install blueman using
sudo aptitutde install blueman

This installs the bluetooth manager.  It should be easy to configure bluetooth support for your phone with blueman menu.

2.  To get your C6's MAC address, open a terminal and type:

Code:
$ hcitool scan
Scanning ...
        C8:DF:7C:37:AC:CE	Babu
$
My phone is called "Babu" and has a MAC address of C8:DF:7C:37:AC:CE - yours
will obviously be different. Note it down.

3.  Next, determine the Channel your C6 uses to sync with. By default, it should
be Channel 7, but if in doubt, issue the command (substitute your MAC address):

Code:
$ sdptool browse C8:DF:7C:37:AC:CE
...and scroll through until you come to the section referring to "SyncMLClient"
(NOT the "Nokia SyncML Server" or "SyncML DM Client"). Note down the Channel
shown.
Service Name: SyncMLClient
Service RecHandle: 0x1000b
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

4.  Now update the system with new package lists and download the software we
need:

$ sudo apt-get update
$ sudo apt-get install multisync-tools multisync0.90 opensync-plugin-evolution
opensync-plugin-syncml  kdepim opensync-plugin-kdepim

You may also have to install some syncml packages using the instructions in the following link  
[http://ubuntuforums.org/showthread.php?t=1474031](http://ubuntuforums.org/showthread.php?t=1474031)

5.  Go to the Accessories menu and choose "Multisync-gui".
6.  Click on the "Add" icon at the top. You will be prompted for a group name.
You can use whatever you want. I chose "nokia-c6". Type it in and click "Apply".
7.  Now click on the "Edit" button in the middle of the window.
8.  In the new window that appears, click "Add member" on the middle-left. A new
window appears.
9.  Choose "kdepim-sync" from the list and click "Apply". This is your first
member of the group and will appear as "kdepim-sync" in the list under the group
name.
10.  Click on "kdepim-sync" in the list and the window content will change to
show its config. The default config is empty, keep it that way.
11. Now click on "Add member" again and this time choose "SyncML over OBEX
Client" from the list and click Apply. This will be your second member of the
group and will appear as "syncml-obex-client" in the list under the group name.
12. Click on "syncml-obex-client" in the list and the window content will change
to show its config. Ensure that all the text in that window looks like this
(substituting your C6 MAC address and Channel number of course):

<config>
  <bluetooth_address>C8:DF:7C:37:AC:CE</bluetooth_address>
  <bluetooth_channel>7</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>0</usestringtable>
  <onlyreplace>0</onlyreplace>
  <onlyLocaltime>0</onlyLocaltime>
  <recvLimit>0</recvLimit>
  <maxObjSize>0</maxObjSize>
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db></note_db>
</config>

13.  Now press the Refresh button and you are done.

14.  Troubleshooting
 msynctool --sync nokia-c6

This will try to sync your phone and list errors, if any.  I recommend using the multisync-gui.

15.  The file
~/.kde/share/apps/kabc/std.vcf
will have the contacts on your mobile.  All syncs will be through this file. 
Kontact does not automatically sync through this file.  You will can do one of the following:

a)Manually export and import this file before and after syncing respectively.  
b)In Gnome, go to Applications-Office-Kaddressbook-File-Newaddressbook and scroll down to vcard file (last option) and browse for  ~/.kde/share/apps/kabc/std.vcf and press ok.  

Multisync-gui can now sync you contacts and calendar between your Nokia C6 and Kontact.

Note:  This worked for Sony Ericsson W910i as well.  I expect this to work on other phones too.

Warning:  This process is a little buggy, you may experience problems during the first attempt.
Calender syncs well.  New Events sync, but to dos do not.

Not tried notes.

---

### Post by gadepall on 2011-01-25
You also need to install kde-pim plugin for sync

sudo aptitude install opensync-plugin-kdepim

---

### Post by Edifier1007 on 2011-06-13
Hi

Have you upgraded your Ubuntu distro ? and does this still work for you ?

I have 11.04 and tried your steps. Evidently the schema and UI for Multisync have changed. 

I am getting errors on both clients (obex and evol2). Any tips on resolution?

Thanks in advance.

---

