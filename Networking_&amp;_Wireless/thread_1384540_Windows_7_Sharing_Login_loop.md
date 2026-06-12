---
title: "Windows 7 Sharing Login loop"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by shill88 on 2010-01-18
I'm trying to setup a network between 2 Ubuntu 9.10 machines and 1 Windows 7 machine. The windows 7 machine can access both Ubuntu machines without problem. However when trying to access the Windows 7 machine from either Ubuntu machine it asks for a login and password. I enter my login and password that I use on the Windows 7 machine and it loops back asking for a login and password again. Does anyone know what may be causing this.

Thank You

---

### Post by johnson.d on 2010-01-19
This problem may arise when,

1) Permissions are not set for the shared folder to the particular user you are trying to login as.
2) Wrong Entry of the Login credentials
3) If the windows machine is a part of a AD Domain, the Domain name is needed to be entered correctly.

Please cross check the above and let me know if it helps.

---

### Post by shill88 on 2010-01-31
Solved the problem by removing Windows live sign in assistant per the following [Post]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527"). Hope this helps others with the same problem.

---

### Post by dlabelle11 on 2010-02-01
didn't work for me

---

### Post by dlabelle11 on 2010-02-01
didn't work for me

but I guess this leads me to beleive its something in win 7 blocking me out

---

### Post by dmizer on 2010-02-02
See if this post will help: [http://ubuntuforums.org/showpost.php?p=8713204&postcount=2](http://ubuntuforums.org/showpost.php?p=8713204&postcount=2)

---

### Post by dlabelle11 on 2010-02-02
Sweet its working thanks for your support.

I think re-login both computers might of helped a bit after adjusting the advanced sharing settings and just really watching what the settings say in the advance sharing options because I had to make changes multiple times to them after re-logging, maybe because when you change the public settings it also changes some of the home or work setting too.  Just something for others to watch out for.  I 'm also only sharing the public folder as oppossed to all three of my drives like I had it before, so maybe that also had a little something to do with it. Thats pretty much all I did other then update ubuntu to get it working although I did uninstall windows live sign in assistant and some other windows live stuff.

Once again thanks for the help,  I can't beleive it was windows causing the problem all along, microsoft is probably creating this problem on purpose to drive ubuntu users crazy, lol.  Like my windows computers were sharing with each other without any problems.

Im pretty sure windows 7 is using workgroup "WORKGROUP" as default, although I forget where I saw it.

Thanks

---

### Post by dlabelle11 on 2010-02-02
Ho do I share something with ubuntu from windows other then the share folder... thanks in advance.... While I wait for a reply I'll look throiugh the maze for an answer I know I saw it somewhere

---

### Post by dmizer on 2010-02-02
> **dlabelle11 said:**
> Ho do I share something with ubuntu from windows other then the share folder... thanks in advance.... While I wait for a reply I'll look throiugh the maze for an answer I know I saw it somewhere

I am not sure what you mean by this question. If you want to share another folder, just go to a folder, right click on it and select "Properties". Then click on the sharing tab, and configure it the same way you did your other shared folder.

---

### Post by dlabelle11 on 2010-02-02
oh ok I though I read a comment of yours on enother thread something about only being able to read the public folder in your windows computer from the linux computer... I must not of read it very well.

Its enother drive on my windows seven desktop and I get the error can't mount location... once again I blame ubuntu..lol...

---

### Post by dmizer on 2010-02-02
> **dlabelle11 said:**
> oh ok I though I read a comment of yours on enother thread something about only being able to read the public folder in your windows computer from the linux computer... I must not of read it very well.

Its enother drive on my windows seven desktop and I get the error can't mount location... once again I blame ubuntu..lol...

Are you trying to share the whole drive? If so, take a look at the Vista specific information in the 6th link in my sig.

---

### Post by dlabelle11 on 2010-02-03
That's what I was looking for but sadly it's not going to solve my problem like I though it would. I'd rather not have this shared folder on the primary drive, that might be the only thing stopping that fix from working for me.  I'm thinking of taking a closer look at the folders setting in windows that I want to share.

Any suggestions would be appreciated.  Thanks again.

---

### Post by dmizer on 2010-02-03
> **dlabelle11 said:**
> That's what I was looking for but sadly it's not going to solve my problem like I though it would. I'd rather not have this shared folder on the primary drive, that might be the only thing stopping that fix from working for me.  I'm thinking of taking a closer look at the folders setting in windows that I want to share.

Any suggestions would be appreciated.  Thanks again.

Just to be double sure, you read this correct?

> **dmizer said:**
> If your trying to connect to Vista or Win7, you will not be able to connect to any UAC protected drive/directory. Because of this, sharing entire drives will not give you access (unlike it did in XP). Believe me when I say ... this is a very good thing. You don't want your entire system hanging out there for all to see. It's possible to override this protection but I wouldn't advise it.

Instead, share a single folder that your Vista user has control over. If you want an entire drive to be dedicated to sharing, then share the first folder on the drive and put everything else inside it like so:

D:/ddrive-shared/Music
D:/ddrive-shared/Movies
D:/ddrive-shared/Pictures
D:/ddrive-shared/Documents
D:/ddrive-shared/Other
etc 

More information here: [http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)
Related Ubuntu discussion here: [http://ubuntuforums.org/showthread.php?t=1176221](http://ubuntuforums.org/showthread.php?t=1176221)

---

### Post by dlabelle11 on 2010-02-05
ok enother problem solved, thanks, was a simple win 7 folder property keeping me out...  so I just went to properties and then the security tab and then I just had to hit edit and add everyone...

---

