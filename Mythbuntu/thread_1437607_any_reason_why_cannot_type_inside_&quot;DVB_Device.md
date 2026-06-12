---
title: "any reason why cannot type inside &quot;DVB Device Number&quot; field"
date: 2010-03-24
forum: Mythbuntu
---

### Post by dwyersm on 2010-03-24
I have been trying for FIVE days now to setupmythtv 9.10. with a  common dvico  fusion HDTV   DVB-T lite. I am tearing my hair out. What gives.

 In capture card setup, I choose DVB DTV capture card (v4.x), but in the next field which is "DVB Device Number"  I cannot type anything, I have no idea how to get text into this field. 
Would some-one mind a little hand holding here. I am very computer literate, and I have been using linux suse 11.1 for over a year now and  I hate the "other OS" .I consider myself smart enough to know my way around more than the average joe.
 But this is driving me nuts. I have spent about 20 hrs researching on the net,  I have re-installed the system about 12 times now.
 A lot of the pages that come up on the web send me around in circles, ---:do this , do that, do this again but this way, but this only works on this kernel, but this only works on this version of so and so,  this has to be done but you have to read another 17 pages of web first, but after reading 17 pages it says "but wont work with my setup!!" and so on and on.

Sorry about my complaining ,  but I am one confused and almost worn out penguin.

I have done as much as I can on my own, but now I think I need some help.

Cheers and much appreciated.

Shane,
Brisbane, Australia

---

### Post by klc5555 on 2010-03-24
OK, I don't use your particular card, but in general the dvb device number is assigned by the machine when the driver module and firmware load at boot, and is not assigned by the user. If, in multiple tuner environments, a particular tuner has to persistently assigned dvb0, dvb1, etc., then this is done at bootup time either through udev rules or through particular options being added to the .conf files determining how the modules load.

This seems to be the position taken in the wiki page for your particular tuner card:
  
