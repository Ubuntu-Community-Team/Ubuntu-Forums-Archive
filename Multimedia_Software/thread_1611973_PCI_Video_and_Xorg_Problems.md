---
title: "PCI Video and Xorg Problems"
date: 2010-11-02
forum: Multimedia Software
---

### Post by capsitan on 2010-11-02
Hello, I am getting really frustrated. I am trying to run Ubuntu (or any other Linux distro) with my ATI 
Radeon 7000 PCI card with no luck. Onboard video works fine but cannot use any graphical effects. I have gone through reinstalling ATI driver packages already and that hasnt worked. The only thing I think might work is by making and configuring an xorg.conf file. I have Ubuntu 10.10, which apparently doesnt use an Xorg.conf file anymore. I ended up making my own but after that the screen went blank and I couldnt figure out how to get back the old settings without reinstalling the OS. I am now trying to make another one but I am not sure where to go with this now. Other threads show that some other people have gotten their ATI Radeon 7000 card working with manually configuring the Xorg.conf file. I tried to do an Xorg -configure but then I get this display:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

I have tried to boot using PCI card with live CD as well with no luck, then forced to use on-board graphics. BTW chipset is Intel 810

I am really disappointed at the poor level of support by Linux and other distros. Someone please help!!!

---

