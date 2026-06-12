---
title: "How to create Live CD with v0.24"
date: 2011-02-09
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-09
I just downloaded latest Mythbuntu 10.10 (64bit) and Mythbuntu 10.10 (32bit) two weeks ago. Both of these Live CDs use MythTV 0.23-fixes (revision 26437)

But today I upgraded my desktop from 0.23-fixes to 0.24-153-g6318d52. The desktop works fine. Both FrontEnd and BackEnd work fine.

So now my system has the following components:
mythbuntu 10.10
xfce 4.6.2
mythtv 0.24-153

However, this upgrade now causes another unforeseen problem. I can't use the LiveCD to make my laptop act as a frontend b/c the versions don't match.

How do I create a Mythbuntu LiveCD using what I've got currently installed on the desktop which is the latest version of MythTV 0.24 and ubuntu 10.10 and xfce 4.6.2?

---

### Post by nickrout on 2011-02-09
why not install a frontend on the laptop?

Also google found me this very quickly, you really should try it!

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by nhtrader on 2011-02-10
> **nickrout said:**
> why not install a frontend on the laptop?

Also google found me this very quickly, you really should try it!

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)



1. b/c it doesn't play nice with the newly upgraded BE.

I'm trying to install it but thankfully I didn't yet. My first step was to simply boot from the LiveCD in an attempt to connect to my backend. Basically, I wanted a successful test drive. But it failed.

I booted from the Live CD (mythbuntu 10.10-32bit-0.23-fixes-rev26437) and got to the Try Mythbuntu Button - selected it.
It installed successfully using HP-zv5220us which is a 6 yr old laptop (unlike my new laptop Asus G60JX which failed - corrupt screen)

Then I went to Apps|Multimedia|Mythbuntu LiveCD Frontend
A prompt appeared...
Selected "TestConnection" - ERROR MESSAGE
"Mismatched schema version for 'DBSchemaVer': database speaks version 1264, we speak version 1254

So there's a compatibility error btwn the latest LiveCD(0.23-fixes) and those of us that have upgraded to 0.24. I paid the price for upgrading the desktop today which is now using v0.24-153-g6318d52 for both FE and BE.


This is why I posed the question, how to create a LIVECD using 0.24

2. As for googling, well I spent3 hours at it and found at least 6 different legitimate methods. Each one more daunting than the next. Hence, I posed this question with the hope that ...
A. someone knows of an existing LiveCD containing v0.24 (least amount of work)
B. someone has tread this path b4 (specifically a mythbuntu user) and is willing to share some tips and tweaks. 
C. someone would share what they considered to be the easiest method.

---

### Post by tgm4883 on 2011-02-10
> **nhtrader said:**
> 1. b/c it doesn't play nice with the newly upgraded BE.

I'm trying to install it but thankfully I didn't yet. My first step was to simply boot from the LiveCD in an attempt to connect to my backend. Basically, I wanted a successful test drive. But it failed.

I booted from the Live CD (mythbuntu 10.10-32bit-0.23-fixes-rev26437) and got to the Try Mythbuntu Button - selected it.
It installed successfully using HP-zv5220us which is a 6 yr old laptop (unlike my new laptop Asus G60JX which failed - corrupt screen)

Then I went to Apps|Multimedia|Mythbuntu LiveCD Frontend
A prompt appeared...
Selected "TestConnection" - ERROR MESSAGE
"Mismatched schema version for 'DBSchemaVer': database speaks version 1264, we speak version 1254

So there's a compatibility error btwn the latest LiveCD(0.23-fixes) and those of us that have upgraded to 0.24. I paid the price for upgrading the desktop today which is now using v0.24-153-g6318d52 for both FE and BE.


This is why I posed the question, how to create a LIVECD using 0.24

2. As for googling, well I spent3 hours at it and found at least 6 different legitimate methods. Each one more daunting than the next. Hence, I posed this question with the hope that ...
A. someone knows of an existing LiveCD containing v0.24 (least amount of work)
B. someone has tread this path b4 (specifically a mythbuntu user) and is willing to share some tips and tweaks. 
C. someone would share what they considered to be the easiest method.

If it's a one time test, then just install the mythbuntu-repos package and upgrade the livecd frontend to the same version as the backend.

If it's for extended use, create a bootable usb key, and upgrade the mythtv frontend package using the mythbuntu-repos package

---

### Post by nhtrader on 2011-02-10
> **tgm4883 said:**
> If it's a one time test, then just install the mythbuntu-repos package and upgrade the livecd frontend to the same version as the backend.

If it's for extended use, create a bootable usb key, and upgrade the mythtv frontend package using the mythbuntu-repos package


Please forgive me. I'm confused. Again, I'm trying to get mythtv v0.24 FE on my older winxp laptop (no other OS installed on this laptop) using a LiveCD

I took a crack at it and here's what I just did...

I got my Mythbuntu 10.10 (32bit) LiveCD(v23-fixes) and put it into my old laptop's CD-ROM
Turned off laptop.
Turned on laptop|selected boot menu|selected CD-ROM|selected Try Mythbuntu|loaded trial install
Opened terminal and use commands
sudo su
apt-get update

