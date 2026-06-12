---
title: "terminal server client: connecting to remote computer"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by AlanInVancouverBC on 2008-12-12
I am using my IT's info in the client, which works as is in my other logon (WUBI with 8.04). But it doesn't work in my separate install of 8.04 on a different hard drive. I get the error message attached, which doesn't make sense to me. Help please!

---

### Post by cmnorton on 2008-12-13
I cannot read your thumbnail.

Can you connect to the terminal services host from a Windows terminal server client?

Are you using rdp://hostname as the address?

---

### Post by AlanInVancouverBC on 2008-12-14
I'm using RDP. I can use XP terminal and also my other ubuntu. It's this second Ubuntu that doesn't connect, using the same input, same root user, same target location, same everything (I think).

---

### Post by cmnorton on 2008-12-14
> **AlanInVancouverBC said:**
> I'm using RDP. I can use XP terminal and also my other ubuntu. It's this second Ubuntu that doesn't connect, using the same input, same root user, same target location, same everything (I think).

Is it that you cannot connect into the second Ubuntu system?

---

### Post by AlanInVancouverBC on 2008-12-14
No. It's that I CAN connect through my other log-on OS (also Ubuntu) and I CAN connect through my third log-on OS (XP). It's just this one, the isolated Ubuntu not the WUBI Ubuntu or XP, that I can't connect with.
As the first attachment shows, it seems to be saying that I am connecting to myself!

---

### Post by cmnorton on 2008-12-15
I am missing something as to how these three computers are hooked up and to what.

---

### Post by AlanInVancouverBC on 2008-12-15
We are talking about 2 computers. One at work, one here at home. The one at home has 2 hard drives. On the main drive, there is a WUBI dual boot: one to XP and one to Ubuntu. On the other drive, there is one boot: to Ubuntu. 

On the main drive, the Terminal Server Client works fine (on both the XP and Ubuntu logons). The problem is that, using (I believe) the same settings, the Terminal Server client is not working on the other hard drive (the other Ubuntu logon).

What would cause it to respond that I am trying to log onto itself?

Thanks for staying with me on this.

---

### Post by cmnorton on 2008-12-15
I am sorry for a predictable, perhaps lame, answer, but I'd look in /var/logs to see what's going on when you're logging in.

---

### Post by nixscripter on 2008-12-16
How is your WUBI Ubuntu install set up for the networking? I have a feeling that there's some sort of weird network translation going on behind your back.

---

### Post by AlanInVancouverBC on 2009-01-17
The delay was due to Xmas issues, staffing, etc.
It turns out that it appears that the program I have been using, Terminal Server Client, is corrupt. When I tried a different program, Gnome RDP, it worked.
Thanks for your help.

---

### Post by AlanInVancouverBC on 2009-01-17
Thanks

---

