---
title: "switch to disable compiz, ubuntu one,...  before install!!!"
date: 2010-06-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sartic on 2010-06-11
Every time I install LTS on older systems (example p4 celeron) I have slooow system until i disable compiz and bunch of things.

I know I will be attacked for this, but I have plenty old procesor here in my country.

Second thing i tried many time compiz but has problem width many appz and I _always_ disable and uninstall all trace of this program.

Metacity and maybe some new thing (unity) will have better compatibility width main appplications nowdays on job and multimedia.

---

### Post by taavikko on 2010-06-11
Compiz is only enabled in scenarios that hardware supports it out-of-the-box.

Ubuntu-one isn't running either by default.

---

### Post by sartic on 2010-06-11
Last time it enabled on old oxygen agp 32mb vga, p4 celeron and only 256MB.
They should enabled only if 1GB or more memory if you ask me and VGA is newer!

Ubuntu 1 I do not use, but it is installed (see above for example system)

---

### Post by orlox on 2010-06-11
It's very hard to justify the inclusion of this options in the default installer. Not because they don't make sense, simply because the default ubuntu installation comes with so much stuff, you can't satisfy everyone on this.

Perhaps people don't want openoffice, others don't want bluetooth modules, perhaps you will never need accesibility tools, you don't want evolution, etc...

If you go further, and add the posibility of adding app choices, then things even get worse...pidgin instead of empathy, thunderbird instead of evolution, chrome instead of firefox, and a LARGE etc...However, choices are not very well seen in canonical, since the ideal is to keep one choice of app for each task, in order to normalize documentation.

But well, in the end, if canonical would comply to all this disabling options, then installing ubuntu would become so cramped with checkboxes and possible decisions that it would probably turn out very confusing.

---

### Post by sartic on 2010-06-11
The main problem is that Ubuntu switch on compiz even there is no suitable system requirments. Look above for one example. I can add many more.
For me min. req. to turn on compiz after install is real cpu (not celeron), PCI-E VGA 256MB, 1GB RAM. Not celeron, not oldish agp vga and not only 256MB.
The second problem is look for statistics, ask people if they use compiz in real life.
They can put many appz on cd they want. But Firefox, Thunderbird, VLC, Pidgin, GIMP, etc will be installed in high statistics after 1st install of Ubuntu.

---

### Post by tomillares on 2010-06-11
I have 2 Gb of ram, and I've disabled compiz, because I need a virtual machine runing almost always, and compiz made my machine slower.
I recommend you to use [lubuntu]("http://lubuntu.net/"). I've tried it a bit, and it works fine.

---

### Post by sartic on 2010-06-11
i remove compiz width:

sudo apt-get remove compiz-core libdecoration0

---

### Post by ranch hand on 2010-06-11
> **sartic said:**
> i remove compiz width:

sudo apt-get remove compiz-core libdecoration0
If you boot to recovery on your first boot you can do it from there.  Saves having craziness on that first boot.

---

### Post by ronacc on 2010-06-11
I have installed Ubuntu many many times and I have never had compiz enabled without my specifically enabling it after startup either by using system>preferences>appearances>effects or installing fusion-icon and activating it that way . Just because something is installed does not mean it is automatically active all the time  .

---

### Post by x-shaney-x on 2010-06-11
> **taavikko said:**
> Compiz is only enabled in scenarios that hardware supports it out-of-the-box.

Ubuntu-one isn't running either by default.
Just because hardware supports it, doesn't mean it will run well.
A new user who doesn't understand what compiz does or has never even heard of it could well install ubuntu and think "WOW! this runs like crap, back to windows"

I think a better solution would be to have a popup on the first-run of the desktop saying that your computer is capable of running compiz but warn it may affect performance, ask if the user wants to enable it and also explain how to disable it again later.

As for ubuntu one, it is listed in my startup programs and I didn't put it there so I would say it certainly is enabled by default.
I think this could be handled the same way as compiz with a first run pop-up.

I don't think EVERYTHING should be handled this way but certainly things that can have a large impact on system performance.

---

### Post by x-shaney-x on 2010-06-11
> **Chauncellor said:**
> If you're looking for super lightweight, then look at the derivatives. Ubuntu cannot cater to age-old computers and still expect to go forward. I've run Ubuntu very well on a decade-old computer.
I run compiz on my comp and it runs very well.
Same goes for the missus' laptop.
But I have an old computer for experimenting, effects AREN'T automatically enabled for that comp and it runs adequately without them.

Finally, I have an old crappy laptop.  When I installed Lucid on that compiz was enabled on the first boot.
It ran ok-ish but once a few windows were open everything was jumping around the screen and it was grinding to a halt. Once I disabled it the comp was running well enough again.