Then opened firefox and went to mythbuntu.org/auto-builds 
selected install Mythbuntu repos|selected use Gdebi to install|followed prompts|completed install

back to terminal mode
sudo su
mythfrontend
Prompt: You must be a member of the "mythtv" group before starting any mythtv applications. Would you like to automatically be added to the group? (note: sudo access required) select yes

Prompt: For the changes to take effect, your current login session will have to be restarted. Save all work and then press OK to restart your session. select yes

Failed to receive a reply from the session manager. The name org.xfce.SessionManager was not provided by any .service files. select close.


Sorry, I don't know how to  "just install the mythbuntu-repos package and upgrade the livecd frontend to the same version as the backend". Would you mind explaining this?

---

### Post by nickrout on 2011-02-10
> **nhtrader said:**
> Please forgive me. I'm confused. Again, I'm trying to get mythtv v0.24 FE on my older winxp laptop (no other OS installed on this laptop) using a LiveCD

I took a crack at it and here's what I just did...

I got my Mythbuntu 10.10 (32bit) LiveCD(v23-fixes) and put it into my old laptop's CD-ROM
Turned off laptop.
Turned on laptop|selected boot menu|selected CD-ROM|selected Try Mythbuntu|loaded trial install
Opened terminal and use commands
sudo su
apt-get update

Then opened firefox and went to mythbuntu.org/auto-builds 
selected install Mythbuntu repos|selected use Gdebi to install|followed prompts|completed install

back to terminal mode
sudo su
mythfrontend
Prompt: You must be a member of the "mythtv" group before starting any mythtv applications. Would you like to automatically be added to the group? (note: sudo access required) select yes

Prompt: For the changes to take effect, your current login session will have to be restarted. Save all work and then press OK to restart your session. select yes

Failed to receive a reply from the session manager. The name org.xfce.SessionManager was not provided by any .service files. select close.


Sorry, I don't know how to  "just install the mythbuntu-repos package and upgrade the livecd frontend to the same version as the backend". Would you mind explaining this?

why sudo su mythfrontend - that will run it as root, which is not what you want.

This approach will only updfate you until a reboot - but it gives you a chance to try out 0.24 on that hardware.

Also there might be other live cd's out there that have 0.24 - take a look at mythdora - theres nothing to stop you trying a mythdora 0.24 live cd (assuming such a thing exists) against a *buntu 0.24 backend

---

### Post by nickrout on 2011-02-10
Actually I speak to soon. Latest mythdora seems to have 0.23 as well.

---

### Post by tgm4883 on 2011-02-10
> **nhtrader said:**
> Please forgive me. I'm confused. Again, I'm trying to get mythtv v0.24 FE on my older winxp laptop (no other OS installed on this laptop) using a LiveCD

I took a crack at it and here's what I just did...

I got my Mythbuntu 10.10 (32bit) LiveCD(v23-fixes) and put it into my old laptop's CD-ROM
Turned off laptop.
Turned on laptop|selected boot menu|selected CD-ROM|selected Try Mythbuntu|loaded trial install
Opened terminal and use commands
sudo su
apt-get update

Then opened firefox and went to mythbuntu.org/auto-builds 
selected install Mythbuntu repos|selected use Gdebi to install|followed prompts|completed install

back to terminal mode
sudo su
mythfrontend
Prompt: You must be a member of the "mythtv" group before starting any mythtv applications. Would you like to automatically be added to the group? (note: sudo access required) select yes

Prompt: For the changes to take effect, your current login session will have to be restarted. Save all work and then press OK to restart your session. select yes

Failed to receive a reply from the session manager. The name org.xfce.SessionManager was not provided by any .service files. select close.


Sorry, I don't know how to  "just install the mythbuntu-repos package and upgrade the livecd frontend to the same version as the backend". Would you mind explaining this?

[LIST=1]
[*]Boot up Live CD
[*]Go to web, download and install mythbuntu-repos package
[*]Open terminal
[*]sudo apt-get update
[*]sudo apt-get install mythtv-frontend
[*]Start mythfrontend
[/LIST]

As said before, don't start the frontend as root.

---

### Post by nhtrader on 2011-02-10
> **nickrout said:**
> why sudo su mythfrontend - that will run it as root, which is not what you want.

This approach will only updfate you until a reboot - but it gives you a chance to try out 0.24 on that hardware.

Also there might be other live cd's out there that have 0.24 - take a look at mythdora - theres nothing to stop you trying a mythdora 0.24 live cd (assuming such a thing exists) against a *buntu 0.24 backend


We're not understanding each other. 

I'm sorry, I don't know what you mean. What I just did; didn't do anything. I went through those steps but I can't access mythfrontend from terminal mode. Secondly accessing frontend from Apps Menu still produces the "Test Connection" error: "Mismatched schema version for 'DBSchemaVer': database speaks version 1264, we speak version 1254.  So while I managed to use Gdebi to install mythbuntu-repos succesfully, nothing changed.

You are assuming that the update (mythbuntu-repos) was successful and it wasn't. I switched to root b/c entering terminal mode produced this...

ubuntu@ubuntu:~$mythfrontend
Prompt: You must be a member of the "mythtv" group before starting any  mythtv applications. Would you like to automatically be added to the  group? (note: sudo access required) selected yes

