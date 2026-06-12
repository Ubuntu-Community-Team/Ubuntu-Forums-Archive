---
title: "use PCI Express graphics slot for dvb-card?"
date: 2011-06-09
forum: Mythbuntu
---

### Post by mikulator on 2011-06-09
Hi!

My Backend needs are growing and I thought if I could take out my graphic card and use the "PCI Express x16 graphics" slot for a 4th dvb-card. Making the server headless?

Cheers
Mik

---

### Post by ian dobson on 2011-06-09
Hi,

Firstly you'll need to find a PCI-Express dvb card that's supported by Linux, then in might/should work (A PCI-Express 16 slot should be compatible with a PCI-Express 1,4,8x but should is the correct word).

Secondly quite afew motherboards won't boot if no graphic card is installed, just like the wunderfull old BIOS error message:-

Keyboard missing, press F1 to continue

Regards
Ian Dobson

---

### Post by mikulator on 2011-06-14
Well the last one is easy to test :D

But the "should" work is a bit more... expensive to test

---

### Post by porker on 2011-06-15
> **mikulator said:**
> Well the last one is easy to test :D

But the "should" work is a bit more... expensive to test

Not really, just move one of the cards you already have into the 16x slot and see if it works.

If it does just buy another the same as you already know it works in Linux :)

---

### Post by ian dobson on 2011-06-15
Hi,

What PCI-Express tuner card do you what to use? Is it Linux compatible? I must admit I don't know of any ;)

Regards
Ian Dobson

---

### Post by pu15e on 2011-06-15
Hi Ian,

  Perhaps I've misunderstood your question, but we use a Hauppauge HVR-2200 (AU version of the 2250) which is PCI/E ;-)

Cheers,
 Mattt.

---

### Post by ian dobson on 2011-06-15
> **pu15e said:**
> Hi Ian,

  Perhaps I've misunderstood your question, but we use a Hauppauge HVR-2200 (AU version of the 2250) which is PCI/E ;-)

Cheers,
 Mattt.

Hi,

OK I don't know that the HVR-2200 was PCI-e. I've lernt something new.

Regards
Ian Dobson

---

### Post by mikulator on 2011-11-10
Sorry for the very long wait...

I have with no problems at all removed the graphic card so now the system is headless - which is kind of cool.

Unfortunaly I don't have any PCI Express cards seeing as the MOBO only has PCI slots. 

During my work on the system I have googled around for some hints to whether or not I can use the slot even though it was/is intended for a "distrete graphic card" - so the manual says.

