---
title: "Is hdmi audio possible to set up with my setup?"
date: 2012-05-28
forum: Multimedia Software
---

### Post by crazyjust on 2012-05-28
Hello. I would first like to say, I am not very knowledgeable about hardware and drivers with ubuntu. I have a hp dc5750 sff and ubuntu 12.04 64 bit. I have 2 ports (integrated video) vga and dvi. I have my monitor hooked up to vga, and my tv hooked up to the dvi with a dvi-hdmi adapter. I am also using the onboard sound. I have not installed any drivers, and nothing comes up for it in system tools > system settings > additional drivers. My problem is, I can get a good picture on the tv with hdmi, but no sound. I am comfortable using the terminal if I know what commands to run. Any help would be appreciated. Thank you

---

### Post by jms1989 on 2012-05-29
I'm just going to note that onboard graphics normally do not have the circuitry provide audio through the same connectors. I just know that the nvidia gtx series can do it so unless your system actually shows a audio device in lspci with the same controller as the video device, it won't be possible.

---

### Post by crazyjust on 2012-05-29
Thank you. I wasn't aware how that worked. I have much to learn.

---

