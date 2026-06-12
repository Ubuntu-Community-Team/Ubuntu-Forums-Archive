---
title: "Hauppauge WinTV-HVR 1800"
date: 2008-05-07
forum: Mythbuntu
---

### Post by TomDaBomb2u on 2008-05-07
Hello, I am a relative newbie to Ubuntu and Mythbuntu. I recently upgraded my computer so that I can use it as a DVR. I have run into some issues and need guidance.

I have a Hauppauge WinTV-HVR 1800 and an Nvidia GeForce 7150/nForce 630i motherboard. 

I installed Mythbuntu 8.04, got all my NVidia drivers working correctly, but it will not see my WinTV card. 

Questions
1.) I want to have DVR as well as Desktop capabilities. Is it possible to just run Mythbuntu as a program inside Ubuntu? Or is it only a separate OS?

2.) Is this card even supported? I've been running into a lot of contradictory posts when researching the issue.

Someone please help!

Thanks!
-Thomas

---

### Post by murchball on 2008-05-07
Mythbuntu is it's own distro, but you can install a full desktop on it. In Mythbuntu-control-centre, just select the Gnome desktop role. Conversely, if you already have a desktop ubuntu installation, you can install Mythbuntu-control-centre and all of the other myth goodies to get the same result.

I also have an HVR-1800 that came with a computer I bought. I played with it for an hour or so before giving up. I believe that it is fully supported by MythTV, but getting it running on Ubuntu is not an out-of-the-box experience. I would think that 8.10 will probably support it much better.

---

### Post by TomDaBomb2u on 2008-05-07
> **murchball said:**
> I would think that 8.10 will probably support it much better.

Thanks for the reply. Do you mean 8.04? I looked up the Wiki and it says that the HVR-1800 is supported, but I'm still having trouble. It's still not recognized by Mythbuntu, even when I select DVB.

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800)

Any suggestions? Anyone?

Thanks!
-Thomas

---

### Post by murchball on 2008-05-07
No, I mean 8.10. When I first started playing with MythTV, I had a very hard time getting my PCHDTV HD-5500 to work, because drivers weren't included with the distro, even though Myth had full support. Now that card is very well supported, nothing special required. I'm expecting the same thing with the 1800: right now it will work, but you really have to work at it. This does seem to be a very popular card and I'm guessing that in the next release it will be a very straightforward setup.

When I tried to install the 1800 my problem seemed to be at the OS level, not MythTV. YMMV

---

### Post by TomDaBomb2u on 2008-05-08
Thanks very much murchball. But do you have any insight for getting this to work? Or should I just give up and get a new one? (Actually I'm leaning towards this anyway, since it's even giving me trouble in XP :???:)

---

### Post by murchball on 2008-05-08
I guess it depends on how much fiddling you want to do. I already had other capture devices and didn't pay for this card, so it was easy for me to give up on this. If you really want to get this card working now, it looks like people on this thread have it working: [http://ubuntuforums.org/showthread.php?t=666150&highlight=hvr-1800](http://ubuntuforums.org/showthread.php?t=666150&highlight=hvr-1800)

If you're looking for a straight-forward, out of the box solution and have an extra $170 hanging around, I would spring for an HDHomeRun or an HD-5500 if you really want an internal card.

---

### Post by TomDaBomb2u on 2008-05-08
OK. That's the thread I've been reading. Thanks very much. You have been very helpful!:)

---

### Post by beartard on 2008-05-08
When I first installed this card about a month ago, the drivers were such that I could receive ATSC television without any problems.  NTSC/composite, however, was unavailable.  In the last few days, the v4l-dvb drivers have been updated and both now work.  You can even have analog tv (or your Wii) running in tvtime and hi-def tv playing in kaffeine at the same time.

The quick howto on updating your drivers is this:
1.Install mercurial (hg) from your package manager.
2.Get mercurial to download the video4linux dvb repository.
```
hg clone http://linuxtv.org/hg/v4l-dvb/
```
3. go into the v4l-dvb directory in your home directory.
4. ```
make
sudo make install
```
5. Reboot and it should work.  If you get no results, check that the modules are loaded.  A quick scan of lsmod shows the following related modules are loaded on my system: tuner, tveeprom, dvb_core, cx23885, cx25840, cx2341x, v4l2_common, btcx_risc, videobuf_core, videobuf_dvb, v4l1_compat

---

### Post by murchball on 2008-05-09
Very nice! Does Myth support digital and analog capture at the same time?

---

### Post by beartard on 2008-05-09
I couldn't tell you that.  I always lose patience with mythtv and give up.  For as much as I watch tv, it's more a toy to me anyway.

But you're right...with 8.10 and maybe even a backport to hardy, the driver update I listed probably won't even be necessary.

---

### Post by TomDaBomb2u on 2008-05-10
Thanks beartard! The installation appeared to work, but I'm not sure. I am very a newbie and do not know how to scan for modules. I issued the lsmod command (is this all I need to do?) and here is the output I received.

```
thomas@thomas-desktop:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
mt2131                  6916  1 
s5h1409                10116  1 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
cx25840                30668  0 
snd_seq_oss            35584  0 
psmouse                40336  0 
rt61pci                25472  0 
cx23885                91572  0 
nvidia               7825536  34 
rt2x00pci              11264  1 rt61pci
rt2x00lib              22528  2 rt61pci,rt2x00pci
serio_raw               7940  0 
videodev               34432  1 cx23885
compat_ioctl32          2304  1 cx23885
cx2341x                13572  1 cx23885
videobuf_dma_sg        14980  1 cx23885
v4l1_compat            15748  2 cx23885,videodev
v4l2_common            12672  3 cx25840,cx23885,cx2341x
agpgart                34760  1 nvidia
rfkill                  8592  1 rt2x00lib
snd_seq_midi            9376  0 
btcx_risc               5896  1 cx23885
pcspkr                  4224  0 
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
sky2                   47492  0 
snd_rawmidi            25760  1 snd_seq_midi
tveeprom               13316  1 cx23885
i2c_core               24832  7 mt2131,s5h1409,cx25840,cx23885,nvidia,v4l2_common,tveeprom
videobuf_dvb            7812  1 cx23885
dvb_core               80508  1 videobuf_dvb
mac80211              165652  3 rt61pci,rt2x00pci,rt2x00lib
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
videobuf_core          19460  3 cx23885,videobuf_dma_sg,videobuf_dvb
cfg80211               15112  1 mac80211
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
eeprom_93cx6            3200  1 rt61pci
joydev                 13120  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  13056  4 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
lirc_mceusb2           14980  0 
lirc_dev               15732  1 lirc_mceusb2
wmi_acer                9644  0 
button                  9232  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30720  3 
usb_storage            73664  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
libusual               19108  1 usb_storage
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ahci                   28420  2 
pata_amd               14212  0 
ata_generic             8324  0 
pata_acpi               8320  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 ahci,pata_amd,ata_generic,pata_acpi
ohci_hcd               25348  0 
ehci_hcd               37900  0 
scsi_mod              151436  6 sbp2,sd_mod,usb_storage,sg,sr_mod,libata
usbcore               146028  7 lirc_mceusb2,usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

---

### Post by TomDaBomb2u on 2008-05-10
OK. Update: I got it to work with TVTime! But I'm not getting any signal. I think I'll just play around with it until I figure it out. In the meanwhile, any suggestions?

---

### Post by agamotto on 2008-05-10
I am not sure if I was just lucky, or what.  I have a Mythbuntu setup, and the Hauppauge 1800 card finally works for digital.  I don't think the analog tuner has support yet, but I can confirm that the digital does work.  Part of your fun might be the device number when you are setting up the capture card.  The only other thing I can think of is that I can't get the SD tv guide info to work with it yet.  I just scanned for channels (not from listing source) with my OTA antenna, and it found the channels.  Wierd bit is that there is some guide info in the channels, apparently.  I just don't know how to put it in the program guide, etc... currently.

---

### Post by beartard on 2008-05-11
Ok, maybe I should clarify something I said earlier.  I haven't tried hooking an antenna up and trying analog channels in tvtime.  I have hooked up an old dvd player to the composite input and got some goodness out of the card.  The channel changing in tvtime does work.  I get "good" static.  Before, I got nothing.  I figured that since composite and analog are handled by the same chip, that both worked.

---

### Post by beartard on 2008-05-11
> **TomDaBomb2u said:**
> OK. Update: I got it to work with TVTime! But I'm not getting any signal. I think I'll just play around with it until I figure it out. In the meanwhile, any suggestions?

Hey, man.  Try seeing if this helps:
```
sudo modprobe tuner
```
I noticed it was missing from your list of modules.  Might help you out with tvtime.

And yes, analog is working with the updated drivers.  I don't think the updates made it into hardy final, though.  That's why the mercurial download/build/install is necessary.  I would venture a guess that, if a new kernel gets backported to hardy, that it would have the updates included.  Be on the lookout if the update manager asks you to update.

Oh, and two other things to be careful about.  Every time a kernel update comes out, it might be necessary to do another "make install" or even a complete rebuild of the v4l-dvb system, depending on how major the update.  For example, if it's 2.6.24-17* just a "make install" would be good enough.  If it's 2.6.24-18* then a rebuild would be necessary since that whole modules directory would be different.

Second is that people have reported losing some webcams under these updated drivers.  Those using gspca drivers are usually the ones that stop working.

And keep this in mind:  even experts on some things are "total n3wbz" at others.

---

### Post by TomDaBomb2u on 2008-05-11
Thanks! I issued the ```
sudo modprobe tuner
``` command you gave me, and now I see tuner when I issue lsmod. 

So here's where I am now: I've got static, but still cannot find any channels. I've done ```
sudo tvtime-scanner
``` and scanned the entire range with no luck. I've tried scanning inside the program itself, and just get static.

I'm feeling a bit more optimistic than before; I at least get static now! :-)

---

### Post by beartard on 2008-05-12
> **TomDaBomb2u said:**
> I'm feeling a bit more optimistic than before; I at least get static now! :-)

Then you have achieved DaBomb status and are exactly where I am.  When I get home from work today I'll check with an antenna on analog and see what I can get out of it.  I only tested the composite before, figuring that analog would work if composite worked since they're handled by the same chip.

---

### Post by woodsby on 2008-05-12
> **beartard said:**
> When I first installed this card about a month ago, the drivers were such that I could receive ATSC television without any problems.  NTSC/composite, however, was unavailable.  In the last few days, the v4l-dvb drivers have been updated and both now work.  You can even have analog tv (or your Wii) running in tvtime and hi-def tv playing in kaffeine at the same time.

Beartard, were you able to get the audio working on NTSC in tvtime?  I haven't checked composite audio input, but I can't get audio working on analog cable.

---

### Post by beartard on 2008-05-12
I was getting video static without audio.  On composite I got good video (just the dvd player's boot screen).  Come to think of it, I'm not that great a tester as I didn't put a disc in to check audio.

---

### Post by nowandever29 on 2008-05-12
> **beartard said:**
> When I first installed this card about a month ago, the drivers were such that I could receive ATSC television without any problems.  NTSC/composite, however, was unavailable.  In the last few days, the v4l-dvb drivers have been updated and both now work.  You can even have analog tv (or your Wii) running in tvtime and hi-def tv playing in kaffeine at the same time.

The quick howto on updating your drivers is this:
1.Install mercurial (hg) from your package manager.
2.Get mercurial to download the video4linux dvb repository.
```
hg clone http://linuxtv.org/hg/v4l-dvb/
```
3. go into the v4l-dvb directory in your home directory.
4. ```
make
sudo make install
```
5. Reboot and it should work.  If you get no results, check that the modules are loaded.  A quick scan of lsmod shows the following related modules are loaded on my system: tuner, tveeprom, dvb_core, cx23885, cx25840, cx2341x, v4l2_common, btcx_risc, videobuf_core, videobuf_dvb, v4l1_compat
I got the repositoryu fine, but Running on MB 8.04, I get the following when doing the sudo make install:

bill@TV:~/v4l-dvb$ sudo make install
[sudo] password for bill: 
make -C /home/bill/v4l-dvb/v4l install
make[1]: Entering directory `/home/bill/v4l-dvb/v4l'
No version yet, using 2.6.24-16-generic
make[1]: Leaving directory `/home/bill/v4l-dvb/v4l'
make[1]: Entering directory `/home/bill/v4l-dvb/v4l'
scripts/make_makefile.pl
make[1]: Leaving directory `/home/bill/v4l-dvb/v4l'
make[1]: Entering directory `/home/bill/v4l-dvb/v4l'
Stripping debug info from files
Usage: strip <option(s)> in-file(s)
 Removes symbols and sections from files
 The options are:
  -I --input-target=<bfdname>      Assume input file is in format <bfdname>
  -O --output-target=<bfdname>     Create an output file in format <bfdname>
  -F --target=<bfdname>            Set both input and output format to <bfdname>
  -p --preserve-dates              Copy modified/access timestamps to the output
  -R --remove-section=<name>       Remove section <name> from the output
  -s --strip-all                   Remove all symbol and relocation information
  -g -S -d --strip-debug           Remove all debugging symbols & sections
     --strip-unneeded              Remove all symbols not needed by relocations
     --only-keep-debug             Strip everything but the debug information
  -N --strip-symbol=<name>         Do not copy symbol <name>
  -K --keep-symbol=<name>          Do not strip symbol <name>
     --keep-file-symbols           Do not strip file symbol(s)
  -w --wildcard                    Permit wildcard in symbol comparison
  -x --discard-all                 Remove all non-global symbols
  -X --discard-locals              Remove any compiler-generated symbols
  -v --verbose                     List all object files modified
  -V --version                     Display this program's version number
  -h --help                        Display this output
     --info                        List object formats & architectures supported
  -o <file>                        Place stripped output into <file>
strip: supported targets: elf32-i386 a.out-i386-linux efi-app-ia32 elf32-little elf32-big elf64-x86-64 efi-app-x86_64 elf64-little elf64-big srec symbolsrec tekhex binary ihex trad-core
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/bill/v4l-dvb/v4l'
make: *** [install] Error 2

---

### Post by beartard on 2008-05-12
Ok, just an update.   I just re-installed the drivers to make sure I have the latest versions.  Digital tv works fine.  Audio and video are normal.  Composite has video, but no sound (yet).  Analog gets "good" static (an improvement over a black screen) but no sound.

I've tried all the usual suspects (mixer, etc.)  Most old cards could route the sound via a jumper cable to the sound card, but I don't think the 1800 has audio outs.  Shouldn't be necessary anyway.  I guess the drivers must either be a couple weeks away from 100% or I'm missing something simple.  ;)

---

### Post by beartard on 2008-05-12
> **nowandever29 said:**
> I got the repositoryu fine, but Running on MB 8.04, I get the following when doing the sudo make install:

