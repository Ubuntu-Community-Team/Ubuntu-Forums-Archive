---
title: "Screen wont 'wake up' after swithcing off automatically"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by schweini on 2008-02-27
I updated my nvidia drivers to version 169.09, and that took a while, and quite a lot of tweaking (kernel layer didn't recompile correctly). I finally got it working, but now i have the following problem:
If my HP Pavillion dv6000 switches of its monitor after 45 minutes of inactivity, the screen wont turn back on - i can see the cathode tubes lighting up, but the screen still remains black. CTRL + ALT + Backspace fixes this, but this is obviously very annoying.

Any pointers where i could check what is happening here?

Thanks,

M.

P.S.:the installer required the 'noacpi' kernel option, and it still says that in my grub menu, and numerous threads say that that is almost obligatory for this laptop. yet, when i manually boot without thoat parameter, everything seems to work fine, but the screen still wont wake up after 'sleeping' (not suspending - that is another issue :(  )

P.P.S.: i forgot the specs: Hp Pavillion dv6000, nVidia MCP51 chipset, GeForce 6150 Go videocard running on Ubuntu 7.10 Gutsy

---

### Post by ghstridr on 2008-05-29
I've got the same issue with a dell precision 690 with a nvidia Quadro FX 550 hooked up to two Dell 20"lcds via DV connections.
The driver version from nvidia being used (installed by Envy) is:
1:169.12+2.6.22-14

When the machine sits idle, the monitors go to sleep (as directed by the vid card).  I hit a key on the keyboard or shake the mouse and only the #2 screen comes up.  I have to hit ctrl-alt-bkspc to restart X and login again.  
Really annoying.

Btw, the nvidia driver is set to use TwinView to stretch the one desktop across both monitors

Running Ubuntu 7.10
(Can't run 8 yet because vmware server won't compile and I need it)

---

