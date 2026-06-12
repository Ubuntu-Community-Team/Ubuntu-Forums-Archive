---
title: "networking basic printer"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by jim allAn on 2010-03-15
I will start from the begining as that is where my knowledge is.  My son has a canon mx 860 multi function printer on our lan.  How should it be connected?  Should it be directly to the administrators system or through some print server maybe.  He is running win 7 of which I know nothing.  I am running win xp pro/Ubuntu 9.10.  I was communicating with his system when it suddenly quit.  That was in xp pro.  I can no longer find him.  I tried Ubuntu and found him right away.  I tried setting up a new printer and it looks like it hears what I am saying.  I had to choose a driver which is on the printer and I think it installed.  I get the printer and driver icon and can get the cue list.  The jobs are there but so far no printing.  Where should I start looking?  I may not be using the correct driver.  I here the drivers are with the kernel, but I know nothing about that.  There is a long list of drivers in that printer.
   For future reference, is there a spell checker here and where?

---

### Post by RyanRahl on 2010-03-15
Is the printer hooked up directly to the network or is it shared through another PC?

If it is hooked up to another PC and you are having a hard time seeing it (happens a lot with win7) simply type the network address (\\winpcexample\printersmbname) of the samba share into nautilus and it should pop right up for install.

If it is directly hooked up to the network make sure you give it a static IP and then set up an LPD/LPR port through either your printer administration menu or directly editing your cups configuration on your PC to connect to it. Then obviously choose the correct driver for it, if your manufacturer does not provide linux drivers then windows .ppd files will work a lot of times as they are just standard postscript.

also check your firewall to make sure your LPD port (515) or raw port (9100) is not blocked

---

### Post by jim allAn on 2010-03-16
First I went on the assumption it is hooked to the administrators pc with win 7 OS.  I can't remember if nautilis is a web browser or file browser.  In either case I don't believe I have it.  I have seen no mention of it since I have had this system.  I tried a couple places in a file search and did not find it.  I also tried it in my firefox bowser and did not find it.  Last I tried finding it on administrators system through the lan connection and still did not find it.  I guess I will have to go down there and see where it is hooked up.  Having not found it I am guessing it is hooked up differently.  His wife doesn't like to see me looking at things like that even though I have ten times sons experience and knowledge in PCs. If it is hooked up direct to the network then I will need a lot more help to get through it.  I didn't have any luck back when I was trying to network my two PCs with a switched pair cable and no router.  You probably know that requires static IPs as well.  I know what you are talking about but not how to implement it in Ubuntu.  If it matters I think I can see the router in windows.  It has a strange name and options to "invoke it" rather than connect.


> **RyanRahl said:**
> Is the printer hooked up directly to the network or is it shared through another PC?

If it is hooked up to another PC and you are having a hard time seeing it (happens a lot with win7) simply type the network address (\\winpcexample\printersmbname) of the samba share into nautilus and it should pop right up for install.

If it is directly hooked up to the network make sure you give it a static IP and then set up an LPD/LPR port through either your printer administration menu or directly editing your cups configuration on your PC to connect to it. Then obviously choose the correct driver for it, if your manufacturer does not provide linux drivers then windows .ppd files will work a lot of times as they are just standard postscript.

also check your firewall to make sure your LPD port (515) or raw port (9100) is not blocked

---

### Post by jim allAn on 2010-03-17
While I didn't actually see the printer connection, common sense told me the modem only had it's needed connections and the router only had three besides the wireless.  One for input and one for my son and the final one for me.  I tried the smb name Idea but it didn't show up.  I need to try it again and any other ideas that pop up.

---

