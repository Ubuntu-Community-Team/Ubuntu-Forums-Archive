---
title: "File transfer software"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by Hari5g900 on 2012-12-10
Is there any application to transfer files from my Ubuntu (10.04 LTS) PC to my Windows 7 (Home Basic) Laptop using WiFi?

---

### Post by dannyboy79 on 2012-12-10
its' not really a program per say but there are file transfer protocols. Install samba and smbfs within ubuntu. Edit your /etc/samba/smb.conf file so that the workgroup matches your windows workgroup, not to be confised with windows homegroup) (most likely WORKGROUP) and then you should be able to use the Network location within the left side of your file browser (called Nautilus). Let me know if you need more specifics.

---

### Post by Hari5g900 on 2012-12-11
Yes, I need more specifics

---

### Post by Morbius1 on 2012-12-11
> Is there any application to transfer files from my Ubuntu (10.04 LTS) PC to my Windows 7 (Home Basic) Laptop using WiFi?It all depends on what you mean by "transfer files".

If you are talking about file sharing and you want to access a file on Windows you already have everything installed to do that provided you shared a folder on your Windows machine. Just open up Nautilus and go to Network and you will get a list of all your workgroups and within them all your networked machines.

If you are talking about file sharing and you want to access a file on Ubuntu from Windows then something will have to be installed but it's fairly painless:

Open Nautilus
Right Click a folder you own like ... Documents
Select - Sharing Options
If you don't have Samba installed it will ask you if you want to install it.
Then you just check off all the boxes and you will have created a samba share for the Windows box to access.

If however you just want to get a file or a folder from machine A ( be it Windows, Linux, or OSX ) to machine B then I would recommend **Transfer-on-Lan**: [http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)

Just download it to all your machines and extract it. It's not installed since it's a jar file but all the machines have to have java installed. On Ubuntu just double click the TransferOnLan.sh file and a utility will run that will show all the other machines on your network that have that utility running. If the other user has it running on his machine just drag and drop your file to the desired location and the user on that end will be notified of an incoming file.

---

### Post by Bucky Ball on 2012-12-11
Filezilla. FTP. Is available for Win and Linux.

I avoid SAMBA at all costs (the software, not the music, of course!).

---

### Post by NightsShadeQueen on 2012-12-11
What about Dropbox?

It's probably the easiest to set up, IMO, and gets the job done.

---

### Post by Morbius1 on 2012-12-11
Well, if we're voting on the basis of ease of setup ...  :):

> "Transfer on LAN" is a software that allows multiple users to share files (or folders) on a local network. [COLOR=Blue]It is cross-platform[/COLOR] [COLOR=Blue]and requires no configuration[/COLOR].

Once started, the software displays a list of users who have launched "TransferonLAN" on the local network.

To send files to users, you must first select the relevant users in the list.
Then, by right-clicking, you must select the command "Send" allows you to choose which files to send (use CTRL and SHIFT keys as needed).

It is also possible to drag files from a file browser and drop them on the selected users.

Once the recipient has accepted the transfer, the sending of files begins.Anyway, different paths to the same goal.

---

### Post by dannyboy79 on 2012-12-11
> **NightsShadeQueen said:**
> What about Dropbox?

It's probably the easiest to set up, IMO, and gets the job done.
dropbox is super easy to setup!! I second that IF you don't want to set up samba.

---

