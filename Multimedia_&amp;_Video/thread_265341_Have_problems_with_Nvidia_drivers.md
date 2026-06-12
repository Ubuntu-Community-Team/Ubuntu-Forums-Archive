---
title: "Have problems with Nvidia drivers"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by jpe2000 on 2006-09-25
I have the right kernel and headers. It compiled itself. I just can't go to a higher res. It only goes to 1024x768. What can I do so it can go higher? Thanks.

---

### Post by croak77 on 2006-09-25
Can you post your /etc/X11/xorg.conf?

---

### Post by jpe2000 on 2006-09-25
I'll try to. I know I installed Nvidia drivers correcterely because I see the Nvidia splash screen.

---

### Post by pseudonym on 2006-09-25
Look in the 'Screen' section of xorg.conf. You'll probably need to add the extra res yourself. Do this by -

1. Logging out and pressing Ctrl+Alt+F1 to get to a console prompt.

2. Log in if here if necessary and run 'sudo /etc/init.d/gdm stop' (or kdm if you use Kubuntu) to shutdown X.

3. Now run 'sudo dpkg-reconfigure xserver-xorg' and answer the questions which will appear. Eventually you will get to a section where you can choose your screen res'.

4. When done, type 'sudo /etc/init.d/gdm start' and you should have the res you want, or be able to change into it.

You can also do this by manually editing xorg.conf and restarting X if you prefer.

---

### Post by tseliot on 2006-09-26
> **jpe2000 said:**
> I have the right kernel and headers. It compiled itself. I just can't go to a higher res. It only goes to 1024x768. What can I do so it can go higher? Thanks.

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

