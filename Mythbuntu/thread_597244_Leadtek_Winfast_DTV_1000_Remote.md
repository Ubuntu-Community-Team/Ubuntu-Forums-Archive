---
title: "Leadtek Winfast DTV 1000 Remote"
date: 2007-10-30
forum: Mythbuntu
---

### Post by Lorenzo1985 on 2007-10-30
Hi Guys

Can anyone tell me the steps I need to perform to get my remote on my Leatek Winfast DTV 1000 to be recognised and working on 7.10

Please bare in mind whilst I am prepared to edit config files and script I am not very experienced with linux.

As a suggestion It might be a good plan to try and add support for this card as it is very popular in the UK as it is one of the cheapest and well reviewed HD capable TV cards... It would be great if it were as easy as picking it from the list in the Mythbuntu control panel but i suppose everyone says that.


Any help would be greatly appreciated....


My Setup is
Ubuntu Gutsy 7.10 (32bit) with addition of Mythbuntu-desktop and Kubuntu-desktop 
Pentium 4 
Leadtek Winfast DTV1000 DVB card

---

### Post by superm1 on 2007-10-30
> **Lorenzo1985 said:**
> Hi Guys

Can anyone tell me the steps I need to perform to get my remote on my Leatek Winfast DTV 1000 to be recognised and working on 7.10

Please bare in mind whilst I am prepared to edit config files and script I am not very experienced with linux.

As a suggestion It might be a good plan to try and add support for this card as it is very popular in the UK as it is one of the cheapest and well reviewed HD capable TV cards... It would be great if it were as easy as picking it from the list in the Mythbuntu control panel but i suppose everyone says that.


Any help would be greatly appreciated....


My Setup is
Ubuntu Gutsy 7.10 (32bit) with addition of Mythbuntu-desktop and Kubuntu-desktop 
Pentium 4 
Leadtek Winfast DTV1000 DVB card
Was the remote listed upon installation?  Is it in the control centre?

---

### Post by Lorenzo1985 on 2007-10-31
No I'm afraid not, it wasnt listed and is not in the control centre. Two of the other Leadtek cards are listed but selecting those does not cause the remote on the Leadtek Winfast DTV1000 to function at all...

---

### Post by superm1 on 2007-10-31
> **Lorenzo1985 said:**
> No I'm afraid not, it wasnt listed and is not in the control centre. Two of the other Leadtek cards are listed but selecting those does not cause the remote on the Leadtek Winfast DTV1000 to function at all...

It is very possible that the remote uses a dev/input interface.  When you choose eitherother remote, see what driver it was choosing.

If it is dev/input, you will need to modify /etc/lirc/hardware.conf to represent your remote's /dev/input/eventX driver.

---

### Post by hagenma on 2007-11-02
I got this remote working using the instructions at:
[http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV](http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV)

This involved downloading and recompiling V4L-DVB and then compiling a custom kernel to set the timer frequency to 1000 Hz.

Also, I followed the directions on Making you LIRC Device Static at [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php).

It would be nice if these changes could be incorporated into Mythbuntu, because the V4L-DVB and kernel changes need to be made each time you upgrade your kernel.

---

### Post by superm1 on 2007-11-02
> **hagenma said:**
> I got this remote working using the instructions at:
[http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV](http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV)

This involved downloading and recompiling V4L-DVB and then compiling a custom kernel to set the timer frequency to 1000 Hz.

Also, I followed the directions on Making you LIRC Device Static at [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php).

It would be nice if these changes could be incorporated into Mythbuntu, because the V4L-DVB and kernel changes need to be made each time you upgrade your kernel.
Please file this in a bug against the kernel, and subscribe the mythbuntu team if you would like to see it for hardy.  Otherwise, i'm almost sure this will be overlooked.

---

### Post by Lorenzo1985 on 2007-11-05
> **superm1 said:**
> Please file this in a bug against the kernel, and subscribe the mythbuntu team if you would like to see it for hardy.  Otherwise, i'm almost sure this will be overlooked.


Do you really think they are likely to change the standard Timer frequency in the kernel for one card?

This had already been reported in Fiesty:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/151561](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/151561)

I have added comments to the existing bug report but do not know how to subscribe teams to such a bug.

---

### Post by Lorenzo1985 on 2007-11-08
Any way i can push for this bug to actually be fixed in hardy?

