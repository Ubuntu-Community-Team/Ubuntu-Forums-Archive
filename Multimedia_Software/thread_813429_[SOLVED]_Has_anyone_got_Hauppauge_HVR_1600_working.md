---
title: "[SOLVED] Has anyone got Hauppauge HVR 1600 working?"
date: 2008-05-30
forum: Multimedia Software
---

### Post by sofasurfer on 2008-05-30
I read lots of older post stating that Hauppauge HVR 1600 does not work on Ubuntu. So, has anyone more recently had any success with it on Hardy?

---

### Post by MikeCheck on 2008-06-01
I am also wondering this.  I was looking to buy one.

---

### Post by MikeCheck on 2008-06-01
This is from the Hauppauge website:
> Linux support for the WinTV-HVR-1600
Linux support for the WinTV-HVR-1600 is in the upcoming kernel 2.6.26 release.

Also, there is WinTV-HVR-1600 Linux support for both the analog TV tuner and the digital TV tuner available at LinuxTV.ORG in the "cx18" section.

---

### Post by sofasurfer on 2008-06-01
I saw this info about an hour ago and was going to post it but you beat me to it. Good job.

So, does this mean that the HVR-1600 will be easier to get going or does it mean the it will be automatically detected and operational?

---

### Post by MikeCheck on 2008-06-01
No idea.  Hopefully someone else can answer that, because I want an HVR card, but I am waiting for a definite yes or no on if they work or not.

---

### Post by nwadams on 2008-06-01
i'm tempted to run down to staples tomorrow, try it, adn take it back if it doesnt work (14 day return policy on everything)
so i'll post tomorrow if it works

---

### Post by sofasurfer on 2008-06-01
Great! Looking forward to reading your review.

---

### Post by sofasurfer on 2008-06-02
I decided to try to install the driver for Hauppauge HVR 1600.
Below is the record of what I have done and what happened. I did not finish the installation as you will see. I don't know what my next step is, or if I am doing things correctly so far.

Installing driver for Hauppauge HVR-1600
------------------------------

