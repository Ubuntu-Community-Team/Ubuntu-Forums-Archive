---
title: "[SOLVED] Frontend can't play videos from backend?"
date: 2008-11-06
forum: Mythbuntu
---

### Post by themota on 2008-11-06
I have a strange problem. I have a Backend/Frontend computer in my livingroom. This one works fine. I just tried to set op another frontend, running on a wired lan.

I have achieved to get this frontend up and running, and I can see all the videos and all the music from my backend. But when I try to play a video, from the new frontend it gives me this error:

Failed to open
'filename.avi' in /home/mc/Media/film/Film
Check if the video exists

The directory it mentions is the directory on the backend, where I have my videos. Anyone knows what I can do to solve my problem?

Hope someone can help?

*UPDATE*
I found out that i am able to play my recordings from the new frontend, but I still can't play the movies in my videofolder?

---

### Post by newlinux on 2008-11-06
You need to mount video and music files on remote frontends in the same place they are located on your backend (so they should be mounted on your remote frontend at /home/mc/Media/film/Film). Recordings and livetv stream through a separate myth protocol and don't need to be mounted.

Let us know if you need help with setting up network shares and mounting them on remote computers. There is also plenty of howtos and threads on this  if you want to search.

---

### Post by SiHa on 2008-11-06
Just to add to Newlinux's good advice:

Myth expects all **media** - videos / pictures / music (ie not recordings), to be mounted on the **local** filesystem in order to play them.

And to clarify:[pedant] The mount point can be anywhere on the local filesystem, it doesn't **have** to be the same as on the backend, but it's just probably simpler if they are...[/pedant] ;-)

Have a look here:
[http://ubuntuforums.org/showthread.php?t=908779](http://ubuntuforums.org/showthread.php?t=908779).

Substituting **/home/mc/Media/film/Film** where **/var/lib/mythtv/videos** is referenced.

---

### Post by newlinux on 2008-11-06
Yes, I should clarify. The mount points certainly don't have to be in the same location on each machine. But, if you make the mount points different on different machines, you will probably run into metadata problems if you use any metadata. This is because the DB stores the metadata centrally (not on a per frontend basis). So if you have the videos mounted in one place on machine A and a different place on Machine B when you scan videos and enter metadata on machine A, that information will not work properly with machine B because each video record includes a location of the file (which would be different if your mount points are different). So you would have to rescan on B to get the new locations of the files (and change where it looks for videos), which if you accept the option to delete files it can't find from the DB will delete all the metadata you inputted on machine A.

So I strongly recommend you put the mount points in the same place on all frontend machines. It will probably save you some headaches

---

### Post by themota on 2008-11-06
Thanks for the replies, I can now see that I am on the right way. I have now added this line to fstab:

```

192.168.1.150:/home/mc/Media/film/Film /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
```

But when I run sudo mount -a i get this error:

mount.nfs: access denied by server while mounting 192.168.1.150:/home/mc/Media/film/Film

Can anyone help me solve this problem?

I have tried looking through the thread posted above, but that guy doesn't seem to have the same problem.

---

### Post by newlinux on 2008-11-06
I recommend following:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I don't use the mythbuntu install, I use ubuntu and then install mythtv and I use CIFS for network shares, but I think for NFS you will need to first export the directories you want to share on the backend before you can mount them on remote computers. I think the default /var/lib/mythtv/videos location is automatically shared in mythbuntu, but I'm not sure.

And again, I recommend mounting them in the same place on all frontends.

---

### Post by SiHa on 2008-11-07
> **themota said:**
> Thanks for the replies, I can now see that I am on the right way. I have now added this line to fstab:

```

192.168.1.150:/home/mc/Media/film/Film /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
```

But when I run sudo mount -a i get this error:

mount.nfs: access denied by server while mounting 192.168.1.150:/home/mc/Media/film/Film 

You need to set the premissions on the backend media directory:
```
sudo chmod 666 /home/mc/Media/film/Film
``` so that it is world readeable and writeable.

...or have you forgotten to export the directory?

Also, Newlinux - I take your point about the metadata, I hadn't thought of that, sorry. I was thinking from an nfs point of view. Must try not to be so pedantic inthe future.:redface:

---

### Post by themota on 2008-11-07
I solved the problem. For some reason the exports in the standard exports file in my mythbuntu wasn't working. When I created my own from a "howto" from the ubuntu forums, It worked like a charm. Thanks for all the help guys ;)

---

### Post by newlinux on 2008-11-07
> **SiHa said:**
> ...

Also, Newlinux - I take your point about the metadata, I hadn't thought of that, sorry. I was thinking from an nfs point of view. Must try not to be so pedantic inthe future.:redface:

No worries...

I'm speaking from experience when I first setup myth a couple years ago. I couldn't figure out what the problem was for a bit... Just trying to help others avoid the mistake I made. L)

---

