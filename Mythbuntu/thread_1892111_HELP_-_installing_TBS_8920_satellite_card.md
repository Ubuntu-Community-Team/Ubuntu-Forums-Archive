---
title: "HELP - installing TBS 8920 satellite card"
date: 2011-12-07
forum: Mythbuntu
---

### Post by langner on 2011-12-07
Hi All,

I'm trying to install a satellite card TBD 8920 PCI card but I'm very new at this. 

I need some help making the installer and well installing it. I have downloaded the latest drivers from the website. 
[http://www.tbsdtv.com/english/Download.html](http://www.tbsdtv.com/english/Download.html)
direct link to driver [http://www.tbsdtv.com/download/common/linux-tbs-sources_111118.zip](http://www.tbsdtv.com/download/common/linux-tbs-sources_111118.zip)

I have the basic install of Mythbuntu Front/backend (latest - up to date)

I'll need talking though it as I don't know any code

Thanks in advance

Matthew

---

### Post by nickrout on 2011-12-08
> **langner said:**
> Hi All,

I'm trying to install a satellite card TBD 8920 PCI card but I'm very new at this. 

I need some help making the installer and well installing it. I have downloaded the latest drivers from the website. 
[http://www.tbsdtv.com/english/Download.html](http://www.tbsdtv.com/english/Download.html)
direct link to driver [http://www.tbsdtv.com/download/common/linux-tbs-sources_111118.zip](http://www.tbsdtv.com/download/common/linux-tbs-sources_111118.zip)

I have the basic install of Mythbuntu Front/backend (latest - up to date)

I'll need talking though it as I don't know any code

Thanks in advance

Matthew

There is a folder of readme files in the driver zip file. Have you read them?

---

### Post by langner on 2011-12-08
Hi, 

Thanks for getting back to me. 

I have read the ReadMe file, I believe the correct one, but I must be doing some thing wrong. 

Can you tell if the file will install, if so, I'm definitely doing some thing wrong. I'm new to this and I'm no coder. So some things I just don't know, so please be kind and talk me though it

Thanks

---

### Post by nickrout on 2011-12-08
symptoms?

which read me are you following and where does it fail?

---

### Post by langner on 2011-12-09
I'll talk you though what I'm doing and what I see on screen.

Downloaded the zip file from the main website. 

Unziped it on the desktop

Read the help file called 'README_TBS6920_8920_UBUNTU'

In the first paragraph it asks you to create a directory in root called tbs and copy a series of files to it, listed below it. 

I can't or should I say don't know how to create a file there :confused:.  It keep on saying you don't have the permission. 

As you can expect nothing works from then on in regards to installing or making anything. ](*,)

Thanks for getting back to me

Matt

---

### Post by langner on 2011-12-09
If it help this is what I see in the terminal window

myth@myth:~$


I don't think I'm logged in as root.

Oh and I have put all the file into a folder called tbs in my home folder, which is called myth

If I do 

dir

I get

Desktop Documents Downloads Music Pictures Public tbs Template Videos

in terminal

Thanks

---

### Post by nickrout on 2011-12-09
```
cd tbs
```

for commands that need root permissions use the sudo command.

---

### Post by langner on 2011-12-10
Thanks, 

I'll do that.

Will I be able to 'make' the install file from there. Does it need to be in the root folder as it states in the readme file or will the sudo comment be able to sort it? 

*note*
*There will be a bit of a delay before I can get back to you for the next part.*

---

### Post by nickrout on 2011-12-10
No you shouldn't need to be in the /root directory.

---

### Post by langner on 2011-12-11
Hi,

I have been going through the steps in the readme file. and have got to number II.6, ready for number III. The only problem I got was when I tried *apt-get install linux-kernel-devel*. It couldn't find it to install it. 

I took a chance and moved on the the next part - the make and make install - it seemed to work. Well it took over an hour to go through the code, a lot of it starting with CC [M]. 

I restarted and did the next step *dmesg | grep cx88* and this brings up the code below. I believe it has installed right.


[   24.739498] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   24.749615] cx88[0]: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72,autodetected], frontend(s): 1
[   24.749622] cx88[0]: TV tuner type 4, Radio tuner type -1
[   24.805210] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   25.812275] input: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.2/rc/rc0/input4
[   25.812483] rc0: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.2/rc/rc0
[   25.813165] cx88[0]/2: cx2388x 8802 Driver Manager
[   25.813218] cx88-mpeg driver manager 0000:02:0a.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.813232] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 22, latency: 64, mmio: 0xea000000
[   25.813971] cx8800 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.813987] cx88[0]/0: found at 0000:02:0a.0, rev: 5, irq: 22, latency: 165, mmio: 0xe9000000
[   25.814271] cx88[0]/0: registered device video0 [v4l2]
[   25.814424] cx88[0]/0: registered device vbi0
[   26.596607] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input5
[   26.601213] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   26.601221] cx88/2: registering cx8802 driver, type: dvb access: shared
[   26.601228] cx88[0]/2: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72]
[   26.601234] cx88[0]/2: cx2388x based DVB/ATSC card
[   26.601238] cx8802_alloc_frontends() allocating 1 frontend(s)
[   26.848897] DVB: registering new adapter (cx88[0])
[   26.864934] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0


I can't see any errors but I don't know what to look for. 

I stopped at this point because it was late and should be trying the next bit either tonight or the next day. 

Thanks for your help on this. 

Oh before I forget, when it was making the file before the install, there was a couple of warning but no errors that I could see. I can't paste the code in here as it is no longer in the terminal window.

---

### Post by langner on 2011-12-12
I have tried the next steps in the readme - part number III. Unzipped it and done the *make*. 

The next step states 

> III.4 szap-s2 uses configuration files (see configuration file "astra_szap-s2.conf" for example) - they are simple text files and each line of them contains information about a channel, for example:
BBC:11597:v:0:22000:163:92:10050

Now I have found "astra_szap-s2.conf" file in the tbs folder and it has a couple of lines of text in them like the one above. 

