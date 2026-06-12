---
title: "Tuner card not working in MythBuntu 9.10 - driver issue?"
date: 2009-11-26
forum: Mythbuntu
---

### Post by GeorgeBigfoot on 2009-11-26
Hi Guys,

I'm new to Myth and have just built my first mythbox, although I have been using Ubuntu one one computer at home for some time.

PC Specs:
Core 2 Duo 2.9
4 GB DDRII
 GeForce8400GS
320GB HDD (with 1TB to add once I get the OS working)
2 * Leadtek DTV1000S (product site [here]("http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=382&check=f") )

Onto this hardware I installed Mythbuntu 9.10 but I can't get the tuners to register correctly into the backend. At first I thought it was just me not understanding but running some queries suggests to me that the drivers are not loading correctly

Diagnostics from Terminal:

kernel:
2.6.31-15-generic

lspci relevent output
04:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
04:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

sudo lspci -vnn relevent output
(if I didnt sudo, got an access denied for Capabilities)

04:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
    Subsystem: LeadTek Research Inc. Device [107d:6655]
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at e9100000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

04:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
    Subsystem: LeadTek Research Inc. Device [107d:6655]
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at e9101000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

dmesg relevent output
[    6.547492] Linux video capture interface: v2.00
[    6.740119] saa7130/34: v4l2 driver version 0.2.15 loaded
[    6.740194]   alloc irq_desc for 20 on node 0
[    6.740196]   alloc kstat_irqs on node 0
[    6.740202] saa7134 0000:04:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.740208] saa7130[0]: found at 0000:04:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xe9100000
[    6.740214] saa7130[0]: subsystem: 107d:6655, board: UNKNOWN/GENERIC [card=0,autodetected]
[    6.740243] saa7130[0]: board init: gpio is 2020000
[    6.740247] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.910015] saa7130[0]: i2c eeprom 00: 7d 10 55 66 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    6.910028] saa7130[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[    6.910039] saa7130[0]: i2c eeprom 20: 01 40 01 01 01 ff 01 03 08 ff 00 8a ff ff ff ff
[    6.910050] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910061] saa7130[0]: i2c eeprom 40: ff 35 00 c0 00 10 03 02 ff 04 ff ff ff ff ff ff
[    6.910072] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910083] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910094] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910105] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910116] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910127] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910138] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910149] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910160] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910171] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910182] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.910195] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[    6.910752] saa7130[0]: registered device video0 [v4l2]
[    6.910772] saa7130[0]: registered device vbi0
[    6.910881] saa7134 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.910887] saa7130[1]: found at 0000:04:01.0, rev: 1, irq: 19, latency: 32, mmio: 0xe9101000
[    6.910892] saa7130[1]: subsystem: 107d:6655, board: UNKNOWN/GENERIC [card=0,autodetected]
[    6.910920] saa7130[1]: board init: gpio is 2020000
[    6.910925] IRQ 19/saa7130[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.090014] saa7130[1]: i2c eeprom 00: 7d 10 55 66 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    7.090023] saa7130[1]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[    7.090031] saa7130[1]: i2c eeprom 20: 01 40 01 01 01 ff 01 03 08 ff 00 8a ff ff ff ff
[    7.090039] saa7130[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090047] saa7130[1]: i2c eeprom 40: ff 35 00 c0 00 10 03 02 ff 04 ff ff ff ff ff ff
[    7.090055] saa7130[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090062] saa7130[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090070] saa7130[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090078] saa7130[1]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090085] saa7130[1]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090093] saa7130[1]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090101] saa7130[1]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090108] saa7130[1]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090116] saa7130[1]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090124] saa7130[1]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090132] saa7130[1]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.090141] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[    7.090694] saa7130[1]: registered device video1 [v4l2]
[    7.090715] saa7130[1]: registered device vbi1
[    7.172349] saa7134 ALSA driver for DMA sound loaded
[    7.172353] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[    7.172355] saa7130[1]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[    7.276035] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.276071] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.613870] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5


My understanding (which is probably wrong!)

