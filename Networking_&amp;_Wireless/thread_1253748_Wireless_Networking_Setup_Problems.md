---
title: "Wireless Networking Setup Problems"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by kit294 on 2009-08-30
Having trouble installing wireless network.
New installation Ubuntu 8 older version, Newbee
Showing no wireless connections under System=Administration=Network
Wireless Network Card: Rosewill RNX-N300

First I checked the device for recognition..= UNCLAIMED (no driver?)
 
*-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2


Installed ndisgtk
Inserted windows driver disk..
only inf file on disk is the "autorun.inf" file (with utility .exe files)

Second Ran that driver in ndiswrapper tool = Error Message
Is this wireless card a no-go for Ubuntu or is there a different route??
Or maybe I'm overlooking something here or can use some generic driver here..?
Any help would be greatly appreciated..thanks

---

### Post by bowhuntr09 on 2009-08-30
somehow you will need to get the correct .inf and the .sys files for that NIC. It looks like the download from the vendor wants to install in Windows not just extract so if you have a windows system available try that approach.

---

### Post by kit294 on 2009-08-30
Thanks bowhuntr..but...
I found the wireless card inf driver file (agisP.inf) from the windows system located in the Windows system inf folder and tried to run that one with ndiswrapper...still no luck..gave me another error. (It says its an invalid driver)
Anyone know where i can find a wireless network driver that may work for this??
Thanks

---

### Post by bowhuntr09 on 2009-08-30
The invalid driver error is because you need the .sys file to match the .inf file. If you can locate that and put it in the same folder as the .inf file and use ndisgtk again you should be good to go.

---

### Post by kit294 on 2009-08-31
Im trying different files here..
No luck getting it to work..i wonder if i need a different wrapper version..hmm.. still says invalid driver here..
I even uninstalled the program and reinstalled it..then tried different files, its the files i found in the Windows driver and inf folders because they had the correct dates and name... does the wrapper just not like certain inf files or do different versions work with different wireless drivers? I had the inf file and sys file in a single folder on my desktop..hmm..maybe im not supposed to put it on the desktop for it to recognize it?

---

### Post by bowhuntr09 on 2009-08-31
I assume you did look at this troubleshooting guide? It might just be a unsupported nic. 

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