The changes to the cx88 stuff are really only very simple

Biggest thing is getting the default Timer tick on the kernel to be set to 1000hz?

Anyone know whether the ubuntu team is likely to agree to this? As far as i know this has already been done in Knoppmyth...

---

### Post by barmax on 2007-12-28
Hi, 

This is my first post as I am a former windows user so humour me.  The post was inspired by Lorenzo1985 who has a problem with his remote.  

[QUOTE=Lorenzo1985;3669580]Hi Guys

Can anyone tell me the steps I need to perform to get my remote on my Leatek Winfast DTV 1000 to be recognised and working on 7.10 
QUOTE]

I too have a Leadtek Winfast DTV 1000 which I have unsucessfully installed on Mythbuntu 7.10. and  was hoping you could let me into the secret of your success.  

I have read a load of reports on fixes for the problem but non appear to work for me.  Most of the problems seem to stem from the cx88 module which was supposed to have been fixed in Dec 07.  I have installed the latest weekly update.  

When I go into the backend and setup the card it only wants to use the generic saa7134 module.  I am at a loss.  

BTW I have a Hauppage 350 installed and working no problems.  

Thanks in advance.  I know half my problems stem from my lack of knowledge and experience.  

My Setup Is:
Mythbuntu 7.10 last updated and upgraded 28 Dec 07
CPU 3.0 Ghz
RAM 2 Gb
Graphics Card Nvidia 8500GT 256ram PCI-ex GDDR3
Sound Card - On board
HD 250Gb
Tuner Leadtek Winfast DTV1000S & Hauppage 350 PVR

---

### Post by Lorenzo1985 on 2007-12-29
is your problem with the remote or getting the card to work in myth tv?

if its with the remote there are ways to sort of get this working in ubuntu.

else if the problem lies in getting anything out of the card there are some things i can talk you through to get this card to work.

the first thing i would do is try and establish whether the card works at all with much simpler programs like Klear and dvb-utils

---

### Post by barmax on 2007-12-29
> **Lorenzo1985 said:**
> is your problem with the remote or getting the card to work in myth tv?

if its with the remote there are ways to sort of get this working in ubuntu.

else if the problem lies in getting anything out of the card there are some things i can talk you through to get this card to work.

the first thing i would do is try and establish whether the card works at all with much simpler programs like Klear and dvb-utils

I haven't even contemplated using the remote yet.  

My first goal is to get the card working which it isn't.  I have the card sucessfully working in XP with the remote but that was only because I have XP and Mythubuntu on the same drive.  

I have never heard of Klear or dvb-utils.  I will check them out tomorrow.  

Like I said previously, I have very little experience in the Linux environment so any guidance is appreciated.  

Thanks

---

### Post by Lorenzo1985 on 2007-12-29
ok well firstly i should warn you that i'm only a little bit more experienced with linux than yourself with linux but i have managed to get my card working.

Secondly as i am at my family home i am not near an ubuntu computer and am having to do much of this by my somewhat hazy memory and the commands may not be correct

 here is what I've managed to work out:  

to install  clear goto a terminal and type

sudo apt-get install klear

you'll be asked for you password which you should give.

likewise to install dvb-utils do 

sudo apt-get install dvb-utils

Now for this bit a bit of geography s usefull, you need to work ouyt which tv signal transmitter covers your area:
in a terminal type 
 cd /usr/share/doc/dvb-utils/examples/scan/dvb-t/
ls

