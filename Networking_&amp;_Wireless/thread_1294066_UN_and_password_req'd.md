---
title: "UN and password req'd?"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by ST3ALTHPSYCH0 on 2009-10-17
Alright, I've searched and read until my eyes feel like they're gonna bleed and still can't find the solution to my problem
I have 3 machines in my home network

1. My personal machine is dual booting win 7 Ultimate and Jaunty 64 bit.
   AMD Phenom II 805 OC'd to 3.0 GHz
   6 GB RAM
   OB ATI HD3300 GPU
   HP Deskjet D2500 series printer shared

2. Family internet box running Jaunty 32 bit
    AMD Athlon 900 MHz
    512 Mb RAM
    Nvidia 4400 series GPU

3. My wife's work lappy running Vista Home basic
    Celeron 1.6 GHz
    1 Gb RAM

I'm trying to share the printer on my computer. I have gotten both other machines to print from it when booted into Jaunty, but in windows it's another story. Obviously the Vista machine has no problems (it does say that access is denied to the printer when I'm running Jaunty, but will print anyway), but the family machine insists on asking for a UN and password even though I have all password req's disabled in my sharing settings. Furthermore, my admin UN and passw don't allow me access. I have gotten it to the point that I have full read/write access from my win7 machine, but nothing coming the other way. I can see my entire windows network, but jaunty wants a password to access anything, and no password I give it will suffice. I realize that I can save what little might need printed into a shared folder and then come to this machine to print, but I'm trying to cut a step out of the process. This kind of basic setup should just work.... not require a workaround.

I have seen post after post about this same issue, but have yet to find a resolution. Also, yes I have edited my smb.conf file (hence, I have read write access to my family box) and I can already see my network, so the nsswitch.conf (or whatever the filename is, I've forgotten) edit doesn't help me (yes, I tried it and the only difference I saw was in slower internet speeds, so I changed it back). 
Thanks for any help,

PS, no I won't move my printer, and no, I'm not quite ready to go full Ubuntu.... besides I like win7, I'll admit it.

---

### Post by ST3ALTHPSYCH0 on 2009-10-17
As I was aking for help on another forum (ironically the win forums..... but they have a linux page), I realized that I had left out one detail that might be helpful.

When I try to browse for my network printer (yes I do use the Windows printer via Samba option) it often shuts the entire "add printer" dialog as I'm clicking through the network. When it doesn't just randomly close, it asks for a UN/password when I click on my main desktop to view printers.

---

### Post by ST3ALTHPSYCH0 on 2009-10-18
OK, I'm beating my head against the wall here. 

I've tried totally disabling the windows firewall to make sure that's not the issue (problem persists) and also tried connecting directly to a shared folder with the Places>connect to server... dialog. Everything keeps coming back to req'ing a UN and password, but nothing helps. 

I've tried enabling the guest account on my win7 machine. I've created another account with no password. I feel like a cat who's chased his tail until he pukes..... and the darn thing is still firmly attached......

---

### Post by ST3ALTHPSYCH0 on 2009-10-19
In my instance I had to uninstall Windows live Assistant. After that it was all downhill (I had turned sharing off on the printer somewhere along the way, but that was easily rectified!!!) I'm gonna track down the other people who posted about this problem in case they don't see this post. Thanks to all who looked.

---