All information came from this site:
[http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

I obtained driver from this site:
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

Downloaded file was saved to /home/daryl/temporary/v4l-dvb-398b07fdfe79.tar.bz2

I created a directory at /home/daryl/temporary/unpacked.
This is where I extracted the files to.
The resulting path is:
/home/daryl/temporary/unpacked/v4l-dvb-398b07fdfe79

Open terminal and type cd /home/daryl/temporary/unpacked/v4l-dvb-398b07fdfe79
Now type "make menuconfig". I got an error, so I typed "make".
The output was a huge list of files (modules?) and this message:

make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
./scripts/rmmod.pl check
found 221 modules
make[1]: Leaving directory `/home/daryl/temporary/unpacked/v4l-dvb-398b07fdfe79/v4l'.

Now I type "make install" and this is the output:

daryl@ubuntu:~/temporary/unpacked/v4l-dvb-398b07fdfe79$ make install

make -C /home/daryl/temporary/unpacked/v4l-dvb-398b07fdfe79/v4l install
make[1]: Entering directory `/home/daryl/temporary/unpacked/v4l-dvb-398b07fdfe79/v4l'
Stripping debug info from files
-e 
Removing obsolete files from /lib/modules/2.6.24-17-generic/kernel/drivers/media/video:
mt20xx.ko rm: remove write-protected regular file `/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/mt20xx.ko'? 

I don't no where to go from here. Any help is appreciated.

---

### Post by sofasurfer on 2008-06-03
I read somewhere that I should install package "build-essential". I did this and whether it was my problem or not I do not know, but I then managed to accomplish Unpack, 'make menuconfig', 'make', 'make install' (as root), 'make unload' (as root) and run 'modprobe cx18'.

If you have trouble with any of the above commands, just try using "sudo". I needed to use sudo for "make menuconfig" and "modprobe cx18".

The next instructions are as follows:

The firmware needs to be extracted from the Windows Hauppauge HVR-1600 driver, available here:

[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)

Unzip, then copy the following files to the firmware directory and rename them as follows:

Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw
Drivers/Driver18/hcw18enc.rom -> v4l-cx23418-cpu.fw
Drivers/Driver18/hcw18mlC.rom -> v4l-cx23418-dig.fw

I do not know where to find the firmware directory. Can anyone help me?

EDIT::
I think that this firmware directory is refering to /lib/firmware/2.6.24-17-generic. Can someone please verify this?

Assuming this is correct, I have so far been unable to copy the files. If this is incorrect, its a good thing I have been unable to copy the files.

Is anyone listening?

---

### Post by saedelaere on 2008-06-03
I think you found the correct path for your firmware files.
In order to copy them there you have to be root.

Please post the output of modprobe cx18

If your tv-card is working you may try out [this frontend]("http://ubuntuforums.org/showthread.php?t=763698").

Bye

---

### Post by sofasurfer on 2008-06-03
modprobe cx18 is supposed to give an output? It didn't.  

daryl@ubuntu:~$ modprobe cx18
daryl@ubuntu:~$ sudo modprobe cx18
[sudo] password for daryl: 
daryl@ubuntu:~$ 

I will copy the files this evening.

---

### Post by sofasurfer on 2008-06-03
I have now added the lines from the Hauppauge driver to the firmware file and change the names as instructed.

I sure wish someone would respond and give me some encouragement before I crash my system.

Now that I have edited the firmware file I hope I won't be sorry when I reboot.

---

### Post by sofasurfer on 2008-06-04
System rebooted with no problems.

I have no clue how to start my Hauppauge TV Tuner. The remote has a 'power' button that does nothing. What should I do to see if things are working?

---

### Post by nwadams on 2008-06-04
ok, i coudlnt' get mine to work out of the box (with mythtv)

---

### Post by sofasurfer on 2008-06-04
So where do we go from here?
For all the people that are trying to get the 1600 running they sure aren't responding to this thread.

And just a side note. I installed the software for Windows on my other hard drive and I couldn't get it going there either. I did get the gui running under windows but the "scan for channels" button that the instructions say to click on does not appear that I could see.

If someone doesn't offer some assistance here I will go try to get the windows version running. At teast if I could do that I could see what I should be able to expect here on the linux side.

---

### Post by sofasurfer on 2008-06-04
I may have found a clue to my problems. Maybe someone could have a look at this. I ran "dmesg" and this is (about 20 percent of) my output:

[ 6509.062542] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.066852] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.066854] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.072254] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.072257] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.076967] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.076969] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.081588] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.081590] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.087209] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.087211] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.090832] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.090834] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.094828] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
[ 6509.094830] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[ 6509.098952] phy0 -> rt2x00usb_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.

---

### Post by sofasurfer on 2008-06-04
Does this mean I glitched my kernel? What should I do?
Come on people, just because the going gets tough doesn't mean give up. Give a brother a hand. Please don't make me reinstall my whole system.

---

### Post by msrinath80 on 2008-06-05
In my experience, most TV cards work flawlessly in Fedora 9 out of the box. You could try just using a liveCD of Fedora 9 and checking if the card/stick is detected through dmesg. Don't forget to copy the firmware to /lib/firmware once you boot the liveCD. At least you'll know that it works. Then you can proceed to breaking your head by trying to get it to work with Ubuntu's Hardy Heron.

---

### Post by sofasurfer on 2008-06-05
I'm so happy to hear from you:-)

I may just try that. I sure have enough disk space for a dual boot.

If anyone cares to comment on whether there are any better distributions specifically for TV Tuners please let me know.

Thanks msrinath80

---

### Post by willoconley on 2008-06-05
I am not sure what that dmesg output is all about, I think it might have something to do with a wifi card.

To get your hauppuage card  working:

# go to tty1, to remove the old firmware you installed
$ sudo /etc/init.d/?dm stop
$ cd pathToV4LDir             # in my case ~/v4l*
$ sudo make unload
$ sudo make install -r

# you can now, if you want
$ sudo /etc/init.d/?dm start
# and go back to tty7
$ sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd ~/v4l*
$ sudo make
$ sudo make install

 now after you copy those firmware files you posted about earlier to /lib/firmware/*currentKernel*

$ sudo reboot
$ dmesg | grep cx18
# near the end should say something like:
[   42.230394] cx18-0: Initialized card #0: Hauppauge HVR-1600

from there its works pretty well in mythtv. And remember every time there is a kernel update you will have to recompile v4l:
$ cd ~/v4l*
$ sudo make unload
$ sudo make disclean
$ sudo make
$ sudo make install
 copy all the firmware to the new kernel directory and reboot

also if you are trying to use this with the nvidia drivers, don't ask me why but it dosn't seem to work out well. [follow this guide]("http://wiki.debian.org/NvidiaGraphicsDrivers") and you should get the two working togethar. <-- That worked for me when I was ok with using the driver version from the repo. I just bought an 9600 and now have to use the nvidia installer, if you do to try adding: 
vmalloc=192M pci=nommconf 
to /boot/grub/menu.lst on the kernel line like:

## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f70a49f8-885a-4942-904b-56a0ae6f68bc ro quiet splash rootflags=data=writeback [COLOR="Red"]vmalloc=192M pci=nommconf[/COLOR]
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

that might work for the drivers in the repo's as well, I haven't tried.

---

### Post by willoconley on 2008-06-05
btw saedelaere, I was going to try out your gui but these drivers don't make a /dev/vbi (whatever that is) as you were saying in your post on the 14th.

p.s. now I see you might have fixed that.

---

### Post by willoconley on 2008-06-05
> **sofasurfer said:**
> I saw this info about an hour ago and was going to post it but you beat me to it. Good job.

So, does this mean that the HVR-1600 will be easier to get going or does it mean the it will be automatically detected and operational?

Ok sorry to triple post but this is something I have been wondering about myself. I think it will be included with vanilla kernels like generic and you will just have to load the module you need or something. Anyway I suppose we have a while yet since we aren't even on 2.6.25 yet.

---

### Post by sofasurfer on 2008-06-05
Willoconley.
In this line "$ cd pathToV4LDir # in my case ~/v4l*" I am confused.

These are my 2 V4L directories, "file:///home/daryl/temporary/v4l-dvb-398b07fdfe79" and "file:///home/daryl/temporary/v4l-dvb-398b07fdfe79.tar.bz2".

Shall I assume that you want me to cd to the 1st one, which is the unzipped file?

---

### Post by willoconley on 2008-06-05
in your case
cd ~/temporary/v4l*

at any rate you can remove both of them after you do 
sudo make install -r

---

### Post by sofasurfer on 2008-06-06
willoconley.

O,o!!!

I followed your instructions and all went well. But when it came time to copy the 3 files to the firmware directory and rename them I did not do this. Instead I looked in the firmware directory and saw that they were still there from before. So I just skipped this step and rebooted and did the dmesg | grep cx18. This is the result...

daryl@ubuntu:~$ dmesg | grep cx18
[   39.151776] cx18:  Start initialization, version 1.0.0
[   39.151841] cx18-0: Initializing card #0
[   39.151845] cx18-0: Autodetected Hauppauge card
[   39.152184] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   39.153382] cx18-0: cx23418 revision 01010000 (B)
[   39.274109] cx18-0: Autodetected Hauppauge HVR-1600
[   39.274111] cx18-0: VBI is not yet supported
[   39.619907] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   39.619927] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   39.621054] cx18-0: Disabled encoder IDX device
[   39.621081] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   39.621084] DVB: registering new adapter (cx18)
[   39.937480] cx18-0: DVB Frontend registered
[   39.937497] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   39.937512] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   41.025804] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   41.027243] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 174716 bytes)
[   41.027305] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   41.027362] cx18-0: Retry loading firmware
[   41.079357] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   41.080801] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 174716 bytes)
[   41.080862] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   41.080921] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   41.081584] cx18:  End initialization
[  142.858135] cx18-0: Failed to initialize on minor 0
[  142.860439] cx18-0: Failed to initialize on minor 24
[  142.862130] cx18-0: Failed to initialize on minor 32
daryl@ubuntu:~$ 

I also noticed that I could not connect to any web sites now. My encryption key needed to be re-entered in the "network" settings. 

So, can you tell what my problem is?
Also, I want to verify whether the directory /lib/firmware/2.6.24-17-generic is the correct place to copy the files to.

Thanks for a GREAT try and for your time and patience.

---

### Post by willoconley on 2008-06-06
yeah /lib/firmware/2.6.24-??-generic is where they need to go, you have to have them in every kernel folder you use the card in. I just keep a copy of the firmware files in /lib/firmware and cp them whenever there is a new kernel. 

[ 41.027243] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 174716 bytes)

thats a problem, download these:
[http://www.box.net/shared/l57vmuog8k](http://www.box.net/shared/l57vmuog8k)
unzip them to /lib/firmware and do:
sudo rm -f /lib/firmware/2.6.24-??-generic/v4l-cx23418*
and then copy the three v4l files in /lib/firmware into each kernel directory and reboot
dmesg should say
[   50.052127] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   50.118132] cx18-0: loaded v4l-cx23418-cpu.fw firmware (174716 bytes)
[   50.661242] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

if so try:
mplayer -cache 16384 /dev/video0

---

### Post by Cresho on 2008-06-06
hey I can help you on this issue.  I own the video card myself and threw it in the garage and Really don't want to install anything.  I have my analog television tuner for cable and my High definition for same pupouse.  I posted 2 tutorials

[http://ubuntuforums.org/showthread.php?t=715165&highlight=tuner](http://ubuntuforums.org/showthread.php?t=715165&highlight=tuner)

[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

what this does is help you determine if

1.  you installed the drivers correctly
2.  installed it into your modules correctly
3.  Installed your video software correctly
4.  are able to view and record correctly.

just follow the tutorial i posted and just replace my steps with the steps you are following.  In other words, it kinda guides you.

install the files needed to get your software running first.  then we will configure your hardware.

we need to fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
--------------------------------------------------------
sudo aptitude remove automake1.4
--------------------------------------------------------

secondly,

--------------------------------------------------------
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev
--------------------------------------------------------

this prepares us to install the software needed.


  the first thing you need to do for me is post..

your terminal messages for the following commands.  Ill try and help.

1.  dmesg
2.  lspci -vnn
3.  ls -l /dev/dvb/adapter0

post the whole thing.  I want to see what is going on.

this will benefit me because I already have a kworld 115 and also a avermedia tv tuner and with the 1600, makes 3 television tuners I can use.

---

### Post by sofasurfer on 2008-06-06
I also have a /lib/firmware/2.6.24-16-generic directtory as well as a /lib/firmware/2.6.24-17-generic directory. Should I put the files into both to be sure?

I think I read that there is a kernel update lately. Whats the command to upgrade to be sure I am up to date?

---

### Post by sofasurfer on 2008-06-06
You guys are great for all your help. But work is interferring with my play. Have to run now. Will try some more after work. Bye.

---

### Post by willoconley on 2008-06-06
don't upgrade just yet, when you do you will have to rebuild the v4l module:
cd ~/v4l*
sudo make clean
sudo make distclean
sudo make unload
sudo make
sudo make install
sudo modprobe cx18

the copy the firmware to the new /lib/firmware/kernelDir

ok I will be around tonight if you want to try and get things sorted out, maybe till like midnight central time.

---

### Post by sofasurfer on 2008-06-06
I'm typing from work right now. I work till 3am Michigan time.
Thanks anyway.

---

### Post by Cresho on 2008-06-07
okay!  I cracked, I pulled out my working television tuners and installed my 1600 card.  expect a tutorial in 3 hours.

---

### Post by Cresho on 2008-06-07
OKAY!  I got it working.  Ill post a full tutorial in 2 days.  The reason being is because it hosed my nvidia x display and reinstalling it will not fix my issue.  But the hauppauge new drivers works.  Video0 is hosed.  It could be related to my old setup.

---

### Post by Cresho on 2008-06-07
at the moment, i just discovered installing the new v4lin-dvb latest drivers hoses systems with extra new nvidia graphics card running the latest nvidia drivers.  I have an 8800gt so I have serious issues.  I am almost done debugging it.  I HOPE!

---

### Post by sofasurfer on 2008-06-07
willoconley.
I just finished following your instruction in post #26.
I'm sure I got the desired results from dmesg.
I connected my cable to the tuner and entered "mplayer -cache 16384 /dev/video0". I have video. When I couldn't find a way to change channels it occured to me, "how am I watching tv on a movie player?". Apparently Mplayer displays tv to? How do I change a channel? I also hooked up to cable from my digital converter box. No video from digital tv signal. No function from my remote either.
Gosh, I hate to be a gloomy gus but am I wanting to use Mplayer? Or is there more configuring to do?

---

### Post by Cresho on 2008-06-07
well, you just need to install...I was using me-tv just fine.  if you follow the other tutorials i posted in this thread, it shows you how to install me-tv, grab channels, and view and record.  I appearantly cannot use this card since i use restricted drivers.  I looked around all ready and there is no solution at the moment.

i was able to record, view high definition channels just fine though.  Its just that i need my 3d graphics and it wont work with the current v4l

---

### Post by willoconley on 2008-06-07
No that is just the quickest way to make sure it is working. although you can change channels with it, i think it is alot of trouble. i use mythtv to change channels so if you want to use it and have any trouble i would do my best to help out. Install the base mythtv package from synaptic and set up the backend using the section "Mythtv Setup" from this guide to get started [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php) . I think the only thing you might need to change on the front end is something I posted elsewhere
> 
MythTV sets the sampling frequency to 32kHz and the bit rate to something higher than the default. One or both of these will stop the audio.

Through the MythTV front end you need to adjust your liveTV and recording profiles. I set them all to 48kHz and a bitrate that translates to 10 (I think it was around 224kb/s).

I found that info from [http://www.gossamer-threads.com/lists/ivtv/devel/38314](http://www.gossamer-threads.com/lists/ivtv/devel/38314).

I don't believe the v4l guys claim to have digital working yet, but cresho said his worked. You shouldn't need a converter box, the other coax input on the card is for digital. I haven't bothered with the remote, you will have to use LIRC to set it up, do a google search: lirc mythtv hauppauge, or hauppauge remote mythtv, and you will get plenty of hits. I just haven't had time to sit down and read through any of it yet, it's not really a priority of mine since I am always sitting right in front of my pc. 

BTW I like your cat.

> at the moment, i just discovered installing the new v4lin-dvb latest drivers hoses systems with extra new nvidia graphics card running the latest nvidia drivers. I have an 8800gt so I have serious issues. I am almost done debugging it. I HOPE!  
Dude it's nothing new, there was a long thread of people who couldn't get it the two to work together at the beginning of the year or so. If you haven't used the nvidia script to install them - if you are using the ones from the repo's just read the link to the debian wiki I posted earlier, it tells you how to rebuild the nvidia module, if you do the two play together just fine.

---

### Post by sofasurfer on 2008-06-07
Ok, don't think I am not greatful for y'alls help cause I am. I am just really wanting to get this thing going. And I will continue with the informatioon provided until I get it right. If I do get it going fully and can repeat the process I intend to do a clean post about the process.

I installed Mythtv a while back but have not gotten past looking at the configuration page and going "yikes!".

The cat (bubba) says "Thanks for the recognition. I'm a little embarrassed to be seen because of my weight. Its nice to hear a kind word".

Cresho. I am not ignoring your posts. Is hard to follow the instructions of one person let alone two. This weekend I will go back through these posts and figure out my next step. This is all very complicated to me. But I AM make progress. Don't you guys desert me. This is helpful to more than just me. As you can see, its one of the most read threads lately.

Well, off to work.

---

### Post by Cresho on 2008-06-07
> **willoconley said:**
> No that is just the quickest way to make sure it is working. although you can change channels with it, i think it is alot of trouble. i use mythtv to change channels so if you want to use it and have any trouble i would do my best to help out. Install the base mythtv package from synaptic and set up the backend using the section "Mythtv Setup" from this guide to get started [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php) . I think the only thing you might need to change on the front end is something I posted elsewhere

I found that info from [http://www.gossamer-threads.com/lists/ivtv/devel/38314](http://www.gossamer-threads.com/lists/ivtv/devel/38314).

I don't believe the v4l guys claim to have digital working yet, but cresho said his worked. You shouldn't need a converter box, the other coax input on the card is for digital. I haven't bothered with the remote, you will have to use LIRC to set it up, do a google search: lirc mythtv hauppauge, or hauppauge remote mythtv, and you will get plenty of hits. I just haven't had time to sit down and read through any of it yet, it's not really a priority of mine since I am always sitting right in front of my pc. 

BTW I like your cat.

  
Dude it's nothing new, there was a long thread of people who couldn't get it the two to work together at the beginning of the year or so. If you haven't used the nvidia script to install them - if you are using the ones from the repo's just read the link to the debian wiki I posted earlier, it tells you how to rebuild the nvidia module, if you do the two play together just fine.

I don't use the repose.  I use the ones from nvidia.  I have the latest one.  I install it under root user in grub recovery.  THis is how I always been doing it.  Even after the kernel update to 18, I had to build it again from scratch.  I reinstalled my operating system at the moment.  And I was curious to see what it took to get the card working.  It works just fine, I can view and record but the drivers and v4l-dvb does not like each other at all.

---

### Post by sofasurfer on 2008-06-08
I downloaded saedelaeres TV-Viewer since he recommended try it as long as my card is working.

I'm having trouble running the script.

I downloaded the viewer to /home/daryl/temporary/tv-viewer075-1.tar.gz

I extracted the file and entered this command in terminal... daryl@ubuntu:~$ sh /home/daryl/temporary/tv-viewer075-1/tv-viewer_install.sh

This was the result...

exec: 3: wish: not found
/tv-viewer_install.sh


How do I run the script?

EDIT::

I found that "wish" is a package that needs installation. Then, on trying to install it I learned that it is part of the package tk8.5. I then installed tk8.5.
Now when I run the script I get this...

daryl@ubuntu:~$ sh /home/daryl/temporary/tv-viewer075-1/tv-viewer_install.sh
Program error. There is a missing dependency.
Please install the package tkimg!

Next I try to install tkimg and I get this...

daryl@ubuntu:~$ sudo apt-get install tkimg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tkimg

EDIT::

I have now downloaded tkimg. I extracted it to /home/daryl/temporary/tkimg1.3

I think the first step now is to cd to /home/daryl/temporary/tkimg1.3. Next I did a "make all" as the readme file says and this is my result... 

daryl@ubuntu:~/temporary/tkimg1.3$ make all
make: *** No rule to make target `all'.  Stop.
 
How do I install tkimg?

EDIT::

Ok, a little progress. 
I did a cd...

cd /home/daryl/temporary/tkimg1.3

Then I did a ./configure
then "make all"
then "make install"

I do not know the next step. At this time TV-Viewer does not work.

What do I do next?

---

### Post by willoconley on 2008-06-08
so did tv-viewer_install.sh run without errors

---

### Post by sofasurfer on 2008-06-08
Please see post #40. I require to instal "tkimg" and I am stuck on that.

---

### Post by willoconley on 2008-06-08
if make install ran without errors then tkimg should be installed i believe.

---

### Post by sofasurfer on 2008-06-08
Can I run "make all" and "make install" again? If so I will give you the result.

---

### Post by willoconley on 2008-06-08
do: make distclean
and then start over

---

### Post by sofasurfer on 2008-06-08
daryl@ubuntu:~$ cd /home/daryl/temporary/tv-viewer075-1
daryl@ubuntu:~/temporary/tv-viewer075-1$ make distclean
make: *** No rule to make target `distclean'.  Stop.

I don't know what is wrong or if I am just so tired that I am doing something wrong and not seeing it. I think I am in the correct directory.

---

### Post by willoconley on 2008-06-08
i guess make clean would say the same thing.

"I do not know the next step. At this time TV-Viewer does not work." - did you mean the tvviewer_install.sh still gives errors, if you havn't tried it i would, see if it still complains about tkimg. If it does do make install from the tkimg directory again and post what it says.

---

### Post by sofasurfer on 2008-06-09
daryl@ubuntu:~$ sh /home/daryl/temporary/tv-viewer075-1/tv-viewer_install.sh
Program error. There is a missing dependency.
Please install the package tkimg!

Have a closer look to the user guide for the system requirements.




daryl@ubuntu:~/temporary/tkimg1.3$ make install
make: *** No rule to make target `install'.  Stop.
daryl@ubuntu:~/temporary/tkimg1.3$


This "No rule to..." pops up for everything

---

### Post by saedelaere on 2008-06-09
Hi,

if you want to install tkimg you can use synaptics.
Unfortunately I didn't upload the newest version of the user guide to my homepage. Don't know how I could forget this. I made up leeway.
[Here]("http://home.arcor.de/saedelaere/doc/TV-Viewer_0.7_help_file_eng.html#Specific_informations_for_different_") is the link to the section in the user guide where it is described what packages you need for Ubuntu.
The name for the package you need is libtk-img. Be sure you've also installed the packages tcl and tk.

I'am not so sure if version 0.7.5-2 will work for you if you don't have a VBI device node.
Please post here if it doesn't then I will release a new version.

Regards
Saedelaere

---

### Post by sofasurfer on 2008-06-09
Success.
Installing ivtv-utils did it. Tv-Viewer installed into /home/daryl/tv-viewer.
The wizard shows these results:

video player(mplayer)     OK
video device(dev/video0)  Failed
video stardard(NTSC-M)    Failed
tool v412-ctl             Failed
tool ivtv-time            OK
tool scantv               Failed
temporal filter(0)        Failed
increase videobitrate     Not Chosen
activate osd              Failed
font (dejavu sans mono)   OK

Not sure which video standard I require but I do have that info somewhere if you don't know it right off the top of your head. 

I think that there is no support for ATSC from what I see. Is that correct?

EDIT::

I just restarted tv-viewer and this is the message results:

daryl@ubuntu:~$ tv-viewer

-------------------------------

TV-Viewer is starting

Choosen Language English

No configuration file...
Starting Configuration-Wizard

-------------------------------

Configuration-Wizard is starting

No configuration file
Using standard values


daryl@ubuntu:~$ 
Amixer found
Reading audio channels

Initializing main window

Kaffeine failed 
Error message: sh: kaffeine: not found
cat: /dev/video0: No such file or directory

Device node /dev/video0 failed the test

v4l2-ctl failed the test
Error message: Failed to open /dev/video0: No such file or directory

ivtv-tune successfully tested

osd_cat failed the test
Error message: couldn't execute "osd_cat": no such file or directory

Dejavu sans mono is installed on this system

v4l2-ctl can't change videostandard to 0x000000000000000F ok
Error message: Failed to open /dev/video0: No such file or directory

scantv not installed on this system

Selected video-player OK
cat: /dev/video0: No such file or directory

v4l2-ctl failed the test
Error message: Failed to open /dev/video0: No such file or directory

ivtv-tune successfully tested

osd_cat failed the test
Error message: couldn't execute "osd_cat": no such file or directory

Dejavu sans mono is installed on this system

v4l2-ctl can't change videostandard to 0x000000000000000F ok
Error message: Failed to open /dev/video0: No such file or directory

scantv not installed on this system


I changed the player option to MPLAYER and installed scantv.

I'll go try it out now

---

### Post by saedelaere on 2008-06-09
First of all you'll have to define the correct video device node.

Is /dev/video0 the correct one? 
You can test it with 
```

cat /dev/video0 > test.mpeg

```

The file test.mpeg will be created in your users home directory.

Then the next thing if you found the correct video device node. You should test the tool v4l2-ctl.

```

v4l2-ctl -d /dev/video_device_node --all

```

If the second command works please post the output here.

Regards
Saedelaere

---

### Post by sofasurfer on 2008-06-09
daryl@ubuntu:~$ cat /dev/video0 > test.mpeg
cat: /dev/video0: No such file or directory

Clicking on the created file "test.mpeg" simply opens the mplayer.


daryl@ubuntu:~$ v4l2-ctl -d /dev/video_device_node --all
Failed to open /dev/video_device_node: No such file or directory

---

### Post by saedelaere on 2008-06-09
Hmm is your TV-Card working properly or in other words are the drivers installed and the card is recognized?

What is the output of

```

dmesg | grep ivtv

```

---

### Post by sofasurfer on 2008-06-09
dmesg | grep ivtv

No output at all. The card did play a couple days ago when I followed willoconleys instructions.

I went back to post #35 and see that at that time mplayer worked. The same command "mplayer -cache 16384 /dev/video0" now produces this...

daryl@ubuntu:~$ mplayer -cache 16384 /dev/video0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
File not found: '/dev/video0'
Failed to open /dev/video0.


Exiting... (End of file)

So somewhere between post #35 and now I did something wrong in trying to install some files. I think the main problem I had was with tkimg which I downloaded but was only able to partially complete the install process.

I am going to the store for about an hour now but will be back.

---

### Post by saedelaere on 2008-06-09
I don't think the installation of tkimg could corrupt your working tv-card.
Did you install it via synaptics now?

You should try:

```

modprobe ivtv

```

and then show us the output of dmesg.

---

### Post by sofasurfer on 2008-06-09
The successful installation of tkimg may not cause a problem but unsuccessful partial installation may have done something.

I followed your link in post #49 and successfully installed ivtv-utils.

Heres modprobe ivtv output...

daryl@ubuntu:~$ modprobe ivtv
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting tveeprom (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/tveeprom.ko): Operation not permitted
WARNING: Error inserting cx2341x (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/cx2341x.ko): Operation not permitted
WARNING: Error inserting i2c_algo_bit (/lib/modules/2.6.24-18-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko): Operation not permitted
FATAL: Error inserting ivtv (/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/ivtv/ivtv.ko): Operation not permitted


And dmesg...

```

[    0.000000] ACPI: MCFG 3FFF79C0, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 3FFF7680, 0098 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262128
[    0.000000] On node 0 totalpages: 262031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257229
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=ea29642e-720e-4685-b90c-e03ed2e2c87f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   20.142915] Marking TSC unstable due to TSCs unsynchronized
[   20.142917] time.c: Detected 2210.051 MHz processor.
[   20.145233] Console: colour VGA+ 80x25
[   20.145235] console [tty0] enabled
[   20.145251] Checking aperture...
[   20.145253] CPU 0: aperture @ fbac000000 size 32 MB
[   20.145254] Aperture too small (32 MB)
[   20.151144] No AGP bridge found
[   20.162029] Memory: 1021160k/1048512k available (2488k kernel code, 26964k reserved, 1319k data, 320k init)
[   20.162065] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   20.240831] Calibrating delay using timer specific routine.. 4424.34 BogoMIPS (lpj=8848688)
[   20.240862] Security Framework initialized
[   20.240869] SELinux:  Disabled at boot.
[   20.240882] AppArmor: AppArmor initialized
[   20.240885] Failure registering capabilities with primary security module.
[   20.240971] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.241692] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.242037] Mount-cache hash table entries: 256
[   20.242165] Initializing cgroup subsys ns
[   20.242168] Initializing cgroup subsys cpuacct
[   20.242180] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.242181] CPU: L2 Cache: 512K (64 bytes/line)
[   20.242184] CPU 0/0 -> Node 0
[   20.242186] CPU: Physical Processor ID: 0
[   20.242187] CPU: Processor Core ID: 0
[   20.242210] SMP alternatives: switching to UP code
[   20.242772] Early unpacking initramfs... done
[   20.521800] ACPI: Core revision 20070126
[   20.521844] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.565630] Using local APIC timer interrupts.
[   20.610849] APIC timer calibration result 12557108
[   20.610850] Detected 12.557 MHz APIC timer.
[   20.610939] SMP alternatives: switching to SMP code
[   20.611403] Booting processor 1/2 APIC 0x1
[   20.622021] Initializing CPU#1
[   20.699350] Calibrating delay using timer specific routine.. 4420.12 BogoMIPS (lpj=8840252)
[   20.699355] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.699357] CPU: L2 Cache: 512K (64 bytes/line)
[   20.699359] CPU 1/1 -> Node 0
[   20.699361] CPU: Physical Processor ID: 0
[   20.699362] CPU: Processor Core ID: 1
[   20.699435] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   20.698958] Brought up 2 CPUs
[   20.699050] CPU0 attaching sched-domain:
[   20.699052]  domain 0: span 03
[   20.699054]   groups: 01 02
[   20.699056]   domain 1: span 03
[   20.699057]    groups: 03
[   20.699059] CPU1 attaching sched-domain:
[   20.699061]  domain 0: span 03
[   20.699062]   groups: 02 01
[   20.699064]   domain 1: span 03
[   20.699065]    groups: 03
[   20.699277] net_namespace: 120 bytes
[   20.699654] Time: 21:17:24  Date: 06/09/08
[   20.699688] NET: Registered protocol family 16
[   20.699859] ACPI: bus type pci registered
[   20.699923] PCI: Using configuration type 1
[   20.701002] ACPI: EC: Look up EC in DSDT
[   20.706172] ACPI: Interpreter enabled
[   20.706175] ACPI: (supports S0 S1 S4 S5)
[   20.706187] ACPI: Using IOAPIC for interrupt routing
[   20.713953] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.714489] PCI: Transparent bridge - 0000:00:04.0
[   20.714586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.714792] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   20.741459] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   20.741594] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.741729] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.741861] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.741993] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742126] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742258] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742390] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742522] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742654] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.742796] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   20.742930] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   20.743064] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   20.743196] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.743329] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   20.743462] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   20.743594] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.743728] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   20.743860] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.744026] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   20.744184] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   20.744343] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   20.744500] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   20.744659] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   20.744816] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   20.744975] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   20.745133] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   20.745296] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   20.745454] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   20.745611] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   20.745768] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   20.745927] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   20.746085] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   20.746242] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   20.746401] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   20.746560] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   20.746718] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   20.746879] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   20.746994] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.747018] pnp: PnP ACPI init
[   20.747025] ACPI: bus type pnp registered
[   20.751123] pnp: PnP ACPI: found 16 devices
[   20.751125] ACPI: ACPI bus type pnp unregistered
[   20.751329] PCI: Using ACPI for IRQ routing
[   20.751333] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.762790] NET: Registered protocol family 8
[   20.762791] NET: Registered protocol family 20
[   20.762862] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   20.762865] hpet0: 3 32-bit timers, 25000000 Hz
[   20.763912] AppArmor: AppArmor Filesystem Enabled
[   20.766743] Time: hpet clocksource has been installed.
[   20.766754] Switched to high resolution mode on CPU 0
[   20.767409] Switched to high resolution mode on CPU 1
[   20.774738] system 00:01: ioport range 0x1000-0x107f has been reserved
[   20.774742] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   20.774744] system 00:01: ioport range 0x1400-0x147f has been reserved
[   20.774747] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   20.774750] system 00:01: ioport range 0x1800-0x187f has been reserved
[   20.774752] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   20.774756] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   20.774759] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   20.774762] system 00:01: iomem range 0x0-0x0 could not be reserved
[   20.774767] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   20.774769] system 00:02: ioport range 0x800-0x87f has been reserved
[   20.774772] system 00:02: ioport range 0x295-0x314 has been reserved
[   20.774774] system 00:02: ioport range 0x290-0x294 has been reserved
[   20.774785] system 00:0e: iomem range 0xe0000000-0xe7ffffff could not be reserved
[   20.774791] system 00:0f: iomem range 0xce200-0xcffff has been reserved
[   20.774794] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   20.774797] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   20.774800] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   20.774802] system 00:0f: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   20.774805] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[   20.774808] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   20.774811] system 00:0f: iomem range 0x100000-0x3ffeffff could not be reserved
[   20.774814] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   20.774816] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved
[   20.774819] system 00:0f: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.775160] PCI: Bridge: 0000:00:04.0
[   20.775161]   IO window: disabled.
[   20.775164]   MEM window: e8000000-ebffffff
[   20.775166]   PREFETCH window: disabled.
[   20.775171] PCI: Bridge: 0000:00:09.0
[   20.775172]   IO window: disabled.
[   20.775174]   MEM window: ec000000-eeffffff
[   20.775176]   PREFETCH window: d0000000-dfffffff
[   20.775184] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.775194] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   20.775204] NET: Registered protocol family 2
[   20.810765] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   20.811206] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   20.812697] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   20.813397] TCP: Hash tables configured (established 131072 bind 65536)
[   20.813400] TCP reno registered
[   20.822829] checking if image is initramfs... it is
[   21.367176] Freeing initrd memory: 7503k freed
[   21.373046] audit: initializing netlink socket (disabled)
[   21.373058] audit(1213046244.192:1): initialized
[   21.374790] VFS: Disk quotas dquot_6.5.1
[   21.374853] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.374978] io scheduler noop registered
[   21.374980] io scheduler anticipatory registered
[   21.374981] io scheduler deadline registered
[   21.375066] io scheduler cfq registered (default)
[   21.375642] Boot video device is 0000:02:00.0
[   21.375784] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.375802] assign_interrupt_mode Found MSI capability
[   21.375819] Allocate Port Service[0000:00:09.0:pcie00]
[   21.399654] Real Time Clock Driver v1.12ac
[   21.399827] hpet_resources: 0xfeff0000 is busy
[   21.399861] Linux agpgart interface v0.102
[   21.399863] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.399979] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.400099] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.400554] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.400787] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.401422] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.401479] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.401560] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.401915] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.401919] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.410513] mice: PS/2 mouse device common for all mice
[   21.410549] cpuidle: using governor ladder
[   21.410551] cpuidle: using governor menu
[   21.410697] NET: Registered protocol family 1
[   21.410791] registered taskstats version 1
[   21.410892]   Magic number: 12:622:297
[   21.410920]   hash matches device ttywe
[   21.411024] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.411028] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.411029] EDD information not available.
[   21.411037] Freeing unused kernel memory: 320k freed
[   21.450795] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.585352] fuse init (API version 7.9)
[   22.600010] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.600022] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.002140] usbcore: registered new interface driver usbfs
[   23.002161] usbcore: registered new interface driver hub
[   23.002182] usbcore: registered new device driver usb
[   23.006502] SCSI subsystem initialized
[   23.043063] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   23.043071] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   23.043240] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   23.043246] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   23.043459] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   23.043488] ehci_hcd 0000:00:02.1: debug port 1
[   23.043491] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   23.043501] ehci_hcd 0000:00:02.1: irq 23, io mem 0xef007000
[   23.044466] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.046628] libata version 3.00 loaded.
[   23.052995] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.053114] usb usb1: configuration #1 chosen from 1 choice
[   23.053132] hub 1-0:1.0: USB hub found
[   23.053138] hub 1-0:1.0: 8 ports detected
[   23.082918] Floppy drive(s): fd0 is 1.44M
[   23.100848] FDC 0 is a post-1991 82077
[   23.157872] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   23.157881] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   23.158082] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.158088] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   23.158142] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   23.158161] ohci_hcd 0000:00:02.0: irq 22, io mem 0xef006000
[   23.216000] usb usb2: configuration #1 chosen from 1 choice
[   23.216022] hub 2-0:1.0: USB hub found
[   23.216030] hub 2-0:1.0: 8 ports detected
[   23.317454] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.317780] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   23.317788] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   23.317802] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   23.317808] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   23.318404] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   23.318730] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   23.318738] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[   23.318743] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   23.397816] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   23.715558] usb 1-3: configuration #1 chosen from 1 choice
[   23.837336] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1d:7d:2b:a1:df
[   23.837341] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   23.839360] pata_amd 0000:00:06.0: version 0.3.10
[   23.839415] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.842134] scsi0 : pata_amd
[   23.842249] scsi1 : pata_amd
[   23.842734] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   23.842736] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   24.048453] ata1.01: HPA unlocked: 320170943 -> 320173056, native 320173056
[   24.048458] ata1.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   24.048460] ata1.01: 320173056 sectors, multi 16: LBA48 
[   24.048469] ata1.01: limited to UDMA/33 due to 40-wire cable
[   24.065117] ata1.01: configured for UDMA/33
[   24.064596] ata2: port disabled. ignoring.
[   24.064707] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[   24.067028] sata_nv 0000:00:08.0: version 3.5
[   24.067041] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   24.067240] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.067428] scsi2 : sata_nv
[   24.067473] scsi3 : sata_nv
[   24.067613] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 21
[   24.067616] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 21
[   24.531827] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.711776] ata3.00: ATAPI: PHILIPS SPD2513P, MP03, max UDMA/100
[   24.899632] ata3.00: configured for UDMA/100
[   25.367166] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   25.396285] ata4.00: HPA unlocked: 490232639 -> 490234752, native 490234752
[   25.396291] ata4.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[   25.396294] ata4.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.412818] ata4.00: configured for UDMA/133
[   25.413935] scsi 2:0:0:0: CD-ROM            PHILIPS  SPD2513P         MP03 PQ: 0 ANSI: 5
[   25.414344] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[   25.422404] Driver 'sd' needs updating - please use bus_type methods
[   25.423263] sd 0:0:1:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   25.423274] sd 0:0:1:0: [sda] Write Protect is off
[   25.423277] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   25.423290] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.423336] sd 0:0:1:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   25.423343] sd 0:0:1:0: [sda] Write Protect is off
[   25.423345] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   25.423357] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.423361]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.445695]  sda1
[   25.445759] sd 0:0:1:0: [sda] Attached SCSI disk
[   25.445839] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   25.445850] sd 3:0:0:0: [sdb] Write Protect is off
[   25.445852] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.445866] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.445916] sd 3:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   25.445924] sd 3:0:0:0: [sdb] Write Protect is off
[   25.445926] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.445938] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.445942]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.453382] Uniform CD-ROM driver Revision: 3.20
[   25.453432] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   25.454330]  sdb1 sdb2 < sdb5 > sdb3
[   25.479868] sd 3:0:0:0: [sdb] Attached SCSI disk
[   25.485213] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   25.485233] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   25.485249] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   30.815935] kjournald starting.  Commit interval 5 seconds
[   30.815948] EXT3-fs: mounted filesystem with ordered data mode.
[   38.275083] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   38.354574] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.383376] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.457738] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   38.457759] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc800
[   38.486186] logips2pp: Detected unknown logitech mouse model 127
[   38.653025] input: Power Button (FF) as /devices/virtual/input/input3
[   38.684835] ACPI: Power Button (FF) [PWRF]
[   38.684914] input: Power Button (CM) as /devices/virtual/input/input4
[   38.716779] ACPI: Power Button (CM) [PWRB]
[   38.846384] nvidia: module license 'NVIDIA' taints kernel.
[   39.203215] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   39.272052] parport_pc 00:0b: reported by Plug and Play ACPI
[   39.272096] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.791188] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   39.791197] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 16
[   39.791204] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   39.793578] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   39.794443] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   39.794448] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   39.794629] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   40.771228] phy0: Selected rate control algorithm 'simple'
[   40.819255] usbcore: registered new interface driver rt73usb
[   42.534107] loop: module loaded
[   42.543657] lp0: using parport0 (interrupt-driven).
[   42.937595] EXT3 FS on sdb1, internal journal
[   43.726334] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.156647] No dock devices found.
[   44.414832] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   44.414232] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[   44.414235] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[   44.414237] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   44.414239] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   47.115222] ppdev: user-space parallel port driver
[   47.278586] audit(1213046270.798:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5470 profile="/usr/sbin/cupsd" namespace="default"
[   47.605286] NET: Registered protocol family 10
[   47.605559] lo: Disabled Privacy Extensions
[   48.864911] eth0: no link during initialization.
[   48.865862] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.884311] Clocksource tsc unstable (delta = -272709600 ns)
[   48.932024] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.048948] Bluetooth: Core ver 2.11
[   50.049307] NET: Registered protocol family 31
[   50.049311] Bluetooth: HCI device and connection manager initialized
[   50.049315] Bluetooth: HCI socket layer initialized
[   50.078299] Bluetooth: L2CAP ver 2.9
[   50.078304] Bluetooth: L2CAP socket layer initialized
[   50.100035] Bluetooth: RFCOMM socket layer initialized
[   50.100054] Bluetooth: RFCOMM TTY layer initialized
[   50.100056] Bluetooth: RFCOMM ver 1.8
[   55.301452] NET: Registered protocol family 17
[   55.729903] wlan0: Initial auth_alg=0
[   55.729909] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   55.730651] wlan0: RX authentication from 00:17:3f:f1:1a:2c (alg=0 transaction=2 status=0)
[   55.730656] wlan0: authenticated
[   55.730658] wlan0: associate with AP 00:17:3f:f1:1a:2c
[   55.731726] wlan0: RX AssocResp from 00:17:3f:f1:1a:2c (capab=0x431 status=0 aid=1)
[   55.731730] wlan0: associated
[   55.731733] wlan0: switched to short barker preamble (BSSID=00:17:3f:f1:1a:2c)
[   55.733035] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.689378] wlan0: no IPv6 routers present 
```
daryl@ubuntu:~$

---

### Post by saedelaere on 2008-06-09
Sorry but modprobe has to be executed as root!

sudo modprobe ivtv

and then dmesg

---

### Post by sofasurfer on 2008-06-09
No output from modprobe...

daryl@ubuntu:~$ sudo modprobe ivtv
daryl@ubuntu:~$ 

I think dmesg is the same as before. Do you still want me to post that big list?

---

### Post by saedelaere on 2008-06-09
The modprobe command has normaly no direct output. You can see the results via dmesg.
So please post the results of dmesg again :)

