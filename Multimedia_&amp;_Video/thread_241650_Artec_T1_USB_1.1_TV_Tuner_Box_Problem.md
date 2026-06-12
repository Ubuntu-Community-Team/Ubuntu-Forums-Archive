---
title: "Artec T1 USB 1.1 TV Tuner Box Problem"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by ChrispyUK on 2006-08-22
Right, here's my predicament:

I've got this Artec T1 USB DVB-T tuner, it works great under Windows yet I can't find a nice piece of software to use with it, hence my Linux adventure.

I've tried KnoppMyth which doesn't support the box.

On reccommendation from a friend I'm using Ubuntu (the latest one).

It is supported in Linux because when I restart the machine from Windows into Linux I can watch using Kaffeine (think it must be something to do with firmware loading).
I can't get the box to work if I boot straight into Linux.  I ran some thing in the terminal that told me it was 'usbtest' or something???????:confused: 

I'm a total n00b with this, I have no idea what I'm doing, please help!!!!!](*,) 

Chris!

P.S. So far with the various HOWTO's I've tried on wikis, linux is driving me up the wall!

---

### Post by ChrispyUK on 2006-08-23
Anyone got any suggestions?

I've found that this box that I have uses a firmware loader in windows.  When I boot into windows it loads the firmware to the box which means when I restart into Linux it can use the box since the firmware is already there.
So it must be a problem with Linux not loading the firmware.  I've downloaded the relevant DibCom firmware and put it into the hotplug directory, but where do I go from here? It doesn't seem to do anything!

I've also found that the box uses some sort of generic chip therefore is being recognised by a module called 'USBtest'.  How can I get this thing working? I presume this 'USBtest' is stopping it being recognised as a DVB box.

Cheers!

---

### Post by awaldram on 2006-08-27
You need to recompile the kernel with the 

faulty chip id option enabled in the kernel config

---

### Post by ChrispyUK on 2006-08-29
OK thanks, will try that.

---

### Post by easyease on 2006-09-24
hi id love to know how whether that idea worked cos i have the same device and same problem. how would i go about doinmg this?

---

### Post by awaldram on 2006-09-30
Well I have the same card it's fair to say it wasn't an Idea but a fact.

I use it in debian not Ubuntu but the kernel's the kernel.

The pci id of this device is wrong it reports as a usb chipset because the manfactur was to lazy to reprogram it correctly.

Therfore to stop the dvb driver attaching to every usb chipset thats not programed (what the 'generis usb device' does) it's disabled by default.

Neither Ubuntu nor Debian chose to enable it in their kernel build therfore the device wont  work.

Enabling the option then rebuilding will cause the correct driver to be loaded when the device is inserted so gives you a chance.

2.6.17 also has the wrong tunning steps for this device appears that the develooper regresed to a known buggy set.

If you want I can send you the changes required to use this kernel.

I notified the kernel developer but he hasnt commented.

---

