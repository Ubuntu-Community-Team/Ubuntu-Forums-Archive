---
title: "networking printers and file sharing ubuntu 10.04?"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by proevofanatik on 2010-08-10
my boss has given me the go ahaead to get rid of windows xp on all his machines and install ubuntu on them all. what i want to do is share 1 printer between 3 machines. what is the procedure of this? and also i want to share the documents folders between the 3 machines. so that all 3 machines have access to each others files.

thanks

---

### Post by Peter09 on 2010-08-10
Basically you will have the option to share printers and folders in a similar manner to windows. Click on a folder in ubuntu and declare it as shared. The printer will have a sharing option as well.

---

### Post by willz06jw on 2010-08-20
Howdy,

After you install Samba, use the config-system-samba package (it's a samba GUI). It will make sure you don't overlook some small sambatism. 

If you search in the Ubuntu Software Center for Samba, it will be one of the ones listed (it will be listed as just "Samba" stragely). 

This will put a link to the GUI in your system/administration menu.

I removed some of the security and everything started working hunkey-dory.

Have a good one,
Will from Texas

---

### Post by stijnblommerde on 2010-08-24
samba is used to communicate between ubuntu and windows operating systems. don't use that.

i recently installed ubuntu 10.04 on a desktop and on a laptop, replacing vista on both machines. 
my printer (hp1018) is connected via usb to the desktop.

this is how i set up both computers, in order to print on a single printer, connected to the desktop via usb.

---
desktop, printer server:
system - administration - printing - add -  choose recognized device - drivers are searched for - apply
rightclick printer - properties - policies - state - enables, accepting jobs, shared - ok
server - settings -  basic server settings - publish shared printers connected to this system - ok

laptop, printer client:
system - administration - printing - add - network printer - find network printer - host - IP address

IP address desktop:
applications - accessories - terminal - type: /sbin/ifconfig - write down the number behind: inet addr
---

additional comments:
the printer server is not a real server. i did not install server software on it. 
the last step, the one with the email address, took me a while to figure out.
i am a newbie to ubuntu, just installed the software a few weeks ago. some remarks and steps may sound a bit trivial to more experienced users. forgive me for that.

hope this helps.

greetings, stijn

---

### Post by stijnblommerde on 2010-08-24
update on my last post

instead of using the IP address:

client computer
system - admin - printing - server - settings - show printers shared by other systems

---

