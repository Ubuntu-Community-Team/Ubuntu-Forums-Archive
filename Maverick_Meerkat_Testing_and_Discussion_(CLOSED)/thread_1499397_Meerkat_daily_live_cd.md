---
title: "Meerkat daily live cd"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jppr on 2010-05-27
[URL="http://cdimage.ubuntu.com/daily/"]http://cdimage.ubuntu.com/daily/  
[/URL]

---

### Post by andrewabc on 2010-05-27
Thanks for the info.

I'll be waiting 1 week when alpha 1 is released on June 3.

livecd not uploaded yet.

---

### Post by ranch hand on 2010-05-27
I knew the bugger had to start before the A1 release.  We have to test the ISO for A1 somehow.

Thanks for the heads up.

---

### Post by wayneericgouin on 2010-05-27
When do the live iso's come out? the alternates dont seem to work in Vbox for me anyway

---

### Post by VMC on 2010-05-27
> **wayneericgouin said:**
> When do the live iso's come out? the alternates dont seem to work in Vbox for me anyway

That's what I'm waiting for also. I was keeping both sync'ed in the past, but since daily-live worked so well under Lucid I decided to stop using alternate.

---

### Post by wayneericgouin on 2010-05-27
Yes, I much prefer the live builds also. For some reason the alternates never pan out for me.

---

### Post by ratcheer on 2010-05-27
Funny, I have a lot more luck with the alternates than the lives. At least, with Lucid I did.

Tim

---

### Post by wayneericgouin on 2010-05-27
I tried the alternate about 5 hours ago and ran into an error where it wasn't downloading certain packages, maybe isolated I'm not sure.

---

### Post by wilee-nilee on 2010-05-27
With Lucid I found that a loaded thumb was the most reliable source, but this is just my personal experience. I used both the ubuntu loader and unetbootin, and I always deleted the fat32 and reformatted in gparted before every reload.

---

### Post by Starks on 2010-05-27
LiveUSB using the alternate iso isn't very fun.

---

### Post by wayneericgouin on 2010-05-27
I wonder, Is simply upgrading to maverick packages the same as the daily builds or is it entirely different?

---

### Post by wojox on 2010-05-27
> **wayneericgouin said:**
> I wonder, Is simply upgrading to maverick packages the same as the daily builds or is it entirely different?

Ditto, I'm lost as well.

---

### Post by Starks on 2010-05-27
The same.

---

### Post by ronacc on 2010-05-27
AFAIK the dailys are just a snapshot of the repo at a certain point in time . So upgrading would be the same until more commits were made and then the upgrade at that moment would be newer (until the next daily ).

---

### Post by wayneericgouin on 2010-05-27
ok, that makes sense. Thanks for clarifying for us.

---

### Post by jppr on 2010-05-27
> **ronacc said:**
> AFAIK the dailys are just a snapshot of the repo at a certain point in time . So upgrading would be the same until more commits were made and then the upgrade at that moment would be newer (until the next daily ).

This is same thing like Alpha 1/2/3, Beta, RC. Those are just a snapshot of the repo at a certain point in time. = )

---

### Post by Loxx on 2010-05-27
just grabbing this now to correct some issues with the upgrade from lucid to maverick

---

### Post by Def_101 on 2010-05-27
I seem to only have issues when trying to use the mini.iso. Live and alt work flawlessly, but i prefer the alternate for the option to install command-line-only.

---

### Post by wayneericgouin on 2010-05-27
Well, the problem I had as it turns out, was my attempt to use the alternate via usb drive,that didn't work out no matter the method I tried.I didn't mean to imply that something was wrong with the alternate iso.

---

### Post by ratcheer on 2010-05-27
Yep, I just had to try the daily. destroyed my test system. Install was going well, but failed in step "Select and install software" after step about 40% completed. I can boot it to a text login and I can log in, but it will not start the desktop (gdm unknown).

Is this something I can open a bug for in launchpad?

Tim

---

### Post by wayneericgouin on 2010-05-27
Yes, that's what I ran into as well, after I downed a few shots I tried again and got the installation complete although without gdm or ubuntu-desktop installed.

---

### Post by kansasnoob on 2010-05-27
Far out! 

With alpha 1 coming on the 3rd we should see iso-testing in just a few days, and I can tell you that legitimate bugs reported during iso-testing ALWAYS get some attention!

