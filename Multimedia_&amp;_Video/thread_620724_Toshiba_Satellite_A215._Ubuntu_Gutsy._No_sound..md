---
title: "Toshiba Satellite A215. Ubuntu Gutsy. No sound."
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Roasted on 2007-11-22
I don't know what to do. I just set up dual boot with Vista/Ubuntu Gutsy and I got a few things to work out. I have 3 problems, one of which I fixed. The 3d effects I got fixed by installing the restricted drivers card and doing a few other things. Besides that, I have no sound and no wireless internet. Okay fine. Wireless thread already started, so here is the sound thread.

I have no idea what to do. I've searched and searched. I don't know what to do. I'm at the point where I just need to go to bed and hope that I get a response for the morning.

Has anybody had any luck setting up sound on an A215 Satellite?? HELP!

---

### Post by xeth_delta on 2007-11-22
What sound card do you have? You might be able to find out with:

```
lspci | grep -i audio
```

Xeth

---

### Post by Roasted on 2007-11-23
00.14.2 Audio Device: ATI Technologies Inc SBx00 Azalia

---

### Post by Zack McCool on 2007-11-23
> **Roasted said:**
> I don't know what to do. I just set up dual boot with Vista/Ubuntu Gutsy and I got a few things to work out. I have 3 problems, one of which I fixed. The 3d effects I got fixed by installing the restricted drivers card and doing a few other things. Besides that, I have no sound and no wireless internet. Okay fine. Wireless thread already started, so here is the sound thread.

I have no idea what to do. I've searched and searched. I don't know what to do. I'm at the point where I just need to go to bed and hope that I get a response for the morning.

Has anybody had any luck setting up sound on an A215 Satellite?? HELP!

Hmmm.  It worked here without any config changes.  The only issue I have is that the speakers do not turn off when you plug in headphones.

Have you checked the volume controls to be sure that you are using Alsa, and that the volume is up, and not muted?  The volume knob even works OK here...

---

### Post by Roasted on 2007-11-23
In the upper right corner by the clock the volume controls were sitting there with a red X over top of the icon as if it were muted. I selected it to turn the volume up thinking it was just so low that it was indeed muted. I was prompted with an error, suggesting that maybe I have the wrong gstreamer plugins installed that is causing the error. I have been unable to determine if I have the improper plugins installed or what. I have no clue what to do. However, I will boot back over to Ubuntu to see what's going on.

I'm on Vista now because Vista's sound and wireless capabilities work. Ouch. Burn. lol.

Do you own this same brand of laptop? Are you using wireless internet???

---

### Post by xeth_delta on 2007-11-23
My guess is that your card uses the hda-intel driver, from what I could see in the alsa documentation.

You should first see if there is any sound related module loaded:

```
lsmod | grep -i snd
```

if not, try restarting the alsa sound system:

```
sudo /etc/init.d/alsasound restart
```

or

```
sudo /etc/init.d/alsa restart
```

