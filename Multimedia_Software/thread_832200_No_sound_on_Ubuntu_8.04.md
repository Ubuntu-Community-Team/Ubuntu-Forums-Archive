---
title: "No sound on Ubuntu 8.04"
date: 2008-06-17
forum: Multimedia Software
---

### Post by Vaune on 2008-06-17
Hello all,

I JUST started using Ubuntu after a long while deciding I should.  I installed using Wubi, installed all the necessary updates and am looking to start my epic quest into the wide world of LINUX!!! 

One small problem.

I have no idea what the **** I'm doing!  That will come in time, but one thing I want to get resolved immediately is a no sound issue.  As I said I have Ubuntu 8.04, and I'm not even sure where to start.

Should I run a diag?  If so, where do I start, what am I looking for?

If I don't need to diag, what course of action would be best to follow to isolate why I'm not getting sound, or perhaps there is an update I should download?

I'm not asking for a step by step to learn Ubuntu, I can find guides for that, I guess I'm just looking for a shove in the right direction in fixing problems like this in the future.

Any help will be met with the greatest enthusiasm I can muster over a forum!

//Vaune

---

### Post by Vaune on 2008-06-17
I suppose I should start by looking at the stickied guide about sound problems, huh?  LACK OF PERCEPTION FTW!!

---

### Post by Vaune on 2008-06-17
Ok, so I'm looking at the alsa site, looking for my chipset (SB0350 Audigy 2 ZS - Creative) and can't find that.  

Phew...I don't even know how to ask for help.  Remeber the first time you ever sat down at a computer?  Thats how I feel O_o

---

### Post by Yellow Pasque on 2008-06-17
What kind of sound device do you have? Perhaps these links will help you:
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

### Post by Vaune on 2008-06-17
By sound device do you mean:

Audio Controller:
Creative Labs
Audigy 2 ZS SB0350

---

### Post by Yellow Pasque on 2008-06-17
> **Vaune said:**
> By sound device do you mean:

Audio Controller:
Creative Labs
Audigy 2 ZS SB0350
Yes. Try the OSS4 guide.

---

### Post by Vaune on 2008-06-17
Will do, I'll post here to let you know how it turns out or if I run into any debilitating errors!

Muchos Gracias senior!


I'm not sure what OS Version I'm running.  Rather which OSS Driver to DL.  I'll just download the x86 DEB one I guess.

404 Page Not Found - Download is missing -_-
Any other places I can DL the driver?

---

### Post by Yellow Pasque on 2008-06-17
I also get a 404 error. They just releasesd that build today, so maybe they didn't get the .deb package built.
To figure out what OS you're running:
```
uname -a
```

I do see that the .tar.bz2 package is available. Try downloading that one. Save in your /home directory ~/

Follow the guide as normal, but when you get to the step where you install the .deb, do this instead:

```
sudo apt-get -y install linux-headers-`uname -r` build-essential sed gawk libtool libgtk2.0-dev libesd0 linux-sound-base gcc-multilib libesd0-dev binutils esound esound-common esound-clients gstreamer0.10-esd bc libssl0.9.8 libssl-dev
sudo mv ~/oss-linux-v4.0-1016-i386.tar.bz2 /
cd /
sudo tar -xjvf oss-linux-v4.0-1016-i386.tar.bz2
sudo sh /usr/lib/oss/build/install.sh

```

---

### Post by Vaune on 2008-06-17
Will do, I'll keep you updated on my progress and any snags I run into.

---

### Post by Vaune on 2008-06-17
Well I'm confused.

I'm at step 7, I think I've done it correctly up to this point.  I'm not getting an errors except for when I try to change the volume via slider.

"No volume control GStreamer plugins and/or devices found."

I really have absolutley no idea whats going on right now.  I have no idea if I'm doing it correctly, I have no idea what most of the commands and lingo means.  I am completely lost.

ossdetect -v and ossinfo result in a "command does not exist" message.

ossxmix does not exist either, so the panel icon cannot launch anything.

---

### Post by Yellow Pasque on 2008-06-17
I'm not quite sure what went wrong there. Let's purge that install and try fetching OSS4.1 from the repo.
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

```
sudo apt-get -y install mercurial
cd /usr/src/
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss
cd oss/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

---

### Post by Vaune on 2008-06-17
rm: cannot remove `oss-linux': No such file or directory

Also, I'm not sure if my find function is working.  Every time I try and use it, nothing happens.

---

### Post by Yellow Pasque on 2008-06-17
> rm: cannot remove `oss-linux': No such file or directory
Apparently, it didn't install and there's nothing to purge. Move forward with the commands in my last post.

---

### Post by Vaune on 2008-06-17
Just did, command has completed with no errors.

---

### Post by Yellow Pasque on 2008-06-17
So, do you have sound?

---

### Post by Vaune on 2008-06-17
No, and further more all my songs in Rythmbox are all getting little red error signs next to them.  Something about connection cannot be established.

---

### Post by Yellow Pasque on 2008-06-17
Ok. Run these commands:
```
sudo soundoff
sudo ossdetect -v
ossinfo -d
sudo soundon
```

---

### Post by Vaune on 2008-06-17
None of those commands were found.
Nothing was executed.

EDIT:  BRB 5-10 min

---

### Post by Yellow Pasque on 2008-06-17
You ran these commands successfully?
```
sudo apt-get -y install mercurial
cd /usr/src/
sudo hg clone http://mercurial.opensound.com/ oss-devel
cd ~/
mkdir oss
cd oss/
sudo sh /usr/src/oss-devel/configure
sudo make
sudo make install
```

---

### Post by Vaune on 2008-06-17
On the sudo make command, at the very end I got:

cc1: warnings being treated as errors
vmix_output.c: In function &#8216;process_limiter&#8217;:
vmix_output.c:59: warning: unused variable &#8216;outclip&#8217;
vmix_output.c:58: warning: unused variable &#8216;ioutgain&#8217;
make[3]: *** [../../../target/objects/vmix_output.o] Error 1
make[3]: Leaving directory `/home/vaune/oss/kernel/framework/vmix_core'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/vaune/oss/kernel/framework'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/vaune/oss/kernel'
make: *** [subdirs] Error 1