you should find the one appropriate to you then do the following (for me the transmitter is UK- Hannington so i wil demonstrate as such

cd
sudo scan usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Hannington >.klear/channels.conf

then if you fire up klear and see if that works (if you have a menu you should now find klear in there if so use that. otherwise just type klear & into a terminal)

you should be able to change cards etc in the klear setup menus.


Alternatiely to all of this [Gary Parkers website ]("http://www.parker1.co.uk") is fantastically usefull, especially the pages about [testing your card]("http://www.parker1.co.uk/mythtv_dvb.php") and [this page]("http://www.parker1.co.uk/mythtv_ubuntu.php") 

also thinking about it this might shed some light on your problems:
grep -i dvb /var/log/messages


Post back and let us know how you got on with all of that

---

### Post by barmax on 2007-12-30
> **Lorenzo1985 said:**
> 
you need to work ouyt which tv signal transmitter covers your area:
in a terminal type 
 cd /usr/share/doc/dvb-utils/examples/scan/dvb-t/
ls

I installed klear & dvb-utils.  

I found on for my city - Perth Australia and tried scanning with the following result:

max@MythTV-Max:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ sudo scan usr/share/doc/dvb-utils/examples/scan/dvb-t > /home/max/.klear/channels.conf
[sudo] password for max:
scanning usr/share/doc/dvb-utils/examples/scan/dvb-t
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

Although /dev/dvb is missing, there is a /dev/.static/dev/dvb directory and associated adapter subdirectories.

> also thinking about it this might shed some light on your problems:
grep -i dvb /var/log/messagest

Tried that with the following result:

max@MythTV-Max:/$ grep dvb /var/log/messages
Dec 28 00:37:57 MythTV-Max kernel: [ 5210.033322] cx2388x dvb driver version 0.0.6 loaded
Dec 28 00:37:57 MythTV-Max kernel: [ 5210.033325] cx8802_register_driver() ->registering driver type=dvb access=shared
Dec 28 00:55:55 MythTV-Max kernel: [ 6287.346835] cx2388x dvb driver version 0.0.6 loaded
Dec 28 00:55:55 MythTV-Max kernel: [ 6287.346839] cx8802_register_driver() ->registering driver type=dvb access=shared
Dec 28 01:03:22 MythTV-Max kernel: [ 6735.130072] cx2388x dvb driver version 0.0.6 loaded
Dec 28 01:03:22 MythTV-Max kernel: [ 6735.130076] cx8802_register_driver() ->registering driver type=dvb access=shared
Dec 28 17:42:41 MythTV-Max kernel: [ 3117.350728] cx2388x dvb driver version 0.0.6 loaded
Dec 28 17:42:41 MythTV-Max kernel: [ 3117.350731] cx8802_register_driver() ->registering driver type=dvb access=shared
Dec 28 17:46:17 MythTV-Max kernel: [ 3333.441136] cx2388x dvb driver version 0.0.6 loaded
Dec 28 17:46:17 MythTV-Max kernel: [ 3333.441140] cx8802_register_driver() ->registering driver type=dvb access=shared

I also tried the following:

max@MythTV-Max:/$ dmesg | grep dvb
NO OUTPUT

max@MythTV-Max:/$ lsmod | grep dvb
NO OUTPUT

max@MythTV-Max:/$ lsmod | grep saa713
saa7134_alsa           15392  0 
snd_pcm                80388  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
saa7134               129100  1 saa7134_alsa
video_buf              26244  2 saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  2 saa7134,ivtv
v4l2_common            18432  8 msp3400,saa7127,saa7115,tuner,saa7134,ivtv,cx2341x,videodev
v4l1_compat            15364  3 saa7134,ivtv,videodev
i2c_core               26112  10 msp3400,saa7127,saa7115,tuner,saa7134,ivtv,i2c_algo_bit,tveeprom,nvidia,ir_kbd_i2c
snd                    54660  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

max@MythTV-Max:/$ lsmod | grep dev
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               29312  2 saa7134,ivtv
v4l2_common            18432  8 msp3400,saa7127,saa7115,tuner,saa7134,ivtv,cx2341x,videodev
v4l1_compat            15364  3 saa7134,ivtv,videodev
snd                    54660  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  11136  4 

max@MythTV-Max:/$ dmesg | grep saa
[   42.951116] saa7130/34: v4l2 driver version 0.2.14 loaded
[   44.019334] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   44.187739] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   45.211926] saa7130[0]: found at 0000:07:00.0, rev: 1, irq: 22, latency: 32, mmio: 0x97004800
[   45.211931] saa7130[0]: subsystem: 107d:6655, board: UNKNOWN/GENERIC [card=0,autodetected]
[   45.211937] saa7130[0]: board init: gpio is 20000
[   45.347637] tuner 1-0060: chip found @ 0xc0 (saa7130[0])
[   45.383624] saa7130[0]: i2c eeprom 00: 7d 10 55 66 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   45.383633] saa7130[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   45.383642] saa7130[0]: i2c eeprom 20: 01 40 01 01 01 ff 01 03 08 ff 00 8a ff ff ff ff
[   45.383651] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.383660] saa7130[0]: i2c eeprom 40: ff 35 00 c0 00 10 03 02 ff 04 ff ff ff ff ff ff
[   45.383669] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.383677] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.383686] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.383751] saa7130[0]: registered device video1 [v4l2]
[   45.383781] saa7130[0]: registered device vbi1
[   45.390291] saa7134 ALSA driver for DMA sound loaded
[   45.390308] saa7130[0]/alsa: saa7130[0] at 0x97004800 irq 22 registered as card -2


