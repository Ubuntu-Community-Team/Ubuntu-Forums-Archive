---
title: "xconf problem"
date: 2008-05-14
forum: Multimedia Software
---

### Post by arch.stanton on 2008-05-14
hey gang, i recently installed backtrack 3 and when i boot to it on a usb device, theres no problem at all. It's smooth sailing.
But I recently just found an old hard drive laying around, and decided I should install backtrack on it.

Now every single time I boot up, it works up until the point where I have to type "startx". Then I just get a black screen. So then I tried typing xconf, then startx. Still... a black screen.

Then fluxbox, black screen
xconf;kdm - black
xconf;fluxbox - black
kdm - black.

in every one of these black screens, I kept hitting ctrl+alt+numplus. and still a black screen.

FFS, i dont know what to do. I have a fairly old ATI Radeon 200G something or another (i dont know where to check to see what hardware I have). 
Now I did back up the xorg.conf before installing it. Should I replace the current xorg.conf with the backup one? If I should, how would I get the backed up xorg.conf from my usb drive to replace the current one in the backtrack prompt?

EDIT: ALSO! This may help. When I booted up using the liveUSB if I attempted to start up in any graphical interface other than kdm in vesa 1024x768@75Hz, it gave me that fackin black screen. So I hit tab to edit the function, and I observed the autoexec=kdm. So I typed kdm after I installed it and it didnt work.

So any help would be greatly appreciated because I am absolutely FACKED!

---

### Post by arch.stanton on 2008-05-14
bump. does any one know what I should do?

---

### Post by prshah on 2008-05-15
> **arch.stanton said:**
> 
kdm - black.

edit the function, and I observed the autoexec=kdm. So I typed kdm after I installed it and it didnt work.


To (re)start the kdm, use ```
sudo /etc/init.d/kdm start
``` or restart, or stop, as the case may be.

---

### Post by arch.stanton on 2008-05-15
it says that no such file or directory exists.

---