make[1]: Entering directory `/home/bill/v4l-dvb/v4l'
No version yet, using 2.6.24-16-generic

That's the first thing that doesn't look quite right.  Not trying to insult your intelligence, but did you do "make" first?  Also, if you're on hardy, the latest kernel is 2.6.24-17-generic.  Have you upgraded to it and made sure the kernel source was installed?

I've been checking around to see if I can find someone else who's had the same error with the install.  If I find anything, I'll let you know.

In the meantime, check [http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial](http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial) for more detailed instructions than I gave.  They can be a little out-of-date and not ubuntu-specific, but the general idea is there.

---

### Post by TomDaBomb2u on 2008-05-12
I'm in the same place as you now. . . I think. I just bought a digital converter box and ran the composite audio and video into the card. I have video, but no sound.

---

### Post by cenwesi on 2008-05-20
Any luck with sound on this...i get video just fine but no sound.

---

### Post by TomDaBomb2u on 2008-05-21
Nope. None here. I just went back to using my little TV lol

---

### Post by cenwesi on 2008-05-21
almost 1yr now and still no way of getting sound on this card. Some people claim they got sound working but how???

---

### Post by beartard on 2008-05-22
I do have sound working....on hdtv.  The drivers still haven't gotten sound on analog/composite yet.

If composite is a big need for you (video works) you could hook the audio up to your sound card input and make a script that loads your tv viewer and a sound player like sox at the same time.  That'd be a good temporary fix.  In fact, older tv cards had to do this anyway under Linux.

If it's analog tv, I don't think that's going to work yet, as I haven't gotten good video yet over analog.

These guys are doing a good job reverse-engineering drivers for the chipsets on the card.  Keep in mind they're working on the features they need first.  Then the rest in their spare time.  Since ATSC was the main reason for getting this card, it's the first thing supported by the Linux drivers.  They've come a long way.

---

### Post by cenwesi on 2008-05-22
Thanks for the reply. I believe i have this card working but NO Audio. Right i have comcast and the digital service. The digital box is NOT connected to my server/card. I just have the cable line split into two. One goes to my PVR500 MCE card and the other to the HVR-1800 (don't recall where it is plugged into). Anyway i installed the mercurial stuff and last night i noticed i didn't get sound out of the PVR500 or the HVR-1800. I uninstalled the mercurial stuff and re-installed the current v4l-dvb-9d04bba82511 driver off the [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/) site. No i have sound from the PVR500 MCE board but no video or sound off the HVR-1800. I will try the firmware update stated here to see if i get any lucky. 

[http://forums.fedoraforum.org/showthread.php?t=178654&page=3&pp=15](http://forums.fedoraforum.org/showthread.php?t=178654&page=3&pp=15)

---

### Post by beartard on 2008-05-23
One of us is confused.  The "mercurial stuff" *IS* the driver from linuxtv.org.  When you're dealing with the latest code snippets from the guys who're actually writing the drivers, what makes you think you're gonna get lucky elsewhere?  Just be patient.

---

### Post by MasterDuDe656 on 2008-05-29
Hello everyone, I have this card as well, and have been following this thread since when I bought this card. Is there any new news about this card and the analog tuner working? or at least any other functionality? I would like to get more then the digital tuner, and composite jacks to work so I could move my htpc over to mythbuntu or linuxmce, considering Vista doesnt support QAM as far as I know. :( :confused:

---

### Post by beartard on 2008-05-29
I try to keep up with the updates, reinstalling every few days.  So far the best we have is video via composite without audio (in addition to atsc).  The analog tuner still doesn't work.

---

### Post by cenwesi on 2008-05-30
I am getting to the point where i will soon YANK! this card out and  either sell it or throw it away. I also have the HVR-900 aka 950/980 and that too does NOT WORK!. That is a total of 3 tuners if you think about it. Currently my MCE500 works just fine and have being doing a damn good job.

---

### Post by beartard on 2008-05-30
Glad you got one working, at least.  I just wish manufacturers paid people to write Linux drivers, just like I presume they do for the guys who write Windows drivers.

I think we're doing great for a team of volunteers working in their spare time with little or no information about the chipsets involved.

---

### Post by MasterDuDe656 on 2008-05-30
> **cenwesi said:**
> I am getting to the point where i will soon YANK! this card out and  either sell it or throw it away. I also have the HVR-900 aka 950/980 and that too does NOT WORK!. That is a total of 3 tuners if you think about it. Currently my MCE500 works just fine and have being doing a damn good job.

Meh, things like this take time, and sometimes, unfortunately, sometimes over a year, its not like we are paying them to develop the drivers as far as I know, and besides, I think I can wait hopefully for a little while longer, rather then use vista x64 where this card doesnt want to function well at all. :popcorn: rather have a quality driver that work, with hopefully few bugs, then them rush a fully functional one for this card and it be horrid.

---

### Post by MasterDuDe656 on 2008-05-30
> **beartard said:**
> Glad you got one working, at least.  I just wish manufacturers paid people to write Linux drivers, just like I presume they do for the guys who write Windows drivers.

I think we're doing great for a team of volunteers working in their spare time with little or no information about the chipsets involved.

agreed

---

### Post by wasutton3 on 2008-06-03
keep up the good work, i look foreward to seeing the final driver

---

### Post by woodsby on 2008-06-05
What's funny is I've got analog tv working in tvtime with no audio, but I don't get composite video at all.  If I'm not mistaken I may have had to modprobe tuner or modprobe cx25840 to change channels.
One step further - if I cat /dev/video1 into a file, I get about 2 seconds of video, and then scrambled video, but the audio works fine.  This has been the case since I last investigated about 3 weeks ago.  This must mean they're getting close.

---

### Post by cenwesi on 2008-06-05
Did you try this with the new kernel [2.6.24-18] that was just released? I just can't believe i have this card in there and still cannot use it :(

---

### Post by woodsby on 2008-06-05
> **cenwesi said:**
> Did you try this with the new kernel [2.6.24-18] that was just released? I just can't believe i have this card in there and still cannot use it :(

I just did.  Now it seems worse.  I can't cat /dev/video1 anymore, although it still does exist.  Still no audio in tvtime.  Didn't have time at lunch to check out myth.

Edit: I forgot to mention, I re-installed v4l-dvb from the mkrufky repository

---

### Post by woodsby on 2008-06-05
I just noticed that the 2.6.25 adds analog support for the hvr-1800.  Has anyone tried this yet?

---

### Post by cenwesi on 2008-06-05
hmmm, how does one get kernel 2.6.25?

---

### Post by woodsby on 2008-06-05
I'll check it out tonight and if i get it working, i'll post how i did it.  If anyone else has tried it, please post so I don't waste the time.

---

### Post by cenwesi on 2008-06-05
please if you do, don't hesitate to post for we all are just pulling our head out.

---

### Post by beartard on 2008-06-06
That's good news.  I've never enjoyed compiling my own kernel, even though I've used Linux for years exclusively.  If it's supported in later kernels without mercurial repos, I'll be happy as well.

Keep in mind, if I remember correctly, that odd-numbered kernels are development-only.  Even-numbered kernels are for normal use.  You might be introducing instability into your system just to get analog video working on your tuner card.

Please keep us posted.

---

### Post by woodsby on 2008-06-06
I ran into a snag with the nvidia modules (and a few other things) and ran out of time last night.  I'll have to try to work through the problem again this weekend.  FYI, I run the RT kernel on my pc's so I was compiling with that patch; I'll try again without it this weekend - eliminate one more source of possible problems.  At least it doesn't take 10 hours to compile a kernel like it used to... the last time i was compiling kernels... 9 years ago.
Hey, one other thing i noticed is the cx23885 does appear to have it's own new module in the .25 kernel.
If anyone else has had success with this card and the .25 kernel, please post.

Edit: one more note... this is where I saw that the .25 kernel supports analog on the cx23885... in case you were wondering... [http://lwn.net/Articles/266704/](http://lwn.net/Articles/266704/)

---

### Post by wasutton3 on 2008-06-07
is the fm radio aspect of this card working? or has that yet to be even tackled?

---

### Post by beartard on 2008-06-07
The guys at linuxtv.org (who work on the drivers) tend to work on the features they need or want first.  I've heard it said about several cards that they have no intention of working on analog video, for example.  The 1800 isn't one of those, though ;).  I haven't heard anything about FM support at all.

I didn't try it with the last kernel update to come down the pike, but 2.6.24-19 includes ATSC support by default.  If you just need digital support, there's no need to use mercurial to install the drivers.  The new kernel, however, doesn't have any support for NTSC analog or composite (video or audio) built in.

---

### Post by dafoo21 on 2008-06-08
Ive tried all the latest steps (using mercial, copying the firmware to my /lib/firmware/kernel-version folder, modprobing the modules) and i still cant a "/dev/video0" folder. Ive done all the steps exactly. Help?

---

### Post by beartard on 2008-06-09
When you finished compiling the drivers (make) did you install them (sudo make install)?  The installer script does more than just copy the drivers over to /lib/modules.  It updates the system s o that it knows the new drivers are there.  Once that's done, you should just reboot and not worry about modprobing them.  They should be automatically loaded.  By the way, if a new kernel version comes out, you have to repeat the process.

---

### Post by beartard on 2008-06-09
Just playing around tonight.  They're getting closer   ;)  Still without audio for now.  I'm wondering if a script to pass audio to sox might work like it used to on older cards?
EDIT: Negative on the sox.  The drivers aren't creating a /dev/dspX for analog audio yet.

tvtime analog.                                          tvtime analog and kaffeine HDTV at the same time
[[IMG]http://img340.imageshack.us/img340/480/snapshot13gu0.th.jpg[/IMG]]("http://img340.imageshack.us/my.php?image=snapshot13gu0.jpg")[[IMG]http://img74.imageshack.us/img74/5606/snapshot14ri7.th.jpg[/IMG]]("http://img74.imageshack.us/my.php?image=snapshot14ri7.jpg")

---

### Post by dafoo21 on 2008-06-09
> **beartard said:**
> When you finished compiling the drivers (make) did you install them (sudo make install)?  The installer script does more than just copy the drivers over to /lib/modules.  It updates the system s o that it knows the new drivers are there.  Once that's done, you should just reboot and not worry about modprobing them.  They should be automatically loaded.  By the way, if a new kernel version comes out, you have to repeat the process.


Yeah, i did make and make install. Ive tried both restarting the computer and also just using modprobe...  I compiled the latest kernel that supports the cards analog features and that worked but i couldnt get my soundcard to be recognized and i just went back to the .24 kernel... I had to modprobe with the .25 kernel to get it to work but it still worked so I have had some success, but not with manually installing the firmware and modules on the .24 kernel. (And i did do the same steps for the the new .24-19 updated kernel. )

---

### Post by dafoo21 on 2008-06-09
Okay, now im at "good" static stage after a restart, but when i modprobe i can get a picture. How do i fix this to make it automatic?

---

### Post by beartard on 2008-06-09
It should still be automatic, but you can add the modules to the /etc/modules file, one line for each module.

---

### Post by loudnlownoma on 2008-06-12
Made a post in another thread, but glad to see I'm not the only one having this trouble.  Was finally able to get video from my Satellite tuner in tvtime with Hardy installed and using the S-video, but composite for audio isn't working.  Guess we are back to wait and see mode, but definitely nice to have some progress.  This is about the only thing holding me to using Vista with the dual-boot....

---

### Post by TomDaBomb2u on 2008-06-13
I haven't played with this in a while; been busy with school/ work. I opened TVTime last night, and couldn't even get a picture. Looks like I'm back to square one :-\. Tonight I'll probably go back through and reinstall/ recompile, or whatever I need to do lol.

---

### Post by bmwman on 2008-06-13
I just bought that same TV tuner yesterday. I cheked the linuxtv.org website and it shoul be fully supported. I haven't tried it yet since I was having problems with the MythTv software. Now I have that taken cared of and will be messing with the TV card tonight. Hope I didn't make a bad choice by purchasing it. 

Please let me know if it's a good card for MythTV or I should return it while I can and get something else?
Thanks

---

### Post by beartard on 2008-06-13
Heheh.  Read the above posts.

The drivers are being worked on.  Right now ATSC (hi-def) works fine, right out of the box.  So far we're able to get NTSC (analog) video on tv channels, composite, and s-video; however, this comes without audio so far.  The drivers aren't yet creating a /dev/dspX device for the analog portion of the card.

---

### Post by bmwman on 2008-06-16
> **beartard said:**
> Heheh.  Read the above posts.

The drivers are being worked on.  Right now ATSC (hi-def) works fine, right out of the box.  So far we're able to get NTSC (analog) video on tv channels, composite, and s-video; however, this comes without audio so far.  The drivers aren't yet creating a /dev/dspX device for the analog portion of the card.

How do you use the ATSC feature? I'm getting confused here. I have a COX cable and have digital channels. Of coarse you need to use either a cable box or a cable card which you put inside the TV, that's what I have now. When I plugged the cable to my HVR 1800 all I get is static. Then I booted into windows and used their crappy WinTV software and did a scan - I get like 45 channels (without the cable box), but they're all analog. Apparently all the digital Hi-Def channels that I get, i can only have thru the cable card or cable box. 

So in order to use MythTV with HVR-1800 i have to have a digital signal, which apparantly i can't have without having a cable box. If I get a cable box and connect to the TV tuner, i can only have one channel at a time, correct? So how am I going to record on one channel while watching another? Also I don't have any other antenna so I can't use the QAM or ATSC.

What should I do, please advice?

---

### Post by beartard on 2008-06-16
> **bmwman said:**
> How do you use the ATSC feature? I'm getting confused here. I have a COX cable and have digital channels. Of coarse you need to use either a cable box or a cable card which you put inside the TV, that's what I have now. When I plugged the cable to my HVR 1800 all I get is static. Then I booted into windows and used their crappy WinTV software and did a scan - I get like 45 channels (without the cable box), but they're all analog. Apparently all the digital Hi-Def channels that I get, i can only have thru the cable card or cable box. 

So in order to use MythTV with HVR-1800 i have to have a digital signal, which apparantly i can't have without having a cable box. If I get a cable box and connect to the TV tuner, i can only have one channel at a time, correct? So how am I going to record on one channel while watching another? Also I don't have any other antenna so I can't use the QAM or ATSC.

What should I do, please advice?

I can watch ATSC terrestrial tv via Kaffeine.  NTSC analog is via tvtime on my computer.

I'm not sure how hi-def cable works.  I haven't had a tv in years.  But I'm assuming the cable box sends either an analog signal or an ATSC signal to the card.  In that case, you'd be fine, one channel at a time, if it's ATSC.  If it's NTSC, you won't get any audio yetfrom the card.  It has always been possible to route the audio from the cable box to the sound card and try that route, but you'd have to use sox and tweak it so there's no delay between audio and video.  Of course, that'd be a temporary fix until the drivers give full analog support.

As far as watching two channels at a time (or recording one, watching another) I believe that's only watch analog/record digital or vice versa.  The card only contains one of each kind of tuner.

---

### Post by bmwman on 2008-06-16
Well, sounds like there is no way to use it right now unless I get a cable box. That realy sucks. It's not even a guarantee that the cable box will send a ATSC signal either. And let say I get a cable box, It sends digital signal and  i get it to work one channel at a time, how can I change the channels if my backend PC is in my spare bedroom/office and I'm watching TV from the living room? I know it should be possible, but how to make it work?

---

### Post by beartard on 2008-06-16
I'm gonna attempt an answer, but your setup is over my head, to be honest.

I know the remote control works with lirc (if it's the usb windows-mce remote).  Surely, the IR blaster would work as well.  Maybe a usb extension cable or a wireless extender module would help.  There might be a networked way to do it, but I couldn't help there.

---

### Post by edgesitter on 2008-06-17
You had mentioned that analog (NTSC) was working for you.  I followed your steps on a previous post and I do have static but nothing else.  Here is my lsmod, am I missing a module?
edgesitter@edgesitter-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  10 
xt_limit                3584  8 
xt_tcpudp               4096  10 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  0 
nf_conntrack_ftp       10144  0 
xt_state                3328  6 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
container               5632  0 
dock                   11280  0 
battery                14212  0 
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
mt2131                  6916  1 
s5h1409                10116  1 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
cx25840                30668  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
psmouse                40336  0 
serio_raw               7940  0 
cx23885                92348  0 
evdev                  13056  4 
snd_seq_midi            9376  0 
videodev               35072  1 cx23885
compat_ioctl32          2304  1 cx23885
cx2341x                13572  1 cx23885
videobuf_dma_sg        14980  1 cx23885
v4l1_compat            15748  2 cx23885,videodev
v4l2_common            12672  3 cx25840,cx23885,cx2341x
btcx_risc               5896  1 cx23885
tveeprom               13444  1 cx23885
snd_rawmidi            25760  1 snd_seq_midi
pcspkr                  4224  0 
videobuf_dvb            7812  1 cx23885
dvb_core               80508  1 videobuf_dvb
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
videobuf_core          19716  3 cx23885,videobuf_dma_sg,videobuf_dvb
nvidia               7825536  34 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  1 nvidia
soundcore               8800  1 snd
i2c_nforce2             7680  0 
i2c_core               24832  8 mt2131,s5h1409,cx25840,cx23885,v4l2_common,tveeprom,nvidia,i2c_nforce2
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
button                  9232  0 
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
sata_nv                27528  2 
floppy                 59588  0 
ehci_hcd               37900  0 
pata_amd               14212  0 
forcedeth              51980  0 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 pata_acpi,sata_nv,pata_amd,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci_hcd               25348  0 
usbcore               146028  4 usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
edgesitter@edgesitter-desktop:~$ 

thanks edgesitter

---

### Post by beartard on 2008-06-18
That's a lot to look through.  Just a quick glance, I see the "tuner" module is missing.

(sudo modprobe tuner)

---

### Post by wasutton3 on 2008-06-25
i noticed that the 2.6.26 kernel is in progress. does anyone know if the same fixes from 2.6.25 are built into .26 and if so, when ubuntu might be getting either?

---

### Post by MasterDuDe656 on 2008-06-29
any new updates on sound through NTSC? or no luck as of yet? :confused:

---

### Post by rattletyboom on 2008-06-29
I'm also waiting for the audio for the uncompressed stream to be enabled, but I wanted to point out that the mpeg2 stream on /dev/video1 does include the audio from analog sources. Hardware mpeg2 encoding was the main reason to choose this card anyway. The only sofware I could get to work to both tune and watch /dev/video1 is MythTV. For me this is working well - although MythTV isn't as stable as I'd like, now I've got a working setup with both digital and analog channels available in a nice interface. 

It appears that xine should also be able to tune analog channels and watch the compressed stream, but I wasn't able to figure out how to set it up.

---

### Post by MasterDuDe656 on 2008-06-30
how exactly did you set it up in mythtv? I tried mpeg2 and analog video and neither would recognize /dev/video1/ :confused:

---

### Post by MasterDuDe656 on 2008-07-01
nevermind, I forgot to build the modules and add them too /etc/modules, but still not sure which device to use. I tried MPEG2 but it shows the default device as "unset" although it accurately display which channels I actually have, help please! :D I really want away from Vista as a HTPC :(

---

### Post by rattletyboom on 2008-07-06
I have /dev/video1 configured as an MPEG-2 encoder, which then gives Probed info: Hauppauge WinTV-HVR1800 [cx23885[0]]. The Default input is stuck on unset, but it works that way (I'm not sure how to select the composite input). The DVB DTV card also works for over the air ATSC channels, and both tuners can run simultaneously.

"Watch TV" often doesn't work the first time, so I have to push it several times and cross my fingers to watch live. Sometimes the tuner also gets out of whack on the analog channels (wavy, distorted video), but running TVTime seems to get a lock on the channels, then I start Myth back up and it works. If I figure out any other tricks I'll post them.

---

### Post by cubdukat on 2008-07-14
> **murchball said:**
> Mythbuntu is it's own distro, but you can install a full desktop on it. In Mythbuntu-control-centre, just select the Gnome desktop role. Conversely, if you already have a desktop ubuntu installation, you can install Mythbuntu-control-centre and all of the other myth goodies to get the same result.

I also have an HVR-1800 that came with a computer I bought. I played with it for an hour or so before giving up. I believe that it is fully supported by MythTV, but getting it running on Ubuntu is not an out-of-the-box experience. I would think that 8.10 will probably support it much better.

Perhaps, but I daresay that half the support problem is with Hauppauge itself. They claim that it's supported in the current kernel and they provide links to the V4L driver you're supposed to use. What they don't tell you is that if you have an Nvidia graphics card, you will end up borking your system so bad that you will either be stuck at VGA resolutions or you will need to reinstall Ubuntu. 

For some bizarre reason, Hauppauge has been dragging their heels with Linux support for any of their ATSC tuner cards. I have an HVR-1600, and I have given up any hope of getting it going in Hardy. Maybe they will get it right for Intrepid, but until then...I'm stuck with Vista. UGH! Kinda makes me wanna throw up in my mouth a little bit.

Okay, a lot...

---

### Post by wasutton3 on 2008-07-20
would it be a safe assumption that this would work in intrepid?
or is even then a gamble?

---

### Post by beartard on 2008-07-21
Most of the people trying this out are using the drivers from the linuxtv.org repositories that are bleeding-edge.  If the devs work out the bugs, you'll hear it here.  These drivers at linuxtv.org are the ones that eventually make it into the kernel itself....so if it makes it into the kernel that intrepid ships with, then yes.  It's not something that's really distro-dependent.

---

### Post by TomDaBomb2u on 2008-07-23
OK guys, I'm tired of waiting on these HVR 1800 drivers to get right. The card doesn't even perform satisfactorily in Windows for me. 

What's a suitable (temporary (cheap!)) stand-in that's 100% Ubuntu compatible? Just in the interim (hopefully) until these drivers are completed. . .

---

### Post by reeseslover531 on 2008-07-23
ya I really hope they get audio working soon cause I want to use the s-video to play my PS2!

---

### Post by jaymode on 2008-08-04
I am running 8.04 and am having a hard time even with the digital side of this card :(. I tried various versions of MythTV and got it to work once but now it just fails when trying to view a channel.

I get an error about NVP could not open file on the MythTV side. There are not any errors in dmesg. The file that is created is very small (<1mb).

---

### Post by benrboone on 2008-08-07
I have been able to get the digital side of the car to work with me-tv.  However it was not the version in repositories.  Instead I added these lines to me sources.

deb [http://ppa.launchpad.net/lamothe/ubuntu](http://ppa.launchpad.net/lamothe/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/lamothe/ubuntu](http://ppa.launchpad.net/lamothe/ubuntu) hardy main

and installed version 0.5.30-1 It seems to work pretty good.  The original one 0.5.17 I think, had a bug that wouldn't let it past the channel scan so it would start.

---

### Post by orphean on 2008-08-09
Looking into the mercurial log the last cx23885 commit was on the July 1st.  The last HVR-1800 specific commit was on January, 13th.

Not looking good for analog audio support. So frustrating, its so close to actually working. *shakes fist*

---

### Post by beartard on 2008-08-09
Yeah.  It's a well-known fact that the linuxtv devs only work on the features they want.  Maybe analog support isn't important to them ;)

---

### Post by jaymode on 2008-08-10
> **jaymode said:**
> I am running 8.04 and am having a hard time even with the digital side of this card :(. I tried various versions of MythTV and got it to work once but now it just fails when trying to view a channel.

I get an error about NVP could not open file on the MythTV side. There are not any errors in dmesg. The file that is created is very small (<1mb).

I fixed my errors. I was trying to tune an encrypted channel. 

About the analog support, have the audio issues/bugs actually been posted/sent to the LinuxTV developers? I did a quick search over the mailing list and all I have seen is from back in January.

---

### Post by jaymode on 2008-08-13
Did some more searching on the mailing list and the devs seem to think it is working fine:
[http://linuxtv.org/pipermail/linux-dvb/2008-June/026666.html](http://linuxtv.org/pipermail/linux-dvb/2008-June/026666.html)

I haven't tried to get analog working yet but maybe someone that has can report it?

---

### Post by jaymode on 2008-08-17
Ok so I bit the bullet and upgraded to 8.10 development today. I was having too many freezing issues with 8.04 so I just decided to go ahead and upgrade to see if I could get the analog  to work. Installed it and then extracted the firmware ([http://steventoth.net/linux/hvr1800/](http://steventoth.net/linux/hvr1800/)). I placed the files in both /lib/firmware and then made a directory 2.6.25.2-generic and also copied the files in there and rebooted.

Powered up tvtime but no audio on any of my tuner cards :-(. BUT then I tried to cat and audio was working!!! 

So now on to getting it to work with mythtv. I still have not been successful with video or audio on the latest SVN.

---

### Post by orphean on 2008-08-18
What are you cat'ing? /dev/video0 or /dev/video1?  I get audio from the mpeg stream from video1 but the picture is very staticy and rolling.  tvtime picks up the video signal from video0 just fine but no audio. I have yet to get mythtv to work with either.

---

### Post by beartard on 2008-08-18
how do you determine which input/channel gets through to /dev/video1?

---

### Post by jaymode on 2008-08-18
I am cat'ing /dev/video1. The driver is very bad. It works some times and not the other. As far as input selection I believe the tuner is the only option in the current driver. I set it up as an MPEG (pvr-150) card in mythtv and got it to work a couple times, but after that the video was very poor. Hoping for some progress on the driver. I believe the audio issues are more of a tvtime and ubuntu problem. I couldn't get it to work with another card that does use the IVTV driver, which I know works well.

This is a post I made on another forum:
> Ok so don't get this card for analog. I have tested it and I believe the driver still needs a lot of work. The card works ok with tvtime, sometimes. It is very iffy about working. I get the following errors in dmesg:
```

