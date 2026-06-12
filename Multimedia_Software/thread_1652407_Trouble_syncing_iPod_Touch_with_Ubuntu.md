---
title: "Trouble syncing iPod Touch with Ubuntu"
date: 2010-12-24
forum: Multimedia Software
---

### Post by PhillyPhan627 on 2010-12-24
I've been a long time windows user until this weekend when I made the full switch to Ubuntu and erased Windows from my laptop completely.  I am extremely impressed with Linux and Ubuntu as an OS as I had been using Wubi for the past two months before making the complete switch.  The only problem I had had was attempting to update my iPod touch on Ubuntu which was essentially the only reason I would ever even boot Windows.  Doing some research online I saw that it stated media players like Banshee and Rhythmbox were compatible with iPod's and iTouches.  When I attempted to do this with Rythmmbox, Ubuntu recognized the device as an iPod however clicking sync crashed Rhythmbox and exited the program.  I also attempted manually moving files which resulted in the same outcome.

When trying Banshee it brought up loading bar in the bottom left corner which looked like it was adding my songs however afterwards it brought up a second loading bar that said "syncing" but after letting it run for 4 hours and still not being completed I exited the program. 

I have tried looking up a few tutorials instructing me to input various commands into the terminal, none of which have solved the problem.

I know this is a common problem but any help in solving this would be greatly appreciated.

---

### Post by PhillyPhan627 on 2010-12-25
I tried to restore my iPod on my Window's desktop to see if that would make a difference.

Now rhythmbox gives me this error message:

can't write ipod database because of missing hashinfo file

Any idea what this could be?

---

### Post by PhillyPhan627 on 2011-01-02
On Christmas I was able to restore my iPod and get Ubuntu to recognize it and then add most of my songs.  However it literally took about 4 hours for them to get onto my iPod.  About 3/4 of the way through, Rythembox froze and shutdown.  I have since then tried to connect my iPod to add more songs and it is going back to its original problem, not adding anything and crashing Rythembox.  In other media players like Banshee and Amarok, it recognizes that space is taken up on the device however states that the iPod has no songs listed on it.

---

### Post by optimisteo on 2011-01-03
Similar problem here. I'm still trying to figure out what the HashInfo file has to do with it.
Gtkpod or Rythmbox both copy files to the device (very long time) but fail to sync the database because of missing hashinfo file.
Still working on this, hope an answer is found soon.

---

### Post by sebikul on 2011-02-18
To fix tis issue you have to do the following:

1. Execute the following command:
$ ipod-read-sysinfo-extended

It should return :
"usage: ipod-read-sysinfo-extended <device|uuid|bus device> <mountpoint>"

If you get something telling to install a package, do it.

2. Execute the following command and copy the 40 character string:
$ lsusb -v | grep -i iSerial

3. Now execute this command to generate the hashinfo file:
$ ipod-read-sysinfo-extended <UUID> <mountpoint>

Being <UUID> the code you got in step 2 and mount point the absolute address of your iPod mountpoint, most likely being "/home/USER/.gvfs/NAME

Thats it, now it should work.

---

### Post by 91voyager on 2011-03-10
Hello - I am new to ubuntu, so forgive my ignorance but i have tried several times to follow your instructions above and get this error "Couldn't read xml sysinfo from 7c2e6xxxxxxxxxxxxxxxxxxxxxx80 (<< serial number)  

i am not clear if i am entering the UUID correctly <device|uuid|bus device>

i think i am doing something wrong here: $ ipod-read-sysinfo-extended <UUID> <mountpoint>

can you provide more detail on what goes in <UUID>? 

thanks...

---

### Post by johntaylor1887 on 2011-03-11
> **91voyager said:**
> Hello - I am new to ubuntu, so forgive my ignorance but i have tried several times to follow your instructions above and get this error "Couldn't read xml sysinfo from 7c2e6xxxxxxxxxxxxxxxxxxxxxx80 (<< serial number)  

i am not clear if i am entering the UUID correctly <device|uuid|bus device>

i think i am doing something wrong here: $ ipod-read-sysinfo-extended <UUID> <mountpoint>

can you provide more detail on what goes in <UUID>? 

thanks...

First install the [ipheth-utils]("apt:ipheth-utils") package.
Then: (you can install each command one at a time)
```
mkdir /tmp/packages && cd /tmp/packages

wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb

sudo dpkg --install *.deb

sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```

