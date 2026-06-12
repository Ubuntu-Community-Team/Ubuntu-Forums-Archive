---
title: "Using a printer connected to a Vista box"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by faust7 on 2009-01-28
Hi guys,

I have checked the forums before posting this and I am more than confused at this point.  I want to be able to use my Samsung printer on Ubuntu. That printer is connected to a Vista box. The vista box and the Ubuntu box are both connected on a local router. 

When I go in the Printer menu of Ubuntu 8.10, I click on Windows Printer via SAMBA.  Then I click browse, and I see my Windows Network and the other computer. Unfortunately, I am unable to see the printer in that menu.

I have read things about Samba... and other methods as well but since Samba appears to be installed as a default option on Ubuntu 8.10, I am wondering if you guys could help me make the next step to a successful installation!

Additional info: the printer is shared on the Vista machine. I made sure to put all access to "Everyone" and also unchecked "enable bidirectional support" as some posts had mentioned. 

Thanks in advance!

John from Montreal

---

### Post by faust7 on 2009-01-28
Ok guys, there have been some slight ameliorations...

I've been able to mount a shared folder on Vista and access it from Ubuntu (Workgroup : MYCOMP, Computer name : VISTABOX)

Yet, in Windows Printer via Samba, if I browse manually, I see the workgroup and the computer name but not the printer. The printer is on and is shared on Vista (double-checked that).  Could it be a bug with Vista? If so, is there a way around it to manually add the printer?

Additional info: the printer is hooked up to the Vista machine with a USB connection.

...

---

### Post by faust7 on 2009-01-29
I have been doing extensive research and it may be a problem with VISTA/USB...What do you think?

---

### Post by faust7 on 2009-01-29
Ok Guys! I found the answer! It's really stupid... I had to rename my printer on Vista because the name was potentially too long and hard to recognize or something. So I changed it to Samsung instead of Samsung SCX-4521F and then I went back and added manually /myworkgroup/computername/Samsung   with the username and password and clicked on verify and it worked... !

---

### Post by stennieville on 2009-02-07
I can't get this to work.  I am almost there, I feel, but it's failing just before completion somehow.  I've got a printer connected to my Vista Home Premium box and it's set to share to all computers on the network. From my Ubuntu computer, if I search for printers, it doesn't show up.  Using Samba, I can see the computer it's connected to ("DESKTOP"), but when I click on the chevron to expand, nothing is there.

So I manually added it in Samba:  smb://WORKGROUP/DESKTOP:USB001/Deskjet, and I entered my username & password and could successfully authenticate, and successfully loaded the drivers.  (Where "Workgroup" is the name of the network, "DESKTOP:USB001" is the computer and the port, and "Deskjet" is the name of the printer)

But when I send a document to the printer, it gets stuck in the queue at 64k and doesn't complete.  The printer clicks and whirrs like it's about to print, and then gives up.  On the Vista computer, the document is there in the print queue, stuck at 64k, and won't go any further -- in fact I have to shut the printer off to get it out of my queue.

I'm so close to getting this to work!  Does anyone have any suggestions?

---

