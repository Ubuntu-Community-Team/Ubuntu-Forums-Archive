---
title: "Help patch realtime 2.6.17-rt8 :confused"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by thestuckup on 2006-08-23
I have been following the outline found at

[http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption)

to get the realtime kernel.  So far I am doing ok.  I am new to this stuff so it has taken me a couple tries and re-installs to get where I am at.  I have successfully downloaded the latest kernel source, but then where I get to the part where I patch it;
[COLOR="Red"]
Now, let's patch the kernel source.[/COLOR]

[COLOR="Navy"]cd linux/
patch -sp1 < ../patch-2.6.16-rt26
patch -sp1 < ../kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch[/COLOR]

Mind you I think i've only tried the first patch listed because I anticipated something going wrong. ;)  - so I actually
i changed the directory to /usr/src/linux, and than I did

patch -sp1 < ../patch-2.6.16-rt26

It gave me back that 1 out of 2 hunks failed and crated a file called Makefile.rej, which I assume is just a bunch of unusable trash?

anyway, I can't tell you the exact message it gave me because I didn't have the presence of mind to take note and when I went back to retry it so  I could copy the note, I end up with

[COLOR="Blue"]/usr/src/linux# patch -sp1 < ../patch-2.6.17-rt8
Reversed (or previously applied) patch detected!  Assume -R? [n] y
The next patch would create the file Documentation/DocBook/genericirq.tmpl,
which already exists!  Assume -R? [n] -y
Apply anyway? [n] y
Patch attempted to create file Documentation/DocBook/genericirq.tmpl, which already exists.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/genericirq.tmpl.rej
The next patch would create the file Documentation/RCU/proc.txt,
which already exists!  Assume -R? [n]
[/COLOR]


...As you can see I said yes to the first couple in hopes it would take and there would only be a few files I would have to respond yes to - not the case.  It goes on and on and on and if I answer yes it doesn't matter the system rejects it and saves it to a new reject file.

If anybody could help me

PS  This is a new system so not much is on here - it's not a tremendously huge deal for me to reinstall again if necessary.

Thanks

---

### Post by mlind on 2006-08-24
Latest stable kernel is 2.6.17. Are you're trying to patch it with a diff made for 2.6.16 kernel tree (like the patch name suggests?).

Try this:
[List]
[*]Reverse currently applied patch
```

patch **-R** -p1 < patch-2.6.16-rt26

```

