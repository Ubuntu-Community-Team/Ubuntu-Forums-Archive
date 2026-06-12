---
title: "Configuring my winmodem"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by CoercibleGerm on 2006-05-10
I've been trying to get my winmodem working under Ubuntu for a little while now, and I'm consistently running into dead-ends. Before I give up and spend money on an external hardware modem, I was hoping someone would be willing to take a peek at my ModemData.txt file and offer their input on what should be done, as I may be misreading or misinterpreting what the file tells me to do. The  file reads as follows:

> DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_April_26
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Reading /proc/asound/pcm 
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1
00-01: ALI 5451 modem : ALI 5451 modem : playback 1 : capture 1

The modem is supported by an ALSA modem driver plus slmodemd, OR alternatively
an hsfmodem package from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers). Further diagnostics
below may resolve between the two.
ALSA modem drivers are included in 2.6.n kernel packages and currently include:
	snd-hda-intel, a joint audio + modem driver
	snd-ali5451  ,        "             "
	intel8x0m        , depending on intel8x0    audio driver
	snd_via82xx_modem,          "   snd_via82xx   "
	snd-atiixp-modem ,          "   snd-atiixp    "
Driver loading itself does NOT resolve between ALSA and hsfmodem alternatives. 

 The potentially supporting drivers now loaded on this System are:
0 snd_ali5451


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) 
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:06.0
0000:00:08.0
    
Providing detail for device at  0000:00:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0401: 10b9:5451   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
  SubSystem 103c:0024  Hewlett-Packard Company: Unknown device 0024
	Flags: bus master, medium devsel, latency 64, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  ALI 5451
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5451 103c:0024 debian_version 2.6.12-9-386  3.4.5 none    i686
The audio card 10b9:5451 may carry a soft modem chip.
-------------------------------
The modem should be setup by:
     sudo slmodemd --alsa -c YOUR_COUNTRY 
Get the SLMODEMD.gcc3 from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
and follow guidance therein.
	The soft modem in the 8086:2668 High Definition Audio has low level support by 
the snd-hda-intel driver, beginning with the 2.6.14 kernels.  
        The Conexant soft modem chipset is not supported by snd-hda-intel and
