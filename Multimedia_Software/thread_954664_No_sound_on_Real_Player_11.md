---
title: "No sound on Real Player 11"
date: 2008-10-21
forum: Multimedia Software
---

### Post by felixN on 2008-10-21
Hey guys, i'm new to ubuntu. I expected snags along the way. But i really enjoy the experience. Well i've got Real Player 11 installed on ubuntu 8.04, and plays just fine but one thing, no sound. Hope someone could shed some light. All help are appreciated. Please and thank you! :)

---

### Post by rex_the_first on 2008-12-16
This may not work as expected but worth a try.  I saw this solution from [[COLOR="Blue"]_fwelland_[/COLOR]]("http://forums.fedoraforum.org/showthread.php?t=186200&page=3") on the Fedora forums.



I fix/hacked this by changing the line in the realplay script 

```
sudo gedit /opt/real/RealPlayer/realplay
```

then on line 52 change

```
$HELIX_LIBS/realplay.bin "$@"
```

TO

```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```

---

### Post by annietc on 2009-01-15
> **rex_the_first said:**
> This may not work as expected but worth a try.  I saw this solution from [[COLOR="Blue"]_fwelland_[/COLOR]]("http://forums.fedoraforum.org/showthread.php?t=186200&page=3") on the Fedora forums.



I fix/hacked this by changing the line in the realplay script 

```
sudo gedit /opt/real/RealPlayer/realplay
```

then on line 52 change

```
$HELIX_LIBS/realplay.bin "$@"
```

TO

```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```

Wow cool. I searched for ages for this problem... now I also fixed it. ^_^

---

### Post by hristo.stefanov on 2009-01-17
This solution does not work for me.  I do change the player into OSS mode and try with both the following lines
```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```
or
```
aoss -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```
buth still no success with both. Can someone give me a hint what I may have missed or maybe an alternative solution. (I do have both padsp and aoss on the path).
The player starts normally, and I do not get any error messages in console when opening the BBC .ram file.

---

### Post by hmousavi on 2009-02-03
> **rex_the_first said:**
> This may not work as expected but worth a try.  I saw this solution from [[COLOR="Blue"]_fwelland_[/COLOR]]("http://forums.fedoraforum.org/showthread.php?t=186200&page=3") on the Fedora forums.



I fix/hacked this by changing the line in the realplay script 

```
sudo gedit /opt/real/RealPlayer/realplay
```

then on line 52 change

```
$HELIX_LIBS/realplay.bin "$@"
```

TO

```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```

Great solution! Thanks a lot.:)

---

### Post by verobtes on 2010-04-03
It worked for me. Thanks a lot :p

---

### Post by shortsightedPenguin on 2010-09-09
This worked on Ubuntu 10.04 LTS. Thanks.

---

### Post by alang184 on 2010-09-14
> **rex_the_first said:**
> This may not work as expected but worth a try.  I saw this solution from [[COLOR="Blue"]_fwelland_[/COLOR]]("http://forums.fedoraforum.org/showthread.php?t=186200&page=3") on the Fedora forums.



I fix/hacked this by changing the line in the realplay script 

```
sudo gedit /opt/real/RealPlayer/realplay
```

then on line 52 change

```
$HELIX_LIBS/realplay.bin "$@"
```

TO

```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```

This did not work for me. I'm running RealPlayer11 on Ubuntu 10.04.

I took another step, which made the sound work (and also fixed some kind of playback screen lagging problem). I simply opened RealPlayer, went into Tools -> Preferences -> Hardware, and under Audio Driver, I selected OSS instead of ALSA. I'm not sure whether the previously posted solution made a difference to this.

---

### Post by pvrm on 2010-12-29
> **rex_the_first said:**
> This may not work as expected but worth a try.  I saw this solution from [[COLOR="Blue"]_fwelland_[/COLOR]]("http://forums.fedoraforum.org/showthread.php?t=186200&page=3") on the Fedora forums.



I fix/hacked this by changing the line in the realplay script 

```
sudo gedit /opt/real/RealPlayer/realplay
```

then on line 52 change

```
$HELIX_LIBS/realplay.bin "$@"
```

TO

```
padsp -n RealPlayer -m RealPlayerStream $HELIX_LIBS/realplay.bin "$@"
```
This worked for me, using Ubuntu 10.10 and RealPlayer 11.
Thanks

---

### Post by marl30 on 2011-01-09
This worked for me... 10.10 64 bit. :D

---

### Post by HighWaters on 2011-02-21
> **alang184 said:**
> This did not work for me. I'm running RealPlayer11 on Ubuntu 10.04.

I took another step, which made the sound work (and also fixed some kind of playback screen lagging problem). I simply opened RealPlayer, went into Tools -> Preferences -> Hardware, and under Audio Driver, I selected OSS instead of ALSA. I'm not sure whether the previously posted solution made a difference to this.

I did this in addition to the line 52 change.  Now it seems to work. 

Thanks all!

---

### Post by itsjustarumour on 2011-08-29
> **HighWaters said:**
> I did this in addition to the line 52 change.  Now it seems to work. 

Thanks all!

Ditto for me, did the "line 52" fix and then changed to OSS in Realplayer 11 settings - cheers!

:-)

---

