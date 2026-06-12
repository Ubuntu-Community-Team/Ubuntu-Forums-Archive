---
title: "Edimax MA-2000 and shared folders"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by Steve54 on 2011-11-02
The Edimax is a networked media player and although it can 'see' the Ubuntu server it can't access the shared media folders on it. It can see the shared folders on my XP PC. The XP box can read and write to the Ubuntu server.
 
I thought the key to the problem is permissions (the Edimax doesn't have a facility to input a user name or password), but no matter what I try the Edimax reports "No Shared Folders Found".

---

### Post by Dave1234 on 2011-11-03
Well Steve54 - I am interested in your problem but having just taken same Edimax appliance out of the box, and being a newbie am interested in the answers you get: 

I also shared folders, and could not get Edimax to see them.

Found (in my Linux Mint 11 OS -  which has a 'Control Centre' (looks a bit like Windows Control Panel) an option 'File Permissions' to start file sharing, which identified whether or not a password would be requested (Never). 

So I was about  to try that.  If it failed thought Id try *sudo smbpasswd -a myloginusername*

Then I spotted the advice in your other  thread to upgrade the firmware...   So I set off the download - waited about 5 mins... it rebooted and then nothing occurred but a blank screen!! I cant get the Edimax  talking to the TV now...

Once I get the firmware sorted, will try again with the shared folders problem.  
3 weeks you say?  hmmmm...day 1 here...

---

### Post by Steve54 on 2011-11-15
It's four weeks now Dave and I still haven't resolved it. For some reason it can't 'negotiate' its way past Samba.
 
It still connects perfectly with Windows XP, but using that PC defeats the object of building an Ubuntu media server.
 
I have tried so many changes to smb.conf that I've lost count.
 
The problem maybe that the Edimax doesn't have a netbios name.
 
I've tried using wireshark but to be honest I don't really know what I'm looking for other than to compare the Windows trace with the samba trace.
 
I don't know if you've used the player much yet but I think it's pretty good at what it does, it's played everything I've thrown at it so far (although to a max of 720p). Forget wireless unless you know someone you can steal the recommended usb adaptor from as they have been defunct since about the release time of the player. And forget Edimax support as they are useless too.

---

### Post by Steve54 on 2011-11-17
Looks like it's the end of the line.
 
I've tried Nautilus sharing and Samba sharing, each time my XP PC can read/write to 'guest' shares no problem at all but still the Edimax can't see anything.
 
It still connects flawlessly to the XP PC, so what is Windows doing that I can't reproduce with Samba?
 
Anyone with any suggestions at all as to how I might be able to troubleshoot this problem?

---

