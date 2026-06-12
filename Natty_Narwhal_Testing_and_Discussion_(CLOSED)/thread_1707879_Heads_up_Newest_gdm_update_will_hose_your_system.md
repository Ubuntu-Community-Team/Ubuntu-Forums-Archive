---
title: "Heads up: Newest gdm update will hose your system"
date: 2011-03-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-03-15
gdm 2.32.0-0ubuntu10 is at fault

Stick with ubuntu9 for now.

[https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9](https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9)

---

### Post by beew on 2011-03-15
I think it just killed mine. I have done some updates and now Natty is not bootable. The screen is stuck with "checking battery state"... Just have checked the forum before updating.

---

### Post by beew on 2011-03-15
After some updates this evening( about an hour ago, it was fine in the morning) it seems that my Natty installation is no longer bootable.

The bootscreen is stuck at "checking battery state" forever. It may be related to this thread.
[http://ubuntuforums.org/showthread.php?t=1707879]("http://ubuntuforums.org/showthread.php?t=1707879")

Now is there a way to restore the system without reinstalling?

---

### Post by dinamic1 on 2011-03-15
> **beew said:**
> After some updates this evening( about an hour ago, it was fine in the morning) it seems that my Natty installation is no longer bootable.

The bootscreen is stuck at "checking battery state" forever. It may be related to this thread.
[http://ubuntuforums.org/showthread.php?t=1707879](http://ubuntuforums.org/showthread.php?t=1707879)

Now is there a way to restore the system without reinstalling?

try booting with <Previous linux version> (from grub)

i can boot with gdm_2.32.0-0ubuntu10_i386.deb installed and the 2.6.38-5-generic kernel

---

### Post by mc4man on 2011-03-15
It killed one install here, though possibly there were other issues (was installed off of yesterday's iso w/ a reverted ubiquity.

So a fresh install w/ 03/09 iso, updated everything but gdm -  was fine.
Updated gdm and first boot after that failed
Booted to recovery, logged in, then  rebooted and it's now fine.

The install I'm on now is fully updated except for gdm, don't know if I'll risk it. (though curiosity will probably get the best of...

---

### Post by williejones on 2011-03-15
I just upgraded before seeing the GDM update warning.  My reboot was to a black screen.
Alt-Ctl F3 was able to open tty session to login.  Sudo service gdm stop did nothing, sudo 
service gdm start shows the login screen.  Both login and reboot works.

---

### Post by cariboo on 2011-03-15
Threads merged, as they essentially about the same thing.

---

### Post by nm_geo on 2011-03-15
> **beew said:**
> I think it just killed mine. I have done some updates and now Natty is not bootable. The screen is stuck with "checking battery state"... Just have checked the forum before updating.

Got the same here, but if I reboot a couple of times it finally takes.  Some horse race issue.
So, I will leave my other Natty with the older gdm. Ain't testing fun.

Update> sudo service gdm start 

Works here as well when stuck with "checking battery state"

---

### Post by victor9098 on 2011-03-15
> **williejones said:**
> I just upgraded before seeing the GDM update warning.  My reboot was to a black screen.
Alt-Ctl F3 was able to open tty session to login.  Sudo service gdm stop did nothing, sudo 
service gdm start shows the login screen.  Both login and reboot works.

That worked for me too, thank you!

---

### Post by mc4man on 2011-03-15
Went ahead and updated the other install, basically the same except using a text login.
Kept sending me to tty1 so logged in, did a sudo gdm start. logged in, rebooted and all is fine now..

---

### Post by VMC on 2011-03-16
> **mc4man said:**
> Went ahead and updated the other install, basically the same except using a text login.
Kept sending me to tty1 so logged in, did a sudo gdm start. logged in, rebooted and all is fine now..

Basically I did the same with my system. Strange boot up though. The screen goes black for several seconds, then I hear the startup sound and then the desktop comes up.

---

### Post by Harry33 on 2011-03-16
This bug in the latest gdm (2.32.0-0ubuntu10) does not destroy the whole system.
In fact rebooting after gdm failed (with Alt+PrtScr+ R-E-I-S-U-B) helps.
Then just downgrade to the previous version (2.32.0-0ubuntu9).

There is a bug report in Launchpad, go there and mark "affects me too".
Here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805)

---

### Post by coffeecat on 2011-03-16
Note to self for morning routine: remember to boot into Maverick first, not Natty, to check forum to see if there's been any breakage in Natty's bootup since last night. #-o

> **dinamic1 said:**
> try booting with <Previous linux version> (from grub)

i can boot with gdm_2.32.0-0ubuntu10_i386.deb installed and the 2.6.38-5-generic kernel

Unfortunately, that didn't work for me on a 64-bit system. Perhaps the occasionally works that people are reporting applies to the -5 kernel as well.

Downgraded gdm now and awaiting developments. Thanks all.

---

### Post by coffeecat on 2011-03-16
No, I can do better than await developments.

@Harry33, a diff -u shows that the "gdm.upstart" file that Martin Pitt posted in [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805) is identical to the gdm.conf that comes with gdm 2.32.0-0Ubuntu9. I've re-upgraded gdm to 2.32.0-0Ubuntu10 and replaced its gdm.conf with Martin Pitt's file and I was able to boot up and log in once. That may have been a fluke so I'll try a few more bootups later.

I haven't added to the Launchpad thread - I'll leave that to you if you find the same.

---

### Post by rburkartjo on 2011-03-16
tks sudo service gdm start also worked for me

---

### Post by VinDSL on 2011-03-16
> **Starks said:**
> gdm 2.32.0-0ubuntu10 is at fault

Stick with ubuntu9 for now.

[https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9](https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9)
Heh!  Bit me too!

Actually, I was just heading to bed (perhaps to dream), when I read your post.

I last updated about 4 hours ago, and had logged in/out several times with no probs, but...

I thought I'd better see if this machine would reboot before turning it off... Nope!  Nada!

*sudo service gdm start* worked a charm!

Then...

[LIST]
[*]I went to the link you provided.
[*]Downloaded the deb.
[*]Uninstalled gdm 2.32.0-0ubuntu10
[*]Installed gdm 2.32.0-0ubuntu9
[*]Pinned it.
[*]Rebooted.
[/LIST]

All is good now!

Thank you, soooo much, for posting this.

That would have been a rude surprise, when I turned this machine on, in the morn!  ;)

**EDIT**

BTW, here's the link to the deb file I used (32-bit)...

[https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9/+buildjob/2282263](https://launchpad.net/ubuntu/+source/gdm/2.32.0-0ubuntu9/+buildjob/2282263)

Might save ppl some searching. :)

---

### Post by Harry33 on 2011-03-16
> **coffeecat said:**
> No, I can do better than await developments.

@Harry33, a diff -u shows that the "gdm.upstart" file that Martin Pitt posted in [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805) is identical to the gdm.conf that comes with gdm 2.32.0-0Ubuntu9. I've re-upgraded gdm to 2.32.0-0Ubuntu10 and replaced its gdm.conf with Martin Pitt's file and I was able to boot up and log in once. That may have been a fluke so I'll try a few more bootups later.

I haven't added to the Launchpad thread - I'll leave that to you if you find the same.

Yes so it seems, the bug is in the upstart job.
This is now market as high importance, so the fix will be released soon.

---

### Post by kerry_s on 2011-03-16
i just added "service gdm start &" to /etc/rc.local for now.

---

### Post by zika on 2011-03-16
The only reason I did not notice the bug is: I have &#8222;text&#8220; in kernel line... :)
Tried, now, without it and... There is a bug...

---

### Post by cariboo on 2011-03-16
I'm disappointed :), I upgraded last night, rebooted this morning, my system booted normally.

---

### Post by beew on 2011-03-16
Strange. I have been stuck with a black screen, I then followed the instructions here to use the tty login, which worked. After that I rebooted several times and it just booted normally, I haven't changed any settings or got any upgrade, still the same gdm package. But everything works normally now, just have to test on the other machine.

---

### Post by dino99 on 2011-03-16
a new gdm package will rise into repo soon, fixing the previous issue on some systems

---

### Post by rburkartjo on 2011-03-16
tks for the heads up dino

---

### Post by tad1073 on 2011-03-16
$ gdm --version
GDM 2.32.0

working fine on my computer

---

### Post by Harry33 on 2011-03-16
> **tad1073 said:**
> $ gdm --version
GDM 2.32.0

working fine on my computer

The version that fixed this issue is 2.32.0-0ubuntu11.
Here:
[https://launchpad.net/ubuntu/natty/+source/gdm/2.32.0-0ubuntu11](https://launchpad.net/ubuntu/natty/+source/gdm/2.32.0-0ubuntu11)

---

### Post by VinDSL on 2011-03-16
I just awoke...

[LIST]
[*]Unpinned gdm 2.32.0-0ubuntu9
[*]Installed gdm 2.32.0-0ubuntu11
[*]Rebooted
[/LIST]

gdm 2.32.0-0ubuntu11 fixed the problem.  Startup is back to normal!

That was quick, and I didn't even lose any sleep over it...

**EDIT**

Oops!  Sorry, Harry... didn't see your post (above).

Note to self:  Don't post messages before first pot of coffee.  LoL! :D

---

### Post by rburkartjo on 2011-03-16
harry and vin that worked like a charm. fixed the problem

---

### Post by beew on 2011-03-16
I followed Williejones instruction to log in once and then everything is back to normal (no need for tty login anymore) even though I still have the bad gdm version. 

Weired.

---

### Post by Wobblybob on 2011-03-16
Yep, just done my second sudo aptitude safe-upgrade of the day and the latest gdm package has fixed the problem, well done chaps for a quick fix.

---

### Post by nm_geo on 2011-03-16
I also just upgraded both my Natty's and all is well.  It really was a quick fix.

---

### Post by jerrylamos on 2011-03-16
Upgraded four Natty's, two running Unity 3D two running Unity 2D.

Three of the four went without a hitch.

This one, one of the Unity 3D's, I had to do Ctrl-Alt-F1 and sudo service gdm restart.

Jerry

---

### Post by tjeremiah on 2011-03-17
thats funny. I havent received any new updates for 2 days now.

---

### Post by kansasnoob on 2011-03-17
> **tjeremiah said:**
> thats funny. I havent received any new updates for 2 days now.

Something's borked then ;)

---

### Post by kansasnoob on 2011-03-17
Additional changes to gdm should be expected:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/436936](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/436936)

---

### Post by libihero on 2011-03-17
Natty has always givin me problems booting.  It would freeze with a black screen, and i would have to force reboot multiple times before it actually boots into natty.  now after an update, instead of actually booting (it will still have the black screen and i would have to force reboot), it gives me an error that says "stopping gnome display manager", some other texts, and it freezes at "checking battery state".  when i press the power button once, i see the plymouth splash come up, and it shuts down

---

### Post by tjeremiah on 2011-03-17
> **kansasnoob said:**
> Something's borked then ;)

strange. I've been doing safe upgrade since the beginning. I'll see if anything pops up today, if not, ill do some investigation work.

---

### Post by go7Ul1ai on 2011-03-17
This issue is being discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=1707879](http://ubuntuforums.org/showthread.php?t=1707879)

---

### Post by cariboo on 2011-03-17
Threads merged.

---

### Post by VinDSL on 2011-03-17
> **tjeremiah said:**
> thats funny. I havent received any new updates for 2 days now.

> **kansasnoob said:**
> Something's borked then ;)

I update dev releases via Synaptic, and the updates/installs have been flowing like mad, the past 2 days.

It's been so fast and furious, it reminds me of doing a fresh Windows install.  :D

Synaptic will update 40 things.  I reboot, open Synaptic, and 20  more updates are waiting for me.

Every time I check (every couple of hours) there are even more updates sitting there...

This morning, the updates hosed my Unity Launcher / Dashboard (I'm on 10.10 right now) soooo...

Maybe you're lucky you're NOT getting them...  ;)

---

### Post by tjeremiah on 2011-03-17
> **VinDSL said:**
> I update dev releases via Synaptic, and the updates/installs have been flowing like mad, the past 2 days.

It's been so fast and furious, it reminds me of doing a fresh Windows install.  :D

Synaptic will update 40 things.  I reboot, open Synaptic, and 20  more updates are waiting for me.

Every time I check (every couple of hours) there are even more updates sitting there...

This morning, the updates hosed my Unity Launcher / Dashboard (I'm on 10.10 right now) soooo...

Maybe you're lucky you're NOT getting them...  ;)

I just doubled checked and all the ubuntu software sources were turned off :o. Weird. I currently have 240 updates to catch up to :P

---

### Post by nm_geo on 2011-03-17
> **tjeremiah said:**
> I just doubled checked and all the ubuntu software sources were turned off :o. Weird. I currently have 240 updates to catch up to :P 
Good Luck
:P

---

### Post by tjeremiah on 2011-03-18
> **nm_geo said:**
> Good Luck
:P
thanks. All went well after all those updates. Like the new dash and my drives not showing if they arent mounted.

---

### Post by VinDSL on 2011-03-18
> **tjeremiah said:**
> thanks. All went well after all those updates. Like the new dash and my drives not showing if they arent mounted.
WoW!

Hope you don't mind me piggybacking on your reply, but...

I just experienced one of the weirdest things ever!

As noted above, I fully updated Natty this morning, before going to my job.  In the process, the Unity Launcher / Dashboard was hosed.

I fully expected, by the time I got home, 10's or 100's of ppl would have complained about losing their 'menus' in Natty -- and the problem would be fixed.

To my great surprise, NOBODY complained about it.  Hrm...

Soooo, I booted into the Classic Desktop (which is looking much nicer these days, BTW) and...

[LIST]
[*]Alt-Ctrl-T
[*]unity --reset
[/LIST]

This did nothing, except tell me Unity was not installed.


Then, I tried...

[LIST]
[*]Alt-Ctrl-T
[*]compiz --replace
[/LIST]

LoL!  That was kicking a Harley!

There was a flurry of smoke n' fire, flashing screens, blah, blah, blah.

"Fixed", I thought, and I did a restart into the Unity Desktop.

Still no 'menus', soooo I performed the above (again).

It soon became apparent that Compiz was installed, but Unity had left the building.

Soooo, I installed Unity, rebooted, and all is good.

Anyway, I thought I should document this somewhere, in case others run across the same situation.

Feel free to move this post, if you want, Jim!   ;)

