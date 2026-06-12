---
title: "Small MythUbuntu Review 7.10RC"
date: 2007-10-14
forum: Mythbuntu
---

### Post by pt123 on 2007-10-14
I just did a fresh install. These were the problems what I found with it:

The modprobe recognised my Leadtek Winfast 1000 DVBT card, but this card requires you to add cx88_dvb into the/etc/modules. I am surprised that it couldn't do this. Wasted half an hour because of that. After I added it to /etc/modules, I was able to scan the channels etc. 

Why is that default theme gentium (?) its grey and so depressing. Why not use the  default theme mythTV theme it is so inviting. 

Also why is the default XFCE theme that dull. It is depressing too, the guy that chose this should be put on suicide watch. 

Also with the remotes they have the Winfast 2000 DVBT, and Winfast 2000 XP as options but not the  Winfast 1000 DVBT. So my remote isn't working, I will have to play around with it. 

I am also wondering why is there such a big delay when scrolling down the menus, and changing menus? There needs to be a loading image that should appear, because many times you press the button twice or three times. I am using a P4 1.5 GHz computer. It takes 2 seconds to respond to an up or down input. Does it have anything to do with graphics card, because I haven't enable the restricted nvidia drivers. 

I was also a little disappointed that it couldn't automatically browse the network samba shares for videos & files. 

Apart from that it was quite good the installation went smoothly.

---

### Post by pt123 on 2007-10-14
I can't get it to play mp3s. When I try it crashes the mythtv front end.

It picks up the files. 

Is there some special key to play it ?

Do I need to install any mp3codecs.


The video library worked without any problems.

---

### Post by p$y on 2007-10-14
> **pt123 said:**
> 
Why is that default theme gentium (?) its grey and so depressing. Why not use the  default theme mythTV theme it is so inviting. 


Yes, I think there should really be another default theme.

---

### Post by laga on 2007-10-14
Hey, thanks for your great feedback!

> **pt123 said:**
> 
The modprobe recognised my Leadtek Winfast 1000 DVBT card, but this card requires you to add cx88_dvb into the/etc/modules. I am surprised that it couldn't do this. Wasted half an hour because of that. After I added it to /etc/modules, I was able to scan the channels etc. 


I think there's a reason why cx88_dvb is not autoloaded, but I can't remember why. Please file a bug report at [https://bugs.launchpad.net/mythbuntu/](https://bugs.launchpad.net/mythbuntu/)

> 
Why is that default theme gentium (?) its grey and so depressing. Why not use the  default theme mythTV theme it is so inviting. 


I think you are referring to G.A.N.T. which +is+ the default MythTV theme. What theme do you have in mind?

> 
Also why is the default XFCE theme that dull. It is depressing too, the guy that chose this should be put on suicide watch. 


File a (separate) bug about that, too, please. In the meantime, I'll trsy to make sure that our artwork guy does not hurt himself. ;)

> 
Also with the remotes they have the Winfast 2000 DVBT, and Winfast 2000 XP as options but not the  Winfast 1000 DVBT. So my remote isn't working, I will have to play around with it. 


Are you sure the existing entries for the Winfast remotes are not working? In case they're not working, try to google for a existing remote config and submit them to our bug tracker (again). If you can't get it work, feel free to request help in here.

> 
I am also wondering why is there such a big delay when scrolling down the menus, and changing menus? 
[..] 
Does it have anything to do with graphics card, because I haven't enable the restricted nvidia drivers. 


By default, OpenGL is used to render the menus. Without the proprietary driver, this will be slow. Either enable the proprietary driver or select the Qt painter in the "appearance" settings.

> 
I was also a little disappointed that it couldn't automatically browse the network samba shares for videos & files. 


You have high expectations. File a bug? :)

> 
Apart from that it was quite good the installation went smoothly.

Glad you like it. :popcorn:

---

### Post by superm1 on 2007-10-14
> **pt123 said:**
> 
The modprobe recognised my Leadtek Winfast 1000 DVBT card, but this card requires you to add cx88_dvb into the/etc/modules. I am surprised that it couldn't do this. Wasted half an hour because of that. After I added it to /etc/modules, I was able to scan the channels etc. 

