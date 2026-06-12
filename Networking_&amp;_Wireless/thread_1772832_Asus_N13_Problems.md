---
title: "Asus N13 Problems"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by GaryTheCat on 2011-06-01
Hello

I've managed to get my Asus N13 usb wireless adapter to work using the excellent pointers here:

[HTML]
http://ubuntuforums.org/showthread.php?t=1766327
[/HTML]

But for some reason the connection just seems to drop (other wireless devices in the house don't experience the same thing when this happens).

Is this a known problem?
Can I fix it? and how?

Happy to post the output of any required terminal commands - as always

Many thanks

G

---

### Post by GaryTheCat on 2011-06-01
OK I've tried the solution here [http://ubuntuforums.org/showthread.php?t=1419504&page=4](http://ubuntuforums.org/showthread.php?t=1419504&page=4) at post #35.

When I try to 'make' I get this:


```

make -C tools
make[1]: Entering directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
make: *** [build_tools] Error 2


```

And when I 'make install' this:

```

make -C /home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': Permission denied
make[1]: Entering directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
mkdir: cannot create directory `/etc/Wireless/RT3070STA': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
make: *** [install] Error 2


```

HELP :-(

---

### Post by Toz on 2011-06-01
> make[1]: gcc: Command not foundLooks like gcc is not installed. Install the build-essential package:```
sudo apt-get install build-essential
```

> mkdir: cannot create directory `/etc/Wireless': Permission deniedYou need root permissions to create a directory in /etc (or to run make install). Try running your **make install** command with sudo:```
sudo make install
```

---

### Post by GaryTheCat on 2011-06-01
Tried the first bit and now I get 

```

make -C tools
make[1]: Entering directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-32-generic/build SUBDIRS=/home/fraser/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.32-32-generic/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-32-generic/build'
make: *** [LINUX] Error 2


```

---

### Post by chili555 on 2011-06-01
> **Toz said:**
> Looks like gcc is not installed. Install the build-essential package:```
sudo apt-get install build-essential
```

You need root permissions to create a directory in /etc (or to run make install). Try running your **make install** command with sudo:```
sudo make install
```I think he also needs:```
sudo apt-get install linux-headers-generic
```Then:```
sudo su
make clean
make
make install
exit
```I will be shocked if this works any better than rt2870sta, but please proceed and make me a believer. Shocked I tell you!

---

### Post by GaryTheCat on 2011-06-01
Ah Chilli555 king of the N13 to the rescue....

If I ask really nicely, can you talk me through how to get this thing working? ;)

---

### Post by chili555 on 2011-06-01
Sure, see my post above. Try it and let's see if rt3070sta does a better job. By the way, you'll need to blacklist rt2870sta.

If you are stuck, tell me where and how.

I am taking Mrs. Chili to lunch in 10-15 minutes (not to Chili's!) so I may be gone for a couple of hours.

---

### Post by GaryTheCat on 2011-06-01
I'm trying to follow the method listed at post 35 here [http://ubuntuforums.org/showthread.php?t=1419504&page=4](http://ubuntuforums.org/showthread.php?t=1419504&page=4) 

and basically can't seem to get started with any of it.

would I be better to fresh install 11.04 while you and Mrs Chilli dine? (currently on a fresh install of 10.04).

Many thanks :)

---

### Post by chili555 on 2011-06-01
I think your device is fully supported in 11.04. You can run the live CD and remove the rt2800usb gang:```
sudo rmmod -f rt2800usb
sudo rmmod -f rt2800lib
sudo rmmod -f rt2x00usb
sudo rmmod -f rt2x00lib
```Now connect and see how it runs. Does it disconnect?

If all is well, install and do the blacklist steps documented in several threads and you should be good.

I'll check in apres diner.

---

### Post by GaryTheCat on 2011-06-01
Will get the 11.04 iso on my PC and burn the iso, install it etc etc and hope to hear back

Enjoy your meal :)

---

### Post by GaryTheCat on 2011-06-01
My current status


Installed Xubuntu 11.04 fresh from LiveCD
Updated
Installed Xubuntu restricted extras
Installed build-essential
Installed linux-headers-generic

Have done the following:

```

sudo rmmod -f rt2800usb sudo rmmod -f rt2800lib sudo rmmod -f rt2x00usb sudo rmmod -f rt2x00lib

```

have followed instructions from post 3 here ---> [http://ubuntuforums.org/showthread.php?t=1766327&highlight=N13](http://ubuntuforums.org/showthread.php?t=1766327&highlight=N13) (after installing gedit)

---

### Post by GaryTheCat on 2011-06-01
It seems to have worked - but then again I did get this far yesterday and the connection started dropping this morning, hopefully, the fresh install will have sorted that out.

Thanks tons :-)  :popcorn:

---

### Post by chili555 on 2011-06-01
> It seems to have worked Excellent. Good work. Post back if I can help you further.

---

### Post by GaryTheCat on 2011-06-01
I will indeed - you seem to have helped just about everyone who has one of these things using (X/K)Ubuntu.

Are they prone to dropping connection once they're set up? (like mine did this morning lol)

---

### Post by chili555 on 2011-06-01
> Are they prone to dropping connection once they're set up? (like mine did this morning lol)Not that I've heard of, but quite frankly, once I read, "It works!" I'm pretty much done with the case and I'm off answering two or three new posts. Unless the person posts back to the original thread to which I'm subscribed, I never know.

You did amend blacklist.conf, correct?

---

### Post by GaryTheCat on 2011-06-01
> **chili555 said:**
> Not that I've heard of, but quite frankly, once I read, "It works!" I'm pretty much done with the case and I'm off answering two or three new posts. Unless the person posts back to the original thread to which I'm subscribed, I never know.

You did amend blacklist.conf, correct?

I did indeed - are you subscribed to this thread? ;)

Thanks again :D

---

### Post by chili555 on 2011-06-01
> are you subscribed to this thread?Unless I've had too much adult beverage, then, yes, to every thread I've answered. Thousands...

---

### Post by thenickrulz on 2011-06-03
If anyone is having any problems look at this >>>> [http://ubuntuforums.org/showthread.php?t=1467291&page=4](http://ubuntuforums.org/showthread.php?t=1467291&page=4)

---

### Post by GaryTheCat on 2011-06-03
> **thenickrulz said:**
> If anyone is having any problems look at this >>>> [http://ubuntuforums.org/showthread.php?t=1467291&page=4](http://ubuntuforums.org/showthread.php?t=1467291&page=4)

For some reason I just couldn't get the driver to compile in 10.04 but as Chili555 says, it works pretty much straight from the box in 11.04, you just need to blacklist a few things and job done! :)

---

