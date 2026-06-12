---
title: "Frustrated with nVidia driver"
date: 2008-04-29
forum: Mythbuntu
---

### Post by yonkiman on 2008-04-29
I've been using Mythbuntu (with an nVidia 6200) for several months and I love it.  However I have had nothing but trouble with the nVidia driver and would like some advice.

First, the only way I have ever been able to get the nvidia driver to correctly drive my 720p component input TV is to select it as the driver *when I install Mythbuntu*.  Whenever I tried to install it after a mythbuntu I could never get it to work.  I have also never been able to use my custom modeline to eliminate overscan - the nvidia driver seems to ignore my xorg.conf file.

Then I did a system update and the nvidia driver stopped working ("Ubuntu is running in low-graphics mode"), so now I just have a low-res 4:3 window.  nvidia-xconfig and nvidia-settings don't fix anything.  Trying to uninstall the driver (so I can reinstall it) fails (it can't delete a file or folder or something).

So I am about to reinstall Mythbuntu from scratch yet again, wasting hours of tweaking.  I'd rather fix the frakking problem (reinstall and properly configure the driver), but given my past results that seems unlikely.  Nonetheless, I thought I'd give one last shout out for some advice before I do it again... 

Cheers!

---

### Post by yfaykya on 2008-04-30
Envy! In hardy I think the package is available as envy-ng. This will take care of installation for you. For 720p (with a 7300G) just use 720p as the modeline in your xorg.conf and if there is some overscan try and use your TV to rid it or use the new mythappearance plugin to reconfigure myth to fit.

---

### Post by volkswagner on 2008-04-30
Two things you can try.

[http://ubuntuforums.org/showthread.php?t=763236&highlight=restricted+modules]("http://ubuntuforums.org/showthread.php?t=763236&highlight=restricted+modules")

[http://ubuntuforums.org/showthread.php?t=711591]("http://ubuntuforums.org/showthread.php?t=711591")

Good Luck!

---

### Post by majoridiot on 2008-04-30
> **yonkiman said:**
> I've been using Mythbuntu (with an nVidia 6200) for several months and I love it.  However I have had nothing but trouble with the nVidia driver and would like some advice.

First, the only way I have ever been able to get the nvidia driver to correctly drive my 720p component input TV is to select it as the driver *when I install Mythbuntu*.  Whenever I tried to install it after a mythbuntu I could never get it to work.  I have also never been able to use my custom modeline to eliminate overscan - the nvidia driver seems to ignore my xorg.conf file.

Then I did a system update and the nvidia driver stopped working ("Ubuntu is running in low-graphics mode"), so now I just have a low-res 4:3 window.  nvidia-xconfig and nvidia-settings don't fix anything.  Trying to uninstall the driver (so I can reinstall it) fails (it can't delete a file or folder or something).

So I am about to reinstall Mythbuntu from scratch yet again, wasting hours of tweaking.  I'd rather fix the frakking problem (reinstall and properly configure the driver), but given my past results that seems unlikely.  Nonetheless, I thought I'd give one last shout out for some advice before I do it again... 

Cheers!

unfortunately, overscan settings are not available for all nvidia gpus yet... so don't bother with
custom modelines.  they will be ignored.

the suggestion to install the drivers with envy is **not** a good idea with mythbuntu, is **not** needed
since the restricted drivers manager will install the latest stable binary in the repos and will most likely 
**not** fix your problems.  installing the nvidia driver with envy is not needed unless you always need to be 
running the bleeding-edge driver and can't compile/install on your own.  it can also complicate upgrades, 
since it is not a standard ubuntu package.

i run into the same problem from time to time and have found that the best way to fix the problem is
by manually editing xorg.conf to at least get it driving 720p, so tweaks can be made.  if you post your
xorg.conf, i'm sure the appropriate changes can be pointed out.

---

### Post by yonkiman on 2008-05-01
It's working now!  Thanks for all the suggestions.  I tried a zillion things, but I think the steps that actually made it work were:

1) Going into "Software Sources" and checking "Proprietary drivers for devices" (I don't know how this got unchecked).

2) Running Synaptic Package Manager and loading "linux-restricted-modules-2.6.24"

