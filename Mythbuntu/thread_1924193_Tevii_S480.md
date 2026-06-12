---
title: "Tevii S480"
date: 2012-02-12
forum: Mythbuntu
---

### Post by AlecJ on 2012-02-12
I recently bought a Tevii S480 from ebay.

Had a fun few days getting it to work, in the end a clean install of 11.10 was necessary in order to have my mceusb remote working as well as the S480 being identified.
Once the drivers were downloaded and placed in /lib/firmware.
```

http://linuxtv.org/wiki/index.php/TeVii_S480

```It all works well, BBC HD with my new Nvidia GT520 is very nice.

But..

The Tevii goes to sleep if not used for any length of time and refuses to wake up, only a reboot wakes the card??

I have 4 Nova dvb-s cards in the other pci slots on the motherboard, they should be on different LNB's looking at different satellites, but at boot they all move around?? so that don't work.
```

udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/dvr0) 
```Tells me they are like clones not one thing to separate them. I got away with this on 10.04 because we never rebooted the system.

How to stop the Tevii from going to sleep?
I have found some help here
```

http://bernaerts.dyndns.org/linux/59-ubuntu-xbmc

```on S3 acpi, maybe the USB part of the card is dozing off?

How to identify Nova dvb-S  's and pin then into the same address at boot?
pees in a pod?

---

### Post by Kronalias on 2012-02-12
I've had a similar hiccup with the adapter order changing between boots.

The solution for me was [HERE]("http://www.mythtv.org/wiki/Device_Filenames_and_udev")

Try it out. Post back here if you get into probs ...

Best, K

---

### Post by AlecJ on 2012-02-12
> **Kronalias said:**
> I've had a similar hiccup with the adapter order changing between boots.

The solution for me was [HERE]("http://www.mythtv.org/wiki/Device_Filenames_and_udev")

Try it out. Post back here if you get into probs ...

Best, K

Still have that page open on my desktop, thats where the udev line came from.

I have noticed the cards have different MAC address printed on them, any idea how to probe a DVB card for a MAC address?
 otherwise they look the same in the terminal.

I think the Tevii card may be ok as when I when to check why it was asleep it turned out to be one of the other cards had taken that adapter number..
So when I put it back in I will pin it to the same address, it's the Nova's I need to differentiate between.

---

### Post by mikulator on 2012-02-13
I have had the same issues and spendt many hours on it.

My best solution is one of two - these work every time and are fairly easy to manage.

1) The adapter_nr module option
2) build a boot script that loads the modules in a specific order.

I had many problems getting the udev rules to work properly

---

### Post by mikulator on 2012-02-13
I just purchased the same card for my new BE. Which guide did you use to install?

---

### Post by AlecJ on 2012-02-13
> **mikulator said:**
> I just purchased the same card for my new BE. Which guide did you use to install?

```
http://linuxtv.org/wiki/index.php/TeVii_S480
```Has the best guide, but installing s2-liplianin onto 10.04LTS broke my mceusb remote?
so I upgraded to 10.10 then the remote worked but broke after I installed s2-liplianin,
this went on till 11.10 where everything worked. cos I only had to put the drivers into /lib/firmware

Do the 
```
cd /usr/local/src wget [http://www.tevii.com/s2_liplianin_1.tar](http://www.tevii.com/s2_liplianin_1.tar) tar xvf s2_liplianin_1.tar cd tevii_s2_liplianin-eb8a914cd499/linux/firmware/ md5sum dvb-usb-s660.fw #2946e99fe3a4973ba905fcf59111cf40  dvb-usb-s660.fw cp dvb-usb-s660.fw /lib/firmware/ 
```bit as it appears to have stopped the "loss of signal after not being used for a while" issue but I'm still testing.

I had to reload the BOIS defaults with all the cards installed as I had many many random freezes??

Not sure about the S3 suspend, I don't use it.



The adapter_nr module option looks good but I can't make it work? my dvb.conf appears no to get read?

I've also ordered a new card to start replacing the Nova S 's, this time I've stuck with Nova and gone for a dual Hauppauge WinTV-NOVA-HD-S2.

---

### Post by mikulator on 2012-02-14
The adapter_nr option needs to be supported by the module.

I am rather new to the card, but from what I can see the only module which supports the option is dvb_usb_dw2102.

you can check it by using 
```

$modinfo dvb_usb_dw2102

```

I  would like to use the card together with 2 other cards I already have  in the system. I will try the option and get back to you.

Cheers

