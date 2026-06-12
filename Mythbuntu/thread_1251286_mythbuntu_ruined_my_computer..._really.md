---
title: "mythbuntu ruined my computer... really"
date: 2009-08-27
forum: Mythbuntu
---

### Post by mcmasterp on 2009-08-27
just to let everyone know before you try mythanything.


I downloaded and mythbuntu 9.04 to try on a machine I was already using with windows and BeyondTV. I had an ati x550 pcie graphics card, two duel turner cards,a pci modem, 1 x 40gb ide HD, 2 x 200gb ide HD, 1 x 1TB sata HD.

both 200gb and the 1tb are full of shows in the mpg format, all are formatted ntfs. I ran the liveCD and except for the fact tthat the tv-out only worked during startup and shutdown, everything looked fine.

Then came the install,

I installed it on the 40gb ide drive, using and lcd monitor for now. went through the setup, everything was good until it came to the mythtv setup, all boxes on the screen were black, the framing on the page was there but no words, buttons, etc. it was to late to go back so I tried installing again,  this time using the amd graphics settings. this time it would not even start, it just sticks on a screwed up loading screen.

so then I try installing again, or started to... now the cdrom drive isn't showing correctly in bios, and usb boot is not supported, then the power button on the computer stopped working.

The more I tried the worse it got. I have been building windows based DVRs for 8 yrs so I thing I have a handle on hardware/software

So now I have a large hunk of metal that will not startup even into the bios half the time, or boot from the cd, or boot the installed operating system. so yeah... thanks mythbuntu.

P.S. I know what your thinkin. these things cant possibly be related. I would agree with you if I was not living the reality right now

---

### Post by larsolav on 2009-08-27
> **mcmasterp said:**
> just to let everyone know before you try mythanything.
...
so then I try installing again, or started to... now the cdrom drive isn't showing correctly in bios, and usb boot is not supported, then the power button on the computer stopped working.
...
So now I have a large hunk of metal that will not startup even into the bios half the time, or boot from the cd, or boot the installed operating system. so yeah... thanks mythbuntu.

That is some powerful software, messing with you bios and your power button! 

