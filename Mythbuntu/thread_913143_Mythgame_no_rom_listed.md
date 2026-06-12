---
title: "Mythgame no rom listed"
date: 2008-09-07
forum: Mythbuntu
---

### Post by daniele7910 on 2008-09-07
I have installed mythbuntu.
When I scan for rom it find it but nothing is put in the database.
I try kxmame and it work.
I think the table of the database wrong or the script write the data in the wrong way.

---

### Post by bmwman on 2008-09-07
I'm having the same problem. Please let me know if you find out anything. Thanks

;)

---

### Post by stevanbt on 2008-09-07
Hi,
I had terrible trouble getting Mythgame to work on my Mythbuntu box, but it works now... I didn't make notes so, from memory, a couple of things to check are the permissions on the rom directory and the command to launch mame.

Thanks, Steve.

---

### Post by bmwman on 2008-09-07
I just got mine to work with this How To

[http://www.mythtv.org/docs/mythtv-HOWTO-16.html](http://www.mythtv.org/docs/mythtv-HOWTO-16.html)

---

### Post by daniele7910 on 2008-09-08
the permissions on the rom directory is rwrwrw and the owner is the logged user.

I try with this and other how to but nothing is change.

When I scan the roms dir it find the files:
....
MythGame:GAMEHANDLER: Found Rom : (MAME) - ????????.zip
....

But nothing is in the database.

---

### Post by revival67 on 2008-09-09
> MythGame:GAMEHANDLER: Found Rom : (MAME) - ????????.zip

Maybe i misunderstood but roms are not .zip files but .smc
I think you must unzip the files first.

---

### Post by bmwman on 2008-09-09
You definetly don't have to unzip the roms.

---

### Post by stevanbt on 2008-09-09
Agreed, you don't need to unzip the roms (remember the File Extension in Game Player Setup must not contain a full stop and it is case sensitive).  For info I had to put the following command in the Command on Game Player Setup page:-

```
xmame -dp alsa -vidmod 1 -fullscreen -skip_gameinfo -jt 1 -jdev /dev/input/js0 -gm -rp /usr/share/games/xmame/roms/ -def %s -dp alsa -audiodevice hw:0,1
```

From memory I had to amend three things... I had to put in here are the Rom Path (-rp), the joystick port (-jdev) and the audiodevice (I have SPDIF for my sound).

---

### Post by daniele7910 on 2008-09-10
i can't understand whi kxmame can parse the rom and mythgame don't see any.
There are some log file that can show me whi?

The zip file contain bin files that can't be parse to.

---

