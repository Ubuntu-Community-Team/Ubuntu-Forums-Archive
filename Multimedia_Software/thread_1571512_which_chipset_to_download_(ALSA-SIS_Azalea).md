---
title: "which chipset to download (ALSA-SIS Azalea)"
date: 2010-09-09
forum: Multimedia Software
---

### Post by hihihi100 on 2010-09-09
hi there

I have a SIS-Azalea soundcard
```
Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
    Subsystem: CLEVO/KAPOK Computer Device 0802
    Flags: bus master, medium devsel, latency 0, IRQ 4
    Memory at d3300000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```

as can be seen in the terminal, and in [http://www.alsa-project.org/main/index.php/Matrix:Vendor-SiS](http://www.alsa-project.org/main/index.php/Matrix:Vendor-SiS)
we can see a list of available chipsets.

I know I need to download one, which one? here i dont have any clue. Tips please

cheers

---

### Post by gordintoronto on 2010-09-09
My bet: none of the above. If this is a removable sound card, it probably needs to be selected in Preferences/Sound/Output. Or perhaps sound is muted somewhere. Azalea sound is well supported in Linux.

---

### Post by hihihi100 on 2010-09-10
> **gordintoronto said:**
> My bet: none of the above. If this is a removable sound card, it probably needs to be selected in Preferences/Sound/Output. Or perhaps sound is muted somewhere. Azalea sound is well supported in Linux.

sound is muted somewhere else... well, problems started when I was trying to make VMPK to work (virtual MIDI piano keyboard) so I proceeded to download the most recent ALSA package

if u need more information, let me know

---

### Post by Yellow Pasque on 2010-09-10
The correct driver for Azalia-based chipsets (snd-hda-intel) is already loaded. If you want to try the latest ALSA, use: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by hihihi100 on 2010-09-10
> **Temüjin said:**
> The correct driver for Azalia-based chipsets (snd-hda-intel) is already loaded. If you want to try the latest ALSA, use: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Some more information of what I did with the new inormation u provide:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0

so far:

```
hihihi100@hihihi100-laptop:~$ cd ~/Downloads
hihihi100@hihihi100-laptop:~/Downloads$ 3. tar xvf AlsaUpgrade-1.0.23-2.tar
3.: command not found
hihihi100@hihihi100-laptop:~/Downloads$ 3. tar xvf AlsaUpgrade-1.0.23-2.tar
3.: command not found
hihihi100@hihihi100-laptop:~/Downloads$ cd alsa-driver-1.0.23
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
hihihi100@hihihi100-laptop:~/Downloads/alsa-driver-1.0.23$ 

```what am i doin wrong?

also, take a look at [http://ubuntuforums.org/showthread.php?p=9829501#post9829501](http://ubuntuforums.org/showthread.php?p=9829501#post9829501)

thx

---

### Post by Yellow Pasque on 2010-09-10
It might work better if you don't copy and paste the step numbers (e.g. 3.)

---

### Post by hihihi100 on 2010-09-10
> **Temüjin said:**
> It might work better if you don't copy and paste the step numbers (e.g. 3.)

```
hihihi100@hihihi100-laptop:~/Downloads$ tar xvf AlsaUpgrade-1.0.23-2.tar
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
hihihi100@hihihi100-laptop:~/Downloads$ 

```

and yes, im totally lost: the instructions list on number 1 download the script and save it somewhere, what I have downloaded is alsa-driver-1.0.23 as tarball, then extracted. The folder name is not the same. Is that the script I have to download?

---

### Post by Yellow Pasque on 2010-09-10
NO, the script attached to the OP in the alsaupgrade thread is what you want. THat script will download/unpack all the alsa tarballs for you.

---

### Post by hihihi100 on 2010-09-10
> **Temüjin said:**
> NO, the script attached to the OP in the alsaupgrade thread is what you want. THat script will download/unpack all the alsa tarballs for you.

could u pls paste a link? r we talking about [alsa-driver-1.0.23]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2") tarball? Do I have to download every file from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) ?

---

### Post by Yellow Pasque on 2010-09-10
[http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001](http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001)

---

### Post by hihihi100 on 2010-09-10
> **Temüjin said:**
> [http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001](http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001)

well, many thanks:

```
**091010-19.20****Alsa-Upgrade-Script-1.0.23-2 *********************
*
* You'll be upgraded from Alsa  to 1.0.23
*
* Run -h option for further help and to look up the workflows
*
* Note1: Alsa won't be upgraded before you run the
*        installation option -i!! 
*        The upgrade procedure shouldn't have any effect on Alsa 
*        until then. However - see Note2
*
* Note2: Do not delete the Alsa Source Directory under /usr/src!
*        When starting the script the 2nd time with -d,
*        the Alsa source dir will be deleted automatically!
*        You won't have sound until you're done with that installation
* 
* DISCLAIMER: Use this script at your own risk. I do not take any 
*             responsibility for any problems caused by running 
*             this script. Before running this script I strongly 
*             advise you to make a backup of your system.
*             You might enter problems restoring the system to its
*             original status when running the restore function 
*             supplied by the script.  
*                            
*  
***************************************************************************


```

how do I make a backup?

---

