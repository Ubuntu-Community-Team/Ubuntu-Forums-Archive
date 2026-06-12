---
title: "I need guidance"
date: 2008-04-30
forum: Multimedia Software
---

### Post by babylon2233 on 2008-04-30
I'm now looking forward to re-use Ubuntu after leaving it just a few days ago after a fail upgrade. I'm now really commited to install Ubuntu 8.04 and wipe Windows out of my Hard Drive but i need to know how I want to make my Graphics Card working perfectly. I'm using Nvidia 8600GS..

I hope someone can give me a full guide before i install Ubuntu on my system. If you have any links please give me...or e-mail me [EMAIL="babylon2233@gmail.com"]here[/EMAIL]. 


Thanks

---

### Post by cor2y on 2008-04-30
If its a clean install then there are no problems.
On the other hand if you are upgrading hardware acceleration will be a bit of trouble to enable.
I don't know why this is so but i can attest to it.
I was able to upgrade from feisty to the hardy beta and the graphics card was recognized and the closed drivers worked.
Did the final update from beta to LTS hardy and the closed drivers died, the open source nvidia drivers worked but me enabling the closed drivers via synaptic or even using envy didn't work or any of the fixes suggested in the first few days Hardy was launched.
I had to reinstall 8.04 LTS (luckily ever since 5.04 i have used a seperate /home partition) finally with that i had the closed 3d drivers back and working.
Edit
My card nvidia 8600GTS

---

### Post by babylon2233 on 2008-04-30
> **cor2y said:**
> If its a clean install then there are no problems.


I already try hardy clean install before after that fail upgrade but i can't make my graphics card work as normal. So i need to know what should i do after installing Hardy.

---

### Post by zenkaon on 2008-04-30
You should goto system->Preferences->Hardware Drivers

And then install the relevant 3rd party drivers, you'll probably have to reboot (shocking!!).

You should also install the nvtv app, load up system->admin->synaptic package manager and search for "nvtv". Really cool app, lets you do twinview on multiple monitors and TV out without messing around with /etc/X11/xorg.conf

After installing the 3rd party drivers you should be able to get compiz/quake 3/unreal/whatever working great.

---

### Post by Bruce S on 2008-05-03
> **zenkaon said:**
> You should goto system->Preferences->Hardware Drivers

And then install the relevant 3rd party drivers, you'll probably have to reboot (shocking!!).

You should also install the nvtv app, load up system->admin->synaptic package manager and search for "nvtv". Really cool app, lets you do twinview on multiple monitors and TV out without messing around with /etc/X11/xorg.conf

After installing the 3rd party drivers you should be able to get compiz/quake 3/unreal/whatever working great.
zenkaon,

My computer must be different. Tried System>Preferences -- No "Hardware Drivers" is shown on the list .
 That is a bit strange.

---

