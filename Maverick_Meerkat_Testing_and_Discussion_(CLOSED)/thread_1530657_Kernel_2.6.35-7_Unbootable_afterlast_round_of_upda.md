---
title: "Kernel 2.6.35-7 Unbootable afterlast round of updates"
date: 2010-07-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-07-13
Hey all ...running 10.10 Alpha2

Maybe I screwed up, but after the latest round of updates today Jul 13th approx. 6pm EST suddenly kernel 2.6.35-7 is no longer bootable for me using an iMac 24" late 2008 model. 1GB ram. Seems like an xorg thing ...doesn't give me the flashing cursor when booting after choosing the kernel ....just a blank screen ...tries to boot just freezes looks like a graphics issue? Not sure ...am booting now with the 2.6.32-23 kernel. I am afraid to do anymore updates as I don't want this kernel to become unbootable. Any ideas what I can do to try and fix kernel 2.6.35-7?

It may  have been the updates from this morning Jul 13 ...approx 8:30am EST ...or
latest round Jul 13 approx 6:00pm EST

Thanks ...

Jaco

P.S. Man ...everything was running smoothly until today ....bummer :( I did the upgrade from 10.04 which I'd been running for the longest time. The upgrade went off with out a hitch ...all was good with  kernel 2.6.35-7 until today.

---

### Post by jaco223 on 2010-07-14
Bump

---

### Post by iponeverything on 2010-07-14
Use dpkg to remove 2.6.35-7. I would go ahead with other updates and try the kernel again when moves past 2.6.35-7. 

Open synaptic and search for working kernel select it then go to:

Package -> Lock Version

Running the pre-betas is always an adventure.

---

### Post by wayneericgouin on 2010-07-14
It seems to be the proprietary graphics drivers, for me everything works up until I combine the new kernal with the nvidia currents. On a related note could someone walk me through how to use dpkg to revert back to a working kernel?

---

### Post by iponeverything on 2010-07-14
Fire up Synaptic and remove it from there. :)

---

### Post by wayneericgouin on 2010-07-14
Even with the kernel locked at 2.6.35-6 the proprietary drivers caused X not to start so I'm wondering if perhaps its the drivers and not the kernel, I cant say.

---

### Post by awam66 on 2010-07-14
> **wayneericgouin said:**
> It seems to be the proprietary graphics drivers, for me everything works up until I combine the new kernal with the nvidia currents. On a related note could someone walk me through how to use dpkg to revert back to a working kernel?

Yes I am having problems too. I managed to log in using the rescue boot and tried to install the Nvidia proprietry drivers. This failed and left me with an unbootable system. I can get to the root prompt but startx fails with a can't find file (which of course I can't remember).
How can I get rid of the nvidia driver from the root prompt?

---

### Post by iponeverything on 2010-07-14
Try this to downgrade:

cd to the directory and identify the previous version of the package:

```

cd /var/cache/apt/archives/
ls -ltr |grep -i nvidia

```

downgrade with:

```

sudo dpkg -i <package>

```

---

### Post by wayneericgouin on 2010-07-14
I just tried a fresh install but this time using the 173 drivers which also led to X not starting. So I'm now I'm even more confused about this. I rarely have a problem I cant figure out but when it comes to these proprietary graphics drivers I always end up ripping my hair out.

---

### Post by iponeverything on 2010-07-14
any clues in:  /var/log/Xorg.0.log

Just noticed that you are in Helsinki, I going to be there next month for 4 days.

---

### Post by wayneericgouin on 2010-07-14
The only error in the log that I noticed was (drm) failed to load.
if it helps, I noticed the driver version was 256.35.And, I warn you, if you come to Helsinki you wont want to leave, I came here for a visit about 12 years ago and never left. (also, xorg.conf is empty)

---

### Post by iponeverything on 2010-07-14
Its strange that a clean install didn't work when it had worked before. Did you use any kernel options for the first install?

---

### Post by wayneericgouin on 2010-07-14
Just a clean install with the kernel locked, at least it dropped me to a shell rather than locking at a black screen.In addition, after using dpkg to downgrade the drivers I still end up at the command line log in.

---