[http://www.Linuxant.com](http://www.Linuxant.com) is developing support for these modems.

 For snd-ali5451.ko compiling instructions, see [http://phep2.technion.ac.il/linmodems/archive/msg04955.html](http://phep2.technion.ac.il/linmodems/archive/msg04955.html).
Modem support within the snd-ali5451 driver is included in some 2.6.12 and later kernels
The following two Root commands should set up the modem.
	sudo modprobe snd-ali5451
	sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
Get the SLMODEMD.gcc3.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
       
 The controller: 10b9:5451  ALI 5451 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	AgereSystems
	Conexant
	Smartlink

 Archive records show that 103c:???? Subsystems from HP with the exception of  103c:006b and 103c:3081
 have a Conexant chip.  Thus first test hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers)
 Should that support fail, the alternate route is described in Modem/Slmodem-ALSA.txt
 
Checking for autoloaded ALSA modem drivers
snd_ali5451            22596  2 
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm                78344  4 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    48644  9 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

  Driver snd-ali5451  may enable codec acquisition 
  === Begin mc97 codec query  ===
	   
 Files under /proc/asound/ do not include  modem codec information. 
 If more decisive information is not given below,
 this is a tentative signature of a Conexant hsfmodem.  Download a hsfmodem package from
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) or your installation CDs.  For SuSE/Novell, install both
 km_hsfmodem and hsfmodem packages,  for drivers and configuration tools respectively.
 
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 
 AgereSoftModem drivers only support AC97 or MC97 modem controllers with codecs charcterized by one of:
   SIL_id = 39 
   mc97 codec is SIL27 
   0x27 , as output by modem diagnostics under Microsoft Windows
 If uncertain, identity the softmodem codec through tests described in Modem/SoftModem.txt
 Support is currently ONLY for 2.4.n kernels and the following modem controllers:
   8086:(2416 2426 2446 7196 2486 24C6)  , with 8086 == Intel
   1039:7013  SIS
   1106:3068  VIA
 Access the soft modem software through code sponsor IBM at:
   [http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698](http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698)
 The SmartLink slmodem-2.9.9 may serve for modems not served by this AgereSystems software.
 
 If may be necessary to add -DMODVERSIONS to the compile flags, 
 depending on whether your kernel was thus compiled. See
 [http://linmodems.technion.ac.il/archive-fourth/msg01408.html](http://linmodems.technion.ac.il/archive-fourth/msg01408.html)


 Under the controller 10b9:5451  ALI 5451 ,
 with modem subSystem 103c:0024     
 Alternative supporting packages are the SmartLink slmodem-2.9.n using its proprietary slamr driver, 
 or dependent on  10b9:5451  ALI 5451 , an  Open Source driver from the  ALSA package.
 See Modem/Slmodem-ALSA.txt for details.
 A sample compilation is shown in: [http://linmodems.technion.ac.il/archive-fifth/msg02567.html](http://linmodems.technion.ac.il/archive-fifth/msg02567.html)
  
 For SuSE 9.2 users, there is an update  for driver slamr.ko loading during bootup. 
 To find it easily, search for "slamr" within  [http://www.novell.com/linux/download/updates/92_i386.html](http://www.novell.com/linux/download/updates/92_i386.html)
     

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 

    
Providing detail for device at  0000:00:08.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:5457   Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
  SubSystem 103c:0024  Hewlett-Packard Company: Unknown device 0024
	Flags: medium devsel, IRQ 3
 Checking for IRQ 3 sharing with modem.
      XT-PIC  serial

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5457 103c:0024 debian_version 2.6.12-9-386  3.4.5 none    i686
The following two Root commands should set up the modem.
	sudo modprobe snd-intel8x0m
	sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
Get the SLMODEMD.gcc3.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
       
 The controller: 10b9:5457  ALI 5457 AC-Link 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	Conexant
	Intel
	Smartlink

 Archive records show that 103c:???? Subsystems from HP with the exception of  103c:006b and 103c:3081
 have a Conexant chip.  Thus first test hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers)
 Should that support fail, the alternate route is described in Modem/Slmodem-ALSA.txt
 
Checking for autoloaded ALSA modem drivers
snd_ali5451            22596  2 
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm                78344  4 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    48644  9 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

  Driver snd-intel8x0m  may enable codec acquisition

As always, any help will be greatly appreciated.

---

### Post by az on 2006-05-10
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Specifically:
[https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4)

---

### Post by CoercibleGerm on 2006-05-10
Thanks for the link, hopefully I'll have a little more luck with it this time around.

---

### Post by towsonu2003 on 2006-05-10
[QUOTE=azz][https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)
[/QUOTE]
in the above link, try first the section titled "Modems supported by ALSA drivers (snd_atiixp_modem, snd_via82xx_modem, snd_intel8x0m)"

if you see a "slamr" error, try the section azz recommended. The output of your ModemData.txt suggests that your modem may be able to work without the driver (the next section describes how to compile that driver) bc it is alsa-"capable" (last line in the output you posted above). 

An important note: the first section is ok, but the section that talks about the module (slamr) will **NOT** work with **Dapper**. This is a known bug, but not fixed yet.

---

### Post by CoercibleGerm on 2006-05-17
I've finally found some free time to sit down and try to work this out.

I tried towsonu2003's suggestion hoping the minimalist approach would work, but recieved the slamr error.

After spending a few days in 'dependency hell', I just got all the packages and dependencies needed in the smartlink instructions azz referred me to, where I recieved. . . a slamr error. Except this time, it gave the following output:

> [b]FATAL: Module slamr not found.
SmartLink modem driver not available for this kernel. Please read README.Debian or try to install the package sl-modem-modules-2.6.12-9-386. Exiting. . . [/b]

After searching [http://packages.ubuntu.com](http://packages.ubuntu.com) for the "sl-modem-modules-2.6.12-9-386" package, I discover it to be absent. Does anyone know why this would be, or better yet, where I can find this package?

**EDIT:** As a point of clarification, I should state that I recieved the above output after allowing the command *$ sudo module-assistant auto-install sl-modem* to perform its duties. It was probably implied, but I'd rather make that clear than force someone to assume.

---

### Post by towsonu2003 on 2006-05-17
[QUOTE=CoercibleGerm]
After searching [http://packages.ubuntu.com](http://packages.ubuntu.com) for the "sl-modem-modules-2.6.12-9-386" package, I discover it to be absent. Does anyone know why this would be, or better yet, where I can find this package?

**EDIT:** As a point of clarification, I should state that I recieved the above output after allowing the command *$ sudo module-assistant auto-install sl-modem* to perform its duties. It was probably implied, but I'd rather make that clear than force someone to assume.[/QUOTE]
I believe it's referring to the package sl-modem-source. this "source" is compiled by the "sudo module-assistant auto-install sl-modem" command and so on... in azz' link, it is listed as one of the pre-requisites of the modem configuration steps. 

PS. I thought I filed a bug on that misleading error message but I guess I forgot. File one at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) if you find any free time :)

---

### Post by CoercibleGerm on 2006-05-17
Allright, that makes a little more sense now. After double-checking in synaptic, it shows the package being there without any broken packages, as confirmed by 'apt-get check' from the terminal, so I guess I can safely rule out a missing package.

[quote=towsonu2003]. I thought I filed a bug on that misleading error message but I guess I forgot. File one at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) if you find any free time[/quote]
I've filed the bug report as per your suggestion, so hopefully the erroneous package name will be corrected for future users. :)

Anyways, unless I'm mistaken, it would seem that the winmodem in my laptop won't work in Ubuntu at the present time. In any event, I again thank everyone who tried to help me here. Now that I've forced myself to learn to install packages manually, I'll stick to that while I mull over the possibility of getting a dsl/cable connection. However, If anyone does think of another potential way to get this winmodem operational, I'll be glad to give it a shot, as I'd prefer to have the hardware working, even if it won't be used very often.

---

### Post by towsonu2003 on 2006-05-17
[QUOTE=CoercibleGerm]Now that I've forced myself to learn to install packages manually, I'll stick to that while I mull over the possibility of getting a dsl/cable connection.[/quote]
in that case, you might wanna switch to a distro that comes with more software out of the box. maybe suse...
[QUOTE=CoercibleGerm] However, If anyone does think of another potential way to get this winmodem operational, I'll be glad to give it a shot, as I'd prefer to have the hardware working, even if it won't be used very often.[/QUOTE]
copy paste your ModemData.txt for us, may be there is something one of us could help with in there.

---

