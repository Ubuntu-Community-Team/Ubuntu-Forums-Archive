---
title: "Xubuntu doesn't like to share with windows"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by Kin2InuYasha on 2011-05-10
Hello,

           I have a folder on my windows xp machine that I am trying to share with my xubuntu machine (10.04) and I have been searching all night, and have found several resources for accomplishing this, but nothing that seems to work with this version of xubuntu. I've downloaded Samba and tried the smb://xxx.xxx.x.xxx/Shared Command  and it says "No such file or directory". There is no "Shared Folders" under System, Network, or any directory.  Right clicking on a folder produces no sharing options. The smb.conf file seems to have destroyed itself out of spite. Any help is appreciated.

I'm also on a wired network, if that helps any. 

Thank you.

---

### Post by Kin2InuYasha on 2011-05-10
I did find something called Gigolo and windows share. Could this be something? I'm going to research it.

---

### Post by pherber12 on 2011-05-10
Any luck? I'm having the same problem trying to connect to my roommates Xubuntu pc.. We can't find anywhere that would allow her to share her folders.

---

### Post by Toz on 2011-05-10
> **Kin2InuYasha said:**
> I did find something called Gigolo and windows share. Could this be something? I'm going to research it.

Yes, Gigolo will mount windows shares. See: [http://www.uvena.de/gigolo/](http://www.uvena.de/gigolo/)

---

### Post by Kin2InuYasha on 2011-05-11
Well, I managed to get it to work.

I fiddled with samba and the smb.conf for a while and got kind of lost. (I don't believe I configured smb.conf correctly) I tried using Gigolo. It found all of my shared folders on my Windows machine in the side panel network view. I connected and used Windows Share option to connect. It would not open the folder though. I downloaded everything that had the word samba in it in the Software center, including a program called PCMan File Manager.  I restarted the machine and tried opening the shared folder again and got an error message saying "This folder is empty"

I literally, LITERALLY went and had a cup of coffee, came back and tried again and it worked.

So, in short, I guess I will mark it as solved (Even though I have no idea how I managed it). If anyone can add some clarification as to what I may have done to fix the issue, please enlighten me. I may need to do this again soon.

Thank you.

---

