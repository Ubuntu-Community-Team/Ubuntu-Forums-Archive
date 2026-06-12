---
title: "Leadtek WinFast DTV1000S"
date: 2009-06-02
forum: Mythbuntu
---

### Post by nasha on 2009-06-02
Hi Guys,
Haven't heard anything about this card recently... 
Can anyone say whether it is supported under linux yet?
I have one just sitting here, and my main tuner has just died, so i'd like to avoid purchasing another.

Cheers,
Nash

---

### Post by LowSky on 2009-06-02
Sorry buddy, this card looks like it has no linux support. I cant really find much on this card.

Do you know what chipset it uses, looking that up might help

---

### Post by STYX2009 on 2009-06-03
Hi,

The official Linux v4l-dvb driver for DTV1000 S is here :
   [http://kernellabs.com/hg/~mkrufky/dtv1000s]("http://kernellabs.com/hg/%7Emkrufky/dtv1000s")
   Please send your test result and dmesg output to the author Michael Krufky <mkrufky@kernellabs.com>.

And the firmware dvb-fe-tda10048-1.0.fw is here:
[http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz](http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz)
[http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)
[]("http://tw1965.myweb.hinet.net/")

---

### Post by scintilla on 2010-05-18
Anyone tried to build the driver with ubuntu 10.04?
I am getting a compile error:
```
dvbdev.c:516: error: 'struct class' has no member named 'nodename'
```

I would be interested to know of others' experiences.     This is using the official source as quoted above

Also any advice on how to raise a bug report?  Thanks.

---

### Post by Nicholas Bates on 2010-06-01
Hi Folks

First post...

I came across this thread after installing ubuntu server 10.04 as a basis for a mythtv backend and found the same error when building the driver from kernellabs.org.

However, it seems the tuner driver has been merged into the linux kernel as of 2.6.33... so all I had to do was install one of the corresponding kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

I tried with 2.6.33.4-lucid and the card was working after installing the firmware and rebooting.

Cheers, Nick

---

### Post by tgrego on 2010-06-22
> **Nicholas Bates said:**
> Hi Folks

First post...

I came across this thread after installing ubuntu server 10.04 as a basis for a mythtv backend and found the same error when building the driver from kernellabs.org.

However, it seems the tuner driver has been merged into the linux kernel as of 2.6.33... so all I had to do was install one of the corresponding kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

I tried with 2.6.33.4-lucid and the card was working after installing the firmware and rebooting.

Cheers, Nick

Hi Nick,
can you please explain a little how you manage to get it to work?
I was really mad when realized the dtv1000s was not supported in linux, and am really tired of going to win7 just to watch some tv...
If you did it, so can I!
I'm using the current 'official' ubuntu linux kernel (2.6.32-22-generic amd64) and I believe that's on the list (at least there are several v2.6.32 there...). Or maybe I have to install another... but if it's not on the reps I suppose it will be a painful :s

For the firmware, did you follow the links given by STYX2009?

Cheers, hope to get it working! 
Tiago

---

### Post by ruger01 on 2010-07-31
I have one of these cards as well but cannot get it to work, have downloaded the driver and firware but having issues installing this does anyone have a step by step guide to installing this card in Ubuntu 10.04? Any help would be greatly appreciated for an Ubuntu noob,
 
Cheers Ruger01.

---

### Post by goffa72 on 2010-07-31
There is a bit of a guide here - [http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=9](http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=9) that gives some steps on how to get it working.

edit - more info here also [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek)

Hope it helps.

---

### Post by ruger01 on 2010-07-31
Thanks for thie links Goff72, i had found one of them yesterday, still having issues getting it to work i down loaded the mercurial headers, and also the HG Clone bit as well, did a "make" then "sudo make install" seen a few errors come up as this was happening not sure what they were about. Card doesnt appear to be working though.
 
Is there anyway of getting Terminal to display if the card is detected and what i need to do to fix it and it's errors?
 
I am a complete linux/ubuntu noob keep in mind,
 
Cheers.

---

### Post by goffa72 on 2010-08-03
> **ruger01 said:**
> 
 
Is there anyway of getting Terminal to display if the card is detected and what i need to do to fix it and it's errors?
 
Cheers.

from [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) you could also try here [http://linuxtv.org/wiki/index.php/FAQ_%26_Troubleshooting](http://linuxtv.org/wiki/index.php/FAQ_%26_Troubleshooting)

**(a) For a DVB device**, you should now have a non-empty */dev/dvb* directory.  You can check on whether this is true for you with the following command:   ls -l /dev/dvb/  (alternatively, you can browse your directory structure with the graphical file manager of your choice). If you have a single DVB device installed in your system, then the output of the above command should reveal that /dev/dvb/ is populated by adapter0. Digging further, 
  ls -l /dev/dvb/adapter0   reveals the [character devices]("http://linuxtv.org/wiki/index.php/Device_nodes_and_character_devices#DVB_character_devices") associated with adapter0 for which the drivers have control. If you have more then one DVB device, you can see the same for all with 
  ls -l /dev/dvb/adapter*

from second last post here [http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=4](http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=4)

> If you are getting 'firedtv' errors this is known problem with ubuntu (maybe other distros as well), to fix that go to the driver directory and 
cd v4l
gedit .config
 find the line 'CONFIG_DVB_FIREDTV=m' and change that to 'CONFIG_DVB_FIREDTV=n' then try rebuild and you should be good to go.

---

### Post by ruger01 on 2010-08-06
Hi People, i am still having a few issues installing a **Leadtek DTV1000S TV Card** - Could someone look at the error i am getting and advise what i need to install to fix it? I have downloaded the driver, extracted the gz file into my downloads folder, navigated to the file in terminal but when i do a "make" i get this error -


john@john-desktop:~/Downloads$ cd dtv1000s-43878f8dbfb0
john@john-desktop:~/Downloads/dtv1000s-43878f8dbfb0$ make
make -C /home/john/Downloads/dtv1000s-43878f8dbfb0/v4l 
make[1]: Entering directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/firmware'
make[2]: Leaving directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-24-generic/build
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/dvbdev.o
/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/dvbdev.c: In function 'init_dvbdev':
[B]/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/dvbdev.c:516: error: 'struct class' has no member named 'nodename'
make[3]: *** [/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l/dvbdev.o] Error 1
make[2]: *** [_module_/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/john/Downloads/dtv1000s-43878f8dbfb0/v4l'
make: *** [all] Error 2[/B]
john@john-desktop:~/Downloads/dtv1000s-43878f8dbfb0$ 

Any help greatly appreciated,

Cheers Ruger01.

---

### Post by goffa72 on 2010-08-06
Hi Ruger01, did you follow the advice from the whirlpool forum - 

> @gimbo I have also noticed this issue lately, It is due to the fact that the [http://kernellabs.com/hg/~mkrufky/dtv1000s]("http://kernellabs.com/hg/%7Emkrufky/dtv1000s") branch is no longer updated I believe, this is because it has been merged into the mainline branch so the solution is to use the mainline branch
 The other option is to use 2.6.33 as you said, but this is not fully ready yet.
 To use the mainline branch first install mercurial
 sudo aptitude install mercurial
 then goto a clean directory and
 hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
 then wait while it downloads.... then cd v4l-dvb and follow the make, sudo make install process, you will still get a Firedtv error on the first make you can fix this by going to the v4l directory and editing .config to change the setting to 'n' as described above. Hope this helps
It looks like dtv1000s-43878f8dbfb0 is out of date 

After installing mercurial [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
make
sudo make install

If you still get errors try following the advice in these posts 

[http://ubuntuforums.org/showthread.php?t=1337146&highlight=Mercurial](http://ubuntuforums.org/showthread.php?t=1337146&highlight=Mercurial)

[http://ubuntuforums.org/showthread.php?t=1305228&highlight=v4l-dvb](http://ubuntuforums.org/showthread.php?t=1305228&highlight=v4l-dvb)

> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make menuconfig <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make install

---

### Post by ruger01 on 2010-08-07
Goffa72, thank you so much mate i got it working!!! For anyone interested I did the following in terminal from a fairly new Ubuntu install, forget about downloading files/tarball for the v4l-dvb driver for the DTV100S as these are no longer up to date etc -
 
(Thanks to mike22 whirpool forum user for the following first bit here)
 
**sudo aptitude install mercurial**
 
then go to a clean directory (i.e. exit terminal then reopen a new session)
 
**hg clone **[**http://linuxtv.org/hg/v4l-dvb**]("http://linuxtv.org/hg/v4l-dvb")
 
then wait while it downloads.... then 
 
**cd v4l-dvb** 
 
and then 
 
**make** 
 
 
 
 
I had many errors especially about "firedtv", "nodename" etc I then did as per deejc's post (thanks to you as well)
[http://ubuntuforums.org/showthread.p...ight=Mercurial](http://ubuntuforums.org/showthread.p...ight=Mercurial)
 
 
just run -
 
**make config**
 
press the enter key (lots!) until you reach the point that shows :
 
*Code:*
** Supported FireWire (IEEE 1394) Adapters*
***
*FireDTV and FloppyDTV (DVB_FIREDTV) [M/n/?] *
 
Press -
 
**n**
 
and then press enter key continuously until it exits (i held the enter key down to get to the end), then re run 
 
**make**
 
this stops the error on the card and accepts all the defaults, then -
 
**sudo make install**
 
I then rebooted did a **sudo apt-get update** and **sudo apt-get upgrade **(not sure why i did this just did for good measure i guess, probably didn't need to do this bit) i then rebooted the system yet again.
 
 
Kaffeine would then scan channels after i selected "Autoscan Australia" in device tab, but would not display digital tv, i had an error: 
 
**"kaffeine cannot find demux plugin for MRL"**
 
I Followed [svaens]("http://ubuntuforums.org/member.php?u=484988") post (thanks to you) and installed via terminal -
 
**sudo apt-get install libxine1-all-plugins**
 
All works perfectly well, celebrating with beer now!
 
Cheers, Ruger01.

---

### Post by goffa72 on 2010-08-07
Happy to help you out Ruger01, I had similar problems about a year ago with a Leadtek 1800H.

Have you also got the remote working?

---

### Post by ruger01 on 2010-08-07
Not yet mate, i have torn all the hair out of my head over the last few weeks just getting the card set up, but have learnt heaps about Linux in general so it was a good thing i guess. Don't get me wrong though i reckon Ubuntu is excellent.
 
I have a Logitech 525 Universal remote that i can program, so i reckon that will be the next hurdle getting it set up.
 
Virtual beers to all.

---

### Post by Anoxymous on 2010-08-23
I have managed to get the Tuner to work & watch TV but I am unable to detect input from s-video/composite. I added a new capture card, empty grabber video source & linked the inputs in backend but when I switch to it in front end i get a black screen & the system stalls. Anybody know how I get it working?

---

### Post by GeorgeBigfoot on 2010-10-23
Hi Guys

Looks like you've already fixed it up but for anyone else who stumbles across this....

I had the same issues with the Leadtek dtv1000s. I also posted to this forum and eventually got help from a guy at work. The solution that worked for me I doco'd here: [http://ubuntuforums.org/showpost.php?p=8601490&postcount=17](http://ubuntuforums.org/showpost.php?p=8601490&postcount=17)

I got it working on both 9.04 and 9.10. Just this afternoon I have updated to 10.10. This was an upgrade, not a clean install. Did the install, restarted and the 3 tuners work perfectly. Kernel I'm running: 2.6.35-22-generic

Good luck!

---