Bye

---

### Post by sofasurfer on 2008-06-10
I feel guilty clogging up the forum with all this stuff :-) But here it is...

```

[    0.000000]     0:      256 ->   262128
[    0.000000] On node 0 totalpages: 262031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257229
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=ea29642e-720e-4685-b90c-e03ed2e2c87f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   32.500613] Marking TSC unstable due to TSCs unsynchronized
[   32.500615] time.c: Detected 2210.050 MHz processor.
[   32.502941] Console: colour VGA+ 80x25
[   32.502944] console [tty0] enabled
[   32.502960] Checking aperture...
[   32.502962] CPU 0: aperture @ fbac000000 size 32 MB
[   32.502963] Aperture too small (32 MB)
[   32.508852] No AGP bridge found
[   32.519735] Memory: 1021160k/1048512k available (2488k kernel code, 26964k reserved, 1319k data, 320k init)
[   32.519771] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   32.598528] Calibrating delay using timer specific routine.. 4424.35 BogoMIPS (lpj=8848706)
[   32.598558] Security Framework initialized
[   32.598565] SELinux:  Disabled at boot.
[   32.598578] AppArmor: AppArmor initialized
[   32.598581] Failure registering capabilities with primary security module.
[   32.598667] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.599388] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   32.599733] Mount-cache hash table entries: 256
[   32.599861] Initializing cgroup subsys ns
[   32.599864] Initializing cgroup subsys cpuacct
[   32.599876] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.599878] CPU: L2 Cache: 512K (64 bytes/line)
[   32.599880] CPU 0/0 -> Node 0
[   32.599882] CPU: Physical Processor ID: 0
[   32.599883] CPU: Processor Core ID: 0
[   32.599907] SMP alternatives: switching to UP code
[   32.600468] Early unpacking initramfs... done
[   32.879496] ACPI: Core revision 20070126
[   32.879540] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.923330] Using local APIC timer interrupts.
[   32.968548] APIC timer calibration result 12557105
[   32.968550] Detected 12.557 MHz APIC timer.
[   32.968638] SMP alternatives: switching to SMP code
[   32.969103] Booting processor 1/2 APIC 0x1
[   32.979865] Initializing CPU#1
[   33.057193] Calibrating delay using timer specific routine.. 4420.12 BogoMIPS (lpj=8840253)
[   33.057199] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   33.057200] CPU: L2 Cache: 512K (64 bytes/line)
[   33.057202] CPU 1/1 -> Node 0
[   33.057204] CPU: Physical Processor ID: 0
[   33.057205] CPU: Processor Core ID: 1
[   33.057278] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   33.056658] Brought up 2 CPUs
[   33.056750] CPU0 attaching sched-domain:
[   33.056752]  domain 0: span 03
[   33.056754]   groups: 01 02
[   33.056756]   domain 1: span 03
[   33.056757]    groups: 03
[   33.056759] CPU1 attaching sched-domain:
[   33.056760]  domain 0: span 03
[   33.056761]   groups: 02 01
[   33.056764]   domain 1: span 03
[   33.056765]    groups: 03
[   33.056976] net_namespace: 120 bytes
[   33.057354] Time: 23:59:19  Date: 06/09/08
[   33.057388] NET: Registered protocol family 16
[   33.057559] ACPI: bus type pci registered
[   33.057623] PCI: Using configuration type 1
[   33.058701] ACPI: EC: Look up EC in DSDT
[   33.063871] ACPI: Interpreter enabled
[   33.063873] ACPI: (supports S0 S1 S4 S5)
[   33.063885] ACPI: Using IOAPIC for interrupt routing
[   33.071654] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.072190] PCI: Transparent bridge - 0000:00:04.0
[   33.072286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.072491] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   33.099164] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   33.099298] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.099433] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.099565] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.099698] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.099830] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.099962] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.100094] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.100226] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.100359] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.100500] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   33.100634] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   33.100768] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   33.100900] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.101033] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   33.101166] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   33.101298] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.101432] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   33.101564] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   33.101730] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   33.101888] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   33.102047] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   33.102205] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   33.102363] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   33.102521] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   33.102679] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   33.102837] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   33.102999] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   33.103157] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   33.103314] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   33.103472] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   33.103630] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   33.103788] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   33.103946] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   33.104104] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   33.104263] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   33.104422] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   33.104583] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   33.104698] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.104722] pnp: PnP ACPI init
[   33.104729] ACPI: bus type pnp registered
[   33.108827] pnp: PnP ACPI: found 16 devices
[   33.108830] ACPI: ACPI bus type pnp unregistered
[   33.109036] PCI: Using ACPI for IRQ routing
[   33.109040] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.120490] NET: Registered protocol family 8
[   33.120491] NET: Registered protocol family 20
[   33.120561] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   33.120564] hpet0: 3 32-bit timers, 25000000 Hz
[   33.121611] AppArmor: AppArmor Filesystem Enabled
[   33.124443] Time: hpet clocksource has been installed.
[   33.124453] Switched to high resolution mode on CPU 0
[   33.125253] Switched to high resolution mode on CPU 1
[   33.132437] system 00:01: ioport range 0x1000-0x107f has been reserved
[   33.132441] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   33.132444] system 00:01: ioport range 0x1400-0x147f has been reserved
[   33.132446] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   33.132449] system 00:01: ioport range 0x1800-0x187f has been reserved
[   33.132451] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   33.132455] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   33.132458] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   33.132461] system 00:01: iomem range 0x0-0x0 could not be reserved
[   33.132466] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   33.132469] system 00:02: ioport range 0x800-0x87f has been reserved
[   33.132471] system 00:02: ioport range 0x295-0x314 has been reserved
[   33.132474] system 00:02: ioport range 0x290-0x294 has been reserved
[   33.132485] system 00:0e: iomem range 0xe0000000-0xe7ffffff could not be reserved
[   33.132491] system 00:0f: iomem range 0xce200-0xcffff has been reserved
[   33.132494] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   33.132496] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   33.132499] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   33.132502] system 00:0f: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   33.132505] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[   33.132508] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   33.132510] system 00:0f: iomem range 0x100000-0x3ffeffff could not be reserved
[   33.132513] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   33.132516] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved
[   33.132518] system 00:0f: iomem range 0xfee00000-0xfee00fff could not be reserved
[   33.132860] PCI: Bridge: 0000:00:04.0
[   33.132861]   IO window: disabled.
[   33.132864]   MEM window: e8000000-ebffffff
[   33.132866]   PREFETCH window: disabled.
[   33.132871] PCI: Bridge: 0000:00:09.0
[   33.132871]   IO window: disabled.
[   33.132873]   MEM window: ec000000-eeffffff
[   33.132875]   PREFETCH window: d0000000-dfffffff
[   33.132884] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   33.132894] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   33.132903] NET: Registered protocol family 2
[   33.168465] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   33.168905] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   33.170395] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   33.171096] TCP: Hash tables configured (established 131072 bind 65536)
[   33.171099] TCP reno registered
[   33.180532] checking if image is initramfs... it is
[   33.724899] Freeing initrd memory: 7503k freed
[   33.730757] audit: initializing netlink socket (disabled)
[   33.730769] audit(1213055959.192:1): initialized
[   33.732503] VFS: Disk quotas dquot_6.5.1
[   33.732566] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   33.732690] io scheduler noop registered
[   33.732691] io scheduler anticipatory registered
[   33.732693] io scheduler deadline registered
[   33.732778] io scheduler cfq registered (default)
[   33.733355] Boot video device is 0000:02:00.0
[   33.733497] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   33.733515] assign_interrupt_mode Found MSI capability
[   33.733532] Allocate Port Service[0000:00:09.0:pcie00]
[   33.757368] Real Time Clock Driver v1.12ac
[   33.757542] hpet_resources: 0xfeff0000 is busy
[   33.757575] Linux agpgart interface v0.102
[   33.757577] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.757693] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.757813] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.758263] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.758498] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.759142] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.759200] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.759282] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.759638] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.759642] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.768213] mice: PS/2 mouse device common for all mice
[   33.768249] cpuidle: using governor ladder
[   33.768251] cpuidle: using governor menu
[   33.768399] NET: Registered protocol family 1
[   33.768492] registered taskstats version 1
[   33.768593]   Magic number: 12:558:1009
[   33.768723] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   33.768726] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.768727] EDD information not available.
[   33.768735] Freeing unused kernel memory: 320k freed
[   33.808639] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.940109] fuse init (API version 7.9)
[   34.955874] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   34.955885] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.320181] usbcore: registered new interface driver usbfs
[   35.320200] usbcore: registered new interface driver hub
[   35.320225] usbcore: registered new device driver usb
[   35.321020] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   35.321335] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   35.321343] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   35.321516] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.321523] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   35.321762] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   35.321779] ohci_hcd 0000:00:02.0: irq 23, io mem 0xef006000
[   35.374437] SCSI subsystem initialized
[   35.376808] usb usb1: configuration #1 chosen from 1 choice
[   35.376830] hub 1-0:1.0: USB hub found
[   35.376841] hub 1-0:1.0: 8 ports detected
[   35.387109] libata version 3.00 loaded.
[   35.453055] Floppy drive(s): fd0 is 1.44M
[   35.474023] FDC 0 is a post-1991 82077
[   35.479443] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   35.479750] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   35.479758] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 22
[   35.479763] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   35.782358] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   35.999841] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1d:7d:2b:a1:df
[   35.999847] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   36.000283] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[   36.000290] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 21
[   36.000474] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   36.000479] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   36.000552] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   36.000582] ehci_hcd 0000:00:02.1: debug port 1
[   36.000586] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   36.000595] ehci_hcd 0000:00:02.1: irq 21, io mem 0xef007000
[   36.007966] usb 1-3: device descriptor read/all, error -62
[   36.011416] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.011503] usb usb2: configuration #1 chosen from 1 choice
[   36.011524] hub 2-0:1.0: USB hub found
[   36.011528] hub 2-0:1.0: 8 ports detected
[   36.115593] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   36.115913] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   36.115920] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   36.115948] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   36.115954] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   36.119407] sata_nv 0000:00:08.0: version 3.5
[   36.119423] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   36.119697] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   36.136945] scsi0 : sata_nv
[   36.139503] scsi1 : sata_nv
[   36.139668] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[   36.139671] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[   36.434578] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   36.606954] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   36.752417] usb 2-3: configuration #1 chosen from 1 choice
[   36.786922] ata1.00: ATAPI: PHILIPS SPD2513P, MP03, max UDMA/100
[   36.974276] ata1.00: configured for UDMA/100
[   37.441085] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   37.463228] ata2.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[   37.463232] ata2.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.470058] ata2.00: configured for UDMA/133
[   37.781523] scsi 0:0:0:0: CD-ROM            PHILIPS  SPD2513P         MP03 PQ: 0 ANSI: 5
[   37.781652] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[   37.781352] pata_amd 0000:00:06.0: version 0.3.10
[   37.781399] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   37.781457] scsi2 : pata_amd
[   37.781618] scsi3 : pata_amd
[   37.782088] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   37.782090] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   37.993630] ata3.01: HPA unlocked: 320170943 -> 320173056, native 320173056
[   37.993635] ata3.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   37.993638] ata3.01: 320173056 sectors, multi 16: LBA48 
[   37.993648] ata3.01: limited to UDMA/33 due to 40-wire cable
[   38.010228] ata3.01: configured for UDMA/33
[   38.009535] ata4: port disabled. ignoring.
[   38.009652] scsi 2:0:1:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[   38.021752] Driver 'sd' needs updating - please use bus_type methods
[   38.022995] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   38.023006] sd 1:0:0:0: [sda] Write Protect is off
[   38.023008] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.023021] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.023074] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   38.023081] sd 1:0:0:0: [sda] Write Protect is off
[   38.023083] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.023095] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.023098]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   38.028665]  sda1 sda2 < sda5 sda6 >
[   38.062528] sd 1:0:0:0: [sda] Attached SCSI disk
[   38.062570] sd 2:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[   38.062579] sd 2:0:1:0: [sdb] Write Protect is off
[   38.062581] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   38.062594] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.062623] sd 2:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[   38.062631] sd 2:0:1:0: [sdb] Write Protect is off
[   38.062633] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   38.062651] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.062654]  sdb: sdb1
[   38.085049] sd 2:0:1:0: [sdb] Attached SCSI disk
[   38.088507] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   38.088530] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.088545] sd 2:0:1:0: Attached scsi generic sg2 type 0
[   38.335850] Attempting manual resume
[   38.335854] swsusp: Resume From Partition 8:5
[   38.335855] PM: Checking swsusp image.
[   38.336023] PM: Resume from disk failed.
[   38.344654] EXT3-fs: INFO: recovery required on readonly filesystem.
[   38.344658] EXT3-fs: write access will be enabled during recovery.
[   39.101442] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   39.101447] Uniform CD-ROM driver Revision: 3.20
[   39.101501] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   39.597246] kjournald starting.  Commit interval 5 seconds
[   39.597994] EXT3-fs: sda1: orphan cleanup on readonly fs
[   39.598002] ext3_orphan_cleanup: deleting unreferenced inode 770385
[   39.598029] ext3_orphan_cleanup: deleting unreferenced inode 770259
[   39.598037] ext3_orphan_cleanup: deleting unreferenced inode 180233
[   39.598044] ext3_orphan_cleanup: deleting unreferenced inode 180230
[   39.598049] ext3_orphan_cleanup: deleting unreferenced inode 180228
[   39.598055] ext3_orphan_cleanup: deleting unreferenced inode 180227
[   39.598060] ext3_orphan_cleanup: deleting unreferenced inode 180226
[   39.598065] EXT3-fs: sda1: 7 orphan inodes deleted
[   39.598066] EXT3-fs: recovery complete.
[   39.613909] EXT3-fs: mounted filesystem with ordered data mode.
[   47.662986] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   47.890087] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.910871] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.913535] logips2pp: Detected unknown logitech mouse model 127
[   47.998385] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   47.998402] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc800
[   48.019451] input: Power Button (FF) as /devices/virtual/input/input3
[   48.072885] ACPI: Power Button (FF) [PWRF]
[   48.072947] input: Power Button (CM) as /devices/virtual/input/input4
[   48.136843] ACPI: Power Button (CM) [PWRB]
[   48.379831] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   48.436347] parport_pc 00:0b: reported by Plug and Play ACPI
[   48.436391] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   48.764742] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   48.764746] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   48.764910] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   49.136731] nvidia: module license 'NVIDIA' taints kernel.
[   49.396118] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   49.396127] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 16
[   49.396134] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   49.396319] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   49.760904] phy0: Selected rate control algorithm 'simple'
[   49.804424] usbcore: registered new interface driver rt73usb
[   50.898029] loop: module loaded
[   50.905959] lp0: using parport0 (interrupt-driven).
[   50.990781] Unable to find swap-space signature
[   51.540764] EXT3 FS on sda1, internal journal
[   52.205900] Unable to find swap-space signature
[   52.671938] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.053032] No dock devices found.
[   53.318889] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   53.318070] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[   53.318074] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[   53.318076] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   53.318078] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   55.902671] ppdev: user-space parallel port driver
[   56.074661] audit(1213055982.237:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5315 profile="/usr/sbin/cupsd" namespace="default"
[   56.367760] NET: Registered protocol family 10
[   56.368017] lo: Disabled Privacy Extensions
[   57.423025] Clocksource tsc unstable (delta = -90874434 ns)
[   57.602330] eth0: no link during initialization.
[   57.603396] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.713083] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.924750] Bluetooth: Core ver 2.11
[   58.924833] NET: Registered protocol family 31
[   58.924835] Bluetooth: HCI device and connection manager initialized
[   58.924839] Bluetooth: HCI socket layer initialized
[   58.947702] Bluetooth: L2CAP ver 2.9
[   58.947707] Bluetooth: L2CAP socket layer initialized
[   58.982845] Bluetooth: RFCOMM socket layer initialized
[   58.982865] Bluetooth: RFCOMM TTY layer initialized
[   58.982867] Bluetooth: RFCOMM ver 1.8
[   64.169040] NET: Registered protocol family 17
[   64.593455] wlan0: Initial auth_alg=0
[   64.593460] wlan0: authenticate with AP 00:17:3f:f1:1a:2c
[   64.594208] wlan0: RX authentication from 00:17:3f:f1:1a:2c (alg=0 transaction=2 status=0)
[   64.594212] wlan0: authenticated
[   64.594213] wlan0: associate with AP 00:17:3f:f1:1a:2c
[   64.595450] wlan0: RX AssocResp from 00:17:3f:f1:1a:2c (capab=0x431 status=0 aid=2)
[   64.595453] wlan0: associated
[   64.595456] wlan0: switched to short barker preamble (BSSID=00:17:3f:f1:1a:2c)
[   64.596809] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.423903] wlan0: no IPv6 routers present

```
daryl@ubuntu:~$

