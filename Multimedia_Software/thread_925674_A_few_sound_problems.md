---
title: "A few sound problems:"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Evanagar on 2008-09-20
First off, I want to say that I'm very new to Ubuntu.So very detailed descriptions of how to do things are very much appreciated.

Ok, one of the problems that I'm having and would like to solve is that to change my audio master volume (not in the individual programs) I need to click on the Volume Control and select the device (USB headphones) and change the volume there. I would like to make it to where my default master volume in the taskbar is the USB headphones, not the line out. 

A second problem that I'm having with the volume control when I enter the Volume Control is that in the audio slider bars, the left volume keeps going down on its own when I open the control. My mouse is nowhere near the slider for the volume and I'm not pushing any buttons. Also, when I try to bring the left ear volume up by locking left & right volume the left's desire to go down overrides my mouse pulling up on the right slider bar. Any input on this would be appreciated.

Another thing that I'm looking to do is be able to use the volume up/down button on my Logitech USB headset. I'm not sure if this is possible in Ubuntu, but if it is I'd love to be able to. 

I'll label these 3 problems separately so that any responses can focus on individual problems I'm having here. Thank you for the input.

---

### Post by oobe-feisty on 2008-09-21
i think i can help one of your problems install asoundconf if its not already installed 

"sudo apt-get install asoundconf"

then do asoundconf list

the out put should show you your mobo sound card and your usb headphones 

then do 

asoundconf set-default-card "usb-headphone"

usb-headphone is the name of your usb headphone that was listed you can from now on add that command to your auto start like rc.local

or 

according to this[ thread ]("http://ubuntuforums.org/showthread.php?t=18926&highlight=mips&page=2")you can edit /etc/modprobe.d/alsa-base and set you default card there i have done this way before but i use asoundconf as i dont very often use my headphones and prefer my onboard sound to be default



EDIT: sorry i misread you question you probably dont need to know what i wrote above as you most likely have that sorted but just letting you know that you can select master channel from kmix im not sure how many kde apps will install if you try to do this also give alsa-mixer a try i cannot tell you if that will work

---

### Post by markbuntu on 2008-09-21
You can also get asoundconf-gtk to choose a Default Sound Card in System/Preferences. If all you want is multimedia button control over your usb headphones you can select them in Volume Control/Preferences on the panel.

---

