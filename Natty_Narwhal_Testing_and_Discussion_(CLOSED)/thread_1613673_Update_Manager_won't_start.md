---
title: "Update Manager won't start"
date: 2010-11-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-04
I ran a couple of updates about 6 hours ago. All was well and I went out for a while. I've just come back and run Update Manager and absolutely nothing happens. No circly thing, no entry in the bottom panel to say it is starting - nothing :(
I can still get to Synaptic and Software Sources. Sources look ok. Temporarily stumped :confused:

---

### Post by garvinrick4 on 2010-11-04
I just upgraded an install to natty and update manager does not start. I am wondering if in natty it will only start if upgrades available? Guess I will just have to wait a while until have a few and see. Would be nice if it did not open if there are partial upgrades available would sure stop a lot of trouble with new users doing partials and getting dependency problems right off the bat in their first go at Ubuntu. This could be a good thing. I do not believe a lot of users even open it at all except the new ones and they are valuable to Ubuntu.

---

### Post by Quackers on 2010-11-04
Hi Garvinrick4, Update Manager has been opening whether there were updates available or not, until tonight. I had one partial upgrade last night but I refused it and the next time UM ran it disappeared.
I've tried sudo apt-get update, the first time there was an error with a source so I commented it out then it ran ok, now it fails again with a medibuntu No pubkey error.
UM still no-go :-(

---

### Post by garvinrick4 on 2010-11-04
> **Quackers said:**
> Hi Garvinrick4, Update Manager has been opening whether there were updates available or not, until tonight. I had one partial upgrade last night but I refused it and the next time UM ran it disappeared.
I've tried sudo apt-get update, the first time there was an error with a source so I commented it out then it ran ok, now it fails again with a medibuntu No pubkey error.
UM still no-go :-( My medibuntu is maverick did not think there would be a natty yet. What are you using? My update manager is an hour old install of natty so I guess it is just plain old has gotten buggy if it was opening before with command. I guess you might want to report it or just see what on what your thread brings. Here is my terminal.
rick@rick-laptop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 32, in <module>
    import gconf
ImportError: No module named gconf
rick@rick-laptop:~$

---

### Post by Quackers on 2010-11-04
Medibuntu was Maverick not Natty.

My terminal output is the same
natty64@natty64-laptop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 32, in <module>
    import gconf
ImportError: No module named gconf
natty64@natty64-laptop:~$

Also tried this :-)

natty64@natty64-laptop:~$ sudo apt-get install gconf
[sudo] password for natty64: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gconf' has no installation candidate
natty64@natty64-laptop:~$

---

### Post by cariboo on 2010-11-04
This is pretty normal during the development cycle, packages breaking, only to be fixed a couple hours to days later. I just did the update on my home system and get the same results.

---

### Post by scradock on 2010-11-04
I'm getting the same error; I've filed bug #671222 on launchpad.

---

### Post by autocrosser on 2010-11-04
Just for reference--It is not recommended to use Update-Manager (Mangler) during testing--there have been several people that have had update-hell that way....I only use Apt-get, Aptitude & Synaptic + I REALLY check & cross-check before updates.

---

### Post by Quackers on 2010-11-04
Yep I had a problem at one time with the dreaded partial upgrade, doh! 
So I should just use sudo apt-get update now should I?

---

### Post by scradock on 2010-11-05
> **Quackers said:**
> Yep I had a problem at one time with the dreaded partial upgrade, doh! 
So I should just use sudo apt-get update now should I?
If you avoid "partial-upgrade" I don't think you will have a problem using Update-manager. I have used it consistently during all testing cycles from hoary onwards, and never had more than a temporary hiccup like the present one, when it seems obvious that a faulty file was delivered as part of the package; it would have arrived in your system whichever of the package management front ends you were using.

Synaptic is great for adding and subtracting packages, which UM doesn't do. I find aptitude unduly complicated for my simple needs, and of course Software Center is an abomination.

We all have our favorites, and it's good to have choices. I say don't accept FUD from anyone - follow your own experience.

Good luck, whatever you decide to use.....

---

### Post by Quackers on 2010-11-05
Thanks for that scradock, but I'm intrigued in my current situation. Having lost UM for the moment, how can the system be updated now? The only thing I can think of is sudo apt-get update and sudo apt-get upgrade. Is there a way of using Synaptic to run updates?

---

### Post by cariboo on 2010-11-05
> **Quackers said:**
> Thanks for that scradock, but I'm intrigued in my current situation. Having lost UM for the moment, how can the system be updated now? The only thing I can think of is sudo apt-get update and sudo apt-get upgrade. Is there a way of using Synaptic to run updates?

Open Synaptic, and click the **Status** on the lower left. then just hit the **Reload** in the upper left. To install the updates, is pretty obvious from there. See the screen shot.

---

### Post by Quackers on 2010-11-05
Wow :-) Learning all the time!