max@MythTV-Max:/$ sudo lspci -v
07:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: LeadTek Research Inc. Unknown device 6655
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at 97004800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1

07:01.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at 90000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

It appears that part of my problem stems from the placement of the dvb directory under /dev/.static/dev/dvb.  I don't have the experience or knowledge to work out why.  I have tried researching along that vein but no luck so far.  I also checked out that website.  No bad.  

Thanks for the advice.  Enjoy the rest of your hols.  

regards

---

### Post by ubnewbie2 on 2007-12-30
> **barmax said:**
> I haven't even contemplated using the remote yet.  

My first goal is to get the card working which it isn't.  I have the card sucessfully working in XP with the remote but that was only because I have XP and Mythubuntu on the same drive.  



I have 2 Leadtek Winfast DTV100-T cards in my system.  They work out of the box.  Mythbuntu sees them and uses them without any special intervention by me.

I have never tried to use the remote.

---

### Post by barmax on 2007-12-30
If only I was so lucky.

---

### Post by ozybushwalker on 2008-01-11
G'day barmax,
    Do you have the correct model of DTV1000? The DTV1000S is for use with satellite transmission, the DTV1000T is for use with Terrestrial (free to air TV from a ground based transmitter) broadcasts. You mention you have a DTV1000S, maybe you should have got a DTV1000T. (I almost bought a DVT1000S because they were in stock at the time whereas the DTV1000T wasn't.)

My DTV1000T (which worked out of the box, apart from the remote) shows up in lspci as:
00:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

which is rather different to what your device displays.

---

### Post by ozybushwalker on 2008-01-13
Sorry about my previous post. I thought I had read the DTV1000S was for use with satellite transmission but now I can't find any reference to that being the case. 

However this reference  [http://forums.whirlpool.net.au/forum-replies-archive.cfm/872829.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/872829.html")
treports the 1000S and 1000T have quite different chipsets.

The 1000S is apaprently quite a new card. I suspect thee isn't yet a driver which completely recognises it (notice the saa7130 driver reports the board as UNKNOWN/GENERIC)

---

### Post by mrbandersnatch on 2008-01-29
Sorry for raising a slightly aged thread.

The DTV1000**S** is a refresh of the T using newer (read cheaper) silicon. Composite/SVideo inputs work but (AFAIK) there are currently no Linux drivers for the tuner and wont be until someone reverse engineers them :(

I sadly got one of these cards by mistake and it was a waste of money.

---

### Post by ubnewbie2 on 2008-01-29
I thought the S suffix was for Satellite reception, and T was terrestrial - i.e. FTA broadcasts from normal stations.

---

### Post by barmax on 2008-02-24
Just to keep you up to date (I have been away).  Further to the discussion on the DTV1000S.  The DTV1000S  is a DVB-T TV caputue card - as has been pointed out.  Also, I have a dual boot with XP on a partition which detects the card successfully and all free to air channels are accessible..  The driver is the issue here - I believe..  I have written to the unbuntu developers team regarding the driver without a reply..

---

### Post by kreegor on 2008-02-27
Sorry to add to an old post but this seemed like the logical place to ask this question.

Once the remote is set up and working for the DTV1000T, is it possible to use the remote to power up the pc if it is in hibernation or suspended?

I know the suspend function is script based, basically assigning a suspend scripts location to the button in lirc, but it is the power up feature that interests me.

The reason I ask is because on the leadtek website it says it can be used to power up but I'm not sure if that is just for windows. At the moment I am using a Dvico MCE USB remote which works great but it would be nice to be able to suspend/resume the box with the remote.

---

### Post by saffelli on 2008-03-16
Hi there. I too am new to Mythbuntu and this is my first post so apologies for my inexperience upfront. I have purchased 2 of the Winfast DTV1000S tuner cards and cannot get them working either. I went for these rather than the DTV1000T cards to fit in a small form factor box.

By the sounds of things I am going to be out of luck but was just wondering whether you had heard back from the developer team? Do you think it is worth persevering or should I count my losses now and go for an alternative card?

Thanks for continuing the discussion.

Regards

Steve

---

### Post by chiefchimp on 2008-03-27
> **barmax said:**
> Hi, 


I too have a Leadtek Winfast DTV 1000 which I have unsucessfully installed on Mythbuntu 7.10. and  was hoping you could let me into the secret of your success.  

I have read a load of reports on fixes for the problem but non appear to work for me.  Most of the problems seem to stem from the cx88 module which was supposed to have been fixed in Dec 07.  I have installed the latest weekly update.  

When I go into the backend and setup the card it only wants to use the generic saa7134 module.  I am at a loss.  

BTW I have a Hauppage 350 installed and working no problems.  

Thanks in advance.  I know half my problems stem from my lack of knowledge and experience.  

My Setup Is:
Mythbuntu 7.10 last updated and upgraded 28 Dec 07
CPU 3.0 Ghz
RAM 2 Gb
Graphics Card Nvidia 8500GT 256ram PCI-ex GDDR3
Sound Card - On board
HD 250Gb
Tuner Leadtek Winfast DTV1000S & Hauppage 350 PVR

I'm in a similar position, trying to get a Leadtek Winfast DTV1000S working in Kubuntu 7.10 (I have to keep this box for general use).

there is info on the dtv1000T that uses the cx88 chipset but I have only found a single reference to the DTV1000S that uses the phillips SAA7130 chipset but I'm still searching and trying.

/]/]ik

---

### Post by chiefchimp on 2008-03-27
[QUOTE=ozybushwalker;4119034]G'day barmax,
    Do you have the correct model of DTV1000? The DTV1000S is for use with satellite transmission, the DTV1000T is for use with Terrestrial (free to air TV from a ground based transmitter) broadcasts. You mention you have a DTV1000S, maybe you should have got a DTV1000T. (I almost bought a DVT1000S because they were in stock at the time whereas the DTV1000T wasn't.)

the DTV1000S is an upgrade with different chip set phillips SAA7130 instead of Conexant cx88.

The manuals included in the box clearly state this. Pity leadtek where to dump to realise the confusion the S suffix would cause.

/]/]ik

