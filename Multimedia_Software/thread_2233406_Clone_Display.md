---
title: "Clone Display"
date: 2014-07-08
forum: Multimedia Software
---

### Post by kakashi_12 on 2014-07-08
Can't Clone my Display to TV.
I use to go to System, Preferences, Monitors. Then it would prompt me if  I wanted to use the default driver tool or the NVidia driver/tool. I  choose "Yes" to choose the NVidia tool insted of the Generic tool. Then  I'd go to XServer Configuration or something. Then I had options to  Cone, Extend display, change resolutions, enable TV, etc. Now I ONLY  have the Generic Monitor Tool. I searched for new drivers. There are  about 5 listed and I tried a couple. But nothing changes the "Monitor"  tool. It's still Generic and not NVidia. Also, under Administration, I  see NVidia X Server Settings. But that does not help either. Just shows  something about profiles. I have my TV plugged in via S-Video.

NOTE: I am using GNome FallBack Desktop Environment.

---

### Post by kakashi_12 on 2014-07-08
[Reply to Bucky Ball from previous thread.]

Thanks for the idea. But didn't show the second display.
Found out here.... [https://sites.google.com/site/easylinuxtipsproject/bug](https://sites.google.com/site/easylinuxtipsproject/bug)[B]s
[/B]that I can use "sudo nvidia-settings"
That brings up the tool I use to use. I hope I can use it without su. Other users need to use this tool too.
The only problem is that now my TV is cutting off the sides and top of  the screen. There was a setting in the old NVidia tool that aloud me to  UnderScan or Over Scan. And that fixed it. But that option is not here.
I guess I'll have to make a custom launcher for it, since I can't find  it. I'm testing this in Unity btw. GNome Fallback is failing right now.

---

### Post by kakashi_12 on 2014-07-08
i think I'm going to have to reformat. I messed up. I'm getting several  errors and GNome Compiz has crashed. Metacity and Unity work ok, but  still with weird effects.
I was messing around in the "Additional Drivers" and trying out  different NVidia driver to see if it would me with my issue. I had a bad  feeling about it. Guess I shouldn't have messed. Anyways, I'm back on  the default/recommended driver I think. But everything is still defunct.  I don't suppose there's any way to clean all this up without a  re-format?

---

### Post by kakashi_12 on 2014-07-08
Ok. I had to reformat cause I was messing with drivers. From now on, I'm  not going to change the default driver unless someone else knows which  ones are safe to install.

I ran nvidia-settings in the terminal and it said to install it first.  So I installed it, then ran it and it still did not give me what I want.

I installed ARandR. The menu bar shows now. And I can see my TV in the dropdown list. Not sure how to get it active though????

---

### Post by kakashi_12 on 2014-07-08
Here's where I'm at with the Driver issue.

Tried following directions here...
[http://www.binarytides.com/install-n...-ubuntu-14-04/]("http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/")
But the website does not show my model :-s

So I'm just gonna guess!
I've got a clone of my HDD with CloneZilla incase something decides to go haywire again.

Screenshot shows the default driver installed (option 5) when OS was installed.
I'm going to try (option 1) proprietary and tested 331.38 driver. and see what happens.

---

### Post by Bucky Ball on 2014-07-08
As to which driver you should use, not sure, not my area, but as far as removing the wrong one and getting back to square one (open-source drivers and probably a usable system) you might get some joy here:

[http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers](http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers)

Check the answers down the page. ;)

---

### Post by kakashi_12 on 2014-07-08
That kind of confused me, but I'll try that in a little bit.

I tried the top option. (haha, so much for it saying tested). It wasn't very well tested, it's horrible.
I have the right tool (see attachment), but it crashed GNome Fallback. And even Unity just barely works. Icons are double.

---

### Post by kakashi_12 on 2014-07-08
Trying option: "NVidia legacy ginary driver version 173.14.39 from nvidia-173 (proprietary)"
Nvidia tool won't launch and gnome fallback just launches unity.

---

### Post by kakashi_12 on 2014-07-08
I've tried just about everyone from the list. And it's confusing, they keep reordering the list every time i change drivers. Anyways, it seems the default one works the best. it's the only one that doesn't give me problems or errors.

Is there any way to use the default linux driver (x.org x server driver) and still install the nvidia tool without installing the proprietary driver?

---

### Post by computertip on 2014-07-08
What Nvidia video card do you have?

---

### Post by kakashi_12 on 2014-07-08
Just restored my pc with CloneZilla so I can start from scratch again.

~$ lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: **NVIDIA Corporation G96** [**GeForce 9400 GT**] [10de:0641] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:c945]
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ac00 [size=128]
    Expansion ROM at f7a80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE912x SATA 6Gb/s Controller [IDE mode] [1b4b:91a0] (rev 12) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:83ba]
    Flags: bus master, fast devsel, latency 0, IRQ 16

