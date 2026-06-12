---
title: "Epson TM-U220 - Generic Text Only Printer"
date: 2021-08-07
forum: MINT
---

### Post by adrianmd on 2021-08-07
Hello. I'm new on this forum so, if this question has been resolved in the past, I apologize for it.

Well, I have installed **Linux Mint 20.2 XFCE** (based on Ubuntu 20.04) on my PC. It works pretty well after some manual settings.

The problem I have is with the printer. I have installed an** EPSON TM-U220** printer (POS Ticket - Dot Matrix Printer) using Epson drivers for linux.

Source of the drivers:
[https://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=5&scat=32&pid=42](https://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=5&scat=32&pid=42)

I could only make the version 1.0 to work, probably due to an incorrect uninstalling proccess before trying newer versions. 

The thing is: the printer is working, it is recognized by the CUPS configuration process, but when I use the PPD file that came with the drivers (to configure the printer), the printer is only capable to print plain text as an image. The result: the text is not as clear as it should be, being printed from a txt file, because the printer applies too many points for every line of text.

This is a problem that I also had on Windows, so I've tried to configure the printer via "**Generic Text Only**" drivers. It worked on Windows. But I can not make it work on Linux. 

After I configure the printer via CUPS (using **Generic>Text Only** Drivers), it simply does not print anything.

I've also tried using **Generic>PostScript** Drivers and the printer could print some text, as plain text, but it is some kind of script code mixed with the content of the TXT, what led me to think that this process printed all the coded instructions that were executed behind.

Could anyone teach me how to correctly set this printer, to print tickets as plain text?

---

### Post by coffeecat on 2021-08-08
*Thread moved to **Mint** sub-forum.*

---

### Post by adrianmd on 2021-09-12
[https://i.ibb.co/KXkxXcj/Linux-Mint-Print-01.png](https://i.ibb.co/KXkxXcj/Linux-Mint-Print-01.png)

This is an example of a ticket printed using the driver provided by Epson.

The quality of the text is not as sharp as I would like.

This is an example of the plain text quality I'm looking for:

[https://i.ibb.co/k52dSq2/Linux-Mint-Print-02.png](https://i.ibb.co/k52dSq2/Linux-Mint-Print-02.png)

This ticket was printed using a wrong driver (post script generic), but It shows very well the type of printing I would like to get: one point per line and a much more faster printing proccess, since the printer does not pass by the same point many times.

---

