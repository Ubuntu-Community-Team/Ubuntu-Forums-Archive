---
title: "Sudo timeout problems since sudo update"
date: 2010-12-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-19
Having used visudo to edit the timeout parameter for sudo all was well and I was not repeatedly asked for my password when using sudo. The amendedment worked fine in Maverick and both Natty installs.
However, since the recent sudo updates (during which I chose to "keep" my current configuration, rather than over-writing it) I am asked for my password at every single use of password protected programs.

Here is the relevant line from visudo

Defaults        env_reset,timestamp_timeout=-1

Actually, there is a much bigger space between the Defaults and the env_reset wording in the original.
I've also tried varying amounts of timeout=

Has anybody noticed anything similar recently?
Thanks people :-)

---

### Post by cariboo on 2010-12-19
Personally I prefer a shorter timeout than the default, so I haven't noticed if it's shorter than previously, but I did notice that I had synaptic open for a couple of hours, and I didn't have to enter a password when I went to use it again.

I'd suggest you wait to see if the problem is affecting more people, and if so, submit a bug.

---

### Post by Quackers on 2010-12-19
Hokey cokey, that sounds reasonable :-)

---

### Post by garvinrick4 on 2010-12-19
#Quackers I use a -1 also in default line. Did not work in Natty.
#I changed to a positive number, I used 40 and now I get 40 minutes
  in natty. I imagine natty does not like the -1 for now.

---

### Post by Quackers on 2010-12-19
I tried a few numbers but the result was the same for me. Maybe the numbers I used were to big :-) I'll try some smaller ones :-) Thanks garvinrick4.

---

### Post by Quackers on 2010-12-19
No good. I've tried -1, 20, 40, 240 and 300 and logged out/in or restarted after each change. Synaptic, software sources and any sudo command is asking me for the password every time I use them.
I've tried different ways to save the changes, ctrl + o, enter, ctrl + x and also ctrl + x and enter. No syntax errors are reported.

Garvinrick4, during the recent updates to sudo did you elect to accept the new configuration, or to "keep" the one you had? Thanks.

---

### Post by trulan on 2010-12-19
I've got a different problem (I think) - sudo works but gksu never comes up, it hangs and X hangs with it.  I have to ctrl+alt+F1 to a tty and killall gksu, then the desktop is usable again.  To use synaptic or update-manager, I have to start it from a terminal using sudo.  Anything that calls gksu (unless I call it from a terminal that already has sudo permissions) hangs the desktop.

Edit:  I 'kept' my old sudo configuration when it updated.

---

### Post by mc4man on 2010-12-19
If it hasn't started working for you yet maybe try a couple of  full restarts to the Classic interface, then ck. there.

Saw the same thing here with the terminal and synaptic on 2 machines, both are now using the timeout.

Because i also use the sudoers line in Mav, then went ahead and edited, works as expected, no pass needed after entering at login. (for synaptic and sudo, update manager and ubuntu store use aptdaemon/policy-kit

---

### Post by Quackers on 2010-12-19
Ok, will try that. Thanks mc4man

---

### Post by Quackers on 2010-12-19
oops. Won't be trying that again!
I restarted after changing the Login screen details to allow the choice of desktop.
Went into classic. No top panel plus one or two other things missing. ran visudo changes and rebooted back in. Changes to sudo had no effect - still asking for password at every use of everything. 
So I changed the Login screen details back to auto login and to desktop edition and rebooted.
The top panel has no applets in it at all. Unity isn't running and when I go to ccsm to check the unity plugin - it's gone again!
So I go to synaptic and I confirm that unity is still installed and it is. I run unity from a terminal and the desktop flashes and returns with no window borders and no unity. 20 seconds later it flashes again and the windows borders and unity start up. Everything's back to normal.
oops, not quite. As soon as I mouse over the side bar it disappears! There's a space still there for it, but it's gone.
I close the terminal and everything disappears again. I hit Alt + F2 and a run box comes up! First time in more than a week! I enter unity and after a second the desktop flashes and re-appears and windows borders are gone again. Then 20 seconds later everything comes back to normal - as it did before.
Then the sidebar disappears again and I have no top bar applets (on the right side).
What a mess!

---

### Post by Quackers on 2010-12-19
I found the unity plugin in ccsm. It's now in the Desktop section.
So on reboot most things returned - including a bottom panel! which I haven't had for a while :-)
Also, full screen FF windows now don't double up titles in the top bar!

Sadly it also takes about 20 seconds longer to boot now!

Very weird.

---

### Post by mc4man on 2010-12-19
No problem here with such - I've found if switching interfaces you should do a full restart, ( not a log out/in), at least twice for each interface.

So here 2 restarts to classic produce a normal gnome-panel interface with all applets working and no need to reload them
When returning to unity same deal - 2 restarts produces a solid unity  on my desktop
( a laptop has some separate  [issues in unity]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461"), but not from switching interfaces

---

### Post by Quackers on 2010-12-19
Hmm, I didn't find that at all. I did full reboots in each case. I'll see how things go :-)

---

### Post by garvinrick4 on 2010-12-19
> **Quackers said:**
> No good. I've tried -1, 20, 40, 240 and 300 and logged out/in or restarted after each change. Synaptic, software sources and any sudo command is asking me for the password every time I use them.
I've tried different ways to save the changes, ctrl + o, enter, ctrl + x and also ctrl + x and enter. No syntax errors are reported.

Garvinrick4, during the recent updates to sudo did you elect to accept the new configuration, or to "keep" the one you had? Thanks. I keep the one I have on all installs that come from dist-upgrade. On fresh installs of Alpha's I do not change any files at install so always take the new one there just so I have one install that is how designed. Just a personal thing.
# So on install in question kept the one I had. -1 does not produce desired effects.

---

### Post by Quackers on 2010-12-19
Thanks for that confirmation garvinrick4.
I wondered about the -1 thing, but I have tried many others now, still without success yet :-)