---

### Post by Cresho on 2008-06-10
I thought I posted that ATSC and video0 works with the 1600.  I did a few tests and it all runs fine.  The only problem is v4l-dvb and nvidia does not like each other and will not boot with 3d acceleration. I used me-tv to view and record high definition video with no problems at all.

---

### Post by saedelaere on 2008-06-10
@sofasurfer

Why don't you use quote or code tags to post the output of dmesg?
Funny thing with your tv-card, it seems the device is not recognized at all.
I don't wont to read all prior posts, so what did you do to get your card running?

@Cresho

So you should explain sofasurfer one more time what he has to do to install the drivers properly.

---

### Post by Cresho on 2008-06-10
> **saedelaere said:**
> @sofasurfer

Why don't you use quote or code tags to post the output of dmesg?
Funny thing with your tv-card, it seems the device is not recognized at all.
I don't wont to read all prior posts, so what did you do to get your card running?

@Cresho

So you should explain sofasurfer one more time what he has to do to install the drivers properly.

i did but he never answered.  he might have his card working already.

i just need to see his output

ls -l /dev/dvb/adapter0

the output should say something like this

```
-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-10 09:16 demux0
crw-rw----+ 1 root video 212, 5 2008-06-10 09:16 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-10 09:16 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-10 09:16 net0

```