[http://mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Lite](http://mythtv.org/wiki/DViCO_FusionHDTV_DVB-T_Lite)  

where it points out: "Capture Card Setup (Reminder: the ID and probed info need to be detected rather than entered)"

Now the analog component of the card (if you use it) will be a different kettle of fish. The wiki page seems to assume mythtv 0.20.2, where analog options were configured as a subset of the dvb card. Starting with mythtv 0.21, the analog component will be configured as though it were a separate analog card.

But the dvb device number should be there at boot. If not, then the drivers would appear not to have loaded correctly.

---

### Post by dwyersm on 2010-03-24
klc, thank you for your response.
 I did actually read that page, but after days and days of reading stuff I think my brain turned to mush, and it didnt register too well about  the part where it says the card has to be detected.

 If you wouldnt mind having a look at dmesg output and I can start looking for reasons why the card isnt detected.


I have an Asus P4S800-MX SE mobo with BIOS as:-
Plug and play OS = yes
ACPI 2.0 Supporrt= yes
ACPI APIC Support = enabled

APM CONFIGURATION:-

Power on by PCI = enabled


dmesg output is actually just output redirection to  a .txt file. I dont know what to trim to make it fit within the 19.5k upload limit so I renamed it to a .doc.

regards,
Shane, Brisbane, AU

---

### Post by utar on 2010-03-25
Can you post the output from "lspci -v".

Going by your dmesg output the card is not being properly recognised.


Utar

---

### Post by klc5555 on 2010-03-25
> **utar said:**
> Can you post the output from "lspci -v".

Going by your dmesg output the card is not being properly recognised.


Utar

Agreed.

If lspci doesn't find the card (properly), it could be that the default modprobe has not loaded the bttv driver automatically with the correct options --a problem with a number of cards. You should be able to (having stopped the backend) unload the bttv driver the card is failing to use (sudo rmmod whatever-it-is) and then reload it by hand with the correct parameters, either according to the aforementioned wiki page for the Dvico card, or by specifically identifying your card in the parameters you pass to modprobe, as per section 4.5 and following in [http://www.faqs.org/docs/Linux-mini/BTTV.html](http://www.faqs.org/docs/Linux-mini/BTTV.html) or similar.

The tuner number of your Dvico card would appear to be 128, according to this document here: [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv)

Once you have determined the correct parameters for loading your driver module by hand, then automating the correct parameters at bootup is a not difficult. 

But one thing or so at a time.

---

### Post by dwyersm on 2010-03-25
Thanks guys, I appreciate this very much.
 I know my way around linux at a level better than user level. I have run up and played with many distros over the years. In the last year or so I have stayed with Suse 11.1 and  KDE3.
Dont know why, just liked it. I also like mandriva.
 However I am now involved with another different distro  ie mythbuntu, and I have to change my thinking a little bit. And I am also playing in new terrority eg TV hardware and software. The research Ive done on the web finding out about installing this card has  results like - load this, load that, type this, type that, and sometimes  the distro is not mentioned so the advice may not be at all applicable to mythbuntu's organisational layout and current kernel, and after reading and much confusion you find out some of these pages are 6 years old!
 This is probably why I am a little confused.

I have output from lscpi -vv and a new dmesg.
 In the meantime I may have changed the card to a different slot, I cant remember when though, dont know if it matters.

  The attachments apply to what I have also newly written to /etc/modules :
bttv card=128
dvb-bt8xx 

The "dvb-bt8xx" was in there before my first post


If I may ask a question:-

what is bttv, bt8xx, and v4l lumps of software. are bttv and bt8xx the same things, are both required, and how are these relationships between these 3 lumps.

Would I be correct in saying that v4l should always be present when using TV for linux, and is the api/interface for the other guys (card drivers that is). From what I have gathered bttv and bt8xx may very well be the same thing!
 
sorry I meant two questions:-

There are 2 directories in /etc for module stuff - modprode.d, modutils, and  one file -modules.
 Do the card drivers have to be explicitly written into any of these, and where are the card driver options written ie "card=128". What is the correct syntax or format?

Why arent things like the nic and video cards written in here anywhere? as these cards as well use drivers.

regards,
Shane, Brisbane Au

---

### Post by andree_b on 2010-03-26
After upgrading from 9.04 to 9.10 I I had a problem where i too wondered why one could'nt edit "DVB Device Number" - may be your problem is related to mine which i was able to solve:
Somehow the scheme for dvb devices under /dev created by udev changed from  /dev/dvb/adapter0/frontend0 to /dev/dvb0.frontend0 and mythtv expected the old scheme.

But you can add rules to udev's configurations to change it back to the old scheme (or automatically create symlinks in the old scheme). 
Can attach my udev config files when i am back home - but for testing purposes you could manually create those symlinks.

---

### Post by klc5555 on 2010-03-26
The drivers undergo work from kernel version to kernel version. The docs may or may not keep up.

Short answer: you have to empirically try solutions before finding the one that's going to work for this old card on a new kernel & driver set.

First try: your backend's not running, try "sudo rmmod bttv" If it works, you should get just a prompt. If some other subsidiary driver is dependent on it, you'll get an error. You'll have to "sudo rmmod" the dependent one first, then bttv.

If the module has been unloaded, then "sudo modprobe bttv card=128" _may_ load the driver correctly. You can do a "dmesg | grep bt" or similar may give you the information (i.e. gives you some identification info back on your tuner). If everything looks OK, then you may try to set up the card in the backend. If a dvb0 selection appears, you may be in business. If all you get is a /dev/video0 (which is for analog) then we have to do more research in how to load this particular driver. But the first step is to get it to load by hand, from a prompt, after the machine boots.

In practice, some capture card drivers that require additional parameters to identify the card (and/or tuner)are stubborn and may not pay any attention to parameter information placed in the config files, and persist in loading the incorrect detected parameters. I don't know if the bttv drivers are among these since I don't use such a card. But frequently the final solution is to put the driver into the blacklist file, so that it can't autoload at boot, and then put the modprobe line with the correct parameters at the end of the rc.local file.

But the first thing to do is unload the incorrectly loaded driver and try loading it from a prompt to see whether it functions.

To answer your other question --those other peripherals are being detected correctly and their drivers are loading correctly. On some hardware, they aren't. Then one may have to put parameters in the conf files for them, too (or a modprobe line in the rc.local) One laptop that I stuck Ubuntu 9.10 requires 4 modprobe lines in a particular order in the rc.local  to successfully activate the wireless ... but I digress.

---

### Post by dwyersm on 2010-03-28
Thanks guys,

I decided to check the card out under XP, using the downloaded windows drivers from dvico.kr. I had to thrash the drive to make room for partitions etc.
 To my amazement the latest dvico driver doesnt recognise this older card, so I had to backtrack down a couple of versions of the dvico drivers until it was recognized and installed.
Then guess what, cant tune anything. so I suspect the card due to its age my be faulty.
So back into its box and filed away.

Anyway I have been excited as this is my first venture into pc-tv, so not to give up i did a little research and went and got what appeared to be a close match ie Leadtek DTV 2000H +.

hmmmm.... the little plus on the end is now the problem. Too new for linux driver support, and with a different tuner chip xcieve 4000. Run up XP and ok and it works so my enthusiasm is still not exhausted.

So I have been looking around and it appears that several have had this card working, but once again its a module loading and experimenting exercise.

Thanks for your help and insight. I appreciate the time that supporters lend to the forums.

I'll go through this new exercise as far as I can, all the time learning something new, and when I once again come to the brick wall where my knowledge, common sense and logic stops, I look to the forums.

Cheers and thank you,

Shane Brisbane, AU

---

