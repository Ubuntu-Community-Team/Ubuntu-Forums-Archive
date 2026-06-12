---
title: "Open Source Firmware for b43"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2009-01-30
Has anyone tried this out yet?  It was developed by [OpenFWWF]("http://www.ing.unibs.it/openfwwf/") to help replace the proprietary firmware that is currently being used by the b43 module.  It currently works with open networks and WPA/WPA2.  The firmware has been successfully tested with the following cards:
4306 rev 03
4311 rev 01
4318
4320
They are currently looking for more people to test it out to see if it works with any of the b43 supported cards.

If you are able to use the b43 module and would like to test it out, you may try this [guide]("http://linuxfans.keryxproject.org/?page_id=54").

bviktor also has a guide that he created that can be found [here]("http://wiki.frugalware.org/index.php/B43_with_open_source_firmware").

If you do try it out, please let us know if it works or not and include the following information:
```
lspci -nnm|grep 14e4
```

---

### Post by Ayuthia on 2009-01-30
I have tested out the firmware on my HP laptop and it works with the open network and with WPA2.

My lspci -nnm info:
```
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Hewlett-Packard Company [103c]" "BCM4311 802.11b/g Wireless LAN Controller [1363]"
```

---

### Post by kevdog on 2009-01-30
Ill try this solution this weekend.  Thanks for the heads up.

---

### Post by kevdog on 2009-01-31
Posting using the openfwwf firmware for my bcm4306 rev 03 card.  Using WPA2 encryption to boot! :)

02:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Device [4320]"


Just a few points regarding the instructions:

#1 - Bison needs to be installed as a dependency
#2 - Please include instructions for upgrading from the git tree
#3 - Please also include instructions on how to fall back to the previous closed source b43 firmware
#4 - Anyway to prove that the opensource firmware is indeed the firmware I am currently using?  Command line output or log output?

I think those would be useful additions to your guide! Thanks.

Anyway I can test the performance of this driver and make any reasonable comparison to the closed source b43 firmware.

---

### Post by Ayuthia on 2009-01-31
The documentation has been updated to reflect your comments.  As for verifying that you are using the open-source version, once the wireless card is up (via sudo ifconfig wlan0 up) you should see that dmesg will reflect that you are using the open source firmware:
```
b43-phy4: Loading OpenSource firmware version 410.31754 (Hardware crypto not supported)
```

kevdog- Let me know if you don't see that info in dmesg.  I am currently running in gentoo with debug compiled for the b43 module but I think that the message shows in Ubuntu also.

The only tests that I have done is download files on the net and compare the speeds with the proprietary version.  I have not seen any differences.  I do plan to test out copying files over the network just to see if there are any issues.

Thanks for letting me know what was missing in the guide, kevdog!

---

### Post by Boomhauer on 2009-01-31
this is great work!  broadcom drivers have been an issue for many who come to ubuntu.
my card
```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```
my dmesg
```
b43-phy0: Loading OpenSource firmware version 351.11970 (Hardware crypto not supported)
```
EDIT: also in the guide, i had to install flex to get b43-tools/assembler to make properly.

---

### Post by kevdog on 2009-01-31
Here is what I got (any relevance to the old device firmware?):

```

[ 1560.498378] b43-phy1: Loading OpenSource firmware version 351.11970 (Hardware crypto not supported)
[ 1560.498422] b43-phy1 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[ 1560.498432] b43-phy1 warning: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).

```

---

### Post by Ayuthia on 2009-01-31
I have made the updates to add flex and changed the docs to reflect the 5.1 firmware instead of 5.0.  As for the old firmware message that was with version 5.0.  [Version 5.1]("http://www.ing.unibs.it/openfwwf/firmware/openfwwf-5.1.tar.gz") reflects the newer firmware so "download the latest firmware" message goes away.

---

### Post by kevdog on 2009-01-31
Is there an svn or cvs version of the firmware available since this seems like the easiest method to update the firmware?

---

### Post by Ayuthia on 2009-01-31
> **kevdog said:**
> Is there an svn or cvs version of the firmware available since this seems like the easiest method to update the firmware?

