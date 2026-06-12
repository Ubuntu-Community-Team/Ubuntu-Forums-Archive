---
title: "Can't Access Windows 7 Shares on Ubuntu 10.10, but can do vice versa"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by nickdr on 2010-12-07
Ok this is a really weird issue because of the way it played it out. I have been researching it off and on for weeks now trying to figure it out and have come up with nothing.

Basically when I first installed Ubuntu 10.10 (64 bit) I was able to access the shared files on my Windows 7 (64 bit) computer perfectly once I changed the domain name in Samba. However I wasn't able to access my Ubuntu shares from Windows 7. After researching for a while to figure that out, I found this:

[http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

Boom! Instantly I could access my Ubuntu shares without a problem from Windows 7.

However after I did this something happened where I could no longer access Windows 7 files from Ubuntu. Unfortunately I am not sure if the change happened immediately or some time later.

When I go Places > Network I see the name of my Ubuntu computer (Living-Room) and my Windows computer (Nick-PC) as well as a folder called "Windows Network." When I open Nick-PC it brings up a dialog box saying a password is required. There are three text entry fields and a couple option:

Username: Nick
Domain: NRAU
Password: [not filled in]
_ Forget password immediately
_ Remember password until you logout
_ Remember password forever

The password field has to be filled in and I have tried every option. Each time it thinks for a second and then just pops the same dialog box again.

Please help me, this has become quite the thorn in my side. Let me know if there is any more information needed.

Note: Computers are wired.

---

### Post by nickdr on 2010-12-07
Update: Borrowed my friends computer which is also running Windows 7 64 bit. I could access his shares without any problems.

On the plus side, I guess this tells me there is an issue with the settings on my Windows 7 computer, and not with Ubuntu. On the downside, it is frustrating because it leads me to believe that its the settings I changed to make Windows to Ubuntu work.

Errrrrrrr......

Hopefully this will make sense to somebody.

---

### Post by xflbret on 2010-12-12
i am having an identical problem. i have a win 7 32 bit box and a win 7 64 bit box. i can get into the 32 bit box just fine. no matter what i try i can get into the 64 bit box. ssame as original poster...enter my password wait for a second and reasked for the password

---

### Post by nickdr on 2010-12-12
Can you go from your W7 boxes into Ubuntu shares?

---

### Post by grizz46 on 2010-12-22
I am having the exact same problem. The login box just keeps popping up even when I enter the correct details. Tried a lot of things but nothing worked so far. Anyone ?

---

### Post by mordanda on 2010-12-23
+1 for this.  Exact same issue.  For me everything worked great until I swapped out my router on Sunday.  After that all three of my Ubuntu machines do the never ending prompt thing, but my Mac can access the Windows 7 shares without issue.

I hope someone out here has a solution.

---

### Post by Nicolice on 2010-12-29
Have to "uninstall" the Windows Live Sign-in assistant on the windows 7 ...this fixed mine tho...

---

### Post by PatchesTheCaveman on 2010-12-29
Windows Live Essentials makes a small change in the way Windows 7 communicates via SMB that breaks the version of Samba included with Ubuntu.  While the Samba developers have already fixed this problem, Ubuntu has not yet shipped this new version.

So you will have to uninstall the Windows Live Sign-In Assistant until Canonical releases an update.

---

### Post by vibrunazo on 2011-01-07
I have the same problem getting the dialog asking for password when trying to access a windows 7 machine from ubuntu. But there's no such thing as Windows Live Sign-in Assistant to uninstall on the add/remove programs page.

What else could it be?

---

### Post by zenoran on 2011-01-07
Same problem here...

I've spent about 6 hours nonstop trying to troubleshoot this.  I've gone through every thread and tried everything suggested but still no luck.

I am able to access samba shares from win7 but the password box keeps popping up when I try to authenticate to a win7 share.

I'm on 10.10 and win7 x64

edit:  okay now that's weird... no windows live crap showed up in my programs but after a restart windows live id assistant showed up... uninstalled and works fine now.  bleh.  thanks microsoft for wasting my day!

---

### Post by PatchesTheCaveman on 2011-01-07
vibrunanzo:  Apparently it doesn't appear seperately from Windows Live Essentials.

However, there is another workaround described here:
[http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

---

### Post by gigaferz on 2011-02-19
thank you guys, i was soo close just to forget about it,well its been about 3 days.

well on to the next........thing....

---