PS I am running on 11.04

---

### Post by mikulator on 2012-02-14
Sorry to be back so fast... it was too easy \\:D/

Or at least it looks that way
**$ nano /etc/modprobe.d/dvb.conf**
Add the following lines in to the file

```

# set adapter numbers for tevii s480
options dvb_usb_dw2102 adapter_nr=4,5

```Reboot and check dmesg
[B]$ dmesg | grep "registering adapter"
[/B][    5.158041] DVB: registering adapter 4 frontend 0 (Montage Technology DS3000/TS2020)... 
[    6.033314] DVB: registering adapter 5 frontend 0 (Montage Technology DS3000/TS2020)...In mythtv everything works fine. This is the easiest way to go!

---

### Post by AlecJ on 2012-02-14
Wow how did you find that?
modinfo dvb_usb_dw2102


```
description:    Driver for DVBWorld DVB-S 2101, 2102, DVB-S2 2104, DVB-C 3101 USB2.0, TeVii S600, S630, S650, S660, S480, Prof 1100, 7500 USB2.0, Geniatech SU3000 devices
author:         Igor M. Liplianin (c) liplianin@me.by
srcversion:     5ADF4A68F0C8B5F0FE13B64
alias:          usb:v1F4Dp3100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD482d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD481d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp00A8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1F4Dp3000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3034p7500d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD660d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3011pB012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD630d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v9022pD650d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04B4p2102d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb
vermagic:       3.0.0-15-generic SMP mod_unload modversions 
parm:           debug:set debugging level (1=info 2=xfer 4=rc(or-able)). (debugging is not enabled) (int)
parm:           keymap:set keymap 0=default 1=dvbworld 2=tevii 3=tbs  ... 256=none (int)
parm:           demod:demod to probe (1=cx24116 2=stv0903+stv6110 4=stv0903+stb6100(or-able)). (int)
parm:           adapter_nr:DVB adapter numbers (array of short)

```I was trying to use
```
# TeVii S480 Twin DVB-S2 USB2.0
options dvb-usb-s660 adapter_nr=5,6
```As thats it's driver?

Ok will try that see what happens.

More worryingly,, last night while watching the Tevii card the system froze, froze so bad the Reset button only forced the system down but would not reboot. Only a power off cold boot worked? 5 times last night..
This happened while using both a Nova and the Tevii, but more often on the Tevii?
There is a kernal update about today for the 3.0 ubuntu 11.10 so we see what tonight brings.
I think I have an unhappy hard drive after all the power downs..

---

### Post by AlecJ on 2012-02-14
Thanks that worked the Tevii card is now at 6 & 7.

Kernal updated, now all frontends are on, sort of soak test.

---

### Post by mikulator on 2012-02-14
SUPER!

I have used the adapter_nr option before and remember that I had to do some investigating before finding relevant modules and then having to hope they had the option implemented.

Regards to your freezes I have read about similar before and decided to wait with the upgrade to kernel 3.0. This in turn gives a little challenge with the s480 card.

---

### Post by mikulator on 2012-02-14
Did you get the card to work under 10.04 or 10.10?

I had success under 11.04 but had problems with other cards. I want to go back to the version I can work with.

Cheers for your input

---

### Post by AlecJ on 2012-02-14
Yes got it working in 10.04LTS and 10.10 and 11.04, with the s2-liplianin drivers but it kept breaking the mceuse remote, moving from Lirc to kernal based support.

I spent hours trying to get the Lirc to read /dev/lircd and playing with ir-keytable, in the end I tried 11.10 and all worked. Well I still need to research how to get my remote key map uploaded.

By the way no freezes yet, 2 frontends one on each Tevii adapter playing bbc news.
I so do hope it was a bad kernal causing that..

How did you find the relative modules?

---

### Post by mikulator on 2012-02-14
well been working a good part of the evening on the problem and godt it all to work... i am pleased with the tevii s480 card.

I got all my cards to boot and reboot with the allocated adapter numbers. My post above does work and I hope it does for you too.

finding the relevant module is a matter of following the bread-crumbs so to say.

1) dmesg -> a line noting the dw2102 attached to ds3000
2) lsmod -> looking at all related modules
3) modinfo <module name> -> check if the noted modules support the adapter_nr option

hope it helps

cheers

---

### Post by AlecJ on 2012-02-14
No crash's/freezes tonight, so I guess the kernal update fixed that and the Tevii card is working ok but only time will tell.
Thanks for the heads up on the modules, bread crumbs indeed!

