---
title: "DVB-t scanning problems in fiesty"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by gusjones on 2007-04-20
I have a detected and compatible Hauppage Nova-t DVB-t TV card (shows up detected in device manager), but I cannot create a channels.conf file.

This is what I get:

<Input in terminal> 
scan /usr/local/share/dvb/scan/dvb-t/uk-CraigKelly

<result> 
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

So I cannot therefore create the necessary channels.conf because 'scan' seems to be looking in the wrong place for my dvb card.

Also if I try tvtime-scanner this is what I get

<terminal input> 
rob@rob-desktop1:~$ tvtime-scanner

<output> 
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.
----

(Tried lots of different input numbers but to no avail).

I had this card working in windows so I know the hardware is not faulty.

Can anyone help me out. :confused:

---

### Post by gusjones on 2007-04-22
Is there a problem with Happauge DVB-t cards in Fiesty?

---

### Post by ishaq on 2007-04-22
I'm having the exact same problem, but with different hardware. 

I have the following DVB-T card installed:

04:0e.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:0e.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

---

Any help in resolving this problem will be much appreciated. Thanks

---

### Post by sbelial on 2007-04-22
I have the same problem with a Hauppauge Nova-T DVB-T PCI card which worked fine before my upgrade to 7.04 :( The same error message is produced:

 FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

---

### Post by Erlander on 2007-04-23
Do your cards show up in dmesg?

It appears that there are 2 different Hauppage Nova-t DVB-t TV cards.

Details here:  [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards)

Rob

---

### Post by gusjones on 2007-04-23
Ishaq, try 'sudo modprobe cx88_dvb' in a terminal window as explained by sbelial in this thread,

[http://ubuntuforums.org/showthread.php?t=417758&page=3](http://ubuntuforums.org/showthread.php?t=417758&page=3)

This worked for me.

---

### Post by ishaq on 2007-04-24
Gus, that worked! I've now added that module to /etc/modules so it loads at startup. Thanks for the help. Cheers.

---

### Post by Gina on 2007-04-24
I'm having the same problem.  Followed advice in various places to get things working but although the TV cards (tried a USB one as well as the PCI) seem to be detected and scanning appears to work neither find any channels - reporting no signal or no table (in MythTV).  I have tried several TV apps - MythTV, Kaffeine, TVTime and a couple of others all without success.  In Kaffeine I had to create my own table of MUX frequencies etc. as the one for here (Stockland Hill) was not in the collection.

The cards are a Philips Semiconductors SAA7134/7135HL (as reported by lspci) and the external one a Hauppage DVB-t USB box, which also reports as an SAA7134 chipset.

I've recently upograded to Feisty and most of the problems I had with Dapper running MythTV have been resolved (problems with MySQL stopped me from getting anywhere).  It detects both cards but when trying to scan the 2nd on (USB) the scanning dialog says it on DVB:0 rather than DVB:1 though the results are slightly different when scanning - getting **no table** rather than **no signal** errors.

One other point (and please excuse mentioning *that other OS* here) is that since trying various things in Ubuntu, my PCI card is no longer detected in Windows XP and the driver has disappeared.  Attempts to reinstall the driver from the supplied CD have failed.  I'm wondering if I might have installed the wrong firmware into the card and totally upset things - is this possible/llikely?

---

### Post by equilibrium on 2007-04-24
I just installed feisty + mythtv on my laptop and am also having problems scanning for channels. I can get it to scan ok and it seems to pickup signal, but no channels appear at all.
I've even tried the scan command, but that does exactly the same :(

I'm using a Leadtek USB DVB-T dongle

---

### Post by Gina on 2007-04-24
Still no success! :(

Been doing more research on this including "Googling" and trying various things and come to the conclusion that you need to set the options to the right card type, the right tuner number and maybe set up firmware for the system to install on the card.

Found a table of card types and mine (Medion 7134) is listed as 10 but setting it to this makes things worse.

My PC is a Medion MD8386.  I took the TV tuner card out to get more info...There's a metal box labelled PHILIPS, a label saying "Type. Medion TV_Tuner 7134 - Rev. CTX918_V.2 DVB-T/TV" and a whole collectioon of other numbers - and the card itself says "CTX918_V2".

Has anyone here got one of these working?  Or any suggestions?  Please :)  Meanwhile, I go on trying...

**Later...**  Made some progress :)  set **options saa7134 card=12 tuner=38**  and now have a few channels in MythTV but the display is jerky, showing about 3 or 4 frames a csecond.  The sound is OK.  Kaffeine found more channels but I got an error msg saying a plugin was missing and it wouldn't display live TV  So a couple of things to fix plus sortiung out how to get EPG.  Info obtained from [this link]("http://www.spinics.net/lists/vfl/msg14787.html")

---

### Post by Erlander on 2007-04-25
Have a look at the Feisty documentation for Mythtv here:  [https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

Its much easier to set up now.

Rob

---

### Post by Gina on 2007-04-25
Yes - great improvement :)  I used that link to install and set it up.  Now working but I'm getting jerky video.  It's the only TV app I've found so far that will display any TV.  Kaffeine scans and finds the channells OK but won't disply the TV, reporting missing plugin > 10:36:04: xine: couldn't find demux for >/home/gina/.kaxtv.ts<
10:36:04: xine: found input plugin : file input plugin
10:36:04: video_decoder: no plugin available to handle 'XviD'
10:36:04: xine: found demuxer plugin: AVI/RIFF demux plugin
10:36:04: xine: found input plugin : file input plugin  Other apps (TVTime, Klear etc.) report missing files.

MythTV looks like ir should be good if it can be persuaded to work properly.

---

### Post by Erlander on 2007-04-25
To fix Kaffeine you need to install extra Xine plugins and codecs.

I did a xine search in Synapatice and installed every plugin and codec that looked in any way relevant.

I know there are more scientific ways but it did fix that klaztv.ts message.

Rob

---

### Post by Gina on 2007-04-25
Thanks very much Rob :)  Done that and Kaffeine is now working perfectly :):)  Good picture without any jerkiness, good sound and recording works fine.  Even the EPG works :)  I get a bit of breaking up on some channels but that's a matter of getting the aerial signal right - have same thing in Windows.