Does this mean that I have to add a line of text for each channel I want? Also what does the finished file go, as in what directory should it be in. 

I have also gone into the folder where szap is unzipped to and read the readme file there is well. I have done the make and make install sections for szap but I'm now stuck (again). I can't find the  ~/.szap/channels.conf file it talks about. I have tried pressing ctrl+H.

I have tried running it and got the text below. I have also tried this for scan as well. 

> 
myth@myth:/usr/local/bin$ sudo szap-s2

usage: szap -q
         list known channels
       szap [options] {-n channel-number|channel_name}
         zap to channel via number or full name (case insensitive)
     -a number : use given adapter (default 0)
     -f number : use given frontend (default 0)
     -d number : use given demux (default 0)
     -c file   : read channels list from 'file'
     -V        : use VDR channels list file format (default zap)
     -b        : enable Audio Bypass (default no)
     -x        : exit after tuning
     -H        : human readable output
     -D        : params debug
     -r        : set up /dev/dvb/adapterX/dvr0 for TS recording
     -l lnb-type (DVB-S Only) (use -l help to print types) or 
     -l low[,high[,switch]] in Mhz
     -i        : run interactively, allowing you to type in channel names
     -p        : add pat and pmt to TS recording (implies -r)
                 or -n numbers for zapping
     -S        : delivery system type DVB-S=0, DVB-S2=1
     -M        : modulation 1=BPSK 2=QPSK 5=8PSK
     -C        : fec 0=NONE 12=1/2 23=2/3 34=3/4 35=3/5 45=4/5 56=5/6 67=6/7 89=8/9 910=9/10 999=AUTO
     -O        : rolloff 35=0.35 25=0.25 20=0.20 0=AUTO
myth@myth:/usr/local/bin$ dir
scan-s2  szap-s2
myth@myth:/usr/local/bin$ sudo scan-s2
initial tuning data files:

usage: scan-s2 [options...] [-c | initial-tuning-data-file]
	atsc/dvbscan doesn't do frequency scans, hence it needs initial
	tuning data for at least one transponder/channel.
	-c	scan on currently tuned transponder only
	-v 	verbose (repeat for more)
	-q 	quiet (repeat for less)
	-a N	use DVB /dev/dvb/adapterN/
	-f N	use DVB /dev/dvb/adapter?/frontendN
	-d N	use DVB /dev/dvb/adapter?/demuxN
	-s N	use DiSEqC switch position N (DVB-S only)
	-S N    use DiSEqC uncommitted switch position N (DVB-S only)
	-r sat  move DiSEqC rotor to satellite location, e.g. '13.0E' or '1.0W'
	-R N    move DiSEqC rotor to position number N
	-i N	spectral inversion setting (0: off, 1: on, 2: auto [default])
	-n	evaluate NIT messages for full network scan (slow!)
	-5	multiply all filter timeouts by factor 5
		for non-DVB-compliant section repitition rates
	-O pos	Orbital position override 'S4W', 'S19.2E' - good for VDR output
	-k cnt	Skip count: skip the first cnt 
		messages of each message type (default 0)
	-I cnt	Scan iterations count (default 10).
		Larger number will make scan longer on every channel
	-o fmt	output format: 'vdr' (default), 'vdr16x' for VDR version 1.6.x or 'zap'
	-x N	Conditional Access, (default -1)
		N=-2  gets all channels (FTA and encrypted),
		      output received CAID :CAID:
		N=-1  gets all channels (FTA and encrypted),
		      output CA is set to :0:
		N=0   gets only FTA channels
		N=xxx  sets ca field in vdr output to :xxx:
	-t N  Service select, Combined bitfield parameter.
		1 = TV, 2 = Radio, 4 = Other, (default 7)
	-p	for vdr output format: dump provider name
	-e N  VDR version, default 2 for VDR-1.2.x
		ANYTHING ELSE GIVES NONZERO NIT and TID
		Vdr version 1.3.x and up implies -p.
	-l lnb-type (DVB-S Only) (use -l help to print types) or 
	-l low[,high[,switch]] in Mhz
	-u UK DVB-T Freeview channel numbering for VDR

	-P do not use ATSC PSIP tables for scanning
	    (but only PAT and PMT) (applies for ATSC only)
	-A N	check for ATSC 1=Terrestrial [default], 2=Cable or 3=both
	-U	Uniquely name unknown services
	-D s	Disable specified scan mode (by default all modes are enabled)
		s=S1  Disable DVB-S scan
		s=S2  Disable DVB-S2 scan (good for owners of cards that do not
		      support DVB-S2 systems)
	-X	Disable AUTOs for initial transponders (esp. for hardware which
		not support it). Instead try each value of any free parameters.



**Mythbackend**
In the backend of of myth tv; it has found the card and put it under A4L analogy card, not sure it that is right or not, but it can't find any channels. :confused:

Thanks again for your help.

Matthew

---

### Post by nickrout on 2011-12-12
> **langner said:**
> I have tried the next steps in the readme - part number III. Unzipped it and done the *make*. 

The next step states 



Now I have found "astra_szap-s2.conf" file in the tbs folder and it has a couple of lines of text in them like the one above. 

Does this mean that I have to add a line of text for each channel I want? Also what does the finished file go, as in what directory should it be in. 

I have also gone into the folder where szap is unzipped to and read the readme file there is well. I have done the make and make install sections for szap but I'm now stuck (again). I can't find the  ~/.szap/channels.conf file it talks about. I have tried pressing ctrl+H.

I have tried running it and got the text below. I have also tried this for scan as well. 




**Mythbackend**
In the backend of of myth tv; it has found the card and put it under A4L analogy card, not sure it that is right or not, but it can't find any channels. :confused:

Thanks again for your help.

Matthew

No you need to set it as a dvb card, the v4l box is the default, you have to use the left and right arrow buttons to choose the right type of card.

---

