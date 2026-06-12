---
title: "Mobile broadband problem, AGAIN!"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by sammyko on 2009-11-15
Hi there,
I'm an ABSOLUTE beginer with Ubuntu and Linux in general.
Have just install Ubuntu 9.10 on my Asus laptop. For mobile broadband have purchased Huawei  E1553 (3G).
It seems to install OK (connection established), but Firefox can't connect to anything ("server not found"). And yet, when I've tried to use Skype (skype_static 2.1.0.47) it did connect me and I was able to see and to speak to people. That is until a couple hours ago. Now, it also refuses to work for me (P2P connection failed) and I've tried a quite a few times.
So, I need some HELP, please.

---

### Post by Rhubarb on 2009-11-15
This bug effects me as well.
But I don't use skype, so I can't vouch for that part.

I've been a bit lazy in searching for a solution / workaround to this problem, so it may well be a known bug that's being worked upon as we speak.

The only successful way I can get it working in Ubuntu karmic 9.10 is disconnect / reconnect several times then it'll magically work.
It sucks, but it does work if you're patient.

I have a huawei e160g 3g usb dongle running Ubuntu 9.10 32bit desktop (and netbook remix).

I'll have a decent look around sometime to try and find the cause of the problem and get a fix for it.  But for now I'm feeling too lazy :P

---

### Post by sammyko on 2009-11-17
I've just tried to use this modem on my friend's laptop (he uses E220, also on 3G, and his modem worked on my Ubuntu 9.10), running Ubuntu 9.04.
Guess what? IT DIDN'T WORK! At all....
Is something wrong with the modem? Too new for Ubuntu? It works no problems on Windows...

Please, HELP!!!

---

### Post by mundo on 2009-11-18
I'm experiencing this issue as well using E172 modem on Vodafone in UK. The modem light stays on and the network manager says that I am connected but I don't have any internet. If I remove the modem then re-insert it and then re-connect then it works. All very annoying. Would be great if a solution could be found.

---

### Post by r.mariappan on 2009-11-18
You can probably check the proxy settings for mozilla firefox.
Dono whether you done this already..
But this is what i know..

---

### Post by mundo on 2009-11-18
Blimey, I think it was this simple! All working for me now. I just changed this in Firefox:

Edit>Preferences>Advanced>Network tab>Settings>Change from "Use system proxy settings" to "Auto-detect proxy settings for this network"

Has the default option for this been changed in 9.10 which is creating this issue? I had just assumed that the connection settings were already auto-detect and hadn't thought that this would be the issue.

---

### Post by kensta87 on 2009-11-18
you can try to install mobile partner from huawei website or just google mobile partner for linux ... though it may not work in ubuntu we only need the drivers which come with it upon installation...then go to to the filesystem and check out for this  /dev/ttyUSB_utps_modem thats the driver which mobile partner uses to communicate with your modem
Then got to terminal i.e application>accessories>terminal or try Alt+F2 then type terminal
once in terminal just type pppconfig  and select create new and direct it to that modem port (the one you saw in the dev folder), after creating your connection use pon to connect and poff to disconect.. its old school but it works for me...

---

### Post by itsjustarumour on 2009-11-18
> **mundo said:**
> I'm experiencing this issue as well using E172 modem on Vodafone in UK. The modem light stays on and the network manager says that I am connected but I don't have any internet. If I remove the modem then re-insert it and then re-connect then it works. All very annoying. Would be great if a solution could be found.

Exactly the same problem here, E172 dongle on Vodafone in the UK (fresh install Karmic 9.10, 32-bit).  I get the Notify-OSD notifications too to say that I'm connected, but it appears that I am not.

---

### Post by mundo on 2009-11-18
Did you try changing your Firefox connections settings like I posted above?

---

### Post by pdc on 2009-11-18
if that does not work, 

look at post #44

