---
title: "DViCO FusionHDTV DVB-T Dual Digital 4 with remote tutorial"
date: 2007-11-19
forum: Mythbuntu
---

### Post by oobe-feisty on 2007-11-19
This thread is outdated 
here is the new one that i will try my best to maintain [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)

---

### Post by oobe-feisty on 2007-11-19
edited

---

### Post by bejam on 2007-11-28
Followed the instructions but I never get a /dev/lirc and running irw causes lircd to exit. Have a grey remote for the Dual Digital 4... think it might be different to some. The output from the hardware dump has two entries for event6 and event7 (identical). Have tried setting hardware.conf to both event6 and event7.


I: Bus=0003 Vendor=0fe9 Product=db78 Version=b0a3
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:0a.2-1/ir0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=c00a4 2183051 0 0 0 0 110000 1b8 40002841 1e1680 0 0 10008ffc

I: Bus=0003 Vendor=0fe9 Product=db78 Version=b0a3
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:0a.2-2/ir0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=c00a4 2183051 0 0 0 0 110000 1b8 40002841 1e1680 0 0 10008ffc

Any help gratefully received!

---

### Post by superm1 on 2007-11-28
In looking this over, is it really necessary to reinstall LIRC?  Any remotes that support the dev/input layer can be manually configured still.

Also, can you please file a bug with the lircd.conf for this remote against lirc so that we can support it for hardy?

---

### Post by oobe-feisty on 2007-12-08
> **superm1 said:**
> In looking this over, is it really necessary to reinstall LIRC?  Any remotes that support the dev/input layer can be manually configured still.

Also, can you please file a bug with the lircd.conf for this remote against lirc so that we can support it for hardy?

I woulld be happy to submit all my lircd.conf and lirc to get this remote working 


as for installing from source in hindsight i think you are right is it really a a bug report i need to fill out to submit the lircrc and lircd.conf

---

### Post by oobe-feisty on 2007-12-08
> **bejam said:**
> Followed the instructions but I never get a /dev/lirc and running irw causes lircd to exit. Have a grey remote for the Dual Digital 4... think it might be different to some. The output from the hardware dump has two entries for event6 and event7 (identical). Have tried setting hardware.conf to both event6 and event7.


I: Bus=0003 Vendor=0fe9 Product=db78 Version=b0a3
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:0a.2-1/ir0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=c00a4 2183051 0 0 0 0 110000 1b8 40002841 1e1680 0 0 10008ffc

I: Bus=0003 Vendor=0fe9 Product=db78 Version=b0a3
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:0a.2-2/ir0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=c00a4 2183051 0 0 0 0 110000 1b8 40002841 1e1680 0 0 10008ffc

Any help gratefully received!

here is a pic of the remote i got with the DD4 [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dd4-remote.PNG](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dd4-remote.PNG)
you are not meant to get a /dev/lirc u should be looking for /dev/input/eventx replace x with any number 

as you can see it is black i am going to rewrite this turorial soon as the DD4 driver is merged but the firmware is not released.

is what you pasted the out put of cat /proc/bus/input/devices or are you copying and pasting it directly from my tutorial the best thing i can suggest at the moment is that you post the output of the following back here 

"cat /proc/bus/input/devices"

"dmesg | grep IR"
"dmesg | grep DVB"


hope to hear from you soon

---

### Post by curren on 2007-12-15
Hi, 

Thanks for the tutorial. Have a fusionHDTV dual digital 4. I ran the script on a fresh Mythbuntu 7.10 build after removing comment from apt lines. 

All appeared to go well with the exception of some hunk failures - at the end of script I got two fatal module errors as follows:

FATAL: Module xc3028_fe not found.
FATAL: Module xc3028_fe not found.

