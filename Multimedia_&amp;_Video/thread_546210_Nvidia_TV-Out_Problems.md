---
title: "Nvidia TV-Out Problems"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by playing_with_matches on 2007-09-08
NOTE: I accidently put this post in Hardware at first, so if a Mod is reading this, please delete the Hardware/Laptop version. Thanks!

I'm trying to get TV-OUT (through a S-Video cable) to connect to my TV. I have the glx driver installed (which works great, I have the desktop cube and whatnot working), but anytime I use nvidia-settings to enable TV-OUT, it completely kills Xserver, and I need to run dpkg-reconfigure!
 I am using a GeForce4 MX 440 with AGP8X.

Any advice is greatly appreciated! Thanks!

---

### Post by Telecaster72 on 2007-09-08
Did you try NVTV? It's a gui-program that is in the feisy repo's, it works fine for me, the only bad thing is that you cant save your settings and you have to set your resolution to 800x600 first or else you cant reach your whole desktop because nvtv automatically changes your resolution to the res you have chosen for the TV. It's not the ideal solution, but i made a "movie" user that i log in as with the right resulotion and all moviestuff i use on the desktop that i log into whenever i use TV out...

I know there is probably better ways if you are into xorg editing though, leaving that issue to those who knows more....

Good Luck!

---

### Post by playing_with_matches on 2007-09-08
Hey!  Thanks for letting me know about NVTV.  Unfortantely, I just tried it, and it just turned my monitor black, with nothing showing up on the TV...

---

### Post by Jose Catre-Vandis on 2007-09-08
Try Twinview settings - (search forum for "twinview")  :)

---

### Post by playing_with_matches on 2007-09-09
Hmm... I looked it up, and tried to enable TwinView under nvidia-settings.  I get the error message: "Failed to associate display device 'TV-0' with X screen 0.  TwinView cannot be enabled with this combination of display devices."

I'm really at a lost on how to get this to work in Ubuntu... and as much as I hate to admit it, it works in Billy's ole' operating system(i have a dual boot), so I know it's possible.

---

### Post by Telecaster72 on 2007-09-10
I have gotten the black screen on my monitor also a couple of times...i just dont remember how i got it, make sure you have "dualview" under settings checked (in nvtv), All i do when i use it is choose 800X600 large and and "convert" under config checked to get color, "apply" and "TV on"

I get the same errormessage when i try in nvidia-settings, i will try to do using xorg someday, but for now this works... i have a GeForce 3 Ti200 btw

You can also add the twinview in xorg.conf somehow if your card supports it that is, do another search on twinview and xorg.

I know how annoying it is when it works in XP and not here in Ubuntu, hope it gets better with Gutsy, no way it will make it mainstream until a working TV out is implemented, most people i know have their TV hooked up with their computers (atleast those of them who are lousy criminal filesharers ;) ehrm...

Anyway i hope you get  lucky in getting it to work!!

---

