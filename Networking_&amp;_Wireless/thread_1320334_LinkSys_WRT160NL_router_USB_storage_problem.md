---
title: "LinkSys WRT160NL router USB storage problem"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by omi on 2009-11-09
Hola..

I've  got a brand new WiFi-n router which is very nice. Configuring my wireless network without absolutely no problems..

In addition LinkSys provides and a UBS port for connecting UBS sticks or hard drives. I've connected to the port my external HDD and it was recognized by the router. I've shared the hole partition...

And the problem is: **How to access my HDD with my Ubuntu laptop**?

In the instructions from LinkSys is written how to access your storage in Windows but not and in Linux.
[http://www.linksysbycisco.com/UK/en/products/WRT160NL](http://www.linksysbycisco.com/UK/en/products/WRT160NL)

So I've tried:
* with Nautilus -> File -> Connect to server -> Windows Share with the default "User" *admin* and "Password" *admin* and my server name *WRT160NL* for "Server". Don't know also do I need to point the "share" field

* with Nautilus location bar: smb:\\192.168.1.1

... without success. Does anybody can help with connecting to my wireless storage? I really can't understand which protocol to use connecting this one and couldn't find such a topic in Ubuntu Forums or in Google. Will be appreciated!

I'm attaching and a screenshot from router's storage configuration tab.

---

### Post by freedmv on 2009-12-11
Hi, i faced same problem.

The only way that i found to fix it, is to reset the router to default settings, but **important**, before to do it and during all resetting process, **dettach the hard disk** from the usb input. Then after everything is working fine, you can connect it again and add some shared folders.

to access the disk: user is **admin **and password is **admin**,

hope it can help.

Regards.

---

### Post by ciallu on 2010-08-30
Sorry... don't want to move the topic but... I wondered to know if it supports WPA2 using AES. Are you using that way and is your distro Lucid? Is a real 300n or a 150 Mbps?

Thank you.:)

---

### Post by Stryder78 on 2010-09-16
Hi, I'm facing the same problem. I connected my external hard drive (WD Mybook 1.5 TB) and I can't even see it on the network. My PS3 can access it as a media server, same as my Media Center in Windows 7. 

Now I have Ubuntu 10.04, can anyone tell me how to access it? I want to add movies and music from my PC connected to wireless (hard disk). I'm also new to Ubuntu. Thanks in advance.

---

### Post by bluedalek on 2010-10-25
Hello

I'm having the same problem.  I am unable to access / locate the attached storage drive.

I am running Kubuntu 10.10 64bit on both my desktop and laptop.  Wired and wireless connectivity works flawlessly.  My media PC is running Ubuntu 10.10 32bit w/ XBMC, and it to is able to connect without any problems.

None of my systems are able to locate or access the storage drive.

My storage drive is a WDC 400MB PATA drive in an external PATA-> USB case.  Works fine when connecting direct to any of the PC's, and the Linksys router detects and allows me to share out the entire partition.  The drive is formatted to NTFS.

Any help or suggestions would be greatly appreciated!

---

### Post by joaor10 on 2010-10-30
Please help us, I have the same problem.

---

### Post by bluedalek on 2010-11-09
Finally had time to contact Linksys support via the online chat.  As soon as I mentioned that I was using Linux, the response I got was "sorry, but that is outside our scope of support".

What kind of company makes and markets a device so obviously towards Linux users, then says "sorry, we don't support the operating system we are marketing this towards".

I'm very frustrated!