---

### Post by psypher on 2008-03-30
WHAT are the ways??? please tell me the ways?? I am so tired of struggling with this. I have the Winfast TV2000 XP Expert and has the same chipset as the DTV 1000. can anyone PLEASE tell me STEP BY STEP instructions to get this working on the latest editions of ubuntu, even better if you can tell me how to make this work on Mythbuntu 8.04 (hardy beta). Please do not link to other sites, post it here. I have been trawling for days now and all these links are dead or make no sense

These are my details:

Card: Winfast TV2000 Xp EXPERT 

```
cat /proc/bus/input/devices

I: Bus=0001 Vendor=107d Product=6611 Version=0001
N: Name="cx88 IR (Leadtek Winfast 2000XP"
P: Phys=pci-0000:02:00.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010000 190 4801 1e0000 4400 100000 10000ffc

```

Since mine says event6 I am assuming my hardware.conf should reflect that instead?

This is picked up with a default install btw so no changes have been made up to this point to get that result.

when i run the irrecord command I get the following errors:

```
sudo irrecord -H dev/input -d /dev/input/event6 ~/lircd.conf

Hold down an arbitrary button.
.irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event6'

```

Note the one fullstop before "irrecord: gap not found"
that pops up the second I press any key, so something is coming through.

Please, please, PLEASE can someone give me some help with this.

Thanks!!

> **Lorenzo1985 said:**
> is your problem with the remote or getting the card to work in myth tv?

if its with the remote there are ways to sort of get this working in ubuntu.

else if the problem lies in getting anything out of the card there are some things i can talk you through to get this card to work.

the first thing i would do is try and establish whether the card works at all with much simpler programs like Klear and dvb-utils

---

### Post by psypher on 2008-03-30
K can anyone explain this to me?? Why is that when i do sudo cat /dev/input/event6 and press keys on my remote i get input????
Does that not mean that everything should be fine now and this should actually work. According to this [bug report]("https://bugs.launchpad.net/mythbuntu/+bug/151561") these bug have been fixed in hardy. Does thi have to do with the timing thing??

Thanks again

---