[  925.531792] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xffffffff, cmd = STOP_CAPTURE
[  926.796603] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xffffffff, cmd = PING_FW
[  926.796664] firmware: requesting v4l-cx23885-enc.fw
[  967.482186] __ratelimit: 3 messages suppressed
[  967.482186] mythbackend[6531]: segfault at 144 ip b7daba2d sp ac36af40 error 4 in libmythtv-0.22.so.0.22.0[b7547000+a88000]
[ 1248.983663] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0x0, cmd = PING_FW
[ 1248.983724] firmware: requesting v4l-cx23885-enc.fw
[ 1347.280600] mythbackend[6622]: segfault at 144 ip b7d97a2d sp ab0c3f40 error 4 in libmythtv-0.22.so.0.22.0[b7533000+a88000]


```

Myth gives me the following output:
```

2008-08-18 18:44:29.335 TVRec(1): Changing from None to WatchingLiveTV
2008-08-18 18:44:29.340 TVRec(1): HW Tuner: 1->1
2008-08-18 18:44:30.690 Channel(/dev/video2) Error:
InitPictureAttribute(brightness): failed to query controls.
           eno: Invalid argument (22)
2008-08-18 18:44:31.781 Channel(/dev/video2) Error:
InitPictureAttribute(brightness): failed to query controls.
           eno: Invalid argument (22)
2008-08-18 18:44:31.781

Not ivtv or pvrusb2 or hdpvr driver


2008-08-18 18:44:31.783 MPEGRec(/dev/video2) Warning: Unable to get
recording volume parameters(max/min)
           eno: Invalid argument (22)
           using default range [0,65535].
2008-08-18 18:44:31.792 AutoExpire: CalcParams(): Max required Free Space:
2.0 GB w/freq: 15 min
2008-08-18 18:44:33.021 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.022 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.023 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.023 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.024 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.024 DevRdB(/dev/video2) Error: Problem reading fd(34)
           eno: Input/output error (5)
2008-08-18 18:44:33.027 MPEGRec(/dev/video2) Error: Device error detected
2008-08-18 18:44:33.027 DevRdB(/dev/video2) Error: Stop(): Not running.
2008-08-18 18:44:33.027 MPEGRec(/dev/video2) Error: StopEncoding
           eno: Invalid argument (22)

```

I have passed this along to the linux dvb mailing list. Hopefully this will help spur some development on this driver.

---

### Post by beartard on 2008-08-19
I gotta confess I'm seriously considering finding another solution.  The ATSC side works as well as can be expected on the dirver side.  I wish there were better software support for ATSC, though.  Something easy-to-configure without installing a full-blown mythtv would be nice.

I mainly wanted the card as an attachment point for the occasional video game system via composite.  If I can't use that function, it's not really much use at all to me.

---

### Post by jaymode on 2008-08-20
> **orphean said:**
> What are you cat'ing? /dev/video0 or /dev/video1?  I get audio from the mpeg stream from video1 but the picture is very staticy and rolling.  tvtime picks up the video signal from video0 just fine but no audio. I have yet to get mythtv to work with either.

Orphean and anyone else willing to post feedback to the linux dvb mailing list,

Would you mind looking through this [thread]("http://linuxtv.org/pipermail/linux-dvb/2008-August/027913.html") on the mailing list and trying the steps provided by Steven Toth (one of the devs). We currently have gotten his attention and I think it would be better for others to also provide feedback in hopes that it spurs some sort of action on the driver for this card.

---

### Post by beartard on 2008-08-20
For what it's worth, I just subscribed to the listserv.  I can cat /dev/video1 and get video and audio.  I'm intrigued.

---

### Post by jaymode on 2008-08-21
beartard, I was excited too when it first worked but then after that it will stop working when you change the channels a couple of times or at least it did for myself and others. Keep us and the mailing list updated.

---

### Post by DemonBob on 2008-08-24
Lastest message i got from the DEV. 

> I've noticed a few posts but I'm not able to test or try and repro the 
problem. It sits on my todo list until I have a PCIe development system.

- Steve


[http://linuxtv.org/pipermail/linux-dvb/2008-August/028107.html](http://linuxtv.org/pipermail/linux-dvb/2008-August/028107.html)

---

### Post by LavianoTS386 on 2008-08-27
Whenever I use me-tv all I get is "Failed to tune to transponder"?

---

### Post by DemonBob on 2008-08-29
Anyone try this card with Intrepid, and kernel 2.6.27 yet?

---

### Post by waltclay on 2008-09-02
I see newegg has card/remote on sale [http://http://promotions.newegg.com/NEemail/Sep-0-2008/Promo090208in/index-landing.html?nm_mc=EMC-IGNEFL090208&cm_mmc=EMC-IGNEFL090208-_-email-_-E0-_-HAP]("http://promotions.newegg.com/NEemail/Sep-0-2008/Promo090208in/index-landing.html?nm_mc=EMC-IGNEFL090208&cm_mmc=EMC-IGNEFL090208-_-email-_-E0-_-HAP")
so I have looked through the last few pages of this thread and found no evidence that it works with mythbuntu.

Please correct me if I am wrong.

---

### Post by waltclay on 2008-09-02
Re: Hauppauge WinTV-HVR 1800
I see newegg has card/remote on sale [http://promotions.newegg.com/NEemail/Sep-0-2008/Promo090208in/index-landing.html?nm_mc=EMC-IGNEFL090208&cm_mmc=EMC-IGNEFL090208-_-email-_-E0-_-HAP](http://promotions.newegg.com/NEemail/Sep-0-2008/Promo090208in/index-landing.html?nm_mc=EMC-IGNEFL090208&cm_mmc=EMC-IGNEFL090208-_-email-_-E0-_-HAP)
so I have looked through the last few pages of this thread and found no evidence that it works with mythbuntu.

Please correct me if I am wrong.
Last edited by waltclay; 2 Minutes Ago at 01:03 PM. Reason: disfunctional link 

[Try to get edit to stick by reposting.]

---

### Post by LavianoTS386 on 2008-09-09
> **DemonBob said:**
> Anyone try this card with Intrepid, and kernel 2.6.27 yet?

It works out of the box (ATSC) with me-tv.

---

### Post by cenwesi on 2008-09-15
> **LavianoTS386 said:**
> It works out of the box (ATSC) with me-tv.

Is this with Ubuntu Hardy?. Did you have to recompile the kernel?? if so can you send me your .config file.

Thanks.

---

### Post by beartard on 2008-09-15
It works out of the box on ATSC for just about everybody.  I had some bootup freezes caused by the new kernel intrepid is using.  Haven't really noticed much else.

---

### Post by croxis on 2008-09-17
I have composet working using the latest v4l drivers and tvtime in intrepid.  My current issue is trying to save the stream from my camcorder through the card.  Anything that is suppose to be able to do this doesn't work or the video is funky (vlc).

---

### Post by kpaden on 2008-09-19
I installed Intrepid on a AMD64 box. It was blowing up all over the place. I went back to Hardy, and tried kernel 2.6.27, and could not get it to compile with my configuration. It is still a pre-release kernel after all. I am now running 2.6.26. No sound yet.

---

### Post by Robstarusa on 2008-09-24
I installed this card in a hardy x86_64 server.

I then put grabbed stock kernel 2.6.26.5, copied the .config out of the /boot directory, "make oldconfig && make -j 18" and then followed the steps on the kernel newbies list.  I installed the kernel and then grabbed the appropriate firmwares for the card (google around) and put them in /lib/firmware/2.6.26.5/

```

-rw-r--r--  1 root root 262144 2008-09-23 13:48 v4l-cx2341x-dec.fw
-r--r--r--  1 root root  16382 2008-09-23 14:05 v4l-cx23885-avcore-01.fw
-r--r--r--  1 root root 376836 2008-09-23 14:05 v4l-cx23885-enc.fw
-rw-r--r--  1 root root  16382 2008-09-23 13:48 v4l-cx25840.fw
-rw-r--r--  1 root root   8192 2008-09-23 13:48 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root   8192 2008-09-23 13:48 v4l-pvrusb2-29xxx-01.fw

```

I was able to get a picture (no speakers here so haven't tested audio) on the composite in but it was corrupted (I only tried vlc via x-forwarding reading /dev/video[01]

My next shot is to try taking my video source & using the "rf out" (channel 3/4) instead and seeing if that works.

I will post here if I get it working.

---

### Post by Robstarusa on 2008-09-24
RF out from my video source gives the same corruption as composite in :(

Black/Green/Purple picture.  I can make out faces, lines, read text etc, but the colors are seriously messed up.

---

### Post by mosquitogang201 on 2008-09-30
Has anyone gotten the fm tuner to work or know if radio support is planned?

---

### Post by manro on 2008-09-30
I read at LinuxTV that analog hardware mpeg encoder requires kernel 2.6.26 ... did anyone success on this. Does this analog hardware mpeg econder means *"analog TV (standard cable TV)"*? ... Thanks! ;)

---

### Post by madddddman on 2008-10-01
Greetings. I just tried to clone using  hg clone [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)
but now I am getting the following errors:

user@user desktop:~$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
requesting all changes
adding changesets
transaction abort!
rollback completed
** unknown exception encountered, details follow
** report bug details to [http://www.selenic.com/mercurial/bts](http://www.selenic.com/mercurial/bts)
** or [email]mercurial@selenic.com[/email]
** Mercurial Distributed SCM (version 0.9.5)
Traceback (most recent call last):
  File "/usr/bin/hg", line 14, in <module>
    mercurial.dispatch.run()
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 20, in run
    sys.exit(dispatch(sys.argv[1:]))
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 29, in dispatch
    return _runcatch(u, args)
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 45, in _runcatch
    return _dispatch(ui, args)
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 348, in _dispatch
    ret = _runcommand(ui, options, cmd, d)
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 401, in _runcommand
    return checkargs()
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 357, in checkargs
    return cmdfunc()
  File "/var/lib/python-support/python2.5/mercurial/dispatch.py", line 342, in <lambda>
    d = lambda: func(ui, *args, **cmdoptions)
  File "/var/lib/python-support/python2.5/mercurial/commands.py", line 417, in clone
    update=not opts['noupdate'])
  File "/var/lib/python-support/python2.5/mercurial/hg.py", line 217, in clone
    dest_repo.clone(src_repo, heads=revs, stream=stream)
  File "/var/lib/python-support/python2.5/mercurial/localrepo.py", line 1978, in clone
    return self.pull(remote, heads)
  File "/var/lib/python-support/python2.5/mercurial/localrepo.py", line 1371, in pull
    return self.addchangegroup(cg, 'pull', remote.url())
  File "/var/lib/python-support/python2.5/mercurial/localrepo.py", line 1849, in addchangegroup
    if cl.addgroup(chunkiter, csmap, trp, 1) is None:
  File "/var/lib/python-support/python2.5/mercurial/revlog.py", line 1186, in addgroup
    textlen = mdiff.patchedsize(textlen, delta)
mpatch.mpatchError: patch cannot be decoded

I tried to find a link to report a possible problem with this repo but could not so I am posting it here in the hopes someone can correct the problem. Thanks!!

---

### Post by Robstarusa on 2008-10-02
I have 2.6.26.5 kernel installed along with the latest v4l-dvb app and dvb-apps.

I get nothing but static.....I am using vlc to view and throwing the x display through ssh.

This is on a server w/o gui that is going to be resizing the video & sending it out multicast, so I don't have a local gui to work with.

Has anyone got this working?  I am using analog inputs only.

Rob

---

### Post by DemonBob on 2008-10-02
Nope, and not getting any help from the developer of the driver either. It's starting to piss me off. It's pretty much a 140 dollar paper weight to me, since i don't have use for OTA Digital...

---

### Post by manro on 2008-10-07
I just installed Intrepid Ibex beta x64 (2.6.27-4-generic) and surprise!!! ... I can watch 1 (yes ONE) analog channel (the last one I was watching on winblow$). Still no sound but is one step (big one) forward from what I was. I try to scan for active channels but ***tvtime*** just go through all channels without changing the one is already tuned.

If someone have any suggestion about something I should try please let me know!

Here's some data:

```
manro@manro-desktop:~# dmesg | grep cx
[   14.408937] cx23885 driver version 0.0.1 loaded
[   14.409350] cx23885 0000:08:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   14.409413] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   14.568283] cx23885[0]: i2c bus 0 registered
[   14.568303] cx23885[0]: i2c bus 1 registered
[   14.568320] cx23885[0]: i2c bus 2 registered
[   14.595015] cx23885[0]: hauppauge eeprom: model=78521
[   14.603283] cx25840' 4-0044: cx25  0-21 found @ 0x88 (cx23885[0])
[   14.603886] cx23885[0]/0: registered device video0 [v4l2]
[   14.607518] firmware: requesting v4l-cx23885-avcore-01.fw
[   14.651224] cx25840' 4-0044: unable to open firmware v4l-cx23885-avcore-01.fw
[   14.664775] cx23885[0]: registered device video1 [mpeg]
[   14.664779] cx23885[0]: cx23885 based dvb card
[   14.792146] DVB: registering new adapter (cx23885[0])
[   14.792481] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   14.792487] cx23885[0]/0: found at 0000:08:00.0, rev: 15, irq: 16, latency: 0, mmio: 0xfd800000
[   14.792492] cx23885 0000:08:00.0: setting latency timer to 64
manro@manro-desktop:~#
```Best regards,
MaNRo ;)

---

### Post by cenwesi on 2008-10-07
what about with the latest Kernel just released 2.6.27-5?

---

### Post by manro on 2008-10-07
> **cenwesi said:**
> what about with the latest Kernel just released 2.6.27-5?

Same thing! :???:

---

### Post by Robstarusa on 2008-10-10
Manro>  save us the suspense & tell us which analog input (composite? tuner?) actually works, as well as w hich channel is working :)

If it is the tuner + channel 3 or 4, I might actually try a new kernel.

Right now I'm hesitant with the e1000e issues.

---

### Post by manro on 2008-10-10
> **Robstarusa said:**
> Manro>  save us the suspense & tell us which analog input (composite? tuner?) actually works, as well as w hich channel is working :)

If it is the tuner + channel 3 or 4, I might actually try a new kernel.

Right now I'm hesitant with the e1000e issues.
 
Sure...I'll try a few things later tonight (it's almost 2pm here in Costa Rica and I'm still at work) and let you know the results! ... for now I have to say that I was wrong about the channel I thought was the last one tuned on Winblow$ ... the channel that is always tuned on Linux is number 20.

I haven't test the composite but I sure will! ;)

Regards,
Manro

---

### Post by MoonBlossom on 2008-10-10
My HVR-1800 started to work on Intrepid Ibex 2.6.27-7-generic after 

sudo modprobe tuner

I got that from this link:

[http://linuxtv.org/v4lwiki/index.php/Tuners:_Supported_Tuners#Hauppauge_WinTV_devices](http://linuxtv.org/v4lwiki/index.php/Tuners:_Supported_Tuners#Hauppauge_WinTV_devices)

Using TvTime I can see the picture but I'm not getting any sound :(

I would also appreciate if anyone knows how to configure the radio and remote control for this card.

---

### Post by manro on 2008-10-11
OK, here's the deal!

I updated to the last kernel ( 2.6.27-7-generic) ... did the ***mopdprobe turner*** thing (THANKS **MoonBlossom**) and now I can change channels!!! :) ... everything looks pretty good, sharp image and everything...but still NO SOUND! :-?

So far we are going good...very very close to a happy ending I believe/hope :wink:

Any help will be greatly appreciated!

Regards,
MaNRo

---

### Post by MoonBlossom on 2008-10-11
I got sound!!! Not the best way but it works :KS
I opened TvTime normally (no sound)
Then in console I did this 

mplayer /dev/video1

It opens mplayer in another window with the channel I have in TVTime but with sound :) I don't know if there is a way to make TvTime use /dev/video1 instead on /dev/video0 :( Let's hope somebody else figures a better way to make this Tunner work :)

You may need the firmware from this post: [http://www.linuxtv.org/pipermail/linux-dvb/2008-January/023137.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-January/023137.html)

Direct link: [http://steventoth.net/linux/hvr1800/](http://steventoth.net/linux/hvr1800/):popcorn:

---

### Post by manro on 2008-10-14
MoonBlossom

Maybe this is what you're looking for:
```
tvtime --device=/dev/video1
```Just say that I try it without any results! :(

Regards,
MaNRo

---

### Post by MoonBlossom on 2008-10-14
> **manro said:**
> MoonBlossom

Maybe this is what you're looking for:
```
tvtime --device=/dev/video1
```Just say that I try it without any results! :(

Regards,
MaNRo


Yes, it doesn't seems to work :(

I heard Kaffeine can play TV but I haven't been able to configure it yet (I'm using 0.8.7). So far the only programs that work for me are TvTime and Mplayer. Hopefully someone more experienced in these things may find a solution :)

---

### Post by LavianoTS386 on 2008-10-14
I got this output:

> videoinput: Driver refuses to set norm: Invalid argument

---

### Post by kpaden on 2008-10-19
The first clue was this e-mail I received from Hauppauge Technical Support.

&#8220;If the user is using the first video device ( /dev/video0 ) that is raw analog video, audio currently not supported.
Instead, let the user use the SECOND video device ( /dev/video1 ) -- that is hardware mpeg2 encode audio + video program stream.&#8221;

First get all of the right kernel modules loaded. Second, activate MPEG2 support for mplayer. Then use tvtime on /dev/video0 to tune to the desired channel. Once the channel you want is tuned in, then use mplayer on /dev/video1 because only /dev/video0 will let you change channels. 

My sound cards driver is not the greatest, so I have problems syncing Audio and Video, but this incantation seems to work for about an hour at a time.  :-D

 mplayer /dev/video1 -vo x11 -nobps -autosync 30 -forceidx -hardframedrop -vc ffmpeg12 -idle -menu  -cache 16384  -cache-seek-min 50 -mc 0 -ni 


--Go forth and compute  :-D

---

### Post by orphean on 2008-10-23
After upgrading Ibex I've been able to cat /dev/video1 and get sound and video.  Can't get it working with mplayer yet but still a huge step forward!

Getting excited :)

---

### Post by cenwesi on 2008-10-23
> **orphean said:**
> After upgrading Ibex I've been able to cat /dev/video1 and get sound and video.  Can't get it working with mplayer yet but still a huge step forward!

Getting excited :)

hmmm i am running ibex and i need to check again. I am also running mythtv.

---

### Post by orphean on 2008-10-23
It's a bit finicky but i've been able to use kpaden's incantation successfully and i'm watching (and hearing!) the morning news now via mplayer.

I tried to get mythtv working but couldn't get it going, if you have any success there I'd love to hear it!

Right now I use tvtime to change the channel so it's pretty janky but the fact that it works AT ALL is quite amazing at this point for me.

---

### Post by orphean on 2008-10-23
I got tired of opening tvtime everytime I wanted to change a channel so I bothered to learn how to do it from the commandline.  Turns out ivtv-tune does the trick.

But since I'm really lazy and don't always want to open a terminal to change the channel I just whipped up this tiny app: JankyTv.

It's dirt simple. One button will launch mplayer with the correct settings to stream off of /dev/video1 and then there's a spin button which lets you change the channel.

I will probably stuff this all into a tray icon at some point but for those interested here is the result of an hour's work (or real work shirking depending on your point of view).

Things you need installed:
ivtv-tune
mplayer
gnome-devel (sorry, no deb yet have to compile it)
build-essential

Once those are on its just your usual ./configure, make, make install.

Doubt anyone else cares but figured if I found it useful there might be one or two others as well.

Edit: Helps if I upload a non-broken dist tarball. Fixed now! ;)

---

### Post by MoonBlossom on 2008-10-23
Thank you!

I'll try it :popcorn:

---

### Post by kreucher on 2008-10-24
I'm getting alot of these messages:

[675173.513406] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xffbfedfd, cmd = SET_OUTPUT_PORT

Using latest v4l-dvb hg tree and 2.6.24-21 (hardy) on amd64...

Anyone get past this?
Thanks!

---

### Post by wasutton3 on 2008-10-25
so the question remains. will this be able to work properly in hardy or will it be backported later?

---

### Post by wasutton3 on 2008-10-27
i have followed the above instructions for intrepid, but i cant seem to get audio to work, the incantation described doesnt start mplayer for me. any ideas?

---

### Post by kpaden on 2008-10-31
Drat!!!! Intrepid seems to have broken my incantation. Oh well, back to the Laboratory. :-P

---

### Post by Nativedude on 2008-11-02
Has there been any update to this
I'm sorta new to this:
so far I can get video through the s-video with tvtime
but can't get the tuner to show anything but static
and of course have no audio at all

I've been scouring all different forums looking for something and am at a loss

---

### Post by LavianoTS386 on 2008-11-04
I've been getting random system lockup when I use either the ATSC tuner with me-tv or svideo with tv time. Anybody else?

---

### Post by kpaden on 2008-11-04
I can get mplayer to play audio, but no video.  :-P


I am taking a break from the laboratory. I added all the crazy stuff again like libdvdcss, and loaded all the modules like tuner. I then recompiled mplayer. Now I can run tvtime against /dev/video0, and mplayer against /dev/video1 concurrently. The problem is that audio, and video are not synchronized. The problem seems to be with mplayer. Still working on it. :guitar:

---

### Post by Nativedude on 2008-11-04
Ok sweet!
Just make sure not to forget us when you get it working ;)

---

### Post by kpaden on 2008-11-05
> **Nativedude said:**
> Ok sweet!
Just make sure not to forget us when you get it working ;)

How about this?

I sucessfully used this incantation
/usr/bin/mplayer /dev/video1 -autosync 30 -forceidx -framedrop -idle -cache 16384 -mc 0 -ao alsa


/etc/modules
fuse
lp
rtc
sbp2
tuner
bttv
cx18
cx88_alsa


/etc/mplayer/mplayer.conf
vo=xvmc,xvidix,cvidix
vc=ffmpeg12mc
zoom=yes
ontop=yes
ao=alsa
mixer = /dev/line
ac=ffmp2
framedrop = yes
cache = 8192
alang = en
stop-xscreensaver = "yes"
nojoystick = yes


:guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by theduke88 on 2008-11-08
**Note** **I haven't been back to check on this posting in a while and some things have changed in Ubuntu/Jaunty.  My upgrade went poorly and it required removing all the cards and re-adding before my scheduler would work properly.  My There have been updates in this thread, but I don't want to leave people confused with this slightly out of date info -- In particular you probably want to read: [http://ubuntuforums.org/showpost.php?p=6899234&postcount=168](http://ubuntuforums.org/showpost.php?p=6899234&postcount=168).  I understand this card pretty much works out of the box with slight configuration in Jaunty, so this might be old news**

It took a few days for me to get things running, but thanks to forum posts I have MythTV working on my Hauppauge HVR-1800 with both NTSC and ATSC/QAM (OTA HD) tuners, video output from HDMI on an ATI HD 3450, with both OpenGL working as the painter in real full-screen mode, and sound being played in digital 5.1 via passthru on the HDMI link.  The remote/USB kit my package came with works flawlessly too.

Here were the changes that needed to be made, differing from a 8.10 default Intrepid Ibix install.  I used the x86_64 version for my particular hardware, but there should be no changes for 32b that I can see.
[LIST]
[*]During the install process, you want to use the newer USB Microsoft Media Center settings for the remote (Philips et al)

[*]Setup ubuntu to use the fglrx driver from the restricted drivers configuration.

[*]The v4l-dvb drivers need to be pulled from the mercurial archive, and compliled.  You will need to first install build-essentials and some other development packages for these to compile cleanly (must be done as root, I "sudo su -" first):
[/LIST]

```

