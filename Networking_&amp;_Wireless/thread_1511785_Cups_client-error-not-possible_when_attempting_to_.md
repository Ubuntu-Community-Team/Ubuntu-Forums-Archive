---
title: "Cups client-error-not-possible when attempting to print or add printer"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by fadman on 2010-06-17
I  noticed that a bit after I had updated Ubuntu 10.04 through the Update  Manager, I couldn't print at all!  

(I run ubuntu 10.04 on my laptop and have a networked HP  Officejet 6110xi all-in-one printer  connected to a comp running Windows XP home on the same LAN).  Everything works when I boot up in windows vista, so the problem is definitely in Ubuntu.  

First, I checked the printer jobs and it said  that there was an error with a filter or something.  Restarting the job didn't do squat, so I decided to try  reinstalling my printer, but get the  same CUPS error  "error-client-not-possible" right after I click "Apply".  I then Googled the issue  but didn't find much of anything, so I thought I'd try reinstalling CUPS.  No luck there either... Same error  again and again.

Anyone have any ideas as to what the problem is?

---

### Post by klein de usa on 2010-07-08
hi
i have a simular problem, i have a hp 2100 installed through ptl1 port on an ubuntu 10.04 computer with smb installed , i can connect to the printer with another computer as long as it is running 8.04.

to get another 10.04 computer to see the printer i have to bring up one of the 8.04 computers in printer set up and it will install the printer and print lol 

just to make it more clear to get 10.04 to print to another 10.04 computer with a printer on ptl1 i have to go through a 8.04 computer that i already have the printer shaired on.
anything i try with a 10.04 computer to try to connect to the printer  gives me this error:


 error-client-not-possible

---

### Post by tjanzen on 2010-08-06
I'm having the same problem. Laptop with 10.04 Ubuntu networked (wired) to a Windows XP computer which has a Canon printer.

On the final step of connecting to a network printer, I get the CUPs error 'client-error-not-possible'

I don't use this laptop often, so I'm not sure when problem started, but I know that the printing did work on previous versions of Ubuntu.

---

### Post by klein de usa on 2010-08-08
ok 
i figured out how to share a printer between two 10.04 computers. in 8.04 i copped the ipp (ipp://192.168.1.34:631/printers/Hewlett-Packard-HP-LaserJet-2100-Series) and went to a 10.04 computer and went to add new printer then pasted that in where it says other (enter device uri) and it installs the driver and works, all my computers have static ip's that might help, i'm not sure if it will work with xp vista or win7, but you could give it a try just change  192.168.1.34 to the ip of the computer that has the printer.


ipp://xxx.xxx.xxx.xxx:631/printers/Hewlett-Packard-HP-LaserJet-2100-Series 

x are the computer with the printer hooked to it's ip address

---

