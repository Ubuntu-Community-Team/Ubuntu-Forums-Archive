---
title: "I need help setting up video cards"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by lordjoe_com on 2007-05-02
I have been reading the forums but nothing suggested seems to work.
I an running feisty faun on a Dual Core PC with 2GB Ram
I have an NVidea GeForce 5500 card running my center screen and 
a Dual head Matrox G550 running two side screens.
I have edited xorg.conf over a dozen times - sometimes blowing ny graphics environment and having to restore fron the command line. I have declared second monitors and second screens. 
I have listed and included the hardware cards.
Nothing works 


1) I cannot get either of the matrox screens to turn on.
2) I cannot get the center screen to display at 1280x1024. When I force that reesolution, the display is too high for the monitor as if the hardware was not set
3) After downloading the nvidea drivers
   sudo apt-get install nvidea-new (this is from memory)
 When the graphics environment comes up I get a HAL error
4) When I download the latest matrox driver and try 
   sudo ./install.sh 
I get errors - has anyone gotten these drivers to install properly

So my questions are
1) Where do I get the latest drivers given that the driver from matrox will not install  and what are their names
2) How do I restore the nvidea driver to a more usable state
3) Are there utilities that help set up these cards - The NVidea innstall had one but nothing on it worked

Does anyone out there have specific experience with a similar configuration.

Naturally all the hardware works fine on Windows XP .

---

