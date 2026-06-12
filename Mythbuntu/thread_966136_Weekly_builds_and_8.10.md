---
title: "Weekly builds and 8.10"
date: 2008-11-01
forum: Mythbuntu
---

### Post by ian dobson on 2008-11-01
Hi,

Just upgraded my frontend to 8.10. The process didn't go too badly, I just had to manually reinstall the nvidia driver and screw abot with xorg.conf abit. But that's what I expect from such a major upgrade.

The only thing that doesn't appear to be correct is that I now don't have the weekly builds apt-source in my repositries list

/etc/apt/sources.list

```

deb http://ch.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ intrepid universe multiverse main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse

# deb http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu hardy multiverse universe restricted main

# deb http://packages.medibuntu.org/ gutsy free non-free

```

Should I just enable weeklybuilds.mythbuntu.org but for intrepid something like:-
deb [http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu) intrepid multiverse universe restricted main

Regards
Ian Dobson

---

### Post by Lindsay.Mathieson on 2008-11-01
Hah! I just came to ask the exact same question!

Additionally I had the same issue with xorg.conf and the nvidia :)

---

### Post by ian dobson on 2008-11-02
Hi,

Anyone? Laga are you there?

Regards
Ian Dobson

---

### Post by db260179 on 2008-11-02
The weekly fixes for intrepid is not available yet. The intrepid has the latest version anyway.

Hope this helps?

> **ian dobson said:**
> Hi,

Anyone? Laga are you there?

Regards
Ian Dobson

---

### Post by ghuber on 2008-11-02
Yah, I had probs with Xorg.conf too...

I just copied xorg.conf.failsafe over it, rebooted and installed Envy to fix my nvidia driver problems.

---

### Post by wroopy on 2008-11-21
> **db260179 said:**
> The weekly fixes for intrepid is not available yet. The intrepid has the latest version anyway.

Hope this helps?

Now it looks like weekly builds are available for Intrepid.
Anyone that upgraded to the new weekly builds?

/Andreas

---

### Post by lionsnob on 2008-11-22
> **wroopy said:**
> Now it looks like weekly builds are available for Intrepid.
Anyone that upgraded to the new weekly builds?

/Andreas

Do you happen to know if weekly trunk builds are available yet?  Also, how did you add the weekly builds to your sources?

Thanks!

---

### Post by jboehm on 2008-12-02
> **wroopy said:**
> Now it looks like weekly builds are available for Intrepid.
Anyone that upgraded to the new weekly builds?

/Andreas

I turn on Intrepid weekly builds but it does not appear that there are any updates, as of the last time I looked for updates.  This was several days ago now.

Jon

---

### Post by tgm4883 on 2009-01-06
Weekly MythTV builds (for -fixes) are now fixed for both the US and UK mirrors.  If these are already in your sources.list then you have nothing else to add and it should work straight away.  The GPG key error for the UK mirror has also been fixed.  -fixes will contain MythTV updates for Hardy and Intrepid, and in the future Jaunty.

Trunk/0.22 - If you wish to run trunk please note that the trunk repo address has been changed to reflect 0.22 now.  If you have been previously running trunk or have added the repo before today, you have the wrong repo and will not get trunk updates.  Please go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and add the new repo if desired.  Trunk repo will contain MythTV 0.22 updates for Hardy, Intrepid, and Jaunty.

---

### Post by lionsnob on 2009-01-06
Thanks tgm4883!

---

### Post by Nikas on 2009-01-06
I got updates for:
libmyth-0.21-0
libmyth-perl
libmyth-python
mythtv
mythtv-backend
mythtv-backend-master
mythtv-common
mythtv-database
mythtv-frontend
mythtv-transcode-utils 

No plugins?

0.22-trunk? How stable? :) (no plugins/mythweb there either)

---

### Post by ian dobson on 2009-01-07
Hi,

I wouldn't touch 0.22 trunk at the moment. 0.21-fixes doesn't look too ba at the moment (I've just upgraded by systems). The only problem I'm seening is that mythcommflag seems to be spamming the myth log file.

Regards
Ian Dobson

---

### Post by Nikas on 2009-01-07
I have used fixes for a long time. No problems so far.
Before that i used 0.21-trunk.

---

### Post by neutron68 on 2009-04-04
> **tgm4883 said:**
> Weekly MythTV builds (for -fixes) are now fixed for both the US and UK mirrors.  If these are already in your sources.list then you have nothing else to add and it should work straight away.  The GPG key error for the UK mirror has also been fixed.  -fixes will contain MythTV updates for Hardy and Intrepid, and in the future Jaunty.

I went to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and got the weekly builde package deb.  It downloaded to the desktop and I doubleclicked on it.  It installed.  I set it for -fixes.

How do I initiate a .21 fixes update?   I have looked but have not found any instructions on how to use it.

Thanks,
Eric

---

### Post by tgm4883 on 2009-04-04
> **neutron68 said:**
> I went to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and got the weekly builde package deb.  It downloaded to the desktop and I doubleclicked on it.  It installed.  I set it for -fixes.

How do I initiate a .21 fixes update?   I have looked but have not found any instructions on how to use it.

Thanks,
Eric

apt-get update

apt-get upgrade

---

### Post by neutron68 on 2009-04-04
> **tgm4883 said:**
> apt-get update

apt-get upgrade
Ah, thank you.  :)
I wondered if it was that easy.  Buy it is not documented anywhere, so I could not be 100% sure.

Can this also be done through the graphical Update Manager inside the Mythbuntu Control Centre?
(Click the Check button, click Install Updates?)

Thanks again for the information!
Eric

---

### Post by tgm4883 on 2009-04-04
> **neutron68 said:**
> Ah, thank you.  :)
I wondered if it was that easy.  Buy it is not documented anywhere, so I could not be 100% sure.

Can this also be done through the graphical Update Manager inside the Mythbuntu Control Centre?
(Click the Check button, click Install Updates?)

Thanks again for the information!
Eric

Yes.  Basically it's just more repos

---