This has been the only way that they have presented it.  I can ask the developers of the firmware to see if they have any other methods like cvs/svn/bzr/git (All three letters!!).

---

### Post by kevdog on 2009-01-31
Whats my problem?  I dowloaded and compiled the 5.1 firmware and copied it to the /lib/firmware/b43 directory, reloaded the driver (via modprobe -r/modprobe), but am still getting the following message:
[45972.347336] b43-phy1: Loading OpenSource firmware version 351.11970 (Hardware crypto not supported)
[45972.347373] b43-phy1 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[45972.347382] b43-phy1 warning: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).


---Edit -- Scratch That - I guess its useful to actually bring the device up to reveal the new version with sudo ifconfig wlan0 up:
[56219.232224] b43-phy0: Loading OpenSource firmware version 410.31754 (Hardware crypto not supported)

---

### Post by bviktor on 2009-05-03
hi everyone,

i've also made a howto for this. the linuxfans howto helped me a bit with modprobing, so thanks to Ayuthia;)

you can find it here:

[b43 with open source firmware]("http://bviktor.bplaced.net/?b43")

it would be great if someone made a package for openfwwf so that ubuntu would support b43 cards out-of-box. even modprobe.d hacking will be unnecessary within a few kernel releases, more info in the howto

---

### Post by Don Cox on 2009-05-04
This solution to the BCM4318 problem looks extremely interesting. If I tried it with the live version of 9.04 is it guaranteed that the computer would return to its original state afterwards?

I've stuck with 7.04 as no subsequent version of Ubuntu has worked totally satisfactorily with BCM4318 and Broadcom firmware. I do not even wish to install 9.04 or any future distro unless I am convinced that it works perfectly with the live version beforehand.

---

### Post by bviktor on 2009-05-04
> **Don Cox said:**
> If I tried it with the live version of 9.04 is it guaranteed that the computer would return to its original state afterwards?

of course there's no guarantee. but there's only one way to find out: try it ;)

anyway, i see no reason why it wouldn't do so

all i can say is i have the same card and it works for me nicely on frugalware-current :)

---

### Post by bviktor on 2009-05-05
now i tried it on my laptop with a bcm4318 inside. followed the instructions and it worked with the 9.04 live cd:

[[IMG]http://img11.imageshack.us/img11/373/screenshotvbq.th.png[/IMG]]("http://img11.imageshack.us/img11/373/screenshotvbq.png")

---

### Post by Don Cox on 2009-05-06
Thank you for taking all that trouble Viktor. My knowledge of Linux is much more limited than yours. When I understand the commands better I will give the open source a try with live 9.04.

Kind regards

---

### Post by bviktor on 2009-05-06
> **Don Cox said:**
> Thank you for taking all that trouble Viktor. My knowledge of Linux is much more limited than yours. When I understand the commands better I will give the open source a try with live 9.04.

Kind regards

no problem at all :) i'm no expert, i just like to experiment ;) the commands are not that complex, and i put up the explanation too ;) on a live system there's relatively small chance to ruin anything, so nothing to lose (besides time of course) :)

---

### Post by unipsycho on 2009-05-06
> **Don Cox said:**
> I've stuck with 7.04 as no subsequent version of Ubuntu has worked totally satisfactorily with BCM4318 and Broadcom firmware. I do not even wish to install 9.04 or any future distro unless I am convinced that it works perfectly with the live version beforehand.

I am also very interested in knowing when/if Ubuntu will support a workable solution for b43 out-of-the-box. I've had to advise a friend who has two laptops using the broadcom cards NOT to upgrade beyond 8.10. His initial install went well (sans wifi), but it took almost three hours just to get a working wireless interface. I don't miss doing that kind of support over the phone and I have no desire to do it again when/if upgrading to/beyond 9.04 breaks the b43. Walking a client through command line instructions over the phone can get pretty ugly.

---

