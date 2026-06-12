---
title: "Dual screen display on computer with Nvidia Optimus"
date: 2011-08-17
forum: Multimedia Software
---

### Post by SuchetBargoti on 2011-08-17
Hey guys, just having trouble setting up a dual monitor from my Dell xps laptop using an HDMI port. It dual boots onto Ubuntu 10.04. 

The computer has a Nvidia GeForce GT 555M with Optimus graphics card and there have been issues with this card on linux systems as discussed in this forum [here]("http://ubuntuforums.org/showthread.php?t=1657660")

As mentioned there, to get things working I need to make sure I have not installed the restricted drivers. So I think what is happening right now is that the graphics are shown off the integrated graphics card. 

This is my output from <lspci | grep VGA>

```

00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dcd (rev a1)

```

The forum recommends to use this program called Bumblebee but I have had some issues with that in the past. Is there somehow I can setup my dual display while staying on Ubuntu 10.04 and not installing Bumblebee? I have researched into setting up dual display walkthroughs before but they all concentrate on nvidia or ATI configurations.

---

### Post by matthewtomlinson on 2011-08-18
Hi, I am having the exact same problem, I have even tried Bumblebee and since re-installed and tried a fresh install... still no luck I am afraid

---

### Post by SuchetBargoti on 2011-08-19
Previously when I had 11.04 installed, I couldn't get unity to work. But then I installed Bumblebee and unity worked. But never really figured out how to set up dual monitor. 

Now due to some other programs I am using for my work, they didn't like bumblebee and 11.04 so I downgraded to 10.04. Lets hope someone can help us out :)

---

### Post by jaimefma on 2011-09-07
Hi guys,

I'm in the same situation. I've got a XPS l702x with a Nvidia 550M graphical card, I have installed the experimental 3D support drivers of the additional drivers application and I cannot set up the dual screen display. 

I have connected an external monitor through the HDMI. Usually there is a black screen with no information, but at this moment I have some data of the start up process. Exactly I have a line: "Desconectado de Plymouth". Other times, I have seen the splash screen with dots, when I shut down the computer. This means that the laptop is available to send info ...

Did anyone try the Bumblebee? It seems there is a stable version ...

Cheers,

---

### Post by blitzit on 2011-09-07
Hi,

Do you have these drivers installed : [http://www.nvidia.co.in/object/linux-display-ia32-280.13-driver-in.html](http://www.nvidia.co.in/object/linux-display-ia32-280.13-driver-in.html) ? I you don't, download the drivers from this site. I live in India and this is the Indian version of the site; you could probably check the version for your country. You could search here [http://www.nvidia.co.in/Download/index.aspx?lang=en-in](http://www.nvidia.co.in/Download/index.aspx?lang=en-in).

Step1:
Once you have the file downloaded for your piece and operating system, uninstall all drivers that came default with ubuntu. Do this by:
```
sudo apt-get remove --purge nvidia*
```

Once that is done, you will need to blacklist some drivers to avoid conflicts. Add these lines at the end of the file /etc/modprobe.d/blacklist.conf
```
# This is the list to be blacklisted for the installation of NVIDIA Drivers
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```

Save the modified file and reboot.

Step2:
On reboot you might not be able to get to the x-screen, in which case simply log in to a terminal and run the installed driver installer. e.g., if the file is in your home folder do this:
```
sudo NVIDIA-Linux-x86-xxx.xx.xx.run
``` (The xxx.xx.xx will be replaced by the correct stuff for the file you downloaded; use autocomplete in the terminal to assist you with it). A reboot and you should get going with your NVIDIA hardware. Once that's done go to System->Preferences->NVIDIA X Server Settings and find your second screen.

At Step2, incase ubuntu did boot into the x-screen, stop gdm by:
```
sudo service gdm stop
```. The screen might go blank, press Alt+F2 and log in through the terminal and run the driver software the same way as described above in Step2. Hope this works for you.

I have been using a dual screen myself since the last 1 year on a NVIDIA card with this method. Pretty much tried and tested.

---

### Post by jaimefma on 2011-09-11
Vijay Rao,

Did you try this with an Optimus card? As far as I know, the solution you expose, does not work because I have an Intel and a Nvidia card. If I install the Nvidia drivers it will try to use that driver with the Intel card and then it will crash. One solution is to disable the Intel card through the BIOS panel (if you have this option avaliable, not my case).

---

### Post by realzippy on 2011-09-11
Indeed will not work with Optimus.

---

