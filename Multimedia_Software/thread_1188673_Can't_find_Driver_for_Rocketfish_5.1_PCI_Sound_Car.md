---
title: "Can't find Driver for Rocketfish 5.1 PCI Sound Card"
date: 2009-06-15
forum: Multimedia Software
---

### Post by aaronsnell89 on 2009-06-15
I recently bought a rocketfish 5.1 PCI Sound Card Model RF-51SDCD and I haven't been able to find the driver. Could anyone help?

---

### Post by jerrrys on 2009-06-16
[http://talkback.zdnet.com/5208-9334-0.html?forumID=4&threadID=65484&messageID=1224715&start=0](http://talkback.zdnet.com/5208-9334-0.html?forumID=4&threadID=65484&messageID=1224715&start=0)

---

### Post by aaronsnell89 on 2009-06-16
Thanks, do you have any idea when the drivers will be available?

---

### Post by jerrrys on 2009-06-16
> **aaronsnell89 said:**
> Thanks, do you have any idea when the drivers will be available?

No I do not, probably better to contact rocketfish.

question

have you just tried to use it? maybe ubuntu generic drivers will kick in.

---

### Post by markbuntu on 2009-06-16
Run these commands from a terminal. They will tell you if ubuntu detects your card and loads the driver.

lspci

cat /proc/asound/cards

cat /proc/asound/modules

aplay -l

arecord -l

---

### Post by aaronsnell89 on 2009-06-20
I entered those commands and here's what came up:

trey@trey-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

trey@trey-desktop:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0xde00 irq 21

trey@trey-desktop:~$ cat /proc/asound/modules
 0 snd_ca0106

trey@trey-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

trey@trey-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've never been good with terminal (or DOS when I had windows) could someone help? and When I try to use the speakers all I get is static, I know the speakers are fine I just bought them and they worked on my friends laptop.

Anyway, do you know of a sound card that will work with ubuntu and costs less than $30? (I'm on a tight budget)

---

### Post by JoeyBad on 2009-07-10
Sorry

---

### Post by YFZero on 2009-09-11
> **JoeyBad said:**
> I figured out how to get mine to work. Works great. Paid $7 for new in the box. Rec0rds no different than a 24bit Creative Sound Blaster ;). Do you have the disk that they usually send? Lots of people claim that it causes 'Blue Plague', but there is a way to load the drivers without running the App. Email me if you still need help. [EMAIL="jumpnjoeyscores@hotmail.com"]jumpnjoeyscores@hotmail.com[/EMAIL].

Maybe you can enlighten us then?

---

### Post by ugmoe2000 on 2010-01-11
I bought one of the Bestbuy Rocketfish Cards the RF-51SDCD. It registered as using the snd_ca0106 driver under 'lsmod'. I couldn't get this guy to work... I've tried everything, using it under a live-cd it didn't "work out of the box" either. I think this one is headed back to Bestbuy tomorrow... I just bought a nice Creative Sound Blaster Audigy off e-bay... $15... I needed a card in a pinch and the Rocketfish was at cheap at Bestbuy-- it was worth a shot.

---

### Post by Phases on 2010-01-27
9.10

Thinkin' about this card - has anyone got it to work?

---

### Post by sports.car.guy on 2010-01-27
> **Phases said:**
> 9.10

Thinkin' about this card - has anyone got it to work?


It absolutely has no support for it under Linux. It is a total waste of money! Rocketfish even though they cloned an Audigy did not do it completely and also call it an X-Fi, at least they used to call it that.

Get a HT|Omega on new egg. They are fully supported from what I understand including hardware mixing and onboard AC3 encoding. I could be mistaken on that last part though. Creative cards like the real X-Fi's have the hardware to do on the fly AC3 encoding I believe as well, but it is not supported in Windows by  Creative or in Alsa.

---

### Post by Phases on 2010-01-28
> **sports.car.guy said:**
> It absolutely has no support for it under Linux. It is a total waste of money! Rocketfish even though they cloned an Audigy did not do it completely and also call it an X-Fi, at least they used to call it that.

Get a HT|Omega on new egg. They are fully supported from what I understand including hardware mixing and onboard AC3 encoding. I could be mistaken on that last part though. Creative cards like the real X-Fi's have the hardware to do on the fly AC3 encoding I believe as well, but it is not supported in Windows by  Creative or in Alsa.

I never saw this reply.. yet I subscribed?? Dern.  (Edit: Oops, there it is. :oops:)

Well, I bought the card, and you're right.

Today I updated [pulse and alsa]("http://ubuntuforums.org/showthread.php?p=8738567") and if I end up trying it again when I get home (assuming onboard sound still isn't what I want) and  it happens to work, I'll be sure to post here.

Thanks for the reply!

---

### Post by sports.car.guy on 2010-01-28
> **Phases said:**
> I never saw this reply.. yet I subscribed?? Dern.  (Edit: Oops, there it is. :oops:)

Well, I bought the card, and you're right.

Today I updated [pulse and alsa]("http://ubuntuforums.org/showthread.php?p=8738567") and if I end up trying it again when I get home (assuming onboard sound still isn't what I want) and  it happens to work, I'll be sure to post here.

Thanks for the reply!

Not a problem. I actually tried that card and returned it the same day after googling a bit and finding out it was a hunk of junk not supported under Linux.

---

### Post by mikemunsil on 2010-04-07
Rocketfish™ 5.1-Channel PCI Sound Card

And I just installed the card and it works out of the box on Ubuntu 9.10.  I did have to load the driver from the included CD before Windows 7 would recognize it. After that it worked fine.

I have Windows 7 and Ubuntu 9.10 installed on two separate drives. This is not a dual-boot from one hard drive. I currently go to BIOS to select the operating system to use.

---

### Post by SeraphProfeta on 2010-05-25
The problem is with alsa, several other's have used it. (Alsa being the generic Linux sound driver.) Download the latest one HERE: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Extract install all that jazz. Listen to music. 

My server Mobo is lacking an on-board audio port, figured I'd give it some audio so I could hook it up to my tv.

---

### Post by Budsandsuds on 2010-06-04
I had the same problem but for some reason it's working now.I have a dual boot system windows xp/ubuntu.I went onto windows and played something to make sure the card  worked.Then i rebooted into ubuntu and the i had sound.Is there any way to copy the settings.As a back up.Maybe i could post it too.I'm still really new to ubuntu so any help would be great.Thank you

---

### Post by ccreamer_22 on 2010-06-24
[FONT=Arial][SIZE=2]I have a rocketfish model RF-51SDCD. I am currently running 10.04 LTS with[/SIZE][/FONT] the latest version of alsa installed and it still does not work. All I get is static. I opened a ticket with rocketfish and this is what they said:

Hello XXXXX,
 
This is Brenda Camargo, part of the Rocketfish Customer Care Team. First of
all let me apologize for the delay of my answer, we are experiencing a higher
volume of e-mails than expected, I hope you can understand.
 
Regarding your question, let me tell you that our products only support
Windows and Mac OS X Operating System, but unfortunately they are not meant to
work with Linux. Therefore, we cannot provide you with a driver or settings to
built one to make the sound card compatible with your OS.
 
I am sorry I cannot give you the answer you were looking for, but if you have
any other question or concern, you can always send us an e-mail, and we will
respond as soon as possible. Or you can call our Rocketfish Customer support
line: 1800-620-2790, 7 days a week! 
For faster and better assistance you can provide the agent with your case
number: XXXXXXXXXX 
 
I hope you have a great day!
 
Brenda Camargo 
Rocketfish Customer Care Team.
[EMAIL="customerservice@rocketfishproducts.com"]customerservice@rocketfishproducts.com[/EMAIL]
                
I included their email address just in case anyone wanted to flame them. Anyways, I have the install disk with all the windows versions of the drivers. I work in IT and I have some experience with pearl scripting, but most of my scripting experience is in windows. Anyways, one of my buddies at work said that he used to know a guy who would create their own simple Linux drivers. I'd be willing to play around with it and pull most of the data out of the windows drivers so that we can get some kind of working solution out of this if some ubuntu guru would be so inclined. It would give me some valuable learning expirience too.

---

### Post by mab879 on 2011-03-24
...

---

### Post by dwwheeler on 2011-10-25
I'm running Ubuntu 10.04 with dual boot to Win7.  I have onboard sound that doesn't work right so gave this card a try 'cuz it was cheap.   I first booted to Win7 and it worked fine after I installed the drivers.  Then I booted to Ubuntu and fired up Amarok.  No sound.  Then I went to System/Preferences/Sound.  On the Output tab I saw the onboard and the rocketfish card (listed as CA0106 Soundblaster Analog Stereo).  I changed the selected device from the onboard sound to the rocketfish and.....viola!  Let there be sound!!!!!

---

### Post by chiefrocka on 2012-09-18
Just upgraded to Ubuntu 12.04 and the rocketfish sound card is detected as "CA0106 SoundBlaster", but whenever audio is played on the system, only white noise is played through the speakers.

I'm guessing the default "CA0106 SoundBlaster" driver is not compatible with this model of sound card.

Also, I'm testing using analog output, *not* the S/PDIF.

I also noticed that the left and right speakers are reversed. When I set the balance to left speaker, white noise comes out the right speaker, and vice versa. Probably due to driver incompatibility.

Anyone know where to look to see how Ubuntu figures out which driver to use based on sound card model?

For ref:
RocketFish RF-51SDCD ([http://www.rocketfishproducts.com/products/computer-accessories/RF-51SDCD.html](http://www.rocketfishproducts.com/products/computer-accessories/RF-51SDCD.html))
Ubuntu 12.04 (64bit)

---

