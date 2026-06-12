---
title: "Missing folders from windows share."
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by cyberdomus on 2012-03-02
Running latest 11.10.

I have a windows 7 machine sharing music, videos etc.  One shared folder has about 60 subfolders in it.  When I connect to this share just simply by connecting to the server and browsing it, I only see about 30 subfolders.  However, I can go to "connect to server" and type in a subfolder that isn't visible, but I know exists, and it comes up.

So basically I just can see all the subfolders in my share.  This poses a problem as I intend on running xbmc and he needs to see all these folders in order to add to its library.

I have a macbook, and it too can only see about 30 subfolders.

Any workarounds, fixes, insight, reasoning?

Thanks,
Josh

---

### Post by dandnsmith on 2012-03-02
I cannot test this directly at this moment.
I can, however, see a shared folder with 120 sub-folders (and view the pictures within) from Ubuntu 10.04 and Mint11
Possibly it is to do with the Win7 networking and shares.

---

### Post by cyberdomus on 2012-03-02
Derek,
What machine is your shared folder on? Xp, 7, Linux?  I could move my share to another machine to fix this. 

Thanks,
Josh

---

### Post by dandnsmith on 2012-03-03
At my last post, the shares were on XP, but I've now checked it working on Win7.
I did find that it wasn't as easy to get the shares working with Win7, when I started Win7 just before Xmas.
HTH

---

### Post by cyberdomus on 2012-03-07
I tested with an xp share and it does indeed work.  I went back to my win7 machine and removed the "Homegroup" sharing and just used standard user/password sharing, and I'm still having trouble.  I'm also notice when I try to copy a large number of files from ubuntu/mac it only copies a fraction of the total... even after several attempts, then eventually I get a security error.   

I'm confident it the win7 machine's fault.  Next time I get around to re-installing windows, I'll see if it fixes it. 

Thanks for your help though.  If I do find the ultimate issue/solution, I'll be sure to post it. 

Josh

---

### Post by dandnsmith on 2012-03-08
That Homegroup sharing seems to be a snare for the unwary - only useful, as far as I could see from reading, for connecting to other win7 PCs. I set up my sharing without, since all the rest of my 'home group' uses XP or Linux.

In the past, Windows networking has made itself infamous for setting things up so you cannot reverse the effects easily, and often have to re-install to get to the desired state.

---

