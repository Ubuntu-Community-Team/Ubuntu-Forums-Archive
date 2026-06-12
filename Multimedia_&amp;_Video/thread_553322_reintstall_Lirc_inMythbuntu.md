---
title: "reintstall Lirc inMythbuntu?"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by DwalerXIII on 2007-09-17
I installed Mythbuntu alpha 4. Everything worked till I was so stupid to mess with it in the Control Center.](*,)
I have a Hauppauge 350 pvr and when installing Mythbuntu I chose the Hauppauge TV card remote.
The remote worked. But in the Control Centre under “Remote Control”, the option  'Genererate Application & Remote Specific Lirc Configuration' was not enabled. I was curious and enabled it.
Mythbuntu reconfigured my remote but the proces hang so I had te restart my PC.

From then on every button on my remote reacts twice in Mythbuntu and not every button reacts when playing video. (volume buttons ...)

How can this be undone? Can I do a clean reinstall of Lirc so all the configuration files will be reset?

---

### Post by superm1 on 2007-09-18
> **DwalerXIII said:**
> I installed Mythbuntu alpha 4. Everything worked till I was so stupid to mess with it in the Control Center.](*,)
I have a Hauppauge 350 pvr and when installing Mythbuntu I chose the Hauppauge TV card remote.
The remote worked. But in the Control Centre under “Remote Control”, the option  'Genererate Application & Remote Specific Lirc Configuration' was not enabled. I was curious and enabled it.
Mythbuntu reconfigured my remote but the proces hang so I had te restart my PC.

From then on every button on my remote reacts twice in Mythbuntu and not every button reacts when playing video. (volume buttons ...)

How can this be undone? Can I do a clean reinstall of Lirc so all the configuration files will be reset?
Update all of your packages, there is a newer control centre and a newer lirc generator.  If you have it regenerate those files again, the problems should go away.

---

### Post by DwalerXIII on 2007-09-22
excuse me for replying a little late.

I installed the updates and regenerated again the Lirc confuguration but this din't solve the problem.
Just reinstalled  mythbuntu.

---

### Post by e1jones on 2007-09-24
I had the same problem actually.  Did the fresh install, then updated and had it create the LIRC file again.  Which produced the same strange remote activity.  Haven't had time to play with it in a week, so its somewhat out of date if theres a more recent version.

Using the remote from the retail PVR-150 MCE box...

---

### Post by superm1 on 2007-09-24
> **e1jones said:**
> I had the same problem actually.  Did the fresh install, then updated and had it create the LIRC file again.  Which produced the same strange remote activity.  Haven't had time to play with it in a week, so its somewhat out of date if theres a more recent version.

Using the remote from the retail PVR-150 MCE box...
There have been updates since then.  Also a new mythbuntu disk should be within the next 1-2 weeks hopefully.

---

### Post by e1jones on 2007-10-01
I tried upgrade/update again.  Tried to get the control panel to regenerate the LIRC, but the remote wasn't responding at all.

Re-installed with the 070830 i386 iso.  Off fresh install the remote worked ok, but as soon as I did the upgrade/update it broke again.  And the LIRC generator thing doesn't help it.

Not sure if its a known issue....

---

### Post by superm1 on 2007-10-01
> **e1jones said:**
> I tried upgrade/update again.  Tried to get the control panel to regenerate the LIRC, but the remote wasn't responding at all.

Re-installed with the 070830 i386 iso.  Off fresh install the remote worked ok, but as soon as I did the upgrade/update it broke again.  And the LIRC generator thing doesn't help it.

Not sure if its a known issue....
You had version (0.6) of the control centre right?  The re-generation should have been fixed in there.

---

### Post by e1jones on 2007-10-01
I did a fresh upgrade/update, however, I don't know what version it pulled in.  If 0.6 is in the normal gutsy repos, it should have grabbed it I believe?  I didn't add any special repos otherwise, so if there is one i should add...

I'll have to check specifically tonight when I get home on the version.

---

### Post by superm1 on 2007-10-01
> **e1jones said:**
> I did a fresh upgrade/update, however, I don't know what version it pulled in.  If 0.6 is in the normal gutsy repos, it should have grabbed it I believe?  I didn't add any special repos otherwise, so if there is one i should add...

I'll have to check specifically tonight when I get home on the version.
Yes 0.6 is the version in the gutsy repos (as of a day or two ago).  0.7 is uploaded right now and fixes a few other items that were found (unrelated to lirc).  

What exactly is happening now, still the double keypresses?  Those should go away with the control centre when you hit regenerate.

---

### Post by e1jones on 2007-10-02
Ok.  Upgraded from 0.6 to 0.7 last night.  Ran the regenerate script, but the remote doesn't do anything still.  No response to any input at all.  Same thing that happened after i upgraded from the fresh install to 0.6.