My new Win TV nova turned up tonight, I going to leave it a few days, it all seems to working don't want to muddy the waters just yet.

This incarnation of our myth box have been trouble free for 2 years, the Tevii card and major upgrades has been stressful. You don't realize how much of a part of life it becomes until it stops working, we have all our music, photos and dvd's on it. Nearly 3Tb of stuff that you can't live without, apparently?

Thanks for your help.

---

### Post by AlecJ on 2012-02-15
Bad news.
Everything was working well last night, but this morning when I tried.
Both Tevii cards have lost signal, took a while to get switch to one of the Nova's which works fine.

I need a way to prevent these cards dozing off, or at least a way to wake them up.

dvbshop-tv said i need to unload and reload the modules but that was after suspend
I never turn off the Myth box and i don't use suspend?

Really annoying

---

### Post by mikulator on 2012-02-15
Could it be something in your bios?

As my tevii s480 card is in a new system that I don't use I should be able to test the issue. E.g. leaving it turned on then notice if they work after X hours.

How many hours of "idling" do you think you had?


Cheers


Anothering thing I noticed is that seeing as the card actually is a USB hub hosting 2 usb dvb units it does not boot as fast at a pci based dvb tuner card.

---

### Post by AlecJ on 2012-02-15
I stopped watching it last night at 1.30am then tried to watch again at 8.30am. it's still got no signal now at 11.30am, been using one of the Nova's for homes under the hammer.

I just switched to it again, first you get 0% signal-No Lock ,then 77% signal- partial Lock, then 80% signal-Lock but no picture just really low signal bit's flashing on the screen and bit's of audio then Myth errors out with frame buffer error.

This is the reply I got from dvbshop-tv ebay:-

Hello,

I doubt that an exchange to another PCIe card will help, as the Standby issue, especially in Linux is mainly based on handling from Mainboard.
If PC goes to standby, it usually has to shut down the power to the PCIe bridge. Once it wakes up again, it should reproduce the power to the PCIe card and
then re-initialize it, which does not happen in your case.

In your case your mainboard seems to provide voltage to the PCIe bridge, even if it is in standby, maybe not 3.3V, but a lower voltage, making the device (Tevii)
as "reserved" or "occupied" to the system (Linux).

Nevertheless there are several guides, how to make it work in Linux, Ubuntu etc.

