---
title: "Networked printer &quot;Authentication Required&quot;"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Anessen on 2009-07-12
Hey
I have a HP Deskjet F4180 printer attached to my server computer, which runs Debian. I have a Ubuntu 9.04/Windows XP machine that connects to it fine and can print just fine. 

I have a second computer which runs Ubuntu 9.04 which used to work just fine up until a few days ago when I ran some updates before upgrading the distribution. Now, when ever any user on the system tries to print, they are prompted for a user name and password in a dialog saying "Authentication Required". Entering user names and passwords into these does not allow it to print, it remains in the queue with the status "held for authentication".

Any ideas what this can be? I can't find anything on the internet about this problem, and as I said it works fine on another Ubuntu installation and Windows installation.

---

### Post by John_T on 2009-07-19
I haven't yet figured out how to skip the authentication step, however, you can release a job as follows:

1. Bring up your printer list. ( System > Administration > Printing )
2. Right click on the printer, select "view print queue"
3. Select one of the "Held for authentication" jobs, right click and choose the "Authenticate" option.

You'll then be prompted for the appropriate password, and the job should print.

This works for me from an Ubuntu 9.04 desktop machine to a printer shared on a Windows Server 2003 server, which is running as a domain controller.

---

### Post by Rob Maurer on 2009-08-20
I find that feature a bit time-consuming. I don't know if disabling it will open a security hole. Any insights?

---

### Post by jdorenbush on 2010-03-16
As of this morning Ubuntu has been asking me for my password for authentication every time I print on my networked printer. Any ideas how to stop it from asking me?

---

### Post by asdlkj1986 on 2010-04-06
You can set the username and password while configuring itself..

Select " Set Authentication details now " and set the details. This is working for me.

---

### Post by manthony121 on 2010-08-15
I got rid of the "Authentication Required to Print" dialog by directly editing the file, "/etc/cups/printers.conf", as follows:

Step 1.  Open a terminal window:

   [Applications|Accessories|Terminal]

(In the lines below, '$' is the prompt character.  Type what comes after it.)

Step 2. Stop the cups server:

   $ sudo service cups stop
 
Step 3. Edit the printers.conf file.  I use 'vim' for text editing; you can use whatever editor you like.  'gedit' comes standard with Ubuntu:

   $ sudo vim /etc/cups/printers.conf 

Near the top of file "/etc/cups/printers.conf" is a line:

   AuthInfoRequired username,password

Insert a "#" char in the first column (or, just delete the line):

   #AuthInfoRequired username,password

Step 4. Save edited file
Step 5. Restart cups server:

   $ sudo service cups start

This should fix the problem.  I ran thru the printer config dialog after this change, and it did not change the line back.  It seems there is no way to change it except by directly editing the printers.conf file.

I only have one printer, but you may have to repeat for other printers listed in "/etc/cups/printers.conf".

---

### Post by no1glr on 2011-02-04
Re: Networked printer "Authentication Required"

Had some problem, would not authenticate, clicking remember password did nothing. 

All the recommended solutions i could find, did not work. Was printing from Windows OK, but not Ubuntu from same machine. I really didn't want to log into Windows unless I needed to use Access.

Fixed By
Installing CUPS Web interface
Logging on [http://localhost:631/](http://localhost:631/) on host machine
Add Printer from Admin tab
Re installed printer again, even though it had already been installed from the System, Admin, Printing menu previously, ensuring that share this printer was ticked
Printed without an issue after printer had been added though CUPS web interface

---

### Post by tsilande on 2011-03-29
Manthony's instructions worked for me, thanks! 
Is this a bug (I'm using Ubuntu 10.10) that even if you give a user id and password and ask to remember it when configuring the printer, the conf file has this line: 

AuthInfoRequired username,password

there. Anyway, I commented it out and started the cups and now the system does not ask the uid, password every time. 
ts.

---

### Post by csumm101 on 2012-05-13
I had the same problem. I tried everything on this page.

But I found the problem. I was trying to connect to a network printer.

Somehow Ubuntu tried to use the Samba (smb) protocol instead of ipp.

I just went into the general add printer window on Ubuntu. I selected "add printer". I clicked on "find printer". Then I entered the ip address of the computer which had the shared printer.
It found the printer - but somehow, by default it automatically assumes it is on a samba network. I selected "ipp" near the bottom of the window, added the printer. And everything worked fine.

Tip: Just make sure you select IPP protocol instead of SMB, unless you want to use a samba server.

---