### Post by bviktor on 2009-05-06
> **unipsycho said:**
> I am also very interested in knowing when/if Ubuntu will support a workable solution for b43 out-of-the-box. I've had to advise a friend who has two laptops using the broadcom cards NOT to upgrade beyond 8.10. His initial install went well (sans wifi), but it took almost three hours just to get a working wireless interface. I don't miss doing that kind of support over the phone and I have no desire to do it again when/if upgrading to/beyond 9.04 breaks the b43. Walking a client through command line instructions over the phone can get pretty ugly.

well, if enough users try it and it works for them, there might be place for a brainstorm idea. i'm not an active ubuntu user so i don't think i'm the proper person for such actions :)

---

### Post by unipsycho on 2009-05-06
> **bviktor said:**
> well, if enough users try it and it works for them, there might be place for a brainstorm idea. i'm not an active ubuntu user so i don't think i'm the proper person for such actions :)

Agreed. Also, if I had a Broadcom card I could tinker with, I'd be more than happy to do any testing I could. Unfortunately, my friend and his machines are about six hours away and I'm not going to do any testing with him over the phone. So, I hope there are some enterprising folks willing to help get this worked out. Or someone could donate a laptop with a broadcom chipset to me. ;-)

---

### Post by MilesCrew on 2009-05-13
I'm trying to get this to work with my Dell Latitude X300 with TrueMobile 1350 (Broadcom 4306, 14E4-4320). I've gone through all the steps, but messages always shows that it's looking for b43legacy. Says something like...

```
b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
input: b43legacy-phy0 as /devices/virtual/input/input11
Cannot find firmware file 'b43legacy/ucode4.fw'
```

This is on an absolutely fresh install of Ubuntu Jaunty 9.04 32-bit. I literally came up from the fresh install and worked through the commands. I have NOT enabled the b43legacy driver that I was notified about. How can I get this working? I've tried everything to get this card working in 9.04 including ndiswrapper, wicd, etc. The most I ever got was the ability to connect to open networks but never any secure ones (WPA-PSK nor WPA-TKIP with PEAP).

---

### Post by bviktor on 2009-05-13
> **MilesCrew said:**
> I'm trying to get this to work with my Dell Latitude X300 with TrueMobile 1350 (Broadcom 4306, 14E4-4320). I've gone through all the steps, but messages always shows that it's looking for b43legacy. Says something like...

```
b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
input: b43legacy-phy0 as /devices/virtual/input/input11
Cannot find firmware file 'b43legacy/ucode4.fw'
```This is on an absolutely fresh install of Ubuntu Jaunty 9.04 32-bit. I literally came up from the fresh install and worked through the commands. I have NOT enabled the b43legacy driver that I was notified about. How can I get this working? I've tried everything to get this card working in 9.04 including ndiswrapper, wicd, etc. The most I ever got was the ability to connect to open networks but never any secure ones (WPA-PSK nor WPA-TKIP with PEAP).

how about trying to unload the b43legacy module and loading the b43 one?

---

### Post by Ayuthia on 2009-05-13
> **MilesCrew said:**
> I'm trying to get this to work with my Dell Latitude X300 with TrueMobile 1350 (Broadcom 4306, 14E4-4320). I've gone through all the steps, but messages always shows that it's looking for b43legacy. Says something like...

```
b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
input: b43legacy-phy0 as /devices/virtual/input/input11
Cannot find firmware file 'b43legacy/ucode4.fw'
```

This is on an absolutely fresh install of Ubuntu Jaunty 9.04 32-bit. I literally came up from the fresh install and worked through the commands. I have NOT enabled the b43legacy driver that I was notified about. How can I get this working? I've tried everything to get this card working in 9.04 including ndiswrapper, wicd, etc. The most I ever got was the ability to connect to open networks but never any secure ones (WPA-PSK nor WPA-TKIP with PEAP).

It looks like you might have the firmware in /lib/firmware/b43 instead of /lib/firmware/b43legacy.  Can you post the results of:
```
ls /lib/firmware/b43
ls /lib/firmware/b43legacy
```
If you are using the open source firmware, you can try and copy the files into /lib/firmware/b43legacy.

---

### Post by MilesCrew on 2009-05-14
A couple of things...

Yes, I tried removing the b43legacy by running

```
modprobe -r b43legacy
```

