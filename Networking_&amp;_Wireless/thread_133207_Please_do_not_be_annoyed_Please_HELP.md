---
title: "Please do not be annoyed Please HELP"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by Neomor on 2006-02-19
Hi.  I will admit to being totally clueless but I am trying my best.  I just installed Ubuntu 5.10.  Trying to get my Dell 1450 Wireless UBS 2.0 Adapter wireless working.   Found what looks like an awesome HOW TO from jonny on these forums.  Problem is, I am too clueless to even follow the seemingly very step-by-step HOW TO.  Will someone please take a few moments to walk me through it.  Here is how bad it is:

Step 1 is to copy a couple of files, bcmwl5.inf and something else to the desktop.  I went to go do that and realized--I can't find those files and would not know how to copy them if I did.

Please do not make fun of me!  Please help.  How do I find and copy these files?

---

### Post by Jedeye on 2006-02-19
could you send a link to the guide so we will all be on the same page.

---

### Post by Neomor on 2006-02-19
Maybe I should have posted this in the "Total Beginner Talk" forum.  Sorry!  If someone will tell me how to move the thread, I will.

---

### Post by atomicmoose on 2006-02-19
A mod will probably have to move your thread if that is what you want.

---

### Post by Neomor on 2006-02-19
Thanks for the reply.  Here is the link to the HOW TO that I am trying to follow:

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=1450+wireless+dell](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=1450+wireless+dell)

---

### Post by Jedeye on 2006-02-19
ok... the files you are confused about finding to copy to your desktop > 1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop those are the drivers from windows... so if you are duel booting you can go back to windows and find possibly find them and as jonny said > Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON) if you dont have windows installed anymore you could try searching the internet for your drivers... 

anyway let us know how that part goes for you.

---

### Post by Neomor on 2006-02-19
OK I found the files.  I copies them.  I followed the rest of the HOW-TO.  It is still not working....  When I open "Networking" the wireless doesn't show up at all.  I don't know what to do now?

---

### Post by joshuapurcell on 2006-02-19
so you found the Windows drivers and copied them. I'm assuming you copied them over to a CD or a shared partition accessible from your Ubuntu install. What step did you make it to in the how-to you are following? What is the step you are first seeing problems with?

---

### Post by Neomor on 2006-02-19
So, now I can tell that I have installed the drivers in ndiswrapper.  At least, I can see them when I am in "Terminal" mode.  But the computer does not seem to associate the drivers with the device.  When I go to "Networking", the wireless doesn't show up.

So, in the how-to, it all breaks down around step 4 or 5.

---

### Post by Jedeye on 2006-02-19
did you make sure to enable the repositories needed? it was step 2
> 2. Follow the advice given here under [How to add extra repositories]("http://ubuntuguide.org/#extrarepositories")

EDIT:
Ok so this is not the problem ;) I am just slow at the post today - everybody has been edging me out

---

### Post by StageMgr2Stars on 2006-02-20
Find a different driver with the same chipset. The one I downloaded off the site for my Dell 1370 said everything was installed and the hardware was there, but would never show up in networking either. Whats your chipset?

PS: Dell sucks

---

