---
title: "[SOLVED] usb on bd-v1100 time-warner box?"
date: 2008-03-19
forum: Mythbuntu
---

### Post by elj4176 on 2008-03-19
Just switched from directv to time-warner HD on the main tv and a time-warner bd-v1000 stb on my mythbox. I have been using a serial cable to usb for my directv box to change channels and it worked great. 
I haven't tried with the time-warner box yet but I did see that I can get an irblaster if the usb route fails.

Anyone else have this box and using the usb?

edited to add:
it is now a v1000 not a v1100. this box has a usb port but it doesnt appear to work so far. Anyone have any input on getting this to work? I did find a page about the v1100 with an irblaster.

---

### Post by foxbuntu on 2008-04-02
> **elj4176 said:**
> Just switched from directv to time-warner HD on the main tv and a time-warner bd-v1000 stb on my mythbox. I have been using a serial cable to usb for my directv box to change channels and it worked great. 
I haven't tried with the time-warner box yet but I did see that I can get an irblaster if the usb route fails.

Anyone else have this box and using the usb?

edited to add:
it is now a v1000 not a v1100. this box has a usb port but it doesnt appear to work so far. Anyone have any input on getting this to work? I did find a page about the v1100 with an irblaster.
IIRC most of the time the STBs have usb but it is not an active data port that can be used for this. If the box has a DB9 Serial port that might be easier, if not I suggest the irblaster.

---

### Post by elj4176 on 2008-04-03
i have an irblaster with the lightup led but I still cannot get this to work. it makes my mythbuntu box useless and makes me wish I had stayed with directv. 
I find it hard to believe that I'm the only one with this box (pioneer bd-v1000) from time-warner.
is there a differnet stb that I shouls ask for? One that someone can help me get working with lirc? 

The instructions for the bd-v1100 are very complicated and did not work for me anyway.

---

### Post by elj4176 on 2008-04-14
An update - I was trying to change channels on my Pioneer Time-Warner bd-v1000 STB via lirc and serial blaster. I decided to switch to a USB MCE remote/Blaster setup and upgraded to 8.04. 
The Pioneer STB uses an AT8560 remote so during setup I had to select the ScientificAtlanta irblaster instead of the pioneer. This uses the SAE8000 remote config and works fine with this remote and STB. 

I suspect that the upgrade to 8.04 is responsible for getting the blaster working since it allowed me to select the blaster type and it config'd lirc for me. 
If anyone has any questions let me know and I'll try to help.

---

