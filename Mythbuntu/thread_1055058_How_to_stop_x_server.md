---
title: "How to stop x server"
date: 2009-01-30
forum: Mythbuntu
---

### Post by rschapman on 2009-01-30
I was interested in installing the new drivers from nvidia that support my 9400gpu. I tried all the means to quit x that I could search in the forums but when I went through the setup the nvidia congif tool kept telling me I had an x server running. Can someone point me in the right direction of completely stopping x in mythbuntu. Thanks.

---

### Post by alderion on 2009-01-30
'init 3' should put you into runlevel 3 which has no x; however, i'm not sure this is actually what you want.  iirc, the nvidia tool is a graphical one and thus needs an x server.  try nvidia-xconfig instead maybe.  this will change your x config to use the nvidia server.  perhaps the complaint isn't that an x server is running but that you aren't running an nvidia xserver.

-peter

---

### Post by rschapman on 2009-01-30
noob question but can you tell me in more detail how to get to init 3? Thanks.

---

### Post by liquidhot on 2009-01-30
In the terminal, type init 3 (you may have to prepend 'sudo' no quotes)

---

### Post by nilber on 2009-01-30
Let me know if this works for you.  typing init 3 into my system (with or without sudo) does nothing.  Typing telinit and a number, has slightly more effect, but none that will take me to a straigh command line without x running.

I'm pretty sure you are trying to update the NVIDIA drive, as am I, and having no luck shutting x down, not trying to configure the NVIDIA server.

---

### Post by rschapman on 2009-01-30
Hey thanks for the reply. Yeah I did try what you mentioned and still no luck. You are absolutely right I'm trying to update to 180.22/25 either one.

---

### Post by clustermonkey on 2009-01-30
Actually, you need to do "sudo telinit 1" to get out of
X into a shell.  Run level 3 starts the X server and 
desktop.  If you are using the xxx.run package for your
drivers, it is essentially a compile of the drivers against
your current kernel.  Once you start the Nvidia install, 
you will probably get a warning that says something to the
effect that some required processes may not be running at
this run level (I can't remember the exact message).  You
can ignore this warning and proceed.  Other messages will
indicate if you need additional kernel packages installed.

Good luck...

---

### Post by rschapman on 2009-01-31
I followed the instructions but I'm having some issues. I have it hooked up to my LCD TV through VGA and when I ran the command. The screen messes up and doesn't show anything but trash. It doesn't seem to drop to a terminal. When I tried to SSH in and do it from another machine it messes up. Does init 1 break a wireless connection?

---

### Post by clustermonkey on 2009-01-31
Run level 1 does not include networking, wired or wireless.
Originally the runlevels were:
  0 - halt 
  1 - Single user mode
  2 - Multiuser, with networking, but no NFS  
  3 - Full multiuser mode
  4 - unused
  5 - Multiuser with X11
  6 - reboot (Do NOT set initdefault to this)

Recent releases have pared this down to:
  1 - Single user
  3 - Multiuser, networking and X11
  6 - reboot

If you want to know exactly what services are running in
each runlevel, look in the /etc/rc<n>.d directories (<n>
is a number 0-5 for each run level).  these scripts are
run when "start"ing or "stop"ping a run level.

---

### Post by august495 on 2009-01-31
correct me if I'm wrong...

ctrl+alt+f2
sudo /etc/init.d/gdm stop

Would be the easiest way.It's how installed them.

---

### Post by rupert80 on 2009-01-31
> **august495 said:**
> correct me if I'm wrong...

ctrl+alt+f2
sudo /etc/init.d/gdm stop

Would be the easiest way.It's how installed them.

That's how I would do it too, assuming you're running gnome.  Then
sudo /etc/init.d/gdm start
after you've finished.

If you're running KDE or some other gui, you would need to find the name of the start/stop script in /etc/init.d and do the same as above for it.

---

### Post by hooiberg on 2010-01-24
While 

sudo /etc/init.d/gdm [stop/start]

works in Karmic, it does not work in Intrepid.
The console nicely says that the stopping of the X server went [ OK ], but the server keeps running. I fill fiddle about some and let you know when I have something that works.

---

### Post by hooiberg on 2010-01-24
Ah, it is vital not log off Gnome first. Then the GDM can really be stopped.

---