---

### Post by douham on 2011-03-18
> **VinDSL said:**
> WoW!

Hope you don't mind me piggybacking on your reply, but...

I just experienced one of the weirdest things ever!

As noted above, I fully updated Natty this morning, before going to my job.  In the process, the Unity Launcher / Dashboard was hosed.

I fully expected, by the time I got home, 10's or 100's of ppl would have complained about losing their 'menus' in Natty -- and the problem would be fixed.

To my great surprise, NOBODY complained about it.  Hrm...
   ;)

I had all sorts of problems this morning. Tried a reinstall everything is still borked. There is a bug [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203")
 I will try your suggestions, cheers
Doug

> **douham said:**
> My latest update has bought Unity (3.66) breakage too. If I launch the dash ¨play music" will launch firefox. Also launching  the applications dash, then all aplications-click on a category eg; system, education etc launches the whatever icon is underneath.
This system was installed at alpha2.

I might download the latest nightly.

---

### Post by masodin on 2011-03-26
hello all,

i am an ubuntu nooby, out of curiosity i installed ubuntu 11.04 alpha3 last night.
Yes, i will definitely never install an alpha version unless i wish to test it!
Frankly said, i first installed 386 version on a notebook which runs just fine. So I thought why not install the 64 bit version on my pc.

Unfortunately, the system did not finish the first reboot in order to complete the installation. First it always stopped at "checking battery state". There, I read that this bug is already fixed:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805)

