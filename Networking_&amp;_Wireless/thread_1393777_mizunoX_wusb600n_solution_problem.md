---
title: "mizunoX wusb600n solution problem"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by GazRockK on 2010-01-29
> **mizunoX said:**
> I've noticed a few posts from people frustrated with the WUSB600N and the lack of support for it in Ubuntu/Linux so I thought I'd set the record straight for those searching the forums for answers.

The Linksys WUSB600N doesn't work in Ubuntu out of the box (current as of the release of Ibex)
Also it does not play nice with ndiswrapper (frequent disconnects, no 5Ghz support, no WPA2 support)

I was able to get it working with 5ghz and WPA2 by following steps that I found here:
[https://answers.launchpad.net/ubuntu/+question/45440]("http://posting%20on%20external%20website/")
Credit goes to the original author.

I've downloaded and modified the driver source for your convenience.  

Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar)
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.

Heres what happened during step 4 and 6:
```
Step 4:
-----
ubuntu@5m-ubuntu:~$ sudo su
root@5m-ubuntu:/home/ubuntu# cd /home/ubuntu/Desktop/WUSB600N
root@5m-ubuntu:/home/ubuntu/Desktop/WUSB600N# sudo make
make -C tools
make[1]: Entering directory `/home/ubuntu/Desktop/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ubuntu/Desktop/WUSB600N/tools'
/home/ubuntu/Desktop/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/ubuntu/Desktop/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/ubuntu/Desktop/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/ubuntu/Desktop/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/ubuntu/Desktop/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [LINUX] Error 2
root@5m-ubuntu:/home/ubuntu/Desktop/WUSB600N# 
``````
Step 6:
-----
ubuntu@5m-ubuntu:~$ sudo su
root@5m-ubuntu:/home/ubuntu# cd /home/ubuntu/Desktop/WUSB600N/os/linux
root@5m-ubuntu:/home/ubuntu/Desktop/WUSB600N/os/linux# sudo insmod rt2870sta.ko
insmod: can't read 'rt2870sta.ko': No such file or directory
root@5m-ubuntu:/home/ubuntu/Desktop/WUSB600N/os/linux# 
```

For step 4, I have no idea what's wrong, but with step 6, I checked /WUSB600N/os/Linux and I couldn't find a "rt2870sta.ko" file. Any help please? Thanks.

---

### Post by pdc on 2010-01-29
in this thread

[http://ubuntuforums.org/showthread.php?t=1347123](http://ubuntuforums.org/showthread.php?t=1347123)

in post #2 chili555 commented that the error message was due 


.. then ...

to 

> Your headers are too new for this antique driver file, evidently built in 2008

chili commented (as I have seen him do in another file) that the rt2870 that you need may well be in the kernel and to explore the command

> I guess I am wondering if the built-in rt2870sta module works for you and others. If you do:


Code: **sudo modprobe rt2870sta**

Is an interface created? Find out with:

Code:

**iwconfig**

there is a very recent post: (that I would need to hunt to find, where that seemed to be the answer)       .found it ...................

see here, post #8

[http://ubuntuforums.org/showthread.php?t=1392294](http://ubuntuforums.org/showthread.php?t=1392294)

---

### Post by chili555 on 2010-01-29
> make: *** [LINUX] Error 2Once you error out, all bets are off. There is no reason to proceed until you have that sorted out. May we please see:```
lsusb
```Also, please confirm that you have installed *build-essential.*

---

### Post by chili555 on 2010-01-29
Please see post #5 and beyond:  [http://ubuntuforums.org/showthread.php?t=1392957](http://ubuntuforums.org/showthread.php?t=1392957)

---

### Post by GazRockK on 2010-01-29
ubuntu@5m-ubuntu:~/Desktop/2009_0820_RT2870_STA_WebUI_v2.2.0.0$ lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1737:0079 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@5m-ubuntu:~/Desktop/2009_0820_RT2870_STA_WebUI_v2.2.0.0$ 

------

Also, I definitely have build-essential 

ubuntu@5m-ubuntu:~/Desktop/2009_0820_RT2870_STA_WebUI_v2.2.0.0$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@5m-ubuntu:~/Desktop/2009_0820_RT2870_STA_WebUI_v2.2.0.0$ 

looking at post #5 now.. thanks for looking at my question btw.

---

### Post by chili555 on 2010-01-29
> [COLOR="Red"]1737:0079[/COLOR] Linksys I don't believe rt2870sta is your friend.

---

### Post by GazRockK on 2010-01-29
Eh, I don't even know who he is.

I followed the instructions on the #5th post and got stopped at step 8 [the last one]

> 8) execute the command "sudo modprobe rt3572sta" => a blue light will turn on and the network interface "ra0" will createhere's the terminal output:
```
root@5m-ubuntu:/home/ubuntu/Desktop/RT2870_LinuxSTA_V2.3.0.0# sudo modprobe rt3572sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rt3572sta not found.