I hope there will be an official upgrade option so I can try to get some attention focused on this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Let's kill some bugs!

---

### Post by Starks on 2010-05-27
Don't get me wrong, there are benefits to installing from the daily iso over upgrading from Lucid.

Most importantly though, the system environment would undoubtedly be cleaner.

---

### Post by wayneericgouin on 2010-05-27
Yea, I fully intend on getting a live-daily once available, it will ease my mind.

---

### Post by ranch hand on 2010-05-27
If you log in on the terminal login you should be able to install any missing items from there such as thee ubuntu-desktop.  I believe that xhould also get you the gdm (not sure but you can apt-get install it too).

---

### Post by ranch hand on 2010-05-27
> **kansasnoob said:**
> Far out! 

With alpha 1 coming on the 3rd we should see iso-testing in just a few days, and I can tell you that legitimate bugs reported during iso-testing ALWAYS get some attention!

I hope there will be an official upgrade option so I can try to get some attention focused on this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Let's kill some bugs!
 I would sure hope so.  That is causing a lot of problems, particularly for folks suffering from MS.

---

### Post by Universal344 on 2010-05-27
> **ranch hand said:**
> If you log in on the terminal login you should be able to install any missing items from there such as thee ubuntu-desktop.  I believe that xhould also get you the gdm (not sure but you can apt-get install it too).

That was what I was hoping, but when I rebooted, my sources.list only listed the CD so I had to chroot in from my stable Lucid install and copy in my sources.list from there replacing all lucid's with maverick's.  But when I ran apt-get update it told me the http method failed after trying to read a couple repositories.  However I may just be doing something wrong.  On the plus side though, the thing booted insanely fast (however this may be due to the fact that I have no functioning Plymouth or X or all that extra stuff).

---

### Post by ratcheer on 2010-05-27
> **ranch hand said:**
> If you log in on the terminal login you should be able to install any missing items from there such as thee ubuntu-desktop.  I believe that xhould also get you the gdm (not sure but you can apt-get install it too).

But, as the "Select and install software" step was only partially complete, there would be ***a lot*** of stuff missing. I'll just zsync the iso and try again, tomorrow.

Tim

---

### Post by wayneericgouin on 2010-05-27
Yes I tried some really ugly methods to get the sources read after the installation, but to no avail. I wasnt sure if it was something I did to cause it or not.

---

### Post by wayneericgouin on 2010-05-28
Is it possible to install the daily alternate from a usb stick similar to the live-cd method?

---

### Post by jppr on 2010-05-28
> **wayneericgouin said:**
> Is it possible to install the daily alternate from a usb stick similar to the live-cd method?

Yes, it is possible. I did already  lucid usb stick installs, both live-cd and alternate, i never use the cd discs. That yesterdays daily-build is broken and its not possible install even cd discs...

---

### Post by wayneericgouin on 2010-05-28
I got the alternate working now via usb drive, used the syslinux.cfg method by pointing it to the usb stick rather than cd.

---

### Post by Universal344 on 2010-05-28
I got mine to work, looks like it was just an issue w/ the repos yesterday.  If anyone wants to fix their install, just chroot in from a lucid CD and copy the sources.list file over (making sure you replace all instances of 'lucid' with 'maverick' first), run apt-get update and then apt-get install gdm ubuntu-desktop.  However, be warned this takes a very very long time to install, you'll want at least an hour.

---

### Post by Starks on 2010-05-28
> **wayneericgouin said:**
> I got the alternate working now via usb drive, used the syslinux.cfg method by pointing it to the usb stick rather than cd.
I didn't even need to do that.

usb-creator/Startup Disk Creator worked fine.

---

### Post by wayneericgouin on 2010-05-28
Well, the real problem as I see it now was the repos, but at the time I didnt realize that so I assumed it was a problem with the alternate not reading the usb drive as the installation media, which is why I edited the syslinux.cfg. But as it turns out it was in fact the repos. So case closed for me at least.

---

### Post by ratcheer on 2010-05-28
Ok, thanks for the info about the repos. I will just do a clean re-install of the CD.

Tim

---

### Post by ratcheer on 2010-05-28
> **ratcheer said:**
> Ok, thanks for the info about the repos. I will just do a clean re-install of the CD.

Tim

I still got the same failure about five times.

Tim

---

### Post by wayneericgouin on 2010-05-28
If your trying to install it from a usb stick try adding cdrom-detect/try-usb=true to the syslinux.cfg file on the usb stick. That's how in the end I got it to work.

