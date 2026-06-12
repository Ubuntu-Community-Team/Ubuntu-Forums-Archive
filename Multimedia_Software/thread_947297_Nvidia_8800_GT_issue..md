---
title: "Nvidia 8800 GT issue."
date: 2008-10-14
forum: Multimedia Software
---

### Post by Recesange on 2008-10-14
I am very new to Linux as a whole, and decided to just jump in to see what it has to offer. I have Ubuntu hardy on my system at the moment, because I read that it was the most novice friendly distro out there. I do plan to install Fedora Core and others after I get the general gist of things, but I am having some issues with my video card driver. I plan on sticking around and learning everything I can, but I am the kind that gets stuck on an issue and can’t move on until it is resolved. 

I currently have a Nvidia 8800 GT video card. The first day that I was poking around with Hardy, I came across an option to enable desktop effects, which I did, and was prompted with the option of loading the restricted drivers that were necessary in order to enable my card to do 3D acceleration. I followed the prompt and installed the drivers. It then prompted me to reboot in order for the changes to take effect. The system rebooted, and everything seemed fine, except after the Ubuntu screen with the load bar, the screen went black, but I heard the sound transition as though it went to the splash screen, but I was unable to see it. Then my monitor started to try and detect a signal on both analog and digital channels. I pushed the system power button and could then see the Ubuntu power down screen as the computer shut off.

I booted to my Windows hard drive and researched a bit. I went back to my Ubuntu drive and went to recovery mode, and removed the drivers with the command line. I rebooted and everything worked fine. I then tried loading the drivers using Envy, and had the same situation. So I removed the drivers that envy had installed, and was able to once again see. 

I don’t know if I am doing something wrong or if the new drivers are making my card send the signal somewhere else being that my monitor appears to indicate it is receiving no signal after the ubuntu loading screen. I have tried 3 ways total of installing the drivers and all come to the same end of the road. So I assume the drivers are loading properly but that my cards settings are being changed to where the signal is being rerouted or lost before they get to my monitor. Any help, suggestions or miracles welcomed. 

Again I am completely new so talk slow, and as though I was a baby. Well maybe not with goos and gaahs.

---

### Post by Artemis3 on 2008-10-17
Check my little guide, or try the new Ubuntu 8.10 which hopefully has newer drivers.

---

### Post by Recesange on 2008-11-03
Well i did a clean install of 8.10 on a separate partition, and this time when i loaded the restricted drivers when prompted to, my 8800 gt was up and running completely fine. 

I never did get it to work under 8.04 (even with every work around i read), and eventually had to switch to an old ATI x800 XL just to get my 3d rendering up and going.

---

