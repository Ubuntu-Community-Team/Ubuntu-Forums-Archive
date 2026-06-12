---
title: "Windows 7 can not access CUPS printer"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by pktiwary on 2011-10-29
Hello experts,

I am a new member and a new ubuntu user but a long time linux user and I am having problem with a printer access. Here is my setup.

My desktop has ubuntu 11.10 (64-bit) and a laptop which runs Windows 7 (64-bit). I have an HP printer which is connected via USB to my desktop. I have been able to added the printer successfully and have been able to print from ubuntu. I am also able to see the printer via CUPS i.e http://localhost:631/printers shows me the printer.

I was not able to configure the wireless network card on my desktop on ubuntu after a lot of struggle so I connected my desktop via ethernet cable to a dd-wrt supported wireless router acting as a bridge and this is how I brought my desktop in the home network, just giving this information in case that is relevant.

I added the printer in my laptop by specifying the URL http://192.168.1.3:631/printers/Photosmart_C4200 and looks like windows 7 found it because it successfully added the printer. When I try to print a page from windows, nothing happens. I mean I don't even see that job in my printer queue.

I will provide more details if required. Please help me get this setup fine.

Thanks in advance

---

### Post by pktiwary on 2011-10-30
Any suggestions? I am surprised to see no response so far.

---

### Post by kurt18947 on 2011-10-30
I am not an expert and prefer to network printers by attaching them to a router rather than to a PC.  It's simpler and I don't have to have a PC on to use the printer nor play with samba & windows shares and the rest.  I would suggest a few minutes with Google.  Here is a thread which is not real user friendly but seems plausible.
[http://www.unixmen.com/linux-tutorials/148-sharing-printer-on-ubuntu-linux-with-windows-](http://www.unixmen.com/linux-tutorials/148-sharing-printer-on-ubuntu-linux-with-windows-)
There are other tutorials & how-tos by searching "configuring printer sharinging with ubuntu and windows".  You could also search within this forum.  I know there have been people asking about doing what you want to do and were able to share their printers successfully.

edit:  Here's some 'official' info: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

