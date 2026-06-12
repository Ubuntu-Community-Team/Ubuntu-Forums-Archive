---
title: "Sharing a Windows 7 Printer with an Ubuntu 12.04 computer"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by DZDB on 2013-09-01
**Sharing a Windows 7 Printer with an Ubuntu 12.04 Computer Problem**
 
 
**_Background Information_**

[LIST]
[*]I have successfully installed “Sharing Service”.  I was prompted to install “libpam-smbpass” but I did not install it.  Do I really need to install “Sharing Service” to share a printer? Or is installing “Sharing Service” only necessary for sharing files?
[/LIST]
 

[LIST]
[*]Using my Windows 7 computer I successfully pinged my Ubuntu 12.04 computer.
[/LIST]
 
I used the following navigation to confirm:

[LIST]
[*]I went to the cmd promt
[*]I typed ping and then the ip address of my Ubuntu 12.04 computer
[*]I received a reply from message.  I sent 4 packets, received 4 packets, and lost none.
[/LIST]
 

[LIST]
[*]Using my Ubuntu 12.04 computer I successfully pinged my Windows 7 computer.
[/LIST]
I used the following navigation to confirm:

[LIST]
[*]I went to the terminal.
[*]I typed ping and then the ip address of my Window 7 computer
[*]I received a reply from message.  I sent 6 packets, received 6 packets, and lost none.
[/LIST]
 
So I concluded that the two computers communicating with each other.  Am I correct?
 
In addition I confirmed that the subnet mask for both computers are the same. 
 
 

[LIST]
[*]I have successfully configured Windows 7 to share my HP Laser Jet 1020 printer.
[/LIST]
 
I used the following navigation to confirm this:

[LIST]
[*]Clicked “Start”
[*]Clicked “Device and Printers”
[*]Right clicked on the HP Laser Jet 1020 printer
[*]Clicked Printer Properties
[*]Clicked on the Sharing tab
[*]I ensured that “Shared this printer” and “Render Print jobs on client computer” boxes were checked.
[/LIST]
 
 
 
**_Problem adding Windows 7 Printer_**
I used the following navigation steps to add a Windows 7printer on my Ubuntu 12.04 computer:
 

[LIST]
[*]Click on “System Settings”.
[*]Click on “Printing”.
[/LIST]

[LIST]
[*]Click on the down arrow of “ADD”.
[*]Click on “Printer”.
[*]Click on “Network Printer”.
[*]Click on “Windows Printer via Samba”
[*]Click on “Browse”.
[*]Click on the right arrow of “WORKGROUP” (in the Share column)
[/LIST]
 
**Note:** In the Comment column, DZDB-WINDOW7 is displayed – this is the correct Computer Name of my Windows7 Computer 
 

[LIST]
[*]Click on the right arrow of DZDB-Windows7
[*]At this point an “Authentication” prompt is displayed
[*]The “Username” displayed is the correct “Username of my Windows7 computer.
[/LIST]
 
**Note: **I confirmed this by going to the C:\User folder of my Windows 7 computer. 
 

[LIST]
[*]The “Domain” is also correct; it is the default “WORKGROUP”.  I used the following navigation to confirm this:
[/LIST]

[LIST]
[*]Clicked “Start”
[*]Right clicked on “Computer”
[*]Clicked “Properties”
[*]I noted that Workgroup: WORKGROUP
[/LIST]
 
 
**Additional Note:** The “Domain” of my Ubuntu 12.04 Computer is also “WORKGROUP”
 
 I used the following navigation to confirm this:

[LIST]
[*]I went into the terminal.
[*]I typed without the quotes: “sudo gedit /etc/samba/smb.conf
[/LIST]
 
 

[LIST]
[*]The “Password” – I left this blank as I don’t have a Windows7 password.  When I boot my Windows7 computer, it boots all the way to my desktop screen.  I believe this means that I don’t have a Windows 7 password.  Am I correct?
[/LIST]
 

[LIST]
[*]I click “Ok”.
[/LIST]
 

[LIST]
[*]I then get the following error message:
[/LIST]
 
“Not authorized”
 
“The password may be incorrect”
 
 
So what are my next steps to resolve this issue? Do I need to go to the terminal and install some type of application? Or do I need to adjust some Network setting in one of the computers?

---

### Post by wyliecoyoteuk on 2013-09-01
Ping only bounces packets off the target, which just means that they are on the same network and responding
Windows uses SMB for sharing, the Linux equivalent is called Samba.
Samba has 2 parts, the client (needed for connecting to other computer's samba shares) and the server (needed for sharing resources to other computers).
Sounds like you have them both installed. Most of the smb.conf file refers to the server, not the client.
To connect to a windows 7 machine, you will need a username and password.
Even if your windows user has no password, you will need at least a username.
Look in the control panel under users.

You will need to provide the username in the format computername\username to connect to the windows 7 share.

---

### Post by DZDB on 2013-09-02
Hi Wyliecoyoteuk,

I turned off the firewall of my Windows7 computer (the attached printer was also turned on).  I then logged into my Ubuntu 12.04 computer and navigated to "Adding Printers" and "Windows Printer via Samba".  When the authentication prompt was displayed, I used the following formats for the User Names:

1) computername\username
2) computername/username
3) computername username
4) computernameusername 
5) username
6) computername

None of the above formats worked.

So what is my next step? Should we/I check if I have correctly installed both parts of Samba? If so then how do I perform this check?

---

### Post by DZDB on 2013-09-03
Wyliecoyoteuk or anyone,

I successfully added my HP 1020 LaserJet to my Ubuntu 12.04 computer.  I used the following format:

smb://Windows 7 Computer IP address/HP-LaserJet-1020

Note: I substituted a "-" for the blank spaces in the shared printer name.

Now I have a new problem.  I cannot print from my Ubuntu 12.04 computer.  I receive a new error message:

"Connection failed: NT_STATUS_Unsuccessful"


How do I resolve this issue?

---

### Post by DZDB on 2013-09-14
[SIZE=7]**Solved!**[/SIZE]


After exhaustive googling and research, I finally resolved the issue.  Regarding my post where I received the following error message:(

"Connection failed: NT_STATUS_Unsuccessful"

The resolution posted to solve the "adding a printer" issue is incorrect.


If your Windows 7 computer does not have a password (If your Windows 7 computer boots to the desktop screen, then your Windows 7 computer does not have a password) and you receive the follow error message (please see the very first post):

"Not authorized"

"The password may be incorrect"

Then what you need to do is turn off "password protected sharing" on your Windows 7 computer.  The navigation is as follows:

[U]Windows 7 Computer Navigation:
[/U]- Control Panel
- Network and Internet
- Network and Sharing Center
- Change advance sharing settings (look at top left of screen)
- **Turn off password protected sharing **(note: scroll down a bit)

---

### Post by BlinkinCat on 2013-09-14
Hi,

I'm glad you have solved your problem -

In case you are unaware - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - ;)

---

### Post by DZDB on 2013-09-14
Thanks BlinkinCat.  I was trying to mark my thread as solved but I didn't know the procedure.

---

### Post by BlinkinCat on 2013-09-14
> **DZDB said:**
> Thanks BlinkinCat.  I was trying to mark my thread my thread as solved but I didn't know the procedures.

Glad to help! - :D

---

