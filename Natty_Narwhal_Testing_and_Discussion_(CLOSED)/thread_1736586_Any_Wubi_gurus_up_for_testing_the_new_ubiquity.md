---
title: "Any Wubi gurus up for testing the new ubiquity?"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-04-22
I'm trying madly to do as much testing as possible, but I have no router so I'm limited to using one box at a time.

For those who don't know, it's become quite frequent for "branded" Windows PC's to have 4 primary partitions by default. In such a case the new ubiquity is supposed to default to presenting the option to perform a Wubi install.

We're now in Natty final iso-testing:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I have a number of tests to repeat and I'd appreciate help if it's possible for anyone to do so, but **[COLOR="Red"]be aware of the dangers involved[/COLOR]**!

Data loss is always a possibility when installing, repartitioning, etc!

---

### Post by kansasnoob on 2011-04-23
We're now up to round three of iso-testing:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I'm going to try real hard to squeeze at least one Wubi test into my schedule but it's going to be tough :(

---

### Post by kansasnoob on 2011-04-24
Basically just a bump ;)

I'm rather expecting a fix for this in the next build:

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/768469](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/768469)

I'm hoping for a fix for this, but not holding my breath:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

Anyway I'm going to try a "Wubi by default if four primary partitions exist" install later today, but **I really, really would appreciate someone that's used to Wubi to get involved in this** :)

Wubi has never been a good choice in my rural area because power outages are common and the Wubi FS seems to not withstand hard shutdowns well, from their webpage:

> Any gotcha?

Hibernation is not supported under Wubi, moreover **Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem**, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


If a bug is found in that install scenario and reported via the iso-tracker the odds of it being fixed or at least being mentioned in the release notes goes up dramatically :D

This is what's been reported so far with the last build:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Specific to Ubuntu/Wubi:

[http://iso.qa.ubuntu.com/qatracker/result/5586/11](http://iso.qa.ubuntu.com/qatracker/result/5586/11)

But the test I'm talking about is not yet included in the test specs:

[http://testcases.qa.ubuntu.com/Install/DesktopWubi](http://testcases.qa.ubuntu.com/Install/DesktopWubi)

I hope some brave soul(s) step up to the challenge :)

---

### Post by kansasnoob on 2011-04-24
Holy crap! How can anyone use this Windows garbage?

I have my old Win XP running now with everything updated, including the AV/Firewall that my IP provides, but it's sooooooooooooooo butt ugly compared to Ubuntu!

The fonts are almost impossible for me to see! And everything seems prehistoric!

End of rant, but I just don't see how anyone can use this crap :(

I think this will be my last Wubi test. I just can't stand Windows any longer.

---

### Post by bcbc on 2011-04-24
Hey Kansasnoob,

I have been testing Wubi - but have difficulty with this particular test case. I'll see if I can try it later. 

But I've been running the normal Wubi 11.04 install and the wubi upgrade from 10.10 - and both are working flawlessly - so I think things are positive for Wubi on 11.04  (Colin Watson has fixed all the grub booting issues that plagued 10.04 and upgrades to 10.10).

Thanks for checking this new feature out. Your tireless efforts to get Ubiquity into a rational state are very much appreciated

---

### Post by kansasnoob on 2011-04-24
This is proving to be much more difficult than I'd expected.

They really do have the detection of existing partitions and operating systems fairly fine tuned:

[ATTACH]189940[/ATTACH]

Wild times :D

---

### Post by bcbc on 2011-04-24
As long as you think like a developer you'll be fine ;)

I heard someone complaining about the "upgrade" option being a source of confusion - since it's different to a normal upgrade; instead it's the install over everything keeping /home

---

### Post by kansasnoob on 2011-04-24
> **bcbc said:**
> As long as you think like a developer you'll be fine ;)

I heard someone complaining about the "upgrade" option being a source of confusion - since it's different to a normal upgrade; instead it's the install over everything keeping /home

I've tried the new upgrade via Live CD and it saves a bit more than just /home. I was using a test install with my typical packages installed and Opera from a dot-deb. All of my packages survived but Opera.

Anyway the last time I tried this Wubi via live installer thing it was less picky about what it saw on other partitions, but I got it figured out and I'm completing and installation right now :)

I think I even have a couple of pictures. I say, "I think", because I can't actually see what I'm doing while I take pictures. Like I can't see what's actually in the little LCD screen on the camera, and instead of being able to see the flash setting I just know what the default is, so I count button clicks to get where I need to be.

But the only problem I could see was that the screen telling me what it was going to do was just a bunch of text, although one line of the text did say to reboot.

ATM I'm in Win XP waiting for the Wubi install to complete. When I can work from Ubuntu I'll hopefully be able to add more, and contemplate bug filing :)

---

### Post by bcbc on 2011-04-24
That's good to know how that upgrade option works. I still prefer the inside upgrade, which has always worked flawlessly for me, but good to know there are options.

Since you're talking about difficulty reading the screens: ironically, Wubi has an option for visually impaired users. It offers meaningless descriptions - I can't remember exactly, but something like, Visual option 1, 2, 3 (without any clue as to what these are). And even a Braille reader option. But once you reboot it always looks the same.

I think I filed a bug on this back in October, but maybe it's time to revisit the windows installer side again.