once this is done, we can install a television viewer software

---

### Post by sofasurfer on 2008-06-10
daryl@ubuntu:~$ sudo ls -l /dev/dvb/adapter0
[sudo] password for daryl: 
ls: cannot access /dev/dvb/adapter0: No such file or directory

I am convinced that I have a major glitch in my system. I don't know what happened. I will go over this thread and condense down what steps I have taken. I had some steps where I could only partitially install packages and I have no idea what damage may have occured. 

I am sure that the information that has been provided is valid and will get things going. The card was actually working at one point. Then when I started to install tv-viewer I felt that progress was good until I had some problems with tkimg (I think that was the one that gave me trouble).

Now I also have some problems with my boot menu because I deleted a partition on my 2nd hard drive. But the good news (theres good news?) is that I have learn some things about grub :-)

So give me a couple of days to condense this thread down and I have a feeling that I may want to reinstall my system since that is the only way I have of knowing that bad things are not present. And reinstalling is the only thing that I am really really good at.

Take a break. I know you's have worked very hard to help me and I will not give up.

---

### Post by Cresho on 2008-06-11
your card is not operating.  are you running an nvidia car?  if you are, i am going to warn you streight up that the directions will corrupt your setup because the new v4l-dvb is not compatible to work with nvidia under xorg. 

I got my card working without installing nvidia drivers.  When i do, my res drops to 640x480 resolution.

The 1600 drivers work flawlessly.  the v4l-dvb does not.  The ones in ubuntu is too old and hope the guys working on the v4l fixes this issue.  It seems they are aware but do not have enough testers.  Ill probably be emailing them soon.

Do you still want the instructions?

so what do we have?
we have
1. working 1600 drivers
2. none working v4l-dvb drivers
3. working software "me-tv" works flawlessly on this card as well as my wintv 115 card

you dont need to use sudo for ls -l /dev/dvb/adapter0
.  if you are, you did not install anything correctly.

---

### Post by sofasurfer on 2008-06-11
>if you are, i am going to warn you streight up that the directions will >corrupt your setup because the new v4l-dvb is not compatible to work >with nvidia under xorg.

I believe this statement is saying what you said in post #34 when you said "i just discovered installing the new v4lin-dvb latest drivers hoses systems with extra new nvidia graphics card running the latest nvidia drivers".

I actually have a newer video card ,a Nvidia GeForce 7200 GS.
I believe that in post #20 is where I installed (reinstalled after I had trouble on my own) the v4l driver.

Question: I thought the v4l WAS the Hauppauge drivers. If it is NOT then what is it?

OK. If you are not just plum worn out from this I will try out your instructions.

Are you saying that my problem is just the wrong drivers for the Hauppauge Tuner?

If you are ready I am to. Otherwise tell me at your leisure.

---

### Post by Cresho on 2008-06-11
the drivers are the ones you grab from this file hauppauge_cd_3.4d1.zip

the library is the v4l-dvb which comes from the updated one that works with the latest ubuntu kernel v4l-dvb-24d053746e48.tar.bz2.

first off, you will need to set up your computer to use development libraries which are capable of compiling the stuff.fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  refresh with button on top.  Also add third party software and source software sources.
now enter this in terminal and type y when it asks you questions.
```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev
```


Driver Install
------------------------------------------
download drivers from hauppauge
[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)

Unzip, then copy the following files to the firmware directory and rename them as follows:

Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw
Drivers/Driver18/hcw18enc.rom -> v4l-cx23418-cpu.fw
Drivers/Driver18/hcw18mlC.rom -> v4l-cx23418-dig.fw

then in terminal 

sudo nautilus /lib/firmware
and drag and drop those 3 files into the firmware directory.  So now you have 3 in here.



Now for the libraries.(WARNING! THIS IS THE PART THAT HOSES YOUR SYSTEM)
------------------------------------------
download
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

extract here in the desktop and open terminal and enter commands

cd ~/Desktop/v4l-dvb-04ddbe145932
make
sudo make install (dont forget to enter password)



now to add a startup and in terminal you type
------------------------------------------
sudo gedit /etc/modules
add cx18 at the bottom.
save and exit
reboot (your computer may run at 640x480 because it dislikes nvidia{im talking about v4l-dvb which needs fixing and none available at the moment})

now do a "ls -l /dev/dvb/adapter0" without parenthesis.

and you should see an output like this part

-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-10 09:16 demux0
crw-rw----+ 1 root video 212, 5 2008-06-10 09:16 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-10 09:16 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-10 09:16 net0

what this tells you is that there is a dvb adaptor (High Definition television tuner) working in adapter0.  The drivers are working fine but the libraries what works with the drivers are not.  NOW!  the current v4l(i just noticed it got updated)-dvb helps the drivers talk to the kernel.  Once it does like the above says, you just need to get a video software working.  USE ME-TV!


install me-tv!
and here is my guide for the video software.
------------------------------------------
try installing the me-tv software through add and remove application in start menu of ubuntu. Some reason, works better. Then you will need to download the updated version and install it without uninstalling the older version. Don't ask why but it works better (I was expiriencing driver issue when the drivers are loaded correctly. Having the old version and installing the new one over it worked for me). Download [https://launchpad.net/me-tv/+download](https://launchpad.net/me-tv/+download) the latest one. download it to your desktop and extract it. Then you cd into your directory "cd /home/yourname/Desktop/me-tv-0.5.25

in terminal you

./configure
make
sudo make install

now for the dvb utilities. me tv helps you with everything but dvb utilities actually works better in detecting channels.

sudo apt-get install dvb-utils
directory is here! /usr/share/doc/dvb-utils/
do a

mkdir /home/yourusername/.azap
and this creates a very needed directory

in terminal do this next line
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