```help. ._.

---

### Post by chili555 on 2010-01-29
> [COLOR="Red"]root[/COLOR]@5m-ubuntu:/home/ubuntu/Desktop/RT2870_LinuxSTA_V2.3.0.0[COLOR="Red"]#[/COLOR] [COLOR="Blue"]sudo[/COLOR] modprobe rt3572staFirst, if you are already switched to root, you don't need sudo. Second, did make and make install go without error? Warnings are OK, but not errors.

---

### Post by chili555 on 2010-01-29
Also, we are building rt3572sta, not this:> /home/ubuntu/Desktop/[COLOR="Red"]RT2870[/COLOR]_LinuxSTA_V2.3.0.0rt2870sta is not your friend.

---

### Post by GazRockK on 2010-01-29
WHAT!? so I was processing the wrong files the whole time? oh, and about the sudo thing, I thought that was the equivalent of Microsoft Window's "run". Guess not. 
It gives admin status to commands then?

So I need to look for rt3572sta then huh. If there's multiple versions of this file [like there was for rt2870] which one do I need to download. Just a precaution before I start hunting for files.

---

### Post by GazRockK on 2010-01-29
okay.

I've got the one and only version of 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2 on my desktop. I'm going to review mizunoX and post #5's steps to see if I can set this up. and God so help me, I better not have anymore "wrong" files..

WISH ME LUCK
=.=

---

### Post by chili555 on 2010-01-29
> It gives admin status to commands then?Yes.> WISH ME LUCKGood luck. See you after a good night's sleep!

---

### Post by GazRockK on 2010-01-29
HAH! IT WORKED! TYSM CHILI555!! (Must've been pretty easy answering this though.. This question seems to be pretty consistent in the forums..) Anyways, all I need to do now is figure out how to configure wireless..\\:D/ [once again ThnkYouSoMch this problem took me the whole day to fix and I hated running a cable two stories down from the router to the basement. ]

---

### Post by GazRockK on 2010-01-30
Wait.

I restarted, [COLOR="Red"]feeling like the happiest guy in the world[/COLOR], then my network manager died on me, and now neither my wireless or cable give me working internet. I know I shouldn't say it, but I can't help thinking it. WTF. I do all that and now I'm [COLOR="Red"]way below where I started[/COLOR]. I went to the terminal and tried running network-connections from there, but it didn't recognize the process. 
once again, wtf. 

Anyways, I shouldn't be getting mad at you guys, and I'm not. Its just frustrating working so hard to do something and losing it all again. I actually haven't felt that in awhile. (The last time I felt this I think was in grade 2. I planted a carrot and watched it grow, then when I was sure it would be the perfect carrot, some dumb*ss rabbit ate it.):evil: [Sorry if you really don't wna hear my stories. It's around 11.20pm here and my true personality likes to ramble. ] 

Anything I can do here? I've gotten quite attached to Ubuntu and really don't like booting Windows. (I just noticed its so SLOW!) :P

---

### Post by pdc on 2010-01-30
I guess you could see what 

> iwconfig

says but maybe go to sleep on it and chili555 can help you out tomorrow

---

### Post by chili555 on 2010-01-30
Perhaps the driver did not load automatically. Please try:```
sudo modprobe rt3572sta
iwconfig
```Is your wirless back? If so, please edit */etc/modules* to add a single line:```
rt3572sta
```If your wirless does not spring to life, the next thing I'd check is step 4, where you edited the file "common/rtusb_dev_id.c" If it's not correct, we'll have some steps to take to undo and redo. Please let me know.

---

### Post by chili555 on 2010-01-30
> how rudeIndeed! I'd hope we could keep this forum family friendly. If you'd care to apologize and ask politely and respectfully, and post:```
lsusb
```Then I am sure someone will be happy to help.

---

### Post by mas2ery on 2010-01-30
haha.. my hoh girlfriend use to say that a lot....

USB\Vid_0411&Pid_015d&Rev_0101  :popcorn:

---

### Post by chili555 on 2010-01-30
> my hoh girlfriendFamily friendly?

Good luck to you in your future endeavors.

---

### Post by mas2ery on 2010-01-30
seriously, do u have any input on my theory of ralink printing rt3070l on a chip , selling it as a certain hardware dvice, binary code and all ,  with mismatching software code  incompatible with any kernal it claims to support

---

### Post by GazRockK on 2010-01-30
Seems my previous post attracted alot of attention.. Srry about the crude language, (you can call that an apology), but like I said it was really frustrating doing that all day and going back to below nothing. Anyways. 

Post #20 by mas2ery makes no sense to me. I never really bothered reading any guides or tutorials that didn't pertain to my current problems, so I'mg guessing I should do a bit of research before going back to the terminal. 
I'm booting Windows btw, I'll probably fix the Ubuntu problem sometime this week. I'm pretty busy today, tomorrow, the next day after that, you know. 
Fortunately, my life doesn't revolve around Ubuntu, but it was really interesting [and somewhat fun]typing out all those commands and editing root files. Windows just boringly does everything for you. (It's pretty convenient for Windows though, everything being compatible with it..)

Thanks for putting up me and not leaving this thread. Sorry again for the "not family friendly" post. I probably should've just stated my problem and slept on it. All in all, I won't be fixing this problem anytime soon. :-?

---

### Post by chili555 on 2010-01-30
> Sorry again for the "not family friendly" post.My comment was not directed at you. I will be glad to help you at any time.

---

