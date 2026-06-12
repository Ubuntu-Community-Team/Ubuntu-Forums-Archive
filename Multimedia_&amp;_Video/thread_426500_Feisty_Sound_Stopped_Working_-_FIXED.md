---
title: "Feisty Sound Stopped Working - FIXED"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by superyounan1 on 2007-04-28
I updated to Feisty, sound worked ok for a day or two, it was fun! Even the water effects in Beryl worked on my ATI! But then sound stopped working soon after... Odly enough the log-in sounds still worked, but once gnome loaded, any application that plays sound would crash

I found a couple 'miracle solutions' in the forums, people reported that they work like a charm, but they didnt for me. So I tried the "comprehensive solution"

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Basically had me remove ALSA audio drivers and reinstall them, and it worked. The thread warns that you need to reinstall GDM after you remove the audio driver, and I made sure I did.

When i restarted, the login window was the default Kubuntu login winodow instead of the custom one I was used to?? (I have KDE installed as well).  Although I thought that was weird, I logged in to Gnome with no problem and sound was working!!

But here's the strange part, when I went to switch back my login window GDM theme by System>administration>login window, i got the following error:

```
GDM(The GNOME Display Manager) is not running. You might in fact be using a different display manager, such as KDM or xdm. If you still wish to use this feature, either start GDM yourself or ask your system administrator to start GDM
```

I'm positive I reinstalled it! and to verify, when i run
```
sudo apt-get install gdm ubuntu-desktop
```

I get the expected 
```
ubuntu-desktop is already the newest version.
```


To recap, SOUND WORKS FINALLY, but GDM doesnt...

---

### Post by superyounan1 on 2007-04-28
Ok, I found out how to set GDM back to be your default display manager, simply run:

```
sudo dpkg-reconfigure gdm
```

It will ask you to choose between gdm and kdm, if you are a special case like I was and you have both KDE and Gnome installed.

I hope this helps someone.

Again, this is for getting audio to work after an upgrade to Feisty. Use the "comprehensive" solution found in the link above if the following solution didnt work for you:

[http://ubuntuforums.org/showthread.php?t=418360]("http://ubuntuforums.org/showthread.php?t=418360")

---

### Post by thegreygeek on 2007-04-28
Thanks.  I had the same problem.  You fixed it!

---

