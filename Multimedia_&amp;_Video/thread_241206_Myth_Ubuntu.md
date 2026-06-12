---
title: "Myth Ubuntu?"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by crispy_420 on 2006-08-22
Just wondering if there has ever been talk about a side project like this? What could be better than this? Ubuntu & MythTV together.

I tried to install MythDora and could not get TV-Out working from default install. That is a major thing for me since I got my system all plug-in and setup in entertainment center. But in contrast, when I install Ubuntu on the same setup it just worked.

I think many others would like a project like this. Install and be ready to go without all the headaches. If MythDora is possible why not this?

---

### Post by basketcase on 2006-10-13
Hate to bring a topic from the past, but I've been considering just this.  I should have my hardware soon, and I'll know more then.  

subscribed...

---

### Post by Titus A Duxass on 2006-10-14
Crispy - MythDora will not help with your TV-out, you have to do that yourself.
You need to edit your xorg.conf file.

---

### Post by crispy_420 on 2006-10-15
Well in the mean time I just took my time and setup mythtv under ubuntu. As far as mythdora, I'll try it again in the future when I get a extra TV-card sitting aside.

And I thought I would never get a reply to this thread.

---

### Post by superm1 on 2006-10-30
Crispy_420 
I'm looking to start a project like this now that the packages are shaping up in the repositories.  I'll put together a brain dump of it eventually on a wiki page.

---

### Post by basketcase on 2006-10-30
> **superm1 said:**
> Crispy_420 
I'm looking to start a project like this now that the packages are shaping up in the repositories.  I'll put together a brain dump of it eventually on a wiki page.
Here is a post I made a while back...if you start working on this project. 