[http://ubuntuforums.org/showthread.php?t=1305931&page=5](http://ubuntuforums.org/showthread.php?t=1305931&page=5)

and install the Vodafone package, that also works for networks other than Vodafone;

VMC seems a very good product, that is actively maintained; and provides a forum support for those interested in mobile broadband

google on betavine linux VMC

---

### Post by cavh on 2009-11-19
These steps helped me:

1. update your modem firmware by browsing the support section on the website of your mobile operator. You will unfortunately need access to a Windows machine for this.

2. disable the 'boot from USB' option in your BIOS.

These two steps seem to have resolved my issue with my Huawei E17X on the T-Mobile network here in the UK (using Karmic Koala 9.10 with kernel version 2.6.31-14-generic).

---

### Post by Rhubarb on 2009-12-22
I ended up using wvdial, a cool app I discovered back when I tried out Arch a few months ago.
wvdial works, and for me works better than network manager ever did (even back when it was working in Ubuntu 9.04).

I put my solution in this thread (post number 5):
[rogers rocket stick]("http://ubuntuforums.org/showthread.php?p=8544216")

---

### Post by svetiev on 2009-12-22
Sammyko, 

I've had the same problem. To fix this, you need to do what was instructed in post #6 and also in network connections > mobile broadband > your mobile provider > edit - you need to enable the option - available to all users.

Right now it seems to be working for me, although i've been fooled by this problem sevaral times into thinking that it was solved.

I also did one other thing, in passwords and encryption keys I left the keyring passwd blank so it doesn't ask me for it everytime i wan't to connect.

---

### Post by svaens on 2009-12-22
I have, I think, the same kind of problem. 

I make a connection with my mobile broadband (usb). 
I see the network manager applet icon swirl around (karmic) until it shows the blue connection strength bars. Good. Connected!
Skype, which was showing grey, is then showing green (connected), and I am able to chat, voip etc without troubles. 

However, sometimes, at this stage I am both unable to;

1. ping from console
2. browse using browser such as firefox (or any other browser). 

Even If I was willing to accept 'changing the connection settings for firefox' as a solution (ignoring the fact that ping was still not working), I have proven (at least for my circumstances) that this does not help. I changed firefox settings to 'automatically detect' and I have still had the situation where skype was connected, and yet firefox was not able to do anything.

This looks to me like the steps through network manager goes through to setup a network connection are sometimes incomplete. 

What is different between how skype connects to the outside world and what a basic 'ping' does ? Is skype using UDP or something ? Is somehow the TCP/IP settings not setup properly sometimes on the mobile broadband ? 

I have had this problem on both jaunty and now karmic. 

Any experts got an opinion on this?

---

### Post by svetiev on 2009-12-23
You also need to open network connections (right click on the network notification icon and select "manage connections", there you need to open the mobile broadband tab, then select your mobile operator and click edit.

At this point it's probably gonna ask you for your use password, before you do that you have to minimize the "authenticate" window as you will see another ERROR window beneath it. Close the ERROR window and then wait at least 30 seconds before entering your password in the authenticate window (it's a bug don't ask why is it so, but you have to wait 30 sec otherwise it just crashes). 

If the operation was successful than nothing would happened and you will have to click edit again. This time the settings for you mobile operator should appear. Here at the bottom just ENABLE the "AVAILABLE TO ALL USERS" option, click apply and then close everything.

Voalla, this should give you a working mobile broadband connection when you connect for the first time after booting up. If you try to reconnect it won't work anymore. I'm pretty much a noob but this is what I understand about this problem:

1. There is some kind of root vs. user conflict in network manager concerning the password which is used to log in to a mobile broadband connections. It seems to constantly erase that passwd while leaving the field blank. 

2. So according to no. 1, the problem is somehow connected to Seahorse encryption keys manager, as it doesn't show the stored passwd for the mobile broadband operator anywhere.

This is basically what i've been able to deduce about this problem, but I lack the knowledge t provide a better solution to it :(. So I hope this is gonna help someone else to figure this thing out completely :)

---

