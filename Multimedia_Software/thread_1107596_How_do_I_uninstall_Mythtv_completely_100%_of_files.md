---
title: "How do I uninstall Mythtv completely 100% of files"
date: 2009-03-26
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-03-26
Hi, 

I recently installed mythtv and got it working.  But now for some reason I can't record, when I select record nothing happens.  

I want to reinstall mythtv because when I first installed it I could record programs.  I have tried sudo apt-get remove mythtv --purge and selecting completely remove from synaptic package manager.

But I still have configuration files because when I reinstall it has the theme that I was using and my capture card is already there and so is my guide data.

I want to delete 100% of the files that were installed and then re download and install mythtv from scratch.  How do I do this?

---

### Post by lovinglinux on 2009-03-27
Go to System >> Administration >> Synaptic Package Manager, then click the button "status", select "Not Installed (residual config)" in the left panel, then right-click the MythTV packages and select "Mark for complete removal". Click "Apply".

---

