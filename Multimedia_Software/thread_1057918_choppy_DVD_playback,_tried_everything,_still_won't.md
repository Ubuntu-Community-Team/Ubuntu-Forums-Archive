---
title: "choppy DVD playback, tried everything, still won't work"
date: 2009-02-02
forum: Multimedia Software
---

### Post by spookymulder on 2009-02-02
hey all

i've been reading these forums for a while avoiding asking a question that appears to be ubiquitous. but the truth is none of the answers seem to make a difference in my case! so i finally registered...

i have an hp laptop (AMD Turion 64, nvidia).. originally equipped with Vista it had a bad hard drive and they gave me a new one but requested that i repurchase Windows. unwilling to pay, i got ubuntu. following advice in this forum i got the dvd player (VLC and Totem) to work but the playback is still choppy.

here's what bothers me:

typing "sudo hdparm -d1 /dev/hdc" in the terminal results in the following message

sudo hdparm -d1 /dev/hdc no such directory

what am I doing wrong? dma seems to be enabled... i don't know what else to do! please help.

thanks, spooky

---

### Post by redroad55 on 2009-02-02
I have used this guide many times and it has worked without fail except for a few operator errors ..> Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts.
you have to have disk in before your given the choice .. Sorry if you've tried this option already but you haven't listed what you have tried..give this guide a good read and double check your steps..
Post back with results and or questions..Best to you..
[http://http://ubuntuforums.org/showthread.php?t=766683]("http://http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by spookymulder on 2009-02-02
I have to have a DVD in before what choice? sorry, I'm new to this! oh, and with Turion 64 I have to install the 64 bit Ubuntu package, right? i know, i sound like a total noob... I am. Thanks...

---

### Post by mc4man on 2009-02-02
hdparm doesn't really do much anymore, dma should be enabled by default. If you wanted to ck. it's
sudo hdparm -i <device> (most likely /dev/scd0, so sudo hdparm -i /dev/scd0

This will give you the /dev's of your drive

```
sudo lshw -C disk
```

You could try turning off visual effects in System -> Preferences -> Appearances if they're enabled.

Otherwise you could try setting the video output to X11 in the settings of vlc or system wide for totem (Multimedia Systems Selector in System -> Preferences (may not be present by default, if not go alacarte in terminal
For vlc how you change the video output depends on whether your using 0.8.6 or 0.9.x ...?

> i have an hp laptop (AMD Turion 64, nvidia).. originally equipped with Vista it had a bad hard drive and they gave me a new one but requested that i repurchase Windows


Are you saying hp was unwilling to give you a means to restore the Os that shipped with pc at no cost?
Was the drive still under warranty or did you have to purchase it?

edit: do you have restricted drivers installed (or available)? System -> Admin.. -> hardware drivers

---

### Post by spookymulder on 2009-02-02
> hdparm doesn't really do much anymore, dma should be enabled by default. If you wanted to ck. it's
sudo hdparm -i <device> (most likely /dev/scd0, so sudo hdparm -i /dev/scd0

This will give you the /dev's of your drive

```
sudo lshw -C disk
```

This is what it gave me

Model=TSSTcorpCD/DVDW TS-L632M                , FwRev=0917    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 AdvancedPM=no

 * signifies the current active mode

> You could try turning off visual effects in System -> Preferences -> Appearances if they're enabled.

Otherwise you could try setting the video output to X11 in the settings of vlc or system wide for totem (Multimedia Systems Selector in System -> Preferences (may not be present by default, if not go alacarte in terminal
For vlc how you change the video output depends on whether your using 0.8.6 or 0.9.x ...?

Turning off visual effects did nothing. Multimedia Systems Selector not present by default... how do I go "alacarte"? (sorry, total noob)



> Are you saying hp was unwilling to give you a means to restore the Os that shipped with pc at no cost?
Was the drive still under warranty or did you have to purchase it?

edit: do you have restricted drivers installed (or available)? System -> Admin.. -> hardware drivers

Indeed they were going to charge me $50... not that it was going to break me, but it really turned me off. The drive was under warranty. The fact that I pretty much hated Vista didn't help. So when I found out that Open Office was word compatible (every week I have to submit word compatible reports to my superiors) I decided to give Ubuntu a try. I got the flash to work flawlessly for youtube, smooth DVD playback really is the only thing I am missing.

---

### Post by redroad55 on 2009-02-02
> I have to have a DVD in before what choice? sorry, I'm new to this! oh, and with Turion 64 I have to install the 64 bit Ubuntu package, right? in know, i sound like a total noob... I am. Thanks...
If you are playing video in VLC
> Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts
the deinterlacing tab won't appear until dvd is in player .. Post back with results and or questions .. Best to you..
> oh, and with Turion 64 I have to install the 64 bit Ubuntu package, right?

If you installed the 64 bit OS than yes

---

### Post by spookymulder on 2009-02-02
enabled it with DVD playing, nothing changed, still jerky playback...

in the meantime, i followed the instructions in this link ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)), and installed the 64 package (for my Turion 64, right?) for ubuntu... halfway through it gave me this java message, something about some agreement, i couldn't click ok or do anything, so i reopened the terminal and now when i try to reinstall the 64 package it's telling me:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

what gives? :(



PS: i ran the above command (sudo dpkg --configure -a), and it said

Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...


I then tried installing the 64-bit package from the above link again, and it said

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
....................................................................................................................(I'm not listing them)
                 Recommends: gsfonts-x11 but it is not going to be installed
  vlc-nox: Depends: libavcodec51 (>= 3:0.svn20080206-8) but it is not going to be installed or
                    libavcodec-unstripped-51 (>= 3:0.svn20080206-8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


AND WHEN I DID THAT, IT TOOK ME BACK TO THE BLUE SCREEN THAT SAID

package configuration java6-bin

it's clearly asking me to ok something, but how do i do that?

---

### Post by Neural oD on 2009-02-02
have you tried to use cache in your player? I know that mplayer and vlc both support it!

---

### Post by spookymulder on 2009-02-02
> **Neural oD said:**
> have you tried to use cache in your player? I know that mplayer and vlc both support it!

i don't know how to do that, please advice!

and most importantly, i don't know what to do with the blue system configuration screen in my terminal. it doesn't seem to react to the enter key... what else can i do?

---

### Post by redroad55 on 2009-02-02
this is taken from the guide..
> Note: Those of you installing Sun Java will be asked to accept an end-user license agreement (EULA) before the installation of the Sun Java packages begins. Press the tab key on your keyboard (above the caps lock key), followed by the enter key to accept the EULA and complete the installation
I promise this guide works but you have to pay attention to the details .. You will get it.. slow down to a place where nothing falls between the cracks and you will have success ..let me look through the rest of your post and I'll be back .. Best to you

---

### Post by redroad55 on 2009-02-02
there is one step in the begining of guide where you have to enable Medibuntu repositories .. check if you have done this by going to applications > system > administration > software sources >> there in third party tab it should have medibuntu listed .. also check updates tab and make sure unsupported updates is checked..If you find that medibuntu is not in software choices then go here 
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") 
complete the steps there and return to the guide..Post back with the results and or questions ..Best to you

---

### Post by Neural oD on 2009-02-02
> **spookymulder said:**
> i don't know how to do that, please advice!

and most importantly, i don't know what to do with the blue system configuration screen in my terminal. it doesn't seem to react to the enter key... what else can i do?

sorry - I don't use vlc that much, but under tools -> preferences-> Input & Codecs, look for caching, and try it under higher latency.
Your blue screen - I'm not too sure about - but if all else fails use ctrl-alt-backspace   - this will restart your x session

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> there is one step in the begining of guide where you have to enable Medibuntu repositories .. check if you have done this by going to applications > system > administration > software sources >> there in third party tab it should have medibuntu listed .. also check updates tab and make sure unsupported updates is checked..If you find that medibuntu is not in software choices then go here 
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") 
complete the steps there and return to the guide..Post back with the results and or questions ..Best to you

I did that (unsupported wasn't checked, i checked it), finished with the instructions... playback still choppy! Thanks for pointing out the cracks to me - I finished installation successfully... the playback quality hasn't changed.

I'm fielding all offers. maybe i just have a bad cd-rom? thanks 4 all the help, by the way! I tried switching the vlc to higher latency, too. Basically, what happens is it plays great for about 40 seconds then all of a sudden starts being jerky again. And I have been switching the deinterlacing to blend every time!!

---

### Post by redroad55 on 2009-02-02
If you download a video file and play it is it still choppy? ..post back with results ..

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> If you download a video file and play it is it still choppy? ..post back with results ..

i haven't tried downloading (honestly, I never download videos so i wouldn't know where to start), i just want to watch my (or rental) DVDs... :) and those are being choppy...

---

### Post by redroad55 on 2009-02-02
the video down load would tell if dvd player was suspect or if software related , if video download was successfully played .. Best to you

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> the video down load would tell if dvd player was suspect or if software related , if video download was successfully played .. Best to you

downloaded a movie trailer, played just fine through VLC! ...best to you too (appreciate the help, seriously)! but what to do next? :D

the sound keeps disappearing when playing DVD too... not always, but in quite a few cases!

---

### Post by redroad55 on 2009-02-02
Let's eliminate any hardware possibilities first .. If drive is not new borrow an optical cleaner from a friend if you don't have one and clean laser lense .. Check all cables related to optical drive including small grey one running from drive to motherboard , checking to make sure they are not just partially plugged in and check the drive to make sure jumper is properly set for your application .. Post back with results .. Best to you..

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> Let's eliminate any hardware possibilities first .. If drive is not new borrow an optical cleaner from a friend if you don't have one and clean laser lense .. Check all cables related to optical drive including small grey one running from drive to motherboard , checking to make sure they are not just partially plugged in and check the drive to make sure jumper is properly set for your application .. Post back with results .. Best to you..

everything seems in place...

---

### Post by redroad55 on 2009-02-02
Is audio issue only in DVD or ? post back

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> Is audio issue only in DVD or ? post back

only in DVD... the movie trailer played fine, not choppy, never losing audio, as many times as i played it (5 or 6)... thanks for sticking around!

would "xine -pfhq -D --no-splash -s DVD" help? perhaps, changing my deinterlacer? came across these ideas in some of the forums, but I wasn't sure... maybe, this has something to do with my nvidia?

---

### Post by redroad55 on 2009-02-02
Hi haven't forgotten you.. Just wondering how much of this in the guide you've done..
> --PART 4/5, DVD PLAYBACK/RIPPING/BURNING--


DVD PLAYBACK


Note: I recommend disabling the CD/DVD-ROM source before completing this section, as you will receive numerous prompts if you need to run the "install-css.sh" command. If you're not sure whether it's disabled or not, take a look at the preparation instructions in Part 1.

For the best DVD playback in Ubuntu, including menu support, install the following packages:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

You can also use the Xine engine in Ubuntu (default engine in Kubuntu and Xubuntu) for video/DVD playback. This can be done without having to change the back-end of Totem - just install an alternative GNOME front-end for Xine called Gxine (this is optional, VLC will do just fine):

sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Kaffeine, Gxine or whatever your favourite media player is. Enable deinterlacing ("VLC > Video > Deinterlacing > Blend") if playback is choppy or if you notice artifacts.

Note: Those of you still having DVD playback issues after installing the above packages should try the solutions in the troubleshooting section, which you can find at the end of this howto.


Post back..Best to you

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> Hi haven't forgotten you.. Just wondering how much of this in the guide you've done..

Post back..Best to you

I actually did all of that, exactly step by step. I installed both packages, and then tested the DVD enabling the interlacer like the OP suggested.

In the meantime I have also added nvidia in hardware drivers. That also did nothing.

---

### Post by redroad55 on 2009-02-02
Let me eliminate one other thing in your system bios does it give you a video aperture if so is it set for your card .. I wasn't sure if you had card or onboard video .. you said nvidia in one post that all I caught on that .. So I guess what nvidia do you have ?? Post back..Best to you

---

### Post by spookymulder on 2009-02-02
> **redroad55 said:**
> Let me eliminate one other thing in your system bios does it give you a video aperture if so is it set for your card .. I wasn't sure if you had card or onboard video .. you said nvidia in one post that all I caught on that .. So I guess what nvidia do you have ?? Post back..Best to you

 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)

---

### Post by redroad55 on 2009-02-02
So you put in the suggested driver from Gnome and restarted machine or logged out and still nothing? Hmm.. trying to get a little more familiar with your setup .. Here's a link that had your 6150 listed 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
still trying to turn up something..Post back any new results ..Best to you

---

### Post by skullmunky on 2009-02-02
I've never had occasion to deal with choppy DVD playback, but I wonder if there's a way to rule out hardware issues.  If the HD failed in that machine already, perhaps it's a lemon?  I had a car like that once ... :)  

Not sure if this will show anything useful, but you could try the "dmesg" command.  If there are things like I/O errors, that'll show them.

0. turn on the computer
1. open a terminal
2. ```
dmesg
```
3. it'll show a bunch of stuff, all the "kernel messages" that are output while the system is starting up.  In my case the end of it looks like this:
```

[   50.459437] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.459443] apm: disabled - APM is not SMP safe.
[   50.795197] ppdev: user-space parallel port driver
[   51.106204] audit(1233624018.320:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5765 profile="/usr/sbin/cupsd" namespace="default"
[   51.576653] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   51.657579] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   51.664139] NFSD: starting 90-second grace period
[   52.819456] Clocksource tsc unstable (delta = -78571946 ns)
[   54.318123] Bluetooth: Core ver 2.11
[   54.318183] NET: Registered protocol family 31
[   54.318184] Bluetooth: HCI device and connection manager initialized
[   54.318188] Bluetooth: HCI socket layer initialized
[   54.342526] Bluetooth: L2CAP ver 2.9
[   54.342529] Bluetooth: L2CAP socket layer initialized
[   54.346311] Bluetooth: RFCOMM socket layer initialized
[   54.346321] Bluetooth: RFCOMM TTY layer initialized
[   54.346323] Bluetooth: RFCOMM ver 1.8
[   56.049754] NET: Registered protocol family 5

```
none of that matters, you just want to see what it's like NORMALLY before you play a DVD.


4. play a DVD
5. when the stuttering begins, click back to the terminal and run "dmesg" again.
6. see if anything new, particularly helpful error messages, has been added.

---

### Post by skullmunky on 2009-02-02
If all else fails, you could use a program such as k9copy, K3B, or similar to transfer the movie off the DVD to your hard drive first, then watch it from your hard drive.  Just be sure to delete it when you're done.  Otherwise your drive will get full pretty fast.

---

