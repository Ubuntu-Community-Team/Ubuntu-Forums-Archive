---
title: "RDP Help"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by burgechris on 2012-05-10
I'm about to die here.  I made the horrible decision to move to 11.10 and I'm too afraid to go to 12.04 because of the issues I've been having.  I use ubuntu daily but I have to rdp into windows systems all the time.  Tsclient worked fine until the upgrade and now using it will cause the whole OS to freeze (except for some of the hotkeys which allows me to reboot).  I tried Remmnia (sp?) but that failed because it just did a 35 GB (yes GB) dump in to my log file of errors (though the connection seems fine until the systems gets bogged down by the 25 gigs).  In KRDC I can log in but I can't type into any of the windows.

I'm willing to use rdesktop but I don't know if it was tsclient or rdesktop that causes the freeze (my understanding is that tsclient just is a gui for rdesktop so please correct me).  Do I need to uninstall ubuntu and use 10.10 or (gasp) get Windows 7?  I can't do work without rdp and thus ubuntu becomes useless without it.  I love ubuntu otherwise but this is killing me!

---

### Post by burgechris on 2012-05-10
As an update, I can sometimes type in krdc though it is not consistent.  I'll let people know what I find on krdc (i.e. if I can find a common action that allows me to type into it or not) in this thread but any other alternatives would be great.  As a note, I switched from unity to gnome3 because of the issues I was having with unity in case your point of reference is dependent upon my desktop.

---

### Post by Gyokuro on 2012-05-10
Rdesktop works for me - I have to check sometimes different Windows systems and never had any freezes (W2008r2,W7Prof,W2003r2) on Lucid 10.04.4 or testing 12.04 with rdesktop now.

---

### Post by burgechris on 2012-05-10
Did you ever experience a freeze with tsclient?

---

### Post by burgechris on 2012-05-11
Apparently, the issue is with rdesktop.  I also discovered that if I do Ctrl-alt-F2, login, kill the gnome-shell (thus it respawns) and press ctrl-alt-f7 that everything is fine ecpet for the session.  I know that this is with rdesktop because it has now happened in remmina, krdc and tsclient and when it is the only thing out there.

AMD-64
11.10
rdekstop latest on synaptic (1.7.0 though 1.7.1 is the latest on their site)

Am I the only one with this issue?
 
Thanks

---

### Post by The Cog on 2012-05-11
I wonder if it's an issue with gnome. I have used rdesktop pretty-much every working day for years without ever seeing a problem. However, for the last year or two, I have been using Xubuntu, not Ubuntu. If it makes any difference, I normally launch rdesktop from the command line.

---

### Post by burgechris on 2012-05-15
Okay...It finally happened (2 times) without rdesktop or any rdesktop session open.  I ran dmesg and I don't see anything that speaks of anything but wondering which forum I should go to now to help resolve this.  It does seem to happen more frequently with a redktop session open.  My fix now is to Ctrl-Alt-F2, kill gnome-shell, and then Ctrl-alt-F7.

Any ideas or redirection to an appropriate board would be appreciated.

Thanks

---

### Post by Gyokuro on 2012-05-15
Hi,

can you please let us know some details about your hardware? In case rdesktop should have problems more people would post about this erros and I have even tried to watch a video remote via rdesktop - no freezes at all.

---

### Post by narcisgarcia on 2012-07-12
I'm using Lubuntu 12.04 and both remmina and rdesktop fail in this computer.

rdesktop freezes the computer completely (kernel frozen too), and remmina breaks with "Segmentation fault (core dumped)" when exporting to an .rdp file.

> VGA VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
Mainboard P4M800CE DDR : 5VKM3i
CPU Intel(R) Celeron(R) CPU 3.06GHz
RAM 1152MiB
Ethernet VIA VT6102 [Rhine-II] (rev 78)


---

### Post by narcisgarcia on 2012-07-12
[This workaround]("http://ubuntuforums.org/showthread.php?p=12095781") solves my problem.

Adding the following line to /etc/sysctl.conf
```
net.ipv4.tcp_window_scaling=0
```

---

### Post by HawkinsTheWizard on 2012-07-16
Problem persists (with rdesktop-1.7: after logging in to the remote desktop the whole window freezes while loading the remote desktop icons; or xfreerdp-1.0 : segmentation fault)
The difference in rdesktop-1.6 is a dependency on libssl-0.9.8 vs 1.0

Will now try to install libssl-0.9.8 to see if this is the culprit, however I doubt it since on my archlinux systems I always update to the latest versions and they have no problems.

#update
Downgrading libssl and rdesktop does not solve the problem either.

---

