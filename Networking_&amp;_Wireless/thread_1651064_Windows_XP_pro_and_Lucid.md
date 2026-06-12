---
title: "Windows XP pro and Lucid"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Strategist01 on 2010-12-22
Hi guys.

So I just got a new PC with 2TB of HDD space and it's running Ubuntu 10.04.1 32bit. I have created a user for networking, called share and have created a folder within the home folder called public. I then shared the folder and gave 777 access to it as I want this to be public - but for my local network and my later for ssh access.

I have installed samba, and under the sharing options I allowed for guest logins and people to write and delete from folder. SO how would I be able to "see" this from my windows machine? It's running XP pro and it has a domain other than workgroup - but that shouldn't affect it should it?

Also, the laptop with XP is on the wireless with and internal IP of 10.0.0.135 and my PC is on the LAN connection with and internal IP of 10.0.0.1

I'm sort of familiar with networks, but I have NO clue as to how to do this.

Anything that could help would be much appreciated - thanks.
Strategist01

---

### Post by luvshines on 2010-12-23
To start with first make sure that your Samba sharing is working by first connecting to the share from the same Samba server :)
```

Places -> Connect to Share -> switch to windows share -> fill in the details and make see if it works
```

If it does, then go ahead and try from windows```

#In start->run type and fill in username/passwd when prompted
\\<Samba-server-ip>

```

If Samba share doesn't work from server itself, then try switching off firewalls (if they are on) and if that also doesn't solve it then post output of```

testparm -s

# And also
net usershare info
```

---

### Post by Strategist01 on 2010-12-24
Ok that worked! I just typed \\server_IP into windows explorer from the XP machine and I got the files! Thanks!

---

### Post by mastablasta on 2010-12-24
not even type any commands. what you need to do is to go to network neighbourhood and then find the linux computer there.
 
at least that was the case for me...

---

