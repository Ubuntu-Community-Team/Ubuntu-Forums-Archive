---
title: "Internet doesn't work in Karmic"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by dj-toonz on 2009-10-29
Hi all, Just Installed Karmic 9.10 (dual booting with Jaunty 9.04) & I get a message on screen saying 3connect not responding :( & no mobile broadband showing up in the network-manager, the modem does show up when I do a lsusb 

Bus 002 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

how can I get the connection working under Karmic or update karmic via Jaunty as I can only get internet via Jaunty :(. or totally remove Karmic & give Jaunty back the space I wasted on Installing Karmic, cheers

I just had to a couple of commands in terminal & now it's working again :popcorn:

---

### Post by DavisYZA on 2009-10-29
Hey, what exactly were those commands? I have a similar problem, only that it's my first time I connect a Huawei Broadband on Karmic.

Delighted to see those commands!

---

### Post by dj-toonz on 2009-10-30
[ How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


Open up places, Computer & if you see a virtual CD ROM & HUAWEI SD Storage (for the microSD card if your modem Has one

right mouse click on the Virtual CD ROM (you don't need it as there windows drivers) & select safety remove device)

then when the HUAWEI SD Storage device & the virtual CD ROM has Gone , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these following commands (there just to get your modem to be seen by network-manager)

sudo modprobe -r option

[enter your user password if asked for it] then can follow on with the rest without entering your user password

sudo modprobe -r usbserial 

sudo modprobe usbserial vendor=0x12d1 product=0x1001

or 

sudo modprobe usbserial vendor=0x12d1 product=0x1003 [If the first code doesn't work]


& don't forget to close the terminal box when finished with it ;)


then when you goto Network-Manager & right mouse , click on edit connections, Mobile broadband, Add a connection , your modem will now be showing like it is in the screen shot

[[ UPDATE ]] Just been told, if it doesn't work the first time around, insert a MicroSD card in the modem before inserting into the machine ??? funny that,, but somebody said it worked for them that way, thought I would mention it, other wise I would be getting told off

And the screen shots to show the modem not working before I used the following commands & the modem working after.


P.S you have to do the following the first time you want to connect using the connection. After that you can disconnect & connect all you want, just make sure you don't reboot other wise you will have to repeat the above commands to get the connection working again 

*** you don't need to re-enter network-manager & re-add the connection after making it the first time *** your connection you made stays in network-manager 

"" If you do pull the modem out & plug it back in , just go back into places, Computer & safety remove the virtual CD & the connection will show back up in Network-Manager ""

now you can surf to your hearts content

sorry It's taken a bit to post back but just got in

Big shout out & credit goes to dmwelsch for letting me know about the MicroSD card tip & unpluging the modem & pluging it back in , that you have to either reboot the system to get the modem working or safety remove the virtual drive & HUAWEI SD Storage 

And finally to prove That the connection is live, screen shot *** IP address Masked for for privacy reasons ***

Any questions that need answering or your stuck trying to get your modem working under Karmic, just give me a private message or post in here & I will try to get it sorted out as quick as possible ;)

---

### Post by johnystevenson on 2009-10-30
dj-toonz 

well done mate on your how to.

that seems to have me sorted:D:D

---

### Post by dj-toonz on 2009-10-30
Just make sure you bookmark or write the commands down as you'll need to do the same when you reboot the Machine as they don't get stored :(, it's just a work-around till the problem gets fixed, come on admins make that a sticky for other people who's having problems

---

### Post by dj-toonz on 2009-10-30
Just bumping it so it goes to the top for others to benefit from the HOW-TO :p

---

### Post by dj-toonz on 2009-10-30
Bumping again to keep it up top, so others can find it

---

### Post by dmwelsch on 2009-10-30
Hi all, I tried these command without any success! Unfornately :(

The mobile broadband device is a Vodafone K3520 aka Huawei E169 (afaik).

Dmesg says:

```
[  770.168099] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  770.328389] usb 4-1: configuration #1 chosen from 1 choice
[  770.333222] usbserial_generic 4-1:1.0: generic converter detected
[  770.333332] usb 4-1: generic converter now attached to ttyUSB0
```Any suggestions?

Cheers

---

### Post by dj-toonz on 2009-10-30
type in lsusb in a terminal & give the output for the huewi modem

---

### Post by dmwelsch on 2009-10-30
lsusb gives

Bus 004 Device 004: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

---

### Post by dj-toonz on 2009-10-30
The above does work on a E169 as that's what I've got (got 5 Huwei modems) e220, a 02 one a vodafone & orange & it works on all the lot, did you do the first part of it, by going into places, Computer & removing the Virtal Drive ?. as I'm trying to think what could of gone wrong


Try this one aswell, Just had a look in my code book

modprobe usbserial vendor=0x12d1 product=0x1003

then carry on with the rest of it

*** it's just taking time to find the right product code that's all *** the rest of the HOW:TO works with them all

---

### Post by dmwelsch on 2009-10-30
Yes, I did. The icon appeared also on the Desktop where I right-clicked the icon and then safely removed the drive. Since no microsd card is inserted into the usb dongle, there was no reader icon. In the Computer view, there are only the ubuntu root file system, a windows partition, and a dvd drive nothing else.
After that I tried the commands you provided without any success. I will try it a fifth time. Perhaps I did something wrong berfore.

---

### Post by dj-toonz on 2009-10-30
after the first product number use this one

modprobe usbserial vendor=0x12d1 product=0x1003

and carry on

---

### Post by dmwelsch on 2009-10-30
Hi,
I repeated the procedure with product=0x1001 but this time is inserted a microsd card before plugging-in the Huawei stick and TADA: It works. Did you try it with inserted cards only? I will try to find out if the installed miscosd makes the difference.

Thanks a lot and Cheers

---

### Post by dj-toonz on 2009-10-30
I don't know if I did or not :) cheers for that I'll update the walk though now :D, I think there might be a card in mine, good luck, just remember to repeat it again the first time, before you start the connection after booting the system up, after that, you can disconnect & connect all day till you shut down

---

### Post by dmwelsch on 2009-10-30
There is still one flaw:
After I was able to connect to my provider via mobile broadband, I removed the Huawei stick and plugged it in again. I was not able to connect again since the network manager does not list the mobile broadband entries again. For now, just a reboot circumvents this problem

Cheers

---

### Post by dj-toonz on 2009-10-30
I posted that in the above HOW-TO lol never mind I'll edit it & add that part aswell

---

### Post by dj-toonz on 2009-10-30
bumping it up to help the community out with the HUAWEI 3G bug in karmic

---

### Post by madmax75 on 2009-10-31
Thanks, dj-toonz! I have a Huawei e169 and your instructions worked for me!

I just wish there will be an update soon to this problem. At least here in Finland there are tons of people using 3G broadband modems as their only connection to the net, more than many of them being Huawei modems.

The fact that these modems just don't work in 9.10 compared to 9.04 where they worked flawlessly as far as I can tell, is a VERY bad PR for Ubuntu.

If I hadn't my phone to access Ubuntu forums, I would still wonder why my net suddenly doesn't work anymore. Probably would have already re-installed 9.04.

---

### Post by dj-toonz on 2009-10-31
I know it's stupid that this has got into the final release of karmic, the modems used to work in the beta & RC version but then they stopped working after updating the kernel to the one in the final release :( at least my workaround work's to get the modem working , going to have to change it as I've just found out it work's with just 3 of the commands, you don't have to do all of them :)

---

### Post by johnystevenson on 2009-11-02
i was going to add that as its the same here.  The modem connects before i can paste in the last command (k3520 vodafone).

again well done.:D

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by deebocean on 2009-11-27
Thanks, worked great for me :)

---

