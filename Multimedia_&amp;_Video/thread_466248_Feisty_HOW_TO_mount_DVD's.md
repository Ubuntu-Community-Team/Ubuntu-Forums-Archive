---
title: "Feisty: HOW TO mount DVD's"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by DeathStar on 2007-06-06
Hi all,

I noticed a problem when I first installed Feisty in that DVD's wouldn't not mount / play. CD worked fine, but DVD's didn't. I tried several things to remedy this and eventually I got it working, but because I'd attempted so many things, I wasn't sure exactly WHAT had fixed it.

I recently had to re install Feisty (for other reasons) and the same issue occurred... I couldn't mount / play DVD's. This time, I have only done ONE fix and it seems to work now. So, here is what I did in order to get this to work:


[B]
STEP ONE:[/B] Update you system.
You must make sure that your system is up-to-date. You can do this either using the "update manager" in the System Menu, or by using a terminal windows and typing:

```
sudo apt-get update
sudo apt-get upgrade
```



**STEP TWO:** Medibuntu Repository
From what I can gather, the reason that DVD's don't mount is down to CSS encryption not being read correctly. Although you system will already have libdvdcss2, it doesn't work correctly. You need the one from the Medibuntu repository.

Add the Repository Key:
```
wget http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Add the Repository to the sources list:
FEISTY FAWN
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
EDGY EFT
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list
```
DAPPER DRAKE
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```


[B]
STEP THREE: [/B]Another Update
Now that you've added a new repository, you need to perform another update
```
sudo apt-get update
```



**STEP FOUR: **Install the packages
Now, you can install the necessary packages to get the latest version from the Medibuntu repository
```
sudo apt-get install libdvdread3
sudo apt-get install libdvdcss2
```



**STEP FIVE:** Restart
When I first tried this, I did a reboot, but it still didn't work. I recommend shutting down the system entirely and then turning it back on.
```
sudo shutdown now
```
Once your system is turned off, switch it back on.



Hopefully, you should be able to mount / play DVD's. Please accept my apologies if this walkthrough doesn't work for you, but this is what I did and it worked for me.

Please post back whether this worked or failed.

Cheers,
DS

---

### Post by gfixler on 2007-06-13
I registered just now so I could thank you for your guide. I have an operating drive again. It hasn't been mounting, or doing much of anything for awhile, but this did it. Thanks for the simple, easy-to-follow walk-through.

---

### Post by 23kota on 2007-07-14
Thanks a lot! This helped me too. I would never found such solution by myself :-)

---

### Post by mikehipson on 2007-07-21
just had to say thank you very much for that post, it was super easy to follow, and IT WORKED!!!  I can now play dvds, i just have to figure out how to play vcds.  :)

---

### Post by minhtrietle on 2007-07-29
i didn't work for me though. I followed the steps really carefully.

I'm really frustratted with this issue. I think i might go back to 6.10

---

