---
title: "Wireless Adapter not working with Ubuntu"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Skeeter7 on 2010-12-08
I am new to Linux and Ubuntu. So far so good. 
My TRENDnet TEW 424UB Wireless Adapter does not show up in the network window. The light does work while using Ubuntu but it goes on during Windows. How do I fix this?

---

### Post by walt.smith1960 on 2010-12-09
What hardware version number? H/W 2.x use an SIS chipset and it apparently only works with NDISwrapper.  I have a H/W 3.1 and it has never failed to connect with different machines and Ubuntu versions. H/W 3.x uses a RealTek 8187B chipset (I think) which is supported natively.  If you're using Network Manager, make sure 'enable networking' and 'enable wireless' are checked.  I've had Network Manager deselect 'enable networking' for no apparent reason.  I hope this helps.

---

### Post by Skeeter7 on 2010-12-09
> **walt.smith1960 said:**
> What hardware version number? H/W 2.x use an SIS chipset and it apparently only works with NDISwrapper.  I have a H/W 3.1 and it has never failed to connect with different machines and Ubuntu versions. H/W 3.x uses a RealTek 8187B chipset (I think) which is supported natively.  If you're using Network Manager, make sure 'enable networking' and 'enable wireless' are checked.  I've had Network Manager deselect 'enable networking' for no apparent reason.  I hope this helps.


Thanks you , but im alittle confused.
In the Network Manager I don't see an option for wireless, could that be the problem?
Nothing appears in the Network connections window. 

Wireless Adapter  TRENDnet TEW-424UB  H/W:V2

I am also unable to figure out how to see my PC hardware specs in Ubuntu.
In windows I would have just right clicked on My computer and hit properties, how do you do this here?
and yes IM new to this so bare with me, LOL thanks

---

### Post by bkratz on 2010-12-09
> **Skeeter7 said:**
> Thanks you , but im alittle confused.
In the Network Manager I don't see an option for wireless, could that be the problem?
Nothing appears in the Network connections window. 

Wireless Adapter  TRENDnet TEW-424UB  H/W:V2

I am also unable to figure out how to see my PC hardware specs in Ubuntu.
In windows I would have just right clicked on My computer and hit properties, how do you do this here?
and yes IM new to this so bare with me, LOL thanks

The last posting on June 20th 2010 
[http://ubuntuforums.org/archive/index.php/t-1429731](http://ubuntuforums.org/archive/index.php/t-1429731)
gives a description of how that user used ndiswrapper for that card. If sufficient details are not there you might try PMing that person.

---

### Post by walt.smith1960 on 2010-12-12
Yes, the H/W version 2 is more difficult. If I recall correctly, H/W ver.2 uses an SiS chipset which does not have native support in Linux.  Version 3 uses RealTek 8187B which does have kernel support.  NDISwrapper is your only chance with H/W ver.2 it seems.

---

### Post by huwjenjinn on 2010-12-13
There's nice little GUI for ndiswrapper in the repository. So, if you have a windows driver (.inf) for the device you can simply use this driver under Ubuntu by configuring the Ndiswrapper GUI - hangs of the Administrator menu once installed.

I'm not at my machine so I can't paste up the command to download and install the ndiswrapper stuff. But if you're familiar enough with installing packages through Synaptic it's there under "ndiswrapper".

---

### Post by walt.smith1960 on 2010-12-14
> **huwjenjinn said:**
> There's nice little GUI for ndiswrapper in the repository. So, if you have a windows driver (.inf) for the device you can simply use this driver under Ubuntu by configuring the Ndiswrapper GUI - hangs of the Administrator menu once installed.

I'm not at my machine so I can't paste up the command to download and install the ndiswrapper stuff. But if you're familiar enough with installing packages through Synaptic it's there under "ndiswrapper".

The package is ndisgtk or something similar in synaptic. If you select that package, it should select and install the other required packages without further prompting.  Yes, it makes installing Windows drivers simple.  The trick can be to find with Windows drivers; some vendors use .exe files which are difficult to extract the .inf, .sys files etc.  The one time I used Ndiswraper, I installed the device on Windows then found out where the files were placed and copied them from there. RealTek seems to use .zip files rather than .exe files which is helpful.

---

