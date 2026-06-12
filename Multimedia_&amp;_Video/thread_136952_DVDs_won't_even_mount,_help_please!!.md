---
title: "DVDs won't even mount, help please!!"
date: 2006-02-27
forum: Multimedia &amp; Video
---

### Post by dermotti on 2006-02-27
I have a dvd drive, when i put a CD in, it mounts automatically. I put a dvd in, the light blinks for a few seconds, then nothing.

I try to manually mount the dvd, it says unable to mount device, no media found.

I have installed libdvdcss2.


What am i missing???

---

### Post by Sutekh on 2006-02-27
Only thing I can think of is to check the **System -> Preferences** menu and the **Removable Drives and Media Preferences**.

Go to the **multimedia** tab and make sure that 'Play video DVD discs when inserted' is checked, and there is a command to execute.  I have **totem %d**

---

### Post by dermotti on 2006-02-27
Yea thats what i have in there too :-(

---

### Post by dermotti on 2006-02-27
I think the problem is it doesnt know that there is a DVD in there....I have Mepis  on my other harddrive and it plays them fine...

---

### Post by Sutekh on 2006-02-27
[QUOTE=dermotti]I think the problem is it doesnt know that there is a DVD in there....I have Mepis  on my other harddrive and it plays them fine...[/QUOTE]
Okay can you check the entry for the DVD in /etc/fstab.  In the filesystem part it should include both iso9660 (for CDs) and udf (for DVDs)

Here's mine
```

/dev/hdc /media/cdrom0 **udf,iso9660** ro,user,noauto 0 0

```

---

### Post by dermotti on 2006-02-27
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0  udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dermotti on 2006-02-27
cdrom1 is my dvd player, cdrom0 is my cd burner. just fyi

---

### Post by Sutekh on 2006-02-27
Well I didn't really expect that your fstab would be wrong, but this is most puzzling.

When you put in a DVD, what's the output from ```
dmesg | tail
```
(I'm really pushing the boundaries of my linux diagnostic ability!)

---

### Post by dermotti on 2006-02-27
mike@warlock:~$ dmesg | tail
[4298329.606000] VFS: busy inodes on changed media.
[4298329.609000] VFS: busy inodes on changed media.
[4298331.934000] VFS: busy inodes on changed media.
[4298332.293000] VFS: busy inodes on changed media.
[4298334.298000] VFS: busy inodes on changed media.
[4298334.301000] VFS: busy inodes on changed media.
[4298334.472000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298334.472000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298334.555000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298334.555000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

---

### Post by dermotti on 2006-02-27
If i use the gnome applet to mount, it get this

[4294898.070000] cdrom: open failed.
[4294898.073000] cdrom: open failed.

---

### Post by dermotti on 2006-02-27
Oh god i am an idiot........I don;t know what i was smoking, this computer doenst have a DVD player. I have an identical IBM next to it with a dvd player. I was just confusing myself...


Garrr sorry guys.....

---

### Post by dermotti on 2006-02-27
Ok pulled the dvd from the other machine and installed it. Ubuntu reads dvds now :-P

In the words of Napolean Dynamite "God im so stupid....uhhh!"

---

### Post by Sutekh on 2006-02-27
[QUOTE=dermotti]Ok pulled the dvd from the other machine and installed it. Ubuntu reads dvds now :-P

In the words of Napolean Dynamite "God im so stupid....uhhh!"[/QUOTE]
Hooray!  I must say my self belief was quite shaken for a while there ;)

Glad its working!

---