This probably has something to do with it. Per the instructions, I was supposed to rename /lib/firmware/b43 to /lib/firmware/b43-proprietary. Well, it doesn't exist on a fresh install, so I actually just created the directory. To make sure, I also created /lib/firmware/b43legacy and copied the firmware files to both directories...but still gives "cannot find firmware file".

Another problem is probably that when I follow the instructions and build the firmware files, it gives me a ucode5.fw, not ucode4.fw like /etc/messages is complaining about.

What's up here? I don't have the /lib/firmware/b43 directory to begin with and the instructions produce a ucode5.fw. Is it all because I'm running 9.04 which came out after these instructions?

---

### Post by Ayuthia on 2009-05-14
> **MilesCrew said:**
> A couple of things...

Yes, I tried removing the b43legacy by running

```
modprobe -r b43legacy
```

This probably has something to do with it. Per the instructions, I was supposed to rename /lib/firmware/b43 to /lib/firmware/b43-proprietary. Well, it doesn't exist on a fresh install, so I actually just created the directory. To make sure, I also created /lib/firmware/b43legacy and copied the firmware files to both directories...but still gives "cannot find firmware file".

Another problem is probably that when I follow the instructions and build the firmware files, it gives me a ucode5.fw, not ucode4.fw like /etc/messages is complaining about.

What's up here? I don't have the /lib/firmware/b43 directory to begin with and the instructions produce a ucode5.fw. Is it all because I'm running 9.04 which came out after these instructions?

It might be possible that the open source firmware does not work with the b43legacy cards.  If dmesg is looking for ucode4.fw, then it most likely won't work.  Most of the conversations with the open source have been with the 4311, 4312, and the 4306 (rev 03) cards.

Can you post your lspci -nn info and the results of:
```
dmesg|grep b43
```

---

### Post by bviktor on 2009-12-22
just a note, my howto has moved to the [frugalware wiki]("http://wiki.frugalware.org/index.php/B43_with_open_source_firmware")

---

### Post by raikou on 2009-12-23
I might try this later on and report my findings.

i've got a 14e4:4315 (BCM4312 LP-PHY) wireless card, which so far has been tricky to set up in Karmic.

---

### Post by bviktor on 2009-12-23
> **raikou said:**
> I might try this later on and report my findings.

i've got a 14e4:4315 (BCM4312 LP-PHY) wireless card, which so far has been tricky to set up in Karmic.

that one will be tricky. there's probably something wrong with the atom platform in this regard. the bcm43xx-dev mailing list is full of those dma errors, and the devs still couldn't find the solution...

---

### Post by onurozcelik on 2010-01-08
Hi

I am going to test the driver on my laptop
But I have a small problem.
I am very new to linux .conf files. I read the frugalwiki but I don't understand what I need to write in b43.conf.

Can somebody please help

---

### Post by onurozcelik on 2010-01-08
At least I figured out what I need to write in b43.conf.:D.
And my wireless works now. Thank you for developing such a driver. I always have a problem with my Broadcom wireless driver under Ubuntu. I think this driver solves my problem.

---

### Post by onurozcelik on 2010-01-08
I guess I was a bit hurry about .conf files. 
Can somebody explain what I need to write inside b43.conf file. Because I got error when I write sudo modprobe b43 to console.
Currently I left it blank and my wireless still works.

---

### Post by Ayuthia on 2010-01-08
> **onurozcelik said:**
> I guess I was a bit hurry about .conf files. 
Can somebody explain what I need to write inside b43.conf file. Because I got error when I write sudo modprobe b43 to console.
Currently I left it blank and my wireless still works.

If I recall correctly, there are some things that the open source firmware is not able to do right now so we need to add some options to the b43.conf file so that the module does not use those features.  They should be:
```
options b43 qos=0
options b43 nohwcrypt=1
```

---

### Post by onurozcelik on 2010-01-08
Thanks Ayuthia

---

### Post by bviktor on 2010-01-08
thanks for the question, i added explanation to the wiki

---

### Post by bkratz on 2010-01-08
> **bviktor said:**
> thanks for the question, i added explanation to the wiki

