---
title: "Presonus Firebox Driver's"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by nobodysdarling on 2006-07-11
I am trying to locate some driver's for the Presonus FireBox. 

What are some other's quality FW interface's that have compiled Linux driver's /

---

### Post by libertyforever on 2006-08-21
Have you checked out the FreeBob project yet?

[http://freebob.sourceforge.net/index.php/Main_Page](http://freebob.sourceforge.net/index.php/Main_Page)

They list the Presonus Firebox as one device that they have working on their "List of Supported Devices" page.  I'm too much of a newbie to do anything with it.  Is there anyone out there that knows how to install FreeBob on Dapper?  I also would like to go get the Presonus Firebox to do some acoustic recording, but not sure how to set it up.  The FreeBob guys have instructions for doing it [here]("http://freebob.sourceforge.net/index.php/Building_and_Installing"), but I'm afraid it's still a little over my head.  :-k   Any chance Ubuntu will add a build of libfreebob to the repositories so guys like me can install it?

---

### Post by floogy on 2006-08-21
One could build probably a backport of the debian packages:
[http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux](http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux)

---

### Post by libertyforever on 2006-08-21
> **floogy said:**
> One could build probably a backport of the debian packages:
[http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux](http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux)

Ouch!  Yeah, I have been looking at the FreeBob page, and it is WAY over my head.  But, if that's the only answer, then I guess I'd better get caught up on my knowledge ](*,)

---

### Post by libertyforever on 2006-08-21
O.K., I took a deep breath and started going through the FreeBob build instructions that ***floogy*** suggested for gnu/debian install found [here]("http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux").  When I typed in: 

**grep IEEE1394 /boot/config-`uname -r` **

I found these lines:

[B]CONFIG_IEEE1394=m
CONFIG_IEEE1394_RAWIO=m[/B]

According to the directions, this means I have *"modular support,"*  (=y would mean built in support) and then it says, *"If there is not raw1394 kernel support, you must recompile kernel with this setup or install kernel image packaged. Linux Kernel version 2.6.15 or later is recommendable not mandatory."*  Then, I am told to *"Run as root: # apt-get install linux-image-2.6.*  Here's where I stopped because I got scared.  Can anyone out there tell me what I'm getting myself into?  I really don't want to mess things up.

---

### Post by floogy on 2006-08-21
I think you got proper firewire support compiled in your standard kernel. You can try that by typing modprobe ieee1394 && modprobe ieee1394_rawio (I'm not sure about the '-'vs. '_' though).
After that a lsmod|grep eee should show you the firewire kernel modules.

You can load them on bootup with appropiate line in /etc/modules:

```

gerhard@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ieee1394
ieee1394_rawio


```

There might be no need for you to compile a new kernel (?).

---

### Post by libertyforever on 2006-08-23
I learned you are right - I have modular support for the raw1394 kernel.  However, when I type what you suggested: *modprobe ieee1394 && modprobe ieee1394_rawio,* I get this: 

[B]steve@steve-desktop:~$ sudo modprobe ieee1394 && modprobe ieee1394_rawio
FATAL: Module ieee1394_rawio not found.
steve@steve-desktop:~$[/B]

When I type: *lsmod|grep eee*, I get this:

[B]steve@steve-desktop:~$ sudo lsmod|grep eee
ieee1394              299832  0
steve@steve-desktop:~$[/B]

Can you translate before I go any further?

Also, I have gone through the ubuntustudio tutorial to get jack going with other apps in the Ubuntu Studio Launcher (i.e., VKeyBd and Zynaddsubfx).  Everything worked properly and I had a measure of optimism (good job dolsen!).  Now the big question: if I go out and buy an audio interface such as the Presonus Firebox, will it work using the same steps (i.e., connect Firebox to Ardour, and then connect Ardour to sound card for play-back)?

---

### Post by floogy on 2006-08-24
I was guessing about the module name, but it is raw1394 instead of ieee1394_rawio, I think.

And grepping for 1394 is more appropriate too #-/

---

### Post by libertyforever on 2006-08-24
I typed in: 

steve@steve-desktop:~$ sudo modprobe raw1394
steve@steve-desktop:~$

Does this mean anything?  I get the same when I do the other:

steve@steve-desktop:~$ sudo modprobe ieee1394
steve@steve-desktop:~$

As for grepping, I don't know what that means (I'm a newbie).  Is there a place I can go study and learn about grep?

