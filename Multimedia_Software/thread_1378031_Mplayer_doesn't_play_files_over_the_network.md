---
title: "Mplayer doesn't play files over the network?"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Sugi on 2010-01-10
How can I get mplayer to play files over the network?  It seems like I am not the only one that wants this feature.  Does anyone got a work around for this?

Thanks,
Sugi

---

### Post by andrew.46 on 2010-01-11
Hi Sugi,

> **Sugi said:**
> How can I get mplayer to play files over the network?

Which particular files are you trying to play?

Andrew

---

### Post by Sugi on 2010-01-11
I want to play avis and mkv over the network.

Sugi

---

### Post by SlugSlug on 2010-01-11
I found (with VLC i think) your best of copying the film to your desktop leave for a few secs and then play that file

just a work round I used for sftp

---

### Post by Sugi on 2010-01-11
SlugSlug, Ya that's what I am doing now.  :/ I am hoping on finding some kind of fix or a way to work around this without coping every single file to my desktop.  

Though thanks for the tip,
Sugi

---

### Post by Loosewheel on 2010-01-11
Hi Sugi,
Would an NFS share work for you? I export my media directory to the LAN with the /etc/exports file, and mount it on the client machines with /etc/fstab. 
I've tried VLC streaming and that works but is a little bit to set up on both boxes....with NFS ya just click on a file.

---

### Post by Sugi on 2010-01-11
NFS sounds really good actually, but one problem.  The files that I want to play are on my remaining windows  box.  So my xp box will host the files and my ubuntu box will be the client.  I have read some tutorials setting up nfs server on windows (and even linux box).  It sounds a bit confusing on the windows end.  Any tips guys?

Sugi

---

### Post by Loosewheel on 2010-01-11
> **Sugi said:**
> NFS sounds really good actually, but one problem.  The files that I want to play are on my remaining windows  box.  So my xp box will host the files and my ubuntu box will be the client.  I have read some tutorials setting up nfs server on windows (and even linux box).  It sounds a bit confusing on the windows end.  Any tips guys?

Sugi

What about 'Places'-> 'Connect to Server'-> 'Service Type = Windows Share'
and plugin the XP machine's IP Address? Does that get you there?
(Also take a look at 'man smbclient' in a console).

---

### Post by Sugi on 2010-01-12
I think I have to setup something up on the Windows end, because if I enter the IP for the windows machine nothing happens.

Sugi

---

### Post by aeiah on 2010-01-12
so is it that the files dont play properly, or that you havent got filesharing set up yet? if you're using windows you're best going down the samba route. there are many tutorials for ubuntu and samba on the net that should help you.

if you find your movies are stuttering and stopping when played over the network once you can actually access them, then you're best looking at mplayer streaming options and such. ive had no problems playing files normally with mplayer though over a network, but i dont do it regularly so i just do it over ssh

---

### Post by Sugi on 2010-01-12
I got samba working.  I use smb:// to mount share directories over the network, but I can't get mplayer to see them.  I have had issues with totem shuttering and sometimes even stopping.  I have even noticed some shuttering during playback of a local file as well.

Sugi

---

