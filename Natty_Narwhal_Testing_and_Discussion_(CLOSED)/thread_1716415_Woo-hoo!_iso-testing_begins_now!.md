---
title: "Woo-hoo! iso-testing begins now!"
date: 2011-03-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-28
Be sure you have the proper image:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Check the md5sum against that published there :)

---

### Post by cariboo on 2011-03-28
I'm downloading a fresh daily iso as I type this. :)

---

### Post by Kirboosy on 2011-03-28
AWESOME!! Downloading it now. 


Are they doing away with Netbook Edition since Unity is included by default now? (I didn't see it in the list of available ISOs)


~Caboose

---

### Post by ELD on 2011-03-28
> **cariboo907 said:**
> I'm downloading a fresh daily iso as I type this. :)
 
Since the beta tracker link in the OP the files are dated today, will they be exactly the same as todays daily iso?

---

### Post by kostkon on 2011-03-28
> **Caboose885 said:**
> 
Are they doing away with Netbook Edition since Unity is included by default now? (I didn't see it in the list of available ISOs)
Affirmative.

---

### Post by kansasnoob on 2011-03-28
> **ELD said:**
> Since the beta tracker link in the OP the files are dated today, will they be exactly the same as todays daily iso?

I'd zsynced todays earliest iso and NO, it wasn't. But I checked while zsyncing again and the current daily at that time was identical.

Always make sure the md5sum is correct before iso-testing :D

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Linux](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Linux)

Save time and zsync:

[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

---

### Post by wojox on 2011-03-28
Sweet, thanks for the heads up. :D

---

### Post by joffe on 2011-03-28
Where would I file a bug relating to the hostname that the wizard proposes at install time? I have tried to file one here:

[[COLOR="Navy"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/735072[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/735072")

but never gotten any response...

---

### Post by cariboo on 2011-03-28
If the hostname is to long, your username is probably longer than need be. I personally name my computers after lakes in my area.

---

### Post by kansasnoob on 2011-03-28
Having a bit of a chuckle here :lolflag:

I got rushed and sloppy adding the new iso-testing status to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/728615](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/728615)

After realizing that I added:

"Oops, wanting to rush ahead with more testing, that last post & screenshot is based on the i386 Beta1 image."

The response was:

"I already fixed the big pile of text. Try tomorrow's test images?

(**There's no such thing as the beta-1 image yet**.)"

In order to really enjoy the LOL you need to realize I've ruffled a lot of feathers at the ubuntu-installer team and Ayatana regarding ubiquity.

I can't help it. Sometimes I can be very cantankerous. I asked earlier today at bug 652852, "**Do you and Evan have a dart board dedicated to me yet?**"

I somehow know they do :D

---

### Post by ranch hand on 2011-03-28
OK, thought I would try this crap one more time.  Got the Xubuntu and Ubuntu amd64 desktop images.

Haven't tried the Ubuntu one yet but the Xubuntu image will not boot.

So, how do I file this bug correctly?

I am really tired of the big rush to improve Ubuntu without seeing if they can get the stuff they have to work even a litttle bit.

---

### Post by joffe on 2011-03-28
> **cariboo907 said:**
> If the hostname is to long, your username is probably longer than need be. I personally name my computers after lakes in my area.

The thing is that if my user name is "johan", then the installer tries to give this specific notebook the name "johan-aspire-3820".

**Fail**. This computer will never be able to share files on a windows network unless you rename it. A basic user may or may not change the hostname to something else but I think this is a serious design flaw.

---

### Post by vishalrao on 2011-03-28
Sadly, I'm more of a weekend warrior, so by the time I'm ready to test anything, beta1 will already be out! :lolflag:

---

### Post by cariboo on 2011-03-28
We lobbied pretty hard during the last release cycle to have the ability to change your computers name during the installation process, for just that reason. It is on the same page as where  you enter your user name and password.

---

### Post by joffe on 2011-03-28
So my question is why the default hostname that shows up on this very page can be allowed to be longer than 15 characters when this obviously cripples basic functionality, rendering the file sharing option in nautilus useless. I did not choose this hostname, the installer did it based on data from dmidecode.

---

### Post by encefalocardia on 2011-03-28
Ley me get this straight. Should I be able to smootjly upgrade my alpha 3 install to final without reinstalling?

---

### Post by cariboo on 2011-03-28
@joffe As I've said several times before, you have the ability to enter a different hostname.

The installer is setup for new users, advanced users like yourself, are expected to know about these types of problems, and know how to deal with them.

I would suggest, if you feel the hostname is a problem, please submit a bug report, after all that is what we are here for.

@encefalocardia, if you keep up-to-date, you will have the final release.

---

### Post by joffe on 2011-03-28
> **cariboo907 said:**
> If you know the length of the hostname is going to be a problem, you have the ability to change it during installation. If this doesn't answer your question, I'd suggest you file a bug report against the length of the hostname.

And if you don't know this you will inevitably run into trouble if username+[dmidecode's Product name] happens to be longer. I have already filed a bug and was actually wondering under which discipline to put it so that someone can take a look at it:

[[COLOR="Navy"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/735072[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/735072")

Right now it's been two weeks to the day and it just sits there...

---

### Post by ranch hand on 2011-03-28
Well, that is nice, tried to file on both images on Launchpad and could not.  Cannot boot either.  At least 2 solid pages of "fails" before locking me up so tight I had to unplug the box to get out.

Can't file a fail in ISO Testing with out bug report.  Can't, it appears, file unless using Ubuntu to do it.

If someone knows how this can be done, please tell me.  If not there is no sense in wasting my time anymore on this toy OS.

---

### Post by ronacc on 2011-03-28
I zsynced this evening and booted it (ubuntu amd64) and the only good thing I can say is that it did boot , all 3 of the "show stopper" problems I have been having from the start are still there , it appears that neked newt is going to be as worthless to me as errant elf was .

---

### Post by beew on 2011-03-29
I thought I can just upgrade from alpha3 to beta through regular updates, why is everyone talking about downloading? Am I missing something?

---

### Post by cariboo on 2011-03-29
> **beew said:**
> I thought I can just upgrade from alpha3 to beta through regular updates, why is everyone talking about downloading? Am I missing something?

Like the title of the thread says, and kansasnoob's link in the first post, this thread is about iso testing. Most of us have a blank partition of a testing system where we try out the iso's leading up to the beta release, and file as many bugs as we can possibly find with the install process. It has nothing to do with the regular upgrade process.

If you keep your system up-to-date you will essentially have the beta when it's released this Thursday, and if you keep on updating you'll have the final release when it comes out on April 28th.

---

### Post by alphacrucis2 on 2011-03-29
> **beew said:**
> I thought I can just upgrade from alpha3 to beta through regular updates, why is everyone talking about downloading? Am I missing something?

The point is to test the iso image. ie clean/first time install. People do that, so I'm told ;)

---

### Post by kansasnoob on 2011-03-29
> **ranch hand said:**
> OK, thought I would try this crap one more time.  Got the Xubuntu and Ubuntu amd64 desktop images.

Haven't tried the Ubuntu one yet but the Xubuntu image will not boot.

So, how do I file this bug correctly?

I am really tired of the big rush to improve Ubuntu without seeing if they can get the stuff they have to work even a litttle bit.

Did you check the md5sum of the images?

If an image fails altogether about the only thing you can do is file at launchpad using "no-redirect":

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

I'd guess replacing "PACKAGENAME" in their example with casper, but that's only my best guess. They'll want to know if you checked the md5sum and the integrity of the CD/DVD/USB:

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by kansasnoob on 2011-03-29
Just completed an i386 Ubuntu upgrade test and all worked quite well :D

Compiz is funky on this hardware but it always has been, even on Lucid and Maverick, so that's to be expected.

When iso-testing for Beta1 is all done I think I'll dedicate this partition to trying various docks (awn, docky, cairo) to "add" a bottom panel/dock to see if I can obtain some of the old "goodies" I personally miss running unity-2d :)

No boredom on the horizon any time soon \\:D/

---

### Post by kansasnoob on 2011-03-29
Round 2 begins now:

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by ELD on 2011-03-29
Downloading the round 2 iso, downloaded the daily iso earlier and the ubuntu home button still doesn't show up for me, hopefully the beta test iso will work properly.

---

### Post by joffe on 2011-03-29
> **cariboo907 said:**
> @joffe As I've said several times before, you have the ability to enter a different hostname.

The installer is setup for new users, advanced users like yourself, are expected to know about these types of problems, and know how to deal with them.

I would suggest, if you feel the hostname is a problem, please submit a bug report, after all that is what we are here for.


Well, if you actually took the time to [[COLOR="Red"]read my first post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10612025&postcount=8") you'd see the link to my bug report. My original question was: under what project should I file this bug to get a developer to look at it?

My point here is that since, as you put it, "the installer is setup for new users", the hostname should be proposed as 15 characters or less. If you are an advanced user like you or me, then you could of course change it, but don't let it be the other way around. It's far too much hassle for a beginner to google the reason your file sharing is broken.

---

### Post by jerrylamos on 2011-03-29
> **kansasnoob said:**
> Round 2 begins now:

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

29 March 2011 .iso ubiquity fails on Acer Aspire one netbook at "Preparing to install Ubuntu".  Ubiquity is hung on interpreting the partitions.  

Launchpad bug #744438.

Note there is one new partition prepared by gparted for the install.

Also note, on boot, there is an error message ubi-language fails with code 10.  Already entered as a launchpad bug.

---

### Post by ranch hand on 2011-03-29
> **kansasnoob said:**
> Did you check the md5sum of the images?

If an image fails altogether about the only thing you can do is file at launchpad using "no-redirect":

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

I'd guess replacing "PACKAGENAME" in their example with casper, but that's only my best guess. They'll want to know if you checked the md5sum and the integrity of the CD/DVD/USB:

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Maybe I had a bad connection, although every thing else seemed to load fine, that report page came up but that was all.  It was dead after that.

Md5 sums were right on.

I will try the new ones and see if the reporting works today.

Thanks.

---

### Post by jerrylamos on 2011-03-29
No go on .iso testing.  The i386 desktop image is listed at 700.6 MB.  

I burned two CD's with Lucid LTS, claimed to be burned successfully.

Both failed with initramfs, squashfs error.

So much for iso-testing on CD.

Jerry

---

### Post by kansasnoob on 2011-03-29
I was just going to add a report and I see they're now rebuilding, so round 3 coming soon :D

---

### Post by cariboo on 2011-03-29
@jerrylamos, are you getting your iso from [here]("http://cdimage.ubuntu.com/daily-live/current/"). The only iso I see above 700MB is the powerpc desktop iso.

---

### Post by ronacc on 2011-03-29
I have noticed that the file size as listed on the live cd repo ( and others for that mater ) do not always agree exactly with the size as downloaded and on your disk . ( note I am not talking about bad downloads ) , it seems that the repo determines the size ( or rounds it off ) differently than your installed file system , so jerry could well have had a 700.6 mb image where the repo showed 699mb  (for the i386) .

---

### Post by VastOne on 2011-03-29
> **jerrylamos said:**
> 29 March 2011 .iso ubiquity fails on Acer Aspire one netbook at "Preparing to install Ubuntu".  Ubiquity is hung on interpreting the partitions.  

Launchpad bug #744438.

Note there is one new partition prepared by gparted for the install.

Also note, on boot, there is an error message ubi-language fails with code 10.  Already entered as a launchpad bug.

Jerry,

I noticed that Ubiquity has been updated all the way to 2.5.32 in the latest iso from daily

That is one revision bump more than what I needed to get mine working, so ubiquity is still being worked on ..

---

### Post by julianb on 2011-03-29
the ISO i downloaded today (i386) was oversize but it's fine on USB - which I highly recommend as a way of saving CDs as well.

I actually used [these instructions]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/") to make my usb key boot up the ISO rather than having to process the ISO into separate files (unetbootin)

---

### Post by VastOne on 2011-03-29
> **julianb said:**
> the ISO i downloaded today (i386) was oversize but it's fine on USB - which I highly recommend as a way of saving CDs as well.

I actually used [these instructions]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/") to make my usb key boot up the ISO rather than having to process the ISO into separate files (unetbootin)

Thanks for that.. Easy and well written, a very good guide.

Query - when you get a new iso for testing, do you just remove the current .iso on the flash drive and replace it with the current... Meaning, no need for extracting the iso, it is just dumped on the flash drive?

Thanks  :popcorn:

---

### Post by kansasnoob on 2011-03-29
> **ronacc said:**
> I have noticed that the file size as listed on the live cd repo ( and others for that mater ) do not always agree exactly with the size as downloaded and on your disk . ( note I am not talking about bad downloads ) , it seems that the repo determines the size ( or rounds it off ) differently than your installed file system , so jerry could well have had a 700.6 mb image where the repo showed 699mb  (for the i386) .

That actually is partly my fault :D

The devs were trying to really fix **** and I stuck my nose in:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

Sometimes it's good to spoil a party :lolflag:

---

### Post by kansasnoob on 2011-03-29
Just noticed they're going for a fourth round on K, X, etc. Not yet on Ubuntu:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I've been at this iso-testing for nearly 3 years and the most I've ever seen is 5, will we set a new record :confused:

I personally do love this, not sure what a qualified shrink would make of that, but to me this is the best time to catch and kill bugs!

That's not to say that all bugs will be fixed if you report properly during iso-testing, but it definitely improves the odds :)

---

### Post by ELD on 2011-03-29
Well i tried round 2 iso earlier and it booted, got to the try or install box, clicked try and it hanged :\
 
Does anyone know why i wouldn't be getting the home button show up on daily iso's either? Would it be due to compiz/unity and my graphics hardware maybe?

---

### Post by ranch hand on 2011-03-29
> **VastOne said:**
> Thanks for that.. Easy and well written, a very good guide.

Query - when you get a new iso for testing, do you just remove the current .iso on the flash drive and replace it with the current... Meaning, no need for extracting the iso, it is just dumped on the flash drive?

Thanks  :popcorn:
If you are on a single partition install you can boot the ISO from grub pretty easily.

If you are on 2 partitions you need to move the ISO to a file on the / partition and use an etry like this;
```

echo "Adding Ubuntu 10.04B1 ISO on sda9" >&2 
cat << EOF
menuentry "Ubuntu 10.04B1 ISO on /dev/sda0" {
loopback loop (hd0,9)/etc/aa/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/etc/aa/natty-desktop-amd64.iso noprompt 
initrd (loop)/casper/initrd.lz
}
EOF

```
The path on most systems of a one partition install would be /home/<user>/downloads/whatever.iso

Bugger wouldn't boot from there or a CD.

---

### Post by VastOne on 2011-03-29
> **ranch hand said:**
> If you are on a single partition install you can boot the ISO from grub pretty easily.

If you are on 2 partitions you need to move the ISO to a file on the / partition and use an etry like this;
```

echo "Adding Ubuntu 10.04B1 ISO on sda9" >&2 
cat << EOF
menuentry "Ubuntu 10.04B1 ISO on /dev/sda0" {
loopback loop (hd0,9)/etc/aa/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/etc/aa/natty-desktop-amd64.iso noprompt 
initrd (loop)/casper/initrd.lz
}
EOF

```
The path on most systems of a one partition install would be /home/<user>/downloads/whatever.iso

Bugger wouldn't boot from there or a CD.

Hey Ranch.. Long time no mangler grumbles.... :P

I was able to get this to work following the instructions.. 

One thing that did not happen was the wget failed to pull the grub.cfg  - which, obviously, tells this process where to go and what to get

I manually pulled the grub.cfg and put it in it's correct spot (/flash drive/grub)and then copied the ubuntu.iso (renamed from natty-desktop-amd64.iso)to the flash drive and installed it

Cheers...

---

### Post by VastOne on 2011-03-29
Query on ISO testing...

Does it matter what medium you test from as long as it is the current iso from the site?

Meaning, testing the ISO does not matter if it is tested from a CD, DVD or Flash Drive?

---

### Post by ronacc on 2011-03-29
You are free to use what ever medium works best for you , it makes no difference .

---

### Post by jerrylamos on 2011-03-30
Took several tries at install and finally have 29 March .iso running on an older desktop and Thinkpad T40 laptop - Unity 2D from Synaptic on both now.

On my newer Compaq the .iso installed and ran no hitch, Unity 3D.

No go at all on Acer Aspire one netbook.  Ubiquity fails on the Acer by cycling endlessly when it should be determining the partition structure.  Yes there's a launchpad bug written.

The Acer does run Unity 3D but only by taking the USB hard drive to the Compaq to do the install, moving it to the Acer then running Grub again.

So 3 out of 4 success rate so far...

Jerry

p.s. I'm not a Unity fan, it's just that's what we're supposed to be testing.

---

### Post by ranch hand on 2011-03-30
I am just happy that Xubuntu actually installed and runs.  Ubuntu would not boot the CD.

On my upgraded install (9.04>9.10>10.04>10.10>11.04) Unity will no longer run at all.  Unity 2D will not run on it either.

---

### Post by IWantFroyo on 2011-03-30
Yay! The beta is out! I am technically a developer, but I haven't really gotten caught up on what's happening in the beta, so I'm going to have to catch up (awkward face here).

---

### Post by cariboo on 2011-03-30
> **IWantFroyo said:**
> Yay! The beta is out! I am technically a developer, but I haven't really gotten caught up on what's happening in the beta, so I'm going to have to catch up (awkward face here).

The beta doesn't come out until the 31st. I'd suggest you subscribe to the [ubuntu-devel-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce") mailing list to be one of the first to see when it is officially released.

If you see somewhere other than Canonical/Ubuntu saying they've got the beta, it's just the same daily iso the rest of us are testing right now.

---

### Post by kansasnoob on 2011-03-30
Wow, round 4 begins now!

I'm zsyncing the new image:

[http://iso.qa.ubuntu.com/qatracker/info/5335](http://iso.qa.ubuntu.com/qatracker/info/5335)

---

### Post by ranch hand on 2011-03-30
> **kansasnoob said:**
> Wow, round 4 begins now!

I'm zsyncing the new image:

[http://iso.qa.ubuntu.com/qatracker/info/5335](http://iso.qa.ubuntu.com/qatracker/info/5335)
Yup, me too.   I am a glutton for punishment.

May be surprised, I hope so anyway, it may boot.  Be the first image in a long time that would boot (sometime in 10.10 testing).

---

### Post by ranch hand on 2011-03-31
Well, that was another wast of time.  See no difference from the last one.  This one did flicker the error page once before going to frozen black.

having to unplug the box to get out is not a good thing.  I think I will give up on trying this one.  Ubuntu is just to hard on my hardware to believe.

---

### Post by jerrylamos on 2011-03-31
> **cariboo907 said:**
> The beta doesn't come out until the 31st....

Any  number of times over the past few years, the "daily image" freezes a day or two before a "release" and has the same MD5SUMS.  Not always of course.

Jerry

---

### Post by shuttleworthwannabe on 2011-03-31
I see WUBI is not working yet; does anyone have Ubuntu installed through WUBI?

---