Also ls /dev/dvb/* gave me "ls: /dev/dvb/*: No such file or directory"


Any suggestions?

Thanks

---

### Post by curren on 2007-12-16
OK got the modules loading - seems I did not have kernel headers installed and so if failed on the make / make install. Installed the header file with this command:

sudo apt-get install linux-headers-2.6.22-14-generic

---

### Post by oobe-feisty on 2007-12-16
> **curren said:**
> OK got the modules loading - seems I did not have kernel headers installed and so if failed on the make / make install. Installed the header file with this command:

sudo apt-get install linux-headers-2.6.22-14-generic

thanks i add this to the apt lines linux-headers-`uname -r`

---

### Post by hawko on 2008-02-09
Great work.

Things are going pretty good except that my second tuner is getting no love. DVB0 is working fine but I am getting nothing from DVB1. I didn't follow the turtorial (you clone from main tree now) but I reviewed all of the steps.

 I test using tzap:

**Adapter 0 - **No probs
```

hawko@mythbox:~$ tzap -a 0 -c /etc/channels.conf -r "ABC2"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 205625000 Hz
video pid 0x0903, audio pid 0x0904
status 00 | signal 2a60 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1e | signal b568 | snr c4c4 | ber 00000000 | unc 00000152 | FE_HAS_LOCK
status 1e | signal b640 | snr c4c4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK

```

**Adapter 1 -** Nothing
```
hawko@mythbox:~$ tzap -a 1 -c /etc/channels.conf -r "ABC2"
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
tuning to 205625000 Hz
video pid 0x0903, audio pid 0x0904
status 00 | signal 3478 | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 2638 | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 26cc | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 261c | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 22f4 | snr 0000 | ber 00000000 | unc 00000000 | 
```

Any suggestions?

---

### Post by martymoose on 2008-02-15
just building a new box
bought a new dvico dual 4 pci card
followed all the tuts but still will not work
bloke on other forum said it could be a new revision
as i had to wait a week for the card to arive from dvico to the supplier
any way heres what i posted about mine and his

note product id's are changed a bit

my quote
"i am setting up mythbuntu
i have a brand new (3 days old) dd4 card
was a new batch from korea
i have followed and tried every option i can find on google, here, and from chris pascoe
the card will not appear in mythtv
linux kind of see's it
lsusb
Bus 004 Device 002: ID 0e5e:6622
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0424:2228 Standard Microsystems Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0fe9:db98 DVICO
Bus 002 Device 002: ID 0fe9:db98 DVICO
Bus 002 Device 001: ID 0000:0000

lspci
01:0e.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:0e.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:0e.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

can anyone help
from an other forum i guy reakons it might be a new revision
so i have email chris pascoe hope he gets back
cheers marty"

matts answer about his dd4
 marty writes...

Bus 002 Device 003: ID 0fe9:db98 DVICO
Bus 002 Device 002: ID 0fe9:db98 DVICO

Hmm; that's strange. My DD4 cards appear as:

Bus 008 Device 003: ID 0fe9:db78 DVICO
Bus 008 Device 002: ID 0fe9:db78 DVICO

Bus 007 Device 002: ID 0fe9:db78 DVICO
Bus 007 Device 003: ID 0fe9:db78 DVICO
(emphasis mine)

Edit: read the rest of your post. I agree with the other forum - looks like you have a new version of the card. Try emailing Chris to see if he's seen one in the wild.

---

### Post by oobe-feisty on 2008-02-19
here is my lsusb 

Bus 002 Device 003: ID 0fe9:db78 DVICO
Bus 002 Device 002: ID 0fe9:db78 DVICO

i seen a guy reporting the same problem on the linux tv mailing list

---

### Post by martymoose on 2008-02-19
yea thats me
theres a post over on whirlpool.net.au about the new card
there are 2 of use now so looks like a new revision
onto chris got to get some hires photos for him
cheers

---

### Post by vk3heg on 2008-02-22
I also have just got a DViCO Dual4, after spending a couple of months searching/researching for a good card with two tuners and linux support.

I'm in the same boat as the last poster, my card isn't detected correctly.

lsusb outout is:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0fe9:db98 DVICO 
Bus 004 Device 002: ID 0fe9:db98 DVICO 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

(I have pulled down the latest v4l code, and install it, with no luck).

Mythtv (mythbunto 7.10+ updates) doesn't detect the card. :confused:

---

### Post by wombo on 2008-02-22
I brought a card today too and am having troubles with it

**lsusb**
Bus 007 Device 003: ID 0fe9:db78 DVICO
Bus 007 Device 002: ID 0fe9:db78 DVICO 

I have been following this guide: [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4)

when I get to 'make' I get this error
```
htpc@htpc:~/v4l-dvb$ make
make -C /home/htpc/v4l-dvb/v4l 
make[1]: Entering directory `/home/htpc/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.24
File not found: /lib/modules/2.6.24-7-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/htpc/v4l-dvb/v4l'
make: *** [all] Error 2
```

Has anyone got any ideas, ive done a google but cant seem to find anything.

I have tried upgrading the kernel from 2.6.24-7-generic to 2.6.24-8-generic which does not seem to help.

Its also worth noting that the old 2.6.24-7 directory does NOT have a 'build' directory but the 2.6.24.8 directory does.

Should it be trying to use the 24-8 directory instead of 24-7, if so how would this be done?

Thanks

---

### Post by martymoose on 2008-02-22
> **vk3heg said:**
> I also have just got a DViCO Dual4, after spending a couple of months searching/researching for a good card with two tuners and linux support.

I'm in the same boat as the last poster, my card isn't detected correctly.

lsusb outout is:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0fe9:db98 DVICO 
Bus 004 Device 002: ID 0fe9:db98 DVICO 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

(I have pulled down the latest v4l code, and install it, with no luck).

Mythtv (mythbunto 7.10+ updates) doesn't detect the card. :confused:

re 0fe9:db98
have been in touch with chris pascoe
he is a very busy man but has agreed to look at my card
just waiting for some time for him to be available
ill keep you posted

---

### Post by wombo on 2008-03-03
[http://forums.whirlpool.net.au/forum-replies.cfm?t=919552&p=3](http://forums.whirlpool.net.au/forum-replies.cfm?t=919552&p=3)

You all might be interested in following this thread regarding the new revision of the card

---

### Post by dacium on 2008-06-02
i cant even get lirc to make...

dump_config.c:218: error: struct 'ir_remote' has no member named 'ignore_mask'

how can the latest csv available 'build' not even compile. rediculous

---

### Post by DadAgain on 2008-07-27
I have a rev1.0 DD4 card - (after much searching). and decided it was time to throw away my old FC4 Myth system and crappy over sensitive tuners (twinhan) and rebuild. My initial attempts at Mythdora5 left me with a completely silent machine with lots of problems so I tried mythbuntu 8.04. Initially things seem ok - but I'm having a few troubles with the tuner.

I've tried running through the tutorial above to get the tuners going but to no avail this is the output when I try and run the dvb_installer script at the top of this thread.

```
make[3]: *** [/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l/cxusb.o] Error 1
make[2]: *** [_module_/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l'
make: *** [all] Error 2
rm: cannot remove `firmware_v*.tgz': No such file or directory
--14:01:22--  http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/6591/dd4_firmware.tgz
           => `dd4_firmware.tgz'
Resolving www.itee.uq.edu.au... 130.102.79.1
Connecting to www.itee.uq.edu.au|130.102.79.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,150 (27K) [application/x-tar]

100%[=====================================================================>] 27,150        --.--K/s

14:01:22 (288.10 KB/s) - `dd4_firmware.tgz' saved [27150/27150]

FATAL: Module xc3028_fe not found.
FATAL: Module xc3028_fe not found.
myusername@mymachinename:~/dvico_tutorial/tuner$ ls -ls /dev/dvb*
ls: cannot access /dev/dvb*: No such file or directory

```

Any clues?

---

### Post by oobe-feisty on 2008-08-25
> **DadAgain said:**
> I have a rev1.0 DD4 card - (after much searching). and decided it was time to throw away my old FC4 Myth system and crappy over sensitive tuners (twinhan) and rebuild. My initial attempts at Mythdora5 left me with a completely silent machine with lots of problems so I tried mythbuntu 8.04. Initially things seem ok - but I'm having a few troubles with the tuner.

I've tried running through the tutorial above to get the tuners going but to no avail this is the output when I try and run the dvb_installer script at the top of this thread.

```
make[3]: *** [/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l/cxusb.o] Error 1
make[2]: *** [_module_/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/myusername/dvico_tutorial/tuner/v4l-dvb/v4l'
make: *** [all] Error 2
rm: cannot remove `firmware_v*.tgz': No such file or directory
--14:01:22--  http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/6591/dd4_firmware.tgz
           => `dd4_firmware.tgz'
Resolving www.itee.uq.edu.au... 130.102.79.1
Connecting to www.itee.uq.edu.au|130.102.79.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,150 (27K) [application/x-tar]

100%[=====================================================================>] 27,150        --.--K/s

14:01:22 (288.10 KB/s) - `dd4_firmware.tgz' saved [27150/27150]

FATAL: Module xc3028_fe not found.
FATAL: Module xc3028_fe not found.
myusername@mymachinename:~/dvico_tutorial/tuner$ ls -ls /dev/dvb*
ls: cannot access /dev/dvb*: No such file or directory

```

Any clues?

yes im sorry that tutorial and script is now outdated i didnt have a chance to update till now here is the link to the tutorial i will try to maintain [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)

---

### Post by oobe-feisty on 2008-09-08
I know this question is old but usually when one of the tuners is missing or not working it can be resolved by turning off the pc **not** rebooting for a minute or 2 i remember reading this on a mailing list somewhere i havent needed to do this for some time though and it may no longer be an issue with the latest firmware and drivers.


> **hawko said:**
> Great work.

Things are going pretty good except that my second tuner is getting no love. DVB0 is working fine but I am getting nothing from DVB1. I didn't follow the turtorial (you clone from main tree now) but I reviewed all of the steps.

 I test using tzap:

**Adapter 0 - **No probs
```

hawko@mythbox:~$ tzap -a 0 -c /etc/channels.conf -r "ABC2"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 205625000 Hz
video pid 0x0903, audio pid 0x0904
status 00 | signal 2a60 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1e | signal b568 | snr c4c4 | ber 00000000 | unc 00000152 | FE_HAS_LOCK
status 1e | signal b640 | snr c4c4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK

```

**Adapter 1 -** Nothing
```
hawko@mythbox:~$ tzap -a 1 -c /etc/channels.conf -r "ABC2"
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
tuning to 205625000 Hz
video pid 0x0903, audio pid 0x0904
status 00 | signal 3478 | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 2638 | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 26cc | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 261c | snr 0000 | ber 00000000 | unc 00000000 | 
status 00 | signal 22f4 | snr 0000 | ber 00000000 | unc 00000000 | 
```

Any suggestions?

---

### Post by hawko on 2008-09-08
Thanks for the reply.  Unfortunately, as I couldn't get any joy (even in windows in the end) I sent the card back for a replacement.  That was a bad idea, because it got replaced with the new rev card so screwed me horribly.  However, thanks to the great community, I have it up and running now, remote and all.

Thanks again for your help (and your lircrc ;)

Hawko

---

### Post by maniaq on 2009-03-21
Hello, did you get the remote working with lirc? I have the new rev card and I've got everything but the remote going...

The remote works only insofar as it doubles as a keyboard - but that's only good for a handful of buttons - I've had no joy with lirc whatsoever...

Can you possibly post your lircrc and maybe hardware.conf contents?


cheers

---

### Post by wombo on 2009-03-29
Hi all I have rev2 of this card it has been working fine on my 8.04 system for ages now. but today I reinstalled for a number of reasons not to do with the tuner. hence it is now on Mythbuntu 9.04 beta.

But since the install I have not been able to get the tuner going at all. When I try the scan in Mythbuntu setup I get the following error
    Timeout Scanning -- no 
But the status is Locked.

If I try the following
    scan /usr/share/dvb/dvb-t/au-Perth
I get 'Tuning Failed' errors

If I try the following
    w_scan -a 1 (first tuner on DD4r2)
all it does is the following
177500:
184500:
191500:
etc


Does anyone have any ideas of what could be causing this?

I have trying playing with the cabling including removing everything except the single tuner. but it was all working ok before the reinstall.

---

### Post by oobe-feisty on 2009-03-30
please use the current thread [http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103) 

answer these questions in above thread.

did you compile the v4l-dvb source or are you using modules in the newer kernel ?

what does "dmesg | grep dvb" say?



 > I have trying playing with the cabling including removing everything except the single tuner. but it was all working ok before the reinstall.

do you have a cable on your pci tuner that plugs in are you sure this is a dd4?

---