my mobo is 6-7 years old and I was thinking of replacing it, but hay it does the job... so I guess I will just have to test it. [-o<

Does anyone have anything to add?

Cheers

PS the card I was considering is a **TeVii S480 Dual DVB-S2                    PCIe **which requires one free PCI Express X1 slot

---

### Post by Drenriza on 2011-11-10
A PCI card can go into a PCI-E slot and a PCI-E card can go into a PCI slot.

The only thing is the speed will decrease if you take a PCI-E into a PCI slot.
And i am not 100% sure the power input will be sufficient.

But the slot is backward & "forward" compatible.

---

### Post by mikulator on 2011-11-10
OK! :D

I did not know that!

I will test it later today!

---

### Post by mikulator on 2011-11-10
Ok I just took a quick look at a picture of the mobo... I cant see that a PCI card would be able to fit into the PCIe slot

The PCIe slot is placed a little further "back" compaired to the CPI slots

---

### Post by oobe-feisty on 2011-11-10
> **Drenriza said:**
> A PCI card can go into a PCI-E slot and a PCI-E card can go into a PCI slot.

The only thing is the speed will decrease if you take a PCI-E into a PCI slot.
And i am not 100% sure the power input will be sufficient.

But the slot is backward & "forward" compatible.

you forgot to add except not really at the end of each sentence

---

### Post by mikulator on 2011-11-10
> **oobe-feisty said:**
> you forgot to add except not really at the end of each sentence

Soooo what you'r sating is "do I feel lucky today?"

 Just to be clear. Because it does not seam to physically fit, I will not try inserting a PCI card into a PCIe slot

---

### Post by oobe-feisty on 2011-11-10
no Im saying he was wrong there is no way a regular PCI card will fit in a PCI-E slot or vice versa

---

### Post by mikulator on 2011-11-10
> **oobe-feisty said:**
> no Im saying he was wrong there is no way a regular PCI card will fit in a PCI-E slot or vice versa

OK Then I will not get my big hammer out of the toolbox

---

### Post by oobe-feisty on 2011-11-10
anyway another thing for you to consider is mythtv has a setting that is configured in the backend using mythtv-setup where you can record 2 channels at once with the same tuner as long as the channel is on the same multiplex this is only applicable to certain broadcasting networks though.

How many tuners do you have already?
How often do you end up with scheduling conflicts?

if the answer to the second one is all the time then I guess its worth looking for another tuner but I am not even certain if PCI-e tuners can be plugged into the PCI-E X16 slot designated for Graphics.

---

### Post by mikulator on 2011-11-10
> **oobe-feisty said:**
> How many tuners do you have already?
How often do you end up with scheduling conflicts?

if the answer to the second one is all the time then I guess its worth looking for another tuner but I am not even certain if PCI-e tuners can be plugged into the PCI-E X16 slot designated for Graphics.

First to answer your questions:
1) I have 3 tuner cards: 1xdvb-t and 2xdvb-s2
2) well seeing as most of the family's favorite tv shows are on sat channels I do run into conflicts. my kids most often watch live-tv and absolutely hate changing source when they can't change channel. 2 more tuners will solve this... and here is where the Tevii PCIe card comes into play - it is a dual card \\:D/

And your final comment is in fact the purpose of my thread... I have googled for a long time and found no solid info on:
1) is my PCIe slot on my mobo able to do anything but graphics - I think it is a matter of trial and error here because it is a BIOS thing
2) is it possible to put a PCI Express device into a PCI Express x16 slot - this I am fairly certain of

Cheers

---

### Post by tester100 on 2011-11-10
> **mikulator said:**
> First to answer your questions:
1) I have 3 tuner cards: 1xdvb-t and 2xdvb-s2
2) well seeing as most of the family's favorite tv shows are on sat channels I do run into conflicts. my kids most often watch live-tv and absolutely hate changing source when they can't change channel. 2 more tuners will solve this... and here is where the Tevii PCIe card comes into play - it is a dual card \\:D/

And your final comment is in fact the purpose of my thread... I have googled for a long time and found no solid info on:
1) is my PCIe slot on my mobo able to do anything but graphics - I think it is a matter of trial and error here because it is a BIOS thing
2) is it possible to put a PCI Express device into a PCI Express x16 slot - this I am fairly certain of

Cheers




Whowwwwww finally something interesting enough


so let me ask u a few questions maybe i can get rid off some doubts i have

1-which system are u using mythtv in order to stream all 4 DVB cards ?

2-are u using it for PAL or NTSC ?

3- Which PCI sat card model are u using for the DVB-S and S2 streams ?

4- How does mythuntu behaves with all the 4 cards ?

5- Are u using a HDMI motherboard with HDTV graphic card onboard or using extra slot for Graphic card ?



I am building a new HTPC, but need to know a common sense good setup Hardware in order to make it work properly


So far i bought jut the HTPC case with iMon VDF display and control remote...

I am looking to buy a ATX motherboard with HDMI onboard graphics, intel duo or quadcore x64bits  , 8GB ram to manage lots of apps running same time and to handle the HDTV streams well enough.

So shall i go for Intel or AMD ?  Motherboard Gygabite or Asus ??? which ones have more support for the linux drivers?

sorry to hijack your post in a certain manner...