On the page listing card types supported ([this link]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134")) it lists the relevent driver on line 176 so this card should work

Several sites have told me to check under /usr/src/linux/Documentation/video4linux/ for a list of supported cards but there is only a makefile and a pl script (perl script I think?) - ie the folder exists, but there is no README or CARDLIST files

I've installed the drivers several times following instructions here: [http://linuxtv.org/cvs.php](http://linuxtv.org/cvs.php)

I've been fiddling with modprobe but not getting anywhere - probably cause I don't really understand what I am doing there. The fact that dmesg shows output that its auto-detected as an unknown/generic indicates that I need to modify something to manually specify the card type???

I have confirmed the aerial connection is OK. 

I've trawled through a lot of forums, sites etc, and they've taught me everything (I think!) I've learnt above but I'm really not sure where to go from here. Any suggestions/advice greatly appreciated.

Thanks

George

---

### Post by Caysho on 2009-11-26
According to the [DTV1000 S]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV1000_S") page on linuxtv.org, it is only just supported as of a few weeks ago - the links will take you to the [mkrufky dtv1000s changesets]("http://kernellabs.com/hg/~mkrufky/dtv1000s").
I suggest pulling the kernellabs.org hg codeset; however, the comments suggest that it should be in linuxtv.

When I compiled from linuxtv, there was a [problem with the firedtv module]("http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html"), which you must disable for the build to complete.  It is possible you are using the older module when doing modprobe because the linuxtv build did not complete.

---

### Post by thor-on-kveven on 2009-11-27
If it' of any help:

As Cashyo says the DTV 1000S wasn't supported in Linux until recently. I've used the card for a few months, I could make it work for me through the drivers from here: [http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)

That worked in a fashion up to and including 9.04. After installing 9.10 I haven't been able to make it work at all. I haven' had much time to do any further. 

On previous ubuntu versions I often had to redo the driver installation after upgrades, and the TV experience wasn't great, with picture/ sound poorly synchronised. If you have the chance I would consider changing TV card to one that is better supported, for stability at least.

Anyway, I'll be watching your thread for news, my thread on the subject here: [http://ubuntuforums.org/showthread.php?t=1337822&highlight=leadtek](http://ubuntuforums.org/showthread.php?t=1337822&highlight=leadtek)
though I think you've done your homework better.

Cheers

---

### Post by GeorgeBigfoot on 2009-11-27
Thanks for the info Caysho, I hadn't found/been to [http://kernellabs.com/hg/~mkrufky/dtv1000s/rev/43878f8dbfb0]("http://kernellabs.com/hg/%7Emkrufky/dtv1000s/rev/43878f8dbfb0") so i downloaded the bz2 file from there - unfortunately I couldn't get it to work. I'm going to document my steps below in case I'm doing something wrong (which is probably more likely than the system being wrong).

Downloaded the file and un-tarred it
From terminal cd into the un-tarred folder
sudo make config
hit Y/M on what I thought was appropriate (ie the prompts for saa7134 and what sounded like generic necessities) - this generated config file which I have attached at config.old.txt
sudo make install
Restart
no change in the output on lspci -vnn or dmesg - ie still generic/unknown card

Un-tarred the file again
cd into the un-tarred folder
sudo make config - config file attached as config.txt
hit Y/m on everything
sudo make install
Restart
Again, no change, cards still don't work

On both of the above attempts I checked/chagned that firedtv was disabled. On both times, there was no errors given back to me and they appeared to install correctly.

A colleague from work told me these cards would work, he sent me the drivers as well (a slightly older version than I've found on the web) and he has them working fine in his Myth box. He said they would take a little configuring but I didn't expect quite this much. I'm not sure which exact MythBuntu version he is running, but I'm sure its not 9.10. Can't check with him either cause he is overseas. 

I've attached a two other file - lspci contains the full output of "sudo lspci -vnn". dmesg.tar contains the full output of "dmesg" command in case I've inadvertently cut off relevant info in the post above. 

thor-on-kveven -> my work friend recommended the site you mentioned but I haven't had any joy with those drivers either. I tired those first but moved onto the LinuxTV site etc because they seem to be more up to date.

Any advice gratefully received

Cheers
George

---

### Post by thor-on-kveven on 2009-11-27
Too bad, was hoping you could make them work and tell me how ;-) 

The links from the page I gave you should actually take you to the same kernellabs page that Caysho gave you, I only realised after my previous post. The procedure you describe above is the same that worked for me on previous ubuntu versions but not anymore. I fear none of the established drivers will work with 9.10. I'm considering going back to the 8.04 Long Term Support version if I can't find a solution.

Good Luck

---

### Post by Caysho on 2009-12-03
The config file shows firedtv will not be compiled.

The following section from dmesg:
```
[    5.979557] saa7130/34: v4l2 driver version 0.2.15 loaded
[    5.981587]   alloc irq_desc for 20 on node 0
[    5.981590]   alloc kstat_irqs on node 0
[    5.981596] saa7134 0000:04:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.981602] saa7130[0]: found at 0000:04:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xe9100000
[    5.981608] saa7130[0]: subsystem: 107d:6655, board: UNKNOWN/GENERIC [card=0,autodetected]
[    5.981641] saa7130[0]: board init: gpio is 2020000
```
indicates it does not know the card number.

This [dmesg part]("http://osdir.com/ml/linux-media/2009-10/msg00788.html") has card=175.  I found that by more searching on the subsystem ID.

```
modinfo saa7130
```
will show the options you can give it, and you will need to pass the card number.  Where that is done I do not know.

---

### Post by GeorgeBigfoot on 2009-12-11
Thanks for the info Caysho and sorry for the delay in reply, I have been in rural Australia for a few days and WiFi spots are very far between!

I had figured out tha the generic part of the dmesg output was not a good sign, just couldn't figure a way around it. Given the comments in this thread and some other sites I've been trawling, I decided to roll back. Last night I installed MythBuntu 9.04. Downloaded latest drivers from: [http://kernellabs.com/hg/~mkrufky/dtv1000s]("http://kernellabs.com/hg/%7Emkrufky/dtv1000s") and installed them. Checking dmesg output after that shows that the unknown/generic line has now become correct (ie "card = 175, autodetected"). However, just below that, it showed that it was failing to load "dvb-fe-tda10048-1.0.fw". Did some digging around, found the file somewhere on the net, can't quite remember where, I think on the kernellabs site again, downloaded/extracted from tar and copied into /lib/firmware using a sudo cp. Restart. 

This sorted out the error with the firmware not loading, dmesg now shows it loading successfully. However, I can't find any channels in MythBuntu backend setup. It will scan but it says that no input was detected. I guess the next thing is to check that this antenna point works but i'm 99% certain it does... have to be sure I guess. 

I did wonder whether uploading a channels.conf file into the Myth backend would be helpful. That way, I could be certain that I was 'looking' in the right place, can then nail it down to not a Myth problem. Any ideas on where to find a channels.conf file for Brisbane, Australia????

As an interesting point for any others with similar problems, see this post:  [http://forums.whirlpool.net.au/forum-replies.cfm?t=942269](http://forums.whirlpool.net.au/forum-replies.cfm?t=942269) - its a long running thread and provides a lot of useful background info. However, the interesting part is the last few posts which suggest that support for these cards will be integrated into the next linux kernel. Last post was yesterday. 

Thanks for everyone continued help

Cheers

George

---

### Post by Caysho on 2009-12-11
Attach the new dmesg.
Also, what does mythtv detect the card as (backend setup) ?

The whirlpool thread indicates you might have to specify which tuner is being used for the module to work correctly, in addition to the card.

If the card is installed correctly, use scan to get the channels.conf file.  Sometimes multiple scans are needed for frequencies affected by signal strength problems or a digital cliff.
I suggest installing all the dvb-t packages available from the repositories.  I recall there being at least two different scan programmes.

I used MeTV to check the resulting file.  MeTV can also use the basic frequency file to go channel scanning.

If you are lucky, the channels.conf file referenced online might be current.

---

### Post by GeorgeBigfoot on 2009-12-12
new dmesg attached as tar (due to file size restriction). Has both dmesg output and lspci output. Working on your other suggestions now....

---

### Post by GeorgeBigfoot on 2009-12-12
Ok, so I've been fiddling with "scan" and "w_scan" options in Terminal but haven't gotten anywhere. Nothing I do gives me *any* output. I've attached a file showing several of the commands I've used and what Terminal comes back with. 

To be clear on the hardware setup I am using: I have 2 LeadTek Winfast DTV1000s. From my wall point I am using a new 4 way splitter - 2 of these are unused, 2 then go to the cards. To rule out the splitter or leads, I re-ran the scan options with the aerial going straight from the wall outlet to card1 and then straight from the wall outlet to card2. I know the lead from wall to PC is ok (it is normally on a tv in the back room). Exactly the same as the output I've attached below... nothing. I think my signal should be strong enough. I had the aerial re-done a year ago and there was a booster put on the aerial to provide for the 8 tv out ports in our house. Currently I am using 2 - 1 for the TV and one for the myth box so I dont' think a lack of signal is to blame. It is possible that this wall outlet is bad so 2morrow morning I will move the myth box to where I know there is a wall outlet that works and check with that. 

If again I get no results from this other wall outlet, I'm really not sure where to go to from here.... With a bit of guidance from forums and plenty of Googling I can usually at least have a go at something, but I'm just not sure what the fault is. If I had some idea on fault, I could at least be trying something, no idea on fault, I'm stumbling around in the dark....

Thanks

---

### Post by Caysho on 2009-12-12
dmesg shows both the dvb front ends are being detected correct (NXP TDA10048HN DVB-T).

Given it is not picking up any channels, you still need to deal with the tuner side.

I found this [walkthrough for saa7130]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux"), which can give you better hints than I can.

One of the suggestions from the link is getting the chip ID's from the card - actually looking at the physical board.

---

### Post by GeorgeBigfoot on 2009-12-12
so I've moved the computer to a location where I can plug it in an aerial outlet I know works - using the same lead that connects the TV that normally sits there. Ran w_scan and scan commands (as per the txt file I attached in my previous post) with exactly the same results - Ie nothing found. I have a single aerial cable so I ran each scan and then w_scan with it attached to one card, then re-ran with it attached to the other. I think this tells me conclusively that something is still wrong in the software side of things... I'll have a look at the link you provided Caysho and try their ideas.

Searching around last night I did find [this]("http://www.itee.uq.edu.au/%7Echrisp/Linux-DVB/channels.conf") -  a channels.conf file for brisbane, I'm not sure how up to date it is.... Up one directory (ie [this]("http://www.itee.uq.edu.au/%7Echrisp/Linux-DVB/")) has some quite interesting info for others with issues. 

Cheers

---

### Post by GeorgeBigfoot on 2009-12-13
I've been fiddling with the information from the link Caysho provided. The Kernel I am running is "2.6.28-17-generic". I pulled out the tuner cards to have a look at them. They have chips manufactured by "NXP" on them - one has SAA7130HL and the other TDA10048HN. I dug into /usr/src/linux-headers-2.6.28-17-generic/include/media and looked at the file "tuner.h". Browsing through the file I found a line that caught my attention... "#define TUNER_PHILIPS_TDA8290        54". Took me a while to figure out why 8290 was familiar but I eventually found it in my dmesg output

[    4.920512] Chip ID is not zero. It is not a TEA5767
[    4.920591] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[    4.956007] tda8290: no gate control were provided!

The above was repeated twice, one for each tuner. I then did a lsmod and it showed "tda8290 " as a running module. I know from dmesg output that it is identifying the card correctly (cause dmesg shows it ID'ing the card as card type 175) but from this I assumed that it may not be identifying the tuner correctly (from the comments on the link Caysho provided). Thus I issued the following "modprobe saa7134 card=175 tuner=54". Re -ran scan and w_scan from terminal without any luck.

Found another post on the net (link [here]("http://ubuntuforums.org/archive/index.php/t-41123.html")) suggesting that I also needed to include a "gbuffer" option and that I should actually put the above command (ie  "modprobe saa7134 card=175 tuner=54") inside /etc/mobprobe.d/ in a file called saa7134.conf. Created the file with contents: 

#WinFast DTV 1000s
options saa7134 card=175 tuner=54

Restart, rerun w_scan and scan - still nothing. Modify saa7134.conf to be: 

#WinFast DTV 1000s
options saa7134 card=175 tuner=54 gbuffers=4

Restart, rerun w_scan and scan - again nothing. I should note that before I run w_scan or scan I need to stop the myth backend using: "sudo /etc/init.d/mythtv-backend stop"

My location/creation of the conf file is based on the link Caysho provided above ([link]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux"))

So i am unsure if 
1. the saa7134.conf is in the right spot/has the correct options
2. if I am even mucking around with the right options...

Thanks for reading! :)

---

### Post by Caysho on 2009-12-14
To both questions, I do not know.

The kernel version you last posted is different from your original post, but given you are compiling from a kernellabs hg, I doubt that matters.

However, after all this effort, I suggest getting a card that works out of the box :)
Though you do seem very close to having it working.

---

### Post by GeorgeBigfoot on 2009-12-19
IT WORKS!!! :)

Sorry I haven't posted back for a few days, I found out I have an exam for a work related course and thats somewhat distracted me. The day I found out I had the exam coming up I managed to get it working (mostly) thanks to a friend. I have doco'd what I did, when I have time in 2/3 days after the exam, I post back what I did and what is/isn't working so anyone else with this type of issue can benefit....

Thanks for all your help

---

### Post by marrabld on 2010-01-02
Any chance you can post how you got it working.  I seem to be having the same problem.

---

### Post by GeorgeBigfoot on 2010-01-03
Sorry for the delay in posting back, I was crazy busy with an exam and then went away over Christmas/New years....

So, these are the steps I went through with my friend at work. At the time I had mythbuntu 9.04 installed and fully patched. We got it working on that distro, then figured we might as well see if we could make it work on mythbuntu 9.10. Again, we got it working so these steps should work on both releases.

# Straight install of Mythubuntu 9.10
# Patched it
# Downloaded drivers from [http://kernellabs.com/hg/~mkrufky/dtv1000s]("http://kernellabs.com/hg/%7Emkrufky/dtv1000s")
# Open up terminal and do the following (after of course cd into the directory you downloaded the above file to)

```
tar -xvzf dtv1000s-43878f8dbfb0.tar.gz
cd dtv1000s-43878f8dbfb0/
make
cd v4l
nano -w .config
```# Nano will open up (its a minimalist text editor) and you will need to scroll through and look for the line that says "CONFIG_DVB_FIREDTV=m" and change it to "CONFIG_DVB_FIREDTV=n" (ie change the m at the end to n).

# Back to terminal....

```
cd ..
make
sudo make install
```Each of the above steps may take up to 5 minutes, just be patient and watch the screen in case you get errors...

After this you should have the drivers installed. For me it still didn't work, if yours does, great!...For me, if you do a dmesg and scroll through it you will noticed a line that says something about "dvb-fe-tda10048-1.0.fw" failing to load. To fix this, I downloaded firmware.tar.gz from this link: [http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz](http://tw1965.myweb.hinet.net/Linux/firmware.tar.gz)

Back to terminal, cd to the directory when you downloaded it and:

```
tar -xvzf firmware.tar.gz
cd firmware/
sudo cp dvb-fe-tda10048-1.0.fw /lib/firmware
```I then did a restart just to tidy up and I was now working! :)

One note in case someone was really stupid like me, in mythtv backend, when in the capture card menu, be sure to choose the type of capture card as "dvb dtv capture card" - I didn't on one of my many attempts and it really had me scratching my head.

Using mythtv I did a scan and picked up all the channels in my area (Northside Brisbane, Australia) except Channels 9 and SBS - I got all the other digital channels but nothing from 9 or SBS. I could view these channels fine in the frontend. I then switched back to terminal: 

```
cd /usr/share/dvb/dvb-t$ scan -a0 -o zap au-Brisbane  > /tmp/channels.conf
```(you may need to install scan first, to do that in terminal: "sudo apt-get install dvb-utils"

This generates a channels.conf file in the tmp directory which you can then use to import into the myth backend. Once I had imported this in, all the channels show up in myth however, it still has intermittent problems with actually getting a lock onto SBS or channel 9 - sometimes it will, sometimes it won't... still gotta have a fiddle with that. The resulting problem is of course that you can't program anything to record in case it doesn't get a lock :(

I also used "Me TV" to double check - using Me TV I get onto any of the channels straight off, no problems... There is a post here: [http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=6#r105](http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=6#r105) and the a few of the posts below that describe the same problems and a solution, but I haven't had a chance to try it yet. 

I also got the remote that came with the card working without any config, doesn't work the best but it is kinda OK. I got these instructions off a website, I can't remember which one and I'm writing these from memory but Thanks to whichever person posted these! I have two dtv1000s's in my box so for me I also had to determine which card I am plugging the receiver for the remote into.

In terminal: 

```
cat /proc/bus/input/devices
```You are looking for something similar to: 

I: Bus=0001 Vendor=107d Product=6655 Version=0001
N: Name="saa7134 IR (Leadtek Winfast DTV"

There several lines under this as well (and for me this was repeated twice, once for each card). Specifically, you are looking for the line that for me said:

H: Handlers=kbd event5 

You need to note the number... IE in this case 5 (for me the other number was 7).

Then, again in terminal: 

```
sudo cat /dev/input/event7
```Above, I have put "event7" - I tried event5 first, didn't work, so I tried event7 and it worked. You can tell it works because after you have issued the above command, you get your remote and press random buttons... If it is working you will see random characters appearing on your screen. Control -C to exit when you have finished putting random stuff on the screen. In theory, if you now switch to mythtv frontend you should be able to do stuff on screen. For me, not all of the buttons work or do what the icon says they should, but the important stuff like up/down channel, up/down volume etc does. If this doesn't work, I have no ideas, something to do with LIRC I think. LIRC fiddling should also fix the buttons not working correctly but I haven't done this....

I have attached the channels.conf file that was generated from code I used above. This was generated about 20th December 2009, Brisbane Australia in case anyone wants it for reference. Renamed from channels.conf to channels.txt so it would attach, just rename it back if you need to import it into myth backend.

Thanks to everyone for their help and hopefully this helps others fix their problems

Cheers

George

---

### Post by marrabld on 2010-01-23
Thanks sooo much for taking the time to write out those steps nice and precisely.  It worked a treat for me.  I have been pulling my hair out for ages!!!!

I haven't tried the remote as I am using a wiimote through bluetooth.

Champion! thanks again.

note.  in your first few lines of code you say

```
tar -xvzf dtv1000s-43878f8dbfb0.tar.gz
cd dtv1000s-43878f8dbfb0/
make
cd v4l
nano -w .config
```

The ```
 make 
``` isn't really necessary if you are going to edit the .config file.  It just tries to build and fails.

---

### Post by GeorgeBigfoot on 2010-01-31
Cheers marrabld, I didn't really think when I was posting these up, I just went through terminal history and copy/pasted out the commands. I was just so happy to get it working!!! If someone had told me it was necessary to hop around the computer three times I would have done it :P

For anyone else following my 'fun' with Myth, I have now managed to get channels 9 and SBS to lock on. I spent a couple of hours this afternoon mucking around with various suggestions. This was mostly to do with the hierarchy in the channel tuning. 

I tried modifying the original channels.conf with suggestions from: [http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=6#r105](http://forums.whirlpool.net.au/forum-replies.cfm?t=942269&p=6#r105) and a couple of posts below it (ie change hierarchy from None to Auto) and then importing the channels file into the backend but that didn't help. Also used the suggestions from[ this thread]("http://ubuntuforums.org/showthread.php?t=1329178"), specifically [post 5]("http://ubuntuforums.org/showpost.php?p=8655809&postcount=5") - again it didn't solve the problem completely although I did seem to get a Lock more often than before. 

What eventually worked for me was to delete all my existing channels just re-import the channels.conf file (same one I attached to my previous post). The only change I can think of that I made was in the Backend. I went to channels editor -> edit transports and for each one in that screen I edited the Hierarchy to None - which actually goes against how I read the posts above!?

To delete all the channels -> Backend -> Channel Editor -> delete

To import the new file -> Backend -> channel Editor -> Channel Scan -> Change scan 'type' to Import Channels.conf. I also changed Desired Services to "All" so I would get radio as well. 

Cheers

George

---

### Post by Fr3ddY on 2010-03-10
GeorgeBigfoot Thanks You so much my DTV1000 s is now working Ubuntu 9.10 x64 

The CONFIG_DVB_FIREDTV m to n made the install work..Great Thanks Again :D

---

