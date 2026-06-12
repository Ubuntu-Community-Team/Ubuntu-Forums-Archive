---
title: "Home FTP server + streaming video"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by xexets on 2009-02-04
Dear all,
 I have just finished setting up a home network as follows:
wireless router
2 macbooks connected wirelessly
1 'linuxbox' with UBUNTU, controllable through SSH, with vsftpd SFTP server.
This allows me to use the linuxbox to store files, download with transmission when I need it and control everything from the macbooks. 
To this point I managed to do everything I needed: control transmission via web, control linuxbox via SSH, get and files from and to the linuxbox via sftp (I use cyberduck on mac).
Now the only thing I can't do, and I would like to do is to watch the films stored on the linuxbox without having to move them to the macbook. It is time consuming and it sort of misses the point of having a linuxbox.
As I am an utter newby I opened VLC on the mac, and pasted the FTP link to one of the files, just to try and VLC does not seem to react in any way, it does not load, open the file or anything. It just does not react. I guess I am doing something wrong, or even that this method is absurd.
Any clues? Do I have to install something other than vsftpd to do the job? Can I do it through vsftpd with configs I am not aware of?
Any help would be much appreciated, thank you in advance!

---

### Post by scurry7 on 2009-02-04
sound like you need software on your macbook so it apears to your media programs that the files are local
but i don't know mac stuff

from ubuntu I would "mount" the ftp or sshfs to a local directory on my computer then too all programs it would act like the files were local on my computer...

from windows I would use a program to "mount" the ftp server to a drive letter so it act like the files were on a local drive letter...

hope it helps

---

### Post by xexets on 2009-02-04
Thank you very much! I found Expanddrive for mac and it works, it mounts my linuxbox as if it was a local drive. Still, I can open files, but it takes +infinte to load them into VLC for example, I guess that could be a problem of my network, though I think that I might need maybe a different protocol, I am not sure FTP is good for these needs, what do you think?

---

### Post by pdtpatrick on 2009-02-04
Or you can make samba on your ubuntu drive and then on your mac .. hit command+k and connect to the samba drive .. smb://servername  ... this will mount the drive and you will be able to view on it finder which means you can then watch the movies as they will be streamed from the linux box and if you are on the same network then it should be a bit faster than when you remote in.

---

### Post by punx45 on 2009-02-04
use NFS.   Samba is designed with windows in mind and is therefore more effort than you require.

 heres the readers digest version:

install nfs-kernel-server

set up an /etc/exports file

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#

/media/mediaserver/ 192.168.1.0/255.255.255.0(rw,async,insecure,all_squash,anong
id=1000,anonuid=1000)
/var/www 192.168.1.0/255.255.255.0(rw,async,insecure,all_squash,anongid=1000,ano
nuid=1000)

```

view man nfs and exports or google for details on the exports file.

then on the mac, command+k in finder, type in nfs://ip.of.the.box and it mounts and appears in the shared section in the finder window (in leopard anyway)   drag that into startup items in user account prefs, and it auto mounts at login!  it then functions just like any other directory, you can put subfolders under places, and it also shows up in /Volumes 
this is pretty reliable. i have my itunes library set to an NFS directory and have had zero problems.

---

### Post by xexets on 2009-02-04
Thanks for all your answers!
I am trying nfs at the moment.
When you say in the code 192.168.1.0 you mean the address of the linuxbox, that of the macbook or that of the router?
I did all you advised, substituting the 192.168.1.0 in the code with the address of the linuxbox, connected in Finder, but it returns that user or password (which it did not ask) are incorrect.
Sorry for this but as I told you I am a real newby! Any clues?
thanks a lot!

---

### Post by xexets on 2009-02-05
That's wonderful, thanks a lot for the advice. I googled a bit and configured the nfs, eventually the my macbook can see the linuxbox via nfs. As you suggested it is way faster than ftp! I managed to watch a piece of a film through nfs, it goes pretty well but it jumps let´s say once every 2 seconds or so. Do you have any suggestions on how to optimize the nfs connection? I have seen there are many options to optimise but I was wondering if any of you had some advice!
Thanks once again,

---

### Post by punx45 on 2009-02-05
> **xexets said:**
> Thanks for all your answers!
I am trying nfs at the moment.
When you say in the code 192.168.1.0 you mean the address of the linuxbox, that of the macbook or that of the router?
I did all you advised, substituting the 192.168.1.0 in the code with the address of the linuxbox, connected in Finder, but it returns that user or password (which it did not ask) are incorrect.
Sorry for this but as I told you I am a real newby! Any clues?
thanks a lot!

the 192.168.1.0/255.255.255.0 is setting an ip range that the share is available to.   basically that is saying any computer on the network whose ip matches 192.168.1.x is allowed.   if you state a specific ip (take off the mask, the 255 part) then only that ip will be able to mount the share.   setting a range rather than listing specific ips is helpful if your macbook, as mine is, uses DHCP to acquire an IP.   

also i didnt mention it earlier, but the anonid and anonguid i have set are for a specific user listed in my /etc/passwd file.   i did it to resolve some permissions issues i had.   depending on how you set this, you might not be able to write to certain directories that you may want to.   it is telling the host system that any other system mounting the NFS volume is acting as user X on the host system.   as you may have noticed, there is no login or password challenges with NFS, and this may be a security risk.   i highly suggest reading documentation on the anon settings.

as for the video hiccups, you said you are wireless.   this can affect playing video, especially higher quality stuff.   on standard 100Mbs wired ethernet i have no problem watching HD divx videos.    wireless, not so sure.   wirelessly, music isnt a challenge, and compressed SD video clips shouldnt be, but a high quality DVD rip or HD video might be.   it depends on your router and structural features between you and the router.

---

### Post by xexets on 2009-02-06
Fantastic! Following your advice I connected the linux box via standard ethernet, while leaving the MBs on wireless and now I can seamlessly watch HQ films and I have I near-USB2 transfert rate. Wonderful, you've all been great, thank you very much for helping me out!

---

