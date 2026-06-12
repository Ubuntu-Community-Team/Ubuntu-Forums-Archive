---
title: "Password required for Network Manager??"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by redb on 2009-02-26
I am new to the system.  I have the newest version of Ubuntu all updated I guess.  I have been using it for a few weeks and have loved it.  However, today I am getting this message when I start up my machine....

Enter Password for default keyring to unlock

The application 'Network Manager Applet' (/user/bin/nm-applet) wants access to the default keyring but it is locked.

I enter my wireless network pass-phrase and it.

How do I get it to stop asking me this?

Thanks,

---

### Post by jimbren on 2009-02-27
Did you change your password recently?

---

### Post by redb on 2009-02-27
I had reconfigured my linksys  router and installed a new wep security. 

I was also asked to change my password while trying to set up file sharing with I believe SAMBA yesterday.  I am a complete beginner and am trying to stay out of too much trouble.

---

### Post by linux6994 on 2009-02-27
I had the same trouble and looking at other posts I found that this worked:

Applications > Accessories > Passwords and Encryption Keys go to Passwords
the right click on Login, go to password. You will be able to then enter and remove the default password. I set it as the same as my login password then removed it. On the next reboot all was fine and it connected automatically.

---

### Post by redb on 2009-02-27
I tried what you had suggested but to no success. It is seahorse.

 I did notice in my Network Connections (wireless) that the VPN is locked??  I don't remember setting up a VPN.

---

### Post by robincawser on 2009-03-02
I'm running crunchbang linux, an ubuntu derivative, and was getting annoyed with this too.

The way to solve it is to go to User/Groups (or User Settings), press the unlock button and enter your root password, then go to the properties for your user, go to the 'User Privileges' tab and tick the item labeled 'Connect to wireless and ethernet networks'.

What this does is allow your user to connect to networks without root authentication. 
Hope this helps.

EDIT: Scrap the above. A better solution is to install 'wicd' from the repos.

---

### Post by neanderslob on 2009-03-06
Does anyone know what one should do if the option "Connect to wireless and ethernet networks" doesn't appear in user settings?  Of course I can connect once the password is entered but it's so damn annoying to enter two passwords on startup.

Regards

Sam

---

### Post by elitenoobboy on 2009-03-13
Why can't developers fix this? I've been having this problem for a while now, with nothing I've tried fixing it. If I don't put in a password and just hit cancel instead, another keyring window will come up, then another, then a wpa password dialogue. I have to hit escape SEVEN times before it will stop bugging me. This has been a problem for a while now. Why is it so hard for developers to fix this? Do they not care? Don't know how?

---

### Post by QwUo173Hy on 2009-03-13
> **elitenoobboy said:**
> Why can't developers fix this? Do they not care? Don't know how?

They may indeed not know. This has been a problem for me for a while but I've never reported a bug on launchpad. The developers rely on us to submit reports so they know what's a priority for the users of Ubuntu. If you haven't bothered to post a detailed bug report, then the developers will naturally assume that it's not that big a deal for you.

---