I tested the remote immediately after the fresh install (friday) and it worked as expected.  But as soon as I updated/upgraded everything it became non-responsive.  I think theres a different issue here now, though previously I did experience the double keypress, but no more.

---

### Post by superm1 on 2007-10-02
> **e1jones said:**
> Ok.  Upgraded from 0.6 to 0.7 last night.  Ran the regenerate script, but the remote doesn't do anything still.  No response to any input at all.  Same thing that happened after i upgraded from the fresh install to 0.6.

I tested the remote immediately after the fresh install (friday) and it worked as expected.  But as soon as I updated/upgraded everything it became non-responsive.  I think theres a different issue here now, though previously I did experience the double keypress, but no more.
Hm well this isn't good.  I guess time to start going down the debugging path:

What remote?
Does /etc/lirc/lircd.conf look like the right setup?
Does irw work?

---

### Post by e1jones on 2007-10-02
The remote is from the PVR-150 MCE set, using the new version in LIRC.

I'll have to check the rest tonight when i get home and hope i remember how :p I've run irw on another set up, but I'll have to post the /etc/lirc/lircd.conf because I don't know what I'm looking for.

---

### Post by e1jones on 2007-10-03
Strange.

Ran /etc/init.d/lirc start  ... returned message that it couldn't find it, should install lirc-modules-source,  and irw wouldn't work.  Tried dmesg | grep -i lirc and got nothing. 

lircd.conf looked like it was set up for (new) Philips et al mceusb remote, which is the one i had working previously.

Now, off a fresh install on friday, the remote worked up until i ran apt-get update & apt-get upgrade.  as of last night the system was updated to mythbuntu control center 0.7, and the remote was still missing.

---

### Post by superm1 on 2007-10-03
> **e1jones said:**
> Strange.

Ran /etc/init.d/lirc start  ... returned message that it couldn't find it, should install lirc-modules-source,  and irw wouldn't work.  Tried dmesg | grep -i lirc and got nothing. 

lircd.conf looked like it was set up for (new) Philips et al mceusb remote, which is the one i had working previously.

Now, off a fresh install on friday, the remote worked up until i ran apt-get update & apt-get upgrade.  as of last night the system was updated to mythbuntu control center 0.7, and the remote was still missing.

Um lirc-modules-source isn't needed at all.  how about this:

sudo apt-get install --reinstall lirc 

perhaps?  You'll get your init script back at least.

---

### Post by e1jones on 2007-10-03
ran 'sudo apt-get install --reinstall lirc', which gave me

#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################

so went and did LOAD_MODULES=false in /etc/lirc/hardware.conf

tried running 

sudo apt-get install --reinstall lirc

again, failed.  entering irw doesn't give a message (it had been giving a failure message), but there is no response to remote input either.

---

### Post by morgwon on 2007-10-03
what exactly is updating? does it update your kernel? If so then you have to rebuild lirc. What is the output of ls -l /dev/l*? if you don't see lirc or lirc0 then I suspect you updated the kernel and need to rebuild lirc.

---

### Post by superm1 on 2007-10-03
> **e1jones said:**
> ran 'sudo apt-get install --reinstall lirc', which gave me

#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################

so went and did LOAD_MODULES=false in /etc/lirc/hardware.conf

tried running 

sudo apt-get install --reinstall lirc

again, failed.  entering irw doesn't give a message (it had been giving a failure message), but there is no response to remote input either.
Okay, can you try to modprobe lirc_i2c?  There has to be a sensible reason why it's not loading.

---

### Post by e1jones on 2007-10-03
response to running modprobe lirc_i2c is 'module lirc_i2c not found'

to running ls -l /dev/l* : /dev/lircd, and some others that aren't related.

as for what it updated... probably everything, since it is gutsy based.  anything that got added to those repos likely was changed.  so yes, probably a few kernel changes.  But would running the control panel script to regenerate the lirc stuff fix it after changing the kernel or not?

---

### Post by superm1 on 2007-10-03
> **e1jones said:**
> response to running modprobe lirc_i2c is 'module lirc_i2c not found'

to running ls -l /dev/l* : /dev/lircd, and some others that aren't related.

as for what it updated... probably everything, since it is gutsy based.  anything that got added to those repos likely was changed.  so yes, probably a few kernel changes.  But would running the control panel script to regenerate the lirc stuff fix it after changing the kernel or not?

Well lirc_i2c is shipped in linux-ubuntu-modules-2.6.22.  Do you have that package installed?

---

### Post by e1jones on 2007-10-03
linux-ubuntu-modules-2.6.22-12.32 is installed. as is 10.25

---