### Post by langner on 2011-12-13
> **nickrout said:**
> No you need to set it as a dvb card, the v4l box is the default, you have to use the left and right arrow buttons to choose the right type of card.

Thanks for that, I didn't know it was the wrong one. I have changed it now to DVBinput card and input the following setting

[I]Astra 28.2E

Signal types: TV/Radio
Freq: 10714000 (kHz)
Polarity: Horizontal
Symbol rate: 22000000
Mod Sys: DVB-S
FEC: 5/6
Modulation: QPSK
Inversion: Auto
Rolloff: 0.35[/I]

Only now I have over 400 channels to sort out. But hey, I have channels :D. 

I'm not going to do the DVB-s2 for the HD channels as my current pc is rubbish. 

I just have to sort out the internal setting now for correct display on my TV. 

Thanks for you help on this. Not sure I could have done it without your help. 

Matthew

---

### Post by langner on 2011-12-13
Oh I got some good information from this site which could help someone else

[http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

---

### Post by tester100 on 2012-09-14
Hi lads

i am having the same problem around here heheh sort of

ok so i have read the readme files.. all of them

installed everything ok, driveres, compiled and so on..

now my problem is on the scan-s2 to scan the channels.

i have modified the correct file in sat confg i needed for my provider here, but it fails to scan the channels none of them ared found, mynd you i am using terminal, i have not yet installed mythtv i will later on install XMBC with mythtv

here´s  the log output

scan-s2 dvb-s/PAS-43.0W > channels.conf
API major 5, minor 3
scanning dvb-s/PAS-43.0W
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder DVB-S  10722000 H 30000000 3/4 AUTO AUTO
initial transponder DVB-S2 10722000 H 30000000 3/4 AUTO AUTO
initial transponder DVB-S  10722000 V 30000000 3/4 AUTO AUTO
initial transponder DVB-S2 10722000 V 30000000 3/4 AUTO AUTO
initial transponder DVB-S  10802000 H 30000000 5/6 AUTO AUTO
initial transponder DVB-S2 10802000 H 30000000 5/6 AUTO AUTO
initial transponder DVB-S  10802000 V 29000000 3/4 AUTO AUTO
initial transponder DVB-S2 10802000 V 29000000 3/4 AUTO AUTO
initial transponder DVB-S  10882000 H 28000000 3/4 AUTO AUTO
initial transponder DVB-S2 10882000 H 28000000 3/4 AUTO AUTO
----------------------------------> Using DVB-S
>>> tune to: 10722:hC34S0:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:hC34S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10722:hC34S1:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:hC34S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10722:vC34S0:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:vC34S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10722:vC34S1:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:vC34S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10802:hC56S0:S0.0W:30000:
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
>>> tune to: 10802:hC56S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10802:hC56S1:S0.0W:30000:
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
>>> tune to: 10802:hC56S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10802:vC34S0:S0.0W:29000:


any hints on whay i might be doing wrong ?

thxs
tester100

---

### Post by langner on 2012-09-14
Hi, 
Not sure how much it will help you but I never got the 'scan-s2' to work either. As it turned out I didn't need to. Mythtv found the channels just fine, well after I increased the scanning time it did. 

If you can, install Mythtv and find the channels using that. Although I do see that you are planning to install XBMC as well, I have not used this so I can't help you there. 

Good luck

Matt

---

### Post by nickrout on 2012-09-14
> **tester100 said:**
> Hi lads

i am having the same problem around here heheh sort of

ok so i have read the readme files.. all of them

installed everything ok, driveres, compiled and so on..

now my problem is on the scan-s2 to scan the channels.

i have modified the correct file in sat confg i needed for my provider here, but it fails to scan the channels none of them ared found, mynd you i am using terminal, i have not yet installed mythtv i will later on install XMBC with mythtv

here´s  the log output

scan-s2 dvb-s/PAS-43.0W > channels.conf
API major 5, minor 3
scanning dvb-s/PAS-43.0W
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder DVB-S  10722000 H 30000000 3/4 AUTO AUTO
initial transponder DVB-S2 10722000 H 30000000 3/4 AUTO AUTO
initial transponder DVB-S  10722000 V 30000000 3/4 AUTO AUTO
initial transponder DVB-S2 10722000 V 30000000 3/4 AUTO AUTO
initial transponder DVB-S  10802000 H 30000000 5/6 AUTO AUTO
initial transponder DVB-S2 10802000 H 30000000 5/6 AUTO AUTO
initial transponder DVB-S  10802000 V 29000000 3/4 AUTO AUTO
initial transponder DVB-S2 10802000 V 29000000 3/4 AUTO AUTO
initial transponder DVB-S  10882000 H 28000000 3/4 AUTO AUTO
initial transponder DVB-S2 10882000 H 28000000 3/4 AUTO AUTO
----------------------------------> Using DVB-S
>>> tune to: 10722:hC34S0:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:hC34S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10722:hC34S1:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:hC34S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10722:vC34S0:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:vC34S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10722:vC34S1:S0.0W:30000:
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
>>> tune to: 10722:vC34S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 972000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10802:hC56S0:S0.0W:30000:
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
>>> tune to: 10802:hC56S0:S0.0W:30000: (tuning failed)
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S2
>>> tune to: 10802:hC56S1:S0.0W:30000:
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
>>> tune to: 10802:hC56S1:S0.0W:30000: (tuning failed)
DVB-S IF freq is 1052000
WARNING: >>> tuning failed!!!
----------------------------------> Using DVB-S
>>> tune to: 10802:vC34S0:S0.0W:29000:


any hints on whay i might be doing wrong ?

thxs
tester100

where is the lnb frequency specified when using scan-s2? I don't see anything in your command-line that referes to the lnb at all.

---

### Post by tester100 on 2012-09-14
Hi

I have installed mythtv , selected the DVB card it showed up the conexant cx2388x  from my tbs8920

configured everything ok 

input:  /dev/dvb/adapter0/frontend0 ] (DVBinput)

then input my frequency from my tv provider

