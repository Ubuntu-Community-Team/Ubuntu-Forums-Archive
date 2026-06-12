---
title: "Make /dev/video* Static"
date: 2008-04-12
forum: Mythbuntu
---

### Post by Freddie on 2008-04-12
I have a PVR-150 and a Nova-T. Both of those export something to /dev/video. However, I am only interested in the PVR-150. Problem is that this changes seemingly random at boot-up.

How can I fix this?

Regards, Freddie.

---

### Post by KillerKiwi on 2008-04-12
You need to create a udev rule, this will make a symlink that is always pointed to the correct device

You can use the attahed script to do it for you

syntax

sudo python udev-rules.py CURRENT_DEV SYMLINK

or

sudo python udev-rules.py /dev/video0 /dev/video_pvr150
sudo python udev-rules.py /dev/video1 /dev/video_novaT

---

### Post by Freddie on 2008-04-18
> **KillerKiwi said:**
> You need to create a udev rule, this will make a symlink that is always pointed to the correct device

You can use the attahed script to do it for you

syntax

sudo python udev-rules.py CURRENT_DEV SYMLINK

or

sudo python udev-rules.py /dev/video0 /dev/video_pvr150
sudo python udev-rules.py /dev/video1 /dev/video_novaT

Thank you! That worked an absolute treat.

Regards, Freddie.

---

### Post by mo-hog on 2009-03-26
KillerKiwi (great to see another Kiwi around!)