Then you can install gtkpod to sync your ipod.

---

### Post by hoamer on 2011-03-25
Hi,

(IOS 4.3, Jailbreaked, 3GS)
i got this error too, so i searched a lot.
At first, i updated libgpod, nothing. Then i downgraded gtkpod. Then i upgraded to an unstable version (2....).
Now i did as you said. 
When executing i got the following message:

```
root@hoamer:/tmp/packages# ipod-read-sysinfo-extended 7xxxxxxxxxxxxxxxxxxxxxxx5a61333 /home/hoamer/.gvfs/Hoamers\ iPhone

Entity: line 56: parser error : Char 0x0 out of allowed range
        <string>s5l8920x
                        ^
Entity: line 56: parser error : Premature end of data in tag string line 56
        <string>s5l8920x
                        ^
Entity: line 56: parser error : Premature end of data in tag dict line 10
        <string>s5l8920x
                        ^
Entity: line 56: parser error : Premature end of data in tag dict line 4
        <string>s5l8920x
                        ^
Entity: line 56: parser error : Premature end of data in tag plist line 3
        <string>s5l8920x
                        ^
Speicherzugriffsfehler (Memory Acces Error)

```With my second iPhone there are no failures. With it i can sync at this time (2G, 3.1.3, Jailbreaked)

What's the matter and what should i do now?

Thanks ;)


Greetings
Hoamer

---

### Post by superclyde on 2011-03-26
Exactly the same "parse error" for me when running "ipod-read-sysinfo-extended". 

Un-jailbroken iOS4.3/Ubuntu 10.10 (laptop edition). Would be grateful if someone could assist.............thanks.

---

### Post by hoamer on 2011-03-27
@superclyde: When sync. on iTunes, i get the following message: "...there can't opened a session with the iPhone". 
Do you [or anyone else] the same issue?

---

### Post by alex.barchiesi on 2011-08-28
Anyone succeed in fixing this issue ? 
I'm having the same after Ipod disconnected accidentally during a sync with gtkpod. 
I tried the following without any improvement: 
1. solution suggested in this thread "ipod-read-sysinfo-extended" which gives no 
2. create a new HashInfo file with [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
3. Add songs through iTuens to have it rebuilt 
4. Reboot both pc and Ipod 

thanks alex

---

### Post by gumb3l on 2011-12-14
description in the post above works fine :KS

perhaps op or admin should mention this in the first post of this thread to spare other users to read trough all the posts.

as sebikul mentioned:
> lsusb -v | grep -i iSerialgets you the serial number you need on [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) to create the hash file for your device.
in my case is listed 8 entrys. just take the longest one and mind not to copy the single digit before the hex code.

just follow the rest of the description on that page and enjoy an iTunes free life.

---

### Post by add1kt on 2012-05-28
> lsusb -v | grep -i iSerial

gets you the serial number you need on [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) to create the hash file for your device.
in my case is listed 8 entrys. just take the longest one and mind not to copy the single digit before the hex code.

just follow the rest of the description on that page and enjoy an iTunes free life.

Worked for me!

---

### Post by brenthalamu on 2012-07-02
i got a dependency problem with the main package:


dpkg: error processing libmtp-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libmtp8
 libmtp-dev

---

### Post by Lady C007 on 2013-01-14
Hi everyone, can someone please tell me where I shoulp put the hashinfo file? I tried all of the above and nothing is working yet.  Thank you!

---

### Post by RoUS on 2013-03-19
> **sebikul said:**
> 3. Now execute this command to generate the hashinfo file:
$ ipod-read-sysinfo-extended <UUID> <mountpoint>

Being <UUID> the code you got in step 2 and mount point the absolute address of your iPod mountpoint, most likely being "/home/USER/.gvfs/NAME

Thats it, now it should work.

I get a
  
**GnuTLS error: A TLS packet with unexpected length was received.**

message.  My iTouch is passcode-protected and that can't be disabled (enforced by a required app), but I don't know if that's the problem.

---

### Post by sandyd on 2013-03-19
**Necromancing - thread closed**
Please do not post in threads more than one year old.

Thanks!

---

### Post by Elfy on 2013-03-19
I'd suggest you start a new thread - this one is 2 years old. 

Closed

---