[http://www.vdr-portal.de/board16-video-disk-recorder/board85-hdtv-dvb-s2/102390-tevii-s480-dual-sat-pcie-installation-und-technische-infos/](http://www.vdr-portal.de/board16-video-disk-recorder/board85-hdtv-dvb-s2/102390-tevii-s480-dual-sat-pcie-installation-und-technische-infos/)

Finally you need the "reload after wakeup" tool/script, to solve your problem, which isn't driver or hardwarerelated.



- dvbshop-tv


I replied saying I don't use standby (that I know of).

---

### Post by mikulator on 2012-02-15
do you supply the card with "extra" power via the floppy power cable?

---

### Post by AlecJ on 2012-02-15
Yes thats installed.

---

### Post by AlecJ on 2012-02-15
Ok well had to remove the card, fed up with it, not passed the wife factor.

Going to return it, maybe look at the TBS dual dvb-S2

---

### Post by mikulator on 2012-02-16
arh... I hope I don't run into the same issue. This morning - after 12 hours of "ideling" - I was still able to get a picture.

my WAF has been bleeding over the past 6 months, the patient is in intensiv care, but their is still hope for survival. The only thing I need is more tuners and HDD space... we are recording like mad

---

### Post by AlecJ on 2012-02-16
I wonder if my card was faulty then?
I rebooted and it worked but after 2 hours (watching a DVD) it lost signal again, so i had to take it out.

---

### Post by mikulator on 2012-02-16
I will try again this evening. Tomorrow I will test with HD channels.

But yes your card could be defect. Do you have another PCIe slot you could test it in?
Worst case would be if your mobo is at fault.

The other dvb cards I use are TechnoTrend S2-3200 Budget cards and those I will not recommend - slow tuning and HD does not really work.

---

### Post by AlecJ on 2012-02-16
My motherboard [(asus M2N66)]("http://www.amazon.co.uk/Asus-Mainboard-Socket-GeForce-Channel/dp/B001UNI9IQ/ref=sr_1_2?ie=UTF8&qid=1329403028&sr=8-2") has 2 PCI-e slots but one in covered by the heat sink of the video card, I paid much less of the price amazon is asking which is mad!

The card was detected fine and worked, both tuners were in use for 13 hours continuously. it's this losing signal when idle that caused the problems.
I think that rules out the motherboard?

The card is in the post now, on it's way back to Germany not wasting anymore time on it.

I also note the seller has reduced this card by £10 so I guess he is having a few problems with it.

Will be looking at other cards for the S2 channels, The Nova S2 I ordered arrived but was returned as it was sold as a dual tuner which it's not, only 1 LNB input and a price tag of £108 for a single tuner is a non starter.

The TBS quad 6984 has working Linux drivers and I've seen it at £160 so £40 per tuner which is pretty good.

I really hope you have a better experience with the Tevii s480.

---

### Post by mikulator on 2012-02-17
Well I have been testing it to see if it drops its signal at any point and still now issues.

I left the machine on for 14 hours without any sat cable connected. Reconnected and got instant picture. Now I will leave it on a channel with the cable connected to see if it looses the picture at any point.

What else could I test?

I fully understand why you returned the card and I also would go for the TBS as an alternative.

---

### Post by AlecJ on 2012-02-17
Sounds like your card is working well.
I had no other issues with the card after I got it working, just this losing signal.

Shame really as the picture from it was very good.
The card stayed "found" by the system, so not like it was asleep and you had to wait for it to wake like waiting for a usb hard drive to spin up.

more like the one of the amplifiers powered down on the card, but thats so deep into the firmware how would you be able to power it back up or stop it powering down?
I also had problems with the onboard sata not finding the disks when the Tevii card was plugged in, that was why it was "hanging" at boot.

Maybe I will look only at full size PCI DVB-s2 cards?

I hope the German seller plays ball, they have not emailed me.

My box is much happier now, the stability has returned, the picture is not as good from the Nova cards but then they are a few years old now.

Whats your dish setup? I have 2 quad LNB's 1 looking at 28.2 and the other looking at 19.2 on a side arm mounted on a 90cm dish. Bags of signal no rain fade anymore.

---

### Post by mikulator on 2012-02-17
I would for sure google all I can to be sure to find a card that is well supported in this and Mythtv forum.

the TBS cards look nice but I don't know how well supported they are in the different forums.

Happy hunting and when you have decided please post it here as a "solution"

Cheers

PS. I have one quad lnb also on a 90 cm dish. I am in Denmark. My new build is based on a Asus M4A785TD-M EVO rev 1.02G which support my old PCI cards as well as 2 PCIe cards. This a 100% BE so no need for the nvidia vdpau support.
3x500GB HDD for recordings and 1x250 HDD for OS and DB.

---

### Post by AlecJ on 2012-02-18
If your setup is a backend only how do you get the HD signal out to the frontends? When I try to stream HD across my network I find it too slow, I run a 1Gb router with a 1Gb hub?

I was left thinking the backend/frontend is the only one that can "play" the HD dvb-s2 stuff.

My little laptop in the kitchen when trying to watch HD gives me 2 screens split across the middle that update very very slowly, takes ages to get it to change off the HD channel.

I've not played too much as I was busy with the card issues.

---

### Post by mikulator on 2012-02-18
I also have a gigabit network, but no problems with HD.

A good picture is often dependant on the FE and its GPU. I know that Nvidia currently provide best support under linux and therefor also for HD.

Read more here

[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

And HD material cannot be viewed over wifi - it is too slow.

---

### Post by nickrout on 2012-02-18
> **AlecJ said:**
> If your setup is a backend only how do you get the HD signal out to the frontends? When I try to stream HD across my network I find it too slow, I run a 1Gb router with a 1Gb hub?

I was left thinking the backend/frontend is the only one that can "play" the HD dvb-s2 stuff.

My little laptop in the kitchen when trying to watch HD gives me 2 screens split across the middle that update very very slowly, takes ages to get it to change off the HD channel.

I've not played too much as I was busy with the card issues.

Does the laptop run an ATI card? If so switch to a different deinterlacer.

---

### Post by AlecJ on 2012-02-20
I upgraded my old Nvidia 9400GTto a fanless GT520, to get VDPAU working properly.
The 9400gt could only get slim VDPAU without tearing, but the 520 has no problem. I'm on the latest drivers now as well
```
[COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current[/COLOR]
```The old IBM thinkpad in the kitchen has the problem with the HD feeds, I probably need to set up it's screen better.
Not tried WIFI but I guess even 802n would be too slow.

I thinks it's got intel graphics, will look

---