[*]Download appropriate patch for your kernel from [http://people.redhat.com/mingo/realtime-preempt/older/](http://people.redhat.com/mingo/realtime-preempt/older/)
[*]**Test the patch first**!
```

patch -p1 **--dry-run** < /path/to/file.patch
[*]If patch applies cleanly, patch without --dry-run

```
[/LIST]

---

### Post by thestuckup on 2006-08-24
Ok - that was a good point you made about the patch but I had actually just misposted it because I wasn't copying and pasting.  I was updating the 2.6.17 with the 2.6.17-rt8 - I was just careless in my post.  I went back to strip the patch and than reapplied it and ended up with similar results...So...

The beginner's solution - I went back and reinstalled and than instead of doing the most recent patch I did the exact one in the Vanilla Kernel walk through: 2.6.16 with the rt-26 patch.  This time, I made sure to do as you said and do a dry run ... this is what follows: (I should mention that before I patched these, and after typing the line
[COLOR="DarkSlateBlue"]
mv linux linux.old[/COLOR]

I of course realized that there was no "linux" folder under my /usr/src directory, so instead, I just created a folder called linux.old, and than of course after the next line
[COLOR="DarkSlateBlue"]
ln -s linux-2.6.16-rt26/ linux[/COLOR]

I had a linux directory that pointed to the patch directory.

[COLOR="DarkSlateBlue"]
/usr/src/linux# patch -p1 --dry-run < /usr/src/patch-2.6.16-rt26
patching file Documentation/DocBook/Makefile
patching file Documentation/DocBook/genericirq.tmpl
patching file Documentation/RCU/proc.txt
patching file Documentation/RCU/whatisRCU.txt
patching file Documentation/feature-removal-schedule.tx[/COLOR]


...(a ton of those lines followed)... and than
[COLOR="DarkSlateBlue"]
patching file drivers/scsi/aacraid/aacraid.h
patching file drivers/scsi/aic7xxx/aic79xx_osm.h
patching file drivers/scsi/aic7xxx/aic7xxx_osm.h
can't find file to patch at input line 18461
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: linux/drivers/scsi/libata-core.c
|===================================================================
|--- linux.orig/drivers/scsi/libata-core.c
|+++ linux/drivers/scsi/libata-core.c
--------------------------
File to patch:[/COLOR]

Since this looks like it is because I am missing that file, and I'm sure there will be a bunch more of them too, Is there something I can type in my initial bash line that will make it ignore all these - or do I not want to ignore them, and instead make sure I go around and collect all these files from off the internet (or maybe there is a package they are part of?)

---

### Post by mlind on 2006-08-24
Could you post the exact kernel, patch and commands you are using.
My kernel tree contains drivers/scsi/libata-core.c ..

---

### Post by thestuckup on 2006-08-24
[COLOR="DarkSlateBlue"]sudo su
cd /usr/src
wget [http://people.redhat.com/mingo/realtime-preempt/older/patch-2.6.16-rt26](http://people.redhat.com/mingo/realtime-preempt/older/patch-2.6.16-rt26)
apt-get install kernel-patch-evms
gunzip kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch.gz

Now download the latest matching official kernel source from [http://www.kernel.org/](http://www.kernel.org/). At the time of writing, the latest kernel is 2.6.16 (do not use the 2.6.16.x kernels, they will cause issues when patching!).

wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2)
tar jxf linux-2.6.16.tar.bz2
mv linux-2.6.16 linux-2.6.16-rt26
mv linux linux.old
ln -s linux-2.6.16-rt26/ linux

If you use the NVIDIA module for your video, you can prepare to make the deb package for this as well:

apt-get install nvidia-kernel-source
tar zxf nvidia-kernel-source.tar.gz

There are other modules that you may require as well. Please add them to the wiki here if you have the package names. If you require assistance, post on the discussion page of this wiki and one of the editors will hopefully be able to assist you.

Now, let's patch the kernel source.

cd linux/
patch -sp1 < ../patch-2.6.16-rt26
patch -sp1 < ../kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch
[/COLOR]

I also used the synaptic package manager to get:

fakeroot patchutils gcc nvidia-glx kernel-package devscripts

---

### Post by mlind on 2006-08-24
I tested this with 2.6.16 kernel and [newest RT patch against that kernel]("http://people.redhat.com/mingo/realtime-preempt/older/patch-2.6.16-rt29"). Patching seems to work fine.
```

wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.tar.bz2
wget http://people.redhat.com/mingo/realtime-preempt/older/patch-2.6.16-rt29
tar jxvf linux-2.6.16.tar.bz2
cd linux-2.6.16/
patch --dry-run -p1 < ../patch-2.6.16-rt29

```

You can probably get this working with newest 2.6.17 kernel using
[http://people.redhat.com/mingo/realtime-preempt/patch-2.6.17-rt8](http://people.redhat.com/mingo/realtime-preempt/patch-2.6.17-rt8)

---

### Post by thestuckup on 2006-08-25
Thanks!  That patch worked fine on the dry run so I installed it.  Still not sure what I was doing wrong before.  (By the way; what is different about the jxvf command from the jxf command?)

Following that I unlinked the linux directory from the 2.6.16-rt26 file and linked it to the new rt29 file.

I have run into a couple questions since:Following the page for compiling the vanilla kernel and it says:

[COLOR="Sienna"]Now, copy the config from Ubuntu's default kernel, install libncurses-dev dependency and run menuconfig.

cp /boot/config-`uname -r` .config
apt-get install libncurses-dev build-essential
make menuconfig[/COLOR]

2 things: 1) I don't have a config file under boot that has my user name as a part of it, I have 2 config files: config-2.6.15-23-386, and config-2.6.15-26-386. And 2) There is already a '.config' file under the linux directory, so do I really want to replace it? ...

anyway...

So I copied the .config file from the new patch and named it config-2.6.16-29.config and stuck it in on my desktop and just named it randomly - I figured I could copy it back later if I try something that screws the original up.  I have been apprehensive about copying either config-2.6.15-23-386, config-2.6.15-26-386 to the /usr/src/linux directory. 

That being said I proceeded with things as is, installed the build-essentail and libncurses-dev packages, and did the make menuconfig and set the presets as described in the vanilla kernel outline:

[COLOR="DarkSlateBlue"]make menuconfig[/COLOR]

[COLOR="Sienna"]If you have never used menuconfig before, you should learn. Look around, change the settings that you are certain you want to change. In this step, you must change the following settings:

    * Enable Processor type and features > High Resolution Timer Support
    * Set Processor type and features > High Resolution Timer resolution (nanoseconds) to 1000.
    * Set Processor type and features > Processor family to the type of CPU in your system.
    * Set Processor type and features > Preemption Mode to Complete Preemption (Real-Time).
    * Set Processor type and features > Timer frequency to 1000 Hz.
    * Disable Kernel Hacking > Kernel debugging 

Once you have done that, Exit from menuconfig and select Yes to save your kernel configuration. 
[/COLOR]

So I did that and it gave me back this...

[COLOR="Sienna"]root@TowerofPower:/usr/src/linux# make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
  HOSTCC  scripts/kconfig/lxdialog/inputbox.o
  HOSTCC  scripts/kconfig/lxdialog/lxdialog.o
  HOSTCC  scripts/kconfig/lxdialog/menubox.o
  HOSTCC  scripts/kconfig/lxdialog/msgbox.o
  HOSTCC  scripts/kconfig/lxdialog/textbox.o
  HOSTCC  scripts/kconfig/lxdialog/util.o
  HOSTCC  scripts/kconfig/lxdialog/yesno.o
  HOSTLD  scripts/kconfig/lxdialog/lxdialog
scripts/kconfig/mconf arch/i386/Kconfig
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:144:warning: trying to assign nonexistent symbol X86_UP_APIC_DEFAULT_OFF
.config:166:warning: trying to assign nonexistent symbol 05GB
.config:167:warning: trying to assign nonexistent symbol 1GB
.config:168:warning: trying to assign nonexistent symbol 2GB
.config:169:warning: trying to assign nonexistent symbol 3GB
.config:210:warning: trying to assign nonexistent symbol ACPI_SBS
.config:220:warning: trying to assign nonexistent symbol ACPI_PCC
.config:221:warning: trying to assign nonexistent symbol ACPI_SONY
.config:229:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:230:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:231:warning: trying to assign nonexistent symbol ACPI_DEV
.config:336:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM


[/COLOR]Are these warning messages something I need to take care of, and if so how?

---

### Post by christhemonkey on 2006-08-25
Just to let you know;
```
uname -r 
```
Does not give the user name, it gives you your currently running kernel version.

(i.e. 2.6.16-12-386 or whatever)

---

### Post by thestuckup on 2006-08-25
oh, thanks good to know

---

### Post by christhemonkey on 2006-08-25
and i think,

(although dont quote me on this :p)

that, as the .config file is from a previous kernel,
and that there have been changes in the kernels naming of things and the like, that the references in the .config file to CLEAN_COMPILE and KOBJECT_UEVENT are all to things that have been renamed/moved.

So basically, yes, these error messages are fine and ignorable.

---

### Post by dolson on 2006-08-26
christhemonkey is right about the .config stuff. Copying the .config just gets as many of the same configuration parameters as Ubuntu uses as possible. You can do anything you want to, but I tend to stick to what they use, with the minor tweaks i want from there.

As for the tar jxvf vs the tar jxf, the difference is the v. ;)

Ok, that's not what you meant. You want to know what the v does. Well, according to the help file, the v means verbose, and so it doesn't print a bunch of crap on your terminal as it is extracting. I leave out the v  for two reasons, 1) it seems to be faster on my system to not bother printing out all the file names as they extract. 2) errors are easy to see - if there is no output, then it's all good. If there is, then it is probably an error, and it's easily spotted. That's all. You can use v if you want.

---

### Post by thestuckup on 2006-08-28
Ok, thanks - that is also good to know.  Thank you to everyone on this thread.:D  Realtime is up and running for me...now for the sound card...a new thread i suppose

---

