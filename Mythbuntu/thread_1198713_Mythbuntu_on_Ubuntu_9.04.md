---
title: "Mythbuntu on Ubuntu 9.04"
date: 2009-06-27
forum: Mythbuntu
---

### Post by Jayy on 2009-06-27
I have installed a clean install of Ubuntu 9.04, downloaded and installed the updates, and downloaded and installed NVIDIA Accelerated Graphics Driver Version 173 for my onboard graphics card.

Now I would like to install Mythbuntu in Ubuntu.

My tuner is a WinTV HVR-1800, and I want to view and record OTA digital TV in Portland, Oregon. My motherboard is an Asus M2N68-VM with onboard GeForce 7050PV graphics. I am connected to an LG HDTV via HDMI.

I have tried in the past and failed, so I would like step-by-step help. First off I need to install Mythbuntu Control Centre, correct? And then what would be next?

Thanks. :D

---

### Post by roundhay on 2009-06-28
why not install mythbuntu 9.04? this will save you a lot of configuration steps?

---

### Post by Jayy on 2009-06-28
I want the Ubuntu applications and the Ubuntu interface and stuff, and it's a lot easier to put Mythbuntu on top of Ubuntu, than Ubuntu on top of Mythbuntu.

---

### Post by klc5555 on 2009-06-28
> **Jayy said:**
> I want the Ubuntu applications and the Ubuntu interface and stuff, and it's a lot easier to put Mythbuntu on top of Ubuntu, than Ubuntu on top of Mythbuntu.

Well, then, a good place to start would be to install the mythtv packages using synaptic. Since it's Ubuntu, you won't even have to worry about resolving the dependencies. When the packages are installed, run mythtv-setup from a prompt, or from the System menu in Gnome, and follow the steps in the mythtv manual [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) beginning with chapter 3 configuring the backend. 

There's nothing particularly special about it.  And the standard configuration settings are treated in the manual in much greater detail than you're likely to find anywhere else. If particular problems arise, for example with the perhaps problematical PVR-1800 driver support in Linux, they can be dealt with in forums like this one.

---

### Post by Jayy on 2009-06-28
> **klc5555 said:**
> Well, then, a good place to start would be to install the mythtv packages using synaptic. Since it's Ubuntu, you won't even have to worry about resolving the dependencies. When the packages are installed, run mythtv-setup from a prompt, or from the System menu in Gnome, and follow the steps in the mythtv manual [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) beginning with chapter 3 configuring the backend. 

There's nothing particularly special about it.  And the standard configuration settings are treated in the manual in much greater detail than you're likely to find anywhere else. If particular problems arise, for example with the perhaps problematical PVR-1800 driver support in Linux, they can be dealt with in forums like this one.
Okay, thanks. Could you give me a list of the packages I need to install?

---

### Post by klc5555 on 2009-06-29
> **Jayy said:**
> Okay, thanks. Could you give me a list of the packages I need to install?

That's Synaptic's job. Open Synaptic. Search "mythtv". Install them all. Synaptic will also recommend required and suggested dependencies. Install them all. Then you should be ready to proceed with the setup.

---

### Post by novellahub on 2009-06-30
Mythbuntu can be installed on top of Ubuntu.

[http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)

---

### Post by Jayy on 2009-06-30
> **klc5555 said:**
> That's Synaptic's job. Open Synaptic. Search "mythtv". Install them all. Synaptic will also recommend required and suggested dependencies. Install them all. Then you should be ready to proceed with the setup.
Okay, thank you.

---

### Post by Jayy on 2009-06-30
> **novellahub said:**
> Mythbuntu can be installed on top of Ubuntu.

[http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
yes, I know, but I need help to set it up. :|

---

### Post by novellahub on 2009-07-01
> **Jayy said:**
> yes, I know, but I need help to set it up. :|

You need this then?

[http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

---

### Post by Jayy on 2009-07-01
I got it working besides some minor issues. Thanks for the help!!

---