Also, it's kind've tricky to supply boot workarounds (once you reboot from windows to do the actual install). The options aren't very helpful for current issues (like nvidia cards). Here's a link to a thread that covers boot options, this post is specific to the Wubi install: [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by kansasnoob on 2011-04-25
Well, not knowing what to expect I didn't get my screenshot saved to my flash drive before clicking on install inside Windows. I expected another chance to copy it from the live desktop, but after confirming that I did want to install in Windows I get this screen:

[ATTACH]189956[/ATTACH]

Not the greatest pic but good enough to show what it does, then after ejecting the CD and hitting enter you get this:

[ATTACH]189957[/ATTACH]

I assume that's typical :confused:

One thing that puzzles me. I get the expected Windows boot screen asking whether to boot Windows or Ubuntu, but after choosing Ubuntu I get the grub screen asking whether I want to boot Ubuntu or Windows.

That seems odd to me.

---

### Post by kansasnoob on 2011-04-25
As I think about it, I wonder why I didn't just see an option to use the Live CD for the source of Wubi rather than it downloading Ubuntu?

I think I'll have to repeat this, only this time I'll leave the Live CD in and select "boot from hard drive" from the boot menu.

---

### Post by kansasnoob on 2011-04-25
OK, I'm pretty sure we have problems here :(

I did get a better picture of the screen after selecting the Wubi option, and I saved the ubiquity screenshot:

[ATTACH]189969[/ATTACH]

[ATTACH]189970[/ATTACH]

But after completing the installation the first reboot into Windows shows this:

[ATTACH]189971[/ATTACH]

Why would it do that?

Also, as previously mentioned, the grub boot screen appears after selecting Ubuntu from the Windows boot screen, and it lists Windows. But naturally if you try to boot Windows it fails.

I need to do some more reboots into Windows to see if that window keeps popping up asking to uninstall. Then I need to try and file some bug reports.

We're in the midst of a thunderstorm so I hope I can get this done before a power outage screws things.

---

### Post by kansasnoob on 2011-04-25
> **kansasnoob said:**
> As I think about it, I wonder why I didn't just see an option to use the Live CD for the source of Wubi rather than it downloading Ubuntu?

I think I'll have to repeat this, **[COLOR="Red"]only this time I'll leave the Live CD in and select "boot from hard drive" from the boot menu.[/COLOR]**

I decided not to do that!

---

### Post by kansasnoob on 2011-04-25
I added to an older bug report about the grub issue:

[https://bugs.launchpad.net/wubi/+bug/466745](https://bugs.launchpad.net/wubi/+bug/466745)

---

### Post by kansasnoob on 2011-04-25
I see we're getting a rebuild so I can't report that in the iso-tracker :(

---

### Post by kansasnoob on 2011-04-25
I reported the prompt to uninstall issue here:

[https://bugs.launchpad.net/wubi/+bug/770256](https://bugs.launchpad.net/wubi/+bug/770256)

---

### Post by rbrick49 on 2011-04-25
no kansasnoob because it has never worked for me before

---

### Post by kansasnoob on 2011-04-25
> **rbrick49 said:**
> no kansasnoob because it has never worked for me before

That's OK :)

It's just that the quantity of tests is now getting a bit much:

1) Standard upgrade via net, which requires a spare Maverick fully updated with my favorite mods
2) Upgrade/replace OS via live CD, also requiring a modified existing OS
3) Entire disc install
4) Side-by-side letting the partitioner do the auto-resizing
5) Side-by-side using existing free space
6) Manual partitioning
7) Wubi if four primary partitions exist

Even if all goes well that amounts to about 6 to 8 actual man hours, and if all doesn't go well it's "rinse-n-repeat" ad nauseam :(

We've just completed three rounds of testing for Natty final and we're in a rebuild right now, so I know there's at least one more round of testing up.

I need a router so I can use more than one puter at a time :D

---

### Post by bcbc on 2011-04-25
The wubi installer is also the wubi uninstaller. Now that you've done it the design flaw is clear: adding the installer to windows's startup programs will install the first time it runs, and then on each subsequent boot into Windows it will prompt you to uninstall and reinstall.

And the whole idea about downloading the CD image again is a bit painful - for some people this can cost a lot of money.

Regarding that second Grub menu, that's always been the way it works. The first menu is the Windows boot manager, the second is the grub menu. Grub detects multiple OS's (30_os-prober) - and this by default disables direct boot into Ubuntu - and so yes you can select Windows from the grub menu (should work) and then you'll get the Windows Boot Manager again. When you say it doesn't work to boot windows, maybe it doesn't work the way you expect, but it should work (take you to the Windows boot manager again) or else it's a bug.

---

### Post by kansasnoob on 2011-04-25
> The wubi installer is also the wubi uninstaller. Now that you've done it the design flaw is clear: adding the installer to windows's startup programs will install the first time it runs, and then on each subsequent boot into Windows it will prompt you to uninstall and reinstall.

Where should I look for that in the Windows files?

BTW I have rebooted 4 times and each time the "uninstall" prompt shows up, of course I'll have to repeat this when the rebuild is complete and verify that it's still broke.

> And the whole idea about downloading the CD image again is a bit painful - for some people this can cost a lot of money.

No doubt. I have no limit on downloads and a 700MB iso normally takes me about 20 minutes to DL, but the Wubi DL takes 35 to 40 minutes.

So, I wonder how we should approach this?

> Regarding that second Grub menu, that's always been the way it works. The first menu is the Windows boot manager, the second is the grub menu. Grub detects multiple OS's (30_os-prober) - and this by default disables direct boot into Ubuntu - and so yes you can select Windows from the grub menu (should work) and then you'll get the Windows Boot Manager again. When you say it doesn't work to boot windows, maybe it doesn't work the way you expect, but it should work (take you to the Windows boot manager again) or else it's a bug. 

It spits an error instead of returning to the Windows boot menu. The next go around I'll pay more attention to what the error message actually says.

Many thanks for working with me on this. I'd bet it's doubtful we'll see these issues fixed so we probably need to work on getting these issues mentioned in the release notes and developing work-arounds :D

Many, many thanks again.

---

### Post by bcbc on 2011-04-25
If it's added the entry to the startup folder, then that's a problem. It will never be deleted. There are a number of startup folders depending on the users, but likely they chose a generic one:
```
C:\Documents and Settings\All Users\Start Menu\Programs\Startup
```

The easiest way to find it is to: click START, run, msconfig

Then select the Startup tab and look for the Startup Item named wubi. It will show the location of the program as well as where it was added. It should be the RunOnce part of the registry.

---

### Post by bcbc on 2011-04-25
> **kansasnoob said:**
> It spits an error instead of returning to the Windows boot menu. The next go around I'll pay more attention to what the error message actually says.

Many thanks for working with me on this. I'd bet it's doubtful we'll see these issues fixed so we probably need to work on getting these issues mentioned in the release notes and developing work-arounds :D

Many, many thanks again.

It probably says "error: invalid command: drivemap". I noticed that a while ago, but it seems to work anyway so hard to tell whether it's a 'real error' (and the computer reboots) or whether it is working.

And I'm more than happy to help. You are doing the heavy lifting on this ;) that's for sure. But I do spend time helping after the fact, so this upfront work is good.
But you're right they're unlikely to do any major changes so close to release - so this will just be a "natty thing".

---

### Post by kansasnoob on 2011-04-25
> **bcbc said:**
> It probably says "error: invalid command: drivemap". I noticed that a while ago, but it seems to work anyway so hard to tell whether it's a 'real error' (and the computer reboots) or whether it is working.

And I'm more than happy to help. You are doing the heavy lifting on this ;) that's for sure. But I do spend time helping after the fact, so this upfront work is good.
But you're right they're unlikely to do any major changes so close to release - so this will just be a "natty thing".

That is exactly correct! In fact while I was writing that error down the boot back to Windows boot menu completed :)

