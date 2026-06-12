---
title: "How to print from a guest win 95 machine"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by fred6633 on 2010-08-01
Hello,

I don't konw if this is the right forum. 

My knowledge of networks is very limited.

I have googled and googled how to print to cups from Windows.

I have Ubuntu 10.04 installed and have a win 95 installed as a guest machine in Virtualbox.

I have found hundreds of articles similar to this:
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Every article talks about cups print server's ip address, which always seems to begin with 192.168.

I'm not sure I have understood what the print server IP address is. Is it the same as the IP address I get every time I start my computer? In that case it would be problematic since it's a new address every time. 

If it's not the same, how can I find out the ip address of the cups server?

Fred

---

### Post by marc.verwerft on 2010-08-01
> Every article talks about cups print server's ip address, which always seems to begin with 192.168.That's because not all ip addresses are equal - for more info see: [http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html) The 192.168 sequence is typically used for private networks (they are not directly connected to the internet).

The cups server is the computer where cups is running.

If your computer gets a new address  then it gets it thru DHCP (dynamic host configuration protocol).

Maybe this can be a starter to study more about networks: [https://help.ubuntu.com/10.04/internet/C/index.html](https://help.ubuntu.com/10.04/internet/C/index.html)

---

### Post by fred6633 on 2010-08-02
Thanks for the links.

I typed ifconfig and got  85.230.xxx.xxx for ethO.

In windows 95 I selected add new printer, then selected network printer and entered [http://85.230.xxx.xxx:631/printers/HP](http://85.230.xxx.xxx:631/printers/HP) and got an error message that windoze was unable to connect to the printer.

Also when I tried to setup Adobe's postscript driver I got an error that the printer couldn't be opened.

But in the browser in Windows 95 I could type [http://85.230.xxx.xxx:631/printers/HP](http://85.230.xxx.xxx:631/printers/HP) and came to the Cups administration page, and I could even print out a test page.

Could it be a Windows error, e g some protocol that is missing?

Fred

---

### Post by fred6633 on 2010-08-02
Additional info: It worked with Windows XP, so it seems to be a Windows 95 issue.

Fred

---

