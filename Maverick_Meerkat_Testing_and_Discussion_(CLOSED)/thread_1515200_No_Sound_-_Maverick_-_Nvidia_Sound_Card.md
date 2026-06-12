---
title: "No Sound - Maverick - Nvidia Sound Card"
date: 2010-06-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-06-22
I have created a Bug Report here  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882)

and am keeping track of information here [http://ubuntuforums.org/member.php?u=953253](http://ubuntuforums.org/member.php?u=953253)

My question is ..... does anybody else have the same problem ......

and if so ,,,,,, have you fixed it and how did you do it ......

The Sound card that I have is a inbuilt MCP78 HDMI in a ACER ASPIRE LAPTOP

as described in my footer .......

current ALSA driver

Advanced Linux Sound Architecture Driver Version 1.0.23.

I know that the sound card is ok and works as it runs perfectly well in MINT 9 and ZORIN 3 which I also have on my system ...... 
here is a link to the Operating systems and my updates on what I find ....
[Information about Desktops that run on My Laptop]("http://sites.google.com/site/23dornot23d/")

The link to the two files below is showing the differences between Mint and Maverick ....... 
Sound setups ....  if you open them side by side using gedit it is quicker to spot relative differences .......
but knowing which programs change each of these things is not apparent ........ 

[http://sites.google.com/site/gettingsoundworkinglaptop/sound-realated-files](http://sites.google.com/site/gettingsoundworkinglaptop/sound-realated-files)

I will continue to look deeper ...... maybe I will understand more about how this system works if nothing else .........

---

### Post by dino99 on 2010-06-22
this is how i've tuned my sound issues:

-remove/purge ALL alsa/pulse installed related packages with synaptic
-remove .pulse folder
- reinstall alsa-utils, pulseaudio (or ubuntu-desktop)
- install gnome-alsamixer (and set your prefs)

reboot

[http://www.google.fr/search?as_q=MCP78%2Bsnd_hda_intel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=MCP78%2Bsnd_hda_intel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by 23dornot23d on 2010-06-22
Cheers for the information  ...... 

I will give it a try .... I did as you said and I got further than before ...... 

I can now run alsaconf ....... where I could not before ......

But it tells me I have no pci sound card ...... 

( there is something wrong - usually even in Lucid it would let me pick ALC888 )

Then the sound would work .........

Ok the Latest ..... [Driver and Hardware not seen]("http://sites.google.com/site/gettingsoundworkinglaptop/finding-info-on-your-system-for-sound-to-work") .....

The sound is not working ....... usually I can compile the latest ALSA drivers and off I go

I am pretty positive that the problem lies with something not finding my Hardware ...... as 
I can go into older versions and the sound works .....

I guess this is the answer  ...... go back to a version that works .......

I will try the Old Alsa drivers now, the one that I know worked in LUCID ......

____________________________________________________________

But if the kernel does not find my sound card and set this piece of hardware up  ,,,,,,,, then no other program will find it ?

How can I prove to anyone that the Kernel is or is not working properly ...... for my sound card .......... ?

---

### Post by dino99 on 2010-06-22
[http://ubuntuforums.org/showthread.php?t=1055105](http://ubuntuforums.org/showthread.php?t=1055105)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by 23dornot23d on 2010-06-22
Thanks .....for the links they show that Pulseaudio was at fault before .... for this hardware ..........
____________________________________________________________

That seems to be why removing it and replacing with ALSA worked for me and I guess you you too  ....

This time its not finding the Hardware in ALSA ....... to set up ALC888 properly ......

With the old kernel I did get errors back in KDE saying it was having a problem setting up ALC888 ..... (* but at least it still worked then .... after the errors popped up ).
So it is not finding the hardware and setting it up properly.
I still have not had chance to try the Old ALSA files yet ...... but I know that they worked in  ......... Lucid ....... (* but I cannot see this working as it does not find the hardware to set up )
 
Setting audio from the wrong data supplied by the Kernel   ...... 
Maybe I should pop over to the Linux Mint Forum and ask why there's works ......

As I am listening to Streamtuner on Linux Mint and its perfect not one error ......
on kernel 2.6.32-22-generic ........ this was the last version that I had sound on
that worked ....... (* it also worked in Lucid on this Kernel  2.6.32-22-generic )

So ....when I was using ALSA in LUCID with that same KERNEL 2.6.32-22-generic  
THE SOUND worked ....... so what has changed ............ 

But whats wrong  ...... since the KERNEL was changed !!!!!!!!! 

What else has changed too .........

Lets just try to do a process of working this out ......

1 ......... the Soundcard works on this computer ............................... tick
2 ......... ALSA works on this computer ............................................ tick
3 ......... The Pulsaudio works on this computer in 3 other Distros ...... tick

So where do we look next ........ oh yes volume controls checked   .... tick

Maybe User burnt a bad disk  .. loaded a clean install of Maverick with no errors on Distro and burn and checksum were perfect ......... tick 

What was the most obvious Initial problem on a clean install  ........... No Sound ......... 

So after spending 10 straight hours the other day on this problem determined to get to the bottom of it ...... and I have .......

I did everything I could that anybody has offered as a solution ,,,,

The 4 separate responses I got from the developers ....... on this Bug report
leads me to believe that you do not have enough developers ......
as they do not have time to write a sentence for this BUG ......

I doubt they even did anything more than glance at the files ...... from the responses
I do not expect a detailed answer ..... but the ones I got amazed me ........

I would be embarrassed to treat anyone the same way .....

So they have basically cleared it by saying its a duplicate of one that has 
nothing to do do with the one posted ......

That Bug has been solved by setting the volume up ....... Basically .........


Oh why didn't I realize ......... Thats all it was ................ !!!!!!!!!!!

Thats why I did the following ....... 

After the first response .....

1 ...... Not enough information ......... can you add more info ..... so I did

2 ...... Not enough information.......... yet there was plenty by this point ..... can you try on latest kernel .....  so I did

3 ...... Its a duplicate of another problem the User must have his sound turned down
checked the volumes and it was true the volumes were initially turned down ...... 

**So .....I rectified this** .. ( as I did not realize the system sets everything off on sound ) 

4 ...... I have also added as many follow up responses as I can to help  ......... 


So do you think I could have done this better ..... yes ..... so how ......
I have in the past just fixed it for myself ..... this time I thought lets get it done
properly ......... so what have I supplied to help sort it ......

This information will still be here in 6 months time so if I see any reports on the forum
saying that they have problems ...... at least all the information will be here for them
to go through and see why .........

**I have now 1 Bug report and 3 web pages** ..........
 
Each organized with screen shots and the information I have gained from this .......

The Bug Report
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882)

The commands I have used to find any relevant information so others can use them 
[http://sites.google.com/site/gettingsoundworkinglaptop/finding-info-on-your-system-for-sound-to-work](http://sites.google.com/site/gettingsoundworkinglaptop/finding-info-on-your-system-for-sound-to-work)

My Initial start page here detailing the problem as I go along ...... and what is current
[http://ubuntuforums.org/member.php?u=953253](http://ubuntuforums.org/member.php?u=953253)

A list of the Distributions I run to try to show that I am not a complete Noob
[http://sites.google.com/site/23dornot23d/](http://sites.google.com/site/23dornot23d/)

Although I admit I feel relieved now that I understand the problem ......

Does anybody understand it more maybe [Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds")  knows if there is a problem with the latest Kernel

If I knew that the kernel is working properly for my Hardware and sets it up correctly

Then I would do the following ......... ( But ..... Oh yes I tried this ....... )

I could work out why the ALSA Driver ...... will not compile ...... 
Its because it cannot find my SOUND device ..... so what shows my sound device is there and gets its settings ..........

**The Kernel**

Can anybody see what might be wrong .....
_______________________________________________________________

Conclusions ...........

So no other USERS use ALC888 ....  as they would have posted here ..... or
at least added to the Bug report .....

So they have all tried it out and found that the SOUND WORKs .... you are all OK then 

None have been on the FORUM saying it does not work ...... so my guess is its
only affecting me .....

and the music played on :guitar::guitar::guitar:  but  only if I use ......


LINUX MINT or ZORIN 3 .....


My last problem with Maverick was that the USB Hard Drive was badly overheating .......

But ......... 

I will not be putting a bug report in for that as enough of my time has been wasted here. ( I can only believe that I would get the same response )

But Thank You to the two people that did respond Ranch hand in the other Sound thread to do with the volumes 

and to Dino 99 for the ones here ....... 

Even though this thread has had many views ........ 

This has been a very enlightening experience ..... ):P

---

### Post by cariboo on 2010-06-23
Your bug reports are pretty confusing, it may be better instead of using links to files, include the files as attachments, so that all the information is in one place.

---

### Post by 23dornot23d on 2010-06-24
What does ...... the Maverick Operating System see and know about my  SOUND SYSTEM at the moment ..........



cat  /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec:  LSI ID 1040
Codec: Nvidia MCP77/78 HDMI

dmesg | grep Linux
[     0.000000] Linux version 2.6.35-5-generic (buildd@vernadsky) (gcc  version 4.4.4 (Ubuntu 4.4.4-4ubuntu1) ) #6-Ubuntu SMP Mon Jun 21  21:33:48 UTC 2010 (Ubuntu 2.6.35-5.6-generic 2.6.35-rc3)
**[     0.177007] ACPI: BIOS _OSI(Linux) query ignored**
[    1.010000]  Linux agpgart interface v0.103
[   17.062395] Linux video capture  interface: v2.00



aplay -l
**** List of PLAYBACK  Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888  Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice  #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888  Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0:  Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices:  0/1
  Subdevice #0: subdevice #0


cat /proc/asound/cards
 0  [Intel          ]: HDA-Intel - HDA Intel
                      HDA  Intel at 0xf0500000 irq 46


cat /proc/asound/version
Advanced  Linux Sound Architecture Driver Version 1.0.23.



00:1b.0  Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller  (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0142
     Flags: bus master, fast devsel, latency 0,** IRQ 46**
    Memory at  f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50]  Power Management version 2
    Capabilities: [60] Message Signalled  Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70]  Express Root Complex Integrated Endpoint, MSI 00
    Capabilities:  [100] Virtual Channel <?>
    Capabilities: [130] Root Complex  Link <?>
    Kernel driver in use: HDA Intel
    Kernel  modules: snd-hda-intel

___________________________________________________________________________________________________________________________

The sound works on all of the Systems below ................[B]

Operating Systems where the sound works ok ....... 

keeping all the information together so that it can be followed ...... 



This first one is from Linux Mint where it works ok .......[/B]  

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0142
    Flags: bus master, fast devsel, latency 0,** IRQ 22**
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

MAYBE IT IS THE ALSA VERSION .....



**This one is from Zorin 3 ......**

root@keith-laptop:/home/keith# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0142
    Flags: bus master, fast devsel, latency 0, **IRQ 22**
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


**This one is from Mandriva 2010 .............**

Linux localhost 2.6.31.5-desktop586-1mnb #1 SMP Fri Oct 23 00:21:26 EDT 2009 i686 Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz GNU/Linux


[root@localhost keith]# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                                                                       
        Subsystem: Acer Incorporated [ALI] Device 0142                          
        Flags: bus master, fast devsel, latency 0, **IRQ 22                       **
        Memory at f0500000 (64-bit, non-prefetchable) [size=16K]                
        Capabilities: [50] Power Management version 2                           
        Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+              
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00     
        Capabilities: [100] Virtual Channel <?>                                 
        Capabilities: [130] Root Complex Link <?>                               
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel


Ok so I guess now ..... update the ALSA in one of these and see if the Sound stops working

__________________________________________________________________________________________

Updated ...... Re Booted ....... and guess what ...... I still have sound ..... with the latest ALSA drivers installed .......

Just for information for other users that may find this of a little use ...... **the latest ALSA is not the problem **



Linux keith-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
root@keith-laptop:/home/keith# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 24 2010 for kernel 2.6.32-22-generic (SMP).

---

### Post by cariboo on 2010-06-24
Actually I meant in the bug report, but lets have a go.

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 0/1
Subdevice #0: subdevice #0


cat /proc/asound/cards
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xf0500000 irq 46

According to the above, you sound card is detected. 

When you go to sound preferences and click the output tab, does it look similar to the screenshot?

Do you have your HDMI cable connected to a monitor with builtin speakers, or are you connecting your speakers to the output jack on the motherboard?

---

### Post by 23dornot23d on 2010-06-24
Mine is just the internal audio ......

What shows up ....... is the internal one as shown below  ..... 

( I do not connect to external ..........) its a laptop but it has

a surround sound system built into it ........... (sounds good too) when its working ......

This is in Maverick 10.10   ( I have now  loaded the ultimate edition on but the same problem exists in it too )
............  
I will do a screen shot for you ....

Does the fact the interrupt is different not make a difference .... the different IRQ that it uses  ...... 
its **IRQ 46**  in **Maverick** ......  but its ** IRQ 22** in all the systems that **the SOUND** works ok on ..........
I just looked for what I could find that was not the same ...... but this is all I really spotted
was the IRQ being different ... ... so what sets the interrupt up and does it matter ?



IRQ problems of the form you report can arise from a couple of places - 
one is vendors getting IRQ routing tables wrong (suprisingly common),  the other may be a Linux bug. 




What is odd  ....... is that my knowledge on these is limited ...... 
I believe that they just constantly send signals back and forth between the devices ........ 
I need to know more about these

but does it make a difference which [interrupt]("http://www.rigacci.org/wiki/doku.php/doc/appunti/linux/sa/irq_acpi_apic") is used ?  (as long as it goes to the right device .....)
```

THIS NEEDS TO BE CHECKED as 22 is missing from the list that this command outputs ...
from what I read ....... I think it needs doing at boot time from GRUB irqpoll

But still not sure if that will give me tha answer that I am looking for ........ !!!

root@keith-laptop:/home/keith# cat /proc/interrupts
This is From Zorin ...... 
I will add another from Maverick ....  

         CPU0       CPU1       
  0:     253440     236226   IO-APIC-edge      timer
  1:          5       1747   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:         78         35   IO-APIC-fasteoi   acpi
 12:         69         76   IO-APIC-edge      i8042
 16:       2121          8   IO-APIC-fasteoi   uhci_hcd:usb3, nvidia
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8, mmc0, jmb38x_ms:slot0
 19:       1389      45062   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb7, ath9k
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:       4993       1441   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 29:      25482       2694   PCI-MSI-edge      ahci
 30:        207        908   PCI-MSI-edge      hda_intel
 31:         18       8312   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     254897     115621   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       8475       4625   Rescheduling interrupts
CAL:       2414        252   Function call interrupts
TLB:       3491       2908   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          6          6   Machine check polls
ERR:          1
MIS:          0


```[IMG]http://5583407636427854343-a-1802744773732722657-s-sites.googlegroups.com/site/gettingsoundworkinglaptop/finding-info-on-your-system-for-sound-to-work/snapshot18.jpeg?attachauth=ANoY7cpl1gqoxYG_e78TTtkw4WCrlo9R-2gfEyzw-YuSFr29vHDRA_o8v90E_7QuyzrBhYEdhNsfWFuEcN84zYZVK9sljjJroMfEPfwh4skibxOnXHnnbVeesU_iNiNp5iPzMF3VLfrRsWhjLijl1t-6Pgv-9jTquGBtkLrXVMC19NqiwU7Blfcq1RLd0C-Hf6c6LrvQSjzV4Z-wTgW6R29JiaLWRjs8TAgH5lOlSECW5hEOn8ZCVH71KORy-00PkIzgTLGGmsyF_R-Kqf8xZVNCMDypmVIsyg%3D%3D&attredirects=0[/IMG]


Link to fixing [SOUND PROBLEMS]("http://ubuntuforums.org/showthread.php?t=205449")

I still have no sound at all ........ after updating to the latest kernel ....... 
Linux keith-laptop 2.6.35-5-generic #6-Ubuntu SMP Mon Jun 21 21:33:48 UTC 2010 i686 GNU/Linux


So anything else ......

The Codecs maybe
        
**Maverick**

snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
        
**Zorin** ....  

snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device



I am more inclined to go for the easy option here ........ 

Which is > ? 

Finding out if I can change the interrupt to see if it makes a difference ....
or adding more codecs ................ if I add more codecs what damage can I do .... 

or do I simply turn the volume control up ....... as the answer in the Bug Report implied

I would have added to the Bug Report if it made the slightest bit of difference ......

I will add to it when I solve this little puzzle .......

All the information to solve this is available between the 4 Operating Systems 
and seeing that it only seems to be a problem for me .......  on one of them ....

[B]Which to be homest ......... I think that it is highly unlikely .......
at least one more person in this community must have a 
Acer Aspire 7730ZG ....... 

if I get to understand how this all works will be of benefit to me .....

____________________________________________________________

The Problem has only happened now on three completely clean installs of Maverick.

I have sound working perfectly on   Zorin ....... Linux Mint ......... Mandriva 2010 .......
[/B]
So I am pretty certain that the problem lies here and I am pretty certain it can be solved as other
OS's have got it working properly ......... the devs have more problems to sort out than they can
handle though so I will continue ..... but it is nice when the odd remark is added to these to try to
help solve the problem ........ saves me wasting time looking in the wrong places .......

As you probably know ...... I think its the **Kernel** ......... but we have to start somewhere .....
and then disprove the theory .........

Whats before the **Kernel **........ surely its not something to do with something prior to **Grub 2** ........
nope don't be silly ...... the other OS 's would not work if it was ........ so .... what next ?

---

### Post by clivejo on 2010-06-24
I have a similar problem with my audio, but it seems that the volume is minimized or muted on reboot.  Here's how I get my sound to work again.  

In your Sound preferences if you go to the Output tab and select each output in turn, slide the slider right down to minimum, then let go and slide it to maximum.  Check and un-check the mute button.  Don't ask me what this does but when I do it the sound comes back on again.

PS Good idea to play a music file in the background so you know when its working or not!

EDIT : Oh and if that doesn't work try running alsamixer from the command prompt, move all the sliders to maximum and check they arent muted.

---

### Post by 23dornot23d on 2010-06-24
Its the** Kernel **........... thats **messed up** the Interrupts ........



Sound Works ...........  This is Lucid Lynx 10.04 .........  2.6.32-21-generic

root@keith-laptop:/home/keith# uname -a
Linux keith-laptop  2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686  GNU/Linux


00:1b.0 Audio device: Intel Corporation 82801I  (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer  Incorporated [ALI] Device 0142
    Flags: bus master, fast devsel,  latency 0,** IRQ 22**
    Memory at f0500000 (64-bit, non-prefetchable)  [size=16K]
    Capabilities: [50] Power Management version 2
     Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0  Enable-
    Capabilities: [70] Express Root Complex Integrated  Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
     Capabilities: [130] Root Complex Link <?>
    Kernel driver in  use: HDA Intel
    Kernel modules: snd-hda-intel


[LEFT][[IMG]http://sites.google.com/site/23dornot23d/_/rsrc/1277381467219/sound-problems/DesktopLucid16.jpeg?height=250&width=400[/IMG]]("http://sites.google.com/site/23dornot23d/sound-problems/DesktopLucid16.jpeg?attredirects=0")[/LEFT]


____________________________________________________________________

This is the same Lucid Lynx 10.04 + directories and everything ...... after a Kernel update ..... 

Sound Stops working ........ after I updated the Kernel ........... The IRQ is 3 here !!!!!

Capabilities:  [50root@keith-laptop:/home/keith# uname -a
Linux  keith-laptop 2.6.35-4-generic #5-Ubuntu SMP Wed Jun 16 18:53:19  UTC 2010 i686 GNU/Linux
] Power Management version 2

00:1b.0 Audio device: Intel  Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
     Subsystem: Acer Incorporated [ALI] Device 0142
    Flags: bus master,  fast devsel, latency 0,[B] IRQ 3
[/B]    Memory at f0500000 (64-bit,  non-prefetchable) [size=16K]
    Capabilities: [60]  Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
     Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
     Capabilities: [100] Virtual Channel <?>
    Capabilities:  [130] Root Complex Link <?>
    Kernel modules: snd-hda-intel



[LEFT][[IMG]http://sites.google.com/site/23dornot23d/_/rsrc/1277381856268/sound-problems/DesktopLucid17.jpeg?height=250&width=400[/IMG]]("http://sites.google.com/site/23dornot23d/sound-problems/DesktopLucid17.jpeg?attredirects=0")



No Kernel Driver in use > ?


[/LEFT]

---

### Post by cariboo on 2010-06-24
Is your sound problem with an Nvidia chipset or Intel, all your listings point to Intel.

From the screenshot, it looks like sound is working in audacious, just that there is no output. I noticed last night that the screenshot of the sound preferences showed that it was set to analog output, checking with my notebook the connector is set to analog speakers, have you tried that?

Also I would suggest stop posting what is happening with other version, your just adding way to much information.

What is the output of:

```
sudo lshw -C multimedia
```

---

### Post by cariboo on 2010-06-24
What are you actually having a problem with, the thread title says Nvidia, but all your screenshots and listings show Intel.

I noticed last night, in the screen shot you posted and then took down, that you had the output in set to analog output, I checked my notebook, and the sound output is set to analog speakers, have you tried that?

Could you please post the output of:

```
sudo lshw -C multimedia
```

for maverick only.

---

### Post by 23dornot23d on 2010-06-24
This is the output from the command ..........   lshw -C multimedia

As you say it appears to be Intel ....... ( ..... not Nvidia ..... )

I originally looked up the specifications for sound on a 7730ZG  
on the net and it said it was Nvidia ... thats why its in the title ......

But as we can see from all the outputs its **Intel** ...........

This is the output for Maverick only .......

[IMG]http://5583407636427854343-a-1802744773732722657-s-sites.googlegroups.com/site/gettingsoundworkinglaptop/finding-info-on-your-system-for-sound-to-work/snapshot20.jpeg?attachauth=ANoY7cqhNG61lsVILz-9ijmUY8EMrlYn-d-11ATawnKTvJ11k_2pr1uUrlM_ldq7AfnMzxZrpKsPvld13IMi2qWbCcStB-f1vwz0Fxcx_j0ZwDcAX7x2QKHZmrsBcCyU6tG3gymhCyPOAtpcJuCN_UgMl5cLFaY4p_T-lS1E0Rxornjs6ugbDPc9sC7R7dX06o4uouFyk5TEzO0uMXXsFIpkW2rhfb8E_Pe9-AFOF-SZOb8gSPHjw7-oX1dMm7fK_Iw37n7Hb_XNHBA54HzbAwhe7BPVUbvpNQ%3D%3D&attredirects=0[/IMG]

(* by the way Audacity was running in Lucid with the latest kernel added ..... that was to show the IRQ 3 change only ) 

In Maverick it does not ...... show any bars at all when running ........ and makes no sound whatsoever ......

This is screen shot of Maverick with the Sound up and the Radio Playing ...... 

I picked the full surround here to give it a chance of working on any of the speakers

But I have tried all the options ...............

[IMG]http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot22.jpeg?attachauth=ANoY7cpTopEMzZXkR9OiiDuwC9ynD8WvcbfsFwu5RonTaSsUqzWs4oU5g7Cjzjce3mzwpqw8nCNJdB0LcZqAvN2VZ589KDJxb1Zw40CTXOJldkF4VutJyioR-Iwho8z7yQyJp81cpd-Xfk4qq-6_mfuogBm-6mn3EKyyL0m58cPCPmgk1B_73bA2up-f5Ep8xEih8eHlLbf8v6E1p1T4sjLUPBlB2-Igmg%3D%3D&attredirects=0[/IMG]

I will just post what you ask for ........ 
( ignore all the previous posts and I will give you screen shots of exactly what you want )

I will not alter anything - by doing updates or anything else unless you ask me to do so .......

As for the choices ..... I do not have external speakers ........ these are my options

[IMG]http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot23.jpeg?attachauth=ANoY7cpbvfuCIZHFrUI1Ke4W_I8FbrHDR-TKqcBZayO9DAJd4KZFdkamrXDDvWg6hzmnMwg0L7JSjUkh4MPYIgRE1klIf78TM76jsKFhA8852TQ6oFi2IDWduKB0djJLE85_4Tq8c9G1nEsWA_WW9EIWPqK5s4OgJIFFsooBME3moEXYz4_YAXztI4OjXQtqkHUDvwujzgmd5cg0Mxm490r6d2m98P_Y6A%3D%3D&attredirects=0[/IMG]



I have tried them all I think  ...... if you want to pick one we will go with that choice.

---

### Post by cariboo on 2010-06-24
In your 3rd screenshot you have a check mark in mute beside output, is it there for a reason?

---

### Post by 23dornot23d on 2010-06-25
That check mark is in its off state ...... if you click it - it goes white and a lot brighter ,,,,,,

Here is a shot of it with the desktop scheme changed


[IMG]http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot24.jpeg?attachauth=ANoY7cpa54sMeINzuU1Spq_EQyJ9bkgluht_FreKeIMhstwfODA3x4m4T_9abaJW36AvLgEKnPW85cn_pbutiEkrSyeiy6-ztjGSM1Azu3BO9QMqPW91HEpsiKqSKLs0ccQ2-_n454_HwUvGCZJj8_4NOkFMpf1h1BaC-iQyUf-MBOmIocpHWcAhFS2uQQpP6CRY-zpEBozoARpVR6DdafJq6FyLxHM_Qg%3D%3D&attredirects=0[/IMG]


No Sound .....

---

### Post by cariboo on 2010-06-25
TO me it looks like you sound is working, there is just no output, have you made sure the volumes isn't muted. Have you tried alsamixer.

---

### Post by 23dornot23d on 2010-06-25
Here is a screenshot of what I get when I open the alsa mixer

[Screenshot of AlsaMixer]("http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot3.jpeg?attachauth=ANoY7crybZnnfIkVO9o1JdChzuTjAnBQ4GrqJQX7Qlum6gg4Emo0y5-6ZHg08c6esb_phCtxw6xdxigT3eYqgrA8eIXUFLeZoj67Tyarlj34fBQwdhhKlxULKGxBy4aBfFh2f5UDoY1FKegtru_Ua--zTbsPaaj5xhaly2Kf4BseBqnchfKLWhwxT9i1xH0vRWmpPgj7L2HaPaM47gLD7fAhnwrcXCbLvQ%3D%3D&attredirects=0")

---

### Post by clivejo on 2010-06-25
Try running aslamixer from the terminal, and post the output fro us to see.

---

### Post by clivejo on 2010-06-25
Regarding the Nvidia sound card, do you have a HDMI output on your machine, this is probably related to that.

---

### Post by 23dornot23d on 2010-06-25
I have a HDMI output but it is not currently in use ..... 
or being used .... by this I mean that ......
( I do not have a cable plugged into it )

Here is the [FULL SCREEN SHOT]("http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot6.jpg?attachauth=ANoY7cryuRvR8csWEN-KmG4nk4X32evHFw0P46JDWOryshYl6FwDTN16Udmps-8mJSAQ9ywA40ChFSjtuKIOZbG8oWQisAXPnImBQ50gkffT1CHty3WgRAwt0930eOt4w7ljvwR5wd2Hj59S2FPK8ovQTeQmalegMANPlb8x7i4UWmzGne8rp-6Xge8FJiRGSfDGw5oG4ZaXqzCQmWM4JtJKwrr9ivqDYg%3D%3D&attredirects=0") of the Alsa mixer run from the terminal

[IMG]http://5107642209104388977-a-1802744773732722657-s-sites.googlegroups.com/site/23dornot23d/sound-problems/snapshot2.jpg?attachauth=ANoY7crQUo7SYWyjYOYkPYkBRQx02kYwTJUYNwFnx2uh4PCjquLbPm9ZdOb1fQGDGM3ohzQDLA4KdP-rPdUKWAbxixafYPOaYr7RVXID5-KIP6EhoC5C8WVoJURanJ9Mteb5zttopH-hTapKWtY-60WuFf4yb68RlRpA-rHuGjRLgJfE-zBrDo1zshV6cm-X7dV5PYj5AvxVFhd5fHYX94NEQMth8lZptg%3D%3D&attredirects=0[/IMG]

---

### Post by 23dornot23d on 2010-06-25
Ok the good news ....... I have sound working in Fedora 13 now 

 Problem and [Solution LINK]("http://sites.google.com/site/23dornot23d/sound-problems")

---

### Post by cariboo on 2010-06-25
Have you tried one of the vanilla ubuntu kernels? More info [here]("https://wiki.ubuntu.com/KernelTeam/KernelGitGuide?action=show&redirect=KernelGitGuide")

---

### Post by lidex on 2010-06-25
Just a thought. Have you tried MSI options in alsa-base.conf? From alsa documentation:
> Interrupt Handling
~~~~~~~~~~~~~~~~~~
HD-audio driver uses MSI as default (if available) since 2.6.33
kernel as MSI works better on some machines, and in general, it's
better for performance.  However, Nvidia controllers showed bad
regressions with MSI (especially in a combination with AMD chipset),
thus we disabled MSI for them.

There seem also still other devices that don't work with MSI.  If you
see a regression wrt the sound quality (stuttering, etc) or a lock-up
in the recent kernel, try to pass `enable_msi=0` option to disable
MSI.  If it works, you can add the known bad device to the blacklist
defined in hda_intel.c.  In such a case, please report and give the
patch back to the upstream developer. 


---

### Post by lidex on 2010-06-25
There is also a model option for your laptop. Have you tried it? I am a bit lost with all the info you provided. In essence:
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer-aspire-7730g 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by 23dornot23d on 2010-06-25
> **lidex said:**
> There is also a model option for your laptop. Have you tried it? I am a bit lost with all the info you provided. In essence:
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=acer-aspire-7730g 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.


Cheers .... lidex ..... have tried the edit above ...... but with no success .....
have even tried on different kernels too ...... 

The  2.6.33 realtime kernel is really fast .....but still no sound for me yet ....
but when I get it working ,,,, this will become my main system ......

I will keep trying ......  there will be a answer ...... its just working between the
systems that work and the only one that does not now ...... 

To work out whats so different !!! :guitar: and the music played on ..... 
and soon it will be playing in Maverick too.   ;)

---

### Post by lidex on 2010-06-25
How about this:
```
options snd-hda-intel enable_msi=0
```

Or 1 perhaps. You currently have no options added, correct?

---

### Post by 23dornot23d on 2010-06-25
Just the one you gave me before and the ones already in the file .....

I will try this out soon .....

---

### Post by cariboo on 2010-06-25
@23dornot23d

Could I suggest you stop using the trailing periods, it makes your posts and diagnostics confusing. It makes the post seem as if you are talking to yourself. :)

---

### Post by 23dornot23d on 2010-06-25
Lols ..... I spend a lot of time doing that ,,, ;)

Thats the full alsa-base.conf file .... that I have

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=acer-aspire-7730g
options snd-hda-intel enable_msi=0

```Nope ,,,, tried it both ways ..... and it still does not work ,,,, should I have placed it earlier in this file
or is it ok at the end .... ?

Last try tonight ..... I will have another try at compiling the ALSA drivers and re loading them ....

If it does not work will look at the vanilla kernels tomorrow ...... cheers  ...... ;)

---

### Post by lidex on 2010-06-25
Do you mean you tried msi=1 as well? I would only use one line at a time. Some other options for model:
```
options snd-hda-intel model=acer-aspire position_fix=1 enable=yes 
options snd-hda-intel model=auto
options snd-hda-intel model=acer
options snd-hda-intel model=acer-aspire
```

---

### Post by 23dornot23d on 2010-06-25
Ok will try these new commands out thanks ..... 

I did try that command with a 1 ,,,,,,,,,, as well as the other way with a Zero ......
and did full shutdown and a cold boot each time .....

But made No difference ..... 

I tried my DVD with the distro on it on another computer too and the
sound works fine on that .....  Acer Aspire 1351 ...... very old so slow like me ..... but
doing this showed me 2 things .... the disk was ok and the sound does work .....
it also showed me that the sound should play at the animated logo in this Extreme Edition

As yet nothing not even a murmer ....but it is going to work ..... trust me .... ;)

Once I can get the latest ALSA drivers to compile !!! .... it was so easy before .....


I will try your commands out before doing the new compile of the ALSA for my machine .

Now thats interesting ........ (although does it just mean not tested on yet ,,,,)
ALSA
Supported kernels: 2.6.24/26/27/28/29/30/31/32 family (including  rt-kernel & NON-Ubuntu ZEN-rt-kernel)

---

### Post by 23dornot23d on 2010-06-26
SORTED ..... Thank you very very much Lidex ......... :popcorn::popcorn::popcorn:


The file alsa-base.conf now looks like this
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto


```Adding this command did it .......... :KS:KS:KS:KS

gksudo gedit /etc/modprobe.d/alsa-base.conf

**options snd-hda-intel model=auto** 



:guitar:

And Now the Music plays in Maverick also ................ on a ACER ASPIRE 7730ZG ...... 

SUCCESS ......

and thank you CARIBOO907 for keeping the thread on track and getting me to look at
 other things - without your help I may not have continued to the end ,,,

_______________________________________________________________

There are 2 very small problems that remain ,,,, ( These are minor though )
The visualization of the sound ..... ie the little green bars moving are not showing in Audacious
and 
it will only allow playing in Stereo not the Full Surround Sound ...... ( Full surround would be good though )
not that this is a big problem now ( I will check the alsa-base.conf ) in Zorin

I will also check the other commands out ......
to see if they make any more difference ...... 

Sorry I blamed the Kernel ..... and good calls in the Bug forum .....
I may have wasted a lot of their time going down the wrong track ........

I am just so happy to hear sound now ........

---

### Post by cariboo on 2010-06-26
I'm glad to see you got sound working.

---

### Post by k4341 on 2010-09-01
> **23dornot23d said:**
> 
Adding this command did it .......... :KS:KS:KS:KS

gksudo gedit /etc/modprobe.d/alsa-base.conf

**options snd-hda-intel model=auto** 
Thank's All
 my sound work with delete 

```
 [B]# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2[/B] 
```sudo killall pulseaudio
n edit /etc/pulse/default.pa  delete "#"  into this ```

[B]### Register ourselves in the X11 session manager
load-module module-x11-xsmp[/B]

```

---

### Post by Ktron on 2010-09-09
> **dino99 said:**
> this is how i've tuned my sound issues:

-remove/purge ALL alsa/pulse installed related packages with synaptic
-remove .pulse folder
- reinstall alsa-utils, pulseaudio (or ubuntu-desktop)
- install gnome-alsamixer (and set your prefs)

reboot

[http://www.google.fr/search?as_q=MCP78%2Bsnd_hda_intel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=MCP78%2Bsnd_hda_intel&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

These steps worked perfectly for me on my Intel DQ35JO motherboard running Maverick Meerkat Beta (32bit).

---

### Post by coibyxqx on 2010-10-06
> gksudo gedit /etc/modprobe.d/alsa-base.conf

[B]options snd-hda-intel model=auto
[/B]It works for me. I can listen to my music now:guitar:. 
But I am wondering why **"options snd-hda-intel model=acer-4930g" **music didn't work.
> **23dornot23d said:**
> SORTED ..... Thank you very very much Lidex ......... :popcorn::popcorn:


The file alsa-base.conf now looks like this
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto


```Adding this command did it .......... :KS:KS:KS:KS

gksudo gedit /etc/modprobe.d/alsa-base.conf

**options snd-hda-intel model=auto** 



:guitar:

And Now the Music plays in Maverick also ................ on a ACER ASPIRE 7730ZG ...... 

SUCCESS ......

and thank you CARIBOO907 for keeping the thread on track and getting me to look at
 other things - without your help I may not have continued to the end ,,,

_______________________________________________________________

There are 2 very small problems that remain ,,,, ( These are minor though )
The visualization of the sound ..... ie the little green bars moving are not showing in Audacious
and 
it will only allow playing in Stereo not the Full Surround Sound ...... ( Full surround would be good though )
not that this is a big problem now ( I will check the alsa-base.conf ) in Zorin

I will also check the other commands out ......
to see if they make any more difference ...... 

Sorry I blamed the Kernel ..... and good calls in the Bug forum .....
I may have wasted a lot of their time going down the wrong track ........

I am just so happy to hear sound now ........

---