On sudo make install, I got:

cc1: warnings being treated as errors
vmix_output.c: In function &#8216;process_limiter&#8217;:
vmix_output.c:59: warning: unused variable &#8216;outclip&#8217;
vmix_output.c:58: warning: unused variable &#8216;ioutgain&#8217;
make[3]: *** [../../../target/objects/vmix_output.o] Error 1
make[3]: Leaving directory `/home/vaune/oss/kernel/framework/vmix_core'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/vaune/oss/kernel/framework'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/vaune/oss/kernel'
make: *** [subdirs] Error 1


I take it it DIDN'T run successfully.

---

### Post by Yellow Pasque on 2008-06-17
```
gksudo gedit /usr/src/oss-devel/kernel/framework/vmix_core/vmix_output.c
```
Go to line 58 and delete this:
```
const unsigned ioutgain = ((unsigned) 0x100) * 0x100 >> 8;
  const int outclip =
    ((unsigned) 0x100) * 0x7FFF + (((unsigned) 0x100) * 0xFF >> 8)
```
Save and try it again from the beginning
```
cd ~/oss
sudo rm -rf *
ls -la
```
There may be some leftover configuration files. rm them too.

---

### Post by Vaune on 2008-06-17
Command executed.

Results from final ls -la

> drwxr-xr-x  2 vaune vaune 4096 2008-06-17 17:07 .
drwxr-xr-x 35 vaune vaune 4096 2008-06-17 16:41 ..
-rw-r--r--  1 root  root     0 2008-06-17 16:41 .depend
-rw-r--r--  1 root  root    49 2008-06-17 16:41 .directories
lrwxrwxrwx  1 root  root    26 2008-06-17 16:41 .hgtags -> /usr/src/oss-devel/.hgtags
-rw-r--r--  1 root  root    19 2008-06-17 16:41 .makefile
-rw-r--r--  1 root  root    28 2008-06-17 16:41 .version


Anything else I should rm?

---

### Post by Yellow Pasque on 2008-06-17
Yes, rm all those files. The directory needs to be empty.

---

### Post by Vaune on 2008-06-17
Done

final ls -la
> vaune@vaune-desktop:~/oss$ ls -la
total 8
drwxr-xr-x  2 vaune vaune 4096 2008-06-17 17:39 .
drwxr-xr-x 35 vaune vaune 4096 2008-06-17 16:41 ..


---

### Post by Yellow Pasque on 2008-06-17
> **Vaune said:**
> Done

final ls -la
Awesome. Try it again :P

---

### Post by Vaune on 2008-06-17
Sudo make worked fine (I think)
However, sudo make install gave the following results:

> OSS build environment set up for REGPARM kernels

Building module osscore
Failed to compile OSS
make[1]: Entering directory `/usr/lib/oss/build'
make -C /lib/modules/2.6.24-19-generic/build M=/usr/lib/oss/build modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/oss/build/osscore.o
In file included from /usr/lib/oss/build/osscore.c:41:
/usr/lib/oss/build/../include/internals/audio_core.h:97: error: expected specifier-qualifier-list before &#8216;oss_dma_handle_t&#8217;
make[3]: *** [/usr/lib/oss/build/osscore.o] Error 1
make[2]: *** [_module_/usr/lib/oss/build] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/lib/oss/build'
make: *** [install] Error 2


---

### Post by Vaune on 2008-06-17
Could be because I have the wrong type, or version, of oss?

---

### Post by Vaune on 2008-06-17
Ok so it turns out I have amd64, who knew?  Anyways, I have oss loaded, sudo soundon works and all that stuff.

However, I still don't have sound.  I can't open the volume control because it says I don't have GStreamer plugins.

I tried dl'ing them off of your post, but I'm not sure how to install them.


EDIT:

Ok, I think I installed the GStreamer plugin, but I still can't unmute my sound.  IE I'm still hearing nothing.

---

### Post by DeWilly on 2008-06-18
After months of trying sound worked finally.

Allthough everything worked fine under Windows XP it would simply not work under Ubuntu 7.10 nor 8.04

I blamed Ubuntu for it.

But I did injustice.

When I assembled my computer a few years back a Soundblaster Audigy was installed and to avoid conflicts the onboard sound processor disabled.

Then time passed and due to what I dont know ( maybe CMOS battery low ) the CMOS was reset to Automatic detection. Under Windows everything was still OK but Under Ubuntu no way.

So During Power On Self Test (POST). 
:)Stop the memory check bij pressing DEL.
Then go in the CMOS setup and look for onboard soundchip
Set detection to NO
Save CMOS and EXIT
Restart

Huray everything worked fine.

So Ubuntu My apologies.

Keywords

Audigy
Soundblaster
Sound
ASUS P4T-U

---

