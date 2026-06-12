---
title: "DVB-T2 PCIe card TBS6280"
date: 2011-08-09
forum: Multimedia Software
---

### Post by Leechpool on 2011-08-09
Hi,
Has anyone tried the TBS6280. Its a dual tuner DVB-T2 card. Dabs is selling it:

[http://http://www.dabs.com/products/tbs-dual-dvb-t2-pcie-tv-tuner-card-7KTR.html]("http://www.dabs.com/products/tbs-dual-dvb-t2-pcie-tv-tuner-card-7KTR.html")

and the TBS marketing info says drivers are available and it works with ubuntu and is mythTV supported. But I can find no references to anyone who is sucessfully using one......

Cheers
:P

---

### Post by sparky64 on 2011-09-10
As I am also looking at this card £89.00 on Amazon. thought I would add to this instead of start a new thread.
I came across [[COLOR="Red"]THIS[/COLOR]]("http://www.gossamer-threads.com/lists/mythtv/users/489205") discussion on another site.
I have also downloaded the driver package from [[COLOR="Red"]HERE.[/COLOR]]("http://www.buydvb.net/download_center.html")
It looks fairly simple to install, But I have reservations about my kernel.
2.6.39-0-generic
So it looks like it works but will take a bit of work.:(
So have added to wish list and am going to wait a couple of weeks for the drivers to merge.

---

### Post by 337Manni on 2011-09-12
I too am after a DVB-T2 card. I would love to know has anyone had any success with this card as well. I'm looking to replace my Compro E700 as its doesn't look like it's supported under Linux.

Ive seen these options below:

Pinnacle - PCTV nanoStick T2 290e - Fully Supported? but I'm not convinced by USB TV Tuners.

BlackGold - BGT3620 - Dual DVB-T2 - Seems the best card to date but not yet supported by Linux.

TBS - 6280 - Dual DVB-T2 - Seems supported but not seen any success stories.

TBS - 6220 - Single DVB-T2 - Again, seems supported but not seen any success stories.

Tranquil - Dual PCIex DVB-T/T2 - Website says it runs on Linux but again I cant find any success stories

Are there any other DVB-T2 cards on the market (PCI or PCIe)? Especially ones supported by Linux? Or any up and coming cards to watch out for?

---

### Post by sparky64 on 2011-09-13
I have bit the bullet.
Should be here by Friday. so as soon as I get a spare moment I will give it a go getting it installed.
According to the emley moor page I should be able to pick up a couple of hd channels.
Will keep you posted.

---

### Post by 337Manni on 2011-09-16
Well fingers crossed it's easy for you to setup! [-o<

---

### Post by sparky64 on 2011-09-18
Its arrived and fitted.
had a couple of problems though.
Downloaded the latest drivers from the tbs website.
1. there are no readmes for the 6280 but an email to support-sent Friday night and replied by sat morning told me to follow the instructions for the 6980.
2 I cocked up the install by going into the 4vl directory to execute tbs-x86_64.sh
doing it by the instruction properly took a couple of mins and worked perfectly.
3 there is no HD with the standard driver it seems it is one or the other at the moment,they plan to merge after further testing. I have sent an email to support asking for instructions on how to enable.
But the card works fine and seems to be better than my win nova card. 
At least a couple of low signal radio stations that stuttered and dropped out on win nova now sound perfect.

Install instructions.

Create directory, for example /root/tbs and copy the following file to it:

- linux-tbs-drivers.tar.bz2 (S2API Linix driver for TurboSight TBS 6980)
- szap-s2.tar.bz2 (szap tool compatible with new DVB-S2 aware S2 API for Linux)
- scan-s2.tar.bz2 (scan tool compatible with new DVB-S2 aware S2 API for Linux)
- astra_szap-s2.conf (example configuration file for szap-s2)
- astra_scan-s2.conf (example configuration file for scan-s2)
- v4l-cx23885-avcore-01.fw (CX23885 AV core firmware, optional)

I.1 extract linux-tbs-drivers.tar.bz2 archive:

# tar xjvf linux-tbs-drivers.tar.bz2

I.2 go to driver package directory:

# cd linux-tbs-drivers

I.3 depending on if the kernel is x86 or x86_64 (check output of 'uname -a') do:

- for x86 kernel (x86 32 bit installations of Linux):

# ./v4l/tbs-x86.sh

- for x86_64 kernel (x86 64 bit installations of Linux):

# ./v4l/tbs-x86_64.sh

I.3 build and install the driver:

# make && make install

I haven't install the szap/scan packages as I don't need them or fitted the remote control for the same reason.

will update when support reply and get hd working.

Nb:- tbs website is giving opens dns errors for me this morning or i would have provided link for latest drivers.

---

### Post by sparky64 on 2011-09-18
tbs site is back up.
link is here.
[http://www.tbsdtv.com/english/Download.html](http://www.tbsdtv.com/english/Download.html)
Also here are my specs.
running kubuntu 11.04 with kernel 2.6.39-0-generic

---

### Post by 337Manni on 2011-09-18
:D That's great news! :D Glad you've got it working.


> I haven't install the szap/scan packages as I don't need them or fitted the remote control for the same reason.How are you using it... Myth?

I'd like to set it up on a Ubuntu 11.04 PC with a Myth Backend / Frontend, so I could use it on that PC and over a network to a laptop.

I wonder when they will decide to merge the two drivers. I't would be nice to get all the standard channels plus the HD ones, and use the card to it's full potential.

Have you got both tuners setup and working?

How many chanels can you record at once?

---

### Post by sparky64 on 2011-09-18
> **337Manni said:**
> :D That's great news! :D Glad you've got it working.


How are you using it... Myth?

I'd like to set it up on a Ubuntu 11.04 PC with a Myth Backend / Frontend, so I could use it on that PC and over a network to a laptop.

I wonder when they will decide to merge the two drivers. I't would be nice to get all the standard channels plus the HD ones, and use the card to it's full potential.

Have you got both tuners setup and working?

How many chanels can you record at once?

 I am using kubuntu with the latest kernel.
The comp is in my kitchen/office area so I don't need the remote.
 I also use kaffeine so as soon as I rebooted the card showed up under the configure tv tab, No faffing needed.
 I also still have the win nova dual card installed and have recorded up to 6 overlapping programs (on the same multiplex)with that card. So with four tuners now fitted it should cover my future needs.
 I am looking to build a media centre (myth) for a friend so if this works out OK may buy another instead of using this one.
 I seem to remember that you can record up to 10 programs at once on myth with that card.

Also kaffeine records in a format that I can stream to my living room set-up without converting, Yay for archos format support. Just hope the high def does the same.

 I did read a post somewhere that they were hoping to have merged drivers towrds the end of september, But i did not save the page so don't quote me.
 I also read that if your kernel is updated you will have to reinstall the drivers.

Just waiting for support now for info on how to swap to T2 Hd.
will post asap.

---

### Post by sparky64 on 2011-09-23
Finally had time to sort out hd drivers.
This[ link ]("http://www.tbsdtv.com/forum/viewtopic.php?f=52&t=1381") is the official tbs forum page for this card.

It looks like merged drivers will be out in a couple of weeks.
  The only problem I have is that kaffeine has no sound. It records and plays back OK but no sound live.
I have tried increasing the buffers as in [ This thread.]("http://ubuntuforums.org/showthread.php?t=1429279") 
 Also it seems epg data is not included due to copyright/recording restrictions.

---

### Post by sparky64 on 2011-09-25
Progress report.
Still can't get sound to work live.
But I can record in HD and then play the file in vlc. Tried out on the grand prix, And watched the whole race with no problems.
There also seems to be a problem that I can't change to watch other channels if recording an HD channel, even on a second card. On normal channels i have recorded up to 3 programs while listening to the radio channel.
Here's hoping the merged drivers improve matters.

---

### Post by 337Manni on 2011-09-30
Think I'm going to hold off until the merged driver is released and proved to be working. I would like to purchase a tuner that will fully work for both standard and HD channels at the same time. Gonne stick with my dual boot for now using Win 7 and my current tuner until I have a new card....being this one or another, then I'm going to fully commit to Ubuntu

Fingers crossed the merged driver release goes smoothly!

I hope your sound and recording issue have been picked up by TBS and have been fixed in this 

merged driver, assuming its a driver issue that is. It may be a kaffeine issue with the sound and this card?

---

### Post by sparky64 on 2011-10-13
Quick update.
sound needs pulseaudio to work (on playback of recordings)
without I get no sound at all. I use kde so always remove asap as it rarely works properly.
It also won't yet run on kernel 3.0 till the merged drivers are released. 
Still can,t get sound on kaffeine.

New updated driver released for 11.10
will try out tomorrow.

---

### Post by 337Manni on 2011-10-14
That's great news. Hope it contains both drivers merged into one!

:D

---

### Post by sparky64 on 2011-10-15
Finally got 11.10 installed after numerous partitioner crashes.
Spent ages trying to get firmware to load. must have done 7-8 reboots before giving up for night.
When I switched on this morning firmware loaded perfect.
Must need a complete shut down? before working.
Bad news is It's not the merged drivers so have hd or standard only.No sound on kaffeine.
I am now trying the new digital control centre to see if that works.
At least I got to watch GP in high def, (At 10 seconds behind signal)

---

### Post by Leechpool on 2012-03-16
Hi all,
just thought I'd provide some feedback.
I eventually bought a TBS6284 - quad DVB-T2 tuner.
Installed with Mythbuntu 11.10 without problem.
Works very well. Have been using for over a month now with no crashes/lockups or anything.
Note TBS have merged the drivers so both SD and HD work.
Have set myth to use two virtual tuners per physical tuner so can record two channels from any mux using a single tuner i.e. can record up to 8 channels across 4 mux.
Would recommend card.
Cheers
:)

---

### Post by timswait on 2012-03-19
I've just got a TBS6280 and used it in a new mythbuntu machine. I tried following the instructions in post #6, but it's not worked for me :( All the instructions I can find seem to be for TBS69XX cards and satelite not terrestrial tuners. My attempt at building the drivers ended with:
```
found 496 modules
make[1]: Leaving directory `/home/trilby/Driver/linux-tbs-drivers/v4l'
make -C /home/trilby/Driver/linux-tbs-drivers/v4l install
make: *** /home/trilby/Driver/linux-tbs-drivers/v4l: Permission denied.  Stop.
make: *** [install] Error 2
```
So I guess it didn't install the drivers, the card still isn't listed in Myth. I've attached the full output from trying to install the drivers, can anyone tell me what is wrong please?
Cheers

---

### Post by Chris Musampa on 2012-03-26
> **Leechpool said:**
> Hi all,
just thought I'd provide some feedback.
I eventually bought a TBS6284 - quad DVB-T2 tuner.
Installed with Mythbuntu 11.10 without problem.
Works very well. Have been using for over a month now with no crashes/lockups or anything.
Note TBS have merged the drivers so both SD and HD work.
Have set myth to use two virtual tuners per physical tuner so can record two channels from any mux using a single tuner i.e. can record up to 8 channels across 4 mux.
Would recommend card.
Cheers
:)

This looks the D's Bs, I've just ordered one off Amazon :p

---

### Post by BicyclerBoy on 2012-03-28
@timswait
try:
make
sudo make install

(don't use make as sudo)

---

### Post by timswait on 2012-03-28
I'd actually away got the answer from technical support so good work TBS! But yes, bicyclerboy, that was what they told me to do and it worked, so that was the answer!

---

### Post by sparky64 on 2012-04-08
Been a while since i posted.
updated to 12.04 today and reinstalled card.
Sound now works perfectly in kaffiene. also recording programs in sd and hd works ok.
also works fine in vlc 2.
did have one problem when recording one channel and trying to watch another with a differnt card. But as it sorted itself out after half hour i think it was more of a signal problem.
The only annoying thing is having to reinstall after kernel update.

---

### Post by timswait on 2012-04-29
Sparky (or anyone else): How do I reinstall the drivers? Mine has stopped working since upgrading to 12.04, so I guess I need to reinstall, but don't know how to do it. I tried navigating into the directory with the drivers and typing "sudo make install" again, and it did quite a lot of lines of text, so was obviously doing something, but it's still not working :( Do I need to remove the drivers first and then start again? In that case how do I remove them?

---

### Post by BicyclerBoy on 2012-04-29
You'll need at a minimum ..
new kernel headers package
make
sudo make install
reboot

Could need to run any './configure --help' script & 'make clean' before make..

---

### Post by timswait on 2012-04-29
Thanks for the quick reply. That works, it's back up and running again now :)

---

### Post by matt0978 on 2012-08-02
What is the status with the TBS6280 now? I've just installed Ubuntu Precise and downloaded the latest drivers from TBS, what program is best to use to start watching TV?
 
Thanks

OK, because I couldn't make sense of sparky's instructions I followed instructions from here:

[http://linuxtv.org/wiki/index.php/TBS6280](http://linuxtv.org/wiki/index.php/TBS6280)

(I've got latest drivers v120709, at time of post)

and this is what I was getting:


mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709$ untar/bzip linux-tbs-drivers.tar.bz2
bash: untar/bzip: No such file or directory
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709$ untar linux-tbs-drivers.tar.bz2
No command 'untar' found, did you mean:
 Command 'unrar' from package 'unrar-free' (universe)
 Command 'unrar' from package 'unrar' (multiverse)
 Command 'unar' from package 'unar' (universe)
untar: command not found
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709$ untar /linux-tbs-drivers.tar.bz2
No command 'untar' found, did you mean:
 Command 'unrar' from package 'unrar-free' (universe)
 Command 'unrar' from package 'unrar' (multiverse)
 Command 'unar' from package 'unar' (universe)
untar: command not found
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709$ cd linux-tbs-drivers
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$  find -type d -exec chmod 755 \{\} \;
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$  find -type f -exec chmod 644 \{\} \;
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$  find -name '*.sh' -exec chmod 755 \{\} \;
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$ ./v4l/tbs-x86_64.sh -j5
TBS drivers configured for x86_64 platform.
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$ make
make -C /home/mattmoo/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers/v4l 
make[1]: Entering directory `/home/mattmoo/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers/v4l'
No version yet, using 3.2.0-29-generic
make[1]: Leaving directory `/home/mattmoo/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers/v4l'
make[1]: Entering directory `/home/mattmoo/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers/v4l'
scripts/make_makefile.pl
make[1]: execvp: scripts/make_makefile.pl: Permission denied
Updating/Creating .config
/bin/sh: 2: ./scripts/make_kconfig.pl: Permission denied
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/home/mattmoo/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers/v4l'
make: *** [all] Error 2
mattmoo@mattmoo-kUbuntu:~/Downloads/tbs-linux-drivers_v120709/linux-tbs-drivers$ 

so I still haven't managed to get the drivers working in kUbuntu 12.04. Can someone post step by step idiot-proof instructions  please?

---

