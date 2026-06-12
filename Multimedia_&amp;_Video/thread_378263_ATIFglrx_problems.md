---
title: "ATI/Fglrx problems"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by Godmanliving on 2007-03-07
Well, basically ive gone and shot myself in the foot.  I was using a wiki to install the ati/fglrx to setup direct3d rendering or opengl rendering so i could set up beryl and after following the guide step by step and double checking to make sure i typed things in right, I thought I had gotten it installed.  Unfortunatly, I was wrong.  When I boot Ubuntu now, the loading splash screen appears with a loading bar.  Ubuntu loads and as it trys to switch to the desktop, my moniter goes black, switching between digital and analog signals.  It flickers a bit and then goes completely black and the moniter lite flashs (indicating that there is no signal basically).  
I am a complete newbie at Linux, as in I just started messing with it a couple of weeks ago.  I just installed Ubuntu a day ago.  I dont really know what to do.  I dont know the terminal well enough to troubleshoot the problem in recovery mode.  One thing I do remember is that i set fglrx to blacklist when I was trying to install a newer version.  I dont know if fglrx is what renders the on screen stuff or how all of this stuff works.  Anyhow, my card is a radeon 9800.  If anyone can offer any help, it would be much appreicated.

---

### Post by sysdrum on 2007-03-07
Okay this is an issue to solve at the prompt type
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the on screen opts choose the vesa driver
that will get you back to the GUI
if you are using edgy you may need to visit the  ati wiki to setup the driver but it took me like 2 weeks to setup the driver last time and beryl still has issues with the 9000 series cards. there are hacks and stuff to get it working but you have to search high and low.

well if you need any help let me know I am working on setting up the fglrx in fawn right now..
I am running a 
nvidia gforce 440 on an  duron 850 drake 6.06 
ati 9250 on an athlon 1ghz fawn 7.04 --- :( Fglrx does not work but compiz does work by default on the  Radeon driver with xorg.conf edit
ati 9800 on an athlon xp 2ghz edgy 6.10 --- Fglrx works had to edit the xorg.conf and did not use the tools

---

### Post by Godmanliving on 2007-03-07
Thank you very much.  Would you be able to explain to me what Fglrx and Beryl are?

---

### Post by sysdrum on 2007-03-07
Okay on windows you have a Hardware driver that tells the XP or 2000 how to setup direct 3d or opengl settings plus how to behave in at different times. 
Well that is what Fglrx does for your xserver (base layer of your GUI)
Now you have 3 layers in your GUI (graphical user interface) 
You have your base layer that is your xserver that runs on top of your terminal or (outside of the terminal which is basicly what xserver does) then you have layer 2 that is GNOME or KDE or XFCE which they are your graphic shell layer they talk to you other hardware and allow you to play in your GUI 
Then you have Metacity or Compiz or Beryl they are windows mangers under gnome or kde or xfce
but Beryl is a combined window manager and composite manager it takes what metacity does in gnome and makes it look pretty. that is about it.
Atleast that is my take on things

---

### Post by Godmanliving on 2007-03-09
Ok, its not working.  Ive used the HOW TO guide provided here by the community, ive used ENVY, ive used one of the wikis and I either get no screen at all, or with the HOW TO guide, I got a blue screen with several error messeges.  There has to be a way to do this.  Any more tips?  (beryl installed at one point and running but i could not choose beryl as my window manager)

---

