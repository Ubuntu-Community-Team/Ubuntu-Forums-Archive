---
title: "ATI X200M PowerState cannot be set as default"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by karhulitos on 2007-06-12
Hi,

I've now spent 2 days searching answer to get ATI 200M eat less current out of my battery. There are some things people have suggested but none helped me.

I can do: 
```

~$ aticonfig --set-powerstate=1
~$ aticonfig --list-powerstates
    core/mem      [flags]
-----------------
* 1: 100/150 MHz  [low voltage]
  2: 301/200 MHz  [default state]

``` 

so far so good. If I connect to mains, system actually changes to power hogging mode. And if I disconnect, it's back in low volt mode. This started to work after added xhost +local:root to startup programs.

But I fail to put this as system default.

I have tried:
```
:~$ cat /etc/X11/xorg.conf | grep -i power
        Option "PowerState" "2"

```
```
~/data/scripts/fglrx-powermode.sh into Sessions Startup programs. 

```
No errors, no change in PowerState. :(

Anyone? Please help!

---

### Post by karhulitos on 2007-06-14
Anyone, please? This seems to hard but hopefully not impossible..!

---

### Post by karhulitos on 2007-06-17
Still not actual default, but closer. I had done [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Fglrx_lowpower") in some point of time.
It never worked for me. I had done this for both accounts on this PC, mine and wife's.

I happened to notice that when my wife was logged in with battery only, the fglrx powerstate was indeed low.

I don't know what I had done earlier, but [this]("http://ubuntuforums.org/showthread.php?t=246370&highlight=.Xauthority") helped me. I had somehow managed to do break my .Xauthority permissions, root had them and not me.

```
sudo chown `whoami`:`whoami` ~/.Xauthority
```

Brilliant! Not full system fglrx low power default but time spent on login screen only isn't usually that long..!

---