Also, anybody know if a firewire audio interface will connect with jack?

---

### Post by floogy on 2006-08-25
Hi,

It seems that the firewire modules are loaded, due to the lack of error messages ;-)

You can test that by lsmod on the Terminal. When typing lsmod only you would be a bit overwhelmed by all the modules your kernel loaded.

Therefore I use grep (A Pattern search program, which provides you with the matching lines) to filter the output to my needs.

In this case I have chosen "eee" to get all the firewire modules, but that suggestion was quite stupid, as all firewire modules got "1394" in their names, but only one the pattern "eee". Therefore I suggest now, to check after loading the modules with this line:

```
lsmod|grep 1394
```

If all modules show up, then your firewire device should be recognized. If not you might check the kerneloutput with **dmesg|tail**, or **xterm -e tail -f /var/log/messages &** .

[http://en.wikipedia.org/wiki/Grep](http://en.wikipedia.org/wiki/Grep)
[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

### Post by libertyforever on 2006-08-25
Thanks for helping me out on this floogy.  I think I'm catching on ;)  Here's what I've done so far:

[B]root@steve-desktop:~# modprobe ieee1394
root@steve-desktop:~# modprobe raw1394
root@steve-desktop:~# lsmod|grep 1394
raw1394                30956  0
ieee1394              299832  1 raw1394[/B]

I'm assuming this means my modules are showing up and my kernel should recognize my firewire.  I actually don't have a firewire card yet - it's should be here in the next few days from newegg.com.  I guess that will be the real test.  Next step to buy a Presonus Firebox, hook it up and test again - though I think I will need [FreeBob]("http://freebob.sourceforge.net/index.php/Main_Page") from what I've been researching.  Any suggestions on further steps I should take to achieve my goal?  Thanks for being there.

---

### Post by libertyforever on 2006-08-25
I also did this:

[B]steve@steve-desktop:~$ sudo gedit /etc/modules
[/B]
and added

[B]ieee1394
raw1394[/B]

If I understand you correctly, this should add the modules to boot up with the kernel, right?

---

### Post by dolson on 2006-08-26
That's basically right.

If you don't want them loaded when you boot up anymore, you can just remove them from there. I thought that ubuntu would automatically detect if you had firewire and auto-load them though.. maybe i'm wrong.

---

### Post by libertyforever on 2006-08-29
> **dolson said:**
> I thought that ubuntu would automatically detect if you had firewire and auto-load them though.. maybe i'm wrong.

You could be right dolsen.  I don't currently have a firewire card - should be here in the mail today from newegg.  BTW, thanks for all the work you have put into this.  Most of what I have learned has been from your work and posts  =D> 

Once I install the firewire card and Ubuntu is detecting it properly, I'm thinking that in order to use a firewire audio interface (Presonus Firebox), I will still need the FreeBob driver in addition to everything else I have done in the Ubunbu Studio wiki.  Is this correct?  Also, any word on the release of Edgy, as I have seen posts stating that it will have FreeBob built in?  I don't know if I want to wait so I may push my way forward into installing FreeBob myself.  Would this be a mistake or not?

---

### Post by dolson on 2006-08-29
You're welcome. :)

Unfortunately, I don't know anything about FreeBob. Someone told me a long long time ago that they would write a FreeBob tutorial in the wiki and it never showed up.

I do believe it is built into the newer JACK releases, and therefore will be standard in Edgy. I don't know if it is already in Edgy's current version.

Edgy will almost certainly be released in October, as Ubuntu sticks to 6-month release cycles (Dapper was pushed by a few weeks for extra polish and bugfixes, as being a 5-year supported release, they wanted it as polished as possible).

---

### Post by libertyforever on 2006-08-30
> **dolson said:**
> Someone told me a long long time ago that they would write a FreeBob tutorial in the wiki and it never showed up.
Would it be appropriate to tell me who that was so I can ask them if they would still be willing to do it - or at least if they would be willing to help me out?

> **dolson said:**
> I do believe it is built into the newer JACK releases, and therefore will be standard in Edgy.
Would it be possible to add the newer Jack version to Dapper and thus get FreeBob in the process?

In another [forum]("http://ubuntuforums.org/showthread.php?t=214911"), I found [this]("http://www.davidemorelli.it/dokuwiki/doku.php?id=other:freebob_on_ubuntu") link for compiling FreeBob in Breezy.  *"Aldous,"* in the other forum, seemed to be having trouble with it.  Is there a great difference between Breezy and Dapper in following these instructions?  Again, thanks for your help!

---

### Post by floogy on 2006-08-30
I think there is now heavy development to make things work better together, but I don't know, if this will make it into the new Edgy release:

[http://www.mail-archive.com/proaudio@lists.tuxfamily.org/msg00325.html](http://www.mail-archive.com/proaudio@lists.tuxfamily.org/msg00325.html)

---

### Post by libertyforever on 2006-08-31
I noticed on the [FreeBob page]("http://freebob.sourceforge.net/index.php/News") that the new version of Jack 0.101.1 has FreeBob built in and it is available at [http://sourceforge.net/projects/jackit](http://sourceforge.net/projects/jackit).  I have two questions:

1. Would it be best to update to Jack 0.101.1 to get FreeBob capability on my system, or would it be better to stick with the current Ubuntu build of Jack and build/install FreeBob?

2.  Can anyone direct me to a wiki or some other resource that explains how to download stuff?  My only exposure to linux is Ubuntu and I have never downloaded anything outside of using synaptic package manager (I only recently started messing with apt-get in a terminal - I'm really moving up in the linux world ;)).

Thanks for any help!

---

### Post by bloodniece on 2006-09-20
You can install the new (jackd 0.101.1) by downloading the source tarball from [URL="http://prdownloads.sourceforge.net/jackit/jack-audio-connection-kit-0.101.1.tar.gz?download"]
Here[/URL].
Make sure you have build-essential installed.
Terminal:
```
sudo apt-get install build-essential
```
Install checkinstall *(not necessary but makes installation easy, checkinstall creates a deb package and installs it. You can later uninstall with synaptic.)*
```
sudo apt-get install checkinstall
```
Untar and decompress tarball
```
tar zxvf jack-audio-connection-kit-0.101.1.tar.gz
```
cd into jack folder
```
cd jack*
```
```
./configure
```
```
make
```
Create DEB package and install (optional, but recommended)
```
sudo checkinstall
```
or
```
sudo make install
```

If all goes well, see if jack will run.
```
jackd
```

I have a Firebox and Dapper, I'll let you guys know how it turns out.

Enjoy and good luck,
Bloodniece

---

### Post by dolson on 2006-09-20
> **libertyforever said:**
> Would it be appropriate to tell me who that was so I can ask them if they would still be willing to do it - or at least if they would be willing to help me out?


Would it be possible to add the newer Jack version to Dapper and thus get FreeBob in the process?

They got back to me, and I remember now what happened. There was an issue with the wiki at the time, and they couldn't paste their tutorial into our wiki page. I do recall getting it fixed shortly after and attempting to let them know, but for whatever reason, it just didn't happen. However, apparently the author of FreeBob asked him/her to take down the tutorial and link directly to the official how-to. So that's where I will point you... To the FreeBob page.

---

### Post by bloodniece on 2006-09-21
Well, I've decided to live on the bleeding edge to make life easier.
Installed Edgy, installed FreeBob per the freebob page tutorial for debian.

I have freebob running with jack and I got the Firebox to work for one session with Ardour. :) :(
I have the raw1394 module loaded in /etc/modules
and lsmod|grep 1394 
gives me this:
```
dv1394                 22232  0 
raw1394                30712  0 
ohci1394               37296  1 dv1394
ieee1394              307000  4 sbp2,dv1394,raw1394,ohci1394

```


Jack keeps barking about raw1394 not being loaded though. :(

---

### Post by bloodniece on 2006-09-21
Well, I'm proud to say I have the Presonus Firebox up and running on Edgy using:
JACK 0.101.1 
qjackctl
Freebob packages from Freebob site

The real trick is setting:
```
sudo chmod a+g /dev/raw1394
```
I have to do this after every boot, so I'm sure there is something I'm not setting right. 
The latency needs some fussing with in Ardour, but it works.
I haven't tested it rigorously using a 6 inputs at 8 outs at once, but it was nice to see that little red light turn blue.

---

### Post by dolson on 2006-09-22
Who is the owner and group of that device? Perhaps you just need group membership instead of changing permissions on every boot.

---

### Post by jbp006 on 2006-11-20
Can anyone give me advice on how to get Freebob working on Edgy? I tried to install based on the instructions for Debian on the Freebob site, but this failed due to libasound2 dependencies. It looks like Freebob needs greater than Alsa 1.0.10. I tried to upgrade to the latest version of Alsa based on the Ubuntu Studio wiki directions found:
[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard)

Everything went apparently went OK with that, but after reboot and another attempt to install Freebob again, it looks as if version 1.0.10 of Alsa is still present on my system. Do I need to remove Alsa entirely before an updrade works?

---

### Post by plong0 on 2007-01-11
I am trying to get my Firebox to run under Edgy...
I am working on setting up FreeBoB via the instructions on [*Compiling from SVN HOWTO*]("http://freebob.sourceforge.net/index.php/Compiling_from_SVN_HOWTO") ... but having problems with installing libiec61883 ... 
when I do the **./configure --prefix=/usr** command it says...

> checking for LIBRAW1394... configure: error: Package requirements (libraw1394 >= 1.2.1) were not met:

Requested 'libraw1394 >= 1.2.1' but version of libraw1394 is 

I think it is because I have the libraw1394 1.2.1-ubuntu version installed and it is not recognizing it
I did the instructions for installing libraw1394 from svn, but I guess it still uses the ubuntu version (which I'd like to keep because it has some other dependencies)

Anyone have suggestions?

Thanks!

---

### Post by plong0 on 2007-01-12
took another run at it tonight and managed to get freebob and jack installed!
can now do jackd -d freebob and get the groovy blue light!
to solve my problem ...
sudo vi /usr/lib/pkgconfig/libraw1394.pc
and modified ...
Version:
into
Version: 1.2.1
the rest of the install went nicely from there

managed to get qjackctl up and running... had to compile it from tarball in order to work with freebob

Now I can run jack with qjackctl and I'm working on getting Ardour to work correctly ... 
tried installing ardour with Synaptic (thought maybe I would be lucky?) and it wouldn't start, complaining Jack wasn't running
tried downloading the source and compiling / running it .. managed to get it running, but after it's creates the session, it crashes.  I think it may be something with the dependencies and I just got lucky that it compiled.  Gonna have another look at it later

---

### Post by plong0 on 2007-01-12
gave up on Ardour and managed to get it working with Audacity ... still need to play with it a bit more, but I definitely saw the signal being recorded in Audacity

when configuring audacity, be sure to add the --with-portaudio=v19 option (default is 18, which doesn't support jack)

start qjackctl
start audacity
in audacity in the audio i/o, you can select firebox
and should be able to see the firebox-audacity connection in qjackctl's Connections window

I'm happy I was able to get it working on Ubuntu, but for compatibility with my friends who all use windows + cubase, I'm just going to use my other pc for recording

---

### Post by honkycondor on 2007-01-15
```
sudo chmod a+g /dev/raw1394
```
yeah that was the last step for me too. I fixed it so I don't have to do that with

```
sudo chown root:audio /dev/raw1394
```
the group was set to drive instead of audio. 
I haven't got qjackctl to compile (it asks me to set QTDIR?) but I'm working around it with patchage until I feel like messing with it. 

(P.S. is there any way to get other programs, perhaps Firefox, to output to jack. I don't think there is unless they are built with some sort of jack output module, but it would be nice)

---

### Post by plong0 on 2007-01-16
make sure you have the qt3-dev-tools package installed (sudo apt-get install qt3-dev-tools)
then do ...
QTDIR = /usr/share/qt3
export QTDIR
and it should compile

I found for it to work with freebob drivers, I had to compile everything from source... loading it with apt-get or synaptic didn't seem to pick it up

---

