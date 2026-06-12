---
title: "nvidia driver makes ticking noise in my computer!"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by jimmyxx on 2006-05-30
Hi everyone,
this is a problem i've had with breezy and dapper, with my current graphics card (asus v9999 nvidia 6800) & my old graphics card (geforce 4). Everytime something loads it makes a series of ticking noises, when i scroll down a web page, or a I drag a window, or the screen saver starts, it makes this ticking noise! I thought it was my gf4 card so I bought a new one, that didn't help, a lad at work thought it might be the power-supply, so I bought a new case with a silent powersupply, and it still makes the bloody noise! In windows its perfectly silent, and when i set xorg.conf, to use the 'nv' driver instead of the 'nvidia' driver, its quiet again!

Is anyone else having this? I really want to sort it out!

thanks very much! x

---

### Post by Ramses de Norre on 2006-05-30
What exactely is making this noise?? Could you open the case and listen where it's coming from?
There aren't many moving parts on a video card..

---

### Post by ssam on 2006-05-30
i get this sometimes on an ati radeon 9000 mobility with the opensource drivers.

its unrelates to the system sound volume.

i wonder it is to do with powersaving systems switching parts of the GPU off when they are not needed,, and it flicking between the states tens or hundreds of times a second.

anyone have any more info, or crazy theories?

---

### Post by tseliot on 2006-05-30
It might be the hard disk. Especially if it uses the swap file.

---

### Post by jimmyxx on 2006-05-30
I'm fairly sure its coming from the graphics card, when I click Post Reply, while the page is waiting/sending, it 'clicks/ticks'- it must be the nvidia drivers as it stops when on nv?

---

### Post by glennric on 2006-05-30
Does your video card have a fan on it?  It could be something to do with the fan speeding up during these times.  Possibly the nv drivers don't work the fan and the nvidia drivers do.

---

### Post by WalmartSniperLX on 2006-09-30
Yeah I have it too. But, its on my x1600. Had it in windows too :D, usuall when scrolling down pages and stuff. Not sure exactly what it is. Fans work fine, I hear it whining in there :P Dont think theres a pizo on a gpu, is there?

---

### Post by tseliot on 2006-09-30
> **WalmartSniperLX said:**
> Yeah I have it too. But, its on my x1600. Had it in windows too :D, usuall when scrolling down pages and stuff. Not sure exactly what it is. Fans work fine, I hear it whining in there :P Dont think theres a pizo on a gpu, is there?

My father's ATI 9200 does the same thing :-k

---

### Post by impman89 on 2006-11-09
Same graphics card, same problem. Ticking noises coming from the x1600. Weird. Anyone figured this one out?

---

### Post by noxxle on 2006-11-10
mine makes a squeak noise sometimes, like when i minimize and maximize windows if i have nvidia drivers installed from somewhere other than ubuntu's repos.

---

### Post by GameGod on 2006-11-11
I've found that sometimes my Nvidia 6600 GT makes this ticking sound too, exactly as it was described in the first post.

Oddly enough, the only other time I've seen/heard this happen was on a Mac G5, which uses one of those high-end ATI cards...

It's weird...

---

### Post by alecjw on 2006-12-21
It happened to me in windoze XP too (but not in ubuntu), when i was running it on a 3GB hard drive. It was completely full of pagefile, every last byte. When i scrolled down a webpage, a sound which sounded like the scroll wheel on my mouse came through the _speakers_, so I'm not sure if it was anything to do with my GPU, an nVidia geforce 6800.

---

### Post by AleXit on 2006-12-29
I report same problem with a Nvidia Geforce GO 7400 on a Sony Vaio VGN-FE28B laptop.
I upgraded to latest nvidia drivers, but nothing in changed. I'm sure the noise is from video card, because I don't hear it in console-text mode.
This happen since I upgraded to Edgy... there wasn't in Dapper !:-?

---

### Post by esaym on 2006-12-29
I used to be able to hear my video card in my laptop that I used to have.  It was a dell inspiron 8200 with a geforce4 go and windows xp.  When the fans were not on and I scrolled a web page it would make a series of fast ticking sounds.  The sounds were very faint and could not be heard if the laptop fans were on and laptop fans are not that loud to begin with.

Its all probably normal

---

### Post by AleXit on 2006-12-29
> **esaym said:**
> I used to be able to hear my video card in my laptop that I used to have.  It was a dell inspiron 8200 with a geforce4 go and windows xp.  When the fans were not on and I scrolled a web page it would make a series of fast ticking sounds.  The sounds were very faint and could not be heard if the laptop fans were on and laptop fans are not that loud to begin with.

Its all probably normal