So I pressed Alt +F2 in order to log in and performed sudo apt-get update followed by sudo apt-get upgrade. Everytime there was a new update I hoped, that this will fix the issue. But when I shutdown the system with sudo shutdown now -h and restart again there is no progress.

The only thing that changed is that the system no stops at "Stopping userspace bootsplash", whatever that means? 

Can anyone of you PLEASE tell me what to do in order make ubuntu 11.04 apha3 running?

Again, i promise as a nooby i will never run an alpha version!

Thanks.

masodin

---

### Post by rburkartjo on 2011-03-26
tks for the heads up ya'll

---

### Post by kansasnoob on 2011-03-26
> **masodin said:**
> hello all,

i am an ubuntu nooby, out of curiosity i installed ubuntu 11.04 alpha3 last night.
Yes, i will definitely never install an alpha version unless i wish to test it!
Frankly said, i first installed 386 version on a notebook which runs just fine. So I thought why not install the 64 bit version on my pc.

Unfortunately, the system did not finish the first reboot in order to complete the installation. First it always stopped at "checking battery state". There, I read that this bug is already fixed:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805)

So I pressed Alt +F2 in order to log in and performed sudo apt-get update followed by sudo apt-get upgrade. Everytime there was a new update I hoped, that this will fix the issue. But when I shutdown the system with sudo shutdown now -h and restart again there is no progress.

