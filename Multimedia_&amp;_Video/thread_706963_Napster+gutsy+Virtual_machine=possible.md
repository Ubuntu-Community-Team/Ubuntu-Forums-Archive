---
title: "Napster+gutsy+Virtual machine=possible?"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by Jre35 on 2008-02-24
Hello, 
I have a subscription to Napster, and recently installed Gutsy to dual boot with XP. I know the protected files pose a problem in Linux and doesn't work. I thought, install a windows virtual machine, put it in an unused desktop, and it will run. Well, I installed the virtual machine in Ubuntu with vmware workstation and cleaned out all of the unnecessary applications and files. I gave napster the highest priority in the VM, and gave vmaware the highest priority in ubuntu, and yet, even when that desktop is active, Napster is slow in connecting, and has to buffer the song multiple times throughout, and there are pauses, and parts where the song is played extra fast to catch up to where it should be. I had 512mb ram dedicated to vmware workstation, and the virtual desktop itself has a 4 gb of hard drive dedicated. Why is it so slow, and is there a way i can have the song play in real time without buffering and pasuing?

Thanks in advance

Jason

---

### Post by Achetar on 2008-02-25
I believe it would help if you used virtualbox (virtualbox-ose in Synaptic, search for it) and run it in seamless mode it would work fine. I am not sure though. The only problem is you may have to create a new virtual harddrive and install WinXP on it, although VMWare may let you export virtual disks, but I doubt it.

---

