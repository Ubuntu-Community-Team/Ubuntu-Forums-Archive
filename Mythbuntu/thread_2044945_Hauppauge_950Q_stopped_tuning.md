---
title: "Hauppauge 950Q stopped tuning"
date: 2012-08-20
forum: Mythbuntu
---

### Post by twinfrey on 2012-08-20
I am running Mythbuntu 12.04.  I have an HVR-1800 card and an HVR-950Q.  After installing Mythbuntu, I set up my cards and everything worked well.  I added the xc5000.conf file to /etc/modprobe.d to correctly load the firmware for the 950.  I recorded several shows and rebooted a few times.  Everything worked correclty.  Then I decided to install the k3b and k9copy applications.  when I rebooted, the 1800 still tuned correctly but the 950Q didn't.  I looked at the dmesg output and it still said that the firmware was loaded but it still won't tune.  Any ideas?  I'm really having a hard time with the 950Q.  I've been installed multiple times and it always works until I start installing other software.

---

### Post by klc5555 on 2012-08-20
Does 950Q tuning therefore begin to work again if you uninstall these two programs? How about if you uninstall k3b but leave k9copy on the machine? Does tuning begin to fail if you install _any_ 3rd-party software on the machine at all, or just any KDE software on the machine, or just these two programs?

Also, does the mythbackend log provide any information about what is going amiss when the 950Q is trying to tune?

I asked the question about what happens when you uninstall the KDE apps, because although it was several versions ago (7.10-8.04), I used to have strange difficulties frequently pop up whenever I would add k3b to a vanilla Mythbuntu machine. Odd things, like USB/IR keyboards and remotes no longer functioning correctly. Problems would cease immediately when k3b (along with its ancillary dependencies) was uninstalled. Since there were and are no shortage of non-KDE disc-burning apps, this was not a problem worth investigating too seriously. Since I needed no other KDE software on those particular machines, I installed Brasero instead and got on with things. 

If it were to turn out that your machine and its 950Q tuner function correctly without k3b or KDE apps, you may wish to choose a different burner. And since k9copy ceased active development over a year ago you may wish to begin searching out a replacement for it in any event.

---

### Post by twinfrey on 2012-08-20
Hey.  Thanks for responding.  This has been driving me nuts lately.  When I uninstalled the two apps I still coudln't get the tuner to work.  It doesn't seem to be all applications.  I was able to install libreoffice and ntfs configuration tool without it breaking.  I did a fresh install and will attempt to slowly install applications until I can find what causes it to break.  Do you have this specific tuner?  I want to know if it works reliably.

---

### Post by klc5555 on 2012-08-20
No, I had other tuners. I don't think the 950Q even existed 4 years ago. My issue at the time was that the addition of the KDE dependencies for k3b seemed to break stuff --in particular USB and IR applications. Removing all traces of KDE seemed to make things better.

But by all means check your backend logs if tuning breaks again. It's your best shot at clues.

Also check dmesg output again for reference to insufficient vmalloc space. I've had HVR-1600 tuners in installations stop tuning DVB channels for no evident reason only to discover later that this or that which I've added has caused the machine to run short of vmalloc space, necessitating that I add more at boot.

---

