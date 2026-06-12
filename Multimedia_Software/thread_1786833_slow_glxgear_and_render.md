---
title: "slow glxgear and render"
date: 2011-06-20
forum: Multimedia Software
---

### Post by xeyos on 2011-06-20
Hello, i've used ubuntu as main system from a few months to now and i'm finding my first big problem.
 I can use games and see movies without any problem, even using wine i can play wow at 40+ fps with medium/high options. 
 Recently i've downloaded and instaled ogre and found that, if i try to render the sample model.. it slows down. It says it is showing about 2kfps, but the model moves as if it was at 1 or 2 fps. By chance, i saw that if i open wow and then render the model of ogre, suddendly it goes smooth.
 Trying to find the problem, i went to the system test option of ubuntu11, when i arrieved glxgears test, it showed a really slow performance. Tried with wow opened and... magic!, it runs like hell XD.
 Then i tried calling glxgears from console, it says 9k+ fps, but again it went really slow! don't know whats happening.

 My specs:
Intel Quad core processor
Nvidia 8800GTX
4 GB ram

 I've installed the recommended Nvidia drivers. The xconf section looks like this
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

I saw that, in the "other drivers" application says that Nvidia driver is installed but not in use. I've readed arround the red that it is a known bug but doesn't matter. Anyway i tried to remove the driver and install int via apt-get, but it seems that if i install it via Apt, the system cannot restart, so i return to the old driver via ubuntu rescue.

¿Any clue of whats happening?
 Hope you can help, thank you and excuse my bad english

---

### Post by Yellow Pasque on 2011-06-20
Is vsync on?

---

### Post by xeyos on 2011-06-20
I was working arround this about now... i don't know exactly what that option is but it is posible to change it so.. i was trying. Originaly it was deactivate but, if i check it on the nvidia control panel, glxgears run smooth, but other render programs (such as ogre) continue with the problem.

 On this time i have deleted and reinstall all Nvidia drivers. Now i'm working with the ones you can download directly on Nvidia website. 

 I have now 3 computes with different hadware running now in ubuntu, all of them were installed identically by me. 2 of them are using Nvidia and 1 use ati. The problem exists in this (nvidia) and the one with ATI. The third computer seems to work properly. I can say that on this computer and the other with an Nvidia there are some software installed by me or my brother but, the one with an ati... is almost a fresh install.

New info: By now trying to test glx from the system testing option of ubuntu, do not show the window. The orgre project i was using to test... is not opening anymore...
I forget to say before that the glxgears seems to freeze the computer, not completely but it takes some second to do anything, even move the cursor.

---

### Post by xeyos on 2011-06-20
i've installed nvidia-cg-toolkit so the ogre project runs again, the same problem remains. The glx teststill not working and now glxgears from console goes slow even with the vBlank on.

---

