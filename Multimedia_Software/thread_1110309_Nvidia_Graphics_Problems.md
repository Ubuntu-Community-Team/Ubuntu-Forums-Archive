---
title: "Nvidia Graphics Problems"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Drobbins on 2009-03-29
Hello All, 

Okay so last week i posted about a GX240 that i had which would not run compiz however i have now upgraded this machine to a whopping beast which is the Dell Precision T3400.

So i want to activate all the fancy effects that i should be able to run from using a dedicated 3d graphics card, in this case i am running the Quadro 290 card.

So i navigate to the **System -> Adminstation  -> Hardware Drives** and their we have two options 
[LIST]
[*]NVIDIA accelerated graphics driver (version 173)
[*]NVIDIA accelerated graphics driver (version 177) [Recommended]
[/LIST]

So naturally i select the recommended one, but this is where things get a bit weird, after hitting activate a little box pops up saying downloading, activating or something liek that i am not 100% as it happens so fast and then dissapears. 

The problem is after hitting  that 'activate' button nothing is activated :confused:

Can anyone shed any light on this or point me to a graphics card as good as this that is supported. 

Cheers
Rich
:guitar:

---

### Post by 2j4ez on 2009-03-29
try installing the driver from add/remove just type NVIDIA in the search box

That might work

---

### Post by Drobbins on 2009-03-29
Okay so from the add/remove option i searched for NVIDIA as suggested and the driver i wanted appeared, so i checked the box to install it and went to apply the changes but i get a message saying "> Please insert the disc labeled Ubuntu 8.10 _intrepid |bex_-release i386 (20081029.5) in drive /cdrom" So i do that and it wont scan the disk 

Why not? 

Rich

---

### Post by Taus on 2009-03-29
I had the exact same problem a few days ago. First i activated the 173 release and then I was able to enable the 177 release...

you could also just download the driver off nvidias hp - those are also newer than the 177 i believe. 

cheers

---

### Post by Drobbins on 2009-03-29
May i firstly once again thank u Taus for your help and secondaly ask [newbie]what is a HP and where do i access such a thing? [/newbie]

---

### Post by Taus on 2009-03-29
lol no problem bro - anytime :)

you download it off the nvidia homepage at [www.nvidia.com](www.nvidia.com)
i'm guessing that your video card is the NVS series? that's the only section i could find that had a Quadro 290 gfx card...

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

download the and run the package should be very straight forward. or else feel free to ask.

i'm gonna hit the sack for now but i'll check up on this post again tomorrow morning.

cheers bro and good luck

---

### Post by Drobbins on 2009-03-30
Okay i tried firstly to install the 173 but i get the same error asking me to insert the CD-ROM. 

Secondly i downloaded the file opened the terminal typed in sudo sh /files/location/here and it says i am running an x server :( now what am i doing wrong :'(

RIch

---

### Post by |Porsche on 2009-03-30
Hit Alt-F1 or Alt-F2 or 3-6 until you get a terminal.
Issue command ```
sudo /etc/init.d/gdm stop
``` to stop the X server.

Then launch the nvidia file that was telling you that there is an X server active. go through the configs and when you are done you will be back at the command prompt.

To start X issue a ```
sudo /etc/init.d/gdm start
```

And it should be all done.

---

### Post by Drobbins on 2009-03-30
Thanks guys, managed to get X stopped before work so i know that that will work, i just need to try and get the file to run now. 

Will update you on my progress later today :) :KS

---

### Post by Garratt on 2009-03-30
> **Drobbins said:**
> Okay i tried firstly to install the 173 but i get the same error asking me to insert the CD-ROM. 

