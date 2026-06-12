---
title: "Photos, music and video on frontend. Why so complicated?"
date: 2010-11-23
forum: Mythbuntu
---

### Post by hundred1906 on 2010-11-23
Mythtv is great for TV recordings but for a system promising that mythical multi-functionality why is it so complicated to set up for all the other types of media I want to use. 

I know it is all free but I am chasing through stuff on samba/nfs, mounts, shares, starts, permissions ... apparently without end. And it is not as though I am trying to use non-compatible software products but just a Mythbuntu back/frontend and an additional separate mythbuntu frontend - all at 10.10. Oh, and all the photo and music media is pre-existing in the Ubuntu standard places on the backend (home/xxxx/Music etc).

TV which I expected to be the more complex to set up across the network is a complete doddle (easy) by comparison.

Has anyone got the complete "how-to" tucked away to save me tearing any more hair out?

---

### Post by LowSky on 2010-11-23
this is one of the better videos for setting up network shares. its a bit old but still pretty accurate.
[http://www.youtube.com/watch?annotation_id=annotation_888326&v=89hjWOb8qmY&feature=iv](http://www.youtube.com/watch?annotation_id=annotation_888326&v=89hjWOb8qmY&feature=iv)

setting up TV is all done from the backend. It might ,make little sence but stored videos and music is all done from the frontends. so if you have it on one machine you need to share those files and give them permissions to be used. 

Mythmusic wiki is very well written on setting up music playback and even mentions file sharing.
[http://www.mythtv.org/wiki/MythMusic#Linking_Pre-Existing_Audio_Archive_with_MythMusic](http://www.mythtv.org/wiki/MythMusic#Linking_Pre-Existing_Audio_Archive_with_MythMusic)

Now for video storage 
[http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)

---

### Post by hundred1906 on 2010-11-24
Thanks but I have seen that page before. My problem is much simpler. How do I get the out-of-the-box mythbuntu frontend install to see the picture, music and video file storage locations on my back-end. Linking in with iTunes is another problem altogether.

I have installed both SAMBA and NFS separately and together at both ends. Not sure which is best for the job and it is not clear what else needs to be set-up in the way of permissions etc. No doubt it is all pretty obvious if one has been sharing files regularly across a network for other purposes but if the only reason for doing so is to use Myth it seems like a steep learning curve.

---

### Post by tgm4883 on 2010-11-24
> **hundred1906 said:**
> Thanks but I have seen that page before. My problem is much simpler. How do I get the out-of-the-box mythbuntu frontend install to see the picture, music and video file storage locations on my back-end. Linking in with iTunes is another problem altogether.

I have installed both SAMBA and NFS separately and together at both ends. Not sure which is best for the job and it is not clear what else needs to be set-up in the way of permissions etc. No doubt it is all pretty obvious if one has been sharing files regularly across a network for other purposes but if the only reason for doing so is to use Myth it seems like a steep learning curve.

Video storage? Easy, upgrade to 0.24 and use storage groups.

Music and Pictures, IIRC, storage group functionality for that is coming in 0.25. For the time being you need to mount the samba/nfs shares on the frontend from the backend.

---

### Post by hundred1906 on 2010-11-26
Thanks for the advice. I guess I will know what Storage Group Functionality is when it arrives. Mounting samba/nfs shares appears to be the heart of the present difficulty. As far as I can see neither SAMBA nor nfs are part of the basic mythbuntu frontend install which is strange given the fundamental need with picture and music add-ons. I have of course loaded Samba through Synaptic but am still faced with a variety of config setting options whereas it ought to be a more straightforward process (and I am not a complete newbie to networks). I have yet to see anything about doing it on the frontend from the backend and as I cannot even get the file systems at either end to see the other am not sure whether doing it remotely is going to be either straightforward or useful.

I want to repeat at this point that I know that these packages are free but I am getting to the stage where I would rather pay for something that works (as a Ubuntu app) than spend evenings struggling in hope. Reviewing that last sentence ... I would definitely spend the money if there was anything out there.

---

### Post by nickrout on 2010-11-26
the standard places for mythbuntu to store those things are NOT /home, but /var/lib/mythtv, under there is pictures/ for your pics, music/ for your tunes, etc etc.

those dirs are then shared by samba under the standard mythtv samba settings. you simply need to mount them min the same place on the frontend.

---

### Post by hundred1906 on 2010-11-28
Really would like to be able to mount them. That is the problem.

---

### Post by williammanda on 2010-11-28
I can show you how to use NFS and mythtv .23 to view videos, pictures and music on other frontends... if interested?

View videos,pictures and music on other frontends using NFS and mythtv .23. My setup is Ubuntu with mythtv installed.
1. Open Mythbuntu control centre, select Services then enable NFS Service. Do this on the backend that has the pictures, videos and music and all frontends that you wish to view them on.
2. On the backend open an editor in termial.
sudo gedit /etc/exports
3. Add if not already there:
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)
4. Save and close editor.
5. On the frontend open an editor in terminal.
sudo gedit /etc/fstab
6. Add
192.168.1.100:/var/lib/mythtv/videos  /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.100:/var/lib/mythtv/music  /var/lib/mythtv/music nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.100:/var/lib/mythtv/pictures  /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

Note:
I use a static IP address for all my mythtv computers and there are a numbers of ways to do this. The IP address specified is the backend, so this will need to be your backend IP address. Also if the directories (videos, pictures and music) are not there you will need to create them with mythtv as the owner.
7. NFS will need to be restarted to take affect and the easiest way is to restart all the affected computers.

I use NFS since it is easier to setup and the file transfer speed is much greater than samba.

---

### Post by hundred1906 on 2010-12-01
Williammanda thank you, yours was just the clear answer I needed. Am away right now but will give it a try and (anticipating success) will then mark thread as solved. The only difference is that I am not going to use the mythtv locations to start with but the default locations used by the usual Ubuntu media packages (f-spot etc), otherwise I will end up duplicating a lot of files.

---

### Post by hundred1906 on 2010-12-02
The instructions given by Williammanda work. I modified them to use pre-existing directories so, for example, I changed /var/lib/mythtv/videos to /home/trevor/Videos and similar for Music and Pictures. You do need to set access permissions for each of these folders so that MythTV (frontend) has access to them. Additionally you have to tell the frontend not to use the default locations but to use the local folders - in my case /home/trevor/Music (or Videos or Videos) - and you do this in General Settings pages working through until you get to the field called "Directory to hold Music". You do have to go through individual settings pages for each media type rather than do it all in one place but it is pretty quick.

In fstab you need to enter the ip address of the back-end so that the frontend knows where to look. It took me a while trawling through lots of correspondence to work out how to make this IP address remain static without disabling the DHCP capability inside my router. I know I will need to go down that path eventually but for now I just wanted to take one step at a time.

My router is a WR54G from Linksys. Looking at its setup page (on [http://192.168.1.1/](http://192.168.1.1/)) the DHCP start address is 192.168.1.100 and the Maximum Number of  DHCP Users is 50. This means that any ip usage above 192.168.1.150 is unlikely to be reassigned. Consequently I amended the /etc/network/interfaces file (sudo gedit /etc/network/interfaces) to contain only the following:

auto eth0
iface eth0 inet static
address 192.168.1.151
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Doing this for my back-end set its IP address to 192.168.1.151. and this is the address I used in Williammanda's instructions.

One point is that the Nautilus Networks option (Places/Network) does not appear to show the nfs network though it all seems to work OK through MythTV. While doing all this I disabled SAMBA just to keep life simple. It may be that nfs and samba can co-exist but I wanted reduce my options.

Make sure you re-boot after all this.

---

