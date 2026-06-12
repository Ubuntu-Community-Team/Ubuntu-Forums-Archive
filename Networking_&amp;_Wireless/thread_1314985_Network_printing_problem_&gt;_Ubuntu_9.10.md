---
title: "Network printing problem &gt; Ubuntu 9.10"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by KMilburn on 2009-11-04
My attempt at an upgrade failed so I did a clean install of 9.10

So far I have most of my previous setups working.

However network printing from WinXP to the Linux system results in
'Access denied, Unable to connect'

From XP I can see my shared folders and access them OK.

Within linux I have no printing problems.
Reviewing CUPS and Samba configuration files has not solved the problem.

I'm looking for direction.

Thanks.

---

### Post by relic70 on 2009-11-05
Take a look at this

[http://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("http://help.ubuntu.com/community/NetworkPrintingWithUbuntu")


It only covers up to version 9.04, but should be valid for 9.10

You can also do a search for more documentation there on network printing or printing in general

---

### Post by SteveDee on 2009-11-05
> **KMilburn said:**
> ...however network printing from WinXP to the Linux system results in
'Access denied, Unable to connect'

From XP I can see my shared folders and access them OK.

Within linux I have no printing problems.
Reviewing CUPS and Samba configuration files has not solved the problem.

I'm looking for direction.

Thanks.

There seems to be a problem with 9.10 and my workaround is to restart samba. See here: [http://ubuntuforums.org/showthread.php?t=1313049](http://ubuntuforums.org/showthread.php?t=1313049)

---

### Post by JackDeth on 2009-11-06
I have been able to print from my Ubuntu laptop to our Dell A940 printer attached to my Win XP machine across our network by using a Lexmark Z55 driver.

It has been printing fine until the Karmic upgrade. Now printing does not work. I have gone through a complete reinstall of the printer driver without success.


Why does printing in Karmic no longer work?

---

### Post by KMilburn on 2009-11-06
I did discover one option which I should have checked, but it did not change my problem.
Thanks anyway.

---

### Post by KMilburn on 2009-11-06
Thanks SteveDee, I tried your work around (both) but with no success.

Thanks for your input.

---

### Post by SteveDee on 2009-11-07
> **KMilburn said:**
> Thanks SteveDee, I tried your work around (both) but with no success.

Thanks for your input.

I wonder if the difference is that you did a clean install rather than an upgrade.

I have attached extracts from my /etc/samba/smb.conf file. The upgrade has resulted in some strange mods to this file including:-

```
;	printing = cups
```

which looks like it should be disabling cups. Anyway, the important settings are under the [printers] and [print$] stanzas. See if yours are different and, if so, try changing them (after you have created a backup copy of your original smb.conf).

Also, the minimum that I do to get printing working after booting the system (the one with the printer connected via USB) is use the samba restart instruction in a terminal window:-

```
steve@printer-desktop:~$ sudo /etc/init.d/samba restart
```

You may still have an initial problem with remote printing after restarting samba where there are a number of reports in the remote computers print queue, so I'd recommend clearing the queue on the remote computer (System > Administration > Printing > Printer > View Print Queue) then sending a fresh print from a simple app like gEdit.

Also note that in the print screen in gEdit, the printer status is only correct after you have attempted to print. By that I mean that after an unsuccessful print, the status shows something like "Unable to connect to CIFS host". When I reset Samba on the printer host/server this message remains on the remote computer until I try to print again, then it clears.

Please let me know if this helps as I need to know if I have the same common problem (in which case it will probably get fixed by an update) or if I'm on my own (in which case I need to do further investigation).

---

### Post by Chonnawonga on 2009-11-07
The problem may not be with Samba. I can't seem to print over USB to an A940 after upgrading to Karmic. Has anyone else tried connecting directly?

---

### Post by KMilburn on 2009-11-08
SteveDee - Yes you were right!   Thank you
What I changed was removing the ; in the line ;   printing = cups

My installation was a clean install.  In my network of WinXP and Ubuntu 9.10 I can print from XP to Ubuntu and share in both directions.

Thank you again.

---

### Post by hoovie on 2009-11-19
thanks! removing the ";" worked for me as well

---

### Post by holmes1412 on 2009-12-08
but, that's not working on my laptop. Because, after restart, ";" still appear. I already check it after found that I cannot print, similar as before :(

---

### Post by dpcreel on 2009-12-21
see: [http://ubuntuforums.org/showthread.php?t=1342181](http://ubuntuforums.org/showthread.php?t=1342181)

this solved my problem

---

### Post by amazed1963 on 2010-01-26
My Mac now prints to a printer plugged into a  Machine running Ubuntu 9.10
 

 After MANY missteps, I followed these steps and the printer finally started to work using CUPS and the setup above.  As a relative noob to Ubuntu and Linux, I don't know which of these steps were the magic ones that worked.  It is likely that some of these steps can be changed or omitted, but they worked for me, and hopefully, for you as well.  
 

 Printer attached to the parallel port on the Linux machine was installed, running, and set to shared over the local network from CUPS ([http://localhost:631]("http://localhost:631/")[ typed into the firefox location bar]("http://localhost:631/")).
 

 On the Linux machine, I ran ifconfig from the terminal app. to discover the local IP address (starts with 192.168.xx.x)  (Your xx.x will be different numbers).
 

 From the Mac's Safari program's location bar, I went to the url of the Linux machine's CUPS port 631 (192.168.xx.x:631) where xx.x are numbers for the local address discovered using ifconfig above.
 

 This brought up the CUPS system on the Linux machine (which was displayed on the screen of the Mac machine).
 

 I then went to the printers tab on the Linux machine (through safari on the Mac) and copied the location for the printer onto the clipboard ([http://192.168.xx.x:631/printers/Hewlett-Packard-HP-L]("http://192.168.xx/")aserJet-1100).
 

 I then opened port 631 on the Mac machine ([http://localhost:631]("http://localhost:631/")) which brings up the CUPS system on the Mac.  (If it doesn't bring up the Mac CUPS system, you will need to figure this out first).
 

 I went to Add Printer on the Mac CUPS system.
 

 On the Mac, I gave the added printer a name of HP_LaserJet_1100 and “cut and pasted the location into both the location and the description fields.
 

 For device I used IPP or internet printing protocol (http).
 

 For Device URI, I pasted the location copied from the Linux machine yet again.
 

 I selected the proper make and model for the driver on the next screen.
 

 Worked!  Hopefully this saves someone else the hour or two it took me to thread that needle.

---

### Post by pdc on 2010-01-26
well done! great work!

---

