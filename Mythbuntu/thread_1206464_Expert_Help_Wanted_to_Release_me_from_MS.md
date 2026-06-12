---
title: "Expert Help Wanted to Release me from MS"
date: 2009-07-07
forum: Mythbuntu
---

### Post by read_ca on 2009-07-07
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have been using MS MCE and VMC for the last 4 years and always been OK with it, not happy, but OK.  I have been watching the development of 'nix' based MC's (mainly LinuxMCE) for a few years but never had the same success as I have had with MS.  However, recently a colleague who is a staunch Unbuntu fan pointed me towards Mythbuntu and challenged me to give it a go again.  I must say, this time I was quite impressed, the majority of the installation went smoothly.  But again, there is always the ‘however’, I can quite get all of it to work…  It starts up and I managed to get some bits done after a whole day of fiddling but I cannot get TV to work.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have a raft of hardware (5 MC PC’s); all AMD based 680 and 780 chipsets, and most with ATI graphics (HD3200, HD3850 and HD4670).  DVB-T cards Hauppauge WinTV Nova-T 150 (90002) and 500, Pinnalce TwinT.  DVB-C TT C-1501 + CI (never got this to work in VMC).  MS Home Server to store content.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Is there anyone out there who is willing to provide some support for a Linux novice (my background is in VAX/VMS and MS Windows) and get everything working? [/FONT][/COLOR][COLOR=black][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks in advance![/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by AndyCee on 2009-07-07
A lot of people here are willing to help.

Do you have a specific question - is it just TV you can't get to work? Or would you like someone to provide expert one-on-one support via email? Most of the help received or given in these forums is "drive-by". I can point you to the Multimedia & Video section of the forums or [this guide]("http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/").

I'm personally not an expert, but to get some better feedback, type the following into a terminal and post the output here:

```
sudo lspci
```

and

```
sudo lshw -short
```

That should give someone a place to start.

---