then input polarity

simbol rate

dvbs

QSPK

FEC 3/4

inversion : AUTO

roloff : 0.35

i am trying to scan dvb-s channel in mythtv now..

but after inputting all the settings and start scan i get the message no channel found........


this is drivers i have installed in linux

dmesg | grep cx2388
[   13.996826] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   14.000801] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   14.550318] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.639769] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   14.639778] cx88[0]/2: cx2388x based DVB/ATSC card



my provider is Digital dvbs Brazil i am trying to scan with the same data i use on the Set Top Box for the Ku band channels but its not picking any channel at all

---

### Post by nickrout on 2012-09-15
> **tester100 said:**
> Hi

I have installed mythtv , selected the DVB card it showed up the conexant cx2388x  from my tbs8920

configured everything ok 

input:  /dev/dvb/adapter0/frontend0 ] (DVBinput)

then input my frequency from my tv provider

then input polarity

simbol rate

dvbs

QSPK

FEC 3/4

inversion : AUTO

roloff : 0.35

i am trying to scan dvb-s channel in mythtv now..

but after inputting all the settings and start scan i get the message no channel found........


this is drivers i have installed in linux

dmesg | grep cx2388
[   13.996826] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   14.000801] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   14.550318] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.639769] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   14.639778] cx88[0]/2: cx2388x based DVB/ATSC card



my provider is Digital dvbs Brazil i am trying to scan with the same data i use on the Set Top Box for the Ku band channels but its not picking any channel at all

Not surprising if you haven't set up your LNB.

---

### Post by tester100 on 2012-09-15
> **nickrout said:**
> Not surprising if you haven't set up your LNB.


HI M8

cheers for replying bud

how do i setup my lnb frequency on it ?

this is the steps i am doing on MythTV 


i will attach some pics

[[IMG]http://imageshack.us/a/img404/4378/step1capturecardsetup.png[/IMG]]("http://imageshack.us/photo/my-images/404/step1capturecardsetup.png/")


step2

[[IMG]http://imageshack.us/a/img440/7322/step2capturecard.png[/IMG]]("http://imageshack.us/photo/my-images/440/step2capturecard.png/")


step3

[[IMG]http://imageshack.us/a/img824/8912/step3capturescanningcha.png[/IMG]]("http://imageshack.us/photo/my-images/824/step3capturescanningcha.png/")

error failed to scan channels
[[IMG]http://imageshack.us/a/img145/6317/step4resultcapturingsca.png[/IMG]]("http://imageshack.us/photo/my-images/145/step4resultcapturingsca.png/")


Any Ideas on what i could be doing wrong..

PS- I have particioned disk with winxpsp3 installed, tried progdvb on it with tbs8920 bda drivers and it scanned channels ok on same transponder mentioned, so shurelly i know i am missing something here .

Any help will be appreciated guys as i preffer to run a free source machine with xbmc+mythtv...




OK guys i forgot to update the configuration files from diseqc for my LNB which is universal LNB  2 ports


I/P  10.7 - 12.75 ghz

LNB LOF  LOW  9750
LNB LOF  HIGH 10600

[[IMG]http://imageshack.us/a/img715/6756/screen5diseqcoptions.png[/IMG]](http://imageshack.us/photo/my-images/715/screen5diseqcoptions.png/)



thxs guys
tester100

---

### Post by tester100 on 2012-09-15
Just un update on more information about my dvb card setup on linux

> dmesg | grep cx88
[   14.376132] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   14.376170] cx8800 0000:03:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.376564] cx88[0]: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72,autodetected], frontend(s): 1
[   14.376566] cx88[0]: TV tuner type 4, Radio tuner type -1
[   14.426874] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   14.911365] input: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:1e.0/0000:03:02.0/rc/rc0/input4
[   14.911418] rc0: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:1e.0/0000:03:02.0/rc/rc0
[   14.911531] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input5
[   14.911596] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   14.911603] cx88[0]/0: found at 0000:03:02.0, rev: 5, irq: 23, latency: 32, mmio: 0xfb000000
[   14.911614] IRQ 23/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   14.911702] cx88[0]/0: registered device video0 [v4l2]
[   14.911725] cx88[0]/0: registered device vbi0
[   14.911971] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.911987] cx88-mpeg driver manager 0000:03:02.2: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.911994] cx88[0]/2: found at 0000:03:02.2, rev: 5, irq: 23, latency: 32, mmio: 0xfc000000
[   14.911998] IRQ 23/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   14.931454] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   14.931457] cx88/2: registering cx8802 driver, type: dvb access: shared
[   14.931460] cx88[0]/2: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72]
[   14.931462] cx88[0]/2: cx2388x based DVB/ATSC card
[   14.931464] cx8802_alloc_frontends() allocating 1 frontend(s)
[   14.938310] DVB: registering new adapter (cx88[0])
[   19.504132] cx8800 0000:03:02.0: firmware: requesting dvb-fe-cx24116.fw


---

### Post by tester100 on 2012-09-15
Hi guys

all sorted out now...

managed to configure ou a scan-s2.conf file with all the tps


at the beginigi it gave me some tune failures in some tps but other just entered correctly