Secondly i downloaded the file opened the terminal typed in sudo sh /files/location/here and it says i am running an x server :( now what am i doing wrong :'(

RIch

you may have cd enabled for program installation if so this is bad idea, just use the net it has the latest stuffs

go ----> System ----> Administration ----> Software Sources

on the first tab you should see a check-box saying installable from cd, un-tick it, also (unless you are a opensourceware junkie) make sure all other options are ticked eg. main, universe, multiverse, restricted..

now you should be good to go... open console & copy/paste this code..

console is in
-----> applications----> Accessories -------> Terminal

```
sudo apt-get install update
```

enter your password, there shouldn't be any updates.... now copy/paste this code:

```
sudo apt-get install envyng-core
```


This used to have an easy to use Gui, but it has been deleted for some strange reason... i'm guessing Alberto cant be bothered updating (or busy):(

ok now this is installed type:  to run the program.

```
envyng -t
```

You have multiple selections here so I think number 1 is the Nvidia driver, so type 1 and hit enter

Now there is a list of drivers and versions if your using intrepid or hardy i think it's ok to use the first, I'm not positive because it's a very random table that makes no sense whatsoever... :P 


 0      | 177.82-0ubuntu0.1      
 1      | 173.14.12-1-0ubuntu5.1 
 2      | 96.43.09-0ubuntu1.1  
 3      | 71.86.04-0ubuntu10    

But being that 177 is the most common restricted, it's safe to say that 177.82 will more than likely be the most common open source.  

ok type 0 and hit enter

it will then tell you to restart... let us know how you go.


EDIT: or I could be completely wrong... I dunno I just did a reinstall and upgrade to intrepid and having problems with screen resolution, but glxgears is in the 6-9k's so the video drivers are kinda working...games are playing :(

---

### Post by Drobbins on 2009-03-30
Wow that is indepth...Garratt thanks very much :-D

I will report back later.

---

### Post by Garratt on 2009-03-30
sorry ignore the above i'm trying striaght from the website also.

you still may want to disable the cd installations tho if it is enabled.

I don't think envy has the same glory it used to, it isn't working for me.

anyway try the above method but, when you stop x server and get into terminal type: sudo su

then change directory to your desktop or wherever you downloaded file.

and: sh NVIDIA-Linux-x86-180.44-pkg1.run

that should be it...

now start up x-server again by typing /etc/init.d/gdm start

and then restart your computer

---

### Post by Garratt on 2009-03-30
Well hopefully you didn't go ahead and install envy and follow instructions... though this may work for you. If not and you want to uninstall
I'm sure you should know by now but just incase:
open terminal: envyng -t

now click option 3 uninstall all drivers installed by envy.

follow the prompts now.

and then uninstall envy: sudo apt-get remove envyng-core

grab a pen and paper and write this down if you will have trouble remembering

sudo /etc/init.d/gdm stop

you will see a blank screen after a while, I sat for a while but nothing seemed to happen so i pressed ALT F1, this brought up login screen but in text mode.
 so I login: Garratt
then password:   ******

then type cd Desktop
then sudo sh NVIDIA-Linux-x86-180.44-pkg1.run

let that run and follow the prompts, for me it couldn't detect the current kernel and so it created a config file for the kernel. then start up the windows server again, sudo /etc/init.d/gdm start
then restart comp, now for config file... im up to here ill edit in a few mins

---

### Post by Drobbins on 2009-03-30
> **Garratt said:**
> Well hopefully you didn't go ahead and install envy and follow instructions... though this may work for you. If not and you want to uninstall
I'm sure you should know by now but just incase:
open terminal: envyng -t

now click option 3 uninstall all drivers installed by envy.

follow the prompts now.

and then uninstall envy: sudo apt-get remove envyng-core

grab a pen and paper and write this down if you will have trouble remembering

sudo /etc/init.d/gdm stop

you will see a blank screen after a while, I sat for a while but nothing seemed to happen so i pressed ALT F1, this brought up login screen but in text mode.
 so I login: Garratt
then password:   ******

then type cd Desktop
then sudo sh NVIDIA-Linux-x86-180.44-pkg1.run

let that run and follow the prompts, for me it couldn't detect the current kernel and so it created a config file for the kernel. then start up the windows server again, sudo /etc/init.d/gdm start
then restart comp, now for config file... im up to here ill edit in a few mins

Wow you :guitar:

Rich

---

### Post by Garratt on 2009-03-30
i REallY REallY REallY REallY REallY REallY REallY REallY REALLLLLY

wish i didn't do a reformat.... ubuntu is lame and hates me.

The screen is bad still 1324x873 or something... close to 1400x900 but not quite

I installed, went to the page on nvidia website telling you how to configure the config, only problem is it is a page that tells you nothing but has a link to a tar package.

ok so I officially hate tar packages that require you to make files, never heard of a .exe?????

Enough bitching....

the files are:::--->
```

COPYING    make_usable.c     nvidia-xconfig.1.m4     query_gpu_info.c

extract_edids.c     multiple_screens.c    nvidia-xconfig.c    tree.c

gen-manpage-opts.c    nvgetopt.c        nvidia-xconfig.h      util.c

lscf.c               nvgetopt.h           options.c         XF86Config-parser

Makefile             nvidia-cfg.h         option_table.h

```
these are the files how do i run the makefile? and where should it go, currently sitting on desktop.
>.<

---

### Post by Drobbins on 2009-03-30
Okay....so now are we in even bigger mess than we started? :S :confused:

---

### Post by Garratt on 2009-03-30
well kind of, Hows your graphics seem?

I'm googling how to run Makefile from what i can tell it's just a C or C++ but won't compile using g++ or running sh Makefile 2 options i have tried...

I can open the Nvidia X-Server settings under ---> System ---> preferences ----? Nvidia X-S..

but I'm unsure if this is the config file, as it clearly states 
"Nvidia X-Server Settings".

I'm at the point I don't care for it anymore, I might just merge my stuff to run under cygwin / Windows Vista, at least with /bin path in the windows environment variables you can have the best of both worlds. 

a dual Win/Lix Operating system.

This whole exersise started because the Hardy 8.04 kernel shat itself and wouldn't sync kept panic-ing, so I upgrade to intrepid 8.10... it's just one thing after another until you want to smash your head repeatedly against a wall.


EDIT:: WooooHooo I have killed it fully, i only have 1/4 of the monitor displaying a desktop the rest is fuzzy static and different colors.

I was silly and tried to install the 177 driver again from add/remove programs list.

it made my screen 1/4 size and fuzzy, so i reinstalled the 180 driver from nvidia and now it's permanent :D

---

### Post by Drobbins on 2009-03-30
I am going to give it a go when i get home none the less!! Maybe i can get it to work. 

I won't be defeated. :KS

---

### Post by dougfractal on 2009-03-30
This what I would do


1) remove 180.44 with envyng