I just used your script and it was exactly what I needed to fix this:
[https://answers.launchpad.net/ubuntu/+question/65286/+index](https://answers.launchpad.net/ubuntu/+question/65286/+index)

This is an excellent little script for this task.  It would be great if you could clarify the license (add a GPLv3 header into the script, perhaps?) and post it somewhere that doesn't require a login to get to.  Perhaps you could add a short page to the Ubuntu wiki and add the file there.  I am happy to put it on my site if you have nowhere else.  It would mean that mailing lists and "Answers" can link directly to the script and not require people (like me) to get an ubuntuforums login to solve the udev problem.  At the moment, viewing ubuntuforums attachments requires a login.

Thanks again!!

---

### Post by KillerKiwi on 2009-04-12
consider it gpl2

hopefully the need for this will disappear soon...

---

### Post by kees on 2009-04-14
MythTV should be taught to use the static device names in /dev/v4l/by-path/* (which exist starting in Intrepid).  That's how static naming is being solved.

---

### Post by mo-hog on 2009-05-02
I agree - MythTV should be changed to support /dev/v4l/by-paths - I've filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-meta/+bug/370696](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-meta/+bug/370696)

The python script did not work in Jaunty because "udevinfo" is no longer supported.  I have updated the script to work with udevadm instead, which is the new way to access udevinfo.

I have also added a GPLv2 header to the file (though I don't know your name, so only put KillerKiwi!) and made it available through the launchpad bug above as well.  I hope you don't mind.

---

### Post by KillerKiwi on 2009-05-03
cool, thanks for updating the script will be handy when I update :)

---

### Post by Tim L on 2009-09-21
This looks exactly like what I need to solve my problem – I have downloaded the python script – but do not know what to do with it – where do I put it – how do I get it to work – at what stage do I install it? Can someone point be in the right direction. Sorry to ask such basic questions.

---

### Post by KillerKiwi on 2009-09-21
ok :)

When your system starts it assigns all video devices (webcams, capture cards etc) to a node like below
[LIST]
[*]/dev/video0
[*]/dev/video1
[*]/dev/video2
[*]etc
[/LIST]
The issue is video0, video1 and video2 may swap which device it points to on boot

Now the script can create a permanent node that ALWAYS points to the correct device.

So you run a line like below for your video devices (replace PVR150 with a name for the device)
```
sudo python udev-rules-jaunty.py /dev/video0 /dev/video_PVR150
```

You can then update myth backend to point to /dev/video_PVR150 (or what ever you called it) instead of /dev/video0

Problem solved

There is a fix to this coming, but until then...

---

### Post by Tim L on 2009-09-22
Great – I am in New Zealand and using PVR-150 and a Nova-S-Plus. Do I have to put the Pythan file udev-rules-jaunty.py in a specific folder?

---

### Post by Tim L on 2009-09-22
Great – I am in New Zealand and using PVR-150 and a Nova-S-Plus. Do I have to put the Pythan file udev-rules-jaunty.py in a specific folder

---

### Post by KillerKiwi on 2009-09-22
> **Tim L said:**
> Great – I am in New Zealand and using PVR-150 and a Nova-S-Plus. Do I have to put the Pythan file udev-rules-jaunty.py in a specific folder

No

---

### Post by Tim L on 2009-09-22
Thanks – I am in New Zealand using one PVR150 and one Nova-S-Plus. A couple of aditional question. How do I know if the PVR150 is on Video0 or Video1 or does it not matter? The name PVR150 is this the name given in mythtv setup?

---

### Post by grenloch101056 on 2009-09-25
just wanted to say thanks, I had to do a little tweaking, but this script is just what i needed to stop my PVRUSB2 and HVR1600 from swapping ID's.  Great job!

---

### Post by SiHa on 2009-11-10
I have a similar problem. I have Nova-S and Nova-T 500 cards:

/dev/dvb/adapter0/frontend0 - Nova-S
/dev/dvb/adapter1/frontend0 - Nova-T, Tuner 1
/dev/dvb/adapter2/frontend0 - Nova-T, Tuner 2

Adapters 0 & 1 like to swap at boot. This causes tuning errors, when Myth tries to tune to a DVB-T mux using the DVB-S card that has appeared on adapter1

I'm hoping I can use KillerKiwi's script (the Jauntily modified one) to create symlinks and UDEV rules to fix it. The only problem is, I'm not sure what devices to symlink and where to put the new link.

Each /dev/dvb/adapter*n* directory, besides having a frontend0, also have dvb0, demux0 & net0.

I'm thinking I should do this:
```
sudo python udev-rules-jaunty.py /dev/dvb0/adapter0/frontend0 /dev/dvb/adapter0/frontend_Nova_S
sudo python udev-rules-jaunty.py /dev/dvb0/adapter1/frontend0 /dev/dvb/adapter1/frontend_Nova_T_0
sudo python udev-rules-jaunty.py /dev/dvb0/adapter2/frontend0 /dev/dvb/adapter2/frontend_Nova_T_1
```
...but what about the dvb0, demux0 & net0? Can I ignore them?

Or should I be doing this:
```
sudo python udev-rules-jaunty.py /dev/dvb0/adapter0 /dev/dvb/adapter_Nova_S
etc...
``` To me this looks wrong, but I'm not terribly au-fait with the way Linux handles devices.
Any advice greatly appreciated - my wife was less than impressed last night when I temporarily reduced her to a single tuner (adapter2). For now, I've managed to get them to swap back on the 3rd or 4th reboot, so I'll just have to leave it powered until I can fix it.

Cheers,

Simon

---

### Post by Neon Dusk on 2009-11-10
> **SiHa said:**
> I have a similar problem. I have Nova-S and Nova-T 500 cards:

/dev/dvb/adapter0/frontend0 - Nova-S
/dev/dvb/adapter1/frontend0 - Nova-T, Tuner 1
/dev/dvb/adapter2/frontend0 - Nova-T, Tuner 2

Adapters 0 & 1 like to swap at boot. This causes tuning errors, when Myth tries to tune to a DVB-T mux using the DVB-S card that has appeared on adapter1

I'm hoping I can use KillerKiwi's script (the Jauntily modified one) to create symlinks and UDEV rules to fix it. The only problem is, I'm not sure what devices to symlink and where to put the new link.

Each /dev/dvb/adapter*n* directory, besides having a frontend0, also have dvb0, demux0 & net0.

I'm thinking I should do this:
```
sudo python udev-rules-jaunty.py /dev/dvb0/adapter0/frontend0 /dev/dvb/adapter0/frontend_Nova_S
sudo python udev-rules-jaunty.py /dev/dvb0/adapter1/frontend0 /dev/dvb/adapter1/frontend_Nova_T_0
sudo python udev-rules-jaunty.py /dev/dvb0/adapter2/frontend0 /dev/dvb/adapter2/frontend_Nova_T_1
```
...but what about the dvb0, demux0 & net0? Can I ignore them?

Or should I be doing this:
```
sudo python udev-rules-jaunty.py /dev/dvb0/adapter0 /dev/dvb/adapter_Nova_S
etc...
``` To me this looks wrong, but I'm not terribly au-fait with the way Linux handles devices.
Any advice greatly appreciated - my wife was less than impressed last night when I temporarily reduced her to a single tuner (adapter2). For now, I've managed to get them to swap back on the 3rd or 4th reboot, so I'll just have to leave it powered until I can fix it.

Cheers,

Simon

As you're using dvb cards it might be easier just to set the adapter_nr module option.

[thread=1311795]Force order of allocation of DVB frontends[/thread]

---

### Post by SiHa on 2009-11-10
](*,)
Funny, I remember reading that thread as well!

Thanks very much, sounds like a much simpler solution. (simpler = one I fully understand). I'll give it a go tonight.

---

### Post by MountainX on 2009-12-08
> **KillerKiwi said:**
> ok :)

When your system starts it assigns all video devices (webcams, capture cards etc) to a node like below
[LIST]
[*]/dev/video0
[*]/dev/video1
[*]/dev/video2
[*]etc
[/LIST]
The issue is video0, video1 and video2 may swap which device it points to on boot

Now the script can create a permanent node that ALWAYS points to the correct device.

So you run a line like below for your video devices (replace PVR150 with a name for the device)
```
sudo python udev-rules-jaunty.py /dev/video0 /dev/video_PVR150
```You can then update myth backend to point to /dev/video_PVR150 (or what ever you called it) instead of /dev/video0

Problem solved

There is a fix to this coming, but until then...

The script is not working for me (afaik) on Mythbuntu 9.10. Here's my output:

```
# python make-static-udev.py /dev/video1 /dev/video_PVR150
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:09.0/0000:01:04.0/video4linux/video1':
    KERNEL=="video1"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="ivtv0 encoder MPG"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:09.0/0000:01:04.0':
    KERNELS=="0000:01:04.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ivtv"
    ATTRS{vendor}=="0x4444"
    ATTRS{device}=="0x0016"
    ATTRS{subsystem_vendor}=="0x0070"
    ATTRS{subsystem_device}=="0x8801"
    ATTRS{class}=="0x040000"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00004444d00000016sv00000070sd00008801bc04sc00i00"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:09.0':
    KERNELS=="0000:00:09.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x005c"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

If you have 2 identical hardware devices you may want to add
the pci slot to the rule.
Do you want to include pci slot in rule ? (y/N) : y

creating new udev rule for video_PVR150

KERNEL=="video*", ATTR{name}=="ivtv0 encoder MPG", ATTRS{vendor}=="0x4444", KERNELS=="0000:01:04.*", SYMLINK+="video_PVR150"

Add this rule to /etc/udev/rules.d/60-symlinks.rules (y/N) : y
Restart udev now (y/N) : y

 REMEMBER 
 - Restarting udev does not remove old device links.
 - **If your new device node is not present your rule may need tweaking**
```Based on the last line above, I check and see that my new device node is indeed not present. I have run the script in various ways, but I can't seem to alter the outcome.

```
# ls /dev/vid*
/dev/video0  /dev/video1  /dev/video25  /dev/video33
  
```UPDATE: still not working. A reboot got me one step further:
  ```

# ls -la /dev/vid*
crw-rw----+ 1 root video 81, 0 2009-12-08 22:16 /dev/video0
crw-rw----+ 1 root video 81, 1 2009-12-08 22:16 /dev/video1
crw-rw----+ 1 root video 81, 4 2009-12-08 22:16 /dev/video25
crw-rw----+ 1 root video 81, 2 2009-12-08 22:16 /dev/video33
lrwxrwxrwx  1 root root      6 2009-12-08 22:16 /dev/video_PVR150 -> video1  
```But the myth backend setup does not give me an option for video_PVR150.

---

### Post by schwinn on 2009-12-10
^ If I'm reading correctly, the line KERNEL=="video1" is what identifies the /dev/video* location of the device.

However, I, too, am not getting this script to work on Mythbuntu 8.04... the 95-perso.rules are being created properly, but one device's symlink shows up (PVR150), while the other's does not (pcHDTV5500 analog)?

---

### Post by MountainX on 2009-12-10
> **schwinn said:**
> ^ If I'm reading correctly, the line KERNEL=="video1" is what identifies the /dev/video* location of the device.


Thank you! That's great to know and it does seem correct.

This started working for me. From the above post, my last problem was "But the myth backend setup does not give me an option for video_PVR150." I solved that by manually typing "video_PVR150" into the myth backend setup. Tested by rebooting, and it works :)

---

### Post by schwinn on 2009-12-10
Glad you got your end fixed... yes, you have to type in the symlink device name manually - it doesn't show up in the selector.

Unfortunately, this is not the problem I am facing... my pcHDTV hd5500 card simply doesn't show up as a symlink at all (for the analog stream - DVB stream is fine). Anyone have any ideas why?

Is there a log-file for the udev activities that I can look at, to see if there are any errors listed there? I didn't see anything in /var/log/messages

---

### Post by MountainX on 2009-12-10
> **schwinn said:**
>  Is there a log-file for the udev activities that I can look at, to see if there are any errors listed there? I didn't see anything in /var/log/messages

I'm not sure, but that was the general idea behind this thread:
[http://ubuntuforums.org/showthread.php?p=8466982#post8466982](http://ubuntuforums.org/showthread.php?p=8466982#post8466982)

See if anything there helps. dmidecode won't show log messages, but it might give you some clues...

---

### Post by KillerKiwi on 2009-12-10
This code is now hosted at
[https://launchpad.net/make-static-udev]("https://launchpad.net/make-static-udev")

with an updated script available here:
[http://bazaar.launchpad.net/~luna-tick/make-static-udev/trunk/annotate/head%3A/make-static-udev.py]("http://bazaar.launchpad.net/~luna-tick/make-static-udev/trunk/annotate/head%3A/make-static-udev.py")

---

### Post by schwinn on 2009-12-11
MountainX: It's not a matter of ID-ing the existing pcHDTV card - I know it's there, and I know it works. The question is why the udev rule isn't being applied. I imagine there is some log file (somewhere) that can tell me why it didn't create the symlink... that's what I'm looking for.

Bottom line is, the card is not showing up via the script by KillerKiwi. Of course, the other card is working under the script...

KillerKiwi: What changes have you put through with the new script? I don't think they'd make a difference, but I can give it a shot. The rule looks correct, so I don't see what the problem is... hence I'm looking for the logfile.

For the record, my card is showing up as follows under udevinfo:
```
  looking at device '/devices/pci0000:00/0000:00:0b.0/video4linux/video1':
    KERNEL=="video1"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:1"
    ATTR{name}=="cx88_0_ video _pcHDTV HD5500 HD"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0b.0':
    KERNELS=="0000:00:0b.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="cx8800"
    ATTRS{vendor}=="0x14f1"
    ATTRS{device}=="0x8800"
    ATTRS{subsystem_vendor}=="0x7063"
    ATTRS{subsystem_device}=="0x5500"
    ATTRS{class}=="0x040000"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v000014F1d00008800sv00007063sd00005500bc04sc00i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
And the udev rule from the script is (as written to 95-perso.rules):
```
# generated by udev.py script
KERNEL=="video*", ATTR{name}=="cx88_0_ video _pcHDTV HD5500 HD", ATTRS{vendor}=="0x14f1", SYMLINK+="video_hd55"
```

Yes, the video_hd55 isn't showing up in the /dev folder...

---

### Post by MountainX on 2009-12-11
Maybe something like this would help in your debugging:

```
# udevadm monitor --kernel
```**udevadm monitor [options]** 
Listens to the kernel uevents and events sent out by a udev rule and prints the devpath of the event to the console. It can be used to analyze the event timing, by comparing the timestamps of the kernel uevent and the udev event. 

**--environment**  Print the complete environment for all events. Can be used to compare the kernel supplied and the udev added environment values. [B]
--kernel[/B] Print the kernel uevents. [B]
--udev[/B] Print the udev event after the rule processing.

---

### Post by schwinn on 2009-12-12
Thanks for the tip, MountainX. I couldn't get the output from that command to help me much, even when I triggered a udev change-action (like the script does).

Turns out, I think the underscores were probably the reason the match wasn't happening. As posted above, the original rule wouldn't match... but I added a wildcard to the name and changed it to:
```
KERNEL=="video*", ATTR{name}=="*pcHDTV HD5500 HD", ATTRS{vendor}=="0x14f1", SYMLINK+="video_hd55"
```... and now it's working, and my symlink is in!

Thanks for your help, MountainX!

And, thanks to KillerKiwi for the excellent script! You may consider putting in a note saying that if the symlink doesn't work, that the user may consider manually editing the rules and using wildcards to truncate the match-string and seeing if that helps. Again, I'm guessing the underscores were pissing it off... or maybe there were some special characters in there? That's a pretty messy name-string.

---

### Post by MountainX on 2009-12-12
> **schwinn said:**
> 
And, thanks to KillerKiwi for the excellent script! You may consider putting in a note saying that if the symlink doesn't work, that the user may consider manually editing the rules and using wildcards to truncate the match-string and seeing if that helps. Again, I'm guessing the underscores were pissing it off... or maybe there were some special characters in there? That's a pretty messy name-string.

Congrats on getting it working! That's valuable feedback. Thanks for sharing the steps that brought you success. I'll keep that in mind for my next video card (which is sitting on the table awaiting installation!)

---

