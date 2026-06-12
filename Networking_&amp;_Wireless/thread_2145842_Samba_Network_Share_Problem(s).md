---
title: "Samba Network Share Problem(s)"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by ferah on 2013-05-16
Hi guys,

I'm connect my Windows XP and Lubuntu with Samba. It was very changelling for me 'cause I'm a newbie in lubuntu (And ubuntu... And also all kinds of linux) but I succeed it with a few problems. I can see and share files from both of them. You keep in mind this. By the way in Windows I'm not faced with the problems those I'm going to mention about. Just in lubuntu.

Problems:

1) I go smb:// and I can see the Workgroups but when I click on it (Any of them) they give me an error and it says;

"The specified location is not mounted"

I can reach to windows computer's shared folders with it's ip adress like smb://192.168.1.20/

When I right click on that workgroup and choose "Open in New Tab" it opens it in new tab (smb://workgroup_name) but it gives me another error like below and I still cannot see what's in it.

"The specified directory is not valid"

2) in smb:// there are two workgroups but I have only one workgrup. The other workgroup was default value that comes with OS like "Workgroup". I'm not using it and there are no other computer in that workgroup name in my network. I cannot remove it. I google it and I found a file that called browse.dat (in /var/cache/samba/, the funny part in documentation it says that file must be in /var/lock/samba/) anyway with sudo privilege I open that file with leafpad and after that clean what's in it (And there was a Workgroup entry like something). After that I reboot the system but still there is a Workgroup. And I open that file with same way but there is no Workgroup entry just other things.

These two problems very annoying. I fighting for so long. I reach up to a point by myself (Thank to google) but I cannot go any further alone. Because of it I asking for your help. How can I fix this problems?

p.s: My English isn't very well. Because of it if there is a thing that you cannot understand please ask me to clarify. Thanks.

---

### Post by asavah on 2013-05-16
I don't remember how I fixed this issue, maybe
```
sudo apt[COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR] install fuse[COLOR=#666600]-[/COLOR]utils gvfs[COLOR=#666600]-[/COLOR]backends
```

Another approach would be to type full address to get into the share:
```
smb://SERVER/SHARE
```

---

### Post by Merrattic on 2013-05-16
This always works for me:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ferah on 2013-05-17
> **asavah said:**
> I don't remember how I fixed this issue, maybe
```
sudo apt[COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR] install fuse[COLOR=#666600]-[/COLOR]utils gvfs[COLOR=#666600]-[/COLOR]backends
```

Another approach would be to type full address to get into the share:
```
smb://SERVER/SHARE
```

Weird. First thing in the morning I try to install these packages but lubuntu says that they're already installed and nothing is going to be happen. Good thing is after that unused workgroup is disappear. I don't know. May be it is unreleated. Bad thing is it's not fix that issues that I mentioned. Anyway I try the second approach that you said but it's not worked for me either. SERVER is name of the other computer, right? I try this after that shareddocs but it result is the same. But thank you. It might be fix that unused workgroup issue.

Now I try the approach that showed in link send by Merrattic.

---

### Post by ferah on 2013-05-18
It's very weird. I found a solution here [http://askubuntu.com/questions/77087/samba-not-mounting-locations](http://askubuntu.com/questions/77087/samba-not-mounting-locations) and it's working. I can see all workgroup and folders with that application. Another thing is when I open workgroup and windows share (smb://) in new tab it's still blocking me but I click on address bar and press enter voila it's ok. And after that I can open those with double click but I can't open network computers and their share with this way. It still gives me the same error. But with pyNeighborhood I can see those shares without mounting. Addition to all of this, the most weird thing is I cannot go in Lubuntu's own share either. I can see Windows Share with my android tablet (ES File Explorer) but not Lubuntu's share (Just print$).

edit: I tried everything I could but it does not work correctly. And I decided to that Lubuntu is little bit buggy. I give it a try to Xubuntu. Beside all of that there is no Safely Remove for USB Devices. Thanks to both of you.

---

