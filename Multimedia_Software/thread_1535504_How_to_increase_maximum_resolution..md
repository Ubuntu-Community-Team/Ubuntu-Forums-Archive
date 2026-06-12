---
title: "How to increase maximum resolution."
date: 2010-07-21
forum: Multimedia Software
---

### Post by creative2innovative on 2010-07-21
I have a 17" CRT monitor but still ubuntu can't detect 1024x786 resolution it still has 800x600 resolution which is quite cumbersome to use.

$ xrandr      --    when i type the following command it tells that your maximum screen resolution is 800x600 so due to this reason i am unable to get 1024x786. I need help to increase the maximum resolution so that i can set it to 1024x786 one!!

---

### Post by creative2innovative on 2010-07-21
Is nobody here able to solve up this query!! I am fed-up of ubuntu now and i think i should quit using it!! :( :( :(

---

### Post by oldos2er on 2010-07-21
What video card do you have?

---

### Post by creative2innovative on 2010-07-23
I have video card of VIA chrome series. I don't have graphic card.Heartly thanks for replying....... :)

---

### Post by lykeion on 2010-07-23
Hi
I have no experience with VIA Chrome but it seems like it's not very well supported in Ubuntu, 
at least not as good as a "proper" video card like nVidia or AMD.

The reason for this is probably that VIA have chosen to not release any linux drivers. 
Linux users and the Ubuntu community are trying their best to solve problems like this in spite of 
no support from the hardware manufacturers.
An example of this is **_[OpenChrome]("https://help.ubuntu.com/community/OpenChrome")_** who provide open-source graphic drivers for the VIA chipset.

Anyway, what this means for you is that you'll have to work a little more to make it work for you. 
You'll have to ask in forums (like you've done here), search for solutions on the web, and try to fix it yourself. 
This can be very frustrating - been there myself years ago with a troublesome ATI card 
- but in the process you may be learning something about computers and hardware.

Since I have no experience with your hardware I can't give you any specific instructions on how you should proceed. 
So the first thing you should do is to find out your hardware specifics, like the name of your **computer model**, 
the **name of card** (Unichrome, Chrome9?) and the **name of the chipset** (could be something like P4M900 or VX800).
You'll also need to know some software specifics, like your **currently installed driver** (System > Administration > Hardware Drivers).
After you found out these specifics you should search the web and forums like this for solutions to your problem, 
using your VIA card name and chipset as your keywords. 

If you don't find any direct help this way you can post a new thread in this forum, but then I'd suggest you use your keywords 
in the thread title so that you'll attract readers with the specific knowledge you're after. 
"How to increase maximum resolution" is way too vague as a thread title.

This got a tad bit too long for an answer, but I hope you got something out of it anyway.

---

### Post by Yellow Pasque on 2010-07-23
This is pretty common with newer X.org. The problem is the monitor not sending (or X not reading its) EDID properly, and the default horizontal sync is set too low for higher resolutions.
See this to fix: [http://ubuntuforums.org/showthread.php?t=1525883](http://ubuntuforums.org/showthread.php?t=1525883)

---