cd /usr/local/src
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb

make && make install
```

I have in /etc/modules:

```
fuse
lp
rtc
sbp2
tuner
```

[LIST]
[*]Reboot the machine so all those drivers/settings come up.

[*]When you setup mythtv under capture cards, you want to setup the ATSC/QAM tuner as a dvb type, and ignore that it fills in the wrong looking data.  If you want NTSC to work, setup the card as an MPEG4 card and type the /dev/video0 device in the device field.  You will end up with two video devices.  Be sure to scan using the dvb card with dvb settings to add channels when in the video source setup.  On my dvb scan it took a long time and looked like it was only failing (the signal sat at 0% the whole time, but sometimes the screen would go from unlocked to locked and it'd pick up a channel). ATSC/QAM is the 'Antenna' input.  The NTSC scan is pretty normal looking -- my signal stayed at 99% the whole time and I ended up with grainy looking analog OTA on the 'Cable' input after I hooked up an antenna.
[/LIST]

These seem to help when placed in the /etc/X11/xorg.conf file in the 'Devices' section:

```
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "on"
        Option "TexturedVideo" "on"
        Option "TexturedVideoSync" "on"
        Option "Textured2D" "on"
        Option "BackingStore" "on"
        Option "UseFastTLS" "1"
        Option "XAANoOffscreenPixmaps" "on"
```

[LIST]
[*]This one took me forever to figure out -- I'd only get video corruption and strange crashing until this variable was defined before launching mythfrontend.  Before this flag was set, another problem was that the frontend would seem to hang on almost every menu option unless I was running the QT painter or in a window:
[/LIST]

```
export LIBGL_ALWAYS_INDIRECT=1
```

or 

```
declare -x LIBGL_ALWAYS_INDIRECT=1 && mythfrontend
```

Personally, I've modified the mythfrontend.sh caller script to set the variable on bootup.
[LIST]
[*]configure MythTV digital audio to work over HDMI:
[/LIST]
At this point, everything but sound should work.. I had some trouble figuring this part out.  If you use the alsa-utils 'aplay' program, ALSA will show you what it sees for audio devices on the system:

```

root@teevee:~# aplay -L -l
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

root@teevee:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

The important values are the # after card, and the # after device in the first line under the header.  In this instance, our values are 0 and 3.

Your audio device that needs to be specified in the General tab (2nd page) would then be ```
ALSA:plughw:0,3
``` and you will need to type this into the device section.  In the passthrough section, leave the setting as default, and be sure to enable passthru for anything your reciever can handle.

First you will need to unumte your card (press 'M' to mute/unmute) -- run this in a terminal:
```

alsamixer -c 0 

```

You can test this setting with some white noise by executing (be sure to turn the volume down first) -- run this in a terminal:
```

speaker-test -D plughw:0,3
```

And that was pretty much it.  MythTV is fantastic now that it works, but was not fun to spend a week getting to work.  If I did it again, I would not get a Hauppauge 1800 card, as the support is pretty bad, and I would also not run an ATI HDMI card, even though it's very nice to have a fanless HDMI with OpenGL setup on these dirt-cheap HTPC cards.  ATI driver support is the worst, and It took hours to find the LIBGL_ALWAYS_INDIRECT option... MythTV would just crash all the time with a segfault prior to that.  Running with the QT painter or running in a window are the best options while debugging all the ATI garbage (see mythfrontend --help).

Next I will try to make this machine control a Motorola DVR cablebox over firewire, wish me luck as I will need it!

**EDIT:**Some cleanup & additions, and also to mention: I should have known better than to get an ATI card.  The screen tearing is horrible (*STILL* a problem on **any **ATI card with any driver due to lack of proper vsync), even after fiddling with resolutions in my xorg config to get X & myth running at the native resolution of my TV.  I can live with it, but I'm going to have to save up for ANY nVidia card with HDMI to use instead.

---

### Post by Riffer on 2008-11-10
Ok how do you load those modules?  Or even install them?

---

### Post by mosquitogang201 on 2008-11-10
So you have video AND audio for NTSC working in mythtv?? If so I might just install the 64 bit version..I followed your guide on 32 bit Ibex but still only get video in TV time. Also is the radio tuner working (if you have the 1800 with radio)?

To the guy above me once you run make install and add those lines to /etc/modules if necessary then they will load automatically on boot.

---

### Post by Nativedude on 2008-11-11
Yeah I'm not quite sure how to do what you were saying theduke
think you could lay it out a bit cleaner

---

### Post by Riffer on 2008-11-14
Ok did all that.  Got tvtime working but no sound.  Any ideas?

---

### Post by wasutton3 on 2008-11-15
myth tv doesnt seem to work for me. its all pixelated and messed up. coule that be a video problem?
i know xorg consumes an enormous amount of cpu power (15-35% of a quad core) so could that be a problem?

---

### Post by kpaden on 2008-11-19
IT'S ALIVE!!! IT'S ALIVE!!!!!

The picture quality is AMAZING. :lolflag:

Forget TVtime/NTSC. Use Mplayer/ATSC. 

# First I installed the linuxtv applications. 

# Then I disconnected the analog connection on the card, leaving the ATSC connection. I am connected to a CHEAP OTA/ATSC/HDTV antenna.


# I made sure the ~/.mplayer directory exists. 
mkdir ~/.mplayer

# I created a channels.conf file by scanning for ATSC Channels
linuxtv-dvb-apps-1.1.1/util/scan  /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf

# Then I verified that the file has been populated. 
cat  ~/.mplayer/channels.conf

# I use the following script that I call "tv"

awk -F: '{print $1}' ~/.mplayer/channels.conf| cat -n
echo "Enter your channel of choice"; export ANSWER=`line`
CHANNEL=`sed -n ${ANSWER}'p' < ~/.mplayer/channels.conf| cut -f2-10`
mplayer dvb://"${CHANNEL}"  -nobps -autosync 7 -forceidx  -idle -cache 16384 -mc 0 -ao alsa  -framedrop

# The Audio/Video sync is not perfect so now I have to figure out how to get mythtv going. :guitar:

---

### Post by lferree on 2008-11-21
Thank you SOOO much theduke88!!!

I've been trying for months to get OTA ATSC with my HVR-1800.

I followed most of your steps (minus the HDMI and ATI stuff) and it works flawless.

Once I get my FM working and a good way of pulling guide info, I'll be all set.

Can't thank you enough for posting this valuable info.

---

### Post by kpaden on 2008-11-22
EUREKA!!! This tv script is nice, and the Audio, and Video stay in sync. :-)
Yes, it is a more intriquite incantation, but soooo nice.   :-P



# ~/TV/linuxtv-dvb-apps-1.1.1/util/scan/scan  /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > /tmp/channels.conf

while true
do
awk -F: '{print $1}' ~/.mplayer/channels.conf| cat -n |pr -2|uniq
echo
LAST=`cat  ~/.mplayer/last_channel.txt`
echo -n "Enter your channel of choice: (${LAST}), or \"x\" "; export ANSWER=`line`
test -z "${ANSWER}" && ANSWER="${LAST}"
echo "${ANSWER}" | grep x >/dev/null && exit
CHANNEL=`sed -n ${ANSWER}'p' < ~/.mplayer/channels.conf|cut -f2-10`
echo ${ANSWER} > ~/.mplayer/last_channel.txt
mplayer dvb://"${CHANNEL}"  -nobps -autosync 10 -forceidx  -idle -cache 8192 -mc 0.2 -ao alsa  -framedrop
done

---

### Post by manro on 2008-12-02
Hi!

Does anyone has any success making this card work with analog cable tv?

I'll appreciate any help!

Rgds,
MaNRo

---

### Post by cenwesi on 2008-12-03
I have being watching this thread... some people claim to have it working and some only get video but no sound. I get video but the video is very weired purple looking with lines. This was an expensive card that for the past 9-10months is just using up power on my server. Really ticks me off that still no luck getting this card to work on Ubuntu.

PS: someone on this thread said it worked out the box with Fedora if that helps.

---

### Post by nathan42 on 2008-12-08
First, thanks to theduke for the excellent writeup: it has gotten me much further along.

ATSC is almost working.  The video is there and it looks good, but it stutters just a little.  Sound (which IS working over HDMI--again, thanks to theduke) is also way laggy.

Analog cable looks like cenwesi described: very distorted with a green & purple tint and no sound.

Any help is appreciated, otherwise I'll keep searching/waiting.

--Nathan

---

### Post by kepreon on 2008-12-18
I've also been following this thread and have had no luck getting much working.  I can't get my Cable video or audio any of the ways mentioned throughout this post.  I guess we have to wait on v4l for driver fixes?

---

### Post by MoonBlossom on 2008-12-21
I'm having a new problem. I upgraded the v4l drivers from Mercurial and TVTime is now giving me this error:

[INDENT]**vbidata: Can't open /dev/vbi0: No such file or directory**[/INDENT]

I tried to link /dev/video0 to /dev/vbi0 but didn't solve the problem.

My kernel version is 2.6.27-11-generic and I'm running Ibex.

Any help will be appreciated :)

---

### Post by MoonBlossom on 2008-12-26
> **MoonBlossom said:**
> I'm having a new problem. I upgraded the v4l drivers from Mercurial and TVTime is now giving me this error:

[INDENT]**vbidata: Can't open /dev/vbi0: No such file or directory**[/INDENT]

I tried to link /dev/video0 to /dev/vbi0 but didn't solve the problem.

My kernel version is 2.6.27-11-generic and I'm running Ibex.

Any help will be appreciated :)

Answering to my own post :)

In case someone runs into this problem just erase your tvtime XML settings in your home folder. (/home/user/.tvtime)

I was finally able to watch free over the air TV with sound using this card But only on HD digital and not analog. 

TvTime doesn't seem to work with HD channels but Kaffeine was able to find all the channels in my area :)

The only thing missing now is radio :guitar:

---

### Post by manro on 2009-01-14
Has anyone made any advance on analog tv?

Rgds,
MaNRo

---

### Post by smgendler on 2009-01-18
Does anyone else find it odd that a "supported" card creates this much traffic?  Could it be the linux distribution?  Should I abandon Ubuntu and flee to Fedora or OpenSuse?  What is the OS that best works with MythTV and the HVR-1800?

---

### Post by agamotto on 2009-01-19
I have discovered over the last few years that the word 'support' and linux have a very loose arrangement.  Like certain other 'supportive' garments, there are some that are great, and some that are barely better than going starkers.

---

### Post by manro on 2009-01-19
> **agamotto said:**
> I have discovered over the last few years that the word 'support' and linux have a very loose arrangement.  Like certain other 'supportive' garments, there are some that are great, and some that are barely better than going starkers.

Completely agree!

---

### Post by TomDaBomb2u on 2009-01-19
> **MoonBlossom said:**
> Answering to my own post :)

In case someone runs into this problem just erase your tvtime XML settings in your home folder. (/home/user/.tvtime)

I was finally able to watch free over the air TV with sound using this card But only on HD digital and not analog. 

TvTime doesn't seem to work with HD channels but Kaffeine was able to find all the channels in my area :)

The only thing missing now is radio :guitar:

SWEET! I'm bouta try it now. I haven't checked this in MONTHS. I started this thread a looooong time ago and have just been using Windows to watch TV lol.

Edit: Nope. Still not working for me. Can you please share how to configure Kaffeine to get it to work? I have Comcast, which I assume it ATSC, and I have the cable going into "TV IN" and not "ANT IN" on the card.

Please help!
-Thomas

---

### Post by wasutton3 on 2009-01-30
has there been any progress with the analog aspect of this?
i have been using the windows 7 beta with this card and it works perfectly with windows media center.

---

### Post by smgendler on 2009-01-30
FWIW, I gave up on the 1800 and went to the pcHDTV.com HD-5500 card.  Works for analog with an included patch cable into the microphone input of the sound card.  I might go to the HVR-2250 after kernel support is announced for both analog and digital.  Til then, my feeling is it's just hopeless for the new generation of Hauppauge cards.

---