### Post by read_ca on 2009-07-07
[FONT=Times New Roman][SIZE=3]Thanks for the tip.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The system I tried to setup is as follows:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Gigabyte M/B GA-M68SM-S2 using onboard graphics.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://www.giga-byte.co.uk/Support/Motherboard/Driver_Model.aspx?ProductID=2640[/SIZE][/FONT]]("http://www.giga-byte.co.uk/Support/Motherboard/Driver_Model.aspx?ProductID=2640")
[FONT=Times New Roman][SIZE=3]AMD X2 2.6 Ghz[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2 GB RAM[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]500 GB HDD[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Nova-T 150[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]TT C-1501 + CI[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I am in the UK. The main installation for 9.04 (64 bit) went OK and I went through the setup wizard to configure everything. Afterwards I got a message about not being able to connect to the backend database.  I spoke to my colleague (who has never user Mythbuntu before) who tried to help me and we managed to…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Run the Update Manager which worked fine and suggested I use the NVIDIA proprietary drives, which we did.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We got a message about running “mythfilldatabase –manual”.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We tried to configure the TV cards again and after trial and error I set them up as DVB 0 (TT C1501) and DVB 1 (Nova-T 150).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We tried to configure Video Sources and after trial and error set it to XMLTV provider to ‘tv_grab_uk_rt’ which hung at 50% then after a few PC resets discovered accidentally by alt+tab that a terminal window was running in the background – we followed the prompts which seemed to work.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We ran mythfilldatabase –manual which seemed to work.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We found the DVB utils and ran ‘scan’ manually which detected the DVB-T channels OK.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]We went through the setup again and ran a channel scan in the main UI which detected the DVB-T channels.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]…but still no live TV.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]My feeling is that if I could overcome my lack of knowledge I would happily convert my 5 MC’s to Mythbuntu and blow raspberries at MS (I am not looking forward the license to upgrade to Windows 7.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks in advance.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]vmc@MCPC05:~$ sudo lspci[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:09.0 SATA controller: nVidia Corporation MCP67 AHCI Controller (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:12.0 VGA compatible controller: nVidia Corporation GeForce 7025 (rev a2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]01:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]vmc@MCPC05:~$[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]vmc@MCPC05:~$ sudo lshw -short[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]H/W path        Device     Class       Description[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]==================================================[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]                           system      M68SM-S2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0                         bus         M68SM-S2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/0                       memory      128KiB BIOS[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/3                       processor   AMD Athlon(tm) 64 X2 Dual Core Processor [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/3/a                     memory      128KiB L1 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/3/c                     memory      1MiB L2 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/b                       memory      128KiB L1 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/d                       memory      L2 cache[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1a                      memory      2GiB System Memory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1a/0                    memory      1GiB DIMM 400 MHz (2.5 ns)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1a/1                    memory      1GiB DIMM 400 MHz (2.5 ns)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1a/2                    memory      DIMM 400 MHz (2.5 ns) [empty][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1a/3                    memory      DIMM 400 MHz (2.5 ns) [empty][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/4                       memory      RAM memory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1                       bridge      MCP67 ISA Bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1.1                     bus         MCP67 SMBus[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/1.2                     memory      RAM memory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/2                       bus         MCP67 OHCI USB 1.1 Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/2.1                     bus         MCP67 EHCI USB 2.0 Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/5                       bus         MCP67 OHCI USB 1.1 Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/4.1                     bus         MCP67 EHCI USB 2.0 Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/6                       storage     MCP67 IDE Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/7                       multimedia  MCP67 High Definition Audio[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8                       bridge      MCP67 PCI Bridge[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8/6                     multimedia  CX23880/1/2/3 PCI Video and Audio Decoder[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8/6.2                   multimedia  CX23880/1/2/3 PCI Video and Audio Decoder[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8/6.4                   multimedia  CX23880/1/2/3 PCI Video and Audio Decoder[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8/7                     multimedia  SAA7146[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/8/e                     bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9            scsi0      storage     MCP67 AHCI Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9/0.0.0      /dev/sda   disk        500GB ST3500630AS[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9/0.0.0/1    /dev/sda1  volume      11GiB EXT3 volume[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9/0.0.0/2    /dev/sda2  volume      454GiB Extended partition[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9/0.0.0/2/5  /dev/sda5  volume      972MiB Linux swap / Solaris partition[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/9/0.0.0/2/6  /dev/sda6  volume      453GiB Linux filesystem partition[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/a            eth0       network     MCP67 Ethernet[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/12                      display     GeForce 7025[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/100                     bridge      K8 [Athlon64/Opteron] HyperTransport Tech[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/101                     bridge      K8 [Athlon64/Opteron] Address Map[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/102                     bridge      K8 [Athlon64/Opteron] DRAM Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/0/103                     bridge      K8 [Athlon64/Opteron] Miscellaneous Contr[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]/1              pan0       network     Ethernet interface[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]vmc@MCPC05:~$[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by ahood on 2009-07-07
Because MythTV records whatever is watched in livetv, the system must have write privileges to the storage directory defined in the Storage Groups of the backend configuration.

What directories/path(s) were entered for the Storage Groups setting in the backend configuration?

What are the permissions of the storage directories?
Enter the following in a terminal
> ls -l /path/storagedirectoryname
Note: Use a lowercase L after the dash in above command. Replace /path/storagedirectoryname with the path and name of the storage directory defined in the backend configuration.

Can you successfully record a show using the program schedule (i.e., not livetv)?

Other Resources
[**[COLOR="DarkOrange"]9.04 and PVR-350 woes - please help[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1172047)

[**[COLOR="darkorange"]mythtv - no tv in frontend[/COLOR]**](http://ubuntuforums.org/showthread.php?t=928984)

Hope this helps

Al

---

### Post by read_ca on 2009-07-07
Thanks for your help.
 
I've been poking around for 2.5 hours... there were no storage location defined for Live TV and DB Backup so I pointed them at .../recordings/ ad it still doesn't work.  I have checked and put the vmc user is in the main group 'mythtv'.  No joy.
 
What should the TV Capture Cards be configured as?  DVB DTV?
 
At this point I have spent almost 2 whole days on this and feeling down.  The problem is I have no real idea what I am doing.  This is where MS, with all its faults, gets it right.  I get a VMC up and running in half a day including all updates.  Even in the beginning with MCE all I had to do was download and install the MCE driver for the Nova-T 150 and then it all worked.

---

### Post by ahood on 2009-07-07
> **read_ca said:**
> Thanks for your help.
 
I've been poking around for 2.5 hours... there were no storage location defined for Live TV and DB Backup so I pointed them at .../recordings/ ad it still doesn't work.  I have checked and put the vmc user is in the main group 'mythtv'.  No joy.
 
What should the TV Capture Cards be configured as?  DVB DTV?
 
At this point I have spent almost 2 whole days on this and feeling down.  The problem is I have no real idea what I am doing.  This is where MS, with all its faults, gets it right.  I get a VMC up and running in half a day including all updates.  Even in the beginning with MCE all I had to do was download and install the MCE driver for the Nova-T 150 and then it all worked.

Hi read_ca

I hear your frustration and I can certainly relate to your experience when I first started with MythTV five years ago.

I hope you don't mind me saying, but the best thing you can do to relieve your frustration is to change your goals. Although it is understandable to have the goal of getting a MythTV system up and running in a few hours, which is very achievable by experienced users; however, this isn't going to be the case for someone new to Linux. I recommend that you re-set the goal of when to accomplish this task. I cannot say for certain when will be best. I can encourage you to have fun learning something new and rising to the challenges presented.

There are many users at this forum that will help, including myself. Sharing information is fun, and we all learn from each others experiences.

Okay, now to the problem.

> ...there were no storage location defined for Live TV and DB Backup so I pointed them at .../recordings/ ad it still doesn't work.

Based on the above, it certainly seems plausible that the defined storage location can, and may still be, the reason livetv isn't working. I say this because "no storage location defined" certainly will cause livetv not to work.

The ".../recordings/" also seems like a strange entry. The storage location should begin with a slash (/) followed by names of folders representing a location in the file system that meets the following criteria:

(a) Lots of space
(b) Owner is 'mythtv'
(c) Group is 'mythtv'
(d) Owner and Group permissions are set to read and write

To obtain the full path to the recordings directory, it is possible to find files and folders with the name 'recordings'.

> sudo find / -name recordings

The output should list folders and file names that contains the word 'recordings'.

> I have checked and put the vmc user is in the main group 'mythtv'.
Yes, this is correct, but may not have fully solved the problem. If the storage directory does not belong to the 'mythtv' group, then setting the user 'vmc' to be part of the mythtv group won't have much effect. Thus, the goal is to determine the owner, group, and permissions of the storage directory.

If one of the output entries from the find command looks right, then make sure it has the correct permissions by doing the following.

> ls -l /path/recordings
*Note: Replace /path/recordings with actual full path to the recordings directory*.

Try the above and report what you get back.

Al

---

### Post by roundhay on 2009-07-07
Try looking at this to set up a UK Freeview system.

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

There are also lots of useful links at the end.

---

### Post by azmyth on 2009-07-07
The best thing to do is to look at the myth log files. They're very good at pointing you in the right direction. You can navigate to /var/log/mythtv or you can get them from a menu in mythbuntu. I prefer to kill the backend and frontend and then starting both from a terminal to see the logs in the screen.

---

### Post by read_ca on 2009-07-08
Thanks for your responses!
 
I should have been more specific.  The storage location in the Default group was /var/lib/mythtv/recordings so I used this to define the locations for LiveTV and DB Backup.
 
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] ls -l /var/lib/mythtv/recordings
total 0
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] ls -l /var/lib/mythtv/
total 0
drwxrwsr-x 2 mythtv mythtv 6 2009-04-10 07:20 music
drwxrwxr-x 2 mythtv mythtv 6 2009-04-10 07:20 pictures
drwxr-xr-x 2 mythtv mythtv 6 2009-04-10 07:20 posters
drwxrwsr-x 2 mythtv mythtv 6 2009-07-08 09:30 recordings
drwxrwxr-x 2 mythtv mythtv 6 2009-04-10 07:20 videos

This is what I get from the log file:
 
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] tail -f /var/log/mythtv/mythbackend.log
2009-07-08 09:36:52.981 ChannelBase(4): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-07-08 09:36:52.982 ChannelBase(4) Error: Setting start channel 'Please add' failed, 
   and we failed to find any suitible channels on any input.
2009-07-08 09:36:52.982 TVRec(4): HW Tuner: 4->4
2009-07-08 09:36:53.095 DVBChan(4:0) Error: SetChannelByString(Please add): CheckChannel failed.
   Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-07-08 09:36:53.096 TVRec(4) Error: Failed to set channel to Please add. Reverting to kState_None
2009-07-08 09:36:53.097 TVRec(4): Changing from WatchingLiveTV to None
2009-07-08 09:37:59.500 Reschedule requested for id -1.

I have check in the Channel Editor and rescanned the channels which are found OK, but where do I set the starting channel?

---

### Post by ahood on 2009-07-08
> **read_ca said:**
> Thanks for your responses!
 
I should have been more specific.  The storage location in the Default group was /var/lib/mythtv/recordings so I used this to define the locations for LiveTV and DB Backup.
 
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] ls -l /var/lib/mythtv/recordings
total 0
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] ls -l /var/lib/mythtv/
total 0
drwxrwsr-x 2 mythtv mythtv 6 2009-04-10 07:20 music
drwxrwxr-x 2 mythtv mythtv 6 2009-04-10 07:20 pictures
drwxr-xr-x 2 mythtv mythtv 6 2009-04-10 07:20 posters
drwxrwsr-x 2 mythtv mythtv 6 2009-07-08 09:30 recordings
drwxrwxr-x 2 mythtv mythtv 6 2009-04-10 07:20 videos

This is what I get from the log file:
 
[EMAIL="vmc@MCPC05:~$"]vmc@MCPC05:~$[/EMAIL] tail -f /var/log/mythtv/mythbackend.log
2009-07-08 09:36:52.981 ChannelBase(4): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-07-08 09:36:52.982 ChannelBase(4) Error: Setting start channel 'Please add' failed, 
   and we failed to find any suitible channels on any input.
2009-07-08 09:36:52.982 TVRec(4): HW Tuner: 4->4
2009-07-08 09:36:53.095 DVBChan(4:0) Error: SetChannelByString(Please add): CheckChannel failed.
   Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-07-08 09:36:53.096 TVRec(4) Error: Failed to set channel to Please add. Reverting to kState_None
2009-07-08 09:36:53.097 TVRec(4): Changing from WatchingLiveTV to None
2009-07-08 09:37:59.500 Reschedule requested for id -1.

I have check in the Channel Editor and rescanned the channels which are found OK, but where do I set the starting channel?

The starting channel is set in the "Input Connections" of the backend. Do the following...

1. Start mythtvbackend
2. Scroll down to Input Connections and 'Enter' on the keyboard

On the left side, you should see a list of devices (/dev/video0, /dev/video1, etc.) and on the right side the available inputs (tuner, Svideo, composite, etc.).

Initially, "None" will be set for all available inputs and needs to be changed to the appropriate video source.

Thus, scroll down to the appropriate video device and video input and press the Enter key on the keyboard. *Note: This step is not obvious and is easily missed.*

Next will be a screen of options where you select the video source and other settings. The last item on the screen will be 'Starting Channel' and may initially be set to 'Please select a starting channel' or something similar.

I hope the above helps.

Al

---

### Post by read_ca on 2009-07-08
Thanks for the pointers.
 
I started again deleted all the capture cards, video sources and inputs.  I set both capture cards then defined only one video source for the Nova-T 150, this time using atl+tab to switch to the terminal window hidden in the backgroud, then ran mythfilldatabase --manual accepting all the defaults, defined the Channel Input but Channel Scan would not work.  I esc'ped all the way out to the frontend then when to backend setup again, this time the Channel Scan worked and picked up the channels the same as before... and Watch TV worked!!
 
I tried to define a Video Source for the TT C-1501 I did not scan channels because I don't have a cable input in the office and Watch TV stopped working.  I remmoved the Video Source for the TT card and Watch TV worked again.
 
Now for the next challenge, to get the TT card working.  I have a cable card + CI, Diablo CAM and a full Virgin Media subscription.  Can anyone give me some pointers on how to get this working?  (The idea being that I can use the VM card and use the PC to record and stream cable instead of buying a V+ box and pay for multiple extensions.)
 
After this the task is to replace the Windows Home Server...

---

### Post by ahood on 2009-07-08
> **read_ca said:**
> Thanks for the pointers.
 
I started again deleted all the capture cards, video sources and inputs.  I set both capture cards then defined only one video source for the Nova-T 150, this time using atl+tab to switch to the terminal window hidden in the backgroud, then ran mythfilldatabase --manual accepting all the defaults, defined the Channel Input but Channel Scan would not work.  I esc'ped all the way out to the frontend then when to backend setup again, this time the Channel Scan worked and picked up the channels the same as before... and Watch TV worked!!
 
I tried to define a Video Source for the TT C-1501 I did not scan channels because I don't have a cable input in the office and Watch TV stopped working.  I remmoved the Video Source for the TT card and Watch TV worked again.
 
Now for the next challenge, to get the TT card working.  I have a cable card + CI, Diablo CAM and a full Virgin Media subscription.  Can anyone give me some pointers on how to get this working?  (The idea being that I can use the VM card and use the PC to record and stream cable instead of buying a V+ box and pay for multiple extensions.)
 
After this the task is to replace the Windows Home Server...

Unfortunately, I have not worked with that hardware (CI, Diablo CAM) or subscription (Virgin Media).

I recommend searching this forum, google(?) and posting a new thread for addressing the latest challenge.

Also see this post.

[**[COLOR="DarkOrange"]Technotrend C-1501 with MythBuntu[/COLOR]**](http://ubuntuforums.org/showthread.php?t=819903)

I will chime in when I can.

Al

---