>  Chat Transcript	11/09/2010 09:50 AM
[2010-11-09 07:01:04] Please wait... Your number in the queue: 2
[2010-11-09 07:02:04] Please wait... Your number in the queue: 1
[2010-11-09 07:02:05] A representative will be joining you shortly.
[2010-11-09 07:02:46] Roselyn E. (22834) has joined this session.
[2010-11-09 07:03:27] Derek Gentle: Hello. I recently purchase the WRT160NL wireless router w/ USB storage attachment. I have three computers at home all running Ubuntu Linux and have been unable to connect to the shared network drive. I am not at home right now, so I can not trouble shoot with you, but if you could provide a link where I can reference at a later time as to how to do this, it would be greatly appreciated!
[2010-11-09 07:04:37] Roselyn E. (22834): Hello Derek! Welcome to Live Chat Cisco Support for Linksys Products. Have you contacted Linksys before?
[2010-11-09 07:04:50] Derek Gentle: Also, as another note, as a product clearly marketed towards Linux users, there was no documentation included with the router for Linux users...
[2010-11-09 07:05:05] Derek Gentle: No, I have not contacted Linksys support before.
[2010-11-09 07:05:24] Roselyn E. (22834): What are the model and serial numbers of your Linksys device?
[2010-11-09 07:05:48] Derek Gentle: WRT160NL... I don't have the serial number as I am not at home.
[2010-11-09 07:06:56] Roselyn E. (22834): How long have you been using the router?
[2010-11-09 07:07:11] Derek Gentle: About two weeks, maybe three
[2010-11-09 07:10:59] Roselyn E. (22834): Would you like to access the USB drive connected to the router on your Ubuntu computers?
[2010-11-09 07:11:10] Derek Gentle: Yes, please!
[2010-11-09 07:13:23] Roselyn E. (22834): I apologize. It is already beyond our scope of support. Please contact Linux manufacturer to help you further with it.
[2010-11-09 07:14:57] Derek Gentle: You sell a Linux product, designed for Linux users, but when someone uses Linux you don't provide support?
[2010-11-09 07:16:15] Roselyn E. (22834): I do apologize for any inconvenience.
[2010-11-09 07:17:04] Derek Gentle: I'll take that as a yes... thanks for your time and a useless product
[2010-11-09 07:19:23] Roselyn E. (22834): For more information, you can also visit our technical support website located at [http://homesupport.cisco.com](http://homesupport.cisco.com). The site contains troubleshooting tips, how-to instructions, as well as solutions to common issues relating to all Linksys products. Thank you for giving us an opportunity to serve you through Live Chat Cisco Support for Linksys Products. For your records, a case number for this chat session will be e-mailed to you. Feel free to contact us if you require further assistance. Please do not forget to log out from this window. Once again, my name is Roselyn with Badge ID 22834. Thank you for choosing Linksys and have a great day!

---

### Post by bluedalek on 2010-11-10
After doing some more research on this router, I came across these websites:

[http://www.wrt160nl.org/](http://www.wrt160nl.org/)
[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)

Disclaimer: I do not endorse, nor support any information on these pages. I am providing strictly as an FYI.  I have not tried the steps outlined on these sites (although I am planning on it!) so I can not vouch for their validity.

There.. now that is out of the way, hope this helps!

---

### Post by Kalyan-sg on 2011-02-21
I have a WD 2TB HDD, which is connected to WRT 160NL USB port.

I have a Ubuntu desktop 10.10, which is hardwired to the router - no problem accessing the storage
I have an ACER PC on Windows 7 - no problem accessing the storage via wifi
I have a laptop on Windows Vista - no problem accessing the storage via wifi
I have a laptop on UBUNTU Desktop - no problem accessing the storage via wifi

I shall be changing my Ubuntu Desktop to the server version - I shall able to give the feedback on that soon. My Canon all-in-one printer is connected to the Ubuntu Desktop. I cant access that printer using wifi

I wonder if the situation will improve once I have the Ubuntu Sever installed!

---

### Post by gostojic on 2011-05-06
Hi!

I am using Ubuntu 11.04 on ThinkPad T500 and have successfully connected to Transcend StoreJet USB drive via WRT160N router by following these steps:

Places->Connect to Server...

Service type: Windows share
Server: 192.168.1.1 or Setup->Basic Setup->Network Setup->IP Address
Share: Public or Storage->Disk->Disk Management-> Shared Folder Display Name
Folder: [COLOR=DimGray]<leave blank>[/COLOR]
User Name: admin
Domain: WORKGROUP or Storage->Administration->Workgroup Name

Hope this answers original question at least.

---

