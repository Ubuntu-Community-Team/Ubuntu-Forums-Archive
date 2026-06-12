---
title: "OpenShot not responding"
date: 2024-06-19
forum: Multimedia Software
---

### Post by satimis on 2024-06-19
Hi all,

Ubuntu 22.04

OpenShot not working

Version:3.1.1
libopenshot: 0.3.2

Warning:
OpenShot not responding
Wait or Close

Wait - no response. The warning popup repeatedly.  Then I have to close OpenShot.

Please advise how to fix the problem?

Thanks

---

### Post by ajgreeny on 2024-06-20
Try starting it from terminal with command ***openshot-qt*** and show us any error messages you see.
How did you install it?
Is it an appimage or a snap (if there is one), or was it installed from the repos?

---

### Post by satimis on 2024-06-20
I can't reply here

---

### Post by ajgreeny on 2024-06-20
> **satimis said:**
> I can't reply here
But you just did reply!
What do you mean?

---

### Post by satimis on 2024-06-20
> **ajgreeny said:**
> But you just did reply!
What do you mean?
It is very strange here.  It seems out of my control.  Now I make another testing here.

It just happens today.  OpenShot can be started

I have 2 PCs here:-

PC1 - 2 drives running Ubuntu 22.04.  OpenShot can be started on both drives.  Video (mp4) can be imported and added to track.  Starting video works but the progressing pointer won't move, just standing at the start of the track permanently.

PC2 - running Ubuntu 22.04.  OpenShot has the same problem as PC1

I don't know WHY?  According to my recollection OpenShot was install on repo download on OpenShot website.

Regards

---

### Post by satimis on 2024-06-20
Hi ajgreeny,

Previously I ran Google Chrome to browse Ubuntuforums.org.  It was very difficult to control the connection, clicking "Post Quick Reply" or "Reply" without response, just hanging there.

Now I make another test running Firefox to browse Ubuntuforums.org.   It seems without such problems.

Regards

---

### Post by satimis on 2024-06-20
Hi all,

It seems quite strange to me.

Tried again:-
1) Removed OpenShot running
$ sudo apt-get purge openshot-qt


2) Ran flatpak to install OpenShot

$ sudo apt install flatpak
$ sudo flatpak install org.openshot.OpenShot
$ sudo -i flatpak run org.openshot.OpenShot

OpenShot started but problem remains.

I think OpenShot
Version: 3.1.1
libopenshot: 0.3.2

may have problem.  Now I have to looking for its alternative, maybe Shotcut.

I have been running OpenShot for prolonged time

Regards

---

### Post by satimis on 2024-06-21
Hi@ajgreeny,

OpenShot V3.1.1 has problem running on Ubuntu 24.04 and 22.04

Performed following test:-

On my PC1 I have a drive running Windows 10.  

Download OpenShot-V3-1-1-x86-64,exe
and
install it

Start OpenShot and import video(mp4).  OpenShot (Windows version) works without problem.  The slider moves on running the video.

Regards

---

### Post by satimis on 2024-06-25
Hi all,

**[COLOR="#FF0000"]OpenShot Video Editor works on Linuxmint[/COLOR]**

Just performed following test

Start Linuxmint VM

$ lsb_release -a```

No LSB modules are available.
Distributor ID:	Linuxmint
Description:	Linux Mint 21.2
Release:	21.2
Codename:	victoria

```

Install OpenShot Video Editor on PPA
On Terminal ran;```

$ sudo add-apt-repository ppa:openshot.developers/ppa
$ sudo apt update
$ sudo apt install openshot-qt python3-openshot

```

Start OpenShot Video Editor```

$ openshot-qt

```

Import video (.mp4) and add it to Track

**[COLOR="#FF0000"]Video works on OpenShot Video Editor without problem.[/COLOR]**

It is very strange to me. WHY OpenShot Video Editor can't work on Ubuntu 22.04/24.04 ?

About one/two weeks before OpenShot Video Editor worked on Ubuntu 22.04 without problem.  

What I have done on Ubuntu 22.04 was running only ```

$ sudo apt update ; sudo apt upgrade

```

**[COLOR="#FF0000"]It is very strange to me ???[/COLOR]**

Regards

---

### Post by satimis on 2024-06-29
Hi all,

Finally I figure out the problem.  Only OpenShot Appimage, the daily built version, works on Ubuntu 22.O4/24.04

**[COLOR="#FF0000"]Download V3.2.0[/COLOR]**
[https://www.openshot.org/download/#daily](https://www.openshot.org/download/#daily)

**[COLOR="#B22222"]Steps performed:[/COLOR]**
right click on the AppImage
-> choose Properties
-> mark the file as Executable. 

Right-click the AppImage -> Run (to start OpenShot)
Import video (.mp4)
add video to track

Now I can play and edit video without problem.

I have been running OpenShot for prolonged time, on Ubuntu in the past, without problem.  Its alternative is ShotCut.  I'm not well experienced on ShotCut.  I have to start from the beginning.

Regards

---