### Post by Lorenzo1985 on 2008-03-30
They have not and are not likely to fix the kernel tick frequency so the remote is never going to work well unless you compile your own kernel, I've tried this several times and have yet to manage to get this correct, and even if you do you'll loose it every time you do a distribution upgrade. 

My experience of compiling my own kernels with the correct time frequencies is that it has proved to be difficult, time consuming, and very difficult to get right. Whilst i did manage to get to the point where the leadtek remote works better i also found that i broke several other things including my networking.

However Irrecord should work on your system, if it doesnt i've no idea why not

In Hardy you dont really need to do any of the other stuff as these were mostly just steps to get the event driver working

---

### Post by Shodanho on 2008-05-15
Hi I am also very new two Linux,  about 2 days into it :-)

I am trying to setup MythTV and am also having trouble with the DTV1000S by Leadtek.  I have seen some posts indicating that this card is for satellite, but that is not correct check [http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=382](http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=382).  It says on the manufacturers site that it is a terrestrial tuner.

Has anyone been able to get this card to work on linux?  Or do I have to go back to a windows installation.

Shodanho

---

### Post by chiefchimp on 2008-05-15
reading the linux-dvb mailing list, it appears that support for the DTV1000S is not far off, testing of the TDA10048 chip is under way.

fingers crossed!

/]/]ik

---

### Post by Wyld on 2008-05-16
Would be nice once it's here ... I purchased the 1000S a little while ago for a whole $37 (australian) and it's been gold in my Windows partition, even the PVR software from Leadtek is nothing to be sneezed at, very nice.

I've even been tempted to purchase a different card, a HDTV card that is *WELL* supported but I'm not sure which one to get to be honest.

---

### Post by Jetjoint on 2008-08-23
Any further update on the Leadtek 1000S ????

Thanks

---

### Post by chiefchimp on 2008-08-24
> **Jetjoint said:**
> Any further update on the Leadtek 1000S ????

Thanks

I've seen nothing on the linuxtv mailing list

/]/]ik

---

### Post by GtWRX on 2009-06-11
Have compiled twice over last few days and can confirm this works!! 1st version card picked up but would not pick up channels. 2nd version Card picked up, channel scan perfect and now watching TV. Office PC now has TV!!!
 For Reference:
[http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)
 I am more than happy to help with any queries. I also run a Mythbuntu PC in the lounge with other cards, so am familiar with alot of the issues encountered.
 For those running Ubuntu you need to use sudo on the make install.
 This has been done on Ubuntu 9.04 running a Leadtek DTV1000S bought a week ago, man am I lucky!
 Gavin

---

### Post by marrabld on 2009-08-07
I would really appreciate some help.

I followed the link [http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/) (well actually I have tried this a few times already)  I am a little confused where to go here, I am pretty comfortable with compiling, however there are links to a few different files.  

Step 7 the v4l-dvb driver files depending on the correct card and also "official LinuxTV v4l-dvb driver for DTV1000 S"  which is the one that you are supposed to compile.

I compiled the v4l-dvb files, and when i "dmesg | grep -i dvb"

I get ::

[   12.681990] saa7130[0]: subsystem: 107d:6655, board: AverTV DVB-T 777 [card=85,insmod option]
[   12.682142] input: saa7134 IR (AverTV DVB-T 777) as /devices/pci0000:00/0000:00:09.0/0000:05:08.0/input/input6
[   12.864683] saa7130[0]/alsa: AverTV DVB-T 777 doesn't support digital audio
[   13.000966] dvb_init() allocating 1 frontend
[   13.042746] saa7130[0]/dvb: frontend initialization failed
[   13.257552] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   13.257555] cx88/2: registering cx8802 driver, type: dvb access: shared

NOTE -->  "saa7130[0]/dvb: frontend initialization failed"

And if I try to compile the other files in --> 'dtv1000s-21a03349f7f9.tar'

I get ::

make -C /home/server/Desktop/dtv1000s-21a03349f7f9/v4l 
make[1]: Entering directory `/home/server/Desktop/dtv1000s-21a03349f7f9/v4l'
Updating/Creating .config
/bin/sh: ./scripts/make_kconfig.pl: not found
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/server/Desktop/dtv1000s-21a03349f7f9/v4l'
make: *** [all] Error 2

Any help would be greatly appreciated.  Cheers

---

### Post by blueeyesmike on 2009-08-09
I have compiled this driver for the card and can confirm it should work.

> **marrabld said:**
> I would really appreciate some help.

make -C /home/server/Desktop/dtv1000s-21a03349f7f9/v4l 
make[1]: Entering directory `/home/server/Desktop/dtv1000s-21a03349f7f9/v4l'
Updating/Creating .config
/bin/sh: ./scripts/make_kconfig.pl: not found
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/server/Desktop/dtv1000s-21a03349f7f9/v4l'
make: *** [all] Error 2

