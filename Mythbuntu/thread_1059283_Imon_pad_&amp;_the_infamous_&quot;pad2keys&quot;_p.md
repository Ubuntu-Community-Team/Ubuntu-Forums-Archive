---
title: "Imon pad &amp; the infamous &quot;pad2keys&quot; patch"
date: 2009-02-03
forum: Mythbuntu
---

### Post by bag123 on 2009-02-03
Folks,

I have been struggling for several years to get a mythtv system working.  I'm considerably closer now I'm trying to use Mythbuntu, but I am still struggling on a basic function with my Imon Pad remote control.

I have a case that came with an integrated Imon VFD and an Imon Pad remote control.  The Imon pad remote (for those that don't know) contains a pad button that is a touch/pressure sensitive pad.  Under normal conditions, it controls the mouse movement.  Very handy.

However, many people (myself included) find that on a Myth TV box it would be more useful to not see the mouse cursor.  After all, Myth TV strives to make your mythbox a simple (but nevertheless incredibly powerful) utility tool and not a computer...  As such, they would prefer the pad to be used as a simple up/down/left/right cursor that aids menu selection and navigation.

A patch has existed for some time that allows this functionality.  Known pretty much universally as the "pad2keys" patch, it has been floating around the Internet in a couple of different incarnations for various versions of lirc.  A quick Google will bring up a gazillion results discussing its use.

Over the last year, a request was submitted to the Ubuntu team on Launchpad(?) for the inclusion of this into the lirc binary - to allow people to enable the pad2keys patch if they so wished.  As far as I can tell (although I've lost the link), this was done.

I verified several weeks ago that my current version of Mythbuntu (8.10) does in fact include this latest binary - and that it includes the pad2keys patch (the output of some obscure command at the cli posted the version of lirc/Imon driver and that fact that it included the pad2keys patch).  This is a great step forward and helps those less gifted Linux newbies among us (such as myself) the option of just "requesting" that this option is switched on rather than go through a convoluted list of instructions that required patching and recompiling the driver - something I tried over ten times and failed at every attempt.  

However, now that the code is included in the driver, I can't for the life of me find out how to enable this option.  And it sure as hell don't work as a simple navigation tool as it currently stands...  To be fair, it's not supposed to - from what I remember about the Launchpad request, the default is supposed to be the normal driver, and the changed version is supposed to be the pad2keys approach.  But I can't seem to enable the pad2keys functionality.

I have spent months researching this weekly and have not got very far.  There's loads of information out there about how to patch the older versions via the long list of commands that failed on me every time.  Or even alternative long lists of commands for other versions (that have also failed for me).  But nothing out there that indicates what to do with the newly updated Mythbuntu version.

I really could do with some help here.  If I can get the pad2keys stuff working, then at least I can start to use the system as a DVD player whilst I attack the considerably more difficult problems of using a Common Interface card to decrypt my Satellite TV subscription and updating the channel information etc.

If anyone can help me to understand what to do with the new driver to enable the pad2keys functionality, I would be very very happy.

Many thanks in advance.

Bag123

---

### Post by bag123 on 2009-02-06
Bump.

Come one now everyone...  I know that I'm not the only one in the world with an Imon Pad - am I really the only one who's also using Mythbuntu?

Any help here would be very much appreciated.

Many thanks,

Bag123

---

### Post by fatmonk on 2009-02-06
Hi bag123,

You're certainly not the only one with this setup, and not the only one with problems with it either.

As you can see in my sig, I have the Antec Fusion case, which also came with the iMon PAD (RM200) remote.

I can't even get the IR receiver in the case to work under lirc control at the moment, so the pad2keys patch is only looming in the distance on my radar rigth now.

So I guess I can't be of much help, but consider this a bit of moral support. Though reading the fact that you've been trying to get your MythTV system set up for 'several years', it might be me that needs the moral support - I can't imagine spending that long getting something working, and certainly don;t fancy struggling with lirc for that long!

-FM

(For the record, the IR remote is the only thing I have left to get working on my machine, everything else was pretty easy going, especially with the support from people on these forums).

---

### Post by marcos1974 on 2009-02-21
hi bag123

did you get your imon to work?

I'm also owner of a iMon Pad with a VFD (case is Silverstone LC16m).
After 3 weeks of reading and trying things I managed to get the iMon (also the pad!!!) to work with mythtv.
If you need some help just post it here.
I will try to helpy ou step by step
It's not really simply...

regards,
Marcos

---

### Post by bag123 on 2009-02-25
Marcos1974,

Please let me know.  Still trying...  and not getting anywhere fast.

Any help you could give me would be very much appreciated.  I really don't think that it's going to be that hard - it just needs a bit of getting my head around it.

I've got the remote working (pretty much out of the box) - but the pad bit is really not going anywhere fast.

Your help would be very much appreciated.

Thanks in advance.

Bag123.

P.S.  You finding that the default setup in lirc is not giving you the commands that you want with the remote?  Do you have a modified lircrc file that you're using?  Or are you still using the default config files?

---

### Post by Kalibur on 2009-03-01
> **fatmonk said:**
> Hi bag123,

You're certainly not the only one with this setup, and not the only one with problems with it either.

As you can see in my sig, I have the Antec Fusion case, which also came with the iMon PAD (RM200) remote.

I can't even get the IR receiver in the case to work under lirc control at the moment, so the pad2keys patch is only looming in the distance on my radar rigth now.

So I guess I can't be of much help, but consider this a bit of moral support. Though reading the fact that you've been trying to get your MythTV system set up for 'several years', it might be me that needs the moral support - I can't imagine spending that long getting something working, and certainly don;t fancy struggling with lirc for that long!

-FM

(For the record, the IR remote is the only thing I have left to get working on my machine, everything else was pretty easy going, especially with the support from people on these forums).

Hi consider me a victim of IMON hardware I have an antec fusion remote case.  typing lsusb in terminal tell me that my imon hardware and model code is 15c9:0038 can you guys also include this information.  
Just type lsusb at terminal and paste the out put here including what parts of ur hardware you got to work if any.  Mine has an LCD screen, a volume knob and the RM200 none of which under linux.  The remote is plug and play under windows xp which tells me that it functions in a basic manner.

me@mymce$> lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 001 Device 003: ID 0609:0334 SMK Manufacturing, Inc. 
Bus 001 Device 002: ID 07b8:b02c D-Link Corp. BCM92045DG-Flash with trace filter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Only the line with SoundGraph inc is relavant my imon hardware ID is 15c9:0038 as u can see.  Some people have 15c9:ffdc and thats the version that seems to work with most how tos around.  00:38 is fairly new apperantly.

---

### Post by bag123 on 2009-03-04
OK, so my lsusb output looks like this:

```
@mythbox-lounge:~$ lsusb
Bus 004 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

So I guess that my iMON controller isn't the same as yours...


for FM - as far as I remember, my remote worked out of the box (once I'd chosen the correct remote during install of Mythbuntu).

Sorry I can't be more help.

Bag123

---

### Post by madman100 on 2009-03-16
Hi all i too have a case with a imon pad and vfd i too have the same problem when i upgraded to 8.10 the vfd display was not the problem it was getting the pad2key to work even enabling for my imon remote it still did not work only the basic functions too get the vfd display too work you will have to install lcdproc then open a terminal then type sudo gedit  /etc/LCDd.conf 
then change the part Driver=curses too Driver=imon 
then change the part Driver=curses too Driver=imon

then save your changes 
and then reboot the box and enable lcd in mythtv 
you can use any editor that you want i like gedit so i use that one 
as for enbling the pad2key the this open a terminal type sudo gedit /etc/modprobe.conf 

then type this in options lirc_imon pad2keys_active=1

then save changes 
 this did not work for me but might for you if the version of mythbuntu is 8.10 and has the patch all ready in it  by default then it should work i think that y it did not work in mine the imon remote in have is a thermaltake Medialab 

i hope this helps you all 
Thanks 
madman100

---

### Post by fax668 on 2009-08-06
I needed an additional step:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/19](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/19)

---

