---
title: "can't see Windows shares"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by JohnDillinger43 on 2012-01-05
I've tried a couple different things, but I can't seem to get my laptop (dual boot Win7/Ubuntu11.10) to see shares on my wireless Windows network.  The desktop with the shared drives is dual boot WinXP/Ubuntu11.10, and I have another laptop running just WinXP.  From Windows, I set up a network called HOME, and shared several drives on the WinXP/Ubuntu machine.  My WinXP laptop can access these drives (regardless of whether the desktop is booted in WinXP or Ubuntu), but my Win7/Ubuntu laptop can only access the shared drives in Win7, not in Ubuntu.  At this point I'm pretty well switched over to Ubuntu, so I probably wouldn't mind creating a new network just for Ubuntu, but I don't know how to do this.  Also, my preference would probably be to keep the Windows network in place so that I can access things from the WinXP laptop, so really I'd like to able to access the Windows network from my Win7/Ubuntu laptop while running Ubuntu.

Hopefully that wasn't too convoluted to follow.  I've tried editing the smb.conf file, changing workgroup to HOME and removing the semicolon from the name resolve order = lmhosts host wins bcast line (two fixes I came across while researching the issue).  Running smbtree gives me Error NT_STATUS_UNSUCCESSFUL for all three machines.  Any help would be appreciated.

---

### Post by JohnDillinger43 on 2012-01-10
No ideas?  I'm at a complete loss here.  I just keep getting "Failed to retrieve share list" when I try to access the Windows WORKGROUP network I set up.  I tried using domainjoin-cli, but I just get "Error: DNS_ERROR_BAD_PACKET [code 0x0000251e]".

---

### Post by JohnDillinger43 on 2012-01-11
I suppose this is somewhat solved -- I was able to connect to the Windows shares by doing "Connect to server", selecting "Windows share", and putting in the information for the computer with the shared folders.  However, it's still really slow; when I have a document open on the shared folder and I go to save it, the program freezes for 5-10 seconds.  I'm marking this as solved, but I'd still like to find out if there's a better way to connect to Windows shares.

---