### Post by superm1 on 2007-10-03
> **e1jones said:**
> linux-ubuntu-modules-2.6.22-12.32 is installed.

Are you somehow missing the module then?

On my box this is where it shows up:

supermario@portablemario:/lib/modules/2.6.22-12-generic$ find ./ -name lirc_i2c.ko
./ubuntu/media/lirc/lirc_i2c/lirc_i2c.ko


perhaps depmod -a or reinstall l-u-m

---

### Post by e1jones on 2007-10-03
as far as I can tell its missing.  But i'm no expert by any means.  Unless theres a better way to figure out if its there or not...

sorry but 'perhaps depmod -a or reinstall l-u-m' is kinda over my head :p

---

### Post by superm1 on 2007-10-03
> **e1jones said:**
> as far as I can tell its missing.  But i'm no expert by any means.  Unless theres a better way to figure out if its there or not...

sorry but 'perhaps depmod -a or reinstall l-u-m' is kinda over my head :p

Try this:
> sudo apt-get install --reinstall linux-ubuntu-modules-2.6.22-12-generic 

---

### Post by e1jones on 2007-10-04
ok...

ran that, and it has failures on lirc.

> setting up lirc (0.8.2-0ubuntu7) ...
* reloading kernel event manager ...
/etc/lirc/hardware.conf: 1 #: not found
dpkg: error processing lirc (--configure):
subprocess post-installation script returned error exit status 127

> Errors were encountered while processing: lirc
E: sub-process /usr/bin/dpkg returned an error code (1)

so, out of curiosity... since there is a new ISO available, should I just install that and see how it works?  kinda shortcuts any bug fixing this might help... but i've got nothing usefull to loose by reinstalling the latest ISO.

---

### Post by superm1 on 2007-10-04
> **e1jones said:**
> ok...

ran that, and it has failures on lirc.





so, out of curiosity... since there is a new ISO available, should I just install that and see how it works?  kinda shortcuts any bug fixing this might help... but i've got nothing usefull to loose by reinstalling the latest ISO.
Whew yuck.  i hope other people don't run into such a mess.

```
sudo apt-get remove --purge lirc
```

followed by

```
sudo apt-get install mythbuntu-control-centre
```

Will regenerate that hardware.conf

I would really recommend just going for the new iso though.  It's got a ton of other fixes and a new admin env to use, should be a lot less painful (in theory :)).

---

### Post by e1jones on 2007-10-04
ran those two and the second one gave me 

################################################## ###
## I couldn't load the required kernel modules ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware. ##
################################################## ###
## If this message is not appropriate you may set ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf ##
################################################## ###

again.  Circles upon circles... 

I'm beginning to think that latest iso is looking might good! :p

---

### Post by gumperoncini on 2007-10-10
I have the same remote and have had multiple issues with lirc in ubuntu. I installed mythbuntu (latest iso) last night and it went without a hitch. I am really afraid to update anything now because it is finally working and your post scared me. 

I really think that the previous poster had a point. if there was a kernel update then you need to rebuild lirc into your new kernel. you can follow the steps in the ubuntu lirc fiesty documentation

good luck!

---

### Post by superm1 on 2007-10-10
> **gumperoncini said:**
> I have the same remote and have had multiple issues with lirc in ubuntu. I installed mythbuntu (latest iso) last night and it went without a hitch. I am really afraid to update anything now because it is finally working and your post scared me. 

I really think that the previous poster had a point. if there was a kernel update then you need to rebuild lirc into your new kernel. you can follow the steps in the ubuntu lirc fiesty documentation

good luck!
Building kernel modules is *NOT* required in gutsy.  They are shipped with gutsy.

Take a look for yourself:

```
supermario@portablemario:/lib/modules/2.6.22-14-generic/ubuntu/media/lirc$ find ./ -name *.ko
./lirc_serial_igor/lirc_serial_igor.ko
./lirc_cmdir/commandir.ko
./lirc_cmdir/lirc_cmdir.ko
./lirc_streamzap/lirc_streamzap.ko
./lirc_mceusb/lirc_mceusb.ko
./lirc_atiusb/lirc_atiusb.ko
./lirc_i2c/lirc_i2c.ko
./lirc_it87/lirc_it87.ko
./lirc_dev/lirc_dev.ko
./lirc_sasem/lirc_sasem.ko
./lirc_serial/lirc_serial.ko
./lirc_ttusbir/lirc_ttusbir.ko
./lirc_mceusb2/lirc_mceusb2.ko
./lirc_imon/lirc_imon.ko
./lirc_bt829/lirc_bt829.ko
./lirc_igorplugusb/lirc_igorplugusb.ko
./lirc_pvr150/lirc_pvr150.ko
./lirc_sir/lirc_sir.ko

```

---

