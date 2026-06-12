---
title: "Jaunty upgrade:NO display: Screen issues"
date: 2009-05-02
forum: Multimedia Software
---

### Post by trustnone on 2009-05-02
I upgraded to Jaunty and after that there are multi-colored lines on the screen and i cannot use the laptop (gateway MT3707)

I cannot boot to recovery mode also (press ctrl+alt+F1).
When i get through the ubuntu loading screen: ubuntu image with loading bar on the bottom of the image.I get a screen with lines on it.

When i press escape in the beginning i get to grub> and  
aticonfig --initial
aticonfig --acpi-services=off

will not work there.

Please let me know how to get to recovery mode.

thanks a lot.

---

### Post by trustnone on 2009-05-03
When i try to run the command 
aticonfig --initial
aticonfig --acpi-services=off

IT gives an error saying no device found

After working on this further i went into recovery mode and added in the xorg.conf file the following information

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection


Now when ubuntu loads up i see two small ubuntu signs on the screen

Thats really funny. 

Any help will be really appreciated. 
thanks.

---

### Post by trustnone on 2009-05-03
Created a Ubuntu CD and i was able to login with the Live CD and ubuntu works.

Is there a way now that i can configure ubuntu so that the display is correct and i can use ubuntu without the CD.

Any help would be greatly appreciated. 

Thanks.

---

### Post by trustnone on 2009-05-03
So the graphics and et all works with the Live CD but it does not work when i boot without the CD.

What are the files etc that i have to change. 
Please advise.

---