I'll add a comment at that bug report to disregard.

Wow, two heads do work better than one. I'd be lost without you :)

---

### Post by kansasnoob on 2011-04-25
> **bcbc said:**
> If it's added the entry to the startup folder, then that's a problem. It will never be deleted. There are a number of startup folders depending on the users, but likely they chose a generic one:
```
C:\Documents and Settings\All Users\Start Menu\Programs\Startup
```

The easiest way to find it is to: click START, run, msconfig

Then select the Startup tab and look for the Startup Item named wubi. It will show the location of the program as well as where it was added. It should be the RunOnce part of the registry.

I used the Google and did just exactly that, but Win is crying loudly:

[ATTACH]189986[/ATTACH]

[ATTACH]189987[/ATTACH]

[ATTACH]189988[/ATTACH]

[ATTACH]189989[/ATTACH]

I'm quite sure that I've never created an admin account on this Win XP home version.

We need an eloquent way of fixing that :D

---

### Post by kansasnoob on 2011-04-25
Hey, about that heavy lift. It's always a lighter lift if you have someone on the other end helping :)

Without you on the other end I'd have a hernia by now :lolflag:

---

### Post by bcbc on 2011-04-25
> **kansasnoob said:**
> That is exactly correct! In fact while I was writing that error down the boot back to Windows boot menu completed :)

I'll add a comment at that bug report to disregard.

Wow, two heads do work better than one. I'd be lost without you :)
:) I'm getting good at reading grub error messages as they flash by :P

Wubi is a lot of fun. I wonder how many came to Ubuntu through it - I'd guess many.

> **kansasnoob said:**
> I used the Google and did just exactly that, but Win is crying loudly:

[ATTACH]189986[/ATTACH]

[ATTACH]189987[/ATTACH]

[ATTACH]189988[/ATTACH]

[ATTACH]189989[/ATTACH]

I'm quite sure that I've never created an admin account on this Win XP home version.

We need an eloquent way of fixing that :D

OK that is a problem. Adding in Startup instead of the registry's RunOnce. Bad idea.

I think this is trying to be too clever - why not just post a message "To install inside Windows, reboot into Windows and insert your Ubuntu CD". :confused:

And again, you have to wonder if anyone tested this... Kansasnoob, I think you must be the first! Edit: actually there was someone else who tested this, now that I think about it... (just not the developer :P)

PS that is normal behaviour for Windows XP to prompt you the next time you boot after making startup changes.

---

### Post by kansasnoob on 2011-04-25
I last tested this about Alpha 3 I think.

Either it worked different then or I didn't bother to reboot again and again.

I think it must have worked different, but I'm old, may have had a brain fart :(

I do agree that it be best to make recommendations, like:

1) You may want to consider a Wubi install

2) You may want to learn more about manual partitioning

And a link to official documentation for each.

Me thinks we're becoming the king of bloat :D

---

### Post by kansasnoob on 2011-04-25
> Wubi is a lot of fun. I wonder how many came to Ubuntu through it - I'd guess many.

I do know I've recommended your guide to move to a hard install a couple dozen times. So, yes, people do learn from Wubi and end up moving to a full Ubuntu experience.

I moved more quickly :D

I really, really fell in love with Gutsy from day one, and I've only been stressed out once. That's when they introduced pulse-audio in Hardy and that's also when I learned how easy it is to multi-boot :D

I may change DE's but I'm a **buntu devotee!

---

### Post by bcbc on 2011-04-25
> **kansasnoob said:**
> Me thinks we're becoming the king of bloat :D

I don't think it's too serious :) it's not like it's formatting the drive. It will certainly irritate some users :(

---

### Post by kansasnoob on 2011-04-25
Back to business, if this happens to someone how do they recover other than removing the installation that just took one hour or more, and then install again properly?

I'm sure I'm not the only one with no knowledge or memory of an admin account. I mean I'm going to wipe this Wubi install anyway to try the new iso when it's released, but how would I clean that up if I didn't want to reinstall?

---

### Post by bcbc on 2011-04-25
OK... I didn't quite get that bit about not being admin. Usually Windows users run as administrator. For a while I did not, but it's very inconvenient.

Bottom line: if a user is not able to login as an administrator then there is no way to remove wubi.exe from the "all users" startup list. (You can do it from Ubuntu).

If you can log in as an administrator you'd just remove it using msconfig, or you'd go into internet explorer and delete it manually.

---

### Post by kansasnoob on 2011-04-25
> **bcbc said:**
> OK... I didn't quite get that bit about not being admin. Usually Windows users run as administrator. For a while I did not, but it's very inconvenient.

Bottom line: if a user is not able to login as an administrator then there is no way to remove wubi.exe from the "all users" startup list. **[COLOR="Red"](You can do it from Ubuntu).[/COLOR]**

If you can log in as an administrator you'd just remove it using msconfig, or you'd go into internet explorer and delete it manually.

Then shouldn't we focus on that approach?

Also what is the difference going to be between XP, Vista and Win7?

---

### Post by bcbc on 2011-04-25
> **kansasnoob said:**
> Then shouldn't we focus on that approach?

Also what is the difference going to be between XP, Vista and Win7?

I think it has to be done from Windows. 
1) noob gets an Ubuntu disk
2) boots from it, selects "inside windows install"
3) forever after when booting Windows gets prompted to install/uninstall

It's unlikely that they'll want to go fix it from Ubuntu because it's not intuitive:
1. Boot from live CD
2. Select "Try it"
3. Go to Places and find your C: drive, except it's not called C: and maybe you don't have a Places menu because of Unity, or you installed Xubuntu or Kubuntu etc.
4. go to /media/143013874134019341/Documents\ and\ Settings/All\ Users/blah blah blah 

The noob is thinking: "You lost me at Step 1."

So for most (with admin rights), they can boot Windows, right click on START, choose Explore/Open All Users, then navigate to Programs, Startup, and then manually delete: wubi.exe
I assume this works the same in Vista/7 (have to check later).

They can also do it by running the msconfig utility.

Anyone who doesn't have admin rights might have no choice other than to do it from Ubuntu, but they really shouldn't be installing Ubuntu without admin rights.

---

### Post by seeker5528 on 2011-04-25
> **kansasnoob said:**
> Also what is the difference going to be between XP, Vista and Win7?

In XP, the administrator account is available as a log in option until you create an account with administrator rights, as soon as you create a user with administrator rights the administrator account is hidden from the normal log in, it's still an option for all versions if you boot into safe mode, in XP Pro if you have it set up to require hitting 'Ctrl'+'Alt'+'Del' and then type the user name and password, you can type in 'Administrator' to log in as administrator. No UAC so the stuff that needs administrator rights to work just works if you are running from a user account with administrator rights.

