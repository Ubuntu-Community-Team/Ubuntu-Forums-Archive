---
title: "Accessing Windows shares from ubuntu 9.10"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Daedalus0101101 on 2010-02-16
Hello all,

I have searched for 30 minutes and I finally concede.  i have 3 ubuntu machines running 9.10.  All of them are running SMB so that the Windows machines can access the shares on the Ubuntu machines, but the ubuntu machines can not access shares on the Windows machines.  When I click to connect to a windows machine ( all of them running XP), it says  "connecting to COMPUTERNAME....."  It never opens the computer, and it always comes back with an error saying that it failed to connect.   I haven't been using ubuntu for very long, so im not as savvy with it as I am on windows.  All windows machines can see all ubuntu shares, just not the other way around and I'd like it to be both.  

Thanks in advance

---

### Post by KeLa on 2010-02-16
Try to go Places->Network
If all your computers are configured to same workgroup you will see the names
of those computers (at least those that have shares)
If you have multiple workgroups then you will first see those workgroup names and
selecting one of them you will see computers on that group.
That's how it works on my home machines (4 with Ubuntu 9.10, 1 Mac, 1 WinXP ,1 Win7,1 HP Home media server and Buffalo Linkstation)

---

### Post by Silvertones on 2010-02-16
I have also had a little quirkyness in this area. When Id go to Place/  network/ win network the other computer(Win) would not show. To solve  this first connect using "connect to server". You should then be able to  see the other files. Right click on the folder and create a link. This  will now stay as a permanent link under places/bookmarks and has never failed me.  Now going from the windos to ubuntu I sometimes have problems. This is  fixed, for me anyway, by first connecting from the Ubuntu computer to  the Win computer. At this point I'm good to go.

---

### Post by Daedalus0101101 on 2010-02-19
> **KeLa said:**
> Try to go Places->Network
If all your computers are configured to same workgroup you will see the names
of those computers (at least those that have shares)
If you have multiple workgroups then you will first see those workgroup names and
selecting one of them you will see computers on that group.
That's how it works on my home machines (4 with Ubuntu 9.10, 1 Mac, 1 WinXP ,1 Win7,1 HP Home media server and Buffalo Linkstation)
 
 
All my computers are on the same workgroup.  I have 2 WinXP, 1 Vista, 1 Win server 2003, and 2 uBuntu 9.10 computers.  All the windows based computers can see the uBuntu machines and access the shares that i have set up using Samba, but the uBuntu machines can not access the shares that are on the Windows machines, especially the Windows Server machine which has the majority of files I want to access.  It sees it listed under the workgroup folder, but when I click to open it to see the shares or try to create a link for it, it doesn't open.  It hangs at ""connecting to server...."  and nothing happens.  I can ping all the windows based computers and even RDP into all of them.  I have checked firewall settings to make sure that I wasnt forgetting anything.  Still, it will not let me access the windows shares.

---

