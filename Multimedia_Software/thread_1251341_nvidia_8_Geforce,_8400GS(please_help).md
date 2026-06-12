---
title: "nvidia 8 Geforce, 8400GS(please help)"
date: 2009-08-27
forum: Multimedia Software
---

### Post by scion xd on 2009-08-27
I bought a a new video card and every time i put it in it will not log in the computer.

sorry for my English. NOT a native speaker.

---

### Post by beastrace91 on 2009-08-27
Could you try to explain the issue a bit more? Also did you have a different graphics card in the system previously?

~Jeff

---

### Post by scion xd on 2009-08-27
I have Integrated with up to 128 MB allocated video memory.

i tried to put in a bigger better card but it just would not load.
  computer was trying to find hardwere but it could not.

---

### Post by beastrace91 on 2009-08-27
Does the system even get to the grub/ubuntu screen or is it stopping before this? (If it is stopping before this then it is a hardware issue.)

~Jeff

---

### Post by scion xd on 2009-08-27
Its stops on Ubuntu logo. and the progress bar is 1\6 way finished.

---

### Post by scion xd on 2009-08-27
should i do something before i put in the video card.
 like may be install a appropriate driver driver or configure some thing.

---

### Post by scion xd on 2009-08-27
Or should i just Partition the Hard drive and install xp and figure out if its the Ubuntu or the Video Card.

---

### Post by inobe on 2009-08-27
put in the card' boot the computer.

when you see the grub prompt hit escape.

choose recovery mode.

choose xfix, run it and reboot.

if that doesn't work repeat the same except this time choose command line.

type this in and hit enter

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

when it's done type

```
sudo reboot
```

edit: my bad' it's not command line' it's root shell.

---

### Post by inobe on 2009-08-27
note: make sure the monitor is plugged into the new card.

be sure the new card is seated properly.

check to make sure the card doesn't require additional power with a molex plug.

---

### Post by scion xd on 2009-08-27
How do i get to root shell

---

### Post by inobe on 2009-08-27
the same way explained above' this time select "drop to root shell" and not xfix.

---

### Post by beastrace91 on 2009-08-27
> **scion xd said:**
> How do i get to root shell

When grub comes up hit escape and select recovery mode and then root terminal.

~Jeff

---

### Post by scion xd on 2009-08-27
sorry man but it dos not go into recovery mode. so i cannot do xfix or get into root terminal with the czrd installed.

---

### Post by inobe on 2009-08-27
> **inobe said:**
> note: make sure the monitor is plugged into the new card.

be sure the new card is seated properly.

check to make sure the card doesn't require additional power with a molex plug.

did you follow this advice above ?

---

### Post by scion xd on 2009-08-27
Yes  I checked, no power supply needed and yes i did put it in there the right way.

---

### Post by inobe on 2009-08-27
the grub screen will be very quick' only like two seconds to hit escape !

are you sure you didn't miss it ?

---

### Post by scion xd on 2009-08-28
Yeah i did not miss it, its 3 seconds, and i went to my latest kernal( recovery mode).
And i also tried with other versions of kernal. does not work. 

Right now im partitioning my hard drive to install XP to see if my video card is ok.
I know i bought it Brand New but Stuff happens.

ohh Yeah after i do the Recovey mode there whole bunch of numbers with words and Error.

---

### Post by scion xd on 2009-08-28
I did more research and found some people with same card and HP computer, they have the same problem.

---

### Post by gradinaruvasile on 2009-08-28
> **scion xd said:**
> Yeah i did not miss it, its 3 seconds, and i went to my latest kernal( recovery mode).
And i also tried with other versions of kernal. does not work. 
.

What happens ? U should get a login prompt in text mode only.

---

### Post by scion xd on 2009-08-28
I know what you are talking about. there whould be  a blue text with gray box with four or five options, but it does not go there at all.

i tried with out the video card. to see what r u lookinf for and i did find Root terminal and Xfix.  so i know im doing it right.

---

### Post by scion xd on 2009-08-28
would it matter if i have only 250W power supply. On the Box of the Video Card i need 350W power supply.

---

### Post by richlowe101 on 2009-08-28
Yeah you need to get a better PSU. 250W is very small.

---

### Post by scion xd on 2009-08-28
so you think because of the Power supply im having a problem with video card. 

