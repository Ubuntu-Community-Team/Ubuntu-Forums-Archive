---
title: "Installation halts/freezes/locks up"
date: 2010-10-04
forum: Mythbuntu
---

### Post by immudium on 2010-10-04
Hello.  I'm trying to do a fresh install of Mythbuntu 10.04 to run as a frontend only.  When selecting either the "Live" or "Install" options from the CD the installer appears to process normally but after 20-30 seconds it appears to come to a complete halt.  The red/white dots on the splash screen no longer change and the CD is no longer being accessed.  Ubuntu, XUbuntu, etc install CDs all work fine.  Mythbuntu is the only one that locks up.  I also tried the 10.10 rc and it locks up as well similar to 10.04.  I have tried both the 32bit and 64bit versions.  I have burned multiple copies and verified the media which is reported as OK.

My thought is that perhaps there is a kernel panic but I don't know how to get past the splash screen to see what happened?  I tried hitting F6 and randomly selecting the various debug items from the list, but nothing has helped so far.  I haven't been able to find any information searching around on Google and the forums, but maybe I'm asking the wrong question.

My frontend machine is a Pentium dual core with integrated NVidia 9300 graphics and 4GB of memory and sata 200GB hard drive.

Thanks for any help/thoughts.

---

### Post by LowSky on 2010-10-04
If the regular Ubuntu or Xubutn CD's wrk fine, just install on of them, and then add mythtv frontend from their package manager. 

Heck you can install mythbuntu-desktop form synaptic, which gives you the same install as the normal way

---

### Post by immudium on 2010-10-04
Oh really?  I wasn't aware of that.  Well, sounds like a good way to get around whatever is holding me up.  I'll still try to find out what's failing, but in the meantime, I can at least get up and running.  Thanks for the tip LowSky.

---

### Post by elperrillo on 2010-10-05
If Mythbuntu and Xubuntu install fine then you should not have absolutely any problem with Mythbuntu, since it is just version 10.04 with the MythTV program loaded, nothing more. Here is a quick setup guide, follow the section titled "Installing Mythbuntu" and make sure you do not skip any steps.

[http://geekyprojects.com/dvr-pvr/building-your-own-dvr-mythtv-quick-setup-guide/]("http://geekyprojects.com/dvr-pvr/building-your-own-dvr-mythtv-quick-setup-guide/")

Don't try to setup mythTV using synaptic, it will work however Mythbuntu is configured in such as way as to hide the operating system so you do not notice that you are on a computer. What do you rather have a DVR or a computer running MythTV?

---

### Post by LowSky on 2010-10-05
> **elperrillo said:**
> 
Don't try to setup mythTV using synaptic, it will work however Mythbuntu is configured in such as way as to hide the operating system so you do not notice that you are on a computer. What do you rather have a DVR or a computer running MythTV?

NOT TRUE: You can have it set so the frontend starts automatically on any installed version of Mythtv by simply checking a box in the settings menu of the frontend, or in Mythbuntu's control center.

---

### Post by elperrillo on 2010-10-05
> **LowSky said:**
> NOT TRUE: You can have it set so the frontend starts automatically on any installed version of Mythtv by simply checking a box in the settings menu of the frontend, or in Mythbuntu's control center.

No offense but:

Mythbuntu does everything for you, even the color scheme is different so it does not burn you TV screen, you would have to change everything to match Mythbuntu. Mythbuntu is made for that purpose, otherwise why bother making Mythbuntu in the first place? It is supposed to save you work. For that I'll just get Ubuntu 10.04 load it with The Gimp and call it Gimpbuntu.

---

