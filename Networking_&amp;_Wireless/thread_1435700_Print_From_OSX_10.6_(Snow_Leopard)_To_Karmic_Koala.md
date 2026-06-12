---
title: "Print From OSX 10.6 (Snow Leopard) To Karmic Koala 9.10"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by rotox on 2010-03-21
[FONT=Arial][SIZE=2]Hi,

I've just installed Snow Leopard and have had to set up my shared Ubuntu printers again. After a couple of frustrating attempts I Google'd and came up with an answer that worked really well - and it didn't involve editing anything on Karmic!

I have tested this procedure on my dad's OSX/Ubuntu setup and it worked for him, too. So follow this and it should work for you.

** On the Mac**
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2] Finder > Go > Utilities > Terminal[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2] Enter the following
[/SIZE][/FONT][INDENT]```
cupsctl BrowseProtocols='"cups dnssd"'
``` [/INDENT][FONT=Arial][SIZE=2]Quit Terminal[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]Finder > Go > Applications > System Preferences[/SIZE][/FONT][/INDENT][INDENT][FONT=Arial][SIZE=2]Internet & Wireless > Sharing
Enable Printer Sharing[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]Go back to the System Preferences main window[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]Hardware > Print & Fax[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]All of your shared Ubuntu printers should be displayed in the left hand window.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Click on each in turn and then select your Default Printer and set your Paper Size.[/SIZE][/FONT] [FONT=Arial][SIZE=2]You should now be able to print without any hassles.[/SIZE][/FONT]


[FONT=Arial][SIZE=2]Make sure that you do click on each printer in the Print & Fax window as I've noticed that they don't show up as a printer in the applications until you do!
[/SIZE][/FONT]


[FONT=Arial][SIZE=2]Hope this helps![/SIZE][/FONT]

---

### Post by UbMacMan on 2010-04-20
Rotox,

I can't thank you enough for posting your solution!  I spent nearly a full day on this problem and got nowhere.  I had suspected it was a browse protocol problem but could find nothing on Apple's web site about the changes between Leopard and Snow Leopard.  All my other Macs found my Ubuntu printers fine, but only SL had the issue.  

Anyway, thank you again!

---

### Post by vektoruk on 2010-04-22
Thanks for this! I've got 2 Leopard macs and 1 Snow Leopard mac in my office.

We were connecting to our ubuntu file server over NFS but needed to change to AFP.

This broke all the printers - I could get the Leopard machines to connect with AppleTalk compiled in Netatalk, but AppleTalk wasn't an option in SL.

This option has worked over all my macs :) Happy Days!

---

### Post by rotox on 2010-04-28
Hey, UbMacMan & vektoruk.

I'm glad that this worked for you! :D

It's frustrating having to figure out all of the new tweaks that Apple makes every OS update, but i guess that it keeps us on our toes! ;)

rotox

---

### Post by mlebaron on 2010-05-21
Worked for me too, although I didn't have to do the part about enabling printer sharing.

Thanks!

Apple owes me a couple of hours of my life back!

---

### Post by ninosp on 2010-07-24
Cant`t believe, after 1 day spent trying to make it work, thinking the problem was with my Ubuntu print server it was Apple fault..........damn you Apple.....lol.

I didn't have to do the part about enabling printer sharing too.

Thanks rotox!

---

### Post by Javierhermosa on 2010-08-18
Thanks a lot... another guy here spending hours not understanding why could I access CUPS in my Ubuntu machine from my SL machine... and not be able to actually "see" the printer in the Add Printer screen... Thanks a LOT!

---

### Post by rotox on 2010-08-19
mlebaron, ninosp, and Javierhermosa.

It's good to see that this info is still useful - it's also reassuring to know that I'm not the only OSX user that has issues every time Apple introduce a new update! :D
__

---

### Post by Javierhermosa on 2010-08-19
Yeah rotox... It was really useful. By the way, what does exactly do this command?

---

### Post by rotox on 2010-08-19
According to macosxhints.com all that command actually does is add the line 'BrowseProtocols="cups dnssd"' to the file /etc/cups/cupsd.conf. CUPS is disabled by default from 10.5 onwards and this just re-enables it.

Apparently you could just type ```
**cupsctl** BrowseProtocols=all
``` which would enable every browse protocol on your computer, however this may have unexpected effects.

---

### Post by steved27 on 2011-03-11
Just wanted to say thank you!  I lost a whole day trying to get this work before I found this thread, and then I was happily printing in 5 minutes!  :D

---

### Post by JoeHay on 2011-04-05
Cheers rotox! I have been banging my head against a brick wall for the last two weeks trying to get this fixed. Your command worked first time! Superb!

Can't thank you enough.

Cheers 

Joe.

---

