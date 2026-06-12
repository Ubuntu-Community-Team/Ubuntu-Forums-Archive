---
title: "loop based mixing"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by notjohn101 on 2006-07-08
is there a linux equivient to "Acid Pro 5.0"?

---

### Post by Xzallion on 2006-07-08
I think [Hydrogen]("http://www.hydrogen-music.org/") will be the closest you will find.

---

### Post by Sheik Yerbouti on 2006-07-09
Actually Hydrogen is a pattern based drum sequencer and sampler and Acid is a loop based arranger. Really there isn't a loop based arranger like acid that I know of on Linux. You could run Acid 5 under vmware because being a loop based arranger it is not so sensitive to latencies like a DAW would be. 

Also you could try using a multitracker DAW like Ardour with loops. Simply control click your loop to duplicate it and add more dupilicates to paint your loops. One thing Acid does that I am not sure if ardour does is automatically match the key and tempos of your loops. I am guessing ardour does not do this automatically though it may be able to do it somehow. 

Your best bet at this point for a true acid like experience is to run acid under vmware.

One other thing to consider is that loop based arranger is not nearly as liberating creativity wise as using a full on sequencer. A good step up which should provide a nice transition for you would be something like LMMS [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) which aims to be a fruity loops clone. It uses samples and a pattern based sequencer to build patterns (loops) and then you string the patterns together to make songs. Pretty easy really. Version 0.1.2ish is in the repositories. If your really comfortable compiling stuff you might try the cvs version which is coming along nicely. It is early days for this project so the cvs may be a bit buggy. I have found disabling some visual stuff like track indicators makes it stable enough for daily use. Here's a resonably good compiling LMMS how to [http://lxer.com/module/newswire/view/55195/index.html](http://lxer.com/module/newswire/view/55195/index.html)

Cheers

---

### Post by notjohn101 on 2006-07-09
so i guess "vmware" is a kind of windows emulator in a way?

---

### Post by Sheik Yerbouti on 2006-07-09
vmware is virtualiztion technology it allows you to run a virtual computer complete with bios, drives, networking , usb etc... With vmware you can run guest operating systems under other operating systems. The vmware player is free as in beer. See [here]("http://www.hackaday.com/entry/1234000153064739/") for a quick how to on creating a Windows XP virtual machine for the free vmware player. 

This assumes you have a valid Windows XP license and CD and valid copy of Acid 5. You actaully install Windows XP under the virtual machine. What you end up with is actually Windows XP not an emulation mind you but actually two operating systems running at the same time Linux and then Windows running in the virtual computer. 

From a compatibility standpoint it's really Windows so your programs run fine. That is assuming you have a resonably fast PC. I have a 3.8 ghz P4 with 2gb ram and I run vmware player for all sorts of Windows apps I dont want to give up like Macromedia Flash Pro and yes even Acid 5. Works great on this rig speed wise feels just like actually being in Windows alone. Games are a non starter for the most part beyond the very simple but productivity apps work well. A true digital audio workstation (DAW) like Ableton Live would work but the latencies would likely be higher than what anyone would want to deal with. I think I succesfully got 22 msec latencies from it though using FL Studio 6 using plain old wdm audio drivers. One thing to note though vmware is incompatible with any kernel that has been patched with the realtime preemption patch. It works fine with the stock Ubuntu kernel though.

---

### Post by th33nd0fy0u on 2006-07-18
Im sorry for reviving this post but:

I am VERY new to linux and I cant figure out how to install lmms.

The link you gave [here]("http://lxer.com/module/newswire/view/55195/index.html") didnt help me much at all... = /

I tried to run configure but it would not work.

And dont get me started on the Terminal.....  I had to use a basic linux shell years ago when learning C... pfft, so much for that.  I cant remember a thing.

---

### Post by huwshimi on 2006-07-18
> **th33nd0fy0u said:**
> Im sorry for reviving this post but:

I am VERY new to linux and I cant figure out how to install lmms.

The link you gave [here]("http://lxer.com/module/newswire/view/55195/index.html") didnt help me much at all... = /

I tried to run configure but it would not work.

And dont get me started on the Terminal.....  I had to use a basic linux shell years ago when learning C... pfft, so much for that.  I cant remember a thing.

You can get a slightly older version by using Synaptics package manager and searching for lmms.

---

### Post by th33nd0fy0u on 2006-07-18
I installed it but I do not see it listed in my applications menu. :(

---

### Post by huwshimi on 2006-07-19
> **th33nd0fy0u said:**
> I installed it but I do not see it listed in my applications menu. :(

If you type <ALT>-<F2> then type "lmms", press enter and it should run. If you want to add it to the menu then ask and I'll explain how.

---

### Post by th33nd0fy0u on 2006-07-19
> **xi0nblue said:**
> If you type <ALT>-<F2> then type "lmms", press enter and it should run. If you want to add it to the menu then ask and I'll explain how.

Ah ok.  That was easier than I was expecting. :D 

I dont believe I will need it in the menu... too much clutter.

But I am having some trouble with my audio.  I made another post [here]("http://www.ubuntuforums.org/showthread.php?t=218640") in the forums.

---

### Post by drycellbattery on 2006-08-01
Linux does have 2 loop based apps: Freewheeling and Sooperlooper. However, I think they are very different than Acid or Live. I know that Freewheeling is avaible to Ubuntu users, but I think Sooperlooper isn't. Freewheeling has some helpful video tutorials at it's website: freewheeling.sourceforge.net I think. It's simple and fun to use. I haven't tried sooperlooper yet.

---

