---
title: "[SOLVED] VNC Won't Enable in 7.10"
date: 2007-11-26
forum: Mythbuntu
---

### Post by Just4Fun20 on 2007-11-26
I'm running Mythbuntu 7.10.  

I've read prior VNC posts including [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) but they apply to earlier releases and sound overly complex.  

I'd like to enable VNC.  I've never actually used VNC, but have used remote control software.  My "viewer" is on WinXP.  I've tried both TightVNC and VNCViewer.  Both fail to connect.   

The obvious answer is that VNC is not running on the "server" which is the Mythbuntu 7.10 box.  

I go to the  "Mythbuntu Control Centre" (Mythbuntu 'Setup' and then 'Mythbuntu').  I move down to System Services and hit enter.  I get a list of System Service which I can enable (some show enabled).  I go to VNC Service and enable it.  This activates the password dialog box.  I enter a password (which is greater than 6 characters) and then click Apply.  I get an "Apply Settings" dialog box which indicates that it will "add vnc4server service." and I click Apply.  

This returns me to the Mythbuntu graphical user interface with the Mythbuntu option selected.  Trying to VNC in doesn't work.  Recycling and trying again doesn't work.  Going back into Mythbuntu Control Centre shows that VNC is disabled.  Repeating as necessary and trying things differently does not correct the problem.  

Any thoughts?  Do I need to do all those steps listed in thread 122402?  

TIA

---

### Post by foxbuntu on 2007-11-26
One thing that you have to do after enabling VNC is restart the X server

```
ctrl+alt+bksp
```

--or--

Just reboot the machine.

---

### Post by aznewsh on 2007-11-26
Try ensuring the mythbuntu install cd is in your drive when you enable vnc,

---

### Post by Just4Fun20 on 2007-11-26
"Try ensuring the mythbuntu install cd is in your drive when you enable vnc,"

Excellent!  That fixed the problem.  After putting the installation CD in the drive and following the same steps it spent a few minutes installing VNC.  I rebooted and was able to log on to a VNC session.

Thank you very much.

---

### Post by aznewsh on 2007-11-27
> **Just4Fun20 said:**
> "Try ensuring the mythbuntu install cd is in your drive when you enable vnc,"

Excellent!  That fixed the problem.  After putting the installation CD in the drive and following the same steps it spent a few minutes installing VNC.  I rebooted and was able to log on to a VNC session.

Thank you very much.

You are very welcome - now maybe you can solve my vnc problem lol

[http://ubuntuforums.org/showthread.php?t=623993](http://ubuntuforums.org/showthread.php?t=623993)

later...

---