### Post by andrewthomas on 2010-07-14
I was having a similar boot problem that was due to the new grub2 package ```
grub2 (1.98+20100710-1ubuntu1)
``` what I had to do was get edit the menu and remove
```
    recordfail
    load_video
    set gfxpayload=keep
```then I can boot.  Look at your grub.cfg and see if those lines are in your main entries.

I just filed a bug against the grub2 package about this issue.  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614)

---

### Post by wayneericgouin on 2010-07-14
So, just edit /etc/default/grub?

---

### Post by ranch hand on 2010-07-14
That would do it.

Also remember to run;
```

sudo update-grub

```
You can try it first by just getting to the screen menu and hitting e.  This will let you edit the menu entry as you want for just that boot.  After editing hit Ctrl + x to boot.

---

### Post by jaco223 on 2010-07-14
> **iponeverything said:**
> Use dpkg to remove 2.6.35-7. I would go ahead with other updates and try the kernel again when moves past 2.6.35-7. 

Open synaptic and search for working kernel select it then go to:

Package -> Lock Version

Running the pre-betas is always an adventure.

I did what you told me to do ...and I uninstalled the kernel source for my wireless driver
and now can not activate the STA wireless broadcom driver so my wireless is ****ed now
and can not reinstall the driver says to look at the jockey.log file...Man ....sucks

---

### Post by iponeverything on 2010-07-14
Just unlock the version tell synaptic to install it, it should not have to go out to the Internet to get it.

the package will still be in
/var/cache/apt/archives

---

### Post by jaco223 on 2010-07-14
> **iponeverything said:**
> Just unlock the version tell synaptic to install it, it should not have to go out to the Internet to get it.

the package will still be in
/var/cache/apt/archives

I don't know how to unlock it

---

### Post by iponeverything on 2010-07-14
I have to admit that I am somewhat curious about why you are running 10.10 Alfa instead of 10.04 LTS. Surely you know that the Alfa's are a pain if you don't enjoy constantly debugging problems and searching through LaunchPad. 

Running the Alfa is great way to learn though, but like most things worth learning it can be somewhat painful at times.

---

### Post by iponeverything on 2010-07-14
To Unlock it do the same thing that you did to lock it. 

Open synaptic and search for package:

Package -> Lock Version

and uncheck the box

---

### Post by jaco223 on 2010-07-14
> **iponeverything said:**
> I have to admit that I am somewhat curious about why you are running 10.10 Alfa instead of 10.04 LTS. Surely you know that the Alfa's are a pain if you don't enjoy constantly debugging problems and searching through LaunchPad. 

Running the Alfa is great way to learn though, but like most things worth learning it can be somewhat painful at times.

Dude I'm running it because I want to run it ....not trying to be rude but ....
Now I reinstalled the bcmwl kernel source for wireless and I still can't activate the
wireless driver. tells me to look at jockey.log

Man I can see a complete reinstall coming

---

### Post by ranch hand on 2010-07-15
> **iponeverything said:**
> I have to admit that I am somewhat curious about why you are running 10.10 Alfa instead of 10.04 LTS. Surely you know that the Alfa's are a pain if you don't enjoy constantly debugging problems and searching through LaunchPad. 

Running the Alfa is great way to learn though, but like most things worth learning it can be somewhat painful at times.
Oh come on now, this is where the FUN is.  Sometimes more fun than others.  i got to chroot into one install to do update/upgradesduring 9.10 testing for 10 days before the bugger would boot again.

It doesn't get much more FUN than the day it would boot.

---

### Post by jaco223 on 2010-07-15
> **ranch hand said:**
> Oh come on now, this is where the FUN is.  Sometimes more fun than others.  i got to chroot into one install to do update/upgradesduring 9.10 testing for 10 days before the bugger would boot again.

It doesn't get much more FUN than the day it would boot.

Dude I never understand your posts/replies nit to be rude ....maybe you're a linux guru ...
but now my system is completely hosed ....no wireless ....and you offer no help.....
I don't know dude ....strange

---

### Post by cariboo on 2010-07-15
> **jaco223 said:**
> Dude I'm running it because I want to run it ....not trying to be rude but ....
Now I reinstalled the bcmwl kernel source for wireless and I still can't activate the
wireless driver. tells me to look at jockey.log