### Post by ionospheric on 2009-02-02
I require analog S-video input because I have to use a cable box for channels above 100. Mythbuntu seemed to finally put MythTV within reach, and based on the information in
[http://www.linuxtv.org/wiki/index.php/Hauppauge](http://www.linuxtv.org/wiki/index.php/Hauppauge)
I went and bought the Hauppauge HVR-1800.

Not sure what they mean by "Supported: Yes" and I don't easily give up, but the result is not yet satisfactory. In the "watch TV" section of MythTV, the picture is scaled wrong, which can probably be fixed by finding the appropriate config file and changing the resolution (even though I don't know why this doesn't work from the Mythbuntu installation). Of more concern however is the fact that there are artifacts (stripes) in the picture which can probably be attributed to the driver. This was still apparent when tvtime was used to test the S-video input.
I tested again with the same hardware and WinTV under XP, and here the picture is perfect. At the same time, I tried the old PVR500 model and the picture was just fine under tvtime, so it is possible to watch TV under Linux.

Any ideas what to do next? Perhaps a newer version of V4L? How do I find out which one is installed under Mythbuntu? How do I upgrade it, if possible?

---

### Post by wasutton3 on 2009-02-25
its depressing that this issue still has not been solved, i purchased this card because it used pci express, and i needed my other pci slots for different cards. has any progress at all been made in the last 3 weeks or is it just not worth it?

---

### Post by cenwesi on 2009-02-25
If anyone wants to buy mine, please send me an email. I am ready to dump this card, just drawing power off my server!

---

### Post by InHisName on 2009-02-27
I just purchased this card.  Box remains sealed while I research the drivers.  I am running ubuntu Hardy 8.04. I have not installed any mythtv portions yet.  Kernel is 2.6.24.23-generic. 

Is there a soup to nuts HOWTO get me up and going yet?

InHisName
praying for an excellent HOWTO

---

### Post by Hackit on 2009-02-28
> **theduke88 said:**
> It took a few days for me to get things running, but thanks to forum posts I have MythTV working on my Hauppauge HVR-1800 with both NTSC and ATSC/QAM (OTA HD) tuners, video output from HDMI on an ATI HD 3450, with both OpenGL working as the painter in real full-screen mode, and sound being played in digital 5.1 via passthru on the HDMI link.  The remote/USB kit my package came with works flawlessly too.

Here were the changes that needed to be made, differing from a 8.10 default Intrepid Ibix install.  I used the x86_64 version for my particular hardware, but there should be no changes for 32b that I can see.
[LIST]
[*]During the install process, you want to use the newer USB Microsoft Media Center settings for the remote (Philips et al)

[*]Setup ubuntu to use the fglrx driver from the restricted drivers configuration.

[*]The v4l-dvb drivers need to be pulled from the mercurial archive, and compliled.  You will need to first install build-essentials and some other development packages for these to compile cleanly (must be done as root, I "sudo su -" first):
[/LIST]

```

cd /usr/local/src
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb

make && make install
```

I have in /etc/modules:

```
fuse
lp
rtc
sbp2
tuner
```

[LIST]
[*]Reboot the machine so all those drivers/settings come up.

[*]When you setup mythtv under capture cards, you want to setup the ATSC/QAM tuner as a dvb type, and ignore that it fills in the wrong looking data.  If you want NTSC to work, setup the card as an MPEG4 card and type the /dev/video0 device in the device field.  You will end up with two video devices.  Be sure to scan using the dvb card with dvb settings to add channels when in the video source setup.  On my dvb scan it took a long time and looked like it was only failing (the signal sat at 0% the whole time, but sometimes the screen would go from unlocked to locked and it'd pick up a channel). ATSC/QAM is the 'Antenna' input.  The NTSC scan is pretty normal looking -- my signal stayed at 99% the whole time and I ended up with grainy looking analog OTA on the 'Cable' input after I hooked up an antenna.
[/LIST]

These seem to help when placed in the /etc/X11/xorg.conf file in the 'Devices' section:

```
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "on"
        Option "TexturedVideo" "on"
        Option "TexturedVideoSync" "on"
        Option "Textured2D" "on"
        Option "BackingStore" "on"
        Option "UseFastTLS" "1"
        Option "XAANoOffscreenPixmaps" "on"
```

[LIST]
[*]This one took me forever to figure out -- I'd only get video corruption and strange crashing until this variable was defined before launching mythfrontend.  Before this flag was set, another problem was that the frontend would seem to hang on almost every menu option unless I was running the QT painter or in a window:
[/LIST]

```
export LIBGL_ALWAYS_INDIRECT=1
```

or 

```
declare -x LIBGL_ALWAYS_INDIRECT=1 && mythfrontend
```

Personally, I've modified the mythfrontend.sh caller script to set the variable on bootup.
[LIST]
[*]configure MythTV digital audio to work over HDMI:
[/LIST]
At this point, everything but sound should work.. I had some trouble figuring this part out.  If you use the alsa-utils 'aplay' program, ALSA will show you what it sees for audio devices on the system:

```

root@teevee:~# aplay -L -l
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

root@teevee:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

The important values are the # after card, and the # after device in the first line under the header.  In this instance, our values are 0 and 3.

Your audio device that needs to be specified in the General tab (2nd page) would then be ALSA:plughw:0,3 and you will need to type this into the device section.  In the passthrough section, leave the setting as default, and be sure to enable passthru for anything your reciever can handle.

First you will need to unumte your card (press 'M' to mute/unmute) -- run this in a terminal:
```

alsamixer -c 0 

```

You can test this setting with some white noise by executing (be sure to turn the volume down first) -- run this in a terminal:
```

speaker-test -D plughw:0,3
```

And that was pretty much it.  MythTV is fantastic now that it works, but was not fun to spend a week getting to work.  If I did it again, I would not get a Hauppauge 1800 card, as the support is pretty bad, and I would also not run an ATI HDMI card, even though it's very nice to have a fanless HDMI with OpenGL setup on these dirt-cheap HTPC cards.  ATI driver support is the worst, and It took hours to find the LIBGL_ALWAYS_INDIRECT option... MythTV would just crash all the time with a segfault prior to that.  Running with the QT painter or running in a window are the best options while debugging all the ATI garbage (see mythfrontend --help).

Next I will try to make this machine control a Motorola DVR cablebox over firewire, wish me luck as I will need it!

**EDIT:**Some cleanup & additions, and also to mention: I should have known better than to get an ATI card.  The screen tearing is horrible (*STILL* a problem on **any **ATI card with any driver due to lack of proper vsync), even after fiddling with resolutions in my xorg config to get X & myth running at the native resolution of my TV.  I can live with it, but I'm going to have to save up for ANY nVidia card with HDMI to use instead.

Hi theduke,

I have an nvidia card so i'm not following that part,

I ran this part of your instructions: 

```

cd /usr/local/src
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb

make && make install
```

Rebooted and then tried to follow this step:

[*]When you setup mythtv under capture cards, you want to setup the ATSC/QAM tuner as a dvb type, and ignore that it fills in the wrong looking data.  If you want NTSC to work, setup the card as an MPEG4 card and type the /dev/video0 device in the device field.  You will end up with two video devices.  Be sure to scan using the dvb card with dvb settings to add channels when in the video source setup.  On my dvb scan it took a long time and looked like it was only failing (the signal sat at 0% the whole time, but sometimes the screen would go from unlocked to locked and it'd pick up a channel). ATSC/QAM is the 'Antenna' input.  The NTSC scan is pretty normal looking -- my signal stayed at 99% the whole time and I ended up with grainy looking analog OTA on the 'Cable' input after I hooked up an antenna.
[/LIST]

And i still have no option to select the tuner when i scan for channels.

Would it be possible for you to number the steps and have all the commands/code?

I'm a linux noob and I'm sure I have just missed something really obvious. I have cogeco cable in canada and I'm not using the cable box from my provider. I just want to connect the cable right into my 1800 to get the channels.

Thanks.

---

### Post by RockClimb on 2009-02-28
> **smgendler said:**
> Does anyone else find it odd that a "supported" card creates this much traffic?  Could it be the linux distribution?  Should I abandon Ubuntu and flee to Fedora or OpenSuse?  What is the OS that best works with MythTV and the HVR-1800?

I agree!! I recently upgraded my system an bought this card because it was "supported." I should have read the forums _[COLOR="Red"]FIRST[/COLOR]_ I have worked on it for about a week now, trying everything I have read in the forums with no luck on analog audio. Tonight I pulled it from the system and put my old Brooktree card in. It worked as soon as I booted up. I hope I have not bought a brick here and that it will eventually really be "supported."

---

### Post by wasutton3 on 2009-03-02
agreed, i have had this card a year now and it still doesnt work.

---

### Post by NTolerance on 2009-03-02
Will the new kernel in Jaunty add support for this card?  I want an HD tuner for my Mythbox but it seems like getting a PCI-E HD tuner card working in Intrepid is a real pain.  

I have a serious appreciation for in-kernel drivers and would rather wait than compile from source and tweak all day long.

---

### Post by janascii on 2009-03-02
I've noticed that the support for this card will "be in the next release." I've given up on it and while I wait for someone to buy this card I'll hope for a miracle this next release.  Anyone know of any functional pcie cards?

---

### Post by mlord on 2009-03-05
Support for the HVR-1800 appears to have been in the Linux kernel since at least 2.6.28.  So anyone here running Mythbuntu 8.10 should be able to use the HVR-1800 with it by simply building/installing a 2.6.28 Linux kernel.

Has anyone here tried that yet?

---

### Post by monir81 on 2009-03-12
All, I just wanted to share my experiences with the HVR-1800.  I think I've spent now about 45 hours trying to get it all working..with some luck.  I have it working with analog (S-video and coax) but only using tvtime.  In tvtime the picture looks perfect..slightly jerky during fast movements, but a great overall picture.  I was able to get the audio working by using the red/white rca/av cables from my dish network receiver plugged into a Y-adapter that plugs into my microphone jack on my sound card (5 bucks from radio shack).  I believe the only thing I had to do to get it to this point after installing 8.10 mythbuntu was the following:
1. Apply OS updates in Mythbuntu.
2. launch mythtv-setup
3. choose V4L as the 1st capture card. (theduke88 said use MPEG4, but I ran into "failed to open card" when trying to scan the channels)
4. choose DVB as the 2nd capture card and exit mythtv-setup (you don't need to run myfilldatabase at this time)
5. sudo modprobe tuner
6. sudo apt-get install tvtime
7. launch tvtime
8. hit tab, and select "television" (if you have coax plugged in the analog jack) from the input sources menu in tvtime.

My Mythtv setup was not as successful.  When I try to launch "Watch TV" in mythtv I get the same improperly sized, green/purple with lines picture.  Haven't been able to get it past this point.  Here is my config:

Mythbuntu 8.10 (I've also tried 8.04 and most recent MythDora)
Dish Network receiver model 301
NVidia Geforce 6200 PCI x16
Hauppauge hvr-1800 PCI x1
AMD 3000+64bit
MSI MS-7125 motherboard (onboard sound)

Please let me know if there are any ideas out there and if I need to elaborate on anything.  I have an Newegg RMA number for this little fella but I don't want to send it back if I don't have to...well..I'm stubborn and don't want to give up :)  Thanks all!

Other things I've tried/other issues
I've also installed the v4l_dvb drivers from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb).  Once the v4l drivers were downloaded and compiled the analog output of S-video in tvtime actually seems to get worse, with the color changing, getting lighter and darker.

When I try to scan for channels in mythtv, using the dvb capture card, the OS will lock up during the scan and I notice the caps lock and scroll lock are blinking.

The only thing left that I can think of is try to compile and install the vanilla kernel - I'm not sure how to do that yet though.

---

### Post by monir81 on 2009-03-12
Currently compiling 2.6.28-7.  I'll post the results once its finished.

---

### Post by wmarin on 2009-03-13
> **monir81 said:**
> Currently compiling 2.6.28-7.  I'll post the results once its finished.

Hey monir81
Any success ?, here waiting for your response. (crossed fingers)

---

### Post by monir81 on 2009-03-14
Ok, I have it on the 2.6.28.7 kernel.  During the "make menuconfig" I saw a section for the HVR-1800 modules and they were all enabled.  When the system boots I see the cx23885 and cx23840 loaded, and all seems happy.  Sadly though I'm not seeing much of a change..well it broke a few things: found that it wasn't loading my sound card module, Nvidia driver broken so I downloaded the 177.82 driver and installed, and restricted drivers menu silently fails when trying to select a different driver.  Anyhow, when connecting to analog using tvtime, I get video with no audio.  
Things I'm working on currently:
I have noticed that I only have 1 /dev/dsp device, I'm not totally sure but I think this may mean that it still doesn't recognize an audio capture device on the card...but I may be wrong (I hope I am).
I've seen where people have mentioned that I may need to select /dev/video1 to get sound, so I'll try that.
I also will try to recompile the kernel again, selecting xconfig so I can import the selection list from the mythbuntu kernel config.. I'm hoping this will help in the long run.
Any other ideas out there?  Or am I heading the wrong direction?

Thanks all!

---

### Post by marquarc on 2009-03-15
I followed theduke88's post using similar hardware (hvr-1800 with an ati hd 3200) using Mythbuntu 8.10. I got pretty close, but there were two things I had to do differently. I thought I'd document them here, maybe help someone else out.

1. I had to install the firmware for the card. It can be found here: [http://steventoth.net/linux/hvr1800/](http://steventoth.net/linux/hvr1800/)  You just download the zip and sh files, unpack it (sudo sh extract.sh), and copy it to a different location (when you unpack it it tells you where to put it). Before doing this my PC would lock up during the channel scan.

2. I had to use the latest ATI driver. Installing this is a pretty straight forward process - download the driver off ati.com, and use sh on the run file. ie, "sudo sh ati-driver-name.run" and it will walk you through a quick installer. Before doing this, myth would start with a garbled, unreadable screen.

Getting those two things fixed took me a while to figure out, so hopefully this saves someone else some time! Howevever, I still have problems on my LCD tv where the picture is underscanning (there's a 1" black box around the outside of my desktop/myth) that appears to just be how the ATI driver works. If I could choose my hardware over again, I'd go with an nVidia video card.

edit: I guess I didn't specify exactly *what* I got working. Everything in MythTV works just great, BUT, unlike theduke88, I didn't even attempt to get audio going over HDMI. I'm just using the standard 1/8" jack out to a stereo system (2ch). I also did not attempt analog, because there are no analog stations in my area anymore.

---

### Post by monir81 on 2009-03-15
marquarc,
Thats great to hear, what all did you get to work?  Analog with sound?  If so, which inputs are used (s-vid/red and white or coax)?  Also, if you get bored of well, enjoying mythtv :) Could you let me know what audio device your using (maybe /dev/dsp) and if you have multiple /dev/dsp devices on your system.  It would really help me sleep better. Thanks

---

### Post by greyfox1 on 2009-03-15
I am preparing to compile the 2.6.29-rc8 kernel from kernel.org due to no sound with analog signals.  Just like **monir81**, i have a newegg RMA number that I really don't want to have to use.  I am following [this guide]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild") to compile the kernel.  

One interesting thing to note: I went through the bit where I have to answer questions about which modules I want to include (make oldconfig) which creates a config file called .config.  I opened this file and I see the following section:

```
# Multimedia drivers
#
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m
CONFIG_MEDIA_ATTACH=y
CONFIG_MEDIA_TUNER=m
# CONFIG_MEDIA_TUNER_CUSTOMIZE is not set
CONFIG_MEDIA_TUNER_SIMPLE=m
CONFIG_MEDIA_TUNER_TDA8290=m
CONFIG_MEDIA_TUNER_TDA827X=m
CONFIG_MEDIA_TUNER_TDA18271=m
CONFIG_MEDIA_TUNER_TDA9887=m
CONFIG_MEDIA_TUNER_TEA5761=m
CONFIG_MEDIA_TUNER_TEA5767=m
CONFIG_MEDIA_TUNER_MT20XX=m
CONFIG_MEDIA_TUNER_MT2060=m
CONFIG_MEDIA_TUNER_MT2266=m
CONFIG_MEDIA_TUNER_MT2131=m
CONFIG_MEDIA_TUNER_QT1010=m
CONFIG_MEDIA_TUNER_XC2028=m
CONFIG_MEDIA_TUNER_XC5000=m
CONFIG_MEDIA_TUNER_MXL5005S=m
CONFIG_MEDIA_TUNER_MXL5007T=m
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L1=m
CONFIG_VIDEOBUF_GEN=m
CONFIG_VIDEOBUF_DMA_SG=m
CONFIG_VIDEOBUF_VMALLOC=m
CONFIG_VIDEOBUF_DVB=m
CONFIG_VIDEO_BTCX=m
CONFIG_VIDEO_IR=m
CONFIG_VIDEO_TVEEPROM=m
CONFIG_VIDEO_TUNER=m
CONFIG_VIDEO_CAPTURE_DRIVERS=y
```

Some of the tuners mentioned there are the HVR-1800 tuners!  See the [v4l wiki]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800#Components_Used") for the exact module names.  So this confirms that the .28 kernel does support this tuner.

So anyway, here goes nothing, I'm about to start compiling.  I have heard horror stories so I'm hoping this will go well.

---

### Post by rerobins on 2009-03-15
I've managed to get the HVR1800 (actually both of mine) up and running in Ubuntu Intrepid.  What I ended up doing was updating the kernel to the one that is in backports or proposed.. (2.6.27-13-generic).

After doing that I recompiled the v4l-dvb modules.  I've also installed the firmware that is specified throughout this thread.

I then unloaded all of the modules and reloaded them.

```

cd /usr/local/src/v4l-dvb
sudo make unload
sudo modprobe cx23885 && sudo modprobe cx25840 && sudo modprobe tuner

```

I'm now able to use tvtime on /dev/video0 and mplayer /dev/video1 works with sound (coax cable from my cable company straight into the box (NTSC))

The problem that I have is that /dev/video1 is just an mpeg encoded feed of what's on tv.  I have no ability to change the channel of /dev/video1

In order to change the channel I use:

```

ivtv-tune -d /dev/video0 -c 25 

```

And this causes the channel to change on /dev/video1 (I'm assuming this is the correct result).  

This causes problems with me wanting to use mythtv with /dev/video1.  I've tried configuring /dev/video1 as a MPEG2 device, but when it probes the card it is not able to determine what the device type is.  /dev/video0 is able to be probed by MythTv.  

Anyone getting MythTV configured to use this card correctly?  I tried what theduke88 mentioned, but either didn't understand or was unsuccessful in my attempt (I'm leaning towards the former).

---

### Post by TomDaBomb2u on 2009-03-23
Very cool! I'm going to try this sometime this week. I have to reinstall Ubuntu actually, so it may be next week.

---

### Post by wasutton3 on 2009-03-23
WOO! im glad to see progress is still being made with this.

---

### Post by greyfox1 on 2009-03-23
> **greyfox1 said:**
> I am preparing to compile the 2.6.29-rc8 kernel from kernel.org due to no sound with analog signals. 

Just reporting back on this.  I compiled the kernel myself and unfortunately, I had no joy.  I still get video, but no audio when using analog cable.  Analog is a must for me because in addition to watching/recording TV, I wanted to hook up my VCR to the card to capture old home movies from VHS tapes.  I guess I'll have to return my card and eat the shipping charge and newegg restocking fee. :(

---

### Post by DemonBob on 2009-03-24
If it works fine, in TV-Time and MPlayer. Then it's got to be a MythTV specific issue causing it not to work. When using Mplayer i get sounds, or when just cat /dev/videoX > test.mpg i get sound and good video. 

Just for some reason in mythtv i get no sound, and the picure is a redish, purple hue.

---

### Post by monir81 on 2009-03-25
I did eventually return my hvr-1800 to Newegg and got the card listed below instead.  I now have it all working but I had to install Mythdora to support the ir receiver/blaster.  Just thought it might help to list a specific card that is known for analog and digital to work.

Hauppauge WinTV-HVR-1600 ATSC/ClearQAM/NTSC TV Tuner PCI w/Remote 1178 PCI Interface - Retail

---

### Post by wasutton3 on 2009-04-09
I have good (ish) news. The video aspect of this card works out of the box with jaunty beta. we will see with the final release

---

### Post by laskagifts on 2009-04-24
Could someone help me with configuring Hauppauge WinTV-HVR 1800 on Mythbuntu 9.04?

Setup:
PC
NVIDIA Card


TV Cable connected to >>>> Hauppauge WinTV-HVR 1800 >>> NVIDIA Card >>> connected via S-Video to TV and Computer  Sound Card connected to TV Audio in port


Things that I was able to do:

I was able to install Mythbuntu 9.04 and I can see configuration screens on TV. 


Problem description:

Hauppauge WinTV-HVR 1800 is detected by Mythbuntu 9.04. No matter what source and input I select I can't get any TV picture out.

Any suggestions or ideas about backup configuration setup?

---

### Post by theduke88 on 2009-05-13
I haven't been around in a while, I should go back and edit my post because some things have changed with the Jaunty upgrade.  Actually my upgrade to Jaunty went pretty poorly and I had to remove my devices entirely from the mythtv configuration and re-add before I could get the scheduler working again.  At this point I'm also tracking down some issue with the analog tuner (come on with the HD feed comedy central!) that is freezing up mythTV, but everything else is going well.  

Edit:  And thanks for all the kind words.. sorry I sorta left everybody high and dry on this, "real life" got crazy :/  I will post with more updates if I figure anything out.  Anybody have any successes to report on Jaunty?

One big annoyance for me with any upgrade on the stock kernel, is the CPU Frequency governor undoes my overclock (pin mod 1.8Ghz to 2.5 that makes a HUGE difference for HD playback/encode times), and the only way to undo it is to rip the whole section out of the kernel.  I followed [http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/](http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/) to do it the clean-room/Ubuntu way, and it's nicely handled by DKMS this way.  Updating my v4l drivers from the mercurial repo seem to help, but I'm still not there on the analog cable recording correctly.. OTA is still sparkly and nice :)

---

### Post by paintbalforjesus on 2009-05-15
I just ordered this card refurbished for the computer that I built myself.  It will be my only TV in my living quarters so I hope to get it up and running pretty quickly after it gets here.  If anyone can provide more help that would be appreciated, and if I find any discoveries myself I will, of course, post them.

Has anyone tried using this card with a 64-bit OS?  I'm running ubuntu 9.04 64 bit because I have 6 GB of RAM and the 32 bit won't recognize any more than 4 GB.  If anyone has advice on the 64-bit drivers/operation it would be greatly appreciated.

---

### Post by cenwesi on 2009-05-15
> **paintbalforjesus said:**
> I just ordered this card refurbished for the computer that I built myself.  It will be my only TV in my living quarters so I hope to get it up and running pretty quickly after it gets here.  If anyone can provide more help that would be appreciated, and if I find any discoveries myself I will, of course, post them.

Yes it is indeed refurbished, my card is still in my system just sucking up juice...
> 
Has anyone tried using this card with a 64-bit OS?  I'm running ubuntu 9.04 64 bit because I have 6 GB of RAM and the 32 bit won't recognize any more than 4 GB.  If anyone has advice on the 64-bit drivers/operation it would be greatly appreciated.

I don't think the card working has anything to do with 64bit...

---

### Post by theduke88 on 2009-05-15
> **paintbalforjesus said:**
> 
Has anyone tried using this card with a 64-bit OS?  I'm running ubuntu 9.04 64 bit because I have 6 GB of RAM and the 32 bit won't recognize any more than 4 GB.  If anyone has advice on the 64-bit drivers/operation it would be greatly appreciated.

I'm running a 64 bit Jaunty install and things are [s]mostly[/s]**completely** fine.  The analog (NTSC/MPEG) tuner [s]still inst working right[/s]** is now working great**, [s]but[/s] ATSC is still great as a DVB source for some great looking OTA HD.  You should be able to do a hg clone on the v4l sources and get them compiled under 64b with no problems, and the rest is really a matter of picking a mythtv or tvtime/klear style setup for watching.  I'm about ready to give this card a big gold star on linux! [s] no gold star yet. :p[/s]

---

### Post by theduke88 on 2009-05-15
Proud to report that my Hauppauge 1800 is now working 100% under MythTv under the following configuration:

Over The Air High Def (OTA HD) ATSC, up as primary device, DVB device 0.
Analog adapter being fed from cable splitter.  Analog recordings/clear QAM (I haven't had much time to play with the QAM so YMMV) via v4l device (/dev/video0).

This install is with the latest hg clone (5-15-2009) off of the v4l-dvb codebase.  At first I was extremely confused that it was not referencing /dev/video1 (somewhere along the line things got flipped around I think between interfaces).  So, DVB[0] is really /dev/video1 in my configuration, and /dev/video0 is really the analog tuner.  You can confirm this with the tvtime app, which reports a non v4l device on the DVB (ATSC) port, and will show your analog tuner otherwise if modules are installed correctly.   I have also played with the KDE app 'klear' to try to access the DVB side of the card, a tool which was new to me. 

I can watch either encoder live or use to record on mythtv, all of this piped out via hdmi with audio.  Programming data via a schedulesdirect subscription (highly worth the $20 once you get this up), and a bunch of eSata disks hanging off my machine for backend use.  Next up is to try to use the FM radio hack to see if I can get that working.  It also looks like svideo/composite are working, so I might just have take that for a spin although I cant think of a use right now.

:KS):P:popcorn:

PS - I found the need for a quick & dirty app cycler to go between xbmc & mythtv.  There are issues with an IR driven app, I have found, and this does the trick for now.. Very silly little script, but it might help somebody (place this in your startup instead of mythtv or xbmc for HTPC):

```

#!/bin/bash
#Runs xbmc and mythfrontend in a loop ad infinitum
DISPLAY=":0.0"

while [ 1 = 1 ]
do
/usr/local/bin/xbmc
/usr/bin/mythfrontend
done

```

---

### Post by rstewartmailacct on 2009-05-23
Hi all,

Is there some special trick to get this to work with Jaunty 64 bit?  I did a clean install and then installed Myth after all updates.  Configured Myth, did not use schedules direct or any schedule, and scanned for channels.  

When I try to watch, the screen flashes and stays on menu.  I have not done anything with v4l tree, this is purely stock.  I did install Tvtime and tried to view, but I only get snow and no sound.  I selected the IVT card in Myth and my HVR-1800 does show up as detected.

Any help would be great!

---

### Post by rstewartmailacct on 2009-05-23
Hi again,

Used the tree and this works on 64 bit Jaunty as stated above, both NTSC and ATSC.  However, I'm still having sound issues.  Any ideas?

Thanks

---

### Post by computer_guy57 on 2009-05-29
theduke88, how did you configure the NTSC/analog side of the card in MythTV?

If I do Analog V4L card (/dev/video0), all I get is a green screen, both for live tv and recording.
If I do MPEG2 card (/dev/video0), if I go to Live TV in the mythtv menu, I get a black screen for a few seconds and then it goes back to the menu, with a message on the console something like "couldn't find a matching decoder for <so-and-so>.mpg. If I try doing that as /dev/video1, it can't probe the card/

I tried doing it as an MPEG4 device, which is something some people have suggested, but then mythtv-setup can't open the card to search for channels.

The ATSC part of the card is working beautifully for me in MythTV, with the exception of slightly choppy video and audio full of popping, but on only one channel... so I'm not going to blame the card for that.

Any suggestions? Thanks in advance!!!
P.S. I'm using Arch Linux, not Ubuntu, but I'm asking here because this is one of the very few places where I've seen someone with this card working in MythTV. Also, I'm using the latest v4l-dvb out of Mercurial and the NTSC part of the card works quite well using tvtime and mplayer.

EDIT: One more thing: when I had it set up as an MPEG2 card, I tried recording something with it. It recorded a 12GB file into my mythtv folder, but the recordings viewer couldn't find the decoder for it (like above) and when I tried opening it with mplayer, it sat there reading off the hard drive longer than I felt like waiting.

---

### Post by ktuimala on 2009-06-06
I am 100% aggravated. I have a system with a HVR-1800 and a HVR-2250. The HVR-2250 is working perfectly for DVB output through mythtv. I got the HVR-1800 because it was shown to support analog. 

I have all sorts of analog devices I would love to hook up to it, including analog cable. However, the HVR-1800 is only allowing me to scan and find my analog cable, but when I go to watch the channels I get a black screen followed by a complete system lockup that requires me to hard power off my box.

MythTV isn't the only veiwer that crashes. It seems that whenever I invoke the HVR-1800 with tvtime, mplayer, vlc, etc it completely locks up my computer. I am getting sick of hard power offs. I am going to loose hard drives soon!!!

I have the latest mercurial v4l-dvb and firmware from steven toth for the HVR-1800 copied to /lib/firmware/2.6.28-11-generic. All of the firmware shows that it is loaded and for all intensive purposes the HVR-1800 is installed. I have uninstalled, reinstalled, reloaded, reformated, and have gone through just about every forum post i have found on the web to get this to work. So far no dice...

Please find some of my system output below. Perhaps one of you can see what my problem is. While the rest of you seem to have video/audio issues, mine just crashes my whole PC!!

Thanks in advance!!!

dmesg output:
```
[    0.000000] BIOS EBDA/lowmem at: 0009ec00/0009ec00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  modified: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  modified: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef5bd
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb25bd
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef5bc to 00881000 - 00fb25bc
[    0.000000] ACPI: RSDP 000FB6A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF80000, 0040 (r1 NEC             20090409 MSFT       97)
[    0.000000] ACPI: FACP CFF80200, 0084 (r1 040909 FACP2049 20090409 MSFT       97)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080926]
[    0.000000] ACPI: DSDT CFF805C0, D4E7 (r1  A1256 A1256001        1 INTL 20060113)
[    0.000000] ACPI: FACS CFF98000, 0040
[    0.000000] ACPI: APIC CFF80390, 006C (r1 040909 APIC2049 20090409 MSFT       97)
[    0.000000] ACPI: MCFG CFF80400, 003C (r1 040909 OEMMCFG  20090409 MSFT       97)
[    0.000000] ACPI: SLIC CFF80440, 0176 (r1 NEC             20090409 MSFT       97)
[    0.000000] ACPI: OEMB CFF98040, 0072 (r1 040909 OEMB2049 20090409 MSFT       97)
[    0.000000] ACPI: HPET CFF8F5C0, 0038 (r1 040909 OEMHPET  20090409 MSFT       97)
[    0.000000] ACPI: SSDT CFF8F600, 02B4 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2443MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb25bd]      NEW RAMDISK ==> [0000881000 - 0000fb25bd]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000cff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000] On node 0 totalpages: 851726
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4888 pages used for memmap
[    0.000000]   HighMem zone: 620650 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2f700000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845070
[    0.000000] Kernel command line: root=UUID=43d4f476-58b6-4b04-911f-8c5b6279328b ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2707.675 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 17036480 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3346588k/3407360k available (4126k kernel code, 59376k reserved, 2208k data, 532k init, 2502152k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5415.35 BogoMIPS (lpj=10830700)
[    0.004019] Security Framework initialized
[    0.004024] SELinux:  Disabled at boot.
[    0.004034] AppArmor: AppArmor initialized
[    0.004040] Mount-cache hash table entries: 512
[    0.004126] Initializing cgroup subsys ns
[    0.004129] Initializing cgroup subsys cpuacct
[    0.004131] Initializing cgroup subsys memory
[    0.004134] Initializing cgroup subsys freezer
[    0.004142] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004144] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004146] CPU: Physical Processor ID: 0
[    0.004147] CPU: Processor Core ID: 0
[    0.004150] using C1E aware idle routine
[    0.004156] Checking 'hlt' instruction... OK.
[    0.021507] ACPI: Core revision 20080926
[    0.025828] ACPI: Checking initramfs for custom DSDT
[    0.232373] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.273813] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.276001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5415.25 BogoMIPS (lpj=10830510)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.360370] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.360383] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.364025] Brought up 2 CPUs
[    0.364027] Total of 2 processors activated (10830.60 BogoMIPS).
[    0.364067] CPU0 attaching sched-domain:
[    0.364069]  domain 0: span 0-1 level CPU
[    0.364071]   groups: 0 1
[    0.364075] CPU1 attaching sched-domain:
[    0.364077]  domain 0: span 0-1 level CPU
[    0.364078]   groups: 1 0
[    0.364120] net_namespace: 776 bytes
[    0.364120] Booting paravirtualized kernel on bare hardware
[    0.364233] Time:  7:37:13  Date: 06/06/09
[    0.364233] regulator: core version 0.5
[    0.364233] NET: Registered protocol family 16
[    0.364233] EISA bus registered
[    0.364233] ACPI: bus type pci registered
[    0.364233] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.364233] PCI: Not using MMCONFIG.
[    0.364872] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.364874] PCI: Using configuration type 1 for base access
[    0.364875] PCI: Using configuration type 1 for extended access
[    0.365375] ACPI: EC: Look up EC in DSDT
[    0.403437] ACPI: Interpreter enabled
[    0.403440] ACPI: (supports S0 S1 S3 S4 S5)
[    0.403456] ACPI: Using IOAPIC for interrupt routing
[    0.403511] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.409507] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.409509] PCI: Using MMCONFIG for extended config space
[    0.418431] ACPI: No dock devices found.
[    0.418501] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.418570] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.418572] pci 0000:00:02.0: PME# disabled
[    0.418593] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.418595] pci 0000:00:04.0: PME# disabled
[    0.418620] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.418622] pci 0000:00:09.0: PME# disabled
[    0.418642] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.418644] pci 0000:00:0a.0: PME# disabled
[    0.418689] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.418695] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.418701] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.418707] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.418713] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.418720] pci 0000:00:11.0: reg 24 32bit mmio: [0xf7fffc00-0xf7ffffff]
[    0.418736] pci 0000:00:11.0: set SATA to AHCI mode
[    0.418764] pci 0000:00:12.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffefff]
[    0.418812] pci 0000:00:12.1: reg 10 32bit mmio: [0xf7ffd000-0xf7ffdfff]
[    0.418877] pci 0000:00:12.2: reg 10 32bit mmio: [0xf7fff800-0xf7fff8ff]
[    0.418912] pci 0000:00:12.2: supports D1 D2
[    0.418914] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.418917] pci 0000:00:12.2: PME# disabled
[    0.418945] pci 0000:00:13.0: reg 10 32bit mmio: [0xf7ffc000-0xf7ffcfff]
[    0.418993] pci 0000:00:13.1: reg 10 32bit mmio: [0xf7ffb000-0xf7ffbfff]
[    0.419057] pci 0000:00:13.2: reg 10 32bit mmio: [0xf7fff400-0xf7fff4ff]
[    0.419093] pci 0000:00:13.2: supports D1 D2
[    0.419094] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.419098] pci 0000:00:13.2: PME# disabled
[    0.419196] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.419202] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.419208] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.419214] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.419220] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.419272] pci 0000:00:14.2: reg 10 64bit mmio: [0xf7ff4000-0xf7ff7fff]
[    0.419303] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.419307] pci 0000:00:14.2: PME# disabled
[    0.419396] pci 0000:00:14.5: reg 10 32bit mmio: [0xf7ffa000-0xf7ffafff]
[    0.419516] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.419524] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.419531] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.419536] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.419541] pci 0000:01:00.0: reg 30 32bit mmio: [0xfb380000-0xfb3fffff]
[    0.419594] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.419596] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfb3fffff]
[    0.419599] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.419673] pci 0000:02:00.0: reg 10 64bit mmio: [0xfb800000-0xfbbfffff]
[    0.419685] pci 0000:02:00.0: reg 18 64bit mmio: [0xfb400000-0xfb7fffff]
[    0.419715] pci 0000:02:00.0: supports D1 D2
[    0.419716] pci 0000:02:00.0: PME# supported from D0 D1 D2
[    0.419720] pci 0000:02:00.0: PME# disabled
[    0.419773] pci 0000:00:04.0: bridge 32bit mmio: [0xfb400000-0xfbbfffff]
[    0.419826] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbc00000-0xfbdfffff]
[    0.419884] pci 0000:03:00.0: supports D1 D2
[    0.419885] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.419890] pci 0000:03:00.0: PME# disabled
[    0.419947] pci 0000:00:09.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.419988] pci 0000:04:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.420008] pci 0000:04:00.0: reg 18 64bit mmio: [0xfbfff000-0xfbffffff]
[    0.420024] pci 0000:04:00.0: reg 30 32bit mmio: [0xfbfc0000-0xfbfdffff]
[    0.420033] pci 0000:04:00.0: supports D1 D2
[    0.420035] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.420039] pci 0000:04:00.0: PME# disabled
[    0.420087] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.420094] pci 0000:00:0a.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.420148] pci 0000:00:14.4: transparent bridge
[    0.420168] bus 00 -> node 0
[    0.420173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.420480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.420583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.420689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.420788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.420900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.424469] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.424601] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.424731] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.424859] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.424987] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425120] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425250] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11 12 14 15)
[    0.425379] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425520] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - AE, should be A9 [20080926]
[    0.425580] ACPI: WMI: Mapper loaded
[    0.425612] SCSI subsystem initialized
[    0.425612] libata version 3.00 loaded.
[    0.425612] usbcore: registered new interface driver usbfs
[    0.425612] usbcore: registered new interface driver hub
[    0.425612] usbcore: registered new device driver usb
[    0.425612] PCI: Using ACPI for IRQ routing
[    0.432007] Bluetooth: Core ver 2.13
[    0.432016] NET: Registered protocol family 31
[    0.432016] Bluetooth: HCI device and connection manager initialized
[    0.432016] Bluetooth: HCI socket layer initialized
[    0.432018] NET: Registered protocol family 8
[    0.432019] NET: Registered protocol family 20
[    0.432026] NetLabel: Initializing
[    0.432027] NetLabel:  domain hash size = 128
[    0.432028] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.432038] NetLabel:  unlabeled traffic allowed by default
[    0.432051] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    0.432055] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.436016] hpet: hpet2 irq 2303 for MSI
[    0.436040] AppArmor: AppArmor Filesystem Enabled
[    0.444005] pnp: PnP ACPI init
[    0.444010] ACPI: bus type pnp registered
[    0.449085] pnp: PnP ACPI: found 15 devices
[    0.449086] ACPI: ACPI bus type pnp unregistered
[    0.449089] PnPBIOS: Disabled by ACPI PNP
[    0.449097] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.449099] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.449104] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.449106] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.449108] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.449110] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.449112] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.449114] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.449115] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.449117] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.449119] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.449121] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.449123] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.449125] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.449127] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.449128] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.449130] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.449132] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.449134] system 00:0b: ioport range 0xb20-0xb3f has been reserved
[    0.449136] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.449138] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.449140] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.449142] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.449145] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.449148] system 00:0c: ioport range 0x230-0x23f has been reserved
[    0.449150] system 00:0c: ioport range 0x290-0x29f has been reserved
[    0.449152] system 00:0c: ioport range 0x300-0x30f has been reserved
[    0.449154] system 00:0c: ioport range 0xa30-0xa3f has been reserved
[    0.449158] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.449162] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.449164] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.449166] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.449168] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.449170] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.483803] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.483806] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.483809] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfb3fffff
[    0.483811] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.483815] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.483816] pci 0000:00:04.0:   IO window: disabled
[    0.483819] pci 0000:00:04.0:   MEM window: 0xfb400000-0xfbbfffff
[    0.483821] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.483824] pci 0000:00:09.0: PCI bridge, secondary bus 0000:03
[    0.483825] pci 0000:00:09.0:   IO window: disabled
[    0.483828] pci 0000:00:09.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.483830] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.483832] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:04
[    0.483834] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.483837] pci 0000:00:0a.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.483839] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.483842] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    0.483843] pci 0000:00:14.4:   IO window: disabled
[    0.483848] pci 0000:00:14.4:   MEM window: disabled
[    0.483851] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.483862] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.483865] pci 0000:00:02.0: setting latency timer to 64
[    0.483869] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.483871] pci 0000:00:04.0: setting latency timer to 64
[    0.483875] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.483878] pci 0000:00:09.0: setting latency timer to 64
[    0.483881] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.483884] pci 0000:00:0a.0: setting latency timer to 64
[    0.483890] bus: 00 index 0 io port: [0x00-0xffff]
[    0.483892] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.483893] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.483895] bus: 01 index 1 mmio: [0xf8000000-0xfb3fffff]
[    0.483897] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.483899] bus: 01 index 3 mmio: [0x0-0x0]
[    0.483901] bus: 02 index 0 mmio: [0x0-0x0]
[    0.483902] bus: 02 index 1 mmio: [0xfb400000-0xfbbfffff]
[    0.483904] bus: 02 index 2 mmio: [0x0-0x0]
[    0.483905] bus: 02 index 3 mmio: [0x0-0x0]
[    0.483906] bus: 03 index 0 mmio: [0x0-0x0]
[    0.483908] bus: 03 index 1 mmio: [0xfbc00000-0xfbdfffff]
[    0.483909] bus: 03 index 2 mmio: [0x0-0x0]
[    0.483911] bus: 03 index 3 mmio: [0x0-0x0]
[    0.483912] bus: 04 index 0 io port: [0xe000-0xefff]
[    0.483914] bus: 04 index 1 mmio: [0xfbf00000-0xfbffffff]
[    0.483915] bus: 04 index 2 mmio: [0x0-0x0]
[    0.483916] bus: 04 index 3 mmio: [0x0-0x0]
[    0.483918] bus: 05 index 0 mmio: [0x0-0x0]
[    0.483919] bus: 05 index 1 mmio: [0x0-0x0]
[    0.483920] bus: 05 index 2 mmio: [0x0-0x0]
[    0.483922] bus: 05 index 3 io port: [0x00-0xffff]
[    0.483923] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.483930] NET: Registered protocol family 2
[    0.496039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.496212] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.496541] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.496724] TCP: Hash tables configured (established 131072 bind 65536)
[    0.496726] TCP reno registered
[    0.500391] Switched to high resolution mode on CPU 1
[    0.504011] Switched to high resolution mode on CPU 0
[    0.504066] NET: Registered protocol family 1
[    0.504152] checking if image is initramfs... it is
[    0.909856] Freeing initrd memory: 7365k freed
[    0.910022] cpufreq: No nForce2 chipset.
[    0.910110] audit: initializing netlink socket (disabled)
[    0.910124] type=2000 audit(1244273832.908:1): initialized
[    0.915632] highmem bounce pool size: 64 pages
[    0.915635] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.916528] VFS: Disk quotas dquot_6.5.1
[    0.916569] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.916966] fuse init (API version 7.10)
[    0.917021] msgmni has been set to 1665
[    0.917166] alg: No test for stdrng (krng)
[    0.917176] io scheduler noop registered
[    0.917178] io scheduler anticipatory registered
[    0.917180] io scheduler deadline registered
[    0.917192] io scheduler cfq registered (default)
[    1.080028] pci 0000:01:00.0: Boot video device
[    1.085511] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.085531] pcieport-driver 0000:00:02.0: found MSI capability
[    1.085547] pcieport-driver 0000:00:02.0: irq 2302 for MSI/MSI-X
[    1.085553] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.085562] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.085590] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.085607] pcieport-driver 0000:00:04.0: found MSI capability
[    1.085619] pcieport-driver 0000:00:04.0: irq 2301 for MSI/MSI-X
[    1.085625] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.085632] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.085659] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.085676] pcieport-driver 0000:00:09.0: found MSI capability
[    1.085688] pcieport-driver 0000:00:09.0: irq 2300 for MSI/MSI-X
[    1.085694] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.085704] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.085731] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.085748] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.085760] pcieport-driver 0000:00:0a.0: irq 2299 for MSI/MSI-X
[    1.085766] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.085773] pci_express 0000:00:0a.0:pcie03: allocate port service
[    1.085808] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.085814] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.085909] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.085911] ACPI: Power Button (FF) [PWRF]
[    1.085947] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.085949] ACPI: Power Button (CM) [PWRB]
[    1.086201] processor ACPI_CPU:00: registered as cooling_device0
[    1.086205] ACPI: Processor [P001] (supports 8 throttling states)
[    1.086241] processor ACPI_CPU:01: registered as cooling_device1
[    1.089386] isapnp: Scanning for PnP cards...
[    1.443301] isapnp: No Plug & Play device found
[    1.452179] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.452280] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.452559] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.453062] brd: module loaded
[    1.453258] loop: module loaded
[    1.453305] Fixed MDIO Bus: probed
[    1.453309] PPP generic driver version 2.4.2
[    1.453349] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.453369] Driver 'sd' needs updating - please use bus_type methods
[    1.453374] Driver 'sr' needs updating - please use bus_type methods
[    1.453399] ahci 0000:00:11.0: version 3.0
[    1.453415] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.453517] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.453520] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.453794] scsi0 : ahci
[    1.453866] scsi1 : ahci
[    1.453911] scsi2 : ahci
[    1.453954] scsi3 : ahci
[    1.454015] ata1: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 22
[    1.454018] ata2: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffd80 irq 22
[    1.454021] ata3: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffe00 irq 22
[    1.454024] ata4: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffe80 irq 22
[    2.340011] ata1: softreset failed (device not ready)
[    2.340057] ata1: failed due to HW bug, retry pmp=0
[    2.504523] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.506465] ata1.00: ATAPI: PIONEER DVD-RW  DVR-217D, 1.07, max UDMA/66
[    2.508814] ata1.00: configured for UDMA/66
[    3.008012] ata2: softreset failed (device not ready)
[    3.008056] ata2: failed due to HW bug, retry pmp=0
[    3.172016] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.172490] ata2.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
[    3.172492] ata2.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.173033] ata2.00: configured for UDMA/133
[    3.672007] ata3: softreset failed (device not ready)
[    3.672053] ata3: failed due to HW bug, retry pmp=0
[    3.836016] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.836757] ata3.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
[    3.836759] ata3.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.837572] ata3.00: configured for UDMA/133
[    4.172021] ata4: SATA link down (SStatus 0 SControl 300)
[    4.191307] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-217D 1.07 PQ: 0 ANSI: 5
[    4.194245] sr0: scsi3-mmc drive: 94x/94x writer cd/rw xa/form2 cdda tray
[    4.194248] Uniform CD-ROM driver Revision: 3.20
[    4.194312] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.194342] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.194394] scsi 1:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
[    4.194453] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.194463] sd 1:0:0:0: [sda] Write Protect is off
[    4.194465] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194481] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.194520] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.194529] sd 1:0:0:0: [sda] Write Protect is off
[    4.194531] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194544] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.194548]  sda: sda1
[    4.691777] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.691799] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.691835] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
[    4.691885] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.691895] sd 2:0:0:0: [sdb] Write Protect is off
[    4.691897] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.691912] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.691942] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.691951] sd 2:0:0:0: [sdb] Write Protect is off
[    4.691953] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.691966] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.691968]  sdb: sdb1 sdb2 < sdb5 >
[    4.730504] sd 2:0:0:0: [sdb] Attached SCSI disk
[    4.730526] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.730712] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.730729] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    4.730791] scsi4 : pata_atiixp
[    4.730839] scsi5 : pata_atiixp
[    4.732033] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.732036] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.063399] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.063412] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.063423] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    5.063460] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    5.063480] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    5.063497] ehci_hcd 0000:00:12.2: debug port 1
[    5.063510] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf7fff800
[    5.072013] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    5.072055] usb usb1: configuration #1 chosen from 1 choice
[    5.072074] hub 1-0:1.0: USB hub found
[    5.072079] hub 1-0:1.0: 6 ports detected
[    5.072156] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.072163] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.072188] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    5.072203] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    5.072219] ehci_hcd 0000:00:13.2: debug port 1
[    5.072230] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf7fff400
[    5.084010] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    5.084058] usb usb2: configuration #1 chosen from 1 choice
[    5.084073] hub 2-0:1.0: USB hub found
[    5.084077] hub 2-0:1.0: 6 ports detected
[    5.084146] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.084157] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.084166] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    5.084196] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    5.084216] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf7ffe000
[    5.144032] usb usb3: configuration #1 chosen from 1 choice
[    5.144051] hub 3-0:1.0: USB hub found
[    5.144060] hub 3-0:1.0: 3 ports detected
[    5.144121] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.144130] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    5.144154] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    5.144167] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf7ffd000
[    5.200027] usb usb4: configuration #1 chosen from 1 choice
[    5.200045] hub 4-0:1.0: USB hub found
[    5.200052] hub 4-0:1.0: 3 ports detected
[    5.200110] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.200119] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.200146] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    5.200163] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf7ffc000
[    5.256035] usb usb5: configuration #1 chosen from 1 choice
[    5.256049] hub 5-0:1.0: USB hub found
[    5.256057] hub 5-0:1.0: 3 ports detected
[    5.256118] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.256126] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.256151] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    5.256164] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf7ffb000
[    5.312030] usb usb6: configuration #1 chosen from 1 choice
[    5.312044] hub 6-0:1.0: USB hub found
[    5.312051] hub 6-0:1.0: 3 ports detected
[    5.312113] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.312122] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.312150] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.312163] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf7ffa000
[    5.368031] usb usb7: configuration #1 chosen from 1 choice
[    5.368047] hub 7-0:1.0: USB hub found
[    5.368055] hub 7-0:1.0: 2 ports detected
[    5.368118] uhci_hcd: USB Universal Host Controller Interface driver
[    5.368166] usbcore: registered new interface driver libusual
[    5.368187] usbcore: registered new interface driver usbserial
[    5.368194] USB Serial support registered for generic
[    5.396014] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    5.529588] usb 2-6: configuration #1 chosen from 1 choice
[    5.529828] hub 2-6:1.0: USB hub found
[    5.530190] hub 2-6:1.0: 4 ports detected
[    5.531615] usbcore: registered new interface driver usbserial_generic
[    5.531617] usbserial: USB Serial Driver core
[    5.531651] PNP: PS/2 Controller [PNP0303:PSKE,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
[    5.531933] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.531937] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.532004] mice: PS/2 mouse device common for all mice
[    5.532088] rtc_cmos 00:04: RTC can wake from S4
[    5.532109] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    5.532132] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    5.532176] device-mapper: uevent: version 1.0.3
[    5.532236] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.532325] device-mapper: multipath: version 1.0.5 loaded
[    5.532327] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.532394] EISA: Probing bus 0 at eisa.0
[    5.532423] Cannot allocate resource for EISA slot 8
[    5.532425] EISA: Detected 0 cards.
[    5.532478] cpuidle: using governor ladder
[    5.532479] cpuidle: using governor menu
[    5.532818] TCP cubic registered
[    5.532888] NET: Registered protocol family 10
[    5.533176] lo: Disabled Privacy Extensions
[    5.533395] NET: Registered protocol family 17
[    5.533405] Bluetooth: L2CAP ver 2.11
[    5.533407] Bluetooth: L2CAP socket layer initialized
[    5.533409] Bluetooth: SCO (Voice Link) ver 0.6
[    5.533410] Bluetooth: SCO socket layer initialized
[    5.533435] Bluetooth: RFCOMM socket layer initialized
[    5.533440] Bluetooth: RFCOMM TTY layer initialized
[    5.533441] Bluetooth: RFCOMM ver 1.10
[    5.533476] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    5.533507] powernow-k8:    0 : pstate 0 (2700 MHz)
[    5.533509] powernow-k8:    1 : pstate 1 (1400 MHz)
[    5.533586] Using IPI No-Shortcut mode
[    5.533630] registered taskstats version 1
[    5.533725]   Magic number: 13:769:621
[    5.533794] rtc_cmos 00:04: setting system clock to 2009-06-06 07:37:18 UTC (1244273838)
[    5.533798] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.533800] EDD information not available.
[    5.534002] Freeing unused kernel memory: 532k freed
[    5.534108] Write protecting the kernel text: 4128k
[    5.534147] Write protecting the kernel read-only data: 1532k
[    5.682006] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.682020] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.682034] r8169 0000:04:00.0: setting latency timer to 64
[    5.682122] r8169 0000:04:00.0: irq 2298 for MSI/MSI-X
[    5.682546] eth0: RTL8168b/8111b at 0xf7c80000, 00:24:8c:db:53:2a, XID 38000000 IRQ 2298
[    5.913285] usb 2-6.1: new low speed USB device using ehci_hcd and address 3
[    5.962458] PM: Starting manual resume from disk
[    5.962460] PM: Resume from partition 8:21
[    5.962462] PM: Checking hibernation image.
[    5.962618] PM: Resume from disk failed.
[    5.968123] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.968125] EXT3-fs: write access will be enabled during recovery.
[    5.984899] usb 2-6.1: device descriptor read/64, error -32
[    6.225166] usb 2-6.1: configuration #1 chosen from 1 choice
[    6.229039] usbcore: registered new interface driver hiddev
[    6.233775] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6.1/2-6.1:1.0/input/input3
[    6.240045] generic-usb 0003:1241:F767.0001: input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:13.2-6.1/input0
[    6.248640] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6.1/2-6.1:1.1/input/input4
[    6.253753] generic-usb 0003:1241:F767.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:13.2-6.1/input1
[    6.253767] usbcore: registered new interface driver usbhid
[    6.253770] usbhid: v2.6:USB HID core driver
[    6.297490] usb 2-6.4: new high speed USB device using ehci_hcd and address 4
[    6.444052] kjournald starting.  Commit interval 5 seconds
[    6.444063] EXT3-fs: sdb1: orphan cleanup on readonly fs
[    6.444068] ext3_orphan_cleanup: deleting unreferenced inode 23150600
[    6.444089] ext3_orphan_cleanup: deleting unreferenced inode 23150599
[    6.444093] ext3_orphan_cleanup: deleting unreferenced inode 23150598
[    6.444096] ext3_orphan_cleanup: deleting unreferenced inode 23150597
[    6.444100] ext3_orphan_cleanup: deleting unreferenced inode 23150596
[    6.444103] EXT3-fs: sdb1: 5 orphan inodes deleted
[    6.444104] EXT3-fs: recovery complete.
[    6.445730] EXT3-fs: mounted filesystem with ordered data mode.
[    7.028325] usb 2-6.4: configuration #1 chosen from 1 choice
[    7.223705] Initializing USB Mass Storage driver...
[    7.223830] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.223894] usbcore: registered new interface driver usb-storage
[    7.223897] USB Mass Storage support registered.
[    7.223948] usb-storage: device found at 4
[    7.223949] usb-storage: waiting for device to settle before scanning
[   11.580672] udev: starting version 141
[   11.784483] Linux agpgart interface v0.103
[   11.786608] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   11.786610] ACPI: Device needs an ACPI driver
[   11.786616] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.789502] parport_pc 00:07: reported by Plug and Play ACPI
[   11.789554] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.800861] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.867433] ppdev: user-space parallel port driver
[   12.026194] nvidia: module license 'NVIDIA' taints kernel.
[   12.115937] saa7164 driver loaded
[   12.116019] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.116365] CORE saa7164[0]: dev->lmmio  = 0xf8e80000
[   12.116367] CORE saa7164[0]: dev->lmmio2 = 0xf7f80000
[   12.116369] CORE saa7164[0]: dev->bmmio  = 0xf8e80000
[   12.116370] CORE saa7164[0]: dev->bmmio2 = 0xf7f80000
[   12.116372] CORE saa7164[0]: subsystem: 0070:8880, board: Hauppauge WinTV-HVR2250 [card=3,autodetected]
[   12.116377] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   12.116382] saa7164 0000:02:00.0: setting latency timer to 64
[   12.122243] Linux video capture interface: v2.00
[   12.172866] cx23885 driver version 0.0.2 loaded
[   12.172907] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.172993] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   12.284518] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.284526] nvidia 0000:01:00.0: setting latency timer to 64
[   12.284683] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.308529] usb-storage: device scan complete
[   12.315277] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   12.321525] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   12.327774] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   12.334025] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   12.336298] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   12.336374] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   12.339117] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   12.339181] sd 6:0:0:1: Attached scsi generic sg4 type 0
[   12.340104] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   12.340166] sd 6:0:0:2: Attached scsi generic sg5 type 0
[   12.341115] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   12.341177] sd 6:0:0:3: Attached scsi generic sg6 type 0
[   12.362302] tveeprom 1-0050: Hauppauge model 78521, rev C1E9, serial# 4851581
[   12.362306] tveeprom 1-0050: MAC address is 00-0D-FE-4A-07-7D
[   12.362308] tveeprom 1-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   12.362310] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   12.362312] tveeprom 1-0050: audio processor is CX23887 (idx 42)
[   12.362314] tveeprom 1-0050: decoder processor is CX23887 (idx 37)
[   12.362315] tveeprom 1-0050: has radio
[   12.362316] cx23885[0]: hauppauge eeprom: model=78521
[   12.384523] saa7164_downloadfirmware() no first image
[   12.384569] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.384572] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   12.455988] cx25840 3-0044: cx25  0-21 found @ 0x88 (cx23885[0])
[   12.460339] cx25840 3-0044: firmware: requesting v4l-cx23885-avcore-01.fw
[   12.631276] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.663226] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.189745] cx25840 3-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   13.293656] tuner 2-0042: chip found @ 0x84 (cx23885[0])
[   13.337014] tda829x 2-0042: could not clearly identify tuner address, defaulting to 60
[   13.372324] tda18271 2-0060: creating new instance
[   13.417409] TDA18271HD/C1 detected @ 2-0060
[   13.592082] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   13.592085] saa7164_downloadfirmware() firmware loaded.
[   13.592086] Firmware file header part 1:
[   13.592089]  .FirmwareSize = 0x0
[   13.592090]  .BSLSize = 0x0
[   13.592091]  .Reserved = 0x3cb57
[   13.592092]  .Version = 0x3
[   13.592093] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   13.592134] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.592135] saa7164_downloadfirmware() BSLSize = 0x0
[   13.592136] saa7164_downloadfirmware() Reserved = 0x0
[   13.592138] saa7164_downloadfirmware() Version = 0x51cc1
[   14.616394] tda829x 2-0042: type set to tda8295+18271
[   15.720500] cx23885[0]/0: registered device video0 [v4l2]
[   16.808561] cx23885[0]: registered device video1 [mpeg]
[   16.808563] cx23885_dvb_register() allocating 1 frontend(s)
[   16.808566] cx23885[0]: cx23885 based dvb card
[   16.897948] MT2131: successfully identified at address 0x61
[   16.899591] DVB: registering new adapter (cx23885[0])
[   16.899594] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   16.899781] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   16.899788] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfbc00000
[   16.899795] cx23885 0000:03:00.0: setting latency timer to 64
[   17.336049] saa7164_downloadimage() Image downloaded, booting...
[   17.336053] saa7164_downloadimage() Image booted successfully.
[   17.336096] starting firmware download(2)
[   19.456010] saa7164_downloadimage() Image downloaded, booting...
[   21.328041] saa7164_downloadimage() Image booted successfully.
[   21.328085] firmware download complete.
[   21.329052] saa7164[0]: i2c bus 0 registered
[   21.329099] saa7164[0]: i2c bus 1 registered
[   21.329141] saa7164[0]: i2c bus 2 registered
[   21.364440] tveeprom 4-0000: Hauppauge model 88041, rev C1F2, serial# 5185686
[   21.364443] tveeprom 4-0000: MAC address is 00-0D-FE-4F-20-96
[   21.364444] tveeprom 4-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   21.364447] tveeprom 4-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   21.364448] tveeprom 4-0000: audio processor is SAA7164 (idx 43)
[   21.364450] tveeprom 4-0000: decoder processor is SAA7164 (idx 40)
[   21.364452] tveeprom 4-0000: has radio
[   21.364453] saa7164[0]: Hauppauge eeprom: model=88041
[   21.708374] tda18271 5-0060: creating new instance
[   21.712861] TDA18271HD/C2 detected @ 5-0060
[   21.964806] DVB: registering new adapter (saa7164)
[   21.964810] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.249805] tda18271 6-0060: creating new instance
[   22.253895] TDA18271HD/C2 detected @ 6-0060
[   22.504742] DVB: registering new adapter (saa7164)
[   22.504745] DVB: registering adapter 2 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.605944] lp0: using parport0 (interrupt-driven).
[   22.653952] Adding 9068652k swap on /dev/sdb5.  Priority:-1 extents:1 across:9068652k
[   23.177186] EXT3 FS on sdb1, internal journal
[   24.047009] type=1505 audit(1244273857.010:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2259
[   24.081016] type=1505 audit(1244273857.046:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2263
[   24.081089] type=1505 audit(1244273857.046:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2263
[   24.081118] type=1505 audit(1244273857.046:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2263
[   24.081144] type=1505 audit(1244273857.046:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2263
[   24.177159] type=1505 audit(1244273857.142:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2268
[   24.177285] type=1505 audit(1244273857.142:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2268
[   24.202730] type=1505 audit(1244273857.166:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2272
[   24.221566] type=1505 audit(1244273857.186:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2276
[   30.984818] r8169: eth0: link up
[   30.984823] r8169: eth0: link up
[   33.237931] r8169: eth0: link up
[   34.568873] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.568876] Bluetooth: BNEP filters: protocol multicast
[   34.575114] Bridge firewalling registered
[   35.178580] tda18271: performing RF tracking filter calibration
[   37.849532] tda18271: RF tracking filter calibration complete
[   44.148010] eth0: no IPv6 routers present
[   64.966481] UDF-fs: Partition marked readonly; forcing readonly mount
[   65.024228] UDF-fs INFO UDF: Mounting volume 'SHREK_2_US_4X3', timestamp 2004/06/29 06:16 (1000)
[  650.112940] usb 2-6.4: reset high speed USB device using ehci_hcd and address 4
```

lspci output:
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a
    Kernel modules: ati-agp

00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f8000000-fb3fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) [1002:597a]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fb400000-fbbfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E) [1002:597e]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fbc00000-fbdfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390] (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at c000 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=16]
    Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f7fff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f7fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
    Kernel driver in use: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:837b]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
    Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control [1022:1204]
    Flags: fast devsel

01:00.0 VGA compatible controller [0300]: nVidia Corporation D9M-20 [GeForce 9400 GT] [10de:0641] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:1571]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fb380000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

02:00.0 Multimedia controller [0480]: Philips Semiconductors Device [1131:7164] (rev 81)
    Subsystem: Hauppauge computer works Inc. Device [0070:8880]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
    Memory at fb400000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
    Capabilities: [50] Express Endpoint, MSI 00
    Capabilities: [74] Power Management version 3
    Capabilities: [7c] Vendor Specific Information <?>
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [160] Virtual Channel <?>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

03:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Device [14f1:8880] (rev 0f)
    Subsystem: Hauppauge computer works Inc. Device [0070:7801]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data <?>
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [200] Virtual Channel <?>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8385]
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at e800 [size=256]
    Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at fbfc0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 00-e0-4c-68-00-00-00-40
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

lsmod output:
```
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
s5h1411                17668  2 
mt2131                 13444  1 
s5h1409                16772  1 
tda18271               42888  3 
tda8290                21000  1 
tuner                  29960  1 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
cx25840                35444  1 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
cx23885               104084  0 
cx2341x                22020  1 cx23885
videobuf_dma_sg        20484  1 cx23885
v4l2_common            23808  4 tuner,cx25840,cx23885,cx2341x
videodev               44704  4 tuner,cx25840,cx23885,v4l2_common
v4l1_compat            21764  1 videodev
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
videobuf_dvb           15108  1 cx23885
saa7164                67336  1 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videobuf_core          26244  3 cx23885,videobuf_dma_sg,videobuf_dvb
nvidia               7233756  36 
snd_timer              29704  2 snd_pcm,snd_seq
dvb_core               93440  3 cx23885,videobuf_dvb,saa7164
btcx_risc              13064  1 cx23885
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
psmouse                61972  0 
tveeprom               20228  2 cx23885,saa7164
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13316  0 
pcspkr                 10496  0 
parport_pc             40100  1 
i2c_piix4              18448  0 
ati_agp                14988  0 
agpgart                42696  2 nvidia,ati_agp
soundcore              15200  1 snd
parport                42220  3 lp,ppdev,parport_pc
joydev                 18368  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usb_storage            82880  0 
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

dmidecode output:
```

# dmidecode 2.9
SMBIOS 2.5 present.
67 structures occupying 2396 bytes.
Table at 0x0009F000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 0602   
    Release Date: 04/09/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.15

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: System manufacturer
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    UUID: E0630870-D72C-DE11-8C55-00248CDB532A
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M4A78 PLUS
    Version: Rev X.0x
    Serial Number: MT7094K10700525
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Chassis Manufacture
    Type: Desktop
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Asset-1234567890
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000001
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
    Socket Designation: AM2
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: AMD              
    ID: 23 0F 10 00 FF FB 8B 17
    Version: AMD Athlon(tm) 7750 Dual-Core Processor             
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max Speed: 3200 MHz
    Current Speed: 2700 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 2
    Core Enabled: 2
    Characteristics:
        64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 256 KB
    Maximum Size: 256 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 8 KB
    Maximum Size: 8 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 KeyBoard
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB12
    Internal Connector Type: None
    External Reference Designator: USB12
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB34
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB56
    Internal Connector Type: None
    External Reference Designator: USB45
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB78
    Internal Connector Type: None
    External Reference Designator: USB67
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB11
    Internal Connector Type: None
    External Reference Designator: USB89
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT 1
    Internal Connector Type: None
    External Reference Designator: LPT 1
    External Connector Type: DB-25 male
    Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM 1
    Internal Connector Type: None
    External Reference Designator: COM 1
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LAN
    Internal Connector Type: None
    External Reference Designator: LAN
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Line_In
    Internal Connector Type: None
    External Reference Designator: Audio_Line_In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Line_Out
    Internal Connector Type: None
    External Reference Designator: Audio_Line_Out
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Mic_In
    Internal Connector Type: None
    External Reference Designator: Audio_Mic_In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Center/Sub
    Internal Connector Type: None
    External Reference Designator: Audio_Center/Sub
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Rear
    Internal Connector Type: None
    External Reference Designator: Audio_Rear
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Side
    Internal Connector Type: None
    External Reference Designator: Audio_Side
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SPDIF_O
    Internal Connector Type: None
    External Reference Designator: SPDIF_O
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ESATA
    Internal Connector Type: None
    External Reference Designator: ESATA
    External Connector Type: SAS/SATA Plug Receptacle
    Port Type: SATA

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRI IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB_SATA1
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB_SATA2
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB_SATA3
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB_SATA5
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB_SATA6
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PWR FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CHA FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB910
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USBE12
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USBE34
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PANEL
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SPDIF OUT
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0028, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AAFP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0029, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CD
    Internal Connector Type: On Board Sound Input From CD-ROM
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x002A, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIE16X
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIE16X_2
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIE1X
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 10
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 12
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002E, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 13
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002F, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 14
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0030, DMI type 10, 6 bytes
On Board Device Information
    Type: Other
    Status: Enabled
    Description:   To Be Filled By O.E.M.

Handle 0x0031, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: To Be Filled By O.E.M.

Handle 0x0032, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: To Be Filled By O.E.M.

Handle 0x0033, DMI type 10, 6 bytes
On Board Device Information
    Type: Other
    Status: Enabled
    Description: To Be Filled By O.E.M.

Handle 0x0034, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.
    String 2: To Be Filled By O.E.M.
    String 3: To Be Filled By O.E.M.
    String 4: To Be Filled By O.E.M.

Handle 0x0035, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0036, DMI type 15, 35 bytes
System Event Log
    Area Length: 4 bytes
    Header Start Offset: 0x0000
    Header Length: 2 bytes
    Data Start Offset: 0x0002
    Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
    Access Address: Index 0x046A, Data 0x046C
    Status: Invalid, Not Full
    Change Token: 0x00000000
    Header Format: No Header
    Supported Log Type Descriptors: 6
    Descriptor 1: End of log
    Data Format 1: OEM-specific
    Descriptor 2: End of log
    Data Format 2: OEM-specific
    Descriptor 3: End of log
    Data Format 3: OEM-specific
    Descriptor 4: End of log
    Data Format 4: OEM-specific
    Descriptor 5: End of log
    Data Format 5: OEM-specific
    Descriptor 6: End of log
    Data Format 6: OEM-specific

Handle 0x0037, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0038, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0012FFFFFFF
    Range Size: 4864 MB
    Physical Array Handle: 0x0037
    Partition Width: 0

Handle 0x0039, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0037
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz (1.2 ns)
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x003A, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0039
    Memory Array Mapped Address Handle: 0x0038
    Partition Row Position: 1

Handle 0x003B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0037
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz (1.2 ns)
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x003C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x003B
    Memory Array Mapped Address Handle: 0x0038
    Partition Row Position: 1

Handle 0x003D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0037
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer2
    Serial Number: SerNum2
    Asset Tag: AssetTagNum2
    Part Number: PartNum2

Handle 0x003E, DMI type 126, 19 bytes
Inactive

Handle 0x003F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0037
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer3
    Serial Number: SerNum3
    Asset Tag: AssetTagNum3
    Part Number: PartNum3

Handle 0x0040, DMI type 126, 19 bytes
Inactive

Handle 0x0041, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0042, DMI type 127, 4 bytes
End Of Table

```

---

### Post by android6011 on 2009-07-27
So does anyone have this working 100%? If so, out of the box from a clean install, what steps are needed to get this working with mythtv?

---

### Post by wasutton3 on 2009-07-29
my sentiments exactly. I have been following this for a year and a half now. (on and off, as a student i cant be compiling this and that all the time) and it sounds like it is finally ready.

---

### Post by cenwesi on 2009-07-30
> **wasutton3 said:**
> my sentiments exactly. I have been following this for a year and a half now. (on and off, as a student i cant be compiling this and that all the time) and it sounds like it is finally ready.

where did you hear that it is read?

---

### Post by wasutton3 on 2009-07-30
> **theduke88 said:**
> Proud to report that my Hauppauge 1800 is now working 100% under MythTv under the following configuration:


right there

---

### Post by android6011 on 2009-07-30
Ok guys, I tracked down one of the driver developers at [http://www.kernellabs.com/blog/](http://www.kernellabs.com/blog/), this is what he had to say:

> Hi,

NTSC is supported, but Myth currently has some issues understanding that the encoder output comes from a difference place in the driver. This is currently under review. Michael Krufky and myself are reworking part of the driver to remove this issue. I don't have an ETA for this work but I'd expect it to be complete in the next few weeks.

- Steve


---

### Post by NTolerance on 2009-07-30
> **android6011 said:**
> Ok guys, I tracked down one of the driver developers at [http://www.kernellabs.com/blog/](http://www.kernellabs.com/blog/), this is what he had to say:

That's good news.  With regards to the current state of development, would it be accurate to say that this card is has the best support of all PCI-E cards at the moment/near future?  

My HTPC only has an open PCI-E slot so it's a requirement for me.  If analog doesn't work now but will work in the future I can deal with that.  I can still use my PVR-150 in the meantime.

Also, what about the HVR-1250?  Does it have the same level of support as the HVR-1800?  I may not need the analog tuners anyways and could save some money by going with the HVR-1250.

---

### Post by cenwesi on 2009-07-31
> **wasutton3 said:**
> right there

Guys, would you guys please kindly tell us what kernel you are running and what v4l version as well as what you did to get it to work?

---

### Post by cenwesi on 2009-08-04
Well guys, it looks like the digital side of this card works but not the analog part? Any one else have luck with the analog side?

---

### Post by jtmoney on 2009-08-12
Any updates on this card and its status in MythTV?  Should I continue to hold out, or should I buy a different PCIE ATSC/NTSC card?

---

### Post by agamotto on 2009-08-12
Digital works fairly well, I have been using it for nearly a year now.  The analog may work with various patches, but I haven't bothered until it becomes a part of the package updates that come out regularly.

---

### Post by nbetham on 2009-08-25
HI, I have managed to get the analog side of this card partially working. I get sound and video when i set the card up as an MPEG2 source and then typing /dev/video1 in the video device section, it seems to find all the data on the card fine. The problem I have is that whenever I access the MPEG2 encoder side no matter what application I use the audio is very deep and the video is in slow motion. I have run the MythTv frontend in verbose mode and it indicates that the video is around 3 to 4 frames ahead of the audio and tries to slow it down but it never works. I have attached the readout from mythfrontend in verbose mode hopefully it will help to diagnose the problem. 

Any help on this issue would be greatly appreciated.

---

### Post by agwells0714 on 2009-08-27
I just got the Hauppauge 1800 card

I am running Ubuntu 9.04 64bit

and I have compiled the v4l-dvb source as described in this post

however in my /dev/ folder I get video0, but NOT video1

I do however get the /dev/dvb/adapter0/

> 
crw-rw----+ 1 root video 212, 1 2009-08-27 14:37 demux0
crw-rw----+ 1 root video 212, 2 2009-08-27 14:37 dvr0
crw-rw----+ 1 root video 212, 0 2009-08-27 14:37 frontend0
crw-rw----+ 1 root video 212, 3 2009-08-27 14:37 net0


---

### Post by nbetham on 2009-08-27
Try these directions [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") and once you finish with the make install of the drivers go to this page [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800") and about half way down it shows how to get analog working which is /dev/video1. As well if it possible for you I would start with a fresh install of ubuntu. Although i'm not sure that it works fully with mythbuntu. I can get it to play and record in mythbuntu but it is in slow motion and the audio is very deep.

Update: Well I Just talked to some people on the mythtv irc channel and they say that there is a bug that currently prevents the use of the analog tuner but that it is currently being fixed. Hopefully that happens soon.

---

### Post by wasutton3 on 2009-09-24
Alright, its been a month now since i have seen any activity on this thread. Have we given up or is progress being made elsewhere?

---

### Post by nbetham on 2009-09-24
Well, I have been in contact with the developer who has been working on a fix, but there has been no real activity in his section of Mercurial on his site for a couple months. But he has made some progress on the card. Myth is now able to recognize the different inputs through the MPEG encoder, although the experience I have had with experimental driver leads me to believe there is a bit to go to fix it. Currently channel changing is still broken, according to the developer he can get it to change to a few channels but after that the system hangs. The website I would recommend keeping tabs on is [www.kernellabs.com](www.kernellabs.com) this is where the dev posts info about things pertaining to what he is working on, this is where he told me they would post an update when it became available. If you would like to try the experimental driver it is in an HG directory here [www.kernellabs.com/hg/~stoth/cx23885-api/](www.kernellabs.com/hg/~stoth/cx23885-api/) just build it like the regular V4l-DVB tree. This is all the info I have currently on the status of this card. I haven't given up hope yet but I'm starting to think it might be time to look for a different capture card.

---

### Post by android6011 on 2009-09-30
Everyone should show their support in the comments of:

[http://www.kernellabs.com/blog/?p=788](http://www.kernellabs.com/blog/?p=788)

and anyone that can, keep an eye out for his releases to help testing

---

### Post by cenwesi on 2009-09-30
posted :)

---

### Post by jtmoney on 2009-11-04
What a joke this has become.  I wonder how many more years it will be before analog functionality is working on this card.  Time to buy a different card, I'm afraid.

Yes, I know, I should just "write my own driver" instead of bitching about the lack of one.  I would have if the developers had BEEN REALISTIC IN THEIR TIMEFRAMES.

What a joke.

---

### Post by nbetham on 2009-11-04
You have to remember though the developers do this work for free and get nothing out of it. We are lucky to actually have someone willing to work out the kinks in the driver. While it may have taken way longer than most of us have wanted it too the work is getting done to fix the driver.

---

### Post by michcook on 2009-11-05
> **nbetham said:**
> Well, I have been in contact with the developer who has been working on a fix, but there has been no real activity in his 
section of Mercurial on his site for a couple months.....

V4l-DVB Mercurial SVN tagging
--------------------------------
Unless I'm missing something is there any reason why the Mercurial V4L-DVB drivers aren't tagged against a kernel release in svn?  

I had no luck getting HVR1800 to "just work" with Ubuntu 9.04 unless I downloaded v4l-dvb drivers from Mercurial (following some blog)... I had limited success using tvtuner.  In between attempt 1 & 2 ubuntu kernel was upgraded by updates... then everything stopped working.  I then installed MythTV (as per another blog) and things got a lot further but had to recompile the V4l-DVB drivers (for newer kernel).

There seemed to be some 'magic' (API alignment in kernel versions) by using some September-timeframe v4l-dvb (pre-2.6.31) which happen to compile with Ubuntu 9.04.  Using the latest (Oct 2009) v4l-dvb APIs had changed and kernel version updated from Mercurial they need 2.6.31+ kernel drivers to compile cx23885 drivers.  This was only apparent by examining the compilation log.

Overall, I know assume (maybe someone can clarify) that Ubuntu9.10 and the latest (Nov 2009) v4l-dvb drivers will work together but was surprised there was no svn tags to pull a specific v4l-dvb version against a specific kernel release. Maybe it is more compilicated?

The upshot is that it makes following the various compilation guides somewhat hit-and-miss as they all age in relevance and kernel versions.


HD Jerky playback on fast moving scenes
-----------------------------------------
The only other problem I presently have is jerky playback for fast-moving scenes.  I think this is playback and not recording issue.  Does anyone else have any opinions on whether this is kernel, ubuntu, driver, HDD or CPU based?  I'm troubleshooting this one... upgrading to 9.10 I doubt will fix this?  Meanwhile I've disabled all Ubuntu updates because I'll have to recompile everything 'at some point' and I have it working presently.

Thanks
----------------------------------------
Thanks to those who've posted how-to do anything with this card & MythTV and of course, I completely understand this is an opensource effort... great work!

---

### Post by waltclay on 2009-11-17
[http://www.kernellabs.com/blog/]("http://www.kernellabs.com/blog/")will always get you to the latest post. Easy to scroll back through posts. Nothing new on 1800.Tutorial on tuner design.

---

