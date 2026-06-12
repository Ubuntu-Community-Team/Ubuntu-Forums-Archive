---
title: "Dual \ Quad DVB-S2 Card"
date: 2012-09-19
forum: Mythbuntu
---

### Post by rooneybuk on 2012-09-19
Does any one know or a Dual \ Quad DVB-S2 Card which work out of the box or with very little issue.

---

### Post by AlecJ on 2012-09-26
I using a TBS 6981 DVB-S2 Dual, but the quad also works these are PCI-e cards, you do have to compile the drivers and install them but it no big deal.
And recompile and install after a new Linux header is installed after updates.

my machine is set to just download updates and not install automatic, the card will stop working if the header is updated without the new driver. so I do the updates manually then go find the latest driver here 

[HTML]http://www.tbsdtv.com/download/document/common/[/HTML]Choose the latest linux driver (highest number) make a note and change the lines below to suit the new file name,

it's [tbs-linux-drivers_v120827.zip]("http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v120827.zip") right now.

Change the line's in [COLOR=Red]red[/COLOR] italics to suit

```
mkdir driver
cd driver
wget http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v120[COLOR=Red]*827*[/COLOR].zip
unzip tbs-linux-drivers_v120[COLOR=Red]*827*[/COLOR].zip
tar xjvf linux-tbs-drivers.tar.bz2
cd linux-tbs-drivers
```Depending on your kernel version and if the kernel is x86 or x86_64 (check output of ‘uname -a’) do:

- for x86 kernel 3.x (x86 32 bit installations of kernel 3.x): ./v4l/tbs-x86_r3.sh
- for x86 kernel 2.6.x (x86 32 bit installations of kernel 2.6.x): ./v4l/tbs-x86.sh
- for any x86_64 kernel (x86 64 bit installations of Linux): ./v4l/tbs-x86_64.sh

May machine is 64bit so
```
sudo ./v4l/tbs-x86_64.sh
sudo make
sudo make install
```It takes quite a long time to do the make.
Reboot in order to load the newly installed driver.

Before you update to a later driver to suit an upgraded header remember to delete the folder ~/driver first before wget downloads the new driver in to the same folder as the old driver.

Its a fast card very good picture ( the HD from the BBC can take a few mins to lock after the card comes out of sleep mode, so be patient) and I get 2 tuners from each input, as long as the channels are on the same multiplex. it may do more but as I have 3 other cards supplying feeds from 2 quad LNB's.

---

### Post by rooneybuk on 2012-09-27
Thanks for you reply, 
 
I have ordered a TBS 6981 and may order a second at a later stage, also thanks for all the info on compliling and link.
 
also just a fyi i found octo(8) lnbs on amazon for only £14 which are a direct replacement for the standard sky dish ones :) bargin

---

### Post by AlecJ on 2012-09-27
Not a bad price, I use 2 quad LNB's , one looks at 28east Astra (Freesat) the other looks at 19east Astra to get RTL sports, free F1 just in German, both mounted on a bar on the LNB arm of a huge 90cm fixed dish. 
Well huge nowadays, in the old day's I had a 2M on a jager motorized mount and a host of analogue hacked description boxes, but I digress.

The other card I use is a TBS 8922 which is a single DVB-S2 but full PCI and uses the same drivers as the dual. 
Also 2 x Win TV DVB-S full PCI, old cards but supported in the kernel.

You have to set 2 sources up in the backend, 1 for non S2 cards and 1 for S2 cards (the same as the non but with 3 or so extra channels) and link the sources to the right cards. it locks up if you try to view an S2 channel with a non S2 card.
And another one for LNB's looking at different Satellites ect.

I'm hoping in time the TBS drivers will be in the Kernel removing all the fafing about.

---

### Post by rooneybuk on 2012-09-27
Hi

I'm a little confused on your setup, I currently have a Hauppauge WinTV NOVA-HD-S2 single tuner and I'm going to be adding the TBS 6981 once it arrives and the new octo LNB is a direct replacement on my existing sky mini dish, I assumed I would be able to setup 2 maybe 3 sources depending on how the new card is detected and including the Hauppauge to allow me to do watch 1 whilst recording 2 or even record 3 and not watch any does this sound right.

The reason for the octo LNB was to cover the following

Sky HD = 2
Generic Reciever = 1
Computer = 3
And a spare for future upgrades to the computer possible

---

### Post by AlecJ on 2012-09-27
Yes thats right, you can go to 6 inputs if you wish.

I guessing you have separate bits of equipment using the dish.

We just have a computer that does everything, 5 hardware tuners( so 10 inputs + ), all the music and 100's of ripped dvd's

An  octo LNB has 8 output cables, so you need 8 inputs for the cables to  attach too, 2 quad cards or 8 single cards or Sky box etc.

each  cable output is a fully fledged LNB voltage controlled polarization,  horizontal or vertical or left circular or right circular,,etc.

i.e  the card (or sky box) sends a voltage up the coax cable to swing the  coils in the feed horn (wave guide) that focuses the signal into the LNB  (low noise block down converter).

If you look at the channels  they have a frequency and a polarization H or V and are segregated into  groups on carriers called multiplexes.

each card or input from an  LNB can see all channels on the multiplex it's tuned too so you can  watch or record 2 or more channels at the same time from the single  hardware tuner, on MythTV.
The sky box can't do this, hence needing 2 LNB inputs

MythTV  can "share" the tuner across your network to another remote frontend or  record it, but if one front tries to change channel away from the tuned  multiplex, it fails back the original channel.
So the on the front  end you have to use the menu and change the input to another available  free LNB to change channel to another multiplex.
This is something you will find when you add the new card, so name the cards so you can identify them in the frontend menu.

My  remote laptop in the kitchen always chooses to use the same card as the  main backend/front end in the lounge, really annoying, have to use the  menu to choose 1 of the other cards every time, else i can't change  channel.

As i'm sure you know, there are many other Satellites in the sky, on the Clarke belt named after Arthur C.

by  mounting another LNB on a bar just offset from the main LNB it can  "squint" at another Satellites signal reflected by the dish and receive  the channels from that.

Your mini dish can also do this, but it  would be better to point the dish at 19East and squint at 28east as it  has the stronger signal.

I have 1 LNB squinting at 19East just to  get the German free to air sports for the formula one, but there are  loads of channels from 19 east.

You only need another source  (video source in the backend) if your cards are not the same, or looking  elsewhere in the sky, as your dish is only on 28East and your other  card is also S2 you only need 1 source. This you can name FreesatHD or  whatever then link it to all your input cards. so no need to scan, your  win tv card's channel list will be the same as if you were to scan with  the new card.

sorry for being so wordy and if you knew all that anyway.

---

