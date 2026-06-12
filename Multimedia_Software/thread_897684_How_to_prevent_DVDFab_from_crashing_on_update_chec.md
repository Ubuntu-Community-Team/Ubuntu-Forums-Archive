---
title: "How to prevent DVDFab from crashing on update check"
date: 2008-08-22
forum: Multimedia Software
---

### Post by dwasifar on 2008-08-22
I've noticed that since version 5.0.x of DVDFab HD Decrypter, the program often hangs or crashes, apparently related to the update check.  It will start scanning the DVD and then put up a window (two copies of it, actually) reporting that there is a new version available.  Clicking these windows to make them go away results in the main window hanging.

My first thought was to disable the update check in the settings.  But that didn't seem to do anything; the settings showed "Check for new version automatically" with its box unticked, but the update check was still occurring.

Fixing this required me to dust off my rusty Windows skills and do a registry change.  Here is how to do it.

1) Start regedit in Wine: ~/.wine/drive_c/windows/regedit.exe 
2) Find the key HKEY_CURRENT_USER\Software\DVDFab\V5\Generic\UpdateCheck
3) Right-click it, choose Modify, and set the value to 0
4) Do the same for HKEY_USERS\S-1-5-4\Software\DVDFab\V5\Generic\UpdateCheck
5) Exit regedit.  
6) Kill any running wineserver or winedevice.exe processes (or just reboot) and restart DVDFab HD Decrypter.

Of course, after this, you will need to watch for updates manually.

Please post to the thread if this solution worked for you.

edit: For some reason the forum is inserting a space in the first key.  I don't know why, but the key ends in "UpdateCheck," obviously, not "Updat eCheck".

edit: I have since discovered that it also works to just delete the key entirely; so if the above way doesn't work for you, try just deleting the UpdateCheck key from the registry.

---