I think is not so normal. I hear ticking noise always, not only scrolling pages or doing something else!
Moreover, on WinXp the laptop is absolutely silent and there is no noise.

---

### Post by shyster. on 2007-01-13
Adding info to help aid the diagnosis, I have an Inspiron 6400 with an X1400 Mobility Radeon if that helps any. I too have the clicking noises and it occurs when beryl seems to render objects (i.e. snow, scrolling, spinning the cube, etc.). To support this, the clicking noises don't occur in Gnome mode (as opposed to XGL).

The noises also don't change with volume, however they are only heard through the sound system (tested w/ headphones and speakers). I also believe that it is caused by the GPU and not normal at all, as it does not occur in WinXP.

Hope this helps! 

Cheers

---

### Post by lanflett on 2007-01-14
It happens with my graphic card too...
Mine's a NVIDIA FX 6200
It started when I upgraded to Edgy. It doesn't occur in winxp.

---

### Post by emiliogo on 2007-04-03
I'm reporting the EXACT same problem.

When I move the windows around, scrool to a long list, play video, I hear a noise unrelated to the audio system. It comes out of the speakers tought.

The strange thing is that when I'm using "ati" driver on Xorg.conf, there is no such noise.
But when Ichange the driver to "radeon", there is the noise.

Btw, my graphics card is an radeon 9600pro.
Is on a Desktop, on a abit nf7 motherboard.

---

### Post by hoagie on 2007-04-03
Guys this sounds really weird there are not any parts in a GPU that can cause this kind of noise, except if something is stacked in the fan, but I don't think that's what happens. Except if you're GPU switches off some of it's particles when it is at idle.

---

### Post by gillza on 2007-05-15
I installed XGL today and noticed that same sound you were describing. Every time i scroll the page or minimize/maximaze the window i hear that noise. Sound disappears if I disable xgl... 
I have Fujitsu e8210 laptop with ATI x1400 mobility radeon built in.

---

### Post by bdonkey on 2007-06-06
I just noticed that I have this noise, too, when I enabled Beryl. It also happens constantly if I just let glxgears run. I think it's got something to do with the vid card rendering a high FPS...

And all I have is an Intel GMA 950.

---

### Post by MR Bacardi on 2007-06-13
I get this sound too.
To me it sounds like it is being send both through headphones as well as speakers (perhabs system speakers?).
It happens when scrolling, moving mouse over links and using arrow keys to move up / down a window.

The sound only occur when I have Beryl selected as Window Manager.

I am using a Dell Inspiron 6400 with a ATI X1400 graphic card.

Very annoying sound when working in a quiet environment. Hoping for someone to figure out a solution?

---

### Post by Bobbyhate on 2007-08-31
OK i had the same problem and the easy way but not best way is go in to your basic sounds on desktop (play  controll) and go to the top select options then advanced then depending on how old your comp is there should be a small box that says 1 enable 10 check it .

note this will not fix the problem but it will drop the level of the noise so the point where its hard to hear.

one way to help is to make sure your sound card is not under your video card that will bleed the sound 

hope i helped some one

 :guitar:~Bobby:guitar:

---

### Post by frases on 2007-10-27
Guys,
I seem to be encountering the same problem.  I've updated the video on my machine, a Dell SC1430, from the onboard video to an NVidia 8500GT PCI Express card and now I get slight audio crackles at different times when playing any multimedia file, video or audio.  The problem seems to occur more if I move the mouse or other windows or multitask.  If I remove the card and return to onboard video, the problem disappears.

I've moved the audio card to a different slot in the box, changed IRQs and even disabled the fan, but I still get this slight audio distortion with the new video card.  Of course, I get clean audio when I use the onboard video.

I've also put a dual-head VisionTek X1550 card in the box and the same audio problem happens.

I've read and tried the solutions some folks have posted (disabling glx in x/lowering volume/muting channels/changing audio cards/updating video drivers), and they haven't worked.  I also tried every NVidia X config setting listed here to no avail:
[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)

Does anyone have an update to this thread with a solid solution?

thanks for listening,
frases

---

