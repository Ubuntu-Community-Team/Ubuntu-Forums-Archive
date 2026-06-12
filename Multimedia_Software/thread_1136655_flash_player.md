---
title: "flash player"
date: 2009-04-25
forum: Multimedia Software
---

### Post by volter on 2009-04-25
I install ubuntu plugin in firefox and I couldn't play video (in myspace & other sites) then I installed adobe flash player but I don't know how to disable ubuntu plugin. help!!

---

### Post by michaeldt on 2009-04-25
When you open Firefox on a page with Flash, there should be a blue icon in the bottom right of the window. If you click that you'll get a dialog box which lets you choose your flash plugin. What options does it show you>

---

### Post by volter on 2009-04-25
ye its doesn't let me choose

---

### Post by michaeldt on 2009-04-25
[http://ubuntuforums.org/showthread.php?t=1135803](http://ubuntuforums.org/showthread.php?t=1135803)

See thread above to get Adobe's Flash player working in Firefox. Let me know if that helps.

---

### Post by volter on 2009-04-25
no I cann't copy to this folder it gives me an error

---

### Post by michaeldt on 2009-04-25
You need to copy it with superuser rights. Extract the .so file to your home folder and open a terminal. Then type:

```

cd ~
sudo cp libflashplayer.so /usr/lib/firefox-3.0.9/plugins/

```The first command just makes sure you're in your home directory (which it should be by default when you open a terminal). The second just copies the file using superuser rights.

---

### Post by nisna on 2009-04-25
start -> settings-> control panel
delete it like other programs

---

### Post by volter on 2009-04-25
thnx man but I think I fixed it. download tar.gz extract it and run the installer (duble-click)-> run in terminal-> enter.
One more y my linux say  that I'm not root user.

---

### Post by michaeldt on 2009-04-25
Ubuntu doesn't really have a root user account. To perform tasks which you would normally do as a root user you just use sudo instead.

---

