---
title: "Matrox Dual Head with 9.10"
date: 2009-11-03
forum: Multimedia Software
---

### Post by mbmccurdy on 2009-11-03
Hallo!

Has anybody succeeded in getting a dual-screen setup running with a matrox g400 or g450 on 9.10? If you have, could you please send me your xorg.conf, or, if you didn't need to write one, could you tell me how you did it?

Needless to say, I installed 9.10 and now my dual head setup no longer works. It worked with 8.04, so I don't know what happened.

Cheers,

Micah

---

### Post by decubal on 2009-11-06
I have the same problem using a Matrox P690 LP PCIe x16
worked fine in 8.10 :D

---

### Post by kpoole on 2009-11-07
> **mbmccurdy said:**
> Hallo!

Has anybody succeeded in getting a dual-screen setup running with a matrox g400 or g450 on 9.10? If you have, could you please send me your xorg.conf, or, if you didn't need to write one, could you tell me how you did it?

Needless to say, I installed 9.10 and now my dual head setup no longer works. It worked with 8.04, so I don't know what happened.

Cheers,

Micah

I'd still be interested in seeing your xorg.conf, if that was all that was needed, for the g400 with 8.04.  I have one of those cards and I'd love to see both heads working on any version of Ubuntu.  If you wish you can email the file to [email]kenpoole@gmail.com[/email]

Many thanks.

---

### Post by judge jankum on 2010-01-19
I'm using Xubuntu 8.04 and all I have is 800/600 res with a  g400/450
 I need a driver or something..
And I only need one head working...

---

### Post by gon-phishin on 2010-02-27
Any new information on this?
I'm running into the same issue with a Matrox card with 9.10. I haven't been able to get the display to work properly.

---

### Post by Sir_Yaro on 2010-03-02
Anyone ?

---

### Post by ScottMikros on 2010-03-03
Got 2 ancient Matrox G450 dual Video Cards in Ubuntu 9.1 (1 PCI, 1  AGP...in Compaq W6000, you can stop laughing now, it works in Windows  XP)
Matrox support is only thru Ver. 7.0.0:
[http://www.matrox.com/graphics/en/su...wnload/?id=143]("http://www.matrox.com/graphics/en/support/drivers/download/?id=143")
How/where do I tell Ubuntu how to see alt. drivers so I can at least try  above?
BB solutions look like I have to revert to source code.
Anybody have any experience with this configuration or any ideas (that  don't involve a new box)?
Thanks!

---

### Post by sam.reader on 2010-03-03
I had the same problem when I was using Ubuntu 8.10.
Back then I thought that the 8.10 version of Ubuntu doesn't support Dual Screens.
but when i upgraded to 9.10 I have realized that the problem was with my gig.
Am looking for answers.
Can someone help me?

---

### Post by Sir_Yaro on 2010-03-04
Solved.

I had to install *xserver-xorg-video-mga_1.4.9.dfsg-3ubuntu1~bug292214_i386.deb* from [http://ppa.launchpad.net/bryceharrington/ppa/ubuntu/pool/main/x/xserver-xorg-video-mga/](http://ppa.launchpad.net/bryceharrington/ppa/ubuntu/pool/main/x/xserver-xorg-video-mga/)

and now dual head works like a harm....

---

### Post by Sir_Yaro on 2010-05-19
Doesn't work in 10.04 again... !!

---

### Post by Steelkilt on 2010-08-30
Same problem with the Matrox G450 in Ubuntu 10.04.  I am all ears.

---

### Post by Sir_Yaro on 2010-08-30
Any solutions ? :confused::cry::cry:

---

### Post by rutiezer on 2010-12-08
Could not find a close enough similar question after a search of ubuntu forums. Cross posted in [http://ubuntuforums.org/showthread.php?t=1441824](http://ubuntuforums.org/showthread.php?t=1441824), List of dual-head graphics cards that work "out of the box" with Ubuntu 9.10 or later.

Will this Matrox video card, MGA G400/G450, work on 10.04 LTS, 32-bit?
The video card has been working for several years on 8.04.
What do I need to do beside move the video card to the new system, an Asus P5GDC-V? The motherboard has video built-in. 

Can get two used video cards if that would make it easier to get the dual monitor working.

On 8.04 I replaced the file /etc/X11/xorg.conf from the installation with one found at ubuntu forums. Can paste it here if that would help.


~$ lspci| grep VGA
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

~$ sudo lshw -C video
[sudo] password for oem: 
  *-display               
       description: VGA compatible controller
       product: MGA G400/G450
       vendor: Matrox Graphics, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=matrox_w1 latency=32 maxlatency=32 mingnt=16 module=matrox_w1

---

### Post by eldiabolosk on 2010-12-12
Did anybody get the Dual Head working with the Matrox G450 card?

Ed.

---

### Post by rutiezer on 2010-12-12
Experiment regarding my post #13.

Tried to boot from live CD for Ubuntu 10.04 on Dragon Ultra P4X400 where the Matrox dual head does work when runing Ubuntu 8.04. Tried same thing using live disk for Kubuntu 10.04.
 
Short answer is that boot to Ubuntu 10.04 "essentially" fails while boot to Kubuntu does work. Don't know how to check if dual monitors work in this environment.

More details: When Ubuntu 10.04 comes up, there are grey panels at top and bottom of main screen occupying about 1/3 of screen. There are no launchers in the top grey area. Nothing for computer restart, no date/date time, applications, nothing. During startup the secondary screen has a blue moving box that says "Frequency out of range".

---