> pmt_pid = 0x31
service_id = 0x96C
pmt_pid = 0x32
service_id = 0x96D
pmt_pid = 0x33
service_id = 0x96F
pmt_pid = 0x37
service_id = 0x971
pmt_pid = 0x2B
service_id = 0x980
pmt_pid = 0x36
service_id = 0x982
pmt_pid = 0x3B
service_id = 0x983
pmt_pid = 0x2C
service_id = 0x984
pmt_pid = 0x43
service_id = 0x994
pmt_pid = 0x35
service_id = 0x998
pmt_pid = 0x22
service_id = 0x9A2
pmt_pid = 0x58
service_id = 0x9AC
pmt_pid = 0x24
service_id = 0x9B0
pmt_pid = 0x30
service_id = 0x1132
pmt_pid = 0x2A
service_id = 0x1142
pmt_pid = 0x44
service_id = 0x1143
pmt_pid = 0x46
service_id = 0x1144
pmt_pid = 0x4A
service_id = 0x1149
pmt_pid = 0x4B
service_id = 0x114A
pmt_pid = 0x20
service_id = 0x114E
pmt_pid = 0x49
service_id = 0x1196
pmt_pid = 0x47
service_id = 0x235C
pmt_pid = 0x4F
service_id = 0x235F
pmt_pid = 0x55
service_id = 0x2361
pmt_pid = 0x53
service_id = 0x2363
pmt_pid = 0x42
service_id = 0xFF1B
pmt_pid = 0x51
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0211
  AUDIO     : PID 0x0281
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  OTHER     : PID 0x04D4 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x04D8 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x04D6 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x051F TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  OTHER     : PID 0x03BB TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x04B0 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x04AA TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x0518 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x0517 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x0515 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020A
  OTHER     : PID 0x0578 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x0315 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x039D
  AUDIO     : PID 0x039E
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
  AUDIO     : PID 0x039F
  OTHER     : PID 0x03EF TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x03B9 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020D
  AUDIO     : PID 0x028F
  OTHER     : PID 0x03B7 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x0451 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020D
  AUDIO     : PID 0x028F
  OTHER     : PID 0x03B7 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020E
  AUDIO     : PID 0x028E
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020C
  AUDIO     : PID 0x028C
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x020A
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x0210 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0207
  OTHER     : PID 0x039C TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0206
  AUDIO     : PID 0x0286
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  OTHER     : PID 0x04D9 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0203
  AUDIO     : PID 0x0283
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0201
  OTHER     : PID 0x03BE TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x04CF TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x04D4 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x0519 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0202
  OTHER     : PID 0x044F TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
  OTHER     : PID 0x044E TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0205
  AUDIO     : PID 0x0285
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0204
>>> parse_section, section number 0 out of 2...!
0x6030 0x0961: pmt_pid 0x0000 (null) -- (null) (running)
0x6030 0x0962: pmt_pid 0x0023 (null) -- MOS 119 (running)
0x6030 0x0963: pmt_pid 0x0025 (null) -- MOSAICO iTV (running)
0x6030 0x0964: pmt_pid 0x0026 (null) -- REDE VIDA (running)
0x6030 0x0965: pmt_pid 0x0027 (null) -- SKY (running)
0x6030 0x0966: pmt_pid 0x0028 (null) -- TV5 MONDE (running)
0x6030 0x0967: pmt_pid 0x0029 (null) -- PASSO A PASSO (running)
0x6030 0x0968: pmt_pid 0x002D (null) -- MOS 120 (running)
0x6030 0x096A: pmt_pid 0x002F (null) -- PROMO&#65533;&#65533;O (running)
0x6030 0x096B: pmt_pid 0x0031 (null) -- SKY (running)
0x6030 0x096C: pmt_pid 0x0032 (null) -- FUTEBOL NA SKY (running)
0x6030 0x096D: pmt_pid 0x0033 (null) -- SKY 136 (running)
>>> parse_section, section number 2 out of 2...!
Network Name 'SATELLITES'
>>> parse_section, section number 1 out of 2...!
0x6030 0x096F: pmt_pid 0x0037 (null) -- COMEDY CENTRAL (running)
0x6030 0x0971: pmt_pid 0x002B (null) -- AXN (running)
0x6030 0x0972: pmt_pid 0x0000 (null) -- SKY (running)
0x6030 0x0980: pmt_pid 0x0036 (null) -- SKY (running)
0x6030 0x0982: pmt_pid 0x003B (null) -- CHECK-UP SKY (running)
0x6030 0x0983: pmt_pid 0x002C (null) -- SKY (running)
0x6030 0x0984: pmt_pid 0x0043 (null) -- SKY (running)
0x6030 0x0994: pmt_pid 0x0035 (null) -- CANAL DO CLIENTE (running)
0x6030 0x0998: pmt_pid 0x0022 (null) -- CALIBRA&#65533;&#65533;O TV (running)
0x6030 0x09A2: pmt_pid 0x0058 (null) -- VIVA (running)
0x6030 0x09AC: pmt_pid 0x0024 (null) -- (null) (running)
0x6030 0x09B0: pmt_pid 0x0030 (null) -- CARTELA 800 (running)
0x6030 0x1132: pmt_pid 0x002A (null) -- SKY (running)
0x6030 0x1133: pmt_pid 0x0000 (null) -- Cartela Interativa (running)
0x6030 0x1135: pmt_pid 0x0000 (null) -- Cartela Interativa (running)
0x6030 0x1142: pmt_pid 0x0044 (null) -- Esot&#65533;rico (running)
0x6030 0x1143: pmt_pid 0x0046 (null) -- ITV Loterias (running)
>>> parse_section, section number 0 out of 2...!
Network Name 'SATELLITES'
>>> parse_section, section number 2 out of 2...!
0x6030 0x1144: pmt_pid 0x004A (null) -- SKY Empresas (running)
0x6030 0x1149: pmt_pid 0x004B (null) -- MOSAICO ADULTO (running)
0x6030 0x114A: pmt_pid 0x0020 (null) -- COMO PAGAR (running)
0x6030 0x114E: pmt_pid 0x0049 (null) -- MOSAICO HD (running)
0x6030 0x1196: pmt_pid 0x0047 (null) -- Minha SKY (running)
0x6030 0x1908: pmt_pid 0x0000 (null) -- SKY (running, scrambled)
0x6030 0x235C: pmt_pid 0x004F (null) -- MOSAICO ITV (running)
0x6030 0x235F: pmt_pid 0x0055 (null) -- Pacotes de Programa&#65533;&#65533;o (running)
0x6030 0x2361: pmt_pid 0x0053 (null) -- SKY R&#65533;dios (running)
0x6030 0x2363: pmt_pid 0x0042 (null) -- iTV Games (running)
>>> parse_section, section number 1 out of 2...!
Network Name 'SATELLITES'
----------------------------------> Using DVB-S
>>> tune to: 11382:vC34M2O35S0:S43.6W:30000:
DVB-S IF freq is 1632000
>>> parse_section, section number 0 out of 0...!
service_id = 0x0
service_id = 0x76D
pmt_pid = 0x177
service_id = 0x76E
pmt_pid = 0x112
service_id = 0x76F
pmt_pid = 0x113
service_id = 0x770
pmt_pid = 0x114
service_id = 0x772
pmt_pid = 0x116
service_id = 0x773
pmt_pid = 0x117
service_id = 0x774
pmt_pid = 0x900
service_id = 0x775
pmt_pid = 0x119
service_id = 0x776
pmt_pid = 0x11A
service_id = 0x777
pmt_pid = 0x11B
service_id = 0x778
pmt_pid = 0x11C
service_id = 0x779
pmt_pid = 0x11D
service_id = 0x77A
pmt_pid = 0x11E
service_id = 0x77B
pmt_pid = 0x105
service_id = 0x77D
pmt_pid = 0x23
service_id = 0x77F
pmt_pid = 0x27
service_id = 0x781
pmt_pid = 0x100
service_id = 0x784
pmt_pid = 0x20
service_id = 0x786
pmt_pid = 0x26
service_id = 0x787
pmt_pid = 0x29
service_id = 0xFFFE
pmt_pid = 0x1100
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0458
  AC3       : PID 0x04C6
  AUDIO     : PID 0x04C7
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  OTHER     : PID 0x05DC TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  OTHER     : PID 0x1213 TYPE 0xE0
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x04C0
  AUDIO     : PID 0x04CA
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  AUDIO     : PID 0x04D4
>>> parse_section, section number 0 out of 0...!
  AUDIO     : PID 0x0294
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  AUDIO     : PID 0x045C
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x045B
  AUDIO     : PID 0x046F
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0459
  AUDIO     : PID 0x046D
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  OTHER     : PID 0x05DC TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0457
  AUDIO     : PID 0x04D9
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  OTHER     : PID 0x0501 TYPE 0x0B
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0456
  AUDIO     : PID 0x046A
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0455
  AUDIO     : PID 0x0469
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0454
  AUDIO     : PID 0x0468
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  AC3       : PID 0x0472
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0450
  AUDIO     : PID 0x0464
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x044E
  AUDIO     : PID 0x0462
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x044D
  AUDIO     : PID 0x0461
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x04C1
  AC3       : PID 0x04CB
  AUDIO     : PID 0x04D5
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0452
  AUDIO     : PID 0x0466
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
  CA ID     : PID 0x0946
  AUDIO     : PID 0x047A
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x045D
  AUDIO     : PID 0x046B
  CA ID     : PID 0x0946
  CA ID     : PID 0x0942
  CA ID     : PID 0x0907
  AC3       : PID 0x046C
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x045A
  AUDIO     : PID 0x046E
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0452
  AUDIO     : PID 0x0466
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
  AUDIO     : PID 0x047A
