---
title: "Why is Rhythmbox consuming alot of CPU?"
date: 2014-08-23
forum: Multimedia Software
---

### Post by casey9 on 2014-08-23
I am encountering an issue with my installation of Rhythmbox where all of a sudden it is consuming most of my CPU. This problem is fairly new as it started a few months ago. Below are the specs for my machine:

[ATTACH=CONFIG]255761[/ATTACH]

As you can see, I have a good amount of RAM, space and a very good processor.

I have almost 500GBs of music on a NAS that i've created a share for. I used to import all of this music into my Rhythmbox relatively easy, but a few months ago, my rhythmbox began crawling. Not sure why it's doing this.

Can someone please assist here? 

Thanks!

---

### Post by tgalati4 on 2014-08-23
It could be that your library has been corrupted and needs to be wiped and re-established.  It could also be rhythmbox trying to compare the library with the NAS contents to see if there were changes in file locations.  Did you make any big changes in the NAS?  Open a terminal:

```
rhythmbox --debug
```

---

### Post by casey9 on 2014-08-23
I didn't make any changes to the NAS. I ran the command however I cannot see any errors in the output. Should I be looking for something in particular? Also, how do i wipe the library clean?

---

### Post by tgalati4 on 2014-08-23
```
man rhythmbox
```

> OPTIONS
       -d, --debug
              Enable debug output

       -D, --debug-match=match
              Enable debug output matching a specified string

       --no-update
              Do not update the library with file changes


Try running with the --no-update switch.

Install *htop* and watch it:

```
sudo apt-get install htop
htop
```

Don't delete the library until you are clear that it is corrupted.  If you don't see errors, then it might be something else going on.

Try:

```
rhythmbox --debug-match=error
rhythmbox --debug-match=Error
```

---

### Post by casey9 on 2014-09-08
I ran the following command:
rhythmbox --debug-match=Error

Below is the output:
[ATTACH=CONFIG]256277[/ATTACH]
[ATTACH=CONFIG]256278[/ATTACH]

Screenshot #1:
I noticed that multiple instances have been spawned after running the command. Why is this? 

Screenshot #2:
Not sure what these errors are. Can someone please fill me in?

I have a suspicion that it's something to do with my NAS as the network indicator on System Monitor spikes whenever i start rhythmbox. However when I access my files via Nautilus, all is well. Please let me know if this makes any sense.

---

