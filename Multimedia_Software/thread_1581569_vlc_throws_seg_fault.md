---
title: "vlc throws seg fault"
date: 2010-09-25
forum: Multimedia Software
---

### Post by bogaczew on 2010-09-25
for few days vlc is quiting with segmentation fault.

my system:
```
pawel@lambda:~$ uname -a
Linux lambda 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
pawel@lambda:~$
``` 

vlc is from system repo, 1.0.6

problem is with every file. the output on console is very limited

```
pawel@lambda:/dane/dane/filmy$ vlc 26038395.mp4 
VLC media player 1.0.6 Goldeneye
[0x10df4b8] main libvlc: Uruchamianie vlc z domy&#347;lnym interfejsem. U&#380;yj 'cvlc' aby u&#380;ywa&#263; vlc bez interfejsu.
Segmentation fault
pawel@lambda:/dane/dane/filmy$
``` 

i believe that it's something with QT, it propably started  when I installed XBMC from repo on launchpad [https://launchpad.net/~team-xbmc-svn/+archive/ppa](https://launchpad.net/~team-xbmc-svn/+archive/ppa) .

vlc --reset-config dosen't help.

other video players, xbmc, smplayer, cvlc are OK.

What can I do to fix it?

---

### Post by andrew.46 on 2010-09-25
Hi,

More information can be gained by running from the terminal:

```
cvlc -vvv 26038395.mp4 
```

Andrew

---

### Post by mc4man on 2010-09-25
You may also want to try this
```
vlc -I qt4 --reset-config --reset-plugins-cache
```

---

### Post by bogaczew on 2010-09-25
thnx. 
after 

```
vlc -I qt4 --reset-config --reset-plugins-cache
```

there's no more segfaults. thnx again

---

### Post by Gaba_p on 2011-11-19
> **bogaczew said:**
> thnx. 
after 

```
vlc -I qt4 --reset-config --reset-plugins-cache
```

there's no more segfaults. thnx again

Yes! VLC had been giving me this error with .rmvb and .avi files for weeks now and this fixed it.

Thank youuuu :)

---