Presumably the "installed (upgradable)" only appears when there are updates. 

Thanks Mr Cariboooooooo  :-)

---

### Post by autocrosser on 2010-11-05
Also--Synaptic will allow you to look at all the updates & see why something is blocked--just remember---you can really b0rk things by forcing a update--sometimes worse than a partial-update...
Synaptic has lots of control....To learn a bit more about it you only need to go as far as your terminal:```
man synaptic
```And read the Man(ual) page about it :) Then goto the (help) tap in Synaptic
I might point out that almost all Linux software has Man(ual) pages......

---

### Post by Quackers on 2010-11-05
Ah right. I was going to Synaptic after a proposed partial upgrade to see what was going on. The light at the end of the tunnel is much brighter now :-) Thanks autocrosser.

---

### Post by philinux on 2010-11-05
> **Quackers said:**
> I ran a couple of updates about 6 hours ago. All was well and I went out for a while. I've just come back and run Update Manager and absolutely nothing happens. No circly thing, no entry in the bottom panel to say it is starting - nothing :(
I can still get to Synaptic and Software Sources. Sources look ok. Temporarily stumped :confused:

I agree with all above re update manager during dev cycle. Best advice, be very careful with it.

Personally I use aptitude safe-upgrade or synaptic.

---

### Post by garvinrick4 on 2010-11-05
+1 aptitide safe-upgrade

---

### Post by Quackers on 2010-11-05
Thanks philinux and garvinrick4. Presumably this is because sometimes packages are removed during updates which, as I have found previously, can be somewhat borksome. The difficulty is that the more inexperienced among us :-) aren't sure which packages can be safely removed and which can't. But, having said that, it could also be said that the more inexperienced among us shouldn't really be testing new upgrades :-)
This is not my every day system (even though I am using it all the time) so it is not a disaster if something goes horribly wrong. It is as much a learning process for me as anything else.
It does seem to be odd though, that updates can remove packages that can bork the system. I don't really understand how that would be allowed to happen, but I know it does. Obviously I understand that an update to a package could be a problem in a testing environment, but to just remove a package that is needed seems to me to be a severe oversight. Presumably this is a more matter of dependencies being forgotten about? 
Anyway, I'm learning all the time :-)
Thanks again guys.

---

### Post by ronacc on 2010-11-05
> **Quackers said:**
> Thanks philinux and garvinrick4. Presumably this is because sometimes packages are removed during updates which, as I have found previously, can be somewhat borksome. The difficulty is that the more inexperienced among us :-) aren't sure which packages can be safely removed and which can't. But, having said that, it could also be said that the more inexperienced among us shouldn't really be testing new upgrades :-)
This is not my every day system (even though I am using it all the time) so it is not a disaster if something goes horribly wrong. It is as much a learning process for me as anything else.
It does seem to be odd though, that updates can remove packages that can bork the system. I don't really understand how that would be allowed to happen, but I know it does. Obviously I understand that an update to a package could be a problem in a testing environment, but to just remove a package that is needed seems to me to be a severe oversight. Presumably this is a more matter of dependencies being forgotten about? 
Anyway, I'm learning all the time :-)
Thanks again guys.

it is not so much updates that cause problems but partial upgrades with update-manager , the other methods give you more control but also put more responsibility on you to decide for yourself what is safe and what isn't .

and yes it's a great way to learn as long as you are careful to keep it on a system where an oops isn't an OH SH .

---

### Post by Quackers on 2010-11-05
I fell foul of a partial upgrade once :-) It won't happen again! It seems strange of UM to offer a partial upgrade when it can do serious damage. Wouldn't it be better to offer a warning that some files couldn't be upgraded because of problem xxx and that part of the upgrade would be ignored? The less experienced wouldn't think it could be such a problem, unless they'd seen the sticky!

---

### Post by Quackers on 2010-11-05
I've just updated to the 2.6.27-2 kernel and the UM still doesn't start but conky now shows it as trying to - for a few seconds.

---

### Post by douham on 2010-11-05
Hi Quackers,

