---
title: "System un-bootable after today-s update"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quaxo76 on 2011-04-12
I just updated the system a couple of hours ago, but the computer crashed, and now Natty is unbootable.
If I try to boot normally, it stops with the following message on screen:
```

init: udevtrigger main process (345) terminated with status 1
init: udevtrigger post-stop process (349) terminated with status 1
init: udevmonitor main process (344) killed by TERM signal
init: udev-fallback-graphics main process (355) terminated with status 1
fsck from util-linux-ng 2.17.2
/dev/sda9: clean, 200969/979200 files, 1111802/3915520 blocks

```

And it stays there indefinitely. I can reboot with Ctrl+Alt+Del.

If I try to boot the recovery mode, it prints out a lot of text and then it stops, and these are the last lines on-screen:

```

Begin: Running /scripts/local-premount ... done.
[    4.390812] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.

```

If then I press Ctrl+Alt+F7, I get the same messages I get with the "normal" boot (the "udevtrigger" messages) but with this line added:

```

*Stopping Flush boot log to disk                 [ OK ]

```
And here too, the only thing I can do is reboot.

If I try to boot a previous kernel version, I get the following message:
```

The disk drive for / is not ready yet or not present
Continue to wait; or press S to skip mounting or M for manual recovery

```

As it is now, Natty is totally un-bootable.
Any idea what happened and how can I fix this?

Thanks in advance,
Cristian

---

### Post by Yumi on 2011-04-12
I have the same issue. Updated about 3 hours ago. Now Grub is displaying for the first time since I changed to Natty. After Grub a black screen for a while then the message from the monitor - no signal. No boot, no login screen, nothing. The only thing I found working ist Ctrl-Alt-Del to restart the machine.

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3648    29302528+   7  HPFS/NTFS
/dev/sda2   *        3649        4621     7812096   83  Linux
/dev/sda3            4621        5229     4882432   82  Linux swap / Solaris
/dev/sda4            5229        9730    36153344   83  Linux


As I said grub is showin up with options. But there is no menu.lst in on sda2 nor on sda4. My feeling is that grub is pointing to the wrong partition. But where is grub and where is the menu.lst it must have.

Michael

---

### Post by fjgaude on 2011-04-12
Natty uses grub 2 and the file it generates is called **grub.conf**.

You may look at it and see what your issues might be. It's found in **/boot/grub**. Good luck!

---

### Post by Yumi on 2011-04-12
Thank you. I found it as grub.cfg and it contains the menu items I see when booting, pointing to the correct partition as far as I see.

Sorry for hijacking. Back to question 1 from Quaxo76. Maybe the solution to his problem solves mine too.

Michael

---

### Post by dino99 on 2011-04-13
try to boot in recovery mode, then:
- from synaptic:
 remove/purge grub-pc & grub-common
then reinstall them and reboot

---

### Post by Quaxo76 on 2011-04-13
Even in recovery mode, the system hangs.
If I boot a *previous* kernel in recovery mode, then I can get a terminal, but then / is mounted read-only, so I can't do anything.

---

### Post by Yumi on 2011-04-13
Thank you Dino. Booting in recovery mode brought up a lot of text as Quaxo describes it. But it stopped at a point where it asked to "press F to fix the inconsistencies" referring to partitions.

I pressed "F" and more text and happenings. Automatically rebooted the system and - it works. Back to normal.

Quaxo, I hope your system comes back to live too.

The story goes further. It works but it showed the error icon in the upper bar. I was asked to do a "sudo dpkg --configure -a" which I did. After all the rattling the error is gone, the system stable - and grub gone again! But better a stable system than grub!

Michael

---

### Post by Quaxo76 on 2011-04-13
I don't get the "Press F" message... My options are to skip mounting (but I can't skip mounting / !!) or manually fix (but then, I get a terminal where / is read-only. :(

---

### Post by dino99 on 2011-04-13
> **Quaxo76 said:**
> I don't get the "Press F" message... My options are to skip mounting (but I can't skip mounting / !!) or manually fix (but then, I get a terminal where / is read-only. :(

you might be able to run "synaptic" from terminal

---

### Post by Quaxo76 on 2011-04-13
Well, yes, but what good will that do, seeing that / is mounted read-only? I can't update the system or change any files.
If I try to unmount / (so that I can remount it read-write) it doesn't get unmounted.

---

### Post by zika on 2011-04-13
Use chroot with LiveCD?
This is the list of upgrades I had this morning... Nothing looks suspicious...
```
[UPGRADE] bamfdaemon 0.2.86-0ubuntu1 -> 0.2.86-0ubuntu2+r395+201104122113
[UPGRADE] chromium-browser-inspector 12.0.733.0~svn20110411r81064-0ubuntu1~ucd2 -> 12.0.733.0~svn20110412r81202-0ubuntu1~ucd2
[UPGRADE] firefox-4.0 4.2~a1~hg20110412r67892+nobinonly-0ubuntu1~umd1 -> 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1
[UPGRADE] firefox-trunk 4.2~a1~hg20110412r67892+nobinonly-0ubuntu1~umd1 -> 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1
[UPGRADE] firefox-trunk-globalmenu 4.2~a1~hg20110412r67892+nobinonly-0ubuntu1~umd1 -> 6.0~a1~hg20110413r68036+nobinonly-0ubuntu1~umd1
[UPGRADE] google-chrome-unstable 12.0.725.0-r80304 -> 12.0.733.0-r81210
[UPGRADE] libbamf0 0.2.86-0ubuntu1 -> 0.2.86-0ubuntu2+r395+201104122113
[UPGRADE] libunity-2d-private0 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531
[UPGRADE] unity-2d 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531
[UPGRADE] unity-2d-launcher 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531
[UPGRADE] unity-2d-panel 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531
[UPGRADE] unity-2d-places 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531
[UPGRADE] unity-2d-spread 3.8.2-0ubuntu1 -> 3.8.2-0ubuntu2~bzr531

```

---

### Post by Quaxo76 on 2011-04-13
Hm? Can I use the livecd to update/upgrade the installed system? If I can... how? :)

---

### Post by mziel on 2011-04-13
> **Quaxo76 said:**
> Well, yes, but what good will that do, seeing that / is mounted read-only? I can't update the system or change any files.
If I try to unmount / (so that I can remount it read-write) it doesn't get unmounted.

Try this one:
```
mount -no remount,rw /
```

---

### Post by zika on 2011-04-13
> **Quaxo76 said:**
> Hm? Can I use the livecd to update/upgrade the installed system? If I can... how? :)
This might give You some idea:
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)
[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

and many other...

(I'm not saying it is simple, but it is doable...)

---

### Post by Quaxo76 on 2011-04-13
> **mziel said:**
> Try this one:
```
mount -no remount,rw /
```

That worked, thanks! :D :D
After the remount, I had to do
```
dpkg --reconfigure -a
```
and now the system boots again.

Thank you all again, you saved my day! :D

Cristian

---

### Post by zika on 2011-04-13
Nice!

---

