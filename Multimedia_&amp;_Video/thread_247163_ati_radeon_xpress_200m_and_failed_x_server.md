---
title: "ati radeon xpress 200m and failed x server"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by jubilee33 on 2006-08-30
Dear all,

I have just read through the whole 29 pages of sticky thread about the latest ati driver installation.  But I haven't found any similiar situation at this stage.  I have a Radeon Xpress 200M card with shared 128MB memory.  The resolution is 1280x800.  I did a fresh Ubuntu Dapper installation on a brand new laptop and after the first reboot, I got an error message "couldn't start your X server (graphic interface)".  Then I guess I was just in this console.  I am still fairly new to Ubuntu, especially the text mode, so after I saw "Login" in the black screen, I typed in my username (is this right?) and then the system kept asking for a password which I supplied several without seeing any further progress.  I couldn't do anything with Ubuntu then.  What should I do?  I already struggled a long time in Mandriva 2006 and gave up on it because of the graphic card and the wireless connection.  Any help regarding the console and more importantly, the ATI driver would be highly appreciated.  Thank you.

---

### Post by tseliot on 2006-08-30
Boot in RECOVERY MODE (you can choose it from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

---

### Post by jubilee33 on 2006-09-02
Thank you for your reply.  I did what you suggested.  I got the same error - cannot start x server.  I also did some googling and did the following.

> sudo nano /etc/X11/xorg.conf

I checked the section "Device" and attempted to change "ati" to "radeon" as well after failing again.  In short, I encountered the same problem.

This time I went into the x server output for troubleshooting.  I saw some errors like "Invalid IO allocation", "Requesting insufficient memory window", "cannot find a replacement memory range", "screen(s) found, but none have a suitable configuration" and "Fatal server error: no screens found".  What does all this mean?  When I went into xorg configuration, the system did detect the correct graphic card driver.  Why cannot it be properly loaded?  What else can I do at this point?  By the way, I have no connection at this stage so I can only do everything offline.

---

### Post by krajok on 2006-09-03
I got the same error with my Radeon Xpress 1150.

I think that the patch below could help
 - [https://bugs.freedesktop.org/show_bug.cgi?id=6377](https://bugs.freedesktop.org/show_bug.cgi?id=6377)
But I don't know how to apply the patch.

Can anybody help me please ?

---

### Post by krajok on 2006-09-03
My problem have been solved.

[http://ubuntuforums.org/showthread.php?t=249951](http://ubuntuforums.org/showthread.php?t=249951)

---

### Post by jubilee33 on 2006-09-07
Thank you for your help.  But I do not have an active wireless connection yet (that's just another problem I will have to solve after I get my X server to work).  How can I go about trying out your solution?  I am still fairly new to Ubuntu so I have no idea how to proceed.  Would you please teach me the howto in an offline environment without X?  Or is it entirely impossible? ](*,)

---

