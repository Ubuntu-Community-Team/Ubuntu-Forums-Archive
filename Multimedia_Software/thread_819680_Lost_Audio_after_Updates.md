---
title: "Lost Audio after Updates"
date: 2008-06-05
forum: Multimedia Software
---

### Post by gameshints on 2008-06-05
I just installed a slew up updates for Ubuntu 8.04, and lost audio output on my Thinkpad X40.

The weird thing is that audio still works in Firefox 3 through the flash plugin and totem media plugin.

No other software applications, including Ubuntu system sounds, play audio.

Any ideas where to start debugging this problem?

Thanks!

---

### Post by vigyani on 2008-06-05
Hi

May it is similar problem given on [this page]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/"). Check it.

I suspect system updated Kernel ver. too.

Which is the sound card in your system? 

May be try, chose/(Change) the correct Audio device through System--> Preferences --> Sound and test if some output is there.

Sometimes in past when I faced similar problem, reinstalling audio drivers for the new Kernel helped.

---

### Post by shadowfirebird on 2008-06-06
I have no sound this morning.  My system wasn't recognising any sound cards.

I've backed out yesterday's install of "linux-image-2.6.24-18-generic"; that's brought the sound back, but obviously it's not a brilliant solution.  

Can you expand a bit on the idea of re-installing sound drivers?

Update: sorry, typo, that should be 2.6.24-19.  18 works; 19 breaks my sound.

---

### Post by mushi411 on 2008-06-14
Sometimes kernel upgrades don't pull in the modules required...if the following directory does not exist for your new kernel "/lib/modules/<KernelVer>/ubuntu" then you haven't installed the correct linux-modules package in synaptic for your kernel...that should fix the sound issue.
-S

---

### Post by gameshints on 2008-06-14
It looks like with the upgrade, that my default audio devices changed to incorrect ones.  After changing them back and restarting, my system sounds work now.

Still don't know why it worked fine in flash?

Anyways, thanks for your all you help!

---

### Post by rehin on 2008-06-18
> **gameshints said:**
> It looks like with the upgrade, that my default audio devices changed to incorrect ones.  After changing them back and restarting, my system sounds work now.

Still don't know why it worked fine in flash?

Anyways, thanks for your all you help!


How do you change your audio drivers back?  I ask this because after last update to kernel 19 my audio is not working any more.

---

### Post by Atele on 2008-06-18
> **vigyani said:**
> Hi

May it is similar problem given on [this page]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/"). Check it.

Hi, I was having the opposite problem, I had audio playback from everything BUT flash and I installed the package on the page and it somehow worked.

Thanks for the link!

---

### Post by lycopenehead on 2008-06-20
i have the same problem its an ibm x40, with ubuntu 8.04 on it, after a few updates through synaptic package manager,it was for installing "virtualbox" plus some affiliated packages,then it went with no sound also if you check the system--admin--sounds you will find the intel sound driver doesnt in the list nor any 1
here is atemporary solution i  used to make it work
i shut down the sysem
while loading GRUB pressed ESC ,then chose from the list ubuntu generic,,,,,,,system recovery(i dont really remember the actual phrase ) followed the instructions then it coming to work again
the problem that you should make this process every time you power on x40

any help for this guys please

---

### Post by gameshints on 2008-06-20
> **Charles54 said:**
> Hi sorry I cannot help you because I don't have any idea about this matter.

Why would you post a comment as worthless as this?  You're not even involved in the conversation.

> **rehin said:**
> How do you change your audio drivers back?  I ask this because after last update to kernel 19 my audio is not working any more.

I didn't change my drivers, but changed the sound outputs by going to System--> Preferences --> Sound, as mentioned above by vigyani.

---

### Post by lycopenehead on 2008-06-20
HEY GUYS I WOKE UP TODAY ON DAWN,AND I GOT A DESTINY AGOOD 1
i opened the synaptic pack. manager and i guessed which package i may need,i marked up afew and restart system and it came back everything is fine
you may see the applied changes as i got it from the history of synaptic pack.,


Commit Log for Fri Jun 20 15:39:35 2008


Upgraded the following packages:
linux-generic (2.6.24.18.20) to 2.6.24.19.21
linux-image-generic (2.6.24.18.20) to 2.6.24.19.21
linux-restricted-modules-generic (2.6.24.18.20) to 2.6.24.19.21

Installed the following packages:
linux (2.6.24.19.21)
linux-386 (2.6.24.19.21)
linux-image (2.6.24.19.21)
linux-image-2.6.24-19-386 (2.6.24-19.33)
linux-image-2.6.24-19-generic (2.6.24-19.33)
linux-image-386 (2.6.24.19.21)
linux-restricted-modules (2.6.24.19.21)
linux-restricted-modules-2.6.24-19-386 (2.6.24.13-19.42)
linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42)
linux-restricted-modules-386 (2.6.24.19.21)
linux-ubuntu-modules-2.6.24-19-386 (2.6.24-19.27)
linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.27)


i am not adoctor here so i dont know really which pack. made the remedy

---

