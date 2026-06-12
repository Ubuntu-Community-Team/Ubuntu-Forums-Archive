---
title: "Strange behaviour - active vnc server causes a periodical logout"
date: 2010-12-31
forum: Mythbuntu
---

### Post by sepperlchen on 2010-12-31
Hi,

I have an mythbuntu 10.10 installation (64 bit). I use the system as an front-end with an myhttv-backend on an other PC. The system is configured that the only user on the system (except root) loggs on automatically without interaction. It was working fine until I installed the vnc-server from the mythbuntu-setup. From this moment the system logs out the user after about 10 minutes and asks for username and password. If I log on again, after 10 minutes the same uggly thing happens again.
Simply uninstalling the vnc-package did not lead to success, a complete reinstall was neccercary. I tryed to reproduce the failure and it was definitivly the activation/installation of the vnc-server in the mythbuntu-setup.
I will try to reproduce the failure also with an qemu image, to make tests more easy.

Any ideas?

Best regards

Robert

---

### Post by patchyboy on 2011-01-01
Hi, i've got the same problem exactly. As a quick fix i'm running the root account which is unaffected.
Maybe i'll delete then recreate the affected account and see if this fixes it. Thanks for nailing the cause though,
i installed the VNC server 2 weeks ago and the problem showed within 24 hours then got worse and worse. 
thanks  Wes.

---

### Post by jaygardner on 2011-01-22
i have similar behavior also with mythbuntu 10.10 on 64 bit and vnc activated through mythbuntu control center.  Mine doesn't log off every 10 minutes though - my system seems to stay up for a long time and it's only when i am connected to it through VNC that some random mouse movement causes the session to be logged out.  I have a VM running on it also, which stays up, so it only seems to affect the logged in user session.

 It does bring up a log in dialog to enter username and password...

for what it's worth, i'm running a mythbuntu session, but i've noticed similar behavior with a normal ubuntu desktop session, which i think uses remote desktop facility of ubuntu instead of mythbuntu's vnc server.

I'm connected via tightvnc viewer on a mac....

---

### Post by cedyathome on 2012-02-01
I've found the solution, but don't know how to implement it. I can't figure out where mythbuntu starts vnc. 

Here's the link with the solution
[http://ubuntuforums.org/archive/index.php/t-1612704.html](http://ubuntuforums.org/archive/index.php/t-1612704.html)

The solution is to add -noxrecord to the command starting VNC. The explanation is in the link above.

Can someone tell me where VNC is being started from? It isn't in the /etc/gdm/Init/Default file.

Right now, I kill the vnc service and restart it with the -noxrecord flag. It seems to work without crashing gdm.

---

