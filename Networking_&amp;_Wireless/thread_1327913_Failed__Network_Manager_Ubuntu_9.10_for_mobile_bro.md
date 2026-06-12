---
title: "Failed : Network Manager Ubuntu 9.10 for mobile broadband"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by grimanda on 2009-11-15
Hi All...

I'm newbie to ubuntu

I have upgraded from ubuntu 9.04 to 9.10 for AMD64, but currently i can't use my external modem (GSM Network) anymore, 
1. I pluged my external modem (GSM) ==> after login to ubuntu 9.10
2. I click my operator
When i try to click my operator then the network indicator's animation (symbolized as 2 dot at upper right and lower left which form a cicle animation), will loop really fast and never stop execept by clicking "disconnect", and looks like i get no IP from it,

**_If _**i plug the modem since the power off, then start ubuntu, login and click mygsmoperator, sometimes it will connect to the network, but there is no traffic to the network, i can't ping yahoo, or etc..

Kindly need your advice how to solve this problem..


Thankyou in advance

---

### Post by pdc on 2009-11-16
if it all worked on 9.04, many would suggest you just go back to what you know worked: (ie 9.04)

9.10 has a variety of issues it would seem with mobile broadband;

new software may well have problems

---

### Post by grimanda on 2009-11-16
Hi PDC,...
Thx for responding

Actually i don't have much time to reinstall 9.04 including the setting and anyother package software.., it will take a lot of time, so i decide to solve the issue .., 

any other suggestion?

---

### Post by driftertx on 2009-11-16
I use ATT as my carrier for my datacard in ubuntu 9.10 and I've had the best luck with the pc cards (sierra wireless and option wireless pcmcia/pc card express cards).

One thing you might try is turn off your PC then plug in the usb card prior to booting. My older sierra wireless card would not work unless it was booted while the card was in the slot during the boot sequence. I also noticed that if I removed it during usage it would occasionally lock up. The newer gear seems more forgiving and more stable. If you still can't get it to work you can buy sierra wireless pc cards/pc card express slot cards (with no contract attached) for around 40$ used on eBay.

Make sure you go through the network manager and create a connection profile under the mobile wireless for <your carrier> data connect. Another issue I've found to watch out for is you may have to try to get it to establish connections a few times (4-5times) with ATT's network before it registers sometimes.

While some of these things suck to have to do it beats using microsoft's crappy OS. Hope this help!

---

### Post by grimanda on 2009-11-16
Hi driftertx...

I don't think the problems came from my modem, i have used Sierra 881U before (when i still in ubuntu 9.04), and it worked fine, and so my Icon 7.2 modem. Since i upgraded to 9.10, everything just fine, after several online update this problem comes up, i can no longer use my PDA Win 6.1 with share network to my ubuntu, just FYI currently i'm online by using my Icon modem (i pluged it before booting up my ubuntu, yeah sometimes it work, but perhaps the probability is 1/10), and this are the symptoms

1. If get connected and i can ping yahoo, etc,
   a. The network become really slower (3G) than in windows (3G)
   b. there is no traffic activity in traffic system monitor
   c. ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.80.71.188  P-t-P:10.64.64.64 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1547 [COLOR="Blue"]errors:0[/COLOR] dropped:0 overruns:0 frame:0
          TX packets:1473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1206950 (1.2 MB)  TX bytes:177925 (177.9 KB)

2. If connected but i can't ping anything, 
   a. just like c point above, but with error
      RX packets:110 [COLOR="Blue"]errors:52[/COLOR]


So, I think, the problem comes from the ubuntu/package.., 
I'm not sure if i restart/plug off my modem, i can get connected again just like now..


NB: there is no problem with wireless network, only with broadband network

---

