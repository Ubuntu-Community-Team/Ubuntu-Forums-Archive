---
title: "3d acceleration problem"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by zedd2006 on 2006-12-31
ok, heres the deal, i installed 3ddesktop, at the time, i had 3d acceleration working, 3ddesktop worked fine, everything worked fine, i setup the startup programs to open "3ddeskd" and "3ddesk --acquire" and i did not reboot, i installed firestarter, aegis anti virus, and clam av, and panda desktop, and then a update for automatix2 was available  so i did the update and then rebooted, rebooted fine, except when i went to open 3ddesk the screen just flashed, so i went to command line and tried it from there and this is the errors i got.

chris@zedd:~$ 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

chris@zedd:~$ 3ddeskd
Daemon started.  Run 3ddesk to activate.
chris@zedd:~$ 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

and in the process of all of this, i realized my screen saver was taking up alot of process's, so i went to the system monitor to see what was eating up my cpu and found that it only showed "CPU" and before it was showing CPU1  and   CPU2 because of the P4 HT.

Can someone please help me.](*,) ](*,) ](*,) ](*,) ](*,) 


the specs of my machine is...
Pentium 4 HT 3Ghz
1.5 GB Ram
ATI Radeon X300 128mb VC - With dual monitors running
250gb Sata HD - Linux Drive
80 GB IDE HD - Storage Drive

---

### Post by zedd2006 on 2006-12-31
nevermind, got everything back to working once i had to reinstall from messing witht he x.org file

---

### Post by girard on 2007-03-18
i get the same error message. never got to run 3ddesk. how do i configure hardware acceleration?

how do i see the specs of my system much like dxdiag in windows - just switched... so i'm still trying to learn how to use linux. sorry.

---