but if u just ansewer the PCI sat card tunner , that will be good enough as i would be insterested in getting a sort of plug n play tunner card for the DVBS and DVBS2 sat streams out the box thing to work good enough with MythTV.

cheers
tester100

---

### Post by mikulator on 2011-11-11
> **tester100 said:**
> Whowwwwww finally something interesting enough


sorry to hijack your post in a certain manner...

but if u just ansewer the PCI sat card tunner , that will be good enough as i would be insterested in getting a sort of plug n play tunner card for the DVBS and DVBS2 sat streams out the box thing to work good enough with MythTV.

cheers
tester100


Well first off you are hijacking... and when you start to run into trouble/issues or just have questions hijacked threads are a pain to filter out;)

But to answer your questions with a 'one-liner' Before you choose to buy any piece of new hardware make sure these 3 sites in some way support or approve
a) this forum
b) [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/) 
c) [http://www.mythtv.org/wiki/](http://www.mythtv.org/wiki/).

I currently have Technotrend tuners 2Xdvb-s2 and 1xdvb-t. I am not happy with the dvb-s2 tuners because they seem slow in tuning and HD does not work. I have read nice things about the Tevii card.

---

### Post by Drenriza on 2011-11-11
I will quote myself on this

> **Drenriza said:**
> A PCI card can go into a PCI-E slot and a PCI-E card can go into a PCI slot.

The only thing is the speed will decrease if you take a PCI-E into a PCI slot.
And i am not 100% sure the power input will be sufficient.

But the slot is backward & "forward" compatible.

A PCI-E 1x card can go into a PCI-E >1x (higher then 1x)
And a PCI-E 16x 8x 4x can go into a PCI-E 1x

The only thing is the speed will decrease if you take a PCI-E 16x into a 8x 4x or 1x slot.
And i am not 100% sure the power input will be sufficient.

But the slot is backward & "forward" compatible.
PCI-E -> PCI-E
PCI-E <- PCI-E

So besides from a small mistake that oobe-feisty poorly explained over two posts with no explanation. Then we are all good.
> you forgot to add except not really at the end of each sentence
> no Im saying he was wrong there is no way a regular PCI card will fit in a PCI-E slot or vice versa

---

### Post by mikulator on 2011-11-11
> **Drenriza said:**
> 
But the slot is backward & "forward" compatible.
PCI-E -> PCI-E
PCI-E <- PCI-E


OK, but this was just a partial answer to my question. So in summery

1) PCI card cannot not go into a PCI-E slot
2) Any PCI-E card should be anble to go into any PCI-E slot
3) Still no idea if my specific MOBO will support a non graphic PCI-E card in the PCI-E 16x slot - but in theory it should work?

Would you then advice me to test?

Cheers

---

### Post by mikulator on 2011-11-25
Well got my pci express card in and it is - ehm - it is sort of recognized.

I get the following from dmesg
```
vgaard: this pci device is not a vga device 
```

nothing else can be found

---

### Post by nickrout on 2011-11-25
Are there any options in your bios in relation to what goes in that slot?

---

### Post by mikulator on 2011-11-25
well not really

The only option that is close to what goes into the slot is a setting called** Primary Video Adapter **which either can be set to PCI or PCI Express

---

### Post by nickrout on 2011-11-25
Is there an onboard video device? If there isn't, many motherboards require a video card to boot.

---

### Post by mikulator on 2011-11-25
well it boot fine without a graphics card inserted and I have managed to make it headless - booting into vnc.

I can of course not enter into the BIOS without the card.

---

### Post by nickrout on 2011-11-25
> **mikulator said:**
> Well got my pci express card in and it is - ehm - it is sort of recognized.

I get the following from dmesg
```
vgaard: this pci device is not a vga device 
```

nothing else can be found

What do you mean "nothing else can be found"?

What does lspci tell you?
What is the card?

---

### Post by mikulator on 2011-11-25
I cannot find anything that allows me to setup the PCI express slot. But then again I am not sure I know what I am looking for.

