---
title: "Right-click on mounted drive causes desktop to flash off and on and conky display dis"
date: 2010-10-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-10-29
I have had my Maverick drive mounted all day while copying files over to Natty. When I came to right-click on it to unmount the drive the whole desktop goes black for a split second then comes back on but conky display has disappeared. Needless to say, the drive stays mounted and the only way I can unmount it is via cairo dock. I can right-click elsewhere with no problem.
Did I do something silly somewhere?
Any ideas please?
Thanks

---

### Post by ronacc on 2010-10-29
I got something like that trying to eject the install cd after a fresh maverick install on my laptop last night .I haven't followed up on it yet , I just shut down and manually ejected it . After reboot I could eject a usbstick ok but I haven't tried another cd .

---

### Post by Quackers on 2010-10-29
It's got worse :-(
Now I can't even open the mounted partition/drive. If I click on it (left or right click) the mounted drive flashes off and back on with the desktop background and in the bottom panel "Starting File Manager" appears for about 1 second and then disappears.
I've tried rebooting and it's still the same. I've also compared UUID's in fstab with blkid and the only entry missing is the Windows drive, which when mounted, also behaves the same way.

---

### Post by Quackers on 2010-10-29
I thought it might be a user problem so I logged out and it went zombie. Black screen, no alt + F key did anything, no ctrl + F key, nothing. No disk activity, nothing. Tried REISUB, nothing. So I force closed it and it booted right up normally after. But it's still the same.
And System > Admin > Users and Groups starts to work and then dies. No GUI appears.

---

### Post by cariboo on 2010-10-29
Can manually unmount the drive? Open a terminal and type:

```
sudo umount /media/<mount_point>
```

Where <mount_point>  is where the drive is mount for example:

/media/disk

---

### Post by Quackers on 2010-10-29
I can unmount the drive through cairo dock. The problem now is the effect on the desktop and user changing - or more accurately not being able to :-)

---

### Post by Quackers on 2010-10-29
I have 3 users logged in, even though only me has actually logged in. I have 

natty64 on pts/0
guest   on tty10
natty64 on tty9

I don't know how that happened. Obviously when I try to kill one of the natty64s my screen shuts down :-)

---

### Post by ronacc on 2010-10-29
> **Quackers said:**
> I have 3 users logged in, even though only me has actually logged in. I have 

natty64 on pts/0
guest   on tty10
natty64 on tty9

I don't know how that happened. Obviously when I try to kill one of the natty64s my screen shuts down :-)

the problem you are having with  System > Admin > Users and Groups I am having on my desktop test box ,try starting it from a term ```
 sudo users-admin 
``` and see if it bitches about a missing schema .

---

### Post by Quackers on 2010-10-29
ronacc, you were right
```
natty64@natty64-laptop:~$  sudo users-admin
[sudo] password for natty64: 

GLib-GIO-ERROR **: Settings schema 'org.gnome.system-tools.users' is not installed

aborting...
Trace/breakpoint trap
```

---

### Post by ronacc on 2010-10-29
Unfortunately I haven't figured out how to fix it yet .

---

### Post by Quackers on 2010-10-29
I'm ferreting about now myself :-) If I find anything I'll post here.

---

### Post by Quackers on 2010-10-29
It seems I've been a naughty boy........again.
I found a similar problem mentioned in a Launchpad bug.
[https://bugs.launchpad.net/glib/+bug/621507](https://bugs.launchpad.net/glib/+bug/621507)
Thanks ronacc, you put me on the right track.
Whilst cleaning up this afternoon I uninstalled a few packages. One of them was Empathy.

NOTE to myself.....write 100 lines 
I must not uninstall default programs even if I haven't had a problem with it before!
I must not uninstall default programs even if I haven't had a problem with it before!
I must not uninstall default programs even if I haven't had a problem with it before!
I must not uninstall default programs even if I haven't had a problem with it before!

Blah blah blah :-)

Problem solved :-)

---

### Post by ronacc on 2010-10-29
You came to the same place that I am getting to , I was waiting to post until I saw if it worked (still reinstalling ubuntu-desktop ) , ok it finished ,yep that got it , I'm not going to write any lines I'm going to write a bug , removing or replacing a meta-package or a default application ( not system files of course ) should not trash your system.

---

### Post by Quackers on 2010-10-29
I was surprised too, but in all honesty, I've got previous for this. I once completely removed Evolution with all its dependencies. That didn't go down well! So I didn't learn my lesson did I? Enough said :-)

---

### Post by ronacc on 2010-10-29
I always remove empathy and a few other things that I have no use for ( and in the case of empathy a burning hatred of) and have never run into this before . I am going to play around and see if I can get rid of it without nuking my system even if I have to hack the depends in the ubuntu-desktop package .

---

### Post by scradock on 2010-10-29
That's weird. I also remove empathy (and lots of other stuff I don't need), but evince is working fine for me. Running natty 64-bit with compiz; opening evince in a terminal I get a gtk error repeated several times, but the document loads and scrolls OK:

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

(evince:4772): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

(evince:4772): Gtk-WARNING **: Failed to load type module: (null)

---

### Post by Quackers on 2010-10-29
> **ronacc said:**
> I always remove empathy and a few other things that I have no use for ( and in the case of empathy a burning hatred of) and have never run into this before . I am going to play around and see if I can get rid of it without nuking my system even if I have to hack the depends in the ubuntu-desktop package .

Me too :-)
If you don't do too much damage and you find something out I'd appreciate a heads-up. Thank you.

---

### Post by scradock on 2010-10-29
For me, empathy removes without complications; evolution is more complicated - I need to keep a couple of packages (e-data-server-common and e-webcal. I also remove ubuntu-desktop and all the "accessibility" cruft, plus most of the asiatic-languages packages, scim, and suchlike. It's wonderful that ubuntu includes them for those that need them; I just don't, so I purge them, which means removing ubuntu-desktop....

---

### Post by Quackers on 2010-10-29
From memory I think it was removing the data-server that did the damage.

---

### Post by ronacc on 2010-10-29
Ok I think I know what happened , when I removed empathy I didn't "completely remove" it and it left behind its gschema.xml file in /usr/share/glib-2.0 so when the next update caused glib-compile-schemas to run it barfed due to empathys schema being there and pointing at a no longer existing package . Why that didn't throw up a warning I don't know I'll have to wade back through the logs and see what I can find . I just "completley removed" empathy and it didn't leave behind that gschema.xml and didn't cause the problem , I'll see what happens after the next update .
as a side note unity now starts for me , it barfing was the same cause , missing schema .

---

### Post by Quackers on 2010-10-29
Oh well, sort of a result all round then :-) There does seem to be a missing link there, somewhere. I too will watch the next set of updates. I may be back in touch :-) Hope not though. Thanks.

---

