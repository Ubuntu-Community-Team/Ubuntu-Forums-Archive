---
title: "Kubuntu 11.04 How can I install without installing grub2?"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by oldos2er on 2011-04-01
Is it possible to install 11.04 without its bootloader? I already have grub2 installed as part of 10.10, I have no need nor desire for installing Natty's grub2. I got to the 'select a partition for the bootloader' (or words to that effect) in Natty's installation, but there is no 'none of the above' choice. Am I missing something?

---

### Post by Quackers on 2011-04-01
I believe the "no bootloader" option disappeared with 10.10
There are a couple of options perhaps.
You can install grub with Natty to the mbr, then boot into your 10.10 install and run ```
sudo grub-install /dev/sda
``` (if sda is your drive) which will then over-write Natty's version (and make 10.10 the default option in the grub menu).

Alternatively, it may be possible to install grub to a flash drive temporarily. Then you can boot back into 10.10 and run sudo update-grub to update Maverick's grub menu to include Natty. You can then wipe grub from the flash drive.
I haven't tried it, but that may work.

---

### Post by kansasnoob on 2011-04-01
You can also install Natty's grub to its own new / partition (or /boot if you created one) with no harm done. Basically like you'd do if you were going to use Easy-BCD or chainload.

Your Maverick grub2 should pick up the new install just running "update-grub".

NOTE: I personally detest the use of a separate /boot partition, so don't misunderstand me and think you should create one :)

---

### Post by oldos2er on 2011-04-01
> **Quackers said:**
> I believe the "no bootloader" option disappeared with 10.10


That's really a shame. Thank you for the reply.

Thanks, kansasnoob.

---

### Post by Quackers on 2011-04-01
You're welcome. I have no idea why it was decided to do that. After all, in multi-OS systems it is reasonable to not need to install at least the mbr part of grub.

---

### Post by 3Miro on 2011-04-01
Here is what I do:

