---
title: "MythTVbackend setup poblem"
date: 2008-06-11
forum: Mythbuntu
---

### Post by bmwman on 2008-06-11
Hello,

I've been trying to setup this thing for few days now on Ubuntu 8.04. I even downloaded and tried MythUbuntu 8.04 and still get the same error.I have read and read pages of how-to's and threads but nothing works. Basically i'm the very beginning: have the MythTV installed on my main desktop including frontend and backend. I have another PC in the bedroom which i'm planning to set as frontend and maybe a laptop with frontend.

My problem is that i keep getting no UPnP found and unable to login to the database. I have followed the instructions here 

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162) 

But I still get the same error. BTW I have a virtual Ubuntu running inside of VMware in XP and it worked from the first time. I just installed it to try i did it same way like i do now (I think).

Please help me set it up. I really appreciate it

---

### Post by ebike on 2008-06-11
Make sure that on the backend, you have a real IP set in the 1st few pages of mythtv-setup (it needs to set in two places, the same) it's in the general section I think from memory. 

On the remote frontend, when you get that error on connect, it usually means that you have not given the correct user-name and password. The username is usually Mythtv and the password can be found in the backend file /etc/mythtv/mysql.txt

Hope that helps.

---

### Post by bmwman on 2008-06-12
I finally got into the stupid database. I removed the whole mythtv-database and reinstalled. The second time around it worked fine. Now I have to achieve the same thing on my bedroom PC :) I will mess with it after work today.

Anyway, Can you recommend a good not overly expensive TV card. The catch is that I have a small boxed IBM PC and have only one PCIe 1x slot available or the TV tuner needs to be USB. I don't know if the USB ones have issues ot not.

Please advice what to get.

Thanks.

---

### Post by bmwman on 2008-06-12
I got the error again.I don't know what is wrong annd it's driving me nuts. It could be a permissions problem. I can't delete the /home/mythtv folder even with sudo. I know this is a very common problem but trust me I have tried million things and still can't get it to work.

Also I get this 

 sudo /etc/init.d/mythtv-backend restart
 * Restarting MythTV server: mythbackend  
QSettings: error creating /home/mythtv/.qt

Please help me figure it out.

---

### Post by bmwman on 2008-06-12
WOW, over 80 views and no response?! That really sucks.

---