### Post by GraFF on 2007-10-31
[http://ubuntuforums.org/showthread.php?t=532889](http://ubuntuforums.org/showthread.php?t=532889)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130)
> 
Xgl uses the graphics card more intensively than a standard unaccelerated desktop. In addition, it is known to be inefficient with CPU and graphics resources while scrolling. What's happening is that as you scroll, each line it goes down it generates a large spike of CPU and graphics instructions to re-render the screen, which causes the amount of power draw by components on your motherboard to change. This sudden change can often cause certain capacitors in your power supply unit to make weird noises.

Unfortunately this is more of a hardware phenomenon that we can do nothing about. AIGLX has more efficient scrolling support so that it might be able to narrowly avoid these noises.

Another workaround that may help is to lock your CPU into a constant speed, by disabling the /etc/init.d/powernowd service (try /etc/init.d/powernowd stop).
> No, this will not cause any damage to your hardware.

Let us hope that this is a competent conclusion.

---

### Post by frases on 2007-10-31
Thanks for the articles, GraFF.  I'm actually on Fedora 7 with the latest (100.14.19) NVidia drivers, but the Ubuntu forums were the only ones with a lead as to what my problem might be.  

I did enable AIGLX with the instructions from the HOWTO here:
[http://gentoo-wiki.com/HOWTO_AIGLX](http://gentoo-wiki.com/HOWTO_AIGLX)

However, I still get the sound.  Though, I wasn't sure if I was supposed to completely disable GLX in favor of AIGLX in xorg.conf.   I went ahead and disabled GLX by commenting out the "Load xgl" line in xorg.conf, when I did this, I was not able to use any accelerated features at all, so that didn't seem right.  ?

I also disabled "cpuspeed", which is Fedora 7s equivalent to powernowd, though this did not help either.

This one is a bugger, indeed.  It wouldn't be so bad if I wasn't editing video on this box.  Essentially, the noise interferes with my ability to distinguish between the glx created noise or actual noise in my recordings.  Frustrating.  

So, my next step is to try an external firewire interface to see if that helps.

---

### Post by frases on 2007-11-02
As lame as it sounds, I've opted for the easy route and plugged in a friends' M-Audio MobilePre USB interface.  Lo and behold, no noise!

This isn't a DAW, so I'm not concerned about high quality..I just need sound that works.

Thanks for the help, guys.  This one isn't fixed, but the MAudio workaround suits me.

frases

---

### Post by pezplaya on 2007-11-11
I get the same ticking noise.  seems like it only happens when i'm dragging a window.

I have an nvidia 6800

---

### Post by pch0mey on 2008-04-27
I'm getting a pulse high frequency noise from my tower. EVGA NVidia 7800GT on UBuntu 8.04. I'll try some of these solutions.

---

### Post by defe007 on 2008-05-22
I also have this problem of a squeaking sound when scrolling, moving windows, playing videos, etc.  This only started occurring when I upgraded to 8.04 from 7.10.  I have tried disabling Desktop Effects, but it does not make a different.

However, when I tried running Ubuntu from kernel 2.6.24-16-generic, the squeaking stopped but my computer ran really slow and videos played at 1/2 speed.

I am running Ubuntu 8.04 on a laptop.
1.7 GHz Intel Centrino
1 GB RAM
ATI Mobility Radeon 9700 Pro (fglrx driver)

Is there any solution to this?  Thanks for listening.

---

### Post by cegpope on 2008-06-28
> **defe007 said:**
> I also have this problem of a squeaking sound when scrolling, moving windows, playing videos, etc.  This only started occurring when I upgraded to 8.04 from 7.10.  I have tried disabling Desktop Effects, but it does not make a different.

However, when I tried running Ubuntu from kernel 2.6.24-16-generic, the squeaking stopped but my computer ran really slow and videos played at 1/2 speed.

I am running Ubuntu 8.04 on a laptop.
1.7 GHz Intel Centrino
1 GB RAM
ATI Mobility Radeon 9700 Pro (fglrx driver)

Is there any solution to this?  Thanks for listening.

I have a very similar configuration and I just started having this problem earlier this week. 

Reading different threads on clicking noises usually came back to the hard drive, platter parking and inconsistencies in how Ubuntu approaches power management in the disks versus the disc manufactures; this did not seem applicable to me, since I was getting noise in the speakers and not from the drive itself as was the common complaint.

However, this did cause me to check my power settings anyway.

In "Power Management," on the bottom of the "General" tab, is a check box to enable/disable "Use sound to notify in event of an error" this was checked, I unchecked it. 

I have not had a single tick through the speakers since doing this. I do not know what the error could be or if this actually solved the problem, but the speakers have stopped ticking for almost a day now.

---

### Post by freshspinach on 2008-07-05
I just started getting this noise, too. It sounds like static coming through my speakers whenever I move a window, scroll or mouseover.  I recently upgraded to an Nvidia 8800GTS but I don't think this started until long after the upgrade.

I don't get this noise in XP unless I'm playing Assassin's Creed.

It's really starting to get on my nerves.

---

### Post by freshspinach on 2008-07-06
I seem to have sorted this out, at least on my PC. I cracked open my case, shooed away the mice and wiggled the video card. Then I reseated my monitor cable and actually screwed it on this time. After reboot, all was silent again. I guess it wasn't the driver after all.

---

