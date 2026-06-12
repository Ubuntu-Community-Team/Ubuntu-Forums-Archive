---
title: "Qualcomm HS-USB-9212 in Acer Aspire One--No connection"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by jamere on 2009-11-18
Just installed dual boot 9.04 Desktop and XP on my Netbook. Built-in broadband wireless modem works fine in XP but doesn't connect in 9.04. The network manager applet shows in panel but no connection. I suspect a Qualcomm driver problem since it works in XP. The modem is apparently recognized by 9.04.

lsusb output: 
bus 001 device 004:id 05c6: Qualcomm, Inc.

Anyone have any ideas or solutions? Thanks much.

Jim M

---

### Post by jamere on 2009-11-19
any AAO users with the Qualcomm built-in modem with this problem? or solutions?

---

### Post by jamere on 2009-11-19
Well, this problem may be a deal buster with linux. Been using Ubuntu desktop exclusively for several years and several versions, and never run into a mobile broadband problem like this and no help or suggestions from the community. hate to go back to the sucky windows, but not much choice, I guess.

---

### Post by jamere on 2009-11-20
bump

---

### Post by Chiapo on 2009-11-21
> **jamere said:**
> bump

////////////////////////////////

You're not alone...
I've been going through this exact same 3G modem issue ever since I bought my netbook in April 09...
[http://ubuntuforums.org/showthread.php?t=1157846](http://ubuntuforums.org/showthread.php?t=1157846)

[http://ubuntuforums.org/showthread.php?t=1174154](http://ubuntuforums.org/showthread.php?t=1174154)

...
I've tried kuki [http://kuki.me/](http://kuki.me/) which was made specifically for the Acer Aspire One, but had no luck with the 3G connection.

Apparently this Qualcomm 9212 modem needs to have qcserials & usbserials added to the kernel, but am not sure.

For now I just use my cell phone when there's no other connection, Network Manager automatically connects whenever I plug my phone into a USB port. It's not the fastest, but it does allow connectivity.

---

### Post by jamere on 2009-11-21
Chiapo,

Thanks for the reply! I was beginning to feel alone in the wilderness. :)  I went to the Acer forums, but so far no response there either.

[http://www.aspireoneuser.com/forum/]("http://www.aspireoneuser.com/forum/")

Upon seeing all the networking problems reported on 9.10 (UNR), I decided to drop back to 9.04 (desktop) since it was supposedly much more stable. I set up a dual boot (XP and 9.04) since I HAD to have a NW connection. Fortunately the XP 3G connection still works! :)

I'll have to say the install went without a hitch other than the 3G connection not working and the fact that the installer only set up a 3gig 9.04 partition (out of 160 gig on hard drive). I've had nothing but good experiences with Ubuntu for the past couple of years and have used it exclusively.

Would really like to get a solution to this and move on. Have a feeling the developers and networking gurus have been overwhelmed with all the reported NW problems on 9.10. Given all the variations in HW configurations and vendors, I have some sympathy.

Anyway, let me know if you come across any solutions and I'll do the same. BTW, good idea on the cell phone connection! ;)

---

### Post by jamere on 2009-11-21
I got 9.10 working on my Netbook (ZG8 using a USB Startup Disk. Here's what I did briefly.

1) created USB Startup disk using System>Admin>USB Startup Disk Creator. Put on a 4 gig memory stick (2 gig recommended, i think)
2) right-clicked on grayed NW icon in panel and enabled networking
3) edited a new network connection (broadband mobile tab) in same icon (AT&T Data Connect...my plan)
4) in Firefox preferences>advanced>network tab>connection settings>No proxy
5) re-booted from memory stick and amazingly the network came to life!

Maybe this will help get you networking again! This USB memory stick is a pretty handy tool to have around. I don't have confidence yet to blow away XP for a full install of 9.10. Let me know if this works for you...I'm still amazed it worked.

jim m
__________________
Jim M
Jaunty 9.04
Tulsa, OK
USA
Last edited by jamere; 1 Minute Ago at 02:57 PM.. Reason: typo: should be model: zee gee eight

---

### Post by jamere on 2009-11-21
Well, i'm going to have to qualify my earlier statement that 9.10 is working on my Netbook. I got up on the network one time and one time only. When I booted from the USB startup disk (memory stick)the first time (after editing a new AT&T connection), the network actually came to life and I was able to use Firefox for about an hour flawlessly. That was exiting to say the least. I decided to re-boot to satisfy myself that my success would be repeated...didn't happen. The network was nowhere to be seen. I tried everything I could to get the NW activated again to no avail.

It looks like the driver that is used is 'qcserial.ko'. Looks to me like this module is somehow made "unavailable' after being used once. Who knows? Ideas anyone??? I realy did see the network in operation...once! :-))

---

### Post by Chiapo on 2009-11-21
Hello jamere!

We are united in our quest!

Good to hear you were able to connect!

This link might be of interest to you:

