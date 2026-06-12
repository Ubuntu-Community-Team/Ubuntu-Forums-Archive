---
title: "blank (black) video"
date: 2009-11-03
forum: Multimedia Software
---

### Post by moorecf on 2009-11-03
I have been running UBUNTU for many years on my DELL PowerEdge SC440.   
Recently I have upgraded to 9.10 (three times from scratch), and each 
time my NVIDIA 6200 video card gives me a blank screen.   The analog 
screen signal works when I remove the card from the computer.   I have 
installed at least five different drivers.   I have never had any 
difficulty with video before 9.10.   
 
After upgrading, I get a blank screen when I use my NVIDIA 6200 video card.  
I have looked on the internet and found a more recent drive and tried to
install it, using the following commands.

sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

sudo apt-get update

sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190

After doing so, I get the following message:
=============================================
WARNING: You do not appear to have an NVIDIA GPU supported by the 
         190.42 NVIDIA Linux graphics driver installed in this system. 
         For further details, please see the appendix SUPPORTED NVIDIA 
         GRAPHICS CHIPS the README available on the Linux driver download 
         page at [www.nvidia.com](www.nvidia.com).
=============================================
Since the NVIDIA 6200 worked with the older ubuntu 9.04 OS, I think graphics processor is OK and that something else is wrong.  

Thanks for any advice !!!

---