If none of these work,  have a look at the instructions I posted on this thread [http://ubuntuforums.org/showthread.php?t=614773]("http://ubuntuforums.org/showthread.php?t=614773"), it has worked for me before, I don't have the same computer you have, though.

Xeth

---

### Post by Roasted on 2007-11-23
jason@jason:~$ lsmod | grep -i snd
snd_hda_intel         291488  1 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd


The 2 commands you posted didn't work. "Command not found."

---

### Post by xeth_delta on 2007-11-23
Modules seem to be loaded. About the script, you are the second person that tells me they don't have alsasound. Did you write the full path to the script? You can also try looking if htere is any related script in **/etc/init.d**.

Can you check if there is any error while loading the modules?

```
dmesg | grep -i hda
```

I wonder if it doesn't in fact have something to do with your gnome configuration, I am not a gnome user, though.

You wrote it was complaining about codecs, have you installed any extra codecs?

Xeth

---

### Post by Roasted on 2007-11-23
I think what happened was the codecs were part of the software packages that I had to select after installing. I think I jumped the gun and tried to get everything working without realizing that my software sources needed to be tinkered with first.

Okay, fine. 

Now whenever I try to raise/lower my audio, it does so accordingly, however I hear NO sound and I yield no error.

I'm on youtube right now watching a music video that I hear zero sound out of. I also just tried playing an mp3 on the local machine through audacious and I get zero sound.

This sounds to be an easy issue, now. I just need a certain plugin that I am lacking. What could it be?

---

### Post by xeth_delta on 2007-11-23
perhaps the channels are muted. Try alsamixer and enabling / raising the volume for diffrent channels.

---

### Post by Roasted on 2007-11-23
Just did. No luck. :(

---

### Post by Zack McCool on 2007-11-24
> **Roasted said:**
> In the upper right corner by the clock the volume controls were sitting there with a red X over top of the icon as if it were muted. I selected it to turn the volume up thinking it was just so low that it was indeed muted. I was prompted with an error, suggesting that maybe I have the wrong gstreamer plugins installed that is causing the error. I have been unable to determine if I have the improper plugins installed or what. I have no clue what to do. However, I will boot back over to Ubuntu to see what's going on.

I'm on Vista now because Vista's sound and wireless capabilities work. Ouch. Burn. lol.

Do you own this same brand of laptop? Are you using wireless internet???

Yup.  I have an A215-S4697.  The Sound worked fine on a clean install.  No tweaking.  The wireless was detected, but the protected mode Atheros driver did not work, so I installed the Windows driver with NDISWrapper.  Took a couple minutes, and works just fine.  Use it daily.

---

### Post by Roasted on 2007-11-24
> **Zack McCool said:**
> Yup.  I have an A215-S4697.  The Sound worked fine on a clean install.  No tweaking.  The wireless was detected, but the protected mode Atheros driver did not work, so I installed the Windows driver with NDISWrapper.  Took a couple minutes, and works just fine.  Use it daily.

Are you serious? I did a clean install. Twice. Why is mine not being detected then? Are you suggesting I reinstall Ubuntu?

---

### Post by nevhood on 2007-11-24
> **Roasted said:**
> Are you serious? I did a clean install. Twice. Why is mine not being detected then? Are you suggesting I reinstall Ubuntu?

Hello!  I'm using a Toshiba Satellite as well, and was having issues - this worked for me:

[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

Edit - the sound worked for me after this fix, but there are still issues with the headphone jack.  Particularly, when I change the volume with the headphones plugged in, the speakers unmute and play sound as well.

---

### Post by Roasted on 2007-11-24
Every time I issue 1 or 2 commands in terminal, terminal freezes on me. I don't know what to do with this garbage.

I'm going to do another installation. This is just so frustrating. I hate to drop the bombshell - but Vista didn't even drive me this crazy. :(

By the way, on my laptop I'm on the livecd now and I have the sound error. If it would detect my sound card without any issues upon a full installation, it shouldn't yield any errors on the livecd, right? 

My error is this- 

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. You can either remove the volume control from the panel by right clicking the speaker icon on the panel and selecting remove from panel from the menu.

---

### Post by xeth_delta on 2007-11-24
> **Roasted said:**
> Every time I issue 1 or 2 commands in terminal, terminal freezes on me. I don't know what to do with this garbage.

I'm going to do another installation. This is just so frustrating. I hate to drop the bombshell - but Vista didn't even drive me this crazy. :(

By the way, on my laptop I'm on the livecd now and I have the sound error. If it would detect my sound card without any issues upon a full installation, it shouldn't yield any errors on the livecd, right? 

My error is this- 

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. You can either remove the volume control from the panel by right clicking the speaker icon on the panel and selecting remove from panel from the menu.

The terminal freezing? That's new... and strange. It might be worth trying a new installation.
What version are you trying to install, btw? If you are trying Gutsy, may I suggest giving Feisty a try? Also, if you don't mind trying another graphical interface you could try Kubuntu.

To answer one of your questions, if something works on the live cd, it should work on the final installation. By the other hand, if it does not work on the cd, it most likely can be made to work on the final installation. Even if the sound card will work directly, your wireless card will have to be configured manually with ndiswrapper.

Too bad you've been having so much trouble, I guess it can happen sometimes under certain configurations. But don't dispare, in the end it should work. I'm actually on Feisty on a Macbook right now and it runs great.

Let me know what you choose.

---

### Post by Roasted on 2007-11-24
I'm installng Gutsy. I just did a fresh install of Gutsy and the sound does not work. I just put in the LiveCD for Feisty and I received the same sound card error as I did in Gutsy. So at least I know Feisty wouldn't offer me any advantage to downgrade. 

Just for the sake of trying out other distros, I tried Fedora yesterday, which drove me nuts. Maybe I just need some experience in using other distros first but the first taste of Fedora I got I wasn't really happy with. Right now I'm downloading a LiveCD of Suse, so we'll see if Suse can offer anything else on the LiveCD that would work out-of-box. 

I'm not planning on switching distros. It's more of a curiosity thing.

---

### Post by xeth_delta on 2007-11-24
Yeah, it is a good idea to try and see what other distros can offer. Before Ubuntu I used Gentoo and RedHat.

I am curious as to whether the sound problem is limited to Gnome. Do you have a Kubuntu CD around?I think SuSE uses KDE by default (at least it used to), so it might give you a clue.

---

### Post by Yellow Pasque on 2007-11-24
If you can't get it to work with ALSA, my suggestion is to give OSSv4 a shot. IMHO, it's much easier to configure. See my sig for details.

---

### Post by Roasted on 2007-11-25
How do I go about getting OSSv4 a shot? Do I have to install it or is it some kind of configuration utility already in Gutsy? I've NEVER heard of it.

---

### Post by Yellow Pasque on 2007-11-25
> **Roasted said:**
> How do I go about getting OSSv4 a shot? Do I have to install it or is it some kind of configuration utility already in Gutsy? I've NEVER heard of it.
Click the link in my signature.

---

### Post by xeth_delta on 2007-11-25
> **Roasted said:**
> How do I go about getting OSSv4 a shot? Do I have to install it or is it some kind of configuration utility already in Gutsy? I've NEVER heard of it.

If you are planning to give OSS a try and you compiled and installed the alsa driver from source (in the way I suggested several posts ago), remember to go to the driver source code directory and issue a **make uninstall**.

---

### Post by Roasted on 2007-11-26
My head is suddenly spinning. :(

---

### Post by Roasted on 2007-11-27
I've been distracted lately by trying to get my wireless to work... Last night I ordered a 3com usb adapter which is supposedly fully compatible with Ubuntu... so until it gets shipped in, back to the sound problem.

It sounds like Alsa is the easier one of the two to configure. How exactly do I troubleshoot a sound problem with Alsa in Ubuntu? I've never had this issue before... Every other computer I've used, whether it be brand new or 12 years old, has picked up sound immediately.

---

### Post by xeth_delta on 2007-11-27
> **Roasted said:**
> I've been distracted lately by trying to get my wireless to work... Last night I ordered a 3com usb adapter which is supposedly fully compatible with Ubuntu... so until it gets shipped in, back to the sound problem.

It sounds like Alsa is the easier one of the two to configure. How exactly do I troubleshoot a sound problem with Alsa in Ubuntu? I've never had this issue before... Every other computer I've used, whether it be brand new or 12 years old, has picked up sound immediately.

Since you already know what sound card you have you could start by checking if the right modules are loaded cleanly into the kernel.

 I just checked again the alsa website and found this: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI") and [http://www.alsa-project.org/main/index.php/Matrix:Module-atiixp]("http://www.alsa-project.org/main/index.php/Matrix:Module-atiixp")

It seems that in fact you need the atiixp module.  From a previous post of yours I noticed that the respective modules are not loaded.

In the links above you will find instructions on how to compile wht seems to be your sound card driver.

Let me know if you have any questions.

---

### Post by Roasted on 2007-11-27
I thoroughly read over the two links... I'm sort of confused. I thought I had to download something, yet I found nothing to download. So I figured I'd just go with it... and eventually after the section where I create a new directory, it wants me to cp something... RIGHT after making the directory... yet the directory is (obviously) empty...

Just doesn't make sense to me... 

And for the record, xeth, if you didn't live so damn far away I'd take you out for a drink for how much you've helped me thus far. Thanks!

---

### Post by xeth_delta on 2007-11-27
:) I'm glad I can help, don't worry about it, maybe some day.

The steps you have to take:

download the drivers from: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
You can also get the libraries and utils just to be consistent and have the latest version of them all, 1.0.15.

Unpack the three files you just got.
```
cd alsa-lib-1.0.15
./configure
make
sudo make install
```

```
cd alsa-driver-1.0.15
./configure --with-cards=atiixp-modem --with-sequencer=yes
make
sudo make install
```

```
cd alsa-utils-1.0.15
./configure
make
sudo make install
```

```
sudo alsaconf
```
Follow the instructions. Hopefully now you should also have a /etc/init.d/alsasound or /etc/init.d/alsa script you can use to restart the sound system.

Check if the modules have been loaded with **lsmod**. You should have some atiixp or the like. If not try loading the module with
```
sudo modprobe snd-atiixp
```
If there are any error messages post the output here.

Xeth

---

### Post by Roasted on 2007-11-27
After doing the ./configure --with-cards..(etc) I received this.



config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
jason@jason:~/Desktop/alsa-driver-1.0.15$ make
make dep
make[1]: Entering directory `/home/jason/Desktop/alsa-driver-1.0.15'
make[2]: Entering directory `/home/jason/Desktop/alsa-driver-1.0.15/acore'
copying file alsa-kernel/core/pcm_native.c
/home/jason/Desktop/alsa-driver-1.0.15/utils/patch-alsa: 24: patch: not found
make[2]: *** [pcm_native.c] Error 1
make[2]: Leaving directory `/home/jason/Desktop/alsa-driver-1.0.15/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/jason/Desktop/alsa-driver-1.0.15'
make: *** [include/sndversions.h] Error 2
jason@jason:~/Desktop/alsa-driver-1.0.15$ 


After running the ./configure in the utils directory...


checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
jason@jason:~/Desktop/alsa-utils-1.0.15$ 





P.S. - Just curious, how did you know that you had to add the different extensions and switches to the ./configure command under the driver section?

---

### Post by xeth_delta on 2007-11-28
This is strange.

> /home/jason/Desktop/alsa-driver-1.0.15/utils/patch-alsa: 24: patch: not found
indicates that it cannot find tnd the file utils/patch-alsa. I just downloaded the latest version of the alsa drivers, 1.0.15, and compiled without any problems with:
```
./configure --with-cards=atiixp --with-sequencer=yes
make
```

What I can suggest you is to delete the **alsa-driver-1.0.15** directory, where you were compiling, and to download and decompress a fresh driver package, just to make sure.

```
tar -xjf alsa-driver-1.0.15.tar.bz2
```

Then cd to the new directory and try again configuring and compiling.

> configure: error: this packages requires a curses library

That means that you don't have some libraries installed in your system. I did not realize they were needed for the utils, as I already had them installed for when I compiled a kernel.

Do the following:
```
aptitude search curses
```

and check that the following packages are installed: **libncurses5, libncurses5-dev, libncursesw5, libncursesw5-dev, ncurses-base, ncurses-bin**. If a package is installed it will have an "i" at the left column.

Some of them might not be needed to compile the utilities, but honestly I do not remember right now which one of them was specifically needed at this point.

After this, you should be ready to compile alsa-utils.

---

### Post by grupotux on 2007-11-28
**]Re: No sound in gutsy, Toshiba laptops]**

I posted this problem more than four weeks ago on a thread with three entries. Two more entries appeared promptly, including detailed instructions on refurbishing alsa. None worked for me, perhaps because my chipset is an older Intel 82801DB-ICH4. My last post on that thread disclosed the fact that on booting the machine the login drum-roll was clearly audible, yet once inside there was no sound.

Looking elsewhere and after many hours, I managed to get my sound card recognized (aplay -l), but still no sound.

Then roundabout success! I created new extended partitions on approximately half of my disk drive and proceeded to a fresh install of Linux Mint, which is based on gutsy. Not only does my sound work flawlessly now, but my machine is visibly faster. Other bugs, such as having to set permissions to 666 on /dev/scd0 so that K3B would ``see´´ my CD/DVD drive, also went away.

On gutsy, Firefox was slow as molasses in winter. I had taken to using Opera almost exclusively.
On Mint, Firefox works well though it is not as fast as Opera. ( I suspect it never will be,due perhaps,  to irreversible bloat. ) Further on Mint: its graphics and font rendition are superb.

My Toshiba portable is an older A10-S177. The aforementioned thread is:

[http://ubuntuforums.org/showthread.php?t=583606&highlight=gutsy+gstreamer+issue](http://ubuntuforums.org/showthread.php?t=583606&highlight=gutsy+gstreamer+issue)

For the first time ever, this Linux user (since 1994) can say that everything just works, with Mint.

Why does a gutsy-derived distribution work so well while gutsy does not? Ubuntu remains a most important project and distro, but what can possibly account for such misfortunes? ):P

---

### Post by Roasted on 2007-11-28
I've heard a little bit about this Linux Mint. Sure, it's debian based... but what IS it? Is it it's own distro? Is it just like Ubuntu where I primarily use deb files and apt-get? What about compiz fusion? Does it work in mint?

---

### Post by Roasted on 2007-11-30
I put Linux Mint on this computer. I'm having the exact same sound issues. I'm also encountering the exact same freezing issues too. Gee... how nice. 

Any input, anybody??

---

### Post by xeth_delta on 2007-11-30
Did you try  to compile the alsa drivers again? It seemed you were very close.

About the freezes, it's a different issue. What do the logs say? Is that a complete crash?

---

### Post by xeth_delta on 2007-11-30
Roasted, have you checked for possible ahrdware memory errors? You can do that by booting from the livecd. That could be a cause for the instability you are experiencing. In that situation, the linux kernel is able to exclude deffective memory addresses and work normally.

Xeth

---

### Post by Roasted on 2007-11-30
Oh, from the livecd? No, I did not do that. I did select memtest86 from the boot screen, though. I let that run for about 11 hours and I received no errors. How long would it take to run from the livecd? Or do I even need to do that since I did it from the boot menu?

It just makes me raise an eyebrow, because there's two distros, almost identical, that I've used and both yield the same freezing issues.

No, it's not a complete crash. It's more like the feeling you get running Vista on 256mb RAM. It's not that it's slow to boot, but each program can be easily frozen in which I have to force quit it. Also, when I type, what displays on the screen is always about a solid word behind what I am really typing. Even my old Sony laptop with the exact same operating system doesn't do that, and it was made about 9 years ago.

---

### Post by xeth_delta on 2007-11-30
> **Roasted said:**
> Oh, from the livecd? No, I did not do that. I did select memtest86 from the boot screen, though. I let that run for about 11 hours and I received no errors. How long would it take to run from the livecd? Or do I even need to do that since I did it from the boot menu?

It just makes me raise an eyebrow, because there's two distros, almost identical, that I've used and both yield the same freezing issues.

No, it's not a complete crash. It's more like the feeling you get running Vista on 256mb RAM. It's not that it's slow to boot, but each program can be easily frozen in which I have to force quit it. Also, when I type, what displays on the screen is always about a solid word behind what I am really typing. Even my old Sony laptop with the exact same operating system doesn't do that, and it was made about 9 years ago.

That really sounds like the processor is doing something very intensive in the background. A couple of ideas:

If you use beryl / compiz-fusion, check that you actually have 3D hardware acceleration enabled. Otherwise the CPU would be having a rather large load.

```
glxinfo | grep -i direct
```

When the system is sluggish, run a **top** from a console and see what is using that much CPU or use another system monitoring tool.

Is that happening all the time? A program called updatedb runs once a day or so to update the locate database and it can be intensive.

Try the memory test from the CD, too. If there are any serious errors they should not take long to be recognized. On an older computer of mine i found those errors in the first 20 minutes.

---

### Post by Roasted on 2007-11-30
I am running with my graphics card enabled and compuz fusion is in use. I also have a system monitor box on the lower bar of gnome. It's completely black and when the processor gets in high use I see blue spikes. I don't recall seeing any significant blue spikes on the system monitor. In fact, I recall the whole system monitor freezing whenever my computer started to freeze. Typically, on my desktop if a program lags up, the system monitor would still run and I'd see it slowly scrolling to the side. Here on the laptop, it freezes as well. 

FYI - I'm currently on Linux Mint. I'm told it's like 98% Ubuntu with the remaining 2% being greater support for wireless drivers and DVD/Audio codec support.

---

### Post by Roasted on 2007-11-30
Ran it for 30 minutes. Zero errors.

---

### Post by Roasted on 2007-12-01
Now, granted... I'm in Linux Mint now, but I just ran the drivers and whatnot for alsa, and I got back "Checking for C compiler default output file name... configure: error: C compiler cannot create executables. 

What do I doooooo? 

For the record - I'm looking around for another solid distro, perhaps something that's less troublesome for the time being. I'll always run Ubuntu on my desktop, however for my laptop I just need something that plain old works. What can I use? My only requirement is that gnome is available... I've tried Mint, Ubuntu, and Fedora. I didn't give Fedora much of a chance to really shine, as my cousin (A Linux guru) swears by it, but I'm tempted to reinstall it. Thoughts?

---

### Post by xeth_delta on 2007-12-01
You are missing the devemopment packages. Please remember to also install the other paclages I recommended also in a previous post.

```
sudo apt-get install build-essential
```

About a different distro, I really don't know what to recommend you, as I am quite please about how it works on my computer. I used for a long time RedHat 9 and Gentoo, tried a couple of times SuSE. My favourites remain nevertheless (K)ubuntu and Gentoo.

I would say that, once solved the problems you have, Ubuntu would still be very convenient. Anyway, have a look at this website for a very long list of distributions. [http://www.linux.org/dist/]("http://www.linux.org/dist/")

---

### Post by Roasted on 2007-12-01
I got 2 errors after doing the whole alsa thing at terminal. I've gotten the typical one that reads:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

Along with it, I got a second error after a fresh reboot:

No volume control GStreamer plugins and/or devices found.

And it's doing this damn sluggish thing again! Holy ****, this drives me insane. Back to Vista. :(

---

### Post by xeth_delta on 2007-12-01
Hmm, gstreamer... I think that means it is missing the gstreamer plugins.

I must admit that I am amazed at how much trouble you have on that laptop with ubuntu.

Before going back to Window$, could you please give a Kubuntu live cd a try? I know that you might want to run gnome, but I am sure we all want to know if this is something gnome specific. Kubuntu AFAIK does not depend on any gstreamer plugins.

Let us know how it goes.

---

### Post by Roasted on 2007-12-02
I shall download a Kubuntu live cd right now and give it a shot.

Good thinking, by the way. I never would have thought of that myself!! :)

---

### Post by Roasted on 2007-12-02
Aight chief. Here's the update.

I have a live cd of Kubuntu 7.10. I booted up and put an mp3 onto my jumpdrive. I know it's a fully functional file because I am listening to it on repeat as we speak on my desktop. I put it in the laptop and tried to play it. It said amarok currently cannot play mp3 files. I hit the option for "install mp3 support." Even after that, it didn't play. It prompted me again saying Amarok currently cannot play mp3 files. Install mp3 support? 

Blah...

---

### Post by xeth_delta on 2007-12-02
> **Roasted said:**
> Aight chief. Here's the update.

I have a live cd of Kubuntu 7.10. I booted up and put an mp3 onto my jumpdrive. I know it's a fully functional file because I am listening to it on repeat as we speak on my desktop. I put it in the laptop and tried to play it. It said amarok currently cannot play mp3 files. I hit the option for "install mp3 support." Even after that, it didn't play. It prompted me again saying Amarok currently cannot play mp3 files. Install mp3 support? 

Blah...

Ok, it seems you are getting closer. Amarok is a good media player, but you could try also the one I use, xmms, or one of its more up to date successors, Beep Media Player:
```
sudo aptitude install xmms
sudo aptitude install beep-media-player
```

If you wish, you can also install a lot of xmms plug-ins and also a few for beep, just search, choose and install
```
aptitude search xmms
aptitude search beep-media
aptitude search bmp
```

About the codecs, as you know, you have to install them separately, for Kubuntu you have to follow the instructions given by [http://www.kubuntu.org/doc/7.10/musicvideophotos/C/codecs.html]("http://www.kubuntu.org/doc/7.10/musicvideophotos/C/codecs.html") and in general Ubuntu  [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and [https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28restricted%29]("https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28restricted%29")

---

### Post by Sozin on 2007-12-02
I'm not sure if anyone has already suggested this, but I installed linux-backports-modules and now the sound works perfectly on my toshiba tecra, it was really quiet before.

You can find this by searching synaptic package manager for backports. the advice i got was to install this package and the ones it suggests, but none of the other backports

Good Luck :)

---

### Post by xeth_delta on 2007-12-02
I forgot to mention this. You might need to enable certain repositories if you haven't already, probably multiverse. Universe should be enabled by default anyway, IIRC. To do that with adept: Adept->Manage repositories, then Fetch updates. With synaptics: Settings->repositories, then refresh. You can also edit /etc/apt/sources.list and then **aptget update**.

---

### Post by Roasted on 2007-12-02
Multiverse is enabled.

Okay. This is starting to just go too far, in my opinion. The bottom line is, I don't have sound. The errors I get are as follows:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right gstreamer plugins installed, or that you don't have a sound card configured.

No volume control GStreamer plugins and/or devices found.

Okay. Gstreamer stuff should be installed by default, right? I even did a synaptic search of gstreamer and everything visually appeared to be installed. But then again, I'm not an expert.

SO, that leaves us with one last option if the gstreamer plugins are all installed. My sound card is not configured. How do you configure a sound card?

---

### Post by xeth_delta on 2007-12-02
Hmmm, this thread is indeed leading to no solutions, it is a pity. I think it might be a good idea to start from scratch with some fresh ideas. I have to admit I don't understand why configuring sound om your computer is so problematic. I wonder if new Toshibas have some unusual configuration (or at least less frequently met), as for your usb located wireless card.

I can continue trying to help you, if you wish.
Everytime that audio has not been working on my computer after a kernel update, I've been able to compile drivers from source. Are you now on Kubuntu?
Some gstreamer extra codecs (mp3 for instance) are not installed by default because of patent/legal issues that affect some countries. The basic things that the system needs in order to have basic sound are installed by default, and what you might need to do is compile some new drivers.

The compilation under Kubuntu did not work because you did not have the development packages installed (since many users will not develop or compile software by themselves). See one of my previous posts.

Xeth

---

### Post by Roasted on 2007-12-02
I'm in Ubuntu. I was working with Kubuntu from the livecd. I didn't do much with it after I realized that it wasn't doing what I wanted at the time.

I've enabled multiverse.
I've installed additional gstreamer codecs.
I've gotten the additional alsa drivers you suggested.

Do I need to compile the utils and library? I did the drivers to start, nothing worked. The utils and library I haven't done since the fresh install.

I'm GOING to get sound working on this damn laptop. I got this laptop to run Ubuntu, and I'll be damned if it doesn't work after all of this work I've put into it.

Thanks again for helping me. Any additional information you can give me would be great.

---

### Post by xeth_delta on 2007-12-02
Ok, no problem. I like to hear that determination :)

Please give me an update on the status of the compiled drivers. Did you manage to compile them? Please tell me what steps you followed.

---

### Post by Roasted on 2007-12-02
I compiled the driver. As I was trying to compile the library or utils, I forget which one, I got the error for requiring more of the curses modules or whatever. At the time, I had stuff I was working on with the desktop that I could not sacrifice my ethernet connection to plug into the laptop so I could obtain the curses modules. So as of now, I have the alsa driver compiled, however the utils OR library (I forget which one it is) I had an error with.

Blah. I'm in Vista now on the laptop wirelessly downloading virus and spyware scanners. Ahhh I haven't done this in years.

---

### Post by xeth_delta on 2007-12-02
Good, so the modules compiled. After installing them with "sudo make isntall" they should be under /lib...
Let's try to load them. I suppose you compiled for the atiixp card. In that case try:

```
sudo modprobe snd-atiixp
```

Post the possible errors.

---

### Post by ed67 on 2007-12-02
I don't think you're going to find a solution to this sound problem.  I fought the same problem with my Toshiba laptop in Feisty and tried these workarounds ad nauseum.  Only after a kernel update months after Feisty's release did I get sound.  I think it has something to do with the ATI sound  card and how Toshiba deals with it.

I then upgraded to Gutsy and now have the same problem, no sound.  But I'm not too put off by it, I'm just waiting for an update that fixes the issue.  I get no errors though, like I did with Feisty, there is just no sound.

Here's what I've decided:  when a new version is released, I will try the live cd before upgrading.  If the live cd has no sound, I'll wait to upgrade.

Someday hardware manufacturers will develop drivers for Linux as it gains popularity.  This will eliminate these little problems as the community struggles to make drivers work for everyone.

---

### Post by Roasted on 2007-12-02
Then realistically, if I switch to a different distro, you would think I'd have SOME chances of gaining sound. Right? 

Let me pop in my Fedora Core 8 CD... we'll see what happens. Only thing is, sometimes on livecds you don't have audio till you install certain codecs and open up repositories. Blah... Guess I won't figure out till I do a full install. 

Also, after running sudo modprobe snd-atiixp, this was the error I gott.

FATAL: Module snd-atiixp not found.

---

### Post by xeth_delta on 2007-12-02
> **Roasted said:**
> Then realistically, if I switch to a different distro, you would think I'd have SOME chances of gaining sound. Right? 

Let me pop in my Fedora Core 8 CD... we'll see what happens. Only thing is, sometimes on livecds you don't have audio till you install certain codecs and open up repositories. Blah... Guess I won't figure out till I do a full install. 

Also, after running sudo modprobe snd-atiixp, this was the error I gott.

FATAL: Module snd-atiixp not found.

That last line would indicate that the modules were not installed.
```
find /lib/modules/* | grep -i ixp
```

Ed67 might have a good point. Is Feisty an acceptable temporary alternative for you?

---

### Post by ed67 on 2007-12-02
I'm guessing since you've reinstalled Gutsy several times you're not too invested in it as far as having lots of personal files stored.

So I would suggest installing Feisty instead.  Let it go for a while in case you don't have the latest version of everything.  In other words, make sure you allow time for it to update itself even if the live cd doesn't have sound.  Sound should work (it did for me) after the updates were installed.  All these should be available immediately now.

---

### Post by xeth_delta on 2007-12-02
> **ed67 said:**
> I'm guessing since you've reinstalled Gutsy several times you're not too invested in it as far as having lots of personal files stored.

So I would suggest installing Feisty instead.  Let it go for a while in case you don't have the latest version of everything.  In other words, make sure you allow time for it to update itself even if the live cd doesn't have sound.  Sound should work (it did for me) after the updates were installed.  All these should be available immediately now.

Ed, do you know if there is anything unusual about the latest Toshibas, so that they would have these problems? I owned an ati ixp chipset based laptop before my current one. It was an HP, everything except the memory card reader worked out of the box.

Do you remember what module you were using for your sound card?

---

### Post by ed67 on 2007-12-02
> **xeth_delta said:**
> Ed, do you know if there is anything unusual about the latest Toshibas, so that they would have these problems? I owned an ati ixp chipset based laptop before my current one. It was an HP, everything except the memory card reader worked out of the box.

Do you remember what module you were using for your sound card?


I'm sorry, I can't be too much help.  I'm fairly new to Linux (Ubuntu) and am still learning as I go.  I worked very hard with the sound problem when I had Feisty installed but I don't remember many details.  There must be something unusual with Toshiba though, because this seems to be a recurring theme here in the forum.

I'm not very willing to downgrade because Gutsy seems more stable to me.  It wasn't very often but occasionally Firefox would lock me up tight in Feisty.   I narrowed it to a video driver issue but didn't get any further.  But if Roasted doesn't have that issue and is only missing sound, then that's what I'd do as a relative newcomer to make life a bit easier.

---

### Post by Roasted on 2007-12-02
Have you tried ANY other distros at all, Ed? Have you gotten any to work?

---

### Post by ed67 on 2007-12-02
> **Roasted said:**
> Have you tried ANY other distros at all, Ed? Have you gotten any to work?

No, Feisty was the first Linux I've tried.  As I said though, after the kernel update the sound did work.

---

### Post by Roasted on 2007-12-02
Is there anyway I can update the Gutsy kernel? Or is it too new to provide any available updates?

---

### Post by ed67 on 2007-12-02
> **Roasted said:**
> Is there anyway I can update the Gutsy kernel? Or is it too new to provide any available updates?

It will update automatically, but as of yet there hasn't been an update to fix the sound issue.  I have read that it's not advisable to try and downgrade to 7.04, a fresh install is best.  You can manually check for updates by going to System / Administration / Update Manager.

---

### Post by Roasted on 2007-12-02
I wonder if I'd have better luck just switching to another distro.

This is just getting ridiculous...

---

### Post by ed67 on 2007-12-02
> **Roasted said:**
> I wonder if I'd have better luck just switching to another distro.

This is just getting ridiculous...

Well, you'd be looking at a complete reinstall anyway with another distro which may or may not work.  I can't guarantee Feisty will work for you but it did for me after I updated the kernel.  That might be your best bet if you like Ubuntu otherwise.  I'm thinking over time Ubuntu and its variants will become more mainstream because they're already pretty widely accepted.

Good luck though, and I'm subscribed to this thread so if you ever find a solution that works please post it here.

---

### Post by Roasted on 2007-12-02
Ed, I've done about 30 installs in the last 4 days. Doing a fresh install of another distro won't bother me. I'm bound to hit a winner one of these times.

I just installed Mandriva 2008. Is Mandriva packaged with Gnome? I can't stand KDE, and when I went to adjust session type, I didn't see KDE. But I'm rebooting... we'll see what happens...

edit - Mandriva doesn't have gnome. Great.

Is there a gnome distro out there that's half decent that has good chances of supporting my Toshiba's sound? I really don't want to run this entirely from Vista... Yet it's looking like I'll have to.

---

### Post by xeth_delta on 2007-12-03
> **Roasted said:**
> Ed, I've done about 30 installs in the last 4 days. Doing a fresh install of another distro won't bother me. I'm bound to hit a winner one of these times.

I just installed Mandriva 2008. Is Mandriva packaged with Gnome? I can't stand KDE, and when I went to adjust session type, I didn't see KDE. But I'm rebooting... we'll see what happens...

edit - Mandriva doesn't have gnome. Great.

Is there a gnome distro out there that's half decent that has good chances of supporting my Toshiba's sound? I really don't want to run this entirely from Vista... Yet it's looking like I'll have to.

Maybe gentoo, it is source based, though. The advantage is that when it installs programs or drivers, it will compile them to your specifications. The disadvantage is that it is time consuming.

I am sorry, I have to repeat this, but from what I could see, you managed to compile the drivers but it seems to me that you did not install them.

```
./configure --with-cards=...
make
sudo make install
```
it should place them under /lib/modules/kernel-version...

Xeth

---

### Post by Roasted on 2007-12-08
Just curious, for each release of a new kernel, is there a listing of the new hardware that each kernel supports? I'd like to see with the future releases of Ubuntu kernels if they offer support for the sound card I have in the laptop. That way if I get bored of Fedora, I can put Ubuntu back on comfortably full well knowing that it is supported.

---

### Post by Yellow Pasque on 2007-12-08
> **Roasted said:**
> Just curious, for each release of a new kernel, is there a listing of the new hardware that each kernel supports? I'd like to see with the future releases of Ubuntu kernels if they offer support for the sound card I have in the laptop. That way if I get bored of Fedora, I can put Ubuntu back on comfortably full well knowing that it is supported.

Your sound card is supported right now in OSSv4. I've got the same audio chip and I know it basically works (haven't tested out anything like surround or S/PDIF because I use an add-in card). Give it a shot. It's not that hard and if you get stuck, the developers on opensound.com are very friendly and helpful.

---

### Post by Roasted on 2007-12-09
Help me out here. What is OSSv4? What is it in relation to Alsa? Is this a Ford/Chevy relationship here? Do you happen to have a how-to guide of how I can get OSSv4 working with Ubuntu Gutsy? I have no idea what it is. Do I have to disable Alsa for OSSv4 to work? Can I get OSSv4 to work in Fedora Core 8 so I don't have to reinstall to Ubuntu? 

I mean keep in mind, I run Gutsy on my desktop and love it, but I like Fedora too. If I can stick with Fedora, sweet. If not, fk it I'll go back to Ubuntu with OSSv4 if that means I have working sound!

---

### Post by ed67 on 2007-12-09
> **Roasted said:**
> Help me out here. What is OSSv4? What is it in relation to Alsa? Is this a Ford/Chevy relationship here? Do you happen to have a how-to guide of how I can get OSSv4 working with Ubuntu Gutsy? I have no idea what it is. Do I have to disable Alsa for OSSv4 to work? Can I get OSSv4 to work in Fedora Core 8 so I don't have to reinstall to Ubuntu? 

I mean keep in mind, I run Gutsy on my desktop and love it, but I like Fedora too. If I can stick with Fedora, sweet. If not, fk it I'll go back to Ubuntu with OSSv4 if that means I have working sound!

His signature line provides a link that does a nice step by step.  I tried it though and unfortunately it didn't work for me.  Not saying it won't for you, it might not hurt to try it.  I take it to be a Ford/Chevy thing but I'm a long ways from an expert in this area.

I tried a Fedora live cd last night and the sound worked for me in Fedora.  The problem is my wireless did not.  Can't have that, I'll live with no sound before no wireless.

Post here if it works for you, maybe I did something wrong.

---

### Post by Roasted on 2007-12-09
Wait... Ed... don't you have the EXACT same model laptop as me??

My wireless did not work either. However, I bought a 3Com CRUSB10075 usb wireless G adapter. After installing network manager, it recognized the wireless adapter immediately. The only thing is, it appears as if encryption isn't too great on it. So what did I do instead? I went into my linksys router settings and set it up so it only allows the USB adapter's MAC to access my WLAN. Besides that, nothing else can get on. Which works out, since my laptop is the only wireless device I have.

But anyway, back on subject. Yeah I thought you said earlier you have the exact same laptop as me. I don't understand this, then. I used the Fedora Core 8 LiveCD to install it on my laptop. Why, OH WHY, wouldn't mine work then? Were you using FC8?

---

### Post by Roasted on 2007-12-09
I reinstalled Gutsy in an attempt to get OSSv4 running. I got to the part about logging in as failsafe terminal. However, it kept telling me that the directory I was trying to CD into so I can run the sudo soundon command wasn't a directory. Yet, it was. I'm positive it was. The directions had the same exact thing and I was doing it 110% identical. Not a directory.

Pissed off, I just logged back into Ubuntu, where I encountered a series of Pidgin failures for no reason. Just... BAM. It'd shut off. What the hell? So I decided to reboot. However, rebooting didn't work. It just went to a black screen and would never reboot.

Never have I had this much trouble with Ubuntu.

Ubuntu shall remain on my desktop, but my laptop is getting a makeover with Fedora Core 8 (again). I hope OSSv4 is available for Fedora... because I couldn't get my sound working there either. But hey! At least Fedora restarted for me. :P

---

### Post by Yellow Pasque on 2007-12-10
Sorry to hear about all your Ubuntu problems.

For reference, OSSv4 is available for FC (the Ubuntu/Debian package is actually just the RPM package converted with alien)

---

### Post by Roasted on 2007-12-10
Now when you install OSSv4, do you have to install a bunch of garbage to get all components to work, such as flash videos, mpg videos, mp3s, etc? Or is it just one flat general install that'll include everything?

---

### Post by Yellow Pasque on 2007-12-10
The OSSv4 package comes with the necessary files for the sound system. You'll need packages for building software (kernel headers, C compilers, etc.) to get it installed, but it's a good idea to have those installed anyway unless you're hurting for disk space. You may also need codecs just like you would with ALSA. The only difference is that you may have to compile a file for Flash support. Directions to do that are included in the howto.

---

### Post by Roasted on 2007-12-10
I followed your directions exactly. I received no errors whatsoever. However when I ran sudo soundon, it says OSS is already loaded. Okay fine. So I clicked in the upper right corner to my volume icon that had the mute symbol on it and selected it. I was prompted with the exact same errors that I got with Alsa. 

No volume control GStreamer plugins and/or devices found. 

What else can I do?

Note - When I search GStreamer in Synaptic I have gstreamer 0.10-alsa, 0.10-esd, 0.10-gnomevfs installed. Do I need additional GStreamer plugins?


EDIT - New update. I installed java6, flash plugins, etc, just as I usually do when setting up a system. Well I went to youtube to test and make sure my flash worked and... I heard sound. What the hell?? Yes, I heard sound... Right away I heard Pearl Jam playing. However, I'm confused. When I plug in my headphones it doesn't divert the sound to the headphones output... so even with my headphones plugged in, I still hear the sound through the speakers on the laptop.

Secondly, I still have the volume icon in the upper right corner with a red X on it. When I click on it, I still yield the same error as before about no volume control gstreamer plugins and/or devices found.

This is a solid step forward. I heard sound in Linux. Fantastic. Now how can I iron it out so music goes through the headphones when plugged in as well as getting my gstreamer stuff figured out?

---

### Post by Yellow Pasque on 2007-12-10
You need to right-click the mixer icon and remove it from the panel.
Right click the empty space and select Add to Panel.
Select the button that says Custom Application Launcher.
Give it a Name (Mine's uncreatively called "Mixer")
Click the icon picture to select an icon (I used /usr/share/icons/gnome/32x32/status/stock_volume-med.png)
In the command field, type: ossxmix -d0
Click ok.
Now, click the mixer icon to control volume/output.

---

### Post by Roasted on 2007-12-10
Okay. I did. I raised all levels and made sure nothing was checked in the mute section. Still, when I open MP3s, I get this error.

Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.

:(

---

### Post by Roasted on 2007-12-12
I'm confused over something. BTW I went back to Alsa just for some more testing for the time being...

But I don't get this. If I installed the Alsa DRIVER... why wouldn't that DRIVER be functional with the chipset on my sound card? Normally I associate "driver" with the required software for making that piece of hardware functional. 

Is there some kind of ndiswrapper for sound cards?? This is nuts...

---

### Post by xeth_delta on 2007-12-12
> **Roasted said:**
> I'm confused over something. BTW I went back to Alsa just for some more testing for the time being...

But I don't get this. If I installed the Alsa DRIVER... why wouldn't that DRIVER be functional with the chipset on my sound card? Normally I associate "driver" with the required software for making that piece of hardware functional. 

Is there some kind of ndiswrapper for sound cards?? This is nuts...

I think, that probably, the way one has to see it, is that there isn't an ALSA driver, but a collection of them, intented to be used on different hardware. There are lots of different cards available, with different specifications, some of them with less information available to the FOSS developers than others, other rather new.

If you have a look at the file **alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt**, granted that's the version of the drivers you have, or at the --with-driver= option in **./configure --help**, you will see a number of cards that are suppertode by alsa through drivers and their respective drivers.

One think I am not sure you have tried is one that, truth be told, is not elegant at all, is to compile all the drivers in the package provided by alsa. There is still a possibility that somehow, the driver you've been compiling is not the one your card needs. To compile all, just issue a ./configure, make, sudo make install. It might take some time but it might also compile the driver that is actually riht for your card.

Xeth

---

### Post by Yellow Pasque on 2007-12-12
> **Roasted said:**
> Okay. I did. I raised all levels and made sure nothing was checked in the mute section. Still, when I open MP3s, I get this error.

Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.

:(
What program are you using to play audio?

---

### Post by Roasted on 2007-12-12
> **xeth_delta said:**
> I think, that probably, the way one has to see it, is that there isn't an ALSA driver, but a collection of them, intented to be used on different hardware. There are lots of different cards available, with different specifications, some of them with less information available to the FOSS developers than others, other rather new.

If you have a look at the file **alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt**, granted that's the version of the drivers you have, or at the --with-driver= option in **./configure --help**, you will see a number of cards that are suppertode by alsa through drivers and their respective drivers.

One think I am not sure you have tried is one that, truth be told, is not elegant at all, is to compile all the drivers in the package provided by alsa. There is still a possibility that somehow, the driver you've been compiling is not the one your card needs. To compile all, just issue a ./configure, make, sudo make install. It might take some time but it might also compile the driver that is actually riht for your card.

Xeth

That's what I have been doing, is the ./configure, make, sudo make install....

I'll try it again later tonight, though.


I'm using Audacious as my program. (yes I made sure it was not muted) :)

---

### Post by Roasted on 2007-12-15
I found myself over at linuxquestions.org asking the same question to see if anybody could help me. I found somebody who responded to my thread who claimed to have an answer. However, with him only having 1 post, I wasn't completely sure if I should buy into it. But I tried it... It worked! The only thing is, when I plug in headphones, my main speakers don't cut off. Therefore it basically deems the purpose of headphones useless. But anyway, at least I have functioning speakers!!

--------------------------------------------------------------------------------------------------------------------------------
From LinuxQuestions.org:

I was able to get sound working on this exact Toshiba laptop model about a month ago. I installed Linux Mint, which is based on Gutsy Gibbon, so hopefully this will work for you. This is what I remember doing: First you need a different module, which you can get as follows:

sudo apt-get install linux-backports-modules-generic

Then add the following to the end of your /etc/modprobe.d/alsa-base file:

options snd-hda-intel index=0 model=acer

(I know the laptop is a Toshiba but the acer designation in that line worked for me.)
--------------------------------------------------------------------------------------------------------------------------------


Why Acer???? I don't know... but it worked!! Now to get my headphone issue straightened out.... Anybody know what to do??

p.s. - Thanks to all that helped me during this frustration.

---

### Post by xeth_delta on 2007-12-15
> **Roasted said:**
> I found myself over at linuxquestions.org asking the same question to see if anybody could help me. I found somebody who responded to my thread who claimed to have an answer. However, with him only having 1 post, I wasn't completely sure if I should buy into it. But I tried it... It worked! The only thing is, when I plug in headphones, my main speakers don't cut off. Therefore it basically deems the purpose of headphones useless. But anyway, at least I have functioning speakers!!

--------------------------------------------------------------------------------------------------------------------------------
From LinuxQuestions.org:

I was able to get sound working on this exact Toshiba laptop model about a month ago. I installed Linux Mint, which is based on Gutsy Gibbon, so hopefully this will work for you. This is what I remember doing: First you need a different module, which you can get as follows:

sudo apt-get install linux-backports-modules-generic

Then add the following to the end of your /etc/modprobe.d/alsa-base file:

options snd-hda-intel index=0 model=acer

(I know the laptop is a Toshiba but the acer designation in that line worked for me.)
--------------------------------------------------------------------------------------------------------------------------------


Why Acer???? I don't know... but it worked!! Now to get my headphone issue straightened out.... Anybody know what to do??

p.s. - Thanks to all that helped me during this frustration.

Great news, and indeed strange that you have to configure the sound for an Acer computer. I wonder how he found out. I notice you are now also using the hda-intel module, not the ati.

On an old HP of mine (again, using KDE), I used to have a switch in the volume control / mixer window that would allow me to choose between having both, headphones and speakers working, or only headphones, when they were connected.
Maybe you have something like that, too in gnome.

What hapened with the wireless card? Is it working, too?

Xeth

---

### Post by Roasted on 2007-12-15
I just got a 3Com CRUSB10075 USB Wireless G Adapter that was fully tested with Ubuntu. It works great. Only thing is, I cannot seem to get encryption to work. So to get around it I just set my router settings to only permit my MAC address on the network. So now nobody can get in wirelessly unless they spoof my mac address... which considering all of my neighbors aren't computer users (I live around some older folks) I doubt that it's going to be an issue at all. Plus my security instructor at college told me that being able to get encryption to work overtop of the wireless mac filtering would simply be a "small bonus."

Anyway, the guy on the other forums explained to me he read on a thread somewhere here, actually, on Ubuntuforums that there's 3 or 4 module settings. Something like, Acer, Auto, Toshiba, and Stack3. He said he just tried each one until he found one that worked. 

So I'm kind of confused. I don't know if it's an Acer product, or if it's just some kind of a module that is codenamed "Acer" that happens to work for me. I don't know! Hahaha. 

I tried looking for separate output controls for speakers vs headphones and I didn't seem to find any. All I'm using is the basic volume control thing that docks in the upper right by my clock (gnome). Is there something else, a more advanced control system I can install? Or should the option I need be included in what I already have here? It's simply called "Volume Control" when I right click - add to panel.

---

### Post by xeth_delta on 2007-12-15
Off topic. I agree with you, that MAC filtering should not allow others to use your router, but as it is, your connection is rather unsecure, as communication between the router and your computer could be easily intercepted. As an advice, I would not send any critical or important data over wireless until getting encryption working.

This should certainly go on your wireless related thread, but anyway... Are you using regular drivers or ndiswrapper on the 3comm card? I would really recommend you wicd as a wireless configuration GUI. You can find it on [www.sourceforge,net]("www.sourceforge,net"). If you want to give it a try, remeber to put the password/passphrase between quotes.

Xeth

---

### Post by Roasted on 2007-12-15
I'm not using ndiswrapper. I just opened up network manager and bam, I was connected.

What kind of information do you mean? I play a couple online games on the laptop and youtube a bunch of stuff, but that's about it.

I have online banking, though. Are you referring to using only my desktop to log into my account? Is there any way that you know of to get encryption working? I simply encrypted my network and my laptop wouldn't connect. I put in the exact passphrase and it just came back prompting me again for it. Is there anything else I can do? 

P.S. - Do you know anything about what he spoke about? Telling me that there's Acer, Toshiba, Auto and Stack3, and choosing Acer worked? I wonder what in the world those mean...

---

### Post by xeth_delta on 2007-12-15
> **Roasted said:**
> I'm not using ndiswrapper. I just opened up network manager and bam, I was connected.

What kind of information do you mean? I play a couple online games on the laptop and youtube a bunch of stuff, but that's about it.

I have online banking, though. Are you referring to using only my desktop to log into my account? Is there any way that you know of to get encryption working? I simply encrypted my network and my laptop wouldn't connect. I put in the exact passphrase and it just came back prompting me again for it. Is there anything else I can do? 

P.S. - Do you know anything about what he spoke about? Telling me that there's Acer, Toshiba, Auto and Stack3, and choosing Acer worked? I wonder what in the world those mean...

Yes, I meant critical information transferred on online banking or online shopping. Should not access these things in an unsecured wireless network, just as a precaution. Games and youtube, that's a different matter.

What kind of encryption did you try to use, WEP, WPA1/2? I did not manage to connect to an encrypted network with the standard KDE network manager, so I used wicd. It also seems to be working from the command line.

About the options in the /etc/modprobe.d/alsa-base file, Pitifully I don't know much about them. They seem to specify how the driver interacts with the hardware. You can read on these settings on **alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt**
I had to use an option, too for my Macbook:  **options snd-hda-intel model=5**. With some other mode values I remember to always have some crackling noise on the left channel.

Xeth

---

### Post by Roasted on 2007-12-15
I'm going to continue the wireless discussion in my wireless thread.

Until then, anybody have any idea how to get my sound sorted out? Sound works great, it just doesn't cut off when I plug headphones in. On top of that, I may be imagining that, but my sound levels in vista seem a tad higher. Is that possible?

---

### Post by ed67 on 2007-12-15
> **Roasted said:**
> I found myself over at linuxquestions.org asking the same question to see if anybody could help me. I found somebody who responded to my thread who claimed to have an answer. However, with him only having 1 post, I wasn't completely sure if I should buy into it. But I tried it... It worked! The only thing is, when I plug in headphones, my main speakers don't cut off. Therefore it basically deems the purpose of headphones useless. But anyway, at least I have functioning speakers!!

--------------------------------------------------------------------------------------------------------------------------------
From LinuxQuestions.org:

I was able to get sound working on this exact Toshiba laptop model about a month ago. I installed Linux Mint, which is based on Gutsy Gibbon, so hopefully this will work for you. This is what I remember doing: First you need a different module, which you can get as follows:

sudo apt-get install linux-backports-modules-generic

Then add the following to the end of your /etc/modprobe.d/alsa-base file:

options snd-hda-intel index=0 model=acer

(I know the laptop is a Toshiba but the acer designation in that line worked for me.)
--------------------------------------------------------------------------------------------------------------------------------


Why Acer???? I don't know... but it worked!! Now to get my headphone issue straightened out.... Anybody know what to do??

p.s. - Thanks to all that helped me during this frustration.


YES!!

Roasted, you are a god!  This worked for me too and I'm loving it.  I had done a clean wipe of my hard drive and reinstalled Gutsy, nuked Win XP, but still no sound.  Until now!  Now I have everything I need and won't be reinstalling windows because I can vpn to my desktop any time I need Windows.

This is awesome, thanks for keeping after this problem and most of all for posting your findings.  I appreciate it.

Eric

---

### Post by Roasted on 2007-12-15
Hahaha, I'm hardly a God by any means. I'm just a stubborn S.O.B. that refuses to give up on issues like this.

I'm glad to hear that it worked for you. I wonder how the original guy figured this out? It seems like such a strange thing to just randomly try and then.. bam. It works? Either way, it's nice that it's working! Yet, with me being that stubborn S.O.B., I like to know WHAT exactly happened to make it work! haha. 

Do you have the headphone issue to, where your speakers don't shut off if you plug in headphones? Are you also running the same model laptop (A215-S7422) that I am??

I also have to wonder... I was running Fedora Core 8 for a short time and had no sound as well... I wonder if this would have fixed my Fedora issue?

---

### Post by ed67 on 2007-12-15
> **Roasted said:**
> Hahaha, I'm hardly a God by any means. I'm just a stubborn S.O.B. that refuses to give up on issues like this.

I'm glad to hear that it worked for you. I wonder how the original guy figured this out? It seems like such a strange thing to just randomly try and then.. bam. It works? Either way, it's nice that it's working! Yet, with me being that stubborn S.O.B., I like to know WHAT exactly happened to make it work! haha. 

Do you have the headphone issue to, where your speakers don't shut off if you plug in headphones? Are you also running the same model laptop (A215-S7422) that I am??


Yeah I have no idea why that would work.  I don't use headphones at all on my laptop but I plugged in my ipod ones just to check for you and no, they worked fine.  Sound came out the headphones and not the laptop speakers.  The volume appeared to control the headphones just like the regular speakers.

I have no advice at all but what about trying those other two or three options you mentioned from that other forum?  Besides acer there were a couple other choices....maybe one of those would fix it for you.  You could always change it back to acer.

Just a thought.  Post it here though if you find the answer.

I bet it would have fixed the Fedora problem.  I tried Fedora 8 and then 7 and had sound in both.  My problem with Fedora was I had no wireless.  Seems that it didn't support WPA-Personal.  I didn't mess around with it much though, other than to determine that other people also had that issue with it.  For now though I'm all Gutsy until I get the itch to try something new which seems to happen to me pretty often.  It's why I run into these little problems too.

---

### Post by Pgi947 on 2007-12-15
Tried the acer trick, no joy here, similar ATi HD audio device here on an older Toshiba (would you believe) Equium A100.

Been exhausting my self for the last 10 hours trying to find a solution, I'm baffled.

Last 2 Ubuntu Distro's i used, 6.04 and 6.10 BOTH utilised this laptops sound card flawlessly.... 

About the wireless....I remember back in 6.10, it wouldn't detect my wireless (atheros card) so I just set the wireless adaptors name to "ath0" and it worked perfectly, it also auto-detected fine in 7.10 and works fine too, although I seem to have lost a little range...

---

### Post by Roasted on 2007-12-16
> **ed67 said:**
> Yeah I have no idea why that would work.  I don't use headphones at all on my laptop but I plugged in my ipod ones just to check for you and no, they worked fine.  Sound came out the headphones and not the laptop speakers.  The volume appeared to control the headphones just like the regular speakers.

I have no advice at all but what about trying those other two or three options you mentioned from that other forum?  Besides acer there were a couple other choices....maybe one of those would fix it for you.  You could always change it back to acer.

Just a thought.  Post it here though if you find the answer.

I bet it would have fixed the Fedora problem.  I tried Fedora 8 and then 7 and had sound in both.  My problem with Fedora was I had no wireless.  Seems that it didn't support WPA-Personal.  I didn't mess around with it much though, other than to determine that other people also had that issue with it.  For now though I'm all Gutsy until I get the itch to try something new which seems to happen to me pretty often.  It's why I run into these little problems too.

Now wait... you have the EXACT same model laptop as me? A215-S7422?? And your sound works fine and mine doesn't with the exact same damn driver? Are you kidding me? Are you using the regular sound volume controller that you get from the top panel when you click "add to panel?" There has to be an additional setting somewhere where Ic an mute speakers yet let the headphone jack push sound. Maybe you have something I don't? Any input?

---

### Post by Roasted on 2007-12-16
> **Pgi947 said:**
> Tried the acer trick, no joy here, similar ATi HD audio device here on an older Toshiba (would you believe) Equium A100.

Been exhausting my self for the last 10 hours trying to find a solution, I'm baffled.

Last 2 Ubuntu Distro's i used, 6.04 and 6.10 BOTH utilised this laptops sound card flawlessly.... 

About the wireless....I remember back in 6.10, it wouldn't detect my wireless (atheros card) so I just set the wireless adaptors name to "ath0" and it worked perfectly, it also auto-detected fine in 7.10 and works fine too, although I seem to have lost a little range...

What's this? You got your wireless working in Gutsy and you have less range now? Are you sure? My range bars bounce quite a bit even when I'm not really moving at all. It just sits on my desk and it'll bounce a good ways, yet never loses connection. Is that the thing you're talking about? 

P.S. - I don't think there's an ATI sound card in my Toshiba. I remember it being Realtek High Definition Audio (I believe). Maybe that's why it didn't work for you. 

Tomorrow when I have more time I'll try googling around and see if I can find anything that would help ya.

---

### Post by Pgi947 on 2007-12-16
Yeah I'm fairly sure (from using XP) that my audio device is realTEK HD audio, not ATi.

By less range I mean, in XP I can sit where i am now (about 2ft from my router) and get 9x%, but in gutsy In the same place I'm getting about 75%.  Strange, think its to do with the driver, I remember using the standard XP driver for my wireless and getting low range, then installing the official driver and getting excellent range.

I'm going to look into installing some realTEK drivers if I can get my hands on them, do I need to uninstall the 'ATi' audio drivers first?

---

### Post by ed67 on 2007-12-16
> **Roasted said:**
> Now wait... you have the EXACT same model laptop as me? A215-S7422?? And your sound works fine and mine doesn't with the exact same damn driver? Are you kidding me? Are you using the regular sound volume controller that you get from the top panel when you click "add to panel?" There has to be an additional setting somewhere where Ic an mute speakers yet let the headphone jack push sound. Maybe you have something I don't? Any input?


No I don't have that exact model.  Mine says A105-S2101 on the back.  I got it at Wal-Mart a little over a year ago.

That's the volume control I use, the one from "add to panel".  I'm pretty sure my sound is an ATI but I think I read in one of your posts that yours is RealTek.  I have run across this problem in the forums here though while trying to get sound.  Since I don't use headphones I never read into it much so I can't be much help.

I'm betting there's a solution like you found to get sound in the first place though.  Did you try using one of the other options besides acer?

---

### Post by Pgi947 on 2007-12-16
I'm just about to try and install the official realtek HD audio device driver for linux now, I shall report back once its installed :-)

---

### Post by Pgi947 on 2007-12-16
Installed flawlessly, still no sound at all though, for some messed up reason though in my task bar where the volume control should be, if I put my curser over the speaker icon it says 'Microphone'!
  I have no microphone installed, is it possible the driver is confusing line in with line out?

Also if I go into the properties of the 'microphone' Under File>Change Device I have these 2 options...

0 - HD ATi SB (Alsa Mixer)
1 - Realtek ALC861 (OSS Mixer)

No matter which option I select I still get no audio :-(

---

### Post by Roasted on 2007-12-17
That's strange. Why in the world would the official realtek driver not yield any positive results?

Update:

I've tried all 4 of the options in place of the original "acer" as instructed earlier. There's Acer, Toshiba, auto, and stack3.

Auto - No output.
Stack3 - No output.
Acer - Sound works, but when headphones are plugged in, main speakers do not shut off. However, sound is still heard through headphones.
Toshiba - Sound works, but when headphones are plugged in, main speakers mute, yet no output is heard in headphones. If the volume is adjusted during this, the main speakers will unmute and you will hear the output through main speakers by whatever volume range you have just selected. Yet, still no output out of headphones.

This is depressing, because I wanted to load a ton of music on this thing. My Vista partition is so small it only has 6 gig left. It's almost making me consider resizing my partitions so I can at least have my huge music library on the laptop and the ability to listen through headphones with it. 

Oh well, I'll hold off a little while longer. If not, maybe I will bring this laptop back to Vista and just keep the desktop as my Linux machine. After all, I didn't really have to pay extra for Vista... so it's not like I bit the corporate buttcheek to dish out 300 bucks to use an OS.

---

### Post by mlucian72 on 2007-12-17
I don't know if this will help, but it helped me. I'm using Linux Mint, but it should work for Ubuntu as well.
 Do a clean install, then upgrade the repositories, just the ubuntu supported ones, then upgrade the Alsa Driver to 1.0.15. Here is the link : [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)
 Just follow the instructions at the link above.
After you installed the new Alsa driver, edit "alsa-basa" in /etc/modprobe.d and add this line all the way at the end:
 options snd-hda-intel model=toshiba
 Restart computer. Sound should work fine. If not, try model=auto instead.
 After you have the sound working, install the restricted driver for your video card, and then the wireless driver.
 This got my laptop working, a Toshiba A215-S7437.

  Hope this helps.

---

### Post by mlucian72 on 2007-12-17
Sorry for the typo...is "alsa-base" in /etc/modprobe.d/

---

### Post by Roasted on 2007-12-17
mlucian - Can you please do a test for me? While you are playing a music file, plug in headphones. Do your headphones have music coming out of them? Do the main speakers shut off right after headphones are plugged in, or do they simply mute? The problem I'm having is I'll have music output, but once I plug in headphones the main speakers don't shut off. This is under the acer option. If I use the toshiba option, they simply mute, and no music is heard through headphones.

But if you can just plug in headphones while you are listening to music and tell me what the result is. That'd be a huge help... I really don't want to format the entire computer and put Vista as my main OS on the bigger partition. But it's at the point where I need to if I want my music library handy to listen to in lab at school.

---

### Post by Pgi947 on 2007-12-17
I'm going to give it a try tonight, and see what happens, I hope it succeeds, but I NEED audio (especially via headphones) due to the 6 hour train journey I have on sat.

If I get no joy I'm affraid XP is going to have to be put back on....at least until this bizzar issue is sorted.

I'm also going to boot ubuntu 6.10 via live disc and test the sound in that, I'm 99% sure the last time I had it on it worked perfect, so if someone can tell me how to find out the exact driver etc... used in 6.10 it may be helpful? As I should be able to replicate the driver on 7.10...

I don't want windoze but thats the way things are looking :-(

Also when i hit up alsamixer, under the 'Master' column it says "00" and am unable to adjust...

---

### Post by Roasted on 2007-12-17
I don't understand why if certain pieces of hardware work in previous versions of linux that they wouldn't work in future versions. I would think that if you have kernel 1.5 (for example) and a new version comes out that uses an updated kernel, that it would be kernel 1.5 and then some... you know, you take the old kernel and ADD new things which build up to kernel 2.0, for example.

And quite frankly, Windows isn't THAT bad. You can't ignore that it's a functional operating system, even if you're like me who loves linux. I've just come to accept that linux, for the time being, is more of a solid desktop operating system, I guess. I love seeing my big beefy computer at home boot up to Ubuntu. Yet my portable laptop, to me, makes sense to have windows on it, especially since I'm in school now and I have some school (windows only) applications on it.

So yeah, I'll always dual boot, but for the time being vista may be my primary OS if the sound/headphone issue cannot be sorted out. In fact, if I don't get a response on here within the next hour, I'm going to just format it and spend my day in the lab here in class formatting things the way I want them.

---

### Post by Pgi947 on 2007-12-17
Well I re-installed, just trying some new tricks out with adding more option lines to /etc/module.d/alsa-base and seeing what I get. I have to admit, I've used every Ubuntu desktop since 6.04, loved them all, apart from this, some MAJOR improvements, like auto-detecting the wireless, no more messing about with X etc...yet the simple things are letting 7.10 down, a major over-haul is needed IMO, firstly the spash resolution mess up, causing a large number of people to experience 5 mins boot times into the OS, and secondly this sound issue,  I'm seeing people all over the place having issues, either getting no sound, or not getting sound via headphones.

I always say if somethings not broke don't fix it, seems someone is yet to take that advice on-board :-(

Last try for me and then XP is going back on for the foreseeable future (probably till the next release)

---

### Post by Pgi947 on 2007-12-17
Ok I'm not sure if this is progress or not...

Before i added this line: options snd-hda-intel model=3stack to /etc/modprobe.d/alsa-base I had 3 options when i hit up Alsamixer which were....

Master | PCM |Microphone | 2 other inoperable options

Now I strangely get the following (i think this may help the Headphone issue?)

Headphone | PCM | Front | Front Mi | Surround | Center | LFE | Line

Now as default Headphone is set to '00' PCM too '100' and Line too '100' and all others '00'

The thing I'm noticing the MOST messed up, is the speaker icon in my desk tray says 'Microphone' and 'Line-IN'
  I have no mic, nor anything plugged into my line in, now if alsa thinks my line-out is my line-in this might be the problem in the first place!

I think im going to upgrade to the latest version of alsa, currently running default gutsy 1.0.14, and I believe release candidates of 1.0.15 are available.

---

### Post by Roasted on 2007-12-17
I was running the latest alsa drivers.

I'm just setting up my laptop now. 115 gig Vista, 12 gig Ubuntu root, 20 gig Ubuntu home.... using Vista as my primary.

I love Ubuntu. It's great on my desktop. But it just sucks for support on my laptop, so I'll keep my laptop as my windows machine for the time being.

I'll see how the next release goes.

---

### Post by Pgi947 on 2007-12-18
Yeah, I'm going to wait up for the next release, either that or a big update for gutsy, back on my custom XP setup, only a 40gb HDD on my laptop so I don't have room to play with a dual boot...

Its a shame really, I was looking forward to moving to ubuntu full time for my laptop, I'd move the same for my desktop but I need a reliable Media server...

---

### Post by ed67 on 2007-12-18
It would be really nice if there was a site that could analyze your hardware and tell you what would work and not work.  In the mean time we can use the live cd's to test new releases before committing to install them.  That is a very nice deal, but a quicker check via website would be good.

I'm getting along fine now thanks to Roasted but I sympathize because I've fought this sound issue almost constantly while using Ubuntu.  If I ever get a new laptop I'll try to make sure it's Intel based with an Intel sound card, which I think would be better supported.

---

### Post by xeth_delta on 2007-12-18
> **ed67 said:**
> It would be really nice if there was a site that could analyze your hardware and tell you what would work and not work.  In the mean time we can use the live cd's to test new releases before committing to install them.  That is a very nice deal, but a quicker check via website would be good.

I'm getting along fine now thanks to Roasted but I sympathize because I've fought this sound issue almost constantly while using Ubuntu.  If I ever get a new laptop I'll try to make sure it's Intel based with an Intel sound card, which I think would be better supported.

Does this link help: [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

---

### Post by ed67 on 2007-12-18
> **xeth_delta said:**
> Does this link help: [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

It does help.  Thank you for pointing it out.  It's not quite what I was thinking about but it is a good resource.

---

### Post by Pgi947 on 2007-12-19
It is indeed a good resource, still fails to explain why in a previous ubuntu release the sound works fine....

Oh well i'll just sit tight for now and hope for the best :-)

---

### Post by Roasted on 2007-12-27
No more input about sound and Ubuntu? Vista is beginning to piss me off... to the point where I'm going to locate a copy of xp and throw it on... if only ubuntu just fking worked... :(

---

### Post by xeth_delta on 2007-12-27
> **Roasted said:**
> No more input about sound and Ubuntu? Vista is beginning to piss me off... to the point where I'm going to locate a copy of xp and throw it on... if only ubuntu just fking worked... :(

Hi Roasted! I thought you already got basic sound working and only had problems with the microphone. I might be confused, of course... :)

Xeth

---

### Post by Roasted on 2007-12-28
I did get sound working, but if my headphones aren't working it serves little purpose to me seeing as though I use my headphones in lab during class at college.

It sounds as if the wireless problem is solved. Some people have reported the wireless chipset proving to work. Okay, fine. But until I get my sound working, which seems to be the biggest issue at hand, then I'll tackle the wireless and hopefully have a working system.

---

### Post by KoolBeans on 2008-01-07
No sound.

---

### Post by KoolBeans on 2008-01-08
I found the drivers for the Realtek HD Audio. Linux versions available. The downloads are a little slow.

[Linux 2.4/2.6 Realtek Drivers for Toshiba Satellite A215](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

I am not a coder, but this method was suggested to me for manual method:

If you can't install the propriatory driver from the ubuntu sources you can alternatively grab the driver from the manufacturers site. For example for NVIDIA cards go to:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

this will give you a NVIDIAXXX.run file.

[color=red]Caution:[/color] _GDM_ refers to Gnome Display Manager. Which is specific to video. The code for the audio manager may be different.

Place this on your Desktop and goto the command line (crtl + alt + F1).
Kill GDM by typing:

```
sudo killall gdm
```

Change directories to your Desktop:

```
cd /home/YOURNAME/Desktop
```

Start installer by typing:

```
sudo sh NVIDIAXXX.run
```

This should launch the installer, if the installer gives you and error about headers you will need to install the Linuxheaders and buildessetial packages: ```
sudo aptitude search headers / buildessential
``` look for the right package and install them ```
sudo aptitude install PACKAGE NAMES
```
Now reload installer

```
sudo sh NVIDIAXXX.run
```

This will make a custom kernel module (driver), once it is finished reload GDM by typing sudo gdm

I cut and pasted this from[UbuntuForums thread post#28](http://ubuntuforums.org/showthread.php?t=624916&page=3)

---

### Post by Roasted on 2008-01-09
I just found this.

Anybody want to confirm that it works before I go through the hell of reinstalling Ubuntu again just to be disappointed?

[http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10](http://collin.moerman.googlepages.com/toshiba_ubuntu_7.10)

---

### Post by KoolBeans on 2008-01-10
I followed the information in the link in this manner.
I don't use wireless, so I don't know if it is working.
I loaded the shell script for the audio into the text editor to see it as opposed to saving to disk.
Then I copy and pasted each line one at a time so I could see what occured.

I learned that the process is: download, extract, compile, install.
Download=ftp,http; extract=tar xjf; compile=make; install compiled=make install

sudo reboot

Then I input the folowing code into terminal: cat /proc/asound/card0/codec#* | grep Codec

It returned this result: cat: /proc/asound/card0/codec#*: No such file or directory

Previous to the procedure I input the code: cat /proc/asound/card0/codec#* | grep Codec

and it returned the result: generic ffff68xffff-(not exact)

options snd-hda-intel model=auto is not in the location "/etc/modprobe.d/alsa-base"

These are the options that I do have after the above procedure:

options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Thanks for the pointer to the addy, it was an enlightening process.
The mysterious process of compiling your own drivers, compiling being a big word to the uneducated linux nOOb, is a process which is accomplished by the os via a code that tells the os what to compile. It is not as difficult as some linux-mongers would lead you to believe.

---

### Post by Roasted on 2008-01-14
Anymore updates? Any of you folks out there have 100% success with sound (or wireless, for that matter) yet?

---

### Post by Yellow Pasque on 2008-01-14
I think you had 100% success when you tried OSS4. From reading through the thread, it appears you just forgot to change the output plugin in your mp3 player.

---

### Post by Roasted on 2008-01-14
> **Temüjin said:**
> I think you had 100% success when you tried OSS4. From reading through the thread, it appears you just forgot to change the output plugin in your mp3 player.

I changed everything imaginable. But still, when I'd plug in my headphones, my main speakers wouldn't shut off.

It's really sad that an operating system can be deemed "useless" just by a simple thing. But it's the truth... this laptop is my music box for lab work, which it's basically a quiet atmosphere like a library.

I'll give it another shot, but I'm nearly positive I checked everything possible and nothing else worked.

---

### Post by mugiwara on 2008-01-19
I have a Toshiba A215-7444...

Sound: Since overall sounds seems to work for you I'll focus on the headphones. I had problems at the beginning but it works now, **I can use the headphones but not automatically**. It works for me this way:

I can control the headphone volume by right clicking the volume icon on the panel and selecting open volume control, then in the menu: select change device, the options I have are the following:

0: HDA ATI SB (ALSA mixer) - This controls the outer speakers (via the front channel)
1: Realtek ALC268 (OSS mixer) - This controls the headphones for me (via PCM-2)

No matter which one I select the volume knob on the front always controls the outer speakers. So I just mute them with the knob and select option #1 above to control the headphone volume with the control in the panel.

Not the most elegant solution but works for me. In **debian lenny** the speakers do mute when you connect the headphones (using the same alsa release) but I kept having kernel panics. The volume knob didn't work either...so I switched to ubuntu and found that overall support for this laptop is better...

-----------------------------------------------
Wireless works (atheros chipset in my model) compiling madwifi from svn

In general you might find the following link useful (it was for me)

[http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/](http://www.datanorth.net/~cuervo/blog/linux-on-the-satellite-a215-s7407/)

---

### Post by Roasted on 2008-01-19
Blah. I'm still using XP. Nothing wrong with XP, but I miss my Ubuntu roots. I'm not always at my desktop to enjoy it. :( 

Come on Hardy... I'm counting on you!!

---

### Post by HandyAndyShortStack on 2008-03-24
I just tried a Hardy Beta live cd on my a215 toshiba laptop.  My sound issues were gone.  I could use headphones and the volume wheel without any tinkering.  The modified wireless driver workaround doesn't work like it used to though, and the rtl8187b is still not native:(
There is hope!  Try Hardy!

---

### Post by Folk Theory on 2008-03-31
I seem to have the same exact computer and same exact problem. i also get the same output from  lsmod | grep -i snd

ok and then there is this: 
sudo /etc/init.d/alsasound restart
sudo: /etc/init.d/alsasound: command not found

And:
 sudo /etc/init.d/alsa restart
sudo: /etc/init.d/alsa: command not found

so it's not clear how Roaster fixed his (if he did)
please help me.

---

### Post by xeth_delta on 2008-04-01
> **Folk Theory said:**
> I seem to have the same exact computer and same exact problem. i also get the same output from  lsmod | grep -i snd

ok and then there is this: 
sudo /etc/init.d/alsasound restart
sudo: /etc/init.d/alsasound: command not found

And:
 sudo /etc/init.d/alsa restart
sudo: /etc/init.d/alsa: command not found

so it's not clear how Roaster fixed his (if he did)
please help me.

Ok, let's see if the modules are loaded:
```
lsmod | grep snd
```
and if the card is claimed by the driver
```
lshw -C sound
```
Also let's see what codec is being used:
```
cat /proc/asound/card0/codec#0 | grep -i codec
```

---

### Post by Folk Theory on 2008-04-01
thanks everyone but i solved this using this great thread: 
[HOW TO: Toshiba Satellite A215 S5818]("http://ubuntuforums.org/showthread.php?p=4631944#post4631944")

now i'm only missing the wireless...

---

### Post by xeth_delta on 2008-04-02
Great to know it's working now and for linkink to that thread. That ought to help many other stranded users.

---

### Post by sduden on 2008-04-19
I know it's a little late, and not the exact same model as the OP was posting about, but...
For my Toshiba Satellite A215-S6804, I was having pretty much identical issues.  Googling brought up mostly the OP's threads looking for help, and I don't recall seeing this solution elsewhere.

The 'acer' model was giving me the sound through both headphone jack and my laptop's speakers, the 'toshiba' model was muting both whenever I would plug headphones in.

When I looked at the source for alsa, hda-intel had a couple models not listed for ALC268 (the sound chip that comes with this model), dell and zepto.  'dell' was the first of the two I tried, and the headphone jack seems to be working as expected.  When I plug the headset in, they produce sound, the laptop speakers shut off.

I just am afraid I can't guarantee it would work for the OP's model of laptop.


edit: Sorry, forgot to mention: I'm using Hardy on amd64, although I really doubt this would matter so long as your alsa version is the same (1.0.16)

---