>>> parse_section, section number 0 out of 0...!
  VIDEO     : PID 0x0453
  AUDIO     : PID 0x0467
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
  CA ID     : PID 0x0942
  AUDIO     : PID 0x047B
>>> parse_section, section number 0 out of 0...!
  OTHER     : PID 0x03EA TYPE 0x0B
  VIDEO     : PID 0x044F
  AUDIO     : PID 0x0463
  CA ID     : PID 0x0942
  CA ID     : PID 0x0946
  CA ID     : PID 0x0907
>>> parse_section, section number 1 out of 1...!
0x6074 0x077D: pmt_pid 0x0023 (null) -- ITATIAIA AM/FM (running)
0x6074 0x077E: pmt_pid 0x0000 (null) -- SKY (running)
0x6074 0x077F: pmt_pid 0x0027 (null) -- HBO PLUS*e (running)
0x6074 0x0781: pmt_pid 0x0100 (null) -- HBO FAMILY (running)
0x6074 0x0783: pmt_pid 0x0000 (null) -- SKY (running)
0x6074 0x0784: pmt_pid 0x0020 (null) -- JOVEM PAN AM (running)
0x6074 0x0785: pmt_pid 0x0000 (null) -- SKY (running)
0x6074 0x0786: pmt_pid 0x0026 (null) -- NHK (running)
0x6074 0x0787: pmt_pid 0x0029 (null) -- HBO2 (running)
>>> parse_section, section number 1 out of 2...!
Network Name 'SATELLITES'
>>> parse_section, section number 2 out of 2...!
Network Name 'SATELLITES'
>>> parse_section, section number 0 out of 1...!
0x6074 0x076D: pmt_pid 0x0177 (null) -- TV SENADO (running)
0x6074 0x076E: pmt_pid 0x0112 (null) -- CNN INTERNAT. (running)
0x6074 0x076F: pmt_pid 0x0113 (null) -- PLAY (running)
0x6074 0x0770: pmt_pid 0x0114 (null) -- TV CULTURA (running)
0x6074 0x0771: pmt_pid 0x0000 (null) -- SKY (running)
0x6074 0x0772: pmt_pid 0x0116 (null) -- HBO FAMILY (running)
0x6074 0x0773: pmt_pid 0x0117 (null) -- HBO SIGNATURE (running)
0x6074 0x0774: pmt_pid 0x0900 (null) -- MAXPRIME (running)
0x6074 0x0775: pmt_pid 0x0119 (null) -- TV C&#65533;MARA (running)
0x6074 0x0776: pmt_pid 0x011A (null) -- CANAL RURAL (running)
0x6074 0x0777: pmt_pid 0x011B (null) -- CLIMATEMPO (running)
0x6074 0x0778: pmt_pid 0x011C (null) -- MAX HD (running)
0x6074 0x0779: pmt_pid 0x011D (null) -- TRUTV (running)
0x6074 0x077A: pmt_pid 0x011E (null) -- SIC (running)
0x6074 0x077B: pmt_pid 0x0105 (null) -- TV JUSTI&#65533;A (running)
0x6074 0x077C: pmt_pid 0x0000 (null) -- R&#65533;dio Multishow (running)
>>> parse_section, section number 0 out of 2...!
Network Name 'SATELLITES'
dumping lists (87 services)
SKY 123;SKY:10722:vC34M2O35S0:S43.6W:30000:515:643=por:0:0:1034:162:24682:0
PREMIERE 24H;:10722:vC34M2O35S0:S43.6W:30000:517:645=por:0:0:1036:162:24682:0
CANAL DO CLIENTE;:10722:vC34M2O35S0:S43.6W:30000:512:642=por:0:0:1301:162:24682:0
CANAL DO CLIENTE;:10722:vC34M2O35S0:S43.6W:30000:513:641=por:0:0:1302:162:24682:0
SKY 127;:10722:vC34M2O35S0:S43.6W:30000:518:646=por:0:0:1307:162:24682:0
MAX;:10722:vC34M2O35S0:S43.6W:30000:519:687=eng;667=eng:0:0:1308:162:24682:0
SYFY;:10722:vC34M2O35S0:S43.6W:30000:523:651=por,671=eng:0:0:1312:162:24682:0
HBO;:10722:vC34M2O35S0:S43.6W:30000:524:652=eng,668=por:0:0:1313:162:24682:0
GLITZ*;:10722:vC34M2O35S0:S43.6W:30000:525:653=por:0:0:1314:162:24682:0
MAXPRIME*e;:10722:vC34M2O35S0:S43.6W:30000:520:648=eng;658=eng:0:0:1315:162:24682:0
CANAL DO CLIENTE;:10722:vC34M2O35S0:S43.6W:30000:513:641=por:0:0:1352:162:24682:0
[06a5];:11302:vC56M2O35S1:S0.0W:30000:4096:4100;4100:0:0:1701:0:0:0
[06a6];:11302:vC56M2O35S1:S0.0W:30000:4112:4113=por;4115=por:0:0:1702:0:0:0
[06a7];:11302:vC56M2O35S1:S0.0W:30000:4128:4129=eng;4131=eng:0:0:1703:0:0:0
[06a8];:11302:vC56M2O35S1:S0.0W:30000:4144:4147;4147:0:0:1704:0:0:0
[06a9];:11302:vC56M2O35S1:S0.0W:30000:4160:4162;4164:0:0:1705:0:0:0
[06aa];:11302:vC56M2O35S1:S0.0W:30000:4176:4179;4179:0:0:1706:0:0:0
[06ab];:11302:vC56M2O35S1:S0.0W:30000:4192:4196;4196:0:0:1707:0:0:0
MOS 119;:11382:hC34M2O35S0:S43.6W:30000:513:0:0:0:2402:162:24624:0
MOSAICO iTV;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:2403:162:24624:0
REDE VIDA;:11382:hC34M2O35S0:S43.6W:30000:515:643=por:0:0:2404:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:2405:162:24624:0
TV5 MONDE;:11382:hC34M2O35S0:S43.6W:30000:517:645=fra:0:0:2406:162:24624:0
PASSO A PASSO;:11382:hC34M2O35S0:S43.6W:30000:518:646=por:0:0:2407:162:24624:0
MOS 120;:11382:hC34M2O35S0:S43.6W:30000:519:0:0:0:2408:162:24624:0
PROMO&#65533;&#65533;O;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:2410:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:522:0:0:0:2411:162:24624:0
FUTEBOL NA SKY;:11382:hC34M2O35S0:S43.6W:30000:523:0:0:0:2412:162:24624:0
SKY 136;:11382:hC34M2O35S0:S43.6W:30000:524:652=por:0:0:2413:162:24624:0
COMEDY CENTRAL;:11382:hC34M2O35S0:S43.6W:30000:526:654=por:0:0:2415:162:24624:0
AXN;:11382:hC34M2O35S0:S43.6W:30000:529:641=por:0:0:2417:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:525+951:655=por:0:0:2432:162:24624:0
CHECK-UP SKY;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:2434:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:2435:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:2436:162:24624:0
CANAL DO CLIENTE;:11382:hC34M2O35S0:S43.6W:30000:525+951:655=por:0:0:2452:162:24624:0
CALIBRA&#65533;&#65533;O TV;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:2456:162:24624:0
VIVA;:11382:hC34M2O35S0:S43.6W:30000:925:926=por,927=SAP:0:0:2466:162:24624:0
[09ac];:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:2476:162:24624:0
CARTELA 800;:11382:hC34M2O35S0:S43.6W:30000:522:0:0:0:2480:162:24624:0
SKY;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:4402:162:24624:0
Esot&#65533;rico;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:4418:162:24624:0
ITV Loterias;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:4419:162:24624:0
SKY Empresas;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:4420:162:24624:0
MOSAICO ADULTO;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:4425:162:24624:0
COMO PAGAR;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:4426:162:24624:0
Minha SKY;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:4502:162:24624:0
MOSAICO ITV;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:9052:162:24624:0
Pacotes de Programa&#65533;&#65533;o;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:9055:162:24624:0
SKY R&#65533;dios;:11382:hC34M2O35S0:S43.6W:30000:514:0:0:0:9057:162:24624:0
iTV Games;:11382:hC34M2O35S0:S43.6W:30000:516:0:0:0:9059:162:24624:0
TV SENADO;:11382:vC34M2O35S0:S43.6W:30000:1101:1121=por:0:0:1901:162:24692:0
CNN INTERNAT.;:11382:vC34M2O35S0:S43.6W:30000:1102:1122=eng:0:0:1902:162:24692:0
PLAY;:11382:vC34M2O35S0:S43.6W:30000:1103:1123=por:0:0:1903:162:24692:0
TV CULTURA;:11382:vC34M2O35S0:S43.6W:30000:1104:1124=por:0:0:1904:162:24692:0
HBO FAMILY;:11382:vC34M2O35S0:S43.6W:30000:1106:1126=eng,1146=por:0:0:1906:162:24692:0
HBO SIGNATURE;:11382:vC34M2O35S0:S43.6W:30000:1107:1127=eng,1147=por:0:0:1907:162:24692:0
MAXPRIME;:11382:vC34M2O35S0:S43.6W:30000:1108:1128=eng;1138=eng:0:0:1908:162:24692:0
TV C&#65533;MARA;:11382:vC34M2O35S0:S43.6W:30000:1109:1129=por:0:0:1909:162:24692:0
CANAL RURAL;:11382:vC34M2O35S0:S43.6W:30000:1110:1130=por:0:0:1910:162:24692:0
CLIMATEMPO;:11382:vC34M2O35S0:S43.6W:30000:1111:1241=por:0:0:1911:162:24692:0
MAX HD;:11382:vC34M2O35S0:S43.6W:30000:1112:1223=eng;1222=eng:0:0:1912:162:24692:0
TRUTV;:11382:vC34M2O35S0:S43.6W:30000:1113:1133=por:0:0:1913:162:24692:0
SIC;:11382:vC34M2O35S0:S43.6W:30000:1114:1134=por:0:0:1914:162:24692:0
TV JUSTI&#65533;A;:11382:vC34M2O35S0:S43.6W:30000:1115:1135=por:0:0:1915:162:24692:0
ITATIAIA AM/FM;:11382:vC34M2O35S0:S43.6W:30000:0:1116=por:0:0:1917:162:24692:0
HBO PLUS*e;:11382:vC34M2O35S0:S43.6W:30000:1117:1131=eng;1132=eng:0:0:1919:162:24692:0
HBO FAMILY;:11382:vC34M2O35S0:S43.6W:30000:1106:1126=eng,1146=por:0:0:1921:162:24692:0
JOVEM PAN AM;:11382:vC34M2O35S0:S43.6W:30000:0:660=por:0:0:1924:162:24692:0
NHK;:11382:vC34M2O35S0:S43.6W:30000:1216:1226=jpn,1236=eng:0:0:1926:162:24692:0
HBO2;:11382:vC34M2O35S0:S43.6W:30000:1217:1237=por;1227=por:0:0:1927:162:24692:0
Done.