Any help would be greatly appreciated.  Cheers

You need to make to do make -C /home/server/Desktop/dtv1000s-21a03349f7f9/
not make -C /home/server/Desktop/dtv1000s-21a03349f7f9/v4l

or just 
cd /home/server/Desktop/dtv1000s-21a03349f7f9/
make
sudo make install
restart computer (this is all I had to do to get the card working)

If that doesn't work check that the file make_kconfig.pl exists it should be at /home/server/Desktop/dtv1000s-21a03349f7f9/v4l/scripts/make_kconfig.pl It should have been part of the archive you downloaded

---

### Post by marrabld on 2009-08-13
Thanks for the reply.  but this is what I keep getting

server@server-desktop:~/Desktop/dtv1000s-21a03349f7f9/v4l$ make
Updating/Creating .config
/bin/sh: ./scripts/make_kconfig.pl: /usr/bin/perl^M: bad interpreter: No such file or directory
make: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.

I am wondering if it has something to do with perl? or permissions? I did a chmod -R 755 on the whole file with no Joy.  

What does this mean "No rule to make target"  any one know?

Cheers

---

### Post by marrabld on 2009-08-30
I managed to get rid of the 'bad interpreter' error by updating my version of Perl.  however I am still getting 

```
make[1]: Entering directory `/home/server/dtv1000s-21a03349f7f9/v4l'
scripts/make_makefile.pl
make[1]: scripts/make_makefile.pl: Command not found
./scripts/make_kconfig.pl /lib/modules/2.6.28-15-generic/build /lib/modules/2.6.28-15-generic/build
make[1]: ./scripts/make_kconfig.pl: Command not found
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/server/dtv1000s-21a03349f7f9/v4l'
make: *** [all] Error 2

```

I have made sure I have the linux-headers installed but still no joy.  

So I put the v4l folder on my laptop, typed make and it compiled fine.  Problem is, my laptop has no pci slot to use the card (obviously), I just wanted to check.  

I checked that I am running the same version of Ubuntu (Jaunty) and that both computers were up to date and that they were using the same kernel 2.6.28-15-generic  Everything seems the same.

Can anyone suggest how I can investigate what is different between the two computers?

Cheers

---

### Post by blueeyesmike on 2009-10-04
> **marrabld said:**
> I managed to get rid of the 'bad interpreter' error by updating my version of Perl.  however I am still getting 

```
make[1]: Entering directory `/home/server/dtv1000s-21a03349f7f9/v4l'
scripts/make_makefile.pl
make[1]: scripts/make_makefile.pl: Command not found
./scripts/make_kconfig.pl /lib/modules/2.6.28-15-generic/build /lib/modules/2.6.28-15-generic/build
make[1]: ./scripts/make_kconfig.pl: Command not found
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/server/dtv1000s-21a03349f7f9/v4l'
make: *** [all] Error 2

```

I have made sure I have the linux-headers installed but still no joy.  

So I put the v4l folder on my laptop, typed make and it compiled fine.  Problem is, my laptop has no pci slot to use the card (obviously), I just wanted to check.  

I checked that I am running the same version of Ubuntu (Jaunty) and that both computers were up to date and that they were using the same kernel 2.6.28-15-generic  Everything seems the same.

Can anyone suggest how I can investigate what is different between the two computers?

Cheers

you should make sure that the files mentioned exist (I checked they should come with the downloaded package)
/home/server/dtv1000s-21a03349f7f9/v4l/scripts/make_makefile.pl
/home/server/dtv1000s-21a03349f7f9/v4l/scripts/make_kconfig.pl

If they do exist then check that they are executable (if not sudo chmod +x <file name>)

If the files do not exist download the driver package again, try from here, [http://kernellabs.com/hg/~mkrufky/dtv1000s](http://kernellabs.com/hg/~mkrufky/dtv1000s), that is the official driver I think, just click on gz up the top and then unzip the contents to a folder.

Good Luck

---

