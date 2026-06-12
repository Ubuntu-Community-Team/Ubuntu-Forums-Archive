---
title: "Problems playing DVD"
date: 2012-01-18
forum: Multimedia Software
---

### Post by MZ250Supa5 on 2012-01-18
I am having problems playing prerecorded DVDs on my Ubuntu desktop.  It used to work just fine, but now returns this error code when I place a disc in the drive:

"Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Has anyone got any ideas on how to solve this.  I have installed all the usual prerequisites to play DVD, as I have in the past, but apparently this time with no success.

---

### Post by silverhaze06 on 2012-01-21
I have a similar problem. I'm running 11.10 and when I insert a dvd and try to play it, it makes mplayer crash, and any other player just wont play them at all. So if anyone knows how to fix this, please help us!

---

### Post by Basher101 on 2012-01-21
this can be due to not having the needed codecs. One thing you do when you installed ubuntu is to install the "Ubuntu restriced extras". Those include java, flash, codecs and whatnot.

You can find it in the Software Center.


regards

---

### Post by silverhaze06 on 2012-01-21
> **Basher101 said:**
> this can be due to not having the needed codecs. One thing you do when you installed ubuntu is to install the "Ubuntu restriced extras". Those include java, flash, codecs and whatnot.

You can find it in the Software Center.


regards

I already have every codec I can possibly download, so it's not that.

---

### Post by silverhaze06 on 2012-01-21
and when i try opening a dvd with gnome player it will just say that it is loading but then never loads.

---

### Post by Basher101 on 2012-01-21
this is, regretfully, out of my range of specific knowledge about Ubuntu. I know alot about partitioning, boot issues, graphics cards but i have none on DVD playback. You will have to wait until someone who knows more about it can help you.


regards

---

### Post by silverhaze06 on 2012-01-21
I just tried a couple of other media players and they also crash when I try to play a dvd movie. At least until then there is always torrents!

---

### Post by Basher101 on 2012-01-21
> **silverhaze06 said:**
> I just tried a couple of other media players and they also crash when I try to play a dvd movie. At least until then there is always torrents!

well it **_IS_** legal as long as you own the actual copy. Good luck on fixing your issue anyways

regards

edit: just a hinch i got, could it be your DVD drive may not be supported well in ubuntu?

---

### Post by silverhaze06 on 2012-01-21
> **Basher101 said:**
> well it **_IS_** legal as long as you own the actual copy. Good luck on fixing your issue anyways

regards

edit: just a hinch i got, could it be your DVD drive may not be supported well in ubuntu?

The drive works fine otherwise. It reads and burns just fine, and plays dvds that I have burned. When I have a "real" dvd movie inserted, I can open it up in the file browser and I can see all the files, but any media player either crashes or just hangs up.

I think it's most likely the restricted extras drivers are like that on purpose so you'll be forced to buy the fluendo codecs. But screw that, I didn't start using linux so I would have to pay for software!

---

### Post by Basher101 on 2012-01-21
i hardly doubt that the codecs were "made" that way. What players are you using? did you try some others? You could also try some KDE applications (just a small warning, you should look out at your updates, beacuse when i installed just one KDE app, the recommended updates gave me alot of KDE libraries i did not need).

---

### Post by silverhaze06 on 2012-01-21
> **Basher101 said:**
> i hardly doubt that the codecs were "made" that way. What players are you using? did you try some others? You could also try some KDE applications (just a small warning, you should look out at your updates, beacuse when i installed just one KDE app, the recommended updates gave me alot of KDE libraries i did not need).

Ok, I've tried xine now. I can watch the extra features, and see the dvd menue, but it says it I don't have enough right to view the actual movie.

---

### Post by silverhaze06 on 2012-01-21
Ok I've tried a bunch of other media players and xine is the only one that kind of works. And It's only with the protected dvds that this is happening. So I'm thinking it might be a problem with the codecs?

---

### Post by leeper69 on 2012-01-21
I also have had problems with reading dvd,s have you downloaded libdvdread4?
and if you  have have you installed css? this is done in the terminal with the following command.
sudo /usr/share/doc/libdvdread4/install-css.sh
Hope this helps!

---

### Post by Basher101 on 2012-01-21
if you have no permissions to view the movie, try running the player or nautilus with admin rights, to launch them with admin rights type in a terminal ```
gksu nautilus
``` or ```
gksu [name_of_player]
```
note that the terminal must stay open as long as you use the player/nautilus

regards

---

### Post by silverhaze06 on 2012-01-21
> **leeper69 said:**
> I also have had problems with reading dvd,s have you downloaded libdvdread4?
and if you  have have you installed css? this is done in the terminal with the following command.
sudo /usr/share/doc/libdvdread4/install-css.sh
Hope this helps!

Just tried that, then tried playing the dvd again. It opened and played, but was scrambled beyond recognition. I tried to take a screen shot but then my computer froze when I hit the save button. Now after a reboot, none of the media players are able to open them again. They either crash or say the file cant be accessed, or I don't have enough rights to view it.

---

### Post by silverhaze06 on 2012-01-21
ok never mind. I already had css installed, but then i installed it again from the terminal, and its working now! thanks!

---

### Post by silverhaze06 on 2012-01-21
Let me rephrase that, it will play now, but only xine is able to play it. And only when I select xine from the program list when it asks me what to do when I insert the dvd. If i try to open the individual files from the browser, even xine wont play them. So it's still not totally "fixed" but at least I have a workaround now!

---

### Post by MZ250Supa5 on 2012-01-24
Thanks Leeper68, that did the trick for me... I did have that installed, or so I thought, as it seems did others commenting here.  What I found weird is that this isn't on a fresh install of 10.04, but one that's been on my machine for a while now that was previously playing encrypted DVDs with no problem.  Oh well, it works now, so problem sorted.

---