Prompt: For the changes to take effect, your current login session will  have to be restarted. Save all work and then press OK to restart your  session. selected yes

 Log out ubuntu : options (logout, restart, shutdown, suspend,hibernate,cancel)

I'm sure you realize that once I leave  this session all memory is lost. So I'm stuck.

So again, using only a LiveCD on a windows only PC what did tgm4883 mean? (I do not want to install mythbuntu onto my windows laptop HDD at this time)

---

### Post by tgm4883 on 2011-02-10
> **nhtrader said:**
> We're not understanding each other. 

I'm sorry, I don't know what you mean. What I just did; didn't do anything. I went through those steps but I can't access mythfrontend from terminal mode. Secondly accessing frontend from Apps Menu still produces the "Test Connection" error: "Mismatched schema version for 'DBSchemaVer': database speaks version 1264, we speak version 1254.  So while I managed to use Gdebi to install mythbuntu-repos succesfully, nothing changed.

You are assuming that the update (mythbuntu-repos) was successful and it wasn't. I switched to root b/c entering terminal mode produced this...

ubuntu@ubuntu:~$mythfrontend
Prompt: You must be a member of the "mythtv" group before starting any  mythtv applications. Would you like to automatically be added to the  group? (note: sudo access required) selected yes

Prompt: For the changes to take effect, your current login session will  have to be restarted. Save all work and then press OK to restart your  session. selected yes

 Log out ubuntu : options (logout, restart, shutdown, suspend,hibernate,cancel)

I'm sure you realize that once I leave  this session all memory is lost. So I'm stuck.

So again, using only a LiveCD on a windows only PC what did tgm4883 mean? (I do not want to install mythbuntu onto my windows laptop HDD at this time)

See post #8

---

### Post by nickrout on 2011-02-10
A post to the mailing list reveals that this live cd has 0.24, I am downloading now to check it out:

