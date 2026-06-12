---
title: "Configuring network printer"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by techiewannabe on 2009-08-26
I am very much a newbie. Thanks to members of the Ubuntu community, I was able to configure my computer to my home network. (I had great difficulty doing it without the help of contributors of the community. The manuals, by themselves, weren't sufficient for me.)

Now my problem is configuring my printer. It is an HP 950C that is on my home network. With the exception of one computer, the network is Windows based. I have read the directions from  Ubuntu manuals about how to configure printers on a network, but I can't seem to get it to work. 

Here are the steps that I follow: 

                                 System > Administration > Printer.  
 Then I go to Server > New > Search.  
 It searches for a printer.  
 I choose 'Network Printer.'  
 I choose 'Windows Printer via Samba.'
 The screen prompts me for data on 'SMB Printer.'
 I have tried every piece of information that I can think of to follow the prompt of : [smb://]("smb:///"). After putting the data in, I click “Browse.”  
 I have never been successful in finding the printer which is located on my network.  
 

 I'm guessing that I am not putting in the correct “language” to identify the printer. I'm sure that there could be other explanations.   
 

 I would love to hear some ideas about solving this problem.

---

### Post by dbalascak on 2009-08-26
Is the printer connected to a Windows machine?  If it is, have you configured the Windows machine to share the printer?  On Windows machine    Start-> Control Panel -> Printers and Faxes.  Right click on the printer and select Sharing.   Select Share and give it a share name.  Just click browse and it should find the windows share.

---

### Post by techiewannabe on 2009-08-27
dbalasak:

Thanks for your note. 

My printer is connected to a Window computer and has been configured to share printing. (My other Windows-based computers on the network have no trouble sharing the printer.) Nonetheless, my Linux (Ubuntu) computer can't seem to "see" it.

Tom

---

### Post by dbalascak on 2009-08-27
Have you installed the smbfs package?  This what talks to Windows shares.You can install it via the package manager System->Administration->Synaptic Package Manager. 

Or command line 
```
sudo apt-get install smbfs 
```

There is good Windows sharing document in the Ubuntu help pages.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Iowan on 2009-08-27
[Here]("https://help.ubuntu.com/community/WindowsXPPrinter") is a help page that looked promising.

---

### Post by techiewannabe on 2009-08-27
Thanks, dblascaks and Iowan:

I do have an smbf package installed. I can "see" the computer that the printer is connected to. I can't "see" the printer. 

I have also gone to the site that you recommended, Iowan. I have tried to follow the prescribed steps (see them above), but I still can't get this to work. 

I suspect that I'm missing something that is very simple (to each of you), and it may seem so obvious to you that you might not even mention it! As I mention above, the screen prompts me for data on the smb printer. I've tried using IP names; I've tried the name of the computer and printer; I've tried every combination of names that I can think of, but can't get the system to recognize the printer. 

I appreciate your patience with me on this. If you have any sugestions, I'd love to hear them. 

I am determined to become somewhat proficient at Linux! Obviously, it is going to take me some time!

Thanks.

Tom

---

### Post by dbalascak on 2009-08-28
Before you go into Ubuntu printer setup, get the IP of the Windows machine that is serving the printer.
Go into Ubuntu  
System-> Administration-> Printing.  
New -> Netwrok Printer -> Windows printer via SAMBA.
You've been up to this point already.
In the SMB attributes box enter the workgroup / server IP
 smb:// Workgroupname/192.168.1.2
Hit Browse
The server sharing the printer should be listed. Click on the triangle/arrow to open the services in that machine.  The printer should be there.

---

### Post by techiewannabe on 2009-08-29
dbalascak:
You  are great! I think that my system has now found the printer. However, the printer is not working. Apparently, I am having trouble "authenticating" it. When I'm prompted for authentication, my Linux password does not work. My Windows system on the network isn't password protected.
Any ideas?
Thanks for your help.
Tom

---

### Post by dbalascak on 2009-08-29
Offhand, no. Vista or XP?  I think Vista has authentication security for shares as a default. You may have to Google the Windows authentication part of it.

---

### Post by techiewannabe on 2009-08-30
Thanks, dbalascak.
The computer connected to the printer uses XP. Per your advice, I'll google "authentication."
Thanks.
Tom

---

### Post by techiewannabe on 2009-09-02
I solved the problem! Thank you to those who posted suggestions. I found the solution to the problem on this page: [http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html](http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html). In particular, 'Step # 7' was the key suggestion!

Yeah!

---

