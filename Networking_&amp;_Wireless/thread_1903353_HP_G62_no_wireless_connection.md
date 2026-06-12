---
title: "HP G62 no wireless connection"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by MrNaes on 2012-01-02
[SIZE=2]I have just installed Ubuntu 11.10 onto my HP G62 64-bit laptop. Since doing so, I am unable to use my wireless connection. It worked fine when using windows 7.
 Could someone please help me, as I am new to Ubuntu. 

Thanks in advance[/SIZE]

---

### Post by spiky001 on 2012-01-02
Hi  It might be an idea not to double post.  Can you post the output of lspci

---

### Post by MrNaes on 2012-01-02
Sorry, I didn't realize that I had double posted. How do I find the output of ispci?

---

### Post by spiky001 on 2012-01-02
open a terminal and type in lspci FYI if some puts code brackets around a command ```
lspci
``` normally means run in terminal

---

### Post by MrNaes on 2012-01-02
Thanks for the reply. I typed into the terminal as suggested, and here is what came up:

sean@sean-HP-G62-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
sean@sean-HP-G62-Notebook-PC:~$

---

### Post by spiky001 on 2012-01-02
It would help if you could connect with a wired conection an d update te drivers

---

### Post by MrNaes on 2012-01-02
[B]I did try updating this way: system setting, software sources, ticked Propriety Drivers,. I then went to Propriety drivers, removed and then reactivated the drivers. Sorry if I sound stupid, but I am really new to Ubuntu. I did try it last year on another computer, and it worked fine on a wireless connection. 

I have Googled my computer make and model, and apparently there are issues with Ubuntu and wireless connections with my laptop make and model (HP G62). I have not found or understood a solution, however. [/B]

---

### Post by spiky001 on 2012-01-02
I,m not the best with wireless either And dont want to point you in the wrong direction, I know it sounds stupid but is the wireless switch on as it is on a laptop Hopefully some one with the knowledge to get the corect driver will come along

---

### Post by MrNaes on 2012-01-02
Thanks very much for your help. It has been much appreciated, even if you were not able to find a solution. I have the wireless button on, on my laptop. It was working fine on Windows 7. I have even downloaded a .tar file myself from a website which is supposed to be the driver for it. Unfortunately, I don't know how to install it with Ubuntu. I think I have to use Terminal, but this is all so new to me.

---

### Post by spiky001 on 2012-01-02
What did you download and did you read the stickey [ here]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by spiky001 on 2012-01-02
open software centre type in search box sta driver

---

### Post by MrNaes on 2012-01-02
I downloaded Broadcom 802.11 Linux STA Wireless Source. I have managed to install it now, but nothing working. There are some comments on the driver from other people. One of them stipulates that it doesn't work on all hp computers

---

### Post by MrNaes on 2012-01-02
Thanks for the link to the thread, by the way. I am looking at it now. I really want to use Ubuntu, but this is putting me off.

---

