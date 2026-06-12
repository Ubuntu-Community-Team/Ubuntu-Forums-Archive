---
title: "Blacklisted Graphics Chip"
date: 2011-07-07
forum: Multimedia Software
---

### Post by moorhead98 on 2011-07-07
I have a vista-era Sony Vaio VGN-SZ340P laptop, with a Nvidia GeForce Go 7400 graphics chip. The chip works fine for most 3d things, but unfortunately, the chip (or driver, not sure which) is _**blacklisted**_ by Ubuntu.  ](*,) 
Because of that, Unity 3d wont work, and neither will compiz. Is there any way to get compiz working? i figure that if i can get compiz working, unity will follow.
Any ideas? I'll try anything

---

### Post by Yellow Pasque on 2011-07-08
Use Unity 2D

---

### Post by BicyclerBoy on 2011-07-08
Have you installed the proprietary hardware driver ?
Any version from nVidia 173 to 275 should work okay..

---

### Post by logodesigner on 2011-07-08
What is the exact issue you facing, are you simply not able to see 3D unity or you can with some issues (viewing graphics properly). If your 3D Unity is not working at all then you should try 2D Unity, otherwise elaborate the exact issue so solution can be proposed.

---

### Post by moorhead98 on 2011-07-08
> **logodesigner said:**
> What is the exact issue you facing, are you simply not able to see 3D unity or you can with some issues (viewing graphics properly). If your 3D Unity is not working at all then you should try 2D Unity, otherwise elaborate the exact issue so solution can be proposed.

Its strange... I can easily log into regular unity 3d ubuntu, but the dash and launcher are identical to unity 2d (which i got when 3d didn&#8217;t work). I can open up applications, but when i go fullscreen, the launcher just stays there. it doesnt hide, it just stays there, annoyingly in my way. also, workspace switching doesnt exactly work, except for when i use control+alt+right_arrow. and compiz doesnt work, still. any ideas?

---

### Post by moorhead98 on 2011-07-08
@Bicycler Boy, i have used and tested the 173 and version current drivers. they work great for 3d games and stuff, but not at all for compiz or unity3d.

---

### Post by BicyclerBoy on 2011-07-08
Are you running 11.04 ?
From my limited understanding...
11.04 unity 3d uses compiz
10.10 netbook edition unity 3d (broken) used mutter.

A low powered netbook runs 11.04 unity3d fine so your video card could be okay.

---

### Post by moorhead98 on 2011-07-08
> **BicyclerBoy said:**
> Are you running 11.04 ?
From my limited understanding...
11.04 unity 3d uses compiz
10.10 netbook edition unity 3d (broken) used mutter.

A low powered netbook runs 11.04 unity3d fine so your video card could be okay.

I am currently running 11.04. and i think that those quirky little netbooks use low power intel graphics cards. but on my laptop, i use a nvidia geforce go 7400 grahics card. it works exceptionally with everything _**except**_ for unity 3d and compiz.  i can log into regular ubuntu, but it shows something similar to unity  2d, and whenever i maximize something, the launcher doesnt hide (see  attached picture).i think the reason why is because the card is on the blacklist (this link might be helpful: [http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)). From my limited knowledge, Unity checks if the cards are blacklisted, as does compiz. if they are blacklisted, then the programs do not function properly. that is the case on my laptop.
how do i fix this? is there a workaround?

---

### Post by BicyclerBoy on 2011-07-08
Yes those quirky netbooks typically use intel chipset graphics GMA900 (old crap ones).

That posted link seems to contain all required info..
Just use the legacy 173 driver & edit the one file...

Did this not work for you ?

Maybe there is an auto-hide setting for unity3d dock/launcher ?

---

### Post by moorhead98 on 2011-07-09
> **BicyclerBoy said:**
> Yes those quirky netbooks typically use intel chipset graphics GMA900 (old crap ones).

That posted link seems to contain all required info..
Just use the legacy 173 driver & edit the one file...

Did this not work for you ?

Maybe there is an auto-hide setting for unity3d dock/launcher ?

I tried what happened there, but it didnt work. not sure what i did, but whatever happened did nothing. and im using the 173 driver now. going to see if unity works with it

---

### Post by moorhead98 on 2011-07-09
Good news! this youtube video helped sort things out: [http://www.youtube.com/watch?v=5F4VsEc-Arc](http://www.youtube.com/watch?v=5F4VsEc-Arc)
I dd what it instructed. when i logged into regular ubuntu the first time, it just froze on me, and i could only move the mouse. then i hit the button for screenshot, and hit enter a couple of times. it saved (i could tell later on), so the problem was the windows were invisible. then i shut down the computer, logged into classic mode, but the launcher was still there(?). i shut down and restarted again, and, Viola! unity 3d just started working, out of the blue. not sure why, but im glad it did! Also, compiz stuff like snapping and wobbly windows work too!! Yay!
thank you so much for your help

---

### Post by moorhead98 on 2011-07-15
Yay! its working now. 
Not sure why, but i guess u just had to log in/out or restart a bunch of times for it to take effect
Thanks for the help

---