in your folder browser you can navigate to this location while the scan is taking place (nake sure you have view->hidden files in your browser so you can see the invisible directory). It will take a while and will see errors bot its normal till the channels start coming in. After scan terminal says done, open the channel.conf in the /home/yourusername/.azap directory with a text editor and save it as channels.conf on your desktop UTF-8 encoded(the option is available in the save feature so don't sweat it.

copy that channels.conf into the /home/yourusername/.me-tv and do not try using the my-tv channel scanner because it is not as good as the dvb-utils.

Launch the application and you can now record, watch.....ohh yeah, you can change the channels with right click and select the broadcasted name.



I hope you can still bootup into your high resolution desktop after this. :lolflag:  I'm posting all these warnings.  If you want to get your pc back to high resolution, all you need to do is remove the cx18 from startup, and in synaptic uninstall xserver-xorg-video-v4l.  If you do this, you can probably reinstall and synaptic will use the older one.

Don't ask about why it does not work with the ubuntu version.  All I know is the v4l-dvb you install mannually is an updated one for the new kernel.

---

### Post by sofasurfer on 2008-06-11
I had searched for the 1600 drivers earlier and from what I saw they were only available for Windows in the form of an .exe file. Now that I remember this, this is why I did not install them.

Are you saying that they are made for Linux also?

---

### Post by fenian on 2008-06-11
> **Cresho said:**
> 


Now for the libraries.(WARNING! THIS IS THE PART THAT HOSES YOUR SYSTEM)
------------------------------------------
download
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

extract here in the desktop and open terminal and enter commands

cd ~/Desktop/v4l-dvb-04ddbe145932
make
sudo make install (dont forget to enter password)



I think the commands should be...

> cd ~/Desktop/v4l-dvb-04ddbe145932
make menuconfig
make
sudo make install
sudo make unload
modprobe cx18

---

### Post by willoconley on 2008-06-11
did you rebuild the module since you updated the kernel

try:
$ cd ~/v4*
$ make distclean
$ sudo make unload
$ sudo make
$ sudo make install
$ sudo modprobe cx18
$ sudo reboot

---

### Post by sofasurfer on 2008-06-11
Hold it!! Too many people.
I appreciate the help but...

Cresho. In post #26 willoconley had me download and install the v4l drivers into the firmware directory. Look at that post and tell me if those are differant than what you want me to download right now. If so, I will proceed. 

Do you want me to rebuild the module as willoconely suggested in the last post?

---

### Post by willoconley on 2008-06-11
it's just rebuilding the module you already built in my first set of instructions. if you updated your kernel after you built the module the first time, when you did the steps in my first post and you havn't rebuilt the v4l module the drivers won't work, there will be no module to load for the new kernel.

---

### Post by sofasurfer on 2008-06-11
I do not think I updated the kernel...

daryl@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

---

### Post by willoconley on 2008-06-11
post the output of:

ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18

---

### Post by sofasurfer on 2008-06-11
daryl@ubuntu:~$ ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/cx18:
cx18.ko

---

### Post by willoconley on 2008-06-11
the .ko stands for kernel object or module, you just need to rebuild for 2.6.24.18.

---

### Post by sofasurfer on 2008-06-11
Is that your instructions in post #70? If not, how?

---

### Post by willoconley on 2008-06-11
yeah, post 70.

---

### Post by sofasurfer on 2008-06-11
With the make disclean command I got lots of "cannot remove" lines...

```
make[1]: Entering directory `/home/daryl/v4l-dvb/v4l'
rm -f *~ *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c av7110_firm.h fdump \
		config-compat.h Module.symvers
rm -f .version .*.o.flags .*.o.d Makefile.media \
		Kconfig Kconfig.kern .config .config.cmd .myconfig \
		.kconfig.dep
rm -rf .tmp_versions
rm: cannot remove `.tmp_versions/isl6405.mod': Permission denied
rm: cannot remove `.tmp_versions/zr36060.mod': Permission denied
rm: cannot remove `.tmp_versions/b2c2-flexcop-pci.mod': Permission denied
rm: cannot remove `.tmp_versions/ivtv.mod': Permission denied
rm: cannot remove `.tmp_versions/tda7432.mod': Permission denied
rm: cannot remove `.tmp_versions/mt2266.mod': Permission denied
rm: cannot remove `.tmp_versions/sp8870.mod': Permission denied
```


Is this a problem or should I continue?

---

### Post by willoconley on 2008-06-11
dude i'm sorry.
sudo make distclean

sorry. also on the next step
sudo make unload
if a bunch of the lines say 
-- in use 
or something like that off to the right, end your current session and drop to tty1 and run it

i have to hit the sack, hopefully that gets your drivers working again

---

### Post by Cresho on 2008-06-11
> **sofasurfer said:**
> Hold it!! Too many people.
I appreciate the help but...

Cresho. In post #26 willoconley had me download and install the v4l drivers into the firmware directory. Look at that post and tell me if those are differant than what you want me to download right now. If so, I will proceed. 

Do you want me to rebuild the module as willoconely suggested in the last post?

the files he posted are the ones from windows.  in the folder extracted, you go into the drivers/drivers18 directory and rename
Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw

and you do it to the ones you posted.  But he did this for you already.  you place these 3 files he gaved you into the /lib/firmware directory and NOT into the specific kernel such as 2.6.24.18-generic.  I bounced through this many times and /lib/firmware is the best location.

Now that you have the drivers in this location, you modprobe cx18 or sudo modprobe cx18 to start it up.  or if you want to auto load it, you cx18 into sudo gedit /etc/modules and place cx18 into the last part of the file and save.

after this, do a 

ls -l /dev/dvb/adapter0


in the terminal and you should se an adaptor0 output.  This means that your kernel is talking to your card.  This will only work if you have the v4l-dvb driver installed.  Reffer to my tutorial if his dont work.  Mines works just fine.

---

### Post by sofasurfer on 2008-06-11
The rebuild went fine. But I don't see a differance in...


 daryl@ubuntu:~$ ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/cx18:
cx18.ko
/lib/modules/2.6.24-18-generic/kernel/drivers/media/video/cx18:
cx18.ko

---

### Post by sofasurfer on 2008-06-11
Cresho.
I did as I was told and I put the windows driver in the firmware directory. I then renamed the 3 files and put them into the kernel file as I was told. Are you saying that they should NOT have gone into the kernel file?

---

### Post by Cresho on 2008-06-11
hmm..THose three files need to go into the /lib/firmware


Nothing more nor less.


NOW!  follow the next step getting your windows drivers to talk to the kernel.


download
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

extract here in the desktop and open terminal and enter commands

cd ~/Desktop/v4l-dvb-04ddbe145932
make menuconfig
make
sudo make install
sudo make unload
modprobe cx18 



now to add a startup and in terminal you type
------------------------------------------
sudo gedit /etc/modules
add cx18 at the bottom.
save and exit
reboot (your computer may run at 640x480 because it dislikes nvidia{im talking about v4l-dvb which needs fixing and none available at the moment})

now do a "ls -l /dev/dvb/adapter0" without parenthesis.

and you should see an output like this part

-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-10 09:16 demux0
crw-rw----+ 1 root video 212, 5 2008-06-10 09:16 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-10 09:16 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-10 09:16 net0

what this tells you is that there is a dvb adaptor (High Definition television tuner) working in adapter0. The drivers are working fine but the libraries what works with the drivers are not. NOW! the current v4l(i just noticed it got updated)-dvb helps the drivers talk to the kernel. Once it does like the above says, you just need to get a video software working. USE ME-TV!

---

### Post by sofasurfer on 2008-06-11
I have the v4l files in /lib/firmware. However, I also put them into /lib/firmware/2.6.24-18-generic. Do you want me to take them out of /lib/firmware/2.6.24-18-generic?

I need to go to bed now, 5:00am. I will finish your last post tomorrow hopefully. Please, don't post any more until I get cuaght up.

Good night.

---

### Post by willoconley on 2008-06-11
> daryl@ubuntu:~$ ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18
/lib/modules/2.6.24-17-generic/kernel/drivers/media/video/cx18:
cx18.ko
> **sofasurfer said:**
> The rebuild went fine. But I don't see a differance in...


 daryl@ubuntu:~$ ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18
/lib/modules/2.6.24-[COLOR="Red"]17[/COLOR]-generic/kernel/drivers/media/video/cx18:
cx18.ko
/lib/modules/2.6.24-[COLOR="Red"]18[/COLOR]-generic/kernel/drivers/media/video/cx18:
cx18.ko

are things still not working?
if not check to see what the problem is with dmesg | grep cx18

the firmware can be copied by:
cp /lib/firmware/2.6.24-17-generic/v4l-cx23418* /lib/firmware/2.6.24-18-generic

> download
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

extract here in the desktop and open terminal and enter commands

cd ~/Desktop/v4l-dvb-04ddbe145932
make menuconfig
make
sudo make install
sudo make unload
modprobe cx18



now to add a startup and in terminal you type

you do not need to do this. you already did it.

> sudo gedit /etc/modules
add cx18 at the bottom.
save and exit
reboot (your computer may run at 640x480 because it dislikes nvidia{im talking about v4l-dvb which needs fixing and none available at the moment})

I suppose you could do that, i have never had a problem with them loading once everything is installed correctly though.

---

### Post by saedelaere on 2008-06-12
I also got one question. Is the Hauppauge HVR-1600 able to receive digital and analogue signals?
Nobody of you gets a video device node like "/dev/video"?

Thanks

Saedelaere

---

### Post by sofasurfer on 2008-06-12
Good morning.

I think I have some success but I also have a couple things the mention first.

I was going over this thread. Installing me-tv in post #67... some things do not look familiar. So I went through this post again and installed me-tv.

When I installed the libraries...

```

sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev
```

...I did have 1 or 2 errors.


Cresho is very specific that that v4l files go INTO THE FIRMWARE DIRECTORY, next to /lib/firmware/2.6.24-18-generic.

Willoconelly is very specific that these files go INTO /lib/firmware/2.6.24-18-generic.

I eventially removed them from /lib/firmware/2.6.24-18-generic and placed them into /lib/firmware.

In post #67 when I scanned for channels using "scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf"  I did find some channels.

Here is my "channels.conf" file..

```
WDCQ-DT:479028615:8VSB:49:52:3
WDCQ-DT:479028615:8VSB:65:68:4
WDCQ-DT:479028615:8VSB:81:84:5
WDCQ-DT:479028615:8VSB:97:100:6
WNEM Digital Television:521028615:8VSB:49:52:3
WNEM HDTV:521028615:8VSB:65:68:4
[0005]:521028615:8VSB:81:84:5
WEYI High Def:569028615:8VSB:65:68:4
WEYI Digital Television:569028615:8VSB:49:52:3
WJRT-HD:605028615:8VSB:49:52:1
WJRT-S1:605028615:8VSB:65:68:2
WJRT-S2:605028615:8VSB:81:84:3
WAQP Digital Television:677028615:8VSB:49:52:3
WFUM HD:701028615:8VSB:49:52:1
WFUM SD:701028615:8VSB:65:68:2
```

I then performed these steps...

```
After scan terminal says done, open the channel.conf in the /home/yourusername/.azap directory with a text editor and save it as channels.conf on your desktop UTF-8 encoded(the option is available in the save feature so don't sweat it.

copy that channels.conf into the /home/yourusername/.me-tv

```

When I run me-tv I get this error...

"There's an invalid channel record in the channels.conf file"

It looks to me like I have success except for this one error. What is the error? I think it is this line... "[0005]:521028615:8VSB:81:84:5"

Do I just comment it out (in all 3 locations) or what?


Here is my "ls -l /dev/dvb/adapter0" output...

```
daryl@ubuntu:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-12 12:08 demux0
crw-rw----+ 1 root video 212, 5 2008-06-12 12:08 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-12 12:08 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-12 12:08 net0

```

---

### Post by Cresho on 2008-06-12
I am not sure but I remember getting this error as well.  It has an invalid character.  Your card is now working correctly btw.  you can now use any software to view.  To fix your invalid character error you do this.

WDCQ-DT:479028615:8VSB:49:52:3
WDCQ-DT:479028615:8VSB:65:68:4
WDCQ-DT:479028615:8VSB:81:84:5
WDCQ-DT:479028615:8VSB:97:100:6
WNEM Digital Television:521028615:8VSB:49:52:3
WNEM HDTV:521028615:8VSB:65:68:4
[0005]:521028615:8VSB:81:84:5
WEYI High Def:569028615:8VSB:65:68:4
WEYI Digital Television:569028615:8VSB:49:52:3
WJRT-HD:605028615:8VSB:49:52:1
WJRT-S1:605028615:8VSB:65:68:2
WJRT-S2:605028615:8VSB:81:84:3
WAQP Digital Television:677028615:8VSB:49:52:3
WFUM HD:701028615:8VSB:49:52:1
WFUM SD:701028615:8VSB:65:68:2



remove the parenthesis or remove [0005]:521028615:8VSB:81:84:5 .  I remember getting this error and this is how i fixed this problem.  post if it worked.  Are you running the latest me-tv(open up me-tv and under help->about read me the version number.  it could be a version you are using)?  you can also cut and paste your channels.conf from that directory into the destktop with me-tv off and open it up again and allow it to scan.  Me-tv is still being worked on so the scanning feature is weak.  When I try it, I barely get like 1 or 2 channels.  So I am copying my channels back into this directory at this very momment of posting.  YOU ALSO NEED A AMPLIFIED ATSC APPROVED ANTENNA! [http://www.radioshack.com/sm-indoor-vhf-uhf-hdtv-antenna-with-rf-remote-control--pi-2131034.html](http://www.radioshack.com/sm-indoor-vhf-uhf-hdtv-antenna-with-rf-remote-control--pi-2131034.html) but I found out there are better ones.  I have not tried others since I spent a good penny for this one.

---

### Post by xc3RnbFO8P on 2008-06-12
Show the output of channels.conf

---

### Post by Cresho on 2008-06-12
> **Ringi said:**
> Show the output of channels.conf

mines is

```
2-KCBS-DT:749028615:8VSB:49:52:1
4-NBC4-LA:605028615:8VSB:49:52:3
4.1-KNBC-WX-Plus:605028615:8VSB:65:68:4
5-KTLA:575028615:8VSB:49:52:3
5.1-RawNews:605028615:8VSB:81:84:5
7-KABC-DT:707028615:8VSB:49:52:1
7.1-KABC-SD:707028615:8VSB:65:68:2
7.2-KABC-WN:707028615:8VSB:81:84:3
9-KCAL-DT:647028615:8VSB:49:52:1
11-KTTV DT:779028615:8VSB:49:52:3
13-KCOP DT:785028615:8VSB:49:52:3
KDOC-HD:581028615:8VSB:49:52:1
KOCE-HD:677028615:8VSB:49:52:3
KOCE-TV:677028615:8VSB:0:0:65535
KOCE-OC:677028615:8VSB:65:68:4
KOCE-SD:677028615:8VSB:81:84:5
KCET-HD:743028615:8VSB:49:52:1
KCET-OC:743028615:8VSB:97:100:2
KCET-W:743028615:8VSB:65:68:4
KXLA-DT:695028615:8VSB:49:52:3
KVMD-DT:683028615:8VSB:81:84:5
KLCS-DT:635028615:8VSB:33:36:2
KLCS-DT:635028615:8VSB:49:52:3
KLCS-DT:635028615:8VSB:65:68:4
KLCS-DT:635028615:8VSB:81:84:5
ION:617028615:8VSB:49:52:3
IONLife:617028615:8VSB:81:84:5
KPXN qubo:617028615:8VSB:65:68:4
Spanish-TeleFutura:563028615:8VSB:49:52:3
Spanish-Univision:599028615:8VSB:49:52:3
Spanish-Telemundo-KVEA-HD:623028615:8VSB:49:52:3
Spanish-KAZA-DT:671028615:8VSB:49:52:3
Spanish-KRCA-DT:785028615:8VSB:49:52:3
Spanish-KWHY-HD:641028615:8VSB:49:52:3
Spanish-KWHY-SD:641028615:8VSB:65:68:4
Spanish-KCET-Vm:743028615:8VSB:81:84:3
Spanish-LATV:683028615:8VSB:97:100:6
```

If you look carefully, these are only my high definition channels in my area specifically in los angeles.  I modified it and in me-tv, In view->prefference, I changed "channel sort" to channels.conf because that is the order I want to see my channels appear and not by "transponder/service ID"

here is a pick running the me-tv [http://www.gnome-look.org/content/preview.php?preview=3&id=82939&file1=82939-1.jpg&file2=82939-2.jpg&file3=82939-3.jpg&name=E17+Liquid+Mythril](http://www.gnome-look.org/content/preview.php?preview=3&id=82939&file1=82939-1.jpg&file2=82939-2.jpg&file3=82939-3.jpg&name=E17+Liquid+Mythril)  I'm not running the 1600.  this one is the kworld ATSC 115.  The 1600 works on my system as well but I couldnt get it to run under xorg with nvidia.  So just reminding people there is a problem for now with the v4l-dvb and nvidia.

---

### Post by sofasurfer on 2008-06-12
Cresho.
I did save the channels.conf to desktop and then copied it to /home/yourusername/.me-tv, as you said to do.

In installing the newer me-tv I am missing some libraries. Heres the end of my ./configure output...

```

14 libgnomeui-2.0 >= 2.14 libglade-2.0 >= 2.6.0 libxml-2.0 libxine gnet-2.0 xtst gthread-2.0 gtk+-2.0 >= 2.12) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found
No package 'libxml-2.0' found
No package 'libxine' found
No package 'gnet-2.0' found
No package 'xtst' found
No package 'gthread-2.0' found
No package 'gtk+-2.0' found

```

---

### Post by Cresho on 2008-06-12
did you do this part?

we need to fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. 

sudo apt-get update

end then

sudo aptitude remove automake1.4



finally

sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev

---

### Post by sofasurfer on 2008-06-12
Sorry. I missed the server change part.

Heres my library install output. See error at end...

```
daryl@ubuntu:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libgnomeui-0 is already the newest version.
librsvg2-2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpurple-dev: Depends: libpurple0 (>= 1:2.4.1-1ubuntu2) but it is not going to be installed
  pidgin-dev: Depends: pidgin (>= 1:2.4.1-1ubuntu2) but it is not going to be installed
E: Broken packages
daryl@ubuntu:~$ Cresho is online now Report Post   Reply With Quote

```

How the heck did you do that "Cresho is online" part?

---

### Post by Cresho on 2008-06-12
okay now try we need to fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources.



under third-party software put a checkmark on all

add sources code.  put a checkmark on it.  it should have a check mark and not just highlight or blank.

then sudo apt-get update

if all goes well and all libraries install correctly, then try update me-tv  you still have not told me what version you running on me-tv

---

### Post by sofasurfer on 2008-06-12
Those step were already done. But I did not have the source code checked.
Now I still get this error...

The following packages have unmet dependencies:
  libpurple-dev: Depends: libpurple0 (>= 1:2.4.1-1ubuntu2) but it is not going to be installed
  pidgin-dev: Depends: pidgin (>= 1:2.4.1-1ubuntu2) but it is not going to be installed
E: Broken packages

---

### Post by Cresho on 2008-06-12
try and install me-tv.  Not all are needed.  Reason is because the only ones you need are

make sure you have dependencies installed.


* autotools-dev
* cdbs
* debhelper (>= 5)
* libglade2-dev
* libgnet-dev
* libgnome2-dev
* libgnomeui-dev
* libgtk2.0-dev (>= 2.12)
* libxine-dev
* libxml-parser-perl
* libxml2-dev
* libxtst-dev
* pkg-config

if these are not missing, your good to install

now download the letest me-tv

[https://launchpad.net/me-tv/+download](https://launchpad.net/me-tv/+download)

and  you can now
./configure
make
sudo make install

post the version.  I want to see if you installed it, if you have the 5.30, then just run the program and see if you get that error again

---

### Post by sofasurfer on 2008-06-12
I now have all of the above packages. I will install (hopefully) the newest me-tv after work.

By the way, you told me to install me-tv-0.5.25. The newest one is me-tv-0.5.30. Do you want me to install the NEWEST one?

Gotta go to work. Thanks.

---

### Post by Cresho on 2008-06-12
ya, my instructions are dated.  use the new one.  I have the 5.30 as well.

---

### Post by sofasurfer on 2008-06-13
SUCCESS!!
I have a HD channel on me-tv. Looks and sounds good. But I can not change channels with the right mouse button. I have some other issues but I will post about them tomorrow. For now though... success.

---

### Post by Cresho on 2008-06-13
just some usage information.  right click on the television and it pops up a menu at the bottom.  you can expand it so you can scroll down the available channels  you can select your channels here. there is an autosurf button which takes you through the channels every few seconds. you can hide the controls with  with the botton ontop and if you want fullscreen, use f.  and in fullscreen, you can right click.  the recorded shows are put into the your home directory /home/yourusername or ~/ directory.  one last thing, do not change the deinterlace type in from default.  it will consume tons of cpu

---

### Post by sofasurfer on 2008-06-13
I found the tv channel list at the bottom.
There is no program list information, such as the program guide.
Last night when I ran me-tv, every time I clicked a couple times my system would freeze up.
This morning when I first started my system up, I ran me-tv, and I could run normally until after 5 minutes or so my system froze up.
After that, when I run me-tv my system freezes up sometime after 1 click and sometimes after a couple clicks.
Any idea why that is?

---

### Post by Cresho on 2008-06-13
I get the same issues with the screen lockup but the software is functional.  ATSC tuners are slow to begin with.  If your signal is too weak, you will not get  a good signal lock and it will either freeze for a few seconds or not function at all.  Linux or the me-tv is not the problem.  ATSC tuners are just this way.  Believe me when I tell you i tried 3 of them already.

I fixed this problem with a more powerful ATSC antenna.  Instead of getting like 75% lockups, Now i have like 2 or 3 channels that lock up and need antenna adjustment.  The atsc antenna I have rotates with a motor inside of it so it also comes with a remote control.  it will rotate the antenna untill a good signal shows.  Me-TV has no signal meter at the moment to tell you how good the signal is but they are planning on implimenting one.  I would love to see this feature!  SOON!  some channels like High gain, and others like low gain.  I have a file that has specific atsc antenna settings for me to keep track of best settings.  like I use "channel 2cbs channel 12 and 2 gain".  For some reason, I mention me-tv 5.25.  I don't know exactly why but this version seems to work best!  you can use the same method you did with installing 5.30.  no need to uninstall old version.  I can tell you right now that after 10 minutes, i see some lockups in 5.30 and not 5.25.  So try it first before you decide on getting a better antenna.

I still have not found a way to get the program guide running.  I have'nt even tried looking into this.


update.
hmm.  5.30 is not as good as 5.25.  5.25 seems to operate better for some reason.  I'll be posting a bug at launchpad me-tv

---

### Post by sofasurfer on 2008-06-13
I'm not talking about the signal freezing up. That is good. I'm referring to a complete computer freeze. Video image freezes, no mouse function, no keyboard function. This happens less than it did earlier. I can click on the controls quite a bit with no freeze up until I do a lot of clicking. When I open firefox with the video running I get instant freezeup.

---

### Post by Cresho on 2008-06-13
It could be that your system is not running hardware graphics accelerator or is not powerfull enough or drivers are not running for your specific hardware and not supported by linux.

My system spec is
gigabyte motherboard with amd 6400 black edition
2gb ddr800 ram
BFG 8800gt oc.
sata drives

I can tell you that my pc runs at about 12% cpu usage all the time
When I ran the hvr1600 with no hardware acceleration, I did not have any freeze up at all.  You can try another television viewing software.  Now tha your hardware is working, try the suggestion from "willoconley".  His might work better.

---

### Post by sofasurfer on 2008-06-13
I'll check my cpu usage later. 
Off to work.
Thanks for all your help.

---

### Post by Shadowmeph on 2008-06-15
I live on the west coast of Canada and I am not picking any channels at all I am think it is because I am on cable but I am not sure how to change the scanner fore this

---

### Post by Cresho on 2008-06-15
look in the  /usr/share/doc/dvb-utils/examples directory and choose..hmmmm
atsc is for usa
dvb-s is for satelite
dvb-t is cable (terrestrial) europe

[http://en.wikipedia.org/wiki/DVB-T](http://en.wikipedia.org/wiki/DVB-T)

look at the picture.  You are most likely atsc and in this folder, change the scanner from 

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

to

/usr/share/doc/dvb-utils/examples/scan/atsc  look into this directory and you may need to replace
us-ATSC-center-frequencies-8VSB

with either of those in that directory and add it to the command line for an output.  try all of them since ATSC is canadian as well.

post if this info help

---

### Post by Shadowmeph on 2008-06-15
> **Cresho said:**
> look in the  /usr/share/doc/dvb-utils/examples directory and choose..hmmmm
atsc is for usa
dvb-s is for satelite
dvb-t is cable (terrestrial) europe

[http://en.wikipedia.org/wiki/DVB-T](http://en.wikipedia.org/wiki/DVB-T)

look at the picture.  You are most likely atsc and in this folder, change the scanner from 

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf

to

/usr/share/doc/dvb-utils/examples/scan/atsc  look into this directory and you may need to replace
us-ATSC-center-frequencies-8VSB

with either of those in that directory and add it to the command line for an output.  try all of them since ATSC is canadian as well.

post if this info help

so you are saying that I should go through that folder and keep replacing the us-ATSC-center-frequencies-8VSB with another one until I get some channel hits?

---

### Post by sofasurfer on 2008-06-15
I have marked this thread as "solved"
Even though setup of HVR 1600 is still a major task, I have accomplished what I asked for.

In my situation with my system freezing up, sometimes it isn't as bad as other times. 

I have now installed another Ubuntu on my system and I am now going to try to reproduce what was accomplished in this thread.If I can do that I may be able to actually help some people as you's have helped me.

Thanks.

---

### Post by bamboo.7 on 2008-06-16
> **sofasurfer said:**
> I have marked this thread as "solved"
Even though setup of HVR 1600 is still a major task, I have accomplished what I asked for.
Thanks.

Don't mark this as solved until it is 100% working the thread is called "Has anyone got the Hauppauge HVR 1600 working?" You shouldn't call it solved until it works perfectly. A) People with per tenant information will skip over because they assume its solved(fixed) B) It is "working" on the barely sense of the word. Marking it solved is a bit lazy. Anyway I'm glad to see there is progress thanks.

---

### Post by 714snoopy on 2008-06-20
I just wanted to say thanks to everyone on this thread for looking into getting the HVR-1600 working. I bought a new HVR-1600 a few days ago and almost returned it to the store after reading that there was no "real" driver support for the card yet. Google pointed me to this thread and my card appears to work. I say appears because I have not been able to hook up my cable feed to see if I can get some channels. But the driver installs perfectly!

Driver:
I followed Willoconley's #20 post to get the driver compiled and installed and that worked the very first time for me. Thanks for the great instructions! =D>

Just for my information, the line:

hg update -c 7892

What does the "7892" mean? Is that a revision you are updating the code to from the repository?

Maybe for another thread:
Anyone have any luck or pointers on how to get the USB remote working with Mythbuntu? It came with my card "WinTV-HVR 1600 Media Center Kit." (lsusb id: 1784:0001). How should I configure Mythbuntu's Control Center to use this remote? Any tips or link to a thread? :confused:

edit: I figured it out. Its a Phillips IR receiver. It was in the Mythbuntu Control Panel IR list. Now we'll see if the ir blaster will work.

Thanks!

Hardware:
BTW, I'm running Mythbuntu (on top of Xubuntu 8.04) on a Mini-ITX computer with a VIA 600MHz CPU and 256MB RAM! I really had to cram that HVR-1600 card in there! I'm not expecting great performance from this little box but its all I got right now.

---

### Post by willoconley on 2008-06-20
> **714snoopy said:**
> 
Just for my information, the line:

hg update -c 7892

What does the "7892" mean? Is that a revision you are updating the code to from the repository?

Yeah that was a revision I knew for certain worked. to get the latest its just:
hg update
and then recompile

---

### Post by GhettoYhetti on 2008-06-22
Wow!  After reading this "saga" . . . and knowing that I have nVidia 6800 XT to use with this HVR-1600 (model 1183) am I to assume:

1) My resolution will be horrific
2) each time there is a new "update" of "-"buntu  I will spend hours trying to figure out what needs recompling
3) My system will periodically freeze after 5 minutes

The top notch help you all provided was really inspiring, but . . . 

Can you tell me which TV card will make the afore mentioned issues not occur?  I have kids and don't have the time to play with my toys that often.

---

### Post by 714snoopy on 2008-06-23
> **GhettoYhetti said:**
> Wow!  After reading this "saga" . . . and knowing that I have nVidia 6800 XT to use with this HVR-1600 (model 1183) am I to assume:

1) My resolution will be horrific
2) each time there is a new "update" of "-"buntu  I will spend hours trying to figure out what needs recompling
3) My system will periodically freeze after 5 minutes

