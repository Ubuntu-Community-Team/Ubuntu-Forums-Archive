---
title: "Samba printer share with XP"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by the mole on 2010-11-16
My desktop is now dual boot, Xubuntu 10.10 has been added to WinXP. The attached parallel printer works fine with either OS. When running XP I can share the printer with my two XP laptops without problem.  I cannot share it when the desktop is running Xubuntu. Neither laptop can see the printer. However, if I open the desktop Samba config application, change any parameter, retype in the original parameter, both laptops can see and connect to the shared printer - until I reboot the desktop!
Any help would be much appreciated.

---

### Post by Morbius1 on 2010-11-16
It sounds like cups is starting after samba starts. See if this fixes it:
[http://ubuntuforums.org/showthread.php?p=10071367#post10071367](http://ubuntuforums.org/showthread.php?p=10071367#post10071367)

---

### Post by the mole on 2010-11-16
thanks Moribus1

I tried your suggestion but it did not fix the problem.
I also tried adding "sleep 10" to smbd.conf (and nmbd.conf) but no luck.

---

### Post by Morbius1 on 2010-11-16
I wonder if nmbd is running.

When you first boot into the system run:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```After it starts run the following command and see if it lists the printer:
```
smbtree
```If manually starting nmbd fixes it then you can add a script to start nmbd only after the network is up: [http://ubuntuforums.org/showpost.php?p=9724879&postcount=8](http://ubuntuforums.org/showpost.php?p=9724879&postcount=8)

---

### Post by the mole on 2010-11-16
nmbd is running
smbd is running
smbtree does not lists network items but not printers.

nmbd restart
smbtree still does not list printers

smbd restart
smbtree lists printers!
WinXP can now see the printers!

reboot - no printers available again but the above works reliably (well, I did it 5 times)

---

### Post by the mole on 2010-11-16
oops, line 3 of my reply should read
smbtree lists network items but not printers.

---

### Post by the mole on 2010-11-17
Back to square one this morning.
I repeated the tests of yesterday and got different results!
None of the restarts resulted in smbtree showing my shared printers.

The only thing that works reliably is to enter the samba server configuration tool, type in a new value for ANY parameter, retype in the original value and exit the tool.
smbtree then shows the shared printers!
There must be a clue here.
I have tried all the other possible fixes Morbius1 indicated but no luck yet.

---

### Post by Morbius1 on 2010-11-17
I've got one more. When you go into the Samba GUI and make a change the last thing it does is restart smbd. It's possible that on your system smbd is starting before the network is up.

Create a little script:
```
gksu gedit /etc/network/if-up.d/samba
```With this content:
```
#!/bin/sh
service smbd restart
```Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/samba
```Anything added to /if-up.d will be executed only after the network is up.

---

### Post by the mole on 2010-11-17
Morbius1, still no luck.
I assume I have followed your instructions correctly.

Run the first line in terminal, to open the existing file in a text editor (Mousepad - don't have gedit).
Copy the next two lines to the bottom of the text.
Save file.
Run the last line (sudo chmod..) in terminal.
Reboot.

---

### Post by Morbius1 on 2010-11-17
>  Run the first line in terminal, to open the existing file in a text editor (Mousepad - don't have gedit).Well that's the first problem. There shouldn't have been an existing  "samba" file at that location.

Remove the lines you added and post the contents of the samba file:
```
cat /etc/network/if-up.d/samba
```

---

### Post by jpl888 on 2010-11-17
I suppose sharing the printer through Samba is user friendly but you can connect to it directly through CUPS by using IPP at the client end. Nice how to with pictures at [http://howto.ccs.neu.edu/howto/printing/adding-an-ipp-printer-queue-to-windows-xp/](http://howto.ccs.neu.edu/howto/printing/adding-an-ipp-printer-queue-to-windows-xp/)

---

### Post by the mole on 2010-11-17
Morbius1, the file /etc/network/if-up.d/samba is attached as a text file - I hope.

---

### Post by the mole on 2010-11-17
jpl888, Yes I can access my printer using CUPS and an IP address but I want to access the printer in the same way as WinXP does.  As my desktop computer is dual boot (Xubuntu/WinXP) my two laptops (both WinXP) will only need one printer setting and will not care which OS my desktop is running.
Hope that makes sense.

---

### Post by Morbius1 on 2010-11-17
This is really getting complicated. The existing samba script appears to be a workaround for nmbd not starting in the correct sequence. 

I assume because of the the way the script was constructed that the first two lines are the ones you added?
> [COLOR=Blue]#!/bin/sh
service smbd restart[/COLOR]

#!/bin/sh
# Try to bring nmbd up when an interface comes up, if smbd is already running.
Delete the first two lines to bring it back to it's original state.

I suppose we could create another script called: /etc/network/if-up.d/smbdup

But we're getting an awful lot of patches and workarounds happening at the same time in there. If it were me I would try it but I can understand if your patience is running out with me.

---

### Post by the mole on 2010-11-17
Yes, the first two lines as the ones we inserted.

I don't know about the other stuff as this is a new (1 week) install of Xubuntu 10.10
In nearly a year of trying Ubuntu, Mint, PCOS, Fedora and some I've forgotten, this version of Linux is the most successful I have ever used.  I am certainly not running out of patience, your help has been magnificent and much appreciated.
It it worth installing a later version (or older) of Samba.  It is 2:3.5.4.  Is it worth trying another distro?
Let's try another script file first.

---

### Post by Morbius1 on 2010-11-17
I don't think that an older or newer version of samba is the answer. I still think it's a services starting in the wrong order or not running at all problem.

What I was suggesting was going back to my earlier post and creating the same script but with a different name:
Create a little script:
```
gksu gedit /etc/network/if-up.d/smbdup 
```With this content:
```
#!/bin/sh
service smbd restart 
```Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/smbdup
```Just remember to remove what you added to /etc/network/if-up.d/samba before rebooting.

EDIT: Oh, and make sure there isn't an existing /etc/network/if-up.d/smbdup

---

### Post by the mole on 2010-11-17
Now have two scripts, the original samba and the new smbdup.

Printer situation still the same.  Shared printer not seen.
Work-around - go in/out of Samba configuration app - still functions.
Meanwhile I have configured Samba to share files to my XP laptop and vice-versa.
This was painless.  I can now transfer files in both directions.

---

### Post by Morbius1 on 2010-11-17
I'm out of ideas on the printer problem. It sure sounds like cups is starting after samba starts and I have first hand knowledge of this problem because it happened to me. 

The edit to /etc/init/smbd.conf I linked to earlier ( [http://ubuntuforums.org/showthread.php?p=10071367#post10071367](http://ubuntuforums.org/showthread.php?p=10071367#post10071367) ) fixed it for me but clearly it does nothing for you. I just don't know. Sorry.

---

### Post by the mole on 2010-11-18
Morbius1, I'll go through all the fixes on your link again, very carefully.
At least I have a work-around.
It may take a software update or a change of distro, who knows, but I'll post the fix when I find it.
Many, many thanks for your help with this problem.  As I am fairly new to Linux I am sure we will speak again on this forum.

---

### Post by the mole on 2010-11-19
Tried all the fixes again with the same results - nothing.

Then removed Xubuntu 10.10 and installed Ubuntu 10.10.
Same problem!
Tried the first fix from Morbius1 (edit /etc/init/smbd.conf; changed line "stopped on local-filesystems" to "stopped on local-filesystems and stopped rc*)
**Viola!! it worked.**
So, why does the fix work in Ubuntu but not in Xubuntu ?

---

### Post by Morbius1 on 2010-11-19
Well that's interesting. I wouldn't have thought that the desktop environment would have any impact on these service starting at boot. I don't have enough experience with XFCE to know why it would be different than with Gnome since at that level the two should be virtually identical.

---

### Post by the mole on 2010-11-20
:)Ah Ha.
Put Xubuntu back, modified smbd.conf as above, and it worked.
Rebooted and no printer shares !
Rebooted and it worked. etc. etc.
Then I noticed something.  About 50% of boots are accompanied by a notice "A program is still running - Xfce power manager is not responding" just after entering my password.  If the notice does appear, it goes after five seconds and seems to have no consequencies.  But when that notice does appear, I have no shared printer in my smbtree.  When the notice does not appear, I have shared printers.  I have confirmed this over 25 tries.
This notice appearing is a known bug, #563862, but there are no reports of it being associated with my problem - I'll add my troubles to the bug list.

---

### Post by tranbo2@yahoo.com on 2011-09-13
Thanks..this explained the problem I'm having ...but I'm on 11.04 xUbuntu now:popcorn:

---

