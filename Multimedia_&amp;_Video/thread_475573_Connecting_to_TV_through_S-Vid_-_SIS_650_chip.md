---
title: "Connecting to TV through S-Vid - SIS 650 chip"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by jingba on 2007-06-16
**[COLOR="Red"]I've resolved these issues on my own.  There is really no need to read this thread.[/COLOR]**

Hi,
I am extremely new to Ubuntu.  So new, in fact, that I am basically doing things based from the forums.  You could say I am 3-days new.

I have installed it on an old Desknote (ECS).  I've managed to get most things running (not the D-Link DWL-G122 B1 network adapter, though), but I cannot get the S-Video out to work.

The system is using the Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter.  I used lspci to pull up the specs, and here they are.

-------------------------------------------------------------------------------------------------------------------------
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 47)
00:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
-------------------------------------------------------------------------------------------------------------------------

I read where someone got the SIS console to work by following the steps from this site: [http://www.winischhofer.eu/linuxsispart4.shtml#download]("http://www.winischhofer.eu/linuxsispart4.shtml#download")

I went there and followed the directions for the "easy" install in step 5.  Last night, the terminal reported that the src directory could not be found.  I tried it again this morning so I could copy the error, but I got "E: Not Installed" instead.  Now, what does this mean?

I downloaded the src pack from step 4 from the site, but don't know how to install the pack through the terminal.  Basically, I am at a road block.

Is there any other way to get the system to display to a TV using the S-video port without the console?  If so, how?  If not, any ideas on what I might be doing wrong with the site I mentioned?  As I said, I am pretty sure I followed all the steps as listed.  I appended my sources.list.  I added the gpg key.  I typed in the command he gave.  Nothing worked.  I even tried to use dpkg to install from the install-sh file from the src pack I downloaded, but I get a message saying that I have to have superuser privileges.  What is that?  Do I need it?  Can I get it?  If so, how?

Anyway, thanks for the patience and input.  Like I said, I am brand-spanking new to Ubuntu (newest version from their site), so I might need things broken down into "idiot-ese" for me.

---

### Post by jingba on 2007-06-16
Well, I tried something else...  I went back to the site with the sisctrl file (listed in first post), and downloaded the .deb file he has there.

I went to the terminal and typed:
```
sudo dpkg -i sisctrl_0.0.20051202-1_i386.deb
```

The terminal did whatever it does and diplayed the message basically stating that the sisctrl panel was installed.  I checked the Synaptic package manager, and it is listed.  The sisctrl is listed in /usr/bin.  Just to see what would happen, I double-click on it.  An message window popped up with the following:

----------------------------------------------------
[I]SiSctrl interface disabled.

To enable he SiSCtrl interface, place
   Option "EnableSiSCtrl" "yes"
in the "Device" section of your config file.[/I]
-----------------------------------------------------

So, where do I go and  how do I do this?

Thanks

---

### Post by jingba on 2007-06-16
Okay, so I seem to be answering my own questions.  I edited the xorg.conf file.  The sisctrl is now working.  :D

But!  It won't display to the TV.  I assume that I need to further modify the xorg.conf file but don't know what needs to be put in there.  I've seen people adding a TV display option for nVidia--based systems, so I assume I need to do the same.

So, any suggestions?

Thanks

---

### Post by junglizste on 2007-06-23
i'm having a problem with the sis 650 too.

i finally got the sisctrl package installed.

then i got the error message that i need to add that line into my xorg.conf file.

i put it in the device sis section then the next time i booted it was all weird ascii unintelligible crap and i had to reinstall...

i wasn't so concerned about TV output as i was operating at 1280x1024... i can't select higher than 1024x768.

---

