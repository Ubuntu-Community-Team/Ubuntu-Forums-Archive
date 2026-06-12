---
title: "Alpha 2 iso testing"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-02-01
Iso testing has started:

> Hi everyone!

Natty Alpha 2 is due this week and candidate images will start appearing
hopefully Today.

As usual we'll be asking everyone on the QA team to participate in the
image testing to ensure we have good test coverage.

The procedures for testing ISO images and reporting results are
explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

Test results will be tracked on [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

You may have accounts on the tracker from last time. Please register if
you are new to this.

For this testing session we have established the priority list below:
ubuntu-desktop	i386
ubuntu-desktop	amd64
Ubuntu-server	i386
Ubuntu-server	amd64
Ubuntu-alternate	i386
Ubuntu-alternate	amd64
Ubuntu-preinstalled	omap
Ubuntu-server EC2	i386
Ubuntu-server EC2	amd64
kubuntu-desktop	i386
xubuntu-desktop	i386
Ubuntu-dvd	i386
Ubuntu-dvd	amd64
kubuntu-desktop	amd64
ubuntustudio-desktop	i386
xubuntu-desktop	amd64
edubuntu-desktop	i386
ubuntustudio-desktop	amd64
edubuntu-desktop	amd64

Rather than going deep and in order to make sure that there is no big
issue left behind, we'll start by running a testcase for each image
(/Install/DesktopWhole or /Install/AlternateWhole depending on the
image) and ensure that each image have at least been tested once, then
we will run the other test cases.

Please let us know if you have any questions.

We will coordinate testing in #ubuntu-testing on freenode. Please, go
there often to see what others are testing or what needs to be tested.

Thank you very much for your help and happy testing!

-- Jean-Baptiste 

---

### Post by ronacc on 2011-02-01
if we zsync our daily will it be A2 or is that a different download ?

---

### Post by psusi on 2011-02-01
> **ronacc said:**
> if we zsync our daily will it be A2 or is that a different download ?

Yes.

---

### Post by cariboo on 2011-02-01
There was a soft feature freeze set today, so essentially an up-to-date daily should be the same as what will be released Thursday, there will probably be bug fixes added, so just use zsync to keep the images up to date.

---

### Post by ronacc on 2011-02-01
thanks , I zsync daily as a habit .

---

### Post by kansasnoob on 2011-02-02
Anyone else struggling with this one?

It's kicking my butt!

I got the Live CD to work OK, other than persistence failing, but I'd have to Alt+SysReq>K and then select Classic w/o effects to do anything.

Worse yet I'll be darned if I can get a fresh install to boot. It just sits forever on a blank purple screen w/o ever getting to the login screen :(

I even tried recovery mode and I don't see any nasty error messages but it just fails/stalls.

Tis a puzzle I won't solve tonight.

---

### Post by mc4man on 2011-02-02
> Anyone else struggling with this one?
Not exactly, most boots are good here and the live cd's generally work.

What have seen over the last month or so is  that natty is prone to kernel panics, whether booting from an install or even the live cd's.
The last 3 live cd's I've tried (1/27, 1/30, 1/31) all almost always panic on first attempt to boot, all work on the 2nd or 3rd try. (2 different machines
(I can see the output to some extent by removing quiet,splash, and vt.handoff=7

While i haven't seen much direct mention here of this you do see mentioned in an offhand way some of the symptoms - having to boot twice, purple screen, black screen w/ blinking cursor, flashing lights on a laptop, ect.

Noting that here i have maverick also on these machines which boots fine and actually on these same hardwares have never had even 1 panic before natty, going back  to fiesty on a desktop.

---

### Post by Jay Car on 2011-02-02
> **kansasnoob said:**
> Anyone else struggling with this one?

It's kicking my butt!

I got the Live CD to work OK, other than persistence failing, but I'd have to Alt+SysReq>K and then select Classic w/o effects to do anything.

Worse yet I'll be darned if I can get a fresh install to boot. It just sits forever on a blank purple screen w/o ever getting to the login screen :(

I even tried recovery mode and I don't see any nasty error messages but it just fails/stalls.

Tis a puzzle I won't solve tonight.

Yes, this week has been challenging to say the least. Was only able to get it to boot to the desktop twice...once in classic, once with Unity before everything froze, or disappeared entirely. Sometimes all I got were black or purple screens. The more I tried to fix things the deeper it sank into oblivion. Finally decided I was in over my head and set it aside, will wait a few days and try again (occasionally good sense overcomes my stubbornness).

I've heard that we learn more from difficult tasks than from things that are easy. If that's true, my brain should be in a state of exhaustion by April.:lolflag:

Looking forward to trying again this weekend.

---

### Post by kansasnoob on 2011-02-02
Just FYI I'm talking about the official iso-testing build:

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

I'm running into problems that I normally haven't.

---

### Post by Quackers on 2011-02-02
My experiences so far.
Installed it with no problems.
Chose to import settings from alpha1 system - waste of time, as only evolution settings were imported, and even that was missing passwords. No Mozilla settings, no user files/settings.
On reboot I got the Classic desktop and chose to install the new open source 3D nvidia experimental driver.
On reboot I got an empty desktop. No panels, nothing.
On reboot I chose Classic desktop and all was good. Compiz runs but there is no "effects" tab in Appearance (don't know if that's normal or not).
Ran updates (just one) and tried Desktop Edition again. At first I had a top panel but as soon as I tried to open anything compiz crashed and all became unusable. Alt F2 does nothing, neither does ctrl Alt T.
So now I'm back in classic and it's usable again.
Unity doesn't want to run, it seems.
Any ideas?

---

### Post by mc4man on 2011-02-02
> Unity doesn't want to run, it seems.
Any ideas?
I don't think unity will currently work with the nouveau 3d drivers or at least with the nv cards I have.
This occurred before the xserver upgrade and nothing in the X upgrade is going to change that.
So - either for some (hardware specific) or all nvidia users A2 means no unity possible atm

If you were to login to the Ubuntu Desktop (3D enabled) and try to start unity or compiz you may see this?

compiz: nv50_pc_emit.c:863: emit_flop: Assertion `STYPE(i, 0) == 0x09' failed.
Aborted (core dumped)

Edit: this is all a bit off topic  - I think -  in regards to testing the A2 iso

---

### Post by kyleabaker on 2011-02-02
> **mc4man said:**
> I don't think unity will currently work with the nouveau 3d drivers or at least with the nv cards I have.

Works for me after updates a couple hours ago.

---

### Post by mc4man on 2011-02-02
> Works for me after updates a couple hours ago.
Will have to give it a retry in a few..

Edit: still no go, will try again w/ a fresh install when A2 releases

bug report
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588)

---

### Post by kansasnoob on 2011-02-02
The new build this AM worked much better for me, one rather small bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/711965](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/711965)

Another from upgrade testing:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/711896](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/711896)

Of course Unity is still not working well with my Intel i945 but I just use Alt+SysReq>K to get back to the greeter and select Classic w/o effects.

---

### Post by gnomeuser on 2011-02-02
I just tried an install onto Btrfs using the daily-live. The install works okay by the grub configuration is wrong somehow as you are dropped into rescue grub with a file missing message.

---

### Post by ronacc on 2011-02-02
amd64 iso boots for me with no problems seen , defaults to classic desktop , I'm Nvidia here so thats normal with no drivers installed .

---

### Post by clegends on 2011-02-02
For what it's worth installs on my eeepc901 from the daily live won't work properly... haven't submitted a bug as I'm sure it's an issue that will be fixed soon. I can't partition my 4gb ssd drive... system freezes, etc. Anyway, I've been using the alternative installer flawlessly, and zsyncing every few days. I recommend trying this for anyone not able to get the regular install to work. Unity is awesome, and looking forward to a stable build.

~dinky

---

### Post by nm_geo on 2011-02-02
> **mc4man said:**
> Not exactly, most boots are good here and the live cd's generally work.

What have seen over the last month or so is  that natty is prone to kernel panics, whether booting from an install or even the live cd's.
The last 3 live cd's I've tried (1/27, 1/30, 1/31) all almost always panic on first attempt to boot, all work on the 2nd or 3rd try. (2 different machines
(I can see the output to some extent by removing quiet,splash, and vt.handoff=7

While i haven't seen much direct mention here of this you do see mentioned in an offhand way some of the symptoms - having to boot twice, purple screen, black screen w/ blinking cursor, flashing lights on a laptop, ect.

Noting that here i have maverick also on these machines which boots fine and actually on these same hardwares have never had even 1 panic before natty, going back  to fiesty on a desktop.

I do get the kernel panics about 1 out of 3 boot-ups.  Mine seem to occur about 4 or 5 seconds after the HD spins up.  I just reboot and everything goes well on the reboot

---

### Post by ronacc on 2011-02-02
> **nm_geo said:**
> I do get the kernel panics about 1 out of 3 boot-ups.  Mine seem to occur about 4 or 5 seconds after the HD spins up.  I just reboot and everything goes well on the reboot

same here , seems to occur on cold boots about 1 time out of 3 or 4 reboot and all goes normaly .

---

### Post by mc4man on 2011-02-02
> I do get the kernel panics about ....

I'm probably going to file a bug on this, it took me quite some time to get what I hope are relevant lines starting just before and at the panic start (most times the console will just display the tail end.

I guess I was hoping it would just go away, and it has gotten better the last several weeks. 
What I've always noticed is that the panic is always exactly the same w/ the exception of a few unimportant values. (on 2 different machines

The big chore is it's quite a bit of typing, (19 long lines) and i can't type for .... (maybe I can talk my son into doing

As I mentioned before if you go to a text boot you'll see some of the panic when it occurs and for some part I found removing the vt.handoff=7 to be beneficial (it's now removed automatically if you remove quiet and splash from /ect/default/grub

---

### Post by ronacc on 2011-02-03
@ mc4man there are multiple bug reports on this on LP , check there and "me too " one and save your typing finger:p

---

