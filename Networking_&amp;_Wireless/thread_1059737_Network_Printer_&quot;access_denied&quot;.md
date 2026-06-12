---
title: "Network Printer &quot;access denied&quot;"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by bba1973 on 2009-02-04
Hello,

I've got some home networking printer sharing issues. I'm on an ubuntu laptop (which had vista) trying to access a printer on another computer on my home network. This printer is connected to the other computer (vista) via usb. After successfully adding the printer, I cannot print with it. The error is "Processing- Connection failed: NT_STATUS_ACCESS_DENIED." When I had vista on my laptop, this printed just fine. Any ideas? Thanks for reading.

---

### Post by bba1973 on 2009-02-04
I tried changing more settings on both computers, but it still won't work. Anyone have any ideas? I really need this to work.

---

### Post by bba1973 on 2009-02-04
> **pmicheal said:**
> Check the sharing settings on Windows Vista. And allow anyone to use printer on main computer where the printer is attached.

Changed that long ago. I also made a firewall rule for Norton 360 that let me print off of it with vista. Still not working. Thanks for the input though.

---

### Post by cariboo on 2009-02-04
Can you print if you turn the firewall off?

Jim

---

### Post by bba1973 on 2009-02-04
> **cariboo907 said:**
> Can you print if you turn the firewall off?

Jim

Still nothing.

---

### Post by bba1973 on 2009-02-05
Still not working. Anyone have any ideas? Thanks.

---

### Post by trumpeteersman on 2009-02-06
I am having the same issue with Windows XP.

I am able to print from another Ubuntu Hardy no problem.

Method 1 from XP, I use ipp://192.168.1.8:631/printers/Deskjet_722C.
I am able to add the network printer and find a driver, but says access denied.

Method 2 from XP: I add network printer via workgroup(I shared printer via samba) and was able to select printer. But this time the error is "Printer name invalid"


None of the computers have a firewall.

Does it make a difference that it is a parallel port printer?

Can someone that has printer sharing working with Windows clients post some info?

---

### Post by bba1973 on 2009-02-06
Update: I googled my problem and read several solutions. Went into the control panel on the Vista machine with the printer, changed all kinds of stuff that's supposed to work, but nothing worked. Tweaked Norton 360 even more, but still nothing. I'm starting to wonder if network printing like this is even possible..

---

### Post by bba1973 on 2009-02-06
I've got VirtualBox running an XP machine. Will that make things any easier?

---

### Post by trumpeteersman on 2009-02-06
One of the XP computers that couldn't print last night was able to today for some reason. 

We added the printer as:
\\IPADDRESS\PRINTERNAME

IE:
\\192.168.1.22\Deskjet_722C


Make sure the name of the printer is correct.

Seems to be a Windows issue.

Hope this helps.

---

### Post by Spherical on 2009-02-06
Please post your /etc/samba/smb.conf file, might help a lot

Default config... I just got it working myself earlier, but can't find the site that told me howto again, sorry.

---

### Post by cariboo on 2009-02-07
You don't need Samba installed to use a printer connected to a windows computer. Smbclient does all the work. As long as you have the printer setup so that anyone can use it and the printer name doesn't have any spaces in it, you should be able to print. The only reason you might have a problem is if the printer isn't supported in Linux.

Jim

---

### Post by trumpeteersman on 2009-02-07
I have a stock smb.conf.  Running Kubuntu Hardy.

---

### Post by bba1973 on 2009-02-07
> **cariboo907 said:**
> You don't need Samba installed to use a printer connected to a windows computer. Smbclient does all the work. As long as you have the printer setup so that anyone can use it and the printer name doesn't have any spaces in it, you should be able to print. The only reason you might have a problem is if the printer isn't supported in Linux.

Jim

The name does have spaces. I'll go take them out and see if it'll work.

---

### Post by bba1973 on 2009-02-07
> **bba1973 said:**
> The name does have spaces. I'll go take them out and see if it'll work.

This method didn't work. I took the spaces out of the printer name and the shared name on the Vista machine. I'm pretty sure the printer has linux support since there's a driver for it (Brother MFC-8220).

Oh, I'm pretty sure my samba config file is stock. I'm running 8.10, btw.

---