---

### Post by ratcheer on 2010-05-28
If you are talking to me, no, I am just using the daily alternate CD image.

Tim

---

### Post by wayneericgouin on 2010-05-28
Oh,  ok I thought maybe you were having the same issue I had, I apologize for misinterpreting.

---

### Post by phillw on 2010-05-29
Hi,

any news on when the 'powers that be' want the iso build testing yet for the Desktop Version?

Regards,

Phill.

---

### Post by andrewabc on 2010-05-30
> **phillw said:**
> Hi,

any news on when the 'powers that be' want the iso build testing yet for the Desktop Version?

Regards,

Phill.

I think I remember in Karmic or Lucid development, the first alpha only had alternate install. So maybe the same will happen again.

---

### Post by thaumielx72 on 2010-05-30
> **Universal344 said:**
> I got mine to work, looks like it was just an issue w/ the repos yesterday.  If anyone wants to fix their install, just chroot in from a lucid CD and copy the sources.list file over (making sure you replace all instances of 'lucid' with 'maverick' first), run apt-get update and then apt-get install gdm ubuntu-desktop.  However, be warned this takes a very very long time to install, you'll want at least an hour.

Hmmm.  This ran for about 3 seconds on my machine.  It also did not load gnome if that's what the purpose was.  I understand command line well enough to go on but I thought gnome would be in the repo's as it doesn't change that much from the earlier version.

Well I started with command line back in the old DOS days so I'll be OK.  I guess I keep doing apt-get update regularly to keep up with the development, right?

---

### Post by crjackson on 2010-05-30
> **thaumielx72 said:**
> Hmmm.  This ran for about 3 seconds on my machine.  It also did not load gnome if that's what the purpose was.  I understand command line well enough to go on but I thought gnome would be in the repo's as it doesn't change that much from the earlier version.

Well I started with command line back in the old DOS days so I'll be OK.  I guess I keep doing apt-get update regularly to keep up with the development, right?

Not update, upgrade...

sudo aptitude safe-upgrade

---

### Post by cecilpierce on 2010-05-31
"E: Invalid operation safe-upgrade"

doesn't seen to work anymore!

sorry i use apt-get, not aptitude.

---

### Post by null_pointer_us on 2010-05-31
@crjackson

Actually, he said up**d**a**t**e, which is for updating the file lists while up**gr**a**d**e and safe-upgrade are for performing updates. It's a shame they are so similar-looking and have overlapping meanings in normal usage. :(

---

### Post by jppr on 2010-05-31
this works [http://cdimage.ubuntu.com/daily/20100531.2/](http://cdimage.ubuntu.com/daily/20100531.2/)
I did  just clean usb installation and the system works fine :)

---

### Post by VMC on 2010-05-31
[**daily-live**]("http://cdimage.ubuntu.com/daily-live/current/") is now on-board. Alternate has been active for several days, but this is the first time I noticed daily-live Maverick ISO.

---

### Post by Vorksholk on 2010-05-31
Is there another version that is not alternative install out yet?

---

### Post by Vorksholk on 2010-05-31
Hence the name, is there a new build every day?

---

### Post by Vorksholk on 2010-05-31
Never mind, sorry, I found the non-alternative: [http://cdimage.ubuntu.com/daily-live/20100531/](http://cdimage.ubuntu.com/daily-live/20100531/)

---

### Post by Vorksholk on 2010-05-31
I'm sorry, I was being dumb. I found the daily-live .iso [http://cdimage.ubuntu.com/daily-live/20100531/](http://cdimage.ubuntu.com/daily-live/20100531/)

---

### Post by Vorksholk on 2010-05-31
I'm sorry, I didn't think it posted.... I will be quiet now.

---

### Post by cecilpierce on 2010-05-31
I just put maverick-desktop-i386.iso on a flash drive using UNetbootin and got: "FATAL: Error inserting vesafs" then into a shell (initramfs).
Anybody know about this? Im going to try Startup Disk Creator and see what happens, the md5sum checked out ok!

---

### Post by ranch hand on 2010-05-31
I am not sure that I would use that yet.  We are going to have to test the ISO before the release of A1.  I suspect that they are trying to get the ISO ready for that.

---

### Post by ratcheer on 2010-05-31
I could not get a completed installation of the 5/27 alternate CD image (see my earlier posts in this thread), but I am glad to be able to report that today's alternate image installed, perfectly.

Tim

---

### Post by VMC on 2010-05-31
> **cecilpierce said:**
> I just put maverick-desktop-i386.iso on a flash drive using UNetbootin and got: "FATAL: Error inserting vesafs" then into a shell (initramfs).
Anybody know about this? Im going to try Startup Disk Creator and see what happens, the md5sum checked out ok!

Somethings wrong. I tried try before install, then install, then I removed quiet to see what was wrong, but it had all kinds of errors. The md5sum matched. Will try again tomorrow.

> f264ebd29b9c54f9945b254c4e03d02b *maverick-desktop-i386.iso

---

### Post by jppr on 2010-05-31
> **ranch hand said:**
> I am not sure that I would use that yet.  We are going to have to test the ISO before the release of A1.  I suspect that they are trying to get the ISO ready for that.

Why you think, that if you do now fresh installation you can´t do then ISO test? I did now fresh alternate installation and i don´t have any problem and i do ISO test when it is out. :)