2) fix the CD-ROM thing

3) install nvidia-glx-180 with apt-get

4) enable 3d with Preferences > appearance




heres the actions

```
sudo envyng -t  
```

press 1 then exit

I'm hoping this will remove the nvidia install script stuff and get you bact to a fully deb system.


```
sudo synaptic
```

> Settings > repositories >Third party > unselect CD-ROM
update repos.

search nvidia

install > nvidia-glx-180


or use 
```
sudo apt-get install nvidia-glx-180
```



good luck

---

### Post by Drobbins on 2009-03-30
> **dougfractal said:**
> This what I would do


1) remove 180.44 with envyng

2) fix the CD-ROM thing

3) install nvidia-glx-180 with apt-get

4) enable 3d with Preferences > appearance




heres the actions

```
sudo envyng -t  
```

press 1 then exit

I'm hoping this will remove the nvidia install script stuff and get you bact to a fully deb system.


```
sudo synaptic
```

> Settings > repositories >Third party > unselect CD-ROM
update repos.

search nvidia

install > nvidia-glx-180


or use 
```
sudo apt-get install nvidia-glx-180
```



good luck

Tried that - no luck. Nothing happens, so i tried to install 177 and it says that is conflicts. GAH.

Now What

---

### Post by Drobbins on 2009-03-30
Finally -Managed to get the Nvidia 173 [recommended] installed from the Hardware Drivers pane. C'Mon

Thanks for all your help guys.

---

### Post by Garratt on 2009-03-30
Good to hear Drobbins I hope it works for you.

I'm guessing I will have to start my own thread...

---

### Post by Drobbins on 2009-03-30
> **Garratt said:**
> I'm guessing I will have to start my own thread...

I jsut followed the steps to install this from apt-get which didnt work so then i went to add hardware and activated 173 and then everything just works now. 

Try rolling your driver back using the steps provided a few posts back mate.

---

### Post by Garratt on 2009-03-31
I figured it out finally, strangely enough I wasn't trying, I was reading directions to install the new version of ViM. 7.2 which is not in repositories yet.
```

Double click the .tar.gz and extract to desktop.

open terminal and enter root ---> sudo su

cd to the new folder you just extracted and type: make && make install.

```

I don't think has fixed my problems tho, intrepid is just hates me.

EDIT: I have already tried 173 and 177 via restricted and add/remove and apt-get neither work. 173 highest resolution i get is 600x800, 177 highest i get is 1042x800, and 180 highest i get is 1152x864
Things may change on restart but at the moment in downloading tons of pr0n sooo... i will later and I won't hold my breath   :P

---

