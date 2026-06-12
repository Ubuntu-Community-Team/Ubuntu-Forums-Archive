---
title: "adding network printers to Server 9.10"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by associates on 2010-03-01
Hi,

I have Ubuntu Server 9.10 up and running as my file server. However, it sits amongst other PCs running XP Pro and Network Printers (e.g. Xerox Docuprint C2535A) on the network. My question is whether there is a way of adding the Xerox printer to the Ubuntu Server so that other PCs will send print jobs through the server. I think the printer is windows-based printer. Is it possible to do this? or are there any other options that you may be able to share with me?

Any help would be greatly appreciated.

Thank you in advance

---

### Post by arubislander on 2010-03-01
Is the printer connected directly to the network (i.e. not to another computer, but visible on the network)?

---

### Post by UrBob on 2010-03-01
> **associates said:**
> Hi,

I have Ubuntu Server 9.10 up and running as my file server. However, it sits amongst other PCs running XP Pro and Network Printers (e.g. Xerox Docuprint C2535A) on the network. My question is whether there is a way of adding the Xerox printer to the Ubuntu Server so that other PCs will send print jobs through the server. I think the printer is windows-based printer. Is it possible to do this? or are there any other options that you may be able to share with me?

Any help would be greatly appreciated.

Thank you in advance
You will need to set up Samba on the server. Take a look at [http://www.samba.org](http://www.samba.org) for a lot more details. I found Samba in the standard packages on Ubuntu 8.04. It may already be installed, or partly installed.
 
You will probably find that the printer is supported within your Linux box, you just have to find the correct driver. When you install the printer there are options for sharing it. I have only attached network printers so far, using the System|Admin|Printing option from the Gnome desktop, but very straight forward.
 
Of course, if this is a network printer, connected directly to the network, all the other machines will be free to connect directly to it anyway. To restrict access, you would need to connect it directly to your server using USB, for instance.
 
Incidentally, I am not sure what a Windows based printer is. Many printers come with only a Windows driver because they are aiming at that market, but there are often Linux drivers available from the manufacturers or there is an implementation which supports the printer in the Linux community.
 
Let us know if you need any more detailed information.

---

### Post by associates on 2010-03-01
Thank you, arubislander and UrBob for your replies.

arubislander, to answer your question - yes, the printer is connected to the network at the moment. When i bought it, it came with a CD installation driver. To install and get it connected to the network is pretty straightforward under windows operating system. But i do not know how to install the driver onto the Ubuntu Server from the CD. Do you happen to know how to do this?

UrBob, I have read the link you gave. I tried to use CUPS but to no avail. I got stuck when it comes to installing the driver (or ppd). I could find Xerox from the manufacturer list but was unable to find the model for my xerox docuprint C2535A. 

From the installation CD, it does not say anything about Linux though. My suspicion is that it may not support Linux operating system. 

Thank you in advance

---