The only thing that changed is that the system no stops at "Stopping userspace bootsplash", whatever that means? 

Can anyone of you PLEASE tell me what to do in order make ubuntu 11.04 apha3 running?

Again, i promise as a nooby i will never run an alpha version!

Thanks.

masodin

I doubt this has anything to do with the gdm update we were talking about here. I see you'd originally posted here:

[http://ubuntuforums.org/showthread.php?p=10603503#post10603503](http://ubuntuforums.org/showthread.php?p=10603503#post10603503)

I'd suggest you start a new thread here in Natty Dev:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Just click on New Thread and type away :)

But I'll include a few "wild guesses":

You mention Alpha 3 working on other hardware so maybe we should see the hardware profile from the machine that's not working so well. If any Linux will run on it, the output of these commands would be helpful:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo | head -10
```

```
free -m
```

But you also specify that the working version was 32bit and this one is 64bit. So, did you check the md5sum of the 64bit iso? And did you check the disc for errors?

If the iso and disk are both good then I'd assume that it's a problem specific to the 64bit version :confused:

---

### Post by masodin on 2011-03-26
hello kansasnoob,

thank you very for your reply.

As suggested i opened a separate thread here:

[http://ubuntuforums.org/showthread.php?p=10604501#post10604501](http://ubuntuforums.org/showthread.php?p=10604501#post10604501)

I will post all profiles requested by you there.

regards,

masodin

---

