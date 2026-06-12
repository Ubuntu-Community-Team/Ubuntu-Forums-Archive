---
title: "Problem upgrading to 10.10"
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by limjix on 2010-09-11
Hi,

Today i just upgraded my ubuntu 10.04 to 10.10 using the update-manager -d command.

Now after restarting my computer, my computer only boots into a command line interface.

Why cant i log in to the usual ubuntu GUI?
The top of the screen says "Ubuntu Maverick" (development branch)

Need some help on what to do.

Thanks!

---

### Post by Rubi1200 on 2010-09-11
From the Ubuntu website:

> **This is a beta release. Do not install it on production machines. The final stable version will be released on October 10, 2010.**   

---

### Post by limjix on 2010-09-11
Doesn't beta just mean testing? I mean doesn't that mean when they release this to the public it is meant to test the overall functionality for users?

So how do i revert back to 10.04?

Thanks

---

### Post by Rubi1200 on 2010-09-11
Yes, beta means testing, but it also means there are bugs and possibly hardware conflicts and other problems that might make the system unusable.

If you have a computer that is used for testing purposes only, fine.

But if you need an OS that works, you should not think that everything will function as you want/expect.

I suggest you reinstall 10.04 and wait for the final release of 10.10
Once it is made available, first try it as a LiveCD to see if it works on your system and then consider upgrading.

---

### Post by 3rdalbum on 2010-09-11
There are a couple of things you can try:

sudo service gdm start

If no luck, plug your computer into an Ethernet connection and run:

sudo apt-get update
sudo apt-get install ubuntu-desktop

Report the result back here.

Generally, upgrading from a stable Ubuntu to a development snapshot does not go well.

---

### Post by limjix on 2010-09-11
Will by using the 

sudo apt-get update
sudo apt-get install ubuntu-desktop

command delete all the data on my partition?

Thanks

---

### Post by coffeecat on 2010-09-11
> **limjix said:**
> Will by using the 

sudo apt-get update
sudo apt-get install ubuntu-desktop

command delete all the data on my partition?

Thanks

@limjix, since you posted in the **"Absolute"** Beginner's section I assume you really  are a beginner, so this advice (kindly meant) is based on that  assumption.

First - the answer to your question is, no it won't.

Second - there are many reasons that might explain why 10.10 is failing to boot into a GUI. The most  likely is that you have proprietary video drivers enabled. 10.10 is  just not yet ready enough for inexperienced users, and it might be quite  tricky getting your system to work.

I suggest you boot up with the live 10.04 CD, copy all your personal  data onto a USB drive and then reinstall 10.04. That may very well be  quicker and less stressful than trying to repair a broken 10.10 which  may still continue to exhibit breakages for the next couple of weeks or  so.

---

### Post by limjix on 2010-09-11
@coffeecat

Thanks alot for the advice, i just booted my laptop into 10.04 using a live USB. Now copying the files to an external harddrive.

Which will be better? Doing a clean install? or using the

sudo apt-get update
sudo apt-get install ubuntu-desktop

command?

Thanks again!

---

### Post by arpanaut on 2010-09-11
> **limjix said:**
> Will by using the 

sudo apt-get update
sudo apt-get install ubuntu-desktop

command delete all the data on my partition?

Thanks

No, It's worth a shot.
The problem is probably broken video drivers, especially if you had proprietary drivers installed.The new X-org on Maverick is not compatable with older drivers.

If the previous suggestion does not work, try booting into recovery mode and selecting low graphics boot. If that works go to system> administration> Hardware drivers, and disable any video driver you have there if you have ATI.  If you have nVidia I believe the new driver is available and works. then reboot normally, see if that works.

If that don't work come back here and we can try some other things.

If you don't have any really unusual hardware things should be recoverable.

---

### Post by coffeecat on 2010-09-11
> **limjix said:**
> @coffeecat

Thanks alot for the advice, i just booted my laptop into 10.04 using a live USB. Now copying the files to an external harddrive.

Which will be better? Doing a clean install? or using the

sudo apt-get update
sudo apt-get install ubuntu-desktop

command?

Thanks again!

I'm glad you've backed up your files. That was a good move.

Follow arpanaut's advice for now. The system may be recoverable but bear in mind what I said about instability in a pre-release version.

What video card do you have and did you install the proprietary driver - i.e. from 'Hardware Drivers'?

---

### Post by overdrank on 2010-09-11
Moved to Maverick Meerkat Testing and Discussion

---

### Post by limjix on 2010-09-11
I am using a laptop with an ATI RADEON 5430 card and i was using ATI's proprietary driver.

