---
title: "everytime i reboot i have to manually reload the wireless driver"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by platelunch on 2009-11-07
ok, so this is only my second day using linux. i have 9.10 installed using wubi. i had problems with my broadcom wireless card not being recognized by ubuntu. by the way my computer im using is an hp mini 110-1033cl.

 i went to the broadcom website and downloaded the new driver and used the instructions they gave here:[http://www.broadcom.com/docs/linux_sta/readme.txt](http://www.broadcom.com/docs/linux_sta/readme.txt)  i had to modify their instuctions somewhat to get some of the commands to work, such as they give the command :' rmmod b43' and i would get back operation not allowed or something like that, so i figured out how to override that by adding the command 'sudo' in front of it to make it work. also in the instructions it wanted me to echo a line into the file blacklist.conf but i would get back permission denied so i figured out the command 'gksu nautilus' and found the file and changed the permission so that i could write to that file. i added the lines 'blacklist b43' and 'blacklist ssb' .

 the last two commands i had to enter to get the driver to work was 'modprobe lib80211' and then 'insmod wl.ko'    wl.ko is the name of the new driver. after i did all that i finally got internet to work. but when i turned off my computer and turned it back on later, the internet didnt work. i went to hardware drivers and it listed two driver one called b43 and one called sta. i read somewhere that the sta driver is the one to load from there so i tried to load it. it asks me to authenticate and then when i authenticate it says something like downloading and installing and doesnt do anything and the hardware drivers application windows lock up and i can get the app to quit, all i can do is make it minimize.


 then i went into terminal and ran the last few commands 'sudo modprobe 80211' and 'sudo insmod wl.ko' and then the internet starts to work. so my big question is how do i get the internet to work without having to enter these commands everytime i reboot?

 im really happy that i have internet at all because it took me a solid day to get it to work in the first place, and i had never used linux before. like i said i am totally new to linux, and maybe there is some easy way to do this and maybe im doing this all wrong,

 but i know that there must be someway to install this driver so that the internet will work everytime i boot up without me having to start up terminal and enter in a bunch of commands.

---

### Post by t0mppa on 2009-11-07
The */etc/modules* file loads all modules listed there automatically. So, possibly you could simply put wl in there, as it should load all the other modules it needs as a dependency or then have lib80211 there too, if it for some reason doesn't get loaded.

In case that doesn't work, you can add those two lines to */etc/rc.local* (must be before the *exit 0* line) or create a script consisting of said two lines and then use **update-rc.d** to have it loaded at the required run levels.

P.S. I hate to be a grammar nazi, since I know mine isn't perfect either, but with the level of grammar you're using, it'd be perfectly readable, if you bothered to add a few line feeds in there. Even if they don't make perfect essay paragraphs, they'd be a big help, since just one huge chunk of text is rather annoying to read.

---

### Post by puppywhacker on 2009-11-07
I normally use depmod to update the module dependencies, this usually gets modules to load, but I'm still not convinced this is the full truth. Running depmod is a safe thing.
```
sudo depmod -a
```

Before I used to add the module names in /etc/modules.conf which apparently is still a valid way, but I hardly need to actually do this nowadays.

As a last resort you could always put commands in the rc.local file that will be executed as last step of the booting process.
```
/etc/rc.local
```

P.S. If only I typed 5 minutes faster =) but then again, espoo must be in a timezone 5 minutes behind helsinki

---

### Post by platelunch on 2009-11-07
thanks for the tips. i added the line wl.ko to the etc/modules file. i am really new to linux and i'm not even positive as to how to write the path of a file so that it can be found so i put a copy of wl.ko in the top most file directory, the one that has the etc folder in it. i hope that works.

and, as you can see i put some line breaks in my original posting, it was hard to read before. can you recommend somewhere on the internet where i can learn about the basic conventions of linux? the only reason ive had any luck with linux and using the terminal program is because i used to use the dos prompt along time ago, and they are very similar.

thank you for the help, i hope it works.

---

### Post by t0mppa on 2009-11-07
You don't have to add the .ko in the modules file, simply the name of the module, i.e., wl. The system knows where to find the modules, so you don't need to specify the path either. The modules file is just a way of telling it to load a module that normally wouldn't get loaded automatically. Plus I think puppywhacker has a more elegant solution with the depmod command.

And sorry, can't really recommend any tutorials, since I've never truly studied one very thoroughly. Just used DOS a lot back when I was a kid and since moving to Linux, man <command> (on terminal) and Google have been most useful for educating myself. But one shouldn't be too hard to find, Google showed 15M+ hits on the sample search I did.

> **puppywhacker said:**
> P.S. If only I typed 5 minutes faster =) but then again, espoo must be in a timezone 5 minutes behind helsinki

Good point, considering Espoo is slightly west of Helsinki, it would be a bit later, but perhaps not as much as 5 minutes. For once it's this way around, usually I'm the slower poster because of proof reading my posts and usually ending up writing more elaborate replies than necessary.

---