---

### Post by garvinrick4 on 2010-12-19
## From sudoers manual:

timestamp_timeout
                       Number of minutes that can elapse before sudo will ask
                       for a passwd again.  The timeout may include a
                       fractional component if minute granularity is
                       insufficient, for example 2.5.  The default is 15.  Set
                       this to 0 to always prompt for a password.  If set to a
                       value less than 0 the user's timestamp will never
                       expire.  This can be used to allow users to create or
                       delete their own timestamps via sudo -v and sudo -k
                       respectively.

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by Quackers on 2010-12-20
Thanks, but still struggling :-)
I'll wait and see what develops.

---

### Post by mc4man on 2010-12-21
Well much to my chagrin the reason it worked on my desktop was I'd pinned sudo previously and had forgotten all about. (the laptop reverted to this behavior as soon as the terminal was closed and re-opened.

It would seem it has nothing to do with the sudoers file (on the desktop I'm actually using a file in /etc/sudoers.d instead for this), but the new version of sudo itself.

Why exactly don't know, there seemed to be changes about the location of timestamps.
So the timeout only seems to work in the instance that's open and has been previously authenticated.

---

### Post by Quackers on 2010-12-21
Lol, I wouldn't know! After updating just now I can't open synaptic again! I just get a spinning white thing for about 7 or 8 seconds, then it disappears but the desktop is locked up. Can't click on anything at all! However, pressing Esc brings usability back for the rest of items - except Software Sources. Back to no right-click in FF again :-)
I think you're right about the sudo timestamp though mc4man. I think something has definitely changed.

---

### Post by mc4man on 2010-12-21
The updates didn't cause too much issue here (didn't apply them all so lost mouse at login, fixed in recovery.

On one install leaving as is, the other reverted to previous sudo( 1.7.2p7-1ubuntu3) which works fine

On a side note - while I don't know if the intention is (at release) that you'll be able to switch logins at will without issue that's certainly not the case now.
I've found that to go from Desktop (unity) to Classic (gnome-panel) that this works well
_Restart_ and login to Classic, reload any applets that fail to load (I lock their position
_Logout/login_ back to Classic - the panels/applets should/do load cleanly
Then any subsequent logins to Classic work fine (cold or warm

Returning to Desktop (unity) usually works fine, with exception of the current significant bug about menu dropdowns, menu's behind windows, normal or context, launcher going black when r. clicked on or being unresponsive.

For that i've found that opening/closing a dir. on the desktop clears up any of those possibilities
( atm, have created a startup script that has a small sleep and then has nautilus open a dir. on the desktop.
So for the moment unity is absolutely fine, sometimes after a long inactive period one or more of the above reoccurs, opening/closing a dir. or two again clears up.

---

### Post by mc4man on 2011-01-20
Quackers
I don't now if you still wanted this (adjust timeout) but - 

After a couple of times of having the auth box open behind synaptic (and nothing possible till it's addressed which it can't be), I decided to restore the timeout and also then set to -1

It appears that the current sudo still won't use any timeout except in the current open instance so reverted to previous version which works fine with default timeout and can be adjusted.

[prior natty sudo here]("https://launchpad.net/ubuntu/natty/+source/sudo")  (click on the appropriate arch on right

[COLOR="Blue"] Edit I prefer the maverick security updated sudo instead[/COLOR]:
If inclined to use the mav one the package is here
[http://packages.ubuntu.com/maverick/sudo](http://packages.ubuntu.com/maverick/sudo)

Download either and use dpkg to downgrade 
( easiest way - create an empty folder, stick the dl'ed .deb in it. Then in a terminal cd to the folder and 
```
sudo dpkg -i *.deb
```

Decided to use an alternate method to adjust, not big difference  though it does leave the sudoers file alone (01_file is created by visudo
```
sudo visudo -f /etc/sudoers.d/01_file
```
inserted as before
```
Defaults env_reset,timestamp_timeout=-1
```
Ctrl+o, enter, Crtl+x

Have an open bug on that's gone nowhere - for all I know this is the intention..
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391)

---

### Post by Quackers on 2011-01-20
I have been unseuccessful in all my (various) attempts to get this working :-(
I just hoped that it would all become "normal" again with updates :-)  Not yet though!
I'll have another rummage around using the above info.
Thanks for the efforts :-)

---

### Post by Harry33 on 2011-01-20
The new update of sudo (1.7.4p4-5ubuntu3) seems not to touch this issue:
SECURITY UPDATE: privilege escalation via -g when using group Runas_List
    - debian/patches/CVE-2011-0010.patch: prompt for password when the user is
      running sudo as himself but as a different group

---

### Post by Harry33 on 2011-01-20
The new update of sudo (1.7.4p4-5ubuntu3) seems not to touch this issue:
SECURITY UPDATE: privilege escalation via -g when using group Runas_List
    - debian/patches/CVE-2011-0010.patch: prompt for password when the user is
      running sudo as himself but as a different group

---

### Post by mc4man on 2011-01-20
Quackers
I gave you  the 'almost right page' - didn't say what version - this was the last to work as we hoped, from here pick the arch
[https://launchpad.net/ubuntu/+source/sudo/1.7.2p7-1ubuntu3](https://launchpad.net/ubuntu/+source/sudo/1.7.2p7-1ubuntu3)
(sorry if the last link caused you any confusion

> The new update of sudo (1.7.4p4-5ubuntu3) seems not to touch this issue:
While it was a month ago and don't quite remember I recollect when comparing the sources of the above and new upstream seeing something (the location of timestamps.
Now I'm starting to think is may be intended (one of several reasons I find when bug rep's go unattended to

---

### Post by Quackers on 2011-01-20
Thanks again, mc4man :-)
I have tried again with today's version but still no go, as Harry33 has said. 
Not a major problem, just a little irksome, especially when you need to enter your password just to check for updates. I could understand it to install updates! :-)

---

### Post by mc4man on 2011-02-04
Quackers - 
seeing as no info coming from LP did a little test - 
Installed a very recent version of sudo (1.7.4-7) in maverick, and after a restart see the exact same  as in natty.

So it's either the new intended behavior or how the newer sudo is working in ubuntu, but not just  in natty.
Will be interesting to see if this is how natty releases.

---

### Post by Quackers on 2011-02-04
Yes, the silence is deafening on that matter :wink:
As you have said previously, it may be the intended behaviour - they just don't want to say so :-)  We'll see - but hope for the best :wink:

---

### Post by rbrick49 on 2011-02-04
i opted for the new configuration no problems in that field here

---

### Post by mc4man on 2011-02-27
Turns out the 'new behavior' is due to the configure option debian/ubuntu is using for sudo 
--with-tty-tickets
So sudo can either be rebuilt w/ this instead (used on one 1 install, works fine
--without-tty-tickets
or adding this to sudoers  
```
Defaults !tty_tickets
```

Used this here on other install to get the old behavior and desired 1 time password (using a file in sudoers.d instead, that way if any issue could just delete the newly created file rather than messing with the sudoers file itself

```
sudo visudo -f /etc/sudoers.d/01_file
```
enter this line, Ctrl+o, enter, Crtl+x

```
Defaults !tty_tickets,env_reset,timestamp_timeout=-1
```

---

### Post by Quackers on 2011-02-27
Thanks mc4man. I had just run some updates and I noticed your last post. I made the change and rebooted, for good measure :-)  I then sudo update-grubbed and no password required - even on first use!  Then synaptic opened without the screen going dark and wanting the password. Happy, happy, happy :-)
Thanks.

---

### Post by mc4man on 2011-02-27
Quackers - 
slightly off the topic

Prior to fixing natty's current sudo (1.7.4+), I'd been using either the earlier natty package (1.7.2+) or mavericks current sudo package

When I upgraded back to natty's package, (_and before fixing the timeout_), I noticed that while synaptic opens quickly the mouse cursor continues to spin for 6 sec.'s or more. Synaptic is usable while the cursor is spinning, it's just an annoyance of sorts.
With the older sudo installed the cursor stop spinning almost immediatly after synaptic opens.

Curious if you've noticed/see this?

---

### Post by Quackers on 2011-02-27
My cursor always spins like that after opening synaptic. It's usually about 5 or 6 seconds, but can be as much as 10.

---

### Post by mc4man on 2011-02-27
> My cursor always spins like that after opening synaptic. It's usually about 5 or 6 seconds, but can be as much as 10.
Thanks for confirming..
Same here using the 1.7.4 sudo
Don't have a clue as to what's happening, if anything at all
Not going to bother bugging as synaptic is quite usable  while the cursor is spinning

---

### Post by Quackers on 2011-02-27
I find that too. Even while the thing is spinning I can still click on things.

---

### Post by mc4man on 2011-03-18
after using the both the current sudo (1.7.4p) with !tty_tickets and the previous 1.7.2 have decided the best choice here is to use 1.7.2p7 (w/ recent security update patch

It uses tty_tickets but gives the expected behavior w/ the admin. timeout and can be adjusted as we wished.

Also no mouse spin on synaptic or with gksudo nautilus

Can't see any reason to build the source on natty so am using the latest package from [maverick security updates]("http://packages.ubuntu.com/maverick-updates/sudo"). (1.7.2p7-1ubuntu2.1

With the sudoers or sudoers.d/ edit you need to enter once after login, after that good to go.

---

### Post by Quackers on 2011-03-18
Interesting, thanks for the update :-)

---

### Post by mc4man on 2011-03-18
If you decide to try the 1.7.2... package then remove the 
> !tty_tickets,
from your sudoers
You don't have to but I would

---

### Post by Quackers on 2011-03-18
Thanks. I'm happy as I am for the moment, but I'll bear this in mind :-)

---

### Post by nm_geo on 2011-03-19
> **Quackers said:**
> Thanks. I'm happy as I am for the moment, but I'll bear this in mind :-)

Quackers it never fails that I seem to try out some problem you have found.  My sudo reset timing is like yours for now I would just like Synaptic to not require it each time as often as we are updating..:)
 By the way my Lucid and Maverick versions work just fine with the -1. Think I might just try Mc4man's method.

---

### Post by Quackers on 2011-03-19
I'm currently using the method mc4man suggested in post #29, which seems to be working fine :-)
(synaptic doesn't ask any more :wink:)

---

### Post by nm_geo on 2011-03-19
> **Quackers said:**
> I'm currently using the method mc4man suggested in post #29, which seems to be working fine :-)
(synaptic doesn't ask any more :wink:)

Finally got around to putting in mc4man's suggestion works great and saves lots of keystrokes. Thanks

---

### Post by mc4man on 2011-03-19
Just a bit of a recap and why I don't currently use post 29 here, using instead a 1.7.2... sudo

The current 1.7.4.. sudo only uses the admin. timeout/timestamp on current open instance
The prior versions of sudo used the timeout on any instance opened during the set timeout value

There are 2+ unknowns (to me) involved , whether they're positive, negative or irrelevant doesn't much matter, I just don't like unknowns.  - 

Both sudos are default configured with tty_tickets, but the effect is different as seen. (why I don't know, and why ubuntu uses that option I don't know

With current 1.7.4 sudo, when using synaptic or gksu nautilus the cursor spins on for some time ( what's going on during this I don't know

Additionally on the cursor spin - 
with the current 1.7.4 when using gksu nautilus the first time the cursor spin goes on for some time, after that there is none. With the 1.7.4 sudo and !tty_tickets it spins each time used (I don't use gksudo nautilus much but still..

So while i may end up using 1.7.4 as shown in  post 29, for the moment using the 1.7.2 sudo  because it eliminates all the unknowns to me and gives the old wanted behavior
(ie. - uses ubuntu's default option --with-tty_tickets
       - no cursor spin ever

Some apologies about the "unknowns' - at least I didn't go this far - 
[The Unknown]("http://www.slate.com/id/2081042/")
> As we know,
There are known knowns.
There are things we know we know.
We also know
There are known unknowns.
That is to say
We know there are some things
We do not know.
But there are also unknown unknowns,
The ones we don't know
We don't know.

&#8212;Feb. 12, 2002, Department of Defense news briefing


---

