---
title: "Win7 and Samba server share"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Forbees on 2010-01-11
so i found an older computer i want to play with as a file server

ubuntu server edition, installed gnome GUI (to make things easier for now, i plan on removing it later) and used [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+for+noobs]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+for+noobs")
to configure my 1.5tb harddrive so my windows machines can access it

i had everything working but than a fatal crash made me start from scratch (os and all)

now i am unable to access the samba share from a machine running windows 7, but i can access it from a machine running windows XP using the same login and password i set up for windows 7

this makes me believe it's a problem with windows 7 and not samba . .

any input? i'm out of ideas

---

### Post by changingstate on 2010-01-12
I'd be completely unsurprised if microsoft have been playing with their SMB implementation, yet again, in windows 7. It seems like they do this with every single release of windows. Cynical minds might suggest it was to deliberately break compatibility with samba and similar tools. 

Still, if you have a look in /var/log/samba/smbd.log and /var/log/samba/nmbd.log you might find something to shed light on the situation.

---

### Post by Forbees on 2010-01-12
both log files are empty . . . .

---

### Post by obimeister on 2010-01-12
Windows 7 has forced encryption on samba traffic. You need to disable it from local security policy, go to (on your windows machine):

control panel -> administrative tools -> local security policy

There find folder

local policies -> security options 

And change following policies to following settings:

Network Security: LAN Manager authentication level: Set Send "LM & NTLM responses"

Network Security: Minimium session security for NTLM SSP based (including secure RPC) servers: Disable Require 128-bit encryption

---

### Post by Forbees on 2010-01-12
The LAN manager was blank so i changed it, and the Minimum security was already set up right

but still access denied . . . a friend sugested that Samba might be the culperate .. . maybe?

---

### Post by shortcut144 on 2010-01-12
I had this problem and I fixed it with changing the owner or the share on the server. To no owner and that way I couldn't get access denied.  But yes, it does make problems for security.

```
sudo chown nobody.nogroup *share-path*
```

---

### Post by Forbees on 2010-01-12
at this point thats getting very tempting. . . . but i like the idea of everyone having to login to geto  my files . . .

---

### Post by Forbees on 2010-01-13
well i'm reformating the OS on the "server" to see if that fixes it, since it was working the first time. hopefully i can mark this as solved soon

---

### Post by Forbees on 2010-01-13
yep, reinstalling the server OS fixed it . . .

---