I was just curious, I went to the location specified in the first post as the guide, I got a 404 not found; where is the mentioned wiki? I don't even have one of these, this is just for knowledge.

---

### Post by bviktor on 2010-01-08
> **bkratz said:**
> I was just curious, I went to the location specified in the first post as the guide, I got a 404 not found; where is the mentioned wiki? I don't even have one of these, this is just for knowledge.

well i posted a link on the [previous page](http://ubuntuforums.org/showpost.php?p=8545927&postcount=26) :)

anyway, openfwwf may [make it](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513974) into debian

---

### Post by bkratz on 2010-01-08
Thanks, I admit I only looked at the first page and the last--sorry. I guess I better do better reading the wiki!

---

### Post by Ayuthia on 2010-01-08
> **bkratz said:**
> I was just curious, I went to the location specified in the first post as the guide, I got a 404 not found; where is the mentioned wiki? I don't even have one of these, this is just for knowledge.

Thanks for pointing it out.  I forgot to update the link.

---

### Post by onurozcelik on 2010-01-14
Guys

Are there any known poor internet speed issues exist with this Open Source Firmware?

---

### Post by Ayuthia on 2010-01-14
> **onurozcelik said:**
> Guys

Are there any known poor internet speed issues exist with this Open Source Firmware?

I have not heard of any.  You can always try it out first to see if it works well for you and if you don't like it, you can always go back.

---

### Post by onurozcelik on 2010-01-15
> **Ayuthia said:**
> I have not heard of any.  You can always try it out first to see if it works well for you and if you don't like it, you can always go back.

You maybe misunderstand me. My intention is not go to back to ndiswrapper or b43-fwcutter. Because they either do not work for me properly.  I am grateful for open source firmware.

I should tell my problem.

Two days ago I have no poor internet speed issues.
Then I updated my system and I am now using kernel version 2.6.31-18. After that update my internet speed instantly worsened.

I think there may be a problem with this update.
Dou you have any idea what may caused this?

---

### Post by Ayuthia on 2010-01-15
> **onurozcelik said:**
> You maybe misunderstand me. My intention is not go to back to ndiswrapper or b43-fwcutter. Because they either do not work for me properly.  I am grateful for open source firmware.

I should tell my problem.

Two days ago I have no poor internet speed issues.
Then I updated my system and I am now using kernel version 2.6.31-18. After that update my internet speed instantly worsened.

I think there may be a problem with this update.
Dou you have any idea what may caused this?

I am not for sure about what caused it.  You might try going back to the previous kernel and see if the speed is ok there.  If it is, then it is most likely an update in the b43 module.  However, if you are having problems with both ndiswrapper and b43 in the new kernel, then it could be related to NetworkManager.

I am not for sure about how much work you want to try to find the issue, but you might try removing any encryption (WEP/WPA/WPA2) on your router to see if it makes a difference.  I am not saying that you should keep it that way, but more of a tool to see if it is a change in the encryption rules that is causing the issue.

If you know how to connect through the Terminal, you can turn off NetworkManager and see if it makes it work better.

---

### Post by onurozcelik on 2010-01-15
To Ayuthia
Thank you for intention help.

I tried your suggestions. None of them worked for me.
In addition to that I tried ndiswrapper and b43-fwcutter. This time they both work. But unfortunately there is no performance improvement with the poor internet speed.
I would like to admit that b43-fwcutter performance better than others.

I think this problem is not related with configuration, firmware, software or the updates(I am a bit suspicious about updates :))
I guess it is related with pyhsical factors like the distance from wireless router or wireless card.
(But interestingly two days ago while I was downloading Chuck episode I got good internet speed from same place) 

At least I decide to use the wired connection to get better internet speed.

---

