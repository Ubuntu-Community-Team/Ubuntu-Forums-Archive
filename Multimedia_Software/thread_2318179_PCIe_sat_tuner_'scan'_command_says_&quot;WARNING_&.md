---
title: "PCIe sat tuner 'scan' command says: &quot;WARNING: &gt;&gt;&gt; tuning failed!!!&quot;"
date: 2016-03-23
forum: Multimedia Software
---

### Post by torbengb on 2016-03-23
I'm at my wits' end and hope you can help me out:
TLDR:
[LIST]
[*]I've installed a satellite tuner card in my computer, but the 'scan' command does not find any channels; instead, it returns that ugly error: "WARNING: >>> tuning failed!!!"
[*]I believe I have ruled out faults with the dish alignment, LNB, coax cable, physical tuner card, driver software, motherboard, and the basic OS itself.
[*]I have not been able to find useful information on this scan error message, so I still don't precisely know what it means! **How can I troubleshoot and fix this?** *or where can I get the best help for this?*
[/LIST]

Sorry for this wall of text, but I want to show what I've already done:

**Details - first card:**
[LIST]
[*]The first card I tried was **[TBS model 6928SE]("https://linuxtv.org/wiki/index.php/TBS6928")**.
[*]This was on my existing **Ubuntu 14.04.4** machine.
[*]I installed the card drivers as per vendor instructions, then also applied the latest available firmware as per vendor instructions. I also updated the firmware of [my motherboard]("http://www.asrock.com/mb/intel/h87m-itx/") to ensure it has full *PCI-E1.0a* support.
[*]The command *dmesg | grep -i dvb* shows that the card is properly installed and drivers are loaded.
[*]The command *scan -vvvvv /usr/share/dvb/dvb-s/Astra-19.2E* resulted identical outputs:
> scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
tune to: 12551:v:0:22000
DiSEqC: switch pos 0, 13V, hiband (index 2)
diseqc_send_msg:56: DiSEqC: e0 10 38 f1 00 00
DVB-S IF freq is 1951500
tuning status == 0x00
tuning status == 0x00
[...]
WARNING: >>> tuning failed!!!
[*]TBS customer support was not very helpful here. After some basic error-checking, they asked for ssh access to my computer, which I politely declined. (I will not give anyone full and unmonitored access to any computer I own.)
[*]I checked that the coax cable has a solid electrical connection from the dish to the computer. I also replaced the LNB on the sat dish, just to make sure that one was not the source of the problem. And Still that "*tuning failed*" error persisted.
[*]The dish itself is properly aligned for the satellite because that was done using a "sat finder" device. And there is nothing in the line of sight.
[/LIST]

**Details - second card:**
[LIST]
[*]Thinking that maybe something in my computer is messed up, I decided to wipe the disk and install Ubuntu 14.04.4 LTS from scratch, then try with a different card.
[*]The second card I tried was **[DVBSky model S950C]("https://linuxtv.org/wiki/index.php/DVBSKY_S950C")**. Again, drivers and firmware was also installed as per vendor instructions, and the command dmesg | grep -i dvb shows that the card is properly installed and drivers are loaded.
[*]The command *scan -vvvvv /usr/share/dvb/dvb-s/Astra-19.2E* still gives me that damn error.
[*]This continued failure seems to rule out a defective tuner card. It seems to be something elusive about the software, but I'm not experienced enough to figure it out. Help?
[/LIST]

---

### Post by mörgæs on 2016-03-26
Have you tried 16.04?

---

### Post by torbengb on 2016-03-26
> **mörgæs said:**
> Have you tried 16.04? I have not tried this, no. It has not even been released yet, so forgive me for presuming that the current LTS would be a wise choice. I can try (the beta of) 16.04 but may I ask why you think that might work better?

---

### Post by mörgæs on 2016-03-26
The main rule is that new hardware requires new software. I am aware that 16.04 is still in beta but still it's worth to try it.

---

### Post by blm-ubunet on 2016-03-26
You've done all the hard work possibly just the scan tools are no good.
The dvb scan tools in 14.04 (& likely 16.04) are well past their use-by-dates.
The stock scan tools do not work with dvb-s2/t2.
[https://www.linuxtv.org/wiki/index.php/Frequency_scan#Scan_apps_that_don.27t_require_an_initial_channel_file](https://www.linuxtv.org/wiki/index.php/Frequency_scan#Scan_apps_that_don.27t_require_an_initial_channel_file)

The stock std tools work okay here but I have built "w_scan" from source & have found it to be very useful.

As you're building kernel modules you need to be careful with kernel updates, be sure to have kernel headers generic meta package installed & read up on "dkms".

---

### Post by torbengb on 2016-03-26
"Scan" might simply be broken?! Now there's a possibility that never even crossed my mind o_O Thank you!

"Building from source" ... 
"have kernel headers generic meta package installed" ... 
"dkms" ... 
uh-oh, what have I gotten myself into?? This is completely new to me, I'm only a normal user (as far as "normal" applies Linux users). I've only "built from source" as it was described in the installation steps for the driver, but I don't actually know what those steps mean or do. 

Will I have to actually *learn and understand* building and other "deep Linux" stuff? [SIZE=1]I just wanted to watch tv...[/SIZE]

---

### Post by blm-ubunet on 2016-03-26
Just a possibility your "scan" is broken..
As "w_scan" is fairly easy to build, it must be worth a bash..
And/or need to find more debug info with alternative/additional scan options or from errors in "dmesg".

The kernel updates/dkms is an issue for externally supplied kernel modules from TBS (& nVidia) for example. TBS has to build to support a range of kernel versions, go outside of this compatible range & it stops working. Without DKMS you have to recompile against kernel headers with every update..

I did think that there was a recent FOSS driver for TBS h/w..
TBS themselves are probably grateful if that is the case!

TeVii h/w has built-in drivers. I think the built-in support for tuners for dvb-s2/t2 has not keep pace with market.

Once you get it working you'll have completely forgotten about ever watching TV!

---

