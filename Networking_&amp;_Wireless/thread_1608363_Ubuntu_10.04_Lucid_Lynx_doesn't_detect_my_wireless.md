---
title: "Ubuntu 10.04 Lucid Lynx doesn't detect my wireless adapter..."
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by drummynator on 2010-10-28
Hello everyone. Got a new computer and I'm fairly new to Linux. My friend let me borrow his 10.04 disk and i can't get it to recognize my wireless adapter. The wireless adapter is a[FONT=Verdana][SIZE=1]n AZiO AWD102N IEEE 802.11b/g, IEEE 802.11n Draft 2.0 PCI Wireless  Adapter Up to 300Mbps Wireless Data Rates WPA/WPA2; 64/128-bit WEP;  TKIP/AES. I'm sure there are some terminal commands you'd want me to run too, but i'm not sure what they are. Like i said I'm new to linux. Any help is greatly appreciated :)
[/SIZE][/FONT]

---

### Post by sanderj on 2010-10-29
Isn't Ubuntu showing a small icon of green piece of computer hardware in the upper right corner? Hopefully it is. Click on it, and hopefully it will install the proprietary wifi driver.

---

### Post by drummynator on 2010-10-30
ehhh.... nope.[SIZE=1].[/SIZE]

---

### Post by bigfootnmd on 2010-10-30
Have you tried GOOGLING?

This page may help.

[http://www.aziocorp.com/support/download/wireless/AWD102N.html](http://www.aziocorp.com/support/download/wireless/AWD102N.html)

---

### Post by pottzie on 2010-11-28
I'm going to jump in on this thread, as I have the same problem- just installed a AWD102N and it isn't recognised. Went to Azio website and downloaded the driver. It's a .tgz file, and we all know what that means..manual install, via the terminal (unless someone can show me a better way!).
 I found this: [http://ubuntuguide.net/how-to-uncompress-and-install-targztarbz2rar-packages-in-ubuntu](http://ubuntuguide.net/how-to-uncompress-and-install-targztarbz2rar-packages-in-ubuntu)
and made some headway with it. First try at just opening a terminal and entering &quot;sudo tar zxvf&quot; and the file name went down in flames, but I still show the file in Firefox downloads, and right clicked the &quot;open containing folder&quot; and discovered that the file was in &quot;temp,&quot; instead of Downloads, which is where everything usually goes. I was successful at entering &quot;sudo cd/tmp&quot;, and then zxvf worked-the .tgz file untarred. That's where I'm at now. Now the question for me is, &quot;Is that it? Am I done, or do I need to &quot;sudo ./configure>make>makeinstall&quot; as the guide says. I ran the ./configure, etc, but it didn't work. The last file showing after the tarball ran was a Makefile, so I tried doing  &quot;make&quot; followed by what I saw on the screen, but that didn't work either. Installing anything in Ubuntu is such a slam-dunk that it's a shock to have to go the old-school route and open a terminal and manually install anything, but that's what it's all about sometimes, and I guess this is one of those times, so if anyone can help me out, I'd appreciate it.
 If there's a better guide for this, let me know. Thanks.
 Edit: This is almost unreadable because where instead of quotation marks, there's a &quot instead. I have no idea why, but I'm sure it'll make getting an answer that much tougher!

---

