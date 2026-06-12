---
title: "not booting after update"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by hislordship on 2010-10-02
Hello, sorry for not writing this very technically, I'm not familiar with all the jargon

I had been using lucid lync and did the update through pressing alt F2 , entering update-manager -d and then selecting distribution update in the update manager.

Now that all is done my computer won't restart properly. I don't get the graphic interface at all. 

Instead I am being prompted to enter my login and password. If I do that it says (still no graphic interface):

hislordship@thrumptoncastle:~$


What am I supposed to enter here to get my computer started again???? hislordship is my login and thrumptoncastle the name of the computer

I'd really appreciate it if someone more experienced than I am could help me out. I wish I'd be more patient and could have held out until the official release date:-(

---

### Post by hislordship on 2010-10-02
[QUOTE=hislordship;9916362]Hello, sorry for not writing this very technically, I'm not familiar with all the jargon

I had been using lucid lync and did the update through pressing alt F2 , entering update-manager -d and then selecting distribution update in the update manager.

Now that all is done my computer won't restart properly. I don't get the graphic interface at all. 

Instead :
"Ubuntu maverick (development branch) thrumptoncastle tty1
thrumptoncastle login: "

When I enter that it asks for the password
than

"Welcome to Ubuntu!
0 packages can be updated.
0 updates are security updates.

hislordship@thrumptoncastle:*$"


If I do that it says (still no graphic interface):

hislordship@thrumptoncastle:~$


What am I supposed to enter here to get my computer started again???? hislordship is my login and thrumptoncastle the name of the computer

I'd really appreciate it if someone more experienced than I am could help me out. I wish I'd be more patient and could have held out until the official release date:-(

---

### Post by hislordship on 2010-10-02
sorry I posted this twice instead of editing the first one and now I can't delete the first post....

---

### Post by dino99 on 2010-10-02
from there: hislordship@thrumptoncastle:~$

run:

sudo nano /etc/apt/sources.list

change "lucid" by "maverick" on every line related to "main", "update", "universe", "multiverse", "restricted"

comment with # all the extra line(s) if any

save and exit from nano

then:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

Now getting Maverick:
sudo apt-get update
sudo apt-get upgrade

removing xorg.conf:
sudo rm -f /etc/X11/xorg.conf
reboot

---

### Post by hislordship on 2010-10-02
Wow - I don't understand how people get their head around this! Sorry for having to as you to dumb that down even more...

I have done
sudo nano /etc/apt/sources.list

it doesn't say "lucid" anywhere though - always maverick. Do you mean I should erase "maverick" and replace it by "lucid"?

what do you mean by this:
"
comment with # all the extra line(s) if any"? Put a number sign in front of the empty lines?

what does save and exit from nano mean?

---

### Post by hislordship on 2010-10-02
I'm feeling really bad for having to depend on your help here guys. People who don't know much about computers really shouldn't try and change anything to their computers. Sorry!

---

### Post by hislordship on 2010-10-02
This is what I'm getting when running startx:

Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/") to make sure that you have the latest version Markers: (--) probed, (**) from config file, (==) default setting, (WW) warning, (EE) error, (NI) not implemented, (??) unknown. (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 2 22:11:21 2010 (==) Using sysstem config directory "/usr/share/x11/xorg.conf.d" (EE) open /dev/fb0: No such file or directory (EE) intel (0): No kernel modessetting driver detected. (EE) Screen(s) found, but non have a usable configuration.
Fatal server error: no screens found
Please consult the The X.Org Foundation support  at http;//wiki.x.org for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
ddxSigGivup: Closing log giving up
xinit: No such file or directory (errno 2): unabel to connect to X server xinit: No such process (errno 3): Server error.
hislordship@thrumptoncastle:~$

---

### Post by florus on 2010-10-02
Since Dino99 is offline, I will try to help.
> it doesn't say "lucid" anywhere though - always maverick. Do you mean I should erase "maverick" and replace it by "lucid"?
No, you want it to say maverick.
> comment with # all the extra line(s) if any"? Put a number sign in front of the empty lines?
Putting a hash symbol in front of a line stops the computer executing the instruction on that line. It is a way of including comments in a piece of code, hence it is referred to as 'commenting out a line'.
My advice would be to just work through Dino99's instructions. He is a lt more expert than I am.:)

---

### Post by VMC on 2010-10-02
Sounds like your having video issues. Is that intel video graphics card you have?

Did you remove xorg configuration file:

```
sudo rm -f /etc/X11/xorg.conf

```

After that reboot, then when you see grub menu, select the correct line and push E for edit. Then find the line beginning with "linux". Go the the end and remove quiet, then push Ctrl+x(to boot). Look for any error messages.

---

### Post by hislordship on 2010-10-02
Thank you very much Florus, very nice of you to try and help

I think that Dino made his recommendation on a wrong assumption though: that it still says lynx, not maverick. So following his recommendation doesn't make any sense...

---

### Post by hislordship on 2010-10-02
Thanks a lot VMC!!!

But how do I get from here: 
hislordship@thrumptoncastle:~$ to the grub menu?

---

### Post by VMC on 2010-10-02
> **hislordship said:**
> Thanks a lot VMC!!!

But how do I get from here: 
hislordship@thrumptoncastle:~$ to the grub menu?

If you reboot, don't you see the grub menu?

Or do you mean how to reboot from the shell prompt"$"?

Ctrl+Alt+Delete, should reboot the system.

---

### Post by hislordship on 2010-10-02
I'm giving up. I throw the computer away.

---

### Post by sdowney717 on 2010-10-02
Sometimes just doing a fresh install is easiest way to go forward!

> don't you see the grub menu?


he might not. A few distros ago, I had to edit grub configuration to show me the menu with the kernel list.

---

### Post by hislordship on 2010-10-02
yeah thanks...i am just reinstalling lucid lynx. all my data will be lost. 

Thanks for all who've been trying to help.

To the developers who ask people to test this stuff and then aren't there when they get into trouble: this is crab.

---

### Post by florus on 2010-10-02
If you are re-installing, create separate partitions for your home and root directories. Then, should you need to reinstall at any time in the future, your data will not be lost.

---

### Post by 23dornot23d on 2010-10-02
By choosing a separate partition ..... you can still get to access all of the DATA .... 

once you have re-installed the 10.04 version in a clean partition - but by not altering the original partition in any way you can still get to your DATA.

[COLOR=Blue]Seems drastic steps to do either of the things you have mentioned previously .....[/COLOR]


The way I use that can install any version of Linux and **leave your data untouched** ....

Install any other or previous version of a Linux Operating System into a separate new partition use the same username and you can access the **data** from this other linux install ..... as long as you are not trying to read a ext4 partition from a release that does not support that file system 
( some of the earlier LINUX versions only read (8.04 - 8.10 - 9.04 - 9.10 )...... ext3 and do not see the ext4 partitions ) 10.04 is ok though Lucid Lynx.

---

### Post by Catharsis on 2010-10-02
That error in Xorg.0.log means you don't have KMS enabled. You need to enable it by holding down Shift while booting to get to GRUB. Then highlight your kernel, hit 'e', and then type 'i915.modeset=1' after "quiet splash". Ctrl+x to boot.

Also, what graphics card do you have?
```
lspci | grep VGA
```

---

### Post by kansasnoob on 2010-10-02
> **hislordship said:**
> I'm giving up. I throw the computer away.

After 5 hours :confused:

An RC is still a development release :)

---

### Post by kansasnoob on 2010-10-02
> **hislordship said:**
> yeah thanks...i am just reinstalling lucid lynx. all my data will be lost. 

Thanks for all who've been trying to help.

To the developers who ask people to test this stuff and then aren't there when they get into trouble: this is crab.

There is no reason you should have to lose all of your data unless your hard drive is seriously out of space.

I test a lot, not so much recently due to time constraints, but it's very easy to transfer data from one OS to another if you learn to multi-boot. Since "blkid" displays labels this will give you an idea how complex you can go:

```
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="d252929b-949d-432e-a18c-18f9ae770d28" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" TYPE="ext3" 
/dev/sda9: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Squeeze" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="Pure Gnome" UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Peppermint" UUID="720d719e-e571-4bdd-aac9-718f0ffe2266" TYPE="ext4" 
/dev/sda14: LABEL="LL to MM test Be" UUID="c703501f-1f50-465f-8eb7-9f20cbd3485a" TYPE="ext4" 
/dev/sda15: LABEL="LMDE" UUID="22eefad4-870e-4191-87c9-57f4e756411d" TYPE="ext4" 
/dev/sda16: LABEL="LL to MM test RC" UUID="7a90aa0c-2377-48e4-97ad-20283c962abc" TYPE="ext4" 
/dev/sda17: LABEL="vacant" UUID="850462c4-a56d-458f-8316-8174e6bc5230" TYPE="ext2" 
/dev/sdb1: LABEL="Maverick Test" UUID="3f034d3f-00f4-437c-9514-febbcd52c407" TYPE="ext4" 
/dev/sdb5: UUID="5a66ab05-104c-4625-9429-6d143d2519b6" TYPE="swap" 

```

Of course that would be overkill for most people but you certainly could boot Windows, one known good Linux OS, and a third that you're testing. I did just that for a long time.

Once the testing OS was both released as stable/final and I was sure it worked properly for me I'd then use the "old stable" for a new testing install. You need only transfer data from one to another :)

Regardless, this is "testing"! I'd never try a distro upgrade w/o first trying the new Live CD!

I suspect, but can't be sure, that you might be effected by a variant of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

I was concerned that it wasn't addressed in the release notes and said so there:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807/comments/15](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807/comments/15)

Had you been patient we could have tried some variant of this:

[http://ubuntuforums.org/showpost.php?p=9893106&postcount=16](http://ubuntuforums.org/showpost.php?p=9893106&postcount=16)

That is of course a guess. You'll see I'd been trying to figure that out for a while in my spare time :)

---

### Post by Justin_Bailey on 2010-10-02
> **hislordship said:**
> yeah thanks...i am just reinstalling lucid lynx. all my data will be lost. 

Thanks for all who've been trying to help.

To the developers who ask people to test this stuff and then aren't there when they get into trouble: this is crab.

You could have easily avoided this by either backing up before hand, or simply not using a release that isn't ready.
I think your general understanding of linux could have also used some consideration...most people who aren't comfortable with command line do not use alpha/beta releases for this exact reason.  Don't blame other people for what is essentially your responsibility.

---

### Post by hislordship on 2010-10-03
Justin - if you put a version online and make an advert on ubuntu.com first thing asking people to try it out than it is NOT their responsibilty if something goes wrong!

---

### Post by florus on 2010-10-03
hislordship - you did ignore several warnings when you installed a development release. 
It is made accessible for the many thousands of users who enjoy the challenges of working with an alpha or beta release, and who are willing to work to solve the problems that they encounter.

---

### Post by hislordship on 2010-10-03
I'm giving up. There is a banlity of arrogance that infects the reader in what you say.

---

### Post by cariboo on 2010-10-03
I've been following this thread, your problem would have been fairly simple to solve, if you had given us enough info to help you solve it. 

Did you document the problems you had? If so it might be useful if you posted your experience to the QA-mailing list. You can join it [here]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-qa")

---

### Post by exploder on 2010-10-03
cariboo907, thanks for the link to the mailing list! :)

---

