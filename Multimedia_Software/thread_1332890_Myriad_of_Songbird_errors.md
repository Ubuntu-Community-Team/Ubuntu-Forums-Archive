---
title: "Myriad of Songbird errors"
date: 2009-11-20
forum: Multimedia Software
---

### Post by plr4ever on 2009-11-20
Hello all,

I finally decided to move all of my stuff to Xubuntu, from Windows 7. Things have only gotten better over the past year, but the biggest sticking point up to now is my music.

I am a big fan of Songbird; it seems to be miles ahead of any other music player, and I am a big fan of the add ons. However, I restarted it one day and haven't been able to get it to run since. Running "songbird" from the terminal only prints out a few errors involving gstreamer plugins.

So I remove and reinstalled it, to no avail. I then purged it, with no luck. I downloaded the executable from getsongbird.com, but that fails to run, giving me a 
```

./songbird-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory

```
even though the file is CLEARLY in the same folder as the executable. I even made it executable, but no joy.

Finally, I decided to just compile it from source. However, even THIS seems determined to stump me. After installing a list of missing dependencies, I get this error:
> 
checking for hal... Package hal was not found in the pkg-config search path. Perhaps you should add the directory containing `hal.pc' to the PKG_CONFIG_PATH environment variable No package 'hal' found
configure: error: Library requirements (hal) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Now if I'm not mistaken, hal is an integral part of any Linux install, but I made sure I had it installed anyway (I do). 

Is there something obvious I am missing, or is there anyway possible to clear out everything involving songbird and start that from scratch?

---

### Post by komputes on 2009-11-20
I think I had the same issue. I ended up keeping the profile, but downloading the daily build from this ppa:

[https://edge.launchpad.net/~songbird-daily/+archive/ppa](https://edge.launchpad.net/~songbird-daily/+archive/ppa)

Lost iPod support but it's much more stable than 1.2.

---

### Post by plr4ever on 2009-11-20
Thanks for the idea, but nothing comes up when i run it. It doesn't even print any errors when i start it from the terminal. However, once i start it and hit ctrl-c and try to start it again, songbird tells me that it's already running.

---

### Post by lidex on 2009-11-21
Have you tried starting with a new profile and/or removing the database?

More here:
[http://getsatisfaction.com/songbird/topics/why_songbird_crashes_upon_startup]("http://getsatisfaction.com/songbird/topics/why_songbird_crashes_upon_startup")
[http://getsatisfaction.com/songbird/topics/i_cant_use_songbird_on_kubuntu]("http://getsatisfaction.com/songbird/topics/i_cant_use_songbird_on_kubuntu")

---

### Post by plr4ever on 2009-11-21
Wonderful! 

Thank you so much, that worked perfectly. I'm slightly ashamed that I didn't think to delete the preferences folder the first time around.

---