### Post by jzacsh on 2010-01-22
Hey, I'm trying this (as was suggested to me in my post: [http://ubuntuforums.org/showthread.php?p=8703269](http://ubuntuforums.org/showthread.php?p=8703269)) -- I'm stuck on [bviktor's guide]("http://wiki.frugalware.org/index.php/B43_with_open_source_firmware"), under "Assembling the firmware" I get this error:
```

[B]
$ cd openfwwf
$ PATH=$PATH:../b43-tools/assembler make[/B]
b43-asm ucode5.asm ucode5.fw --cpp-args -DDEBUG=1 -- --ivalext .fw --psize
ERROR: Failed to execute the b43-asm binary "b43-asm.bin"
make: *** [ucode5.fw] Error 2

```

Any suggestions? I don't want to screw anything up -- so I'm just going to leave things 'till I get a response :confused:

---

### Post by jzacsh on 2010-01-29
Hello? Anyone still watching this thread? :(

---

### Post by Ayuthia on 2010-01-30
Sorry for not responding.  I have not tried that guide.  The [guide]("http://linuxfans.keryxproject.org/?page_id=54") that I created did things a little differently.  It is not to say that the other one is wrong, but I am not sure why it created that error.  The difference between the two guides is that the one that you are using does not install the b43-asm tool (sudo make install) after the make (in the Building the Assembler section).  My guess is that the step you are doing is missing something.  

You might try going into b43/assembler and doing the sudo make install and then in the Assembling the Firmware section do:
```

cd openfwwf
make

```
instead of
```

cd openfwwf
PATH=$PATH:../b43-tools/assembler make

```and see if it makes a difference.

Hope that helps.

---

### Post by jzacsh on 2010-02-01
> **Ayuthia said:**
> 
```

cd openfwwf
make

```


I tried that ^ -- still didn't work. thank you for reading the other how-to and making a suggestion. I'm trying to go through your how-to...

**[SIZE="4"]I'm stuck at your step 6:[/SIZE]**
> 
Step 6:
Move the current b43 folder and call it b43-proprietary:```

sudo mv /lib/firmware/b43 /lib/firmware/b43-proprietary
```


All I have in my /lib/firmware/ directory is:
```
.
..
2.6.31-14-generic
2.6.31-17-generic
acx
aic94xx-seq.fw
ar9170-1.fw
ar9170-2.fw
ar9170.fw
atmel_at76c502_3com.bin
atmel_at76c502_3com-wpa.bin
atmel_at76c502.bin
atmel_at76c502d.bin
atmel_at76c502d-wpa.bin
atmel_at76c502e.bin
atmel_at76c502e-wpa.bin
atmel_at76c502-wpa.bin
atmel_at76c503-i3861.bin
atmel_at76c503-i3863.bin
atmel_at76c503-rfmd-0.90.2-140.bin
atmel_at76c503-rfmd-acc.bin
atmel_at76c503-rfmd.bin
atmel_at76c504_2958-wpa.bin
atmel_at76c504a_2958-wpa.bin
atmel_at76c504.bin
atmel_at76c504c-wpa.bin
atmel_at76c505a-rfmd2958.bin
atmel_at76c505-rfmd2958.bin
atmel_at76c505-rfmd.bin
atmel_at76c506.bin
atmel_at76c506-wpa.bin
[COLOR="Red"]BCM2033-FW.bin
BCM2033-MD.bin
[/COLOR]dvb-fe-xc5000-1.6.114.fw
dvb-usb-dib0700-1.20.fw
i2400m-fw-usb-1.3.sbcf
i2400m-fw-usb-1.4.sbcf
ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw
isl3877
isl3886pci
isl3886usb
isl3887usb
isl3890
[COLOR="Red"]iwlwifi-1000-3.ucode
iwlwifi-3945-1.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-1.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode[/COLOR]
lbtf_usb.bin
NPE-B
NPE-B.01020201
NPE-C
NPE-C.02020201
ql2100_fw.bin
ql2200_fw.bin
ql2300_fw.bin
ql2322_fw.bin
ql2400_fw.bin
rt2561.bin
rt2561s.bin
rt2661.bin
rt2860.bin
rt2870.bin
rt73.bin
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx2341x-dec.fw
v4l-cx2341x-enc.fw
v4l-cx2341x-init.mpg
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc.fw
v4l-cx25840.fw
v4l-pvrusb2-24xxx-01.fw
v4l-pvrusb2-29xxx-01.fw
zd1201-ap.fw
zd1201.fw
zd1211
```
(*[COLOR="Red"]I highlighted[/COLOR] what I thought might be of interest, but I'm totally unfamiliar with what I'm actually looking at*)

This is what I can see of my NIC in my `lshw`:
```
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:69:76:11:31
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.192 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:fe8fc000-fe8fffff

```

**Any suggestions?** The issues with my connection are really annoying

---

### Post by Ayuthia on 2010-02-04
> **jzacsh said:**
> I tried that ^ -- still didn't work. thank you for reading the other how-to and making a suggestion. I'm trying to go through your how-to...

**[SIZE="4"]I'm stuck at your step 6:[/SIZE]**


All I have in my /lib/firmware/ directory is:
```
.
..
2.6.31-14-generic
2.6.31-17-generic
acx
aic94xx-seq.fw
ar9170-1.fw
ar9170-2.fw
ar9170.fw
atmel_at76c502_3com.bin
atmel_at76c502_3com-wpa.bin
atmel_at76c502.bin
atmel_at76c502d.bin
atmel_at76c502d-wpa.bin
atmel_at76c502e.bin
atmel_at76c502e-wpa.bin
atmel_at76c502-wpa.bin
atmel_at76c503-i3861.bin
atmel_at76c503-i3863.bin
atmel_at76c503-rfmd-0.90.2-140.bin
atmel_at76c503-rfmd-acc.bin
atmel_at76c503-rfmd.bin
atmel_at76c504_2958-wpa.bin
atmel_at76c504a_2958-wpa.bin
atmel_at76c504.bin
atmel_at76c504c-wpa.bin
atmel_at76c505a-rfmd2958.bin
atmel_at76c505-rfmd2958.bin
atmel_at76c505-rfmd.bin
atmel_at76c506.bin
atmel_at76c506-wpa.bin
[COLOR="Red"]BCM2033-FW.bin
BCM2033-MD.bin
[/COLOR]dvb-fe-xc5000-1.6.114.fw
dvb-usb-dib0700-1.20.fw
i2400m-fw-usb-1.3.sbcf
i2400m-fw-usb-1.4.sbcf
ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw
isl3877
isl3886pci
isl3886usb
isl3887usb
isl3890
[COLOR="Red"]iwlwifi-1000-3.ucode
iwlwifi-3945-1.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-1.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode[/COLOR]
lbtf_usb.bin
NPE-B
NPE-B.01020201
NPE-C
NPE-C.02020201
ql2100_fw.bin
ql2200_fw.bin
ql2300_fw.bin
ql2322_fw.bin
ql2400_fw.bin
rt2561.bin
rt2561s.bin
rt2661.bin
rt2860.bin
rt2870.bin
rt73.bin
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx2341x-dec.fw
v4l-cx2341x-enc.fw
v4l-cx2341x-init.mpg
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc.fw
v4l-cx25840.fw
v4l-pvrusb2-24xxx-01.fw
v4l-pvrusb2-29xxx-01.fw
zd1201-ap.fw
zd1201.fw
zd1211
```
(*[COLOR="Red"]I highlighted[/COLOR] what I thought might be of interest, but I'm totally unfamiliar with what I'm actually looking at*)

This is what I can see of my NIC in my `lshw`:
```
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:69:76:11:31
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.192 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:fe8fc000-fe8fffff

```

**Any suggestions?** The issues with my connection are really annoying

It looks like you don't have it, but that is ok.  That step was to backup the previous version so it is not necessary.  You can go ahead and move on to the next step.

---

### Post by jzacsh on 2010-02-08
thank you! I'll try it now :)

---

### Post by jzacsh on 2010-02-15
I did try this out and thought it was fine as I didn't experience **[any problems]("http://ubuntuforums.org/showthread.php?p=8744757#post8744757")** for about a whole day. Then the problems of "[Domain not found]("http://ubuntuforums.org/showthread.php?p=8744757#post8744757")" from my ISP returned, so -- its clearly not solved.


If _anyone_ has any ideas, this is the thread I started, I could **really use the help**.
[http://ubuntuforums.org/showthread.php?p=8744757#post8744757](http://ubuntuforums.org/showthread.php?p=8744757#post8744757)

---

