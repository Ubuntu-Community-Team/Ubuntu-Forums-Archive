---
title: "Trying to install 2nd monitor with 2nd card (8400GS) on Ubuntu 12.04"
date: 2014-05-10
forum: Multimedia Software
---

### Post by Clueless Wonder on 2014-05-10
Hi -

I am fresh off the retired-WindowsXP boat and trying to use a 2nd monitor to extend my desktop.  I have 2 video cards installed, the one that came with the PC and a 8400GS.  The PC one is working fine.  The 8400GS doesn't seem to be activated.  I ran a test I read about through terminal and it appears that the computer can see this card.  When I go to Display Settings, it only shows the one monitor and the ON-OFF switch is set to ON and is greyed-out.  When I click "Detect Displays", the button depresses, but nothing happens.  I checked the Additional Drivers and there is nothing detected.  I have tried many different avenues of installing NVIDIA drivers, but I am not totally clear which ones I need....if I actually need drivers or if it is another issue...if I need to to the XSWAT thing (and if I do that, what are the steps for that), etc.  I have purged NVIDIA , installed NVIDIA current updates, stopped lightdm, tried to install 331.67.run through the F1 terminal (only to be told it couldn't install due to Nouveau issues), and done some rain dances with no luck. 

 I feel like I am missing something really simple.  Can someone please help me?  I knew my way around XP really well, but still figuring out Linux.  I am not afraid of terminal, but need exact steps.  I really appreciate anyone that can work with me on this.

---

### Post by alex199 on 2014-05-12
I'm not an expert myself but i can try to point in the right direction. open terminal and post output of ```
sudo lshw -c video
```

---

### Post by Don_Tai on 2014-05-16
I, too, have been trying, unsuccessfully, to install multiple graphics cards into a Lubuntu 14.04 LTS desktop, and I have the dent in my head to prove it. Here is my thread, as yet unanswered: [http://ubuntuforums.org/showthread.php?t=2221317](http://ubuntuforums.org/showthread.php?t=2221317)

I believe ubuntu does not support multiple video cards. I quote myself:

> **Don_Tai said:**
> 

I believe that ubuntu cannot have 2 video cards in one computer, but want confirmation.

[http://ubuntuforums.org/showthread.php?t=2192417](http://ubuntuforums.org/showthread.php?t=2192417) says "Ubuntu is limited to 1 desktop per GPU". Two video cards would be 2 GPUs?
[https://wiki.debian.org/XStrikeForce/HowToRandR12](https://wiki.debian.org/XStrikeForce/HowToRandR12) says multi-board support is broken



There are many threads about multiple GPU installs, and all seem to get no reply, as I found in my thread. If you find a way please post up. Multiple video monitors need a single GPU with multiple outputs, such as a laptop or a specialty video card. Some people have been able to get two identical video cards to work. I have not seen a thread where two different GPUs in the same computer have worked. In Windows this is easily done.

---

