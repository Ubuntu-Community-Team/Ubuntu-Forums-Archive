---
title: "latest kernel update broke alsa  2.6.32-26 FYI"
date: 2010-11-29
forum: Mythbuntu
---

### Post by iitywygms on 2010-11-29
I am running mythbuntu daily builds.  Did the latest update which included a kernel update to 2.6.32-26
After the update, myth had no sound.  went to scan for new devices and nothing came up, only null available.
went to run alsamixer and it reported directory not available, or something to that nature.
Rolled back kernel to 2.6.32-25 and all is well.
Just a update
I am running an acer revo.

---

### Post by Chunk of Earth on 2010-11-29
Which version of Ubuntu are you running? I'm using the daily builds on Mythbuntu Maverick and my kernel is version 2.6.35-23-generic.
I also have audio problems but ALSA seems to be working. It's the internal player that can't use it right.

---

### Post by iitywygms on 2010-11-30
Im on lucid.
It broke alsa.  Not just in mythtv.
alsamixer would not even open.

---

### Post by Nikas on 2010-11-30
I used this script to upgrade and make alsa work again.
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Just DL AlsaUpgrade-1.0.23-2.tar, extract and run AlsaUpgrade-1.0.23-2.sh -d then AlsaUpgrade-1.0.23-2.sh -c and after that AlsaUpgrade-1.0.23-2.sh -i :)

I have to do -c and -i with every kernel upgrade to make sound via HDMI work again.


Edit: You may need to run alsamixer and "unmute" your outputs after this.

---

### Post by nickrout on 2010-11-30
well it didn't break my alsa. I too am running a revo and kernel 2.6.32-26-generic and all is well.

---

### Post by iitywygms on 2010-11-30
> **Nikas said:**
> I used this script to upgrade and make alsa work again.
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Just DL AlsaUpgrade-1.0.23-2.tar, extract and run AlsaUpgrade-1.0.23-2.sh -d then AlsaUpgrade-1.0.23-2.sh -c and after that AlsaUpgrade-1.0.23-2.sh -i :)

I have to do -c and -i with every kernel upgrade to make sound via HDMI work again.


Edit: You may need to run alsamixer and "unmute" your outputs after this.

sound like that may the issue I have.
I did an alsa upgrade a while back, maybe I will upgrade the kernel and try as you suggest.
Seems like a pain if this has to be reinstalled each time.
Oh well, gives me something to do. :)

---

### Post by thatguruguy on 2010-11-30
> **iitywygms said:**
> sound like that may the issue I have.
I did an alsa upgrade a while back, maybe I will upgrade the kernel and try as you suggest.
Seems like a pain if this has to be reinstalled each time.
Oh well, gives me something to do. :)

In other words, the kernel update didn't break ALSA, it broke the changes that you've made.  You had me worried for a minute.  I've now run the update, and don't have any problems.

---

### Post by thatguruguy on 2010-11-30
Incidentally, the kernel update is an ubuntu update.  It has nothing to do with the fact that you're running the mythbuntu daily builds.  It's not myth-related in any way.

---

### Post by nickrout on 2010-11-30
And whats more you DO not need to go outside the regular myth/ubuntu packages to get alsa to work on a revo. Simply don't go outside the ubuntu packaging (and I include the autobuilds in that) unless there is a VERY compelling reason.

---

### Post by tgm4883 on 2010-11-30
> **nickrout said:**
> And whats more you DO not need to go outside the regular myth/ubuntu packages to get alsa to work on a revo. Simply don't go outside the ubuntu packaging (and I include the autobuilds in that) unless there is a VERY compelling reason.

There is zero difference between the MythTV packages in the Ubuntu repos vs the MythTV packages in the Mythbuntu provided repos from a packaging point of view. They are both done by the same team, one just contains updated mythtv software

---

### Post by Nikas on 2010-11-30
I had to do it to get sound via HDMI from my nVIDIA GT220. :)

---

### Post by Janos1 on 2010-11-30
Hi to all .It not just broke Alsa, i can not find my sound driver anymore.Before just 1 day ago XBMC was working perfect today morning i updated and no more sound no more driver.Unfortunately not understand Linux i used Windows for 25 year long.

---

### Post by iitywygms on 2010-11-30
> **nickrout said:**
> And whats more you DO not need to go outside the regular myth/ubuntu packages to get alsa to work on a revo. Simply don't go outside the ubuntu packaging (and I include the autobuilds in that) unless there is a VERY compelling reason.
I did the alsa update because I could not get boxee sound for the life of me.
It worked after I did he alsa update.
that's another subject thou.
I am considering blowing away my frontend install and installing maverick from scratch.  I have to many hacks and fixes for my liking now.
Maybe over the weekend.

---