---

### Post by tester100 on 2012-09-15
Hi guys


so now i am just steap of completing a full scan on mythtv

so scan-s2 works fine and i can get 82 channels out of my scan with the tps configured

now on the Mythtv i cant get any channel to scan i´ve tried manually by TP and nothing it does not scan anything


i have configured the DiseqC options with LNB universal, but its not getting anything..

any hints or ideas?

---

### Post by langner on 2012-09-15
Hi, 

I have just noticed that in your LNB preset you have it set to Europe and not *'your region / country' *, as you have stated you are scanning in Brazil. Make sure this is done before you scan for any channels as you won't find anything otherwise. 

Also check that you are scanning the right frequencies  for you area as the ones I used in a previous post are for the UK. 

Are the setting / frequencies that you are using for DVB-S or DVB-S2, it may be good just to check them, (as well as all the other setting on that page, just to be sure). 

If you have already done all this, I'm not sure what else to do but keep trying different setting and lengthening the scanning times before it times out. 

I know getting it the work the first time can be a real bugger but it does work, even if you have pulled out all your hair. Mine used to be 3 foot long and now I have a shine on my head. :lolflag:

Anyway good luck.

Matt

---

### Post by tester100 on 2012-09-16
> **langner said:**
> Hi, 

I have just noticed that in your LNB preset you have it set to Europe and not *'your region / country' *, as you have stated you are scanning in Brazil. Make sure this is done before you scan for any channels as you won't find anything otherwise. 