The top notch help you all provided was really inspiring, but . . . 

Can you tell me which TV card will make the afore mentioned issues not occur?  I have kids and don't have the time to play with my toys that often.
GhettoYhetti,

Before I bought the HVR-1600, I was going to play it safe and buy the PVR-150. To my knowledge, this is the best supported "out-of-the-box" card that will work with Mtyhbuntu. There are several for sale on eBay lately.

The reason I wanted to try and get the HVR-1600 working was because of its dual tuner and ability to receive and decode HD digital channels (ASTC). In 2009 when every thing goes to digital I wanted to make sure I didn't have to upgrade my tuner card so soon.

I can't speak to all of the problems you mentioned above. As far as #2 goes, it would take about 5 minutes to recompile the driver when a new kernel is released. (more on my pokey 600MHz machine). Just write a text file with the steps to take and put it in the same folder where the driver lives (or one above it). This is the nature of using Linux. At least you _have_ source code to compile unlike other OSes where you'd have to wait for someone to make a new driver or you might even have to pay for it.

I know where you are coming from by saying you don't have time to mess around with your computer to just get it to work. I have kids too. This thread has saved me an immense amount of time and frustration. The guys who have "time" to "mess" with stuff like this are a tremendous benifit to the rest of us. Thanks to all, agian.

BTW, I got my little mini-ITX working this weekend with Mythbuntu and the HVR-1600. It works! But, a 600MHz machine just won't cut the mustard. Wile watching live TV, every time the processor needed to write the MPEG stream to the disk the video would pause for a half-second or so. Oh, well. I'm going to look into buying a referb P4 at Micro Center and try again.

---

### Post by GhettoYhetti on 2008-06-23
> **714snoopy said:**
> GhettoYhetti,

Before I bought the HVR-1600, I was going to play it safe and buy the PVR-150. To my knowledge, this is the best supported "out-of-the-box" card that will work with Mtyhbuntu. There are several for sale on eBay lately.

The reason I wanted to try and get the HVR-1600 working was because of its dual tuner and ability to receive and decode HD digital channels (ASTC). In 2009 when every thing goes to digital I wanted to make sure I didn't have to upgrade my tuner card so soon.

I can't speak to all of the problems you mentioned above. As far as #2 goes, it would take about 5 minutes to recompile the driver when a new kernel is released. (more on my pokey 600MHz machine). Just write a text file with the steps to take and put it in the same folder where the driver lives (or one above it). This is the nature of using Linux. At least you _have_ source code to compile unlike other OSes where you'd have to wait for someone to make a new driver or you might even have to pay for it.

I know where you are coming from by saying you don't have time to mess around with your computer to just get it to work. I have kids too. This thread has saved me an immense amount of time and frustration. The guys who have "time" to "mess" with stuff like this are a tremendous benifit to the rest of us. Thanks to all, agian.

BTW, I got my little mini-ITX working this weekend with Mythbuntu and the HVR-1600. It works! But, a 600MHz machine just won't cut the mustard. Wile watching live TV, every time the processor needed to write the MPEG stream to the disk the video would pause for a half-second or so. Oh, well. I'm going to look into buying a referb P4 at Micro Center and try again.

714snoopy,

Thanks for the reply and CONGRATS on getting yours going!  I was really interested in hearing about your "mini".

I just may grow a spine and give this a go.  I have a AMD Athlon 64 3500+ and 1GB RAM so I shouldn't experience pausing.  

I agree, all the help from the people in this thread was incredible.  I don't think I would have stuck with it had I been facing it alone.  

I will post my results if I decide to give it a go.

---

### Post by 714snoopy on 2008-06-24
GhettoYhetti:

You've got an awesome machine there. You should have no problems. One thing I should caution you about though: Did you install the 64-bit version of Ubuntu? (Since you have an Athalon 64). I have an Athalon 64 Dual Core that I installed Ubuntu 64-bit on and while it works fine I did have problems compiling some DVD Light-scribe software on it because the code did not support the 64-bit libraries. I wouldn't think you'd have problems with the 1600 driver under this OS. But, if things aren't going well, this might be a clue.

Anyone have succsess with 64-bit Ubuntu and the HVR-1600?

P.S. Just bought a newer 1GHz VIA Mini-ITX from eBay for my next attempt at Mythbuntu. (Only $150!) We shall see what happens ...

---

### Post by GhettoYhetti on 2008-06-27
Sorry for the delay.  I run the 32-bit version.  Things start to get "complicated" when running 64-bit.

---

### Post by willoconley on 2008-07-11
hey i updated post number 20 with a way to get the binary or nivia script, not the ones in the repos, to work with the v4l module.

thanks paulsid.

---

### Post by reeseslover531 on 2008-07-23
so wait I am running 64-bit Hardy with a 8800 GT.  I want to get this card but I don't want my resolution to turn down to 640X480 and I want to make sure that the svideo in works.  Is all of this possible?  I don't mind having to re-compile stuff after every new kernel.

---

### Post by Sin@Sin-Sacrifice on 2008-07-24
I'm not made of money and, in fact, have very little so when I went to buy a computer... I got the best deal I could find at the store. Dumb idea now that I see the deals online but hey... Anyway.. I got the HP m8000n and it has a few toys on it. The HVR 1600 has a few RCA jacks that I liked using my playstation on in windows and would love to hook my TV up to as well. I was wondering if ya'll knew anything I could do for that and if I still have to worry about the NVIDIA incompatibility.

---

### Post by reeseslover531 on 2008-07-30
I got s-video working in 64 bit linux and all, but My problem is I am trying to use the s-video port to plug in a PS2 and there is a major delay between when I click something and when it shows up.  I am viewing the card in vlc.  Is there either another program, or something I can do to stop this delay???

thanks,
Joe

---

### Post by pcozzy on 2008-07-30
I used #20 post willoconley. on a 64 bit ultimate 1.8 ubuntu and nvidia 7300 GT with hauppage 1600.  I then installed mythtv you need to use /dev/dvb/adapter0/ for the digital video not /dev/video0. /dev/video0 is for analog.  It works better than windows hauppauge wintv software. I can fully control recordings with myth and it doesn't bring down my system in power like the windows version does.

huh I even have compiz working on 2 flatscreens, 15inch and 22inch with separate x windows so I run my myth.front.end on the small lcd while I am doing my work on the 22 inch. and separate set of desktops with each screen having it's own compiz.  

Only thing I haven't been able to do is move open apps from one screen to another. no big deal for now.

Overall i stayed away from ubuntu because I thought it wouldn't offer me similar apps and config to sabayon 3.4.  I was wrong Ubuntu is even better and there is much more posts that help you do things that are not in other linux distros. Go Ubuntu!

---

### Post by Robstarusa on 2008-08-06
Hey guys,

I just bought 2 of these and then found this thread.  I want to build a box based on a Celeron 430, console only (no gui).

I want the video device readable by VLC and for VLC to multicast the video feed to the lan.  I'd like two cable channels & 2 ota channels to be multicast.  I figure this is going to take ~ 80Mbit/second or so as the celeron 430 does not have HP to do transcoding.

I also have bought some wireless n routers with gigabit lan interfaces to stream from the living room (with antennas/cable box, etc) to the main switch (managed hp gigabit switch).

Anyone tried this kind of setup?  

I have tried one test with a pvr-350 & a captured/transcoded (by vlc) analog station and multicast it and it worked beautifully.  I hope using these cards is just as easy.

---

### Post by Shadowmeph on 2008-08-27
ok this says solved but I am not sure how to install this on Hardy the card is installed but where do I go from here?

---

### Post by sofasurfer on 2008-09-09
Do I need to perform the "Comprehensive Multimedia & Video Howto" before I attempt this tuner card installation? 

I lost my system and reinstalled. Then I followed post #20...
I then got the wrong results from 'dmesg'.

I have followed these steps about 4 times and I have not had a problem with post #20. The only difference this time around is this. I usually reinstall my package list from my old system (Which includes the "Comprehensive Multimedia & Video Howto") before I do these steps,but this time it is just a fresh install with just the 'sudo apt-get update', 'sudo apt-get dist-upgrade' and 'sudo apt-get upgrade' performed.

---

### Post by sofasurfer on 2008-09-11
I have reinstalled and performed the "Comprehensive Multimedia & Video Howto".
Theres apparently something going wrong that was not going wrong on earlier attempts.
Here is my 'dmesg | grep cx18' output. What does this indicate?

```

test@ubuntu:~$ dmesg | grep cx18
[   32.770450] cx18:  Start initialization, version 1.0.0
[   32.770521] cx18-0: Initializing card #0
[   32.770524] cx18-0: Autodetected Hauppauge card
[   32.770853] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   32.772063] cx18-0: cx23418 revision ffffffff (A)
[   32.926301] cx18-0: Invalid EEPROM
[   32.926304] cx18-0: VBI is not yet supported
[   33.115683] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   33.117653] cx18-0: Disabled encoder IDX device
[   33.117684] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   33.117687] DVB: registering new adapter (cx18)
[   33.198686] cx18-0: frontend initialization failedtest@ubuntu:~$ dmesg | grep cx18
[   32.770450] cx18:  Start initialization, version 1.0.0
[   32.770521] cx18-0: Initializing card #0
[   32.770524] cx18-0: Autodetected Hauppauge card
[   32.770853] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   32.772063] cx18-0: cx23418 revision ffffffff (A)
[   32.926301] cx18-0: Invalid EEPROM
[   32.926304] cx18-0: VBI is not yet supported
[   33.115683] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   33.117653] cx18-0: Disabled encoder IDX device
[   33.117684] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   33.117687] DVB: registering new adapter (cx18)
[   33.198686] cx18-0: frontend initialization failed
[   33.198822] cx18-0: DVB failed to register
[   33.198847] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   33.198862] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   33.198877] cx18-0: Registered device radio0 for encoder radio
[   33.199024] cx18-0: Error -12 registering devices
[   33.200407] cx18-0: Error -12 on initialization
[   33.200424] cx18: probe of 0000:01:06.0 failed with error -12
[   33.200448] cx18:  End initialization

[   33.198822] cx18-0: DVB failed to register
[   33.198847] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   33.198862] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   33.198877] cx18-0: Registered device radio0 for encoder radio
[   33.199024] cx18-0: Error -12 registering devices
[   33.200407] cx18-0: Error -12 on initialization
[   33.200424] cx18: probe of 0000:01:06.0 failed with error -12
[   33.200448] cx18:  End initialization

```

---

### Post by wiltk on 2008-09-11
**sofasurfer**, you may want to consult the ivtv-user mailing list which you can find from the driver's homepage: [http://ivtvdriver.org]("http://ivtvdriver.org")  The developers who actually work on the driver actively try and help people to get their card working and may be helpful to you.

The 'invalid EEPROM' seems to be the biggest issue for anyone trying to use this card.  I myself got it a few times and then miraculously it hasn't happened to me since, although when I did get it, I could sometimes get it to initialize correctly if I ran:

#sudo modprobe -r cx18
#sudo modprobe cx18

