---
title: "Failed to mount Windows share problem"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by ZenecadE on 2010-11-09
Hi.
I have been searching, re-installing and swearing for weeks.  I CAN't access Windows shared on the domain network.  This is NOT limited to the domain either as regular Windows shares give me exactly the same message 'Unable to mount location.  Failed to mount Windows Share.'  I can see every single shared folder but I can't for the life of me open it.  I have tried Ubuntu 10.10; 10.04 and 9.04 to no avail.  I also tried Linux mint 9 with the exact same problem  SuSE on the other had accesses every folder out the box but the entire system is dog slow and I can't get the proprietary nvidia drivers to work.  I can create shares that are accessible from a Windows computer on the linux machine but not other way round.  I have tried scripts, praying, denying sex, kicking the computer and a host of other things but still can't get this bleeding message to go away and the folder shares to open.  Can somebody PLEASE hold my dreary stupid wrinkled little hand and walk me through this before I smash this computer to bits?  I'd rather sit with a broken computer than use Windows.  
Oh, and BTW, I have searched for this topic and tried EVERYTHING i can find on this particular problem for weeks so please don't tell me to search.

---

### Post by ZenecadE on 2010-11-09
Seriously, nobody willing to help?

---

### Post by ZenecadE on 2010-11-09
I can get the printing to work without any problems.  It actually allows me to type in my username and password but the opening of Windows folders is still not working.  

Please somebody help.

I'm connected via wired LAN and am using Ubuntu 10.10.  What other details do you need??

---

### Post by ZenecadE on 2010-11-09
Oh come on.  Somebody please help me.  I'm almost positive I'm the only person on the planet that can't solve this issue.

---

### Post by ZenecadE on 2010-11-09
Okay, I've noticed this.  If the share ends with a $, it will ask for a username and password to access.  After entering the details, I can access that share but still not the others.  So in other words, It needs to have the $ then I know it will open  Heaven only knows what $ means besides money.  

Do any of you have ideas now?

---

### Post by luvshines on 2010-11-09
You look in some real trouble here :)

AFAIK, $ in the end is for admin logins to shares(haven't tried non-admin logins with these ones)

Just to get some better logs/ideas:
1. Are you trying to create password-less shares ?
2. What version of windows is it on the other side ?

Can you list the shares from terminal```

smbclient -L <windows-ip> -U<username>%<passwd>
```

What error does it give while accessing```

smbclient //<windows-ip>/<share-name> -U<username>%<passwd>
```

---

### Post by ZenecadE on 2010-11-09
Yipee!!!  Finally a saint!  

It's in the office where I work so there are access permissions for most folders.  But there are other folders used in collaboration with other people that don't have specific permissions and those are the ones I can't access.

The Windows machine with the shares is Windows Server 2003 SBS.

The first command you gave lists what I pasted below.  The second command gives me access to the desired folder :D  

This shows that something somewhere is working and neither me, nor myself have a cooking clue what I'm doing wrong.  However, I'm positive you are my saviour!

---

### Post by luvshines on 2010-11-09
Ok, so command line is accessible

And GUI is giving issues :(, bad it doesn't give proper error messages and stumps me all the time

Can you connect to windows by places->connect-to-server ?

When you try to access those shares, it must be asking for username/password. There do you provide the same username/password

Also, try accessing it by smb://<windows-ip>/<share-name> in nautilus

I am sure you will be able to access it by mount command as well

PS: You can remove the huge list you have posted in the previous post :), since it is accessible and gave no error messages

---

### Post by ZenecadE on 2010-11-09
YOU ARE A GOD!!
Oddly, I have tried all the methods you have listed but now i tried with a small difference.  I selected connect to server then server type I chose Windows share.  The difference came in when I actually typed in the shared folder I wanted to access.  In this instance, and only this instance, it asked me for a username and password which after typing, I had access to the folder contents.  
Now with the folder open, I can add the password to my keyring and bookmark the share for easy access :D

You have solved the problem I been breaking my head on for weeks!!!  If you are in South Africa, lemme know so I can get you a case of beer!

---

### Post by luvshines on 2010-11-09
> **ZenecadE said:**
> YOU ARE A GOD!!
Oddly, I have tried all the methods you have listed but now i tried with a small difference.  I selected connect to server then server type I chose Windows share.  The difference came in when I actually typed in the shared folder I wanted to access.  In this instance, and only this instance, it asked me for a username and password which after typing, I had access to the folder contents.  
Now with the folder open, I can add the password to my keyring and bookmark the share for easy access :D

You have solved the problem I been breaking my head on for weeks!!!  If you are in South Africa, lemme know so I can get you a case of beer!

Gr8 to know that it worked for you :)

Have seen ppl reporting the same problem that shares are accessible by name directly, rather than connecting to machine first and then selecting. Looks that urs is a similar issue

Really happy that you have spared both your head and your PC from banging against each other ;)

And as far as beer case is concerned, I am a teetotaller :D
Cheers anywayz !!

---

