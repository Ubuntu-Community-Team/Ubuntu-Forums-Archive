---
title: "Update Manager password"
date: 2010-06-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by luceerose on 2010-06-04
This is the one thing that's annoying me slightly so far.
Since my upgrade to Maverick, Update Manager now asks for my password twice.

It used to be;
1) Hit 'Check'
2) Type Password
3) Hit 'Install Updates'

Now it's;
1) Hit 'Check'
2) Type Password
3) Hit 'Install Updates'
4) Type Password

Is this going to be the normal behavior from now on ?

---

### Post by yelo3 on 2010-06-04
this is caused by the migration from synaptic to aptdaemon.
the new authenication method is based on policykit, and the "check" procedure has a different permission rule than "install updates".

What I really miss is a graphical configuration of policykit rules.

---

### Post by yelo3 on 2010-06-04
I've found a way to prevent asking from passwords.
Note that it will NEVER ask from passwords in all APT actions (update the list, install, upgrade and remove packages) using aptdaemon

put this in a (new) file: /etc/polkit-1/localauthority/50-local.d/apt.pkla
```

[Configuration]
Identity=unix-group:admin
Action=org.debian.apt.*
ResultActive=yes

```

---

### Post by dino99 on 2010-06-04
sudo chmod g+r /var/cache/debconf/passwords.dat

---

### Post by philinux on 2010-06-08
> **yelo3 said:**
> this is caused by the migration from synaptic to aptdaemon.
the new authenication method is based on policykit, and the "check" procedure has a different permission rule than "install updates".

What I really miss is a graphical configuration of policykit rules.

If this is the default it's a PITA. I never do workarounds when testing development releases.

Mind you I do my updates from terminal or chroot.

---

### Post by zekopeko on 2010-06-08
AFAIK the plan is to have the Check not require password. Install Updates will require it.

---

### Post by 23meg on 2010-06-08
> **zekopeko said:**
> AFAIK the plan is to have the Check not require password. Install Updates will require it.

Right, that's how U-M worked three cycles ago in the development branch when it had the Aptdaemon backend enabled for a short while.

---

### Post by andrewabc on 2010-06-08
> **zekopeko said:**
> AFAIK the plan is to have the Check not require password. Install Updates will require it.

During 10.04 dev this was the way as well. Then they changed it back to check for password to manually check for updates. Yet it has no problem checking for updates in the background without asking for your password...

---

### Post by zekopeko on 2010-06-08
> **23meg said:**
> Right, that's how U-M worked three cycles ago in the development branch when it had the Aptdaemon backend enabled for a short while.

So is U-M going to transition to aptdaemon in Maverick?

---

### Post by ronacc on 2010-06-08
a simple way to avoid the problem is don't use UM , use synaptic , you give your password to start it and then nevermore .

---

### Post by zekopeko on 2010-06-08
> **ronacc said:**
> a simple way to avoid the problem is don't use UM , use synaptic , you give your password to start it and then nevermore .

That's avoiding the "problem".

---

### Post by ranch hand on 2010-06-08
> **zekopeko said:**
> That's avoiding the "problem".
It sure is.  The problem is Update Mangler and it is real good to avoid.

I just uncheck the bugger in atartup apps and uncheck the check for updates daily box in software sources on ALL my installs first thing.  Problem solved.

---

### Post by zekopeko on 2010-06-08
> **ranch hand said:**
> It sure is.  The problem is Update Mangler and it is real good to avoid.

I just uncheck the bugger in atartup apps and uncheck the check for updates daily box in software sources on ALL my installs first thing.  Problem solved.

That is very unhelpful of you. At least you are consistent :D

---

### Post by Jordanwb on 2010-06-08
> **zekopeko said:**
> That's avoiding the "problem".

I do not understand. You think avoiding an annoying program is bad? When I install Ubuntu the first thing I do is disable Update Manager in the startup apps because it bugs me every few minutes to install an update for gedit (or some other non-life-critical program such as everything).

I like Mint's update manager. It sits in the notification tray behaving itself and if there are updates its icon becomes a blue flag, if there are no updates it shows a green checkmark. It doesn't interrupt me and for that alone I love it.

---

### Post by Merk42 on 2010-06-08
> **Jordanwb said:**
> I do not understand. You think avoiding an annoying program is bad? 
When you're running an OS for the purpose of **testing** yes.

---

### Post by 23meg on 2010-06-08
> **ranch hand said:**
> It sure is.  The problem is Update Mangler and it is real good to avoid.

I just uncheck the bugger in atartup apps and uncheck the check for updates daily box in software sources on ALL my installs first thing.  Problem solved.

Why? What specific problems have you had with it in stable releases?

---

### Post by ranch hand on 2010-06-08
> **23meg said:**
> Why? What specific problems have you had with it in stable releases?
I have to admit to quiting it as a bad deal back in 8.04 so it is possible that it has improved since then.