This was an issue back during feisty that was introduced upstream in v4l-dvb. Can you post your dmesg when you don't add cx88_dvb to your modules? Multiple people using HD5500 cards (which also use cx88_dvb) have had no issues with this driver.

---

### Post by superm1 on 2007-10-14
> **pt123 said:**
> 
Why is that default theme gentium (?) its grey and so depressing. Why not use the  default theme mythTV theme it is so inviting. 

Also why is the default XFCE theme that dull. It is depressing too, the guy that chose this should be put on suicide watch. 

As said above, we are using the default MythTV theme which is GANT.  Plenty of other themes are shipped with the system, its just a matter of preference to what you choose.  Do you have a recommendation for a theme by default for the final CD image coming out in another week?

As for XFCE theme, the overall look is supposed to be a darker look.  For the next cycle we have some other ideas in terms of artwork and color schemes that we are planning.  If you are interested in helping to plan/choose something more eye appealing, please come and join us in #ubuntu-mythtv-dev or on our mailing list [email]ubuntu-mythtv@lists.ubuntu.com[/email].

> 
Apart from that it was quite good the installation went smoothly.

Glad to hear this :)

Thanks for all the feedback.

---

### Post by pt123 on 2007-10-15
> **laga said:**
> 
I think you are referring to G.A.N.T. which +is+ the default MythTV theme. What theme do you have in mind?

I thought the theme on this page was the actual default one:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
It was called mythcenter, and I have seen it around on other sites. That blue is really nice, esp. on TVs. The current makes people wonder if the saturation on their TV is off. 

> 
You have high expectations. File a bug?

It is just you had samba turned on, so why not go all the way. 

As you can see it is only a few steps 
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

> 
By default, OpenGL is used to render the menus. Without the proprietary driver, this will be slow. Either enable the proprietary driver or select the Qt painter in the "appearance" settings.

Strangely it was on QT, but then I swapped it to OpenGL and it was 10 times slower:). But then after enabling the proprietary driver it was very fast on OpenGL


> **superm1 said:**
> 
As for XFCE theme, the overall look is supposed to be a darker look.  For the next cycle we have some other ideas in terms of artwork and color schemes that we are planning. 
I don't mind the darker look but that blue/purple is dull & faded. If you could do something similar to the black look in Ubuntu studio would be good. 

I am real busy ATM I fill out bug reports later. 
_____________
Is there a way to
o get the mp3 playback for music files? 

I am able to listen to streams.

Is there a way to debug why the music playback is not working and crashing?

**Edit: music works now. For some reason the device in setting was listed as : ADSP. **

But when I changed it to Default, it started playing.

---

### Post by superm1 on 2007-10-15
> **pt123 said:**
> I thought the theme on this page was the actual default one:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
It was called mythcenter, and I have seen it around on other sites. That blue is really nice, esp. on TVs. The current makes people wonder if the saturation on their TV is off. 

Ah yes. Mythcenter is a nice looking theme, the only problem is that people immediately draw the comparison to Windows MCE because its so similar.  Just the same as there is the Pear-ody theme which looks great, but feels just like AppleTV.

Ideally setting the theme to something that gives it a MythTV look exclusively would be the way to go I'd think.  Perhaps once of Juski's themes instead.

> 
It is just you had samba turned on, so why not go all the way. 

As you can see it is only a few steps 
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

Oh I wish we had come across this sooner.  We'll leave it as a howto once our docs are ready, and get it setup by default for release.  The archives are already closed for improvements like this, so there isn't a chance of it happening before release.

> 
Strangely it was on QT, but then I swapped it to OpenGL and it was 10 times slower:). But then after enabling the proprietary driver it was very fast on OpenGL

This was a minor error on laga's part.  Qt is the default, but yeah for OpenGL you need a form of hardware accelerated drivers.

> 
I don't mind the darker look but that blue/purple is dull & faded. If you could do something similar to the black look in Ubuntu studio would be good. 

I am real busy ATM I fill out bug reports later. 

Ah you're referring to the splash screen.  I agree, but it was unfortunately a side effect of the limited amount of colors available for those splash images.  During Hardy you'll see something fairly different.

---