### Post by awaldram on 2006-09-30
I beleive 2.6.15 is ok (long time since I've run such an old kernel though ;-))

---

### Post by easyease on 2006-10-10
hi awaldram, yes would appreciate any details you can give if it'as not too much trouble, best thing to do is leave any info on this thread so anyone can read it. It does seem odd how i can use this device in a warm state (after booting into windows firstly) by using kaffeine in breezy, but have no joy with it in dapper. thanks for explaining its a kernal issue, hmmm im totally scared of recompiling a kernal.

---

### Post by awaldram on 2006-10-12
this is the code change for /driver/media/dvb/frontends/dvd-pll.c

Though it looks a lot the only real difference is the timmings ending in 4 not 3 this is from 2.6.16 sources

struct dvb_pll_desc dvb_pll_tda665x = {
        .name  = "Philips TDA6650/TDA6651",
        .min   =  44250000,
        .max   = 858000000,
        .setbw = tda665x_bw,
        .count = 12,
        .entries = {
                {   93834000, 36249333, 166667, 0xca, 0x61 /* 011 0 0 0  01 */ },
                {  123834000, 36249333, 166667, 0xca, 0xa1 /* 101 0 0 0  01 */ },
                {  161000000, 36249333, 166667, 0xca, 0xa1 /* 101 0 0 0  01 */ },
                {  163834000, 36249333, 166667, 0xca, 0xc2 /* 110 0 0 0  10 */ },
                {  253834000, 36249333, 166667, 0xca, 0x62 /* 011 0 0 0  10 */ },
                {  383834000, 36249333, 166667, 0xca, 0xa2 /* 101 0 0 0  10 */ },
                {  443834000, 36249333, 166667, 0xca, 0xc2 /* 110 0 0 0  10 */ },
                {  444000000, 36249333, 166667, 0xca, 0xc4 /* 110 0 0 0 11 */ },
                {  583834000, 36249333, 166667, 0xca, 0x64 /* 011 0 0 0 11 */ },
                {  793834000, 36249333, 166667, 0xca, 0xa4 /* 101 0 0 0 11 */ },
                {  444834000, 36249333, 166667, 0xca, 0xc4 /* 110 0 0 0 11 */ },
                {  861000000, 36249333, 166667, 0xca, 0xe4 /* 111 0 0 0 11 */ },
    }
};
EXPORT_SYMBOL(dvb_pll_tda665x);

---

### Post by awaldram on 2006-10-12
of cause if the last line already has 0xe4 in it then they have fixed it again.

---

### Post by easyease on 2006-10-19
Im sure you will be pleased to know that the the device works great under Edgy using the latest version of kaffeine, only seems to use half the cpu it did under breezy! Im very impressed, especially when i compare it to how it works under windows with the software that was made for it. lol

---

### Post by r76 on 2006-10-23
Easyease, that sounds very encouraging.  Does it work under Edgy from cold (please say yes!), or only if restarting into Edgy from windows?

Also did you do a clean install of Edgy or an upgrade?
Cheers

---

### Post by r76 on 2006-10-29
[COLOR="#ff0000"](EDIT: Works great in Feisty, the channel listings below are now generated from an autoscan which took 5 or 6 attempts)[/COLOR]

Well Kaffeine 0.8.2 in Edgy does indeed run the Artec box better than the bundled Windows software.  I haven't tried recording yet but so far everything seems ok.  I did a clean install of Edgy, and yes it works from cold!  I did need to install xine extra codecs (libxine-extracodecs) as described here to get the sound working:
[http://www.ubuntuforums.org/showpost.php?p=1533316&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1533316&postcount=3)

Unfortunately in my case the autoscan feature didn't pick up all the channels for my local transmitter at crystal palace in london, designated uk-CrystalPalace and it took me so long to add them I thought I'd do it here (see below) so that it'd save anyone else in this area a lot of time.  Two main problems seemed to be the missing out of entire muxes, and that TV channels aren't identified until they are on air e.g BBC3 after 7pm.

Kaffeine doesn't use a file called channels.conf to store channel info, instead it's called channels.dvb and is in a subfolder of your home directory e.g. (with my username as rje):
/home/rje (in View menu set 'show hidden files')
then /.kde/share/apps/channels.dvb

(1) HOW I MADE A NEW CHANNELS.DVB (If you live in London then skip down to part 2, the channels.dvb file I made and use that, it'll save you lots of time)

First I installed dvb-utils as described here
[http://www.linuxtv.org/wiki/index.php/First_steps_with_a_budget_DVB_card](http://www.linuxtv.org/wiki/index.php/First_steps_with_a_budget_DVB_card)
to get the scan utility.  Then I ran this to make a channels.conf output file:
  scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace \
    > /home/rje/channels.conf

Then I converted this into a channels.dvb format as described here:
[http://sourceforge.net/forum/message.php?msg_id=3523571](http://sourceforge.net/forum/message.php?msg_id=3523571)
using the web-based tool here:
[http://lab.infodatei.de/conf2dvb/](http://lab.infodatei.de/conf2dvb/)

Then whilst Kaffeine is closed I replaced the data in Kaffeine's channels.dvb file with this new data (just double-clicking the file thus using gedit text editor, nothing fancy).  Then I saved the file (making a backup of the old incomplete scans, just in case).

I then ran Kaffeine and after selecting a working channel (BBC1) noted that the properties are different to my normal scans, and EPG and subtitles don't work.  So whilst on that channel do a new autoscan which obtains correct info for all channels in that mux (providing the channels are broadcasting at that time!).  Then I deleted the existing (imported) entry for each channel in the mux and replaced it with the new (scanned) entry.  By trial and error I did this or a channel from each mux so I could correct all channels with scanned data.  Then repeated this in the evening when BBC3 and BBC4 were running.

(2) MY NEW CHANNELS.DVB (works for all channels I've tried on the Crystal Palace transmitter) -[COLOR="Red"]**UPDATED 21/8/07**[/COLOR], smileTV and teachersTV are missing
IF YOU SHARE THIS TRANSMITTER PASTE THIS OVER YOUR EXISTING DATA, BUT KEEP A BACKUP OBVIOUSLY ;-)

#Generated by Kaffeine 0.5
RA|1Xtra BBC|0|434(eng),|0|18176|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|1|||
TV|301|203(2)|407(eng),408(und),|0|19456|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|2|603(16)(1)(1)(eng),||
TV|302|204(2)|411(eng),412(und),|0|19520|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|3|602(16)(1)(1)(eng),||
RA|305|0|403(eng),|0|16768|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|4|||
RA|BBC 5L SportsX|0|431(eng),|0|17984|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|5|||
RA|BBC 6 Music|0|432(eng),|0|18048|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|6|||
RA|BBC 7|0|433(eng),|0|18112|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|7|||
RA|BBC Asian Net.|0|435(eng),|0|18240|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|8|||
TV|BBC FOUR|201(2)|401(eng),402(eng),|0|16832|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|9|601(16)(1)(1)(eng),||
TV|BBC Parliament|205(2)|421(eng),|0|17024|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|10|605(16)(1)(1)(eng),||
RA|BBC R5 Live|0|430(eng),|0|17920|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|11|||
TV|Channel 4|560(2)|561(eng),562(eng),|0|8384|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|12|563(16)(2)(2)(eng),||
TV|E4|570(2)|571(eng),572(eng),|0|8448|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|13|573(16)(2)(2)(eng),||
RA|Heart|0|631(eng),|0|8772|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|15|||
TV|ITV1|520(2)|521(eng),522(eng),|0|8261|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|16|523(16)(2)(2)(eng),||
TV|ITV2|530(2)|531(eng),532(eng),|0|8325|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|17|533(16)(2)(2)(eng),||
TV|ITV3|540(2)|541(eng),542(eng),|0|8294|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|18|543(16)(2)(2)(eng),||
TV|ITV4|600(2)|601(eng),|0|8353|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|19|603(16)(2)(2)(eng),||
TV|More 4|590(2)|591(eng),592(eng),|0|8442|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|20|593(16)(2)(2)(eng),||
RA|RadioMusicShop|0|621(eng),|0|8771|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|21|||
RA|Teletext Cars|0|789,|0|8643|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|22|||
RA|Clyde 1|0|1801(eng),|0|23040|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|23|||
TV|E4+1|501(2)|502(eng),504(eng),|0|22336|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|24|503(16)(1)(1)(eng),||
RA|Premier Radio|0|1701(eng),|0|22976|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|25|||
TV|Sky News|101(2)|102(eng),104(eng),|0|22080|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|26|103(16)(1)(1)(eng),||
TV|Sky Spts News|201(2)|202(eng),204(eng),|0|22144|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|27|203(16)(1)(1)(eng),||
TV|SKY THREE|301(2)|302(eng),304(eng),|0|22208|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|28|303(16)(1)(1)(eng),||
RA|talkSPORT|0|1101(eng),|0|22592|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|29|||
TV|UKTV History|401(2)|402(eng),404(eng),|0|22272|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|30|403(16)(1)(1)(eng),||
RA|Virgin Radio|0|1901(eng),|0|23104|20480|Terrestrial|578166|0|v|34|-1|16|34|8|2|32|0|31|||
TV|BBC NEWS 24|640(2)|641(eng),|0|4415|4100|Terrestrial|505833|0|v|34|-1|16|-1|8|2|32|0|32|643(16)(1)(1)(eng),||
TV|BBC ONE|600(2)|601(eng),602(eng),|0|4164|4100|Terrestrial|505833|0|v|34|-1|16|-1|8|2|32|0|33|603(16)(1)(1)(eng),||
RA|BBC World Sv.|0|1601(eng),|0|26496|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|34|||
TV|Film4|701(2)|702(eng),704(eng),|0|27136|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|35|703(16)(1)(1)(eng),||
TV|f tn|301(2)|302(eng),304(eng),|0|25856|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|36|303(16)(1)(1)(eng),||
TV|Ideal World|501(2)|502(eng),|0|25920|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|37|||
TV|ITV2 +1|601(2)|602(eng),604(eng),|0|27072|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|38|603(16)(1)(1)(eng),||
RA|Kerrang!|0|1301(eng),|0|26304|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|39|||
RA|Kiss|0|1101(eng),|0|26176|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|40|||
RA|Magic|0|1801(eng),|0|26624|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|41|||
RA|oneword|0|1501(eng),|0|26432|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|42|||
RA|Q|0|1901(eng),|0|26688|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|43|||
RA|Smash Hits!|0|1201(eng),|0|26240|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|44|||
RA|SMOOTH RADIO|0|1401(eng),|0|26368|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|45|||
TV|The HITS|101(2)|102(eng),|0|25664|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|46|103(16)(1)(1)(eng),||
RA|The Hits Radio|0|1701(eng),|0|26560|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|47|||
TV|TMF|201(2)|202(eng),204(eng),|0|25728|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|48|203(16)(1)(1)(eng),||
RA|BBC Radio 1|0|6210(eng),|0|14336|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|49|||
RA|BBC Radio 2|0|6226(eng),|0|14400|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|50|||
RA|BBC Radio 3|0|6242(eng),|0|14464|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|51|||
RA|BBC Radio 4|0|6258(eng),|0|14528|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|52|||
TV|bid tv|6273(2)|6274(eng),|0|14272|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|53|||
TV|Five|6017(2)|6018(eng),6019(eng),|0|12866|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|54|6022(16)(2)(2)(eng),||
TV|Five Life|6673(2)|6674(eng),|0|12928|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|55|6678(16)(2)(2)(eng),||
TV|Five US|6689(2)|6690(eng),|0|12992|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|56|6694(16)(2)(2)(eng),||
RA|heat|0|6306,|0|14592|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|57|||
RA|MOJO|0|6322,|0|14656|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|58|||
TV|price-drop tv|6513(2)|6514(eng),|0|15616|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|59|||
TV|QVC|6049(2)|6050(eng),|0|13120|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|60|||
RA|RadioMusicShop-1|0|621(eng),|0|8771|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|61|||
TV|SETANTA SPORTS|6801(2)|6802(eng),|0|16096|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|62|||
RA|Teletext Cars-1|0|789,|0|8643|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|63|||
RA|Teletext Games|0|6754(eng),|0|16128|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|64|||
TV|THOMAS COOK TV|6785(2)|6786(eng),|0|15968|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|65|||
RA|Ttext Holidays|0|6354,|0|14784|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|66|||
TVC|UKTV Gold|6497(2)|6498(eng),|0|15552|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|67|6502(16)(2)(2)(eng),||
TV|BBC THREE|620(2)|621(eng),622(eng),|0|4351|4100|Terrestrial|505833|0|v|34|-1|16|-1|8|2|32|0|68|623(16)(1)(1)(eng),||
TV|BBC TWO|610(2)|611(eng),612(eng),|0|4228|4100|Terrestrial|505833|0|v|34|-1|16|-1|8|2|32|0|69|613(16)(1)(1)(eng),||
TV|abc1|6385(2)|6386(eng),6387(eng),|0|14208|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|70|6390(16)(2)(2)(eng),||
TVC|TopUp Anytime1|6705(2)|6706(eng),|0|16224|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|71|6710(16)(2)(2)(eng),||
TVC|TopUp Anytime3|6737(2)|6738(eng),|0|16288|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|72|6742(16)(2)(2)(eng),||
TV|UKTV Br'tIdeas|301(2)|302(eng),304(eng),|0|25792|24576|Terrestrial|537833|0|v|34|-1|16|34|8|2|32|0|73|303(16)(1)(1)(eng),||
TV|CBBC Channel|620(2)|621(eng),622(eng),|0|4671|4100|Terrestrial|505833|0|v|34|-1|16|-1|8|2|32|0|74|623(16)(1)(1)(eng),||
TV|CITV|550(2)|551(eng),|0|8358|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|75|553(16)(2)(2)(eng),||
TVC|Eurosport UK|6609(2)|6610(eng),|0|16000|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|76|6614(16)(2)(2)(eng),||
TV|CBeebies|201(2)|401(eng),402(eng),|0|16960|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|77|601(16)(1)(1)(eng),||
TV|Community|204(2)|411(eng),415(eng),|0|19968|16384|Terrestrial|529833|0|v|34|-1|16|34|8|2|32|0|78|602(16)(1)(1)(eng),||
TV|Teachers TV|6561(2)|6562(eng),|0|15808|12290|Terrestrial|561833|0|v|23|-1|64|12|8|2|32|0|14|6568(16)(2)(2)(eng),||
TV|Channel 4+1|580(2)|581(eng),582(eng),|0|8452|8197|Terrestrial|481833|0|v|23|-1|64|12|8|2|32|0|79|583(16)(2)(2)(eng),||

---

### Post by Navid73 on 2006-11-01
hi
i want to use my usb tv stick on ubuntu .
anyone can help me?

ARTEC T14 usb:
Support DVB Protocol (ETS 300 744)
USB2.0 High Speed Interface Designed for HDTV
Digital Terrestrial TV and Radio Program Playing
Real Time Digital Video Recording
Schedule Recording
Still Picture Capture
Channel Auto scan at 6/7/8 MHz
EPG (Electronic Program Guide)
Time-Shifting
PIP (Picture in Picture)
MTS (SAP, secondary audio program)
On-Fly Decode software technique (Auto-update channel information)
Multi-language Setup and Application Program
Portable Device without any other extra power

---

### Post by r76 on 2006-11-02
Welcome to the forums!  Help you...?  Well we can try.

Are you running Ubuntu already?  If so which version?  The way we have the card working here requires:
1) Ubuntu Edgy Eft (6.10)
2) Kaffeine (0.8.2) the viewer and recording program
3) some extra codecs, easily downloaded.

If not running Ubuntu yet, why not download and burn an .iso file to CD.  As well as being the install CD this also functions in a more limited capacity as a 'Live CD' allowing you to play with and see if Ubuntu is suitable for you - and makes no changes to your existing software, as it loads into RAM without touching your hard drive at all.  Find the CD images here:
[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
Make sure you download 6.10

---

### Post by mike-g on 2006-11-11
Hi there - I hope some ubuntu guru can help!

I've got the Artec t1 usb tv tuner. Works OK under windows, but I want it to work with linux. So, I have installed the latest Ubuntu (6.10), but nothing happens with Kaffeine - no lights on the usb box itself, no pictures nothing. So I have read the this discussion (and everything else I can find) and have the general idea that I need to do something to the kernel. But what and how? **Can someone be kind enough to post step by step idiot proof commands for me to follow? **Otherwise I have to switch to to windows for tv...shudder... Thanks in advance!

---

### Post by r76 on 2006-11-11
Well I pretty much qualify for 'idiot' status so I can't promise to write an 'idiot-proof' guide.  Still, I am working on writing this up.  In the meantime lets start with are you runnng the live CD or have you installed Edgy (not that it mattered for me, either way the lights came on as soon as I plugged the box in)?  Also are you plugging the box into a hub?  I had power problems doing that.  There is some terminal command to tell what is detected in USB ports but I will have to search for that.

edit:
By the way, I never touched the kernel, compiling that sounds too advanced for me just yet.  Try entering this code in a terminal window (the command lists hardware):
sudo lshw

I get the following relevant section, do you see anything resembling this:

        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf40-bf5f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: DVB-T T1
                   vendor: Ultima
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: driver=dvb_usb_dibusb_mb maxpower=500mA speed=12.0MB/s

---

### Post by mike-g on 2006-11-12
Thanks for replying - this has been driving me crazy!

The lsusb returns this : 

*-usb
                   description: Generic USB device
                   product: AN2235 EZUSB-FX Microcontroller
                   vendor: Anchor Chips, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbtest maxpower=100mA speed=12.0MB/s

But no lights on the box (other than when in Windows on same machine) and nothing to see in Kaffeine etc. I guess this means the firmware loader isnt sending its firmware to the box and waking it up (a guess based on what I've read). This is all on a machine with the latest ubuntu release installed on the harddisk. And the connection is direct to the USB on the motherboard - no hub. Any ideas? Thanks!

---

### Post by r76 on 2006-11-13
So from my understanding, there are two different configurations of the box we are using, mine uses AN2135 chipset and is detected automatically by the kernel.  The output you provided is useful, it shows you have an AN2235 box - and it is not detected, so the driver used is usbtest.

From the following website, they definitely were using different firmwares, I'm not sure if the current working one in the Edgy version of the linux kernel for AN2135 should also work for AN2235.  Sorry not to be more help, but I will keep looking.

[http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php)

> 1. How to use?
1.1. Firmware

Most of the USB drivers need to download a firmware to start working.

for USB1.1 (AN2135) you need: dvb-usb-dibusb-5.0.0.11.fw
for USB2.0 HanfTek: dvb-usb-umt-010-02.fw
for USB2.0 DiBcom: dvb-usb-dibusb-6.0.0.8.fw
for USB2.0 AVerMedia AverTV DVB-T USB2: dvb-usb-avertv-a800-01.fw
for USB2.0 TwinhanDTV Alpha/MagicBox II: dvb-usb-vp7045-01.fw

The files can be found on [http://www.linuxtv.org/download/firmware/](http://www.linuxtv.org/download/firmware/) .

We do not have the permission (yet) to publish the following firmware-files.
You'll need to extract them from the windows drivers.

You should be able to use "get_dvb_firmware dvb-usb" to get the firmware:

for USB1.1 (AN2235) (a few Artec T1 devices): dvb-usb-dibusb-an2235-01.fw
for USB2.0 Hauppauge: dvb-usb-nova-t-usb2-01.fw
for USB2.0 ADSTech/Kworld USB2.0: dvb-usb-adstech-usb2-01.fw
for USB2.0 Yakumo/Typhoon/Hama: dvb-usb-dtt200u-01.fw

---

### Post by mike-g on 2006-11-13
I've downloaded the firmware --- but what to do with it, I haven't a clue! Tried following the instructions on the site, but without any success. Do you know where to put the firmware so it can "found" by the system? Thanks for the help so far..

---

### Post by r76 on 2006-11-15
Sorry not to reply sooner, I'm not exactly sure what to do with the firmware either.  I take it you got the dvb-usb-dibusb-an2235-01.fw NOT dvb-usb-dibusb-5.0.0.11.fw ?
I did find the following page most promising:
[http://www.linuxtv.org/wiki/index.php/Artec_T1_USB_TV_Box](http://www.linuxtv.org/wiki/index.php/Artec_T1_USB_TV_Box)

As it involves meddling with the kernel, why not post on another part of the forum where someone more adept at this sort of thing might be more likely to see your post.  Even if they don't use a DVB device, they might speak linux well enough to interpret that page for you.  It looks relatively simple but I've only switched to linux properly a month ago and most of the terminology on that page is over my head :)

---

### Post by mike-g on 2006-11-21
Thanks for all yr help - I'm a lot closer than I was! I will continue to investigate & will post any results here for others. Really nice to find such a supportive community :-) thanks.

---

### Post by r76 on 2006-12-01
So I found I an issue (and the solution!) regarding automatically switching to a channel when starting a recording. If I had the player on one channel (e.g. BBC One) and have a recording set for later that evening on another channel in the same mux (e.g. BBC Two), Kaffeine would not switch to BBC Two.

Instead it starts recording without changing channel from the same mux which makes the current channel unwatchable quality, and the recording similarly very poor quality.

The problem is a bottleneck in the data speed (this box is only USB1.1 after all), whilst Kaffeine is built to enable users to have multiple boxes/ tuners.
 
Seeing as I only record and never watch live TV on Kaffeine, I want it just to zap to the channel selected in the timer, regardless of mux.

To do this is dead simple, just press the stop button, to stop playing the 'live' stream.  Kaffeine is now open but stopped, and any subsequent timers will flick channel (and mux) properly in the background. :mrgreen:

---

### Post by eiffel on 2007-02-06
After months of having this box and trying to find a decent howto that I could use to get the thing working I finally found one:

[http://www.ubuntuforums.org/showthread.php?t=198423](http://www.ubuntuforums.org/showthread.php?t=198423)

basically it's for a Nebula box instead of an Artec but all you have to do is to download 

[http://www.linuxtv.org/downloads/dvb/firmware/dvb-usb-dibusb-6.0.0.8.fw](http://www.linuxtv.org/downloads/dvb/firmware/dvb-usb-dibusb-6.0.0.8.fw) 

instead of the wget istruction there and then when 'make config' asks you how to configure the Video4Linux/DVB-T source answer n for nebula but m for the 2 DiBcom options.

Worked a treat.  Phhwww.

---

### Post by mmoalem on 2007-03-04
hi there all - finally got somewhere woth my artec t1 (with the an225 chipset. thompson tuner)
it did not work unser edgy no matter how hard i tried so thought i could try latest feisty herd 5 and after following the prvious post instructions it seems to be working, light come on, a firmware seems to be loaded and kaffeine finds channels with autoscan...
this is the furthest i ever got with this card but things are still not all right...
all the channels scanned with kaffeine has snr value of 0, dvbstream cant lock onto any channel i tried and the resulting files are 0byte sized. the card works fine under windows xp software, snr seems to be 50% not great but most channels reception seems fine most of the time so not sure why it wouldnt work as well under ubuntu...
also looking at /lib/firmwares/2.6.20.1 the an2235 firmware has red box with white x on it (see picture) - does any one know what does it mean?

---

### Post by r76 on 2007-03-04
Am not sure what that means.  Furthermore, my setup is broken with the automatic upgrade to the most recent kernel in Edgy 2.6.17.10 to 2.6.17.11, so that Kaffeine no longer detects the box (i.e. digital TV is not an option on the front menu in Kaffeine).  I have to boot into the 2.6.17.10 kernel for now.

---

### Post by mmoalem on 2007-03-04
ok i'm a bit further...
kaffeine works and record streams (image is garbled but it is fine for me as it is on headless server used for recording only)
however dvbstream doesnt work (possibly to do with being feisty herd5) so i'm left with kaffeine but that requires me to login into genome session and than using vnc start kaffeine. 
now is there a way of running the scheduled recording feature of kaffeine in the background without the loging in? run it as a server service kind of thing on boot?
any other program?

---

### Post by panch0 on 2007-03-05
You should be able to run mencoder in the background from cron. Have you tried recording with mencoder?

---

### Post by mmoalem on 2007-03-05
thanks for that idea... got mplayer to dump the channel (no need for reencoding) now need to figure out cron and its a start...
however, it does seem quite cumbersome and basic... maybe theres a way to run this through webmin or something... if only some clever guy wrote a script to run through webmin, a page where you fill in the times, channel and filename and it would insert it into cron... would love to have the ability of scheduling through epg...
well maybe i'm asking too much... it took me a year to get this card working on linux...
cheers
michel

---

### Post by easyease on 2007-03-09
> **r76 said:**
> Am not sure what that means.  Furthermore, my setup is broken with the automatic upgrade to the most recent kernel in Edgy 2.6.17.10 to 2.6.17.11, so that Kaffeine no longer detects the box (i.e. digital TV is not an option on the front menu in Kaffeine).  I have to boot into the 2.6.17.10 kernel for now.yep same problem here, its like one step forward two steps back sometimes eh? lol

---

### Post by r76 on 2007-05-24
OK with a clean install of Edgy, applying all software updates, the box did actually run again.  Strange.

ANYWAY, better news, using Kaffeine or dvb-utils, the [COLOR="Red"]**Antec T1 USB box works great with Ubuntu 7.04 Feisty!**[/COLOR]
(an2135 chipset at least, don't know about those of you struggling with an2235)

To celebrate I have updated my channels.dvb file in page 2 of this thread (see sig) with the current channels.  Also I have tried mythTV following this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

MythTV seems really good too, that is a great guide although scanning needs a little help by doing a confscan first, and I can't seem to delete unwanted channels.  But the program itself seems to be fantastic and when I have more time I'll investigate it fully. Until then Kaffeine is doing all my recording.  I don't watch live TV, just record then use a script which runs ProjectX and mplex to remux removing errors and synch sound, then trim using avidemux and save the mpeg for watching or burning without re-encoding on DVD.

---

### Post by LAGMonkey on 2007-05-26
After reading threads like these, i took the plunge and installed Ubuntu (latest 7.04) and managed to get my box working and running in mythTV. It really is fantastic except for the remote that is bundled with it. Is there any way that i can access the IR reciever using Lirc and program in my own remote for it?

Ive tried using my learning remote but the box jsut refuses to see any other remote but the small, annoying and useless one that came with it.

the IR module on the Atrec T1 is acessable with 

sudo cat /dev/input/event4

ive got a serial IR reciever but i have to connect it through a USB-serial adaptor (called USB-SER! in the device list) but lirc wont see that ether!

to put it bluntly, im rubbish at this lirc lark and im still finding my feet when it comes to linux.

Thank you so much for your time.

---

### Post by LAGMonkey on 2007-05-28
Well my box (AN2235) WAS working on 7.04 but now since ive done a kernel upgrade (via the automatic thing) all i get instead is...

May 28 23:24:57 tony-desktop kernel: [  500.185149] usb 2-2: new full speed USB device using ohci_hcd and address 3
May 28 23:24:57 tony-desktop kernel: [  500.389092] usb 2-2: configuration #1 chosen from 1 choice
May 28 23:24:57 tony-desktop kernel: [  500.392039] dvb-usb: found a 'Artec T1 USB1.1 TVBOX with AN2235 (faulty USB IDs)' in cold state, will try to load a firmware
May 28 23:24:57 tony-desktop kernel: [  500.433121] dvb_usb_dibusb_mb: probe of 2-2:1.0 failed with error -22

so im back to square one again :(

however looking at the messages i also find this further up the page (while booting)

May 28 08:42:17 tony-desktop kernel: [   37.728117] dvb-usb: found a 'DiBcom USB1.1 DVB-T reference design (MOD3000)' in warm state.
May 28 08:42:17 tony-desktop kernel: [   37.746180] i2c_adapter i2c-2: SMBus Quick command not supported, can't probe for chips
May 28 08:42:17 tony-desktop kernel: [   37.746185] dvb-usb: will use the device's hardware PID filter (table count: 16).
May 28 08:42:17 tony-desktop kernel: [   37.748092] DVB: registering new adapter (DiBcom USB1.1 DVB-T reference design (MOD3000)).
May 28 08:42:17 tony-desktop kernel: [   37.758039] DVB: registering frontend 0 (DiBcom 3000M-B DVB-T)...
May 28 08:42:17 tony-desktop kernel: [   37.766029] dibusb: This device has the Panasonic ENV77H11D5 onboard.
May 28 08:42:17 tony-desktop kernel: [   37.772127] input: IR-receiver inside an USB DVB receiver as /class/input/input4
May 28 08:42:17 tony-desktop kernel: [   37.772158] dvb-usb: schedule remote query interval to 150 msecs.
May 28 08:42:17 tony-desktop kernel: [   37.790098] dvb-usb: DiBcom USB1.1 DVB-T reference design (MOD3000) successfully initialized and connected.
May 28 08:42:17 tony-desktop kernel: [   43.289448] Using specific hotkey driver

any ideas?

---

### Post by LAGMonkey on 2007-05-28
new info. Just booted without the Artec plugged in. Let the system boot to desktop and then plugged in the box and i got the following messages...

May 28 23:34:27 tony-desktop kernel: [  131.400852] usb 2-2: new full speed USB device using ohci_hcd and address 2
May 28 23:34:28 tony-desktop kernel: [  131.604708] usb 2-2: configuration #1 chosen from 1 choice
May 28 23:34:28 tony-desktop kernel: [  131.751843] dvb-usb: found a 'Artec T1 USB1.1 TVBOX with AN2235 (faulty USB IDs)' in cold state, will try to load a firmware
May 28 23:34:28 tony-desktop kernel: [  131.794642] dvb_usb_dibusb_mb: probe of 2-2:1.0 failed with error -22
May 28 23:34:28 tony-desktop kernel: [  131.794653] usbcore: registered new interface driver dvb_usb_dibusb_mb
May 28 23:34:28 tony-desktop kernel: [  131.823961] usbtest 2-2:1.0: EZ-USB device
May 28 23:34:28 tony-desktop kernel: [  131.823968] usbtest 2-2:1.0: full speed {control bulk-in bulk-out} tests (+alt)
May 28 23:34:28 tony-desktop kernel: [  131.823975] usbcore: registered new interface driver usbtest

debug

May 28 23:34:27 tony-desktop NetworkManager: <debug info>^I[1180391667.975791] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial'). 
May 28 23:34:28 tony-desktop NetworkManager: <debug info>^I[1180391668.200538] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial_if0'). 
May 28 23:34:28 tony-desktop NetworkManager: <debug info>^I[1180391668.246094] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial_usbraw'). 

syslog

May 28 23:34:27 tony-desktop kernel: [  131.400852] usb 2-2: new full speed USB device using ohci_hcd and address 2
May 28 23:34:27 tony-desktop NetworkManager: <debug info>^I[1180391667.975791] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial'). 
May 28 23:34:28 tony-desktop kernel: [  131.604708] usb 2-2: configuration #1 chosen from 1 choice
May 28 23:34:28 tony-desktop kernel: [  131.751843] dvb-usb: found a 'Artec T1 USB1.1 TVBOX with AN2235 (faulty USB IDs)' in cold state, will try to load a firmware
May 28 23:34:28 tony-desktop kernel: [  131.794627] dvb-usb: did not find the firmware file. (dvb-usb-dibusb-an2235-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
May 28 23:34:28 tony-desktop kernel: [  131.794642] dvb_usb_dibusb_mb: probe of 2-2:1.0 failed with error -22
May 28 23:34:28 tony-desktop kernel: [  131.794653] usbcore: registered new interface driver dvb_usb_dibusb_mb
May 28 23:34:28 tony-desktop firmware_helper[5644]: main: error loading '/lib/firmware/dvb-usb-dibusb-an2235-01.fw' for device '/class/firmware/2-2' with driver '(unknown)'
May 28 23:34:28 tony-desktop NetworkManager: <debug info>^I[1180391668.200538] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial_if0'). 
May 28 23:34:28 tony-desktop kernel: [  131.823961] usbtest 2-2:1.0: EZ-USB device
May 28 23:34:28 tony-desktop kernel: [  131.823968] usbtest 2-2:1.0: full speed {control bulk-in bulk-out} tests (+alt)
May 28 23:34:28 tony-desktop kernel: [  131.823975] usbcore: registered new interface driver usbtest
May 28 23:34:28 tony-desktop NetworkManager: <debug info>^I[1180391668.246094] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_547_2235_noserial_usbraw').

---

### Post by r76 on 2007-05-29
Welcome LAGMonkey, which kernel are you running?  If you boot into the original kernel supplied with Edgy does the functionality return?  If so I suggest setting that kernel as your default.

I don't know about using different remotes, I haven't got that far.  In fact I forgot that I had a remote as I haven't ever really used it even in Windows.  You are right though, you'd need something like a MCE remote to get good functionality out of mythTV.  If you'd asked me before I would have thought you didn't stand a chance getting lirc to work with this box but then you get this line:

May 28 08:42:17 tony-desktop kernel: [ 37.772127] input: IR-receiver inside an USB DVB receiver as /class/input/input4

The hardware seems to be detected but I don't know how lirc works or if you can get input from the receiver translated by lirc e.g. into keystrokes recognised by mythtv.

---

### Post by nick_h on 2007-06-07
I have an Artec T1 with the AN2235 with faulty chip IDs and the Panasonic tuner.

Reading this thread I followed the [Nebula HowTo](http://ubuntuforums.org/showthread.php?t=198423) and can get the driver and firmware loading with the green power light coming on.  The logs also look good, for example:

[   24.976000] dvb-usb: found a 'DiBcom USB1.1 DVB-T reference design (MOD3000)' in warm state.
[   24.992000] dvb-usb: will use the device's hardware PID filter (table count: 16).
[   24.992000] DVB: registering new adapter (DiBcom USB1.1 DVB-T reference design (MOD3000))
[   25.056000] DVB: registering frontend 0 (DiBcom 3000M-B DVB-T)...
[   25.060000] dibusb: This device has the Panasonic ENV77H11D5 onboard.
[   25.064000] input: IR-receiver inside an USB DVB receiver as /class/input/input4
[   25.064000] dvb-usb: schedule remote query interval to 150 msecs.
[   25.080000] dvb-usb: DiBcom USB1.1 DVB-T reference design (MOD3000) successfully initialized and connected.
[   25.080000] usbcore: registered new interface driver dvb_usb_dibusb_mb

However, once at this stage I can't get the box to tune with either scan or dvbtune.

Looking through the linuxtv.org site I found [this](http://linuxtv.org/downloads/snapshots/v4l-dvb-ChangeLog-20061209) change log with contains the following:

[i]"There seems to be an off by one error in the dibusb-mb.c which causes
the "Artec T1 with AN2235" box to be detected as a totally different
box - but it only happens if the Artec is one with the correct USB
IDs. A patch is attached to the second post. However, even with this
patch, the box still won't tune. It will tune using a 2.6.12 kernel
though."[/i]

From reading this thread it seems that at least one person has got this box to work with a later kernel.  I have tried with Dapper and Feisty but not a kernel as old as 2.6.12.  Please would someone let me know if they have got hardware like mine to work, and if so, with which kernel version.

UPDATE:  I did get this working in the end.  I had to visit the #linuxtv IRC channel where there was a very helpful developer.  A bug had been introduced into the latest version of the driver.

---

### Post by r76 on 2007-08-21
UPDATE

I have updated the channels.dvb file for kaffeine on [page 2 of this thread]("http://ubuntuforums.org/showpost.php?p=1684397&postcount=13") as Film4+1 has been replaced by Channel4+1, this is a shame as Film4+1 had more compression and less errors than Film4.  Oh well, now I can look forward to such Channel4+1 programmes as "Location, location, location, location" and "10 years, 1 hour younger"...

---

### Post by outer_space on 2007-08-29
Anyone know whats up with that 'usbtest' driver loading?  I'm trying to write a libusb driver for something and it wont work I suspect because this 'usbtest' driver loads for the device and I wish it wouldnt and never said it could.  I can't easily change the vendor ID of the device i dont think, if that would even work.

---

### Post by nick_h on 2007-08-29
I had the same problem and blacklisted it in /etc/modprobe.d/blacklist

---