---

### Post by cecilpierce on 2010-05-31
At least Startup Disk Creator worked better then UNetbootin, went all the way to "Plymouth" and three red lights and then BOOM! pre-mature-lockup, tried all the choices on the menu and nuttin!
Guess ranch hand had a good idea, wait till A1.

---

### Post by ranch hand on 2010-05-31
> **jppr said:**
> Why you think, that if you do now fresh installation you can´t do then ISO test? I did now fresh alternate installation and i don´t have any problem and i do ISO test when it is out. :)
No, I just think that seeing how this is the first they put up it may not be good.

---

### Post by wayneericgouin on 2010-06-01
I tried the x64 live and had it installed without a hitch. So what gives.

---

### Post by ranch hand on 2010-06-01
I do not know when you downloaded but I just checked and we are up for testing the ISO.  You may have a newer version, you are using 64 instead of 32, it is early days so maybe it likes your hardware better than some others.  Take your pick.

I am going to download the thing again and burn it so I can try it tomorrow in the morning.  I have the one from this morning but it is another day GST (I guess it is here to now that I look at the time).

---

### Post by ranch hand on 2010-06-01
I just checked again and we do not appear to be testing the Live CD.  Just UM upgrades and the Alt install CD.

---

### Post by wayneericgouin on 2010-06-01
I just tried the the 32 bit and it ended up dropping to busybox, perhaps I'll wait on Alpha.

---

### Post by ranch hand on 2010-06-01
Upgrades work or none of us would be using it.   The alternate install CD has been working.

The ISO team is calling for tests of the UM update and the Alternate install CD.

You need a Launchpad account that you should have if you are testing a pre-release OS.  And you need to join the testing team so that you can report your results.

It is a good thing to have these things tested on as much different hardware as possible and it is kind of fun.

You should not even think of using this as a production OS until, at least, the beta stage.  I do but it is on a separate drive and I have several installs so if one breaks I have others to fall back on.

For information on the ISO testing (this is why the ISOs end up working at release time) here is a link that will tell you about it and links to join the FUN.  Yes it is still referring to 10.04 don't let that bother you;

[https://wiki.ubuntu.com/Testing/ISO](https://wiki.ubuntu.com/Testing/ISO)

---

### Post by 23meg on 2010-06-01
> **ranch hand said:**
> 
For information on the ISO testing (this is why the ISOs end up working at release time) here is a link that will tell you about it and links to join the FUN.  Yes it is still referring to 10.04 don't let that bother you;

[https://wiki.ubuntu.com/Testing/ISO](https://wiki.ubuntu.com/Testing/ISO)

[It's time]("http://ubuntuforums.org/showthread.php?t=1498784")!

---

### Post by phillw on 2010-06-01
> **23meg said:**
> [It's time]("http://ubuntuforums.org/showthread.php?t=1498784")!

And it's an official hello to 10.10 from  me. (well, in 3hours when the iso has downloaded) :P

Regards,

Phill.

---

### Post by wilee-nilee on 2010-06-01
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

And for you rsync folks.
```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/maverick-desktop-i386.iso .
```

---

### Post by cariboo on 2010-06-01
Merged two threads on the same subject.

---

### Post by wilee-nilee on 2010-06-01
> **cariboo907 said:**
> Merged two threads on the same subject.

Sorry about that I wondered if this wasn't the case, thanks.

---

