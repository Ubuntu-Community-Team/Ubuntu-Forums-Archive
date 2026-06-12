---
title: "Nvidia failed to load kernal module"
date: 2011-12-01
forum: Multimedia Software
---

### Post by adnpearce on 2011-12-01
I know this is a simple one but after 3 hours trying stuff from the stickys im afriad i have to ask for help.
 
Computer worked fine for last year or so then today wont run games or play any sounds from any port. On startup i get low graphics mode warning box saying it cant load the NVIDIA kernal module and that no drivers avialble.
 
Going into admin/hardware drivers/it shows an NIVID accel graphics driver 'activated and currently in use'
 
All plugs are corect and mutes turned off - alsamixer confirms this
 
Going into admin/NVID xserver setting brings up a box saying 'you dont appear to be using the nvis x driver - please edit your x config file (just run nvidia-xconfig' as root) and restart the x server. Ive done the first part of that with a sudo nvidia-xconfig and it just says its backing it up. dont know how to restart the x server (ive tried ctrl/alt/backspace). doesnt fix anything
 
Also tried downloading latest driver from NVIDIA but when i try to run it in a terminal window (from a copy on the desktop of the .RUN file) it says must be run as root - i dont know what that means sorry. Just running it without the terminal woindow doesnt appear to do anything.
 
Ive taken this computer overseas full of films to watch and have no TV here - help !
 
Its an Acer Aspire Revo basic one with NVIDIA ION built in, running Ubuntu 10.04 LTS and please note the Revo is NOT on the internet -anything i want to put onto it has to be downloaded on my windows laptop and moved across by memory stick. 
 
Incidentally, I think the wireless on the revo has gone down too, or maybe my neighbors have all just turned off their routers ?!? - could this be connected ?
 
NOte as I say everything was fine a couple of days ago - maybe theres a way to just revert to the setup then ?
 
cheers, Andrew

---

### Post by IWantFroyo on 2011-12-01
> **adnpearce said:**
> Going into admin/NVID xserver setting brings up a box saying 'you dont appear to be using the nvis x driver - please edit your x config file (just run nvidia-xconfig' as root) and restart the x server. Ive done the first part of that with a sudo nvidia-xconfig and it just says its backing it up. dont know how to restart the x server (ive tried ctrl/alt/backspace). doesnt fix anything

<ctrl><alt><f1>, "startx"

---

### Post by matt_symes on 2011-12-01
Hi

Can you boot into an older kernel ?

Kind regards

---

### Post by grahammechanical on 2011-12-01
You graphics card could be breaking down. The other year my machine would boot into low resolution mode. When I tried to configure the Nvidia adapter using the Nvidia Configuration Settings manager it could not save the changes to the configuration file because it could not make a backup of the file.

It was when I noticed white dots on the machine's opening splash screen that should not have been there that I realised that the problem was with the graphic card as this splash screen appears well before Ubuntu began to load. It was overheating. It was a fanless silent model. I had neglected to keep the vents free from dust.

All my attempts to fix it only made things worse because it ended up not loading Ubuntu at all not even from the live CD.

I concluded that Ubuntu must get its monitor settings from interrogating the monitor each time it loads. And from my investigations I saw that the video configuration did not have settings for my monitor. The video adapter was unable to collect the settings from the monitor.

I know that I do not have scientific evidence for this but I was able to install another Linux distribution that required the user to choose the monitor resolution during the install and that got me a working OS but there were white parallel lines down the screen.

So, to bring a long story to an end I brought a new video card and I now have a working Ubuntu machine again.

If my story sounds in any way familiar to you, then do not rule out the possibility that your video adapter is overheating and about to fail in some way.

Oh, by the way, as this is a forum then 2 hours is not too long a time to wait for a response. Waiting 2 days would be fast. Even then you may not get a solution because we do not have some kind of manual or user guide giving all the answers to every possible problem that every possible person might have with every possible type of computer. This is what we mean when one of us says this is not a support/help desk.

Regards.

---

### Post by adnpearce on 2011-12-02
> **grahammechanical said:**
> You graphics card could be breaking down. The other year my machine would boot into low resolution mode. When I tried to configure the Nvidia adapter using the Nvidia Configuration Settings manager it could not save the changes to the configuration file because it could not make a backup of the file.
 
It was when I noticed white dots on the machine's opening splash screen that should not have been there that I realised that the problem was with the graphic card as this splash screen appears well before Ubuntu began to load. It was overheating. It was a fanless silent model. I had neglected to keep the vents free from dust.
 
All my attempts to fix it only made things worse because it ended up not loading Ubuntu at all not even from the live CD.
 
I concluded that Ubuntu must get its monitor settings from interrogating the monitor each time it loads. And from my investigations I saw that the video configuration did not have settings for my monitor. The video adapter was unable to collect the settings from the monitor.
 
I know that I do not have scientific evidence for this but I was able to install another Linux distribution that required the user to choose the monitor resolution during the install and that got me a working OS but there were white parallel lines down the screen.
 
So, to bring a long story to an end I brought a new video card and I now have a working Ubuntu machine again.
 
If my story sounds in any way familiar to you, then do not rule out the possibility that your video adapter is overheating and about to fail in some way.
 
Oh, by the way, as this is a forum then 2 hours is not too long a time to wait for a response. Waiting 2 days would be fast. Even then you may not get a solution because we do not have some kind of manual or user guide giving all the answers to every possible problem that every possible person might have with every possible type of computer. This is what we mean when one of us says this is not a support/help desk.
 
Regards.
 
 
 
thanks Graham - really useful stuff.  And apologies to everyone if I was impatient - its just that the only time ive used this before you were so lightening fast with responses that I set my expectations a bit high (and I worried that once my pos had dropped off the first screen it would be seen any more).
 
Re graphics card breaking down, it could be that as I do have some odd colours when booting up.  Ive had that same thing on a tower pc with an Geforce card before and yes it was kaput.  Alas this time its integrated (a small form factor 'net top') so I have to do all i can to fix it with software or bin the machine I fear.
 
Perhaps I should concentrate on just one part of my problem with a new more direct question :
 
Q.  I want to reinstall the Nvidia drivers to try to fix the problem.  My ubuntu machine isnt on the internet, so Ive downloaded them to a memory stick in the forma of one .RUN file.  How do I load it onto the ubuntu machine please ?
 
Thanks, Andrew

---

### Post by nothingspecial on 2011-12-02
Threads merged.

---

