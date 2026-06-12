---
title: "Installing nvidia proprietary drivers with intel integrated graphics?"
date: 2013-06-24
forum: Multimedia Software
---

### Post by Vormeph on 2013-06-24
Hi, I'm currently unsure as to how I should install nvidia's proprietary drivers on my distro. One method is through nvidia's website itself, the other is through installing certain packages or using the Additional Drivers. The problem is that I couldn't find my graphics driver under 'Additional Drivers', so I made the assumption that my graphics driver was not being used at all. 

How can I install nvidia proprietary drivers? Please include instructions. Thanks!

---

### Post by TheFu on 2013-06-24
I avoid using drivers directly from the GPU maker. These force us into a manual update mode, which is part of the reason I left MS-Windows. I want my system to maintain itself using the normal package manager.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) explains how.

---

### Post by Vormeph on 2013-06-24
> **TheFu said:**
> I avoid using drivers directly from the GPU maker. These force us into a manual update mode, which is part of the reason I left MS-Windows. I want my system to maintain itself using the normal package manager.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) explains how.

I can't find any of the packages mentioned in that article within the repositories. That article is possibly out of date. Any other solutions?

---

### Post by hansdown on 2013-06-24
Hi Vormeph.

I just installed my nvidia driver yesterday.

First, you need to know which driver is best for your card.

Could you please post which card you have?

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]Vormeph; Hi !

As a new user, you may not be aware of how to obtain the requested information.
Terminal codes:
[/COLOR]```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

``` Will yield display and card info.
Post the output back to this thread between code tags (#) -top of post.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by Vormeph on 2013-06-24
Here is the output:

```
root@#####:~# lshw -C display
  *-display               
       description: 3D controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f4000000-f4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:f5000000-f507ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:52 memory:f5400000-f57fffff memory:c0000000-cfffffff ioport:e000(size=64)
root@#####:~# lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a5]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]Vormeph; Oh my ..could be a tough one (to decide).

Ok hybrid graphics Intel/Nvidia ->
1. Nvidia does not support it and offers no drivers
2. Linux (ubuntu) also does not cope well with switchable graphics.
3. There are options:
a) Disable the onboard Graphics chip OR pull the Nvidia graphics card and force use of the Intel chips;
b) Look into the BumbleBee project ..there have been a lot of success stories installing BumbleBee and in the last year or so it had really gotten solid.
c. There are two huge threads on this forum in respect to switchable  graphics and discussion on how to cope with it. Well worth the read time. If you have problems finding them ... I will see what I can do to find them for you ...Will go a long way in helping you decide what is in your best interest.
[/COLOR][INDENT=2][COLOR=#000000]
not much help, just the best I can do [/COLOR][/INDENT]

---

### Post by Vormeph on 2013-06-24
> **Bashing-om said:**
> [COLOR=#000000]Vormeph; Oh my ..could be a tough one (to decide).

Ok hybrid graphics Intel/Nvidia ->
1. Nvidia does not support it and offers no drivers
2. Linux (ubuntu) also does not cope well with switchable graphics.
3. There are options:
a) Disable the onboard Graphics chip OR pull the Nvidia graphics card and force use of the Intel chips;
b) Look into the BumbleBee project ..there have been a lot of success stories installing BumbleBee and in the last year or so it had really gotten solid.
c. There are two huge threads on this forum in respect to switchable  graphics and discussion on how to cope with it. Well worth the read time. If you have problems finding them ... I will see what I can do to find them for you ...Will go a long way in helping you decide what is in your best interest.
[/COLOR][INDENT=2][COLOR=#000000]
not much help, just the best I can do [/COLOR][/INDENT]


When you say 'disable' the onboard Graphics chip, what do you mean by that? Do you think the Bumblebee project is the direction I need to take? It sure is an adventure! Could you link the two huge threads you mentioned? I would like to read them.

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]Vormeph;

There may be an option in your bios to disable one or either of the graphic display units
Here is the first .. discussion of hybrid drivers is a ways into the thread.. the prologue to what is of interest to you is still an interesting read, I may have it at about the right area.
[/COLOR][http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86)

I do not run swithable graphics, and have yet to encounter such directly. All I can do is provide you a means of information that relates how hybrid graphics relates to your system... and you will have to make the call what you want to do... there are pros and cons to any decision that you may make. BumbleBee may be the better option. In most cases it works well but you must learn to work with it.[INDENT=2]
I'll hunt up the other[/INDENT]

---

### Post by Bucky Ball on 2013-06-24
*Thread moved to **Multimedia & Video**.*

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]Vormeph; More to chew on,
[/COLOR][https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://ubuntuforums.org/showthread.php?t=2152186&p=12684841#post12684841](http://ubuntuforums.org/showthread.php?t=2152186&p=12684841#post12684841)

And this one directed at AMD but will be informative in respect to what is going on with Nvidia:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)[INDENT=2]
The good thing is, there are options

[/INDENT]

---

### Post by Vormeph on 2013-06-25
There are indeed options. I noticed that nvidia released a native version of a driver which supports my graphics card. It does warn that it may not work with nvidia optimus and those with intel integrated cards. I'm not sure if I should install the native version or install bumblebee + primus. The latter appears to be the safer option.

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]Vormeph;

Off the top of my head I do not know which is the top end product..there is nothing to loose but time to:
turn off the intel graphics; booting with Nvidia and I would strongly urge to use the open source driver (that is installed presently) and see what results.
If there are problems ... try with only intel :

[/COLOR]>MAFoElffen has some excellent advise on using the Xorg.conf files to switch graphics drivers if one has or needs to take that route.
[COLOR=#000000]
Then I have seen good report of BumbleBee/optimus ... many have been happy, but again you have to learn to work with BB.

But again I have no experience with which to base any recommendation on. 
[/COLOR][INDENT][COLOR=#000000]others who have the experience can advise much better than I

[/COLOR][/INDENT]

---

### Post by Vormeph on 2013-06-25
Turning off intel graphics can compromise the graphics on my laptop unless I actually install some drivers to cover the nvidia ones. How do I turn off intel graphics?

---

### Post by monkeybrain2012 on 2013-06-25
> **Vormeph said:**
> There are indeed options. I noticed that nvidia released a native version of a driver which supports my graphics card. It does warn that it may not work with nvidia optimus and those with intel integrated cards. I'm not sure if I should install the native version or install bumblebee + primus. The latter appears to be the safer option.

[URL="http://orkultus.wordpress.com/2013/04/20/how-to-nvidia-319-12-drivers-in-ubuntu-based-systems-with-bumblebee/"]
http://orkultus.wordpress.com/2013/04/20/how-to-nvidia-319-12-drivers-in-ubuntu-based-systems-with-bumblebee/[/URL]

Do at your own risk, I never have an Optimus computer and can't say if it works. :)

---

### Post by Vormeph on 2013-06-25
Thanks for all your help; I've installed bumblebee + primus and for now I have to manually assign my games to use my nvidia graphics card. (Which is what I did when I was with Windows too, so it doesn't bother me)

For now, no problems arise.

---

### Post by Bashing-om on 2013-06-25
Vormeph; Hey ,

Great. I am pleased that you are pleased BumbleBee will work out for you. -> enjoy your ubuntu !

Please mark this thread as solved;
In the event there are additional problems, open up a new thread.
 This will aide others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]it is all a learning experience[/INDENT][/INDENT]

---

