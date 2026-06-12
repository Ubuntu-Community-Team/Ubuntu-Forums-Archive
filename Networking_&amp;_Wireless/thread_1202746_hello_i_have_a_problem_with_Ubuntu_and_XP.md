---
title: "hello i have a problem with Ubuntu and XP"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by Defo_ on 2009-07-02
Hello everybody, i have a problem. Here it goes :
1. A shared folder on my PC (win XP)
2. Made **direct** link in "UBUNTU pc"
3. Tested - all worked perfectly (and works)
4. So ze problem - when i not at home i told my perents to boot my PC (XP) to acess that folder. But it seems that ubuntu cant see that folder and my PC (XP), unless i put a password and loged in in windows XP. Normaly if there was 2 win XP pc`s there is no problem with this. And i noticed, ubuntu cant see win PC in network unless (xp user) is logged on. So there is my problem i hope u will understand my poor eng and help me with it. 

5. Thanks



Defo

---

### Post by computer13137 on 2009-07-02
I'd argue that it's not really a "problem" but rather a security feature getting in the way. :P

I tried to setup Samba on my Ubuntu box for printer sharing with Windows clients once, and gave up because I didn't want to bother circumventing the login policies.

However, correct me if I'm wrong other Ubuntu people - but if Ubuntu is the client machine, I don't see why it would access the Windows share any differently than Windows.  In other words, I don't think Ubuntu is the problem, I think the Windows machine has to be the one asking for authentication.  If you try to access it from another Windows box under the same circumstances, you'll likely find the same problem.

The best solution I can think of at the moment is to setup an account on the Windows box with a password you're not afraid to give out, that has access to the fileshares... then login with that on the Ubuntu box when you go to use the share.

-Kirk

---

### Post by Boondoklife on 2009-07-02
Well I can not say that I have had the issue where the XP box needs to be logged on, you could try setting up the share as admin inside the manage computer screen. This may make it available all the time.

what version of XP are you using?

---

### Post by computer13137 on 2009-07-02
> **maletek said:**
> Well I can not say that I have had the issue where the XP box needs to be logged on, you could try setting up the share as admin inside the manage computer screen. This may make it available all the time.

I've seen it happen between two XP boxes many times.  It seems to happen when there's only 1 account, it's an administrator, and it's password protected. :P  But generally there are permissions you can set too, for who has access.  If you give guests full (or read-only) access, it may stop asking for a login too.  That just occurred to me.

Be careful running a Samba share with too little security if your neighbors are using your network.  You should really slap a WPA key on your router.

(Wait, maybe I read that sentence in another thread - after reviewing your post I don't see the reference to that...my bad.)

-Kirk

---

### Post by Defo_ on 2009-07-02
Ok - thx for all advise. Security...nah i am using windows Firewall (defoult). And guest can acess my XP any time from intranet. BUT i noticed that UBUNTU **cant** see my XP pc untill i loget in. What do i meen by that - i boot bouth pc`s (xp waiting for password), and in UBUNTU system trying  to locate XP. It cant see it (in local network).. Well ill do more experiments tomorow. But for now, its a problem for me. I like them all is **Automated**.

---

### Post by Defo_ on 2009-07-02
> **maletek said:**
> Well I can not say that I have had the issue where the XP box needs to be logged on, you could try setting up the share as admin inside the manage computer screen. This may make it available all the time.

what version of XP are you using?

profesional sp3

---