this thread [http://ubuntuforums.org/showthread.php?t=1593270]("http://ubuntuforums.org/showthread.php?t=1593270") will help you get up to the current kernel, for instance this is mine,
```
doug1@doug1-P35-DS3:~$ uname -a
Linux doug1-P35-DS3 2.6.36-1-generic #7-Ubuntu SMP Thu Oct 21 20:36:41 UTC 2010 i686 GNU/Linux
doug1@doug1-P35-DS3:~$
```

update manager is stuffed for me to, I'm not worried, breakage is expected in dev cycles.

---

### Post by ronacc on 2010-11-05
start it in a terminal and it will tell you why it don't start .
```
 update-manager 
```

---

### Post by Quackers on 2010-11-05
It reports the same as I posted earlier on - no change - no gconf module

```
natty64@natty64-laptop:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 32, in <module>
    import gconf
ImportError: No module named gconf
```

---

### Post by ronacc on 2010-11-05
probably because python hasn't fully updated to 2.7 , 2.6 is still the active version although some 2.7 packages are in , use synaptic or apt-get .

this kind of breakage is normal during a dev cycle .

---

### Post by Quackers on 2010-11-05
Thanks ronacc. I was wondering about the possible link with Python. I had to enter Kaivalagi's amendment to conky with regard to Python 2.6 and 2.7 so that conky would keep working.

---

### Post by MacUntu on 2010-11-06
We'll just have to wait.

Run```
python2.6
import gconf
```

=> works fine

But

```
python2.7
import gconf
```

=> fails.

---

### Post by scradock on 2010-11-06
Actually, it seems someone jumped the gun, changing the header in /usr/bin/update-manager to python2.7 before all the needed modules were ready.

Edit /usr/bin/update-manager so that the first line contains python2.6 instead of 2.7 

and presto! all is well - update-manager runs just fine......

PS - where is "Mark Thread Solved"? it should be in Thread Tools, shouldn't it?

---

### Post by arpanaut on 2010-11-06
> PS - where is "Mark Thread Solved"? it should be in Thread Tools, shouldn't it?Not your thread man.  :mrgreen:

---

### Post by scradock on 2010-11-06
> **arpanaut said:**
> Not your thread man.  :mrgreen:

Ah! that explains it.....

---

### Post by Quackers on 2010-11-06
Thanks scradock, UM is churning normally now :-)
I'm not sure whether we've cheated or not, lol, but I'll mark the thread solved.
Thanks all!

---

### Post by autocrosser on 2010-11-07
All is well---There has been many times I've edited things to get them running...you might file a bug report about it......

---

### Post by Quackers on 2010-11-07
> **autocrosser said:**
> All is well---There has been many times I've edited things to get them running...you might file a bug report about it......

scradock filed one. It's been updated.

---

### Post by autocrosser on 2010-11-07
Sounds good---are you having fun yet????:)

---

### Post by Quackers on 2010-11-07
Oh yes indeeeeeeedy :-)
I learned that Synaptic can update too :-) I'm not entirely happy with my sources.list. I think I may have messed about a bit too much with it :-) I'll see how updates go for the next few days.

---

### Post by ronacc on 2010-11-07
you should always make a backup of the original sources.list that the installer installs , that way you can always go back to the default .

---

### Post by Quackers on 2010-11-07
> **ronacc said:**
> you should always make a backup of the original sources.list that the installer installs , that way you can always go back to the default .
Yes, you're absolutely right, and that's something I normally do. This one slipped through the net, unfortunately. Still, there are no apparent problems yet, so it may be alright. I'll know for sure within a week :-)

---

### Post by arpanaut on 2010-11-07
This, is always a handy link to have:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Quackers on 2010-11-07
> **arpanaut said:**
> This, is always a handy link to have:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Very nice, thank you :-) Duly bookmarked!

---

### Post by seeker5528 on 2010-11-08
> **ronacc said:**
> you should always make a backup of the original sources.list that the installer installs , that way you can always go back to the default .

Or better yet, don't mess with our sources.list file at all, create a new *.list file in /etc/apt/sources.list.d/ for each PPA/3rd party repository you add.

Then if you are stuck at the command line and need to disable one of these temporarily, you just need to change to /etc/apt/sources.list.d/ and add '.old' to or remove '.old' from the file name for that particular repository to enable/disable it.

Later, Seeker

---

### Post by Quackers on 2010-11-08
Thanks seeker for that info

---

### Post by autocrosser on 2010-11-08
> **arpanaut said:**
> This, is always a handy link to have:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Very Nice!!!! Thanks!!!!

---

### Post by arpanaut on 2010-11-09
You are welcome!

OT:  > "Let's nobody be dead today----Looks very bad on my report"  One of my favourite lines from AVATAR :grin:
Saw Avatar for the first time last night and when I heard that line, I thought of my Ubuntu brethren, Thanks for that!   Set up the movie perfectly from thereon.

---

### Post by autocrosser on 2010-11-09
Yes--I'm a SciFi "nut" & LOVE good CGI--Avatar has both in spades.....one of my most watched movies--along with the Star Trek series  & the Star Wars arc... Firefly was a series I wished would have stayed along with Babylon 5......waiting for the next "good" space series.

---