Say you install Kubuntu on /dev/sda6 (that is your / root folder and I am assuming you don't have a separate /boot), then you install the bootloader on /dev/sda6 also (not /dev/sda)

Then form your other Linux, you can add command for chainloader, i.e.

title Kubuntu 11.04
root (hd0,5)
chainloader +1

This is for Grub1, there is a way to do that in grub2. What would happen is that regular grub would call Kubuntu 11.04 grub, which would then boot the OS. That way you don't have to update main grub every time you get an update to Kubuntu 11.04 kernel.

---

### Post by 3Miro on 2011-04-01
> **Quackers said:**
> You're welcome. I have no idea why it was decided to do that. After all, in multi-OS systems it is reasonable to not need to install at least the mbr part of grub.

Yes, I agree with you. Ubuntu has been getting somewhat unfriendly towards other Linux distros lately. I just hope it is for a good reason.

---

### Post by seeker5528 on 2011-04-01
> **3Miro said:**
> Yes, I agree with you. Ubuntu has been getting somewhat unfriendly towards other Linux distros lately. I just hope it is for a good reason.

How is installing grub to the partition you are installing on instead of the MBR unfriendly to other distributions?

Later, Seeker

---

### Post by kansasnoob on 2011-04-02
> **seeker5528 said:**
> How is installing grub to the partition you are installing on instead of the MBR unfriendly to other distributions?

Later, Seeker

It's really not. The exception is if you really want to keep booting with a specific OS's grub.

I believe you're the one that taught me to use "dpkg-reconfigure grub-pc" to keep a distros grub from reinstalling to the MBR during package updates.

After following a bug fix I can pretty much assure everyone that it's perfectly safe to install grub2 to the partition that contains "/boot", whether it be / or /boot.

The one place you absolutely don't want to install grub2 to is the PBR of any Win OS or boot partition! That breaks Windows!

---

### Post by Quackers on 2011-04-02
I'm sure it's the bit about
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
``` is what could put some people off.
According to Colin Watson, for good reason (re: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)  -  though the circumstances are not the same in that bug report.
quote
```
Well, it's correct - I think the warning is justified. Does GRUB work
for you for the meantime? If so, I don't really consider the warning a
bug since it points to a genuine unreliability in your setup that can
only be fixed by not doing this (for example, many kinds of filesystem
changes will make your system unbootable unlelss you run grub-install
again afterwards).
```
end quote

---

### Post by ronacc on 2011-04-02
> **seeker5528 said:**
> How is installing grub to the partition you are installing on instead of the MBR unfriendly to other distributions?

Later, Seeker

It is unfriendly in that it takes control away from me that I had before and considering that there have been problems in the past about ubiquity not finding other installs and adding them and also randomly putting grub some where it was not told to ,I'd rather just skip it unless it is the first install on the box .

---

### Post by seeker5528 on 2011-04-04
> **kansasnoob said:**
> It's really not. The exception is if you really want to keep booting with a specific OS's grub.

If you are installing grub to the partition you are installing the OS to, it shouldn't have any affect on that other OS's grub.

> **Quackers said:**
> I'm sure it's the bit about
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
``` is what could put some people off.
According to Colin Watson, for good reason (re: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)  -  though the circumstances are not the same in that bug report.

That seems like a typical 'If you don't know what you are doing, you better think twice' kind of warning.

I expect grub 2 with a blocklist is not any less reliable than pre-grub2 grub.

> **ronacc said:**
> It is unfriendly in that it takes control away from me that I had before

You may consider that to be unfriendly to *you* but that is not the same as being unfriendly to other distributions.

> and considering that there have been problems in the past about ubiquity not finding other installs

That would be a bug.

Do the installers in these other distributions never have problems finding other OS boot partitions while they are going through their development cycles?

> and also randomly putting grub some where it was not told to ,I'd rather just skip it unless it is the first install on the box .

Spamming partitions with copies of grub was a bug. Which I believe was all or none, not some random place, but the file systems used may also have determined which partitions it spammed, which could have made it seem random.

On one hand it seems odd to me that the option not to install to the MBR would be taken away.

On the other hand choosing not to install grub in the MBR seems like an advanced option, so removing the option from the normal set up, resulting in you having to click on the advanced button at the end of the install in order to not have it installed in the MBR, doesn't seem so odd.

Assuming you still have to specify the location as 'hd(X,X)', has anyone tried to specify 'hd()' to see if it gives an error?

It would be nice if when choosing advanced you had a list of the locations and you could just check/uncheck the locations you want/don't want. If it did than not having a separate option to choose whether to install to the MBR would be a non-issue. 

But then again that may not be sufficiently scary to get those people to bail who think they *have* to choose something, so always check a box even if there is only one box that can either be checked or unchecked. :twisted:

Later, Seeker

---

### Post by iClouseau88 on 2011-04-04
I am looking for the same answer as the original poster.  I did install Ubuntu 11.04 beta1 and put grub(2) boot loader in the root partition of /dev/sdax in a multi-OS system but after rebooting I do not see any Grub menu, just 11.04 beta1!

---

### Post by ranch hand on 2011-04-04
If you install to the root partition of the OS you are installing you should never see grub fro m that install at all.  To see grub it has to be on the MBR as that is where bios looks for it (or GBR {or what ever that mac uses}).

If you instructed the installer to install on the / partition of your new installation, and you ended up using that grub, that is a bug with the installer as it installed on the MBR.

---

### Post by beew on 2011-04-05
> **oldos2er said:**
> Is it possible to install 11.04 without its bootloader? I already have grub2 installed as part of 10.10, I have no need nor desire for installing Natty's grub2. I got to the 'select a partition for the bootloader' (or words to that effect) in Natty's installation, but there is no 'none of the above' choice. Am I missing something?

No, there is no option for not installing bootloader for Ubuntu apparently. But if you choose to install the bootloader into the partition where you install Natty instead of the drive then Maverick would retain control over grub (i.e install the bootloader in sda2, say, instead of just sda)

I have a dual boot system with Maverick and Natty beta (actually quadruple boot with Fedora and another Linux distro called qomo) like that and Maverick controls grub (I have been running Natty since alpha 2 so the boot configuration is stable even after numerous Natty updates)

---

### Post by beew on 2011-04-05
> **Quackers said:**
> 

Alternatively, it may be possible to install grub to a flash drive temporarily. Then you can boot back into 10.10 and run sudo update-grub to update Maverick's grub menu to include Natty. You can then wipe grub from the flash drive.
I haven't tried it, but that may work.


Ah! Tried that. It didn't work. In the last step of install the installer would tell you the destination is not allowed and prompt you to make another choice.

---

### Post by iClouseau88 on 2011-04-09
Hello,

I am thinking of trying to install 11.04 beta1 again in a multiboot system where openSUSE 11.4 (GRUB1) controls the booting of Win 7, Fedora and previously Ubuntu 10.10.  This time instead of putting (Grub2) bootloader in the root partition of 11.04 beta1, can I or should I put the boot loader in the root partition of openSUSE 11.4, then once I see the Grub menu, get into openSUSE to edit its /etc/grub/menu.lst file in order to be able to boot Natty?  

Thanks in advance.

---

### Post by Starks on 2011-04-09
Alternate CD install has optional GRUB, right?

---

### Post by cariboo on 2011-04-10
> **iClouseau88 said:**
> Hello,

I am thinking of trying to install 11.04 beta1 again in a multiboot system where openSUSE 11.4 (GRUB1) controls the booting of Win 7, Fedora and previously Ubuntu 10.10.  This time instead of putting (Grub2) bootloader in the root partition of 11.04 beta1, can I or should I put the boot loader in the root partition of openSUSE 11.4, then once I see the Grub menu, get into openSUSE to edit its /etc/grub/menu.lst file in order to be able to boot Natty?  

Thanks in advance.

I'd suggest you install grub to the partition you install Natty on, then boot into openSUSE, and edit /boot/grub/menu.lst to reflect where Natty is. 

I'm so used to grub2 detecting OSs automatically, I've forgotten if grub-legacy automatically detects other operating systems.

---

### Post by iClouseau88 on 2011-04-10
Hello cariboo907,

Thanks for your reply.  When I first upgraded from Maverick to Natty, direct upgrade caused a text-only login.  In the second attempt via a clean install, I chose the third choice ("something else"), did a custom installation to put grub in the root partition of the (Maverick) Ubuntu partition as I used to many times.  In previous Ubuntu installations there were no problems at all.  From Suse's Grub menu I could boot into openSUSE (default) then edit its /boot/grub/menu.lst to enable booting into Ubuntu as one of the OS choices. However, this time after reboot I did not see any grub menu at all so I could not boot into openSUSE, Fedora or Windows.  I only saw Natty.

---

### Post by cariboo on 2011-04-10
You could use your openSUSE live CD to repair grub-legacy, using the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