The whole ATI and 9.04 issue has been addressed before:
[http://ubuntuforums.org/showpost.php?p=7811655&postcount=4]("http://ubuntuforums.org/showpost.php?p=7811655&postcount=4")
But that probably wont help much with your new brick...

---

### Post by mcmasterp on 2009-08-27
the link you gave is to quite a lively discussion, I see what linux users mean by quick solutions from the community. 

I should state for the record that I use Ubuntu netbbok remix on my aspire one and I am moderately pleased with it. I have a touchscreen that works great in widows but not in linux on it but other than that, its good.

The only reason I tried mythbuntu is because my cable provider discountinued standard catv, so my 4 tuners system was useless (cancelled them, yay no more comcast!). So i thought why not go mythbuntu, and torrent all my shows.

---

### Post by klc5555 on 2009-08-27
> **larsolav said:**
> That is some powerful software, messing with you bios and your power button! 

The whole ATI and 9.04 issue has been addressed before:
[http://ubuntuforums.org/showpost.php?p=7811655&postcount=4]("http://ubuntuforums.org/showpost.php?p=7811655&postcount=4")
But that probably wont help much with your new brick...

GRUB has a real problem at install when the system has multiple drives that include both IDE and SATA. It's almost guaranteed to guess wrong where to put the bootloader files, and then won't be able to find those files again after a reboot. So all subsequent boots hang at the "loading Grub 1.5" echo. Archaic/obsolete drive labelling nomenclatures in conflict that became especially annoying once Ubuntu went to all-scsi drive names with 8.04.

You end up having to boot from the CD to rejigger Grub correctly by hand to get it to boot, using info found in the sections beginning with "Changing the Disk that Grub is installed to" in the Ubuntu Community Grub Howto [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) or other places.

Drove me bonkers the first time I ran into it, 'cause I was a LILO guy who was a bit suspicious of GRUB under the best of circumstances. But it's easy to fix once you recognize what the problem is. 

It wouldn't be good way for someone to first encounter a Mythtv distro though. I guess even something as straightforward as Mythbuntu shouldn't really be messed with by people with absolutely no Linux experience.

---

### Post by tgm4883 on 2009-08-27
If you power button isn't working, i'd suspect a faulty power supply

---

### Post by mcmasterp on 2009-08-27
I was able to save the machine, and the cdrom and the power button, but Iapparently don't get to know how I did it, they just work now. though of all the most profound things to happen to a computer in front of me, the image on the bios screen has changed. No kidding, it was a little icon in the corner, now its a big Compaq in the middle. it works so I dont know what to think. I have had this machine a while. (a presario sr1630nx, amd64, ati x550

Now my issue is with the ati x550 pcie graphics card and X. I am sitting in a terminal with no idea how to get it working.

when X starts all I get is black boxes with no text, etc. I can alt-tab, and have seen/used the update manger, and well thats it. when I alt tab I can see that there are to myth frontend something or others running, but switching to them just takes me to a black screen. I have to press esc, or alt-tab,  to get back to black boxes, or ctl-alt-f1 for terminal, not sure whatelse to do or how to fix

---

### Post by mocha on 2009-08-27
Power button stopped working?  I think you must work for the same company as me!  :lolflag:  Probably you confused the fact that power buttons are now soft with the ATX supplies and you have to hold them for awhile to cycle off power, that or just use the main switch on the back of the supply.

---

### Post by mcmasterp on 2009-08-27
Not likely. I have been familiar with how to operate the power switch for many years. including the technique of holding it down.

My primary concern now is fixing the X server, or Xorg, or X or whatever you call it. an interface of blank boxes is not very easy to fix. I am currently sitting in front of a terminal, waiting for someone to give me an idea of how to fix it, I have about 32hrs to spend on it.

---

### Post by epsolon77 on 2009-08-27
> **mcmasterp said:**
> I was able to save the machine, and the cdrom and the power button, but Iapparently don't get to know how I did it, they just work now. though of all the most profound things to happen to a computer in front of me, the image on the bios screen has changed. No kidding, it was a little icon in the corner, now its a big Compaq in the middle. it works so I dont know what to think. I have had this machine a while. (a presario sr1630nx, amd64, ati x550

Now my issue is with the ati x550 pcie graphics card and X. I am sitting in a terminal with no idea how to get it working.

when X starts all I get is black boxes with no text, etc. I can alt-tab, and have seen/used the update manger, and well thats it. when I alt tab I can see that there are to myth frontend something or others running, but switching to them just takes me to a black screen. I have to press esc, or alt-tab,  to get back to black boxes, or ctl-alt-f1 for terminal, not sure whatelse to do or how to fix

I'm sorry if this leads you on any sort of a wild goose chase but I remember having a similar issue with my test of mythbuntu.  If I recall, the ATI drivers did not want to work with the KDE desktop.  There was something I changed in the X11 config.  Try searching for ATI and KDE display issues.  I'm sorry I can't be much help.  My only issue with Mythbuntu was the auto rip of DVD's wouldn't work because I didn't install some codec.  Everything else was quite nice.  I hope you come to enjoy Mythbuntu as much as I have.

---

### Post by mcmasterp on 2009-08-27
Thank you for at least trying. I was not able to figure anything out from your suggestions, but at least you tried.

I am not usre how long I should just sit here on a tty1 terminal screen hoping for help. I may just switch back to winblows


Lol. if its winblows, and it just works out of the box, then what does that make linux??  I believe linux's biggest con is that everyone always says "linux works on everything!" they should add..."except on your particular piece of hardware, sorry"

---

### Post by newlinux on 2009-08-27
> **mcmasterp said:**
> Thank you for at least trying. I was not able to figure anything out from your suggestions, but at least you tried.

I am not usre how long I should just sit here on a tty1 terminal screen hoping for help. I may just switch back to winblows


Lol. if its winblows, and it just works out of the box, then what does that make linux??  I believe linux's biggest con is that everyone always says "linux works on everything!" they should add..."except on your particular piece of hardware, sorry"

USe the best tool for the job, given the circustances. If you hardware doesn't want to work with Linux, and you don't want to fiddle much more with it, use windows. Windows is good for some, as is Linux. They both have a place in the world :).

---

### Post by mcmasterp on 2009-08-27
not exactly the answer I was hoping for.

before I do switch back. does anyone know what stupid setting needs to be changed to get the X whatever working?????????????????????????????????????????????????

---

### Post by tgm4883 on 2009-08-27
> **mcmasterp said:**
> Thank you for at least trying. I was not able to figure anything out from your suggestions, but at least you tried.

I am not usre how long I should just sit here on a tty1 terminal screen hoping for help. I may just switch back to winblows


Lol. if its winblows, and it just works out of the box, then what does that make linux??  **I believe linux's biggest con is that everyone always says "linux works on everything!" they should add..."except on your particular piece of hardware, sorry"**

I don't know anyone that says linux works on everything. They do say that Linux **runs **on everything.

---

### Post by newlinux on 2009-08-27
> **mcmasterp said:**
> not exactly the answer I was hoping for.

before I do switch back. does anyone know what stupid setting needs to be changed to get the X whatever working?????????????????????????????????????????????????

It wasn't an answer, it was a response. You seem so frustrated with Linux, and willing to berate, so I thought I'd make peace with your decision to go back Windows. Your last post didn't really include a technical question.

What driver are you currently using for your card? What's in xorg.conf?

---

### Post by transmition on 2009-08-27
Perhaps this is not the best solution, but maybe you should consider trying a regular Ubuntu install and then customize it to suit your needs. 

There is a possibility this is a mythbuntu specific issue, and as things are right now, it might just be better for you to start fresh (and maybe unplug some of those drives while you do the install ;) )

---

### Post by mcmasterp on 2009-08-27
SOLUTION!

vote with my wallet and show ATI what happens when you discount linux users. I have purchased a Nvidia card that works

---

### Post by jasonsjunk on 2009-08-27
Now thats what I call a good solution!  Chuck the ATI crap, if they don't want to support Linux then they will lose some customers.

---

### Post by epsolon77 on 2009-09-03
> **mcmasterp said:**
> SOLUTION!

vote with my wallet and show ATI what happens when you discount linux users. I have purchased a Nvidia card that works

Here here.  I used to buy tons of ATI equipment.  I haven't purchased or recomended a purchase from ATI in the last two years becuase of a lack of linux support.

---

### Post by epsolon77 on 2009-09-03
Deleted double post

---

