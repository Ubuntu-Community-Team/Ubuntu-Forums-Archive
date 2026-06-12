---
title: "[SOLVED] 3D effects not working"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by shalemjale on 2008-03-07
I have Gutsy Gibbon(GG) and an onboard ATI radeon xpress 200 series vid card (research says it will handle 3D effects). My problem is that I am trying to get compiz to work with the special effects. I have gone to desktop appearances and made changes but still see no spec effects. Now I am thinking that GG has not recognized /installed the drivers for the 3D effect to take effect. Am I in the right ballpark or off somewhere else?

Linux status:Ubuntu Newbie

---

### Post by overdrank on 2008-03-07
> **shalemjale said:**
> I have Gutsy Gibbon(GG) and an onboard ATI radeon xpress 200 series vid card (research says it will handle 3D effects). My problem is that I am trying to get compiz to work with the special effects. I have gone to desktop appearances and made changes but still see no spec effects. Now I am thinking that GG has not recognized /installed the drivers for the 3D effect to take effect. Am I in the right ballpark or off somewhere else?

Linux status:Ubuntu Newbie

HI and welcome, you may need to enable your restricted drivers located under system, administration. Also Envy has helped some users 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by shalemjale on 2008-03-07
Thanks for your suggestions. 
I tried both of your suggestions but was unable to get it to work. I enabled the restricted driver but the window that emerged did not provide the right options for selection. Thus I was set back to where I started after a restart.

---

### Post by SloYerRoll on 2008-03-08
So first thing: Go to System>Administration>Restricted Drivers Manager and make sure the check box beside your video card is ticked. (If it's not ticked, you'll see a red ball (I think). 

Once your driver is installed:
Open up a terminal session and type in the following:
```
glxgears
```
You should see three spinning gears, if you do. Then you have 3D enabled and your almost there! If you don't, you can't use Compiz until you can fix these gears. 

With terminal still open. Copy/paste the following: 
```
sudo apt-get install compizconfig-settings-manager gnome-art usplash startupmanager
```

This will install Compiz for you. I know it's already installed, but it doesn't hurt to do this :)

Best,

---

### Post by shalemjale on 2008-03-08
I saw the gears and reinstalled compiz (the restricted drivers shows that it is in use). However, the spec effects are still not working.

---

### Post by Pamphagus on 2008-03-08
stupid suggestion but I guess u have been to the 
system->preferences->Advanced Desktop Effect Settings?
and then u have initiated the effects -> animations or anything else u like and changed the settings there to what u like? 
I am running the 7.10 version though. I dont recall exactly but some effects were not initiated automatically and I was wondering what happened to the effects untl i enabled them

---

### Post by shalemjale on 2008-03-08
Yes, I have done that. I'm wondering what I am missing. Or is it just a ATI doesn't like Linux type thing so its gonna take a lot of tinkering?

---