Also, are you using the newest version of the firmware?  They are linked to at the bottom of the cx18 driver page: [http://ivtvdriver.org/index.php/Cx18]("http://ivtvdriver.org/index.php/Cx18")

I know that isn't much help, but that's what I have to offer.

---

### Post by Farbi on 2008-09-25
I know this thread says solved but... I came across sofasurfer's problem (error cx18-0:Error -12).  The difference being that mine doesn't say anything about invalid eeprom.  Doesn't work in WinXP either (Not sure if that's relevant.  Anyhow, any help would be wonderful.  The Card worked three days ago... Did a scan for channels overnight and next day card wouldn't respond.  Rebooted thinking it might help (old windows habits die hard) and got this error.  Can post any info you might need... Just lemme know what you're looking for.



Thanks,
Farbish

Output of Dmesg |grep cx18

```
[   38.022565] cx18:  Start initialization, version 1.0.0
[   38.022610] cx18-0: Initializing card #0
[   38.022612] cx18-0: Autodetected Hauppauge card
[   38.022901] cx18-0: Unreasonably low latency timer, setting to 64 (was 2)
[   38.023023] cx18-0: cx23418 revision 01010000 (B)
[   38.213939] cx18-0: Autodetected Hauppauge HVR-1600
[   38.213940] cx18-0: VBI is not yet supported
[   38.610467] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   38.678947] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   38.678966] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   38.906473] cx18-0: Disabled encoder IDX device
[   38.906506] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   38.906508] DVB: registering new adapter (cx18)
[   39.063402] cx18-0: frontend initialization failed
[   39.063550] cx18-0: DVB failed to register
[   39.063626] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   39.063639] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   39.063652] cx18-0: Registered device radio0 for encoder radio
[   39.063763] cx18-0: Error -12 registering devices
[   39.064099] cx18-0: Error -12 on initialization
[   39.064159] cx18: probe of 0000:01:09.0 failed with error -12
[   39.064170] cx18:  End initialization
[85891.115137] cx18:  Start initialization, version 1.0.0
[85891.115184] cx18-0: Initializing card #0
[85891.115187] cx18-0: Autodetected Hauppauge card
[85891.115318] cx18-0: cx23418 revision 01010000 (B)
[85891.300992] cx18-0: Autodetected Hauppauge HVR-1600
[85891.300994] cx18-0: VBI is not yet supported
[85891.383179] tuner 6-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[85891.360579] tuner 6-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[85891.360600] cs5345 5-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[85891.370431] cx18-0: Disabled encoder IDX device
[85891.370464] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[85891.370467] DVB: registering new adapter (cx18)
[85891.371324] cx18-0: frontend initialization failed
[85891.371400] cx18-0: DVB failed to register
[85891.371414] cx18-0: Registered device video32 for encoder YUV (2 MB)
[85891.371425] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[85891.371436] cx18-0: Registered device radio0 for encoder radio
[85891.371528] cx18-0: Error -12 registering devices
[85891.371837] cx18-0: Error -12 on initialization
[85891.371844] cx18: probe of 0000:01:09.0 failed with error -12
[85891.371854] cx18:  End initialization
[85934.252936] cx18:  Start initialization, version 1.0.0
[85934.252977] cx18-0: Initializing card #0
[85934.252980] cx18-0: Autodetected Hauppauge card
[85934.253108] cx18-0: cx23418 revision 01010000 (B)
[85934.439941] cx18-0: Autodetected Hauppauge HVR-1600
[85934.439942] cx18-0: VBI is not yet supported
[85934.521992] tuner 6-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[85934.523966] tuner 6-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[85934.524413] cs5345 5-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[85934.528813] cx18-0: Disabled encoder IDX device
[85934.529193] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[85934.529635] DVB: registering new adapter (cx18)
[85934.530858] cx18-0: frontend initialization failed
[85934.531667] cx18-0: DVB failed to register
[85934.531983] cx18-0: Registered device video32 for encoder YUV (2 MB)
[85934.532434] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[85934.532917] cx18-0: Registered device radio0 for encoder radio
[85934.533439] cx18-0: Error -12 registering devices
[85934.534808] cx18-0: Error -12 on initialization
[85934.535144] cx18: probe of 0000:01:09.0 failed with error -12
[85934.535664] cx18:  End initialization
```

Computer:
AMD X2 4600+
2GB DDR2 800
ABIT AN52 Main Board
Nvidia GeForce 8600 GTS
Hauppauge HVR-1600 MCE
Anything else you need lemme know
PS it may say that the analog side is registered but mplayer says otherwise

---

### Post by JdawgZX11d on 2008-11-26
I know it is kind of late for entering this post. I just finished installing MythTv on my former MCE machine(F^^K winders...) I am having the same issue. I am kind of looking down the avenue of hardware conflicts. Is there (i am sure there is) a command I can type to give me all of my hardware information and start looking for conflicts? I have only had my Myth box up for 1 day now and so far it is worth the hassle I might add, but let me finish by saying I build a Vista MCE box. You guys can stop laughing anytime...

---

### Post by GhettoYhetti on 2008-12-02
> **JdawgZX11d said:**
> I know it is kind of late for entering this post. I just finished installing MythTv on my former MCE machine(F^^K winders...) I am having the same issue. I am kind of looking down the avenue of hardware conflicts. Is there (i am sure there is) a command I can type to give me all of my hardware information and start looking for conflicts? I have only had my Myth box up for 1 day now and so far it is worth the hassle I might add, but let me finish by saying I build a Vista MCE box. You guys can stop laughing anytime...
lspci  should help you out.

---

### Post by sofasurfer on 2008-12-02
Farbi.
>The Card worked three days ago... Did a scan for channels overnight and next >day card >wouldn't respond. Rebooted thinking it might help (old windows >habits die hard) and got this error.

At one point, long ago, my card stopped functioning also. For weeks I tried to get it running. No success. Then I decided to reinstall Ubuntu. Still no success. Then I tried this... I removed the card, reinstalled Ubuntu, reinstalled the card, success. Its another old Windows trick.

Try this. Shut down computer, remove your card, restart computer with card removed, shutdown computer, reinstall card and then restart computer with card installed.

I'm probably the last person to take advice from on this subject but...

By the way, I moved to 8.10 and the card is recognized immediately. I use it with Mplayer. Haven't gotten Myth working yet. Its as complicated as the 1600 card.

Let us know what happens.

---

### Post by Farbi on 2008-12-07
Thanks for the reply, and the suggestion.  Just recently came back from a horrific hardware failure (just about everything died, MB, HD, Proc (large black burn marks) video card, the 1600 survived though, go figure...)  anyhow now that I'm running 8.10 it is good for me as well.

Again, 
Thanks for the reply, and the suggestion I'll give that a go if it stops working again

Farbish

---

### Post by neumann63 on 2008-12-12
Hi to all,

this card really frustrates me.
Perhaps some of you guys can help me.
Here first some data.

Operation system:Ubuntu 8.10 (Kernel:2.6.27-9-generic)
Grafik-card:NVidia 8400 GS
First DVB Card: Hauppauge Nexus-S
Second DVB Card: Hauppauge HVR-1600
Desired Recorder: VDR

Due to dmesg | grep cx18 everthing seems to be alright. Correct ??

```
root@family-desktop:/home/neumann# dmesg | grep cx18
[   12.914248] cx18:  Start initialization, version 1.0.3
[   12.914300] cx18-0: Initializing card #0
[   12.914304] cx18-0: Autodetected Hauppauge card
[   12.914401] cx18 0000:01:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.916047] cx18-0: cx23418 revision 01010000 (B)
[   13.152242] cx18-0: Autodetected Hauppauge HVR-1600
[   13.152245] cx18-0: VBI is not yet supported
[   13.293282] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   13.293324] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   13.352078] cx18-0: Disabled encoder IDX device
[   13.352218] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   13.352223] DVB: registering new adapter (cx18)
[   13.480083] cx18-0: DVB Frontend registered
[   13.480150] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   13.480216] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   13.480220] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   13.480395] cx18:  End initialization
[   29.569840] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   30.346421] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   30.352791] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   31.938160] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[  133.816033] Modules linked in: af_packet binfmt_misc bridge stp bnep rfcomm sco l2cap bluetooth ppdev ipv6 acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative wmi video output sbs sbshc pci_slot container battery iptable_filter ip_tables x_tables ac lp stv0299 ves1x93 mxl5005s s5h1409 tuner_simple tuner_types cs5345 tuner snd_hda_intel dvb_ttpci snd_pcm_oss snd_mixer_oss snd_pcm cx18 snd_seq_dummy dvb_core saa7146_vv compat_ioctl32 snd_seq_oss saa7146 joydev i2c_algo_bit cx2341x videobuf_dma_sg videobuf_core evdev videodev snd_seq_midi v4l2_common tveeprom v4l1_compat ttpci_eeprom pcspkr snd_rawmidi atl2 nvidia(P) snd_seq_midi_event parport_pc parport i2c_core snd_seq snd_timer snd_seq_device button intel_agp snd iTCO_wdt agpgart iTCO_vendor_support soundcore shpchp pci_hotplug snd_page_alloc ext2 mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid ata_piix pata_acpi ata_generic libata scsi_mod dock ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
``` 

I deactivate my VDR-System (/etc/init.d/vdr stop) and let w_scan run

```
root@family-desktop:/home/neumann#  w_scan -f a -A 2 -i 2 -O 0 -X >>/var/lib/vdr/channels.conf.czap4
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found ATSC frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend Samsung S5H1409 QAM/8VSB Frontend supports
FE_CAN_8VSB
FE_CAN_QAM_64
FE_CAN_QAM_256
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 
63000: 
69000: 
79000: 
85000: 
177000: 
183000: 
189000: 
195000: 
201000: 
207000: 
213000: 
123012: 
129012: 
135012: 
141000: 
147000: 
153000: 
159000: 
165000: 
171000: 
219000: 
225000: 
231012: 
237012: 
243012: 
249012: 
255012: 
261012: 
267012: 
273012: 
279012: 
285012: 
291012: 
297012: 
303012: 
309012: 
315012: 
321012: 
327012: 
333012: 
339012: 
345012: 
351012: 
357012: 
363012: 
369012: 
375012: 
381012: 
387012: 
393012: 
399012: 
405000: 
411000: 
417000: 
423000: 
429000: 
435000: 
441000: 
447000: 
453000: 
459000: 
465000: 
471000: 
477000: 
483000: 
489000: 
495000: signal ok (ch69 QAM)
501000: 
507000: 
513000: 
519000: 
525000: 
531000: 
537000: 
543000: 
549000: 
555000: signal ok (ch79 QAM)
561000: signal ok (ch80 QAM)
567000: signal ok (ch81 QAM)
573000: 
579000: 
585000: 
591000: signal ok (ch85 QAM)
597000: no signal(0x00)
603000: signal ok (ch87 QAM)
609000: signal ok (ch88 QAM)
615000: signal ok (ch89 QAM)
621000: signal ok (ch90 QAM)
627000: signal ok (ch91 QAM)
633000: signal ok (ch92 QAM)
639000: no signal(0x00)
645000: 
93000: 
99000: 
105000: 
111012: 
117012: 
651000: 
657000: 
663000: 
669000: 
675000: 
681000: 
687000: 
693000: 
699000: 
705000: 
711000: 
717000: 
723000: 
729000: 
735000: 
741000: signal ok (ch115 QAM)
747000: 
753000: no signal(0x00)
759000: 
765000: 
771000: 
777000: 
783000: 
789000: 
795000: 
801000: no signal(0x00)
807000: no signal(0x00)
813000: 
819000: 
825000: 
831000: 
837000: 
843000: 
849000: 
tune to: 
----------no signal----------
tune to:  (no signal)
----------no signal----------
tune to: 
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x1ffb
tune to: 
WARNING: descriptor_tag == 0x80, len is 0
WARNING: descriptor_tag == 0x80, len is 0
Info: filter timeout pid 0x1ffb
tune to: 
Info: filter timeout pid 0x1ffb
tune to: 
Info: filter timeout pid 0x1ffb
tune to: 
Info: filter timeout pid 0x1ffb
tune to: 
Info: filter timeout pid 0x1ffb
tune to: 
service is running. Channel number: 1008:0. Name: ''
service is running. Channel number: 1008:0. Name: ''
tune to: 
service is running. Channel number: 1008:0. Name: ''
service is running. Channel number: 1008:0. Name: ''
service is running. Channel number: 1008:0. Name: ''
service is running. Channel number: 1008:0. Name: ''
tune to: 
Info: filter timeout pid 0x1ffb
tune to: 
----------no signal----------
tune to:  (no signal)
service is running. Channel number: 1008:0. Name: ''
tune to: 
----------no signal----------
tune to:  (no signal)
----------no signal----------
dumping lists (107 services)
Done.

```

For me this looks like w_scan finds some channels and it confirms that /dev/dvb/adapter0/frontend0 is my ATSC device.

Changing the channels.conf a little bit. The starting czap it tells me that my card is not QAM-device. Can someone help me on this ??

```
root@family-desktop:/home/neumann# czap -a 0 -f 0 -d 0  -c /var/lib/vdr/channels.conf.czap4 [0139]
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
 37 [0139]:603000000:INVERSION_OFF:0:FEC_NONE:QAM_256:289:290:313
 37 [0139]: f 603000000, s 0, i 0, fec 0, qam 5, v 0x121, a 0x122
ERROR: frontend device is not a QAM (DVB-C) device

```

I tried my luck with other programs like mplayer but there I have only
some funny snow-storm-pictures (this seems to be the analog site).
And with vlc I tried a lot of things too. No Success.

I really don't know whats wrong. But why seems the scan to work ??

I really need some help.

Mike

---

### Post by fryed_1 on 2008-12-23
FYI I found that the module:  lirc_pvr150 was interfering with the cx18 module trying to unload.  It appears to be the blaster module.  When I commented it out in /etc/lircd/hardware.conf it loaded without issue.  Granted I lost control of my blaster... but now I have HD working, so it's better for me in the short run since the only reason I was using the blaster was for controlling my HD box until I got HD working within the tuner.

---

### Post by RGPerson on 2009-06-21
Willoconley or anyone, I could use some help. Tried installing the drivers and firmware as instructed at [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

but after I shutdown as instructed, we have a severly screwed up GUI.  It's so distorted nothing can be done. I was able to boot with the Terminal and that's where I am now.

> **willoconley said:**
> To get your hauppuage card  working:

# go to tty1, to remove the old firmware you installed
$ sudo /etc/init.d/?dm stop

I did this.  Nothing appeared to happen.  Maybe it did.  Went on.

> **willoconley said:**
> 
$ cd pathToV4LDir             # in my case ~/v4l*


Couldn't even get this far. I had downloaded and extracted the drivers to the tmp folder. (tmp/HVR1600 to be exact, and then renamed the next folder as V4l-dvb)  It couldn't be found. I did a dir of tmp and there were only a few folders in there, none of which were HVR1600

Can someone give me a command to download them again to a better place?  And to extract them.  I'm not the best person for the command line.

Is that it below?

> **willoconley said:**
> 
$ sudo make unload
$ sudo make install -r

# you can now, if you want
$ sudo /etc/init.d/?dm start
# and go back to tty7
$ sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd ~/v4l*
$ sudo make
$ sudo make install

 now after you copy those firmware files you posted about earlier to /lib/firmware/*currentKernel*

$ sudo reboot 

I skipped all that for now as I can't seem to undo what I'd already done before I can start fresh.

But on a lark, I did the next bit:

> **willoconley said:**
> 
$ dmesg | grep cx18
# near the end should say something like:
[   42.230394] cx18-0: Initialized card #0: Hauppauge HVR-1600


...and I did get pretty much what willoconley put there.  It seems the card did make it. 

I don't have an nVidia card. We have an ATI Radeon 4550.  The computer is a Dell Inspiron 530N, dual-core with 4GB of memory and a 320GB hard drive.

I'd very much appreciate any help on this.  

Gabrielle

---

### Post by RGPerson on 2009-06-21
Well some progress or at least maybe a clue.

We got an old monitor out of the closet and hooked it up. We have GUI there.  It's low res (800x600 or 640x480) but it's there.

Could the HVR-1600 drivers or firmware have messed with out ATI Radeon 4550's drivers/firmware?  We normally (and would prefer to) use our LCD TV as the monitor as this computer is to be our TV.

On the not so progress side, we can't even boot to the terminal with the TV now.  All we have is a black screen.  Did see the Dell logo and the GRUB, saw Starting Up... and then black.

Update: for some reason, we have a GUI again with the TV as monitor. We're stuck in low resolution with not a lot of colors.  I'm really suspecting the HVR driver or firmware install messed with the Radeon.  Should I try to reinstall the latter?


Gabrielle

---