That said, it ran updates that screwed my system 3 times.  I can't be more specific as I was very fresh at that time and didn't have a clue.  I am glad that I had taken to dual booting with 8.04 and tried everything on my "playtime" install before doing it to my main install.

I also do not like at all the updating of my packages list automatically a bit.

If there are updates I do not want it is a pain in the butt to uncheck them in UM.  As a noob, I found it much easier to use synaptic where you check the ones you want.

I was and is also nice to be able to actually learn something about your system while doing upgrades and synaptic gives you a gui that will tell you things you may want to know and possibly should know.

I realize that the idea is to dumb down the gui of the OS to the level that the average MS user can deal with.  I am not sure this is a wise thing to do.  I would prefer an approach that makes it easier to learn to control your own system.

That is the strength of Linux and I think we should go with that rather than a free version of what has already been done and irritates folks with the ability to think for them selves.

I do not push this idea because I am not sure how to approach the self education enhancement problem so I have nothing to offer but a whine.

Update Mangler, on the other hand, I object to on principle and as an unreliable (in my experience) application.  It is not something that I would recommend to anyone starting out and no one else needs it.

I therefore feel no remorse at all in not testing it.  I do not use it in normal use and I think that is the way we need to test the system.

I also do not even look at the games.  I have a deck of cards AND a table.

---