How do i boot into recovery mode?

---

### Post by arpanaut on 2010-09-11
Single OS installed?

If so, immediately after POST hold down the shift key and the grub menu should be presented -> choose recovery mode.

---

### Post by limjix on 2010-09-11
Okay so i am in recovery mode, i have a menu that asks me to choose:

resume
clean
dpkg
failsafex
grub
netroot
root

How do i disable the graphics driver now?

---

### Post by arpanaut on 2010-09-11
failsafex and hopefully that will get you to the desktop

then go to the Hardware Drivers section and disable the ATI drivers, then reboot
that should engage the default FOSS drivers.

There are no proprietary ATI drivers that are working Iin Maverick for now.

---

### Post by limjix on 2010-09-11
Tried it already, it doesn't work. I also tried using the command line to do


sudo apt-get update
sudo apt-get install ubuntu-desktop

but i can't use it to downgrade the system back to 10.04

So wats the next plan?

Question: If i do a fresh install, and then i copy the whole old linux directory, will the system be restored to the point before i upgraded?

---

### Post by arpanaut on 2010-09-11
Bummer dude! well it was worth the shot.

Unfortunately it is not that simple to get back to where you were.
Let me do some digging for some more recovery tactics.

For now try  netboot, and try

```
sudo apt-get update && sudo apt-get upgrade
```

It might shake some things out... and might give some error messages we can work with

---

### Post by limjix on 2010-09-11
I think ill give up on trying to make 10.10 work haha. Can you help me get back to the original point instead?

Thanks for all your help so far bro

---

### Post by arpanaut on 2010-09-11
Well, since you didn't backup your partition until after you tried to upgrade, what you have in anything other than /home is not going to do you much good.

How fresh of an install was your 10.04?

You are looking at a reinstall, of the OS and then reinstalling all your apps and programs. You can then transfer your data back into the appropriate folders in /home.

You can save your firefox profile, and your e-mail, but personally I wouldn't try to save much else of your configuration files (hidden files) in /home.

Sorry to be the bearer of bad news, Sometimes a fresh start is just what the system needs... at least you have a good idea of how you want things now, Experience is a wonderful teacher!

There a bunch of people around here a lot smarter, and more experienced than I am, so you might want to hang tight and wait to see if you can get some additional advice. 
I think you can probably recover your system, I just don't have my CLI chops down well enough to help you right now, Sorry

Good Luck.

---

### Post by limjix on 2010-09-11
Haha well i just finished reinstalling my whole operating system.
Really true that experience is the best teacher. Now i know never to mess with Beta versions until it is stable haha.

Its my first few months using Ubuntu so its been a crazy learning experience cause you don't do stuff in Windows like this.

Anyways thank you so much for your help! Really good to know there are good people around to help instead of those people who just tell you to google it or point out your stupidity before helping you.

Kudos to you ! :D

---

### Post by coffeecat on 2010-09-11
> **limjix said:**
> Its my first few months using Ubuntu so its been a crazy learning experience cause you don't do stuff in Windows like this.

And an excellent learning experience too. I broke and reinstalled several Linux distros in my first few months. That taught me a lot. The trick is to keep your personal files adequately backed up.

Have fun! :)

---

### Post by limjix on 2010-09-11
Personal files meaning? Stuff in the home folder?

---

### Post by arpanaut on 2010-09-11
No Problem!

The first few months I used Ubuntu I reinstalled dozens of times because I didn't have a clue how to recover from my own ignorant actions. LOL I'd get stuck at the terminal and didn't know that most of the time recovery was just a few commands away... but not knowing anything, I'd just reinstall and started over.

That's when I found this place and the slow process of learning linux began.
Yup! Good people around here!

Take Care...

---

### Post by coffeecat on 2010-09-11
> **limjix said:**
> Personal files meaning?

You know - personal files. All your mp3s, photos, documents, etc.

---

### Post by unclefrancis on 2010-09-11
> **arpanaut said:**
> No Problem!

The first few months I used Ubuntu I reinstalled dozens of times because I didn't have a clue how to recover from my own ignorant actions. LOL I'd get stuck at the terminal and didn't know that most of the time recovery was just a few commands away... but not knowing anything, I'd just reinstall and started over.

That's when I found this place and the slow process of learning linux began.
Yup! Good people around here!

Take Care...
I'm new to linux and have been lurking around the forums for a couple months. Most everyone on here is nice and extreamly helpful. I havent had to ask for support yet simply because my questions have been answered all ready. so, thanks forum people! And just so this isnt a total waste of space, dont do any partial upgrades like I did...oops. got things straightened out for now.

---

