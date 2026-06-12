---
title: "NAS Stopped auto mounting on login/startup - help"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2010-05-01
I am running a buffalo nas (linkstation live) connected to my wireless router with a static IP address, for ages i have had it auto mount via samba with a line in my /etc/fstab and all was working fine.

Just recently I have noticed that the nas doesnt always auto mount on login.  Sometimes it does sometime i have to load a bash prompt and sudo mount /media/nas.  The nas always mounts fine after the sudo command so its not an ip address issue or the nas as far as i can see.

I have a mythbuntu machine on the same network and this isnt an issue on that machine (although it is wired directly to the router rather than the wireless im using on my laptop).

Anyone have any thoughts what might be going on?

Thanks

---

### Post by geekyhawkes on 2010-05-03
Anyone any ideas?  I did a fresh install of 10.04 and am still having the same problems (it was time for upgrade anyway).   

Is there some way that ubuntu is trying to mount the drive too early (ie before the wireless has completed its authent?).

Thanks

---

### Post by stormcel on 2010-05-03
when I ran into this awhile ago, it was indeed determined that the network connection was not yet established when it was trying to mount.
It's not the best answer, but I just put a bash script in rc.local to run the mount -a option which just runs through the fstab again and rc.local always runs last.

---

### Post by Rubicon_82 on 2010-05-03
Is your wireless connection enabled before you've logged into GDM (and Network Manager has started)?  This can be checked by:
1) Disable Auto-Login if necessary.
2) Reboot.  After the system has booted, switch to VT1 (Alt-Ctrl-F1), login and issue:
```

ifconfig

```
Check whether the wireless interface (probably wlan0) has a valid IP address.

If the wireless connection isn't properly configured at this point then it's probable that the configuration is being handled by Network Manager.  To overcome this, you could try any of the following:

A) Configure wlan0 manually in '/etc/network/interfaces'.  This should bypass Network Manager entirely.

B) Create an Autostart script in '~/.config/autostart/' to issue the mount command.  If you also add the 'user' option to the NAS mount point description in /etc/fstab, you won't need to run the script as root.

C) Remove Network Manager, and install wicd instead.  Wicd doesn't use the Gnome Keyring to store network passphrases. Because of this, it can configure the wireless interface earlier in the boot process, giving mountall a chance to mount the remote filesystems.

---

### Post by geekyhawkes on 2010-05-04
Ok, so I am getting somewhere, as described the wireless hasnt started so no mount command works pre login.  I have tried WICD and didnt really get on with it, just didnt like the look of it as much as network manager.

I am thinkgin the Autostart script would work,sadly this is about where my knowledge is drying up, how should my script look in this directory?

Can i just put 

#!bin/bash
mount /media/nas

?

Should this work for the user tab in fstab?

//192.168.1.14/share/ /media/nas smbfs,user 0 0

Does the syntax matter for the extra options (after mount point)

Thanks for the help

---

### Post by geekyhawkes on 2010-05-04
Something must be wrong with


//192.168.1.14/share/ /media/nas smbfs,user 0 0

The machine doesnt boot up with this in fstab, how do i use the user tag?

---

### Post by Morbius1 on 2010-05-04
If you still have your original fstab entry that used to work you could try adding one more option:

       ```
  _netdev 
```Option "_netdev" delays mounting until the network has been enabled.

[COLOR=Blue]EDIT:[/COLOR] Don't forget the preceding underscore "_"

---

### Post by tgalati4 on 2010-05-04
I presume that you rebooted your NAS and your router and it still doesn't work consistently?  Because Lucid boots up quicker, it could be a speed issue with the older Buffalo.  Also reseat all the network cables.  All it takes is a cat to play trapeze on your wires and you will never know what is going on.

Try changing your network port.  You could have an intermittent router switch.

---

### Post by Morbius1 on 2010-05-04
Follow up: I offered the _netdev option in another post and it did not resolve the issue but this post did:
[http://ubuntuforums.org/showpost.php?p=9226244&postcount=7](http://ubuntuforums.org/showpost.php?p=9226244&postcount=7)

Perhaps you can adapt your mount command  to his example.

---

### Post by geekyhawkes on 2010-05-04
Thanks for all the tips, i will work my through and report back exactly what does work for me, im sure this isnt just effecting me!

And fstab wise, would this be fine for the _netdev to be in use like this;


//192.168.1.14/share/ /media/nas smbfs 0 0 _netdev

---

### Post by geekyhawkes on 2010-05-06
Right now im confused, i created a nas.sh file as follows;

#!/bin/bash
if [ "$IFACE" = "wlan0" ]; then
      mount -t smbfs //192.168.1.14/share/ /media/nas/
fi

Made it executeable (and checked in the gui that it is also owned but root but no luck.  Ifconfig reveals that I am using wlan0 so why doesnt it work? 

If i put the mount -t command directly in a terminal once logged on then the nas mounts.  What have i missed?  (the file is in /etc/network/if-up.d)

EDIT it seems it might be related to my nas needing a password to mount, so see how that goes.

---

### Post by geekyhawkes on 2010-05-06
Plot thickens... so Im now trying this script;

#!/bin/bash
if [ "$IFACE" = "wlan0" ]; then
	mount -t cifs -o rw,user=xxx,pass=xxx,iocharset=utf8,file_mode=0777,file_mode=0777,dir_mode=0777 //192.168.1.14/share/ /media/nas/
fi

If i paste the mount command above into a terminal then the nas mounts fine, but for some reason the script doesnt seem to mount the nas (even if i ./nas.sh).  What is going on?

---

### Post by Morbius1 on 2010-05-06
My recommendation is to go to the source and post your difficulties to the guy that created the script:

[http://ubuntuforums.org/showthread.php?p=9226244#post9226244](http://ubuntuforums.org/showthread.php?p=9226244#post9226244)

---