---

### Post by kakashi_12 on 2014-07-08
> **Bucky Ball said:**
> As to which driver you should use, not sure, not my area, but as far as removing the wrong one and getting back to square one (open-source drivers and probably a usable system) you might get some joy here:

[http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers](http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers)

Check the answers down the page. ;)
Thanks for the input. But this didn't help. I've already got the open  source driver installed again (restored my drive with CloneZilla to be  back at square 1). nvidia drivers just crash the system.

---

### Post by kakashi_12 on 2014-07-08
Currently chatting with NVidia support. They gave me this link for my particular video card.
[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.24/NVIDIA-Linux-x86_64-340.24.run&lang=us&type=geforcem](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.24/NVIDIA-Linux-x86_64-340.24.run&lang=us&type=geforcem)
But they had no instructions on how to uninstall my open-source driver.

Anyone know how to uninstall open-source driver? So I can give this a try.

---

### Post by Bucky Ball on 2014-07-08
Just install the driver on that link. Don't bother about uninstalling open-source ones for the moment.

The instructions for installing should be in a README file in the download somewhere.

---

### Post by kakashi_12 on 2014-07-08
Installing their driver didn't work either. The file has a .run extension. It just failed saying couldn't read some of the info. It's a text file with commands in it.

---

### Post by Bucky Ball on 2014-07-08
> **Bucky Ball said:**
> 

The instructions for installing should be in a README file in the download somewhere.

?

---

### Post by kakashi_12 on 2014-07-08
There was no readme file. Just a .run file.

With the x.org driver, this is the only options I have (attachted). No options to do anything with.

---

### Post by kakashi_12 on 2014-07-08
ARandR only shows DVI1 and DVI2. yes, I have 2 DVI ports. But it won't show my SVideo port. Which is what my tv is plugged in through.

---

### Post by kakashi_12 on 2014-07-10
? unsolved

---

### Post by kakashi_12 on 2014-07-14
Trying to use ARandR again. Noticing that it does not have an option for S-Video. Only for DVI 1 and DVI 2.
I am following this.... [http://superuser.com/questions/24909/output-screen-to-tv-set-using-s-video](http://superuser.com/questions/24909/output-screen-to-tv-set-using-s-video)
but the commands aren't recognized. Of course this is for xrandr. Can't find that one in Software Center.
Is there a similar command to get this work, Bucky?

---

### Post by kakashi_12 on 2014-08-16
Well, I finally broke down and bought a DVI cable. I figure since S-Video does not show as an option in RandR and it is old, it must be out-dated and not offered a lot anymore in applications.
My cable is a DVI to Component. That's what I have available on my TV (Comp).

I connect the cable and open RandR, but I'm not sure what to do from there.????
I tried to move the screens over top of each other and then click Apply, but nothing comes up on my TV.
Just this outlined box on my Monitor.

---

### Post by kakashi_12 on 2014-08-22
Bought a DVI to HDMI cable. Now it works using ARandR!

---

