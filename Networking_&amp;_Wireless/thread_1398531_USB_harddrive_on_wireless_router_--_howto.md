---
title: "USB harddrive on wireless router -- howto?"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by P3t3r on 2010-02-04
I have just bought a wireless D-Link DIR-635 router (with usb slot) to be able to access my internet and harddisk all over the house. The wireless configured without any problem, however, I can't figure out how to access my harddisk through the network.

I have three options in the config: 
"My plug of USB type is:"[LIST][*]Network USB
[*]3G USB Adapter
[*]WCN Configuration[/LIST]

However I'm clueless what to do now. The first option requires a windows-only program, and I can't find an ubuntu equivalent. The second and third option seem irrelevant, or at least I don't know how I could access my disk in that way.

Any help would be appreciated.

---

### Post by dmizer on 2010-02-05
I just had a good long look at the manual for your router. The USB does not appear to support file shares. It seems to be only available for saving or uploading router configuration files, allowing network access to a computer via usb (instead of LAN) or for attaching a 3G broadband wireless adapter.

Sorry.

---

### Post by P3t3r on 2010-02-05
> **dmizer said:**
> I just had a good long look at the manual for your router. The USB does not appear to support file shares. It seems to be only available for saving or uploading router configuration files, allowing network access to a computer via usb (instead of LAN) or for attaching a 3G broadband wireless adapter.

Sorry.

I don't understand... it claims to work in windows, so all I need is a program similar to their (windows-only) utility, no? 

The salesman told me explicitly that the usb port could be used for attaching a printer (to print over the network), does that mean he lied to me? Or is a printer different from a hard disk for this purpose?

---

### Post by gspat on 2010-02-05
I have the D-Link DR-655 router with the same shareport thing...

I had been hoping to use it to share a printer across the network. The long and short of it is that no, nothing will work with it from linux at this time. The shareport driver will not even run under wine.

Best advice is run a lower power server for your file needs and if you'd like printing as well, set up CUPS on it as well.

BTW: The shareport thing has really bad limitations, even for windows users. Only one connected computer can access the HHD / printer / whatever at a time. It's probably best to just ignore it's even there.

---

### Post by dmizer on 2010-02-05
I am not sure I can help much then because I don't see anything in your router's manual regarding file sharing. Perhaps you can try FTP?

Try going to places > connect to server, and make sure the service type is ftp
For "Server" enter your router's IP address, and click "connect".

---

### Post by dmizer on 2010-02-05
> **gspat said:**
> I have the D-Link DR-655 router with the same shareport thing...

I had been hoping to use it to share a printer across the network. The long and short of it is that no, nothing will work with it from linux at this time. The shareport driver will not even run under wine.

Best advice is run a lower power server for your file needs and if you'd like printing as well, set up CUPS on it as well.

BTW: The shareport thing has really bad limitations, even for windows users. Only one connected computer can access the HHD / printer / whatever at a time. It's probably best to just ignore it's even there.

Ugh ... you're right. It looks like the shareport driver simulates a local USB port. I found documentation on it here: [http://www.dlink.com/shareport/](http://www.dlink.com/shareport/)

There's no way that's going to work in Ubuntu.

---

### Post by vishnumrao on 2010-08-11
I too am looking to use shareport to share a USB external disk. I recently got a DNS-323 NAS and Dlink provides a shareport utility addon for the NAS that lets you share any USB device connected to the USB port on the NAS. 

I have had success with using the Windows Utility. Its loses connection but it work mostly. I am looking for a way access the shareport devices on my Ubuntu system.

I find it ironic that a company that uses linux as their OS on their product releases a shareport utility for Windows and Mac OSX, and leaves Linux users out in the cold. Or shall I call it hypocrisy or Is it the laws of economics that prevent them from devoting resources to developing a Linux client!

---

### Post by MartyBuntu on 2010-08-11
> **vishnumrao said:**
> 

I find it ironic that a company that uses linux as their OS on their product releases...


Do you mean *Linksys* instead and not *D-Link*?

---

### Post by vishnumrao on 2010-08-16
> **MartyBuntu said:**
> Do you mean *Linksys* instead and not *D-Link*?

Nope, I meant Dlink! Dlink uses linux on the DNS-323 NAS which also has the shareport feature!

Since it runs linux, there are so many hacks available for the NAS. One can ssh into it, install svn, cvs, lighttpd etc.

---