I reckon Kaffeine will now be my chosen TV viewing and recording app on the PC.  I'll probably abandon MythPC.  Now just need to sort out TV and video editing in Ubuntu and I think that just about leaves Win XP out in the cold :):)

---

### Post by equilibrium on 2007-04-25
I have mine working now :)

It turned out to be the driver for my DVB dongle. I just installed the latest ones from v4l-dvb. The playback is a bit jerky atm tho. Prob cos I have a ATI card :(
I also can't find out how to get the program guide up :( I am using a MCE remote, but pressing the guide button doesn't do anything.

---

### Post by megamaced on 2007-04-25
> **gusjones said:**
> Ishaq, try 'sudo modprobe cx88_dvb' in a terminal window as explained by sbelial in this thread,

[http://ubuntuforums.org/showthread.php?t=417758&page=3](http://ubuntuforums.org/showthread.php?t=417758&page=3)

This worked for me.

Thank you thank you thank you! :) 

Don't understand why this step is nessacary though, because my Hauppauge card worked out of the box in Dapper Drake!

---

### Post by Jose Catre-Vandis on 2007-05-22
> **gusjones said:**
> Ishaq, try 'sudo modprobe cx88_dvb' in a terminal window as explained by sbelial in this thread,

[http://ubuntuforums.org/showthread.php?t=417758&page=3](http://ubuntuforums.org/showthread.php?t=417758&page=3)

This worked for me.

Thanks, this got me going after a new install to Fiesty. Strange that it worked out of the box on Dapper. That's progress I guess!  :-)

---