The point is, in THAT case compiz WAS having an impact on performance but I knew exaclty what was causing it and how to disable it.
A complete novice to ubuntu using that same comp would have probably just assumed that either the comp wasn't capable of running ubuntu (which it is) or would have just assumed ubuntu is a boated waste of space.

---

### Post by JohnnyC35 on 2010-06-11
> **Chauncellor said:**
> If you're looking for super lightweight, then look at the derivatives. Ubuntu cannot cater to age-old computers and still expect to go forward. I've run Ubuntu very well on a decade-old computer.

Would it not be possible to have a Standard/Custom option during install so that if people chose Custom they can not install Compiz, OpenOffice, etc and then after installation they can install what they want:confused:

---

### Post by ranch hand on 2010-06-11
> **Chauncellor said:**
> If you're looking for super lightweight, then look at the derivatives. Ubuntu cannot cater to age-old computers and still expect to go forward. I've run Ubuntu very well on a decade-old computer.
If you look at the specs for my box, see sig, I do not need light weight.  What I do not need is compiz.

I have another, much older box (hpl pavilion xt993) which has all the ram it can carry (512Mb) and it has no trouble with compiz at all.

Yes, it is not supposed to be enabled unless the hardware can handle it.  I has always been enabled on this box and until 9.10 just really screwed with me.

It is interesting to me that the HP did not have it enabled.  I had to do that and it was no problem at all.

I do not like compiz so it is not in use anywhere here.  I am not sure why anyone likes it but boy, say anything negative about it and the fanboys are upset and on your case.  I do not care what crap you want on your box.  I do not like being called a liar when I simply state facts that contradict some folks "religion".

The OP has a problem that is not all that strange or unusual, particularly on older hardware.  All he wants is a simple solution (a switch in install is not that) to a real problem with an app that is good for nothing but eye candy for folks suffering from sensory deprivation and probably a short attention span.

---

### Post by JohnnyC35 on 2010-06-11
My system can handle it and I remove it when ever I install. Takes up CPU power that can be used else where, and it's ugly and distracting. ... well with exception of the Alt-Tab thing where the windows cycle thru.

---

### Post by ranch hand on 2010-06-11
> **JohnnyC35 said:**
> Would it not be possible to have a Standard/Custom option during install so that if people chose Custom they can not install Compiz, OpenOffice, etc and then after installation they can install what they want:confused:
The Cd is pretty crowded right now.  Even a DVD is going to be too small if you go for all the options different folks may want.

There is such an install available, now, for people with a good internet connection.  Netboot install.

To use that for not having compiz would require you to really know the packages for the gui really well as the Ubuntu Desktop and the Gnome Desktop meta packages will both install it.

It is a lot easier to just remove the lib.

---

### Post by JohnnyC35 on 2010-06-11
> **ranch hand said:**
> The Cd is pretty crowded right now.  Even a DVD is going to be too small if you go for all the options different folks may want.

There is such an install available, now, for people with a good internet connection.  Netboot install.

To use that for not having compiz would require you to really know the packages for the gui really well as the Ubuntu Desktop and the Gnome Desktop meta packages will both install it.

It is a lot easier to just remove the lib.


What I meant was, you have a list of what will be installed and if you don't want it installed then you just uncheck it and it's not installed. Then after Ubuntu is installed they would go thru Synaptic or apt-get or whatever and get the software they want. So that if they don't want Compiz, then it's not installed. If they don't want OpenOffice then it's not installed and they don't have to search out lost files/dependencies, and then after installation they can install AbiWord, or whatever. This could cause an issue for people without an internet connection, but it would be easier than a Net Install I would think.

---

### Post by JohnnyC35 on 2010-06-11
or if it were possible a GUI version of PerfectMinimal from andyduffell.com : [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by ronacc on 2010-06-11
My aging (more than 10 year old)"stable" system with an FX5200 and 128 mb vram handles compiz with no problem , even my early mogel eee 4g with an 800 mhz ( throttled  to 600 mhz by asus ) celeron and shared mem Intel graphics only takes a minimal performance hit . If your box is struggling with it you might want to consider a new box .

---

### Post by sartic on 2010-06-12
> **ranch hand said:**
> If you boot to recovery on your first boot you can do it from there.  Saves having craziness on that first boot.

thx, i will try this idea!

---

### Post by 23meg on 2010-06-12
> **Chauncellor said:**
> 
Compiz being activated on a low-spec machine that wouldn't be able to handle it is a bug. Report it. Such machines are blacklisted. Going ape-nuts and asking for yet ANOTHER option for going out of our way to solve ANOTHER problem that a small minority of people have is hardly needed.

Quoted for emphasis. 

Here's a sample bug report:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/513950](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/513950)

---

