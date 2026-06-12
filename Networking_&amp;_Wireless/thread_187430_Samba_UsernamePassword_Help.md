---
title: "Samba Username/Password Help?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by TuXethic on 2006-06-03
I have switched my desktop os to ubuntu =) I got everying working fine. I can connect to my shared folders from ubuntu laptop to ubuntu desktop. But I cant connect to my ubuntu desktop from my windows laptop. It asks for the username and password all ways. What should I do? Please help!?

---

### Post by nikolokolus on 2006-06-03
[QUOTE=TuXethic]I have switched my desktop os to ubuntu =) I got everying working fine. I can connect to my shared folders from ubuntu laptop to ubuntu desktop. But I cant connect to my ubuntu desktop from my windows laptop. It asks for the username and password all ways. What should I do? Please help!?[/QUOTE]

the Wiki [here]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29") is a great starting point for setting up a basic samba server.  You'll want to pay close attention to setting up user accounts that are permitted to access your shares.  In a nutshell you'll either need to add a "guest" user account to your linux box and add it to your /etc/samba/user file or add your normal ubuntu account to /etc/samba/user.  Once you've added the user account you'll need to run 'sudo smbpasswd' and setup a password for your user accounts (just remember you need a real linux user account and not some username made up on the spot).  

It's been awhile since I've done this, but I seem to recall that username format for windows will be something like \"Ubuntuhostname"\"username" or "username"@"ubuntuhostname"  (obviously, you will use whatever username and hostname you have for your linux computer and **not** the generic entries I put in quoatations)

Ps. there are other wiki entries for samba that might be worth checking out if the above doesn't solve your problems.  Good luck

---

### Post by blackjack6.21.91 on 2006-06-03
If your smb.conf files are exactly the same except for the shared files part, everything should be fine

---

### Post by Ray100 on 2006-06-03
I hope no-one minds but I'm going to hijack this thread to save starting another one with the same questions.

I'm running two XP boxes and one Dapper. All of them are folding and I have Electron Microscope set up on my main XP box.
As of yesterday all was well, I was able to connect with Ubuntu and get the folding info. Today it doesn't seem to want to work for me, I keep getting asked for a username and password to log in to Ubuntu.
If I try and login from Ubuntu I get asked he same thing to login to mshome.

I read the Wiki, but Dapper seems to be a little different in it's setup so I got nowhere with that. I feel like I'm going in circles, this network stuff is all new to me, with Windows I've never had to bother around with it much.

I would really appreciate any help that I can get, and be prepared to simplify things for me :-? 

Ray

---

### Post by s31523 on 2006-06-03
> All of them are folding 
Huh?

What exactly are you trying to do?  Use Nautilus to browse to a Samba share someplace? (This may be a problem, I think Nautilus is screwed up see [http://www.ubuntuforums.org/showthread.php?t=186393](http://www.ubuntuforums.org/showthread.php?t=186393))

Some general hints:
Make sure the Windows domain name is the same in your smb.conf that it is on your windows machines.

Make sure your windows machines are shared out.

---

### Post by Ray100 on 2006-06-03
[QUOTE=s31523]Huh?

What exactly are you trying to do?  Use Nautilus to browse to a Samba share someplace? (This may be a problem, I think Nautilus is screwed up see [http://www.ubuntuforums.org/showthread.php?t=186393](http://www.ubuntuforums.org/showthread.php?t=186393))

Some general hints:
Make sure the Windows domain name is the same in your smb.conf that it is on your windows machines.

Make sure your windows machines are shared out.[/QUOTE]

Sorry I should have been more explicit, Folding@Home is part of a distributed computing network for Stanford University. I have a viewer on my main XP machine that lets me see the other machines work progress.

I just can't gain access over the MShome network to the Ubuntu machine now, it keeps asking me for a password that only it knows](*,) 

I read the other post and started to try the fix that was suggested, but I got stuck at the end with names of servers and such, I'll go try again and make note this time and I'll post back here with questions.

Ray

---

### Post by Ray100 on 2006-06-03
Ok, got it working from here

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

Ray

---

### Post by zantos1 on 2008-02-08
This worked for me. 

sudo smbpasswd -a *user*

---

### Post by linuxisfree on 2008-02-08
This might help.
 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows)

---

