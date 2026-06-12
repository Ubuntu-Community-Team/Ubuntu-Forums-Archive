---
title: "Video, distro problem?"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Stuffrish on 2009-08-15
Erm.. When I try to run a certain game([http://www.planeshift.it/](http://www.planeshift.it/)) the game freezes and stops refreshing the actual game area. Though the UI is completely useable and moveable.

-Image-
[IMG]http://i221.photobucket.com/albums/dd283/Demonwithoutwings/Screenshot.jpg[/IMG]

I posted this on their forums, though this seems to be a problem with some video packages. I got help to some degree, but they didn't know the exact packages that I needed to have for Ubuntu.

I might've written something wrong now, it's early morning. But take a look at the forum I posted in. That should clear things up.

[http://www.hydlaaplaza.com/smf/index.php?topic=35759](http://www.hydlaaplaza.com/smf/index.php?topic=35759)

---

### Post by dlmarti on 2009-08-15
> PlaneShift is not a complete game, and it's in development right now. 

According to the PlaneShift website, the game is in early development, and is not ready for play.

---

### Post by Stuffrish on 2009-08-15
If you check some of the patchnotes I'd say that the game is playable. Since they patch it and tell people to download the new verision to win, mac and linux.

---

### Post by Ebonwumon on 2009-08-15
The game is very much playable in its current state and the problem is not a matter of playability as this is a problem with Stuffrish's drivers and the software that goes along with them, not the game.

The problem is simply Ubuntu's repositories changing the names of all the packages. Simply needs the names of these packages in the ubuntu repos.

intel-dri-git
mesa-git
dri2proto-git
xf86-video-intel-git

---

### Post by Stuffrish on 2009-08-15
> **Ebonwumon said:**
> The game is very much playable in its current state and the problem is not a matter of playability as this is a problem with Stuffrish's drivers and the software that goes along with them, not the game.

The problem is simply Ubuntu's repositories changing the names of all the packages. Simply needs the names of these packages in the ubuntu repos.

intel-dri-git
mesa-git
dri2proto-git
xf86-video-intel-git


Can't find any of those packages in Synaptic Packages Manager.
I've posted my lspci -tv output in the thread I linked earlier ( [http://www.hydlaaplaza.com/smf/index.php?topic=35759](http://www.hydlaaplaza.com/smf/index.php?topic=35759) ).

Hope this'll help.

---

### Post by plaid on 2009-11-21
Stuffrish,

        I have also just discovered PlaneShift, and it looks good.  I have an Intel 910GL graphics adapter and am using Jaunty Ubuntu.  When I first installed Jaunty, my 3d acceleration was awful because the default drivers are crummy.  I followed these instructions, [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582"), and all my 3d games work fine.  

Hope this helps,
  Plaid

---

