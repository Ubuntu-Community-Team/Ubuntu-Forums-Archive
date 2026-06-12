---
title: "cannot view pictures file on windows machine"
date: 2011-04-21
forum: Mythbuntu
---

### Post by bryan.sailer on 2011-04-21
I have set up nfs to share my videos and pictures from my backend to my remote front end. That is working properly. On my wife's Windows machine I can see the Mythtv and I can open the Videos and the Music file. When I open the pictures file I get 'No files have been found on this remote library'. What could I have done wrong?

I have also installed samba but when I go to /etc/init.d and samba is not there so when I go to restart samba it does not restart.

---

### Post by nickrout on 2011-04-21
the samba init script is called smbd not samba.

---

### Post by bryan.sailer on 2011-04-21
Thank you, I was looking online and all of the examples I saw had the file as samba. That worked, at least as far as letting me restart samba. I am now getting a permissions error. I just do not understand this because I did not setup any permissions for the other three files that I can access. I am the owner of all of the files and it is listed as my group. Now when I open up the MythGallery I can see the pictures. When I try to open the file from the desktop to add photos is when I get the permissions error. Where do I need to look now to grant permission to access the file?
 
Mythbuntu 10.10
Ubuntu 10.10

---

