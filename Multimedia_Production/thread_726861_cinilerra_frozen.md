---
title: "cinilerra frozen"
date: 2008-03-17
forum: Multimedia Production
---

### Post by sanddgroper on 2008-03-17
Hi All
Have installed the synaptic package for cinilerra but when I go to
run the program it is frozen and the only way I can shut it down
is to kill the process through system->adminstration-> system monitor
were cinilerra shows up as sleeping.
I have added the line to the sysctl.conf file as suggested in other
post's in these forums but to no avail.
I am using hardy alpha4 and have the cinilerra repository for hardy
The thing is that I have a live CD of elive which has cinilerra on it and
it seems to work ok though I have not tried to do anything with it.
The thing is I am using only a 10G HDD with 512 of ram so could
cinilerra need more space to work.
I get no error messages wether I use GUI or command line.Just 
four dead screens

Cheers
Sandy

---

### Post by cotcot on 2008-03-17
I am running cinelerra on hardy alpha 6 without problem. (P4 processor). How much of the 10 GB is free ? Cinelerra as such does not need that much. When you load a longer video then it could freeze. An avi of 1 hour is over 10 GB. 512 ram should not be a problem. You might try to compile it yourself. 
[[COLOR="Red"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911&page=2") you can find how i did the compilation (#12)

---

### Post by keykero on 2008-03-17
From a terminal, try 

```

sudo cinelerra
```

Does that work?  There is some bizarre, inexplicable problem with it on Hardy as well as other newer distros.

---

### Post by sanddgroper on 2008-03-17
Thanks cotcot
I only installed it to try it and don't want to go down the compile road
at this time.
As I said the thing I find strange is that it is running but in sleeping mode.

Thanks keykero
Yes I have run it from the command line with the same result.
Only thing I get is this from the command line.
> PluginServer::open_plugin: /usr/lib/cinelerra/threshold.so: undefined symbol: __sync_fetch_and_add_4.
What that means I do not know.

Cheers
Sandy

---