[http://ubuntuforums.org/showthread.php?t=279972](http://ubuntuforums.org/showthread.php?t=279972)

---

### Post by superm1 on 2006-10-30
basketcase -

I will talk with cecil and find out if there is any validity to knoppmyth being switched to ubuntu based.  I'm hoping that by the time a mythbuntu project emerges, things will be a lot easier to understand and much more straight forward.  Lots of people have had issues with mysql, and a lot of it stems because there were some pretty drastic changes with the way mysql was handled between .18 and .20 without damage recovery.

In the meanwhile, if your inclined to give ubuntu a 4th chance before mythbuntu emerges, take a look at the howto that I have written for edgy.  I plan to maintain this as I update the packages, and add from any feedback given to me about it.  I have already had 4 people or so contact me about it with plenty of suggestions for it, and I've verified it to be functional myself in virtual machines and on my network.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by basketcase on 2006-10-30
Ubuntu will get as many chances necessary to get it up and running.  I've wanted to be part of an open-source project for a while now, and I think I might be biting off more than I can chew, but it is something I've very interested in, which should give me the drive necessary to make something happen.  

Will definitely keep up with the links you posted.  

I'll see if I can find in regards to Myth and switching to ubuntu

---

### Post by Jerk on 2006-10-31
I had to go to Win MCE on my HTPC because MythTV does not support my tuner card, "WinTV PVR USB2."

My girlfriend HATES Win MCE she wants me to do that "Lidix thing" I was talking about before I had to install Win MCE. So, as soon as I can I'm buying a new tv tuner card and then I'm back on the Myth train.

I'd like to see a "UbunTV" release but is it possible to have a one-size-fits-all solution?

---

### Post by superm1 on 2006-10-31
Hopefully the plan is to have myth very easily installable within the next release or two, to the point that you don't have to work to build lirc or ivtv.  Myth should install right into those roles described, without too much hassle.  One size fits all eventually ;)

---

### Post by basketcase on 2006-11-01
Complete and TOTAL failure with Ubuntu 6.06 and 6.10 installation...Primarily with ivtv.  Didn't even try to install Mythtv -- didn't get that far.  

I've been at this long enough tonight.  Come back to it another day.

---

### Post by superm1 on 2006-11-01
Where did things go south with ivtv?  You followed the ivtv installation for edgy off the wiki right?

---

### Post by loboson on 2006-11-02
Some problems here installing MythTV, but all solved now. Running nicely and crisply, small things to solve, tough (i.e. TV image doesn't fill all the screen..)



> **basketcase said:**
> Complete and TOTAL failure with Ubuntu 6.06 and 6.10 installation...Primarily with ivtv.  Didn't even try to install Mythtv -- didn't get that far.  

I've been at this long enough tonight.  Come back to it another day.

---

### Post by basketcase on 2006-11-02
Okay...

I went back and looked at the wiki...I knew I needed to install ivtv, but didn't see the how-to on installing ivtv for edgy.  

So I went loosely off the dapper ivtv installation instructions.  

When I was creating a link to /usr/src/linux -- it would tell me file exists, so it couldn't create the link, or it already had, and wouldn't create it again.  

When I went to edit /usr/src/linux/Makefile -- It said file did not exist.  

So it said /usr/src/linux didn't exist, but I could cd /usr/src

Made no sense to me.  

After looking at the wiki, I see ivtv for edgy, and I'll go back and see what I can come up with.  I wonder how I COMPLETELY undo what I did last night, as it seems in past experiences the only way to get rid of it completely was to just start over -- most time spent just reinstalling. 

Will look at it tonight and see what I come up with.  Won't be able to do anything with it till Sunday/Monday.

---

### Post by basketcase on 2006-11-03
Per this link: [https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

> root@ubuntu:~# sudo apt-get install ivtv-source devscripts ivtv-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ivtv-source
So I'm stuck right there!

With this

> sudo apt-get install ivtv-source devscripts ivtv-utils

Was able to install devscripts, but not ivtv-utils.  

Moved on.  

Was able to: 
> wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)  


When doing this...

> export DEBFULLNAME="Mario Limonciello" 
export DEBEMAIL="superm1@ubuntu.com"
sudo ivtv-make-fwpkg pvr_1.18.21.22254_inf.zip 

> root@ubuntu:~# sudo ivtv-make-fwpkg pvr_1.18.21.22254_inf.zip
sudo: ivtv-make-fwpkg: command not found


I basically didn't go any further.

---

### Post by Titus A Duxass on 2006-11-03
Re: IVTV - if you do an apt-cache search ivtv it comes up with three files, the source, the utils and a lib file.  Try installing that as well.

For the next step I think that you should extract the zip file first.  That seems logical to me and if you read Hyam's how-to it is one of the steps during the IVTV process.

---

### Post by superm1 on 2006-11-03
> **basketcase said:**
> Per this link: [https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

So I'm stuck right there!

With this



Was able to install devscripts, but not ivtv-utils.  

Moved on.  

Was able to: 



When doing this...





I basically didn't go any further.

Sounds like your missing universe and multiverse.  Enable both these repositories and the rest of the steps should work out fine.

---

### Post by basketcase on 2006-11-03
They were uncommented from the beginning.  

> bdmorrison@ubuntu:~$ vi /etc/apt/sources.list
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


---

### Post by basketcase on 2006-11-03
> **Titus A Duxass said:**
> Re: IVTV - if you do an apt-cache search ivtv it comes up with three files, the source, the utils and a lib file.  Try installing that as well.

For the next step I think that you should extract the zip file first.  That seems logical to me and if you read Hyam's how-to it is one of the steps during the IVTV process.


>  bdmorrison@ubuntu:~$ apt-cache search ivtv
libvideo-ivtv-perl - Perl extension for using V4l2 in the ivtv perl scripts

So no go...

---

### Post by basketcase on 2006-11-03
per the comment regarding extract the zip file, that didn't work, but apt-get install unzip I was then able to get that part to work.  

On I go.  Will report back with any further issues

---

### Post by superm1 on 2006-11-03
Yes they are uncommented for edgy backports, edgy updates and edgy security updates.

You need to have them also for "edgy".

Here is a quick graphical way to make sure that the repos are setup correctly.  This is also detailed in the mythtv installation guide, you might have just mixed up a step.
[https://help.ubuntu.com/community/MythTV/Install/Live/Edgy/Repositories](https://help.ubuntu.com/community/MythTV/Install/Live/Edgy/Repositories)

---

### Post by superm1 on 2006-11-03
Also,

unzip will be installed as a dependency of ivtv-utils, it doesn't need to be installed seperately.

---

### Post by basketcase on 2006-11-03
No gnome, so your graphical representation doesn't help me.  I searched for forum for edgy source lists and found this...

[http://www.ubuntuforums.org/showthread.php?t=265326](http://www.ubuntuforums.org/showthread.php?t=265326)

Pasted one of theirs into mine, and I am now able to get

> sudo apt-get install mythtv-frontend gdm edgy-gdm-themes xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu

So....moving ahead!

---

### Post by basketcase on 2006-11-03
Making Progress...

When I do dmesq

Here is the output:

> 

[42949399.800000] ivtv:  ==================== START INIT IVTV ==================                                                         ==
[42949399.800000] ivtv:  version 0.7.0 (tagged release) loading
[42949399.800000] ivtv:  Linux version: 2.6.17-10-server SMP mod_unload 686 REGP                                                         ARM gcc-4.1
[42949399.800000] ivtv:  In case of problems please include the debug info betwe                                                         en
[42949399.800000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42949399.800000] ivtv:  any module options, when mailing the ivtv-users mailing                                                         list.
[42949399.800000] ivtv0: Autodetected Hauppauge WinTV PVR-350 card (cx23415 base                                                         d)
[42949399.810000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[42949399.810000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (                                                         level, high) -> IRQ 201
[42949399.810000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[42949399.860000] tveeprom 2-0050: Hauppauge model 48132, rev K268, serial# 8603                                                         000
[42949399.860000] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, typ                                                         e 47)
[42949399.860000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[42949399.860000] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[42949399.860000] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[42949399.860000] tveeprom 2-0050: has radio, has IR remote
[42949399.990000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[42949400.210000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[42949400.270000] saa7115 2-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[42949400.500000] saa7127 2-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[42949400.530000] msp3400 2-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[42949400.530000] msp3400 2-0040: MSP4448G-B3 supports radio, mode is autodetect                                                          and autoselect
[42949401.230000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42949401.270000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[42949401.540000] ivtv0: Encoder revision: 0x02050032
[42949401.560000] ivtv0: Decoder revision: 0x02020023
[42949401.560000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (                                                         4096KB total)
[42949401.560000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2                                                         048KB total)
[42949401.560000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2                                                         048KB total)
[42949401.560000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffe                                                         rs (2048KB total)
[42949401.560000] ivtv0: Create encoder radio stream
[42949401.560000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1                                                         024KB total)
[42949401.560000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (10                                                         24KB total)
[42949401.560000] ivtv0: Create decoder VOUT stream
[42949401.560000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (10                                                         24KB total)
[42949401.650000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[42949401.690000] NET: Registered protocol family 17
[42949401.780000] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[42949401.840000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[42949401.840000] ivtv:  ====================  END INIT IVTV  ==================                                                         ==

I'm going to try and rebuild IVTV and see what I come up with.  

Man it seems my source list being off was causing my of my problems.  Seems easier so far in some regards with Edgy.

*** Edit ***

I removed/rebuilt IVTV and I believe the output above says I'm successful!!

---

### Post by superm1 on 2006-11-03
> **basketcase said:**
> Making Progress...

When I do dmesq

Here is the output:

I'm going to try and rebuild IVTV and see what I come up with.  

Man it seems my source list being off was causing my of my problems.  Seems easier so far in some regards with Edgy.

*** Edit ***

I removed/rebuilt IVTV and I believe the output above says I'm successful!!
Looks like your chugging along just fine :).  Glad to hear things are working.

---

### Post by basketcase on 2006-11-03
doing the plug-ins now, then going for playback and media. 

The one thing I'm wondering, is with knoppmyth and fedoramyth they both start with mythv user instead of my user account.  

When I do sudo gdmsetup, there is no option available for me to select mythtv as the user.  How do I set it so that mythtv user account automatically logs in and mythtv-frontend starts up?

---

### Post by superm1 on 2006-11-03
This is because of the mythtv user having a UID < 1000 (eg not a normally logging in user).  Doing it as the normal user account will work out fine.  If you really want to log in as the "mythtv" user, then you will have to manually edit the gdm.conf file in /etc/X11/

---

### Post by basketcase on 2006-11-03
Myth is up and running (both back end and front end).  I guess it likes 127.0.0.1 better than it's IP address on the network.  

When I try and import a CD, it starts to import it, then ejects the disk and that is that.  It doesn't import it.  

I'm wondering if it isn't a permission issue on /var/lib

Problem is, I don't know what the permissions should be.  777?  On Mythtv?  mythdvd?  mythvideo?    ls -ltra of /var/lib shows that the prior mentioned myth* files are all owned by Mythtv user.  So I must be off base with my assumption.  

Or am I completely off base here?

A couple of other things I noticed.  

MythWeb -- nothing comes up
Netflix -- Nothing comes up
Weather -- Does Come up
News -- Nothing comes up

---

### Post by basketcase on 2006-11-03
Another question I'm left it.  I see lirc doesn't work with Edgy.  sudo apt-get install lirc got me 0.8.0 or something of the sorts, but I see it needs to be patched.  How do I go about patching it?

---

### Post by basketcase on 2006-11-03
> **basketcase said:**
> Another question I'm left it.  I see lirc doesn't work with Edgy.  sudo apt-get install lirc got me 0.8.0 or something of the sorts, but I see it needs to be patched.  How do I go about patching it?
Answered my own question
[http://ubuntuforums.org/showthread.php?p=1711097](http://ubuntuforums.org/showthread.php?p=1711097)
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

but didn't work for me. 

I still get LIRC is not configured when I try and start it.  I replied in your other thread Mario.

---

### Post by Titus A Duxass on 2006-11-04
Basketcase,
I have just done a fresh server install of edgy, then configure my wireless card.
Then I followed the wiki and had 100% success.  There is no need to extract any zip files.
I think this is done with the commands in the wiki.

It is certainly quicker than the manual installation of ivtv described in Hyam's how-to.

I just wish I new what the commands mean.

---

### Post by superm1 on 2006-11-04
Well for the curious, I'll detail what some of the commands are doing.

```
apt-get
```
downloads and installs packages

```
wget
```
downloads a file from a website supplied as an argument

```
m-a clean
```
cleans up any old builds of a package by module-assistant

```
m-a update,prepare
```
updates the /usr/src/linux symlink to the currently installed headers and downloads the newer headers.  This can be broken into two seperate steps as well

```
m-a a-i ivtv
```
runs module assistant in auto build/install mode.  This will build the module into a deb and install it.

```

export BLAH="BLAH3"
```
sets up an envrionment variable BLAH to be set to the value BLAH3

```
ivtv-make-fwpkg
```
Builds a firmware package from a windows driver

---

### Post by Yumi on 2006-11-04
Reading through the thread I get the impression that the right hardware is the prerequisite for MythTV to work. But then it will work flawless.

Rather to solve all the problems arising from exotic hardware, does somebody have a list of all hardware components required to build a Ubuntu TV box with computer (Internet) capabilities and on which MythTV installs easy. 

I found a thread [http://www.tomshardware.com/2006/10/16/building_a_low-power_home_theater_pc_system/](http://www.tomshardware.com/2006/10/16/building_a_low-power_home_theater_pc_system/)  
outlining basic considerations like low noise levels and good looks. But it does not contain references to the operating system. However, I think it asumes MythTV as the TV program.

---

### Post by basketcase on 2006-11-04
[http://mythtv.org/docs/mythtv-HOWTO-3.html](http://mythtv.org/docs/mythtv-HOWTO-3.html)

FWIW, I have a PVR-350 card, box is a Shuttle XPC, AMD 2400+, 512MB DDR333 RAM, and only a 40GB HDD for now just for testing purposes.  Using the remote that came with the card.  

Only using the local cable company, so I don't need to control a dish reciever yet.

---

### Post by Titus A Duxass on 2006-11-05
SuperM1,
Thanks for the clarification.

---

### Post by basketcase on 2006-11-14
> **Titus A Duxass said:**
> Basketcase,
I have just done a fresh server install of edgy, then configure my wireless card.
Then I followed the wiki and had 100% success.  There is no need to extract any zip files.
I think this is done with the commands in the wiki.

It is certainly quicker than the manual installation of ivtv described in Hyam's how-to.

I just wish I new what the commands mean.
Titus, 
I started over and was successful.  The only thing I need to fix is the mapping of lircrc so that I can navigate around with the remote -- the configuration I downloaded didn't work like I wanted it to.

---

### Post by NT4usB on 2006-11-15
Just popping in to sing praises for MythTV 0.20 on Dapper per superm1's instructions.
Been struggling with making DVD's of programs using howto's and programs (nuv2disc, etc) from all over the web.
Something's broke on the box though 'cause I keep getting errors regarding locals, libc6, C something is broke and reverting to default... etc. when I try to install or run new programs.
Stumbled into the archive section of myth and to my surprise, myth has a perfectly good DVD program. Don't need no stinkin' other software. (all along I thought it was for just archiving mythtv programs in myth format...doh!)
Burned a couple disks to share with friends and they came out good.

---

### Post by cborga1985 on 2007-07-04
> **Jerk said:**
> I had to go to Win MCE on my HTPC because MythTV does not support my tuner card, "WinTV PVR USB2."

My girlfriend HATES Win MCE she wants me to do that "Lidix thing" I was talking about before I had to install Win MCE. So, as soon as I can I'm buying a new tv tuner card and then I'm back on the Myth train.

I'd like to see a "UbunTV" release but is it possible to have a one-size-fits-all solution?

This does not work. You just have to build a new kernel with support. Than extract the firmware from the windows drivers. [http://ubuntuforums.org/showthread.php?p=2040162](http://ubuntuforums.org/showthread.php?p=2040162)

---