[ftp://ftp.knoppmyth.net/R7/R7.00.01/LinHES_R7.00.01.iso](ftp://ftp.knoppmyth.net/R7/R7.00.01/LinHES_R7.00.01.iso)

[http://mysettopbox.tv/](http://mysettopbox.tv/)

---

### Post by tgm4883 on 2011-02-10
> **nickrout said:**
> A post to the mailing list reveals that this live cd has 0.24, I am downloading now to check it out:

[ftp://ftp.knoppmyth.net/R7/R7.00.01/LinHES_R7.00.01.iso](ftp://ftp.knoppmyth.net/R7/R7.00.01/LinHES_R7.00.01.iso)

[http://mysettopbox.tv/](http://mysettopbox.tv/)

As far as I can tell, that hasn't been released yet. So as long as thats an option, the 11.04 ISO has 0.24 on it as well.
[http://cdimage.ubuntu.com/mythbuntu/daily-live/current/](http://cdimage.ubuntu.com/mythbuntu/daily-live/current/)

Again, it's unreleased, so it may be a bit buggy

---

### Post by nhtrader on 2011-02-10
> **tgm4883 said:**
> 
[LIST=1]
[*]Boot up Live CD
[*]Go to web, download and install mythbuntu-repos package
[*]Open terminal
[*]sudo apt-get update
[*]sudo apt-get install mythtv-frontend
[*]Start mythfrontend
[/LIST]

As said before, don't start the frontend as root.

Thank you for being explicit. Just tried your instructions. Sorry to say that these steps didn't work. These steps produced the same errors cited earlier.

After mythfrontend failed (it produced the prompt sequence that ended with Log Out), I also tried to start FE using the Apps Menu|Mythbuntu Live CD Frontend . This produced the same Test Connection Error.


Sorry, things apparently don't work like they might have in earlier versions.

---

### Post by nickrout on 2011-02-10
try opening a terminal, after the upgrade cycle, and type ```
mythfrontend --version
dpkg -l mythtv-frontend
```

Report back :)

Also if that shows 0.24 versions, try simply starting mythfrontend from the terminal:

```
mythfrontend
```

---

### Post by AlecJ on 2011-02-11
I have a solution for you.

install onto a USB stick just a frontend only and boot from that when required, this can be upgraded

---

### Post by nhtrader on 2011-02-11
> **AlecJ said:**
> I have a solution for you.

install onto a USB stick just a frontend only and boot from that when required, this can be upgraded

Good Idea. I'll try this some time in the future. Right now I'd like to iron out a few things b4 I attempt this. Something else new for me to learn. Not ready yet.

---

### Post by nhtrader on 2011-02-11
> **nickrout said:**
> try opening a terminal, after the upgrade cycle, and type ```
mythfrontend --version
dpkg -l mythtv-frontend
```Report back :)

Also if that shows 0.24 versions, try simply starting mythfrontend from the terminal:

```
mythfrontend
```


For clarity's sake I'm using LiveCD (Mythbuntu 10.10 (32bit) MythTV v0.23-fixes rev-26437 on a winXP only PC.
Also worth noting is that I used Update Manager to update my MythTV Backend. 
A new build was released last night and I installed v0.24-159-gv259732
NOTE: I figured I should check b4 trying to upgrade LiveCD. I need network protocols to match.


turned off Laptop (HP-zv5220us: AMD Sempron 3000+ 1.2GbRAM)
Turned on laptop
pressed ESC to enter boot menu
inserted LiveCD
selected CD-ROM | <E>
Prompt: selected "Try Mythbuntu"
used firefox to goto [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)
selected link to install mythbuntu-repos
followed prompts: use Gdebi to install
select install package
would you like to update the mythtv updates repository? checked
which version would you like to update to? selected 0.24
which repo would you like to use? selected ppa
would you like to activate the mythbuntu updates ppa? checked
Please use a package manager to finish updating.
please open update-manager and clock Check and the install updates as you normally would.
enter terminal mode
sudo apt-get update
sudo apt-get install mythtv-frontend (followed prompts)
mythfrontend --version
Prompt appears: You must a member of the "mythtv" group before starting any mythtv applications.
Would you like to automatically be added to the group? (NOTE: sudo access required) selected yes
Next prompt: 
For the changes to take effect, your current login session will have to be restarted.
Save all work and then press OK to restart your session.

This time I selected Logout. (prior to this I've always stopped here and shut off the laptop)
username: ubuntu
password: (default=no entry/empty/blank/none)
Back into xfce space
enter terminal mode
ubuntu@ubuntu:~$mythfrontend --version
MythTV version: v0.24-159-gb259732
MythTV branch: fixes/0.24
Network Protocol: 63
Library API: 0.24.20101129-1

Hurray progress. 

dpkg -l mythtv-frontend
mythtv-frontend 2:0.24.0+fixes

mythfrontend <E> ( now working. I see Main Menu. )

But error message apears: Your time zone in the frontend doesn't match the backend. selected OK and FE dies.

The key was to log out and back in again as user: ubuntu

Now I have to figure how to change the time zone.


(Time required for this = 45 minutes and I still didn't configure it yet for my backend)

---

### Post by tgm4883 on 2011-02-11
> **nhtrader said:**
> For clarity's sake I'm using LiveCD (Mythbuntu 10.10 (32bit) MythTV v0.23-fixes rev-26437 on a winXP only PC.
Also worth noting is that I used Update Manager to update my MythTV Backend. 
A new build was released last night and I installed v0.24-159-gv259732
[B]NOTE: I figured I should check b4 trying to upgrade LiveCD. I need network protocols to match.
[/B]

Not necessary, 0.24 is compatible with other 0.24. Doesn't hurt though

> **nhtrader said:**
> 
turned off Laptop (HP-zv5220us: AMD Sempron 3000+ 1.2GbRAM)
Turned on laptop
pressed ESC to enter boot menu
inserted LiveCD
selected CD-ROM | <E>
Prompt: selected "Try Mythbuntu"
used firefox to goto [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)
selected link to install mythbuntu-repos
followed prompts: use Gdebi to install
select install package
would you like to update the mythtv updates repository? checked
which version would you like to update to? selected 0.24
which repo would you like to use? selected ppa
would you like to activate the mythbuntu updates ppa? checked
Please use a package manager to finish updating.
please open update-manager and clock Check and the install updates as you normally would.
enter terminal mode
sudo apt-get update
sudo apt-get install mythtv-frontend (followed prompts)
mythfrontend --version
Prompt appears: You must a member of the "mythtv" group before starting any mythtv applications.
Would you like to automatically be added to the group? (NOTE: sudo access required) selected yes
Next prompt: 
For the changes to take effect, your current login session will have to be restarted.
Save all work and then press OK to restart your session.

This time I selected Logout. (prior to this I've always stopped here and shut off the laptop)


Yes, if you shut off the laptop then you lose the upgraded package you did. Don't blame the software if you can't follow instructions.

> **nhtrader said:**
> 
username: ubuntu
password: (default=no entry/empty/blank/none)
Back into xfce space
enter terminal mode
ubuntu@ubuntu:~$mythfrontend --version
MythTV version: v0.24-159-gb259732
MythTV branch: fixes/0.24
Network Protocol: 63
Library API: 0.24.20101129-1

Hurray progress. 

dpkg -l mythtv-frontend
mythtv-frontend 2:0.24.0+fixes

mythfrontend <E> ( now working. I see Main Menu. )

But error message apears: Your time zone in the frontend doesn't match the backend. selected OK and FE dies.

The key was to log out and back in again as user: ubuntu

Now I have to figure how to change the time zone.


(Time required for this = 45 minutes and I still didn't configure it yet for my backend)

There were only 6-7 real steps in there and should have taken about 15 minutes to get to the point that you are at. If that took you 45 minutes you likely are doing something wrong

[LIST=1]
[*]Boot Live CD (2 minutes)
[*]Download, Install & Configure mythbuntu-repos package (5-7 minutes)
[*]apt-get update && apt-get install mythtv-frontend (2-5 minutes)
[*]start mythfrontend (10 seconds)
[*]logout and back into frontend (not reboot) (2 minutes)
[*]start mythfrontend (10 seconds)
[/LIST]

---

### Post by nickrout on 2011-02-11
On the frontend run ```
TZ=Pacific/Auckland mythfrontend
```

Inserting the timezone on your backend (the terminal where you run mythfrontend will have given you a message like this showing what the backend is set to:

> 2011-02-11 19:54:24.997 Detected time zone settings:
    **Master: Zone ID: 'Pacific/Auckland',** UTC Offset: '46800', Current Time: '2011-02-12T08:54:24'
     Local: Zone ID: 'NZDT', UTC Offset: '0', Current Time: '2011-02-11T19:54:24'


---

### Post by nhtrader on 2011-02-11
> **tgm4883 said:**
> Not necessary, 0.24 is compatible with other 0.24. Doesn't hurt though



Yes, if you shut off the laptop then you lose the upgraded package you did. Don't blame the software if you can't follow instructions.



There were only 6-7 real steps in there and should have taken about 15 minutes to get to the point that you are at. If that took you 45 minutes you likely are doing something wrong

[LIST=1]
[*]Boot Live CD (2 minutes)
[*]Download, Install & Configure mythbuntu-repos package (5-7 minutes)
[*]apt-get update && apt-get install mythtv-frontend (2-5 minutes)
[*]start mythfrontend (10 seconds)
[*]logout and back into frontend (not reboot) (2 minutes)
[*]start mythfrontend (10 seconds)
[/LIST]


1. Glad to learn that all changes to 0.24 are compatible. This was not the case for 0.23, so I wouldn't have assumed this as a Newbie. Upgrading made sense.

2. As a newbie, again I didn't know if logging out would erase everything that I had done in a session that is using a virtual disk drive and virtual memory. Now I know that I can do that. Remember I've done this process 3 times now - each time 1 hour.

3. Your download times are awesome. For me they are twice as long. Plus I'm running a single core CPU circa 2005 - it's slower.

4. As for changing the time zone...

terminal commands:
sudo su
dpkg-reconfigure tzdata (follow prompts)
exit (root)
mythfrontend (error msg does not appear! hurray!)

I went into setup menu and discovered that all of the info (ip address, user name,  database name, password) was inserted. I didn't even have to change one  setting.
Back to Main Menu. Select TV | TV recordings
IT WORKS. I watched a TV recording. Sound and Video worked!

Now this completes this test of the old laptop. But the corrupt screen remains with the new laptop. I guess I'm going to make my own LiveCD or USB stick with the new build 0.24-159

Now on to learning how to create/use USB stick.

---

### Post by nickrout on 2011-02-11
> **nhtrader said:**
> 1. Glad to learn that all changes to 0.24 are compatible. This was not the case for 0.23, so I wouldn't have assumed this as a Newbie. Upgrading made sense.

2. As a newbie, again I didn't know if logging out would erase everything that I had done in a session that is using a virtual disk drive and virtual memory. Now I know that I can do that. Remember I've done this process 3 times now - each time 1 hour.

3. Your download times are awesome. For me they are twice as long. Plus I'm running a single core CPU circa 2005 - it's slower.

4. As for changing the time zone...

terminal commands:
sudo su
dpkg-reconfigure tzdata (follow prompts)
exit (root)
mythfrontend (error msg does not appear! hurray!)

I went into setup menu and discovered that all of the info (ip address, user name,  database name, password) was inserted. I didn't even have to change one  setting.
Back to Main Menu. Select TV | TV recordings
IT WORKS. I watched a TV recording. Sound and Video worked!

Now this completes this test of the old laptop. But the corrupt screen remains with the new laptop. I guess I'm going to make my own LiveCD or USB stick with the new build 0.24-159

Now on to learning how to create/use USB stick.

Simply use it as the target drive when using the install program. Even unplug the harddrive from the machine to make sure you don't over-write it by mistake.

But dual booting is fine too, but perhaps you don't have enough disk space?

---

### Post by tgm4883 on 2011-02-11
> **nhtrader said:**
> 1. Glad to learn that all changes to 0.24 are compatible. **This was not the case for 0.23, so I wouldn't have assumed this as a Newbie.** Upgrading made sense.


Glad it's working for you. Just a quick note about the above comment. This was most certainly the case for 0.23(.0) as well. You either

A) Were using another distribution that didn't specify the difference between 0.23.0 and 0.23.1

or

B) Had one of your clients using 0.23.0 and the other using 0.23.1.

or 

C) Just happened to update during the short period that a 0.23.1 build made it into the 0.23.0 PPA


All 0.23.0 versions are compatible with other 0.23.0 versions. (0.23.1 is compatible with other 0.23.1 builds, 0.24.0 builds are compatible with other 0.24.0 builds, etc).

---

### Post by AlecJ on 2011-02-12
> **nickrout said:**
> Simply use it as the target drive when using the install program. Even unplug the harddrive from the machine to make sure you don't over-write it by mistake.

But dual booting is fine too, but perhaps you don't have enough disk space?

Yes _[COLOR=Black]DO[/COLOR]_ unplug, I tried this without unplugging the hard drive's and it rather upset Grub on my daul boot laptop. Was unable to boot without the USB plugged in. The only or fasted way was to boot but selecting my normal ubuntu boot, unplugging USB and then reinstalling Grub.

A simple but superb solution, Thank you.

I'm going to try again now grub is fixed.

---

### Post by AlecJ on 2011-02-12
Looks like a 2Gb Key is too small for all the upgrades, going to try a 4Gb

---

### Post by nickrout on 2011-02-12
> **AlecJ said:**
> Looks like a 2Gb Key is too small for all the upgrades, going to try a 4Gb

You could mount /var/cache/apt/archives elsewhere [1] to make enough room.

As a quick and dirty method to make sure each frontend doesn't have to separately download updates, I first update the always on backend. Then on each frontend ```
sudo sshfs media://var/cache/apt/archives /var/cache/apt/archives/ -o nonempty
``` where media id the backend. The only problem is that it's rather insecure - you need a root password set up on the backend and use it when booting.

[1] to another drive or over a network.

---

### Post by nhtrader on 2011-02-14
> **tgm4883 said:**
> Glad it's working for you. Just a quick note about the above comment. This was most certainly the case for 0.23(.0) as well. You either

A) Were using another distribution that didn't specify the difference between 0.23.0 and 0.23.1

or

B) Had one of your clients using 0.23.0 and the other using 0.23.1.

or 

C) Just happened to update during the short period that a 0.23.1 build made it into the 0.23.0 PPA


All 0.23.0 versions are compatible with other 0.23.0 versions. (0.23.1 is compatible with other 0.23.1 builds, 0.24.0 builds are compatible with other 0.24.0 builds, etc).

I'm glad to learn that all 0.23.0 versions are compatible with other 0.23.0 versions. 

In my case, I tried to connect to my BE which was a 0.23.0-fixes rev26437. Then I loaded a 0.23.0-fixes FE "MythTV for Windows" on a Win7 PC. This produced a network protocol error. One was using protocol 2356 and the other was using 56. So this I why for me 0.23 didn't interact well.

Figures I found the problem scenario/combination.

---

### Post by nhtrader on 2011-02-14
> **AlecJ said:**
> Looks like a 2Gb Key is too small for all the upgrades, going to try a 4Gb

I'm ordering an 8Gb myself. Should get it by end of week.

---

### Post by tgm4883 on 2011-02-14
> **nhtrader said:**
> I'm glad to learn that all 0.23.0 versions are compatible with other 0.23.0 versions. 

In my case, I tried to connect to my BE which was a 0.23.0-fixes rev26437. Then I loaded a 0.23.0-fixes FE "MythTV for Windows" on a Win7 PC. This produced a network protocol error. One was using protocol 2356 and the other was using 56. So this I why for me 0.23 didn't interact well.

Figures I found the problem scenario/combination.

0.23.0 used protocol version 56
0.23.1 used 23056

The last build of 0.23.0 for Ubuntu was 0.23.0++fixes25362 (provided in the Mythbuntu repos). The problem build was 
0.23.0+fixes25423


In your case, you either

A) are confused about the version you had installed, because 0.23.0-fixes26437 is impossible from the Mythbuntu repositories

B) The MythTV for Windows that you were using lied about the version number it was on.

---

### Post by nickrout on 2011-02-14
To be fair the transition from 0.23 to 0.23.1 was a stuff up, and should not have been necessary. There was a protocol change, which necessitated a sudden and confusing shift from 0.23 to 0.23.1. There is not usually a protocol change unless you bump a whole version (eg 0.23 to 0.24) in which case people are aware of it and can plan a smooth transition by upgrading all machines at once. As nhtrader was not around at the time it's no wonder he is confused. Hopefully it will not happen again.

And yes, the win version may not have been labelled right, or nht may not have appreciated the difference between 0.23 and 0.23.1, or many other things could be confusing any and all of us.

Anyway it is historical now. I'll stop rambling.

---

### Post by nhtrader on 2011-02-18
Well, I got my 8Gb USB stick/flash drive and after many hours of googling, I decided to use this package: "remastersys"

It can be used to 1. backup everything; 2. save only user data; and most importantly, it can be used to create a custom ubuntu LiveCD from the user's installation. 

This is what I wanted. I didn't want to create a custom LiveCD using an existing LiveCD *.iso b/c the current version of Mythbuntu 10.10 installs MythTV 0.23. I want a Mythbuntu LiveCD with the current version of MythTV which is 0.24-181-g2b7036f

Fortunately if took me a few days to stumble upon "remastersys" b/c this week MythTV had 3 revisions (159, 179, and 181). So I didn't have to do this 3 times.

So after following the installation instructions found at:
    [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

I started "remastersys" and selected the option "dist"

Sorry to say it didn't create a simple LiveCD. It created a complete backup of my system which is now up to 400Gb.

Needless to say, the first attempt at creating a LiveCD with MythTV 0.24-181 failed.

I'll try again tomorrow.

---

### Post by nickrout on 2011-02-18
Say again:

Use the 10.10 cd, boot it and choose install. Choose the 8G flash drive as the target drive to install to.

Once installed on the flash drive, boot from the flash drive.Upgrade your packages using mythbuntu-repos. Thereafter boot from the flash drive when you want to use myth.

---

### Post by nhtrader on 2011-02-20
> **nickrout said:**
> Say again:

Use the 10.10 cd, boot it and choose install. Choose the 8G flash drive as the target drive to install to.

Once installed on the flash drive, boot from the flash drive.Upgrade your packages using mythbuntu-repos. Thereafter boot from the flash drive when you want to use myth.

Two things.

1. This method seems simple enough, although it requires that I spend the time to redo/reinstall many extra packages that I have already installed. I spent the past 3 weeks customizing and upgrading, so I don't want to this all over again. So I was interested in finding a method that would take my current system and create a LiveCD from this.

2. With that said, I decided what the heck. I decided to try your method.

Now I'm in trouble. The only problem now is that I'm stuck. 

a. I followed your advice. rebooted system using my current Mythbuntu 10.10 LiveCD
b. I inserted my USB stick
c. I selected the USB as the destination for the install.
d. shutdown computer. off.
e. removed USB stick (b/c I wanted to check something on my current system's HDD)
f.  turned on computer
g. I'm stuck with the following error msg: 
     no such device 9a32b94e-xxxx-xxxx-xxxx-xxxxxxxxx
    grub rescue>

h. if I turn offed computer and reinserted usb stick and turned computer on
     Now I see:  GNU GRUB version 1.98+201008045ubuntu3

and I need to select one of many choices to boot up.


So what do I do now. Apparently installing the USB stick didn't work out so well.

How can I get my system to run without the USB stick inserted? (it's acting like a lock. I start it without it.)

What do I do with the prompt: grub rescue>

How do I fix this?

---

### Post by nhtrader on 2011-02-20
The solution to this problem of needing the USB stick to boot is to ...

1. find a way to get the system to boot up off of the HDD.
2. once system is running (with USB stick inserted) using the HDD, remove USB stick.
3. Use Synaptic Package Manager
4. search for grub
5. select grub-pc (right click, and mark for re-installation)
6. press button "apply"
7. shutdown
8. reboot. fixed. USB stick no longer required to get system started.


Why this happened I don't know. But apparently this has occurred often enough.

---

### Post by nickrout on 2011-02-20
possibly you missed the post telling you this might happen if you didn't unplug the hard drive before installing (and, yes, I forgot to add it to my last post)

Glad you fixed it.

All well now?

---

### Post by nhtrader on 2011-02-20
BEWARE: the USB stick's copy of Mythbuntu didn't work. And more importantly, it corrupted another Windows PC when I inserted the USB stick and attempted to use it.

Fortunately, Win7 built-in and automatic system rescue was able to repair MBR and reboot. I wouldn't have known what to do.

Lastly, I deleted the USB stick's contents and will try again. 

What a mess this caused. That's why us newbie's hate experimenting. It gets us into trouble.

---

### Post by nickrout on 2011-02-20
what do you mean corrupted? Simply running inserting a usb stick and booting linux will not touch the windows partition, or the MBR.

---

### Post by nhtrader on 2011-02-20
> **nickrout said:**
> what do you mean corrupted? Simply running inserting a usb stick and booting linux will not touch the windows partition, or the MBR.

That's what I thought, but apparently when I inserted the USB stick  into my Win7 PC and attempted to use it as the boot device in my Win7 machine, and it failed to load the Mythbuntu OS. It did something to my Win7 HDD.

When I noticed that the install was hanging, I shutdown the Win7 PC and removed the stick. Then rebooted Win7 PC and Win7 detected a corrupted state and displayed the system rescue prompt from which I selected to automatically fix/repair the MBR problem.

Note that when my Mythbox's grub was corrupted, it would not boot up without the USB stick. The USB stick acted like a hardware-security-key. The system would not start without it. But once I reinstalled the grub-pc package it removed the connection btwn the HDD and the USB stick. I don't know what's going on, but all I can do is describe the events. And fortunately, I got past this problem without losing any data/recordings, or my Win7 stuff.

---

### Post by nickrout on 2011-02-20
I think something like this is happening:

1. when you boot the live cd it detects two hard drives - the USB one and the internal one. It detects them in an arbitrary order. 

2. During install it places grub on the MBR of the internal disk, but grub also needs to access files on a hard drive, and the MBR is hard wired to point to a particular drive. It does this in terms of pointing to drive N, where N is the number of the drive in the order they are detected. It will point to the USB drive at that's where the rest of the grub files are.

3. If you reboot without the USB drive, the drives are detected differently and N on the MBR points to the wrong place. 

Or something like that.

During the install, just before it asks you to confirm everything and do the actual install, there is an option I think called "advanced" which gives you a chance to install grub to a different drive. Where you are not truly 'dual booting' you would be better to put grub on the mbr of the USB drive.

---

### Post by nhtrader on 2011-02-20
> **nickrout said:**
> 
During the install, just before it asks you to confirm everything and do the actual install, there is an option I think called "advanced" which gives you a chance to install grub to a different drive. Where you are not truly 'dual booting' you would be better to put grub on the mbr of the USB drive.

Good to know for the future and as always, the devil's in the details. I've made good progress in peeling this onion, one layer at a time.

---

### Post by nhtrader on 2011-02-20
SUMMARY

Here's how I created a custom LiveCD
======================================

I started with a standard Mythbuntu 10.10 (32bit) LiveCD
which started with...
ubuntu 10.10
xfce 4.6.2
MythTV 0.23.0-fixes

Then I used "update manager" to upgrade all packages:
ubuntu 10.10 - upgraded approx. 180 packages
xfce 4.8.0 - forced upgrade to latest version
MythTV0.24-184 -forced upgrade to latest version
(use MythTV Control Centre to select repositories button. enable activation of mythtv updates repository
select version 0.24 from dropdown box, select PPA from dropdown box. Press button Apply.)

Then added a few convenience packages:
Libre 3.3.0 (new office suite)
evince (multi-format document viewer)
geany (text editor)
kompozer (HTML editor)
xfburn (cd/dvd burner)
gimp (image editor - used to convert screenshots from large sized png to jpeg)
screenshot (screenshot capture program)
opera (webbrowser)
skype (video phone)
Adobe Reader 9 (pdf reader)
remastersys (LiveCD creator)
usb-creator-gtk (usb transfer utility)
cups (printer utilitiy)
cups-bsd (required to print when using Adobe Reader 9)



LiveCD instructions:
=====================
NOTES:
The Backend needs to be off when making the LiveCD. Kill the running process, or else it will interfere with the creation of the LiveCD. (maybe somebody knows a more elegant method to turn it on/off and will post this info)

MOVE MEDIA FILES:  Also, this process is best done before you amass recordings (*.mpg). Basically, this will copy your recordings into your LiveCD. However, to avoid this you can move your recordings from /var/lib/mythtv/* to /home/mythv/* . This of course sounds simple but isn't so easily achieved. (And I should add that you shouldn't be moving files while your are actively recording one.) Simply put, these commands will not work as expected ...
sudo su
mv /var/lib/mythtv /home/mythtv

The commands will produce the following results b/c /home/mythtv isn't empty. Your new path is: /home/mythtv/mythtv/*
Notice the double "/mythtv/mythtv" 

Next you need to change all of the parameters that specify a path in the FrontEnd and BackEnd. Then you're good to go. You shouldn't have to change any thing else (MYSQL database parameters). MythTV's database will remain intact and all references should still work.

I didn't even have to change permissions b/c I started the process as a "root" user. Moving the files as "root" meant that the original username and groupname remained intact.

Now that you moved your recordings, the size of you LiveCD will be under the 4Gb limit imposed by the software.



1.0 The first step is a difficult one only b/c you probably don't know if you have a proprietary graphics driver installed.
    However, the easiest way to figure this out is to use "MythTV's Control Centre" (APPS|SYSTEM|MythTV Control Centre) and select the Graphics Driver Button. 
    This should help you in determining whether or not you have installed a non-open source graphics driver.

    Note that any proprietary (non-open source) driver installed must be uninstalled to create a LiveCD that can be applied/used universally.
    Uninstall any Nvidia or ATI/AMD graphic drivers before creating your LiveCD.
    However, if you do not remove these drivers then your LiveCD will work, but it will be restricted to only those PCs that use the same graphics adapter.


2.0 install package "remastersys" following instructions found on 
       [http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

2.1 first modify the repository list: 
    sudo pico /etc/apt/sources.list (insert the following two lines)
        # remastersys package for Karmic, Lucid and newer
        deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
    press CTRL+X
    press Y
    press <E>
    
    sudo apt-get update

    
2.2 use synaptic package manager: APPS|SYSTEM|Synapic Package Manager
    search for "remastersys"
    select for installation
    press button "apply"


3. use remastersys:
    APPS|SYSTEM|Remastersys Backup
        select Clean -> OK
        select Modify -> OK
            change parameters/variables as needed.
        select Dist
            (wait 40 minutes to process/complete task)
        select Done/Quit

At this point, two files interest you in /home/remastersys/remastersys :
   1.log file - read it to help you troubleshoot if this process fails.
   2. *.iso file (this is the image file you need to burn to your usb/cd/dvd depending on its size.)
             remember CDs are less than 700Mb and you should use a DVD when size is greater than 700Mb, and up to 4Gb


4.  install package "usb-creator-gtk"

    use synaptic package manager: APPS|SYSTEM|Synapic Package Manager
    search for "usb-creator-gtk"
    select for installation
    press button "apply"

5.  use usb-creator-gtk:

    insert USB stick/flash drive
    APPS|SYSTEM|Startup Disk Creator
        upper listbox: select button "Other"
            select /home/remastersys/remastersys/*.iso
            highlight newly added ISO
        lower listbox: select USB entry that has free space
            (if no device has free space then select button "format")
            once formatted, select button "Erase Disk"
        select button "Make Startup Disk"
   
 Your USB stick should now be a custom Live CD.

---

### Post by nickrout on 2011-02-20
So...

Are you now able to connect to your frontend from the laptop?

---

### Post by nhtrader on 2011-02-20
Yes.

I can now access my primary mythbox (FE & BE) on my home network and I can temporarily use any other PC in the house as a FE to watch LiveTV, recordings, etc. after I install  my customized LiveUSB with MythTV 0.24-184.

This works with AMD or Intel based PCs using ATI/AMD or Nvidia graphics adapters.


Now my next step is to learn how to convert/transcode recordings so that I can access these compressed recordings remotely. My outbound bandwidth is limited to approx 90 KBytes per second or 700Kbits per second.

I should add I can use MythWeb remotely (outside my home network) for scheduling. But streaming using ASX is still problematic. However, enabling the flash video option in MythWeb and watching recordings in the mini flash player works great. I can't believe how simple it is to use flash video in this version of MythTV and that it converts *.mpg in realtime.

---