Man I can see a complete reinstall coming

So what does /var/log/jockey.log tell you?

---

### Post by wayneericgouin on 2010-07-15
Just for testing purposes I tried a clean install and fully updated everything except for the kernel and grub, and ended up with the same problem...X wont start.So now I'm really confused.

---

### Post by caryb on 2010-07-15
2.6.35-8 just hit the repo's that might help!

Cary

---

### Post by wayneericgouin on 2010-07-15
I hope so lol, I dont mind a little breakage but this one got old fast.

---

### Post by iponeverything on 2010-07-15
> **jaco223 said:**
> Dude I'm running it because I want to run it ....not trying to be rude but ....
Now I reinstalled the bcmwl kernel source for wireless and I still can't activate the
wireless driver. tells me to look at jockey.log

Man I can see a complete reinstall coming


ok :) I am glad you want to, without adventurous souls like you Ubuntu would not be evolving as fast as it does. I didn't take is as being rude, you just seemed seemed surprised when things went south after an update. Expect lots of things to break in the alpha. What I do is have separate partition for testing, this way I just boot to stable release when I just want check my email after alpha borked itself again... 

I don't think that alphas should be gurus only, far from it - it take guru and novice alike properly test a new releases - with that said - thanks. 

If you reinstall, leave enough space for a 10.04 install too so that can work on things from the working install if need be.

---

### Post by wayneericgouin on 2010-07-15
> **andrewthomas said:**
> I was having a similar boot problem that was due to the new grub2 package ```
grub2 (1.98+20100710-1ubuntu1)
``` what I had to do was get edit the menu and remove
```
    recordfail
    load_video
    set gfxpayload=keep
```then I can boot.  Look at your grub.cfg and see if those lines are in your main entries.

I just filed a bug against the grub2 package about this issue.  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614)

I can confirm that this does the trick, in addition the 2.6.35-8 kernel upgrade did not remedy this.

---

### Post by wayneericgouin on 2010-07-15
> **andrewthomas said:**
> I was having a similar boot problem that was due to the new grub2 package ```
grub2 (1.98+20100710-1ubuntu1)
``` what I had to do was get edit the menu and remove
```
    recordfail
    load_video
    set gfxpayload=keep
```then I can boot.  Look at your grub.cfg and see if those lines are in your main entries.

I just filed a bug against the grub2 package about this issue.  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614)
  Does anyone know how I might put this in /etc/default/grub to make it stick?

---

### Post by iponeverything on 2010-07-15
> Does anyone know how I might put this in /etc/default/grub to make it stick?

```
sudo nano /etc/default/grub
```



Add these lines at line 9:

```

GRUB_CMDLINE_LINUX="recordfail"
GRUB_CMDLINE_LINUX="load_video"
GRUB_CMDLINE_LINUX="set gfxpayload=keep"

```

then run:

```
sudo update-grub
```

---

### Post by trulan on 2010-07-15
> **jaco223 said:**
> Dude I never understand your posts/replies nit to be rude ....maybe you're a linux guru ...
but now my system is completely hosed ....no wireless ....and you offer no help.....
I don't know dude ....strange
Actually Ranch Hand did offer you help for an unbootable system - chroot.  Google "chroot upgrade ubuntu" and see what you can learn.  When testing an alpha there will likely be times that the only way to rescue it is to boot from a live cd or another Linux install on your computer, chroot into the broken alpha, and upgrade it that way.

---

### Post by wayneericgouin on 2010-07-15
> **iponeverything said:**
> ```
sudo nano /etc/default/grub
```



Add these lines at line 9:

```

GRUB_CMDLINE_LINUX="recordfail"
GRUB_CMDLINE_LINUX="load_video"
GRUB_CMDLINE_LINUX="set gfxpayload=keep"

```

then run:

```
sudo update-grub
```

thats to stop it from loading right?

---

### Post by iponeverything on 2010-07-15
No that is to load with those options.


To not load with those options:

```
sudo nano /etc/default/grub
```

and remove the lines that contain:

```

recordfail 
load_video
set gfxpayload=keep

```

---

