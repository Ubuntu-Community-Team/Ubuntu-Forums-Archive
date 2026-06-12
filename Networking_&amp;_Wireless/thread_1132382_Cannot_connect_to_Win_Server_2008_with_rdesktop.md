---
title: "Cannot connect to Win Server 2008 with rdesktop"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by borophyll on 2009-04-21
Hi,

As the title suggests, I cannot connect to a windows server 2008 installation.  The error I get is "ERROR: recv Connection reset by peer".  rdesktop connects fine to my Vista workstation on the same network, so it seems to be an issue with the server, but I'm not sure what?

rdesktop version: 1.6.0
Ubuntu Intrepid
System properties of server says: Windows Server Enterprise without HyperV, Service Pack 1.

Any help would be appreciated.

Thanks in advance.

---

### Post by aquateen.carl on 2009-08-18
I too was having this issue, but with a 2003 server. It was driving me crazy since I could connect to other 2003 servers with no problem. I tried upgrading from rdesktop 1.5 to 1.62 and using the -y option for raw keyboard support... nadda. So since I knew it was only this server having this issue, I remote desktoped into one of the other servers then into the one giving me the issue (yes very ghetto). I then brought up the mmc and added the terminal services snap-in. I changed the following settings:

[COLOR="Blue"]***Connections***[/COLOR]

**_General Tab_**
Security Layer: FROM **RDP security layer** TO **Negotiate**

Encryption Level: FROM **FIPS** TO **low**

**_Sessions Tab_**
Unchecked: Override user settings (When session limit is reached or connection is broken: )

**_Environment Tab_**
Checked radio button for "Do not allow an initial program to be launched. Always go to desktop"

**_Client Settings Tab_**

Unchecked each of the following under "Disable the following:"

Windows printer mapping
LPT port mapping
COM port mapping
Audio mapping


***[COLOR="Blue"]Server Settings[/COLOR]***

Restrict each user to one session=Yes


After doing all this and rebooting the server, I was finally able rdesktop into the server with no issues. Making these changes reminding me that I manually changed some of these settings awhile back to harden the server, but I forgot that I did that. Which is a good example of why documentation of any changes made is important. Unfortunately, because I was so frustrated I didn't make one change at a time like I should have. So I can't pin point which change fixed the issue. If I had to guess I would say it was the changes under the sessions tab and client settings tab.

In your situation 2008 may have some of these settings enabled by default now to try to increase security (just a guess).

Hope this helps.

:)

---

### Post by flitclicker on 2010-06-02
Hi - had the same issue and thought I'd work my way down your list one-by-one.

Happily it was the second one - I set Encryption Level to "Client Compatible" - that got me working.

Just in case that helps anyone else!

---

