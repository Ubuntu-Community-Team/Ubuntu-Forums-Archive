---
title: "Unable To Watch DVD's"
date: 2008-08-04
forum: Multimedia Software
---

### Post by CarlosinFL on 2008-08-04
I am running 8.04 x86 on my machine and I wanted to watch a DVD movie today so I placed the disk in my DVD ROM and it would not play in Totem (Movie Player). Does anyone know exactly what is needed in order to play the DVD on my Ubuntu system? When I throw the disk in my player, I get a message error that indicates:

---

### Post by tuxxy on 2008-08-04
Did you install the ubuntu-restricted-extras package, this will provide DVD, MP3 play back codecs etc


To install search for it in synaptic or do this in terminal;

```
sudo apt-get install ubuntu-restricted-extras 
```

Heres some more info

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by CarlosinFL on 2008-08-04
> **tuxxy said:**
> Did you install the ubuntu-restricted-extras package, this will provide DVD, MP3 play back codecs etc


To install search for it in synaptic or do this in terminal;

```
sudo apt-get install ubuntu-restricted-extras 
```

Heres some more info

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks - I just installed that per your recommendation and it installed a bunch of stuff including a bunch of .exe fonts I did not want. When it was done, I tried to watch the movie in Totem again and I got the same error:

---

### Post by tuxxy on 2008-08-04
Try another player apart from Totem for example VLC media player, search for it synpatic, it will play virtually any file you care to throw at it.

EDIT : Make sure you have these packages installed , libdvdcss2 and libdvdread3

---

### Post by CarlosinFL on 2008-08-04
Thanks for the info but I am not willing to try another player - I know this is supported on Totem.

```
cwilliams@tunafish:~$ sudo apt-cache policy libdvdcss2
[sudo] password for cwilliams: 
libdvdcss2:
  Installed: (none)
  Candidate: (none)
  Version table:
cwilliams@tunafish:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

?

---

### Post by pmlxuser on 2008-08-04
try using synaptic package manager > search libdvdcss2
just out of curiosity are all the repositories checked (just to make sure that you are able to see most of the packages in repos) ;)

---

### Post by CarlosinFL on 2008-08-04
Apt & Synaptic both can't find "libdvdcss2".

And it is not installed on my system.

---

### Post by Afkpuz on 2008-08-04
libdvdcss2 is no longer in the repos.  You must get it through the medibuntu repository.

follow instructions here.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then, after you've completed that step, do this.

```
sudo apt-get install libdvdcss2
```


You might also want to install w32codecs while you've got the medibuntu repository set up so you can use some of the windows codecs too.

But after you install libdvdcss2, I would suggest using vlc and also reboot.  After that, vlc should work with movies.  Totem is just a lousy player in general for movies.

---

### Post by tuxxy on 2008-08-04
I agree VLC is much better player, and them files libe libdvdread should of been installed with the ubuntu-restricted-extras

---

