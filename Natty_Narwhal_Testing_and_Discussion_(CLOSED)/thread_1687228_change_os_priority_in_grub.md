---
title: "change os priority in grub"
date: 2011-02-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-02-13
I have maverick, natty and windows triple boot. I want grub to book maverick as default OS. Maverick Grub is set to boot it as default but i suppose boot is controlled by Natty grub. I tried to change boot order in natty grub by changing the default number but it reverts back to 1. Maverick OS is 5th entry in natty grub. Can you please help me change the default OS.

Thanks.

---

### Post by cariboo on 2011-02-13
Did you run update grub after changing the boot order?

---

### Post by Quackers on 2011-02-13
The grub which is in control will list its own operating system at the top of the grub menu. It's usually the latest installation's grub.
For instance, if the Natty option is the top one in the grub menu (when no manual editing has taken place), then the Natty installed grub is in control.
If you want Maverick's grub to be in control, just boot into Maverick and run
```
 sudo grub-install /dev/sda
```
That is assuming that Maverick is on sda. (Change as necessary).

---

### Post by oldfred on 2011-02-13
Several choices.

You can reinstall grub from Maverick so Maverick grub is in charge and with a sudo update-grub it should find Natty to let you boot it.

You can customize menu in Natty.

Do not know if this works yet in Natty.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Do not know if this works in Natty:
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Or you can manually edit default in grub.cfg.

These are instructions for Windows but should work for anything:
But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by zika on 2011-02-13
We talked about problems with nested approach in Grub... [http://ubuntuforums.org/showpost.php?p=10169056&postcount=681](http://ubuntuforums.org/showpost.php?p=10169056&postcount=681) is the one option I proposed. It is not nice and clean but... I do not use it, myself, now, because I've cleaned my kernels...

---

### Post by donniezazen on 2011-02-13
> **Quackers said:**
> The grub which is in control will list its own operating system at the top of the grub menu. It's usually the latest installation's grub.
For instance, if the Natty option is the top one in the grub menu (when no manual editing has taken place), then the Natty installed grub is in control.
If you want Maverick's grub to be in control, just boot into Maverick and run
```
 sudo grub-install /dev/sda
```
That is assuming that Maverick is on sda. (Change as necessary).

My maverick root is on sda8. When i try to run the above mentioned command i get following error.
> 
sudo grub-install /dev/sda8
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


Thank you all.

---

### Post by Quackers on 2011-02-13
You install grub to the drive, not a partition.
In other words to /dev/sda not /dev/sda8
And there's a space before /dev/sda (it's not too clear to me whether you were leaving one).

---

### Post by donniezazen on 2011-02-13
> **Quackers said:**
> You install grub to the drive, not a partition.
In other words to /dev/sda not /dev/sda8
And there's a space before /dev/sda (it's not too clear to me whether you were leaving one).

thanks /dev/sda worked.

---

### Post by Quackers on 2011-02-13
You're welcome :-)
Don't forget that if grub is updated in a different installation (via synaptic or Update Manager), that one will take control again.
In that event you can boot into Maverick again and re-use this method to put Maverick's grub back in control.

---

### Post by andrewthomas on 2011-02-14
> **Quackers said:**
> You're welcome :-)
Don't forget that if grub is updated in a different installation (via synaptic or Update Manager), that one will take control again.
In that event you can boot into Maverick again and re-use this method to put Maverick's grub back in control.
or you can boot into natty and reconfigure grub from there and install it to its root partition and be done with it

---