if so them ill buy a 400w just to be safe.

---

### Post by toddr on 2009-08-28
Weak power supplies can do funny things to your system.

---

### Post by inobe on 2009-08-28
things to keep in mind.......

some computers with agp slots only have 4X's capability !

your card may only support agp 8X's....

older fx cards were capable of both 4x's/ 8x's

what brand model is this card ?

we need the model of your computer to determine that, if you already released the model to us' my mistake.

---

### Post by scion xd on 2009-08-28
**the Video Card: **
EVGA Nvidia Geforce 8400 gs 512 MB ddr2 PCI 2.1compliant slot

[http://www.evga.com/products/moreInfo.asp?pn=512-P1-N724-LR&family=GeForce%208%20Series%20Family](http://www.evga.com/products/moreInfo.asp?pn=512-P1-N724-LR&family=GeForce%208%20Series%20Family) 

**Computer:**
HP Pavillion a1257c 4gig of Ram, Pentium4 630 (P) HT 3.0    GHz

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00497088&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00497088&dlc=en) 

**MotherBoard: **

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00361570&lc=en&dlc=en&cc=uk&lang=en&product=1149367](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00361570&lc=en&dlc=en&cc=uk&lang=en&product=1149367)

---

### Post by scion xd on 2009-08-28
Ohh the Only thing i upgraded my was Ram to 4 gig .

---

### Post by scion xd on 2009-08-28
This bothers Me (512 MB, 64 bit DDR2) I have a 32 bit OS. is this mean that this video card will not go with my computer.

---

### Post by inobe on 2009-08-28
no' that will not matter..

lets connect the card and go into the system bios and disable onboard video.

wait' no agp slot !

> Expansion slots   	

    * Three PCI
    * No AGP slot


---

### Post by inobe on 2009-08-28
that's a shock to me' i assumed this was and agp card ..

i would disable onboard video for sure !

---

### Post by scion xd on 2009-08-28
so there would be an option to disable the on board card in bios right.
thanks i will try to do this right now.

---

### Post by inobe on 2009-08-28
yes assuming it's not locked out by the manufacturer !


i feel that if you disable this' it will not get detected by ubuntu....


thus allowing only detecting the pci card.

this is the problem

edit: example

---

### Post by scion xd on 2009-08-28
I just checked.
yes it did it automatically PCI video as primary card.

when the ubuntu logo comes up, underneath the logo i have logs. well it stops and freezes when It Says LOADING HARDWARE DRIVERS.

So it could be a driver problem.

And yesterday i started a fresh start on my Ubuntu.

---

### Post by inobe on 2009-08-28
> **scion xd said:**
> I just checked.

And yesterday i started a fresh start on my Ubuntu.

was the pci card in when you started fresh ?

---

### Post by scion xd on 2009-08-28
I did it with a new card. and still it would not do it.

---

### Post by inobe on 2009-08-28
during the install' if not mistaken you should be able to choose save graphics mode.

if there was a way to get in to recovery and run that command we can fix this.

---

### Post by scion xd on 2009-08-28
Hmm, do you know the comand code. ill try it tonight or some thing.

---

### Post by inobe on 2009-08-28
it's more like this

---

### Post by scion xd on 2009-08-28
thank you i will try that tonight.

---

### Post by scion xd on 2009-08-28
BUt first i will try to buy a bigger Power Supply and exchange for a new video card if possible.

---

### Post by inobe on 2009-08-28
if you think something is wrong with the card' do that.

a power supply is a great choice as it may be part of the problem.


i used these type cards before with less wattage and they worked' though it's not recommended.

---

### Post by scion xd on 2009-09-08
Im Back, 

well i installed windows to see if i have a bad video card, and found out it works perfect with windows.

 so im still trying to figure out why is wrong with my Ubuntu, why its stops on the Loading the drivers.

Do any of you think i should install driver before putting in the card?

---

### Post by ticket on 2009-10-07
I'm having problems with this 8400GS PCI card too - see:

[http://ubuntuforums.org/showthread.php?t=1260508](http://ubuntuforums.org/showthread.php?t=1260508)

I could get it to work on a Dell Dimension XPS Windows XP machine, but not on an older Ubuntu Dell Precision 340.  I have a 400W PSU.

---