Also check that you are scanning the right frequencies  for you area as the ones I used in a previous post are for the UK. 

Are the setting / frequencies that you are using for DVB-S or DVB-S2, it may be good just to check them, (as well as all the other setting on that page, just to be sure). 

If you have already done all this, I'm not sure what else to do but keep trying different setting and lengthening the scanning times before it times out. 

I know getting it the work the first time can be a real bugger but it does work, even if you have pulled out all your hair. Mine used to be 3 foot long and now I have a shine on my head. :lolflag:

Anyway good luck.

Matt


Hello m8

i appreciate your input, but actually it was a freeking straight forward thing, that did not come across my mind at all.

i was beyond that to much teck involved and not smart enough to realize the actuall problem.


so here it goes

after setting up my LNB to europe UNIVERSAL, which is in fact the same as in my south america region.

i completely forgot something which came across in another tutorial i found on the net.

so here it goes

example, the only reason why i was not getting signal was for the pure fact that i was inputting the wrong frequency mhz for scanning in the   scan option

example i was using

10802 H 28000 mhz TP

in mythtv i was using

10802

H
28000000


which was failing.


so i tried

with information found in other tutorial


10802000

H

28000000

and bang straight on finding signal

how  000 in the end of the frequency made such difference, specially when i lost around 6hours trying to find for tech solutions over the net, and at the same time blaming the faulty hardware for some kind of bug.

Needless to say that the only bug at the moment was me completely bugged off assuming it was a hardware fault instead of a human being fault.


as someone told me once.

the hardware is 99,99% right is just a matter of what you do with it that will respond accordingly to your input information...

so here is a screenshot of working solution scanning channels so if anyone else had the same issue and started blaming the h/w first ...

[[IMG]http://imageshack.us/a/img18/9381/scanok.png[/IMG]]("http://imageshack.us/photo/my-images/18/scanok.png/")

---

### Post by nickrout on 2012-09-16
yes the first computer acronym I ever learned - GIGO - garbage in garbage out.

It is frustrating that scan and similar utilities tend to deal in kHz and myth wants Hz, a factor of 1,000.

Glad you got it working!

---