### Post by mc4man on 2010-06-09
While I think synaptic is best for package management and gathering info  - particularly when building or looking for useful additions there is nothing wrong with um and it is quite useful in itself.
(And I believe the best 'first stop' in updating.

> I also do not like at all the updating of my packages list automatically a bit.

There is nothing about the um that requires "automatically", you are free to pick thru like in synaptic.

> to actually learn something about your system while doing upgrades and synaptic gives you a gui that will tell you things you may want to know and possibly should know.

While synaptic is clearly best info wise, um also provides useful info - most times the chanelogs are right there to view- I get the feeling based on some threads and posts many never bother to read thru them.
> 
Update Mangler, on the other hand, I object to on principle and as an unreliable (in my experience) application

I've never found it to be "unreliable", actually just the opposite and quite 'safe' to use, - the only exception is clicking yes on a 'partial upgrade' pop up.
Making a distinction between  that and just letting um install packages it's marked as 'installable which has never caused an issue here. (and really can't..

> I do not want it is a pain in the butt to uncheck them in UM.
right click - uncheck all

---

### Post by ranch hand on 2010-06-09
While we obviously disagree on UM in general, I have to agree that the level of willing literacy seems awfully low.

I know that I have been guilty of this at times myself.  Some folks just seem to object to reading anything.

On the other hand they do not seem to mind complaining, at length, about the results of not reading.

---

### Post by Longinus00 on 2010-06-09
update-manager is more or less an improved apt-get upgrade. It shows both a description of the package and the changelog associated with the update. Synaptic might let you see what files a package installs or what dependencies it has but I'm not sure how that's useful when you're just upgrading bugfix versions.

I'm also curious as to what types of upgrades people are skimping on. If you actually need that type of fine grained control in the first place then why not forbid or hold/lock the package?

> **Jordanwb said:**
> I do not understand. You think avoiding an annoying program is bad? When I install Ubuntu the first thing I do is disable Update Manager in the startup apps because it bugs me every few minutes to install an update for gedit (or some other non-life-critical program such as everything).

I like Mint's update manager. It sits in the notification tray behaving itself and if there are updates its icon becomes a blue flag, if there are no updates it shows a green checkmark. It doesn't interrupt me and for that alone I love it.

There is a gconf key to revert the behavior to the good old days. Then you can use update manager like you were used to.

---

### Post by zekopeko on 2010-06-09
> **ranch hand said:**
> I have to admit to quiting it as a bad deal back in 8.04 so it is possible that it has improved since then.

That said, it ran updates that screwed my system 3 times.  I can't be more specific as I was very fresh at that time and didn't have a clue.  I am glad that I had taken to dual booting with 8.04 and tried everything on my "playtime" install before doing it to my main install.

I also do not like at all the updating of my packages list automatically a bit.

If there are updates I do not want it is a pain in the butt to uncheck them in UM.  As a noob, I found it much easier to use synaptic where you check the ones you want.

I was and is also nice to be able to actually learn something about your system while doing upgrades and synaptic gives you a gui that will tell you things you may want to know and possibly should know.

Your wants don't align with what the majority of casual users want. A casual user wants to do a specific task as easily as possible. The computer should be there to help her accomplish that without requiring a huge time investment.
I probably have more computer experience and knowledge then you but I value simplicity in a good design.  

> I realize that the idea is to dumb down the gui of the OS to the level that the average MS user can deal with.  I am not sure this is a wise thing to do.  I would prefer an approach that makes it easier to learn to control your own system.

That is the strength of Linux and I think we should go with that rather than a free version of what has already been done and irritates folks with the ability to think for them selves.

This is what YOU think is the goal. That isn't correct. The point isn't to "dumb down" the experience but to make it more streamlined and user friendly. User friendly doesn't equal more options and complexity in the system. That is yet again your flawed perception of the situation.

> I do not push this idea because I am not sure how to approach the self education enhancement problem so I have nothing to offer but a whine.

The majority of users don't want to spend an excessive amount of time learning something. They want to do something not fight with their system.

> Update Mangler, on the other hand, I object to on principle and as an unreliable (in my experience) application.  It is not something that I would recommend to anyone starting out and no one else needs it.

I therefore feel no remorse at all in not testing it.  I do not use it in normal use and I think that is the way we need to test the system.

I also do not even look at the games.  I have a deck of cards AND a table.

Just above you pointed out that you haven't used UM for the past two years. So you calling it "Update Mangler" isn't honest, constructive criticism, even when you point out what you don't like, since you have non to offer.

---

### Post by Slug71 on 2010-06-09
Well i dont have a problem with UM but if packagekit.d replaces aptdaemon the i hope Software Update replaces UM. I actually prefer it over UM and its easy to uncheck updates you dont want.

---

### Post by zekopeko on 2010-06-09
> **Slug71 said:**
> Well i dont have a problem with UM but if packagekit.d replaces aptdaemon the i hope Software Update replaces UM. I actually prefer it over UM and its easy to uncheck updates you dont want.

Thankfully, I think, that won't happen.

---

### Post by philinux on 2010-06-09
Just installed alpha1 64bit from the daily builds and UM only asked for password once.

Also looking good with new gui. Download rate from the servers not to good.:shock:

---

### Post by Jordanwb on 2010-06-09
> **Merk42 said:**
> When you're running an OS for the purpose of **testing** yes.

I agree but update-manager has always been annoying as long as I can remember.

---

### Post by seeker5528 on 2010-06-09
> **mc4man said:**
> There is nothing about the um that requires "automatically", you are free to pick thru like in synaptic.

It was the automatic updating of the package lists that was the annoyance.

You can disable the scheduled check for updates.

When you run update-manager it automatically updates the list at various times, if there is a way to disable this, I don't know what it is.

Not a big deal when sticking with the stable release, you don't expect a bunch of changes, much less new stuff, every day.

My problem with this during a development release is that I like to see what packages are new, which Synaptic shows you. Problem being, Synaptic doesn't know which packages are new if the package lists were updated by another program.

So if update-manager, Software Center, etc.... update the lists and Desktop Nova happened to be added to the repository at that particular time, Synaptic won't see it as a new package the next time you run it and not likely to recognize it as new the next time there is an update for it either.

If you were following along in Synaptic when Desktop Nova was added and you happened to be looking for something to replace wallpaper-tray, then you could see it in that list of new packages and see > DesktopNova changes the desktop background image after an adjustable time.
It can choose the images from single files and folders (with or without
subfolders). An autostart feature is also implemented. hmmm, maybe it doesn't do something wallpaper-tray did but maybe it's worth checking out.

Later, Seeker

---

### Post by VastOne on 2010-06-21
> **ranch hand said:**
> Update Mangler, on the other hand, I object to on principle and as an unreliable (in my experience) application.  It is not something that I would recommend to anyone starting out and no one else needs it.

Ranch Hand...

Just wanted to say thank you for the heads up on UM.  After reading of your experiences, I started taking a closer look at what was going on and will say that apt-get update and apt-get upgrade are a hell of lot better for what I need and parses what I do not need.

Thanks

:guitar:

---

### Post by ranch hand on 2010-06-21
Apt will hold things back that are safe to upgrade.  Synaptic, with all but the last box checked in Settings>Preferences>General, will be a real good guide to what you can install.

New kernels, for instance, are always held by apt because they require the installation of other packages.  This type of package is generally safe to upgrade.  The upgrades for the Rhythbox packages is a good example currently.

Synaptic will also (with all that stuff checked) give recommendations on dealing with "broken" packages.  I like to read those (or any error messages from synaptic) before attacking a problem, usually in terminal with dpkg commands.

---

### Post by seeker5528 on 2010-06-21
> **ranch hand said:**
> New kernels, for instance, are always held by apt because they require the installation of other packages.  This type of package is generally safe to upgrade.  The upgrades for the Rhythbox packages is a good example currently.

Installing upgrades that have new dependencies is by definition, unsafe, from a 'do the safe version of select all' standpoint.

There is no way in the packaging to differentiate a kernel metapackage that depends on a new kernel image package with a new ABI number in it's name from any other type of package that wants to install something new.

So if the safe option is chosen, it is correct behavior not to install those.

Similarly there is no built in to the apt utilities mechanism to indicate available packages are bad. That's why in Debian it is suggested to install apt-listbugs when running Debian testing/unstable, which is specific to the Debian bug tracking system, so not useful in Ubuntu.

Update Manager seems not to always show the user all the updates that are available, so there may be something specific to Update Manager that can be used in cases where something is found to be bad or some other situation like maybe putting a hold on a group of packages until the entire group hits the archive. If so this behavior is probably more useful during a stable release than in a development cycle.

Later, Seeker

---