3) After a reboot (I booted into a 1024x768 screen with the nvidia driver running), I copied my old 720p xorg.conf file over the current xorg.conf file, and everything was back to normal after another reboot.

There may have been a step between 2 and 3 where I told it to use the nvidia driver - I can't recall.

Thanks again!

---

### Post by stronzo on 2008-05-01
had exact the same problems. nvidiadriver could not be loaded because of the missing restricted modules, which i had to manually reinstall after upgrade to mythbuntu 8.04. and lirc is also not working anymore, still trying to fix it.

---

### Post by superm1 on 2008-05-01
> **stronzo said:**
> had exact the same problems. nvidiadriver could not be loaded because of the missing restricted modules, which i had to manually reinstall after upgrade to mythbuntu 8.04. and lirc is also not working anymore, still trying to fix it.
Make sure that linux-ubuntu-modules is installed

---

### Post by superm1 on 2008-05-01
> **yonkiman said:**
> It's working now!  Thanks for all the suggestions.  I tried a zillion things, but I think the steps that actually made it work were:

1) Going into "Software Sources" and checking "Proprietary drivers for devices" (I don't know how this got unchecked).

2) Running Synaptic Package Manager and loading "linux-restricted-modules-2.6.24"

3) After a reboot (I booted into a 1024x768 screen with the nvidia driver running), I copied my old 720p xorg.conf file over the current xorg.conf file, and everything was back to normal after another reboot.

There may have been a step between 2 and 3 where I told it to use the nvidia driver - I can't recall.

Thanks again!
Can you post your upgrade logs about this?

---

### Post by superm1 on 2008-05-01
> **majoridiot said:**
> unfortunately, overscan settings are not available for all nvidia gpus yet... so don't bother with
custom modelines.  they will be ignored.

the suggestion to install the drivers with envy is **not** a good idea with mythbuntu, is **not** needed
since the restricted drivers manager will install the latest stable binary in the repos and will most likely 
**not** fix your problems.  installing the nvidia driver with envy is not needed unless you always need to be 
running the bleeding-edge driver and can't compile/install on your own.  it can also complicate upgrades, 
since it is not a standard ubuntu package.

i run into the same problem from time to time and have found that the best way to fix the problem is
by manually editing xorg.conf to at least get it driving 720p, so tweaks can be made.  if you post your
xorg.conf, i'm sure the appropriate changes can be pointed out.
Let me add a little bit extra to this post.  For Ubuntu 7.10 and below, Envy did some nasty things from what I understand.  In 8.04 it has entered universe (as envy-ng), and is much more sane.  It uses DKMS to build the modules (like the AMD driver does).  So, install using restricted drivers first, and iff for some reason you need a newer nvidia version, use Envy-ng to get it.

---

### Post by yonkiman on 2008-05-02
> **superm1 said:**
> Can you post your upgrade logs about this?

I don't know what those are.  Tell me what they are and where exactly to find them and I'll post them.

---

### Post by superm1 on 2008-05-03
> **yonkiman said:**
> I don't know what those are.  Tell me what they are and where exactly to find them and I'll post them.
Look in /var/log/dpkg.log and /var/log/update-manager

---

### Post by Daminator on 2008-05-06
I'm having this problem and it's driving me nuts!

I've just spent all night trying every solution I can find any hint to on the net and I've got nowhere. This thread looked promising, but I seem to have everything installed that's mentioned here.

Can anyone suggest anything I can do to sort this out?

My daughter is supposed to be having a 'Cinema' birthday party in a couple of days. If I don't get this system fixed I think my Linux/Myth time is for the chop :-)

Seriously, I just don't know what to do. Can someone tell me what to post to enable someone to help out?

---