### Post by andrewthomas on 2010-07-15
> **andrewthomas said:**
> 
```
    recordfail
    load_video
    set gfxpayload=keep
```
Actually if you change```
 set gfxpayload=keep
``` to ```
set gfxpayload=text
``` everything will be good.

To make permanent: add this line to /etc/default/grub:```
 GRUB_GFXPAYLOAD_LINUX=text
```

---

### Post by jaco223 on 2010-07-15
> **trulan said:**
> Actually Ranch Hand did offer you help for an unbootable system - chroot.  Google "chroot upgrade ubuntu" and see what you can learn.  When testing an alpha there will likely be times that the only way to rescue it is to boot from a live cd or another Linux install on your computer, chroot into the broken alpha, and upgrade it that way.

I'm sorry if I seemed rude ....didn't mean to be ....I'm still a n00b ....with that said I didn't realise he was
offering ....so my apologies to everyone in the thread. I did a fresh install of 10.10 ...was confused as to
where to put the boor  loader....I'm dual booting Mac OSX and Ubuntu ....weird thing I wasn't able to install
grub on sda3 which is where I installed it on 10.04....I chose sd4 and it installed it there but was unbootable.
In refit, it showed an HD install and a partition 4 choice ....neither would boot ....I''m going to re-install again,
and see if the default location where the installer wanted to put grub will work ...Man I hope I don't screw my OSX installation .....looks like a long day in front of me ..... :)

---

### Post by wayneericgouin on 2010-07-15
On a somewhat related note, does anyone know if this bug affects Karmic and Lucid as well, or is it isolated to maverick? I ask because I ran into a similar issue on my wife's fresh lucid install.

---

### Post by andrewthomas on 2010-07-15
> **wayneericgouin said:**
> On a somewhat related note, does anyone know if this bug affects Karmic and Lucid as well, or is it isolated to maverick? I ask because I ran into a similar issue on my wife's fresh lucid install.
Look at the grub.cfg for the offending lines.  Or push 'e' at the grub menu.

---

### Post by trulan on 2010-07-15
> **jaco223 said:**
> I'm sorry if I seemed rude ....didn't mean to be ....I'm still a n00b ....
Hey it's OK.  We're all here more or less to learn, and like Ranch Hand said, it's supposed to be fun too.  It's fine if you want to test an alpha even if you're new - but if you're frustrated with it, it makes it harder to fix problems, and impedes the learning process.  So if you can keep your cool in the face of major breakage, and stick with it until that delightful "Hey, it works again!" moment, then welcome to Alpha testing!
> **wayneericgouin said:**
> On a somewhat related note, does anyone  know if this bug affects Karmic and Lucid as well, or is it isolated to  maverick? I ask because I ran into a similar issue on my wife's fresh  lucid install.
Those 'offending' lines are not there in Karmic (Karmic is controlling grub2 on my test box).  I put them there just to see what would happen...recordfail and load_video are unknown commands.  set gfxpayload=keep gives me a graphical splash screen (plymouth?) rather than the text one that usually shows when booting Maverick.  It does not cause boot to fail.

---

### Post by jaco223 on 2010-07-15
> **trulan said:**
> Hey it's OK.  We're all here more or less to learn, and like Ranch Hand said, it's supposed to be fun too.  It's fine if you want to test an alpha even if you're new - but if you're frustrated with it, it makes it harder to fix problems, and impedes the learning process.  So if you can keep your cool in the face of major breakage, and stick with it until that delightful "Hey, it works again!" moment, then welcome to Alpha testing! .

Trulan ....

Thanks dude....I spent a painful afternoon completely wiping my mac and reinstalling everything .....Sigh ...
just finished installing lucid 10.04 with all updates ....got my wireless back ....am going to jump to Maverick Alpha2 without installing the offending kernel ...I think that should do the trick ....everything should be ok ...
Thanks for understanding my bit of frustration ......I guess I'm a n00b .....I consider myself one ...I ran Lucid from the Beta stage on ....until my upgrade to Maverick Alpha2 .....still have tons to learn ....

Thanks

Jaco

---

### Post by cariboo on 2010-07-16
If you have the hard drive space, it may be an idea to install Maverick on a separate partition, just in case something else blows up.

---

