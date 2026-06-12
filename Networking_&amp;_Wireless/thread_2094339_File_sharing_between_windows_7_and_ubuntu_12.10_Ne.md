---
title: "File sharing between windows 7 and ubuntu 12.10 Need some help"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by Ghostcore on 2012-12-13
Hows it going everybody.

I recently switched my laptop over to Ubuntu 12.10, no more windows there woot. Thus far the ride has been a fun and refreshing trip with this new version.

However i have managed to hit a snag. Now please note to my credit I did search first... quite a bit actually but I just cant seem to get this problem nailed down.

The problem being my inability to access my Windows7 Desktop from my Ubuntu Laptop. I can see the Desktop in my network however when I try to connect I get prompted for a password multiple times then eventually an error stating "failed to retrieve list from server"

Naturally I can access my Ubuntu Laptop from my Windows7 Desktop and  should I desire enact all sorts of chaos thanks to samba.

I have set sharing so many different way on this desktop that it's down right maddening LOL.

anyhow where I stand right now is the following:
  1. Sharing to the desktop is flawless.
  2. Sharing from the desktop is Nonfunctional.
  3. The desktop IS listed in the network.
  4. Though unneeded ping tests to the desktop are successful.
  5. File and Printer sharing has been enabled via advanced sharing.
  6. I am sharing a folder as opposed to the entire volume.
  7. I have tried with and with out password protected sharing.

I'm to be honest stumped at this point thus any and all help would be greatly appreciated.

Thank You in advance.

P.S Could it be a services Issues on the desktop?

---

### Post by drdos2006 on 2012-12-13
This is what works for me.

From the Control Panel -> Network and Internet -> Network and Sharing Center -> Advanced Sharing Setings.
In both the Current Profile and also in the expanded Public section, Turn on Network Discovery, File and Printer Sharing.
Turn off Password Protected Sharing.
Save and CLose.

From Computer, 
Select the folder you wish to share.
Right click the folder, Share With -> Specific People.

In the Drop Down List select Everyone

From the Drop Down List for Everone, select Read or Read/Write.

From your Ubuntu machine, you should be now be able to connect.

regards

---

