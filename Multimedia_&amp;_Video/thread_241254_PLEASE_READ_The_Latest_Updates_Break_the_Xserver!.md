---
title: "PLEASE READ: The Latest Updates Break the Xserver!"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by tseliot on 2006-08-22
[SIZE="4"]HOWTO solve the problem[/SIZE]

[COLOR="Red"]UPDATE:[/COLOR]
The version of xserver-xorg-core which causes the problem is 10.3. (version 10.4 fixes the problem)

See which version is available in the repositories:
```
sudo aptitude update
```

```
sudo aptitude install -s -V  xserver-xorg-core
```

and see which version the system would install (it's just a simulation)

if it's version 10.4 then you can install it:
```
sudo aptitude dist-upgrade
```

If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work

[COLOR="Red"][SIZE="3"]
HOWTO check which version you have installed:[/SIZE][/COLOR]
```
sudo aptitude show  xserver-xorg-core | grep Version
```

(the "V" of Version must be in capital letter)

__________________________________________________________________________
[SIZE="3"]**[COLOR="Red"]If version 10.4 is not in the repos yet you should do this:[/COLOR]**[/SIZE]
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```
Then restart your computer
```

sudo reboot
```
**OR if the file is not on your computer:**
**for Ubuntu 32 bit:**
```
wget http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
```
```
sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
```
**For Ubuntu 64bit:**
```
wget http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_amd64.deb
```
```
sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10_amd64.deb
```
__________________________________________________________________________
[SIZE="3"]**Howto fix the problem with the Alternate Installer CD of Ubuntu (not the live installer)**[/SIZE]
1) make a backup of your repository list:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
```
2) Add your cd to as your repository:
```
sudo apt-cdrom add
```
it will ask you to insert your CD
3) Try:
```
sudo apt-get install sudo apt-get install -s xserver-xorg-core=1:1.0.2-0ubuntu10
```
Or (if that package can't be found):
```
sudo apt-get install -s xserver-xorg-core=1:1.0.2-0ubuntu10.1
```
4) reboot

---

### Post by aurelieng on 2006-08-22
This bug is really annoying, thanks for your fix !

---

### Post by The Pinny Parlour on 2006-08-22
argh.. To late.  I saw this updated and absolutely dreaded and hesitated installing it.  Xserver-xorg failed on reboot,  suprise suprise.  Stuff like this makes the ubuntu experience a painful one.   

Yes, I am pissed off.

---

### Post by Kilz on 2006-08-22
](*,)  I was working on getting the new ATI drivers working. I bashed my head into a wall for a few hours thinking it was something I did. ](*,) 
Thanks for saving me more pain

---

### Post by The Pinny Parlour on 2006-08-22
It doesn't work.  Can't change because of some customised configuration file  blah blah.   

Tried sudo dpkg-reconfigure xserver-xorg    tried vesa, vga, nvidia and nv  all die when I get to 24 bits  blah blah blah.

---

### Post by The Pinny Parlour on 2006-08-22
Why has this broken update been allowed to go live?  How ridiculous.

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> It doesn't work.  Can't change because of some customised configuration file  blah blah.   

Tried sudo dpkg-reconfigure xserver-xorg    tried vesa, vga, nvidia and nv  all die when I get to 24 bits  blah blah blah.

I hate xserver xorg, it's a piece of utter crap.

I need to know the exact error otherwise I'm afraid I can't help you

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> I need to know the exact error otherwise I'm afraid I can't help you

Thank you tseliot.

I'm just that pissed off because of phucking xserver xorg.  It is the devil I swear to goodness.  It is a bucket of shit.  This should NOT be happening and it IS.  

Oh why oh why did I click 'update' it this morning????

---

### Post by The Pinny Parlour on 2006-08-22
1.  Failed to start xserver .....

2.  Couldn't open RGB-RD  /usr/share/X11/rgb    then a heap of other gibber.

3.  Would you like to view the detailed xserver output as well?

4.  more gibber

5.  The Xserver is now disabled.  Restart GDM when it is properly configured.

6.  Then it goes to CLI login

7.  User of this ubuntu PC REALLY PISSED OFF](*,) ](*,)

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> Thank you tseliot.

I'm just that pissed off because of phucking xserver xorg.  It is the devil I swear to goodness.  It is a bucket of shit.  This should NOT be happening and it IS.  

Oh why oh why did I click 'update' it this morning????

Please, restrain yourself from using swear words in this forum.

BTW without the Xserver we would be stuck to the command line

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> 1.  Failed to start xserver .....

2.  Couldn't open RGB-RD  /usr/share/X11/rgb    then a heap of other gibber.

3.  Would you like to view the detailed xserver output as well?

4.  more gibber

5.  The Xserver is now disabled.  Restart GDM when it is properly configured.

6.  Then it goes to CLI login

7.  User of this ubuntu PC REALLY PISSED OFF](*,) ](*,)

I meant:
What happens if you type:
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

Please report the error

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> Please, restrain yourself from using swear words in this forum.

BTW without the Xserver we would be stuck to the command line

Sorry   but it's how I feel.   BTW I AM stuck in command line.  That's the issue.  A way to get out of it would be really handy.

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> I meant:
What happens if you type:
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

Please report the error

No error now.  It went smootly as far as a downgrade goes, (why on earth should any of us be doing a downgrade is beyond me.  How was this ever released?)  Now I just can't start x  grumble.

---

### Post by petri on 2006-08-22
tseliot, seems like you know ATI? :)

Still after the downgrade the X won't start. The usual Ubuntu start comes upp then screens go black as usual but it stays black. No Ctrl+Alt+F1, Ctrl+Alt+Backspace etc works. No sound either that signals the login has loaded.

I did install new drivers with [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant) Method 2 and this xorg update shows up and I installe dit too.

I guess I have to reinstall kernel etc. But how, any good links?

---

### Post by MaximB on 2006-08-22
thanks tseliot
I hope you saved my ubuntu dapper
but I don't get it....what they do not check for bugs and errors Before the realese an update ???

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> No error now.  It went smootly as far as a downgrade goes, (why on earth should any of us be doing a downgrade is beyond me.  How was this ever released?)  Now I just can't start x  grumble.

You need to reinstall the nvidia driver (or set it to "nv", vesa, etc.)

Then reboot:
```
sudo reboot
```

---

### Post by tseliot on 2006-08-22
> **petri said:**
> tseliot, seems like you know ATI? :)

Still after the downgrade the X won't start. The usual Ubuntu start comes upp then screens go black as usual but it stays black. No Ctrl+Alt+F1, Ctrl+Alt+Backspace etc works. No sound either that signals the login has loaded.

I did install new drivers with [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant) Method 2 and this xorg update shows up and I installe dit too.

I guess I have to reinstall kernel etc. But how, any good links?

Reinstall the driver.

---

### Post by tseliot on 2006-08-22
> **MAXDDARK said:**
> thanks tseliot
I hope you saved my ubuntu dapper
but I don't get it....what they do not check for bugs and errors Before the realese an update ???

It happens :(

---

### Post by Cryonic on 2006-08-22
Thanks for the notification, luckily I was keeping on eye on the forums. Downgraded, rebooted and all is well. (Dell laptop D820)

---

### Post by Dale61 on 2006-08-22
G'day, another recent Ubuntu convert.

Took the plunge 3 weeks ago, and all was going swimmingly, until this morning.

I had been telling a few mates about how much better my pc was running since installing DD, and had convinced one to consider changing his small office pc's over from Windoze.

Anyway, was sitting here showing him around the desktop and what different things were when I noticed I had an update ready for downloading.  Perfect, I thought, as this will show him how easy it is to keep his systems up-to-date.

Proceeded to d/l the xserver update, rebooted, and nothing!  Xserver failed, and I couldn't explain why.  After an hour or so, he was no longer interested in upgrading, which means there will be a dozen less pc's converting to Ubuntu.  May not sound like a lot, but he will tell others, and so, it will travel down the line.

I continued to find a remedy, and fortunately, I have a laptop (XP) setup close by, so I connected to the net and searched far and wise for an answer.  I came across this forum, and following the instructions above, I was able to get my pc up and running as it was pre-update.

Overall, this was an 8 hour exercise, 8 hours that I could afford to take out of my day, but how many others have that luxury?  I'm wondering how many others, particularly those in business, who are still trying to find a solution to a problem that should NEVER have happened in the first place.  I pity those who don't have a backup system and are still trying to work out what's happened.

I would just like to thank all those who were quick to see the problem and submit a fix, but there needs to be some serious questions answered as to why this happened in the first place.  Don't the developers test these things on their own machines first, or are we the guinea pigs for their experiments.

My apologies for such a harsh first post, but as I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.

---

### Post by tseliot on 2006-08-22
> **Dale61 said:**
> G'day, another recent Ubuntu convert.

Took the plunge 3 weeks ago, and all was going swimmingly, until this morning.

I had been telling a few mates about how much better my pc was running since installing DD, and had convinced one to consider changing his small office pc's over from Windoze.

Anyway, was sitting here showing him around the desktop and what different things were when I noticed I had an update ready for downloading.  Perfect, I thought, as this will show him how easy it is to keep his systems up-to-date.

Proceeded to d/l the xserver update, rebooted, and nothing!  Xserver failed, and I couldn't explain why.  After an hour or so, he was no longer interested in upgrading, which means there will be a dozen less pc's converting to Ubuntu.  May not sound like a lot, but he will tell others, and so, it will travel down the line.

I continued to find a remedy, and fortunately, I have a laptop (XP) setup close by, so I connected to the net and searched far and wise for an answer.  I came across this forum, and following the instructions above, I was able to get my pc up and running as it was pre-update.

Overall, this was an 8 hour exercise, 8 hours that I could afford to take out of my day, but how many others have that luxury?  I'm wondering how many others, particularly those in business, who are still trying to find a solution to a problem that should NEVER have happened in the first place.  I pity those who don't have a backup system and are still trying to work out what's happened.

I would just like to thank all those who were quick to see the problem and submit a fix, but there needs to be some serious questions answered as to why this happened in the first place.  Don't the developers test these things on their own machines first, or are we the guinea pigs for their experiments.

My apologies for such a harsh first post, but as I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.
There's no need to vent. The developers won't read this.

I have sent an email to the chief of the team which maintains the Xserver.

---

### Post by Kabal on 2006-08-22
Thanx for the info and why do they release in such a hurry without testing?

---

### Post by Dale61 on 2006-08-22
tseliot, I never intended to upset anyone, if I have, but just felt that I had to post what happened to someone who is trying to convince others to make the change.  If I was giving my demo yesterday, all would have been sweet, but today of all days!?

Yes indeed Kabal, the fix is quick and painless, but only if you know what the problem is in the first place, and have the facilities to find the fix.

---

### Post by jessexoc on 2006-08-22
This may belong in the beginners forum, but how can i downgrade xserver without an internet connection. i cant connect to the internet after xserver crashes and i reach the command line.

Cheers
-Jesse

---

### Post by funchords on 2006-08-22
Thank you!!! :KS You caught me after I installed it but before I rebooted.
```

robb@TOPOL016:~$ sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be DOWNGRADED:
  xserver-xorg-core
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 3529kB of archives.
After unpacking 4096B disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main xserver-xorg-core 1:1.0.2-0ubuntu 10 [3529kB]
Fetched 3529kB in 6s (560kB/s)
dpkg - warning: downgrading xserver-xorg-core from 1.0.2-0ubuntu10.3 to 1.0.2-0u buntu10.
(Reading database ... 79295 files and directories currently installed.)
Preparing to replace xserver-xorg-core 1:1.0.2-0ubuntu10.3 (using .../xserver-xo rg-core_1%3a1.0.2-0ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Setting up xserver-xorg-core (1.0.2-0ubuntu10) ...
robb@TOPOL016:~$ 
```

---

### Post by svenaron on 2006-08-22
Just FYI I just upgraded xserver on a Dell X300 laptop 10 minutes ago and everything works hunky dory.
/Sven

---

### Post by Dale61 on 2006-08-22
svenaron, have you rebooted yet?  When I d'led the update, I didn't reboot until about an hour afterwards.  That was when the problems started.

---

### Post by DFNC on 2006-08-22
tseliot: THANK YOU 

Since i am a new "convert" to ubuntu, and a n00b on *nix i was terrified that i fouled up the install and the uppgrades. You saved my wall, no need to bash my head in it anymore :)

Huge Thanks!

---

### Post by funchords on 2006-08-22
> **The Pinny Parlour said:**
> Why has this broken update been allowed to go live?  How ridiculous.

And why is it still live?

---

### Post by hvbakel on 2006-08-22
Exactly, pulling the update from the repositories will at least keep other people from running into this mess...

---

### Post by tseliot on 2006-08-22
> **jessexoc said:**
> This may belong in the beginners forum, but how can i downgrade xserver without an internet connection. i cant connect to the internet after xserver crashes and i reach the command line.

Cheers
-Jesse

Try with
```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

---

### Post by alainhenry on 2006-08-22
Thanks for the forum help, I fixed the upgrade with the prposed command.  it took me 2 minutes.  Though I agree this upgrade should not have come live and should have been taken back quickly, it's also fair to say that the forum helped fixed this swiftly.  So many thanks to the forum.  

Unfortunately, accidents do happen.  I assume the Ubuntu team will seize this opportunity to improve the error checking procedure.

---

### Post by tseliot on 2006-08-22
> **funchords said:**
> And why is it still live?

They told me that they are working on it

---

### Post by tengil on 2006-08-22
> **jessexoc said:**
> This may belong in the beginners forum, but how can i downgrade xserver without an internet connection. i cant connect to the internet after xserver crashes and i reach the command line.

Cheers
-Jesse

From the ubuntu-users mailing list:

$ mount /media/cdrom0
$ dpkg -i /media/cdrom0/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb

Ubuntu is losing lots of users today :-(

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> You need to reinstall the nvidia driver (or set it to "nv", vesa, etc.)

Then reboot:
```
sudo reboot
```

Thank you.

Tried nv and nvidia and vesa, still it doesn't work.  I installed nvidia drivers via automatix and have no idea how to do it otherwise.   Any how-tos on this would be great.

Thanks  :mrgreen:

---

### Post by Stormbringer on 2006-08-22
In regards to the complaints about the latest xserver-xorg-core update ...

> **tseliot said:**
> It happens :(

Yeah, it may happen that a buggy update may slip out ... but lately this happened much too frequently. THIS is NOT the first dapper-update that severly b0rk3d my, or others, install. Remember the ia32-libgtk update on the amd64 platform that borked the file requesters in OpenOffice and the VMware GUI for example?

Very slowly I'm losing faith into Ubuntu as the developers have an annoying tendency to screw up royally lately ... seems as Mr. Shuttleworth didn't had the funds to make up a R&D department.

However, just my two cents on the latest issue - now go ahead and call me rude for speaking out the truth.

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> Thank you.

Tried nv and nvidia and vesa, still it doesn't work.  I installed nvidia drivers via automatix and have no idea how to do it otherwise.   Any how-tos on this would be great.

Thanks  :mrgreen:

try Envy:
```
wget -c http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb
```

then:
```
sudo dpkg -i envy_0.4.2-1ubuntu3_all.deb
```

then type:
```
envy
```


**P.S. If after choosing the "install" option, envy hangs on Ubuntu's splash screen, press Ctrl+Alt+F1**

---

### Post by tseliot on 2006-08-22
> **Stormbringer said:**
> In regards to the complaints about the latest xserver-xorg-core update ...



Yeah, it may happen that a buggy update may slip out ... but lately this happened much too frequently. THIS is NOT the first dapper-update that severly b0rk3d my, or others, install. Remember the ia32-libgtk update on the amd64 platform that borked the file requesters in OpenOffice and the VMware GUI for example?

Very slowly I'm losing faith into Ubuntu as the developers have an annoying tendency to screw up royally lately ... seems as Mr. Shuttleworth didn't had the funds to make up a R&D department.

However, just my two cents on the latest issue - now go ahead and call me rude for speaking out the truth.

There's no sense in complaining here. This thread is for support ONLY.

The developers won't see your complain here

---

### Post by petri on 2006-08-22
> 
Quote:
Originally Posted by petri View Post
tseliot, seems like you know ATI?

Still after the downgrade the X won't start. The usual Ubuntu start comes upp then screens go black as usual but it stays black. No Ctrl+Alt+F1, Ctrl+Alt+Backspace etc works. No sound either that signals the login has loaded.

I did install new drivers with [http://wiki.cchtml.com/index.php/Ubu](http://wiki.cchtml.com/index.php/Ubu)... ule-assistant Method 2 and this xorg update shows up and I installe dit too.

I guess I have to reinstall kernel etc. But how, any good links?

> **tseliot said:**
> Reinstall the driver.

I do not have a prompt to use, the screen is black. :-|

---

### Post by tseliot on 2006-08-22
**[COLOR="Red"][SIZE="3"]UPDATE: the problem has been fixed but you should wait to upgrade until xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb is uploaded to the ubuntu servers.[/SIZE][/COLOR]**

OR you can install the new packages manually:
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb)

---

### Post by tseliot on 2006-08-22
> **petri said:**
> I do not have a prompt to use, the screen is black. :-|

Boot in Recovery mode (you can choose it from the GRUB menu almost as soon as you turn on your computer)

---

### Post by biocrasher on 2006-08-22
Thanks for the solution tseliot. And btw this problem reminded me why I
love lynx. No reboots, no panic, just 5 minutes on the web and the
problem is fixed.

---

### Post by tseliot on 2006-08-22
Instructions updated!

---

### Post by reskerix on 2006-08-22
I'm wondering 2 questions:
- Why ubuntu(people working in) haven't blocket the wrong packege? (upgrade is suggesting my to install xserver 10.3!)

- When I will know the package is updated in the servers?

PD: I fixed the problem reading this forum. Thank you very much!

---

### Post by thojoh on 2006-08-22
thanks for the support. It was rather scary for a moment. I downgraded and rebooted and all is well.

Do I understand correctly that by now I can trust again the message that tells me to upgrade and just do it? (Maybe for my own piece of mind I might wait another day).  :)

And for those in this forum who complained: I know what you feel as problems on my computer get to me strongly as well (especially if there is work to be done). But I remember having loads of those moments when working under Windows as well. So I really feel well supported by the ubuntut community and for the rest I think it is good to face the facts:  Computers tend to give you problems every now and again (because they run on human software). 

Thanks again for your unfaltering support and trying to answer peoples' questions, tseliot!

---

### Post by doomstone on 2006-08-22
Dam i got scared there :D
But hey thx for the fix. but ppl whom don't know lynx and is not good at linux would might have a problem here.

---

### Post by raffytaffy on 2006-08-22
ow man...i was right in the middle of compiling new kernel...did everything..tried getting it to work...xserver ..blah blah..i was convinced my new kernel was @ fault...so i ran every possible check / command ///3 hrs ...3 cups of coffee and 2 packs of skittles later...i remember i did a xorg update...boy did i feel dumb:(

---

### Post by anindya_m on 2006-08-22
I think Ubuntu should remove the upgrade till fixed, since the problem is so easily reproduced (to be fair: thanks to apt it is also easily fixed).

---

### Post by tseliot on 2006-08-22
> **thojoh said:**
> Do I understand correctly that by now I can trust again the message that tells me to upgrade and just do it? (Maybe for my own piece of mind I might wait another day).  :)
It's all explained in my 1st post (which I have updated)

---

### Post by tseliot on 2006-08-22
> **anindya_m said:**
> I think Ubuntu should remove the upgrade till fixed, since the problem is so easily reproduced (to be fair: thanks to apt it is also easily fixed).

They are uploading the new packages

---

### Post by svenaron on 2006-08-22
> **Dale61 said:**
> svenaron, have you rebooted yet?  When I d'led the update, I didn't reboot until about an hour afterwards.  That was when the problems started.

Kind of a moot point now but yes, I did reboot several times.

cheers
/Sven

---

### Post by Copter on 2006-08-22
hi!

thanks again for help tseliot. i was just about to reboot after 1.5 hour of update downloads. you saved me from entering Windows. feels great :)

copter :]

---

### Post by toasterofirony on 2006-08-22
Oh man, now that was the kind of brown trouser moment I *never* want to relive. It was getting to the "sod this, I'm going into reinstall windows *grumblegrumblegrumble*". Especially after I'd just expounded the virtues Ubuntu to my father!

Thank you so much for the help tseliot, I hope at least someone buys you a drink tonight :)

---

### Post by petri on 2006-08-22
> Quote:
Originally Posted by petri View Post
I do not have a prompt to use, the screen is black.

Boot in Recovery mode (you can choose it from the GRUB menu almost as soon as you turn on your computer)


Well, yes of course. I had # for the lines for recovrey in my menu.lst in Grub which I had totally forgotten. :rolleyes: 

Thanks tseliot!

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> There's no sense in complaining here. This thread is for support ONLY.

The developers won't see your complain here

I wonder were they can hear us users complain then.

---

### Post by almost_extinct on 2006-08-22
Another vote of thanks for TSEliot - I grow old, I grow old, etc... but the young guys keep things going.

This is every tech support person's nightmare.  A few of us got caught before the fix went in.

Let's just applaud the developers and tech support for fixing this so quickly.

BTW instructions for ATI proprietary drivers installation - remember you should reinstall them if you use them - can be found at:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

You'll need to do a 

```
sudo apt-get remove xorg-driver-fglrx
```

before the 

```
sudo apt-get install xorg-driver-fglrx
```

Worked for me.

---

### Post by raffytaffy on 2006-08-22
i was thinking...i have a perfectly functioning xserver ( prior to this update) do i really need to update xorg and other apps..that do not cause any trouble..and work 100%.....which brings me to another question...how does one disable update manager from remind me everytime i update certain things..about the ones i dont want to update:(

---

### Post by AndrewShugg on 2006-08-22
> **petri said:**
> I do not have a prompt to use, the screen is black. :-|

Can you get to a console with Ctrl+Alt+F1 ?

If not, you may need to forcibly reboot (ick) and choose the recovery option if it is there, or edit your GRUB boot line to go into single-user mode (by adding 'single' to the kernel boot parameters).

The days of X11 b0rkage actually killing the system are hopefully behind us. ;)

Andrew S.

---

### Post by AndrewShugg on 2006-08-22
> **raffytaffy said:**
> i was thinking...i have a perfectly functioning xserver ( prior to this update) do i really need to update xorg and other apps..that do not cause any trouble..and work 100%.....which brings me to another question...how does one disable update manager from remind me everytime i update certain things..about the ones i dont want to update:(

You can right-click the notifcation icon and click (to untick) "Show notifications" ... then turn it back on in a week or so when the dust has settled.

Andrew S.

---

### Post by petri on 2006-08-22
AndrewShugg

No, I couldn't use Ctrl+Alt+F1. I have my system running again now but thanks anyway ;) 


The Pinny Parlour

Why complain? How many of us have ever called that other OS manufacturer :rolleyes:  and complained? I did actually. I live in Scandinavia, a Finn living in Sweden and girl who answered spoke Norwegian. I just did not understand her. We tried english also but... ](*,) Spoken foreign language isn't my strong side.


I am going to install another Ubuntu or maybe a Kubuntu which shares the same /home partition. In that way I should always have an funtioning OS. Maybe some other partitions too to share webbrowser bookmarks and email. :-k

---

### Post by ubuntu_demon on 2006-08-22
> **AndrewShugg said:**
> You can right-click the notifcation icon and click (to untick) "Show notifications" ... then turn it back on in a week or so when the dust has settled.

Andrew S.
IMHO a week is a bit long. 

We just have to wait until xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb is uploaded to the ubuntu servers which will probably happen (somewhere) today.

---

### Post by kiikkuja on 2006-08-22
quote: sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

This worked like a charm with my 64-bit dapper...thanks!! I thought it was something else...something i did myself. BTW since i did both of the operations 32-bit and 64-bit fix i was wondering if i should reinstall my nvidia drivers. All seems to be ok?!

---

### Post by tristan on 2006-08-22
Sorry, but I have to vent about this one. Updates which cause a few unforseen bugs or glitches are annoying but I can live with them. Updates which render a system essentially unusable (unless you're a dab hand on the command line) are pretty much inexcusable.

I appreciate all that the various ubuntu developers do for us, but this is the kind of mishap which will lose them users (particularly the kind of non-technical users which ubuntu is aiming for) and goodwill.

---

### Post by E_lexy on 2006-08-22
TSEliot,

Well done, I paniced a little, when the first posts didn't help me.

But your stuff worked rightaway!

Thanks:D

---

### Post by TNBY963 on 2006-08-22
This worked for me!

I installed the updates, but before I rebooted I saw this post. I followed the instructions in the first post and reinstalled my ATI driver.

Rebooted and everything is ok. 

I hear some people are upset because this was allowed in the repo's. Well, accidents happen. And one of the main reasons why I chose Ubuntu is not because of the updates, but because of the great community (wich has fixed the problem)!

---

### Post by hansi70 on 2006-08-22
Hi,

Is there a way to perform those commands (32-bit) without the presence of a network. I have a wireless and I can't get it to work from the console.

Regards, 

Hansi

---

### Post by dcstar on 2006-08-22
> **TNBY963 said:**
> 
.......
I hear some people are upset because this was allowed in the repo's. Well, accidents happen. And one of the main reasons why I chose Ubuntu is not because of the updates, but because of the great community (wich has fixed the problem)!
Other threads on this mess are saying that other Linux distros have been similarly hit, so it seems it is an Xorg stuff-up that the various distros have let get through.

It isn't just Ubuntu that is suffering, it seems it is a lot of Linux users.

---

### Post by tseliot on 2006-08-22
> **hansi70 said:**
> Hi,

Is there a way to perform those commands (32-bit) without the presence of a network. I have a wireless and I can't get it to work from the console.

Regards, 

Hansi

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10_i386.deb
```

---

### Post by hansi70 on 2006-08-22
Hi tseliot,

How can I perform the instructions for a proposed solutin you mentioned without a network? It is difficult to get my wireless to work while on console. Is there a way (after downloading those files) to do it offline?

Regards,

Hansi

---

### Post by Sirron on 2006-08-22
gosh, what an update.

I installed a new application after the update, tried to run it and the system locked up like Windows ME. So naturally I suspected the app, restarted the computer with the power button and decided to uninstall it when Ubuntu had reloaded. Then Xserver wouldn't load. Things were said. Nasty, evil things about Windows and how it's never truly let me down like this, as a result of an update.

So, I booted into XP and found this forum post.

I tried writing the fix on a post-it but couldn't be bothered so I just copied the code into a text document and saved it to a USB memory deely. I then put that on my Vista running PC, and proceeded to boot this one into Ubuntu Recovery Mode.

I naievely expected to be able to just type it and press return - until I actually read it while ubuntu recovery mode was booting. This fix needs a working internet connection.

And when the recovery mode had loaded it tried to dial with my Alcatel (or Thomson) USB Modem. I originally set it up with these instructions [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

But it just hung on synchronising.

So I unplugged the modem, and rebooted, and this time I was able to type, but had no way of connecting to the internet. So I plugged the modem back in, it automatically loaded the drivers, but I was able to type still.

I referred to those instructions and found that to make it dial manually, you need to type:
```
modprobe ppp_generic
modprobe pppoatm
pppd call speedtch
```

And that, shockingly, worked, I was then able to download the packages and the fix was sucessful! Thanks very much, tseliot.

---

### Post by azmrb on 2006-08-22
> **tseliot said:**
> **[COLOR="Red"][SIZE="3"]UPDATE: the problem has been fixed but you should wait to upgrade until xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb is uploaded to the ubuntu servers.[/SIZE][/COLOR]**

OR you can install the new packages manually:
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb)

OK, I am on amd64 and I luckily did not install the 10.3 version but I still have the notification to install the 10.3 version and your first post indicates the 10.4 version is 32bit only, that 64bit users should revert back to 10.2         ?How do I get the notifyer to stop prompting me to install the 10.3 buggy version?

---

### Post by hajk on 2006-08-22
Let me just say that all the enraged comments about a broken update appear a bit overdone to an old-time Linux user... what will these complainers do when they hit a real tough spot in life, I wonder.

The good news is that not *all* Intel-based computers suffered from this update: the X-server on the Ubuntu install (latest 686-SMP kernel) on my MacBook laptop started just fine with the new xserver-xorg-core package.

But, alas, the one on my AMD64 system did not, but reinstalling a previous version of the package is not difficult, since all copies of them are kept in the /var/cache/apt/archives directory for that purpose. Having a "revert" option in apt-get should then include a choice option of which older package to install (they're all kept, not only the immediately preceding one) -- it hardly seems worth the trouble to write that kind of code.   

My €0.02 worth...

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> try Envy:
```
wget -c http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb
``` 
then:
```
sudo dpkg -i envy_0.4.2-1ubuntu3_all.deb
``` 
then type:
```
envy
``` 

**P.S. If after choosing the "install" option, envy hangs on Ubuntu's splash screen, press Ctrl+Alt+F1**


thanks  but this totally FAILED.

I'm jack of ubuntu.  This is just B*******.  I can't believe this.  Ubuntu--B*** ME.
[coarse language modified by matthew]

FORMER UBUNTU USER.

---

### Post by hansi70 on 2006-08-22
Hi Tseliot,

I have already asked this question before. So sorry about the duplication of the message.

> **hansi70 said:**
> Hi tseliot,

How can I perform the instructions for a proposed solutin you mentioned without a network? It is difficult to get my wireless to work while on console. Is there a way (after downloading those files) to do it offline?

Regards,

Hansi

---

### Post by PolarBear on 2006-08-22
Phew, that was a SCARY experience! And it happened at the worst imaginable moment, when I simply didn't have time for this kind of problems!!

But luckily the fix wenth smooth and managed to get my system back working.

---

### Post by macstevejb on 2006-08-22
this has now been fixed and no doubt the new update will appear in the repos shortly.

meanwhile the deb can be found here:

[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)

I have just installed without any problems.

regards

:o

---

### Post by tseliot on 2006-08-22
> **hansi70 said:**
> Hi tseliot,

How can I perform the instructions for a proposed solutin you mentioned without a network? It is difficult to get my wireless to work while on console. Is there a way (after downloading those files) to do it offline?

Regards,

Hansi

You can do what I suggested without downloading anything. That command reinstalls a package which is already on your hard disk

---

### Post by anando on 2006-08-22
tseliot - why did you stop the thread that I started on xserver update bug and sticky your own ? What information is new in your sticky thread that wasn't already there in the previous thread ? 

Ridiculous !!

---

### Post by tseliot on 2006-08-22
> **macstevejb said:**
> this has now been fixed and no doubt the new update will appear in the repos shortly.

meanwhile the deb can be found here:

[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)

I have just installed without any problems.

regards

:o

It's all in my 1st post

---

### Post by hansi70 on 2006-08-22
Hi Tseliot,

Can you tell me where I can download specific linux drivers for Nvidia graphic cards (GeForce FX Go5700)? I found some sites via google but they had a long shell script (12.4 MB) that is used for all Nvidia drivers? 

Regards,



> **tseliot said:**
> ```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10_i386.deb
```

---

### Post by givré on 2006-08-22
> **The Pinny Parlour said:**
> thanks  but this totally FAILED.

I'm jack of ubuntu.  This is just BULLSHIT.  I can't believe this.  Ubuntu--BITE ME.

FORMER UBUNTU USER.
Did you try to upgrade to the latest version like mention in the first post.
This update version is already in the repo, just need time to hit all the mirror.

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> thanks  but this totally FAILED.

I'm jack of ubuntu.  This is just BULLSHIT.  I can't believe this.  Ubuntu--BITE ME.

FORMER UBUNTU USER.

I had already warned you against using such an inappropriate language.

---

### Post by Tantalus90 on 2006-08-22
Would be a help if someone could post the Version 

Just so we all know what not to install :) 

Tant

---

### Post by tseliot on 2006-08-22
> **Tantalus90 said:**
> Would be a help if someone could post the Version 

Just so we all know what not to install :) 

Tant

Read my 1st post

---

### Post by ingwa on 2006-08-22
tseliot, thank you for the update you provided.  I had installed this mornings patch and had to shut down the box to use the power cord etc.  When I rebooted I panicked that it hadn't been shut down properly, however we all now know that it was the patch that broke it.  I had spent hours trying to reconfig xserver using the commands on the net, but then realised there must be a whole system wide problem as the website was unreachable for a while.  Thanks again for the quick fix, and thanks for saving me hours of heartache having to rebuild.

I'm not complaining about fixes being applied and not being properly tested, these things happen, and thank goodness this is a free system where there are 100's or 1000's of contributors to make things right.

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> I had already warned you against using such an inappropriate language.

i finding it most appropriate considering the absolute balls up this xorg has cause me.  

I'm sorry if I have offended anyone here (including yourself) with my colouful use of the english language.  I'm just so darn angry that this MAJOR MAJOR BALLS UP, has been allowed to go live and stuff up alot of users machines.

---

### Post by The Pinny Parlour on 2006-08-22
> **givré said:**
> Did you try to upgrade to the latest version like mention in the first post.
This update version is already in the repo, just need time to hit all the mirror.

yes tried everything,  latest DOWNGRADE....then upgrade....then nvidia drivers....then  xorg failed to start   grrrrr ](*,) 

nano'ed the heck out of xorg.conf too.   still nothing...

---

### Post by tseliot on 2006-08-22
> **The Pinny Parlour said:**
> yes tried everything,  latest DOWNGRADE....then upgrade....then nvidia drivers....then  xorg failed to start   grrrrr ](*,) 

nano'ed the heck out of xorg.conf too.   still nothing...

Do what I suggested in my 1st post

Reboot

Install the Nvidia driver

---

### Post by mattlach on 2006-08-22
> **tseliot said:**
> 
**[COLOR="Red"]NOTE: 64bit users should do this:[/COLOR]**
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```
Then restart your computer
```

sudo reboot
```

Aww :(  No 10.4 for us 64 bitters?  :p

---

### Post by The Pinny Parlour on 2006-08-22
> **tseliot said:**
> Do what I suggested in my 1st post

Reboot

Install the Nvidia driver

Cheers tseliot,  

have done mate.  all fail.

You want to know why I'm so angry at this?  I just spent all last weekend installing a fresh copy and configuring ubuntu to how I like it.  Everything was going great.  I was grinning from ear to ear.  Then this morning, the update light comes on and its xserver-xorg.  my haert sunk when I saw it and imediately I thought trouble, as I had been stuffing around with it for most of my last weekend to get my ubuntu install working. 

I installed it as i'm sure most would only to reboot this afternoon and find a pear-shaped xserver-xorg.

This is one of the reasons I'm so angry at this.  The other is how could "they" let this massive BALLS UP go live...?

My weekend is gone AGAIN.  I will have to reinstall, (and lose all my data in the process) this weekend.  NOT A HAPPY CAMPER...](*,)

---

### Post by GothicX on 2006-08-22
> **hansi70 said:**
> Hi tseliot,

How can I perform the instructions for a proposed solutin you mentioned without a network? It is difficult to get my wireless to work while on console. Is there a way (after downloading those files) to do it offline?

Regards,

Hansi


SpeedTouch 330 auto-install package offline: [http://marco.tondela.org/stuff/speedtch330.tar.gz](http://marco.tondela.org/stuff/speedtch330.tar.gz)

---

### Post by The Pinny Parlour on 2006-08-22
In addition, I'm pretty new to ubuntu and this is not a good endorsement for ubuntu.  I have been raving about to everyone that would listen.  I won't be raving about it anymore.  I'll tell them to buy an apple instead.

---

### Post by GothicX on 2006-08-22
> **Sirron said:**
> gosh, what an update.

I installed a new application after the update, tried to run it and the system locked up like Windows ME. So naturally I suspected the app, restarted the computer with the power button and decided to uninstall it when Ubuntu had reloaded. Then Xserver wouldn't load. Things were said. Nasty, evil things about Windows and how it's never truly let me down like this, as a result of an update.

So, I booted into XP and found this forum post.

I tried writing the fix on a post-it but couldn't be bothered so I just copied the code into a text document and saved it to a USB memory deely. I then put that on my Vista running PC, and proceeded to boot this one into Ubuntu Recovery Mode.

I naievely expected to be able to just type it and press return - until I actually read it while ubuntu recovery mode was booting. This fix needs a working internet connection.

And when the recovery mode had loaded it tried to dial with my Alcatel (or Thomson) USB Modem. I originally set it up with these instructions [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

But it just hung on synchronising.

So I unplugged the modem, and rebooted, and this time I was able to type, but had no way of connecting to the internet. So I plugged the modem back in, it automatically loaded the drivers, but I was able to type still.

I referred to those instructions and found that to make it dial manually, you need to type:
```
modprobe ppp_generic
modprobe pppoatm
pppd call speedtch
```

And that, shockingly, worked, I was then able to download the packages and the fix was sucessful! Thanks very much, tseliot.


SpeedTouch 330 auto-install package offline: [http://marco.tondela.org/stuff/speedtch330.tar.gz](http://marco.tondela.org/stuff/speedtch330.tar.gz)

---

### Post by mattlach on 2006-08-22
> **The Pinny Parlour said:**
> Cheers tseliot,  

have done mate.  all fail.

You want to know why I'm so angry at this? 

...

How about reserving your anger for a service you are actually paying for.  The Ubuntu team owes you nothing.  Way to complain and get angry about something that dedicated people are doing for you, absolutely free. We all make mistakes occasionally and it is very difficult to monitor a large software project like this.

I think they are doing a smashing job, especially since this is the first time I have lost my Xserver in the 4 months I have been using Ubuntu.  (This was a weekly troubleshooting adventure when I was running Gentoo, but I was also using the experimental tree)

---

### Post by The Pinny Parlour on 2006-08-22
> **mattlach said:**
> ...

How about reserving your anger for a service you are actually paying for.  The Ubuntu team owes you nothing.  Way to complain and get angry about something that dedicated people are doing for you, absolutely free. We all make mistakes occasionally and it is very difficult to monitor a large software project like this.

I think they are doing a smashing job, especially since this is the first time I have lost my Xserver in the 4 months I have been using Ubuntu.  (This was a weekly troubleshooting adventure when I was running Gentoo, but I was also using the experimental tree)

I'm a tell like it is guy,  this is how I feel    I will say it.  Sorry to offend you.  :mrgreen:  
I'm just venting, after the crap weekend i went through HELL installing ubuntu last weekend, only to have this crap.

---

### Post by hansi70 on 2006-08-22
Hi tseliot,

I tried that command and I get an error message "package not found". I checked the spelling with your command and it looks right. I then checked the files in the archives folder and the package you named does not exist. I think the faulty package was the only Xserver core package there.

Any other suggestions?

Regards,

> **tseliot said:**
> ```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10_i386.deb
```

---

### Post by milkmaid on 2006-08-22
it has been quite a while since this update has been released,
why hasnt it been removed from the repos. yet?

or has it been fixed and is it save to preform an upgrade already?

and, even more important i presume; arent new installations of dapper automaticly failing as updates are being installed with it?...

.........

---

### Post by matthew on 2006-08-22
> **The Pinny Parlour said:**
> I'm a tell like it is guy,  this is how I feel    I will say it.  Sorry to offend you.  :mrgreen:A person who is fluent in their native language is generally capable of "telling it like it is" without being offensive in their manner of expression. I suggest and recommend that you please take this into account and choose to express your frustration and ideas using language that is less course and rude. Thank you. It is not your ideas that are offensive, but your manner of expressing them is unnecessarily rude and harsh. You have every right to be disappointed and frustrated, but you do not have the right to take it out on people in these forums.

---

### Post by gmc on 2006-08-22
> **The Pinny Parlour said:**
> Cheers tseliot,  

have done mate.  all fail.

You want to know why I'm so angry at this?  I just spent all last weekend installing a fresh copy and configuring ubuntu to how I like it.  Everything was going great.  I was grinning from ear to ear.  Then this morning, the update light comes on and its xserver-xorg.  my haert sunk when I saw it and imediately I thought trouble, as I had been stuffing around with it for most of my last weekend to get my ubuntu install working. 

I installed it as i'm sure most would only to reboot this afternoon and find a pear-shaped xserver-xorg.

This is one of the reasons I'm so angry at this.  The other is how could "they" let this massive BALLS UP go live...?

My weekend is gone AGAIN.  I will have to reinstall, (and lose all my data in the process) this weekend.  NOT A HAPPY CAMPER...](*,)

I can understand your frustration, however perhaps all is not lost. If you are going to do a re-install from scratch this might be the ideal time to consider making /home a separate partition. Since most of your desktop configuration is stored in your home directory. In future if you need/decide to do a re-install, you simple need not format the partition that your /home directory is on and you won't lose your desktop customizations. This has saved me on a number of occassions. Just food for thought...

G.

---

### Post by matthew on 2006-08-22
> **milkmaid said:**
> it has been quite a while since this update has been released,
why hasnt it been removed from the repos. yet?

or has it been fixed and is it save to preform an upgrade already?

and, even more important i presume; arent new installations of dapper automaticly failing as updates are being installed with it?...

.........The updated and working update has been made and is currently being mirrored to all the repos around the world. As this may take some time I suggest everyone follow tseliot's downgrade solution temporarily and check again in a few hours, or maybe tomorrow to see that the correct version has been posted. I'm sure we will have some announcements in the forums as well, at least in this thread.

As to the new installations automatically failing...it's likely. The devs started the fix immediately upon noticing the problem. Hopefully it won't affect too many more people...

---

### Post by davidshere on 2006-08-22
Hi.  Longtime user here, firstime poster.

I have Ubuntu on my home and work computer, and I installed the latest update last night on my home computer, and am experiencing the no-GUI problem.

I have not done the update yet on my work computer.  I've read through this thread and I'm still unclear on whether or not the bug fix is complete, and it's okay to run the update on my work computer.  

Is there a page somewhere that details when the updates are published, and differentiates between them? something like this:

[I]Update 321564 released last-night:   updates xxxxx <-- This breaks xserver
Update 321565 released this-morning: fixes bugs in update 321564.[/I]

---

### Post by dcherryholmes on 2006-08-22
> **The Pinny Parlour said:**
> 
My weekend is gone AGAIN.  I will have to reinstall, (and lose all my data in the process) this weekend.  NOT A HAPPY CAMPER...](*,)

Hey, I don't know if you're still going to stick with linux or not (believe me, these things happen in other distros, too), but I do have a suggestion with respect to you losing your data on a re-install.  If you format your hard drive so that you have a seperate partition for your home directory and another for the system files (i.e. "/"), then when you reinstall it only will re-write the one partition while leaving your home directory, your configs, and all your data untouched.  You can also copy config files, such as xorg.conf, to your home directory before the reinstall, and then just copy them back after you are finished.

Partitioning can be a little tricky if you aren't used to it, although it's pretty easy once you've done it a few times, and there's a nice GUI in the repositories to help you (looks a lot like Partition Magic, if you've heard of that): sudo apt-get install gparted

If you have any questions, feel free to PM me.

---

### Post by The Pinny Parlour on 2006-08-22
> **matthew said:**
> A person who is fluent in their native language is generally capable of "telling it like it is" without being offensive in their manner of expression. I suggest and recommend that you please take this into account and choose to express your frustration and ideas using language that is less course and rude. Thank you. It is not your ideas that are offensive, but your manner of expressing them is unnecessarily rude and harsh. You have every right to be disappointed and frustrated, but you do not have the right to take it out on people in these forums.

thank you for your suggestions and recommendation.  I'll take them onboard. :)

---

### Post by stig on 2006-08-22
I got caught out on one PC but the instructions solved the problem within minutes. Now I have a couple more ubuntu PCs so I guess I got to wait until the problem is fixed before I can do the update safely. How will we know when the update is safe to use - will there be a notice somewhere?

But I have to say the recovery through the Forum was impressive! I run a business and if this had been a Windows problem we would have been stuck for ages. All we have to do in ubuntu is to dip into the vast pool of information and expertise that the ubuntu community represents. And you don't have to to try and penetrate voice-mail systems or wait for people to call you back. And... it's free!

I read a post on the OpenOffice forum this morning by a guy from Banco de Santos (I think that was the name) in Brazil saying that they have switched 40,000 PCs to Linux. I wonder if they have discovered ubuntu....?

---

### Post by milkmaid on 2006-08-22
myea, lets hope :)

---

### Post by matthew on 2006-08-22
> **The Pinny Parlour said:**
> thank you for your suggestions and recommendation.  I'll take them onboard. :)Thanks, mate.:)

---

### Post by The Pinny Parlour on 2006-08-22
> **gmc said:**
> I can understand your frustration, however perhaps all is not lost. If you are going to do a re-install from scratch this might be the ideal time to consider making /home a separate partition. Since most of your desktop configuration is stored in your home directory. In future if you need/decide to do a re-install, you simple need not format the partition that your /home directory is on and you won't lose your desktop customizations. This has saved me on a number of occassions. Just food for thought...

G.

Thanks.  Sounds like a great idea. For a new comer, I'm sure it involves a heap of CLI which is just a daunting prospect.

---

### Post by Minigun_Fiend on 2006-08-22
Well this thread should save me. I just booted after shutting down earlier - I only just got Unreal Tournament GOTY working >:[ - and, lo and behold, error.

So I have to run the commands in the first post, then change the x config file to "nv" instead of "nvidia", right?
Then what? How do I get the 3D back after X is (hopefully) working again?

---

### Post by mattlach on 2006-08-22
> **gmc said:**
> I can understand your frustration, however perhaps all is not lost. If you are going to do a re-install from scratch this might be the ideal time to consider making /home a separate partition. Since most of your desktop configuration is stored in your home directory. In future if you need/decide to do a re-install, you simple need not format the partition that your /home directory is on and you won't lose your desktop customizations. This has saved me on a number of occassions. Just food for thought...

G.

I've never bothered to put my home on a separate partition (I usually just go to the console and back it up if I need to reinstall), but all my files are on different partitions than my system install.

---

### Post by cstudent on 2006-08-22
> **stig said:**
> I got caught out on one PC but the instructions solved the problem within minutes. Now I have a couple more ubuntu PCs so I guess I got to wait until the problem is fixed before I can do the update safely. How will we know when the update is safe to use - will there be a notice somewhere?


Just inspect the version number of the update before installing. Avoid the update that has ubuntu10.3 in the name. You want ubuntu10.4.

---

### Post by frankzen on 2006-08-22
> **tseliot said:**
> [SIZE="4"]HOWTO solve the problem[/SIZE]

[COLOR="Red"]UPDATE:[/COLOR]
The recent updates break the Xserver. If you have already updated Ubuntu please type the following command:

//snip///

sudo reboot[/CODE]


For those of us who HAVEN'T updated...how long should we wait???

Thanks

---

### Post by magnoliablossom on 2006-08-22
> **The Pinny Parlour said:**
> I'm a tell like it is guy,  this is how I feel    I will say it.  Sorry to offend you.  :mrgreen:  
I'm just venting, after the crap weekend i went through HELL installing ubuntu last weekend, only to have this crap.

Dude, even MS updates break things every now and then...I've had to reinstall drivers a few times after MS updates....for some reason it doesn't like my sound card....go figure...At any rate, your berating of tseliot is really out of line.  He didn't single-handly wreck havoc on the world and any problems weren't intential.  The development of Ubuntu is a team effort (and an excellent team imo).  He's just the unfortunate one taking the flack for it.  Even if was completely his fault, he's human.  Humans make mistakes.  Bet you've made quite a few in your lifetime.

---

### Post by allix on 2006-08-22
Wow, this was one major f-up... The devs may have screwed up completely but this community were there to save the day, as always. This is truly inspiring to see. :) Thanks to whoever posted the fix. 

A little tip: Install and learn how to use Lynx. Lynx is an command line webbrowser and a great asset if you happen to screw up your system. Just reboot into recovery mode and find the fix online. Much faster than booting a live cd. Oh, and learn Ctrl+Alt+F1 F2 F3 and so on... :)

---

### Post by allix on 2006-08-22
> **magnoliablossom said:**
> Even if was completely his fault, he's human.  Humans make mistakes.  Bet you've made quite a few in your lifetime.

If only everyone had the same attitude. :)

---

### Post by Raavea on 2006-08-22
Oh dear oh dear.. 

 I didn't get the error until I woke up after a nap and re-booted. Took me a few seconds to figure out how to 'log in' to the CLI.

 None of the commands I have tried that are listed in this thread have worked. I'm using my girlfriend's XP (it acts like ME) laptop.

 Thank god she went out before I rebooted! I'm starting to get her to see the light, ya know.


 Aaanyhow. I connect to the 'net via a netgear router, as we share a connection. The commands involving the /archive folder can't find the packages... D:

 What should I do? I'm still rather new to Ubuntu, and though I love re-installing it (I just enjoy starting with a clean slate, excepting my documents o'course) I only did that a few weeks ago! I'd like to have this done before my girl gets home, so she never knows!

 PS: Please excuse any errors in this post. This laptop's keyboard doesn't even CLACK. *shudder*

> **allix said:**
> (...)
A little tip: Install and learn how to use Lynx. Lynx is an command line webbrowser and a great asset if you happen to screw up your system. Just reboot into recovery mode and find the fix online. Much faster than booting a live cd. Oh, and learn Ctrl+Alt+F1 F2 F3 and so on... :)
 Thanks for this, I'll note down to install 'Lynx' asap!



EDIT: I havn't tried what [this person]("http://www.ubuntuforums.org/showpost.php?p=1408007&postcount=25") did, about to now.

---

### Post by matthew on 2006-08-22
> **frankzen said:**
> For those of us who HAVEN'T updated...how long should we wait???

ThanksProbably until you hear people saying they have successfully updated using the newest version that is being uploaded to the repos now...most likely in a few hours or tomorrow.

---

### Post by stig on 2006-08-22
> **frankzen said:**
> For those of us who HAVEN'T updated...how long should we wait???

Thanks


See the following message:
> **cstudent said:**
> Just inspect the version number of the update before installing. Avoid the update that has ubuntu10.3 in the name. You want ubuntu10.4.

---

### Post by davidshere on 2006-08-22
> **cstudent said:**
> Just inspect the version number of the update before installing. Avoid the update that has ubuntu10.3 in the name. You want ubuntu10.4.
Thanks.  That's **exactly** what I needed!

---

### Post by Badfish on 2006-08-22
I just want to link to my post here

[http://www.ubuntuforums.org/showthread.php?p=1408701#post1408701](http://www.ubuntuforums.org/showthread.php?p=1408701#post1408701)

I'm not certain, I could be terribly off-base, but right after I updated the new xserver, my ATI card completely died.  Just a word of caution.

---

### Post by allix on 2006-08-22
> **Raavea said:**
> 
 Aaanyhow. I connect to the 'net via a netgear router, as we share a connection. The commands involving the /archive folder can't find the packages... D:

 What should I do? I'm still rather new to Ubuntu, and though I love re-installing it (I just enjoy starting with a clean slate, excepting my documents o'course) I only did that a few weeks ago! I'd like to have this done before my girl gets home, so she never knows!

Maybe you could download the file in Winxp, burn it to a CD+rw and install it using dpkg -i <filename>? I'm no command line hacker but I'm getting there, things like this are great practice. :D

---

### Post by leb3000 on 2006-08-22
I imagine a lot of people who trying linux and got this update will be put off forever now.

a lot won'y even try fix the problem and just boot windows. lol mine stopped workin and i thought it was something i did

---

### Post by The Pinny Parlour on 2006-08-22
> **magnoliablossom said:**
> Dude, even MS updates break things every now and then...I've had to reinstall drivers a few times after MS updates....for some reason it doesn't like my sound card....go figure...At any rate, your berating of tseliot is really out of line.  He didn't single-handly wreck havoc on the world and any problems weren't intential.  The development of Ubuntu is a team effort (and an excellent team imo).  He's just the unfortunate one taking the flack for it.  Even if was completely his fault, he's human.  Humans make mistakes.  Bet you've made quite a few in your lifetime.

I bet you I have too. I'm not berating anyone.  I'm having a good old whinge mate.

---

### Post by Raavea on 2006-08-22
> **The Pinny Parlour said:**
> Thanks.  Sounds like a great idea. For a new comer, I'm sure it involves a heap of CLI which is just a daunting prospect.
 It's not that hard, really! ^_^ I did it. Not the /home folder, because I enjoy doing all the games and such again, but i made myself an /everything folder for my documents and the like.

 By the way, what I'm just trying is working! I typed the other stuff twice.. Maybe I made some mistake like using a comma that I wouldn't notice. xD

---

### Post by Frank Golden on 2006-08-22
> **tseliot said:**
> [SIZE="4"]HOWTO solve the problem[/SIZE]

[COLOR="Red"]UPDATE:[/COLOR]
The recent updates break the Xserver. If you have already updated Ubuntu please type the following command:
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
```
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
```

```
sudo dpkg -i xserver-xorg-core*.deb
```

If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work


**[COLOR="Red"]NOTE: 64bit users should do this:[/COLOR]**
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```
Then restart your computer
```

sudo reboot
```

Thanks tseliot,
    For the record somebody dropped the ball on this one. You however
neatly picked it up. One question what did your fix do exactly? Did it rollback the update or fix it? BTW it doesn't appear to have affected
my ATi proprietary drivers. Also I am using the i686 SMP kernel, shouldn't
the kernel at end of the first two commands in my case have been i686?
Lots I don't understand. Your fix as you wrote it worked for me. Glad 
I spotted this sticky in XP before I rebooted to Ubuntu. It was broken
and I would not have known what to do short of restoring my partimage image.

---

### Post by Adler on 2006-08-22
Well, now I know that is wasn't just something that I did! Talk about a real pain in the neck.

Adler

---

### Post by rudiz on 2006-08-22
I just install with apt-get the update.  :)

---

### Post by bignickel on 2006-08-22
I just installed the new version and it works.  Just make sure that when you update you are updating to xserver-xorg-core 1:1.0.2-0ubuntu10.4 and NOT 10.3.  If your automatic updater is telling you it's going to update to 10.3 click "Check" and it will update to 10.4.

---

### Post by Raavea on 2006-08-22
Did someone say this would break nVidia stuff? Cause mine *appears *to still be okay. Then again, it's pretty old - not quite legacy (5200) but nearly. heh

I'm back in Ubuntu! Thanks guys! Thanks for the big fat warning sign TSEliot. I wouldn't'a noticed this thread without it.

And I never even considered re-installing Windows thanks to the absolute awesomeness of the community. ^_^


> sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10Is for 64bit users though, isn't it? I'm sure I don't have 64bit.. Isn't that all new and spangly or something? My PC hasn't had a physical upgrade for yeaaars. (As ye can tell: 5200 was top-of-the-range when I bought it!)

---

### Post by ditikos on 2006-08-22
As a user (and not an active member to the linux community), I found it frustrating (I was using a very well made xfce/xubuntu desktop) and tried the windows approach --- format and play. I found it frustrating the second time also (I always thought that I had a hw card problem, so I did the update again, when I realized that the update itself was problematic), and this is an action that most xp users going to linux will probably have.

Is there an ncurses something program that can give you the latest on the sw problems that occur (like an extra bulletin)? Because ok,  the forum is the first place to find the problem, but I googled the obvious "xorg no screens found nvidia dapper" and it always links to the nvidia installation guide.

---

### Post by tseliot on 2006-08-22
> **Frank Golden said:**
> Thanks tseliot,
    For the record somebody dropped the ball on this one. You however
neatly picked it up. One question what did your fix do exactly? Did it rollback the update or fix it? BTW it doesn't appear to have affected
my ATi proprietary drivers. Also I am using the i686 SMP kernel, shouldn't
the kernel at end of the first two commands in my case have been i686?
Lots I don't understand. Your fix as you wrote it worked for me. Glad 
I spotted this sticky in XP before I rebooted to Ubuntu. It was broken
and I would not have known what to do short of restoring my partimage image.

my 1st suggestion installs the latest update (which might not have been uploaded to all the servers yet)

my 2nd suggestion downgrades to the previous (working) package


[COLOR="Red"][SIZE="3"]**Xserver updates might break openGL. That's why I suggest reinstalling the driver too**[/SIZE][/COLOR]

---

### Post by cstudent on 2006-08-22
Just a little fyi: If you do not compile your own updated drivers, you should not need to install the dev package:

xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb

---

### Post by Snowmayne on 2006-08-22
LOL and here I thought it was something *I* did last night that done gone and brokeded my 'puter ;) Good to know that Ubuntu/Linux ain't more better than Windows :)

Now I just have to wait until I get home to run the fix and get back to learning how to mess up my PC with ubuntu even more. :D :mrgreen:

---

### Post by tseliot on 2006-08-22
> **Raavea said:**
> Is for 64bit users though, isn't it? I'm sure I don't have 64bit.. Isn't that all new and spangly or something? My PC hasn't had a physical upgrade for yeaaars. (As ye can tell: 5200 was top-of-the-range when I bought it!)

That works on all architectures.

The links which I have posted (my 1st suggestion) work only with 32bit operative systems instead

---

### Post by Raavea on 2006-08-22
> **tseliot said:**
> my 1st suggestion installs the latest update (which might not have been uploaded to all the servers yet)

my 2nd suggestion downgrades to the previous (working) package


[COLOR="Red"][SIZE="3"]**Xserver updates might break openGL. That's why I suggest reinstalling the driver too**[/SIZE][/COLOR]

...What's OpenGL? I know it's something important.. But what exactly? Now that ubuntu is working again, what should I do to be sure it don't kill mah PC? Should I upgrade to the 10.4 version? Or do I need to do other things? Will it have done something bad to my nVidia that I wouldn't immediately notice? *(I can usually tell as my screen is ancient and goes mad when the drivers are not installed, and my menu is slower to open, and I would expect the big white nVidia splash thing to just.. not be there)*

[B]
 Augh, late! Gotta run! x.x Will check up when I get back. Hold in there if you aren't fixed yet - this community always pulls you through![/B]

---

### Post by gommle on 2006-08-22
Now my gnome-terminal doesnt work after the reboot. How can i get it back?

I cant apt-get it because of "E: Broken Packages" (translated).

---

### Post by glowplug on 2006-08-22
Thank you once again tseliot - a rollback and it worked 100%.
OK so I was down for 1/2 an hour, mistakes happen - we all make them.

Some weeks ago some MS people realised they'd made a mistake but they'd had time to think it through.

After their rollback I was unable to get to my outlook pst file - I'd had it shared between outlook on xp64 and outlook on xp32.
I reinstalled office on each o/s but outlook still wouldn't open - said it had no permission.
I tried substituting the pst, hacking the registry but nothing worked.
Reinstalled xp32 and it wiped out the file indexes for the other 2 partitions - over 150 gig.
It took 8 hours to run a recovery then 2 days to rebuild to where I'd been up to.
Of course I had backups but it's not the point.

The xorg update is the first such mistake I've seen since I've been on ubuntu - about 8 months.
I've made plenty worse in that time but you've always been there with fast and solid support.

Thank you.

---

### Post by matt.vapor on 2006-08-22
> **Kilz said:**
> ](*,)  I was working on getting the new ATI drivers working. I bashed my head into a wall for a few hours thinking it was something I did. ](*,) 
Thanks for saving me more pain

I was doing the exact same thing and thought the same thing too!!!!!!

---

### Post by frrobert on 2006-08-22
Thanks for the fix.  I had installed the update but hadn't rebooted yet, so I then installed the fix, rebboted and everything was good.

---

### Post by ischg on 2006-08-22
Thanks tseliot for making this issue sticky. I don't want to rant, but it's been a very long time since the buggy xserver-xorg-core patch went online (I downloaded it yesterday 4pm and now it's 8:40am). I'm really grateful to this forum, since the reaction was super-fast (after ](*,) for about 2 hours).

Still, isn't there something like an emergency system to pull ubuntu updates in place? It seems odd that a broken package can live for 16+ hours while many, many people get really distressed with ubuntu? As a distro, this is about the worst-case scenario that can happen. Don't get me wrong, I love ubuntu and won't switch, but I bet this hiccup really upset a bunch of people (especially ppl who aren't used to the commandline).

---

### Post by The Pinny Parlour on 2006-08-22
ANYONE...Got ANY ideas on what i can edit to get xserver-xorg up and running???

---

### Post by TomG on 2006-08-22
Arrrgh I just found this topic and... the thing that made me crazy this last 2 days :(
Too late for me. I tried to repare without success so I had to re-install... I lose lot of time. I will be more prudent next time :)

---

### Post by Elis on 2006-08-22
Thanks tseliot, the fix worked fine =D>  Luckily I looked in the Ubuntuforums before I was about to reinstall the whole OS.
But it wasn't so easy to write in those 3 lines correct for me, got it wrong a couple of times, first write them on a piece of paper and then in the computer. So used to just copy and paste. Anyway, thanks :)

---

### Post by Uncle Spellbinder on 2006-08-22
As I stated on the lengthy, now closed, thread. I was lucky and did not update to the "bad" X because I thought I should check here first. Just a gut feeling, I guess. Anyway, I just updated through the *update manager*. All went fine. No problems what so ever.

---

### Post by wolfchri on 2006-08-22
**[SIZE="5"]HOW TO prevent faulty security updates from happen:[/SIZE]**

Very simple, folks:

1. Publish updates first in a single repository that is not part of the official Ubuntu repos in the sources.list but can be added by those who want to test and take the risk. Call this Repo "PreCache" or whatever, but make it publicly accessible for the testing community. 

2. Delay copying from "PreCache" to the live repos and mirrors by 24h. 

That should prevent such desasters, Prio 1 bugs like an X.Org crash from slipping through undedected.

---

### Post by h00s on 2006-08-22
Updated to 10.4. Everything is fine.

---

### Post by kjkrum on 2006-08-22
> 1. Publish updates first in a single repository that is not part of the official Ubuntu repos in the sources.list but can be added by those who want to test and take the risk. Call this Repo "PreCache" or whatever, but make it publicly accessible for the testing community.

2. Delay copying from "PreCache" to the live repos and mirrors by 24h.

That should prevent such desasters, Prio 1 bugs like an X.Org crash from slipping through undedected.

Or just, you know, install and reboot yourself before you upload "bugfixes" for general distribution.  Seriously, how the heck does something like this get through?  Greased Turkey, anyone?

Where can I get 10.4?  apt-get update/upgrade found nothing to update as of five minutes ago.

---

### Post by prizrak on 2006-08-22
I guess now Ubuntu is ready for the desktop ;) (Anyone remember the WinME update that destroyed the OS)

---

### Post by warbread on 2006-08-22
> **magnoliablossom said:**
> Dude, even MS updates break things every now and then...I've had to reinstall drivers a few times after MS updates....for some reason it doesn't like my sound card....go figure...At any rate, your berating of tseliot is really out of line.  He didn't single-handly wreck havoc on the world and any problems weren't intential.  The development of Ubuntu is a team effort (and an excellent team imo).  He's just the unfortunate one taking the flack for it.  Even if was completely his fault, he's human.  Humans make mistakes.  Bet you've made quite a few in your lifetime.

I agree.  Not only do M$ updates break Windows, but how quickly does M$ get to fixing the problem?  Not as quickly as the Ubuntu community, that's for sure.

---

### Post by brickhead20 on 2006-08-22
Atleast its not ATI's fault for once. Thats refreshing :rolleyes: 

Hope this is going to work

---

### Post by deepspring on 2006-08-22
Dammit! :twisted: 

If only I had of read this thread about one and a half hours ago. I was installing Xgl+Compiz when X broke. I thought I stuffed something really badly. I ended up doing a full reinstall.

Oh well... practice makes perfect [-X :biggrin:

---

### Post by Lonthong on 2006-08-22
How come update 10.4 is not available for AMD64 yet?? :confused:

---

### Post by LWP on 2006-08-22
TSEliot, you turned my frown upside-down.  Took 5 minutes and was back up and running, no problem (luckily I had a spare computer with which I could browse to find your thread).  Nice work!

---

### Post by oskar2000 on 2006-08-22
it's fixed

I just did another update, and it's fine again.

$sudo apt-get update
$sudo apt-get upgrade

that should fix it now.

PS: What a pointless steaming heap of posts. :roll:

---

### Post by JeremyWorst on 2006-08-22
> **tseliot said:**
> **[COLOR="Red"][SIZE="3"]UPDATE: the problem has been fixed but you should wait to upgrade until xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb is uploaded to the ubuntu servers.[/SIZE][/COLOR]**

OR you can install the new packages manually:
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)
[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb)

I can't connect my laptop to the Internet here (I'm using my desktop right now) and would like to try the manual install, but need a little help.  I've copied the files to my flash drive, but don't know where to find the flash drive using the command line.  An icon usually appears on my Desktop, but of course no Desktop is available (yet).  I thought I'd find it in /media, but it isn't there.  Assuming somebody can tell where it is, then what commands do I run on the two files?

Thanks! - Jeremy

---

### Post by hbostrom on 2006-08-22
Just wanted to say thanks, tseliot! Following your instructions, I was up and running within two minutes. I share the general frustration expressed in this thread, though...

---

### Post by mommebu on 2006-08-22
after plugging it in check in /var/log/messages for the device it got connectged to, usually s.thing like /dev/sda*, then you can mount it manually.

---

### Post by ThrobbingBrain66 on 2006-08-22
as of 9am Central Standard Time the xserver-xorg10.4 update is in the repos.  good luck eveyone!

---

### Post by Tails Prower on 2006-08-22
.

---

### Post by matthew on 2006-08-22
> **ThrobbingBrain66 said:**
> as of 9am Central Standard Time the xserver-xorg10.4 update is in the repos.  good luck eveyone!It's still populating some parts of the world (like mine...) but it is coming online.

---

### Post by mattlach on 2006-08-22
> **allix said:**
> 
A little tip: Install and learn how to use Lynx. Lynx is an command line webbrowser and a great asset if you happen to screw up your system. Just reboot into recovery mode and find the fix online. Much faster than booting a live cd. Oh, and learn Ctrl+Alt+F1 F2 F3 and so on... :)

Agreed, but I am actually preferential to links2, which is really just an enhanced lynx.

---

### Post by r_mano on 2006-08-22
tseliot, I would like to add myself to the thanks. Great work here. 

Just one little thing: I found this thread almost by luck. Information on a problem on this scale should be available somewhere under [www.ubuntulinux.org](www.ubuntulinux.org), directly or as a link.

Said that, probably I'd never noticed it, if not for my 11-month old stumping on the power cord... ;)

---

### Post by hexion on 2006-08-22
> **JeremyWorst said:**
> I can't connect my laptop to the Internet here (I'm using my desktop right now) and would like to try the manual install, but need a little help.  I've copied the files to my flash drive, but don't know where to find the flash drive using the command line.  An icon usually appears on my Desktop, but of course no Desktop is available (yet).  I thought I'd find it in /media, but it isn't there.  Assuming somebody can tell where it is, then what commands do I run on the two files?

Thanks! - Jeremy

Jeremy, usually flash drives are in /dev/sda or /dev/sdb
If your pendrive has more than 1 partitions (not too normal) then it's in /dev/sda1 , /dev/sdb1, /dev/sda2... 

So for doing what you want, you should:

> cd ~
mkdir pendrive
mount /dev/sda -t vfat pendrive

And then your files should be there.
If it doesn't work, try with sdb, sda1... as I told you before.

---

### Post by brickhead20 on 2006-08-22
All is good. The nice thing about problems with ubuntu and other linux distros, is if something breaks, you can be damned sure that theres plenty of other people equally as amused as you, and you can be damned sure that by the time windows or your backup loads (which is a sufficiently long time), there will be something on the forum to help you. (Actually I should learn to use lynx instead :rolleyes: )

I think some people should be more glad that linux has the CLI. When Xserver breaks, atleast there is the almost unbreakable command line to help pick it up again. Thats a luxury windows users don't share. Yes Xserver can be a pain, especially if you live with something labelled 'ATI', but at least at the core, your system still runs, and there will be something on the forum to help you get it running from it. Moreover, to those it concerns, you should be more grateful for people who dedicate their time to post up threads on how to fix things...

---

### Post by The Pinny Parlour on 2006-08-22
OMG I got it going.  i nano'ed my *** off but I finally entered something that xserver-xorg liked.  bout time too.  PC nearly went out the window.

---

### Post by Klaidas on 2006-08-22
Why did we get an update that breaks everyone's X in the first place? :mad:

---

### Post by mattlach on 2006-08-22
> **tseliot said:**
> my 1st suggestion installs the latest update (which might not have been uploaded to all the servers yet)

my 2nd suggestion downgrades to the previous (working) package


[COLOR="Red"][SIZE="3"]**Xserver updates might break openGL. That's why I suggest reinstalling the driver too**[/SIZE][/COLOR]

Oh.   You meant the GLX driver?   I thought you were talking about the kernel-driver (and I was trying for the life of me to figure out why)

---

### Post by Sfac on 2006-08-22
Look like xserver-xorg-core 1:1.0.2-0ubuntu10.4 is just released. Anyone tried it?

---

### Post by The Pinny Parlour on 2006-08-22
> **Sfac said:**
> Look like xserver-xorg-core 1:1.0.2-0ubuntu10.4 is just released. Anyone tried it?

I just installed it, goodness know why.  I will reboot in a moment.

---

### Post by alligator424 on 2006-08-22
I simply don't understand why that bad xorg update is still AVAILABLE TO CRASH MANY xWINDOWS SYSTEMS...

any way, it is a good idea to use backups of ubuntu partitions, for example made with this nice program: g4l (ghost for linux...)

GET IT HERE: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by missmoondog on 2006-08-22
> **Sfac said:**
> Look like xserver-xorg-core 1:1.0.2-0ubuntu10.4 is just released. Anyone tried it?

about to right now. better not break stuff again!! ](*,)

oh boy! downloading at a whopping 9000B's!!

---

### Post by matthew on 2006-08-22
> **Klaidas said:**
> Why did we get an update that breaks everyone's X in the first place? :mad:Human error? I know one person who had 4 computers that were NOT affected when upgraded. Just one of those things you try to avoid, but sometimes don't.

---

### Post by Klaidas on 2006-08-22
Well, I understand that we all make mistakes :)
It's just that it's main repo, it's stable release...

---

### Post by The Pinny Parlour on 2006-08-22
Well, I just installed the latest update and rebooted.  Suprise Suprise... It all CRASH 'N" BURNED.  Xserver-xorg died AGAIN.

LIVID?  yes.

---

### Post by Dr. Feelgood on 2006-08-22
> **brickhead20 said:**
> I think some people should be more glad that linux has the CLI. When Xserver breaks, atleast there is the almost unbreakable command line to help pick it up again. Thats a luxury windows users don't share.

Exactly why I'm using Linux now.  As soon as windows stopped haveing DOS available as a shell I knew it was time for a new OS.  I might be alone here but I loved DOS.  Anyway, thanks for the help TS, this one could have gotten very ugly.

---

### Post by Klaidas on 2006-08-22
The update manager says...
[QUOTE=Update manager because the damn X got broken]Error:BrokenCount >0[/QUOTE]

How should I fix that?

---

### Post by DaveRowell on 2006-08-22
Bless you sir!  ;-)

A prompt efficient fix for a pesteriferous problem!

Thanks  Dave Rowell

---

### Post by missmoondog on 2006-08-22
> **The Pinny Parlour said:**
> Well, I just installed the latest update and rebooted.  Suprise Suprise... It all CRASH 'N" BURNED.  Xserver-xorg died AGAIN.

LIVID?  yes.

yay! my update worked!! =D>

---

### Post by r4ik on 2006-08-22
> **Sfac said:**
> Look like xserver-xorg-core 1:1.0.2-0ubuntu10.4 is just released. Anyone tried it?

Installed and rebooted no problems.

---

### Post by bigblondbear on 2006-08-22
Hoi all,

Although I should have known better I must admit that I'm surprised about two things. My first surprise is the number of unpleasant rants about this update problem. Have those people perhaps forgotten how long it usually takes the makers of another OS (Windows) to fix problems they create? True, you probably won't notice immediately after an update but your system may be compromised as a result of yet another vulnerability introduced. Have those people forgotten they've gotten all this for free?

Even though I appreciate the frustration something like this can cause, I think it is not on to start throwing mud or worse.

My second surprise is the slowness of Canonical's response. Surely some alarmbells must have rang and a "Breaking News" ;) message on Ubuntu's website would have been appropriate, including a short description of how to fix the problem (saves people from having to read the many posts). Most ordinary people (those I'm trying to convince to migrate to Unbuntu) would be up shit creek without a paddle after applying this update.

Of course, the 10.3 release should also have been removed from the servers... (my system still suggests I upgrade) to prevent any further trouble.

I do think though that something good will come out of this... chances something like this will happen again have just become a lot less and perhaps we'll even get an easy to use (read for non technical people) mechanism to revert to previous versions.

with regards,
BBB

---

### Post by mattlach on 2006-08-22
> **The Pinny Parlour said:**
> 
LIVID?  yes.

Throwing computers out windows, being livid...

Ever think you might have anger issues, man?

Going to get all pissed off just because a computer doesnn't boot?   What are you going to do when you have something really bad happen?

[Here's a link for you](http://www.youtube.com/watch?v=kBVmfIUR1DA) :p

---

### Post by matthew on 2006-08-22
I've been watching the bug report [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153) and it looks like the fix is working for some but not for all. I still recommend everyone keep/reinstall the earlier package (xserver-xorg-core=1:1.0.2-0ubuntu10) and wait for a day or two before upgrading while the devs sort things out.

---

### Post by The Pinny Parlour on 2006-08-22
Is there a way of totally and completely uninstalling xserver-xorg and reinstalling it from scratch?

---

### Post by brickhead20 on 2006-08-22
> **Dr. Feelgood said:**
> Exactly why I'm using Linux now.  As soon as windows stopped haveing DOS available as a shell I knew it was time for a new OS.  I might be alone here but I loved DOS.  Anyway, thanks for the help TS, this one could have gotten very ugly.

Yeah it was better than windows now. I don't think it was quite as good as the linux CLI, but not bad anyway, you knew you could fix stuff with it, you just had to learn how. Its cool that pretty much whatever you can do in the graphical user interface, you can do in the command line too. Its simple and safe.

---

### Post by givré on 2006-08-22
> **bigblondbear said:**
> 
My second surprise is the slowness of Canonical's response. Surely some alarmbells must have rang and a "Breaking News" ;) message on Ubuntu's website would have been appropriate, including a short description of how to fix the problem (saves people from having to read the many posts). Most ordinary people (those I'm trying to convince to migrate to Unbuntu) would be up shit creek without a paddle after applying this update.

Of course, the 10.3 release should also have been removed from the servers... (my system still suggests I upgrade) to prevent any further trouble.

with regards,
BBB
Not so slow than that finaly, The fix is release since a long time now. It takes just some time to hit all the mirrors.

---

### Post by The Pinny Parlour on 2006-08-22
> **matthew said:**
> I've been watching the bug report [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153) and it looks like the fix is working for some but not for all. I still recommend everyone keep/reinstall the earlier package (xserver-xorg-core=1:1.0.2-0ubuntu10) and wait for a day or two before upgrading while the devs sort things out.

Some constructive critisism then.  The Devs should haul out making these updates available then.  Why are they letting these through?

---

### Post by philipgm on 2006-08-22
The correction to the update has reached the repos. I've downloaded and installed it and still have an Xserver after a reboot. Unlike with 10.3 which killed my Xserver and had me taking the machine apart and cursing the second hand graphics card I bought on ebay! Not a faulty card of course!

Of course, just because the revised update works for me doesn't mean it will work for everyone else, but given the speed it's appeared at I think the problem was pretty trivial (in a programming sense that is!)

---

### Post by givré on 2006-08-22
> **matthew said:**
> I've been watching the bug report [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153) and it looks like the fix is working for some but not for all. I still recommend everyone keep/reinstall the earlier package (xserver-xorg-core=1:1.0.2-0ubuntu10) and wait for a day or two before upgrading while the devs sort things out.
I don't think so. Those people don't seams to speak about the new version.
Just my 2 cents

---

### Post by Klaidas on 2006-08-22
> Although I should have known better I must admit that I'm surprised about two things. My first surprise is the number of unpleasant rants about this update problem. Have those people perhaps forgotten how long it usually takes the makers of another OS (Windows) to fix problems they create? True, you probably won't notice immediately after an update but your system may be compromised as a result of yet another vulnerability introduced. Have those people forgotten they've gotten all this for free?

True, BUT...
Windows is another story...
We all make mistakes. This was a mistake. Ok, I'm using linux on a home PC only about 30% of time, so I guess this update didn't really do damage to me.

But imagine if some system administrator which is "linux rule, win suck, open source forever" dude installs ubuntu on 1000 PCs for a company.
People update and they break X. Company almost stops working (We all know how computer are used these days)... OUCH! That's not so good.
Besides, this is not backports, universe/multiverse. It's MAIN. Shouldn't the package pass testing before getting to the updates?

---

### Post by bigblondbear on 2006-08-22
> **The Pinny Parlour said:**
> Is there a way of totally and completely uninstalling xserver-xorg and reinstalling it from scratch?

No need. Just logon, then type on the commandline:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

Thats all. Not too complicated really -once you know it 8-)

---

### Post by matthew on 2006-08-22
> **givré said:**
> I don't think so. Those people don't seams to speak about the new version.
Just my 2 cents:) You are probably right...my statement might help dissuade an impatient person from installing an update before the newest update-fix hits their mirror. :)

---

### Post by JeremyWorst on 2006-08-22
> **hexion said:**
> Jeremy, usually flash drives are in /dev/sda or /dev/sdb
If your pendrive has more than 1 partitions (not too normal) then it's in /dev/sda1 , /dev/sdb1, /dev/sda2... 

So for doing what you want, you should:



And then your files should be there.
If it doesn't work, try with sdb, sda1... as I told you before.

Thanks!  That works, so now I can see the pendrive and the files.  Now what do I do with the files:
xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb

---

### Post by Tyltyl on 2006-08-22
I updated without thinking and I got stuck with the bug. 
BTW THANKS A LOT TSELIOT!!! You saved me :KS =D> 

It's all ok now.

---

### Post by MachineBucket on 2006-08-22
I'm using the 64 bit version of Dapper and do not have an continuos internet conection. I do have an external USB modem but I don't know how to connect through the command line. I have already tried the method of installing the previous version supposedly saved on the HD. However the directory does not seem to exist and have tried the command 3 times and checked spelling.

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

Is there any way I can download a binary on another machine and tranfer via cd or USB drive? Or how can I connect my external modem  using the command line? I was using gnome-ppp to dial out since it doesnt need any special drivers. Thanks. :)

---

### Post by matthew on 2006-08-22
> **Klaidas said:**
> But imagine if some system administrator which is "linux rule, win suck, open source forever" dude installs ubuntu on 1000 PCs for a company.
People update and they break X. Company almost stops working (We all know how computer are used these days)... OUCH! That's not so good.Those people are generally smart enough to install updates on ONE computer first and give it a thorough testing before rolling it out to all the company's computers.

---

### Post by davidshere on 2006-08-22
> **Sfac said:**
> Look like xserver-xorg-core 1:1.0.2-0ubuntu10.4 is just released. Anyone tried it?
I have, and rebooted.  Everything works fine.

---

### Post by nocturn on 2006-08-22
And the story hits Digg.

This is some serious bad press for Ubuntu...

---

### Post by japurcell on 2006-08-22
If we haven't upgraded yet, what's the best thing to do to save a headache?:confused:

---

### Post by matthew on 2006-08-22
> **japurcell said:**
> If we haven't upgraded yet, what's the best thing to do to save a headache?:confused:Wait a day or two and don't upgrade anything right now.

---

### Post by bhdenterprises on 2006-08-22
oh my God. i don't know the bug has to do with the Xserver update! my system broke this morning and i was really terrified. thought reinstalling everything will solve the problem but it isnt so i thought it must be the Gnome desktop... i reinstalled the server version then apt-get the kubuntu-desktop and still i dont have a desktop.. my god its a good thing i logged on to my friend's computer and check the forum... ihaven't tried it yet but i guess i have to go home and try it myself..

---

### Post by Klaidas on 2006-08-22
If it hit digg, it will probably hit /.

---

### Post by loserboy on 2006-08-22
can I ask what time this update came through, because my xserver is broken but i thought it had to do with me trying to install suse last night. my xserver has been screwed since about 1:30am central time.

or is there a way to find out which problem it is by getting a report and reading it back?

thanks sorry if this was already asked i only read like 3 pages.

---

### Post by bigblondbear on 2006-08-22
> **Klaidas said:**
> True, BUT...
Windows is another story...
We all make mistakes. This was a mistake. Ok, I'm using linux on a home PC only about 30% of time, so I guess this update didn't really do damage to me.

But imagine if some system administrator which is "linux rule, win suck, open source forever" dude installs ubuntu on 1000 PCs for a company.
People update and they break X. Company almost stops working (We all know how computer are used these days)... OUCH! That's not so good.
Besides, this is not backports, universe/multiverse. It's MAIN. Shouldn't the package pass testing before getting to the updates?

It wouldn't be much of a system administrator to roll out updates without testing those updates. I also think updates applied to 1000 PCs for a company are done in a different way (for instance by using your own copy of the repositories that are only updated after verified to be correct) and/or are not done by the end users themselves at all.

It also wouldn't be much of a system administrator if (s)he is not able to find the cure online... (hence my suggestion that Canonical makes finding the solution obvious).

---

### Post by bigblondbear on 2006-08-22
> **Klaidas said:**
> True, BUT...
Windows is another story...
We all make mistakes. This was a mistake. Ok, I'm using linux on a home PC only about 30% of time, so I guess this update didn't really do damage to me.

But imagine if some system administrator which is "linux rule, win suck, open source forever" dude installs ubuntu on 1000 PCs for a company.
People update and they break X. Company almost stops working (We all know how computer are used these days)... OUCH! That's not so good.
Besides, this is not backports, universe/multiverse. It's MAIN. Shouldn't the package pass testing before getting to the updates?

It wouldn't be much of a system administrator to roll out updates without testing those updates. I also think updates applied to 1000 PCs for a company are done in a different way (for instance by using your own copy of the repositories that are only updated after verified to be correct) and/or are not done by the end users themselves at all.

It also wouldn't be much of a system administrator if (s)he is not able to find the cure online... (hence my suggestion that Canonical makes finding the solution obvious).

Having said that, obviously Canonical should have tested this update before uploading it to the mirrors. As you said yourself: it was a mistake...

---

### Post by Torstein_V on 2006-08-22
Thank God I'm not the only one who experienced this problem. 

I was working on getting K9Copy to work, when the update notifier popped up on my desktop (Ubuntu 6.06). It told me I had one more update for my system, which I updated yesterday. Update Manager told me the xserver.org was ready to install, and so I did. When I restarted my computer, Ubuntu through me right into SHELL, and told me that xserver.org was broken, and that my LCD couldn't be detected by the system.

So, what did I do, except from hyperventilate? I went outdoors, got some fresh air while thinking of my dad's important and possibly lost documents,  went back to the computer, and did this:

```
sudo apt-get update
sudo apt-get upgrade
```

Synaptic told me that there was one more update for my system, and that was no other update than the fixed xserver.org library. I installed, rebooted, and voilá! My GUI was back.

So, as many others here, I too wonder what the f...amily is going on here?

---

### Post by euxneks on 2006-08-22
Is there some sort of CLI program where we can see the previously installed updates and rollback to a last known good state? 

I was tearing my hair out last night thinking I fudged up X with my xorg.conf =P 

Just wish I had a history log of what had just been installed because I had a feeling it was the last update.


Thanks,

---

### Post by nocturn on 2006-08-22
> **bigblondbear said:**
> 
Having said that, obviously Canonical should have tested this update before uploading it to the mirrors. As you said yourself: it was a mistake...

What bothers me most is that the faulty update wasn't pulled immediately after the first problems where reported.  In fact, it remained active until the fix was uploaded.

An immediate pull would have prevented a lot of breakage.

---

### Post by nlogax on 2006-08-22
Ubuntu need to seriously consider a GRUB option that will rollback packages installed by apt-get/aptitude to the previous snapshot/known good checkpoint.

I am very disappointed that this bug was allowed through, and can only imagine all the people recently upgraded to Ubuntu by helpful friends that are now staring at the text mode console and wondering what the hell they've done - how will *they* get a fix for this?

---

### Post by mattlach on 2006-08-22
> **nocturn said:**
> What bothers me most is that the faulty update wasn't pulled immediately after the first problems where reported.  In fact, it remained active until the fix was uploaded.

An immediate pull would have prevented a lot of breakage.

Agreed.

---

### Post by Klaidas on 2006-08-22
Yet another proof that you must have a LiveCD by hand, even if you dual boot :roll:

---

### Post by Uncle Spellbinder on 2006-08-22
> **nocturn said:**
> What bothers me most is that the faulty update wasn't pulled immediately after the first problems where reported.  In fact, it remained active until the fix was uploaded.

An immediate pull would have prevented a lot of breakage.

"Ubuntu is free. They owe us nothing as we paid nothing." I've seen this in several responses to posts like yours. While, in general, I tend to agree with that statement. There is such a thing as common decency and responsibility. The very moment breakage reports started, the update should have been pulled. It was quite obvious that the update affected *everyone* who updated. Leaving it in the repos  after reports started is irresponsible at the least, leaving it in the repos until a fix was uploaded borders on insanity.

---

### Post by matrooswolf on 2006-08-22
Just confirming that with the latest update, everything works fine ...
 Let's get the good vibes back ;)

---

### Post by davidshere on 2006-08-22
If I'm not a 64 bit user, can I still run this command?



sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

---

### Post by JeremyWorst on 2006-08-22
OK, I'm back up and running.  I DL'd the files:
xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb

using the links tseliot posted.  I ran:
sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb

and then rebooted.  Everything OK now.

-Jeremy

---

### Post by tseliot on 2006-08-22
> **davidshere said:**
> If I'm not a 64 bit user, can I still run this command?



sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

Sure

---

### Post by MachineBucket on 2006-08-22
I'm using the 64 bit version of Dapper and _do __not _have an continuous internet conection. I do have an external USB modem but I don't know how to connect through the command line. I have already tried the method of installing the previous version supposedly saved on the HD. However the directory does not seem to exist and have tried the command 3 times and checked spelling.

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

Is there any way I can download a binary on another machine and tranfer via cd or USB drive? Or how can I connect my external modem  using the command line? I was using gnome-ppp to dial out since it doesnt need any special drivers. Thanks. :)

---

### Post by George_S on 2006-08-22
Instead of going through 22+ pages of messages, can one of of the admins simply post an announcement like this one:

"New version: 1:1.0.2-0ubuntu10.4 is safe to install"

I know this update is available because it's flashing on my screen right now. However, I don't want to do fixes any more (at least not today).

---

### Post by The Pinny Parlour on 2006-08-22
Again, FINALLY  after non-stop nano'ing in xorg.conf for most of this evening, i have gotten a broken X to work again.  Updates are notifiying me to install xserver-xorg updates.  ummm no thanks.

Computer is staying on till I get home tomorrow from work, then I will back the blasted thing up.

---

### Post by anindya_m on 2006-08-22
The 64 bit repository now shows a 10.4 update to xserver-xorg. Has any one tried this on an AMD64 nvidia system ?

---

### Post by saladasalad on 2006-08-22
> **bigblondbear said:**
> It wouldn't be much of a system administrator to roll out updates without testing those updates.

And what sort of maintainer releases updates without first testing those updates?

---

### Post by Torstein_V on 2006-08-22
Agree with that, "The Pinny Parlour". It is when things like this occur we get reminded on backing our systems up.

I noticed someone recommended g4l as a backup tool for Ubuntu. [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I think I'll give it a try, unless someone else has a better recommendation?

About backups, does anyone know if Ubuntu ever will get a backuping tool like Apple's TimeMachine?

---

### Post by glotz on 2006-08-22
Hey there. Just 'victim' of this and wanted to check out the reaction on the forums. What I did was simply after seeing the error, I logged in and typed
[B]sudo apt-get update
sudo apt-get upgrade[/B] and finally
**startx**

---

### Post by dca on 2006-08-22
Did this glitch only affect nVidia & ATi driven systems because I updated first thing this morning (Eastern Time, US) on my Dell Inspiron (POS) 1150 that uses generic Intel Graphics Controller and it worked fine....

---

### Post by Owdy on 2006-08-22
> **tengil said:**
> 
Ubuntu is losing lots of users today :-( That is so true. 
Unbelievable hassle from Ubuntu. This should be stable release. What are normal user do now. They dont have no idea what to do with blue screen of death from X. __

---

### Post by towsonu2003 on 2006-08-22
> **George_S said:**
> Instead of going through 22+ pages of messages, can one of of the admins simply post an announcement like this one:

"New version: 1:1.0.2-0ubuntu10.4 is safe to install"

I definitely agree...

---

### Post by mtn on 2006-08-22
I think it would have been a good idea to send out an email to all registered forum users warning of this problem. I got stung with this this morning, tho I checked my email first so If there had been a warning I could have held off. Just a suggestion!

---

### Post by Stinger on 2006-08-22
Thanks tseliot ! 
You saved my day , I just saw your howto before I left work , did a quick print out and was able to get X up and running in next to no time when I got back home.
Thanks again.
I really hope the developers have learned a lesson :oops: :oops: , so this or something similar won't happen again.

---

### Post by anindya_m on 2006-08-22
While it is true this has been a hassle, other linux distributions have also caused such trouble at times. I still remember one Red Hat 7 kernel update which completely broke sound on all the machines (6 of them) which we installed it on. So let's not be too hard on Ubuntu.8)

---

### Post by pepolez on 2006-08-22
and to think i just spent at least 6 hours trying to fix it, only to find it wasn't something i'd done (for once). ](*,) 

ah well, i guess at least i've got a fresh install now

oh the bright side, at least automatix installs in 'blocks' so i can listen to music while watching automatix scroll by installing stuff and rsync scroll by copying ut2004 as well as various other boring progress bars.

---

### Post by sbassett on 2006-08-22
> **dca said:**
> Did this glitch only affect nVidia & ATi driven systems because I updated first thing this morning (Eastern Time, US) on my Dell Inspiron (POS) 1150 that uses generic Intel Graphics Controller and it worked fine....

The Intel chipsets were the main reason for the release of this package, so hopefully those users should be fine. I am just astounded that this made it through, especially with Dapper, Ubuntu's LTS release. This is just not a good image to put forward at this point and time.:(

---

### Post by wagerrard on 2006-08-22
For the sake of clarity, it's worth remembering that people whose Ubuntu machine is their only machine have no way to access this forum. Even if their net connection is up, odds are they've never heard of Lynx.  For those, like me, who run wireless and depend on nm-applet to set it up, an X crash keeps us off the network.

Not a good show for a distribution that makes such a point about getting non-geeks on board.

---

### Post by 9_Below_Zero on 2006-08-22
Hi tseliot,
thank you very much for your help!:eek: 
Don't worry about some bad comment... they are only ridiculous... :mad: 

9_Below_Zero

---

### Post by fegor on 2006-08-22
Ok, thanks tseliot, but don't work with "nvidia" driver, only "nv" driver is functionally :(

---

### Post by pepolez on 2006-08-22
> **wagerrard said:**
> For the sake of clarity, it's worth remembering that people whose Ubuntu machine is their only machine have no way to access this forum. Even if their net connection is up, odds are they've never heard of Lynx.  For those, like me, who run wireless and depend on nm-applet to set it up, an X crash keeps us off the network.

Not a good show for a distribution that makes such a point about getting non-geeks on board.

my first thought when X went down and i couldn't fix it was these forums. but of course, i can't view them in lynx (something to do with js and redirects i suspect)

---

### Post by kakashi on 2006-08-22
you know. i think the whole lts nonsense is plain stupid. 
this update would never have gone through if there was community testing. the dev don't have time to gug check the update. if only it had been realeased in beta to the community and checked for a few weeks. 

sigh. oh well. 
another (preemptive) solution is to remove the dapper-update for your repos. FOREVER
and don;t update also

---

### Post by The Pinny Parlour on 2006-08-22
> **sbassett said:**
> The Intel chipsets were the main reason for the release of this package, so hopefully those users should be fine. I am just astounded that this made it through, especially with Dapper, Ubuntu's LTS release. This is just not a good image to put forward at this point and time.:(

I would be certain that there is some high up wrist slapping going on right now.  The hard work of countless people trying to spread the word just went horribly pear-shaped.  

I am relatively new to linux and if you go back 20 pages, you will see I was pretty annoyed at what has happened.   I'm just a persistant bugger and have learned what to do (quickly), to get my ubuntu box going.   I'm sure newbies are just throwing their arms up in disgust at the the PC and thinking about the person that put them on to ubuntu.

---

### Post by bhdenterprises on 2006-08-22
guys, my system is now running after downgrading the xserver-xorg-core. but now the system notification area reports that it has still 16 package updates and im afraid that if i do that something will go wrong again. im using kde desktop now...

---

### Post by viper on 2006-08-22
I think that we tend to get really upset at these guys that compile and oversee the updates, yet we fail to realize that this is the best Linux distro around for such a wide audiance. My thoughts are give them a break. I had the same issue rebooted this morning and blah :(  no GUI, checked the forums (first port of call!) and a few hours later i typed "sudo apt-get upgrade" and presto all was as back to normal. Thanks to all that got onboard and helped out us newbs especially tseliot.......

---

### Post by stig on 2006-08-22
Hello tseliot,
I asked earlier how we would know when it was safe to use the update and someone replied saying "When version 10.4 appears". I had downloaded 10.3 earlier today, suffered the crash, then followed the "downgrade" instructions on this thread and quickly recovered.

Now my updater has lit up again, so I thought great, here is 10.4 - but when I looked it was offering me 10.3 again!

Is this the "bad" update or have the developers given the repaired file the 10.3 number?

Thanks for the all the info!

---

### Post by The Pinny Parlour on 2006-08-22
> **bhdenterprises said:**
> guys, my system is now running after downgrading the xserver-xorg-core. but now the system notification area reports that it has still 16 package updates and im afraid that if i do that something will go wrong again. im using kde desktop now...

Don't install anything for a few days was one of the forum mods recommendation.

---

### Post by tehnad on 2006-08-22
No it is still broke

---

### Post by Bloch on 2006-08-22
This is not the first time an update in Dapper has broken people's systems. An earlier kernel upgrade caused the graphics card drivers to fail to load and they had to be reinstalled.

No smallish company could afford to take the risk. As for myself, I have to get a taxi across the city this evening to fix the ubuntu system I installed for a friend a couple of months ago. I can't realistically tell him the commans over the phone.

---

### Post by Gudanov on 2006-08-22
> guys, my system is now running after downgrading the xserver-xorg-core. but now the system notification area reports that it has still 16 package updates and im afraid that if i do that something will go wrong again. im using kde desktop now...

I just did apt-get update, apt-get upgrade and that got the new X update and fixed things.

I never restarted my other computer I installed the bad update and then installed the new update. I'm guessing I'll still need to reinstall NVIDIA drivers, right?

---

### Post by Spookster on 2006-08-22
> **stig said:**
> Hello tseliot,
I asked earlier how we would know when it was safe to use the update and someone replied saying "When version 10.4 appears". I had downloaded 10.3 earlier today, suffered the crash, then followed the "downgrade" instructions on this thread and quickly recovered.

Now my updater has lit up again, so I thought great, here is 10.4 - but when I looked it was offering me 10.3 again!

Is this the "bad" update or have the developers given the repaired file the 10.3 number?

Thanks for the all the info!

10.4 is definitely the 'good' version - keep waiting until that one appears. (Shouldn't be long).

---

### Post by matthew on 2006-08-22
> **stig said:**
> Hello tseliot,
I asked earlier how we would know when it was safe to use the update and someone replied saying "When version 10.4 appears". I had downloaded 10.3 earlier today, suffered the crash, then followed the "downgrade" instructions on this thread and quickly recovered.

Now my updater has lit up again, so I thought great, here is 10.4 - but when I looked it was offering me 10.3 again!

Is this the "bad" update or have the developers given the repaired file the 10.3 number?

Thanks for the all the info!Do not install the 10.3 version! It is showing as an update because it is newer than the one you downgraded to. Wait for the 10.4 version to show up for you and you will be fine.

---

### Post by givré on 2006-08-22
The fixed version is the 10.4, it need some time to hit all the mirror.
So just wait a bit, and when you'll see the 10.4, it should be ok.

---

### Post by kakashi on 2006-08-22
> **wagerrard said:**
> For the sake of clarity, it's worth remembering that people whose Ubuntu machine is their only machine have no way to access this forum. Even if their net connection is up, odds are they've never heard of Lynx.  For those, like me, who run wireless and depend on nm-applet to set it up, an X crash keeps us off the network.

Not a good show for a distribution that makes such a point about getting non-geeks on board.

very true. 
perhaps in the next update the dapper-update could be removed from the repos so that ppl don't encounter the problem unless they choose to update to buggy  code.

---

### Post by viper on 2006-08-22
beleive its already out as i have now

---

### Post by whatrucrazy on 2006-08-22
any news on what happened? was it a bug in the 10.3 release, or was the file in the repos corrupt?
just curious, cause the more i consider it the more it seems unlikely that a 'bug' this big would just slip through.

---

### Post by richardward101 on 2006-08-22
[SIZE="5"]INSTALL ELINKS[/SIZE]
It will be a light for you when all other lights grow dim.
Seriously tho it's great for when a cock-up happens (be it your fault or a silly slip on the part of the otherwise excellent repo managers). Only problem is there seems to be no way to log in to the forums so you can't post, only search.

I think a nice feature of apt would be to keep a history of install/uninstall commands so you can rool back, but when th bug has such an easy fix, it doesn't seem like a high priority.

---

### Post by mattmole on 2006-08-22
Slightly funny story from me.

Booted up my machine this morning, installed the update and everything was hunkydory.

I then changed my xorg conf file to change the screen res (I really should find an easier way to do it, is there one?). I then killed and reloaded X and surprise surprise it was broken.

I then huffed and puffed and realised I would have to go to work instead of working from home ;) 

I tried dpkg-reconfigure... I copied conf files from my other machine etc all to no avail.

Then about 20mins ago I SSH'd from work, ran apt-get update apt-get upgrade and all was well!

Just the laptop to fix when I get back now :D

Matt

---

### Post by -Phi- on 2006-08-22
The first post should be updated with the information about 10.4. I just did the "fix" and then realized it was never broken in the first place by the time I read to the end.

- Phi

---

### Post by stig on 2006-08-22
Thanks for the suggestions to wait for 10.4!

Well, I guess there was one big mistake at the beginning in letting this buggy update out of its cage. But let's look on the bright side. There has been an enormous amount of help from the people in this forum. Also it has generated loads of useful suggestions for improvement - so it won't happen again, will it?  ;)

---

### Post by hippy4life on 2006-08-22
ta for that!

saved my bacon there :D

things dont always work but its good to know that the linux/ubuntu community is always there to help out!

Nice one!

---

### Post by deepspring on 2006-08-22
I just got caught out big time. I accidently installed the buggered update while installing a stack of other updates and programs on a fresh Ubuntu install.

I tried the fix on the main page of this thread and everything is still broken. Here is what I've tried thus far:
[list]
[*]Downloaded and installed the package from the main page of the thread
[*]Re-installed the nvidia-glx driver
[*]Rebooted
[/list]
So now I'm using Lynx to post this and wondering what to do next.

---

### Post by Dinerty on 2006-08-22
> **tseliot said:**
> [SIZE="4"]HOWTO solve the problem[/SIZE]

[COLOR="Red"]UPDATE:[/COLOR]
The recent updates break the Xserver. If you have already updated Ubuntu please type the following command:
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
```
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
```

```
sudo dpkg -i xserver-xorg-core*.deb
```

If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work


**[COLOR="Red"]NOTE: 64bit users should do this:[/COLOR]**
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```
Then restart your computer
```

sudo reboot
```


You sir are a legend; installed the update prior to visitng forums, but now all is fine and dandy, however my graphics driver seems to still be installed, do I need to reinstall it?

(nvidia driver from your guide)

---

### Post by whatrucrazy on 2006-08-22
> **deepspring said:**
> I just got caught out big time. I accidently installed the buggered update while installing a stack of other updates and programs on a fresh Ubuntu install.

I tried the fix on the main page of this thread and everything is still broken. Here is what I've tried thus far:
[list]
[*]Downloaded and installed the package from the main page of the thread
[*]Re-installed the nvidia-glx driver
[*]Rebooted
[/list]
So now I'm using Lynx to post this and wondering what to do next.

yeah me too a few hours ago.
what worked for me was upgrading to xserver 10.4, the re installing the nvidia driver (i used the envy script). i used the proceedure at the start of this thread and it all worked.
the important thing is that once the xserver install is done you *must* update the nvidia gear.
so 1: the proceedure in the first post here [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

*then*
type:
wget -c [http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb](http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb)

then:
sudo dpkg -i envy_0.4.2-1ubuntu3_all.deb

then:
envy

and run the script till all is updated.
then you should be ok, hopefully.

good luck

---

### Post by panrubius on 2006-08-22
Hi, tseliot. I tried everything in your first post and its still not working.

I have a MGA graphics card, please help me!

---

### Post by mostwanted on 2006-08-22
> **Dinerty said:**
> You sir are a legend; installed the update prior to visitng forums, but now all is fine and dandy, however my graphics driver seems to still be installed, do I need to reinstall it?

(nvidia driver from your guide)

I didn't have to. Think this is only an ATI issue.

---

### Post by Donnut on 2006-08-22
Thanks.  I was installing ATI drivers, and thought for sure it was something I did.

---

### Post by hexion on 2006-08-22
> **JeremyWorst said:**
> Thanks!  That works, so now I can see the pendrive and the files.  Now what do I do with the files:
xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb

Just do this:

> sudo dpkg -i xserver-xorg*

---

### Post by Dinerty on 2006-08-22
> **mostwanted said:**
> I didn't have to. Think this is only an ATI issue.


Thanks mate, going to sort out my other box now which uses ATI drivers :(

---

### Post by Nannygoat on 2006-08-22
Guys, I've read a huge amount of the thread and still don't get it - are the packages in the first post official? I mean are the fixed packages in the repos and the tseliot's ones all the same? Anyway, just wanted to say thanks to tseliot - this thread saved my life. This morning I updated but didn't rebooted and than excidently saw the thread. Thank you!

edit: fglrx still working with latest ati drivers.

---

### Post by bhdenterprises on 2006-08-22
do other linux distro which use xorg as xserver suffer from the same bug we suffered/currently suffering today? just a question...

---

### Post by anindya_m on 2006-08-22
Just to confirm: **The latest 10.4 release of xorg is working with nvidia on AMD64**. If anyone is still stuck with the command line run the following commands:```
apt-get update
apt-get upgrade
```and then reboot. Everything should work fine.

---

### Post by arijarot on 2006-08-22
Thank you very much for the fix, tseliot. this error was a real scare since i just switched from M$ and had no clue what to do after it failed to boot. is there any other way, aside from checking the forums, to get informed of these things--fixes? luckily had a access to another computer to search the forums for a solution!

---

### Post by rapha on 2006-08-22
Since that's the info I was looking for, and the big red messages seem to work so well:

[COLOR="Red"][SIZE="7"]It's not yet in the repos.[/SIZE][/COLOR]

Next question would be "why". It's kinda sad this is taking so long. tseliot, you might not have Marks phone number to get things rolling, do you?

---

### Post by bonefry on 2006-08-22
Thanks @tseliot for the fix.

I got a bit scared here, luckly I'm not afraid of lynx.

I am dissapointed that such a patch got through, but then again, the fix came quickly, so no real harm was done to me.

Now hury those devs to put the new patch in the repos.

(and to think that I was kind of afraid to press the update button before I pressed it, seeing that's xserver being upgraded, next time I will trust my instinct more)

---

### Post by mrojas73 on 2006-08-22
> **bonefry said:**
> Thanks @tseliot for the fix.

I got a bit scared here, luckly I'm not afraid of lynx.

I am dissapointed that such a patch got through, but then again, the fix came quickly, so no real harm was done to me.

Now hury those devs to put the new patch in the repos.

(and to think that I was kind of afraid to press the update button before I pressed it, seeing that's xserver being upgraded, next time I will trust my instinct more)

I am there with you!

---

### Post by anindya_m on 2006-08-22
Hey the update is already in the repos (I installed it from there). Did you run apt-get update ?

---

### Post by zaziork on 2006-08-22
I simply did an apt-get update, apt-get dist-upgrade from the command line, and rebooted. Now it's working fine. I'm also using Nvidia drivers.

---

### Post by kombat on 2006-08-22
Why has nobody removed the bad package from apt since 9 hours?!

---

### Post by mattlach on 2006-08-22
> **Owdy said:**
> That is so true. 
Unbelievable hassle from Ubuntu. This should be stable release. What are normal user do now. They dont have no idea what to do with blue screen of death from X. __

If you don't know your way around the console (or are willing to learn) you shouldn't be using Linux.  Plain and simple. :p

---

### Post by rapha on 2006-08-22
@mattlach: that is plain and utter bullshit (@tseliot, sry for the lang)

@anindya_m: not in the repos here, but I'm using the German mirrors.

---

### Post by neymac on 2006-08-22
> **Dale61 said:**
> tseliot, I never intended to upset anyone, if I have, but just felt that I had to post what happened to someone who is trying to convince others to make the change.  If I was giving my demo yesterday, all would have been sweet, but today of all days!?

Yes indeed Kabal, the fix is quick and painless, but only if you know what the problem is in the first place, and have the facilities to find the fix.

For this reason I keep 3 OS installed in my home computer:
Ubuntu 6.06
Suse 10.1
and if the two above fail, Windows XP.

Yesterday when my X windows broked in Ubuntu due the wrong update, I used OpenSuse to read this forum and search the fix.
Thanks for the quick fix.

---

### Post by Klaidas on 2006-08-22
> you don't know your way around the console (or are willing to learn) you shouldn't be using Linux. Plain and simple
What if you started using linux a day/two before? :)

---

### Post by neymac on 2006-08-22
> **Dale61 said:**
> tseliot, I never intended to upset anyone, if I have, but just felt that I had to post what happened to someone who is trying to convince others to make the change.  If I was giving my demo yesterday, all would have been sweet, but today of all days!?

Yes indeed Kabal, the fix is quick and painless, but only if you know what the problem is in the first place, and have the facilities to find the fix.

For this reason I keep 3 OS installed in my home computer:
Ubuntu 6.06
Suse 10.1
and if the two above fail, Windows XP.

Yesterday when my X windows broked in Ubuntu due the wrong update, I used OpenSuse to read this forum and search the fix.
Thanks for the quick fix.

---

### Post by mattlach on 2006-08-22
> **pepolez said:**
> my first thought when X went down and i couldn't fix it was these forums. but of course, i can't view them in lynx (something to do with js and redirects i suspect)

Try links2 instead.  I can view them fine from links2.

---

### Post by deepspring on 2006-08-22
> **whatrucrazy said:**
> yeah me too a few hours ago.
what worked for me was upgrading to xserver 10.4, the re installing the nvidia driver (i used the envy script). i used the proceedure at the start of this thread and it all worked.
the important thing is that once the xserver install is done you *must* update the nvidia gear.
so 1: the proceedure in the first post here [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

*then*
type:
wget -c [http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb](http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb)

then:
sudo dpkg -i envy_0.4.2-1ubuntu3_all.deb

then:
envy

and run the script till all is updated.
then you should be ok, hopefully.

good luck

Thanks mate!

It turned out to be an issue with some illegal characters in my xorg.conf file from when I was setting up compiz.

---

### Post by loserboy on 2006-08-22
thanks anindya_m, for putting it plainly.

---

### Post by Klaidas on 2006-08-22
neymac, you should also have a livecd lying around - you never know what might happen ;)

---

### Post by rapha on 2006-08-22
> **Klaidas said:**
> What if you started using linux a day/two before? :)
You got a prob then. If I was in the situation, I'd prolly call up the guy who recommended this Linux thing to me and tell him to give me WinXP back. This definitely needs to be addressed by Mark so that something like this happens never again.

---

### Post by karas on 2006-08-22
thanks soo much for the quick fix tseliot. You saved me from an unscheduled reformat/reinstall. It's time like these that I'm glad that Ubuntu has a live cd that can be booted from if my system messes up. (Glad I'm on this forum too :D )

---

### Post by mduduzi on 2006-08-22
AMD64 Help!!!

My K7 was fixed easily... So was one AMD64. But the last AMD64's still says no screen found...

 /etc/init.d/gdm start

fails to start GDM.

I have run updates and build-deps on just about every package.
I've noted that dpkg-reconfigure xserver-xorg runs but only a few graphoc cards are show. I installed nvidia and now at least it appears, but not nv...

What can I do?](*,)

---

### Post by mattlach on 2006-08-22
> **Bloch said:**
> This is not the first time an update in Dapper has broken people's systems. An earlier kernel upgrade caused the graphics card drivers to fail to load and they had to be reinstalled.

No smallish company could afford to take the risk. As for myself, I have to get a taxi across the city this evening to fix the ubuntu system I installed for a friend a couple of months ago. I can't realistically tell him the commans over the phone.

No linux distribution, no matter how user friendly it claims to be is fire and forget like Windows is.  If you can't do some elementary fixes (like recompile kernels, install modules, know how to edit xorg.conf, etc. etc.) using linux as a primary operating system is not for you.  Sorry.  If you want sometyhing dumbed down that you'll never have to troubleshoot go back to windows or macos.  If you want a powerful, flexible operating system that takes some smarts and computer knowledge to use, stay here and quit complaining!

---

### Post by b_martinez on 2006-08-22
Thank You very much for posting this. 
Bill

---

### Post by sefs on 2006-08-22
Ok.

I have an update to be downloaded

Xserver-Xorg-Core

Version 1:1.0.2-0ubuntu10.4: 

From reading this thread I cannot tell clearly if i should apply this or not.

What should I do.  Ignore or apply.

Thanks. (Thanks CStudent!)

---

### Post by mduduzi on 2006-08-22
AMD64 with nVidia

it says it cannot find the 'wacom' module...
How do I install this?

---

### Post by cstudent on 2006-08-22
> **sefs said:**
> Ok.

I have an update to be downloaded

Xserver-Xorg-Core

Version 1:1.0.2-0ubuntu10.4: 

From reading this thread I cannot tell clearly if i should apply this or not.

What should I do.  Ignore or apply.

Thanks.


ubuntu10.4 is the fixed version. You want to avoid ubuntu10.3, it's the borked packaged.

---

### Post by karas on 2006-08-22
sry-bad post

---

### Post by marianoi on 2006-08-22
> No linux distribution, no matter how user friendly it claims to be is fire and forget like Windows is. If you can't do some elementary fixes (like recompile kernels, install modules, know how to edit xorg.conf, etc. etc.) using linux as a primary operating system is not for you. Sorry. If you want sometyhing dumbed down that you'll never have to troubleshoot go back to windows or macos. If you want a powerful, flexible operating system that takes some smarts and computer knowledge to use, stay here and quit complaining!
__________________

That is non sense. That mentality will keep Linux far from prime time forever.

Ubuntu linux is aim to BOTH power and NEW users. In an stable version this type of mistakes should not happen.

---

### Post by MikeMLP on 2006-08-22
edit: pointless post

---

### Post by missmoondog on 2006-08-22
ok. i think the settings for refresh rates are sticking now. only had time to check it once before i had to leave. can't get on that computer again until tomorrow morning.

i did notice in settings that it has 2 monitors listed now. where'd that second one come from and how do i remove it?

thanks

although very frustrated from this happening, i surely do appreciate the help/work from here. keep it up!!

---

### Post by tseliot on 2006-08-22
> **missmoondog said:**
> ok. i think the settings for refresh rates are sticking now. only had time to check it once before i had to leave. can't get on that computer again until tomorrow morning.

i did notice in settings that it has 2 monitors listed now. where'd that second one come from and how do i remove it?

thanks

although very frustrated from this happening, i surely do appreciate the help/work from here. keep it up!!

Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by shanepardue on 2006-08-22
if i haven't restarted the xserver to break it, could i perhaps just wait until an update to fix it becomes available or should i go through this procedure to fix it?

---

### Post by spockrock on 2006-08-22
10.4 works on both of my machines.


I can see why people are getting upset but at the same time I have used ubuntu since hoary and this is the first update that broke anything and it took less then 5mins to fix.  The fix was there the next morning.  I cant say wiblowz expee has been that nice to me.  Yeah if you started using dapper in the last two days you would get upset, but when I started using ubuntu I still visited this forum.  Any one using the search function, or seeing the multiple threads on it could of fixed it.

---

### Post by mattlach on 2006-08-22
> **marianoi said:**
> That is non sense. That mentality will keep Linux far from prime time forever.

Ubuntu linux is aim to BOTH power and NEW users. In an stable version this type of mistakes should not happen.

Don't get me wrong.   I have no problem with people asking questions and being willing to learn.  It's all the complaining for such a simple fault like this that bothers me.   If you cant take a little X-crash every now and then and are willing to learn from the experience, then linux may not be for you.

Sure, linux now is more user friendly then it has ever been, but it is still an enthusiasts operating system.  It's an operating system for people who LIKE computers, not for people who just like what computers can do for them.

If you arent willing to learn the console, and fundamental usage of non-gui linux, I think you have no place using it.  If people are willing to learn, I am more than willing to help.

For instance, this silly litte problem that lasted only a few hours tought a whole lot of you how to downgrade unwanted packages.   Was that an entirely bad thing?   Linux SHOULD be a challenge, cause if it isn't you don't learn anything from it.

The world doesn't need another Ms Windows.

---

### Post by encompass on 2006-08-22
I agree. .. at least when you yell at ubuntu we respond rather then other companies "We will return your email wihting 24 hours. :)"
I like the service... they do a great job and if you wnat to be careful do what I do, and wait. BTW... servers running this udate stillwork.  cool huh?  I would like to see that in windows.

---

### Post by sprung on 2006-08-22
omg, a horrible day for ubuntu indeed, thank you very much for the fix, lynx and the decision to go to ubuntuforums first saved me (worked flawless, i use xgl, nvidia-glx), but many others will not be so lucky..

what p*s me off most is not that this was released unchecked and stayed online for like 10 hours or more (?), which really must not happen in a stable, "LTS" version, but that there is still nothing about it on the official ubuntu website! most people will go there first, and not to ubuntuforums! insanely bad errors happen, but you have to at least stand straight for them..

i still love ubuntu and am very thankful to everybody involved, but i'm less sure about recommending it now :(

---

### Post by Brownedwg89 on 2006-08-22
hehe... good thing i decided to leave my computer on last night

---

### Post by encompass on 2006-08-22
> **shanepardue said:**
> if i haven't restarted the xserver to break it, could i perhaps just wait until an update to fix it becomes available or should i go through this procedure to fix it?

Yeah.. I think it would work.  worth a try right?

---

### Post by Cope57 on 2006-08-22
Ubuntu has 1 buggy update... now how many has M$ had? :lol: 

Ubuntu is doing a great job. =D>  Heep up the great work!!! :biggrin:

---

### Post by MKR. on 2006-08-22
> **sprung said:**
> omg, a horrible day for ubuntu indeed, thank you very much for the fix, lynx and the decision to go to ubuntuforums first saved me (worked flawless, i use xgl, nvidia-glx), but many others will not be so lucky..

what p*s me off most is not that this was released unchecked and stayed online for like 10 hours or more (?), which really must not happen in a stable, "LTS" version, but that there is still nothing about it on the official ubuntu website! most people will go there first, and not to ubuntuforums! insanely bad errors happen, but you have to at least stand straight for them..

i still love ubuntu and am very thankful to everybody involved, but i'm less sure about recommending it now :(

Remember that Ubuntu is backed by a company, and companies have to be careful about what they say.

I expect an official announcement to be out, for it to be quicker than most corporate press releases, and for it to be better written than most press releases, but it's still safe to expect it to take time.

---

### Post by spockrock on 2006-08-22
> **shanepardue said:**
> if i haven't restarted the xserver to break it, could i perhaps just wait until an update to fix it becomes available or should i go through this procedure to fix it?

the update and fix is already on the repos for me.  10.4 fixed my woes.

---

### Post by Porta on 2006-08-22
I've tried to use the fix for this but no luck, i can't connect to the server (404 not found)
I've also tried the archives but no luck with that either.
So i am stuck and without my ubuntu.

regards
Porta

---

### Post by spockrock on 2006-08-22
try

```
sudo apt-get update

sudo apt-get upgrade
```

I just pulled 10.4 off the repos, granted I am using the canadian repos.

---

### Post by MKR. on 2006-08-22
> **Porta said:**
> I've tried to use the fix for this but no luck, i can't connect to the server (404 not found)
I've also tried the archives but no luck with that either.
So i am stuck and without my ubuntu.

regards
Porta

That's because your update list is out of date and still shows 10.3, which was removed.

Following spockrock's suggestion should fix it.

---

### Post by Porta on 2006-08-22
Ok, thanks i will try this.

Porta

---

### Post by Cope57 on 2006-08-22
deleted

---

### Post by EduardoFonseca on 2006-08-22
Well. After all this, Debian is not so wrong about being cautious... 

I have 30+ customers using Dapper Drake (desktop) to run my software. After today, I think I will change the repos to Debian, for safety...

E.

---

### Post by Minigun_Fiend on 2006-08-22
Well its all done and dusted for me.
Just followed the instructions, changed "nvidia" in xorg.conf to "nv" and rebooted, and X was back up.
Went into Synaptic, found nvidia-glx and selected it for reinstall, then put "nv" back to "nvidia" and rebooted again, and its all great and working with 3D again.

Still, I'll have to remember not to update tomorrow:roll:

---

### Post by ischg on 2006-08-22
Ubuntu rocks. and so does the ubuntuforum. I got hit yesterday and was able to resolve the xserver issue even before this thread was open - I posted my cry for help and got the solution posted within minutes (!). That's what's really great about using this distro.
Still, it's a sad day for ubuntu, since I'm sure it lost lots of users over this fatal bug. It's really sad to see that one little error like that pisses of so many people, who don't care how much excellent work had been done before. If any of the big guys should ever read this, please make sure that new packages are tested before they end up in the repository. Thanks, and keep up the good work!

---

### Post by spockrock on 2006-08-22
I updated to 10.3 didnt work downgraded, then updated to 10.4 this morning and x worked without having to reinstall the nvidia drivers.  lucky me.

---

### Post by OneSeventeen on 2006-08-22
I for one can't believe this happened!!!

Ubuntu sent out a system debilitating update and before it is a few hours old a solution is posted in the forums, and a few hours later a fix is pushed out!

Thanks Ubuntu Team, and tseliot, for keeping our systems up and running.  Accidents happen, and I hope they are less frequent in the future, but considering the number of systems-critical applications I have seen demolished by Windows Updates, I'm not too worried.

Thanks again for the updates, and the fixes.  But bear in mind, as soon as you start charging hundreds of dollars for each version of Ubuntu, I might not be as forgiving. :p

---

### Post by slight on 2006-08-22
To those saying that there are lots of bad updates to Windows I would have to  ask if you can point me to a Windows update that hoses the main user interface? To expect the average user to a) know this forum exists and b) to have to use the command line to fix an official update is not reasonable.

Overall I think Ubuntu is excellent, but slip-ups of this magnitude are not acceptable if Ubuntu wants to fix bug #1. I also have issues with the general quality of the Dapper release and Canonical's refusal to accept that it may have been below par, but that's a whole other conversation :)

---

### Post by Sandsound on 2006-08-22
A huge thanks to tseliot for the fix... you have saved my day.

---

### Post by angkor on 2006-08-22
I'm lazy tonight and didn't feel like reading all the 32 pages of this thread so maybe this has been covered. I apologize if it has.

Does anyone know why ubuntu decided to bring out bug fix updates during the stable release cycle? We're supposed to get only security fix. aren't we, or was this also a security related update?

---

### Post by Big_J on 2006-08-22
I just turned my computer on and I couldn't start x (I used the update), all I did was:
sudo apt-get update
sudo apt-get upgrade
And x started without a problem, nvidia drivers are still installed, and the only problem is that compiz and xgl no longer work.

---

### Post by far2bored on 2006-08-22
I ran the update this morning and have not rebooted yet. I actually dropped by the forums to figure out why my synaptic isn't working and happened to spot this thread on chance. 

Is there a quick way to check what version of Xserver I installed? I'm not getting anything with apt-get upgrade or apt-get dist-upgrade, but I'd like to check that 10.4 is installed just to be sure.

Thanks!

---

### Post by Azriphale on 2006-08-22
I just attempted the update on 2 machines. And *bang*, they're useless!
Until I found this thread

Thanks for the fixed packages.

---

### Post by spockrock on 2006-08-22
@big J
did you update using quinns repos? try this first

```
sudo apt-get install -f 
```

and then give compiz a restart that might fix it.

---

### Post by rexey on 2006-08-22
This worked like a charm.
Thanks!

---

### Post by RESmonkey on 2006-08-22
Wow...thankfully I had a dualboot going on with Windows...

What was the point of the update?  People could have been doing college papers and business stuff and BOOM!

---

### Post by spockrock on 2006-08-22
> **far2bored said:**
> I ran the update this morning and have not rebooted yet. I actually dropped by the forums to figure out why my synaptic isn't working and happened to spot this thread on chance. 

Is there a quick way to check what version of Xserver I installed? I'm not getting anything with apt-get upgrade or apt-get dist-upgrade, but I'd like to check that 10.4 is installed just to be sure.

Thanks!

if you are using xgl and compiz, an update in quinns repos borked synaptic

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

will fix it

---

### Post by peteruta on 2006-08-22
Thanks for the fix....

I did the update to the update and had to run the reconfigure command and finally came back after waisting more than 1/2 my day...:(....

I still have a problem though.

After I put my user/passwd in, it take about 3 min before I desktop comes up... The system load is very load... like it is waiting for a timeout...

Peter

---

### Post by far2bored on 2006-08-22
Thanks spockrock! Two birds with one stone.

---

### Post by Big_J on 2006-08-22
> **spockrock said:**
> @big J
did you update using quinns repos? try this first

```
sudo apt-get install -f 
```

and then give compiz a restart that might fix it.
Oh no, I don't have a problem with compiz, I can fix it, I was just pointing out that all you have to do is this:
sudo apt-get update
sudo apt-get upgrade

and you'll get x back without loosing the graphic drivers. So I don't see a need for the fix in this thread. I mean my problem is fixed, I only came here to report a possible bug. I mean you might as well give this a try before doing that fix which will risk loosing your drivers!

---

### Post by phansiizwe on 2006-08-22
Thanks tseliot!

The fix worked for me as well (running 2.6.15-26-686 + nvidia)

---

### Post by Metacarpal on 2006-08-22
There's an idea been put forward on how [this might be prevented in the future.]("http://www.ubuntuforums.org/showthread.php?t=241473")  Thoughts?

---

### Post by feest on 2006-08-22
first of all:

[SIZE="7"]***_THANK YOU!!!:D :D :D _***[/SIZE] 

second:

i was just about to post a message about a failing x server and i spent the whole evening trying to fix it, really thx...

---

### Post by Erik Trybom on 2006-08-22
I'm sorry if this has been asked before but the thread is huge by now:

What if I haven't installed the update yet? Is it now or will it soon be safe to update the system without X breaking?

---

### Post by Raavea on 2006-08-22
> **stig said:**
> Hello tseliot,
I asked earlier how we would know when it was safe to use the update and someone replied saying "When version 10.4 appears". I had downloaded 10.3 earlier today, suffered the crash, then followed the "downgrade" instructions on this thread and quickly recovered.

Now my updater has lit up again, so I thought great, here is 10.4 - but when I looked it was offering me 10.3 again!

Is this the "bad" update or have the developers given the repaired file the 10.3 number?

Thanks for the all the info!
> **rapha said:**
> Since that's the info I was looking for, and the big red messages seem to work so well:

[COLOR="Red"][SIZE="7"]It's not yet in the repos.[/SIZE][/COLOR]

Next question would be "why". It's kinda sad this is taking so long. tseliot, you might not have Marks phone number to get things rolling, do you?
 For these two, I should say I had the same thing! But I clicked 'check' and it now says 10.4 though I'm wary of installing it.

 I'll wait a few days. Sorry if those two were answered, this thread is growing faster than I am reading and I'm off to bed!

---

### Post by mduduzi on 2006-08-22
My machine still cannot find version 4 for AMD64, even though the computer next to it (already fixed as described in this thread can find it using synaptic).

Can anybody please give me the URL of

xserver-xorg-core_1.0.2-0ubuntu10.4amd64.deb

then I can install it locally.

Thanks,

---

### Post by interse on 2006-08-22
Thanks to tselliot

To err is human, to fix it is divine!

Enough said.  Errors happen.   Thanks to a vibrant community, we are back on track.

---

### Post by tseliot on 2006-08-22
> **Raavea said:**
> For these two, I should say I had the same thing! But I clicked 'check' and it now says 10.4 though I'm wary of installing it.

 I'll wait a few days. Sorry if those two were answered, this thread is growing faster than I am reading and I'm off to bed!

10.4 works just fine here.

---

### Post by Noxide on 2006-08-22
Is it just me?
I installed the 10.3 update on 2 machines today (one is VMWare) and X worked like a charm. :-s 
Maybe becuase I don't have 3d acceleration on either of them...

---

### Post by RESmonkey on 2006-08-22
Fix won't work.

"Temporary Failure in Name Resolution" for the .deb file

---

### Post by MoebusNet on 2006-08-22
Thank you spockrock!

tselliot's fix resulted in an Error:404 server not found, so I used your recommendation of:

sudo apt-get update

sudo apt-get upgrade

sudo reboot

and all is well again!

Thank you tselliot and everyone who has worked so hard to fix this!!

---

### Post by RESmonkey on 2006-08-22
I searched around, I'm the only one with that problem or what?  What is temporary failure in name resolution anyway?

---

### Post by MarvinZurcher on 2006-08-22
Where do enter the code to fix x-server when my machine crashes? I can't get to the terminal.

---

### Post by gannic on 2006-08-22
help...none of this works. I have no network connection via the affected computer and the CD doesnt even contain an /x/ directory. The archive solutions all fail with 'missing files'

What can I do?

---

### Post by xtknight on 2006-08-22
> **MarvinZurcher said:**
> Where do enter the code to fix x-server when my machine crashes? I can't get to the terminal.

Press Ctrl+Alt+F2 to get to a virtual terminal.  Then login with your regular username/password.  Type:

sudo killall gdm
sudo apt-get update
sudo apt-get -s upgrade
(This is a simulation of apt-get to verify that it is indeed 10.4.  If it looks like the new one is, then)
sudo apt-get upgrade
sudo gdm

Then you should be good.

---

### Post by mduduzi on 2006-08-22
temporary name resolution failure indicates that your DNS server is either not working or you cannot use it.

---

### Post by Porta on 2006-08-22
The fix worked like charm, all problems solved.
Thanks tselliot and spockrock for your effort in this.


regards
Porta

---

### Post by gannic on 2006-08-22
> **MarvinZurcher said:**
> Where do enter the code to fix x-server when my machine crashes? I can't get to the terminal.

Press escape in GRUB (appears on boot) and choose recovery mode for the most recent kernel option.

---

### Post by RESmonkey on 2006-08-22
Marvin, just reboot and start ubuntu, say no no to the error and you will be in a fullscreen terminal...

tseliot, any help?  (sorry, I'm impatient-yes, I like, like everyone else, am a busy hu-man.

---

### Post by texxan on 2006-08-22
:confused: I have been using four flavors of the Ubuntu distribution on the same computer, all four installad on the partitioned hard drives (2 drives). Last night I updated Ubuntu and Kubuntu, and while I had the distribution up, I added my wife to the user list so she would have her own files. I then decided to reboot to make sure I had her login information correct when, wham-o, the X thing didn't work. Being the novice that I am I decided to reinstall Ubuntu first then the others to follow. Well to make a longer story a little shorter, eventually I had repartitioned a couple of times and ended up loosing 3 Gb of one of the drives. I don't know if it is just inaccessible now or if I could clean the drives to restore them to their previous state. I don't mind reinstalling the software as I've been experimenting with these flavors to decide which i like the best. Can anyone tell me if it is a possibility to clean the drives prior to the reinstallation of these excellant distributions? Thankyou ever so much.

---

### Post by tseliot on 2006-08-22
> **mduduzi said:**
> My machine still cannot find version 4 for AMD64, even though the computer next to it (already fixed as described in this thread can find it using synaptic).

Can anybody please give me the URL of

xserver-xorg-core_1.0.2-0ubuntu10.4amd64.deb

then I can install it locally.

Thanks,

[http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb](http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb)

---

### Post by gannic on 2006-08-22
> **tseliot said:**
> [http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb](http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb)

what about the 32 bit version please?

---

### Post by RESmonkey on 2006-08-22
DNS?  But the thing does have internet running...because when it didn't the termnal spat out an Error 404.  With internet it's spitting out 'temporary failure in name resolution'...

---

### Post by sefs on 2006-08-22
> **RESmonkey said:**
> I searched around, I'm the only one with that problem or what?  What is temporary failure in name resolution anyway?

Could that be a problem with your /etc/hosts file? check it to see if it has been mangaled

---

### Post by tseliot on 2006-08-22
> **gannic said:**
> what about the 32 bit version please?

have a look at my 1st post

---

### Post by RESmonkey on 2006-08-22
YES! Worked, I went and did it in Recovery mode instead of default ubuntu  (or was I supposed to do that, all along?  hahaha....*ilookstupiddon't-I?*)

Well, one question.  How come when I do fglrxinfo it's still ATi Radeon, didn't you say proprietary drivers won't work?

---

### Post by carontis on 2006-08-22
Hi Tseliot. If you or others need I can post the last update for xserver-xorg in .deb format. It works fine and without problems, also if I think at present time there shouldn't be anymore problem in updating. Let know.

---

### Post by akak8ty on 2006-08-22
> **The Pinny Parlour said:**
> argh.. To late.  I saw this updated and absolutely dreaded and hesitated installing it.  Xserver-xorg failed on reboot,  suprise suprise.  Stuff like this makes the ubuntu experience a painful one.   

Yes, I am pissed off.

Understandably. Sorry that happened to you.
I fixed it with the help of a game comrade online, then found this. 
I think Ubuntu is way slower than windows. Good thing I can switch back and forth, but my 4 year old likes the games here. She's quite the computer maven ;) 
I start them with old  mouse about 2 1/2 so they get the feel of maneuvering- and not clicking too much.

---

### Post by Big Fish on 2006-08-22
I just installed 10.4, but I haven't rebooted yet. I'm glad that I was at work today and didn't install the bad one.

---

### Post by robw003 on 2006-08-22
**OH MY GOD!!! Thank you for the fix. =D>  =D>** 

I knew it was the update that broke it, but did not have a good way back.

Your fix worked great. Thanks for the concise and clear instructions.

It would be REALLY cool if an update causes a FAILURE of a critical system, there would be an ability to revert out the update!!!!

Has someone requested that this package/update get pulled???

Regards,
Rob

---

### Post by straypackets on 2006-08-22
If you run wireless, reinstalled the old deb from cache, only to find that you still don't have a network connection, it's probably because Network Manager didn't launch.

At the command line, do "sudo nm-applet".

You should see the Network Manager spinning away in a panel, trying to connect to something. Look in the bottom panel for an alert about NM needing a password. Click on the NM icon and you'll see a dropdown listing the network it sees. Click on your's and you should be good to go.

Install the update xserver-xorg.  If you'd been running with NM up in the panel, it should be back.

Also, if you're doing the dpkg-reconfigure xserver-xorg thing, let it answer it's own questions, and otherwise opt for very generic responses.  Select "16" as the display depth.  Select 1024 or 800 as the resolution.  And, if you've got an Nvidia card, be sure to check the resulting xorg.cong file to make sure it really says "nv", not "nvidia" on the Device line.  Change it back after you've grabbed the update, reboot, and you should be happy.

---

### Post by petri on 2006-08-22
The new update 10.4 works after rebooting with ATI 8500 and with drivers from
 
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (Method 2)

---

### Post by akak8ty on 2006-08-22
yep. like I said...fortunately I posted somewhere else (not here)
and was given the instructions. It took a couple tries, but all is well...I lost some of my programs though- I am not real happy about that- but its fixable.

I had a cat named tselliot.

---

### Post by thisguyiknow on 2006-08-22
Hey, all.  I just wanted to say to the folks who have expressed negative feelings toward ubuntu over the xserver problem (1) yes, I got caught too, and spent the whole morning poring through, and writing and re-writing xorg.conf.  And I was feeling pretty steamed (mostly at myself).  But you wouldn't believe how much worse it could have been!  Remember, the extensions to ubuntu packages are .deb -- Years ago, when I was running debian exclusively, I was continually going nuts over stuff like this, and 'though the debian community is great in so many ways, it had **nothing** that could touch what this forum thread has done for us today.  Back then, at least, debian had **one** developer to port the X system over to .deb packages: his web page, 'though funny, basically said "Don't bug me, I don't have time for it--the next release will be ready when it's ready, so just go away."  Debian is **sooo** careful to test packages to death that it's hard for me, at least, to fault ubuntu's developers for making a working assumption that the base package was likely to be sound.  (It may be a while before they do that again.)  
 
Anyway, just to celebrate how alive and responsive the ubuntu community is--those who raised complaints, and those who sought out the solutions, working together.
 
Oh, and as an antidote for thoughts of returning to windolts, just remember those "security vulnerabilities" they keep addressing: if one of those slips through, it could ruin not just a morning, it could ruin your whole month!  Or worse, if your thesis was sitting on that trashed-out drive.
 
Too long, I know, but...well, I do that.  Sorry!  tgin

---

### Post by azmrb on 2006-08-22
I just checked and synaptic is still bugging me (no pun intended) to update
to version 10.3 just like it was this morning when I went to work.  Is there no 10.4 version in the repositories yet?  I ran sudo apt-get update

amd64 Dapper.

---

### Post by TFX360 on 2006-08-22
Thanks tseliot,

Got everything up and running again in five minutes. Almost missed the notice on the frontpage. I was lucky.

How can it be that after twelve hours the repo's aren't fixed. Just updated my laptop too, same old.

Downloaded the new ati drivers and compiled them. Works like a charm again. Xgl too.


Thanks!


Kind regards,


TFX

---

### Post by StreetSmart on 2006-08-22
Out of all the updates the Ubuntu developers have sucessfully put out how many have caused problems? Be thankful that this doesnt happen more often. Be thankful that Tseliot is taking his time to answer EVERYONES questions.

---

### Post by gammagoat on 2006-08-22
This did not work.


sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

sudo reboot

says it cant find 1:1.1.0.2 xserver-xorg-core. 

what can I do now?

---

### Post by schlumbohm on 2006-08-22
Sadly one of the last things I did was check the forums.  However, I am glad I did.  Easy fix.

From the forums I performed the two lines from tseliot:
wget -c [http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)

sudo dpkg -i xserver-xorg-core*.deb

Then I had to repair all of the "fixing" that I did....and I did it from the cchtml site.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo reboot

Running a Dell Latitude D600.  Worked perfectly.

---

### Post by Pcghost on 2006-08-22
What a horrible coincidence.  I just did a dapper reinstall on my desktop system (Athlon X2 4200, 2xNvidia 6800 XT running 32-bit).  Could this bug be the reason X is locking up after about 5 minutes whenever the nvidia driver is used?  I have been working the issue all day and will cry if it was a freakin X bug. :-|

---

### Post by bubz_the_troll on 2006-08-22
I have my desktop back up and running but I still need to reinstall the nvidia drivers.  I have not run the update on my lap top yet.  What version of the xserver am I supposed to avoid and which one should I keep an eye out for when it is ready?

---

### Post by TrendyDark on 2006-08-22
tseliot, I tried your solution and it worked great for me. Once everything was installed I just did "killall gdm" and "sudo gdm" and x started perfect. THanks!

---

### Post by spockrock on 2006-08-22
@ azmrb

as tseliot pointed out the deb can be found here.
[http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb](http://archive.ubuntulinux.org/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb)

also I would like to point depending on the repository that you are using updates may take longer.  Yes its the offical server, however I believe that the a server gets the updates and the other repository servers then pull the updates and add them to thier own.  I know there was a slight delay between the Canadian repos from the archive repos.  I am not positive but I am sure thats how the repos work, but this means faster downloads by connecting to servers closer to you.  lmfao if I am wrong, hahahhaaha.  but I think thats how the repositories work.

____________

And I agree with StreetSmart its understandable that some of you are getting upset, but so the devs put one bad update on the repo.  Big deal, first bad update on two machines since I have been using hoary.  Thats give or take 1.5 years.  Thats a better track record then M$.

---

### Post by spockrock on 2006-08-22
10.3 is the bad one 10.4 is the good one.

> **gammagoat said:**
> This did not work.


sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

sudo reboot

says it cant find 1:1.1.0.2 xserver-xorg-core. 

what can I do now?


the fixed version is on the repos.

```
sudo apt-get update
sudo apt-get upgrade
```


I was able to update and run x without reconfiguring or re-installing nvidia drivers. you may.

---

### Post by Big_J on 2006-08-22
> **spockrock said:**
> 10.3 is the bad one 10.4 is the good one.




the fixed version is on the repos.

```
sudo apt-get update
sudo apt-get upgrade
```


I was able to update and run x without reconfiguring or re-installing nvidia drivers. you may.
That's what I've been saying, but no one seems to read anything except for the first page.

---

### Post by Mr. Picklesworth on 2006-08-22
Is the update still live, or has it been removed/fixed at this point?

---

### Post by jgallagher on 2006-08-22
Thank you for the quick answer. :)

---

### Post by spockrock on 2006-08-22
@ Big_J vv point prooven I guess

> **Mr. Picklesworth said:**
> Is the update still live, or has it been removed/fixed at this point?

the fix is in the repos. version 10.3 = bad, 10.4 = good.

---

### Post by anasofiapaixao on 2006-08-22
**THIS** is a decent and fair way of venting your frustrations:

> **Dale61 said:**
> G'day, another recent Ubuntu convert.

Took the plunge 3 weeks ago, and all was going swimmingly, until this morning.

I had been telling a few mates about how much better my pc was running since installing DD, and had convinced one to consider changing his small office pc's over from Windoze.

Anyway, was sitting here showing him around the desktop and what different things were when I noticed I had an update ready for downloading.  Perfect, I thought, as this will show him how easy it is to keep his systems up-to-date.

Proceeded to d/l the xserver update, rebooted, and nothing!  Xserver failed, and I couldn't explain why.  After an hour or so, he was no longer interested in upgrading, which means there will be a dozen less pc's converting to Ubuntu.  May not sound like a lot, but he will tell others, and so, it will travel down the line.

I continued to find a remedy, and fortunately, I have a laptop (XP) setup close by, so I connected to the net and searched far and wise for an answer.  I came across this forum, and following the instructions above, I was able to get my pc up and running as it was pre-update.

Overall, this was an 8 hour exercise, 8 hours that I could afford to take out of my day, but how many others have that luxury?  I'm wondering how many others, particularly those in business, who are still trying to find a solution to a problem that should NEVER have happened in the first place.  I pity those who don't have a backup system and are still trying to work out what's happened.

I would just like to thank all those who were quick to see the problem and submit a fix, but there needs to be some serious questions answered as to why this happened in the first place.  Don't the developers test these things on their own machines first, or are we the guinea pigs for their experiments.

My apologies for such a harsh first post, but as I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.


THIS is NOT.

> Why has this broken update been allowed to go live? How ridiculous.

I hate xserver xorg, it's a piece of utter crap.

It is a bucket of shit. This should NOT be happening and it IS.

Mentioning names is not what matters. Mistakes HAPPEN and we are ALL subject to them, at least while computers don't take over the world :D. 

It is important for people to realize this is NOT costumer service, ***_THIS IS A COMMUNITY_***. All one can get with this kind of behavior is a (well-deserved) answer of the kind "well go get a refund". And one should know this is NOT a common situation and is being solved quite quickly. Also, sure we all can vent but providing we do it in a decent way. No one needs people trashing down the Ubuntu's staff hard work! Sorry for the harshness, but come on...

Back on topic: Seriously, This morning when I turned on my computer I thought: let's go check the xorg file... Checked the debugging info, checked that everything was correct. What I thought? I didn't do anything... wait... I upgraded the X server. Then I thought to myself: I am feeling SO lazy today, I'll just wait until the end of the day and check what was the answer to all the people who complained about the bug (even tought a little afraid that the problem could be only mine). Luckily I haven't upgraded my mum's computer, so here I am.

P.S. - No I have nothing to do with Ubuntu's staff; just your average forum user:P.

---

### Post by Mr. Picklesworth on 2006-08-22
I wonder if it's possible for Ubuntu to have an automated emergency fallback in the case of the X server not loading?
Perhaps it could automatically attempt to launch a pre-installed text-based web browser displaying the Support section at Ubuntu.com, or offer to file a bug report... or both.
Then those people without alternative computers could still hopefully find what went wrong without too much terminal use.

Some fancy offline trouble-shooting docs would be cool as well, but that would undoubtedly be very difficult and would take a long time to perfect considering how open-ended this is.

---

### Post by jaywatkins on 2006-08-22
Okay, here is my problem.

Aside of being dumb enough to update w/o realizing the potential for breaking Ubuntu, I have the firewalker firewall running, and it is set to start at boot.  All I have been able to do so far is get it to block all connections, which it is currently doing.

How does one turn off Firewalker from the terminal?  

The ps -ax command sends all data rushing past w/o a way to scroll and find the process.  Plus, the data moves off of the screen and each line cannot be completely read in it's entirety.  

What directory and what command shuts off Firewalker?

I love Ubuntu, and I cannot complain because all of this is free, but this is the type of thing that would send some folks rushing back to Windows.  I had to type this on a Windows machine because Ubuntu had an update for XServer.

Lesson learned, DO NOT update Ubuntu...

Thanks

/J

---

### Post by joeinazyes on 2006-08-22
Rather than complaint about Xserver, I'll say thank you.  I am running DD 6.06 64-bit version.  Your commands were quick, easy, fixed the problem in less than 2 minutes.

I appreciate your help.

---

### Post by spockrock on 2006-08-22
> **jaywatkins said:**
> Okay, here is my problem.

Aside of being dumb enough to update w/o realizing the potential for breaking Ubuntu, I have the firewalker firewall running, and it is set to start at boot.  All I have been able to do so far is get it to block all connections, which it is currently doing.

How does one turn off Firewalker from the terminal?  

The ps -ax command sends all data rushing past w/o a way to scroll and find the process.  Plus, the data moves off of the screen and each line cannot be completely read in it's entirety.  

What directory and what command shuts off Firewalker?

I love Ubuntu, and I cannot complain because all of this is free, but this is the type of thing that would send some folks rushing back to Windows.  I had to type this on a Windows machine because Ubuntu had an update for XServer.

Lesson learned, DO NOT update Ubuntu...

Thanks

/J

I am not sure if this is the best way to solve your problem but killall might work.

```
killall <name of execuatable>
```

my guess would be killall firewalker
you could always use tab to help you figure it out.

after that you might be able to connect I am not sure.

also plx this is the first update that has been this bad, there is nothing wrong with updating ubuntu.

---

### Post by gammagoat on 2006-08-22
Guys none of this is working apt-get finds no pakages, and the deb package doesnt work either.   

have tried

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10  

sudo apt-get install xserver-xorg-core=1:1.0.4-0ubuntu10

sudo apt-get update
sudo apt-get upgrade....solved nothing.

---

### Post by autosuggested on 2006-08-22
Congratulations to the team on getting this fixed quickly, but it worries me that this is the [second]("http://www.ubuntuforums.org/showthread.php?t=143334") major f**kup in a few months that is specific to Ubuntu.

// Dave

---

### Post by Ricko on 2006-08-22
I just tried installing Ubuntu for the first time on a new laptop using a distro 5.10 disk I'd gotten at a con. Everything went fine until I hit this xserver problem. 

Now I'm at a loss. Like Gammagoat above I tried the things he listed - update and upgrade and installing the .4 version but it still doesn't work. 

What am I missing?

---

### Post by compwiz18 on 2006-08-22
Would it be possible for some back up solution to be implemented, like Ubuntu keeps the last good version of xserver-xorg-core and the last good version of Xorg.conf, and if the Xserver fails to start, it installs/replaces both of them automagically, boots the Xserver, and informs you that the Xserver is not running the lasted version and Xorg.conf was temporarily replaced and gives you the ubuntuforums.org website for help?

Just something more then "your Xserver is unable to start."

Anyway, thanks for all the hard work on Ubuntu and the quick and easy fix to solve the problem - it took less then two minutes.

---

### Post by WiLLiE on 2006-08-22
Reinstall your gfxdriver, as explained in the first post.

---

### Post by spockrock on 2006-08-22
> **gammagoat said:**
> Guys none of this is working apt-get finds no pakages, and the deb package doesnt work either.   

have tried

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10  

sudo apt-get install xserver-xorg-core=1:1.0.4-0ubuntu10

sudo apt-get update
sudo apt-get upgrade....solved nothing.


sorry but how is are the deb packages not working??

and

what happens when you run
```
apt-cache policy xserver-xorg-core
```

I get this
```
 *** 1:1.0.2-0ubuntu10.4 0
        100 /var/lib/dpkg/status
     1:1.0.2-0ubuntu10.3 0
        500 http://archive.ubuntu.com dapper-updates/main Packages
     1:1.0.2-0ubuntu10 0
        500 http://archive.ubuntu.com dapper/main Packages
```

note is that version 1.0.2-0ubuntu10.4 is installed....if you have what I have on the top line then you may have to reconfigure the package and install your drivers as it has been stated.

---

### Post by croc1 on 2006-08-22
Thanks for the fix it worked great,will check the forums next time before in stalling this type of update :D

---

### Post by Myrgen on 2006-08-22
I've tried all the fixes suggested. Unfortunately, no joy. I finally tried the apt-get update: no problem. apt-get upgrade: error 404 - Not Found??????? I must add that I get the same 404 when wget -c http:// to any of the links given here.. Any idea?
(I'm on Windows atm, and missing my Ubuntu)

---

### Post by gammagoat on 2006-08-22
after running this{apt-cache policy xserver-xorg-core} I get not installedin on my top line. I dont know what to do with a deb package in this situation, think you could clue me in spockrock?

---

### Post by wrgross on 2006-08-22
I've heard some complaining in this thread...

To be fair.  I have been using Ubunto for about 2 months.  Before that I've used Red Hat, Fedora Core, Suse, Mandrake, Debian, DSL, Gentoo and a few others for years.

Ubuntu is the easiest distro I've ever used.

This was the first issue I've had, and there was a fix up by the time I got home !

Props to all the peeps in Ubuntu land.

System:
64bit AMD Turion laptop and using the wireless nic!

Soon as I get WoW running on the Wine, I can nuke my last Winblows box.

Bill

---

### Post by Jax55 on 2006-08-22
Thanks for the patch, all at Ubuntu...

But, seriously, why the heck wasn't that 10.3 patch pulled off the servers yesterday when the news broke?   Surely a few alarm bells should have gone off when the first few bug reports started rolling in.

I know this is a free service, and yes it happens in Windows land too, but Linux hitting the big time comes from advocacy, and it is pretty hard to do that when all Ubuntu machines on a site go down one morning after an auto update (and all Windows and Slackware machines stay up).

Sure people make mistakes in software and send them out in live versions (done that plenty of times myself), but there was a good opportunity to pull that patch until some serious investigating was done.   Instead, it stayed there untile the (potentially equally buggy) 10.4 version surfaced.

---

### Post by Rick Myers on 2006-08-22
I'm going to add my 2 cents here.

Have ya'all heard of Quality Control? Is this stuff tested before it's released? ](*,) 

I've got one Ubuntu installation that required special tweaks on the xorg.conf file. That was also lost during this little mishap. No backup was created during upgrade that I can find.

You're doing nothing to advance the cause of getting Linux adopted on the desktop with this type of problem. In fact, you're actually hurting the effort. The Dapper upgrade caused problems and now this! Strike 2!! 

Personally, I'll switch to a different distro if it happens again.

---

### Post by thibeaz on 2006-08-22
You mean I could of avoided this messup. I thought my ubuntu partition was gone](*,)  (at least the xserver) so I installed another linux distro called Dreamlinux. ahh I stop using ubuntu for a bit but not for a long while. I'll wait for the edgy eft release

---

### Post by daynah on 2006-08-22
Wow. There are some serious issues with some of the people above. How many blue screens did you get before switching? On a linux forum, the number is probably disproportionally low to the majority of the population. And this is nothing compared to many of the problems plagued by other operating systems over and over and over again.

Somebody screwed up. Yes. But guess what? You screw up. All the time. Just ask your significant other (or for a possible better example, look at your lack of significant other). Everyone fucks up, sometimes major. No one said the O-Ring was a-okay even though it was a bit nippy. There's no massive tragedy or loss of... really... anything here!

So calm down. Take a chill pill... or a bottle, or two, or some funny tasting kool-aid, and remember you have screwed up just as bad, if not worse. Reserve yelling rights if the person doesn't try to fix their momentary blondeness.

---

### Post by nikosft on 2006-08-22
Thanks god I have a dual boot with windows and I was able to view this post. Make the announcement bigger and may be put it in the ubuntu.com

Why the update still exists in the repositories?

That's the bad things about community things and that's why some people are willing to pay for software

What about creating a system restore utility, just like windows?

---

### Post by Seer on 2006-08-22
I gotta say....

Number of times an update in Windows XP has hosed my system in some way in the last 4-5 years........ Zero

Number of times an Ubuntu (component) update has hosed my install in some wa in the last 4-5 MONTHS ...... 4 or 5

Number of Blue Screens seen in Windows in since turned of the century ..... <1

Please stop the FUD. I love and use both OS's but I have to say the stereotypical MS bashers are just making themselves look stupid with FUD like the above post by Daynah

---

### Post by eddmun on 2006-08-22
Can we change the announcement on the front page to a really big bright red thing, I missed it when I came in a posted a new thread. 

Now I feel like an idiot.

Took some fixing, that one did though - bringing the whole networking CLI out of the box.

I agree with daynah about everyone calming down a bit, but it is just the fear or what to do next. My experience is that when it breaks, it really royally screws up bad. 

It's a good job I have a Windows computer to hand when things go wrong ;)

---

### Post by gottferdamnt on 2006-08-22
Another problem after upgrade: [http://www.ubuntuforums.org/showthread.php?t=145068&page=127&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=145068&page=127&highlight=compiz)
:'(

---

### Post by spockrock on 2006-08-22
> **gammagoat said:**
> after running this{apt-cache policy xserver-xorg-core} I get not installedin on my top line. I dont know what to do with a deb package in this situation, think you could clue me in spockrock?

please understand I am a relatively new user but to my understanding that mean that its not installed so best bet is to

```
sudo apt-get install xserver-xorg-core
```

as for .deb files

you just have make sure you are in the same directory as they are saved in terminal. and 

```
sudo dpkg -i <filename>.deb
```
using the tab key is great for getting the filename right.

so if a deb was saved on desktop, then cd to the desktop and run that command above. hope that helps.

---

### Post by n00blar on 2006-08-22
Quick updated for those running NVIDIA drivers.


_I just ran the updated xorg deb files and the NVIDIA drivers seem to run fine without having to re-install them._

The way I know that the NVIDIA drivers run fine is because I see the NVIDIA logo, or the screen, come up after I type my username and password.

---

### Post by jaywatkins on 2006-08-22
> **spockrock said:**
> I am not sure if this is the best way to solve your problem but killall might work.

```
killall <name of execuatable>
```

my guess would be killall firewalker
you could always use tab to help you figure it out.

after that you might be able to connect I am not sure.

also plx this is the first update that has been this bad, there is nothing wrong with updating ubuntu.

I tried that, but I needed a process ID.  That flew by the screen.  

How would a terminal command be issued to display the return one page at a time?

Thanx

---

### Post by cantormath on 2006-08-22
I wish I had read this before I reinstalled my system.
The updates completely broke my xserver.  even on a fresh install.
thanx for the fix, will try it.

---

### Post by NewDisciple on 2006-08-22
Thanks to tseliot who has saved the day.  I got a 404 error with the first set of instruction so I went ahead and used the 64 bit version.  Worked like a charm and I didn't have to reinstall my nvidia drivers.  The Ubuntu community is great.  If this had happened on window the majority of victims would still be on hold waiting for tech support.

---

### Post by najames on 2006-08-22
tseliot, thanks for posting the information (64bit).  Like I said elsewhere, I tried reconfiguring xserver a couple of times and gave up and went to bed, hoping for some help today. I was dreading losing my system drive, and 4 drive raid5 setup, VMware server test box.  You made my day ole buddy!!!

To the whiners.  If you want, feel free and start coding to make it better.  My M$ Internet Explorer totally died at work too, AFTER they installed M$ hotfixes.  Did anyone offer a fix within a day there?  Nope.  It took about a  week for me to get an answer.  Did I know what patches they applied that broke it?  Nope.

As the saying goes, Sh*t happens.

---

### Post by spockrock on 2006-08-22
> **gottferdamnt said:**
> Another problem after upgrade: [http://www.ubuntuforums.org/showthread.php?t=145068&page=127&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=145068&page=127&highlight=compiz)
:'(

try what I suggested in that thread it fixed it for me, here it is anyways

```
sudo apt-get install -f
```

---

### Post by cantormath on 2006-08-22
> **Rick Myers said:**
> I'm going to add my 2 cents here.

Have ya'all heard of Quality Control? Is this stuff tested before it's released? ](*,) 

I've got one Ubuntu installation that required special tweaks on the xorg.conf file. That was also lost during this little mishap. No backup was created during upgrade that I can find.

You're doing nothing to advance the cause of getting Linux adopted on the desktop with this type of problem. In fact, you're actually hurting the effort. The Dapper upgrade caused problems and now this! Strike 2!! 

Personally, I'll switch to a different distro if it happens again.

I hate these kinda of comments, they are totally unproductive, unhelpful, and generally come from a source who has no place to comment.

---

### Post by Adler on 2006-08-22
**Is** there a fix for this?

I've been waiting for things to settle down since crashing 15 hours ago and now up-dater isn't working. 

Adler

---

### Post by AllenGG on 2006-08-22
Now working:
sudo apt-get update
sudo apt-get upgrade

.....then reboot, NOTE: you must be in as 'ROOT"

---

### Post by selfmade on 2006-08-22
i had already updated and managed to break x. tried apt-get update and apt-get upgrade to fix, no dice. really dont want to have to reinstall, since i didnt set up the partitiions on this machine and am not sure whats what. please help?

---

### Post by spockrock on 2006-08-22
ok umm I am sorry I do not I am sure the but I am guessing the deamon starts with 'f' you could try killall f and press tab to see whats running.  it might be fire something.....maybe sorry I couldnt even find firewalker on google, so I couldn't even check for you.

---

### Post by garba on 2006-08-22
all i can say is that what happened is embarassing to say the least ](*,)

---

### Post by jaebird on 2006-08-22
Without the community there is NO open source. Well... maybe one dude coding alone at night! I mention as much in my blog post at [http://jaebird.wordpress.com/](http://jaebird.wordpress.com/)

Edit:
OK...well it took awhile for that comment to publish...doesn't make sense where it ended up. I did a:
sudo apt-get dist-upgrade

when my x.org first blew up. That did the trick for me.

---

### Post by spockrock on 2006-08-22
@jaywatkins
ok umm I am sorry I do not I am sure the but I am guessing the deamon starts with 'f' you could try killall f and press tab to see whats running.  it might be fire something.....maybe sorry I couldnt even find firewalker on google, so I couldn't even check for you.

---

### Post by nikosft on 2006-08-22
Before applying the fix I messed up with xserver-reconfigure. Now everything works well apart of a message at boot time saying : 

agpgart:Aperture conflictes with PCI mapping

and then everything loads smoothly. Is that a coincdene? Has anybody a clue?

---

### Post by gottferdamnt on 2006-08-22
> **spockrock said:**
> try what I suggested in that thread it fixed it for me, here it is anyways

```
sudo apt-get install -f
```

Thank but It doesn't work :frown:

---

### Post by Mr. Picklesworth on 2006-08-22
More thoughts...
Sorry for being detached from this thread. I should start my own, and this should actually be in the bugs/feature requests database.
Anyhow...

System-critical packages like the X server stuff should (and could) be identified by the Synaptic Package Manager.
The updater would then be able to highlight any system-critical updates that have a chance of messing something up.

Theoretically, such a change would be very well worth it.
Could start off with just a little list of System-Critical Applications in Synaptic, and later updates could perhaps add user-defined notable package lists (NPLs?) as well.

If a package from the system-critical list is updated, Synaptic could hold onto the old version for a while in case something goes wrong.
In the previously suggested X-less fallback mode (or just on the desktop when something really bad happens), it could suggest that a system-critical package has been updated (using dependencies to figure out that it could be connected to the problem?) and ask if the user wants to revert to the previously installed version.

Further enhancements to user-defined noteable package lists could be commands to call when a package is updated.
For example, if I get a kernel update I always need to recompile ndiswrapper and turn off the default mrv8k driver. It would be amazing to have that done automatically.

It is undoubtedly a much bigger job than I make it seem, but imagine how good it would be :)
Ubuntu could go from having a rough track record for updates to having the most safe and featureful updater ever!

---

### Post by chinaski on 2006-08-22
> **Rick Myers said:**
> I'm going to add my 2 cents here.

Have ya'all heard of Quality Control? Is this stuff tested before it's released? ](*,) 

I've got one Ubuntu installation that required special tweaks on the xorg.conf file. That was also lost during this little mishap. No backup was created during upgrade that I can find.

is a good rule to backup **anything** important. if you didn't followed it, don't blame others. this applies to conf files too (and especially).
> 
You're doing nothing to advance the cause of getting Linux adopted on the desktop with this type of problem.
 it's still much, much more than [B]you do
[/B]> In fact, you're actually hurting the effort.
 you are hurting the effort of being a nice community

BTW, I am sorry for who had problems, but thanks god I am on holiday and have no broadband connection to do updates:mrgreen:

---

### Post by Craftaz on 2006-08-22
yeah.. after installing drivers my gf Ti 4200 became a ATI RV100 :DDDD is it a joke or what???
-----------------------------before----------------------------
Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	60-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"

------------------------------------after-----------------------
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
----------------------------------------------------
did I do something wrong?...

---

### Post by jonprc on 2006-08-22
this might be a real stupid quesiton after 11 page of this.
but i just want to check if this update i'm being offered is the bad one OR a new replacement that's good:
1:1.0.2-ubuntu 10.4

thanks.

---

### Post by jaebird on 2006-08-22
That is what I've got

---

### Post by givré on 2006-08-22
It's the good.

---

### Post by steve.horsley on 2006-08-22
> **jonprc said:**
> this might be a real stupid quesiton after 11 page of this.
but i just want to check if this update i'm being offered is the bad one OR a new replacement that's good:
1:1.0.2-ubuntu 10.4

thanks.

That's the fixed one. I don't know the version number of the broken one, but it's gone froim the mirrors, and I have seen other posts in this thread that name 10.4 as the fix. In fact, see the first post (edited) by tseliot.

---

### Post by mrgnash on 2006-08-22
I'm getting a 404 error when trying to upgrade to the new package.

---

### Post by killkoy on 2006-08-22
i reinstalled ubuntu because of this, lol I thought id broken it with my fiddling, thats one lesson learnt > use lynx in future :D

---

### Post by cantormath on 2006-08-22
is the xserver-xorg-input-mouse alright to install, or is that cause the error also?

---

### Post by jaebird on 2006-08-22
This may work well and good, but I was able to get my system back by simply doing a dist-upgrade. My proprietary NVIDIA driver was intact as was my XGL/Compiz.

---

### Post by givré on 2006-08-22
> **mrgnash said:**
> I'm getting a 404 error when trying to upgrade to the new package.
I had the same one. I guess it's because the upload package.gz file before the package, so it don't propose you the 10.3.
Be patient and retry.

---

### Post by ispmarin on 2006-08-22
... just two seconds before updating. The fix was fast, but the error, terrible. The problem is not a hiccup here and there, but the rate that this errors are happening in ubuntu and the problems that they are causing. Maybe this is the cause that the debian developers are angry at ubuntu, and with reason.

---

### Post by cantormath on 2006-08-22
> **ispmarin said:**
> ... just two seconds before updating. The fix was fast, but the error, terrible. The problem is not a hiccup here and there, but the rate that this errors are happening in ubuntu and the problems that they are causing. Maybe this is the cause that the debian developers are angry at ubuntu, and with reason.

This is the first time I have had a problem like this, and there was a fix up in a few hours......
thats pretty fast.

Does ANYONE know if the **_xserver-xorg-input-mouse_** update is part of this error???????????

---

### Post by BillsterJ on 2006-08-22
UNABLE TO ACCESS KDE IN KUBUNTU

I reverted back to the old Xserver provided in this thread.  I also reinstalled the nvidia drivers as directed by this thread.  I am running on an Alienware laptop (LCD screen).

It boots like normal, however, when it gets past the initial splash screen I get garbled video.  Instead of being able to input my password it looks like a big white blotch.  Perhaps I need to install drivers particularly for laptops?  I never had any problems before running on the old open source "nv" drivers with just a normal install.  Can I somehow get Kubuntu to run the auto-config done by the installer?  Is it trying to send my LCD monitor a CRT signal?

PLEASE Help, I'm a Kubuntu newbie at this and I don't want this to be the third time I have to reformat.

---

### Post by probbins on 2006-08-22
It was a simple fix for me. 
Logged in as root,
Did apt-get update,
then apt-get upgrade all.

This installed a new version of the xserve.

Rebooted the computer, a cold start, and all was fine.

I haven't needed to re-install Nvidia.

I'm on an Acer 1710 laptop.

---

### Post by cantormath on 2006-08-22
> **cantormath said:**
> This is the first time I have had a problem like this, and there was a fix up in a few hours......
thats pretty fast.

Does ANYONE know if the **_xserver-xorg-input-mouse_** update is part of this error???????????

Thats a no.....

---

### Post by jonzep on 2006-08-22
don't know if it's been mentioned (didn't rtf 43 pages) but all i had to do is type...


```
sudo apt-get upgrade
```

that updated X in 5 seconds and after a reboot all is fine.

---

### Post by ispmarin on 2006-08-22
> **cantormath said:**
> This is the first time I have had a problem like this, and there was a fix up in a few hours......
thats pretty fast.


It is not the speed of the correction (if you follow the launchpad bug report, you will see Rodrigo working as fast as hell), but the frequency that major bugs are happening in ubuntu, and the severity of those. Even in your post you show (and with total reason, as everybody else) to NOT to trust the updates. And this is a serious problem for ubuntu. Even in debian unstable something as large as this would be problematic. And this is vanilla ubuntu...

---

### Post by TrendyDark on 2006-08-22
Has the bad update been removed from the repositories? I did a fresh install of Ubuntu and when I update I don't want to break it again.

---

### Post by glennric on 2006-08-22
The problem has been fixed in the repositories.  The newest version there works fine.

---

### Post by JamesAguilar on 2006-08-22
You guys are awesome.  You've given me a great free operating system and I love it.  However, stuff like this is the reason Linux and Ubuntu are not ready for the common man's desktop.  

Not that I have any right to complain -- it is all free.  And I'm happy with it, even with its faults and foibles.  But I just want you to know.

---

### Post by TrendyDark on 2006-08-22
> **glennric said:**
> The problem has been fixed in the repositories.  The newest version there works fine.

Thanks, I was just wondering. Right after I posted that I read on a blog somewhere that the bug was fixed and that the new packages have been uploaded.:biggrin:

---

### Post by Bigmack on 2006-08-22
Many thanks to you, tseliot!!!!:D :D 
Following your instructions at the beginning of the thread fixed my machine:D 
I allowed ubuntu to boot, acknowledged the error and the system continued to the prompt. Typed in the code, rebooted and everything is fine!:D 

This is an outstanding education!! Not only am I learning Linux, but also how to ttyyppee as well!!!:D 

Community support is where it's at!!:biggrin:

---

### Post by palz on 2006-08-22
worked like a charm! Thanks!=D>

---

### Post by Adler on 2006-08-22
tseliot,

**Thanks** for the post @ the start of the thread! I'd actually thought there were two threads going on the same issue.

On a fresh install of UBUNTU I ran your codes and eveything is back to normal as far as the OS goes.

Again, Thanks!

Adler

---

### Post by selfmade on 2006-08-22
teh fail. apt-get update, apt-get upgrade didnt work. neither did downgrading. still getting no screens found and PCMCIA keeps failing. i have to use windows to do anything and its making me crazy. please help?

---

### Post by Lord Landis on 2006-08-22
**glennric** - *The problem has been fixed in the repositories. The newest version there works fine.*

Sooo...  The version that I just updated to about twenty minutes ago or so won't break X now?  I hate having to re-install fglrx...

---

### Post by jaebird on 2006-08-22
Can you try:

$ sudo apt-get dist-upgrade

---

### Post by Bozebus on 2006-08-22
Thank you tseliot. Its friendly, knowlegable people such as yourself that make the linux experience much better for all of us. In the future, I will allow a 24 hour period before I do another update.

---

### Post by Eleka on 2006-08-22
Thanks a lot, I think that this problem is only form me .... ufff!!!

A question now: I reinstalled the Nvidia driver (the nvidia-glx package) and I can't have direct rendering ... Should I re-install some more packages?

---

### Post by selfmade on 2006-08-22
sudo apt-get dist-upgrade .... no dice

---

### Post by JackAcid on 2006-08-22
I followed a different thread and downgraded Xserver. If I follow your instruction, will it get rid of the upgrade icon in the status bar?

Also has anybody reported good results with your fix? I haven't read all of the replies yet, but people don't seem too happy with the situation right now.
Anyway.... Thanks for your efforts=D> , this thing really caught me off guard! Thank goodness for the forum!
Regards,
Jack
> **tseliot said:**
> [SIZE="4"]HOWTO solve the problem[/SIZE]

[COLOR="Red"]UPDATE:[/COLOR]
The recent updates break the Xserver. If you have already updated Ubuntu please type the following command:
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
```
```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
```

```
sudo dpkg -i xserver-xorg-core*.deb
```

If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work


**[COLOR="Red"]NOTE: 64bit users should do this:[/COLOR]**
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```
Then restart your computer
```

sudo reboot
```

---

### Post by jrjr on 2006-08-22
.

---

### Post by jryer on 2006-08-22
I would try the recommended terminal commands to solve the problem; however, I have no working Internet connection. How do I set my wireless eth0 connection from the terminal?

Alternatively, I would copy the update to a flash drive and then access it from my ubuntu shell to install; however, ubuntu fails to recognize my USB device. Rather, when my flash is plugged in, I receive constant errors that the USB cannot be read or mounted or something like that. Maybe there is a fix for this? However, I would have to download it and without having Internet, I am back to the first problem mentioned above.

Does anyone have any recommendations on how to solve this problem? For the time being, I cannot work in Ubuntu.

I appreciate any help in advance in solving the problem but honestly and without mincing my words, shit like this really should not happen. Hopefully we learn from our mistakes, right? But in the meantime, its back to Windows.

Saludos,
Jason

---

### Post by shanen on 2006-08-22
I also regard this as an extremely unfortunate incident, and it took me about a hour of struggling before I was able to fix it. All that was finally required in my case was an "apt-get upgrade" command. I think I was already in the "sudo -s -H" condition, so I didn't use the sudo for the apt-get. Mostly it took me a long time to reach the conclusion that I hadn't done anything wrong, but I'm not sure how I leapt to the conclusion of hoping that an upgrade might fix it...

Kudos to whoever implemented the fix via the fairly natural apt-get approach. The long confusing fix should be removed from the front of this thread. More likely to make things worse if someone makes a typing mistake.

Anti-kudos to whoever approved the distribution of this poorly tested patch. Auto-update should *NEVER* break things so badly. I shudder to think how many people may have gotten a negative exposure to the deep internals of Ubuntu because of this mistake.

---

### Post by Cephus on 2006-08-22
The fix worked perfectly on my Sony Vaio laptop.  The downside is I had to start a Windows session in order to even see the fix documentation.  I'm not afraid of the command line, but as a Linux newbie, I don't know how to surf the web from the command line.

---

### Post by Lonthong on 2006-08-22
when I tried to update to version 10.4 I got this warning:
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb)
404 Not Found

---

### Post by missmoondog on 2006-08-22
ah! now that's better. updated computer #4 just now. no problems even with the ancient nvidia card in here. 

was already able to fix one of the other computers that was all foobarred from this mornings fiasco!

one more to fix and 3 more to risk doing the update on. tomorrow, that is. after wasting all day this morning on this mess, it's time to play for awhile! ;)

---

### Post by JRS on 2006-08-22
=D> Thanks for yhe fix. Just like it was before. Love this O/S!

---

### Post by wordsmythe on 2006-08-22
I've tried all the suggestions so far (yeah, I've read all 45 pages of "thanks" and such comments :roll: ).  Still no luck.  I must have messed something up before I found this thread.

[http://www.ubuntuforums.org/showthread.php?p=1411080](http://www.ubuntuforums.org/showthread.php?p=1411080)

Can someone just tell me what needs to be installed in order for X to run and see a monitor?  I've got a KVM switch going, but I've tried it without, too.

---

### Post by mrgnash on 2006-08-22
> **Lonthong said:**
> when I tried to update to version 10.4 I got this warning:
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_amd64.deb)
404 Not Found

Same problem here. What's the deal?

This is more frustrating than the breakage (which was easily fixed), if only because of that annoying little update icon ;)

---

### Post by unwoken on 2006-08-22
Wow.

There is an awful lot of anger in this thread.  Maybe constructive comments would be more useful.  If this is enough to make somebody immediately uninstall Ubuntu, i hate to think what these same people may think if/when they attempt even simple things like configuring TV-out, or connecting to a VPN...

This is the first time an official update has crashed my system in my ~year or so of using ubuntu.  I was able to fix it in a few minutes (very easily).  I have crashed my own system countless times over that period, and got it back - mainly thanks to this community.

Firstly i would like to thank tseliot for the fix on page 1 which helped me restart my computer, fully operational, with very little disruption.


I do have a comment / plea, for tseliot (just because it is obvious on this thread), and also to **ANY** other person who makes a howto etc.  

I am happy to learn anything, and generally enjoy attempting to fix my computer when things go wrong.

What i find to be slightly frustrating is a general lack of instruction or maybe explanation, of fixes.  For example.  What do the instructions on page 1 do?  Why am i told to download 2 seperate files?  Was i even supposed to install both (the instruction was not written with a plural)?  Am i rolling forward/rolling back whatever it is i am installing?  Why am i told to reinstall my graphics drivers, with no explanation at all? or even instructions on how to do so?

When people ask legitimate questions and are told to see page 1, which actually in no way answers the question they asked (at least to a non expert), then what does one do?

If one asks question, posts such as: "Reinstall your gfxdriver, as explained in the first post.", many pages into a thread, which point a user to an incomplete instruction, are not massively helpful.

..

It seems fair to say that the people who are on this thread complaining bitterly about the breakage are not console or ubuntu gurus.  It is worth remembering that the more automated installation programs e.g. automatix, easy ubuntu - that exist, the more people there are who are not quite sure how (for example) to install their graphics driver from scratch.

I also think that it is a reasonable proposition that telling such a person to install a graphics driver without instruction, when they are already seeing red over the lack of a GUI, is a recipe for potentially extreme frustration.

..

Don't get me wrong.  I love Ubuntu.  I love using ubuntu.  I see this as a very minor event, when my overall experience of this OS has been brilliant.

I know that the people involved with this community offer help with an almost universally fantastic spirit.  They give help for it's own sake, and this to me is a great thing.

My point is that by thinking about these things, we can minimise the general frustration of certain members, and teach people so that they have a greater understanding of what is happening, rather than knowing that somebody will probably come along and give them some code to type in the next time something goes wrong.

peace all ;) 

u.

---

### Post by crgutierrez on 2006-08-22
God bless you! :KS 
Your indications got my laptop's xserver runing again!

This is more than LTS, this s support on real time!!!!!

Just one question: why, if I updated both my desktop and my laptop this morning, only my laptops xserver failed? Is my desktop going to fail tomorrow?

Regards from Costa Rica

---

### Post by jimmygoon on 2006-08-22
As much as I'm nearly ready to jump in front of a train for the name sake of ubuntu, I have to say I'm disappointed that this update was not only made live... but LEFT live...

Oh well... mistakes happen. I just hope it gets fixed soon! Thanks guys! BTW: I've yet to reboot after upgrading. I wrote down everything in case... hope I can read my writing!

WISH ME LUCK... or not ;)

---

### Post by craig109 on 2006-08-22
After trying other fixes that didn't work, the "apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10" did the trick!

My video card is an ATI X300.

Thanks for the quick fix. I just started using Ubuntu last night (have run Debian, AIX, Red Hat in the past) and I must say that although this was a rather serious glitch, finding the solution was a lot more simpler than finding many fixes for Windows issues.

Never mind those who are getting all pissed...they're just not ready for Linux yet.

=D>

---

### Post by bsell on 2006-08-22
> **mrgnash said:**
> Same problem here. What's the deal?

This is more frustrating than the breakage (which was easily fixed), if only because of that annoying little update icon ;)

Either the file isn't there or the server refused your request without telling you why.

The first bug report on the breakage was filed with Launchpad  on August 21st. Yesterday. I downloaded the update 4 hours ago and had to downgrade  immediately. My hat is off to those who have expressed frustration in a manner that irked some of the more sensitive members and forum staff. 'Tis fitting and righteous.

---

### Post by ChuckNH on 2006-08-22
I've tried every solution offered, and none have worked! Planning to stick by Ubuntu, but very frustrated to go throught this process.......how could such a simple bug get through? Did no one run this "upgrade" before posting it????? Never mind the defensive posture of the hard core here.  I like the fact that this could be a learning experience, but this does seem a bit careless, no?  I cannot get back to my desktop that I was so happy with.......and would like some help....

---

### Post by VoodooChile on 2006-08-22
I got the xserver error after updating and rebooting, so I did a sudo aptitude update, and then sudo aptitde dist-upgrade, and now instead of getting the xserver error and then the command prompt I get a blank screen, it looks as if its going to load into the login screen, but it doesnt, at that point my only choice is to press the restart button. Any ideas? I'm pretty much new to linux, so detailed help would be much appreciated.

---

### Post by jonathansizz on 2006-08-22
> Don't get me wrong. I love Ubuntu. I love using ubuntu. I see this as a very minor event, when my overall experience of this OS has been brilliant.

You've got to be joking. I doubt the thousands of recent converts who just got their machines hosed see this as a 'minor event', and such ridiculous apologetics isn't going to help matters, is it?

I certainly won't be recommending Ubuntu or it's derivatives to anyone I know again. This was the last straw. It's embarrassing when I have just explained to someone how Ubuntu is better coded and more stable than windows for this kind of thing to happen. And the update stayed in the repositories for hours after this problem was known!

---

### Post by mrgnash on 2006-08-22
And how exactly is whining about it going to help? 

Personally I wouldn't recommend any distro to computer novices, or anyone who isn't prepared to learn enough to at least get around the CLI; which, after all, is still the foundation of Linux.

---

### Post by mgpower0 on 2006-08-22
> **jonathansizz said:**
> You've got to be joking. I doubt the thousands of recent converts who just got their machines hosed see this as a 'minor event', and such ridiculous apologetics isn't going to help matters, is it?

I certainly won't be recommending Ubuntu or it's derivatives to anyone I know again. This was the last straw. It's embarrassing when I have just explained to someone how Ubuntu is better coded and more stable than windows for this kind of thing to happen. And the update stayed in the repositories for hours after this problem was known!

been reading crap like this for the last two days now. Thing is linux is a comand line based OS. xserver is just a pretty GUI for it. suggest if you want to use linux then learn at least a bit about using command line. If you don't want to learn stick to windows and stop the bitching.

---

### Post by spockrock on 2006-08-22
> **ChuckNH said:**
> I've tried every solution offered, and none have worked! Planning to stick by Ubuntu, but very frustrated to go throught this process.......how could such a simple bug get through? Did no one run this "upgrade" before posting it????? Never mind the defensive posture of the hard core here.  I like the fact that this could be a learning experience, but this does seem a bit careless, no?  I cannot get back to my desktop that I was so happy with.......and would like some help....

what does 
```
apt-cache policy xserver-xorg-core 
```

if it gives you.....try installing you drivers.

xserver-xorg-core:
  Installed: 1:1.0.2-0ubuntu10.4
  Candidate: 1:1.0.2-0ubuntu10.4
  Version table:

---

### Post by bsell on 2006-08-22
> **VoodooChile said:**
> I got the xserver error after updating and rebooting, so I did a sudo aptitude update, and then sudo aptitde dist-upgrade, and now instead of getting the xserver error and then the command prompt I get a blank screen, it looks as if its going to load into the login screen, but it doesnt, at that point my only choice is to press the restart button. Any ideas? I'm pretty much new to linux, so detailed help would be much appreciated.

Try downgrading and wait before installing the latest "update". Use this code to downgrade:

```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

---

### Post by spockrock on 2006-08-22
> **VoodooChile said:**
> I got the xserver error after updating and rebooting, so I did a sudo aptitude update, and then sudo aptitde dist-upgrade, and now instead of getting the xserver error and then the command prompt I get a blank screen, it looks as if its going to load into the login screen, but it doesnt, at that point my only choice is to press the restart button. Any ideas? I'm pretty much new to linux, so detailed help would be much appreciated.

first you can press ctrl+alt+f1 and bring up virtual terminal from there re-install your video card driver or reconfigure the package as stated in this thread earlier.

---

### Post by jckdnk111 on 2006-08-22
> **Dale61 said:**
> G'day, another recent Ubuntu convert.

Took the plunge 3 weeks ago, and all was going swimmingly, until this morning.

I had been telling a few mates about how much better my pc was running since installing DD, and had convinced one to consider changing his small office pc's over from Windoze.

Anyway, was sitting here showing him around the desktop and what different things were when I noticed I had an update ready for downloading.  Perfect, I thought, as this will show him how easy it is to keep his systems up-to-date.

Proceeded to d/l the xserver update, rebooted, and nothing!  Xserver failed, and I couldn't explain why.  After an hour or so, he was no longer interested in upgrading, which means there will be a dozen less pc's converting to Ubuntu.  May not sound like a lot, but he will tell others, and so, it will travel down the line.

I continued to find a remedy, and fortunately, I have a laptop (XP) setup close by, so I connected to the net and searched far and wise for an answer.  I came across this forum, and following the instructions above, I was able to get my pc up and running as it was pre-update.

Overall, this was an 8 hour exercise, 8 hours that I could afford to take out of my day, but how many others have that luxury?  I'm wondering how many others, particularly those in business, who are still trying to find a solution to a problem that should NEVER have happened in the first place.  I pity those who don't have a backup system and are still trying to work out what's happened.

I would just like to thank all those who were quick to see the problem and submit a fix, but there needs to be some serious questions answered as to why this happened in the first place.  Don't the developers test these things on their own machines first, or are we the guinea pigs for their experiments.

My apologies for such a harsh first post, but as I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.

No offense, but I wouldn't consider myself lucky to have windows installed on any of my computers. Ubuntu is a great OS and if you had to rant every time micro$oft shipped out a bug / shipped out a bug patch full of bugs, you would need a a team of witty bloggers at your side.

Instead of bitching at people who write nice open source software and package it up nicely for lazy people like you and I, you should read a book or learn a little about the OS / software you are using (y? because you can and it's free). If windows suddenly blue-screened on you, you better believe you'd be reinstalling from scratch. I installed lynx (apt-get install lynx) and went straight to the forums when x wouldn't start. Amazing, an operating system that can actually recover from an admittedly rare developer error.

You want to pay for windoze and still have to spend 8 hours figuring out what the hell went wrong, go right ahead. 

Go Ubuntu!

---

### Post by akak8ty on 2006-08-22
I have told microsoft off sooooooooo many times, calling them capitalistic ********* words I am not allowed to say here, and they were the Masters of bugs and glitches. 
As I was just saying to someone else, I use open source, Sourceforge and have been fiddling with xampp, apache, PHP, Perl et al. for a while. 
In this scenario I don't know if the release was tested first, but other places usually will inform you the status, beta, unstable release, stable release- 
So in the karmic scheme of things those who were ill mannered on my first days of getting set up are hopefully having a BIG slice of humble pie now.

---

### Post by jonathansizz on 2006-08-22
> Personally I wouldn't recommend any distro to computer novices, or anyone who isn't prepared to learn enough to at least get around the CLI; which, after all, is still the foundation of Linux.

So the foundation of linux is still the CLI? Well, why don't you tell the people who want to switch from Windows this, instead of erroneously claiming Ubuntu as a Windows replacement?

Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.

---

### Post by mnorwood154 on 2006-08-22
Just as an aside for those of you crying foul and running back to Windows.  Microsoft is currently in the process of updating a patch that was pushed out last week that made Windows XP SP 2 vulnerable to compromise that could give  a malicious user/site admin access.  The patch is due out on Tuesday.  Hmmmmm, a week to fix. Nice.  And this flaw in the Ubuntu patch was put out 1 or 2 days ago, has already been fixed and is being published, and you can actually get support on their forums right now for an available workaround.  Nice work on the speedy response and fix Ubuntu guys.  

=D>

---

### Post by bodycoach2 on 2006-08-22
I did the broken update this morning, before I left for family visit. When the computer restarted, I saw the error messege. 

I think I was lucky that I had to wait till this evening to try and fix it. Came home, did the 'sudo apt-get upgrade ..."""upgrade' procedure, and fixed everything. I'm glad I wasn't stuck at home trying over and over again to fix it. 

Unfortunately, it appears I'm going to have to treat Ubuntu updates like I do the Windows or Mac updates; I wait for a few days to see if there are problems caused from the update. Had I read the forums, I would have known better than to do the update first.

Should there be a seperate section for 'update problems' or 'update conditions'? Maybe a poll section for successful updates? Not being able to start your computer (if you're an Ubuntu only home) is a problem, though.

Anyone else have any ideas on things like this?

---

### Post by spockrock on 2006-08-22
> **jonathansizz said:**
> You've got to be joking. I doubt the thousands of recent converts who just got their machines hosed see this as a 'minor event', and such ridiculous apologetics isn't going to help matters, is it?

I certainly won't be recommending Ubuntu or it's derivatives to anyone I know again. This was the last straw. It's embarrassing when I have just explained to someone how Ubuntu is better coded and more stable than windows for this kind of thing to happen. And the update stayed in the repositories for hours after this problem was known!

and a windows update hasnt hosed anyones computer, and has microsoft left the updates available.  I dont get why the ubuntu/devs does one bad update its no longer a viable OS.  yes this was a huge mistake, but seriously, I willingly downloaded, and restarted know the issue last night, X broke, I went to virtual terminal, downgraded, and come morning I had the correct update ready for download.  Both machines are working great.  Anyone using linux has to understand they have to use the terminal.

I dont see how (in my experience) one bad update in 1.5 years really bad....

---

### Post by jperez on 2006-08-22
> **jonathansizz said:**
> So the foundation of linux is still the CLI? Well, why don't you tell the people who want to switch from Windows this, instead of erroneously claiming Ubuntu as a Windows replacement?

Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.

You DO know that Windows, even XP and Vista, still run via the command-line, right?  The only thing is, you can't see it anymore because Microsoft has decided to hide that from the end-user.  Remember MS-DOS?  It's still there, you just can't really access it.  Besides, how often is it that this happens in Linux?  How often does this happen in Windows?

Really, let me know.  I'm a Windows/MS-DOS command-line junkie.  Remember your roots.  Windows still depends on MS-DOS.  No command-line, no GUI.  Remember that.

Jesse~

---

### Post by lime4x4 on 2006-08-22
Ran into the same problem..Took the updated rebooted my computer a few hours later and i was dropped to a shell.. Used my kubuntu box and ssh into my ubuntu box and followed the directions in the first post.. Now i just have to load my ati drivers again

---

### Post by raldz on 2006-08-22
Good thing I know how to downgrade packages via recovery mode when something goes wrong with an upgrade.. I was surprised to stare at the blank screen after the reboot.. downgraded immediately and checked forums.. I feel sorry for those who could not fix it immediately and render their computer useless at that moment..

---

### Post by bsell on 2006-08-22
> **jperez said:**
> You DO know that Windows, even XP and Vista, still run via the command-line, right?  The only thing is, you can't see it anymore because Microsoft has decided to hide that from the end-user.  Remember MS-DOS?  It's still there, you just can't really access it.  Besides, how often is it that this happens in Linux?  How often does this happen in Windows?

Really, let me know.  I'm a Windows/MS-DOS command-line junkie.  Remember your roots.  Windows still depends on MS-DOS.  No command-line, no GUI.  Remember that.

Jesse~

Neither XP nor Vista use DOS. They use a DOS emulator.

---

### Post by LateNighter on 2006-08-22
> **tseliot said:**
> Please, restrain yourself from using swear words in this forum.

BTW without the Xserver we would be stuck to the command line

 Agreed!!!

 Get over it Things happen...
 Samething happened to me...
 I'm not Complaining, But I bet you Dollars to Donuts he won't be Complaining Once they get it fixed...

 Just do like I did reinstall..

 And don't Upgrade xserver again, until they give the Green Light...

 or at least the Yellow One...:wink:

---

### Post by NRTech on 2006-08-22
I tried the three commands but after connecting to the service I received a 404 error - page not found.  Tried 'apt-get update' followed by 'apt-get upgrade' and everything went smoothly.  I now have my desktop back.  Excellent work Ubuntu for providing a fix so quickly!:cool:

---

### Post by Oblong_Cheese on 2006-08-22
Just wanted to say thanks for the heads-up and the fix.

I had installed the update on my AMD64 box but have refrained from doing so on my girlfriends AXP system.

Once again, thanks!

---

### Post by RRS on 2006-08-22
> **spockrock said:**
> and a windows update hasnt hosed anyones computer, and has microsoft left the updates available.  I dont get why the ubuntu/devs does one bad update its no longer a viable OS.  yes this was a huge mistake, but seriously, I willingly downloaded, and restarted know the issue last night, X broke, I went to virtual terminal, downgraded, and come morning I had the correct update ready for download.  Both machines are working great.  Anyone using linux has to understand they have to use the terminal.


Pretty much the same here, since I use my machines for learning (mostly how to fix what I've broken) rather then work it was no big deal.

I haven't read all 48 pages so maybe it's allready been asked/answered, but did this update affect other distro's as well or just Ubuntu?

And just for info, my last update of windows installed bad drivers for both my NIC and audio, had to roll them back too.

---

### Post by spockrock on 2006-08-22
just ubuntu I am sure.

---

### Post by jimmygoon on 2006-08-22
> **jonathansizz said:**
> So the foundation of linux is still the CLI? Well, why don't you tell the people who want to switch from Windows this, instead of erroneously claiming Ubuntu as a Windows replacement?

Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.


fine. You fit the bill as one of those people that tries to know what they are talking about, acts rude, realizes that human beings NEED to learn the command line regardless of whether its with a recovery console in windows or downgrading a package in ubuntu. You're one of those people that Ubuntu users don't appreciate having in the community.

If you were so intelligent you would realize that linux itself is simply a kernel and it offers nothing but a command line and that it is completely different than MS-DOS... so yes, Ubuntu still is a Windows replacement.

NO ONE is going to tell you ubuntu is perfect, and no one in their right mind would IMAGINE that windows is perfect... but I'll tell you what. How many major problems have you had with windows (x divided by zero... equals what?) and ubuntu? 1 (actually I was unaffected so, 0) but.... Ubuntu is definetly closer to perfect than windows.

---

### Post by nfs510 on 2006-08-22
I would like to say the same, please allow me to quote: "I tried the three commands but after connecting to the service I received a 404 error - page not found. Tried 'apt-get update' followed by 'apt-get upgrade' and everything went smoothly. I now have my desktop back. Excellent work Ubuntu for providing a fix so quickly!" In addition, could someone explain why the page was not there?
Thanks.

---

### Post by mrgnash on 2006-08-23
> **jonathansizz said:**
> So the foundation of linux is still the CLI? Well, why don't you tell the people who want to switch from Windows this, instead of erroneously claiming Ubuntu as a Windows replacement?

Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.

I trust you have some evidence to back your claim that I've been evangelizing Ubuntu as a 'Windows replacement?' Especially given that my statement included an anticipatory clause to the opposite.

---

### Post by Epperly on 2006-08-23
Was this fixed automatically in a newer update or do I still have to do this?? I don't get what the error is(never saw it)

---

### Post by shookmon on 2006-08-23
I find it very interesting that of all the complaints against this issue, they all seem to have at their root the same thing:

Users have learned so well the M$ model of dealing with errors and bugs (the YOYO model - "You're On Your Own") that their first step was to immediately dive into their system and try to either fix the issue themselves or back out of the upgrades. Sometimes even re-installing the OS from the ground up. This of course leading to panic, and foul language against "those idiots" running things. Whoever "they" are, and no matter "their" track record.

Rather, they should have simply and calmly gotten on to the Ubuntu forum from another PC (work, Library, friends, etc...) gone to the forum and read up on the issue and learned how to patch their system.

It's amazing how M$ and their concept of "customer dis-service" has poisoned the average users ability to deal appropriately with bugs when they happen.

On a side note, there have been MANY useful bits of things discussed in this forum that would have been really useful to know when this issue occured, and I was trapped at the CLI. Like the Lynx browser, or being able to back out of the update. Perhaps in a future version of Ubuntu there could be a MAN entry built related to how to diagnose and possibly fix your system if all you have is the CLI. Kind of like a "So your system is busted, start here".

Just my 2cents.

BTW, THANK YOU!!!! tseliot and others for an amazingly painless process that got us all through this issue. WOW, this is why open source will ultimately win over closed source models for software.

---

### Post by leeyee on 2006-08-23
That's odd, I never saw this error.
I'm using Ubuntu Dapper, and I did upgrade last night for Xserver, but my box works fine! 
BTW,I have ATI driver installed.

---

### Post by roselawn on 2006-08-23
TSEliot, Thank you for the fix! You are the best, I just wish I checked the forums earlier.

---

### Post by Carbonfish on 2006-08-23
> **Epperly said:**
> Was this fixed automatically in a newer update or do I still have to do this?? I don't get what the error is(never saw it)

I will have to second this question. I ran the update this morning, but my system seems to be running fine. It's a laptop, so I've booted the thing about 10 times since the update and have used most of the apps. that I use day-to-day and haven't run into any problems. 

Should I still run the downgrade? Or did I unwittingly dodge a bullet? Or am I secretly *bulletproof*??

Most importantly, do I have to go back and read all 49 pages to find out?

Thanks for any info.

Kent

---

### Post by wavetheory on 2006-08-23
tseliot -- thanks much for this fix--worked great for me (after reconfiguring xorg.conf)

---

### Post by jesterthejedi on 2006-08-23
I darn lifesaver you are! I joined this forum cuase this fix was exactly what  did the trick. Ubuntu needs to stop breaking the perfect OS!

---

### Post by akak8ty on 2006-08-23
> **jonathansizz said:**
> So the foundation of linux is still the CLI? Well, why don't you tell the people who want to switch from Windows this, instead of erroneously claiming Ubuntu as a Windows replacement?

Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.


Hmmm. I am sitting here now using my **[SIZE="2"]windows[/SIZE]** *shell* with an apache server because Ubuntu can't seem to load pages any more tonight.
Every download had an error, and I am not doing anything different than I did last week when it worked perfectly
So I think there is still work to be done.
And for Jesse who said where is the microsoft dos prompt...its in my start panel because I knew where to look and actually use it often.
Could I find dos in Ubuntu? No, not until this morning when I had to manually correct the blunder...exactly as it was emailed to me **_before_** I knew there was a major faux pas.

---

### Post by H.E. Pennypacker on 2006-08-23
Why should the x server breaking be the end of the world?  It just means you can't use X.  Big deal!

Stop attacking the developers, who are, by the way, are great at what they do.  Mistakes do occur with all operating systems.  Let it not be the end of the world, but let's turn our mistakes into solutions.  Let's find solutions to prevent something like this instead of attacking one person or another.

---

### Post by boon on 2006-08-23
> **Myrgen said:**
> I've tried all the fixes suggested. Unfortunately, no joy. I finally tried the apt-get update: no problem. apt-get upgrade: error 404 - Not Found??????? I must add that I get the same 404 when wget -c http:// to any of the links given here.. Any idea?

this is the exact same problem that's happening to me. Whether I use tseliot's 'wget' command or apt-get upgrade, I get a error 404 Not Found message.

---

### Post by unwoken on 2006-08-23
> **jonathansizz said:**
> You've got to be joking. I doubt the thousands of recent converts who just got their machines hosed see this as a 'minor event', and such ridiculous apologetics isn't going to help matters, is it?

I certainly won't be recommending Ubuntu or it's derivatives to anyone I know again. This was the last straw. It's embarrassing when I have just explained to someone how Ubuntu is better coded and more stable than windows for this kind of thing to happen. And the update stayed in the repositories for hours after this problem was known!

thank you 'jonathansizz'.  despite your obviously outstanding empathic qualities, you have attributed the wrong emotion to my post.  I was not joking.  I would have thought the lack of an exclamation mark or smiley may have been the first hint :p .

Judging by your reaction to my post, combined with the tenacity you have shown, even temperament under pressure, and demonstrably powerful problem solving ability, it appears unlikely that anyone you know would listen to any OS recomendation you would make anyway.  I certainly won't take anything you say seriously after your efforts.

Notice I used the word '**I**', in my post.  **I** was describing my own reaction to this issue, as **I** was able to fix this problem, with the help of tseliot and other community members, very quickly.

**I** made the suggestion in my post, that people explain any solutions they offer, in order that the understanding of the group as a whole (especially new members) could be increased in the easiest possible manner.

I am still attempting to find anything useful in what you have written in this thread (aside perhaps from the fact that it looks like you may not be in these forums for long).

---

### Post by spockrock on 2006-08-23
if you upgraded this morning like i did then you should have the fixed version.  no need to downgrade.

---

### Post by akak8ty on 2006-08-23
Human Beings don't want to learn the command line. They want an OS that just works. Stop claiming that Ubuntu can meet their needs.

[COLOR="Red"]**No, I'll learn anything, particularly commands. Hopefully you all will stop yapping soon because you are clogging ubuntu's tenuous server- or do you have another *special* name for it?**[/COLOR]:-x

---

### Post by JasT on 2006-08-23
```
X: cannot read /etc/X11/X symbolic link (Invalid argument), aborting.
```
I had replaced files in /etc/X11/X with files from livecd ubuntu 6.06, and now have such error. Before replacing files were packed in zip.
Help me please!!!

---

### Post by Abiezer on 2006-08-23
> **Epperly said:**
> Was this fixed automatically in a newer update or do I still have to do this?? I don't get what the error is(never saw it)

Just want to echo Epperly's question, as I think I'm in the same boat. Updated yesterday and again with what I presume is the fix today Haven't rebooted yet so not seen a problem. Can I carry on without any other fix?

EDIT: I see that's been answered already. Thanks all.

---

### Post by funchords on 2006-08-23
> **Carbonfish said:**
> I will have to second this question. I ran the update this morning, but my system seems to be running fine. It's a laptop, so I've booted the thing about 10 times since the update and have used most of the apps. that I use day-to-day and haven't run into any problems. 

Should I still run the downgrade? Or did I unwittingly dodge a bullet?

You dodged a bullet.  The bad update was replaced with a working one about 15-16 hours ago.  

The bum update was xserver-xorg-core 1.0.2-0ubuntu10.3.
This was replaced on the server by 1.0.2-0ubuntu10.4.

If you got 1.0.2-0ubuntu10.4, then you don't need to do anything.  

If you got 1.0.2-0ubuntu**10.3**, and haven't rebooted yet, then re-run the update and get 1.0.2-0ubuntu10.4.

---

### Post by textnotspeech on 2006-08-23
I ran the wget command and it worked 

when I tried the dpkg -i ... command it gave this error:

dpkg: error processing xserver-xorg-core*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered during processing:
xserver-xorg-core*.deb

Command line is cool and all but windows are nice.
Please let me know if anyone can help.

---

### Post by Metacarpal on 2006-08-23
I like the way you think, Shookmon

---

### Post by tjfitz on 2006-08-23
TSEliot's instructions worked fine for me.  I checked the forum on Lynx, but mis-typed a wget line on my first attempt, and got a 404 error.  If you are getting a 404, please double-check that you have entered the commands/arguments EXACTLY as posted.

ps: For Pete's sake....if you now hate Ubuntu so much, just quit using it.  Go back to being babysat and spoonfed by MicroShaft if you wish, but don't clog up our support forum with vitriolic, profanity-laden tirades!

---

### Post by paulm on 2006-08-23
It is reasonable for people to be upset.

Were this sort of thing to happen with any frequency it would certainly be cause to think long and hard about continuing to use Ubuntu.

However, so far it has happened (as far as I know) once so it's worth trying to retain a little perspective.

Hopefully at some point when Ubuntu people have had time to analyze what happened we will hear about some (additional) measures they are going to be taking to help prevent similar problems in the future.

---

### Post by funchords on 2006-08-23
> **textnotspeech said:**
> I ran the wget command and it worked 

when I tried the dpkg -i ... command it gave this error:

dpkg: error processing xserver-xorg-core*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered during processing:
xserver-xorg-core*.deb

Command line is cool and all but windows are nice.
Please let me know if anyone can help.

The error means its not finding the file in your current directory.  Did you perhaps change directories between the wget and the dpkg command?

Type cd and press enter, then try the procedure at the top of this thread, again.

---

### Post by paulm on 2006-08-23
> **funchords said:**
> The bum update was replaced with a working one about 15-16 hours ago.
Anyone know how long the mirrors take to update? I am still getting:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)  404 Not Found

when I try to do my upgrade.

---

### Post by spockrock on 2006-08-23
> **textnotspeech said:**
> I ran the wget command and it worked 

when I tried the dpkg -i ... command it gave this error:

dpkg: error processing xserver-xorg-core*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered during processing:
xserver-xorg-core*.deb

Command line is cool and all but windows are nice.
Please let me know if anyone can help.

instead of the star try pressing tab there and see if it auto completes.

---

### Post by Carbonfish on 2006-08-23
> **funchords said:**
> You dodged a bullet.  The bum update was replaced with a working one about 15-16 hours ago.  

The bum update was xserver-xorg-core from 1.0.2-0ubuntu10.3.
This was replaced on the server to 1.0.2-0ubuntu10.4.

If you got 1.0.2-0ubuntu10.4, then you don't need to do anything.  

If you got 1.0.2-0ubuntu**10.3**, and haven't rebooted yet, then re-run the update and get 1.0.2-0ubuntu10.4.

Rob, Thanks for that. Ironic that out of the world Ubuntu community it's another Oregonian that puts my mind at rest.

Where do I find the upgrade log so that I can be sure that I got 10.4? (I know n00b question, but what can I say??:redface: )

Thanks,

Kent
(Milwaukie, OR)

---

### Post by akak8ty on 2006-08-23
I trust Microsoft as far as I could comfortably spit a rat.

Can we have a few beers so I can see just how far that is?
Your quote was funny. It reminds me of my government ](*,)

---

### Post by mrgnash on 2006-08-23
> **Carbonfish said:**
> Rob, Thanks for that. Ironic that out of the world Ubuntu community it's another Oregonian that puts my mind at rest.

Where do I find the upgrade log so that I can be sure that I got 10.4? (I know n00b question, but what can I say??:redface: )

Thanks,

Kent
(Milwaukie, OR)

```
pico /var/log/dpkg.log
```

You might have to scroll down a bit ;)

---

### Post by spockrock on 2006-08-23
> **Carbonfish said:**
> Rob, Thanks for that. Ironic that out of the world Ubuntu community it's another Oregonian that puts my mind at rest.

Where do I find the upgrade log so that I can be sure that I got 10.4? (I know n00b question, but what can I say??:redface: )

Thanks,

Kent
(Milwaukie, OR)

```

apt-cache policy xserver-xorg-core 
```

will tell you the version

or what is suggest above

---

### Post by statictonic on 2006-08-23
This saved me, much thanks!!!

---

### Post by tseliot on 2006-08-23
> **Carbonfish said:**
> Rob, Thanks for that. Ironic that out of the world Ubuntu community it's another Oregonian that puts my mind at rest.

Where do I find the upgrade log so that I can be sure that I got 10.4? (I know n00b question, but what can I say??:redface: )

Thanks,

Kent
(Milwaukie, OR)
Try this:
```
dpkg -s xserver-xorg-core | grep Version
```

---

### Post by tseliot on 2006-08-23
> **textnotspeech said:**
> I ran the wget command and it worked 

when I tried the dpkg -i ... command it gave this error:

dpkg: error processing xserver-xorg-core*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered during processing:
xserver-xorg-core*.deb

Command line is cool and all but windows are nice.
Please let me know if anyone can help.

get to the folder in which you downloaded the files

and post the result of this command:
```
ls *.deb
```

---

### Post by spockrock on 2006-08-23
lol three different ways to do the same thing hahahahhaha.

---

### Post by akak8ty on 2006-08-23
> **Carbonfish said:**
> Rob, Thanks for that. Ironic that out of the world Ubuntu community it's another Oregonian that puts my mind at rest.

Where do I find the upgrade log so that I can be sure that I got 10.4? (I know n00b question, but what can I say??:redface: )

Thanks,

Kent
(Milwaukie, OR)

Don't ever feel ashamed or embarrassed for asking a question when learning something new. The fact that you are learning something new is a beautiful thing, and those that are unkind or intolerant towards those in learning mode need to remember they were once in your/our shoes ;)

---

### Post by smoothridersean on 2006-08-23
> **mrgnash said:**
> ```
pico /var/log/dpkg.log
```

You might have to scroll down a bit ;)

Instead of scrolling, you could use **tail** - which is fantastically useful.  

```
tail -n 5 /var/log/dpkg.log
```
will show you the last 5 lines of that file.  The default is 10, which is how many it shows if you leave off the "-n 5".  There's also this flag:
```
tail -f /var/log/apache2/error.log
```
Which will just follow that file, displaying lines as they are written to it.  As in the example, it's great when you want to "watch" something happening (like buggy PHP code!)

EDIT: Four!

---

### Post by Carbonfish on 2006-08-23
> **spockrock said:**
> lol three different ways to do the same thing hahahahhaha.

Wow! Thanks everybody! I am going to try them all just for fun.
Man, I love this OS *and* this community.

Oh yeah. Rob, nice web page. :biggrin:

EDIT: Well, I guess I did dodge a bullet. I have version 10.4 and had no idea there was any trouble (until 45 mins. ago).

I realize that this is coming from a *bullet-dodger*, and that the broken version shouldn't have gotten out into the repositories, but I think that it is a testament to the dev. community that they got the problem contained as fast as they did.  

Thanks again,

Kent

---

### Post by funchords on 2006-08-23
> **Carbonfish said:**
> Wow! Thanks everybody! I am going to try them all just for fun.
Man, I love this OS *and* this community.

Oh yeah. Rob, nice web page. :biggrin: 

Thanks again,

Kent
I didn't know the answer to your question, so I had to change rooms to find out.  My solution was...

 cat /var/log/dpkg.log | grep "status installed xserver-xorg-core"

... but I noticed that others beat me to it, and I liked the "apt-cache policy xserver-xorg-core" solution better than mine.

Great community!

---

### Post by penguinfan on 2006-08-23
Thanx TSeliot, worked for 1st time

Asus L3H =D>

---

### Post by whatrucrazy on 2006-08-23
> **Craftaz said:**
> yeah.. after installing drivers my gf Ti 4200 became a ATI RV100 :DDDD is it a joke or what???
-----------------------------before----------------------------
Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	60-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"

------------------------------------after-----------------------
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
----------------------------------------------------
did I do something wrong?...


hmmm, me too.

i just checked my xorg.conf and have found the same thing. my graphics card is an nvidia Gforce4 MX420, yet now the config file says:

[I]Section "Device"
    Identifier     "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Monitor        "Generic Monitor"[/I]

i have updated to 10.4, and used the envy script to update my nvidia driver.

what's going on then? is this an issue that should be fixed? how?
a few people have asked this now but no-one has answered yet.

---

### Post by raichuwood on 2006-08-23
Thank you tseliot.

---

### Post by Josh_b on 2006-08-23
This is what I love about Linux and its community. Not even 1 minute searching for an answer (5 minutes after I found I had a problem) from a update that is not even a week old and I already have answer. In windows, that would've taken weeks.

Anyway, thx tseliot, also, do I have to reinstall the nVidia drivers if they're not playing up (screensaver works with no lag and quake3 runs exactly the same, still with no sound though.)

---

### Post by XXFCTEXX on 2006-08-23
> **Dale61 said:**
> I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.

I was going to do the unthinkable as well and just as that shiny disk with the evil EULA lurking inside it almost hit the tray I decided to use my Dapper live disk instead and search the forums for an answer first. :idea: 

Typed in "xserver crash" and voila a whole thread of equally disturbed and disgruntled users and an answer that fixed my machine. :cool:

> **Dale61 said:**
> I pity those who don't have a backup system and are still trying to work out what's happened.


You don't need a spare machine, just pop in your Dapper disk and use it live.

---

### Post by TFX360 on 2006-08-23
> **anasofiapaixao said:**
> **THIS** is a decent and fair way of venting your frustrations:




THIS is NOT.



Mentioning names is not what matters. Mistakes HAPPEN and we are ALL subject to them, at least while computers don't take over the world :D. 

It is important for people to realize this is NOT costumer service, ***_THIS IS A COMMUNITY_***. All one can get with this kind of behavior is a (well-deserved) answer of the kind "well go get a refund". And one should know this is NOT a common situation and is being solved quite quickly. Also, sure we all can vent but providing we do it in a decent way. No one needs people trashing down the Ubuntu's staff hard work! Sorry for the harshness, but come on...

Back on topic: Seriously, This morning when I turned on my computer I thought: let's go check the xorg file... Checked the debugging info, checked that everything was correct. What I thought? I didn't do anything... wait... I upgraded the X server. Then I thought to myself: I am feeling SO lazy today, I'll just wait until the end of the day and check what was the answer to all the people who complained about the bug (even tought a little afraid that the problem could be only mine). Luckily I haven't upgraded my mum's computer, so here I am.

P.S. - No I have nothing to do with Ubuntu's staff; just your average forum user:P.


Couldn't agree more!

Hail!

Portugal? I'm having my vacantion there in two weeks!


Kind regards,


TFX

---

### Post by frenzie on 2006-08-23
> **The Pinny Parlour said:**
> 1.  Failed to start xserver .....

2.  Couldn't open RGB-RD  /usr/share/X11/rgb    then a heap of other gibber.

3.  Would you like to view the detailed xserver output as well?

4.  more gibber

5.  The Xserver is now disabled.  Restart GDM when it is properly configured.

6.  Then it goes to CLI login

7.  User of this ubuntu PC REALLY PISSED OFF](*,) ](*,)


This sounds pretty similar to what i was getting, booted up again and "no devices detected".

At first i found another forum and installed this:
[http://www.linux2go.dk/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu8linux2go1_i386.deb](http://www.linux2go.dk/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu8linux2go1_i386.deb)
using dpkg -i and rebooted and X started up fine. 

I then saw the forums and the fact that the update breaks X and did:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

The first step of installing from linux2go may be unnecessary, but though i'd include all the steps i did and got it to work fine.

---

### Post by dgrafix on 2006-08-23
Grrr!

---

### Post by boon on 2006-08-23
> **boon said:**
> this is the exact same problem that's happening to me. Whether I use tseliot's 'wget' command or apt-get upgrade, I get a error 404 Not Found message.

ok i fixed the problem but it took more time reading the forums and trying different things than i might care to admit.

This strikes me as a major ubuntu problem. If you upgrade your system as per the official notifications and it breaks like this a large number of people could be stuck without knowing what to do. Usually the upgrade system works wonderfully well - a great feature of ubuntu.

For me it was good practice with the command line and I re-learned a useful lesson: in ubuntu the command line is your friend, use it as often as possible, learn a new command or technique every day.

Luckily I had earlier gotten used to using the command 'pon' to dialup my internet connection and was familiar with lynx also, so as an emergency I was able to dialup and surf the web from the command line.

Firstly, i tried to follow tseliot's advice, ie:

wget -c [http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/server-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/server-xorg-core_1.0.2-0ubuntu10.4_i386.deb)

This produced a '404 Error not found' message. Now that's a html message isnt it? Server overloaded?

Failure here meant I did not have any idea what was wrong and so had to keep reading. Eventually I figured out what the basic problem was: the upgrade of xorg-server to version 10.3 broke the x server. The solution is to either upgrade to the fix (version 10.4) or downgrade to an older version.

I must say all the advice and comments on the forums is a little confusing. I tried a number of different commands without success, including:

sudo dpkg -i xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
sudo apt-get install xserver-xorg-core_1.0.2ubuntu10.1.i386.deb

Doing things like this i began to get 'file not found' and 'directory not found' messages. (I suppose you can tell i didnt really know what i was doing.)

I also read in the forum that the fix (10.4) had been uploaded to the official servers so all you had to do was an update and upgrade using apt-get on the command line, ie:

sudo apt-get update

This worked fine and i was informed there was one upgrade available, xserver-xorg-core! Now we seemed to be getting somewhere.

But then I ran:

sudo apt-get upgrade

and it gave me an error message. Failed to fetch... 404 not found.

Finally I decided to go into the /var/cache directories and identify the old file by sight. I spotted a 10.3 version and a 10.1 version but curiously no 10.2 version.

Anyway I ran the following command:

sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb

This succeeded in downgrading the package from version 10.3 to 10.1 and the problem was solved.

And I can now see via both software updates and apt-get upgrade that the new package (10.4) is ready to download, although it is still giving me 404 not found messages. Perhaps the patch hasnt reached my local servers yet?

I think i will take my own advice and become friendly now with apt-get....

---

### Post by nocturn on 2006-08-23
> **Dale61 said:**
> G'day, another recent Ubuntu convert.


I agree, what happened is horrible and it shows a big problem with the quality testing of the Ubuntu updates.  I hope these events will prompt a change in those procedures, because Dapper Drake is by far the best distro I've ever used.

---

### Post by imihai on 2006-08-23
i had the same problem! yesterday morning! i have updated the system, shutdown the pc and in the evening when i came home my ubuntu was going into console.No p[roblem, I love it!
what I did was to connect to internet, 
sudo apt-get update, 
sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg
sudo startx
all done!

---

### Post by dgrafix on 2006-08-23
You cant win...

Windows=Dreaded spyware
Ubuntu=Dreaded updates 

Slice of apple macos anyone :P

What with this and my wireless fiasco the other day, windows is starting to look like home.

I Had some important work to do this morning...
NOT HAPPY AT ALL!

---

### Post by givré on 2006-08-23
> **imihai said:**
> 
sudo dpkg-reconfigure xserver-xorg

You shouldn't really need this one. Was it necessary ?

---

### Post by daou on 2006-08-23
Ok I finally got around to updating the xserver core after being too lazy to do it. And yes I got the problem too but fixed it according to the directions given in the first post.

A few questions. Why was the xserver-core still up on my updates list even 24 hours after the problem had been detected? Would the update not have been there anymore if I had just done an apt-get update?

If so, maybe from now on I'll wait a week before applying a patch, and refresh the list to see if the update is still there to avoid anything similar.

---

### Post by etotehpii on 2006-08-23
Can someone go over how to install the new files from a cd?
I think I have mounted the cd with:

```
sudo mount /media/cdrom0
```

Then I check to see my files:
```

ls /media/cdrom0
xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-dev_1.0.2-0ubuntu10.4_i386.deb
```

Then I try and install one of the files:

```
sudo apt-get install /media/cdrom0/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
Reading package lists...Done
Building dependency tree...Done
E: Couldn't find package
```

I have both the files burned on a cd and they arnt in any folder on the cd.  Thanks.  I can't get my wired or wireless internet to work in console as I'm a linux noob.

---

### Post by givré on 2006-08-23
you'll have to install them with ```
sudo dpkg -i
```
but now a 
```
sudo apt-get update
sudo apt-get upgrade
```
should be enough

---

### Post by Llywelyn on 2006-08-23
I'm no expert and correct me if I'm wrong, but...

sudo apt-get update
sudo apt-get upgrade
sudo reboot

should also work, (as it did for me). Just let Xserver fail than get to the command line, log in with your usual name and password then type in the above commands at the $ prompt, followed by reboot.

---

### Post by adam_kimber on 2006-08-23
All local packages can be installed using dpkg with the i option for install. So dpkg -i somepackage.deb will install somepackage. 

Has the patched version now reached the repository?

---

### Post by wip3out on 2006-08-23
> **tseliot said:**
> Please, restrain yourself from using swear words in this forum.

BTW without the Xserver we would be stuck to the command line

I don't understand why people have to use such languauge... some what immature hey;)
I'm glad we're not stuck with the cmd line.. would be pretty boring.

Thanks for the fix :p

---

### Post by etotehpii on 2006-08-23
Thank you very much that did the trick!
The core part installed fine and the dev part was unsuccessful because something wasnt there.  Long string of this works but we need this etc etc...
However, I rebooted and I was able to use my desktop.
I did the update and upgrade commands you suggested and rebooted.  
Things seem to be functional now. 
I've learned my lesson, I will wait a few days before letting something be updated on my linux partion.

Thanks again.

---

### Post by the_thunderbird on 2006-08-23
It's stuff like this that brings linux as a whole down. Esp the likes of Ubuntu. I've just got my dad swearing by ubuntu and this happens... Sods law I guess... Maybe I should go back to gentoo.

Doesn't anyone actually do testing when releasing a package?

Obviously not!

---

### Post by ndee703 on 2006-08-23
Thanks a lot tseliot!
Just got terribly frustrated after getting the updates yesterday and rebooting today :-)

Isn't there any chance to avoid such struggle by having a better quality assurance BEFORE releasing such updates?

If we want more people to become Linux/Ubuntu users, such things should not happen at all.

Who are the guys in charge for the xserver?

BTW: Just installing your files on my compaq nx8220 with the existing fglrx driver worked !

Greetings
Ndee

---

### Post by philipbakerclarke on 2006-08-23
Panic over Mine is sorted
I enjoy using ubuntu and I like the real kind of support like I get in these forums
Many thanks



p.s Anyone can make a mistake once, only microsoft can make them twice and three times and then again

---

### Post by Agio on 2006-08-23
Thank you **tseliot** for your help, easy and painless. It's the comunity what makes this distro so good.

Agio

---

### Post by Andrew1234 on 2006-08-23
Thank you for the fix, 

Since the xserver update I am finding the mouse freezes when in Firefox, is anyone else having this problem?? if so is there a fix!

---

### Post by Robert Leithe on 2006-08-23
I'm still in the dark - so to speak. I'm one of those "first time offenders", that is I'm completely new to Linux and my initial install of Ubuntu is about one week old .

My problems is as this thread explains. But I cannot seem to get the suggestions to work properly.

I have tried these suggested solutions:

1) wget -c /../xserver-xorg-core-1.0.2-0ubuntu10-4_i386.deb (I shortened that one) and the same for the "dev file".

Both downloads went just fine. But when I ran the
**sudo dpkg -i xserver-xorg-core*.deb**
I get this error:
[B]dpkg: error processing xserver-xorg-core*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xserver-xorg-core*.deb[/B]

2) I also tried the solution mentioned later in the thread, about downgrading without an internet connection

sudo dpkg -i **/var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb**

but got the same error as above (just another filename)

3) I also tried the CD-ROM approach

mounted my CDROM and tried this command:
**sudo dpkg -i /media/cdrom0/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb**

...and I get the same error (I did an ls on the CDROM and under **/media/cdrom0/pool/main** I have no directory named **x**.

Any suggestions as to what I can try next?

Sincerely
Robert Leithe

---

### Post by justinflavin on 2006-08-23
from my update manager:

Version 1:1.0.2-0ubuntu10.4: 

  * Reverted patch 005_pci_domain.dpatch -> breaks PCI setup for many users.
    This patch will need further work before it is reintegrated into
    xorg-server again.


this is as bad as the XOrg hardlock for certain ATI graphics cards (if you have a fresh Dapper install + updates).

is there enough testing being done?  is that the problem?
does Ubuntu need more volunteers for testing beta versions?

---

### Post by aiu on 2006-08-23
Thanks very much Tseliot!

:D

---

### Post by justinflavin on 2006-08-23
> **Robert Leithe said:**
> I'm still in the dark - so to speak. I'm one of those "first time offenders", that is I'm completely new to Linux and my initial install of Ubuntu is about one week old .

My problems is as this thread explains. But I cannot seem to get the suggestions to work properly.

I have tried these suggested solutions:

1) wget -c /../xserver-xorg-core-1.0.2-0ubuntu10-4_i386.deb (I shortened that one) and the same for the "dev file".

Both downloads went just fine. But when I ran the
**sudo dpkg -i xserver-xorg-core*.deb**
I get this error:
[B]dpkg: error processing xserver-xorg-core*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xserver-xorg-core*.deb[/B]


are you sure you are in the same directory as the deb file?

have you tried using the full name:

sudo dpkg -i xserver-xorg-core-1.0.2-0ubuntu10-4_i386.deb

---

### Post by johnnie69 on 2006-08-23
Really cool!
The fix worked, everything is ok!

People stop bitchin' Bad things DO happen (Murphys Law) and the point is what we can do to repair the damage!

In this case the Ubuntu community has shown a very fast reaction time! Thumbs up!

Special thanks to tseliot!

And again, be cool and for those of you who cannot ...stop bitchin'

---

### Post by johnnie69 on 2006-08-23
Please read carefully the repair instructions

you must have mispelled something

I think it is ...ubuntu10.4_.....

and NOT  .....ubuntu10-4_.........

---

### Post by true_friend on 2006-08-23
is it all ok for Kubuntu??
or it has also the same problems?

---

### Post by munckfish on 2006-08-23
After the events of this last week I'm disabling the XGL repos (so I can keep my fonts) and I'm not applying any updates for at least a day after (so I don't have to scratch around on the terminal trying to guess whats broken) and before I do I'm going to scour the forums for issues.

I think this is a big big shame cause there will be a lot of non-tech converts lost after this, and I'm just not as confident to pass on those 5 CDs I had sent to me. Really sad about this cause I believe Ubuntu is a seriously good operating system.

---

### Post by Robert Leithe on 2006-08-23
> **justinflavin said:**
> are you sure you are in the same directory as the deb file?

have you tried using the full name:

sudo dpkg -i xserver-xorg-core-1.0.2-0ubuntu10-4_i386.deb

That's maybe just it - where did the file go? I did the download, watched the progress go to 100 %, no errors displayed. I didn't change directory before I tried to apply the download. But the download does not show when I do an **ls**... To which directory must I go before applying the downloaded file?

I did try the full filename, as you suggest, but receive the same error.

Robert

---

### Post by SteveHoffmanUK on 2006-08-23
I have checked and rechecked my typing of the first line of the original fix and get
```
HTTP request sent, awaiting response.... 404 Not Found
09:33:56 ERROR 404: Not Found
```

Tried this several times. Any suggestions?
Thanks

---

### Post by petri on 2006-08-23
> That's maybe just it - where did the file go? I did the download, watched the progress go to 100 %, no errors displayed. I didn't change directory before I tried to apply the download. But the download does not show when I do an ls... To which directory must I go before applying the downloaded file?

I did try the full filename, as you suggest, but receive the same error.

Robert



> I have checked and rechecked my typing of the first line of the original fix and get
Code:

```
HTTP request sent, awaiting response.... 404 Not Found 09:33:56 ERROR 404: Not Found
```


Tried this several times. Any suggestions?
Thanks

You can fix this easily by using the automatic updater, there is a new xorg in repositories called 10.4 and it works for me with ATI 8500 which isn't the best choice in Linux. You can use Synaptic too -- "Mark all updates"

---

### Post by tseliot on 2006-08-23
> **SteveHoffmanUK said:**
> I have checked and rechecked my typing of the first line of the original fix and get
```
HTTP request sent, awaiting response.... 404 Not Found
09:33:56 ERROR 404: Not Found
```

Tried this several times. Any suggestions?
Thanks

The server might be down.

Try with:
```
sudo aptitude update
```

```
sudo aptitude install -s -V  xserver-xorg-core
```

and see which version the system would install (it's just a simulation)

if it's version 10.4 then you can install it:
```
sudo aptitude dist-upgrade
```

---

### Post by Zay on 2006-08-23
> **Kilz said:**
> ](*,)  I was working on getting the new ATI drivers working. I bashed my head into a wall for a few hours thinking it was something I did. ](*,) 
Thanks for saving me more pain

I had the same problem. Lost 3 hours on it before reading it was a bug in the xorg-core though :(

---

### Post by Eleka on 2006-08-23
I upgraded the xserver-xorg-core package from the respository and now my XSession starts, but my restricted driver Nvidia dont't works.

I followed the instructions and re-installed it from zero, but in glxinfo I saw that I have OpenGL activated with Nvidia driver but not direct rendering ... when I test my FPSs with glxgears I only obtain 3000, and before aall that I had around 8000 ....

What I am doing wrong?

---

### Post by tseliot on 2006-08-23
> **Eleka said:**
> I upgraded the xserver-xorg-core package from the respository and now my XSession starts, but my restricted driver Nvidia dont't works.

I followed the instructions and re-installed it from zero, but in glxinfo I saw that I have OpenGL activated with Nvidia driver but not direct rendering ... when I test my FPSs with glxgears I only obtain 3000, and before aall that I had around 8000 ....

What I am doing wrong?
Try this if you installed the driver from the repositories:
```

sudo aptitude reinstall nvidia-glx linux-restricted-modules-`uname -r`
```

then restart the xserver

---

### Post by philipbakerclarke on 2006-08-23
If we can look at this positively.

How can ubuntu be set up so that, should this happen again. We can update/revert back or whatever so that ubuntu is up and running again with the least amount of distress for the user. 
Without having to log into my windows partition to read the forum.

A backdoor into the repo's. A command that could be entered that checks against an information server.

The ability to restore the problematic updated files from the ubuntu install cd.

---

### Post by SteveHoffmanUK on 2006-08-23
> **tseliot said:**
> The server might be down.

Try with:
```
sudo aptitude update
```

```
sudo aptitude install -s -V  xserver-xorg-core
```

and see which version the system would install (it's just a simulation)

if it's version 10.4 then you can install it:
```
sudo aptitude dist-upgrade
```

Tseliot: Brilliant! It worked. This is much easier than all that typing of the original code (I appreciate that you had to recommend that when the faulty version was still current). Many thanks for your help. Like many others I am seriously angry but not here. :D

---

### Post by Robert Leithe on 2006-08-23
> **Robert Leithe said:**
> That's maybe just it - where did the file go? I did the download, watched the progress go to 100 %, no errors displayed. I didn't change directory before I tried to apply the download. But the download does not show when I do an **ls**... To which directory must I go before applying the downloaded file?

I did try the full filename, as you suggest, but receive the same error.

Robert

An update: I tried downloading the packages again (as initially explained in this thread) because I wanted to se if I could figure out where those packages were stored. They were both stored in the current directory (as I would expect), but this time I saw then when running the ls command, and the install (downgrade) went flawlessly(!).
So, in writing this I'm back on my wonderful Ubuntubox, everything's ok. But this one still puzzles me... Well, not to worry :)

Regarding all the unhappy users here today - I can't speak for any of them, only for myself. And I want to say that my resolve to switch to Linux is only strenghtened by this experience. Seeing as how so many devoted users around the world keep an eye on the forums in times like this, waiting to help beginners and others to solve the problem... That's simply beautiful! Thank you :)

Sincerely
Robert Leithe

---

### Post by tomBorgia on 2006-08-23
Generally "rolling back" - Go to synaptic's history and work out which update broke your system. Go to /var/cache/apt/archives and grep for the package (in this case I did this for the xserver-xorg .deb file) - you should find several versions of each package - 

tom@tom-ubuntu-desktop:/var/cache/apt/archives$ ls | grep xorg
xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.3_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-input-mouse_1%3a1.0.3.1+cvs.20060109-0ubuntu1.1_i386.deb

As the 10.4 xserver update managed to break my nvidia support I then used dpkg --install xserver-xorg-core_1%3a1.0.2-0ubuntu10.1
it informed me I was downgrading but then everything seemed to work after a reboot... so this method may work if there are any similar problems in the future... think I'm gonna wait for 10.5 ;-)
Tom.

---

### Post by royale on 2006-08-23
Thank you and there should be a link to this thread on the main Ubuntu home pages.

---

### Post by 3rdalbum on 2006-08-23
I found it interesting that version ubuntu10.4 is not actually a fix for the bug in ubuntu10.3 - it is just ubuntu10.2 with a higher version number.

---

### Post by royale on 2006-08-23
> **3rdalbum said:**
> I found it interesting that version ubuntu10.4 is not actually a fix for the bug in ubuntu10.3 - it is just ubuntu10.2 with a higher version number.

As long as you're running the latest version, everything should be fine.  lol  ;) 


> How can ubuntu be set up so that, should this happen again. We can update/revert back or whatever so that ubuntu is up and running again with the least amount of distress for the user.
Without having to log into my windows partition to read the forum.

I was able to boot from the cd and check the forums.

---

### Post by angrykeyboarder on 2006-08-23
> **funchords said:**
> And why is it still live?

Why? Cuz s*** happens. :-)

---

### Post by givré on 2006-08-23
> **3rdalbum said:**
> I found it interesting that version ubuntu10.4 is not actually a fix for the bug in ubuntu10.3 - it is just ubuntu10.2 with a higher version number.
You are wrong. ubuntu10.3 contains 3 patch and only one was wrong. The 2 other are still there.

---

### Post by angrykeyboarder on 2006-08-23
I'm not sure what I did wrong, but here's what happened to me and how I got it fixed.

1) I had the same experience as others with the update breaking X-Window.

2) I tried "sudo dpkg-reconfigure xserver-xorg" a few times to no avail.

3).  I then restarted my computer and logged in to Windows (omigod!), and checked out the Ubuntu Users mailing list to see what was up.

4). I then figured out what to do.  I [downgraded]("https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091447.html") to the previous version.

5). I then rebooted and all was right with the world.

6) About 14 hours later (when I was reasonably sure the update had made it to my mirror) I opened a terminal and entered "sudo apt-get upgrade -s".  I saw that the package was to be upgraded and noted it was now a new version.

7) I then did "sudo-apt get-upgrade".

8) I rebooted

9) all was well.

Note when I rebooted the last time I got the NVIDIA splash screen and my 3d stuff works like it's supposed to.  Therefore I didn't have to do anything as far as reconfiguring or re-installing NVIDIA Drivers.  I'm not sure why anyone else did, but I thought I'd point that out.

I'm not sure how this mess got through in the first place.  Very poor QC I'd say.  But I will say the response and fix was **very** prompt. :-)

---

### Post by mustekala on 2006-08-23
This might work:

sudo dpkg-reconfigure xserver-xorg

---

### Post by Perfect Storm on 2006-08-23
> **johnnie69 said:**
> Really cool!
The fix worked, everything is ok!

People stop bitchin' Bad things DO happen (Murphys Law) and the point is what we can do to repair the damage!

In this case the Ubuntu community has shown a very fast reaction time! Thumbs up!

Special thanks to tseliot!

And again, be cool and for those of you who cannot ...stop bitchin'

Right on!

---

### Post by gnarula on 2006-08-23
i am getting the following error:

```
root@ubuntu-desktop:/home/ubuntu# sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  xserver-xorg-core
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3531kB of archives. After unpacking 4096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err http://au.archive.ubuntu.com dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4
  404 Not Found
```

---

### Post by Jaxilian on 2006-08-23
When was this first discovered? Please write date/time with timezone.

---

### Post by Perfect Storm on 2006-08-23
I don't have the exact time/date etc. but I think somewhere yesterday.

---

### Post by mustekala on 2006-08-23
> **JeremyWorst said:**
> I can't connect my laptop to the Internet here (I'm using my desktop right now) and would like to try the manual install, but need a little help.  I've copied the files to my flash drive, but don't know where to find the flash drive using the command line.  An icon usually appears on my Desktop, but of course no Desktop is available (yet).  I thought I'd find it in /media, but it isn't there.  Assuming somebody can tell where it is, then what commands do I run on the two files?

Thanks! - Jeremy

This was exactly the same problem I had with my wife's laptop. I copied the updated deb to my flash drive, rebooted her laptop then typed the following commands:

$ cd /mnt
$ sudo mkdir xyz
$ sudo mount /dev/sda1 xyz
$ sudo dpkg -i xyz/xserver-xxx.deb

---

### Post by mebrooker on 2006-08-23
I've tried all of the suggested fixes, but none worked for me. 
I seemed to be able to install 10.4 OK, but to no avail.

I tried downgrading too. In the end, I've just reinstalled, and I'm holding back the upgrades to xorg core until I'm sure they'll be OK for my ATI card.

I'm using the xorg-driver-fglrx that comes with dapper, rather than the later one you can get from ATI.

I'm using an ATI Radeon 9200 Pro card, with AMD Athlon 64, but running 32bit Ubuntu dapper. 

As for all the grumbles, we should understand that Ubuntu is a bit of bleeding edge distro, so we can expect the odd bit of trouble, now and again. If we desire stability, there's always Debian Sarge. 

Ubuntu is the best Linux distribution, so credit to everyone who's on the project for doing such a great job!

---

### Post by mustekala on 2006-08-23
> **The Pinny Parlour said:**
> ANYONE...Got ANY ideas on what i can edit to get xserver-xorg up and running???

This might work:

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by jrjr on 2006-08-23
.

---

### Post by The Pinny Parlour on 2006-08-23
> **frenzie said:**
> This sounds pretty similar to what i was getting, booted up again and "no devices detected".

At first i found another forum and installed this:
[http://www.linux2go.dk/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu8linux2go1_i386.deb](http://www.linux2go.dk/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu8linux2go1_i386.deb)
using dpkg -i and rebooted and X started up fine. 

I then saw the forums and the fact that the update breaks X and did:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

The first step of installing from linux2go may be unnecessary, but though i'd include all the steps i did and got it to work fine.

I was VERY heated and acrimonious in my initial posts.  I am not appolgising for my behaviour, as this was how I felt, but I will applogies to any individuals who interpreted what I said as a personal attack.  I was annoyed greatly at X itself and that it went live, and really, my lack of knowledge on how to fix it.  
I have since corrected my ubuntu issues/problems with an 8 hour, crash course in CLI and nano.  I got some aquired answers that I received in the last few months of using ubuntu from these forums, and just went nuts on nano'ing xorg.conf.  I have learnt alot, both in what I have read in this thread and also in others opinions on everything discussed here.  I has been a great experience for me to learn and read everyones views.  For this I do thank you all. Truly great this community is.   

I have not 100%, totally fix my ubuntu yet, but I'm closer than ever.

---

### Post by Casey on 2006-08-23
> **jrjr said:**
> Ok I just checked for updates and there are 3 for me

libkrb53
libmagik9
xserver-xorg-core 1:1.0.2-0ubuntu10.3

Why didnt I get these automatically? I never turn my machine off
Should I install them or not?????

This one:

xserver-xorg-core 1:1.0.2-0ubuntu10.3

you really don't want.

Don't upgrade it until it says
xserver-xorg-core 1:1.0.2-0ubuntu10.4
or higher

---

### Post by Kabatwa on 2006-08-23
I just want to thank tseliot! Read your message before I rebooted and everything went smoothly. 
To *The Pinny Parlour* yeah it was pretty pants what happened and a big mistake but that's what it was, a mistake. You're using free, open source software and Ununtu and the like is still pretty young so bad things are bound to happen. In fact if things like this didn't happen I'd be worried because that'd mean there's no development going on!
Anyway I hope everyone gets their systems sorted soon and thank you to everyone who looked for a fix to this problem =D>

---

### Post by jrjr on 2006-08-23
.

---

### Post by RRS on 2006-08-23
First off, a proper thankyou to tseliot and all the others who so quickly responded with solutions and support.

For future reference as a possible work around for similar problems? Would this upgrade have affected all installed kernels? 

I always keep the last working kernal in grub, would booting to it have given me a working gui? Since solutions had already been posted I never thought to try.

Thanks again to all who helped.

---

### Post by Gyrotwister on 2006-08-23
> I always keep the last working kernal in grub, would booting to it have given me a working gui? Since solutions had already been posted I never thought to try.

Tried that, it didn't work for me.

---

### Post by Senshi on 2006-08-23
I would like to say thanks to everyone who helped to provide information on the fix.  

Took me forever to at least downgrade.  I had no internet connection, my cache is empty and I couldn't get it off the disc.  Only because I used the command someone posted and on my Ubuntu DVD the file has a different name.  But it's no big deal.  All that is left for me is to upgrade.

It's also amazing how many people are quick to create a new post on their problems instead of reading the sticky.  It tends to bombard the forums with the same thing.  Oh well.

Thanks alot guys for everything.  :D

---

### Post by rovernaut on 2006-08-23
I've tried all the solutions and can only get the 404 error.
Are the servers down????

---

### Post by tseliot on 2006-08-23
I have updated this "guide" (or whatever it is)

---

### Post by digitalgecko on 2006-08-23
BOON'S suggestion worked for me. Have you tried it?



"Finally I decided to go into the /var/cache directories and identify the old file by sight. I spotted a 10.3 version and a 10.1 version but curiously no 10.2 version.

Anyway I ran the following command:

sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb

This succeeded in downgrading the package from version 10.3 to 10.1 and the problem was solved.

And I can now see via both software updates and apt-get upgrade that the new package (10.4) is ready to download, although it is still giving me 404 not found messages. Perhaps the patch hasnt reached my local servers yet?

I think i will take my own advice and become friendly now with apt-get....":D

---

### Post by sda5150 on 2006-08-23
Hadn't read this page before upgrading and got caught out :twisted: 

Tried to fix it by running dpkg-reconfigure xserver-xorg and made a mess of it.

Read this thread and was able to fix it by rolling back to xserver-xorg-core=1:1.0.2-0ubuntu10

Rolled back to previous version of my xorg.conf

After rebooting all was fixed and could update to 10.4

---

### Post by Senshi on 2006-08-23
> **rovernaut said:**
> I've tried all the solutions and can only get the 404 error.
Are the servers down????

You are going to have to do it manually.  [Check page 4 for 2 of the solutions to do it manually.]("http://www.ubuntuforums.org/showthread.php?t=241254&page=4")

---

### Post by jrjr on 2006-08-23
.

---

### Post by linebp on 2006-08-23
I was just about to panick when my xserver wouldnt start this morning, I am not really into all that xserver setup stuff, but then I found this post and followed the instructions and all was fine and working again :) Thanks for the guide and the quick fixing of the problem :)

Sorry for the unnecessary spamming in this really long thread.

---

### Post by Senshi on 2006-08-23
> **jrjr said:**
> I have not done any updates in a while

The output of 
```
sudo aptitude show  xserver-xorg-core | grep Version
```

Is this
```
Version: 1:1.0.2-0ubuntu10.4
```

When I check System/Admininstration/Update Manager  there are 3 updates
10.4 is one of them

Why?
Why isn't my auto update check working? It always has in the past.

Did you try rebooting?

---

### Post by jrjr on 2006-08-23
.

---

### Post by Turin Turambar on 2006-08-23
I downloaded xserver 10.4 version from WindowsXP and then in linux just instaled it with dpkg. Rebooted and now it's working.

But honestly, I think that Ubuntu needs some sort of graphical (X window) safe mode. At least by putting the Ubuntu CD.
It's too bad that when just something small happens to the X, you must face a command prompt - no alternatives. I can't even imagine new users going there and fixing something from it.

---

### Post by pannerrammer on 2006-08-23
Thanks. Instructions worked as given. My wife has forgiven me! :D

---

### Post by themainliner on 2006-08-23
Bashes head against desk... ](*,) ...again...

I just knew when I saw the xserver updates appear last night that I'd have trouble today.

Well, I also knew that Alberto would have the answer!  I was right, one problem mate...how do you deactivate and reactive eth0 from the  CLI to get a network connection?  I have a thread in networking about my 'small' startup networking problem.  It's now a BIG network problem, especially as I am reduced to post to this forum from WINDOZE ecspee...urrrggghhh, filth! :grin: 

Seriously, how do I get a network connection?

[http://www.ubuntuforums.org/showthread.php?t=240799](http://www.ubuntuforums.org/showthread.php?t=240799)

---

### Post by pashby on 2006-08-23
Thanks for the fix.

I was REALLY lucky that I was using my XP partition at work and didn't boot into Ubuntu until late. If I had I would have gone and reloaded Ubuntu again by the time the fix came upon the forum.

You can be lucky sometimes.

Peter :) :) :)

---

### Post by paulchen on 2006-08-23
Hello World.
Guess what, I just had given up on Gentoo because of serious manual malfunctions and my own inadequate skills, dug up the old hoary hedgehog slumbering away in my emergency box, used this to download the dapper drake, install - everything fine - update - BANG. 
Reinstalled the whole thing after walking up some walls and feeling very much like pinny parlour (maximum respect to tseliot for keeping his cool the way he did). 
Now I get to the point of this whole post (besides asking for your prayers on my next reboot) - I would still be looking for the answers if the most recent post hadn´t been exactly to my problem.
One possible solution would be to increase my understanding of computers and the way they work inside those humming, blinking, wiresprouting boxes (and I try).
Until this effort has borne fruit and for the next generations of newbies would it be possible to do a Header somewhat like "You are innocent... This time." and inside just links to threads like this and nothing else.
This idea is based on me always going "What did I do NOW?" when something unexpected happens on my desktop.
Maybe someone has already tried that and it got too cluttered too fast, maybe the idea needs some modification until it is workable.

Happy penguining

Paul

---

### Post by Abilnet on 2006-08-23
Thanks guys for your hard work by providing the fix and instructions, appreciated! :grin: 

All the best, keep up the Great Work! ;)

---

### Post by oliverb on 2006-08-23
> **tseliot said:**
> :
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```


Hey thanks for the solution. I guess I'm lucky I haven't customised anything so the downgrade went smoothly. The update tool found 10.4 immediately so I updated to that and it seems OK.

I wonder is there a way to fix a broken system from a livecd boot to avoid command line stuff?, say by running synaptic package manager or similar on the installed copy while running off the CD?

---

### Post by wild77 on 2006-08-23
Thanks for the fix! I am fairly new to Ubuntu and still learning how to work with the command line part of it. I was a little freaked out when I re-started my machine yesterday and found the scrambled screen and error message. Thanks to the info here I was able to update the xserver (after a few tries) and bring Ubuntu back to life. Thanks again for the help!

---

### Post by mjezell on 2006-08-23
Thanks for the timely and very helpful post to this problem.  Some people need to sit back and take a breathe and realize that there is no perfect code in the world.  All you can ask is for the community to do it's very best and I know that this is the case with Ubuntu.  Your detication is much appreciated.

---

### Post by hellfried on 2006-08-23
deleted

---

### Post by jaywatkins on 2006-08-23
Back online...

Here is what I did to get around Firewalker.

sudo apt-get remove firewalker
Y
ping <default gateway>  */Tests local connection
apt-get update
apt-get upgrade
Y
restartx

Thanks for the quick update tseliot.  I am still waiting for the patches from Microsoft for their office vulnerability last week.  It is amazing on how everyone was just throwing Ubuntu under the bus because of this little hiccup.  IT IS LINUX PEOPLE, it is meant to be tweaked.  Plus it is free!  A free operating system that is better than Windows, now that is something.

Great job Ubuntu guys, thanks!

---

### Post by phibuntu on 2006-08-23
Hi

Thanks *tseliot*. You saved the live of a computer of a friend of mine who uses after my advice **ubuntu** (for e-mails and playing **go**) and otherwise has not much experience in computing. :D

And linke jaywatkins I say: "[COLOR="Lime"]Einem geschenkten Gaul schaut man nicht ins Maul![/COLOR]" (German proverb)

---

### Post by IndyBart on 2006-08-23
I am a very new Ubuntu user and new to Linux as well. As much as this was an issue, it served as a good learning experience - correcting problems seem to help with learning more than anything. Thank you for the quick response with 10.4 which fixed my system straight away. One interesting observation that I would appreciate any comment on (I'm sorry if this is crossing over forums).
My installation and set up has run perfectly except I have never been able to get audio to play with Flash. I've tried all of the suggestions I could find in this community to no avail. Interestly, after I upgraded to 10.3 and BEFORE I rebooted, the audio played on Flash!!! Now that I've corrected the xserver issue with the 10.4 upgrade I once again have no Flash audio. Does this help diagnose my Flash problem?

---

### Post by tseliot on 2006-08-23
[COLOR="Red"]**I have added a method to solve the problem offline from Ubuntu's Alternate installer**[/COLOR]

---

### Post by raldz on 2006-08-23
Why is everybody cursing? When I encounter this problem, I did not bother to look at the forums.. the last thing I did was upgrade, and it broke the system, so the most logical solution at that instant is to downgrade.. since I know how to downgrade, it just took me less than 10 minutes to fix it... and in case I don't know how to downgrade, I would ask here at the forums.. now my system is updated to the 10.4 xorg core version.. 

So guys, next time, be kind enough to ask first before cursing.. I know how you feel... I was like that before everytime MS Windows flashes its Blue Screen of Death.. and I have no one to ask help to at that time.. and now I'm happy using Linux (MEPIS, Ubuntu, Fedora, SUSE, PCLinuxOS).. because the community support is great! =D> =D> =D> =D>

---

### Post by imhdd on 2006-08-23
tseliot: I was shocked when I tried to boot into Ubuntu Dapper this morning and got the warning that xserver wasn't working. Thank you for the quick fix.It works. imhdd.

---

### Post by mycelo on 2006-08-23
Ok, I've read this whole thread and things still aren't clear for me. Please edit the very first post with even more clarified instructions.

I understand that the xorg upgrade is now fixed, the download that's showing up for me reads 10.4 at the end of that bizarre version string.

Yesterday I successfully downgraded my xorg-core after reading some of the several threads that spawned here minutes after the flawed upgrade became available.

But the first post says that I need, for some reason, reinstall my "nv" drivers, but it's not clear if I still need to do this since I'm getting the fixed upgrade. I mean, it is fixed now, right? If this upgrade needs a driver reinstall, it should, at least, warn somehow the kind of user that don't visit forums prior to upgrading (which was my case until yesterday).

Anyway, my xserver is working fine at this moment, I have the old xorg-core installed, the fixed xorg upgrade is ready to download, and I have working NVidia drivers. Can I upgrade it now without worring about anything else?

I wont mess with my video drivers (which were a pain to install by the way). So if this needs a driver reinstall, I'll just refuse to upgrade.

OFF-TOPIC: I used to smile when the upgrade icon popped in my screen. Now it gives me the shivers. I don't blame the people who uploaded the flawed upgrade. I am a programmer and I myself make this kind of fiasco sometimes. Some posters even said that "it happens", which I agree. But I do blame the people who took way too long for removing it from the mirrors thus avoiding this shameful disaster. I have several friends that I convinced to install Ubuntu, and none of them even read support forums and such. Now they are just helpless noobs staring astonished at a text prompt. Most of them gave up Linux and went back to pure Windows, and I took the blame. Yes, support teams shouldn't hear complaints, but they must retransmit them to the team that can do something about it.

mycelo

---

### Post by lerrup on 2006-08-23
> **raldz said:**
> Why is everybody cursing? When I encounter this problem, I did not bother to look at the forums.. the last thing I did was upgrade, and it broke the system, so the most logical solution at that instant is to downgrade.. since I know how to downgrade, it just took me less than 10 minutes to fix it... and in case I don't know how to downgrade, I would ask here at the forums.. now my system is updated to the 10.4 xserver core version.. 

So guys, next time, be kind enough to ask first before cursing.. I know how you feel... I was like that before everytime MS Windows flashes its Blue Screen of Death.. and I have no one to ask help to at that time.. and now I'm happy using Linux (MEPIS, Ubuntu, Fedora, SUSE, PCLinuxOS).. because the community support is great! =D> =D> =D> =D>

And if it is your only computer and you are a mere human being?  This is why people are cursing.

Also, TSEliot, my nvidia drivers worked fine without reinstalling, should this be in the first post?

---

### Post by raldz on 2006-08-23
> **lerrup said:**
> And if it is your only computer and you are a mere human being?  This is why people are cursing.

Also, TSEliot, my nvidia drivers worked fine without reinstalling, should this be in the first post?

That is why we have this LiveCD.. so that we can use our computers in case of times like this..

---

### Post by gambal on 2006-08-23
OK, got it fixed but now the package xserver-xorg-dev (version 10.4) seems to be broken according to Synaptic. There was also some error message regarding this when I fixed the issue by installing the suggested packages. What should I do with the broken package, remove it or what?

---

### Post by boon on 2006-08-23
> **Robert Leithe said:**
> I'm still in the dark - so to speak. I'm one of those "first time offenders", that is I'm completely new to Linux and my initial install of Ubuntu is about one week old .

2) I also tried the solution mentioned later in the thread, about downgrading without an internet connection

sudo dpkg -i **/var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb**

but got the same error as above (just another filename)


Any suggestions as to what I can try next?

Sincerely
Robert Leithe


Robert, 

I had similar problems. 

Firstly, do you have internet access from the command line? If so you can upgrade to the 10.4 fix easily with a couple of commands:

sudo apt-get update
sudo apt-get upgrade

If that doesnt work (maybe the patch is not on your local servers yet, or if you cannot get internet access), you can try the downgrade route, by accessing an old file in your archive and downgrading to it. This is what worked for me.

The trick is to locate and identify the exact name of the old file that is still in your system (in the cache/archives).

I used commands:

cd
ls

until I found the file and its exact name and location. In my case it was:

/var/cache/apt/archives/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb

Note that this xserver-xorg-core package was version 10.1. If you have 10.2 that should be ok, but 10.3 of course is the bug you want to get rid of.


Then, I did the command:

sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb

This successfully downgraded the package to version 10.1 and the problem was fixed. Reboot and back to normal.

The 10.4 patch fix has been uploaded by developers to my local servers and so later on I was able to download and upgrade to that using apt-get (or synaptic if you prefer).

hope this helps,

---

### Post by monkeeshyne on 2006-08-23
I would just like to stay that people need to realize that no one is perfect.  There are always going to be bugs.  Just be thankful that unlike Windows, Linux distributions like Ubuntu have such great community support that any problems are fixed in a very timely manner.  

Also, don't forget that you haven't paid a dime for this, so in reality, you have absolutely no right to demand anything.  If having to manually fix something once in a blue moon bothers you so much, then just return to Windows. There are so many bugs there that your expections should be much lower, and therefore, little things like this won't affect you so much!

---

### Post by Rick Myers on 2006-08-23
> **Seer said:**
> I gotta say....

Number of times an update in Windows XP has hosed my system in some way in the last 4-5 years........ Zero

Number of times an Ubuntu (component) update has hosed my install in some wa in the last 4-5 MONTHS ...... 4 or 5

Number of Blue Screens seen in Windows in since turned of the century ..... <1

Please stop the FUD. I love and use both OS's but I have to say the stereotypical MS bashers are just making themselves look stupid with FUD like the above post by Daynah

I'm not an MS lover, I obviously use Ubuntu, and I couldn't agree with you more...

And I apologize for being hostile in my first post in this thread. I expect the same thing my clients expect from me. Working software, working upgrades. Forgive me for holding my operating system to a higher standard than any other piece of software. 

The arguement that "humans make mistakes" doesn't hold water. If Ubuntu was developed by a lone programmer I'd buy into it. Ubuntu is an organization, as such, I suspect more than one person is involved. Organizations have a responsibility to test product and insure quality. If they don't, they won't last long. This demonstrates the need to review quality control procedures and implement changes. 

I, for one, would like to see Linux adpoted on the desktop. This will help force the major software manufacturers to port their apps to Linux. That will give all of us more choices. What about the Linux newbies that decided to try Ubuntu? Now they may have a bad taste in their mouths and may just abandon the effort of learning Linux altogether. These people may just say "Linux sux". Most average users won't be able to seperate Ubuntu and Linux in their minds. Should Linux lose ground on the desktop over an Ubuntu mistake that could and should have been avoided?

I've read over and over again in this forum and other Linux forums; "People will just have to get used to the command line" or "You'll have to get used the Gimp way of doing things". The average users response will be; "I already know how to use Windows and I don't have to learn the command line" and "I already know how to use Photoshop". There is nothing so special about Linux that it will compel an average user to completely change the way they do things. To achieve desktop adoption, Linux will have to meet these people much more that half way.

Stepping off the soapbox now...

---

### Post by iampoch on 2006-08-23
> **Robert Leithe said:**
> I'm still in the dark - so to speak. I'm one of those "first time offenders", that is I'm completely new to Linux and my initial install of Ubuntu is about one week old .

My problems is as this thread explains. But I cannot seem to get the suggestions to work properly.

I have tried these suggested solutions:

1) wget -c /../xserver-xorg-core-1.0.2-0ubuntu10-4_i386.deb (I shortened that one) and the same for the "dev file".

Both downloads went just fine. But when I ran the
**sudo dpkg -i xserver-xorg-core*.deb**
I get this error:
[B]dpkg: error processing xserver-xorg-core*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xserver-xorg-core*.deb[/B]

2) I also tried the solution mentioned later in the thread, about downgrading without an internet connection

sudo dpkg -i **/var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb**

but got the same error as above (just another filename)

3) I also tried the CD-ROM approach

mounted my CDROM and tried this command:
**sudo dpkg -i /media/cdrom0/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb**

...and I get the same error (I did an ls on the CDROM and under **/media/cdrom0/pool/main** I have no directory named **x**.

Any suggestions as to what I can try next?

Sincerely
Robert Leithe

I second this, have the same problem.

---

### Post by givré on 2006-08-23
> sudo apt-get update
sudo apt-get upgrade
If he want to install the 10.4 version, go for it.

---

### Post by lompa on 2006-08-23
Thanx tseliot!

...I was already thinking about reinstalling ubuntu :-)
Anyway, I do have a problem: I'm sure that updating the xerver core to the latest version (10.4) everything would be fixed, but I cannot do that 'cause after the xserver crashes my system hangs up and doesn't display any command line login. 

Is there a way to explicilty boot ubuntu without xserver? On my laptop the recovery mode doesn't work because for some reason it tries to load ACPI support, which has some imcompatibility with my CPU (AMD Turion - I had to disable ACPI support when I installed ubuntu)

Thanx again

Lompa

P.S. great nick name! I love TS

---

### Post by micheldad on 2006-08-23
I just want to say THANKS to this community from a nube.

I installed ubuntu about a week ago, and I'm learning linux as I go. So far I'm impressed. Got nvidia drivers working so Google Earth will work on my machine, and have been able to use VNC to connect to my home linux machine from my work WinXP pc. The package managers are great, and as a techie, linux is making much more sense to me after a week than Windoze has from v3.1 thru XP. No registry, and much less "deciding what's best for me and sparing me the details" thank you very much (not).

Anyway, I happened across a story on Digg about the xserver upgrade breaking the xserver while I was at work (on a working XP machine :D ). I realized that I had just ran the update in the morning. I was able to read these forums, the solution (downgrade), people's experiences with the solution, and learn quite a bit before the problem even affected me. Quite the opposite experience of what I'm used to.

When I booted linux this morning, sure enough, xserver crashed. Went to the command line, ran the downgrade command, rebooted, and POOF! I'm working again. Can't comliment this community enough for the timely advice. BRAVO!=D> 

BTW, I also saw on this forum this morning that 0ubuntu10.4 fixes the problem caused by 0ubuntu10.3. Ubgraded to 10.4 and seem to be good to go.

And this has been a nice practical learning experience. Ran "man" on apt-get, aptitude and other commands to see what these strange linux commands are all about and I'm learning as I go.

In short, Linux, ubuntu, and this community have been a pleasure for this new user.

Now if I could just stream videos to my xbox360, and share my printer to my fiancee's laptop whether I'm in XP or ubuntu. Also, can't wait to be able to read/write access my NTFS partitions. That's when I'll really cut the cord. 

Again, thank you all.

---

### Post by mordi on 2006-08-23
I didn't want to post on this thread for something that I would consider a minor issue. However, after seeing page after page of complains, my two cents.
updated, saw this warning, rebooted, xserver error, took me a couple of minutes to fix the problem (I type slow). it wasn't even necessary to reinstall the ati drivers, everything was back to normal. thak you tseliot.
@ people with the 404 Error: I had the same problem at first. turned out I made a typo. food for thought.
@ people that are complaining: you can try another distro, or buy a mac, or buy winxp home edition + a decent av licence + a couple of good free anti-spyware and pray you don't download the wrong torrent or install the wrong "free" software.

---

### Post by akak8ty on 2006-08-23
I have a friend, he's a 'broker.' Nice Italian man, **if** *you know what I mean.* 
He doesn't believe in computers because computers fail.
He still uses pen and paper (and a calculator _sometimes_)
He never loses productivity or money because he doesn't use his time to mess with machines. Remember those days? I do.

---

### Post by kulashaker on 2006-08-23
tseliot/community - thank you!

I was quite surprised when my laptop just booted to at blank screen. Did notice the update yesterday evening and wondered if everything would be allright.. guess it wasn't all allright, but your thread quickly led me to a solution. I logged in via ssh and the dist-upgrade pulled it off for me in no time. Very nice!

By the way, I don't really understand what all the complaining is about - just have a little patience and it'll work out.

Shaken, not stirred!
Kula

---

### Post by BatteryCell on 2006-08-23
Yes, just wanted to thank tseliot once again for taking his time to correct someone else's error.  I think that anyone whos complaining once they've seen this thread is just crazy because it has the fix... I could see complaining if there was no fix but there is...so everythings fine.

---

### Post by Eleka on 2006-08-23
tseliot: Yes, IO have installed nvidia-glx, nvidia-kernel-common and linux-restricted-modules from my running kernel, but the direct rendering is "no". I think that it would be a problem with my xorg.conf, but I didn't change anything on it ...

---

### Post by Dale61 on 2006-08-23
The majority seem to be saying one of two things - reboot via the CD, or just rollback to the previous version of xserver.

That's all good and well for experienced and seasoned users, but in the 3 weeks I've had to learn the new terminology, everything is not a simple as it seems.

I'm still in the process of setting up Ubuntu in a way that is easy on the eye (for me), and is not going to be a too difficult of a transition for my partner.  The 'ease-of-use' factor is the most important aspect of this install.

I had ordered my CD via ship.it a few weeks ago, and whilst I was waiting for delivery, I tried to read up as much as I could about what was going to be a totally new experience in the way I used my pc.  Days lead into weeks, and then a mate of mine purchased a copy of a monthly PC magazine, and the cover disc contained a copy of DD.  I used this to install, and then gave him back the disc, as I didn't expect to need it again before my copy arrived.  Unfortunately, this proved to be incorrect as I could have used the CD to re-install after the xserver breakage, if I had access to one at 11.45pm at night.

Funnily enough, the CD arrived yesterday, but only after fixing the xserver and getting everything to where it once was.

OK, so we all now know that the breakage was due to a faulty update, and if that update was all that you d/l'ed, it may have been obvious how the problem came about.  In my case, i had been d'ling and updating several things throughout the night (without rebooting after each stage), so I had no idea whatsoever of what caused the problem.

When I first setup my nVidia drivers, I got the xserver failed to run, etc, etc, screen, and by using the User Guide at wiki, I was able to get everything working as it should.  So, I fired up my laptop (XP), opened up my html version of the user guide, found the page I referred to earlier, and followed the instructions to the letter.  Nothing changed.  This is when panic mode set in.  I read the guide from top to bottom, trying anything and everything I thought would help, but to no avail.

Then it hit me.  Try this Ubuntu forum.  Bingo!  Thanks to tseliot (mate, you're a legend), I found that the break was due to the xserver update, and following his instructions back on page one (pre-edit), I was able to recover from what I thought was a major whoopsie on my behalf.

So, what may appear to be the obvious fix is not always possible, and if anything, I have now learnt to reboot after every update, no matter how minor, rather than update and/or install numerous packages all at the same time.

I do agree, however, that 10.3 was kept live for far too long, and that more users suffered from it than should have, but who do you blame?  Me, I'm just thankful that I've been released from a Windoze prison, and to the developers, for that a wholehearted 'Good On Ya, mates',

---

### Post by hobbit1983 on 2006-08-23
Thanks to tseliot.  

Mistakes happen - at least the command line was available and we could upgrade (or downgrade) and get x back.  If this had been another OS then we would have had no other feasible option than to re-install

tseliot represents the good of this community.  There was an big mistake but he came along and gave instructions on how to fix it.  In turn he seems to have born the brunt of many upset users.  

Thanks again

---

### Post by givré on 2006-08-23
> I do agree, however, that 10.3 was kept live for far too long, and that more users suffered from it than should have
It seams that people are not really aware of how the things were fixed.
If you follow the discution in this bug, you'll understand better :
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153)
In short,
On 2006-08-22 07:39:26 UTC, as soon as he could, Rodrigo Novo (the maintener of the x package) looks at this poblem and find the buggy patch.
On 2006-08-22 09:36:42 UTC, the problem was resolved and upload
> 
Just for reference: xorg-server 1:1.0.2-0ubuntu10.4 was uploaded to the archives a few moments ago. It will take a one to two hours before the packages are published and mirrored, but if you are in great hurry, you are also welcome to use the fixed packages available at:

[http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/)

2 hour to solve the problem it's not that much man. You should thanks him to reslove the problem as fast as he could (even if he is a bit responsable of the problem also :cool: )

---

### Post by georgetoon on 2006-08-23
Last night (08/22/2006), I got an update to, I think,Xserver....not sure now.  

Anyhow, this thread dates back to 2005.  Is this a recent problem?  I'm confused.  

I'm not in Ubuntu right now.

Edit -- Whoops, I just noticed I was lookinga thte orng date. thsi thread goes back to yestrday which means when I boot my system tonight, I'ts not gonna work casue i Downloaded tht update and then shut the system off.  Great!

If I boot ubuntu tonight and it's broken in some way and does not come up, I'm just gonna write over the HD with Freespire. 

Why?  Because I ha to do a lot of tweaking to get Ubuntu to read my storage drives.  And then I had to jump through hoops to get the screen rez to work.  

Nah, I'm not going through that again.

I'm hoping it'll start. We'll see.

---

### Post by markthecarp on 2006-08-23
Thank you givre for the insight into how this works. Two hours is pretty quick.

Folks if you keep using Linux you will see this happen again. I saw the first update come down and thought it odd that there was only one package. I had too much going on on my system so I didn't restart X. Next day there is another patch of the same package. "Ah something is "funny" here", I thought. So I checked the forums and read some of the ruckus on this thread. Thanks for the laughs folks. I still haven't restarted X, too much stuff to close out.

BTW: it is not necessary to reboot to restart X.

-mark

---

### Post by autocrosser on 2006-08-23
I have not chimed in on this yet---I THANK TSELIOT FOR HIS QUICK WORK TO HELP THE COMMUNITY!!!  Now that I've got everyone's ear-- I was lucky in that I am testing Edgy & it was working right then--I have been dual & triple booting for years and credit having a "fall-back" OS as my easy recovery from the "update".
 
When it's so easy to create another working OS--I would recomend creating a backup OS to anyone--very easy to sync your users data between Ubuntu installs & you can just reboot into your backup until you find out what the problem is.
 
Just my two cents worth--just remember people---everyone is HUMAN.

---

### Post by tomski on 2006-08-23
thanks tselliot for at least getting my x to start but now i am faced with command promt when ever i start up & i have to type in startx......

so as well as trying to get my gfx card to do 3d i now have to figure out how to get my login back thanks package support you really do help a noob dont you (sorry i know they cant hear me) but all this is just moving me back to windows which since all these problems i really am considering buying an XP license

im just fed up with configuring this damn pc I WANT TO USE IT....
....i even have to stay on longer at work just to admin my website!!

At this rate i may as well just give up & put up with windows lockups & frezze's, at least then i can use the damn pc rather than:
 config this, then install that, then whoops that update breaks this if you have that..
..I'm really trying to learn all this but its all going to far now

---

### Post by Dale61 on 2006-08-23
givre, I don't have a problem in how the problem was fixed, moreso the fact that the problem update was still being made available well after Rodrigo was informed.  In fact, referring to the same bug report, it was requested to remove it some 13 minutes (07:52:41 UTC) after Rodrigo posted he was working on the fix (07:39:26 UTC), and again almost 2 hours later (09:33:16 UTC).  Another request for it's removal was made at 11:25:52 UTC.

A lot of people can receive the update within that time frame, and that was what my point was aimed at.

---

### Post by givré on 2006-08-23
> **Dale61 said:**
> givre, I don't have a problem in how the problem was fixed, moreso the fact that the problem update was still being made available well after Rodrigo was informed.  In fact, referring to the same bug report, it was requested to remove it some 13 minutes (07:52:41 UTC) after Rodrigo posted he was working on the fix (07:39:26 UTC), and again almost 2 hours later (09:33:16 UTC).  Another request for it's removal was made at 11:25:52 UTC.

A lot of people can receive the update within that time frame, and that was what my point was aimed at.
I think it's more complicated that it seams. There is automatic process to upload, but i'm not sure there is the same for removing. On top if you consider the time that it takes to upload all the mirrors, you could think about the time to remove a package on all the mirror.

---

### Post by IanVaughan on 2006-08-23
Ok, help me - I have important work I need to get on with!!!

Auto updated new xserver as per everyone else, rebooted next day and bingo...

So, not thinking it was the update, I went to try and fix it myself, (with dpkg-reconfigure xserver-xorg) with no luck, so then found this!

So now easy, follow nice easy instructions in post 1, followed them, the "sudo aptitude install -s -V  xserver-xorg-core" simulation showed no updates to be done (I did do an update before).

I greped for the installed Version which shows 10.4, so all should be ok, but reboot and still no go.

So I reversed xserver to 10 (via sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10) but again still no go!
Instrestingly with this atempt, is that even after installing 10, the "show xserver... grep Version" still shows 10.4!!!

I am in hell!

Xorg.0.log :-
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]".
(EE) No devices detected.

Fatal server error:
no screens found


What do I need to do???

---

### Post by givré on 2006-08-23
```
sudo apt-get update
sudo apt-get upgrade

```
the apt-cache show show you the package available, not the package you had install.

---

### Post by IanVaughan on 2006-08-23
Did that, but nothing changed! 

Reading package lists...
Building dependency tree...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo aptitude show xserver-xorg-xore | grep Version :-

Version: 1:1.0.2-0ubuntu10.4

(I have previously used Automatix to update repositories list?!)

Any more clues?

---

### Post by zazery on 2006-08-23
> **Andrew1234 said:**
> Thank you for the fix, 

Since the xserver update I am finding the mouse freezes when in Firefox, is anyone else having this problem?? if so is there a fix!
I noticed a similar issue with the latest update (10.4). I run a dual monitor setup and my mouse cursor icon does not change to the approppriate icon on the second monitor. For example if my cursor was touching a window border (to resize) on my first monitor, and the then moves to the secondary monitor, the cursor will stay as a dual arrow head icon.

Also it appears that KDM fails to start at boot up, this did not occur until I tried to revert to the 10.2 xserver modules. Seeing as that didn't work I updated to the 10.4 drivers again, trying to fix it up again.

It leaves me wondering if this update was a step backwards in stability even if the breaking issue has been fixed.

---

### Post by ajaustin on 2006-08-23
Just to say thanks to tseliot for simple instructions that solved the problem for me in a few minutes.

---

### Post by fakie_flip on 2006-08-23
Is this the guy responsible for putting a package into the updates without testing it first, and breaking millions of systems around the world? 

```
ubuntu@ubuntu:~/Desktop$ apt-cache show xserver-xorg-core
Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 10168
**_[COLOR="Red"]Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>[/COLOR]_**
Architecture: i386
Source: xorg-server
Version: 1:1.0.2-0ubuntu10.4
Replaces: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Depends: x11-common, libc6 (>= 2.3.4-1), libfontenc1, libgcc1 (>= 1:4.0.2), libxau6, libxdmcp6, libxfont1, zlib1g (>= 1:1.2.1)
Recommends: xkeyboard-config
Conflicts: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
Size: 3530826
MD5sum: 522234ab64aa99af13253c65084906b9
Description: X.Org X server -- core server
 The X.Org X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The X.Org server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'xserver/xorg' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 10164
Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>
Architecture: i386
Source: xorg-server
Version: 1:1.0.2-0ubuntu10
Replaces: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Depends: x11-common, libc6 (>= 2.3.4-1), libfontenc1, libgcc1 (>= 1:4.0.2), libxau6, libxdmcp6, libxfont1, zlib1g (>= 1:1.2.1)
Recommends: xkeyboard-config
Conflicts: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
Size: 3529126
MD5sum: d359edda430ad9ac6d119e5a3bb213ad
Description: X.Org X server -- core server
 The X.Org X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The X.Org server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'xserver/xorg' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

ubuntu@ubuntu:~/Desktop$

```

---

### Post by Ann667 on 2006-08-23
I haven't been running Ubuntu for very long, maybe a couple months.  This was the first experience I've had with an update doing something like this.  I just wanted to say that I'm impressed with the quick response and fix.  I believe that tseliot and everyone else involved in supporting and correcting this issue deserve a huge thank you.  So, Thank You!

And I won't be putting Windows back on this computer.  (not that I can anyway, as I don't have the install disk...  but even if I did, I'll be sticking with Ubuntu.)  I did learn that it's a good idea to keep the live CD handy.  I can always boot from that and still get online to search the fourms.

---

### Post by TFX360 on 2006-08-23
> **fakie_flip said:**
> Is this the guy responsible for putting a package into the updates without testing it first, and breaking millions of systems around the world? 

```
ubuntu@ubuntu:~/Desktop$ apt-cache show xserver-xorg-core
Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 10168
**_[COLOR="Red"]Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>[/COLOR]_**
Architecture: i386
Source: xorg-server
Version: 1:1.0.2-0ubuntu10.4
Replaces: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Depends: x11-common, libc6 (>= 2.3.4-1), libfontenc1, libgcc1 (>= 1:4.0.2), libxau6, libxdmcp6, libxfont1, zlib1g (>= 1:1.2.1)
Recommends: xkeyboard-config
Conflicts: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
Size: 3530826
MD5sum: 522234ab64aa99af13253c65084906b9
Description: X.Org X server -- core server
 The X.Org X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The X.Org server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'xserver/xorg' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

Package: xserver-xorg-core
Priority: optional
Section: x11
Installed-Size: 10164
Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>
Architecture: i386
Source: xorg-server
Version: 1:1.0.2-0ubuntu10
Replaces: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Depends: x11-common, libc6 (>= 2.3.4-1), libfontenc1, libgcc1 (>= 1:4.0.2), libxau6, libxdmcp6, libxfont1, zlib1g (>= 1:1.2.1)
Recommends: xkeyboard-config
Conflicts: xserver-xorg (<< 6.8.2-38), xserver-xfree86
Filename: pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
Size: 3529126
MD5sum: d359edda430ad9ac6d119e5a3bb213ad
Description: X.Org X server -- core server
 The X.Org X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The X.Org server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
 .
 This module can be found as the module 'xserver/xorg' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

ubuntu@ubuntu:~/Desktop$

```
Uhm,


[B]Bill Gates

Is this the guy that is responsible for....[/B]


Not a very appropriate post. I bet he does good work the rest of the year around. If it even was his fault. I had the problem solved - with recompling my display drivers - in under five minutes. Xgl and all.


Thank you for your hard work Fabio M. Di Nitto. Keep it up. Anybody can make a mistake in a while, whe are all still human.


Kind regards,


TFX

---

### Post by hajk on 2006-08-23
> **fakie_flip said:**
> Is this the guy responsible for putting a package into the updates without testing it first, and breaking millions of systems around the world? 


Hey dude (fakie_flip), there's something seriously wrong with your attitude, what's next -- organize a lynching party? These maintainers make it possible that you can enjoy software at the cutting edge. What have you contributed lately?

---

### Post by h0mer on 2006-08-23
oh please, like MS has accounted someone publicly responsible for all the BSOD's...

just another word of thanks from here. I was trying to install an experimental ntfs driver while I updated xorg... of course after the crash I figured I had messed all up with the driver... a quick search here with Lynx gave an answer. Downtime: about 15 mins. It was awkward, but it could of been hell. Thank you all for a quick solution.

---

### Post by IanVaughan on 2006-08-23
Sorry to butt in, but maybe I think its going off topic, this isn't about blame etc, but solving ppls problems! Of which I have one!

My xserver states version 10.4, but even tho I have reconfigured xserver, it still doesn't work. 
Version: 1:1.0.2-0ubuntu10.4

1. Any ideas on getting this version to work?
2. I cannot get it to resort to version 10, why not and how can I get this to work?
3. Can I completely reinstall xserver (either from boot disc/disc/net?)
4. Could I of messed up my repositories?
5. Sorry to be soo utterly usless, but I a pretty new, and need all the help I can get!

---

### Post by koolguynet on 2006-08-23
I need some help.  I did the downgrade and at least got to where kdm will show a place for username and password.  In my quest to fix this problem I reinstalled kde (kubuntu-desktop) and kdm.  I also ran dpkg-reconfigure xserver-xorg .   Now I get to the login screen, login, and then everything starts to load but then fails.  When I say fail...I mean fail.  Hard disk stops, mouse locks up, keyboard ceases to function.  Any ideas?  Any more info I can post?

---

### Post by BatteryCell on 2006-08-23
So is it better to stay with the downgraded version or upgrade to the 10.4??

---

### Post by givré on 2006-08-23
An official fix :
[https://wiki.ubuntu.com/ResolutionForBug57153](https://wiki.ubuntu.com/ResolutionForBug57153)
Creator : JaneSilber & MattZimmerman
Never saw that for a bug. But it was indeed necessary.

---

### Post by CaveRat on 2006-08-23
Whew! Good thing I have not formated my (UHG) Windows box. Thanks to tseliot and whomever else worked on helping us to solve this minor glitch. I am too new at this to have figured it out on my own. I would have had to resort to reinstalling again if not for these most excellent people. Give up, give in to Windows? I don't think so. This is just way too much fun no matter how many times I have to install.

---

### Post by CaveRat on 2006-08-23
> **BatteryCell said:**
> So is it better to stay with the downgraded version or upgrade to the 10.4??

My box is working fine with the new update. I did not even have to reinstall my Nvidia driver.

---

### Post by crgutierrez on 2006-08-23
Congratulations for the very fast response eyesterday. I had the trouble fixed in less than 5 hours. Just two nagging questions: Why didi it happen to my laptop, but not to my desktop (I upgraded both at almost the same time)? Why did I apply some specific instructions yesterday, but today the final fix looks different?

In any case Great Work! I feel really very well supported.

CRG from Costa Rica

---

### Post by hellfried on 2006-08-23
woke up and there r 3 more updates this morning. the funny thing is that when i click on the update icon, synaptic opens up rather than the usual software update. why is this so and is it safe to update since it involves compiz, compiz-core and compiz-gnome? admittedly i am a bit paranoid after the latest debacle.....

---

### Post by sda5150 on 2006-08-23
For those that ran dpkg-reconfigure xserver-xorg (reconfigured xserver) and are now having issues. (IanVaughan and koolguynet)

I would try rolling back to your previous version of xorg.conf

steps:

> cd /etc/X11
> sudo cp xorg.conf xorg.conf.old
> sudo cp xorg.conf.2006*xxxxxxx* xorg.conf

Enter Y to overwrite.

> sudo shutdown -r now

This should roll your xserver config back to what it was before the problem.

---

### Post by koolguynet on 2006-08-23
sda5150, Thank you so much!  That solution worked!:D

---

### Post by georgetoon on 2006-08-23
Hi, Folks.:)

Well, I booted Ubuntu just now and I'm up and running.  I don't see anything wrong. Things appear to be ruing as they were last night.  I did do an update lat night, but nothing has crashed so far. 

should i check my system in some way? Or am I okay?

---

### Post by gregn on 2006-08-23
Fix worked. Am back up

Thanks

---

### Post by ChuckNH on 2006-08-23
Okay....nothing's working for me.  I figured I'd try the alternate CD method, but this is what results....

Version '1"1.0.2-0ubuntu10' for 'xserver-xorg-core' was not found.

What am I to make of this???? 

Oddly, when going through the code, the downgrade was observed, but still no xwindows upon reboot.  Where is this noob going wrong with this thing? I'm hanging in, but all the shouts of joy that the downgrade/upgrade has worked leave me just a tad frustrated.........

---

### Post by givré on 2006-08-23
> **georgetoon said:**
> Hi, Folks.:)

Well, I booted Ubuntu just now and I'm up and running.  I don't see anything wrong. Things appear to be ruing as they were last night.  I did do an update lat night, but nothing has crashed so far. 

should i check my system in some way? Or am I okay?
The buggy version actually may work on certain hardware.
It's why they let it go in the repo, their test was done with some hardware not hit by the bug.

---

### Post by givré on 2006-08-23
> **ChuckNH said:**
> Okay....nothing's working for me.  I figured I'd try the alternate CD method, but this is what results....

Version '1"1.0.2-0ubuntu10' for 'xserver-xorg-core' was not found.

What am I to make of this???? 

Oddly, when going through the code, the downgrade was observed, but still no xwindows upon reboot.  Where is this noob going wrong with this thing? I'm hanging in, but all the shouts of joy that the downgrade/upgrade has worked leave me just a tad frustrated.........
What's happens if you upgrade to the latest version?
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by HereInOz on 2006-08-23
Thanks tseliot.  It is good to know that when something like this happens, as it inevitably will, there are people out there who are able and prepared to help the rest of us.

Again, many thanks for helping get my system back up and running.

Cheers,

Alan

---

### Post by georgetoon on 2006-08-23
> **givré said:**
> The buggy version actually may work on certain hardware.
It's why they let it go in the repo, their test was done with some hardware not hit by the bug.

Thank you.:)  I saw [the page with the explanation]("http://www.ubuntu.com/FixForUpgradeIssue") on the fix and the overall situation. It says:> A subsequent update published 17 hours later corrects this, so if your system is fully up to date now and you have no obvious graphical system failures, then you are highly unlikely to be affected.

So, I have to assume that my hardware is unaffected, or i downloaded the corrected download.


I gotta tell ya, I'm really glad I don't have to overwrite this Ubuntu install.:)  I really do like it and appreciate the work of all those who contribute to its build.  I do plan on doing a dual boot with Freespire, though.:) I'll wait for a few more updates to make sure that all is well with my system before I attempt anything new.:)


BTW, sorry for the typos in my previous posts. I gotta remember use Aspell more often.:):)

---

### Post by Jax55 on 2006-08-23
> **givré said:**
> It seams that people are not really aware of how the things were fixed.
If you follow the discution in this bug, you'll understand better :
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153)
In short,
On 2006-08-22 07:39:26 UTC, as soon as he could, Rodrigo Novo (the maintener of the x package) looks at this poblem and find the buggy patch.
On 2006-08-22 09:36:42 UTC, the problem was resolved and upload

2 hour to solve the problem it's not that much man. You should thanks him to reslove the problem as fast as he could (even if he is a bit responsable of the problem also :cool: )

A big thanks to Rodrigo for that one...

The problem in my case was that I got the package and ran into the problem at about 2006-8-21 22:00 UTC (8AM local Aust time), which means *at least* 11 hours with the buggy patch being downloaded.   Launchpad was down for maintenance, but quite a few of us reported stuff on the forums.   (Thanks to jlx and tseliot for the fixes then).

I know fixes take time, but is there any way to get a message to someone to pull a potentially buggy patch until somone can verify what needs to be fixed.   11-13 hours means a heck of a lot of people downloaded it... And given Ubuntu prides itself on GUI-based ease-of-use goodness, there are probably still a huge number of people staring at a frozen Ubuntu splash screen with no idea what they did, or where to look for help.

I overheard a couple of people in our building saying "Yeah that Ubuntu is a real problem...  I wish we could just go back to Windows".   Unfortunately, this is the type of press we are getting.   I know it would be worse in Windows-land, but when it happens there **they get roasted** and we gloat.   It might be an idea to stop burying our heads in the sand and saying things like "well if you don't like learning the CLI, then go back to Windoze land luser".   These are the people we are trying to convert!

PS - I am a recent covert from being a 9-year Slackware veteran (so I am fine with the CLI myself ;) ) - Ironically, I was using Ubuntu because the update management was a bit more slick.   Still an excellent distro, but for goodness sake can we try and learn something from this!

---

### Post by boon on 2006-08-23
> **Andrew1234 said:**
> Thank you for the fix, 

Since the xserver update I am finding the mouse freezes when in Firefox, is anyone else having this problem?? if so is there a fix!

I have had a problem since the update to v10.4 of a keyboard freeze (only in Firefix). eg, when I tried to type into the address bar.

Quitting Firefox and restarting it solves the problem, but its happened at least 2 or 3 times so far.

---

### Post by RobNY on 2006-08-23
I, too, was broken and now fixed... the only thing I've noticed so far is that the Ubuntu logo seems screwy when loading Nautilus, etc..  Anyone else notice this?

---

### Post by ColonelPanik on 2006-08-23
Thank you for the fix!  I did not even have to reinstall my nVidia drivers.

Did you all work at M$?

---

### Post by Flysafe on 2006-08-23
Thanks. This solution got my system back working.

---

### Post by pt123 on 2006-08-23
How terrible is this bug. My grandma has no idea what do with the terminal screen. 
Ubuntu clearly is not sufficient for beginners. Now I have to go back and reinstall Windows back on her computer. 

What kind of testing are they doing at Ubuntu.

---

### Post by akak8ty on 2006-08-23
**gambal wrote:**
OK, got it fixed but now the package xserver-xorg-dev (version 10.4) seems to be broken according to Synaptic. There was also some error message regarding this when I fixed the issue by installing the suggested packages. What should I do with the broken package, remove it or what?

Everything package I installed in synaptic was not without error after the fact, so I was either removing or reinstalling. There really are some great packajes and little programs in Ubuntu. That is what captured my mom's attention. Mom's jaw dropped to the floor as she watched her great grand daughter, who was just 4 in May ace the memory game everytime- doing a far better job than we did- *tres amusant.*
I taught her well ;)

---

### Post by raw_knee on 2006-08-24
I'm one of those who immediately applied the update after it popped up on update manager...

Quite annoying, really... I spent almost the whole day bringing my desktop machine back on its feet after X won't start... I just reinstalled and updated everything except for that Xserver update... But not everyone has the luxury of doing that on their system...

Now that taught me a lesson -- I won't apply any update on my desktop machine right away... I'll just let a day or two pass in case something like this would happen again... :frown:

---

### Post by bullgr on 2006-08-24
this is the second (and more worse) bug from updates the last week...

the other bug was in compiz who after the update screw synaptic and was unable to run it (but was easy to fix this problem).

i figure that is better to make my updates every 15 days... so i can see in the forum if is there any problem with the new updates.

with this method i save many unecesary problems.
there is no need to rush for updates...

im not a guru but i believe if you guys follow this steps you will avoid the bugs in the updates:

-update every 15 days or better every month
-before the updates check the forum if is there any bug

---

### Post by Perfect Storm on 2006-08-24
The compiz repo have nothing to do with the official ones. If you use the extra compiz'n'XGL repo it's on your own responsibility.

---

### Post by msandersen on 2006-08-24
How ironic; these days, Linux is far more affected by the Blue Screen of Death than Windows. Sometimes a Black Screen of Death.
I did update, and noticed the Update manager had trouble with some of them and advised using Synaptic. So I did. It had trouble with broken packages, which I removed. I didn't reboot, as I'm downloading something. Just as well. I've upgraded to 10.4, we'll see the next time I reboot if there are any issues.
Mandrake made its name as a cutting-edge Desktop distro with the latest packages, but they had (have?) continual quality assurance problems. It was buggy as hell, it was only ever good for me to test what the whole Linux thing was and how it measured to the hype. I also needed to test PHP scripts on a Unix-like system. Eventually RPM Hell and some showstopper bugs (in particular one which destroyed the partition table of some users) made me think twice about upgrading. 
Now I'm giving Linux a second try with Ubuntu, I've learnt Linux still does not live up to the hype and they have ongoing upgrade issues. This one being a doosey, which they do seem to take to heart. But there has been other times when I've been stuck on a command line. Something that would be unthinkable on a Mac, or Windows for that matter.
Debian may be conservative in having a Testing branch which leaves Stable with outdated packages, but it does lead to a stable system. But whereas that may suit Server admins, it definitely doesn't suit Desktop users who usually want the latest and greatest.

Windows has a "Safe" mode, and Linux has one of sorts, but whereas Windows boots with backup base drivers known to work with all other services turned off, Linux Safe Mode boots with the current modules which are causing the trouble. So in this instance, Safe Mode wouldn't have made a difference. 
Maybe Linux should have a backup of core system files like the Linux kernel and the X-Server which has been marked as "Stable" after an extended testing cycle, like Debian perhaps, so it can drop back to that if necessary and using default display drivers like "nv" etc. That could make for a decent "Safe Mode" from which people had a better chance of recovery, especially as they often have to get on the internet to read the forums for help.

---

### Post by divali on 2006-08-24
Well, I'm just glad I saw this sticky in time and was able to correct it 
before I started fiddling about trying to fix it myself. :-\"

---

### Post by Adler on 2006-08-24
Can't we just close this thread?

I lost stuff, along the way we all can complain. I run UBUNTU as a Workstation -- there is a lot involved here. More than most. 

I think the lessons have all been learned here. To be sure -- we weren't warned fast enough.

Adler

---

### Post by addisor on 2006-08-24
I'm a newbie to Ubuntu and aim enjoying the challenge of learning. I too had the Xserver problem and found the only solution for me was to roll back to 1:1.0.2-0ubuntu10. Why has 10.4 not worked as a solution? please make any replies simple procedures.

---

### Post by pelago on 2006-08-24
I see this has now made the front page of ubuntu.com, with a link to [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue) which further links to [http://www.ubuntu.com/UpgradeIssue](http://www.ubuntu.com/UpgradeIssue) describing what happened. In that last page it says:

> An update to the windowing system in Ubuntu was incorrectly released for Ubuntu 6.06 LTS. When applied to Ubuntu 6.06, the patch inadvertently breaks the desktop windowing environment on some systems. **When we learned of the problem, the patch was immediately withdrawn.** Mirrors have also been disabled to ensure that the faulty patch isn't available from them. For the limited number of users who received the patch in question, the corrective action above will resolve the issue.

The bit in bold (my bold) isn't true, is it? Many people in this thread and in the launchpad discussion noted that 10.3 was available on each mirror until 10.4 replaced it. There was no period when 10.3 was deleted, was there?

---

### Post by jrjr on 2006-08-24
.

---

### Post by cevans on 2006-08-24
Why is it that all of the guides on how to fix this have what appears to be an unnecessary reboot step, instead of the faster sudo /etc/init.d/{g/k/x}dm restart (or startx, in my case)? If I recall, the xorg packages in question don't affect anything other than Xorg itself, so a reboot shouldn't be required.

---

### Post by Qvistgaard on 2006-08-24
As an anacronistic DOS-fan (but no M$-fan) I'm new to the Linux alternative.

Installed 6.06 to my NTFS partition on one of my identical HD's and upgraded (all 167) with the known result - I had no idea as to what to do with a linux-promt.

Found this forum and TSEliot's 3 lines. 1st line went fine, number 2 had for some reason to be written blindfolded but went fine, number 3 -no reaction.

Rebooted by cont-alt-del - same prompt.

Wrote the downgrade line - no 10.3 to be found was the answer.

Rewrote the number 3 line - and now it worked.

Rebooted - and tada - I had a desktop again.

Installed KDE - desktop ....nowhere to be found...

printer (Canon 4u laser) ... doesn't work

WineHQ - nowhere to be found.

Can't read the other partitions - so I can't use the fonts from WindowsXP or the music.

Rome still wasn't build in one day. 8)

---

### Post by dkitty on 2006-08-24
Many thanks for posting this tseliot, especially for including instructions for those of us with the alternate install CDs.

---

### Post by HeresJohnny on 2006-08-24
Thank you, tseliot, you saved my life.  I thought it was something I did.  I really appreciate your efficient solution.  I followed it to the letter, and I'm up and running again.  Yahoo!!!:KS 
(now, to get the different input languages working again, and access my mp3s.  And what's this I hear about being able to access my Windoze fonts?  Ohh, daddy's gonna play today!)

---

### Post by mycelo on 2006-08-24
Again, will I have to reinstall NVidia drivers or not?

mycelo

---

### Post by Eleka on 2006-08-24
> **mycelo said:**
> Again, will I have to reinstall NVidia drivers or not?

mycelo

Mycelo, I have reinstalled it, but it don't works for me today ... I'm working on fix that problem

---

### Post by tseliot on 2006-08-24
> **mycelo said:**
> Again, will I have to reinstall NVidia drivers or not?

mycelo

I said this in my first post:
> If you installed the proprietary drivers for ATI or Nvidia cards you will have to reinstall them otherwise they won't work

---

### Post by Eleka on 2006-08-24
But I have reinstalled the nvidia driver and it don't works for me :(

---

### Post by givré on 2006-08-24
I don't really understand why you need to reinstall the driver, could you explain me tseliot, please?
If it is, upgrade of xserver-xorg are not really welcome, since lots of user use restricted nvidia/ati driver.

---

### Post by ChuckNH on 2006-08-24
> **givré said:**
> What's happens if you upgrade to the latest version?
```
sudo apt-get update
sudo apt-get upgrade
```

after update - reading package lists...done
after upgrade - 

building dependency tree...done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm at a loss, but remaining patient and glad to have the community help available.  Can't wait to get out of echspee, though.  Thanks for your reply.

---

### Post by tobyhdr on 2006-08-24
I have followed tseliot's instructions, but it has not solved the problem.

I have a Siemens Lifebook, but am not sure as the the graphics card, except that it must be an ATI Radeon judging from the output fromXorg.0.log:

(II) ATI: Candidate "Device" section "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]".
(EE) No devices detected.

After upgrading xorg-core to 10.4 and verifying its existence with aptitude, I searched for what drivers I might have. I then removed and reinstalled xserver-xorg-driver-ati AND xserver-xorg-driver-atimisc, was told by apt-get the actions hade been successful, but nevertheless X still fails with the above error message.

Any help would be greatly appreciated. I do not want to reinstall.

Cheers

Toby

---

### Post by MKR. on 2006-08-24
> **tobyhdr said:**
> I have followed tseliot's instructions, but it has not solved the problem.

I have a Siemens Lifebook, but am not sure as the the graphics card, except that it must be an ATI Radeon judging from the output fromXorg.0.log:

(II) ATI: Candidate "Device" section "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]".
(EE) No devices detected.

After upgrading xorg-core to 10.4 and verifying its existence with aptitude, I searched for what drivers I might have. I then removed and reinstalled xserver-xorg-driver-ati AND xserver-xorg-driver-atimisc, was told by apt-get the actions hade been successful, but nevertheless X still fails with the above error message.

Any help would be greatly appreciated. I do not want to reinstall.

Cheers

Toby

With proprietary drivers, there's usualy a command you have to run to make it work. Check the package description (use aptitude [like synaptic, but less refined, and works on the CLI] if you don't have another functional linux box available to check with).

---

### Post by jayfish on 2006-08-24
> **Dale61 said:**
> ...which means there will be a dozen less pc's converting to Ubuntu.  May not sound like a lot, but he will tell others, and so, it will travel down the line.

...My apologies for such a harsh first post, but as I came within a bulls' roar of ditching DD and going back to Windoze, I just needed to vent.

 Good post. I’ve been a Windows user for 17 years and in the past two or three I have been looking for an excuse to switch over to alternative OS. In the past 6 months I have been really cramming the distros in there(must be around ten). All of the distros I have tried have been somewhat underwhelming until I tried  Ubuntu. I was really digging it. I even went to the point of forcing my wife to use U. If she needed anything from her Windows box she could use RDP to access it. Then this little SNAFU reared its’ ugly head. Luckily for me I found the fix rather quickly, but since all kinds of other issues have begun to pop up. I just don't think Linux is ready for prime-time yet. It reminds me a lot of Windows 3.x through ME, a marginal GUI running on top of a character driven OS. It's too much work for to little reward. I'll still play around with Linux but I've connected my wife’s PC back up to its' keyboard, monitor and mouse. Better luck next release I guess.

Jay

---

### Post by spockrock on 2006-08-24
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

here is a wiki on installing radeon drivers on dapper.

---

### Post by moephan on 2006-08-24
This fix worked perfectly for me. I had no gui for about 5 minutes total. Also, I didn't lose any data or anything. The support that comes with Ubuntu, which is itself free, makes Ubuntu an incredible value. 

Stuff like this happens, even to big companies like Sun and Microsoft.

---

### Post by funchords on 2006-08-24
> **tobyhdr said:**
> I have followed tseliot's instructions, but it has not solved the problem.

I have a Siemens Lifebook, but am not sure as the the graphics card, except that it must be an ATI Radeon judging from the output fromXorg.0.log:

(II) ATI: Candidate "Device" section "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]".
(EE) No devices detected.

After upgrading xorg-core to 10.4 and verifying its existence with aptitude, I searched for what drivers I might have. I then removed and reinstalled xserver-xorg-driver-ati AND xserver-xorg-driver-atimisc, was told by apt-get the actions hade been successful, but nevertheless X still fails with the above error message.

Any help would be greatly appreciated. I do not want to reinstall.

Cheers

Toby


Toby,

When I read the bug report for "the incident," the buggy behavior in xorg-core 10.3 caused "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" to be listed in error.  

Since you have 10.4 and are still having this problem, you probably have bad info in your xorg.conf.

1.  Go to /etc/X11 ...   cd /etc/X11
2.  Copy the current copy to a safe name .... sudo cp xorg.conf xorg.conf-badbadbad
3.  look for prior copies of xorg.conf and use it to restore ... sudo cp xorg.conf-20060731 xorg.conf
4.  reboot ... sudo reboot

If you don't have a prior copy (in step 3), there's a command you can use to recreate it.  **Someone else, please provide that command -- because I cannot find it right away.  **Everyone knows it, except for me. :-& 

HTH

---

### Post by BerlinOliver on 2006-08-24
Hi,

I just updated to 10.4 but now my problems are starting.

1) synaptic shows an error when installing new software. 
> X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

2. I reinstalled my nVidia drivers, but glxgears says:
> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Can you please help me?

---

### Post by tomski on 2006-08-24
Firstly i must appollogise for my earlier post.. i was in a bit of a bad mood & i am deeply sorry for ranting, i now understand im complaining about something that is free.

Humans do & will make errors 

The Problem:

I have followed tselliot's instructions but it seems i have lost GDM, when i start up all i get is the login prompt with black screen.
Which then i have to type:

startx

I know it's not much of a problem but it is not as it was before,
What has changed?

Corrective Actions taken so far:

I have tried to reinstall ati drivers from repo & ati site, i also reinstalled resricted modules for my current running kernel  before the drivers each time.
No joy.
I then tried to reinstall ubuntu-desktop, but strangely when apt-get did this it just replaced 48kb of files?????
Reboot.
no joy.
login.
startx.
fired up synaptic reinstalled GDM
no joy.

At this point i could check which files have root/user permissions, but i have no idea what files to check & what permisions these files need!

I am lost & out of my depth & as well as that my legs have got cramp from treading water for too long!!
 but i am still reluctant to return to windows 

please help

Quick tip:
You don't need to reboot, try:

telinit 1

this will send all process the TERM signal!! & drop to single user then go straight to runlevel 2

---

### Post by jayfish on 2006-08-24
> **tomski said:**
>  ....i now understand im complaining about something that is free.



Bull, you have every right to complain, and you should, whether it's free or not. These are the same snobbish folks who will extol the virtues of Linux, to a non-Linux user, to the point of beratement. Now when it busts a cog they have the audacity to say you can't complain? Ya know what, air is free too but when it makes you sick to breath it you bet your *ss I'm gonna complain.

Jay

---

### Post by yaztromo on 2006-08-24
> Thank you for your hard work Fabio M. Di Nitto. Keep it up. Anybody can make a mistake in a while, whe are all still human.

He just breaks the Xserver on thousands of machines by putting out a totally untested patch and you're thanking him for his hard work?? :o 

I hope he got some kind of ticking off. We don't need developers that don't know the meaning of the word test. A five year old could have employed better quality control. Sheesh.

---

### Post by tobyhdr on 2006-08-24
thanks funchords and mkr. However, your advice has not helped X.

I did:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

and recreated xorg.conf too (with dexconf by the way), but neither has helped, not even the even newer xorg.confs generated by the commands above. Xorg.0.log reports the same error as before, only this time after having loaded a bunch of other drivers, obiously from the aticonfig commands. None of my three xorg.conf files helps, they all bring "No deviced detected" errors.

I am at a loss, and am beginning to think a reinstall is necessary.


Toby

---

### Post by funchords on 2006-08-24
Toby,

I'm afraid that, beyond the very simple things that I am comfortable with, I can't help you further.  (New here, myself.)

This Thread is 71 pages, has a lot of noise in it, and the people "in the know" have probably stopped looking at it.  Since you're on 10.4 and having problems, you're in a different situation.  

Consider starting a new Thread in [Hardware Help - Video & Sound]("http://www.ubuntuforums.org/forumdisplay.php?f=138") with a concise Subject line and a recap of what happened and where you are now.

Hopefully that will prevent you from a reinstall ... which you can still save as Plan B.

---

### Post by tseliot on 2006-08-24
> **yaztromo said:**
> He just breaks the Xserver on thousands of machines by putting out a totally untested patch and you're thanking him for his hard work?? :o 

I hope he got some kind of ticking off. We don't need developers that don't know the meaning of the word test. A five year old could have employed better quality control. Sheesh.

The update did not cause the problems on some computers of a few people. The update was tested (on several computers). The only question is why the package messed up only some computers?

**Please, restrain yourself from criticising the work of other people if you don't know the facts.**

---

### Post by tseliot on 2006-08-24
> **tobyhdr said:**
> thanks funchords and mkr. However, your advice has not helped X.

I did:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

and recreated xorg.conf too (with dexconf by the way), but neither has helped, not even the even newer xorg.confs generated by the commands above. Xorg.0.log reports the same error as before, only this time after having loaded a bunch of other drivers, obiously from the aticonfig commands. None of my three xorg.conf files helps, they all bring "No deviced detected" errors.

I am at a loss, and am beginning to think a reinstall is necessary.


Toby

Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then:
```
sudo dpkg reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to the questions.

If vesa doesn't work try with "vga".

---

### Post by Adler on 2006-08-24
> This Thread is 71 pages, has a lot of noise in it, and the people "in the know" have probably stopped looking at it. Since you're on 10.4 and having problems, you're in a different situation.

Toby,

The ATI Driver thread is over 100 pages long! So no big deal in regard to length. **However**, this situation is far worse. Being trashed like this is not fun.

I did a fresh install and followed the code at the beginning of this thread. 

BTW, nice site from your side.

Adler

---

### Post by tomski on 2006-08-24
i have tried downgrading my xserver core
then reinstalled my ati drivers
that did not work
i then installed the latest 10.4 version followed by the ATI installer script & that has given me my 3d support but i still get the default login promt.
still no gdm

any idea's
EDIT:

i have just got 3d back by using the script created by kilz & i have fixed my xserver problem, but i had to do some rather odd things to fix it:

1 follow the instructions on page 1 of this post
2 reinstall ati drivers using steps in [this post]("http://www.ubuntuforums.org/showthread.php?t=235145")
3 create the following folder tree:
/etc/X11/xserver/
4 save following code as: SecurityPolicy
```

version-1 

# $Xorg: SecurityPolicy,v 1.3 2000/08/17 19:47:56 cpqbld Exp $

# The site policy fields are interpreted by the XC-QUERY-SECURITY-1
# authorization protocol.  The values are arbitrary and site-specific.
# Refer to the Security Extension Specification for the usage of the policies.
#sitepolicy A
#sitepolicy B
#sitepolicy C

# Property access rules:
# property <property> <window> <permissions>
# <window> ::= any | root | <propertyselector>
# <propertyselector> ::= <property> | <property>=<value>
# <permissions> :== [ <operation> | <action> | <space> ]*
# <operation> :== r | w | d
#	r	read
#	w	write
#	d	delete
# <action> :== a | i | e
#	a	allow
#	i	ignore
#	e	error

# Allow reading of application resources, but not writing.
property RESOURCE_MANAGER	root	ar iw
property SCREEN_RESOURCES	root	ar iw

# Ignore attempts to use cut buffers.  Giving errors causes apps to crash,
# and allowing access may give away too much information.
property CUT_BUFFER0	root	irw
property CUT_BUFFER1	root	irw
property CUT_BUFFER2	root	irw
property CUT_BUFFER3	root	irw
property CUT_BUFFER4	root	irw
property CUT_BUFFER5	root	irw
property CUT_BUFFER6	root	irw
property CUT_BUFFER7	root	irw

# If you are using Motif, you probably want these.
property _MOTIF_DEFAULT_BINDINGS	root	ar iw
property _MOTIF_DRAG_WINDOW	root	ar iw
property _MOTIF_DRAG_TARGETS	any 	ar iw
property _MOTIF_DRAG_ATOMS	any 	ar iw
property _MOTIF_DRAG_ATOM_PAIRS	any 	ar iw

# If you are running CDE you also need these
property _MOTIF_WM_INFO		root	arw
property TT_SESSION		root	irw
property WM_ICON_SIZE		root	irw
property "SDT Pixel Set"	any	irw

# The next two rules let xwininfo -tree work when untrusted.
property WM_NAME	any	ar

# Allow read of WM_CLASS, but only for windows with WM_NAME.
# This might be more restrictive than necessary, but demonstrates
# the <required property> facility, and is also an attempt to
# say "top level windows only."
property WM_CLASS	WM_NAME	ar

# These next three let xlsclients work untrusted.  Think carefully
# before including these; giving away the client machine name and command
# may be exposing too much.
property WM_STATE	WM_NAME	ar
property WM_CLIENT_MACHINE	WM_NAME	ar
property WM_COMMAND	WM_NAME	ar

# To let untrusted clients use the standard colormaps created by
# xstdcmap, include these lines.
property RGB_DEFAULT_MAP	root	ar
property RGB_BEST_MAP	root	ar
property RGB_RED_MAP	root	ar
property RGB_GREEN_MAP	root	ar
property RGB_BLUE_MAP	root	ar
property RGB_GRAY_MAP	root	ar

# To let untrusted clients use the color management database created
# by xcmsdb, include these lines.
property XDCCC_LINEAR_RGB_CORRECTION	root	ar
property XDCCC_LINEAR_RGB_MATRICES	root	ar
property XDCCC_GRAY_SCREENWHITEPOINT	root	ar
property XDCCC_GRAY_CORRECTION	root	ar

# To let untrusted clients use the overlay visuals that many vendors
# support, include this line.
property SERVER_OVERLAY_VISUALS	root	ar

```

reboot or if impaitent run
telinit 1 as root

bingo bango working desktop

now i just got to work out what had deleted the folder & file in the first place!!!??

thanks to all involved you have kept me away from the clutches of Billy Gates & his mates

---

### Post by jbonll05 on 2006-08-24
Another fix;

   Download and intall 6.06.1. I thought the whole os had crashed. Checked website for downloads and downloaded 6.06.1. It installed clean and had only four updates. They were uneventful. I have two machines on Ubuntu, the other one had not been updated. They very much mirror each other, so restoring files was easy with an usb hd. I did the 6.06.1 to the second machine. All is peaceful here now.

   I noted that there were 300 tweaks (my word) in the updated 6.06.1.
JB, Ubuntu for all, someway.

---

### Post by getglenn on 2006-08-24
I had success with the following...

choose the RECOVERY boot option
then
SUDO apt-get update
SUDO apt-get upgrade
and
REBOOT the pc

---

### Post by funchords on 2006-08-24
> **tseliot said:**
> The update did not cause the problems on some computers of a few people. The update was tested (on several computers). The only question is why the package messed up only some computers?

**Please, restrain yourself from criticising the work of other people if you don't know the facts.**

I suppose it is natural to speculate when one does not know the facts.  

Most people try to do a good job each day.  This incident may have been an omission/accident by a well-intentioned developer/team.  It may have been a bad or missing process.  Quite possibly, it was a mix of both.  It was a major ](*,), but it wasn't malicious.

As a user of software (free or not), I do not feel entitled to know the embarrassing details.  But I do want to know that the circumstances have been reviewed and that actions will be taken to reduce the risk of something like this happening again.

My $0.02 (USD -- which is dropping fast)

 -- Robb

PS:  Good job by you that night!

---

### Post by jrjr on 2006-08-24
.

---

### Post by monktbd on 2006-08-25
I have not read all the pages, but maybe it would be a good idea to implement a featue into the update manager that allows one to set his level of knowledge with linux.

The result of such a setting is only to hold back updates for a short amount of time (e.g. 24 hours).

There are still a lot of distributions out there that do not feature automatic update notifications and i doubt everyone tries to update there daily.

People proficient enough with the command line interface were able to overcome the problem with the x-server but new users who recently switched to linux were stuck. 
So maybe delaying updates for newbies might be an idea.

---

### Post by Dale61 on 2006-08-25
I was able to fully recover by downgrading back to 10.2, and then locked that installation as per an earlier poster.

Last night (Australian time), as I was confident enough to know how to fix the problem if it were to happen again, I decided to upgrade to 10.4.

Firstly, I checked what version was actually installed here, and it indicated I had 10.4, so checked Synaptic, and it still showed I had 10.2 installed.

Hmm, ok, I thought, so I unlocked the installed version, updated the Synaptic, and uploaded the indicated update (10.4).

Fingers crossed, I rebooted, and everything was looking as I had come to expect.  Double checking my drivers, I found that my nVidia drivers were still installed, and that 3D rendering was still running.  It's just like nothing untoward ever happened.

Apart from the frustration of thinking it was something I did wrong, the best thing to have come out of all this, for me, is that I was able to better understand the use of a command line, which is a good thing.

I have got a Ubuntu installation to do tonight (the owner of that machine is less pc literate than a block of wood), so hopefully, nothing like this will happen again in the near future as he will have absolutely no idea how to go about fixing it, even with simple, written instructions.

BTW, for all those who have this thread showing in 70-odd pages, go to your User CP and change the setting for posts per page to 40.  I have done that and this thread is 'only' 18 pages in length.

---

### Post by yaztromo on 2006-08-25
> **tseliot said:**
> The update did not cause the problems on some computers of a few people.

Correct. It caused the problems on some computers of a lot of people.

> 
 The update was tested (on several computers). The only question is why the package messed up only some computers?

**Please, restrain yourself from criticising the work of other people if you don't know the facts.**

Several computers? Sorry but thats not really good enough testing in my eyes. Several computers to me means 4 or 5. An update like this needs testing on lots and lots of computers. Doesn't anyone know how to properly test a patch? Obviously you and the developer don't.

**This part is really bold!! and stands out!!!**

---

### Post by tseliot on 2006-08-25
> **yaztromo said:**
> Correct. It caused the problems on some computers of a lot of people.



Several computers? Sorry but thats not really good enough testing in my eyes. Several computers to me means 4 or 5. An update like this needs testing on lots and lots of computers. Doesn't anyone know how to properly test a patch? Obviously you and the developer don't.

**This part is really bold!! and stands out!!!**

Again, did you know exactly how things went and therefore also on how many computers the update was tested?

If not, then just stop bashing the developers. The fact of being angry with them does not justify what you said. **Offending other people is NOT tolerated on this forum**.

About testing:
I am not a developer. But that does not allow you to claim that I don't know how to test things since you don't know me.

If you are a developer and you think to be much better than the current developers then apply for a job or work as a volounteer and contribute instead of claiming that the developers don't know "how to properly test a patch".


**Now, let's get back on topic. I remind you that this is a support thread.**

---

### Post by The Pinny Parlour on 2006-08-25
> **tseliot said:**
> Again, did you know exactly how things went and therefore also on how many computers the update was tested?

If not, then just stop bashing the developers. The fact of being angry with them does not justify what you said. **Offending other people is NOT tolerated on this forum**.

About testing:
I am not a developer. But that does not allow you to claim that I don't know how to test things since you don't know me.

If you are a developer and you think to be much better than the current developers then apply for a job or work as a volounteer and contribute instead of claiming that the developers don't know "how to properly test a patch".


**Now, let's get back on topic. I remind you that this is a support thread.**

OMG You must be joking.   If people where affected by this then they have a right to express their dissapointment.  There are to many people scared of speaking their mind on this forum.

---

### Post by tseliot on 2006-08-25
> **The Pinny Parlour said:**
> OMG You must be joking.   If people where affected by this then they have a right to express their dissapointment.  There are to many people scared of speaking their mind on this forum.

Claiming that the developers (and I) "don't know how to properly test a patch" seems an insult to me.

Now, back on topic.

---

### Post by Perfect Storm on 2006-08-25
If they want to express themself, there's alot of related threads in the Café to this issue.
This thread purpose is to give tech support.


Thanks.

---

### Post by matthew on 2006-08-25
> **The Pinny Parlour said:**
> OMG You must be joking.   If people where affected by this then they have a right to express their dissapointment.  There are to many people scared of speaking their mind on this forum.
> **yaztromo said:**
> Correct. It caused the problems on some computers of a lot of people.
Several computers? Sorry but thats not really good enough testing in my eyes. Several computers to me means 4 or 5. An update like this needs testing on lots and lots of computers. Doesn't anyone know how to properly test a patch? Obviously you and the developer don't.
> **Artificial Intelligence said:**
> If they want to express themself, there's alot of related threads in the Café to this issue.
This thread purpose is to give tech support.


Thanks.

I am going to suggest everyone who wants to discuss the devs and what will be done to prevent this in the future [go to this thread]("http://www.ubuntuforums.org/showthread.php?t=243511") and read about recent discussions they are having. If you have further comment, then comment there and leave this thread for actual tech support. Thank you.

---

### Post by The Pinny Parlour on 2006-08-25
> **tseliot said:**
> Claiming that the developers (and I) "don't know how to properly test a patch" seems an insult to me.

Now, back on topic.

You personally tseliot have been a shining light to many here.  You are a credit to the forums.  I'm not directing ANY insult or other at you.

The following has been uploaded to [www.ubuntu.com](www.ubuntu.com). [http://www.ubuntu.com/UpgradeIssue](http://www.ubuntu.com/UpgradeIssue)   <-- Read for yourself.  In particular, 

<quote>
What has happened?

An update to the windowing system in Ubuntu was incorrectly released for Ubuntu 6.06 LTS. When applied to Ubuntu 6.06, the patch inadvertently breaks the desktop windowing environment on some systems. When we learned of the problem, the patch was immediately withdrawn. Mirrors have also been disabled to ensure that the faulty patch isn't available from them. For the limited number of users who received the patch in question, the corrective action above will resolve the issue.

We have launched an investigation and formal quality process review to understand exactly how this happened and what corrective actions to take. We will provide further information from this review when it is available. 
</quote>

So I will leave others to decide whether dev's know how to test a patch.  My guess is they do.  Anyway it's a MOOT Point.  I appreciate that there is work even done on ubuntu.


People WERE affected and have a right to have a say.

---

### Post by akak8ty on 2006-08-25
> **tseliot said:**
> The server might be down.

Try with:
```
sudo aptitude update
```

```
sudo aptitude install -s -V  xserver-xorg-core
```

and see which version the system would install (it's just a simulation)

if it's version 10.4 then you can install it:
```
sudo aptitude dist-upgrade
```

I had those as well my first couple tries. I figured so many ppl were trying to get into the server. On the 2rd try smooth sailing again. It worked better for me in safe mode. 
What I used to do with windoze updates was disable them...then wait and install until I could find out more about the update...because they put things on my machine I did not want once too often- OR it was buggy.
I do not like tracking cookies. That makes me....well NOT VERY HAPPY, to really minimize how I feel about it. The buildings are still standing :twisted:

---

### Post by frodon on 2006-08-25
> **The Pinny Parlour said:**
> People WERE affected and have a right to have a say.Of course but in a respectful way and in the correct thread.
This is a tech support thread, if you wish to give an opinion use a non-tech thread in ubuntu cafe.

Now please back on topic, other non-tech posts will be move in the ubuntu cafe, if you have an issue with forum governance please use the resolution center to fil a complaint.

---

### Post by jrjr on 2006-08-25
.

---

### Post by tseliot on 2006-08-25
> **jrjr said:**
> I just installed sysinfo and it tells me I have .3 installed eh? Or is this not what I should be looking at?
Where do you see that?

gcc-4.0.3 is a compiler and has nothing to do with the xserver

---

### Post by jrjr on 2006-08-25
.

---

### Post by ThirdWorld on 2006-08-25
I followed this thread and the official fix and neither worked for me. i even downgrade xorg, no luck.

I cant fix this crap, it said:

Failed to load module "glcore" (loader failed,7)
no devices detected

Can somebody please help me with this one? i have no clue, i cant restart or use xorg. Maybe i have to configure xorg?

---

### Post by ThirdWorld on 2006-08-25
i dont understand why Xorg is such a big problem, i mean why it cant load in a safe mode like legacy OSes like windows 95. Good Lords, that was back in 1995. i feel like im back in 1995 again looking at a black screen.

---

### Post by ThirdWorld on 2006-08-25
hey guys i know your busy figthing but can you take a brake and help me out please?

---

### Post by jrjr on 2006-08-25
.

---

### Post by akak8ty on 2006-08-25
I am growing concerned now about why suddenly my machine blinks out for a second (goes black) Its Never, **ever** happened before this.

---

### Post by ThirdWorld on 2006-08-25
> **jrjr said:**
> LOL

Looks like Matthew has his hands full with an "IT Expert"
:mrgreen: 

Did you reinstall your video drivers?

that will be a good idea, you mean reinstal the ati drivers?

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by matthew on 2006-08-25
> **ThirdWorld said:**
> hey guys i know your busy figthing but can you take a brake and help me out please?
I'm sorry. I didn't see your post. Let me see if I can help...the guru seems to be offline at the moment.
> **ThirdWorld said:**
> I followed this thread and the official fix and neither worked for me. i even downgrade xorg, no luck.

I cant fix this crap, it said:

Failed to load module "glcore" (loader failed,7)
no devices detected

Can somebody please help me with this one? i have no clue, i cant restart or use xorg. Maybe i have to configure xorg?
Let me confirm:
-your computer does boot, but only to a command line prompt.
-you can still log in, but only in a text interface.

If that is correct, then first make sure the correct version of the file is installed by doing this:
```
sudo aptitude update
sudo aptitude install -s -V  xserver-xorg-core
```If the correct version of the xserver-xorg-core file is listed (10.4) then```
sudo aptitude dist-upgrade
```
If it is not, then
```
 sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

Then reboot ```
sudo reboot
```

Now, if this isn't working for you please post the exact error messages you are receiving.

---

### Post by matthew on 2006-08-25
> **ThirdWorld said:**
> that will be a good idea, you mean reinstal the ati drivers?

```
sudo apt-get install xorg-driver-fglrx
```
This would be my next suggestion.

---

### Post by jrjr on 2006-08-25
.

---

### Post by matthew on 2006-08-25
> **jrjr said:**
> I just installed sysinfo and it tells me I have .3 installed eh? Or is this not what I should be looking at?
Do this and it will tell you what you need to know```
sudo aptitude show  xserver-xorg-core | grep Version
```

---

### Post by matthew on 2006-08-25
Alright. Again, I don't mind the topic nor the conversation, but this is not the place for it...let's leave this thread for tech support. I'm going to split all the other chatter from the last hour or so into a new thread in the cafe and I'll post a link in this post once that's accomplished.

EDIT: Here's the link to the new thread: [FONT=monospace][http://ubuntuforums.org/showthread.php?t=243561](http://ubuntuforums.org/showthread.php?t=243561) 
Please move the non-tech-support chatter there. Thank you.
[/FONT]

---

### Post by ThirdWorld on 2006-08-25
i cant make it work i have tried everything, all the tips of this thread. But nothing seems to work. it keep saying:

failed to load module "glcore" (loader failed,7) 

dont know what else to do.

---

### Post by kickblow on 2006-08-25
hi, i'm a linux n00b.

this xgl/compiz started me on a linux journey w/ ubuntu. it sucks so far!

i install ubuntu thru a live cd and immediately upgrade and install ati drivers for my tablet w/ ati x600. suffice to say, the 3d desktop works quite well! abeit few crashes, of which i can't seem to reproduce. i immediately tell myself i will never turn back to windows xp. but then more updates arrived and it included xserver-xorg-core! i chose to upgrade them all. what a fatale mistake that was!

i have spent many a sleepless night since that date trying to get a working compiz. with dozens of reinstalls from live cd and setting the graphic card and driver, i think i learnt a bit about the gdm, xorg, sudo, sh, generating ati driver packages. but i especially learnt not to update immediately. 

so the question i want to ask is: Is safe yet? Is it safe to update ubuntu 6.06 LTS?

The update now stands at close to 200MB w/ 163 file. the synaptic package manager list xserver-xorg-core to be version 1:1.0.2-0ubuntu10.4. (i saw a previous post did not specify the ".4" at the end.) so i am asking.

Should i update my fresh install with that xserver-xorg-core (include all other updates) and then go thru the troubles of update my ati graphics? 

When my xgl/compiz worked a few hours ago all the updates except xserver-xorg-core, i notice synaptic have a few more updates for opengl. and being stupid, i updated those and on restart my laptop failed. there were some errors on wacom iinputs. of course, i don't have wacom devices; i have FinePoint device use by gateway tablet. there were also firegl error, and locking error on the graphic card.

ugh. as i use to say to my linux friends, "linux is so troublesome." well, it still is. i am tired of writing and recounting this experience. been up too long for so-ooo long--sleepy. ZzzzZZZzzzzZZZz.....

---

### Post by ThirdWorld on 2006-08-25
well looks like, i would have to reinstall this thing. nobody seems to know whats going on with my pc. its so weird, why nobody is having this problem? it doesnt make any sense to me. i didnt touch anything i follow all the instructions, maybe is the fact that i upgrade from 5.10 to 6.06 lts.

---

### Post by jrjr on 2006-08-25
.

---

### Post by jrjr on 2006-08-25
.

---

### Post by tseliot on 2006-08-25
> **ThirdWorld said:**
> i cant make it work i have tried everything, all the tips of this thread. But nothing seems to work. it keep saying:

failed to load module "glcore" (loader failed,7) 

dont know what else to do.

> **jrjr said:**
> I did find this for you with a google search.. still looking. Sorry you are having so much trouble and only getting responses from a noob like me!

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33368](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33368)

If it's the same problem as the one reported on launchpad you should:

```
sudo nano -w /etc/X11/xorg.conf
```

get to the Section "Module"

and comment out (i.e. put a # before) Load "dri"

CTRL+X to exit (save the file)
```

then sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by Qvistgaard on 2006-08-25
> **matthew said:**
> This would be my next suggestion.

Has ATI's own drivers no interest?

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by ChuckNH on 2006-08-25
Okay...no editorial comment here.  Just need help, pls.  When I run sudo apt-get upgrade, this is the end of the resulting response:

No packages will be installed, upgraded, or removed.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.


So, what am I to make of that? Hoping for an answer, or I'm just going to have to reinstall, I guess.

---

### Post by givré on 2006-08-25
Chuck,
- are you sure you have the good version install, do that to be sure :
```
sudo aptitude show xserver-xorg-core |grep Version
```
- what is your graphic card?

---

### Post by ChuckNH on 2006-08-25
> **givré said:**
> Chuck,
- are you sure you have the good version install, do that to be sure :
```
sudo aptitude show xserver-xorg-core |grep Version
```
- what is your graphic card?

I actually don't seem to have the good version, and couldn't seem to downgrade out of 10.3. 

The other (possible) complication is that I have an ATI Radeon graphic card. It's the 128 All-in-wonder AGP.

Thanks for quick response.

---

### Post by givré on 2006-08-25
> **fakie_flip said:**
> **** this stupid nigger. he ****** up my computer. he put the bad software in the repos.

Package: xserver-xorg-core
Maintainer: Fabio M. Di Nitto <fabbione@ubuntu.com>

I got his email from apt-cache show xserver-xorg-core
You are stupid for two reason:
- because i don't know why we should point the finger on one man if their is a problem. Mistake is human. What we should change is the system to avoid human mistake (and that's what they are doing at this time of speaking.
- because the maintener field contain the first creator of the package, and actually it's no more Fabio the maintener. On top this field caintain in the majority of the case (like for the firefox package) debian dev, and i don't know why we should blame debian dev for an ubuntu mistake.

And stop bashing please, how many time we'll have to say that.
Thanks

---

### Post by givré on 2006-08-25
> **ChuckNH said:**
> I actually don't seem to have the good version, and couldn't seem to downgrade out of 10.3. 
Thanks for quick response.
- be sure to have that in your sources.list :
```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
```
- do you have some error when you do :
```
sudo apt-get update
```
- are you connected to internet?

---

### Post by ba5e on 2006-08-25
This is an absolute farce for Canonical and I am shocked that this was allowed to happen.

Of course human error is inevitable, but in any case it is not acceptable in a production environment.

On a lighter note I suppose this is the very first serious error to hit Ubuntu, and may it be the last.

---

### Post by ba5e on 2006-08-25
> **ChuckNH said:**
> Okay...no editorial comment here.  Just need help, pls.  When I run sudo apt-get upgrade, this is the end of the resulting response:

No packages will be installed, upgraded, or removed.
Need to get 0B of archives. After unpacking 0B will be used.
Would download/install/remove packages.


So, what am I to make of that? Hoping for an answer, or I'm just going to have to reinstall, I guess.

thanks for your query, you should be running: 
```
sudo apt-get update
```

followed by

```
sudo apt-get dist-upgrade
```

Hope this solves your problem :)

---

### Post by vigi1 on 2006-08-25
> **thojoh said:**
> thanks for the support. It was rather scary for a moment. I downgraded and rebooted and all is well.

Do I understand correctly that by now I can trust again the message that tells me to upgrade and just do it? (Maybe for my own piece of mind I might wait another day).  :)

And for those in this forum who complained: I know what you feel as problems on my computer get to me strongly as well (especially if there is work to be done). But I remember having loads of those moments when working under Windows as well. So I really feel well supported by the ubuntut community and for the rest I think it is good to face the facts:  Computers tend to give you problems every now and again (because they run on human software). 

Thanks again for your unfaltering support and trying to answer peoples' questions, tseliot!



I agree totally-I have been using ubuntu for some six months and it has failed twice. Both times due to upgrades, but lets put this into context.
If I were using windows, I would have to reload my system and possibly lose some data. Using unbuntu with xp dual boot, I can get some expert advice from this forum, fix the xserver and my ubuntu system is exactly as I customized it. 

 Thank you very much for you fix.        tseliot
It worked perfectly for me.

---

### Post by vigi1 on 2006-08-25
When you reinstall-be sure to put /home on a separate partition and you will not lose any data again.
Isn't this what linux is all about?

---

### Post by Eleka on 2006-08-25
Hello guys!

I'm tring to return to me status before "the crash" and I can't.

I have restored my Xorg and it works, and then my Nvidia driver ... but now Xgl don't works. I don't know if it's problem of the new package of xserver-xorg-core, the options that I passed to Xgl to run ... but I can't get it working more :( And before it works preety good! 

Is somebody in the same situation?

EDIT: I resolve that mistake, thanks!

---

### Post by NamShubCMX on 2006-08-25
oliverb: you can mount the broken partition from the liveCD (rw mode), chroot to it and then update/upgrade, but that's not really the quick visual solution you were talking about I guess...

It wouldn't be an idea to set up the LiveCD so that it recognizes an existing Ubuntu partition (or any other linux partition) and automatically mount/chroot/set X so it can run apps from this partition...

---

### Post by The Pinny Parlour on 2006-08-25
I'm finally back up and running after a REINSTALL.   :-#

---

### Post by LateNighter on 2006-08-25
\\:D/ Thanks Guys for the quick fix to the XServer.

 I did a reinstall, got it up and running on the Old One they put back in till they got it fixed.

 Got all my stuff back on my HD. 65gig of 80gig.

 Alomost time for a bigger HD:-k 

 Next day they released the New Version "FIX", Held my Breath and it booted just fine, with no crash Now for 2 days.\\:D/ 

 I'm one Happy Camper now, But I was never mad to begin with...

 This kinda Stuff Happens....:D :cool:

---

### Post by mozza314 on 2006-08-26
*sigh*, I'm fairly certain this is what's happened to my computer... I spent quite a bit of time backing up and re-installing etc. because I had no idea what to do.

Don't they test the updates before putting them on the server??

---

### Post by matthew on 2006-08-26
> **mozza314 said:**
> *sigh*, I'm fairly certain this is what's happened to my computer... I spent quite a bit of time backing up and re-installing etc. because I had no idea what to do.

Don't they test the updates before putting them on the server??For those asking/curious about the devs, the process of update testing, and if anything is going to change after this mess, please read this thread: [http://www.ubuntuforums.org/showthread.php?t=243511](http://www.ubuntuforums.org/showthread.php?t=243511)

---

### Post by baldwin14 on 2006-08-26
It seems that the so called far right have noticed the problems been experienced by RedWare, and not just the Ubuntu distro.

[http://www.solargeneral.com](http://www.solargeneral.com)
[http://www.skrewdriver.net](http://www.skrewdriver.net)

Universal systems whether software and/or politically based are prone to instability, but we all live and learn.


Dave.

14/88

---

### Post by baldwin14 on 2006-08-26
By the way, Ubuntu is still a good operating system, I am merely highlighting here the known fact that universal systems, whether software based or otherwise are prone to instability. I believe the scientific reason behind this has something to do with the entropics of information based systems, that there needs to be a lot more energy spent on maintaining a universal system then one dedicated to a sub-group (or many systems for many sub-groups). The higher the energy flow through a system (whatever system adopted - National Socialist ones are equally prone to entropics of course, as observed when the Third Reich unfortunately ran out of oil reserves in Germany during the 1930s), the higher the resultant entropy, and decay. This leads to instability. Ubuntu suffers from component dependency, and is not the only OpenSource software to have this problem.

It is unfair to target Ubuntu Linux in this regard.

It looks like Ubuntu is past the worst of this CURRENT episode, and hopefully those behind it will live and learn, without resorting to more energy and hence more entropic consequences....compared to Windoze, Ubuntu is on another planet.. 


Best Wishes,

14/88


Dave Baldwin

> **baldwin14 said:**
> It seems that the so called far right have noticed the problems been experienced by RedWare, and not just the Ubuntu distro.

[http://www.solargeneral.com](http://www.solargeneral.com)
[http://www.skrewdriver.net](http://www.skrewdriver.net)

Universal systems whether software and/or politically based are prone to instability, but we all live and learn.


Dave.

14/88

---

### Post by reuben on 2006-08-26
Well for me I couldn't even get to the command line. I'm on kubuntu/nvidia - the nvidia splash would load and then the system would hard freeze.

(Probably an easier way, but...)

I booted using the live cd, mounted my system partition:

mkdir /tmp/hda7
sudo mount /dev/hda7 /tmp/hda7

...and then went through all of the /etc/rc.* directories moving S99kdm out of the way -- 

cd /tmp/hda7/etc/rc2.d
sudo mv S99kdm __S99kdm

(etc) to prevent kdm from loading on boot.

Then I rebooted, got to the cli, and used apt to downgrade.

---

### Post by tseliot on 2006-08-26
> **reuben said:**
> Well for me I couldn't even get to the command line. I'm on kubuntu/nvidia - the nvidia splash would load and then the system would hard freeze.

(Probably an easier way, but...)

I booted using the live cd, mounted my system partition:

mkdir /tmp/hda7
sudo mount /dev/hda7 /tmp/hda7

...and then went through all of the /etc/rc.* directories moving S99kdm out of the way -- 

cd /tmp/hda7/etc/rc2.d
sudo mv S99kdm __S99kdm

(etc) to prevent kdm from loading on boot.

Then I rebooted, got to the cli, and used apt to downgrade.
You could have booted in Recovery Mode so that you wouldn't have had the xserver or splash.

---

### Post by Dan Ballantine on 2006-08-27
I did the update and my monitor said the frequency was out of range? so I could not get an x session.
I reconfigured the x server: sudo dpkg-reconfigure -phigh xserver-org cannot be sure of the syntax, but it is posted.
I did use automatix to reinstall the nvidia drivers.

---

### Post by baldwin14 on 2006-08-27
I don't know about anyone else here, but I think Tseliot should be praised for the cool and professional way he has handled this near nightmare situation, and should not be knocked down by hot heads and irrelevant emotional outbursts he has experienced. Compared to the near zero response you get from Microsoft support for their Windoze packages (and do they have problems, things get so bad there that they discontinue product support altogether, imagine if car makers did the same thing).

Is there anyway we can show our support via a donation page? 

I feel slightly guilty mentioning the negatives of universal systems (I believe that on stability grounds dedicated targetted systems are better), it's kind of like rubbing salt into a wound. It isn't Ubuntu's fault, accept in the regards that it is part of the fashionable cult of universalism doing the rounds at present. it is no different than someone falling off a chair and then blaming gravity for their misfortune. 

FULL MARKS FOR SUPPORT TSELIOT!

14/88

Dave Baldwin, 

Note: I use Ubuntu linux myself, which often gets chuckles when comrades/friends come around, but in my view if the Soviet style thought police turn up and take my pc away for investigation, it makes a great cover for myself, especially the logo :-)

---

### Post by bflat on 2006-08-27
The last upgrade did not affect my Xserver totally, only compiz starting by default proposed me a blank (litterally white) screen. Metacity works better. It does not let me switch to terminal mode tough.

Hacking for a quick recover I noticed that compiz complained not having a valid 0:0 server, unfortunately I did not cut & paste the message. (Eventually I can reproduce the message).

Now, for my system the matacity+mesa drivers is less resource consuming and works very well. So maybe it could be worth to try to stick to this solution. Some sort of advice would be welcome for further upgrades (or in order to stop upgrading if ain't no use).

Sick from angries towards a totally free system and a lot of good work going on. It's right to figure out 'when they will have real troubles how they will act?'
_________

Infos for the eventually interested

Card: ATI Radeon RV100 QY [Radeon 7000/VE]

The update comprised new mesa drivers and the Xorg server:

$ sudo aptitude show  xserver-xorg-core | grep Version
Password:
Version: 1:1.0.2-0ubuntu10.4

this is the string about Open Gl

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

some strings from my working from Xorg.conf


Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection



Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"radeon"
	Option "XAANoOffscreenPixmaps"
	Option		"AGPMode"	"4"
	Option     "BackingStore"     "enable"
	Option     "EnablePageFlip"   "true"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"JT178x4"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"JT178x4"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400"

"640x480"
Option     "BackingStore"     "enable"
Option     "EnablePageFlip"   "true"
	EndSubSection
EndSection

Section "ServerLayout"
	Option "AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by Graciosa on 2006-08-27
=D> =D> =D> Hey thanks so much sda 5150 ... your solution saved me!! Took me long enough to sift through 70 odd pages of random comments ... you are a :KS 

> **sda5150 said:**
> For those that ran dpkg-reconfigure xserver-xorg (reconfigured xserver) and are now having issues. (IanVaughan and koolguynet)

I would try rolling back to your previous version of xorg.conf

steps:

> cd /etc/X11
> sudo cp xorg.conf xorg.conf.old
> sudo cp xorg.conf.2006*xxxxxxx* xorg.conf

Enter Y to overwrite.

> sudo shutdown -r now

This should roll your xserver config back to what it was before the problem.

---

### Post by jkelly@trillian on 2006-08-27
1. Update breaks linux side of my dual-boot laptop. 
2. I read the xserver diagnostics but can't find anything I can really use, so I use the Windoze side for a week.
3. I google "ubuntu xserver problem" and get complete instructions for fixing the problem.
4. I fix the problem. I don't even have to think about it -- just follow the instructions.

Not so bad! And now I see I could have got it fixed in one day, not seven, if I'd checked in earlier.

No complaints here!

---

### Post by LateNighter on 2006-08-27
I know everyone's gonna SHOOT me for this...

But I've gotta say this...:eek: 

Let this be a Leason to everyone...

Back Up at least once a day, then when STUFF like this happens..

A Simple reinstall and some Copying solves it all...

:tongue:

UNTIL they/we can find a Solution to the MESS...;)

---

### Post by Anarchy99 on 2006-08-28
So when my xserver got broken, I think I found an alternate way to fix it.  I'd try to start GDM and it would direct to xorg.conf and xorg.conf would bring back an error in libGLcore.so

Now, my situation is unique since I'm running one of those 1440x780 widescreen Nvidia Go5200 laptops, and my xorg.conf is a creation of all my own (I'd be happy to post it if anyone is having the same problems I had getting full resolution on Unbuntu).

The new xserver installs nvidia-glx, which conflicts with my previous nvidia-settings package that ran all of my graphics stuff.  I figure out that by going command line into the package manager, I could just remove nvidia-settings and then start the Xserver no problem. Has anyone else had this expirence?

---

### Post by tseliot on 2006-08-28
> **Anarchy99 said:**
> The new xserver installs nvidia-glx, which conflicts with my previous nvidia-settings package that ran all of my graphics stuff.  I figure out that by going command line into the package manager, I could just remove nvidia-settings and then start the Xserver no problem. Has anyone else had this expirence?
nvidia-settings is already included in nvidia-glx therefore nvidia-settings must not be installed (unless you use the legacy driver)

---

### Post by mycelo on 2006-08-28
For me it wasn't necessary to reinstall NVidia proprietary drivers at all. And this is how things should be. Patches should do everything automagically, unless it explicitly and loudly warns the user *before* installing, explaining meticulously what the user is supposed to do. Otherwise we would be patching the patch.

mycelo

---

### Post by roee88 on 2006-08-28
I have updated ubuntu to 6.06 TODAY, and still got the same message as described here and on the Ubuntu HomePage.
Cheking the Xserver version shows 10.4 and there following the instructions you gave brings up a message saying no update needed.

So I got the lateset Xserver. EVERYTHING is up-to-date. But I still can't run Ubuntu.
Any idea? ](*,) 

_________________
[IMG]http://www.ubuntu.com/FixForUpgradeIssue?action=AttachFile&do=get&target=failedb.png[/IMG]

---

### Post by tseliot on 2006-08-28
> **roee88 said:**
> I have updated ubuntu to 6.06 TODAY, and still got the same message as described here and on the Ubuntu HomePage.
Cheking the Xserver version shows 10.4 and there following the instructions you gave brings up a message saying no update needed.

So I got the lateset Xserver. EVERYTHING is up-to-date. But I still can't run Ubuntu.
Any idea? ](*,) 

_________________


boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by roee88 on 2006-08-28
Many thanks tseliot :)

---

### Post by ikester8 on 2006-08-28
Thank you, the new xserver-xorg-core package works perfectly. Just a quick reinstall of the nvidia drivers and I'm good to go!

---

### Post by ShadowRage on 2006-08-29
technically, you shouldnt have to reboot for anything except major kernel changes. I've found with any changes to X, logging out and zapping the server does the trick.

alt + ctrl + backspace.

also, another thing I'll throw in: mouse pointer stuck? fix for that. 
ctrl + shift + numlock and the numeric keypad keys (the keys with arrows) will move the mouse around. sometimes the resolution needs to be fixed to get the mouse working, perhaps you need to click a terminal or click an icon to run a program to just exit it, but it helps.

also, if your Xserver failed to start and you're trying to get it to run again, no need for a reboot. this isnt windows ;)

```
sudo killall -HUP gdm
```

do that after fixing your xserver's config when it failed to load, voila. GDM will restart (and thus start X)

---

### Post by ggregoro on 2006-08-29
hey man, do what i did.  put a fresh copy of XP SP2 back on my thinkpad and everything is working just fine.

linux (Slackware) might make a nice server, but this stuff is not ready for the desktop.  what a joke.

---

### Post by Stinger on 2006-08-29
> **ggregoro said:**
> hey man, do what i did.  put a fresh copy of XP SP2 back on my thinkpad and everything is working just fine.

linux (Slackware) might make a nice server, but this stuff is not ready for the desktop.  what a joke.

Sorry ggregoro , I have to disagree on that.
Windows and the XP version in particular has always brought me more trouble Than Ubuntu ever did , not to mention the license issues and all the extra software you'll have to pay for  to get to the same level of productivity as Ubuntu.

---

### Post by Statik on 2006-08-31
Here's something weird . . . and I think its related. I'm having trouble with firefox on certain web pages now. I never did before. When I get to that page the system either freezes or xserver restarts and I have to login again. Its not a full reboot tho.

It could be an extension interaction, but I didn't have trouble with these pages until the upgrade to 10.4.

Any thoughts tseliot?

Statik

---

### Post by tseliot on 2006-08-31
> **Statik said:**
> Here's something weird . . . and I think its related. I'm having trouble with firefox on certain web pages now. I never did before. When I get to that page the system either freezes or xserver restarts and I have to login again. Its not a full reboot tho.

It could be an extension interaction, but I didn't have trouble with these pages until the upgrade to 10.4.

Any thoughts tseliot?

Statik

It might be related to the openGL rather than on firefox.

Try reinstalling the driver for your graphic card (BTW I had the same problem in the past)

---

### Post by David Oxland on 2006-08-31
I've got xserver going again, I think.  
The GUI login proceeds OK but just after that I go to a brown screen and freeze. The cursor is alive but that's it.  Seems to hang there.

Can anyone help
Thanks

---

### Post by tseliot on 2006-08-31
> **David Oxland said:**
> I've got xserver going again, I think.  
The GUI login proceeds OK but just after that I go to a brown screen and freeze. The cursor is alive but that's it.  Seems to hang there.

Can anyone help
Thanks
What is the model of your graphic card?

---

### Post by Adler on 2006-08-31
tseliot,

Thanks again for the install script. Everything works geat after the mess...

Adler

---

### Post by ga@aggies.com on 2006-08-31
I have tried updating with the xxx10.4 xserver-xorg-core and still no luck when running startx on my HP Kayak?

LiveCD still boots?

I am at the point at reinstalling off the CD and wiping my hard drive?  

Any advice?

---

### Post by tseliot on 2006-08-31
> **ga@aggies.com said:**
> I have tried updating with the xxx10.4 xserver-xorg-core and still no luck when running startx on my HP Kayak?

LiveCD still boots?

I am at the point at reinstalling off the CD and wiping my hard drive?  

Any advice?

type:
sudo aptitude update && sudo aptitude dist-upgrade

then
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

then:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by imperiosus on 2006-08-31
Help! :(

when I attempt to have X run with GLX and hardware support(nvidia driver), it gives the error talked about here... no screens found.  My video card is a PCI Express Geforce Go 7600.  I checked my version of xorg-core and I SUPPOSEDLY have the version that corrects the mistake(10.4), it still however does not work.  Here is the xorg output...

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux imperio-laptop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 31 15:55:51 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 103c,30a5 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 103c,30a5 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 103c,30a5 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 103c,30a5 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 103c,30a5 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 103c,30a5 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 103c,30a5 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 103c,30a5 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0398 card 103c,30a5 rev a1 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 8086,4222 card 103c,135b rev 02 class 02,80,00 hdr 00
(II) PCI: 08:06:0: chip 104c,8039 card 3400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 08:06:1: chip 104c,803a card 103c,30a5 rev 00 class 0c,00,10 hdr 80
(II) PCI: 08:06:2: chip 104c,803b card 103c,30a5 rev 00 class 01,80,00 hdr 80
(II) PCI: 08:06:3: chip 104c,803c card 103c,30a5 rev 00 class 08,05,00 hdr 80
(II) PCI: 08:08:0: chip 8086,1092 card 103c,30a5 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:28:2), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
        [0] -1  0       0x52000000 - 0x520fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,12), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 8 I/O range:
        [0] -1  0       0x00003000 - 0x000030ff (0x100) IX[B]
        [1] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [2] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
        [3] -1  0       0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
        [0] -1  0       0xd2000000 - 0xd20fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
        [0] -1  0       0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:6:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
        [0] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [1] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
        [0] -1  0       0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0398) rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24, I/O @ 0x2000/7
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xd2006000 - 0xd2006fff (0x1000) MX[B]
        [1] -1  0       0xd2007800 - 0xd20078ff (0x100) MX[B]
        [2] -1  0       0xd2005000 - 0xd2005fff (0x1000) MX[B]
        [3] -1  0       0xd2000000 - 0xd2003fff (0x4000) MX[B]
        [4] -1  0       0xd2007000 - 0xd20077ff (0x800) MX[B]
        [5] -1  0       0x52000000 - 0x52000fff (0x1000) MX[B]
        [6] -1  0       0xd2404000 - 0xd24043ff (0x400) MX[B]
        [7] -1  0       0xd2400000 - 0xd2403fff (0x4000) MX[B]
        [8] -1  0       0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
        [9] -1  0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [10] -1 0       0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x00003000 - 0x0000303f (0x40) IX[B]
        [12] -1 0       0x000018c0 - 0x000018df (0x20) IX[B]
        [13] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [14] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [15] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [16] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [17] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [18] -1 0       0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xd2006000 - 0xd2006fff (0x1000) MX[B]
        [1] -1  0       0xd2007800 - 0xd20078ff (0x100) MX[B]
        [2] -1  0       0xd2005000 - 0xd2005fff (0x1000) MX[B]
        [3] -1  0       0xd2000000 - 0xd2003fff (0x4000) MX[B]
        [4] -1  0       0xd2007000 - 0xd20077ff (0x800) MX[B]
        [5] -1  0       0x52000000 - 0x52000fff (0x1000) MX[B]
        [6] -1  0       0xd2404000 - 0xd24043ff (0x400) MX[B]
        [7] -1  0       0xd2400000 - 0xd2403fff (0x4000) MX[B]
        [8] -1  0       0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
        [9] -1  0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [10] -1 0       0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x00003000 - 0x0000303f (0x40) IX[B]
        [12] -1 0       0x000018c0 - 0x000018df (0x20) IX[B]
        [13] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [14] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [15] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [16] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [17] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [18] -1 0       0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd2006000 - 0xd2006fff (0x1000) MX[B]
        [5] -1  0       0xd2007800 - 0xd20078ff (0x100) MX[B]
        [6] -1  0       0xd2005000 - 0xd2005fff (0x1000) MX[B]
        [7] -1  0       0xd2000000 - 0xd2003fff (0x4000) MX[B]
        [8] -1  0       0xd2007000 - 0xd20077ff (0x800) MX[B]
        [9] -1  0       0x52000000 - 0x52000fff (0x1000) MX[B]
        [10] -1 0       0xd2404000 - 0xd24043ff (0x400) MX[B]
        [11] -1 0       0xd2400000 - 0xd2403fff (0x4000) MX[B]
        [12] -1 0       0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x00003000 - 0x0000303f (0x40) IX[B]
        [18] -1 0       0x000018c0 - 0x000018df (0x20) IX[B]
        [19] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [20] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [21] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [22] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [23] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [24] -1 0       0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by David Oxland on 2006-08-31
I've got xserver going again, I think.
The GUI login proceeds OK but just after that I go to a brown screen and freeze. The cursor is alive but that's it. Seems to hang there.
> **tseliot said:**
> What is the model of your graphic card?
My card is a GeForce 6800 fitted to a Dell Inspiron 9300

---

### Post by tseliot on 2006-09-01
> **imperiosus said:**
> Help! :(

when I attempt to have X run with GLX and hardware support(nvidia driver), it gives the error talked about here... no screens found.  My video card is a PCI Express Geforce Go 7600.  I checked my version of xorg-core and I SUPPOSEDLY have the version that corrects the mistake(10.4), it still however does not work.  Here is the xorg output...
Please post the output of this command:
```
lspci -n | grep 300
```

---

### Post by leemckusic on 2006-09-03
As previous poster said : I agree there still is a problem with the xserver-xorg-core package.

   10.4 does not work with my 700 mHz Athlon box with a Matrox Mg400 video card.

    The error doesn't really look like an X problem.

    .. because the system does throw up a Sign-In screen. Right after signin crashes, after the TTY1 login name return-key is pressed  I see errors like "configuration error ... "QUOTAS_ENAB" which suggests a failure with gdm configration.

     One of the problems with this "bug" is I couldn't recognize an error in the  /var/log/Xorg logfiles.

     I wish there was a place in the Wiki to post a high quality guide page with reminders for all the useful apt-get commands. I have been running so many Linuxes for so long I am beginning to forget some of these commands...

     I upgraded from 5.10 Breezy to 6.06.1 LTS on Friday night August 31st and I ran into the noted failure of the graphic display to stop after filling out the username and password fields.

This works for me: downgrading xserver to "10" and I played with the x server configuration, specifically choice of video card driver.

If not posted earlier, the way to change the video driver used by your X installation is:

[SIZE="5"]sudo dpkg-reconfigure xserver-xorg[/SIZE] 

It helps to make trials, make notes and change only one thing at a time. The configuration script is pretty good at detecting hardware

---

### Post by tseliot on 2006-09-03
> **leemckusic said:**
> As previous poster said : I agree there still is a problem with the xserver-xorg-core package.

   10.4 does not work with my 700 mHz Athlon box with a Matrox Mg400 video card.

    The error doesn't really look like an X problem.

    .. because the system does throw up a Sign-In screen. Right after signin crashes, after the TTY1 login name return-key is pressed  I see errors like "configuration error ... "QUOTAS_ENAB" which suggests a failure with gdm configration.

     One of the problems with this "bug" is I couldn't recognize an error in the  /var/log/Xorg logfiles.

     I wish there was a place in the Wiki to post a high quality guide page with reminders for all the useful apt-get commands. I have been running so many Linuxes for so long I am beginning to forget some of these commands...

     I upgraded from 5.10 Breezy to 6.06.1 LTS on Friday night August 31st and I ran into the noted failure of the graphic display to stop after filling out the username and password fields.

This works for me: downgrading xserver to "10" and I played with the x server configuration, specifically choice of video card driver.

If not posted earlier, the way to change the video driver used by your X installation is:

[SIZE="5"]sudo dpkg-reconfigure xserver-xorg[/SIZE] 

It helps to make trials, make notes and change only one thing at a time. The configuration script is pretty good at detecting hardware

I think you should file a bug on launchpad:
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Let the developers know that there is a problem and they will fix it

---

### Post by ispmarin on 2006-09-03
Still problems... not updating any of my work machines, not until the release become "stable" again. Sighf.

---

### Post by tseliot on 2006-09-04
> **ispmarin said:**
> Still problems... not updating any of my work machines, not until the release become "stable" again. Sighf.

It works fine here

---

### Post by ispmarin on 2006-09-04
Lucky you. Not yet fully convinced about 10.4 on production machines.

---

### Post by tseliot on 2006-09-04
> **ispmarin said:**
> Lucky you. Not yet fully convinced about 10.4 on production machines.

If you don't trust 10.4 you can pinpoint the version you're using and update the rest of the system

---

### Post by bPawn on 2006-09-04
There are a lot pages to read so I will just ask.

I made a clean install of ubuntu server and installed all the updates.
My kernel is the latest (2.6.15-26-386) and the kubuntu-desktop. Every thing works fine, and my xserver version is 1.04. By the time I install nvidia-glx , do a dpkg-reconfigure xserver-xorg and set the driver to nvidia it wont start kde, it frezees with showing the Kubuntu's ugly progress bar. I have "NVIDIA Corporation NV43 [GeForce 6600]" in my system. Now i use the 'nv' module and it works with poor performance.

I tried easyubuntu to install the nvidia driver but no lack.

Any ideas or more info to give you?

I attach my working xorg.conf

---

### Post by Princey on 2006-09-04
10.3 broke my xserver and I downgraded. Upgraded this morning to 10.4 and no problems whatsoever. It works as far as I can say.

---

### Post by bPawn on 2006-09-04
I mean, I tried to install nvdia-glx at 1.04 version. nvdia-glx was not already installed in my system as Princey's. I guess this is the problem(?)

---

### Post by tseliot on 2006-09-04
> **bPawn said:**
> There are a lot pages to read so I will just ask.

I made a clean install of ubuntu server and installed all the updates.
My kernel is the latest (2.6.15-26-386) and the kubuntu-desktop. Every thing works fine, and my xserver version is 1.04. By the time I install nvidia-glx , do a dpkg-reconfigure xserver-xorg and set the driver to nvidia it wont start kde, it frezees with showing the Kubuntu's ugly progress bar. I have "NVIDIA Corporation NV43 [GeForce 6600]" in my system. Now i use the 'nv' module and it works with poor performance.

I tried easyubuntu to install the nvidia driver but no lack.

Any ideas or more info to give you?

I attach my working xorg.conf
Honestly I doubt that your problem has to do with the one which this thread is about. It looks like a problem with the driver.

Try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by bPawn on 2006-09-04
Hmmm, the xorg log says differnet things. I disabled the Kubuntu loading screen from GRUB and I realised that x dont even start. I attach the log.
Still looking for a solution. My symptoms are not like the PROBLEMS SECTION 4.

---

### Post by tseliot on 2006-09-04
> **bPawn said:**
> Hmmm, the xorg log says differnet things. I disabled the Kubuntu loading screen from GRUB and I realised that x dont even start. I attach the log.
Still looking for a solution. My symptoms are not like the PROBLEMS SECTION 4.

Apart from the symptoms, did you try point 4?

---

### Post by bPawn on 2006-09-04
will do it asap

---

### Post by bPawn on 2006-09-04
Same thing. 

I have tried also to install the official drivers and it complained something about nvidia,ko (If I remember right)

---

### Post by bPawn on 2006-09-04
Before the clean installation I had successfully installed the drivers:
nvidia-glx and the official, just for the record

---

### Post by tseliot on 2006-09-04
> **bPawn said:**
> Before the clean installation I had successfully installed the drivers:
nvidia-glx and the official, just for the record
Try Envy:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by bPawn on 2006-09-04
Hmm besides the realy easy installation -> no result
take a look at the log

---

### Post by tseliot on 2006-09-04
> **bPawn said:**
> Hmm besides the realy easy installation -> no result
take a look at the log
Thanks for posting the log. I guess I've found where the problem is.

Why do you use kernel 2.6.15-26-server ?

Install a kernel for the desktop, such as linux-386 or linux-686 or linux-k7 (as I suggest in my Method 1).

After that you should reboot and try installing the driver again.

---

### Post by bPawn on 2006-09-04
?! This kernel is the default for the ubuntu-LAMP-server installation. Anyway I'll give it a try and keep you posted. Thanks for the interest

---

### Post by bPawn on 2006-09-04
HOORAY! everything went smooothly.

Weird anyone who uses the server kernel has the same problem?

anyway everything is ok now. Thanx for the brainstorming.

---

### Post by crashtestyyz on 2006-09-05
I have:
AMD64, ASUS motherboard, ATI X1600Pro, and a pair of SATA drives.

Regular Debian won't even find the hard drives from a boot disk, so i went with Ubuntu.

I just did a fresh install, did the update.  Version of xorg-server was 10.4.
Installed the xorg-driver-fglrx.

BlackScreen of doom.  reading through many of the posts here, downgrading was supposed to fix (along with de-installing and re-installing the ATI driver)

No avail.  I'm stuck here with a dead ubuntu system.

I think at this point I've burned about 60 hours with ubuntu, where  I would have expected a debian system to take 2 (given that I could make it install of course)
Oh yes, I'm pissed.  I've been using Linux (debian) for years, and have never encountered anything even remotely like this.
okay.
 /rant

What's the fix for this problem from a fresh install, or is it not supposed to happen from a fresh install? :evil:

---

### Post by tseliot on 2006-09-06
> **crashtestyyz said:**
> I have:
AMD64, ASUS motherboard, ATI X1600Pro, and a pair of SATA drives.

Regular Debian won't even find the hard drives from a boot disk, so i went with Ubuntu.

I just did a fresh install, did the update.  Version of xorg-server was 10.4.
Installed the xorg-driver-fglrx.

BlackScreen of doom.  reading through many of the posts here, downgrading was supposed to fix (along with de-installing and re-installing the ATI driver)

No avail.  I'm stuck here with a dead ubuntu system.

I think at this point I've burned about 60 hours with ubuntu, where  I would have expected a debian system to take 2 (given that I could make it install of course)
Oh yes, I'm pissed.  I've been using Linux (debian) for years, and have never encountered anything even remotely like this.
okay.
 /rant

What's the fix for this problem from a fresh install, or is it not supposed to happen from a fresh install? :evil:
Uninstall the fglrx driver and set your xorg.conf to "ati" or "vesa" in the Section Device.

It might be related to a failure of the fglrx driver rather than of the xserver itself.

---

### Post by DalHelpdesk on 2006-09-06
Hi,

I am new to this ubuntu and have come across this Xserver issue. I read the threads and did what was said there but in my case nothing is working. 
Like when i do sudo apt-get upgrade it runs for a while and then gives me this error 

"Reading database ... dpkg: error processing /var/chache/apt/archives/libmagick9_6%3a6.2.3.4.5-0.6ubuntu0.2_i386.deb  (--unpack):
files list file for package 'libxdmcp-dev' conatains empty filname
Errors were encountered while processing:
/var/cache/apt/archives/libmagick9_6%3a6.2.3.4.5-0.6ubuntu0.2_i386.deb
processing was halted bacause there were too many errors.
E:Sub-process /usr/bin/dpkg returned an error code (1)"

Sorry for putting the whole error message hear, but thought it might help. 

Any help,tips regarding this will be appreciated.

Thanks,

---

### Post by tseliot on 2006-09-06
> **DalHelpdesk said:**
> Hi,

I am new to this ubuntu and have come across this Xserver issue. I read the threads and did what was said there but in my case nothing is working. 
Like when i do sudo apt-get upgrade it runs for a while and then gives me this error 

"Reading database ... dpkg: error processing /var/chache/apt/archives/libmagick9_6%3a6.2.3.4.5-0.6ubuntu0.2_i386.deb  (--unpack):
files list file for package 'libxdmcp-dev' conatains empty filname
Errors were encountered while processing:
/var/cache/apt/archives/libmagick9_6%3a6.2.3.4.5-0.6ubuntu0.2_i386.deb
processing was halted bacause there were too many errors.
E:Sub-process /usr/bin/dpkg returned an error code (1)"

Sorry for putting the whole error message hear, but thought it might help. 

Any help,tips regarding this will be appreciated.

Thanks,
Try with this command:
```
sudo apt-get update
```

```
sudo apt-get install -f
```

P.S. your problem is not caused by the xserver package

---

### Post by iyre on 2006-09-06
tseliot,

I have a similar problem to crashtest, however I have reproduced it on 4 PC's now.

The issue isnt the updated driver, its the ASUS motherboard. Installing a base installation from the live or alternate CD should use a non broken xorg server (1.02 IIRC, right?).

The mainboard I am using is an ASUS P5VDC-MX. I have tried it with the onboard video, an NVIDIA 6200, a tnt2, ati RADEON and various other AGP cards but the error is always "no screens found". NOTE: this is on the initial install, not after any update.

All these PC's have the same mainboard, however I am currently using the same default installation on a gigbyte mainboard with an nvidia 6200 mainboard.

It seems to me that the kernel is having trouble scanning the hardware. I have tried all manner of means of making it work, including copying the xorg config from this machine (which is identical in every way including the monitor and video card except for the mainboard).

Any ideas?

---

### Post by Iwan_from_Belgium on 2006-09-06
ROFLOL and another ROFLOL...

My first Linux install without any knowledge of Linux at all, and i get this.

Very exciting, i will try this solution right now, because...i updated my 4.10 version directly after i installed it. I'll post again to tell if it helped...

Greetz,
    Iwan

---

### Post by tseliot on 2006-09-06
> **iyre said:**
> tseliot,

I have a similar problem to crashtest, however I have reproduced it on 4 PC's now.

The issue isnt the updated driver, its the ASUS motherboard. Installing a base installation from the live or alternate CD should use a non broken xorg server (1.02 IIRC, right?).

The mainboard I am using is an ASUS P5VDC-MX. I have tried it with the onboard video, an NVIDIA 6200, a tnt2, ati RADEON and various other AGP cards but the error is always "no screens found". NOTE: this is on the initial install, not after any update.

All these PC's have the same mainboard, however I am currently using the same default installation on a gigbyte mainboard with an nvidia 6200 mainboard.

It seems to me that the kernel is having trouble scanning the hardware. I have tried all manner of means of making it work, including copying the xorg config from this machine (which is identical in every way including the monitor and video card except for the mainboard).

Any ideas?
Did you try flashing the bios?

---

### Post by iyre on 2006-09-06
> **tseliot said:**
> Did you try flashing the bios?

yes, there isnt an updated one available at this time.

---

### Post by Iwan_from_Belgium on 2006-09-06
After

    sudo aptitude install -s -V xserver-xorg-core

I get

    couldn't find any package whose name or description matched "xserver-xorg-core"

---

### Post by tseliot on 2006-09-06
> **iyre said:**
> yes, there isnt an updated one available at this time.

Did you try any other distro?

I suggest you to try Fedora's livecd (since it is very up-to-date in terms of kernel and Xserver):

---

### Post by tseliot on 2006-09-06
> **Iwan_from_Belgium said:**
> After

    sudo aptitude install -s -V xserver-xorg-core

I get

    couldn't find any package whose name or description matched "xserver-xorg-core"

Try with:
```
sudo aptitude show xserver-xorg-core | grep Version
```

---

### Post by tlue on 2006-09-06
2006-Sep-6: Update to 10.4 worked fine for me. Thanks a lot!
(after one evening of searching for a solution 1 1/2 week ago and shortly before reinstalling.)
--> Special thanks to ubuntu_demon for the link PLEASE READ: at
[http://ubuntuforums.org/showthread.php?t=241288](http://ubuntuforums.org/showthread.php?t=241288)

---

### Post by iyre on 2006-09-06
> **tseliot said:**
> Did you try any other distro?

I suggest you to try Fedora's livecd (since it is very up-to-date in terms of kernel and Xserver):

I'll try it and let you know what happens.

---

### Post by Iwan_from_Belgium on 2006-09-07
> **tseliot said:**
> Try with:
```
sudo aptitude show xserver-xorg-core | grep Version
```

Thanks for the reply tseliot, but i moved away from the old CD.
I downloaded the latest cd and installed it, everything works fine now. Can i  do the updates now without any risk?

---

### Post by tseliot on 2006-09-07
> **Iwan_from_Belgium said:**
> Thanks for the reply tseliot, but i moved away from the old CD.
I downloaded the latest cd and installed it, everything works fine now. Can i  do the updates now without any risk?

It should work just fine (as it does on my computers here :mrgreen:  )

---

### Post by bradsucks on 2006-09-07
I updated Ubuntu last night (130 or so updates were waiting for me) and I woke up this morning to a broken X server. I searched around and thought the culprit might be the xserver-core 10.3 bug. I checked and I was running 10.4. I've tried downgrading to pre-10.3 versions but it's giving me the same error in Xorg.0.log:

> (EE) SIS(0): **************************************************
(EE) SIS(0):                       ERROR:
(EE) SIS(0): Virtual screen too big for memory; 5120K needed, 4096K available
(EE) SIS(0):                   END OF MESSAGE
(EE) SIS(0): **************************************************
(II) UnloadModule: "sis"
(II) UnloadModule: "ddc"
(II) UnloadModule: "ramdac"
(II) Unloading /usr/lib/xorg/modules/libramdac.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

You can see the full log file [here](http://www.bradsucks.net/misc/Xorg.0.log). Thanks for any help you can provide.

---

### Post by tseliot on 2006-09-07
> **bradsucks said:**
> I updated Ubuntu last night (130 or so updates were waiting for me) and I woke up this morning to a broken X server. I searched around and thought the culprit might be the xserver-core 10.3 bug. I checked and I was running 10.4. I've tried downgrading to pre-10.3 versions but it's giving me the same error in Xorg.0.log:



You can see the full log file [here](http://www.bradsucks.net/misc/Xorg.0.log). Thanks for any help you can provide.

Try the instructions which I suggested in my 1st post

---

### Post by bradsucks on 2006-09-07
I had tried it before and it didn't work. I just tried again though as per your instructions. It seemed to upgrade to 10.4 fine but X still will not start:

> (EE) SIS(0): **************************************************
(EE) SIS(0):                       ERROR:
(EE) SIS(0): Virtual screen too big for memory; 5120K needed, 4096K available
(EE) SIS(0):                   END OF MESSAGE
(EE) SIS(0): **************************************************
(II) UnloadModule: "sis"
(II) UnloadModule: "ddc"
(II) UnloadModule: "ramdac"
(II) Unloading /usr/lib/xorg/modules/libramdac.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Full Xorg.0.log [here](http://www.bradsucks.net/misc/Xorg.0-02.log).

---

### Post by bradsucks on 2006-09-07
Duh. Looks like after the upgrade it was trying to do 1280x1024 which my video card doesn't support. I removed the 1280x1024 references and it seems to work now.

---

### Post by wvernon on 2006-09-08
Since having this problem, I have been having problems with my keyboard.

If I run:
sudo setxkbmap -layout 'gb,us' -model pc105
in a terminal when I first boot up, I'm OK, but when I try to do it using the gnome preferences graphical method, I get:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Any ideas?

Regards,

Wayne

---

### Post by tseliot on 2006-09-08
> **wvernon said:**
> Since having this problem, I have been having problems with my keyboard.

If I run:
sudo setxkbmap -layout 'gb,us' -model pc105
in a terminal when I first boot up, I'm OK, but when I try to do it using the gnome preferences graphical method, I get:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Any ideas?

Regards,

Wayne
Try to update your xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then
```
sudo dpkg-reconfigure xserver-xorg
```

and set the keyboard you want to use (press ENTER whenever you don't know the answer to the other questions)

---

### Post by diggitydank on 2006-09-08
Pretty much a Linux n00b here. Have played with Dapper and Breezy quite a bit lately (started with PCLinuxOS a while back), but still learning. Last night I finally decided to make the complete switch to Dapper. Everything went well, so it seemed. I ran the updates, restarted, installed some stuff with Automatix (including the Nvidia drivers) and now the screen goes black when logging in. I can Ctrl-Alt-Backspace and get into X, but then when shutting down, the screen just goes black, but everything stays powered on. I have to force shutdown (which sucks). Is this related to the problems stated in this thread or do I have something else going on? I am at work now, so I cannot try any of the fixes, yet. Thanks.

Poop happens. I am still a big Ubuntu fan.

---

### Post by tseliot on 2006-09-08
> **diggitydank said:**
> Pretty much a Linux n00b here. Have played with Dapper and Breezy quite a bit lately (started with PCLinuxOS a while back), but still learning. Last night I finally decided to make the complete switch to Dapper. Everything went well, so it seemed. I ran the updates, restarted, installed some stuff with Automatix (including the Nvidia drivers) and now the screen goes black when logging in. I can Ctrl-Alt-Backspace and get into X, but then when shutting down, the screen just goes black, but everything stays powered on. I have to force shutdown (which sucks). Is this related to the problems stated in this thread or do I have something else going on? I am at work now, so I cannot try any of the fixes, yet. Thanks.

Poop happens. I am still a big Ubuntu fan.

You can try point 13 of the Problems Section of my guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-b5fef156d1e6aba56287648d7adf3902f6b83ca9](https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-b5fef156d1e6aba56287648d7adf3902f6b83ca9)

If you upgraded (dist-upgraded) your system from Breezy to Dapper I suggest you to do a clean installation

---

### Post by diggitydank on 2006-09-08
> **tseliot said:**
> You can try point 13 of the Problems Section of my guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-b5fef156d1e6aba56287648d7adf3902f6b83ca9](https://help.ubuntu.com/community/Latest_Nvidia_Dapper#head-b5fef156d1e6aba56287648d7adf3902f6b83ca9)

If you upgraded (dist-upgraded) your system from Breezy to Dapper I suggest you to do a clean installation

Thanks for the help. I will try that tonight.

This was a fresh install. Wiped Windows clean off my system. I might just do another fresh install if I cannot get this to work. I haven't put anything important on there, yet.

---

### Post by DalHelpdesk on 2006-09-08
> **tseliot said:**
> Try with this command:
```
sudo apt-get update
```

```
sudo apt-get install -f
```

P.S. your problem is not caused by the xserver package

Thanks for the info Tseliot. My OS crashed overnight i think, it started giving alot of errors about nodes failure and i had to re-intall Ubuntu.
I am actually setting up the Ubuntu to auth against LDap. It started working and everything and then this Xserver failure happend(i was getting the same Xserver not config error).

I am again trying to auth against Ldap but don't know where to start. Have you done this? If yes, can you give me some pointers on how to go about it.

Thanks,

---

### Post by tseliot on 2006-09-08
> **DalHelpdesk said:**
> I am again trying to auth against Ldap but don't know where to start. Have you done this? If yes, can you give me some pointers on how to go about it.

Thanks,
Sorry but I have no experience of LDap

---

### Post by wvernon on 2006-09-09
tseliot - you are a genius.  Your suggestion worked a treat!

Thanks very much.

I probably messed my config up while messing around with the original xserver fault.

Regards,

Wayne

---

### Post by engineering.concepts on 2006-09-10
I am having issues with my compaq n800c - ati video card

I will try to give as much detail about the problem, feel free to ask as many questions as necessary - I will be more then happy for anyone's assistance

From power on- everything looks normal - goes to GUI login screen
I enter my username - GUI now askes for password
I enter my password - Screen goes black - see a command prompt -
Screen goes brown - see a "wait" icon (circle with spinniy lines all around)
Goes back to GUI login screen.
I can try this many times and it will just repeat the cycle
I thought I might have a similar issue as listed in [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
so I hit "ctrl-alt-F1" to get me to a prompt.
I enter my username
prompt asks for password - I enter my password - I am in
I can type ls to see all my files,
so I tried the steps listed on [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
ie.
sudo apt-get update
sudo apt-get install xserver-xorg-core
but it tells me that my xserver-xorg-core is up to date.
I tried sudo apt-get install --reinstall xserver-xorg-core
and it reinstalled, but when I reboot, I get the same problem.

also tried - 
sudo dpkg-reconfigure xserver-xorg
and set it up, but still the same issue

then I tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
and downgraded my xserver
still no luck!!!!!

This is driving me crazy! I can log in from the prompt, but need a gui!!!
how can a see any gui????

---

### Post by tseliot on 2006-09-10
> **engineering.concepts said:**
> I am having issues with my compaq n800c - ati video card

I will try to give as much detail about the problem, feel free to ask as many questions as necessary - I will be more then happy for anyone's assistance

From power on- everything looks normal - goes to GUI login screen
I enter my username - GUI now askes for password
I enter my password - Screen goes black - see a command prompt -
Screen goes brown - see a "wait" icon (circle with spinniy lines all around)
Goes back to GUI login screen.
I can try this many times and it will just repeat the cycle
I thought I might have a similar issue as listed in [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
so I hit "ctrl-alt-F1" to get me to a prompt.
I enter my username
prompt asks for password - I enter my password - I am in
I can type ls to see all my files,
so I tried the steps listed on [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
ie.
sudo apt-get update
sudo apt-get install xserver-xorg-core
but it tells me that my xserver-xorg-core is up to date.
I tried sudo apt-get install --reinstall xserver-xorg-core
and it reinstalled, but when I reboot, I get the same problem.

also tried - 
sudo dpkg-reconfigure xserver-xorg
and set it up, but still the same issue

then I tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
and downgraded my xserver
still no luck!!!!!

This is driving me crazy! I can log in from the prompt, but need a gui!!!
how can a see any gui????
Try adding a new account (i.e. username):

1) Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).


2) Type:
```
adduser new_username
```

**NOTE: replace "new_username" with your new username (which must be different from the one you already have**

```
passwd new_username_password
```

**NOTE: replace "new_username_password" with the password for your new username**

3) Add your new username to the sudoers list (otherwise you won't be ablet o use sudo)

Type:
```
visudo
```

and look for these lines:
```
# User privilege specification
root    ALL=(ALL) ALL[CODE]

Add your new username so as to make it look like this:

[CODE]# User privilege specification
root    ALL=(ALL) ALL
**new_username ALL=(ALL) ALL**
```

**NOTE: replace "new_username" with your new username**

After you did that type: 
```
:wq
```

and press ENTER in order to save


4) Restart your computer. Type:
```
reboot
```

5) Boot Ubuntu as usual and log in using your new username

---

### Post by engineering.concepts on 2006-09-10
when I type addusr ralph - I get
-bash: addusr: command not found

---

### Post by tseliot on 2006-09-10
> **engineering.concepts said:**
> when I type addusr ralph - I get
-bash: addusr: command not found

my bad: it's adduser

---

### Post by engineering.concepts on 2006-09-10
I added the user (using the steps above)
when it reboots, I enter username and password, it tries to login but goes abck to the login gui (same as before)

---

### Post by tseliot on 2006-09-10
> **engineering.concepts said:**
> I added the user (using the steps above)
when it reboots, I enter username and password, it tries to login but goes abck to the login gui (same as before)

when did you get the problem the first time? What you did before having the problem?

---

### Post by engineering.concepts on 2006-09-10
Got the problem for the first time yesterday after a reboot.
Everything was working perfectly up until then 
It is possible updates might have been installed - my wife says no, but I installed updates a few days ago (she only reboots her laptop once a week)
Is it possible this has something to do with the ati drivers? My IBM has no issues at all.
What is the command to start xserver?
typing - xserver at the prompt gives me an error
typing - xubuntu at the prompt gives me an error
typing - ubuntux at the prompt gives me an error

is there any way to see any gui?
If I type an incorrect username/password, it will tell me that it is incorrect, but when I try the new / old username, just goes back to gui login. 
I tried different login sessions (failsafe gnome/failsafe terminal) and they all do the same thing - at one point it crashed after trying lots of different sessions. 
Could my session manager be corrupted?
Thanks for your assistance!!!

---

### Post by tseliot on 2006-09-10
> **engineering.concepts said:**
> Got the problem for the first time yesterday after a reboot.
Everything was working perfectly up until then 
It is possible updates might have been installed - my wife says no, but I installed updates a few days ago (she only reboots her laptop once a week)
Is it possible this has something to do with the ati drivers? My IBM has no issues at all.
What is the command to start xserver?
typing - xserver at the prompt gives me an error
typing - xubuntu at the prompt gives me an error
typing - ubuntux at the prompt gives me an error
```
startx
```


> **engineering.concepts said:**
> I tried different login sessions (failsafe gnome/failsafe terminal) and they all do the same thing - at one point it crashed after trying lots of different sessions. 
Could my session manager be corrupted?
Thanks for your assistance!!!
Try installing Xubuntu or Kubuntu from Terminal:
```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install kubuntu-desktop
```

than reboot see if you can access the desktop using XFCE or KDE

---

### Post by engineering.concepts on 2006-09-10
according to [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153)
this bug affects my computer - n800c - is it possible the ati drivers are corrupted or need some generic drivers?

---

### Post by T-MAN3000 on 2006-09-10
You can start the x-server by typing "startx" 

If your problem is caused by the faulty update to xserver-xorg, which I doubt, because there only was a problem window of a few hours, about two or three weeks ago, you can solve the problem by just hitting this command: ```
sudo apt-get update && apt-get upgrade
``` and then reconfigure your videodrivers by this command: ```
sudo dpkg-reconfigure xserver-xorg
```

In general I would recommend this to everyone as a first step when you can't start an x session.

edit: I need to learn how to use F5 8)

---

### Post by tseliot on 2006-09-10
> **engineering.concepts said:**
> according to [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153)
this bug affects my computer - n800c - is it possible the ati drivers are corrupted or need some generic drivers?

try with:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "ati" driver

---

### Post by engineering.concepts on 2006-09-10
Thanks for your help!!!!
Finally got it working - the key was when I typed startx - could not start due to insufficant disk space!!!

I deleted some files, but it still would not boot into Gnome, so I tried Knoppix, and Ubuntu Live CD, but both could not mount the drive, so I ripped it out of the laptop and connected it via usb to my ibm laptop (good thing I have parts lying around) and delted movies etc...

Everything works great now.
THANKS!!!!!!!!:D 

How much free space does Ubuntu need?
Should I create a 50meg garbage file that can be easily deleted in the future if this happens?
Will future versions of Ubuntu create a 50mb temp file and delete it on logout to ensure this can not happen?

Sorry for the run around in finding the issue, - this xserver problem took me for a loop

---

### Post by crashtestyyz on 2006-09-10
> **tseliot said:**
> Uninstall the fglrx driver and set your xorg.conf to "ati" or "vesa" in the Section Device.

It might be related to a failure of the fglrx driver rather than of the xserver itself.

Clarification: My motherboard is an A8R-MVP.  flashed to latest code too.

I could re-use the vesa driver, but then i'd get a refresh rate that kills my eyes in under 5 minutes.
as I have an RADEON X1600, the "ati" driver will not work.  I'm stuck with flgrx.

And so, just to test, AGAIN, I did a *fresh* install, updated, installed the xorg fglrx driver, rebooted.. the result.. BSOD (Black Screen Of Death)

At this point it's hard to decide whether to conclude whether xorg is garbage, ATI is garbage, my motherboard is garbage, or ubuntu itself is garbage.
Before the "latest update breaks X" scenario, the ubuntu-distro fglrx driver actually worked. :mad: 

--C

---

### Post by tseliot on 2006-09-10
> **crashtestyyz said:**
> Clarification: My motherboard is an A8R-MVP.  flashed to latest code too.

I could re-use the vesa driver, but then i'd get a refresh rate that kills my eyes in under 5 minutes.
as I have an RADEON X1600, the "ati" driver will not work.  I'm stuck with flgrx.

And so, just to test, AGAIN, I did a *fresh* install, updated, installed the xorg fglrx driver, rebooted.. the result.. BSOD (Black Screen Of Death)

At this point it's hard to decide whether to conclude whether xorg is garbage, ATI is garbage, my motherboard is garbage, or ubuntu itself is garbage.
Before the "latest update breaks X" scenario, the ubuntu-distro fglrx driver actually worked. :mad: 

--C

Try Fedora Core 5 and see if you get the same error

---

### Post by jcmhunting on 2006-09-11
It seems I installed 22 desktops in my classroom at just the wrong time.  Although I haven't had any problems, the only update that shows up is to xserver 10.3.  I tried following the directions from page 1 of this thread, but haven't had any luck.  When I try to update, it will not connect to the server. Any help would be greatly appreciated.

JCM

---

### Post by tseliot on 2006-09-11
> **jcmhunting said:**
> It seems I installed 22 desktops in my classroom at just the wrong time.  Although I haven't had any problems, the only update that shows up is to xserver 10.3.  I tried following the directions from page 1 of this thread, but haven't had any luck.  When I try to update, it will not connect to the server. Any help would be greatly appreciated.

JCM

If you don't have any problem then you don't need to do anything

---

### Post by jcmhunting on 2006-09-11
Sorry to be a bother, but why would it tell me to update, and then fail to connect to the server?  And have no updates in 3+ weeks?

Thanks,

JCM

---

### Post by tseliot on 2006-09-11
> **jcmhunting said:**
> Sorry to be a bother, but why would it tell me to update, and then fail to connect to the server?  And have no updates in 3+ weeks?

Thanks,

JCM

It's because of your repository list.

Your problem is not caused by the update described in this thread.


Read this thread:
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)


EDIT: this thread is about the Xserver (Xorg) (which enables you to use Desktop Environments such as GNOME) and not the Ubuntu's servers

---

### Post by kendals on 2006-09-12
tseliot, I'm having serious problems, and I'm not sure if it's due to the recent update (which I did last night and was told to reboot, the start of my problems)- i didn't reboot until I finished trying to install compiz+aiglx (see my thread here- [http://ubuntuforums.org/showthread.php?t=255790)](http://ubuntuforums.org/showthread.php?t=255790)), and now it keeps telling me 'Failed to start the X server'.

I've done everything- tried the dpkg reconfigure command for xorg.conf with no luck.I am using a GMA900 onboard my Toshiba laptop, and am led to believe that the BusID is PCI:0:2:0 (or 0:2:1, but it doesn't like either!), but no matter what I do, it still says this X Server failed, and I can't do anything.

Please help. I'm desparate. I cannot access the net on the laptop to downgrade, and the cd command mentioned on the first page of this thread 'wasn't found' ...:(

---

### Post by tseliot on 2006-09-12
> **kendals said:**
> tseliot, I'm having serious problems, and I'm not sure if it's due to the recent update (which I did last night and was told to reboot, the start of my problems)- i didn't reboot until I finished trying to install compiz+aiglx (see my thread here- [http://ubuntuforums.org/showthread.php?t=255790)](http://ubuntuforums.org/showthread.php?t=255790)), and now it keeps telling me 'Failed to start the X server'.

I've done everything- tried the dpkg reconfigure command for xorg.conf with no luck.I am using a GMA900 onboard my Toshiba laptop, and am led to believe that the BusID is PCI:0:2:0 (or 0:2:1, but it doesn't like either!), but no matter what I do, it still says this X Server failed, and I can't do anything.

Please help. I'm desparate. I cannot access the net on the laptop to downgrade, and the cd command mentioned on the first page of this thread 'wasn't found' ...:(
I can only suggest you to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

type
```
nano -w /etc/gdm/gdm.conf-custom
```

Make your gdm.conf-custom look like this:

```
[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
```

Press CTRL+X to exit (save the file)


Then you will need to update your xorg.conf:
```
dpkg-reconfigure -phigh xserver-xorg
```

Then configure it:
```
dpkg-reconfigure xserver-xorg
```

and select the driver for your card. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by kendals on 2006-09-12
OMG TSELIOT! I LOVE YOU!

You now rock my world :D

Any ideas why it might have done this? Like, shoud I stray away from compiz+aiglx for now? :P

---

### Post by tseliot on 2006-09-12
> **kendals said:**
> Any ideas why it might have done this? Like, shoud I stray away from compiz+aiglx for now? :P
Yep. Wait for Ubuntu Edgy for that

---

### Post by kendals on 2006-09-12
Roger. *Suppose* I can wait until Oct. 26th....:P Thanks!

---

### Post by gmcm1979 on 2006-09-14
i had the error before of xsever failing to start but upgraded to 10.4 and everything was working fine until today, i now get the same error message, please help

---

### Post by tseliot on 2006-09-14
> **gmcm1979 said:**
> i had the error before of xserver failing to start but upgraded to 10.4 and everything was working fine until today, i now get the same error message, please help
Then it might not be the same problem.

Did you install Compiz/XGL or install anything else before the error?

Or are you using the nvidia driver?

---

### Post by saz on 2006-09-14
the same thing happened to me today, and all i did was install the new updates (new linux-image and new kernel headers)

---

### Post by iyre on 2006-09-14
> **tseliot said:**
> Did you try any other distro?

I suggest you to try Fedora's livecd (since it is very up-to-date in terms of kernel and Xserver):


> **iyre said:**
> I'll try it and let you know what happens.

I tried this and it didnt work either (trying fedora core)

So I remembered your suggestion about flashing the BIOS with an update. There wasnt one, but there was an 'original' one (supposedly the one that is imprinted when it leaves the factory). I downloaded and reflashed the BIOS with this one and miracle of miracles, X server just started working.

I did notice that FC had trouble locating the network card, which suggested to me the issue was mainboard related rather than distro.

Odd problem no? And sorry for the posts that are now obviously not on topic.

---

### Post by gmcm1979 on 2006-09-15
i'm not too sure as i think i changed the updates to install automatically, i had nvidia drivers installed but i'm not too sure if i have installed Compiz/XGL

---

### Post by tseliot on 2006-09-15
> **gmcm1979 said:**
> i'm not too sure as i think i changed the updates to install automatically, i had nvidia drivers installed but i'm not too sure if i have installed Compiz/XGL

Read this:
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by xyz on 2006-09-15
Is there any explanation as to why some of us, like me, "luckily" escaped problems related to this particular update? I updated as soon as they were available.

---

### Post by xero 1ne on 2007-04-05
Hello, I have recently run into this problem, although I am using 6.10...

My current version of xserver core is 1:1.1.1-0ubuntu12.2

After an update to that, and a restart, the gdm loads, and beryl loads, but just about when it is to display my desktop, xserver crashes.

No errors, it just drops and restarts, putting me back at the login screen.

Just a thought though, could a large number of files on the desktop do this? prior to restarting I had downloaded some songs from a friends computer, and being lazy like I am, I just dragged and dropped to the desktop....
If that could be the problem, how can i cut/paste that out of there using the command lines?


Many thanks to all the wonderfull Ubuntu contributors!

P.S. The *failsafe gnome* has the same problem, even though in there I can see an error message come up before xserver drops out. Unfortunetly there's not enough time to read it...

---

### Post by boarderpatrol on 2007-04-05
Hello, I have recently run into this problem as well.  Just started today for me today.
 I have AMD 4400 nvidia 7600 gt with nvidia driver edgy eft.
2.6.17-11-generic  I have been using Envy to load my nvidia drivers after kernel updates
My current version of xserver core is 1:1.1.1-0ubuntu12.2
I dont run beryl/compiz etc. so I can get to Desktop fine but when 
trying to launch any openl gl app  (google earth, secondlife etc.)
xserver crashes and reboots back to login prompt.

I checked for error. Here is what im getting.

2007-04-05T21:50:01Z INFO: main: Initializing window...
2007-04-05T21:50:01Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2007-04-05T21:50:01Z INFO: ll_try_gtk_init: GTK Initialized.
2007-04-05T21:50:01Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2007-04-05T21:50:01Z INFO: ll_try_gtk_init: - Running against GTK version 2.10.6
2007-04-05T21:50:01Z INFO: createContext, fullscreen=0 size=1280x887
2007-04-05T21:50:01Z INFO: createContext: Compiled against SDL 1.2.5
2007-04-05T21:50:01Z INFO: createContext:  Running against SDL 1.2.11
2007-04-05T21:50:01Z INFO: createContext: creating window 1280x887x32
2007-04-05T21:50:01Z WARNING: createContext: window creation failure. SDL: Couldn't find matching GLX visual
2007-04-05T21:50:01Z INFO: destroyContext begins
2007-04-05T21:50:01Z INFO: destroyContext: shutdownGL begins
2007-04-05T21:50:01Z INFO: destroyContext: SDL_QuitSS/VID begins
2007-04-05T21:50:01Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.

Window creation error pops up there.
I reinstalled nvidia drivers but that didnt help.

Thanks for any help or suggestions for me to try.

---

### Post by xero 1ne on 2007-04-05
Yah, I'm also running an Nvidia card(7900gs), mabey that's where the problem lies...

I'll check my xorg.conf file and mabey reinstall my Nvidia drivers.......

---

### Post by boarderpatrol on 2007-04-05
Saw this forum post:

[http://ubuntuforums.org/showthread.php?t=400989](http://ubuntuforums.org/showthread.php?t=400989)

Topic concerns replacing symbolic link to libglx.so.1.0.97xx.

so I used envy again to install nvidia driver and this time I let it update my xorg.conf.
still not working tho.

---

### Post by xero 1ne on 2007-04-05
Alright,reinstalling the Nvidia drivers (v9755) worked! 
I can now see my desktop and beryl and everything works perfectly:guitar: .....except.....


MY TASKBARS ARE MISSING!!!! :lolflag: :mad:

---

### Post by boarderpatrol on 2007-04-05
I reinstalled driver again.  I am getting 9446 driver,  i think thats it.  I know its not the 9755 you just installed,  
    but it's working now again .  YAY

   When reinstalling got a msg about no symbolic link to libglx.so.   Hopefully that 
 will help some one know where to look to keep this from happening to other users.

---

### Post by emarcellus on 2007-04-05
My main machine crashed as well from the update. I could not get Gnome to load.
I ended up switching to console 1 and running

sudo apt-get install kde

210 megs later I rebooted my machine and at the login I switched to KDE.
KDE would come up and then I was able to use Synaptic Package Manager to Force the xorg package back to the previous version.

Another reboot and Gnome was happy again.

Does anyone know how to have done this from the command prompt?

If I had not noticed the xorg updated the night before I likely would have still been lost.

I still do not know what the issue is.

I have an AMD64 box with an NVIDIA graphics card. Before the rollback I did try Envy reload and a configure of the xserver but neither helped.

From now on I will likely start keeping multiple desktops installed just in case.

I feel for the more novice Ubuntu users that have crashed machines. They might not be able to get it fixed. It seems when it comes to xorg the Ubuntu team needs to do better testing. I know last year there was another x issue and that one crashed my X server as well.

Ed

---

### Post by xero 1ne on 2007-04-05
Alright, when I've logged in, I get the error message : 

"I've detected a panel already running, and will now exit." and I don't have taskbars with the aplications and junk like that.

What controls this?:confused:

---

### Post by ispmarin on 2007-04-05
The xserver-xorg updates changes several things in the X configurations and/or modules, so if you are using the NVIDIA binary driver (from NVIDIA site) you`ll have to reinstall the driver after the xorg update. Happened to me. 

Hope it helps.

---

### Post by rare HERO on 2007-08-04
> **tseliot said:**
> I meant:
What happens if you type:
```
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
```

Please report the error

It reads:

```
xserver-xorg-core is already the newest version
```

---

### Post by rare HERO on 2007-08-04
When I type

```
sudo aptitude install -s -v xserver-xorg-core
```

I get

```
The following essential packages will be removed
sysvinit
```

When I type

```
sudo aptitude show xserver-xorg-core | grep Version
```

I get

```
Version: 1:1.1.-0ubuntu12
```

When I type

```
wget http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xwerver-xorg-xore_1.0.2-0ubuntu 10-i386
```

I get 

```
404 not found
```

That's probably because my problem is outdated: "xserver-xorg is broken..."

When I type

```
sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
```

I get

```
no such file or directory
```

When I type 

```
sudo apt-get install
sudo apt-get install -s xserver-xorg-core=1:1.0.2-0ubuntu10.1
```

I get
```

is already the newest version
```

Should I try fixing the drivers?

If so how do I go about doing that (in detail since I'm not familiar with this type of troubleshooting)
In advance thank you.

---

### Post by frodon on 2007-08-04
This bug is one year old now and has been fixed so if you have a bug with xorg this is not related to what this thread describe.

---

### Post by ganjuror on 2007-10-21
I think I messed up... 

I tried the upgrade first, but the output from 'sudo aptitude install -s -V  xserver-xorg-core' was a touch cryptic, so I let it go and hoped for the best. It did _not_ find 10.4 in the repositories.

I tried the downgrade, it succeeded, but I still can't startx:

(EE) module ABI minor version (7) is newer than the server's version (5)
and...
(EE) failed to load module "kbd" (module requirement missmatch, 0)

It seems I may have inadvertantly updated some of the dependancies for the downgrade version?

Ideally, I'd like to actually 'upgrade' but doing an aptitude update doesn't make 10.4 available. How is it that some people are finding this updated version in repo's and others aren't? Are there some repo servers that have the update while others don't? Is there any way to manually get v 10.4 from the command line? If not, how do I find/install the corresponding downgrades to make my downgraded xserver work?

Thanks in advance,
River Hume

---

### Post by Adler on 2007-10-21
ganjuror,

Dude wasn't that about a year ago? That *was* horrible.

Adler

---

### Post by ganjuror on 2007-10-21
Whoah! Yeah I had JUST noticed the date on the thread after I posted! YIKES well, I'm having what _seems_ to be the same problem after just yesterday updating to gutsy gibbon... 

Anyhow, I got it fixed (nvidia driver issue) - thanks for the reply...

-River

---

### Post by Adler on 2007-10-21
ganjuror,

Best bet is a fresh install. I'd like to know if that is a problem e.g. Gutsy.

Adler

---

### Post by Perfect Storm on 2007-10-21
I'm going to close this thread as it's from the past.

---