In Vista/Win 7, you can't log in as administrator even if you boot into safe mode. UAC will ask permission before doing the majority of things that require administrator rights.

Outside of the UAC stuff the biggest way this would affect most people is on XP sometimes people would skip the step about creating a user account and just log in as administrator, then later they or someone else might create a user account with administrator rights causing the person using the administrator account to lose access to their files since the administrator account then becomes hidden from the normal login screen. Since a user account is *always* created during Vista/Win 7 installation that is not an issue there.

You should be able to google and find instruction on how to unhide the administrator account from the normal XP login screen, if you really need to.

Going toward state of mind.....

Vista/Win 7 using UAC is, on the surface, a bit like Ubuntu using sudo. but... While this was one of the things that was talked about during the development of Vista as an example of how security had been improved, when people raise a fuss about the way UAC does some things in relation to what it allows, what it doesn't allow, and when, then someone inside of Microsoft comes up with a 'UAC is not a security feature so those issues are not bugs' type of response, whether this is how it is generally viewed inside of MS or schizophrenia resulting from different people/groups having a different view of the role of UAC, I don't know. 

Is that the 'how are they different' kind of information you were looking for? :P

Later, Seeker

---

### Post by kansasnoob on 2011-04-26
Well, this is being a real pita for me. I napped for a few hours and I'm still trying to get that cleaned up so I can repeat the test with the newest iso-testing build.

However I'm sure ubiquity is the problem and the version has not changed so I'm sure it'll be the same. I'll fiddle a bit more :(

---

### Post by bcbc on 2011-04-26
Sorry to see you're still having issues deleting the wubi.exe. From Ubuntu, when you mount the partition (assuming it's mounted as /mnt) can you do this:
```
sudo rm /mnt/Documents\ and\ Settings/All\ Users/Start\ Menu/Programs/Startup/wubi.exe
```

I just had a look at the [code]("http://bazaar.launchpad.net/~ubuntu-installer/ubiquity/trunk/revision/4550#ubiquity/"), so I think the above command will do it for XP:
```
def windows_startup_folder(mount_path):
 390    locations = [
 391        # Windows 7
 392        'ProgramData/Microsoft/Windows/Start Menu/Programs/Startup',
 393        # Windows XP
 394        'Documents and Settings/All Users/Start Menu/Programs/Startup',
 395        # Windows NT
 396        'Winnt/Profiles/All Users/Start Menu/Programs/Startup',

```

---

### Post by kansasnoob on 2011-04-26
I'll have to get back to that later. The optical drive in that box took a dump so I just hooked up my other computer.

I have a spare drive so I'll get that changed while I'm doing some other testing, then I'll get back to the Windows box.

---

### Post by kansasnoob on 2011-04-26
Dumb question; since I've already removed the Wubi install how do I mount Windows properly from the Live CD?

I'm just going to begin a couple of tests on my main box, sip some coffee, and change that drive :)

---

### Post by bcbc on 2011-04-26
For XP, Windows' C: drive is usually the partition with the boot flag set. So CTRL+ALT+t, "sudo fdisk -l" and then mount the one with the boot flag set.

e.g. assuming /dev/sda1 has the boot flag
```
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo rm /mnt/Documents\ and\ Settings/All\ Users/Start\ Menu/Programs/Startup/wubi.exe

```

You can also find the partition by partition label or size from the Places menu or Nautilus on Unity, then clicking on it will be mounted as /media/label or /media/uuid

---

### Post by kansasnoob on 2011-04-26
> **bcbc said:**
> For XP, Windows' C: drive is usually the partition with the boot flag set. So CTRL+ALT+t, "sudo fdisk -l" and then mount the one with the boot flag set.

e.g. assuming /dev/sda1 has the boot flag
```
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo rm /mnt/Documents\ and\ Settings/All\ Users/Start\ Menu/Programs/Startup/wubi.exe

```

You can also find the partition by partition label or size from the Places menu or Nautilus on Unity, then clicking on it will be mounted as /media/label or /media/uuid

Thanks bcbc. I have that drive almost changed, have to dig out the pdf guide to see which SATA ports are which because I'm replacing an IDE drive with a new SATA drive.

Anyway, I'll push another test through my main box and then get back to that. We did get a positive response here:

[https://bugs.launchpad.net/wubi/+bug/770256](https://bugs.launchpad.net/wubi/+bug/770256)

> Erick, thanks for reporting this. We need to understand what went wrong, and at a minimum document it in the release notes, to avoid problems for others.

Would you care to add a comment?

Many, many thanks again :)

---

### Post by bcbc on 2011-04-26
I just added a comment (more like a missive). Hopefully I got all the salient bits ;)  

Thanks for figuring this stuff out! Noobs around the world will (or should) thank you.

---

### Post by kansasnoob on 2011-04-26
I wish I'd found it sooner, but I made it my last test scenario :(

I do see that Evan Dandrea is now assigned, and it's both confirmed and critical so maybe they'll push out a fix tomorrow.

I've completed all of my other tests with the latest iso-testing image and I'm a bit tired so I'm going to rest, then in the AM I'll hook up the Windows box and have at it again :)

I'll tell you, I never did know much about Windows and never really cared to learn. I've felt just the opposite about Ubuntu, I love getting into the nuts & bolts of the OS and testing.

Oops, I guess it is already tomorrow.

---

### Post by bcbc on 2011-04-26
> **kansasnoob said:**
> I wish I'd found it sooner, but I made it my last test scenario :(

I do see that Evan Dandrea is now assigned, and it's both confirmed and critical so maybe they'll push out a fix tomorrow.

I've completed all of my other tests with the latest iso-testing image and I'm a bit tired so I'm going to rest, then in the AM I'll hook up the Windows box and have at it again :)

I'll tell you, I never did know much about Windows and never really cared to learn. I've felt just the opposite about Ubuntu, I love getting into the nuts & bolts of the OS and testing.

Oops, I guess it is already tomorrow.

Yeah I faded quickly ;)

Well done on getting this bug out there and fixed. I've been pretty busy at work - so I've been stick to the normal wubi scenarios for testing - this was good catch.

Downside is we all have to test the latest wubi.exe again ;) (just kidding)

---

### Post by kansasnoob on 2011-04-26
I've been wondering, since the package fixed is Wubi, when would be a good time to test again.

This is funny, just as I was typing this I got a mail notification of another new build :)

So it's rinse-n-repeat time again.

---

