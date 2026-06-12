---
title: "Can't add shared printer in Windows XP"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by akelsall on 2009-01-14
I'm currently running 8.10 with an HP C5580 printer attached to it. That works fine. I'm trying to add the printer to my XP box. When I do so, I get the error message "Windows cannot connect to the printer. Operation could not be completed". I have the printer say to be shared in Ubuntu (and it's published). The HP driver for XP is installed in the WinXP box. 
Why am I getting this error message?

I'm using the XP Add Printer Wizard and selecting the "Connect to a printer on the Internet or on a home or office network" option. The URL I'm using is [http://192.168.2.16:631/printers/HP_C5500](http://192.168.2.16:631/printers/HP_C5500). I am able to ping from my Linux box to the XP box, and vice versa.

Thanks,

Andy

---

### Post by lance bermudez on 2009-01-14
have your tried to take the space out between HP_C5500 to something like HPC5500 or C5500 for the share name? I know that when I used to share the printer attached to my windows xp box or files windows and ubunt bothed seem to play nice together with short names.

---

### Post by akelsall on 2009-01-15
Lance, I tried your suggestion with no change. All of the posts I've read inidicated I need to use the printer name shown in CUPS (or shown in the "Printer Configuration" window accessed via System | Administration | Printing". I wouldn't think it would be this difficult, but it sure has been a headache so far. 

Andy

---

### Post by MeURi on 2009-01-15
Same thing here...

I share a printer with my sister's pc, but I have bot Windows and Ubuntu, so I tried to make her add both printers, one to be used while I'm on Windows, and the other one to be used while I'm on Ubuntu (actually the printer is just one, the shares are two, one for each OS).

But I got that error, always.

Could it be something related to Samba users? As to say: should I create an account for my sister, 'mirroring' her account on her pc (Win), and add that to the samba users?

---

### Post by superprash2003 on 2009-01-15
have you tried doing this via samba?? and connecting via smb ??

---

### Post by MeURi on 2009-01-17
Definitely.

The problem occurs while connecting via Samba to a printer shared by Ubuntu (the opposite works flawlessly, at least for me).

---

### Post by superprash2003 on 2009-01-18
this would tell you about samba users [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) .. and this should help you configure printer sharing [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by MeURi on 2009-01-19
Thanks for these links. As soon as I reboot under Ubuntu, I'll try to reconfigure Samba following those instructions, and I'll let you know what happens :-)

---

