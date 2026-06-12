---
title: "hauppauge pvr 150 is not recognized"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by wesmsl on 2007-03-07
Lets see I installed a ubuntu 6.10 on my machine I am trying to turn into a mythtv box.  I have a hauppauge pvr 150.  I used this guide [https://help.ubuntu.com/community/Install_IVTV_Edgy]("https://help.ubuntu.com/community/Install_IVTV_Edgy") and got all the way to the Check IVTV is initialized part.  I ran "dmesg |grep Initialized" and it returned 

[17179606.752000] [drm] Initialized drm 1.0.1 20051102
[17179606.768000] [drm] Initialized radeon 1.25.0 20060524 on minor 0

I don't think the card is recognized.  I am trying to use ivtv, lirc, mythtv all together and the process is a pain but I know it will be worth it in the end.  If anyone could help that would be very much appreciated.

---

### Post by rsambuca on 2007-03-07
Did you try to do a test capture?

---

### Post by wesmsl on 2007-03-07
Yes, that didn't work either.  I'm really stumped on this one.

---

### Post by rsambuca on 2007-03-07
Are you sure you prepared the module-assistant and then inserted the ivtv driver?

---

### Post by wesmsl on 2007-03-07
I typed in the commands, I'm not sure if they worked or not.

---

### Post by wesmsl on 2007-03-07
Should I install the ivtv drivers first then mythtv and then lirc?  Or mythtv then ivtv?  I am going to fresh install using this guide.  

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

hopefully i'll have better luck

---

### Post by rsambuca on 2007-03-07
>  Install the firmware

    *

      If you are in a gnome based environment (for example a desktop install of Ubuntu)
          o

            DEBIAN_FRONTEND=gnome sudo apt-get install ivtv-firmware

      or

      If you are in a text based environment (for example a fresh command line system install)
          o

            DEBIAN_FRONTEND=dialog sudo apt-get install ivtv-firmware

Do you remember which of these commands you used to set-up the firmware?

Also, you definitely want to get the ivtv working first, before setting up MythTV.

Probably better to get this figured out first.  I am not sure what the problem could be.  I have set this up a few times for myself and others, and it always worked first time using the instructions on that same webpage.  Are you using Edgy?  Ubuntu or Kubuntu?

---

### Post by wesmsl on 2007-03-07
I am using ubuntu 6.10 edgy eft.  I'm not sure I got the firmware squared away.  That might be the problem.  I don't remember typing those commands.

---

### Post by rsambuca on 2007-03-07
Just start at the top of the Installation instructions again from the webpage in your first post.  If you do each step you shouldn't have a problem.

---

### Post by wesmsl on 2007-03-07
oh wait i did the second one you posted.  that might be the problem because i am in a gnome environment not the text based one.

---

### Post by wesmsl on 2007-03-07
Well I retried the guide from a fresh install and it didn't work.  The card did not show up and the test capture wouldn't work either.  I'm not sure what I'm doing wrong.  I'm not getting any error messages.  Have any ideas?

---

### Post by rsambuca on 2007-03-08
Are you sure you have the card seated properly into the PCI slot?

Could you post the output of the "lspci" command please?

---

### Post by wesmsl on 2007-03-08
It says command not found.  I am pretty sure it is in the pci slot correctly.  It shows up in the device manager.

---

### Post by rsambuca on 2007-03-08
```
lspci
```

---

### Post by wesmsl on 2007-03-08
I'm pretty sure its the one in bold.
it outputs:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**01:08.0 Multimedia video controller: Conexant Unknown device 5b7a**
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

---

### Post by rsambuca on 2007-03-08
Your tuner card is not being detected for some reason.

What does this command give you```
find /lib/modules/`uname -r`/ -name ivtv.ko
``` (just copy and paste it into a terminal)

---

### Post by wesmsl on 2007-03-08
It outputs:

/lib/modules/2.6.17-11-generic/ivtv/ivtv.ko

---

### Post by rsambuca on 2007-03-08
Have you tried a cold boot?  (Shutting down for at least 30 seconds to allow the registers to clear)

---

### Post by wesmsl on 2007-03-08
And unplug the power cable?  I turned the computer off last night.  But I didn't unplug the power.  I'll try that now.

---

### Post by rsambuca on 2007-03-08
No, you shouldn't have to unplug.  Hmmm, sorry, I can't think of much else.  You might try checking out the [[COLOR="Red"]IVTV.org troubleshooting page[/COLOR]]("http://ivtvdriver.org/index.php/Troubleshooting").

Let me know how it goes.

---

### Post by wesmsl on 2007-03-08
I haven't installed the motherboard drivers yet.  I just built the PC.  I'll try installing some drivers from the CD if I can.

---

### Post by wesmsl on 2007-03-08
Damn, the CD is made for windows.  Only dll's and exe's.  I'll look on the ivtv troubleshooting page.

---

### Post by wesmsl on 2007-03-08
I don't see anything on that page, I remember looking there before.  There was nothing relevant to the problem I am having.

---

### Post by barney_1 on 2007-03-08
Make certain you have the most up-to-date bios for your motherboard.  Also, try moving the card to a different PCI slot and see if lspci will recognize the card as a 150.

---

### Post by wesmsl on 2007-03-08
I have moved the card that didn't work.  How do you set up the latest BIOS?

---

### Post by wesmsl on 2007-03-08
It still outputs:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**01:09.0 Multimedia video controller: Conexant Unknown device 5b7a**
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

I have no idea what to do.

---