### Post by bcbc on 2011-04-26
The approach they've taken is for Wubi.exe to detect where it is being called from, and if it's the Common Startup, it delete's itself.

That should work - good luck with the test!

---

### Post by kansasnoob on 2011-04-26
> **bcbc said:**
> For XP, Windows' C: drive is usually the partition with the boot flag set. So CTRL+ALT+t, "sudo fdisk -l" and then mount the one with the boot flag set.

e.g. assuming /dev/sda1 has the boot flag
```
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo rm /mnt/Documents\ and\ Settings/All\ Users/Start\ Menu/Programs/Startup/wubi.exe

```

You can also find the partition by partition label or size from the Places menu or Nautilus on Unity, then clicking on it will be mounted as /media/label or /media/uuid

Far out this worked :)

Now for the fun.

---

### Post by kansasnoob on 2011-04-26
Now the Wubi install stops with a no such file or directory error:

[ATTACH]190117[/ATTACH]

I tried to find the recommended file but Windows files and folders are totally foreign to me :(

---

### Post by bcbc on 2011-04-26
> **kansasnoob said:**
> Now the Wubi install stops with a no such file or directory error:

[ATTACH]190117[/ATTACH]

I tried to find the recommended file but Windows files and folders are totally foreign to me :(

Open up your windows explorer and enter %temp% in the address bar.
Then look for the file wubi-11.04-rev209.log and open with Notepad

---

### Post by kansasnoob on 2011-04-26
Here it is:

> 04-26 06:11 INFO   root: === wubi 11.04 rev209 ===
04-26 06:11 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev209.log
04-26 06:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe"']
04-26 06:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data
04-26 06:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
04-26 06:11 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 06:11 DEBUG  CommonBackend: Fetching basic info...
04-26 06:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe
04-26 06:11 DEBUG  CommonBackend: platform=win32
04-26 06:11 DEBUG  CommonBackend: osname=nt
04-26 06:11 DEBUG  CommonBackend: language=en_US
04-26 06:11 DEBUG  CommonBackend: encoding=cp1252
04-26 06:11 DEBUG  WindowsBackend: arch=i386
04-26 06:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
04-26 06:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 06:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 06:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 06:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 06:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 06:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 06:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 06:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 06:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 06:11 DEBUG  WindowsBackend: Fetching host info...
04-26 06:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 06:11 DEBUG  WindowsBackend: windows version=xp
04-26 06:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 06:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 06:11 DEBUG  WindowsBackend: windows_build=2600
04-26 06:11 DEBUG  WindowsBackend: gmt=-6
04-26 06:11 DEBUG  WindowsBackend: country=US
04-26 06:11 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 06:11 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 06:11 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 06:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 06:11 DEBUG  WindowsBackend: windows_language_code=1033
04-26 06:11 DEBUG  WindowsBackend: windows_language=English
04-26 06:11 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 06:11 DEBUG  WindowsBackend: bootloader=xp
04-26 06:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33357.5898438 mb free ntfs)
04-26 06:11 DEBUG  WindowsBackend: drive=Drive(C: hd 33357.5898438 mb free ntfs)
04-26 06:11 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 06:11 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 06:11 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 06:11 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 06:11 DEBUG  WindowsBackend: uninstaller_path=None
04-26 06:11 DEBUG  WindowsBackend: previous_target_dir=None
04-26 06:11 DEBUG  WindowsBackend: previous_distro_name=None
04-26 06:11 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 06:11 DEBUG  WindowsBackend: keyboard_layout=us
04-26 06:11 DEBUG  WindowsBackend: keyboard_variant=
04-26 06:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 06:11 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 06:11 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 06:11 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 06:11 DEBUG  CommonBackend: Searching for local CDs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 06:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 06:11 INFO   root: Running the installer...
04-26 06:11 DEBUG  WindowsFrontend: __init__...
04-26 06:11 DEBUG  WindowsFrontend: on_init...
04-26 06:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 06:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 06:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=lance
04-26 06:16 INFO   root: Received settings
04-26 06:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 06:16 DEBUG  TaskList: # Running tasklist...
04-26 06:16 DEBUG  TaskList: ## Running select_target_dir...
04-26 06:16 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 06:16 DEBUG  TaskList: ## Finished select_target_dir
04-26 06:16 DEBUG  TaskList: ## Running create_dir_structure...
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 06:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 06:16 DEBUG  TaskList: ## Finished create_dir_structure
04-26 06:16 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 06:16 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 06:16 DEBUG  TaskList: ## Running create_uninstaller...
04-26 06:16 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 06:16 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
04-26 06:16 DEBUG  TaskList: # Cancelling tasklist
04-26 06:16 ERROR  root: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
04-26 06:16 DEBUG  TaskList: # Finished tasklist


---

### Post by bcbc on 2011-04-26
> 4-26 06:16 DEBUG WindowsBackend: Copying uninstaller C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 06:16 ERROR TaskList: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'

Did it delete itself prematurely?

Lol - I always laugh when the dev doesn't do at least 1 unit test

PS I can test this bit easily - I am going to download and run it to confirm

---

### Post by kansasnoob on 2011-04-26
> **bcbc said:**
> Did it delete itself prematurely?

I don't know, I filed a new bug report:

[https://bugs.launchpad.net/wubi/+bug/771517](https://bugs.launchpad.net/wubi/+bug/771517)

The installer only ran for a few seconds after entering the info and clicking on Install.

---

### Post by bcbc on 2011-04-26
> **kansasnoob said:**
> I don't know, I filed a new bug report:

[https://bugs.launchpad.net/wubi/+bug/771517](https://bugs.launchpad.net/wubi/+bug/771517)

The installer only ran for a few seconds after entering the info and clicking on Install.

Yeah it deletes itself before the user even selects the target drive, so it can't copy itself to it. :( 

Bad bug

---

### Post by kansasnoob on 2011-04-26
Please confirm here:

[https://bugs.launchpad.net/wubi/+bug/771517](https://bugs.launchpad.net/wubi/+bug/771517)

Minor rant ahead :)

You know I've spent a lot of time testing various features of ubiquity, raised all kinds of heck both before and after Maverick was released :mad:

Now, besides this debacle, today Evan made a comment here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

> This occurs when the installer chooses a large amount of free space to install into instead of resizing a partition. Because the former does not need any further interaction from the user, and because it visually does not follow the two partitions presented next to one another that the resize page does, it is not given an additional page. **The button text is changed to "Install Now" to reflect this.**

This is intended behavior, but the inconsistency in the way the side-by-side option is presented dependent on what is happening underneath the covers is worth a look in O.


I certainly called BS on that:

> "The button text is changed to "Install Now" to reflect this."

**No, it's not. That would at least be some indication that the the install was really going to begin right then. I just repeated a test to be certain and the attached screenshot shows exactly what does happen.**

The shot on the left displays that I've chosen alongside with 10GB free, and the shot on the right displays exactly what happens when you click on forward. You'll notice it does display "installing" at the bottom, which rapidly changes to "detecting file systems" and the "quit" button has disappeared, the back button is grayed out (non-functional), so the only way to quit is to hit the reset button on the box.

The next screen to appear is "Where are you". Now, If you know in advance what the installer is likely to do that should be OK, something we can revisit in Oneiric for sure, and I definitely agree that it would be foolish at this point to fiddle with ubiquity.

I do however believe we need to make some mention of this in the release notes (not real sure how to word that though). Keep in mind that posts #4 thru #10 reflect what happened when I had a blank 4GB flash drive plugged in, albeit intentionally to prove my point.

I've helped troubleshoot quite a few boot problems where someone had mistakenly left a memory card from a camera or such inserted and ended up cussing grub when the problem was actually located between the chair and the keyboard :^)

OTOH it shouldn't cause any data loss, at worst a wasted 20 minutes of install time and the simple reformatting of whatever drive/partition was mistakenly used.

Anyway I'm subscribing the release team so they can decide if this warrants a mention in the release notes.

I've been flogging that for a long, long time now and I'm pretty darn dismayed that the dev can't even properly identify what actually happens in a given installation scenario :(

End rant :)

Thanks again for stepping up and helping me with this. I couldn't have done it without you.

Of course this means a sixth round of testing which will be a new record for me.

---

### Post by bcbc on 2011-04-26
I can't believe they had to respin all the CD's for this patch and they didn't even test it once beforehand !!!!

---

### Post by kansasnoob on 2011-04-26
Since the devs are on the other side of the pond I guess I'll switch back to my good box .............. I need a router really bad.

Quite a while back I posted a query about that:

[http://ubuntuforums.org/showthread.php?t=1735495](http://ubuntuforums.org/showthread.php?t=1735495)

You wouldn't happen to have any suggestions :)

Also, remember to confirm that bug.

---

### Post by bcbc on 2011-04-26
> **kansasnoob said:**
> Please confirm here:

[https://bugs.launchpad.net/wubi/+bug/771517](https://bugs.launchpad.net/wubi/+bug/771517)

Minor rant ahead :)

You know I've spent a lot of time testing various features of ubiquity, raised all kinds of heck both before and after Maverick was released :mad:

Now, besides this debacle, today Evan made a comment here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)



I certainly called BS on that:



I've been flogging that for a long, long time now and I'm pretty darn dismayed that the dev can't even properly identify what actually happens in a given installation scenario :(

End rant :)

Thanks again for stepping up and helping me with this. I couldn't have done it without you.

Of course this means a sixth round of testing which will be a new record for me.
Yeah it's kind of disappointing - after the confusion from the ubiquity changes with Maverick - where some users lost their windows installs by accident - I would expect that they'd do a rational design and then build to that spec and then test it to death to confirm everything works well in advance.

Now we'll need separate install instructions for 10.04, 10.10, 11.04 and soon, when they change it yet again, for 11.10.

PS I confirmed the bug 

I can test this fairly easily, since the deleting logic is all contained within wubi.exe. So I'll test it again if they drop a wubi-rev210.exe

But I reckon 3rd time's a charm on this :)

Again, well done for being persistent and testing this stuff.

---

### Post by kansasnoob on 2011-04-26
> I reckon 3rd time's a charm on this

Did this also effect normal Wubi installs?

If not they might go for something in the release notes.

If they do release a new iso tomorrow I'm going to skip all the other installs, hook up this Windows box, and start right here.

I performed the live w/persistence test and four other installation tests today before trying this.

We're really down to the wire on this.

---

### Post by bcbc on 2011-04-26
> **kansasnoob said:**
> Did this also effect normal Wubi installs?

If not they might go for something in the release notes.

If they do release a new iso tomorrow I'm going to skip all the other installs, hook up this Windows box, and start right here.

I performed the live w/persistence test and four other installation tests today before trying this.

We're really down to the wire on this.

No I tested a standalone install (outside of common startup) to make sure it didn't delete itself and it was ok.

---

### Post by wilee-nilee on 2011-04-26
Not sure if this is helpful, but I installed Natty in W7 with the daily from a cd just minutes ago.

acer aspire one d250 for anybody wanting to know.

---

### Post by kansasnoob on 2011-04-27
OK, I'm trying the iso-testing build 20110427, and I think there's progress but I get a new error, "Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing."

So I need to poke around and see if I can find that. Here's the full text if needed:

> 04-26 10:27 INFO   root: === wubi 11.04 rev210 ===
04-26 10:27 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev210.log
04-26 10:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-26 10:27 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\data
04-26 10:27 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\bin\7z.exe
04-26 10:27 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 10:27 DEBUG  CommonBackend: Fetching basic info...
04-26 10:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-26 10:27 DEBUG  CommonBackend: platform=win32
04-26 10:27 DEBUG  CommonBackend: osname=nt
04-26 10:27 DEBUG  CommonBackend: language=en_US
04-26 10:27 DEBUG  CommonBackend: encoding=cp1252
04-26 10:27 DEBUG  WindowsBackend: arch=i386
04-26 10:27 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\data\isolist.ini
04-26 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 10:27 DEBUG  WindowsBackend: Fetching host info...
04-26 10:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:27 DEBUG  WindowsBackend: windows version=xp
04-26 10:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 10:27 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 10:27 DEBUG  WindowsBackend: windows_build=2600
04-26 10:27 DEBUG  WindowsBackend: gmt=-6
04-26 10:27 DEBUG  WindowsBackend: country=US
04-26 10:27 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 10:27 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:27 DEBUG  WindowsBackend: windows_language=English
04-26 10:27 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 10:27 DEBUG  WindowsBackend: bootloader=xp
04-26 10:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33338.09375 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(C: hd 33338.09375 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: uninstaller_path=None
04-26 10:27 DEBUG  WindowsBackend: previous_target_dir=None
04-26 10:27 DEBUG  WindowsBackend: previous_distro_name=None
04-26 10:27 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:27 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:27 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:27 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:27 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 10:27 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:27 DEBUG  CommonBackend: Searching for local CDs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu Netbook CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Kubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Kubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Xubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Xubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Mythbuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Mythbuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
04-26 10:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
04-26 10:27 DEBUG  Distro: wrong arch: i386 != amd64
04-26 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-26 10:27 INFO   root: Running the CD menu...
04-26 10:27 DEBUG  WindowsFrontend: __init__...
04-26 10:27 DEBUG  WindowsFrontend: on_init...
04-26 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\translations, languages=['en_US', 'en']
04-26 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\translations, languages=['en_US', 'en']
04-26 10:27 INFO   WindowsFrontend: Operation cancelled
04-26 10:27 DEBUG  WindowsFrontend: frontend.quit
04-26 10:27 DEBUG  WindowsFrontend: frontend.on_quit
04-26 10:27 DEBUG  root: application.on_quit
04-26 10:27 INFO   root: sys.exit
04-26 10:43 INFO   root: === wubi 11.04 rev210 ===
04-26 10:43 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev210.log
04-26 10:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe"']
04-26 10:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data
04-26 10:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
04-26 10:43 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 10:43 DEBUG  CommonBackend: Fetching basic info...
04-26 10:43 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe
04-26 10:43 DEBUG  CommonBackend: platform=win32
04-26 10:43 DEBUG  CommonBackend: osname=nt
04-26 10:43 DEBUG  CommonBackend: language=en_US
04-26 10:43 DEBUG  CommonBackend: encoding=cp1252
04-26 10:43 DEBUG  WindowsBackend: arch=i386
04-26 10:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
04-26 10:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 10:43 DEBUG  WindowsBackend: Fetching host info...
04-26 10:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:43 DEBUG  WindowsBackend: windows version=xp
04-26 10:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 10:43 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 10:43 DEBUG  WindowsBackend: windows_build=2600
04-26 10:43 DEBUG  WindowsBackend: gmt=-6
04-26 10:43 DEBUG  WindowsBackend: country=US
04-26 10:43 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 10:43 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:43 DEBUG  WindowsBackend: windows_language=English
04-26 10:43 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 10:43 DEBUG  WindowsBackend: bootloader=xp
04-26 10:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33335.34375 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(C: hd 33335.34375 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: uninstaller_path=None
04-26 10:43 DEBUG  WindowsBackend: previous_target_dir=None
04-26 10:43 DEBUG  WindowsBackend: previous_distro_name=None
04-26 10:43 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:43 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:43 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:43 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:43 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 10:43 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:43 DEBUG  CommonBackend: Searching for local CDs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 INFO   root: Running the installer...
04-26 10:43 DEBUG  WindowsFrontend: __init__...
04-26 10:43 DEBUG  WindowsFrontend: on_init...
04-26 10:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:44 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=lance
04-26 10:44 INFO   root: Received settings
04-26 10:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:44 DEBUG  TaskList: # Running tasklist...
04-26 10:44 DEBUG  TaskList: ## Running select_target_dir...
04-26 10:44 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-26 10:44 DEBUG  TaskList: # Cancelling tasklist
04-26 10:44 DEBUG  TaskList: # Finished tasklist
04-26 10:44 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.


I wonder if I should report this at that bug report?

---

### Post by kansasnoob on 2011-04-27
OK that was easy to find, it's size was zero so I deleted it. Going to reboot and try again :D

---

### Post by kansasnoob on 2011-04-27
Aargh, this is not going well :(

Now I get a "IOError: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
04-26 11:15 DEBUG  TaskList: # Finished tasklist" error. Full text:

```
04-26 10:27 INFO   root: === wubi 11.04 rev210 ===
04-26 10:27 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev210.log
04-26 10:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-26 10:27 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\data
04-26 10:27 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\bin\7z.exe
04-26 10:27 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 10:27 DEBUG  CommonBackend: Fetching basic info...
04-26 10:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-26 10:27 DEBUG  CommonBackend: platform=win32
04-26 10:27 DEBUG  CommonBackend: osname=nt
04-26 10:27 DEBUG  CommonBackend: language=en_US
04-26 10:27 DEBUG  CommonBackend: encoding=cp1252
04-26 10:27 DEBUG  WindowsBackend: arch=i386
04-26 10:27 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\data\isolist.ini
04-26 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 10:27 DEBUG  WindowsBackend: Fetching host info...
04-26 10:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:27 DEBUG  WindowsBackend: windows version=xp
04-26 10:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 10:27 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 10:27 DEBUG  WindowsBackend: windows_build=2600
04-26 10:27 DEBUG  WindowsBackend: gmt=-6
04-26 10:27 DEBUG  WindowsBackend: country=US
04-26 10:27 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 10:27 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 10:27 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:27 DEBUG  WindowsBackend: windows_language=English
04-26 10:27 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 10:27 DEBUG  WindowsBackend: bootloader=xp
04-26 10:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33338.09375 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(C: hd 33338.09375 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 10:27 DEBUG  WindowsBackend: uninstaller_path=None
04-26 10:27 DEBUG  WindowsBackend: previous_target_dir=None
04-26 10:27 DEBUG  WindowsBackend: previous_distro_name=None
04-26 10:27 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:27 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:27 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:27 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:27 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 10:27 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:27 DEBUG  CommonBackend: Searching for local CDs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Ubuntu Netbook CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Kubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Kubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Xubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Xubuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Mythbuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp is a valid Mythbuntu CD
04-26 10:27 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\casper\filesystem.squashfs
04-26 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
04-26 10:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
04-26 10:27 DEBUG  Distro: wrong arch: i386 != amd64
04-26 10:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-26 10:27 INFO   root: Running the CD menu...
04-26 10:27 DEBUG  WindowsFrontend: __init__...
04-26 10:27 DEBUG  WindowsFrontend: on_init...
04-26 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\translations, languages=['en_US', 'en']
04-26 10:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl66.tmp\translations, languages=['en_US', 'en']
04-26 10:27 INFO   WindowsFrontend: Operation cancelled
04-26 10:27 DEBUG  WindowsFrontend: frontend.quit
04-26 10:27 DEBUG  WindowsFrontend: frontend.on_quit
04-26 10:27 DEBUG  root: application.on_quit
04-26 10:27 INFO   root: sys.exit
04-26 10:43 INFO   root: === wubi 11.04 rev210 ===
04-26 10:43 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev210.log
04-26 10:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe"']
04-26 10:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data
04-26 10:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
04-26 10:43 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 10:43 DEBUG  CommonBackend: Fetching basic info...
04-26 10:43 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe
04-26 10:43 DEBUG  CommonBackend: platform=win32
04-26 10:43 DEBUG  CommonBackend: osname=nt
04-26 10:43 DEBUG  CommonBackend: language=en_US
04-26 10:43 DEBUG  CommonBackend: encoding=cp1252
04-26 10:43 DEBUG  WindowsBackend: arch=i386
04-26 10:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
04-26 10:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 10:43 DEBUG  WindowsBackend: Fetching host info...
04-26 10:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:43 DEBUG  WindowsBackend: windows version=xp
04-26 10:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 10:43 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 10:43 DEBUG  WindowsBackend: windows_build=2600
04-26 10:43 DEBUG  WindowsBackend: gmt=-6
04-26 10:43 DEBUG  WindowsBackend: country=US
04-26 10:43 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 10:43 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 10:43 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:43 DEBUG  WindowsBackend: windows_language=English
04-26 10:43 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 10:43 DEBUG  WindowsBackend: bootloader=xp
04-26 10:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33335.34375 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(C: hd 33335.34375 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 10:43 DEBUG  WindowsBackend: uninstaller_path=None
04-26 10:43 DEBUG  WindowsBackend: previous_target_dir=None
04-26 10:43 DEBUG  WindowsBackend: previous_distro_name=None
04-26 10:43 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:43 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:43 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:43 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:43 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 10:43 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:43 DEBUG  CommonBackend: Searching for local CDs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 10:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 10:43 INFO   root: Running the installer...
04-26 10:43 DEBUG  WindowsFrontend: __init__...
04-26 10:43 DEBUG  WindowsFrontend: on_init...
04-26 10:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:44 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=lance
04-26 10:44 INFO   root: Received settings
04-26 10:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 10:44 DEBUG  TaskList: # Running tasklist...
04-26 10:44 DEBUG  TaskList: ## Running select_target_dir...
04-26 10:44 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-26 10:44 DEBUG  TaskList: # Cancelling tasklist
04-26 10:44 DEBUG  TaskList: # Finished tasklist
04-26 10:44 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
04-26 11:14 INFO   root: === wubi 11.04 rev210 ===
04-26 11:14 DEBUG  root: Logfile is c:\docume~1\erickb~1\locals~1\temp\wubi-11.04-rev210.log
04-26 11:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe"']
04-26 11:14 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data
04-26 11:14 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
04-26 11:14 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
04-26 11:14 DEBUG  CommonBackend: Fetching basic info...
04-26 11:14 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe
04-26 11:14 DEBUG  CommonBackend: platform=win32
04-26 11:14 DEBUG  CommonBackend: osname=nt
04-26 11:14 DEBUG  CommonBackend: language=en_US
04-26 11:14 DEBUG  CommonBackend: encoding=cp1252
04-26 11:14 DEBUG  WindowsBackend: arch=i386
04-26 11:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
04-26 11:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 11:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 11:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 11:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 11:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 11:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 11:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 11:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 11:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-26 11:14 DEBUG  WindowsBackend: Fetching host info...
04-26 11:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 11:14 DEBUG  WindowsBackend: windows version=xp
04-26 11:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-26 11:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-26 11:14 DEBUG  WindowsBackend: windows_build=2600
04-26 11:14 DEBUG  WindowsBackend: gmt=-6
04-26 11:14 DEBUG  WindowsBackend: country=US
04-26 11:14 DEBUG  WindowsBackend: timezone=America/Chicago
04-26 11:14 DEBUG  WindowsBackend: windows_username=Erick Brunzell
04-26 11:14 DEBUG  WindowsBackend: user_full_name=Erick Brunzell
04-26 11:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Erick Brunzell
04-26 11:14 DEBUG  WindowsBackend: windows_language_code=1033
04-26 11:14 DEBUG  WindowsBackend: windows_language=English
04-26 11:14 DEBUG  WindowsBackend: processor_name=                   VIA Esther processor 1500MHz
04-26 11:14 DEBUG  WindowsBackend: bootloader=xp
04-26 11:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33328.1992188 mb free ntfs)
04-26 11:14 DEBUG  WindowsBackend: drive=Drive(C: hd 33328.1992188 mb free ntfs)
04-26 11:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 11:14 DEBUG  WindowsBackend: drive=Drive(E: hd 10434.7421875 mb free ntfs)
04-26 11:14 DEBUG  WindowsBackend: drive=Drive(F: hd 98791.4804688 mb free ntfs)
04-26 11:14 DEBUG  WindowsBackend: drive=Drive(G: hd 2211.31640625 mb free ntfs)
04-26 11:14 DEBUG  WindowsBackend: uninstaller_path=None
04-26 11:14 DEBUG  WindowsBackend: previous_target_dir=None
04-26 11:14 DEBUG  WindowsBackend: previous_distro_name=None
04-26 11:14 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 11:14 DEBUG  WindowsBackend: keyboard_layout=us
04-26 11:14 DEBUG  WindowsBackend: keyboard_variant=
04-26 11:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 11:14 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 11:14 DEBUG  WindowsBackend: total_memory_mb=958.484375
04-26 11:14 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 11:14 DEBUG  CommonBackend: Searching for local CDs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-26 11:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-26 11:14 INFO   root: Running the installer...
04-26 11:14 DEBUG  WindowsFrontend: __init__...
04-26 11:14 DEBUG  WindowsFrontend: on_init...
04-26 11:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 11:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 11:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=lance
04-26 11:15 INFO   root: Received settings
04-26 11:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ERICKB~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
04-26 11:15 DEBUG  TaskList: # Running tasklist...
04-26 11:15 DEBUG  TaskList: ## Running select_target_dir...
04-26 11:15 INFO   WindowsBackend: Installing into C:\ubuntu
04-26 11:15 DEBUG  TaskList: ## Finished select_target_dir
04-26 11:15 DEBUG  TaskList: ## Running create_dir_structure...
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-26 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-26 11:15 DEBUG  TaskList: ## Finished create_dir_structure
04-26 11:15 DEBUG  TaskList: ## Running uncompress_target_dir...
04-26 11:15 DEBUG  TaskList: ## Finished uncompress_target_dir
04-26 11:15 DEBUG  TaskList: ## Running create_uninstaller...
04-26 11:15 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\All Users\Start Menu\Programs\Startup\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-26 11:15 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
04-26 11:15 DEBUG  TaskList: # Cancelling tasklist
04-26 11:15 ERROR  root: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Documents and Settings\\All Users\\Start Menu\\Programs\\Startup\\wubi.exe'
04-26 11:15 DEBUG  TaskList: # Finished tasklist

```

---

### Post by kansasnoob on 2011-04-27
Well, Colin's test build works great but it's about 9 or 10 PM over there. Will they release a new iso?

I kind of doubt it. Anyone care to make a bet :lolflag:

---