lspci gives me:
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:03.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
03:04.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
03:05.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
```

the card is a dvb-s2 card

---

### Post by nickrout on 2011-11-26
there are at least 3 tuner cards there, is it one of them?

---

### Post by mikulator on 2011-11-26
The three you see are PCI cards that are also in the server.

I have added a PCI Express Card and it is a dobble dvb-s2 tuner.

---

### Post by nickrout on 2011-11-26
I think you need to consult your motherboard manual, maybe for some reason the pcie slot will only work with a graphics card.

And of course make sure the card is seated properly.

---

### Post by mikulator on 2011-11-27
Well, unfortunatly the manual is very limited in its info.

Thanx for you effort... I guess it's time to spend som money on a new MOBO

---

### Post by mikulator on 2011-11-28
I will try to summerize again.

lspci gives me no direct infor on the card insterted into the pci express slot.

dmesg tell me that vgaard had expected a vga device

BIOS give me no option to control what goes into the PCI slots all though I have an option to select what type of card me primary video adapter is (PCI or PCI Express)

I am on the latest BIOS from HP seeing it is a special HP/ASUS mobo I cannot - from what I understand - flash with anything else but HP BIOS.

So what know :confused: is it realy time for a new mobo/cpu?

---

### Post by nickrout on 2011-11-28
> **mikulator said:**
> I will try to summerize again.

lspci gives me no direct infor on the card insterted into the pci express slot.

dmesg tell me that vgaard had expected a vga device

BIOS give me no option to control what goes into the PCI slots all though I have an option to select what type of card me primary video adapter is (PCI or PCI Express)

I am on the latest BIOS from HP seeing it is a special HP/ASUS mobo I cannot - from what I understand - flash with anything else but HP BIOS.

So what know :confused: is it realy time for a new mobo/cpu?

I have never heard of vgaard. 

Are you sure the card works at all? Have you tried it in another computer? 

Do you have enough power supply grunt to run that many cards? You already have 3 pci cards, plus we don't know what else. Try taking out the pci cards and trying again.

Have you googled for info on your motherboard and what the PCIe slot can or can't be used for?

Have you ensured that the card is seated properly?

Have you tried to manually probe the module for the card (you haven't told us what it is).

---

### Post by mikulator on 2011-11-28
Thanks for all the replies - great support :)

The card is a Tevii s480 dual 

I would suspect it to work seeing as the server works with the other cards + nvidia GeForce 8500 GT card (PCI Express x16)

Besides the 3 x PCI cards and 1 x PCI Express. I have 2 x 500 GB HD - that it

I have not tried to probe it manually - never thought that was possible. I will try and get back to you.

Again Cheers!

---

### Post by nickrout on 2011-11-28
> **mikulator said:**
> Thanks for all the replies - great support :)

The card is a Tevii s480 dual  Now telling us what the card is really helps, because you see when you google it you get this page:

[http://linuxtv.org/wiki/index.php/TeVii_S480](http://linuxtv.org/wiki/index.php/TeVii_S480)

what does lsusb tell you?

> 

I would suspect it to work seeing as the server works with the other cards + nvidia GeForce 8500 GT card (PCI Express x16)

Besides the 3 x PCI cards and 1 x PCI Express.What a strange assumption>  I have 2 x 500 GB HD - that it

I have not tried to probe it manually - never thought that was possible. I will try and get back to you.

Again Cheers!

---

### Post by mikulator on 2011-11-28
I have been working on the problem based on what's on the page from tvlinux.org and only bought the card because it was specifically noted on that site.

lsusb shows nothing but root hub...

I am no super user in linux, but in reference to > What a strange assumption I was trying to answer the question - in regards to power - to the best of my ability and I thought if I replaced my graphics card with this card that it might work - hence the thread. 

This was naive of me - I guess?

I am on kernel 2.6.32 and know that the card is natively supported from 2.6.39, but was expecting it to show up (somewhere) if the assumption that I could use the PCI Express slot in my mobo.

But is this wrong?

---

### Post by nickrout on 2011-11-28
> **mikulator said:**
> I have been working on the problem based on what's on the page from tvlinux.org and only bought the card because it was specifically noted on that site.

lsusb shows nothing but root hub...

I am no super user in linux, but in reference to "What a strange assumption" I was trying to answer the question - in regards to power - to the best of my ability and I thought if I replaced my graphics card with this card that it might work - hence the thread. 

your answer led me to think you assumed that just because other DVB cards worked in linux, a different one would.> 

This was naive of me - I guess?the assumption that adding one extra card will still leave enough power is perhaps naive, at some point the camel's back breaks, maybe you are there. Have you tried my other suggestions? It wouldn't be the first time a brand new card was DOA, or didn't work in combination with other cards for some strange hardware reason.> 

I am on kernel 2.6.32 and know that the card is natively supported from 2.6.39, but was expecting it to show up (somewhere) if the assumption that I could use the PCI Express slot in my mobo.

But is this wrong?

It should still show up in lspci, although likely with some sort of misleading description.

---

### Post by mikulator on 2011-11-29
I done the following 
 - confirmed the card is properly seated in the slot
 - removed other PCI cards without any change in system logs

Googling info on my board gave me no info on weather or not the PCI Express slot can be used for anything but the graphic card. It was because of the lack of information I started this thread.

Of course the card could be DOA, but I would suspect that dmesg would not have given the error twice (because it is a dual card)
```
vgaard: this pci device is not a vga device 
```

My nexted step will be to try the card in another system but with a newer kernel 2.6.39 seeing as the drivers are natively installed in the kernel. This will tell me if the card is working

---

### Post by mikulator on 2011-12-01
Ok a little more testing has been done and strangly enough the error/warning ```
vgaard
``` is not affected by the dvb card being removed. So now I am actually back to finding out if the card is working or can be registered by the system.

lspci and lsusb do not register any hardware changes becuase of my inserting or removing the card.

This I suspect is a bad sign, but I unfortunatly know to little about what level these 2 utilities work.

---

### Post by nickrout on 2011-12-01
What happened when you tried it in another machine or with a newer kernel.

---

### Post by mikulator on 2011-12-07
I have not gotten to that part... first I need to find a machine to use

But I have compaired dmesg logs from machine with and without the card and unfortunatly no difference. I am worried that the PCI Express slot is some how wired to only support graphics.

It could a) be that I have "broken the camels back" and have no more power for the card, b) the card is DOA or c) the BIOS does not support anything else in the slot

---

### Post by mikulator on 2012-02-01
Well unfortunatly... the card works fine in another mobo.

I would therefore have to conclude that some motherboards (from at least before 2004) do not support the use of anything but Graphic Cards in their PCI Express slots. This can be a BIOS issue which I cannot rule out.

There are not garanties that it won't, but I would highly daubt it.

---

### Post by ian dobson on 2012-02-01
Hi,

Are you sure it's a PCI-e x16 slot and not a PEG. PEG slots only support Graphic cards/The BIOS doesn't initalise the slot for PCI-express cards.

I found this the hard way with a PCI-express analog input card in the company.

Regards
Ian Dobson

---

### Post by mikulator on 2012-02-02
Well I am almost sure because the manual, spec. list, etc. state:
> PCI Express x16 graphics
And therefore my thread.

I have therefore gotten a newer board and here they state the same but in the BIOS I can specify whether or not there is a graphics card in the slot.

---

### Post by nickrout on 2012-02-02
> **mikulator said:**
> Well I am almost sure because the manual, spec. list, etc. state:

And therefore my thread.

I have therefore gotten a newer board and here they state the same but in the BIOS I can specify whether or not there is a graphics card in the slot.

Have you tried updating the bios in the first board?

---

### Post by mikulator on 2012-02-03
Yep, but no luck here - it is a special ASUS board made for HP.

Cheers

---

