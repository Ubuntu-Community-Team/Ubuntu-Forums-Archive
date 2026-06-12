---
title: "ubuntu 9.10 to vista file shares - samba - HELP!"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by joshwaaa on 2010-02-27
Hi All,
 
I really hope you can help me out, I am trying to connect to a windows vista share on my network: //joshwaaa-pc/movies
 
Iam trying to connect from a ubuntu 9.10 pc wirelessly. I cannot connect to the windows pc manually or via the GUI. I cannot even see the windows pc in the "windows network" places in ubuntu.
 
I have disabled all firewalls, I have allowed all filesharing (printer, file, no password) on the windows pc. I have double/triple checked the permissions on the share.
 
Out of pure desperation, I have edited the smb.conf and added ntlm v2, i have even edited the vista security policy to allow ntlm1 & 2 but no luck.
 
$ smbtree
Enter users password:
session request to 10.0.0.xxx failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
session request to JOSHWAAA-PC failed (Not listening on called name)
session request to *SMBSERVER failed (Called name not present)
 
$ smbclient -L joshwaaa-pc
Enter users password:
session request to JOSHWAAA-PC failed (Not listening on called name)
session request to *SMBSERVER failed (Called name not present)
 
i have enable netbios over tcp/ip on the vista machine.
 
I have been scouring the forums ubuntu and linuxquestions for hours and hours trying every trick in the book but cant get the damned thing to work....
 
I cant find any errors in the log files.... HELP???!!!??
 
cheers,
 
Joshwaaa

---

### Post by gordintoronto on 2010-02-28
Do you have the same workgroup on all machines?

Do you have the same user name and password on both machines?

If you select places/network and double-click on Windows Network, does the workgroup show up?  Can you double-click on it to see the computer?  And double-click on that to see the Share?

---

### Post by joshwaaa on 2010-03-26
Apologies,
 
this has been solved.
 
turns out windows vista requires you to enable file sharing in more then 1 place..... yeap thank you windbloze.
 
to get it work i did the follwing:
 
- enabled all filesharing in network centre (no password)
- changed network adapters in network centre from public to privates ( enables file sharing)
 
-under network connections, adapter properties, above ipv4 & 6 settings tick the stupid little tick box for file sharing ... (YES, even though you have enabled it in network centre you have to do it here too .......................)
 
Then it worked.
 
Cheers,
 
Joshwaaaaaa

---