[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")

Have you tried kuki? 
More info here:
[http://kuki.me/](http://kuki.me/)
I have been unsuccessful thus far, but have your sentiment regarding keeping the Windows partitions until a 3g connection is not an issue in ubuntu. (xubuntu)

I'll be checking in here more often now that I have a kindred spirit who is seeking that elusive 3g connection through the Qualcomm 9212 modem.

---

### Post by jamere on 2009-11-22
chiapo,

Glad to see you check in and thanks for the links...I'll have a look. I have to admit my linux tech skills are pretty limited. linux has been very reliable, for me anyway, for the past 2 or 3 years. Fortunately, we haven't had many show stoppers like this to deal with. Not a lot we can do with NW connection failures.

I've been pretty disappointed, so far with the Acer forums. Doesn't appear to have much activity or eyeballs looking at our problems. I would think that they of all people, would be interested in coming up with a fix or work-around.

I did see a posting here on the Ubuntu forums by "amartz" that appeared to have a solution but wasn't very eager to share it.

Well, at least for the brief time I was able to network, I saw how it is supposed to work. I had been using a DSL line previously that performed flawlessly.

Guess we'll keep plugging away and hopefully someone will come up with a solution...gotta be optimistic!

---

### Post by jamere on 2009-11-22
Looks like the guy with the gobi loader may have the problem and solution nailed, however implementing is well beyond my tech ability. Also looks like there could be some Qualcomm "legalities" involved. Basically, i don't have the cahones to risk getting into this solution. darn!

---

### Post by jamere on 2009-11-23
The following is "amartz"'s solution to the problem. Please post your results here if you can. I haven't had time to deal with it myself yet. Big THANKS to amartz!! chiafo what do you think?

Jim M
--------

Here's some notes I compiled when I was figuring this out:
Art

First thing, the modem needs it's firmware reloaded every time you turn it on. Without the firmware, it's just an empty shell. I've seen somebody putting together something to load the Qualcomm Gobi firmware from linux, but for now I do it from windows.

Boot to windows first, to load firmware into modem, then reboot to Ubuntu, without powering off.

wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing

art@art-laptop:~$ lsusb
Bus 001 Device 004: ID 05c6:9212 Qualcomm, Inc.

This is the only command you really need, the chat command is not needed, but is a convenient way to tell if the modem is talking.
~$ sudo modprobe usbserial vendor=0x05c6 product=0x9212
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

~$ ls -lha /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2009-07-23 11:29 /dev/ttyUSB0

The probe.txt is as defined in wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing
~$ chat -s -f ~/probe.txt >/dev/ttyUSB0 </dev/ttyUSB0
chat:  Jul 23 11:30:02 +GCAP: +CGSM,+DS,+ES
chat:  Jul 23 11:30:02 +COPS: 0,0,"AT&T",2
chat:  Jul 23 11:30:02 +CREG: 0,1

I would suggest to put the modprobe command in the file /etc/rc.local.
That is the last command which is run at boot time. As it is run as root
anyway, there is no need for sudo. To make the change, use the command

gksu gedit /etc/rc.local

and put the line

modprobe usbserial vendor=0x05c6 product=0x9212

_before_ the line

exit 0

Modem Manager software repository, add
deb [http://ppa.launchpad.net/modemmanager/ppa/ubuntu](http://ppa.launchpad.net/modemmanager/ppa/ubuntu) jaunty main
then run
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF2A6AFA
and
sudo apt-get update

---

### Post by msignor on 2009-11-23
Hey Guys, 

I am really excited to see that guide on how to get the card working. I just wanted to throw something out there to see if anyone had comments.... 

Im running 9.10, and when I do a 'lsusb' I see the qualcomm card like everyone else. I did a 'lsmod' and confirmed that I have usbserial and qcserial loaded. According to dmesg the card is found:

-----
[12743.244590] usbcore: registered new interface driver usbserial_generic
[12743.244593] usbserial: USB Serial Driver core
[12769.972000] USB Serial support registered for Qualcomm USB modem
[12769.972749] qcserial 2-4:1.0: Qualcomm USB modem converter detected
[12769.972836] usb 2-4: Qualcomm USB modem converter now attached to ttyUSB0
[12769.972862] usbcore: registered new interface driver qcserial
-----

However, I am unable to minicom to /dev/ttyUSB0 and it does not show up in NM. 

I was stumped before but I am going to give the directions above a shot. I assume its due to the reasons above... but need to confirm. Have any of you guys gotten your system to detect the card this far? Have you had any success running anything? When i try modem-manager it does not and according to debug its because i dont have privelages.. even when I run with sudo. 

Cheers,

Matt

---

### Post by Chiapo on 2009-11-23
Many thanks to amartz for helping! Also thanks to jamere for helping bring this issue to light.

Unfortunately I don't have usbserials loaded in any of my *buntu distros. (9.04) but following the advice of amartz I was able to get the Device ID changed from 9211 to 9212.

Issuing ```
sudo modprobe usbserial vendor=0x05c6 product=0x9212 results in the following:
FATAL: Module usbserial not found.

:~$ ls -lha /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory

gksudo chat -s -f ~/probe.txt >/dev/ttyUSB0 </dev/ttyUSB0
bash: /dev/ttyUSB0: Permission denied


```So I'm out of luck here...

I tried the UNR 9.10 but had no luck connecting via the Qualcomm 9212 3g modem, so tried kuki where I was unable to connect with any 3g method (cell phone tethering / internal modem) so reverted back to xubuntu 9.04.
I tried "upgrading" to 9.10 but I had so many problems a complete nuke & pave was necessary on that partition.  Followed by a reinstall of xubuntu 9.04, which I grow fonder of with each successive use.

I am really anxious to get Windoze off this machine ASAP so I can make more room, but am trapped by the fact that this modem  is only useable in Windoze.

---

### Post by Chiapo on 2009-11-23
Upon reading the output of dmesg, I noticed the following:
```

[    3.318559] hub 5-0:1.0: USB hub found
[    3.318572] hub 5-0:1.0: 2 ports detected
[    3.318832] usbcore: registered new interface driver libusual
[    3.318908] usbcore: registered new interface driver usbserial
[    3.318930] USB Serial support registered for generic
[    3.318965] usbcore: registered new interface driver usbserial_generic
[    3.318970] usbserial: USB Serial Driver core
```

So I was wrong about usbserial being present?

Nowhere in the output of dmesg could I find "Qualcomm" 

lsusb shows:

```
:~$ lsusb
Bus 001 Device 003: ID 05c6:9212 Qualcomm, Inc. 
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

My current connection is via /dev/ttyACM0 which is the Samsung device.

---

### Post by jamere on 2009-11-24
Hey guys, thought I'd give amartz's procedure a try but didn't get very far. I also noticed (as chiapo did) that 9211 changed to 9212, I assume after firmware load in XP. I also received the following:
FATAL: Module usbserial not found

Is this a correct assumption on my part, that once a successful
modprobe is made on usbserial, that the network should light up until the next power off (after a new mobile broadband connection is edited and added)?

This is probably a dumb question chiapo, but how did you preserve your command output in Linux to post them in the forum, in XP? Very useful.

You expressed my sentiments exactly...

> I am really anxious to get Windoze off this machine ASAP so I can make more room, but am trapped by the fact that this modem is only useable in Windoze.

jim m

---

### Post by Chiapo on 2009-11-25
You can direct terminal output to a text file by using the following sytax:

command > /path/to/filename 

So to save dmesg terminal output to a file named "/Desktop/dmes-output" you would enter the following at the terminal prompt:

dmesg > /Desktop/dmes-output

Of course one would prefer to save to removeable media:

Which would look like this on my system:

dmesg > /media/disk/dmes-output

Luckily for me, I've got my cell-phone working as a modem in xubuntu 9.04, so I haven't needed to do the "Windoze shuffle" via USB flash drive lately.:p

Interesting that you received the same FATAL: error as I did regarding usbserial not found...

Have you gone to any of the ubuntu/kubuntu/xubuntu IRC channels to ask questions?

I think I'll go see what I can find out from the gurus there.

I'll keep you posted on any progress or hints.

Cheers!

---

### Post by pdc on 2009-11-25
I wondered in your google searches if you had seen this posting:

getting the qualcomm to work ........... a few days ago ...

[http://clayeweb.org/blog/category/linux-tech/](http://clayeweb.org/blog/category/linux-tech/)

it was using OpenSuse 11.2 that is just released: the poster describes getting his qualcomm working:

he talks of loading the

> amss.mbn and appsmbn file

he says

> The files you are looking for are the amss.mbn and apps.mbn.  Both files are required.  Some people have reported that their systems contain many different versions of these files.  Mine only had one of each and they where located in the c:\QUALCOMM\QDLService\Packages\2 directory.  The files are specific to your service providor and I have not found a way to figure out which files are the correct ones for your system.  Once you find the files create a /lib/firmware/gobi directory and copy both files to it.

---

### Post by Chiapo on 2009-11-25
You mean like this?  @ pdc

> **Chiapo said:**
> Hello jamere!

We are united in our quest!

Good to hear you were able to connect!

This link might be of interest to you:

[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")
...

The firmware is as you posted... In the c:\QUALCOMM\QDLService\Packages\2 directory...
My system has ten different numbered directories, but the above link tells how to locate the firmware used by the modem in WinXP...

Still, without being able to modprobe usbserial due to usbserial not found, none of the firmware is any good.

Thanks for the heads up re: OpenSUSE, looks like it's time to download another .ISO :)

---

### Post by msignor on 2009-11-25
Guys, 

You need to have both 'usbserial' and 'qcserial' modules for gobi_loader and the firmware to work. 

If you do not have those modules, then you need to first solve that issue. It is most likely the kernel. This works out of the box on 9.10.. You should have a /dev/ttyUSB0 that appears, but is not accessable (because no firmware is loaded) before trying the gobi_loader. 

The firmware that you need should be the smallest physical filesize as indiacted in the README. The firmware I downloaded from Lenovo for my x301 only had 3 files, and the smallest (CDMA) was in folder 1. 

After copying those files to /lib/firmware/gobi (after I make && make install gobi_loader) i can unload and reload the qcserial module and then you can initialize the device as a modem. You will also notice that if you LSPCI before and after the firmware, the model number changes. 

-Matt

---

### Post by Chiapo on 2009-11-25
Thank you for your assistance msignor!
Is there any chance of showing the terminal commands to "make && install gobi_loader" for us total newbz?

Not sure how to accomplish the make & install.


I've downloaded the source, copied the firmware from my WinXP partition, but need further instruction.

Thanking you all once again!

---

### Post by jamere on 2009-11-25
Chiapo, thanks much for the terminal output lesson. Will be very helpful!

I haven't tried any of the IRC channels, but looks like it may be a good source of info for IRC users. I just never have gotten into the IRC thing. Would be great if you should come up with anything useful from the techno-whizzes there. Looks to be some good leads from the posters here.

I hope some of you smart guys can come up with a simple, step-by-step solution (hopefully in 9.04 and/or 9.10) for some of us technically challenged folks! Looking forward to blowing away Windows!

Will be nice to get to 9.10 and back into the Update process. hang in there!:)

---

### Post by msignor on 2009-11-26
Chiapo, 

Download the source for gobi_loader. Extract the source, and then go into the folder containing it. So, if you extracted it to /home/gobi_loader then you need to CD into the /home/gobi_loader folder. 

Once you are in the folder, type 'make' you will see it basically compile a single line of output, then return you to the prompt. (Literally, 1 second).. now that you have made it, you need to install it.. so now type 'sudo make install' and then this will install gobi_loader. 

After install you need to actually make the gobi folder.. so do a 'sudo mkdir /lib/firmware/gobi'

NOW... copy the 2 files (in folder 1, if you have Verizon... should be the smaller files of the bunch) into the /lib/firmware/gobi folder. 

Once you have the firmware there, you can then reload the module. So do a 'sudo modprobe -r qcserial' and then a 'sudo modprobe qcserial' and you should now have a /dev/ttyUSB0 that you can access from minicom or some other dial application. 

----

You MUST have both 'usbserial' and 'qcserial' modules on your system. Technically before you load the gobi loader, you should be getting a /dev/ttyUSB0 that you can do nothing with (due to firmware)... 

If you do NOT have those modules.. then either your kernel is compiled with them built in (aka, not as modules) in which case you just need to reboot and gobi should work.... if your kernel does not have them built in.. you can recompile the kernel and modules yourself, upgrade to 9.10, or download a newer kernel.. Being that I came from a Slackware environment, recompiling the kernel is no big deal.. but it does appear that Ubuntu strongly suggests you dont make your own, instead use one of theirs if you have never done it before. 

Hope this helps...

-Matt

---

### Post by Chiapo on 2009-11-26
Thanks a million msignor!

Appreciate you taking the time to spell it out for us newbz!

Best wishes to you & your loved ones on this Thanksgiving holiday!

---

### Post by jamere on 2009-11-27
Looks like a great solution from msignor! Very encouraging. A very Big THANKS! Unfortunately I'm stuck on msignor's very first sentence. :o  I can see what he's doing, but don't have the terminal wherewithal to get it accomplished.

chiapo: Have you tried this solution? Assuming it works, hopefully you can further translate in more usable detail for the rest of us? This is a little more difficult to digest than the Thanksgiving meal!! 

Thanks Matt for taking interest in our plight!

Jim M

---

### Post by Chiapo on 2009-11-27
I got a connection once, but no page load.

When I try ```
sudo modprobe qcserial
```
It says Module not found...

I got the firmware from my WinXP installation, There's a file called options.txt in the QDL* directory somewhere (copied them awhile ago - forgot the exact path) & in that file is the path to the firmware your modem uses for your provider.

The make & make install were quite straightforward, easy enough that even I could do it.

I have problems in that now I must compile my own kernel with qcserial included, or hope that the latest RC will work with my AA1.

I tried downloading 2.6.30 kernel, but still had the modprobe error regarding qcserial.

I gave up after I downloaded 2.6.32 & ran into the same error.

Maybe I need to sleep for awhile & try after a rest & feast & sleep again.

I shall return.

---

### Post by Chiapo on 2009-11-27
I almost forgot, but the one time the modem connected, I was using GNOMEppp downloaded via Synaptic.

On a side note, I downloaded SliTaz (!#GNU) & while the modem didn't work, the system report showed more detailed information all on one screen, including the Qualcomm device with 2 separate ID's & 2 separate (ports?) /not sure what it was called.

---

### Post by msignor on 2009-11-27
Are you running a stock install of Ubuntu? Everything worked out of the box regarding modules... 

Im running: 2.6.31-15-generic #50-Ubuntu

---

### Post by Chiapo on 2009-11-28
Hello msignor.

I'm using several flavors of linux, most of which are *buntu 9.04. 

To get this Qualcomm 9212 modem working, I'm using Ubuntu 9.04 but I upgraded the kernel to 2.6.30-02063009-generic. I acquired the *buntu's from a linux identity DVD which contained the "Ubuntu Family 9.04" http:linuxidentity.com/

I tried the upgrade option in Update Notifier (Manager?) but ubuntu 9.10 left me with no cell phone modem connection.  

Cheers!

---

### Post by msignor on 2009-11-28
Chiapo, 

NM will not show the device until the modem firmware has been applied, and then Network Manager is restarted. 

In my stock 9.10 install, I had both modules created and loaded... can you confirm? Do you still have the 9.10 installed? 

Once you get the modules, add gobi_loader, copy firmware (the spiel from above) and you should be off to the races. I have been surfing for the past day or so with no issues.. I do find it annoying that I have to log-out and login again to NM for the card to be seen.. but thats just because I am too lazy to dig and restart all the components by hand. Reboot works well too :-) Just make sure Gobi runs first, and its a real reboot.. not a power cycle. 

-Matt

---

### Post by Chiapo on 2009-11-28
Thanks msignor!

Looks like I should just download the latest stable .ISO...

I deleted the upgraded partition to make room for new OS trying to find one that will work right out of the box with my hardware, but that search is proving to be elusive!

I have read somewhere that the latest OpenSUSE works out of the box with the Qualcomm 9212, but I haven't tried it yet...

Cheers!

---

### Post by msignor on 2009-11-28
Chiapo, 

SuSe still needs the firmware. I would suggest getting a copy of 9.10, then you can PM me and I can help you out past that point.. but you should be all set. 

-Matt

---

### Post by rampage_1973 on 2009-11-29
> **jamere said:**
> The following is "amartz"'s solution to the problem. Please post your results here if you can. I haven't had time to deal with it myself yet. Big THANKS to amartz!! chiafo what do you think?

Jim M
--------

Here's some notes I compiled when I was figuring this out:
Art

First thing, the modem needs it's firmware reloaded every time you turn it on. Without the firmware, it's just an empty shell. I've seen somebody putting together something to load the Qualcomm Gobi firmware from linux, but for now I do it from windows.

Boot to windows first, to load firmware into modem, then reboot to Ubuntu, without powering off.

wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing

art@art-laptop:~$ lsusb
Bus 001 Device 004: ID 05c6:9212 Qualcomm, Inc.

This is the only command you really need, the chat command is not needed, but is a convenient way to tell if the modem is talking.
~$ sudo modprobe usbserial vendor=0x05c6 product=0x9212
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

~$ ls -lha /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2009-07-23 11:29 /dev/ttyUSB0

The probe.txt is as defined in wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing
~$ chat -s -f ~/probe.txt >/dev/ttyUSB0 </dev/ttyUSB0
chat:  Jul 23 11:30:02 +GCAP: +CGSM,+DS,+ES
chat:  Jul 23 11:30:02 +COPS: 0,0,"AT&T",2
chat:  Jul 23 11:30:02 +CREG: 0,1

I would suggest to put the modprobe command in the file /etc/rc.local.
That is the last command which is run at boot time. As it is run as root
anyway, there is no need for sudo. To make the change, use the command

gksu gedit /etc/rc.local

and put the line

modprobe usbserial vendor=0x05c6 product=0x9212

_before_ the line

exit 0

Modem Manager software repository, add
deb [http://ppa.launchpad.net/modemmanager/ppa/ubuntu](http://ppa.launchpad.net/modemmanager/ppa/ubuntu) jaunty main
then run
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF2A6AFA
and
sudo apt-get update
thanks to amartz and to you jamere (and everyone else) this little trick worked for me on my ZG5 with at&t mobile broadband, still would like a way to load the firmware in linux though.
i am not sure that my skills will figure it out, while it is a pain to load windows then restart into linux to get 3g working at least it does work. oh i was using network-manager with the modprobe line in rc.local and i am running 9.10 karmic with kernel 2.6.31-14-generic , i did not have to add anything to the kernel (good thing too as i do not know how) other tidbits of info are if you suspend or hibernate you have to reload windows then restart linux again. :( what a pain! still believe ubuntu rocks though!!

---

### Post by jamere on 2009-11-29
Rampage, glad to hear it worked for you! Unfortunately it didn't work for me (mdl ZG8). I think Chiapo and msignor are hot on the trail for a solution. Unfortunately my Linux tech skills are pretty limited also. I agree that a Linux solution is the way to go. I checked launchpad and there's a bug described that looks like it may be the problem (Bug #303665). It's confirmed but no one is assigned the problem. Hopefully the bug gets officially fixed or Chiapo and msignor can come up with a step by step procedure for some of us to follow, otherwise, it'll be XP for me until an official fix is published. Sheesh.

---

### Post by msignor on 2009-11-30
Guys, 

I have to say that gobi_loader works perfectly for loading the firmware. I have successfully loaded firmware in Linux even rebooted and the card still works. 

I do not even have Windows on this machine anymore, and am typing this through my EVDO w/ Verizon..

Where are you guys stuck?

-Matt

---

### Post by Chiapo on 2009-11-30
I jumped ship & have been messing with openSUSE 11.2.

Still prefer xubuntu though, so will download the latest release .ISO today & report back as to my experience getting online with the Qualcomm 9212 in xubuntu 9.10.

Many thanks to all who have contributed to a resolution to this issue.:popcorn:

---

### Post by jamere on 2009-11-30
Chiapo, looking forward to your report on the latest .iso "experience"!!

For what its worth for those just needing to connect on 9.10 using the AAO Netbook and the infamous Qualcomm modem:

My setup:
Dual boot Win XP and 9.04
9.10 USB stick

Steps to connect:

- Boot in XP
- Connect to network
- Insert 9.10 USB stick
- Issue restart in XP
- USB stick boots 9.10 [you may have to change boot sequence in BIOS to put USB stick before hard drive]
- NW starts automatically

This isn't a good solution, but at least you can see the network actually work! I'm assuming the boot and restart in XP retains the needed modules
usbserial, qcserial and retains the loaded firmware as discussed by Chiapo and msignor.

Note: my provider is AT&T and "AT&T Data Connect 1" was set up automatically in Nw-mgr icon. I didn't have to edit the connection.

jim m

---

### Post by jamere on 2009-12-01
bump

---

### Post by Chiapo on 2009-12-03
I finally downloaded xubuntu 9.10 today...

The modem works without any effort beyond choosing an ISP & a few mouse clicks!

:popcorn:

I wish I would have downloaded the 9.10 .ISO a long time ago.

---

### Post by jamere on 2009-12-03
Chiapo,

Congrats on the 9.10 install!!! And I'm jealous! I think dropping back to 9.04 because of all the reported NW problems may have been a tactical error on my part.

A few questions...

1) Which 9.10 .iso version did you download? Desktop i386 Live CD?
2) Did you install from the Live CD?
3) What location did you get the .iso from?
4) Any partitioning problems? (assuming you're still dual booting?)

Do you think the Ubuntu folks update the .iso's frequently? I don't recall seeing a date identifier on the .iso's. Anyway, it would probably be smart to download the .iso again.

Thanks much and again CONGRATS!

jim m

---

### Post by Chiapo on 2009-12-04
Many thanks to you [jamere]("http://ubuntuforums.org/member.php?u=205923")! :KS

The modem still needs to be initialized in winXP, although I haven't got around to doing the make, make install of the gobi_loader yet.

I listed the steps I made here as per yours & msignor's instructions: [http://ubuntuforums.org/showthread.php?t=1157846&page=6](http://ubuntuforums.org/showthread.php?t=1157846&page=6) 

I downloaded the xubuntu 9.10 i386 Desktop ISO from the United States mirror link on the [http://xubuntu.org/](http://xubuntu.org/) site.

I then used unetbootin to write the ISO to the USB flash media from within xubuntu 9.04 Desktop.

As for partitioning, the Ubuntu partitioner is excellent! I have never had any serious problems with any of my numerous *buntu installations. In fact, I've used GParted to resize my WinXP partition twice now, with no problems whatsoever.
On the other hand, the openSUSE 11.2 debacle left me with my main xubuntu 9.04 partition formatted to ext4 & 100% data loss on that partition.
Apparently openSUSE 11.2 only plays nicely with Windoze!

Regarding Ubuntu ISO file updates, I believe the stable release is static, whereas the "Daily Build" files are more on the cutting edge of development, thus recommended for testing purposes.
For a production machine, you want to use the most recent "Stable" release. 

There are different ISO's within a release, such as the UNR, the "Alternate," etc. All of which are 9.10.

I choose the desktop release because I like the traditional interface, & I believe this Netbook has ample resources to support a full desktop version.

Thanks for the encouragement, & much gratitude to all who've helped!

I'll report back after I make & make install the gobi_loader.

---

### Post by amartz on 2009-12-04
> **jamere said:**
> chiapo,

I did see a posting here on the Ubuntu forums by "amartz" that appeared to have a solution but wasn't very eager to share it.


Now wait just a minute here! I was looking for a couple people to work one on one with while I tested my notes.  I didn't want to post something that only I had tested, I wanted somebody else to prove it would work also! I just now found this thread.
Art

---

### Post by amartz on 2009-12-04
> **msignor said:**
> Hey Guys, 

When i try modem-manager it does not and according to debug its because i dont have privelages.. even when I run with sudo. 
Cheers,

Matt

I can only speak to 9.04, not 9.10. The modemmanager that defaults with 9.04 did not work for me. The version in launchpad, as I documented, did work.
Art

---

### Post by Chiapo on 2009-12-04
The gobi_loader works! Much gratitude to msignor & jamere for sharing knowledge resulting in this workaround!!

I suggest a fresh install of 9.10.

I'm using xubuntu 9.10 and the network speed seems faster than when using WinXP! 
------------------------------------------------------------------------------------------------------------
Sorry amartz, I see no reason to hide offline, when we could use as many minds as we can get to work on issues such as this.

Working offline defeats the purpose of this forum, in my opinion.

Thank you for all your help!

---

### Post by amartz on 2009-12-04
> **jamere said:**
> Hey guys, thought I'd give amartz's procedure a try but didn't get very far. I also noticed (as chiapo did) that 9211 changed to 9212, I assume after firmware load in XP. I also received the following:
FATAL: Module usbserial not found

Is this a correct assumption on my part, that once a successful
modprobe is made on usbserial, that the network should light up until the next power off (after a new mobile broadband connection is edited and added)?
jim m

You are correct, changing the 9211 to 9212 shows the Qualcomm firmware has been loaded. Did you do "sudo modprobe usbserial vendor=0x05c6 product=0x9212", including the sudo? The modprobe won't work except as root.

And yes, the network stays up until power-off, or every once in a while, it just hick-ups and looses it's firmware, requiring a brief reboot back to XP.  BTW, my usbserial lives in /sys/module/usbserial and /sys/bus/usb/drivers/usbserial.
Art

---

### Post by amartz on 2009-12-04
> **msignor said:**
> 

You MUST have both 'usbserial' and 'qcserial' modules on your system. Technically before you load the gobi loader, you should be getting a /dev/ttyUSB0 that you can do nothing with (due to firmware)... 
-Matt

It's my understanding that 9.04 has only usbserial, not qcserial, and that it takes 9.10 to get qcserial.
Art

---

### Post by amartz on 2009-12-04
> **Chiapo said:**
> 
Sorry amartz, I see no reason to hide offline, when we could use as many minds as we can get to work on issues such as this.

Working offline defeats the purpose of this forum, in my opinion.

I didn't want to spread mis-information. Interesting to see how you are making out with 9.10.  I was looking to upgrade so I wouldn't need XP, but I've heard enough about 9.10 to give me pause. One thing I'd like to be able to do is test the gobi.loader from the live-boot disk before I upgrade, but I'm not sure that would work. Anybody try it that way?
Art

---

### Post by jamere on 2009-12-04
amartz, no offense intended on my part. We gladly gave you credit for your work, by name, and your work is appreciated by us all. Anyway, you're more than welcome on this thread. You have a couple of sharp guys to work with in Chiapo and msignor. I kind of tag along since I don't have the Linux internals and Terminal skills like these guys. I think msignor has the solution and Chiapo is close if he hasn't solved it already. Hopefully you guys can document the detailed steps to the solution (independent of Windows) and maybe even submit an official solution thru Launchpad or whatever the official Ubuntu fix route is. The last I checked there were quite a few "views" on this thread, so there are probably quite a few folks interested in the solution.

jim m

---

### Post by meread on 2009-12-04
Hello Jim,

You are far from alone in your problem and your quest although mine is a ZTE device marketed through T-mobile (UK) as their usb 120 mobile broadband stick.

Like you I run a laptop with a previous version of ubuntu (8.04 LTS) as this works great for when I am away visiting clients and don't want to risk upgrading for a while yet.  Hotel charges for WiFi are horrendous so I would like my dongle to work but although it is recognised by network manager I just cannot get a connection.  I tried the T-moble support forum and tried some suggestions from there but it is very much like hitting a blank wall all the time.

The problem with this particular forum is that it is so active if the guy with the answer isn't around when your message is in the current 50 it gets missed.

My next attempt will be to set up a persistent live CD system and if that doesn't work will try bluetooth with the mobile phone.  Finally I will keep watching this forum as you never know one of the developers may just come up with the driver you need.

good luck 

Roy

---

### Post by amartz on 2009-12-04
> **jamere said:**
> amartz, no offense intended on my part. We gladly gave you credit for your work.jim m

No offense taken! :-) It's not a matter of credit for me, although I don't object. But I did want to try to get it right first.

I'm interested in the part with different versions of 9.10, and one of them supposedly works out of the box? Did we still have to make the gobi.loader? Can we prove it with a live-boot CD without upgrading?
Art

---

### Post by jamere on 2009-12-04
Roy, welcome aboard! I think the guys here have the problem pretty much defined and close to a solution. "msignor" may even have it solved and working independently of Windows. Still looking for one of those developers to visit our thread! :D

---

### Post by jamere on 2009-12-04
Art, you might want to go back and checkout msignor's and Chiapo's dialog's and see what you think. Check post #35...looks to me like he has the independent solution working. What do you think? I can kind of follow what msignor's saying, but don't have the Terminal skills to do it. Haven't seen him back on the thread, however.

jim m

---

### Post by jamere on 2009-12-05
Well, I think I'm going to try to install 9.10 on my dual boot XP and 9.04 laptop, using my 9.10 USB stick. Yes, I really should know better than to put at risk my only reliable XP NW connection, but think it would be good to get to 9.10. So if you guys don't hear from me for a while, you'll know what happened! ;)

jim m

---

### Post by meread on 2009-12-05
Hi Guys, 

Thanks to everyone's hard work I have made progress though in a negative sort of way.

I mean I think I now know why my modem does not work.

Facts
I am in UK using a t-mobile dongle
Boot up laptop
plug in dongle and up it comes as a flash drive but configured as using a CD drive.  Not listed in lsusb (except as 19d2 2000 as in previous post somewhere I've lost track looked at so many)
Eject 'CD' drive
lsusb now shows 19d2 : 0031
do the sudo modprobe usbserial vendor =0x19d2 product=0x0031
and many dev/ttyu0 through ttyu9 ua ..uf (gosh of course its hex)
but no ttyusb0 or 1 or 2 at all

I feel sure that the hardware in this dongle is different from others as 
1) it is new bought 5 days ago.
2) when listing under modprobe? (forget is shows ONCA a belgian company
3)but model number on reverse is MF626

very puzzling but feel as it will not mount as as a usb0 or 2 or 3 I am up the creek

Cheers

Roy

---

### Post by jamere on 2009-12-05
guys,

Here's the actual error message I got in nm-tool after trying to connect via 9.10 Desktop:

** (process: 2076): Warning**: Tried to set deprecated property GSM/Band

Has anyone seen this error msg from nm-tool? Or checked into it in any way such as Google search?

--------------------

Well, did Google search on: > "Tried to set deprecated property GSM/Band"

Quite a few references to 9.10 Network Manager and Modem Manager reported bugs and problems

---

### Post by Chiapo on 2009-12-05
I think I need to learn how to use the gobi_loader the right way.

I cold booted into xubuntu 9.10 linux kernel 2.6.31.15 with gobi_loader, but was unable to connect via the Qualcomm 9212 3g modem.

I fooled around with gobi_loader but no 3g connection was made.

Then I warm booted into Ubuntu Netbook Remix 9.10 linux kernel 2.6.31.14 generic, and the 3g connection was automatic! No WinXP loading the firmware!

This post has some pertinent info: [http://ubuntuforums.org/showthread.php?p=8447642#post8447642](http://ubuntuforums.org/showthread.php?p=8447642#post8447642)

I'm afraid we'll need someone with more ubuntu smarts to help out with the use of the gobi_loader, but it seems like we're getting closer!

Cheers!

---

### Post by Chiapo on 2009-12-05
Warm boot from UNR to xubuntu resulted in an automatic 3g connection!

No WinXP loaded firmware!

---

### Post by Chiapo on 2009-12-06
Another cold boot into xubuntu, followed by unloading & reloading qcserial & a click on gobi_loader resulted in no 3g connection, but a subsequent warm boot into Ubuntu Netbook Remix 9.10 resulted in an automatic 3g connection, No WinXP involved.

Of interest was the fact that when I tried to edit the 3g connection in Network Manager while in xubuntu, authentication failed & Network Manager locked up.

:confused:

---

### Post by msignor on 2009-12-06
Hey guys, 

I wanted to confirm some things:

- Yes, I did everything from Linux, with the exception of actually activating the card on Verizon. You NEED to be running windows in order to get this to work properly. You also can not just remove the card and put it in a machine that is already running windows since the card is usually keyed to the manufacturer through firmware. That was the case with my Lenovo but you guys may be different. 

- From a cold-boot, I can login, and have no available 3g connection. When I reboot from that point, then I do have 3g connection just fine through network manager. 

The issue here is that NM is loading before the gobi_loader initializes and then NM misses the card. If you can reboot just the modem-manager portion (or restart network manager) then the card will work on the first boot. Another option is to put the actual command to load the firmware w/ gobi_loader in the rc.local located in /etc/init.d

My solution is to just use sleep mode. My machine with the SSD is quite pepppy so I dont notice the save / restore for sleep mode. 

-Matt

---

### Post by pdc on 2009-12-07
Phew! What a busy thread!

to meread in post #54

I would suggest you have a ZTE MF626; (it is the little brother to the ZTE MF636)

[http://www.draisberghof.de/usb_modeswitch/#hardware](http://www.draisberghof.de/usb_modeswitch/#hardware)

listed in hardware: 

the latest usb_modeswitch has a .deb package, that seems to auto-run and auto-configure

---

### Post by longjohn119 on 2009-12-07
They still aren't initializing this properly ....

In windows if you boot into the system with the 3G enabled you can't get it to connect properly either. You have to turn it off and back on again ... It's when you turn the switch on that it calls the loader program which is always running in the background as a Service ... This is probably why sometimes when you boot to Windows first and reboot into Linux it works and sometimes it doesn't .... You can confirm the operation of the loader by turning the Qualcomm Gobi Loader Service off in Services, opening up the Device Manager in Windows and switch the 3G on and off .... when you turn it on you have a 9211 serial port and no modem .... Now turn the 3G switch off, start the Loader Service and turn the 3G switch back on and it loads the code and initializes a 9212 ethernet adapter, a modem and two serial ports 

So basically they need a hook in the network manager that tells Gobi Loader to execute when it senses the switch go on and perhaps have Gobi Loader running as a Service ... The ironic part of all this is the two programs it loads are written in Embedded Linux so that must be what the ARM computer in the Gobi chipset runs

This all reminds me of the old Winmodem days in the 90's when most still had dialup access and most modems preinstalled in computers wouldn't work in Linux for similar reasons

All I can say is they better get a team on it because these Gobi cards are going to be the de facto standard for netbooks and laptops in about a year because it means manufacturers will need only one modem for worldwide service AND sales instead of multiple cards for two completely different services and different country's frequency bands .... All the Panasonic Toughbooks are going to use them (Many already are) because of their worldwide capabilities and built-in GPS capabilities which Acer (and HP) really needs to support like Lenovo, Panasonic, and Dell do using the exact same card .... Linux needs to be able to enable the GPS on these too but first they need to learn to get working for 3G from the Network Manager because you have to enable the GPS through a Network Manager .... Since they appear to be running Embedded Linux on these devices this should be doable

---

### Post by jamere on 2009-12-07
msignor, pdc, and longjohn...thanks for checking in here guys and thanks much for your VERY informative comments! Msignor, glad to see you back. Was afraid you'd gone on to bigger and better things since you had an apparent workable solution. ;D

I think Chiapos thread and this thread are beginning to get a lot of "eyeballs" judging from the quickly growing number of views. I know Chiapo is busting his rear trying many different configurations to come up with a consistently workable solution. Most of us, myself included, aren't terminal wonks, so we have to pretty much be given terminal commands and step-by-step procedures that can be cut and pasted into Terminal to accomplish a solution. Msignor's given us some very good info also, however I can't work at the "source" level and don't have the know-how to do kernel "makes" and that sort of thing.

I agree with longjohn in that with all the netbooks being offered by the major providers this will quickly turn into a huge problem for the Linux developers. On the surface, it doesn't appear to be that complicated of an issue (easy for me to say). Looks to be a matter of getting the developer's attention and their setting a high priority for the problem. Anyone know what the development process is and if this problem has the attention of developers?

I guess the question I would ask is...Are we beating our heads against the wall trying to come up with solutions for this problem? Hopefully some developers will take notice of this thread and Chiapo's thread!!! Probably a growing segment of Linux netbook users who can't get a connection. My 2 cents, fwiw :confused:

My own goal here is to hopefully come up with a NW connection that is at least consistent enough to get into the Update Mgr process or to be able to download a new .iso that has this problem fixed. Any ideas or comments welcome! And thanks again guys, for your informative input here.

jim m

---

### Post by Chiapo on 2009-12-07
How does one stop & start NetworkManager from the command line?

Does disabling networking via the network icon do it? I don't think so.

---

### Post by jamere on 2009-12-07
Good question...I wondered that myself.

---

### Post by amartz on 2009-12-07
> **jamere said:**
> Good question...I wondered that myself.
Well, under Startup applications preferences, the network manager entry has "nm-applet --sm-disable"
Art

---

### Post by longjohn119 on 2009-12-07
> **Chiapo said:**
> How does one stop & start NetworkManager from the command line?

Does disabling networking via the network icon do it? I don't think so.

sudo restart network-manager

sudo stop network-manager

sudo start network-manager

I still can't get it to properly initialize, the code seems to load, it appears in the network manager but it won't hook up *** If I boot into Windows and 3G is already on the symptoms are exactly what I am seeing in Linux, The modem is there, the code seems to be loaded but it won't hook up unless I reset the 3G

The only way I can get it to work is make sure 3G is on when I leave Linux, boot into Windows and turn the 3G on. If it's already on I have to turn it off and back on to get it working properly which I verify by starting the Acer connection manager and make sure I have a signal (but I don't connect) Reboot into Linux and my connection will work until I turn off the 3G switch, then I'm screwed and have to go through the whole double boot process. 

I haven't had any success cold booting into Linux and getting it to hook up properly even though it shows up in the network manager ... when I run nm-tool from the command line it shows a 9212 device which means the code is loaded but it shows the modem as off ...

---

### Post by longjohn119 on 2009-12-07
Note also the modem process is two step in Windows, the Windows network manager turns the modem on and loads the code which let's the modem search for signals

Step two is the actually connect process which CAN NOT be done from the Windows network manager hence the Acer 3G manager app

I don't think it will work in Linux until they duplicate the same two step process instead of trying to turn on and connect all in one process which is how the Network Manager in Linux appears to be doing (Actually it appears to be NOT turning on the modem but just trying to connect to a modem that's off)

---

### Post by msignor on 2009-12-08
Hey Guys, 

So I wanted to clarify some of my experiences here...

I AM able to work from a cold-boot where NM loads, aircard is detected, and the connection works. I have found that there is a 50/50 shot depending on when / how fast the firmware is loaded and whenever networkmanager scans for the hardware that it can use. I have also seen experiences when NM does not show the card, and the ONLY thing I do is reboot ubuntu and then everything works as it should. 

*I also have been experementing with acutal timings of things and I have found that more times than not, when I let the system "rest" at the login screen for a minute or two, I am more likely to see a working 3g connection from the start.... I have nothing solid to test this theory.. just my $.02 *

For the record, I have not used windows to do anything other than actually activating the card on Verizon (my carrier). Everything I have done to get this working has been directly in Linux from the start. 

The gobi_loader does state that when installed, it adds the Udev rule to automatically load the firmware when the card is detected. That is happening just fine for me, however, I believe that we need to actually invoke the gobi_loader as part of the rc.local to ensure that it loads at boot, before network-manager loads. I have not had a chance to actually try this out but from my past experiences that should solve the issue. Additionally, the part of NM that controls the mobile cards etc, is "modem-manager" and that is the specific service that should be restarted after loading firmware and confirming the product ID changes.. (as stated that it does by others)

I agree with some of the comments here that the gobi cards are not going away.. I actually ordered a few more for my customers in their Lenovo's.. but NM should have some type of "refresh hardware" button that will rescan the machine... I think that this way we can avoid these types of issues where firmware has to load, initialize, etc.

Finally, I think it is important to summarize where this thread is at in terms of progress.... I think that at this point, everyone reading should be able to actually use their card without having to use windows at all.. Please know that if you have not already seen...the other thread on this forum about this card in the HP notebooks goes in the specific detail that some are looking for regarding the command line and how to build gobi loader etc. ([http://ubuntuforums.org/showthread.php?t=1008200](http://ubuntuforums.org/showthread.php?t=1008200))

Here are the steps summarized on how this should work...

1) Confirm that you have the modules "usbserial" and "qcserial" loaded
2) Confirm that your card is found in LSUSB, and note the product ID, for the Qualcomm card. 
3) Download / Make && Make Install the gobi_loader application
4) Create the folder /lib/firmware/gobi
5) Copy CDMA or GSM firmware from windows driver pack, to the firmware directory 
6) Unload & Re-Load the 'usbserial' and 'qcserial' modules
7) Run LSUSB, and now you should see a different Product ID (Bus 002 Device 003: ID 05c6:9202 Qualcomm, Inc.  -- is what yours should look like) 
*** If this is all good, open a dialer like minicom or gnome-ppp or wvdial and make a connection to /dev/ttyUSB0 ***

For reference, the original product ID that is seen is for the Loader portion of the card. That is how we can load the firmware. The new device id shows us that the firmware was applied and is now running. 

-Matt

---

### Post by msignor on 2009-12-08
@chiapo: In the HP thread, you claim that you see no difference with and without gobi_loader.... it is important to know that WITHOUT the firmware loaded you will still get a /dev/ttyUSB0 device that LOOKS like a modem, but you cant actually do anything other than load firmware into it. This is *exactly* whey you need to still boot into windows first...

You need to load the firmware so the device ID changes and ONLY when that happens is the card going to let you dial with /dev/ttyUSB0

---

### Post by jamere on 2009-12-08
Anyone have any idea how to alert developers to this problem? I'm afraid that Ubuntu could lose quite a few users if this problem isn't addressed soon. Just my thoughts...:confused:

---

### Post by Chiapo on 2009-12-08
Interesting point msignor... I was referring to the ability of the xubuntu 9.10 2.6.31.14 generic Desktop USB startup disks ability to establish a connection, but I forgot that WinXP had already loaded the firmware.:p

Sorry to add confusion.

So to start/stop modemmanager would the syntax be the same as for NetworkManager?

Thanks for your time.

Cheers!

---

### Post by longjohn119 on 2009-12-08
Obviously there is a difference between the way Lenovo and Acer work with this card, your steps simply do not work on an Acer ... I get the number change from 9211 to 9212 which means the firmware has indeed loaded but I have to jack around with turning the Network Manager off and on to get it to see the modem but even then it won;'t hook up and nm-tools shows the modem as on but not enabled (obviously a software switch) 

Does the Lenovo have a panel switch to turn the 3G on and off? Perhaps the Acer doesn't intitialize it the same because of the manual switch for power savings 

With the Lenovo you can even use the GPS under Windows with the latest Lenovo 3G/network manager ... Ditto for Dell and Panasonic.

Only people who can't use the GPS are Acer, HP and all Linux users no matter what brand

---

### Post by msignor on 2009-12-08
@longjohn: I have a physical hardware switch to turn my wifi / evdo on and off. I also most likely can shut the card off by echoing a state in linux.. but I have not really researched this. Irconically, if I put my machine in sleep mode I have to cycle the hardware switch to get the light to turn back on.  Perhaps you are right with the fact that the firmware is specific to the manufacturer... I had attempted to activate the card in another laptop rather than format my already installed machine and put on windows but it was no dice...

However, If Chiapo can get it working with the "boot to windows, then boot to linux" method then there has to be a way to load the firmware from linux.... Gobi is a common platform so the loader should work regardless of the vendor. 

After you load the card firmware, try to access the modem through "minicom". You may have to download the package.. but start minicom with "minicom -s" go to the serial port setup, and set the serial port to "/dev/ttyUSB0".. You should then be able to save the changes, and connect with them.. In my case, I get a modem initialization session. I can type "AT" and I get "OK" back.... Can you confirm that you have a /dev/ttyUSB0 also?

On another note..... I wonder if you can take the firmware from another vendor and use it on your machines.. I know in my case, I got the firmware from Lenovo's website, not verizon..

--

I can report that after adding the line to invoke Gobi_loader in rc.local, I get evdo on boot consistently.. (at least the last 3 or 4 times I tried) 

OpenVPN plugin still crashes all the time.. but thats another story all-together. 

-Matt

---

### Post by longjohn119 on 2009-12-09
I'm thinking it's more of a BIOS level problem, After the modem is loaded and turned on by Linux something in the BIOS cycles the 3G switch off and back on and Linux loses the modem

However it works it's not very usable in Linux right now and I really don't have the time or inclination to jack around with it any longer. I'm doing a netbook to touchscreen chartplotter conversion (With Internet access for live weather radar) and was hoping to use Linux for it's flexibility in setting up custom desktops but the drawbacks (No internet, no mature advanced Linux based GPS/mapping software so I have to make my Windows mapping program work under WINE) have tipped the scale back to running  XP  

I was also hoping there would be a better chance of getting the GPS working on this card too but I can see that's probably not going to happen anytime soon ... Also important is others being able to easily duplicate what I'm doing

---

### Post by Chiapo on 2009-12-09
I've had several successful connections without Windows, and without rebooting.

Sometimes when a webpage won't open, the numerical IP address will work, so looks like some DNS issue as well.

When no 3g connection is established, I switch off the modem using the slider switch on the front right edge, then I stop network-manager, then unload qcserial, switch on the modem, reload qcserial, invoke gobi_loader, restart network-manager, and a connection is made.

Of interest is that if I leave my mouse cursor on the Network icon, the tool-tip reflects some of the connection information such as "requesting address from network."

I haven't tried the addition of the gobi_loader to rc.local yet.

Maybe it's time I tried.

Cheers!

---

### Post by amartz on 2009-12-09
> **Chiapo said:**
> I've had several successful connections without Windows, and without rebooting.

Sometimes when a webpage won't open, the numerical IP address will work, so looks like some DNS issue as well.


This is from a complete power-off? I've got an icon on my top bar to run a script to reload my /etc/resolv.conf file. Network manager doesn't always do a good job maintaining this file, especially when you are connecting and then disconnecting to/from a vpn.
Art

---

### Post by Chiapo on 2009-12-09
Yes, I'm connecting from zero power, through GRUB, then xubuntu 9.10 2.6.31.15 w/gobi_loader, to a desktop that sometimes says GSM Network Connected, but no websites will load unless I enter the numeric IP address.

So I stop network-manager;

Then I switch the modem off via the slider on the right front edge;

Unload qcserial;

Reload qcserial;

Switch on the modem;

Run gobi_loader;

Start network-manager;

Connection is sometimes failing to resolve DNS, so I try varying the use of gobi_loader depending on what lsusb shows for the Qualcomm device.

Still haven't had 100% success, but I'm surfing again today without using Windows.

---

### Post by msignor on 2009-12-09
@Chiapo: Can you ping an IP consistently or do the pings actually stop as well? You should not really have any random DNS issues since NM is being assigned everything as soon as a connection is made. Also, do you have strong signal where you are? 

I had almost exactly the same issue where some websites load, then nothing, then it works again and it just turned out to be the signal at the portion of the house I was in. 

Alternatively, you can edit the /etc/resolv.conf and specify the nameservers to use manually if there is an error.

---

### Post by msignor on 2009-12-09
> **amartz said:**
>  Network manager doesn't always do a good job maintaining this file, especially when you are connecting and then disconnecting to/from a vpn.
Art

Agreed. I have had to completely flush the file and shutdown NM to get DNS working properly after quickly switching WAN / VPN connections

---

### Post by msignor on 2009-12-09
> **Chiapo said:**
> I've had several successful connections without Windows, and without rebooting.


Can you confirm that there is nothing special that you did in order to get it working? I think it is important to note since we may be seeing an issue across models or vendors that make this not work.

---

### Post by amartz on 2009-12-09
> **msignor said:**
> Agreed. I have had to completely flush the file and shutdown NM to get DNS working properly after quickly switching WAN / VPN connections

All you have to do to restore the DNS lookup is run a script with a command similar to this: "sudo cp resolv.conf_ATT /etc/resolv.conf", where resolv.conf_ATT contains DNS entries known to work. When you get a working DNS, just copy /etc/resolv.conf over to a backup name, and then write a script to when needed, overwrite the current resolv.conf with your working backup copy. Nothing more need be done, nothing restarted, no gobi loaded.
Art

---

### Post by Chiapo on 2009-12-09
Here's a link to a desktop session recording where I cold boot into xubuntu, but no connection is established until I fool with network-manager.


[http://cid-717bb077cc496be4.skydrive.live.com/self.aspx/.Public/3g%5E_connection.ogv](http://cid-717bb077cc496be4.skydrive.live.com/self.aspx/.Public/3g%5E_connection.ogv)

It's 33 MB so a fast connection would help.

I used gtk-recordMyDesktop to make the video.
I tried using WinFF to convert the video so I could upload to YouTube, but WinFF ended with an error about unknown codec: libmp3lame or something like that...

Cheers!

---

### Post by jamere on 2009-12-11
bump to see the 'views' count. Are we at the end of the line on this issue?


Note: View count = [COLOR="Red"]2090 [/COLOR]3:23 pm

must still be an issue with quite a few folks!

---

### Post by longjohn119 on 2009-12-12
I'm done with it ... for now

I did make some progress getting the GPS to enable under XP, I get a fix but I can't get any data out of the NMEA serial port to my mapping apps yet ... 

Novatel has a Linux SDK (Based on the Qualcomm SDK) for this same chip set which includes the loader API, USB API, connection API and GPS API but I'm no programmer ... I guess the licensing is too restrictive so no one in the Linux Community is using it

---

### Post by jamere on 2009-12-12
longjohn,

Thanks for checking in. I hate to see the thread come to an end as we've seen lots of great participation and good ideas here. My Linux tech skills are pretty limited so couldn't participate in much detail, especially the Gobi loader thing. It looked like Chiapo was beginning to get pretty consistent connections without booting first in XP. I downloaded the Xubuntu iso and installed along side XP and 9.10 and was able to connect long enough to make an Update Mgr run (128 updates). The update did include a newer version of the kernel (2.6.31-16 #52). However was only able to connect one more time after much fiddling and cajoling and then never again. It looks like AT&T (my provider) has a stand-alone process that I have to start called the AT&T Communication Mgr, to make the connection. It appears to manage WIFI and Wired as well as, broadband. It also appears that Linux is handling in one step through Network Manager. Someone here mentioned that there may even be disparities between Acer models (I have ZG8 [530]) in dealing with this problem.

Not sure where to turn now. Don't know anything about the Canonical development process or how to get the attention of developers to this problem. I think the problem will only compound itself as there are more netbooks being offered by the major providers and they appear to be very popular.

I think my only option, after using Ubuntu for several years exclusively, is to endure the dreaded XP until this problem is resolved. I was hoping someone would come up with a detailed, cut and paste solution, but that is probably unlikely.:(

---

### Post by jamere on 2009-12-13
bump

---

### Post by longjohn119 on 2009-12-14
Qualcomm announced on Oct. 28th that they were starting a new Open Source division so hopefully we'll start seeing better support soon

SAN DIEGO — October 26, 2009 — Qualcomm Incorporated (Nasdaq: QCOM), a leading developer and innovator of advanced wireless technologies, products and services, today announced that it has established a separate wholly-owned subsidiary, Qualcomm Innovation Center, Inc. (QuIC), focused on mobile open source platforms. QuIC has brought together a dedicated group of engineers to optimize open source software with Qualcomm technology. The QuIC board of directors has named Rob Chandhok, senior vice president of software strategy for Qualcomm CDMA[ ]("http://www.qualcomm.com/products_services/glossary/index.html#cdma") Technologies, as president of QuIC.

“Open source and community-driven software development is becoming increasingly important to the wireless industry,” said Chandhok, “and QuIC is committed to meaningful participation in these development efforts. To fulfill this commitment and to provide focus to this effort, Qualcomm has transferred experienced software engineers to QuIC. These engineers will focus on such important open source initiatives as Linux and Webkit, and on open source operating systems such as Symbian, Android and Chrome.”

---

### Post by jamere on 2009-12-14
longjohn, THANKS for the encouraging news!

---

### Post by jamere on 2009-12-17
You can contact Qualcomm here:

Contact Us

Thank you for your interest in Qualcomm Innovation Center, Inc.(QuIC). For more information or any other general inquiries, you are invited to contact us at:

Email: [email]info@quicinc.com[/email]

---

### Post by longjohn119 on 2009-12-18
I've started a series of posts on my Blog about the Qualcomm UNDP-1 Gobi 1000 module after a couple of weeks of research. I'm trying to make a centralized location for information on this module. Check it out and let me know what you think. This is in part a lead up to getting the included GPS to work for those of us who's manufacturer failed to include that support.  When we come up with a one-click solution to making this module work under Linux I'll do a write up on that too .... Ditto if someone gets the GPS working under Linux

[http://netbook2chartplotter.blogspot.com/](http://netbook2chartplotter.blogspot.com/)

---

### Post by jamere on 2009-12-18
Good idea longjohn. You have a very interesting blog! Didn't realize the Acer ZG8 has GPS capability built-in.

Sent the following email to Qualcomm Innovation Center, Inc.(QuIC): 

Glad to see Qualcomm taking an active interest in Open Source matters. I (and many others), have new Acer Netbooks that will simply not make a broadband wireless network connection using the newest Ubuntu Linux operating system (9.10). I have a dual boot Windows XP and Ubuntu Linux on my Netbook. Broadband wireless works flawlessly with XP and absolutely won't connect in Linux. I've been a long-time user of Linux exclusively and was really dismayed to find that my new Netbook simply would not make a broadband wireless network connection. Hopefully, with the expertise and help of your engineers and software folks, this problem will be resolved quickly.

I might suggest that your tech folks have a look at the Ubuntu Forums (Networking and Wireless sub-category) to get an idea of the many problems reported concerning wireless modems (not just Qualcomm modems).

Here's my thread in the Ubuntu Forums, in particular:

[ubuntu] Qualcomm HS-USB-9212 in Acer Aspire One--No connection

[http://ubuntuforums.org/showthread.php?s=d78aeb3071a5d09daa1e222c9eeb802](http://ubuntuforums.org/showthread.php?s=d78aeb3071a5d09daa1e222c9eeb802)
1&t=1330488&page=9

Thanks much for your help in this matter...many of us using Open Source systems will appreciate your attention to solving this problem.

Jim M
Ubuntu Linux user

Note:
I know they received my email because I got a "read" receipt, but no "reply" as yet

---

### Post by longjohn119 on 2009-12-18
There are a couple of problems that need to be addressed here, first and foremost the Gnome team needs to come up with a 3G connection manager that works with but is separate from the Gnome Connection Manager. That's how it's done with EVERY 3G modems I've seen under Windows .... A very promising Linux program is being developed in Germany by the guys who wrote the Windows MWConn 3G connection manager [http://www.mwconn.com](http://www.mwconn.com) Someone needs to put the Gnome team and these guys together

Secondly I found this in the latest Qualcomm SDK

Linux USB Drivers

Composite driver
**************
Serial driver that supports QDL (for firmware download) and modem devices

NMEA (proposed)



RmNet network driver (proposed)
*****************************
Qualcomm proprietary network driver (control and data path)



The serial driver we have, qcserial but ALL that does is set up the program loader and creates a modem. In windows a USB Ethernet Adapter(The RmNet network driver) is also created and this is basically  part of the Gobi API in QCWWAN.dll which is how you get things lacking still in Linux, diagnostics, signal strength, controlling the GPS and redirecting the GPS to a NMEA serial port, etc

So basically we are kinda screwed until Qualcomm finishes their proposed Linux equivelent of QCWWAN.dll .... Until then any solution I'm afraid will be half vast .....

---

### Post by jamere on 2009-12-19
longjohn, your comment makes a lot of sense. Looks like we're at the mercy of several bureaucracies. Hopefully this problem will be fixed soon. In the meantime, I was able to make a connection on 9.10 (kernel 2.6.31-14 #48 ) long enough to do an Update Manager run which installed a multitude of fixes. Since doing the update it seems much easier to make the network connection in 9.10, however I still have to boot Win XP first to load the firmware before restarting in 9.10. I'm fortunate to have a dual boot setup. Don't know what folks without dual boot ability would do. Probably SOL. As you say...half vast!

---

### Post by jamere on 2009-12-21
> Since doing the update it seems much easier to make the network connection in 9.10, however I still have to boot Win XP first to load the firmware before restarting in 9.10.

I really shouldn't say it's MUCH easier. It's still hit-or-miss getting a connection and it usually takes a combination of the following TERMINAL commands and sacrifices to the "network" gods:

> sudo stop network-manager
sudo start network-manager
sudo restart network-manager

Judging from the number of views of this thread, there's still a lot of interest! Eagerly awaiting a fix for this problem.

jim m

---

### Post by msignor on 2009-12-22
Hey Guys, 

I have been keeping up with this thread, but wanted to throw this out there for some clarification. 

As mentioned before, the only reason we are able to make a connection now is due to "qcserial" module and the ability to load the necessary firmware to it. Linux is using a (generic) USB-Serial module to provide the ability to make calls out that serial device. 

This is important to note in my eyes since some people reading may wonder "it works, why do I need to wait for the Qualcomm drivers?" And the reason is just because there are no other capabilities of the card available to us; other than just being able to dial.. GPS.

Just my $.02

---- 

PS: Still running strong on my Lenovo x301, no issues and the connection is available every time I boot after adding the loader to the rc.local

-Matt

---

### Post by longjohn119 on 2009-12-22
More stuff than you realize, I have the QCWWAN.dll API and there are 70 functions in the API, only a couple have to do with GPS. 

The set for the Gobi 2000 API is even larger as it adds Assisted GPS, Win7 compatibility and some other functions

Win7 also has a problem with loading the code because even the 32 bit versions now have the Driver Signing crud they put in the 64 bit versions of Vista (and 64 bit XP to a lesser extent) ... If you upgrade from a working system (unlikely since you can't go upgrade from XP, only Vista) it'll keep and use the old drivers but a fresh install it won't except the firmware loader program .... OK that's not really a bad problem and easy for Qualcomm to fix, the real problem is it will take months to go through the Microsoft Certification process and get the drivers signed

This also sucks for Linux folks because it no doubt steals human resources from the Linux development to please the larger Windows customer base and OEMs

---

### Post by jamere on 2009-12-23
> PS: Still running strong on my Lenovo x301, no issues and the connection is available every time I boot after adding the loader to the rc.local

Matt, any way you can show the terminal commands to add the loader to the rc.loc? For us technically challenged folks to cut and paste.:confused:

Thanks in advance.
jim m

---

### Post by jamere on 2009-12-23
bump?

---

### Post by jamere on 2010-01-04
Anyone have any new information concerning this problem? Guess it's up to Linux/Qualcomm. Probably SOL.:confused:

---

### Post by jamere on 2010-01-04
Over 4000 views...still getting lots of eyeballs on this thread.

---

### Post by jamere on 2010-01-07
There's hope yet...see following dialog with Markus from MWconn...




Hi Markus, and thanks for your reply! I'm very encouraged to hear

"there is a MWconn version for Ubuntu under development".

I'll post your encouraging reply in my thread on the Ubuntu Networking Forum. At last count, there were more than 4,000 views of this thread. There are apparently MANY Acer Netbook Ubuntu users trying to use the built-in Qualcomm modem to no avail. Maybe some of the more technically astute folks on the forum can come up with a solution. 

Is there some way we can keep abreast of progress on the MWconn version that is currently under development? I'd sure like to see a Ubuntu solution in the near future! ;-)

Keep up the good work guys!

Jim M


> feedback@mwconn.com wrote:
> Hi Jim,
>
> thanks for your mail!
> I'm sorry to hear that there are problems starting Qualcomm Module with Linux.
> I confess, I do not know what operating systems are supplied by Qualcomm. As far as I remember, the 3G module's firmware must be loaded to the module's RAM at every startup. Using Windows, this is ensured by a special Qualcomm DLL. MWconn uses this DLL, MWfwman.exe too ([http://mwconn.info/wiki/index.php/Qualcomm](http://mwconn.info/wiki/index.php/Qualcomm)).
>
> Maybe there is no replacement for this DLL under Linux. :-(
> But you could try to install the DLLs MWconnQC.dll and QCWWAN.dll in Wine and then load the module software with MWfwman.exe.
>
> If you manage to solve this problem, please write me how you did it. I would be very glad to relay any information to other users or future users. [COLOR="Red"]Currently, there is a MWconn version for Ubuntu under development.[/COLOR]
>
> Best regards, good luck!
>
> Markus
>
>
> -------- Original-Nachricht --------
>   
>> Datum: Mon, 04 Jan 2010 16:08:45 -0600
>> Von: Jim M 
>> An: [email]feedback@mwconn.com[/email]
>> Betreff: Feedback
>>     
>
>   
>> Looks like some great work guys! Any chance you'll be developing a 
>> Linux/Qualcomm version that will work on Acer Aspire One (model ZG8)? 
>> Currently have to boot first in XP to load Qualcomm firmware then 
>> restart in Ubuntu Linux 9.10.
>>
>> Thanks for any info!
>>
>> Jim M
>> Tulsa, OK USA
>>

---

### Post by amartz on 2010-01-07
> **jamere said:**
> I really shouldn't say it's MUCH easier. It's still hit-or-miss getting a connection and it usually takes a combination of the following TERMINAL commands and sacrifices to the "network" gods:
jim m

It's comments like this that keep me firmly anchored on 9.04 for now.  While the double-boot is inconvenient, I can always count on it working, at least if AT&T is doing it's part. I did take the plunge and upgrade my larger HP laptop (non-3g) to 9.10 (after backing it up), and that seems to have gone very well, so far.
Art

---

### Post by jamere on 2010-01-10
Note from Markus (developer at MWconn)...Hopefully their solution will somehow find it's way into the Ubuntu repositories in the near future...

Hi Jim,

> thanks, happy to her this!  :-) 

At present, there is only one thread in MWconn forum concerning the version for Ubuntu:
[http://www.mwconn.info/viewforum.php?f=14](http://www.mwconn.info/viewforum.php?f=14)

And - unfortunately - this thread is in German only. It's just a first call for alpha testers. 

MWconn is able to be run under Wine since some months, but this isn't a good solution. [COLOR="Blue"]The new version will work native with Ubuntu (Gnome/GTK). At these days I am programming the configuration user interface; till now the program can be configured by a text file only and this is not very comfortable.[/COLOR]

Nice Weekend!

Markus

---

### Post by jamere on 2010-01-13
shameless plug to keep issue alive!

---

### Post by Chiapo on 2010-01-14
I've been surfing via my Qualcomm 9212 with regularity, no Windoze necessary...

But it's still not as simple as should be.

Maybe Lucid Lynx will address this issue?

Happy New Year!

---

### Post by jamere on 2010-01-14
Hey Chiapo,

good to hear from you! Still trying to keep the issue alive here on this thread. Sure would like to know how the Ubuntu developer bureaucracy works or how to make sure an issue like this gets into the development mill. I keep looking for a fix to come through the Update Manager process...but not holding breath.

Still depending on Windoze boot (and left-clicking NW icon, connecting and disconnecting until NW finally 'connects')!:confused:

Did you see the emails from Markus at MWconn? Hopefully his programming work will find its way into the Ubuntu repositories in the near future! (again, not holding breath)

---

### Post by Chiapo on 2010-01-14
Here's what works for me, every time. (I have the gobi_loader installed in ~Desktop/gobi_loader/ directory.)

Cold boot into *buntu. (I'm using xubuntu 9.10 with the latest updates)

If exists Mobile Broadband Connection, go into Network Manager and delete the Mobile Broadband Connection.

Open Terminal.

Type ```
sudo stop network-manager
```

Wait a few seconds... Then type ```
sudo modprobe -r qcserial
```

Wait a few more seconds... then type ```
sudo modprobe qcserial
```

Wait a few more seconds... then invoke the gobi_loader. (since I installed it in the directory noted above, I type the following presuming I am currently in my home directory ```
Desktop/gobi_loader/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
```

I usually wait for a longer period before re-starting Network Manager ```
sudo start network-manager
```

Then I click on the Networking icon, select "New Mobile Broadband Connection," then selecting the pertinent options for my ISP, I setup a new connection. (at&t, USA, Data Connect)

Another click on the Network icon should show a Mobile Broadband Connection, so I click on that to establish the 3g connection.

The system should report a GSM Connection

To ensure the connection is working I usually ping some website by typing in terminal ```
ping ubuntuforums.org
```

If you start seeing IP addresses etc and the info keeps scrolling, the connection is good & you can stop the ping by pressing ```
ctrl + c
``` (lower case)

Followed by ```
ctrl + d
``` to exit the terminal window.

These steps always result in a 3g connection through the Qualcomm 9212 HS-USB 3G (WWAN) modem without booting into WinXP to load firmware.
:popcorn:

I've gathered the carrier specific firmware(at&t) from my WinXP installation by looking in the following directory:
C:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt

The Options.txt file should contain the path to the firmware used by your modem.

Get the gobi_loader here:
[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")

It's not as straightforward as it should be, but it does work!

Considering the price(FREE!) I think it's something I can live with for awhile. ;)

---

### Post by jamere on 2010-01-15
Chiapo,

Wow! Thanks for the detailed instructions! Can't wait to give it a try. Hopefully your instructions will help a lot of others with the same dilemma.:D

jim m

Note: quickly approaching 5000 views!

---

### Post by jamere on 2010-01-19
Chiapo,

Finally got around to trying your procedure (thanks again), but I'm not quite there yet. I go through the procedure and everything appears normal, but the system doesn't seem to re-build the Mobile Broadband section that normally appears at the end of NM-tool command. Left-clicking the NW icon doesn't show my new AT&T broadband acct info where I can connect or disconnect the broadband connection. The modprobe commands are working (I think) because the modem model changes from 9211 to 9212 and no errors of any kind. The 2 firmware files are in /lib/firmware/gobi. /dev/ttyUSB0 appears with todays date so that is being created ok. Did the make and install with no apparent problems.


Question:
Did you use 0.3 version of the gobi loader from Matthew Garret? (There were 3 versions available). I picked 0.3 to download thinking the latest would be best.
 
Any ideas?

I'll keep playing with this for a while. :) Maybe I can spot a problem. Maybe I'm not allowing enough time between commands?

---

### Post by Chiapo on 2010-01-20
Good question...

I used the 2nd of the 3 loaders available because my firmware was in the "2" directory, although I have no idea if it makes a difference.

Does lsusb show the Qualcomm as 9211, or 9212?

I also added the following to /etc/modprobe.d/blacklist.conf, but don't know if it helps.

blacklist acer_wmi

Have you tried restarting from Ubuntu back into Ubuntu as sometimes it results in an active connection for me. (set "Connect Automatically" in the Network Manager > Edit Connections dialog box, as well as "Available to All Users")

---

### Post by jamere on 2010-01-20
Chiapo,

I noted the '2' directory also, but didn't tie the 2 to the loader version number. Very astute on your part. I'll try 0.2 soon.

After 'power on' boot in 9.10 the model shows as 9211. After modprobes model is 9212. I think this shows the loader is working?

I'll also try your 'blacklist' mod. Hey, I'll try most anything at this point! :D

I did try booting back into Ubuntu one time and all I had to do was left-click on NW icon and choose AT&T Data Connect 1, and the NW started immediately, with no other action needed from me! I was stunned and just marked it up as a fluke happening as I wasn't very alert at the time (very early in morning).

I'll do more 'fiddling around' today and check back in soon. Thanks again for your input.

---

### Post by Chiapo on 2010-01-20
Hey Jim. Good to hear that you're connecting without Win*. :KS

I also notice that the device ID changes when sudo moprobe qcserial is invoked, my suggestion to invoke the loader directly may be hindering the connection process as I have had a working 3g connection by simply stopping & starting the network-manager.

I further note that if I attempt a connection too soon after boot, the connection fails.

Hopefully Lucid will be better at handling a wide variety of 3g modems.

Best of luck to you, & may the 3g GODs be with you!

---

### Post by jamere on 2010-01-21
Chiapo,

> I further note that if I attempt a connection too soon after boot, the connection fails.

I have a feeling I've been *rushing* the terminal commands in trying to get a connection. I have a Sticky Note with all the various NW commands on part of my screen and the Terminal window in another part of the screen and I simply cut and paste commands into the Terminal. As I'm a terrible typist (and lazy) this saves a lot of time doing repetitive commands, however, I may be feeding commands faster than the Network Mgr can digest them and possibly missing connections. Hope this makes sense as it's shear speculation on my part.

Hope to getting back to doing more *futzing* with 3G gods today!

---

### Post by Chiapo on 2010-01-21
Did you know that when in terminal you can access previously entered commands by pressing the Up Arrow key?

I use this method a lot because I too am a lazy typist.

---

### Post by jamere on 2010-01-21
Chiapo, I didn't know that! Guess that makes me lazy AND uninformed...bad combination. :D

---

### Post by Chiapo on 2010-01-21
So we make up for it by being persistent! :P

---

### Post by Chiapo on 2010-01-22
Tonight I just had trouble connecting, so I tried clcking the disconnect option from the network icon, wait awhile, then select the connect option from the samr icon.

Sometimes my connection will only connect to numerical address... DNS resolution error?

Well, maybe I should be trying this method more...

---

### Post by jamere on 2010-01-22
Chiapo,

Yeah, I think we're dealing with just too much inconsistency and too many variables. I just booted from Win, restarted in 9.10 and the network came up with no intervention on my part...networking was just 'there'! I would like to be able to boot independently of Win but not sure it's worth the effort with 10.4 just a few months away. Whether a fix  for this problem will be in the new version is anybody's guess. Don't know, but looks like developers are going to have to come up with something similar to the AT&T Communication Manager program (Acers) that allows for Wired, WIFI, and Broadband Wireless capabilities. I know Markus in Germany (MWconn?) is working on doing this. Maybe we should volunteer as alpha testers? :D

Anyway, I'm going to fiddle around with version 0.2 of the loader, but if I can't get it to work soon, I may wait on 10.4 hoping for a fix. Guess that makes me a sceptical optimist.:D

Note: after futzing with 0.2 of the loader, I'm now seeing more "security" type checks dealing with 'key ring' and password entry. Also seeing a wildly revolving NW icon that appears to be doing about 10,000 rpm's! :D :D :D

---

### Post by jamere on 2010-01-28
bump

---

### Post by Chiapo on 2010-01-29
Try going into Network Manager >> Mobile Broadband >> IPv4 then click on Method, selecting "Automatic (PPP) addresses only" ...

Then go down to the "DNS servers" text field & enter a DNS.
I chose OpenDNS, which has 2 free DNS servers that I'm familiar with.

208.67.220.220
208.67.222.222

Either one of them works for me. I haven't looked into the syntax for including both primary & secondary DNS records on the single line afforded in Network Manager yet, I guess I could fool around with that a bit today.

I also have stopped invoking the gobi_loader from the command line as it appears that qcserial is handling the firmware without my meddling.

Hope this helps.

---

### Post by jamere on 2010-01-30
chiapo,

Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1008200]("http://ubuntuforums.org/showthread.php?t=1008200")

26,000 + views!  amazing!

Looks like you're still fiddling around. I admire your perseverance. I'm throwing in the towel hoping for a fix in the next version. I may check with Markus in Germany and volunteer as a tester soon. :D :D  Would be nice to get away from the win-lin shuffle!

Will check in periodically for comments/solutions on this thread.

---

### Post by jamere on 2010-01-30
See Markus' web site here:

[http://www.mwconn.com/]("http://www.mwconn.com/")

Looks like good possibilities to me. Anyone tried this?

---

### Post by Chiapo on 2010-01-30
> **jamere said:**
> chiapo,

Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1008200](http://ubuntuforums.org/showthread.php?t=1008200)

26,000 + views!  amazing!

Looks like you're still fiddling around. I admire your perseverance. I'm throwing in the towel hoping for a fix in the next version. I may check with Markus in Germany and volunteer as a tester soon. :D :D  Would be nice to get away from the win-lin shuffle!

Will check in periodically for comments/solutions on this thread.


Hey Jim, Aloha from Hawai'i, & thanks for the link! I am also anxiously awaiting a fix for this modem issue. 
 
Yes, I have been reading the thread you mentioned, but have mostly stayed out of it due to the different PC brand, & the fact that they're also dealing with a GPS.

Sorry to hear that you're giving up, but I can understand. I'm afraid to show off my *buntu laptop unless I'm near a WiFi hotspot because I hate having to try explaining why this operating system I've been raving about is unable to connect via built in hardware without my rebooting a few times.

I haven't booted WinXP in over a month but I do have to jump through hoops to get the Qualcomm 9212 online using only xubuntu. Once it's connected I hate to shut the machine down! (not sure about the difference between suspend & hibernate, but the connection is dropped when I try either)

Good luck in your endeavors, & I'll see you here from time to time.

  
Chiapo.

---

### Post by jamere on 2010-01-30
Chiapo,

Hawaii??? Do folks really fiddle around with computers there? :D  Hope you're not sitting on the beach futzing with your laptop! ;) Here in Okie land, we're under 6" of snow and ice! I'm really envious!

Did you try "wicd" in place of network-manager? Wonder if anyone has tried it with the Qualcomm HS-USB-9212? Just curious but not curious enough to try it on my own.Saw it mentioned on another thread, but don't know anything about it.

Let us know if you have any break-throughs!

Later...jim m

---

### Post by Chiapo on 2010-02-02
Hello Jim.
Yes, we use computers here too, especially nerds such as myself! lol
I usually don't use my laptop at the beach as I don't want to get sand in it! lol

Believe it or not, we actually get snow on the mountains here from time to time.
I don't envy you regarding the seasons there, but there's an old saying that goes like this: "The secret to making a small fortune in Hawai'i? Bring a large one!"
Things are expensive here.

I made a breakthrough with the 3g modem this morning!

When I powered on the unit, it booted into xubuntu normally, but after awhile I noticed that Network Manager didn't see the modem. I was going to reboot, but realized that the modem had been manually switched off, as I was on WiFi yesterday, so I switched the unit on manually & VIOLA! GSM connection established!

This is the first time the Qualcomm 9212 connected without my going into terminal & stopping/starting Network Manager etc.

I think it's due in part to DNS resolution errors, which have vanished ever since I set the mode to Automatic (PPP) Addresses Only & entered the OpenDNS info on the IPv4 tab in Network Manager.

Network Manager >> Mobile Broadband >> AT&T Data Connect >> IPv4 >> Mode

I will test further, shutting the modem off manually prior to shutting the system down, then powering the Qualcomm on manually after the system is up & running for a minute or so.

As for wicd, I have had absolutely no success with it in any of the various linux distros I've tried.

Best wishes for you and your loved ones!

Chiapo.

---

### Post by Chiapo on 2010-02-02
It's working!!!

Switched the modem off manually, powered off, powered back on, booted into xubuntu, waited awhile, then switched the modem back on manually.

Three out of three successful connections!

Still, if you're in an area with poor signal strength, the modem will flip out & the networking icon does its wildly rapid spinning, & then I either have to shut down, or go to the command line & mess around sometimes requiring a reboot.

Let's hope this will work for you & others!

I'm almost ready to call it SOLVED!

:popcorn:

---

### Post by jamere on 2010-02-02
Chiapo,

Got a reply from a developer concerning the gobi loader. Looks like the fix has been made in the kernel 2.6.32, if I understand correctly. Hope it's the same problem we've been dealing with! 
Have a look at the link below and see what you think.

Re: HP un2400 Mobile Broadband Module
Quote:
Originally Posted by jamere View Post

MJG59...have any idea where this problem stands in the development community?


It's a kernel bug. [http://bugzilla.kernel.org/show_bug.cgi?id=15134]("http://bugzilla.kernel.org/show_bug.cgi?id=15134")

---

### Post by jamere on 2010-02-02
Chiapo,

3 for 3, I'd say you have the problem whipped...congrats!:popcorn:

I got the gobi-loader working (ver 0.3) but was never able to make an independent connection. Never could get ver 0.2 to work at all. Probably due to my own ineptness in getting around in terminal mode. Weak signal may play a part also in that I usually only get 2 out of 5 bars signal strength.

Hope kernel 2.6.32 comes out soon! :D

---

### Post by Chiapo on 2010-02-03
So far, so good! 

Ditto on the .32 kernel fix. 

Re signal strength, yes it does make a difference, as when I'm in an area with weak signal the signal will change from 3g, to EDGE, to GPRS without seamless fallback, as advertised by at&t. When the signal type changes, the connection is lost, & the icon starts spinning like crazy.

I have installed every update, and Update Manager says the system is up to date, so this most likely is the reasin for my recent success.

Cheers!

---

### Post by Chiapo on 2010-02-03
It Works!!!

As long as I remember to switch the modem off manually before suspend/hibernate/shut-down, the connection is established after the system is up & running & the modem is subsequently switched on manually!

:KS:KS:KS:KS:KS

---

### Post by jamere on 2010-02-10
bump for view count

---

### Post by jamere on 2010-02-16
Thought I'd check back in to see if Chiapo or anyone else has tried one of the newer kernels (and is up-to-date in Update Mgr)to see if this problem has been fixed yet in 9.10? I have kernels 2.6.17 and 2.6.19 installed but don't have the nerve to do a grub-update for fear of screwing up bootablility to XP. ;)

Any news on this problem? Just curious.

thx
jm

---

### Post by jamere on 2010-02-16
Found this FWIW. This may be the culprit causing our problem but don't know for sure:

> Regressions with patches
Patch		: [http://patchwork.kernel.org/patch/75560/](http://patchwork.kernel.org/patch/75560/)


Bug-Entry	: [http://bugzilla.kernel.org/show-bug.cgi?id=15134](http://bugzilla.kernel.org/show-bug.cgi?id=15134)
Subject		: gobi-loader hangs after commit 8e8dce065088
Submitter	: Matthew Garrett <mjg59@srcf.ucam.org>
Date		: 2010-01-17 2:55 (15 days old)
References	: [http://marc.info/?l=linux-kernel&m=126369696509502&w=4](http://marc.info/?l=linux-kernel&m=126369696509502&w=4)
Handled-By	: Oliver Neukum <oliver@neukum.org>
		  Alan Cox <alan@lxorguk.ukuu.org.uk>
Patch		: [http://patchwork.kernel.org/patch/73878/](http://patchwork.kernel.org/patch/73878/)

---

### Post by Chiapo on 2010-02-19
I'm using kernel 2.6.31.19-generic

System is up to date from Update Manager.

100% connect via Qualcomm 9212 every time I manually switch the modem on after boot.

:popcorn::popcorn::popcorn:

---

### Post by jamere on 2010-02-20
Chiapo...you're gloating again! ;)

Assuming you're still using the gobi loader thing? I'm up-to-date on Update Mgr also, but not on newest kernel. So far, I don't have the cahones to do a "sudo update-grub" for fear of losing XP connectivity in the event Grub gets confused with all the stuff I have on my hard drive. I don't know diddly-squat about Grub. I may try grabbing a beta version of 10.4 when it comes out, to see if this problem has been fixed.

---

### Post by jamere on 2010-02-24
Found the following over in the HP thread...not a good omen for being fixed in new release: :confused:

>  Re: HP un2400 Mobile Broadband Module
I am getting same problem with 10.04 alpha 2. Takes forever to load the firmware then never dials the connection. I am fairly confient I've set it up properly as it was on 9.10.


Can anyone confirm or deny this problem being fixed in 10.4?

---

### Post by jamere on 2010-02-28
bump

---

### Post by Chiapo on 2010-03-02
Hey Jim...

I just did a clean re-install of xubuntu 9.10, kernel 2.6.31-19-generic, installed gobi_loader (the new v4) and have been surfing via the Qualcomm 9212 with no issues other than signal strength.

I have setup the connection as reported previously, being sure to use two or more identical mobile broadband connection profiles in network-manager.

I have done numerous installations of various linux distros, even shrinking my WinXP partition, and have had no problems with accessing the WinXP installation.

Maybe if I get some frree time this weekend I'll try putting together a concise explanation of the steps I took to get this modem working.

I understand your reluctance to mess with your system.

---

### Post by jamere on 2010-03-06
Hey Chiapo,

> Maybe if I get some frree time this weekend I'll try putting together a concise explanation of the steps I took to get this modem working.

That would be great and thanks! Finally worked up the courage to diddle with my Grub boot menu which was kludged with old entries and wasn't recognizing newest kernels. To make a long story short and rather than mess with Grub internals, I just re-installed 9.10 from USB stick. Now I have the newest kernel versions and more importantly Win XP still works. Definitely held my breath for a while during re-install! :D  Haven't been able to work up enthusiasm for messing with gobi-loader again, but it sounds like there's a new version.

Have you checked into [www.MWconn.com](www.MWconn.com)? Looks like they have a linux version of their network mgr program. Appears to be similar in function to the AT&T Communication Mgr in Windoze. Still in alpha or beta stage and the site and forum are mostly in German. Still might be a good alternative (free) in the event Ubuntu developers don't come up with a solution in a reasonable time frame. Sure hope you can come up with something that's a good alternative as I haven't seen anything that leads me to believe that the problem will be fixed in 10.4.

Later...

---

### Post by jamere on 2010-03-09
bump

---

### Post by jamere on 2010-03-12
Has anyone installed 10.04 beta to see if this problem has been fixed? Cautiously optimistic.

---

### Post by Chiapo on 2010-03-16
I haven't tried any new OS' since I got my modem working in xubuntu 9.10, & don't advise trying a beta release unless you have the wherewithal to expend resources on testing.
I'll wait for the official release because of past experience with alpha/beta releases (wasted my time & bandwidth downloading,)  it won't be much longer to wait. 

I haven't needed to do any further kludging to get this modem working beyond the install of gobi_loader & the firmware, plus a small bash script to reset the modem & drivers when the connection is dropped.

_[SIZE=2]***Before***[/SIZE]_ invoking this script you need to*** _turn the modem off manually_*** via the slider switch on the front right edge of the laptop, just below the wireless indicator lights.
```

#!/bin/bash
gksudo -S stop network-manager | zenity --info --title="Resetting 3g modem" --text="Please wait while modem is reset..." --timeout 1
sudo modprobe -r qcserial | zenity --info --title="Resetting 3g modem" --text="Please wait while modem is reset..." --timeout 2
sudo modprobe qcserial
sudo start network-manager | zenity --info --text="Please turn on 3g modem." --title="Please turn on 3g modem." --timeout 3

```This script assumes you have the Mobile Broadband connection set to "Connect Automatically," & "Available to all users," and gobi_loader installed as previously mentioned, along with the pertinent firmware from your WinXP installation.
If your network-manager is disabled, qcserial is unavailable, etc, the script will malfunction.
(so far nothing serious has happened to me)

Save the script in your /home/***username*** directory (name it whatever you want), then open a terminal & make the script executable:
```

chmod u+x ***scriptname***

```
Invoke the script:
```

./***scriptname***

```
I use it when the signal strength/type changes & the connection is lost... I also associated a "Launcher" icon with the script, placing the icon on my side panel to make it easier to use.

The zenity part is a new addition, & needs improvement, but it works for me.

_***If you use this script, you do so at[COLOR=Red] your own peril[/COLOR]***_, so I suggest that you not use the script unless you understand what each line does.

Here's the script without the zenity additions.

```

!#/bin/bash
sudo stop network-manager
sudo modprobe -r qcserial
sleep 3
sudo modprobe qcserial
sleep 2
sudo start network-manager

``` Be sure to remember to turn the modem back on when the script is finished.
If your settings are on auto, the modem should connect on its own after a short time.
I hope this helps.

---

### Post by Chiapo on 2010-03-16
I tried ixconn (MWconn) but got nowhere.

It looks like a good app, but it didn't have settings for at&t laptop connect, & I didn't feel like fooling with it.

In any event, my Qualcomm 9212 is working like a charm without it!

---

### Post by Chiapo on 2010-03-16
ixconn not only borked my 3g connection, but it also borked my VPN setup, & Exaile.

Got the 3g connection working again right away, but it took more fooling to get Exaile back, & I still don't have my VPN working... Even after completely removing OpenVPN & re-installing twice.

Contemplating yet another complete, clean install of xubuntu 9.10 to rectify the situation.

---

### Post by jamere on 2010-03-17
chiapo,

Looks like you've been hard at work with a workable alternative. I had about the same luck with MWconn. I noticed they didn't have a 'AT&T data connect' plan set up and didn't feel motivated to try communicating with them (German) to add that option. AFAIK trying their program didn't hose anything system-wise for me, thank goodness.

I'm also inclined to wait for 10.04 and don't really want to mess with a beta version the more I think about it. I'm hoping the infamous 'kernel' bug (15134) patch fixes the problem. I think its supposed to be in the 2.6.32-10.14 (10.04) kernel, but who knows? I'll explore the gobi-loader thing again and your improvements if this issue isn't fixed in 10.04. Thanks for documenting your efforts in your "work around". Just wondering what everyone else is doing concerning this problem? Probably a lot of AAO folks have gone back to Windoze. yech!

Edit: Well, knowing myself like I do, I won't be able to resist getting into that danged gobi-loader thing again. Already gathering notes and references concerning how to do it...again. Guess it's a compulsion kind of thing! :-D

---

### Post by jamere on 2010-03-18
Chiapo,

Good news to report! Started fiddling with gobi loader (0.4) again with good results this time! Have been able to boot independently of Windoze several times. :popcorn:

Here's what I'm doing that seems to work:

- cold (power-up) boot into Ubuntu
- modprobe -r qcserial
- modprobe qcserial
- load gobi firmware
- "restart" ubuntu without powering off
- Network starts with no other intervention on my part

I don't know how consistent this procedure will prove to be since I've only done it a couple of times, but its pretty easy with no futzing around with other NW commands.
I attribute the apparent success to being on newest kernel (2.6.31-20 9.10 Karmic) and up-to-date in Update Mgr. Will report back after trying the above a few more times to see if it works consistently. If inconsistent, I may try your scripting stuff. 

Thanks for checking in and sharing your info!

---

### Post by Chiapo on 2010-03-18
Congratulations Jim!

Cheers!
:popcorn:

---

### Post by jamere on 2010-03-18
OK Chiapo,

here's one for you that I can't explain. Just did a power on boot into Ubuntu and after logging in and entering password, the NW started with NO INTERVENTION on my part! No modprobes or firmware loading on my part...What gives? I thought firmware was lost on power off. I'm not complaining mind you, but what the heck happened? Somehow the firmware got reloaded automatically or was somehow restored on booting up. Maybe the network gods are finally taking control of the situation and putting a good hex on the gobi loader and NW Mgr! :D

---

### Post by jamere on 2010-03-18
Well, I've booted into Ubuntu 6 times, as described in post #146 above and the network started each time with no problems. Still not ideal, but seems to be reliable and consistent with minimal hassle.

One of the 6 boots happened as described in previous post which I can't explain.:D

---

### Post by Chiapo on 2010-03-18
Cheers Jim! 
I also have noticed that the 3g connection is sometimes made without my intervention.
Apparently the new kernel is handling things better!?

I'm using 2.6.31-20-generic & it seems to be working better with my 3g modem.

I also have updated my modem reset script a little.
The script will hopefully be obsolete soon. (maybe already)

Good to hear that you've made such progress!

Maybe we were the only two AA1 users who had this issue? (lol)

---

### Post by jamere on 2010-03-19
Chiapo

> I also have noticed that the 3g connection is sometimes made without my intervention. I think there's some higher force at work! ;)

> Good to hear that you've made such progress! Thanks much! I guess our persistence eventually paid off. At least we didn't have to revert to Windoze!


> Maybe we were the only two AA1 users who had this issue? (lol) 
Could be true, but last I saw this thread was approaching 9000 views, so there must be 'some' interest or maybe they just like the banter! :D

Seriously, one thing I've noticed is that you've been messing with the 3G switch which I haven't done at all. Think this is a difference in models?

Question: do you know if a 'restart' can be done in a script?

Later...eagerly awaiting 10.04! :D

---

### Post by jamere on 2010-03-20
Re: post #148 above.

After giving a little thought to what happened, the gobi firmware must be remaining "energized" under certain conditions even with the power switch off. That's probably why we see the network connection "miraculously" coming up periodically with no intervention on our part. Also probably why our connection results are so danged inconsistent and erratic! Any EE folks out there who can explain this phenomenon? :confused:
After a power off, how can the firmware remain in tact? hmmm

---

### Post by Chiapo on 2010-03-23
> Seriously, one thing I've noticed is that you've been messing with the 3G switch which I haven't done at all. Think this is a difference in models?

Not sure about switch differences. Does the script work if you leave the modem switched on? (I haven't tried)


> Question: do you know if a 'restart' can be done in a script?

I'm fairly sure you could restart the system in a script, but I haven't tried.

I notice that if the modem is switched on at shut-down, the subsequent start-up will have 3g connectivity problems. Thus I usually try to remember to switch the modem off prior to shut-down.

I believe the firmware is handled automatically by qcserial via the gobi_loader.
If you watch System Monitor while switching the modem on, you can see gobi_loader come up. 


What kind of speeds are you getting?

I'm in a fringe area for at&t data coverage & I get anywhere from 0.2KB/s to 200KB/s download speeds, but in town I get from 300KB/s to 1,400KB/s. 

Kb/s = Kilobits per second.
KB/s = KiloBytes per second.
8 bits = 1 Byte.

I get frustrated when I only get 1KB/s sometimes, & other times I get 200KB+ in the exact same location!

It's been really bad here since last Christmas... So much that I'm considering leaving at&t if I can find a provider who serves my area with better data coverage.
Clear has WiMax on O'ahu & Maui, but they're not here on the Big Island yet.
:p
Funny how last year I would have been happy just to have 3g connectivity, but now it's not good enough!

My greedy materialistic nature, I guess.
lol

Cheers Jim!

---

### Post by jamere on 2010-03-23
Aloha Chiapo,

> Not sure about switch differences. Does the script work if you leave the modem switched on? (I haven't tried)

I run the script which usually doesn't make a connection, but I immediately do a 'restart' (without powering off), login again and the connection is almost always made. The only hassle factor is having to login twice. I'll try the 3G switch trick today to see if that helps connect in the script. Running the script definitely does 'something' that allows the connection to be made on the immediate restart. There's another variable that I'm introducing here also. I made my own variation of a script I saw on the HP 2400 thread. Here's what I'm running (note that I've commented some commands out):

```
#!/bin/sh
#Script to initialize Qualcomm HS-USB-9212 Modem

#sudo stop network-manager
#echo network manager stopped
#sudo killall modem-manager
#echo modem manager killed
#

echo Initialize Qualcomm HS-USB-9212 Modem...

echo Stopping network-manager now...
sudo stop network-manager
echo Sleep 10s ...
sleep 10

echo Modprobe remove qcserial module from kernel...
sudo modprobe -r qcserial
echo Sleep 10s ...
sleep 10

echo Modprobe restore qcserial to kernel...
sudo modprobe qcserial
echo Sleep 10s ...
sleep 10

echo Loading firmware to Qualcomm modem...
Desktop/gobi_loader/gobi_loader-0.4/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
echo Firmware loaded
echo Sleep 20s after loading firmware...
sleep 20

#echo Stopping network-manager now...
#sudo stop network-manager
#echo Sleep 10s ...
#sleep 10

echo Starting network-manager now...
sudo start network-manager
echo Sleep 20s ...
sleep 20

echo Hopefully broadband connection was made...
echo If no connection, Restarting Ubuntu will initialize Broadband connection
sleep 5
```

> What kind of speeds are you getting?
I don't know, but I've notice drastic speed changes when downloading ISO's. Like you, I'm just happy for a connection!

How are you checking line speeds?

I sure don't feel like I'm married to AT&T either and may switch depending on what cellphone they offer or don't offer in another year (when present phone agreement expires)! Heck of a reason to switch...huh? :D I've been keeping up-to-date on the new phones being offered by various providers and there are some really nice phones coming out! I have an HTC Touch Pro that I really like, but its Win Mobile. Like anything Windoze, it has to be soft booted on a fairly regular basis!:D Looking very closely at anything Android, new touch screen technology, and snap dragon processor.

Have a good one and I'll let you know how the 3G switch turn off routine works for me.

Thanks again for the info and suggestions...I'm learning more than ever intended!

---

### Post by jamere on 2010-03-24
Chiapo,

Re: 3G switch setting. So far not seeing a relationship with switch setting and NW connection. You're obviously onto something with the switch off/on thing, but doesn't work for me.

FYI...looks like a new kernel is on the way soon...2.6.31-21 :D

---

### Post by Chiapo on 2010-03-29
Hello Jim. I've noticed that if I manually switch the modem off prior to shut down, the subsequent power on & boot + loading xubuntu followed by manually switching the modem on results in a successful 3g connection with no further fiddling required. -------------------------------- Since the new kernel, I believe gobi_loader is handled by qcserial & thus needs no direct call from your script, as the sudo modprobe qcserial command automatically does this. ------------------------------------------------------------------------------------------------------- To check my mobile speeds I go to [http://www.dslreports.com/mspeed](http://www.dslreports.com/mspeed) -------- If you have Firefox with the WML Browser add-on you can view the WML pages rather than download them. -------------------------------------------------------------------------------------------------------------------------------------- I have been greatly disappointed with at&t lately, especially since last Christmas when it appeared that everyone in my area got an iPhone for Christmas. 3g speeds have been dismally slow since then, & I see no improvement in the near future as at&t will not be rolling out LTE in my area until late this year/early next year. ---------------------------------------------------------------------------------------------- The other disappointing bit of errata from at&t is their dearth of Android devices AND the fact that at&t plans on locking down the OS on all of their Android offerings. This means that unsigned 3rd party apps will be unavailable on locked down handsets, thus requiring some hacking to gain the the full functionality of the device. ---------- I cannot justify the expense of an unsubsidized phone right now, so am considering either getting an iPhone, or going back to T-Mobile so I can get the Nexus 1 (subsidized.) ---------------------------------------------------------------------- Good luck Jim, may the 3g GODs be with you!

---

### Post by jamere on 2010-03-31
Aloha Chiapo,

> The other disappointing bit of errata from at&t is their dearth of Android devices AND the fact that at&t plans on locking down the OS on all of their Android offerings. This means that unsigned 3rd party apps will be unavailable on locked down handsets, thus requiring some hacking to gain the the full functionality of the device.

[COLOR="Blue"]FYI, you might check into this site:[/COLOR] 
[http://www.xda-developers.com/]("http://www.xda-developers.com/")

If you haven't seen this site, it's a large group of developers that have specialized in app development exclusively for HTC Win Mobile phones. They are now getting into development for Android apps. I've used quite a few apps from them on my phone and there are some great ones.  These folks know what they're doing phone-wise. Saw where some developer was able to run three operating systems on his HTC HD2 phone! I think Win Mobile, Android and Symbian. They also do ROM cooking  if you're into that sort of thing. The reason I suggested this site is the fact that they're getting into Android development. These guys can do 'anything' with phones and apps are free (donations accepted). Just my 2 cents worth.

> Since the new kernel, I believe gobi_loader is handled by qcserial & thus needs no direct call from your script, as the sudo modprobe qcserial command automatically does this

You're right about this. I removed the loader reference in my script and it works just as well without it. Still a bit of a hassle "re-starting', but is consistent in making the NW connection. I'm a happy camper for not having to deal with Windoze!:D

Thanks again for your timely and informative info!

---

### Post by jamere on 2010-04-24
> Qualcomm HS-USB-9212 in Acer Aspire One--No connection

Anyone know if this problem has been fixed in 10.04? I saw an email today from a Ubuntu "bug" thread that indicated that this problem has not been fixed. [COLOR="Red"]Not a good omen.[/COLOR] :confused:

---

### Post by JeZ-l-Lee on 2010-04-25
> **jamere said:**
> Anyone know if this problem has been fixed in 10.04? I saw an email today from a Ubuntu "bug" thread that indicated that this problem has not been fixed. [COLOR=Red]Not a good omen.[/COLOR] :confused:

Hi,

I tried Ubuntu 10.04 Release Candidate and the Qualcomm 9212 3G modem is NOT working.  It is listed as a bug on the Ubuntu bug tracker web site but it does not seem to be a high priority.  On Ubuntu 9.10, I was able to get the Qualcomm 9212 3G modem working by using "Gobi Loader" to load modem's firmware but this solution is not working on Ubuntu 10.04.   Hope they can fix this soon or I will be forced to use the older 9.10 Ubuntu on my netbook.

Jesse

---

### Post by jamere on 2010-04-25
Hi Jesse,

Thanks for posting here. I'm subscribed to the bug tracker site (Bug 303665-AAO 3G not detected) and saw your post. A lot of us AAO users will be disappointed to learn that this problem hasn't been fixed in the new 10.04 version. I suppose there's still a glimmer of hope that this bug will be fixed in the final release, but it's doubtful, judging from the overwhelming number of network problems of all types reported on the "networking" forum. There have been over 10K views of this thread which tells me there's a lot of interest in this problem from AAO (Qualcomm modem) users trying to connect. I think a growing class of netbook users are being overlooked by the developers, hence the low priority of Bug 303665. I guess 10K+ views doesn't warrant attention from developers. :)

A lot of us seem to have come up with "work arounds" to get connected on 9.10. I've been able to cobble together a ritualistic process to connect mobile broadband, with suggestions from Chiapo and others. I basically boot to 9.10, run a script that loads the firmware and then I do a restart. This process, worked (almost without fail), to make a connection. As of late the connections haven't been as reliable, so I  made another script to stop and start Network Manager that I run in conjunction with the firmware loader script. I now have to run the second script as many as 6 times to get a connection. I know Chiapo has to fiddle with his 3G switch to get a connection, but so far, I haven't had to do that. My work around is kind of a hassle because I have to log in twice and enter password twice, as well as, password for first use of the scripts. So far this ritual works for me.

Jesse, what model netbook do you have and how are you making connection in 9.10? What did you try in 10.04?

Thanks for any info you can provide us. I guess the Qualcomm modem saga continues...geez. :(

Edit to add the following:

As a side oddity, when I powered on to reply to Jesse's post I noticed that the firmware was still loaded and broadband connection info was still there (left click on icon). 'lsusb' command showed 9212, not 9211.This has happened twice now. How does firmware stay energised after power off under certain conditions? Anyone?

---

### Post by JeZ-l-Lee on 2010-04-25
> **jamere said:**
> Jesse, what model netbook do you have and how are you making connection in 9.10? What did you try in 10.04?

Hi,

I have a Verizon Wireless Gateway LT2016U NetBook.

On Ubuntu 9.10, I did the following to get Qualcomm 9212 3G modem working:
```
Desktop/NetBookModem3g/gobi_loader /dev/ttyUSB0 Desktop/NetBookModem3g/firmware
sudo kill $(pgrep modem)
sudo /usr/sbin/modem-manager
```The above works 100% of the time on Ubuntu 9.10 to initialize the 3g modem (no reboot required).
But, when I try the above on Ubuntu 10.04 RC, Gobi Loader hangs (runs without ending).

So, we must now wait for either Ubuntu staff or Gobi Loader programmer (or both) to provide an update.
Until then I will be using Ubuntu 9.10 on my netbook...


Jesse

---

### Post by jamere on 2010-04-25
Hi Jesse,

Thanks for the info.

```
Desktop/NetBookModem3g/gobi_loader /dev/ttyUSB0 Desktop/NetBookModem3g/firmware
sudo kill $(pgrep modem)
sudo /usr/sbin/modem-manager
```

According to Chiapo, the gobi firmware is now being loaded by module 'qcserial'. I took the firmware loader statement out of my script and it worked fine. Maybe you could remove your first statement above and try again under 10.04 to see what it does?

Questions: 
does the first sudo above kill pgrep and modem processes?
does the second sudo start modem-manager?

I may give your two sudo statements a try in my script, but would kind of like to know what they're doing first. ;-)

I know just enough about this stuff to be dangerous so take my suggestions with a grain of salt.

Thanks again for the info and let us know how you come out fiddling with 10.04.

---

### Post by JeZ-l-Lee on 2010-04-25
[FONT=Verdana]Hi,

I gave up earlier and reinstalled Linux Mint 8 so I would have access to the 3g modem in the netbook.[/FONT] [FONT=Verdana]
(reinstall took about 3 hours)

So your Qualcomm 9212 3g modem works ok on Ubuntu 10.04 Release Candidate?[/FONT] [FONT=Verdana]
Can you provide a URL link to proper instructions on how I would set this up on Ubuntu 10.04?

-------------------------------------------------------------------------------------------------------------------
[/FONT] [FONT=Verdana]sudo kill $(pgrep modem)
- Stops modem manager

sudo /usr/sbin/modem-manager
- Starts modem manager
-------------------------------------------------------------------------------------------------------------------
[/FONT] [FONT=monospace][FONT=Verdana]
Kind of don't want to spend time reinstalling an OS to my netbook.
Maybe with proper instructions I will try again on Thursday when 10.04 goes Final...

Thanks!


Jesse
[/FONT]       
[/FONT]

---

### Post by jamere on 2010-04-26
Hi,

> So your Qualcomm 9212 3g modem works ok on Ubuntu 10.04 Release Candidate?
Can you provide a URL link to proper instructions on how I would set this up on Ubuntu 10.04?

No, I haven't installed 10.04. I was waiting for final release of 10.04 when I saw your post that the Qualcomm 9212 3g modem problem still exists with 10.04 RC. Big disappointment, as I was hoping for a fix in 10.04. 

> Kind of don't want to spend time reinstalling an OS to my netbook.
Maybe with proper instructions I will try again on Thursday when 10.04 goes Final...

I understand... let us know here how you come out with 10.04 final. Don't think I'll get my hopes up for a fix in 10.04. :(

Thanks again for your info and perseverance.

---

### Post by Chiapo on 2010-05-01
Hmmm... I assumed a fix was imminent.

I haven't got around to downloading the lucid ISO yet, as everything is working smoothly in karmic.

I've been getting 100% success connecting when I make sure the modem is powered off prior to shut-down & I wait until after the OS loads to manually switch the modem on. 
No need for a reboot, no need to run the reset script.

One thing I've made sure of is having 2 or 3 identical mobile broadband connections in Network Manager, & have the IPv4 settings set to PPP (Addresses only) For DNS I've been using OpenDNS primary & secondary, separated by a comma.
```
208.67.220.220, 208.67.222.222
```

I might try an in place upgrade to lucid on my test partition, but might have to wait until I get back into town. (slow 3g at my cabin up in the mountains)

---

### Post by jamere on 2010-05-02
Chiapo,

> Hmmm... I assumed a fix was imminent.

Yeah, so did I (but I really knew better). :)

> I haven't got around to downloading the lucid ISO yet, as everything is working smoothly in karmic.

Looking forward to see how you do with Karmic. May try messing with it myself before long, but don't want mess up what I have with Karmic. I can at least log on with out too much hassle. Still can't see a relationship with 3G switch flipping on my AAO.

Considering my hassles with GRUB2 (doesn't recognize new kernel and won't remove old kernels from boot menu) and this Qualcomm modem problem, Windoze is becoming an alternative again, although a BAD one. Thinking about calling my old buddy Mark Shuttleworth to let him know about these problems! Developers seem to be ignoring these two critical issues. 

Chiapo, have you considered tossing your netbook and smart phone and just enjoying your surroundings there in Hawaii? :lolflag:

---

### Post by Chiapo on 2010-05-04
I just finished installing xubuntu 10.04 Lucid Lynx on my netbook. Now I have 3 xubuntu partitions.

3g connection is automatic, with subsequent signal events resulting in a momentary loss of connection, followed by reacquisition of 3g connection without any user input.

:popcorn:

[IMG]http://moco-sux.net63.net/palm-sig.jpg[/IMG]

I like being connected too much to get rid of my electronics!

So far, I'm happy with Lucid Lynx! Great job Dev Crew!

Aloha Jim, best wishes to you & yours!

---

### Post by Chiapo on 2010-05-04
A cold boot into Lucid resulted in zero 3g connectivity.
Restarted to my test partition(karmic) & was unable to revive the modem.
Cold bootedinto my primary xubuntu installation & 3g connection was automatic.
Restarted into Lucid & 3g connected automatically.

It appears we may need to install the gobi_loader with appropriate firmware, but I'll need to inquire further as to the absence or presence of gobi_loader.

---

### Post by klab233 on 2010-05-07
hey all, i am VERY new to the world of ubuntu, and have to say with the exception of a few little frustrations, i have really liked it.  One problem that i have been having was with my dell 1557 studio (thats for another day), but i to have been having to problem with my 3g modem.  I am running ubuntu 10.04 with every update possible (I think).  I have noticed that when i boot into windows XP and connect, then reboot into ubuntu i can connect until i reboot again of close the lid on my laptop.  any way, just wanted to introduce myself.  I will be keeping an eye on the forum to see what everyone comes up with, and if by some stroke of miracle i come across something i will throw it up in a hurry..... ):P

---

### Post by jamere on 2010-05-08
Chiapo,

Did you REALLY have to attach photo of palm tree? geez...location envy continues. ):P

klab233: Welcome aboard...now you can share in our frustrations with Qualcomm modem saga. ;)



> A cold boot into Lucid resulted in zero 3g connectivity.
Restarted to my test partition(karmic) & was unable to revive the modem.

Chiapo you really had my hopes up there for a second. Did you do a "lsusb" to see if the modem model number changed from 9211 to 9212? I think the loader worked (firmware loaded) if the model changed to 9212. I down loaded the 10.04 Desktop ISO but haven't done anything with it yet. Do you know what the kernel number is for Xubuntu 10.04? Wonder if the same kernel is used in 10.04 Desktop?

Dang...looks like modem problems continue.:confused:

---

### Post by jamere on 2010-05-12
Well, finally downloaded and installed 10.04 Lucid Desktop on my AAO netbook. Install went well and 10.04 looks nice, but sorry to say, the Qualcomm problem is still with us (me). 10.04 Network Mgr was dead as a door nail. Had to go back to 9.10 (kernel 2.6.31-21), get network started, then restart in 10.04 (kernel 2.6.32-10). The network came up immediately in 10.04 on the restart. It appears that qcserial is not loading the gobi firmware. My script to load the firmware now gets an error saying that "qcserial is in use", so the firmware doesn't load. Looks like more screwing around with scripts again to get firmware to load. It's a real disappointment that this problem wasn't fixed in 10.04. :confused:

Gotta be positive though...10.04 does look great from what I've seen so far! More tech "entertainment" in the offing, I'm afraid.:)

---

### Post by jamere on 2010-05-14
Well, still having to jumpstart off of Karmic 9.10 to load firmware to enable Lucid 10.04 mobile broadband (and Qualcomm modem) to come alive. Anyone seeing a solution to this situation (other than going back to Windoz)? :confused:

Chiapo, how are you dealing with this situation?

---

### Post by amartz on 2010-05-19
Well, I finally got one place I wanted to be. I burned a live CD with 10.4, and booted my Acer Aspire One from a usb dvd drive. I checked the network manager, and wifi but no mobile broadband. I then rebooted to WinXP, and then rebooted back to the live 10.4 CD, and the Qualcomm modem showed up and connected just fine, once I supplied the required setup info. Once I knew 10.4 could deal with 3g, once the modem was alive, I then upgraded my 9.04 to 9.10, and then upgraded the 9.10 to 10.4. While I still have to boot WinXP first long enough to load the modem's software, it's no worse than how I'd been doing it with 9.04, and at least I'm up-to-date, and didn't have to mess with setting up the modem-manager, or anything like that. Now I guess I need to go back and look at that gobi-loader utility.

---

### Post by rssnow on 2010-05-30
> **Chiapo said:**
> Hello jamere!

We are united in our quest!

Good to hear you were able to connect!

This link might be of interest to you:

[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")

Have you tried kuki? 
More info here:
[http://kuki.me/](http://kuki.me/)
I have been unsuccessful thus far, but have your sentiment regarding keeping the Windows partitions until a 3g connection is not an issue in ubuntu. (xubuntu)

I'll be checking in here more often now that I have a kindred spirit who is seeking that elusive 3g connection through the Qualcomm 9212 modem.
i have the acer aspi 					Beans: 15
re one with the qualcomm 9211/9212 3g modem as well.

*I can't get the gobi l*oader to work, but if I boot into windows 7, and let the ATT Communications manager initialize the modem, then restart into ubuntu lucid i can get a connection.  i am on it now.

---

### Post by amartz on 2010-06-01
> **rssnow said:**
> i have the acer aspi 					Beans: 15
re one with the qualcomm 9211/9212 3g modem as well.

*I can't get the gobi l*oader to work, but if I boot into windows 7, and let the ATT Communications manager initialize the modem, then restart into ubuntu lucid i can get a connection.  i am on it now.

Which version of Ubuntu are you on?  10.4?
Art

---

### Post by Chiapo on 2010-07-12
There's mention of adding an acer-wmi entry to the blacklists, somewhere in these threads.

I also run more than one Mobile Broadband connection in Network Manager.

I no longer need to use the modem reset script in XUBUNTU 10.04, kernel 2.6.32-21-generic .

Nor am I using OpenDNS.

XUBUNTU 10.04 is working well with my ZG5.

I no longer have WinXP on my HDD, but do run my licensed copy in VirtualBox from time to time...

I have not tried the other *buntu versions, other than xubuntu, because xubuntu just works with my netbook.

[IMG]http://moco-sux.net63.net/palm-sig.jpg[/IMG]

---

### Post by jamere on 2010-07-12
Aloha Chiapo! Good to hear from you.

> There's mention of adding an acer-wmi entry to the blacklists, somewhere in these threads.

Not sure of the significance of this?

Since this problem hasn't been fixed by now, I have my doubts that it will ever be officially fixed. It's a real bummer IMO. I'll never knowingly buy another product with a Qualcomm component in it.

Looks like you have it made with Xubuntu 10.04.  I'm back to booting XP first, to load firmware and then into Ubuntu 10,04 (2.6.32-23), Always brings up a reliable connection and is "the path of least resistance" for me. AT&T network service and reliability getting more and more questionable also. 

I would also like to dump Windoze but still wouldn't dare at this point.

Like your pic! :D

---

### Post by Chiapo on 2010-07-17
My current xubuntu setup works because I added the "gobi-loader" prior to the "UPGRADE" which made the new version work with existing hardware.

.
.
.
In other words, I did an "Upgrade' 'In PLACE'...`````````


Thus the "gobi_loader" is carried over to the next iteration...

---

### Post by amartz on 2010-07-18
> **Chiapo said:**
> My current xubuntu setup works because I added the "gobi-loader" prior to the "UPGRADE" which made the new version work with existing hardware.

Any chance you would want to summarize how you got and setup the gobi-loader?
Art

---

### Post by Chiapo on 2010-08-02
Well amartz, since I have already chronicled my myriad attempts at getting this modem working, & all the pertinent information is listed within this thread or the one I started, I must respectfully ask that you read through the relevant threads.

I took the time to relate what I did, can't you take the time to read?

On a final note, maybe the next release will see a solution out of the box?

---

### Post by amartz on 2010-08-02
> **Chiapo said:**
> 
I took the time to relate what I did, can't you take the time to read?

Chill, Chiapo. You've done enough? That's fine!  I didn't ask you for anything I haven't already done myself earlier in this thread. As you said, you went thru myriad attempts. This thread probably has 80% of what didn't work, and 20% of what did work. For posterity, and any new readers that stumble on this thread, I just thought it would be nice to have a single message that says, do this, and it should work.

---

### Post by Chiapo on 2010-08-04
You asked so nicely, how can I deny the request?

I've gathered the carrier specific firmware(at&t) from my WinXP installation by looking in the following directory:
C:\Documents and Settings\All Users\Application Data\QUALCOMM\QDLService\Options.txt

The Options.txt file should contain the path to the firmware used by your modem.

Note that with kernel 2.6.32 & upward, a patch needs to be applied to the gobi_loader, & is linked to below.

Get the gobi_loader here:
[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/) 

Here's the instructions given by msignor:
> Here are the steps summarized on how this should work...

1) Confirm that you have the modules "usbserial" and "qcserial" loaded
2) Confirm that your card is found in LSUSB, and note the product ID, for the Qualcomm card. 
3) Download / Make && Make Install the gobi_loader application
4) Create the folder /lib/firmware/gobi
5) Copy CDMA or GSM firmware from windows driver pack, to the firmware directory 
6) Unload & Re-Load the 'usbserial' and 'qcserial' modules
7) Run LSUSB, and now you should see a different Product ID (Bus 002 Device 003: ID 05c6:9202 Qualcomm, Inc. -- is what yours should look like) 
*** If this is all good, open a dialer like minicom or gnome-ppp or wvdial and make a connection to /dev/ttyUSB0 ***

For reference, the original product ID that is seen is for the Loader portion of the card. That is how we can load the firmware. The new device id shows us that the firmware was applied and is now running. 

-Matt

Where Matt suggests using different apps, I just use Network-Manager.

Cheers!

---

### Post by Chiapo on 2010-08-06
I just downloaded & installed Fedora 13 & it had the same issue with the modem.
[I borked my main xubuntu Lucid partition fooling with Fedora]
Subsequent clean installations of xubuntu 10.04 & following the old instructions above resulted in the gobi_loader not working properly.

Simply following the new instructions provided in the link to the gobi_loader above enables the modem to operate in Fedora 13.

Fedora has packages for handling these modems that *buntu doesn't have yet, hence the [COLOR="Red"]necessity for the gobi_loader patch in Ubuntu.[/COLOR] Applying the patch to the gobi_loader in *buntu 10.04 results in a working Qualcomm 9212 modem.

With a bit more testing, I might end up using Fedora exclusively.

I just need to keep learning! ;)

So far, the gobi_loader is working properly in Fedora 13, kernel 2.6.33.3-85.fc13.i686 & I'm quite happy with the system!
Sometimes the connection is dropped, but reconnecting via the Network Manager icon works fine.

Cheers!

---

### Post by jamere on 2010-09-04
[COLOR="Blue"]Ye who enter here, abandon all hope![/COLOR] 

Just kidding...I think. :D  Any news on this problem being fixed?

---

### Post by amartz on 2010-09-04
> **Chiapo said:**
> You asked so nicely, how can I deny the request?Cheers!

I just realized I've been rude for not thanking you for posting this.  I've just been real busy with work and life in general. Soon as I get some time, I'll give it a whirl. With my luck, just as Ubuntu puts everything in 10.10.  At least one could hope!
Art

---

### Post by houndi on 2010-09-05
Its a bump Would really like to get a solution to this and move on. Have a feeling the developers and networking gurus have been overwhelmed with all the reported NW problems on 9.10. Given all the variations in HW configurations and vendors, I have some sympathy.

---

### Post by Chiapo on 2010-10-15
It's working in Lucid for me... See above for instructions.

---

### Post by Chiapo on 2010-10-18
I just did an in-place upgrade from lucid to maverick & the modem functions properly from a cold boot! :guitar:

It's working nicely, with signal strength indicated in the tooltip for the networking icon.

I had the gobi_loader setup on the lucid system prior to the upgrade.

Thanks Ubuntu!

---

### Post by jamere on 2010-10-19
Hey Chiapo, good to see you check in with what appears to be good news! Not sure I'm grasping the nuances of the gobi_loader vs maverick and Fedora 13. Do you think maverick works "out of the box" so to speak, without having to screw around with the gobi_loader before the upgrade? Same question concerning Fedora 13. I guess another way to ask the question would be...is the gobi_loader fix included in maverick and Fedora 13? Any insight would be appreciated. 

Started looking into Fedora and it looks pretty nice and it looks like the kernel is several versions ahead of ubuntu's kernel, with new network and modem mgrs. I'll probably go ahead and upgrade just to be up-to-date.

aloha!:)

---

### Post by jamere on 2010-10-20
Well, I upgraded to Maverick 10.10 this morning and sorry to say the problem is not fixed in the upgrade (i.e. Qualcomm modem firmware not loading). Still have to do the Win/Lin two-step...dang it!:confused:

As a side note the upgrade went fairly quickly and without a hitch. Good work by some folks somewhere! :) 

Guess I'll have to go back and deal with the gobi-loader if I want to avoid booting into Win XP first. sheesh!

note: Chiapo, no need to reply to my earlier note. :)

---

### Post by Chiapo on 2010-10-21
My Lucid system had been previously configured to properly use the Qualcomm device + firmware. I did an upgrade via Update Manager, from xubuntu 10.04 to xubuntu 10.10

[hr]
Subsequent to the upgrade to Maverick, the Qualcomm 9212 modem is accessible to the system, albeit sporadically.

It appears that this latest iteration of the kernel is still handling the gobi chipset firmware improperly, with constant interruption of connection.

Xubuntu 10.04 works better, if you have the gobi_loader installed properly.

In Maverick Meerkat, the modem connects, but drops the connection after a short period... Repeatedly.

[edit]
I live in an area with a weak signal, thus the constantly dropped connection.
I have noticed that if I'm running a VPN, or tunneling via a remote shell account, the connection is retained, with few interruptions.

---

### Post by Chiapo on 2010-11-08
Well folks, it is with some reservation that I make the announcement that I have completely abandoned Xubuntu 10.10 in favor of Fedora 14 LXDE.

No more constantly dropped 3g connections!

I still had to setup the firmware directory, make && make install the gobi_loader, but this has become rote for me considering how many different distros I've attepted to get this modem to function acceptably with.

So I totally wiped my hdd after a year or more of fooling with multi-boot setups & a confusing number of /dev/sda*[SIZE="1"]n[/SIZE]* partitions, some of which irretrievably went the way of bardo, never to be seen again.

I would like to express my gratitude to all the people who have worked so diligently to bring the Ubuntu family of operating systems to the world absolutely free of charge - even to the point of MAILING ME AN INSTALL DISK FOR FREE!!!:guitar:

[CENTER][IMG]http://moco-sux.net63.net/palm-sig.jpg[/IMG][/CENTER]

Kudos to Canonical for giving less financially endowed individuals a chance to use excellent computer tools without resorting to the status quo systems who's ubiquitous nature favors those in higher income brackets. 

Let me finish by saying that I have a couple of persistent Xubuntu Maverick systems on USB flash drives, & these are valuable tools that I appreciate to the utmost!

Aloha *bunutu!

Thank you for the experience!

I shall return!

---

### Post by jamere on 2010-11-10
Chiapo,

I feel your pain! :) I'm pretty disillusioned myself concerning the lack of developer support on this Acer Netbook modem problem.  I'm through messing with the danged gobi_loader and I'm seriously considering going back to the dreaded Win XP. 

I agree, that 'buntu has been a mostly positive experience over the years. Who knows?...maybe the Qualcomm modem issue will be addressed in years to come... no longer holding my breath. :D

Aloha, and check back in here periodically to let us know how it goes with Fedora. Maybe the Fedora folks will address the gobi_loader problem.

later...


[COLOR="Red"]p.s. Almost 20,000 "views" of this thread!!! AMAZING![/COLOR]

---

### Post by Chiapo on 2010-11-23
So far, Fedora 14 LXDE has been every bit as easy to use as Xubuntu 10.10, with the added bonus of handling the Qualcomm modem quite well once the gobi_loader has been properly installed.

I'm quite happy with the system!

---

### Post by cuervo73 on 2010-11-25
I am jumping into this thread (before it dies) because I have a new netbook. It is an Gateway LT2016u and came with a Qualcomm 3G modem model HS-USB-9212 onboard.  I am a longtime Linux/BSD user and M$ agnostic.  So, I want to follow the footsteps you all have laid down for getting these modems working with Ubuntu. 

I have been using Lucid 10.03 Live on a USB memstick for a few weeks with wifi only.  Now, I need to have the 3G working too.

I read the entire thread, and reread some parts and I have most things well understood.. I have booted WinXP, then booted back into LL and the modem shows up with lsusb as:  
Bus 001 Device 005: ID 05c6 9212 Qualcomm

I have gobi-loader downloaded but haven't built yet becuz the Live version of LL has no gcc/dev-tools installed.  I have identified the driver bits/pieces under WinXP which get loaded there from path:
C:\ACER\preload\Autorun\DRV\Gobi 3G driver\Source\Data Folder\amss.mbn (and apps.mbn)
When I get gobi-loader built, I will also move copies of those Windoze drivers into /lib/firmware/gobi/

My questions: what to use, install and configure for the modem connectivity software?   Do I need to setup CHAP/PAP configs?  I used ppp long ago, but since then, I use broadband cable.  My wife initially took the Gateway for 3G setup at the Verizon store.  She now has no recollection of any account/password stuff; didn't write anything down.  Do I need to ferret around in the WinXP files to get those?  Or visit the Verizon store and have them show me?  I have poked around in the NM setup for BB modems and it asks for:  1) BB Providers name  2) BB Billing Plan Name and 3) Access Point name.  

What I should be doing to get connected with Verizon service?  For Linux configuration?  I figure that once I go to the VZ store, they will NOT have a clue about Linux so I am hoping to get that info here?

Thanks and sorry for this long rant..  ;)

---

### Post by bscoder on 2010-12-02
Have been having similar issue in a Gateway LT2016u netbook with this same modem.

Using Ubuntu 10.10... Installed the gobi_loader and then sometimes it'd work, sometimes it would simply refuse. In those cases, trying to load gobi_loader manually would give me a "device is busy" error.

The solution for me seems to be a little slider switch on the front of the unit that turns the 3g modem off and on... When it is dead (not appearing in my connection list), I turn it off, count 3 seconds, turn it back on, count to 3 again, and then check the network list and it's magically there again.

I don't know why just turning the whole PC off and on doesn't do it - maybe the modem remains powered? But it seems good now and I'm glad I don't have to reboot the thing 15 times to get a connection. =)

Coincidentally, when my desktop pc is hit with Verizon's wonderful 24-hour connection time limit and I get disconnected, I have to physically unplug the (USB720) modem and reattach it before it will dial back up again.

**edit: re: Cuervo73:** You shouldn't need to mess with ppp/chap, chat scripts, etc at all with recent Linux flavors - once they see the modem, you generally only need to tell it who your provider is and it takes care of the rest. With Verizon, I don't have to give it a # or login/pass or anything, it just works.

---

### Post by jamere on 2010-12-03
cuervo73 and bscoder...good luck guys!

I'm with ciapo and agree with his sentiments concerning this modem fiasco. I'm abandoning ship and reluctantly going back to the POS Windoze, sorry to say. I've used Ubuntu for roughly 4 years exclusively, without much in the way of problems, until I got my Acer Netbook with the Qualcom USB modem requiring the Gobi firmware loader. After screwing around with the gobi loader and dual booting for a year, I don't see any hope of this problem being solved by ubuntu developers. At last count there were 20,000 views of this thread, so it's no small issue. Looks like to me there's a whole class of Qualcom USB modems users being abandoned. At least Win XP will boot and maintain a connection reliably.

Anyway, sorry for the rant and I'll continue to monitor this thread hoping for a permanent fix to the problem...but no longer holding my breath! :)

---

### Post by cuervo73 on 2010-12-03
Got it working.  :)

Went to Verizon store where we got the Gateway and "cajoled" the the support folks for the "goods".  At first, they didn't want to help.  As soon as I said the L-word they said, "Oh, we don't support Linux..yadda yadda".  I kept emphasizing that I don't need Linux help.. just the authentication parameters so I could connect. Finally after one of their people watched me boot into LL and show him the NM setup window, he recalled the parameters (Number, Username & Password) I needed and once they were entered into NM, it connected first try.  Of course, that was after I booted into WinXP first for getting Qualcomm firmware loaded.  Hopefully, it will still work in the wild, like it did at the store.  

Did I recall correctly that putting the gobi-loader call into rc.local is a good way to setup firmware?  Now that I see this will work, I need to build gobi-loader and copy those  modules into /lib/firmware.  

If I can't get NM to do the job, I will just script it myself as I have done before for a couple of years while waiting for NM to "mature".  I was running Fedora back then.  I also used wicd for awhile during this period that NM failed to work properly.  Ubuntu is sooo much more stable than Fedora.

Thanks

---

### Post by amartz on 2011-01-24
Well, this is interesting!  I don't know when it started doing this, but my netbook now sees the 3G modem and connects without booting into windows first.  I have just always booted WinXP then rebooted to Ubuntu 10.10 as a matter of course. Since I only did this once a day, I could live with it.  Yesterday, I was distracted and missed the dual-boot window, and it booted directly to Ubuntu from a powered-off state, and much to my surprise, the 3G modem was there and connected.  I had installed the gobi loader thru the package manager a while back, but never followed up with any kind of configuration. In testing it, the modem doesn't show up every boot, but it does show up many to most of the time.  We'll see how it works long term, but it looks like I'll be booting WinXP a lot less now!! :p

---

### Post by amartz on 2011-02-03
Well, it's been over a week since I've had to boot WinXP first to get the 3G modem connected. With a recent tweak at the beginning of this week, the modem loads up almost every time with Ubuntu only.  It's not perfect, but almost every time.  The couple times it didn't work first time, doing a lsusb showed NO modem at all. Shutting down and re-powering would fix it.  So far, I'm quite happy!

---

### Post by Chiapo on 2011-02-14
@ Cuervo... I've been using Network Manager to handle the connection & it's working fine.
As for APN info, the networking wizard presents me with a few options such as Location, Service Provider, Plan Type, and the rest is automatic.
I'm with at&t and I chose the "Data Connect" option & that's it!

Username & password might be in your VZW connection manager debug menu, if any, but I see you've taken care of that already.

As for editing rc.local, I haven't needed to do so as the Network Manager has a check-box for "Connect Automatically."

At first I was intimidated by the gobi loader install process, but since I've done it so many times, I can almost do it blindfolded! [if only I had a bigger keyboard]

@ Amartz... Glad to see you got it working! Perseverance pays off! ):P

So far, I have found no distro that works with this modem "Right Out Of Box."
The good thing is that with the standardized *nix directory tree structure, the firmware goes in the same place in all of the distros I've tried.

Another thing I've noticed is that there have been updates to the page where the gobi_loader app comes from. This may be due to further refinements in the gobi_loader, & there may currently be a better firmware loader version there now. [I have yet to look] The last time I looked there were updated versions of gobi_loader, but there was more than one.
Since my firmware was found in the "2" directory in WinXP, I selected the gobi_loader correspondingly, but I never tried another version as the first one I tried did the job. 


In closing, I remain hopeful that this issue will be rectified with the next iteration of *buntu in April.

Best of wishes to you all.

[CENTER]Chiapo.



[IMG]http://moco-sux.net63.net/palm-sig.jpg[/IMG]
):P
[/CENTER]

---

### Post by DarkTide on 2011-04-05
I just did a clean re-install of xubuntu 9.10, kernel 2.6.31-19-generic,  installed gobi_loader (the new v4) and have been surfing via the  Qualcomm 9212 with no issues other than signal strength.

---

### Post by cejack on 2011-09-02
I have the Acer Aspire One ZG5.  

It is running great on 11.04 Natty.  Very pleased with it and usually use Wireless Networking via 802.11g / n wireless at the house.  

But I do have an unlimited data plan phone with AT&T and a SIM card plug in the AA1 that works in the Windows XP partition.  Doesn't seem to fly at all under 11.04.  

Is there anyone with a good setup like this that can give a step-by-step procedure to make the SIM card / 3G wireless connection work under Ubuntu 11.04?  

I can follow directions but please do not presume that I know how to "compile" anything or know where a certain file is located in order to edit it.  I need explicit instructions for dummies...

Thanks.

---

### Post by Chiapo on 2011-10-23
OK, since I remember how I felt when I couldn't get my AAO ZG5 Qualcomm 9212 '3G' [WWAN] modem online outside of Windoze, I'll list the steps I take to get this modem up and running in *NIX. 
First of all, be sure that the kernel you're using is up-to-date, as the necessary driver [qcserial] is not present in 2.6.29 < ... 
Go here ----> [http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)   <------ Read the page and download the most recent gobi-loader.tar.gz file.

You're going to have to figure out where your firmware files are and copy the two files,  amss.mbn and  apps.mbn, copying them to /lib/firmware/gobi/ 
You'll have to create the gobi directory with root privileges before you can copy the firmware files to their final destination. 
Once you've got the firmware in the right place, you can unpack the gobi-loader.tar.gz archive. I like to use a temporary directory to unpack such files into so as to have a clean workspace without any extraneous files. 
A simple click on the archive should invoke whichever app your distro uses to handle archive files, allowing you to select a destination directory to unpack the archive into. 
When you have the archive unpacked you'll need to open a terminal and navigate to the directory you unpacked the gobi-loader into, then do an ls -a to view the contents of the directory. 
There should be several files, with a README file containing any new instructions pertaining to the install process. 
After you've read and understood the README file, you can begin the compile process by simply typing the following command at the terminal prompt: 
make 
There should be very little output, with no error message. 
If all went well with the make, you then attain root privileges via whichever means you choose, the easiest probably being to add sudo to the make install command as follows: 
sudo make install 
After entering your password, the install process should commence, showing you a few lines of output in the terminal window, along with a success message. 
Now the easiest thing to do would be to simply reboot, but if you like the terminal you can type the following sequence of commands, which will stop networking, unload the qcserial driver module, then reload qcserial and resume networking services: 
sudo network-manager stop 

sudo modprobe -r qcserial 


sudo modprobe qcserial 

sudo network-manager start 

If all went well you should see the Qualcomm device productID change from 9211 to 9212.  
Type the following at the terminal prompt to see: 
lsusb 
If you see the 9212 on the same line as Qualcomm then you're good to go. 
From there, click on the networking icon and select the Mobile Broadband menu item to invoke the setup wizard. 
Follow the on screen instructions and your modem should begin connecting to your 3g provider.

---