### Post by utc271 on 2009-11-16
experienced same problem like yours...[http://nixcraft.com/ubuntu-debian/12...em-ubuntu.html]("http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html").this thread helped me to get online,need to modify a bit though..dont forget to plug modem first b4 booting...after changes hv been made a restart may b needed.
cheers

---

### Post by grimanda on 2009-11-16
Hi UTC271...

Thx for your advice..., I will try to consider sour suggestion, i have used it once when I still with ubuntu 9.04, and it work for almost all modem, but just a little bit inconvenience, that i need to open a terminal to connect, that's why i prefer to use network manger. it's more user friendly.

Currently i'm still waiting for network manager soulution


Thankyou

---

### Post by cavh on 2009-11-19
Try this:

1. update your modem firmware by browsing the support section on the website of your mobile operator. You will unfortunately need access to a Windows machine for this.

2. disable the 'boot from USB' option in your BIOS.

These two steps seem to have resolved my issue with my Huawei E17X on the T-Mobile network here in the UK (using Karmic Koala 9.10 with kernel version 2.6.31-14-generic).

---

### Post by grimanda on 2009-11-23
Hi Cavh..

Seems it's not working for mine, it happened also to my PDA (WinMobile 6.1), My Karmic no longger can connect to the internet by using sharing network from m'PDA..

Is there any update for this issue? 



BR,

---

### Post by cavh on 2009-11-23
Sorry I can't help any further - I have now exhausted my knowledge on this issue!;)

---

### Post by roborob101 on 2009-12-02
i have the same issue with my AT&T USBConnect Mercury (a.k.a., Sierra Wireless 885). Just found this, straight from the Sierra Wireless website.

> **Note: Ubuntu 9.10 distribution is not supported with Sierra Wireless modems. Ubuntu 9.04 distribution is still supported with all Sierra Wireless modems listed in this KB article.
We expect the issue to be fixed in Ubuntu 10.4.

source: [http://sierrawireless.custhelp.com/app/answers/detail/a_id/500]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/500")

---

### Post by grimanda on 2009-12-07
Hi Robo..

perhaps u can try Wvdial..., don't know it would work well or not, but nice to try.

---

### Post by xontero on 2009-12-09
Hello,

I have a fujitsu t5010 with a SierraWireless MC8790 UMTS-Modem. It worked in 9.10 but after a firmware update of the modem not anymore. Does anyone know why the SierraWireless-Devices are not working on Karmic Koala. Is it because of the new Version of NetworkManager (and co. programs) or another piece of ubuntu or is it because of the ubuntu patch on the kernel. I have this question because its maybe possible to run an older version of networkmanager or the accountable program  (for example from ubuntu  9.04).

thanks

---

### Post by lbrooks303 on 2009-12-19
I was having the same issue with my Sierra Mercury USB AT&T mobile broadband card.  Ubuntu 9.10 (Karmic) network manager said I was connected to the AT&T GSM network but I could never get connected to the internet.  My solution was to follow exactly the directions in the Sierra driver download "readme" file for driver download and installation.  Here are the basic steps:

1.  Download and install the latest Sierra Mercury driver from the Sierra wireless website quoted above.  I have updated to the 2.6.31-16-generic Linux kernel so the driver is v 1.7.12.  Verify that you have actually installed the new driver and replaced the default driver (v 1.3.7) by executing the following terminal command:

sudo -s modinfo Sierra

This should return the v 1.7.12, in my case.

2,  Install the KPPP program using the Synaptic Manager - and all required programs - the Manager will tell you what needs to be installed.

3.  Follow the "readme" instructions.  I had difficulty with the configuration and had to do the Modem configuration first, then the Accounts setup.

4.  Also I did not have the "dev/ttyUSB4" selection - only the 0 through 3 - so I chose "dev/ttyUSB3".

5,  For AT&T, the login username is blank, but you must enter a "spacebar" space.  The password is "CINGULAR1" .

6.  The connection worked every time I tested it (about 5) using different initial points (USB modem in on bootup and out on bootup, removing the modem while booted up then reinserting it).

7.  Some observations:

  a.  Network Manager does not recognize the connection done through the KPPP GUI interface - that is, you don't get the bars and connection established on the Network Manager icon.

  b.  KPPP provides very nice connection details and statistics not provided by Network Manager.

  c.  I have no idea how to automate this KPPP process by entering the appropriate data in the mobile broadband configuration dialogue for setting up the mobile broadband connection through Network Manager.

Hope this helps all the other Linux newbies like me.

Good luck,
Preston (lbrooks303)

---

### Post by Paulo Wageck on 2009-12-19
I had a similar problem with a ZTE MF100.

[http://ubuntuforums.org/showthread.php?t=1359410](http://ubuntuforums.org/showthread.php?t=1359410)


The last step in my tutorial solved the DNS problem for me... I think it will work for you all...

Cheers and good luck!

:guitar:

---

### Post by webdevelopment on 2010-03-20
now i need to learn how to use KPPP

i get this error

Could not launch 'KPPP'
Failed to execute child process "kppp" (Permission denied)

---

### Post by 2hot6ft2 on 2010-03-20
I don't know if it will help any but I saw this post the other day that was interesting.
> **fheinsen said:**
> I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install gnome-ppp -- this is the application you will use to connect, and do the following:

**Step 1.** Plug the modem in on a freshly restarted computer.
**Step 2.** Launch gnome-ppp as superuser (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))
If nothing else it may help you figure the problem out.

---

