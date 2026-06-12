---
title: "Wireless passphrase rejected even though it is correct"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by chip616 on 2011-01-15
I have Kubuntu 10.04 installed on an eeepc 901 netbook.  Wireless card is RT2860.  Wired connections work.  Wireless connections work, if they are not encrypted.

The problem comes with my home network.  I have a long passphrase, and I have correctly entered it into Network Manager and KWallet.  However, it fails to connect.

This machine HAS connected in the past, but the signal had to be strong.  My Dell laptop connects wirelessly to the same network with no problem.

I'm stumped as to why the netbook has now stopped connecting.

I tried Wicd, and it too complains of a bad password.  I've since uninstalled Wicd, and am back to NM.

Thing is, the password is NOT bad.  I've cut and pasted it, and it still doesn't work.

Any guesses?

Thanks.

Frank.

---

### Post by chip616 on 2011-02-11
OK. Seems the driver for the Ralink RT2860 wifi chipset is the problem.

Solution is here:

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

Follow the detailed instructions, and it works.

Now, why Canonical has not put an updated driver into the repository is beyond me.  The source is there.  What's the problem?

Frank.

---

### Post by Dark_Stang on 2011-02-11
Did you try installing the backported wireless drivers package? It might be in there.

---

### Post by chip616 on 2011-02-12
Dark_Stang:

No, I try to avoid the backports.  They often just cause other problems.

Unless there are some licensing rules that prevent Canonical from distributing a binary of the driver, I don't understand why this common problem has not been addressed in an LTS release.

Frank.

---

### Post by dmizer on 2011-02-12
> **chip616 said:**
> Unless there are some licensing rules that prevent Canonical from distributing a binary of the driver, I don't understand why this common problem has not been addressed in an LTS release.

Frank.

Is there a bug open on it? If so, does the bug report know of the fix? If not, then there's no way that Canonical can know either about the problem, nor the fix and would thus never end up in the LTS release.

---

### Post by chip616 on 2011-02-12
[https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860](https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860)

Frank.

---

### Post by dmizer on 2011-02-12
> **chip616 said:**
> [https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860](https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860)

Frank.

Then I suggest that you (politely) include your findings about the satisfactory results of the fix posted in this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/320390](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/320390)

---

### Post by chip616 on 2011-02-12
Will do.  Thanks.

By the way, I'm not upset or angry.  These are volunteers that do this work, and I'm happy to benefit from their sweat.  I was just, quite simply, surprised.

Frank.

---

### Post by chip616 on 2011-02-12
dmizer:

OK, replied to all three bug reports listed in the documentation at:

[https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860](https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860)

I read the bug reports through first, and it appears that the new Ralink 2.4.0.0 driver addresses them all.

I did note that the thread at

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

had already been listed on one of the bug reports as solving the problem and that post was several months old.  I can only hope that the devs will see my duplicate report of success, and act on it.

As one of the forum staff members, perhaps you can give them a nudge?  :)

Thanks again.

Frank.

---

### Post by dmizer on 2011-02-12
I have zero influence or association with the developers since development is not even remotely related to my area of expertise.

I do, however, appreciate your surprise and am glad to see that you've added to the bug report.

Thanks for the update and good luck!

---

