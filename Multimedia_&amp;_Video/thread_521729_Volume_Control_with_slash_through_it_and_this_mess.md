---
title: "Volume Control with slash through it and this message"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by Midwest-Linux on 2007-08-09
I just installed Ubuntu 7.04 on a IBM 300 GPL 192 RAM 10 GIG HD 400 MHZ speed. It used to have Windows 98 on it, the sound worked fine to play CDs and system sounds worked too. On Feisty 7.04 there is that volume control but it has a slash right through it. 

 Then there is this message which I included a picture of in here. I Installed the G Streamer packages..all of them..including audio players and such. What do I need to do to get the sound going on this?

---

### Post by Midwest-Linux on 2007-08-09
I am now trying the Comprehensive Sound Solutions Guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


 I went to the terminal and typed in
Aplay -1

it was the wrong command it said to use 
Aplay--help

I typed that in and found that I should use 
Aplay -l

came back as device list 222 no soundcards found

I did the lspci -v


It listed a Host Bridge Intel Corporation  440BX/DX/ZX 


listed flags and memory and at the bottom said <Access denied>


I went to  [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

Be advised that the link is now
[http://bugtrack.alsa-project.org/main/index.php/Matrix:Main](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)


I am now at the intel page at 
[http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I see a 440MX listed which seems close to my 440BX.

So on the Ubuntu computer I am at the intel page 
I type in the terminal
sudo modprobe snd-
and then have to enter my password
then it says
FATAL: Module not found

I re did it and tried 
sudo modprobpe snd-via82443MX 
then I got this
FATAL: Module snd via 82443MX not found

Then I just tried to click on the link it was a zip file, it downloaded it and there are are IF files for Windows 95 and Windows 98 and the read me files. The read me files says this is for Windows.

So now...what folder do I drag these INF into/type into...or is it the BIOS setting that needs fixing? 

If so what setting do I change it to? 

Why would I have to change the bios if sound worked with Windows 98 on this machine? (I used "Boot and Nuke" to purge Windows off this machine).

Would I be better off using Dapper Dan instead? Are there sound card issues with Dapper Dan too?

It would be no big problem to Nuke and boot Ubuntu Feisty off this machine and put Dapper on here if that would be the best method.

---

### Post by Midwest-Linux on 2007-08-09
Anyone?

---

### Post by Midwest-Linux on 2007-08-09
Could the "ACPI-Force " be the cause of this problem? This is a older motherboard from 1999 and I see that others have "ACPI-Force" problems with older boards before 2001 though maybe not related to sound...Again to clarify this , when I had Windows 98 on this machine sound worked fine. but it does not work for Feisty 7.04. 

 I would have left Windows 98 on this machine and do a dual boot, but Windows 98 does not connect to the internet through the ethernet connection...its only Windows 98SE or better that allows it.

However I installed Feisty 7.04 on my APPLE Power Mac using the PPC version and had no sound issues whatsoever, so why would sound work in my Apple G3 running Feisty 7.04, but a Intel machine running Feisty 7.04 will not play sound or recognize that my soundcard is not here??? 

Could the ACPI-Force bug be the culprit? And how come I get a access denied...does that mean I should change the bios? If so to what? I see that there are other posts regarding no sound, though it seems that I might  be the first one with the slash going across that speaker icon ...though.

---

### Post by Midwest-Linux on 2007-08-09
I went to the F1 setup I turned off ACPI and turned on the APM to see that made any differences. I thought at least it solve the minor problem of the computer not shutting properly..it didn't...and it did not resolve the sound problem either.

---

### Post by Midwest-Linux on 2007-08-09
I turned the ACPI back on and turned the APM off...the only thing i could try now is the ACPI-Force add on....to see that works as my last resort and if that does not work....


 Next is to is to wipe Feisty off the computer and try Dapper Dan. If that does not cure the sound problem, then maybe another linux variation or....maybe find another OS that will enable sound.....something has to work...



 Sound works on a Apple G3 Feisty, but not on a Intel IBM machine with Feisty....amazing.

---

### Post by fredj on 2007-08-10
The volume control with a red slash though it means that no soundcard has been detected.
Your PC seems at the low end as far as memory is concerned. Try booting up on the LIve CD
before you install and see if any sound is detected there.
Do you know what the name of the soundchip is?

---

### Post by Midwest-Linux on 2007-08-10
> **fredj said:**
> The volume control with a red slash though it means that no soundcard has been detected.
Your PC seems at the low end as far as memory is concerned. Try booting up on the LIve CD
before you install and see if any sound is detected there.
Do you know what the name of the soundchip is?

Intel Corporation 440BX/DX/ZX

 And I installed Dapper Dan this time, its different...instead of a slash across the speaker icon..it is a "X" across the speaker and have the same issue. The only thing now is to try looking for some option for detecting a sound card and turning on the PCI card function...or there must be some jumper or set up on the soundcard, its either that is the problem ..or I must buy a linux soundcard. This machine originally had Windows 98 on it and the sound worked fine, but could not get on the internet. This is a 400 Mhz machine 192 Ram and 10 gig HD, surely some form of Linux should be able to run sound on it. I installed Feisty 7.04 on a Apple G3 which was only 300 mhz and the sound runs fine on that. I really would hate to spend $100 on Windows to make this machine work properly....

---

### Post by Midwest-Linux on 2007-08-10
[http://download.intel.com/design/chipsets/datashts/440MX-66DSPub.pdf](http://download.intel.com/design/chipsets/datashts/440MX-66DSPub.pdf)  This is the technical data on the chipsets. 

It looks like that soundcard is not supported by Ubuntu, Kubuntu, DSL...except windows, I also tried out DSL and no sound either . So I guess the only option is to buy a modern soundcard and hope that solves  the problem.

---

### Post by Midwest-Linux on 2007-08-14
Just a update...I just added a soundcard to the PCI slot and it worked,... however this still did not resolve the problem of why cannot use the LSA soundcard that is already in the computer. Also just like the other installs I did of Feisty, I can listen streaming audio through the MOVIE PLAYER. 

Rhythum Box does not work when one clicks on the listen link, neither does MMX. In movie player one must manually type in the listen link in the file section of movie player...then one can listen to their stream. I could not type in the link in Rhythum Box or MMX...but movie player works....for listening to streaming online audio...I am sure there is just a matter of configuring and some file associations and such...I haven't had much time to mess with it. make sure you download the all the G codecs.

Still have the ACPI issue, but thats just a minor issue that its not worth spending time tweaking for now. The computer again is the IBM 300GL  400 Mhz   192 MB Ram  10 Gig HD. Its built solid, and it was a used in educational fields and government. I have seen these on e-Bay from 99 cents to $30, its worth the money and a fine candidate for Feisty 7.04. Just use at least 192 MB Ram, Itried 512 MB on the same identical machine running windows and there were "issues"...so I backed down to 384 MB on the other machine. (I have four of these bought at that 127 sale)

When you add ram you have to update the installation...but you just click through the set up menu...I'll try to do a pictorial on the setup menu....I think its important that it is covered at some point. That setup menu was not IBM's strongest concept...

 Remember to buy a PCI sound card to get the sound. Once you install the PCI card that annoying
slash through the speaker will disappear.  Did I mention it comes with a LSA built in sound card. I think in the LSA and IRQ setups one might access it...like I said it ran fine in Windows 98 but not in linux...its just one of those odd things with this computer...

And get to know the set up menu F1 or Ctrl S ....You have to change the start up sequence in these to boot from the disc...oh yes and be sure to use the alternate text installer for Feisty 7.04. This computer is a large desktop, there is a good amount of room inside to work in and around the motherboard. The hard drive swings up on this machine, there are two screws which hold the CD-ROM and the Hard Drive on a swing pivot cradle. Unscrew the two screws, pull and swing up the cradle and the HD is located underneath for fairly quick access. This has to be the easiest computer (other than the Apple G3) to open and access the inside. Two snaps in the back and it slides forward.

---

