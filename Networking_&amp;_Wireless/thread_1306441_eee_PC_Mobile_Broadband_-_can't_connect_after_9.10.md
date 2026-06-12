---
title: "eee PC Mobile Broadband - can't connect after 9.10 upgrade"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by MalphasWats on 2009-10-30
Hi,

  I installed the 9.10 UNR upgrade today, had a few problems getting it going to start with but everything seems ok so far.

One problem I've just noticed though is that I can no longer connect to my built-in mobile broadband connection.

Wireless is working fine, I can see all of the networks around me but there isn't an option to connect to my mobile broadband connection any more.

If I bring up the networking options, there is still a Mobile Broadband tab in there with the connection I set up when I first installed 9.04 but I can't find any way to actually connect to it.

Anyone have any idea?

thanks
-Malphas

---

### Post by scardario on 2009-10-30
The same happened to me :(, I can't connect since the upgrade

---

### Post by yellowbread on 2009-10-31
Same thing here. Its funny, but in karmic alpha 6 it was working fine, then upgrading to the actual release version killed it. I'm connecting with pppd using the /etc/ppp/options and /etc/ppp/chat-options files from my Arch partition for now.

---

### Post by pdc on 2009-10-31
Hi yellowbread;

so you have an Eee with mobile broadband built in?

What does 

> lsusb

and > dmesg give if typed into a terminal?

---

### Post by dj-toonz on 2009-10-31
what modem is it ? if it's a Heuwi, i can probley help you out on that score 

How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


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


& don't forget to close the terminal box when finished with it


then when you goto Network-Manager & right mouse , click on edit connections, Mobile broadband, Add a connection , your modem will now be showing like it is in the screen shot

[[ UPDATE ]] Just been told, if it doesn't work the first time around, insert a MicroSD card in the modem before inserting into the machine ??? funny that,, but somebody said it worked for them that way, thought I would mention it, other wise I would be getting told off

And the screen shots to show the modem not working before I used the following commands & the modem working after.


P.S you have to do the following the first time you want to connect using the connection. After that you can disconnect & connect all you want, just make sure you don't reboot other wise you will have to repeat the above commands to get the connection working again

*** you don't need to re-enter network-manager & re-add the connection after making it the first time *** your connection you made stays in network-manager

"" If you do pull the modem out & plug it back in , just go back into places, Computer & safety remove the virtual CD & the connection will show back up in Network-Manager ""

now you can surf to your hearts content

sorry It's taken a bit to post back but just got in

Big shout out & credit goes to dmwelsch for letting me know about the MicroSD card tip & unpluging the modem & pluging it back in , that you have to either reboot the system to get the modem working or safety remove the virtual drive & HUAWEI SD Storage

---

### Post by slyborg on 2009-11-06
> **dj-toonz said:**
> what modem is it ? if it's a Heuwi, i can probley help you out on that score 

How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


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


& don't forget to close the terminal box when finished with it

Thank you so and so for these suggestions!

Now I tried to automate the job. I did a script as follows:

cd "/media/Mobile Partner"/
if [ "$PWD" = "/media/Mobile Partner" ]; then
cd
umount "/media/Mobile Partner"/
modprobe -r option
modprobe -r usbserial
modprobe usbserial vendor=0x12d1 product=0x1003
echo "modem ready"
else
cd
echo "there's no modem"
fi

(of course "Mobile Partner" is a name depending on the contents of your modem")

It works (you simply must log in admin by 'sudo su' and execute it, exiting when finished), but I don't know where to put it. I seen that the "usb key" modem is mount after user login (if you switch to console and do a "df" or "mount" before and after login you'll see that). So it's not possible to insert this script into /etc/rc.xxx (I don't know  nothing about ubuntu because I'm used to be friendly with other distros).

Anybody has any idea about this automation? I tried with .profile but it seems not to be the right way. Thank you.


(edit: my hspa modem is an external usb, huawei e270)

---

### Post by MalphasWats on 2009-11-07
Hi,

  Thanks for this. I actually don't know what modem I have, it's built into the netbook, so it doesn't sound like it's the right one.

I've actually discovered that if I go into networks, change a setting in the 'Mobile Broadband' tab and reboot, it picks up the modem and it works (I'm using it to post this) however it doesn't work the next time I reboot.

I never had any problems with it under 9.04, so I'm really confused!

---

### Post by slyborg on 2009-11-10
Hi,

it's just because I posted some days ago (it doesn't fix the problem with MalphasWats, I'm sorry). There is a way to go right without any script nor "modprobing". I re-installed ubuntu netbook remix, and as they say (clicking the help button), it's just matter to connect the internet key *after* log-in. Then left click on connections and set the provider.

The problems I had were originated by plugin the "internet box" before turning on the computer. It's the way I used with Slackware, but here it doesn't run. Just matter of plug the box after login.

---

