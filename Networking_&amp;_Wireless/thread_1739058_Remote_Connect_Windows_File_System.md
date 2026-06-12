---
title: "Remote Connect Windows File System"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by lelantus on 2011-04-25
All,

My friend's Windows machine has some nasty malware on it at the moment (won't allow exe. files or task manager to run, and closes any explorer windows into the file system) and I figured I'd use my Ubuntu system to help out.

I'm looking for a way to connect to and browse his file system via a wireless, or preferably, Ad-Hoc network. Once connected, I'll run a sweep with Clamscan and quarantine the file in question so it can be removed.

He has no Remote Desktop clients installed, and wouldn't be able to run them even if he did because of the behavior involved in the malware program. I'm not exactly looking for a Remote Desktop solution, per se, but really just a way to access his file tree.

I am currently running 10.04, but will be upgrading to 11.04 later this week.

Any ideas?

---

### Post by headvampyre@hotmail.co.uk on 2011-04-25
The only way you'd be able to connect would generally be through:

a) a backdoor that the virus wouldnt know about 

b) boot his system via an ubuntu live cd / usb, (youll have to build an ISO with clamav builtin), and install and run clamscan that wya.

---

### Post by spike_seti on 2011-04-25
team viewer [http://teamviewer.com](http://teamviewer.com)

---

### Post by lelantus on 2011-04-25
Wow, neat app. Unfortunately, that would require him to be running his own browser in order to create an account, and he can't launch any exe. files.

---

### Post by jetbangdink on 2011-04-26
i ran into one of theese before on windows heres what i did 
 
downloaded Rkill 
 
Rkill stops all malware processes from running and logs what it killed it is completely free and was made by an IT college student 
 
so i ran Rkill and read the log of what it killed 
 
reason you cant open anything is because the malware is constantly running a process to keep you from opening browsers and antivirus software 
 
so once the process was killed i ran antivirus which detected the malware and removed it 
 
now you may have to boot in safe mode with networking to be able to acess the internet to download and run Rkill or boot in safe mode and download rkill on another machine and save it to a flash drive and upload it from the drive on the machine in safemode run it and run antivirus to remove the threat 
 
it solved my problem maybe it will for you too

---

