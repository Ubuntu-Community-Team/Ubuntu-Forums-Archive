---
title: "How to network between ubuntu and XP?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by lilrayray69 on 2009-05-23
Hi! I have a laptop using Ubuntu 9.04 and a PC using Windows XP Pro SP2. The Ubuntu laptop connects to the router wirelessly, the windows pc connects directly to the router....

I am wondering if there is a way I can network between these 2 machines so I can easily shared files between them? I've heard of using SAMBA or something but as far as I can tell that has to do with running a server, which I don't have... Any help would be appreciated :)

---

### Post by zobcat on 2009-05-23
You do need Samba. 
```
sudo apt-get install samba
```

Now you have to set up the folders you want to share. It's done pretty much the same way in XP and ubuntu: Navigate to the folder you wish to share, right click and choose "Sharing Options". I'm not sure what it's called in XP, but it's something similar. It's self-explanatory after that.

---

### Post by lilrayray69 on 2009-05-23
ok i have installed SAMBA, and I guess I need to do Places > Connect to A Server...

But I don't know what to put for "Server:" ?
how do i find out what all to put for this? thanks

---

### Post by zobcat on 2009-05-23
Once you've shared the folders they will show up in your Network Places in XP and in Places > Network in ubuntu.

---

### Post by lilrayray69 on 2009-05-23
hey!
when I go to Places > Network in Ubuntu I can access my shared folder on the Windows PC!! That's great

But!, the "My Network Places" thing is not showing up on my Windows PC! It seems to not recognize a network like Ubuntu seems to be doing...Do I have to put samba on windows as well or what?

thanks!!!

---

### Post by zobcat on 2009-05-23
Have you shared any folders on your XP machine?

---

### Post by lilrayray69 on 2009-05-23
I just have the default sharing folder..."C:\Docs & Settings\All Users\Documents" and my Ubuntu PC can access that and take files from it.

I just don't know how to reverse the situation and have a folder my XP pc can recognize off my ubuntu laptop and take..

---

### Post by zobcat on 2009-05-23
It should be working. Try rebooting.

---

### Post by lilrayray69 on 2009-05-23
I did reboot...Didn't help. But I did find a way to get to "My Network Places" and by going through "Entire Network > Microsoft Windows Network > Workgroup:" 
I can see my laptop listed as PCNAME server (Samba, Ubuntu) but when I try to double click on it there it asks for a username and password (and my linux ones dont work)...

also, when i go to my network on the ubuntu laptop and go to my laptop area it wont let me create a new folder, all thats in there is a folder called "print$"..

EDIT: Oh, I found out how to share folders onto my laptop network. But now I still can't figure out how to get to those shared files on my Windows PC....

---

### Post by lilrayray69 on 2009-05-23
wow! lol, sorry...dont know how i coulda been so dumb.. XD

i didnt even think for some reason that I could put files from my laptop into that same shared windows folder.......i was trying to make a separate based on my laptop or something ?? lol

thanks a lot, its working great!!

---

### Post by zobcat on 2009-05-23
Great. No problem.

---

