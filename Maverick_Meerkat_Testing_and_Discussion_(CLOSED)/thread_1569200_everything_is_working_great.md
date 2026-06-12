---
title: "everything is working great"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2010-09-06
no problems at all. boot time is a little slow but opening and switching apps is faster in 10.10 than 10.04

---

### Post by karmila on 2010-09-06
Same with me.

Boot a little slow compared to lucid but everything else works fine. Sometime crash error report pop up even there is no crash or error.

---

### Post by exploder on 2010-09-06
There is no text at all showing on boot with Plymouth, now that's nice!

---

### Post by cariboo on 2010-09-06
> **karmila said:**
> Same with me.

Boot a little slow compared to lucid but everything else works fine. Sometime crash error report pop up even there is no crash or error.

If error/crash reports are popping up, then it isn't working fine. There are crashes that don't bring the whole system down. Report the errors that you do get, if they are already reported, add yourself to the affects me too list.

---

### Post by Johan Karl Johansen on 2010-09-06
Suspend works ;) first time ever (since 9.04)
acer aspire 7720g

---

### Post by exploder on 2010-09-06
The crash reports are not showing up for me anymore. I submitted reports.

---

### Post by rburkartjo on 2010-09-06
ex i am getting the crash reports on my end

---

### Post by exploder on 2010-09-06
> ex i am getting the crash reports on my end

Maybe the server you are using has not got the updates yet that fix the crash reports. Things are working amazingly well here.

---

### Post by rburkartjo on 2010-09-06
ex good idea i will try another one

---

### Post by ktp on 2010-09-06
> **rburkartjo said:**
> no problems at all. boot time is a little slow but opening and switching apps is faster in 10.10 than 10.04

enjoy!! =)

---

### Post by Jim March on 2010-09-07
Working solid as hell here: IBM Thinkpad T60p part number 8741-C2U - Intel T7400 CPU, ATI FireGL V5250 (similar to X1700), Intel WiFi, etc.  I've also tested Bluetooth for cellphone tethering, the Expresscard slot works (haven't tried PCMCIA/Cardbus yet).  Here's my lspci output so you can see what parts are in here:

> jim@jim-lappy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
jim@jim-lappy:~$

Best surprise is that I can transmit on the 3945ABG WiFi chip - in other words, rebroadcast a cellmodem to other computers.  Didn't think Intel chips could do that but this one can!

Ethernet also works.  Good thing too - one of the updates broke X, I had to boot to a command prompt, run Ethernet and do a command line update, fixed everything right away.  No biggie :).

Very, very pleased so far.

---

### Post by 23dornot23d on 2010-09-07
What computers are you all using that are saying its working fine ...... Desktops or Laptops 
( what graphics cards are you using ? ) 

With Nvidia at the moment and the latest drivers  256.53  cannot get any 3D whatsoever.

I am guessing none of you are doing any 3D ...... also Cairo Dock no longer seems to function for me.

I have tried everything I know to get beyond generic-19 with the graphics issues ...... but now its all a no go - I am waiting and hope that this will resolve itself somehow.

---

### Post by fabounet on 2010-09-07
for Cairo-Dock use the version from the PPA
[http://www.glx-dock.org/ww_page.php?p=Accueil&lang=en#0-Installation]("http://www.glx-dock.org/ww_page.php?p=Accueil&lang=en#0-Installation")
the version in Maverick is currently an old beta.

---

### Post by 23dornot23d on 2010-09-07
Cheers .... 
I did not know that about Cairo-Dock ....

I will give it a go ..... with Cairo-Dock PPA a little later on ..... 

I am just checking one more system out to see if I still cannot get the 3D to work ...

Its not letting me configure the graphics card Nvidia 9300M GS ...... 256.53 driver will not work now .... generic-20 at least it would set up before in generic-19 on one system.

I do a reconfigure graphics and restart the X-server and it goes in at the right resolution and looks good ..... but none of the 3D applications will work and the Nvidia graphics will not set up.

I am just having one more go on a really clean install that I did to a USB stick to make sure it is not something that I have inadvertently added or changed through the course of the testing. *as everything was fine upto generic-14 .... I stopped upgrading after the warning about graphics problems ..... 
(Its been a great system up to there - but now its not working for me and I cannot tell exactly why this is  ....... yet ....... people keep mentioning glx not working).

But when I saw this thread - **everything is working great** .......

I guess I really wanted to know how many use Nvidia and how many are using 3D ?
and if any are using Acer laptops .....

---

### Post by julianb on 2010-09-07
Success: Maverick's battery power management seems very good. On a eeePC machine where I used to use WinXP and Lucid, maverick seems to make the battery last 20% longer than Windows. That was not my experience with Lucid.

Failure: liveUSB created in PeppermintOS using USB-creator could not boot or install. Same problem using USB-creator.exe or unetbootin in Windows. None of the solutions I saw on this forum seemed to work for me. (was no problem in Lucid)

Success: Upgrade from Lucid didn't seem to introduce any serious problems at all. 

Failure: Performance with the webcam is not good. In Cheese, photos work, video works but not at an acceptable frame rate. (Same as Lucid.)

Success: eeePC boot time of 30 seconds. auto-login works out of the box. as desired, the machine connects to my encrypted wireless network at startup without asking. (better than Lucid)

Failure: eeePC 1201HAB shortcut keys (monitor brightness up/down, volume up/down, etc) don't work out of the box. (same as lucid)

---

### Post by cariboo on 2010-09-07
As I've posted before, I have no problem with the latest nvidia-current from the repositories. I have full affects on three systems.

My main system at home is a custom built system:

[list]
[*] MSI K9N6PGM2 motherboard
[*] AMD X2 240 CPU
[*] 2GB Ram
[*] Nvidia 210GT Video Card
[*] 2X 250GB Hard Drives
[*] Ubuntu only
[/list]

My main office system

[list]
[*] MSI K9N6PGM2 motherboard
[*] AMD X2 3800+ CPU
[*] 2Gb Ram
[*] Nvidia 9400GT Video Card
[*] 2X 160GB Hard Drives
[*] Dual boot Win 7 + Maverick
[/list]

My shop system

[list]
[*] MSI RS480M2 motherboard
[*] AMD 3200+ CPU
[*] 1Gb Ram
[*] Nvidia 8400GS Video Card
[*] 1 30Gb + 1 160Gb hard drives
[*] Quintuple boot XP, Maverick, PCLinuxOS, Fedora and openSUSE
[/list]

---

### Post by Jim March on 2010-09-07
Full 3D effects here including the Compiz cube.  I've also been trying some first-person shooters like Nexuiz and others, no problems at all.  See the details I posted above but it's an ATI FireGL5250, similar to the X1700, on an IBM Thinkpad T60p - tested at full 1680x1050 resolution.

---

### Post by 23dornot23d on 2010-09-07
Cheers .... for the replies - I have got full 3D and all the effects with the older kernels.
But as soon as I upgrade the kernel then things stop working and I am not sure what to do - I can usually get it working ok, by purging the Nvidia drivers and re-installing them - 

...... in the past I have used both sets and they work ok with the older kernels generic 6 through to generic 14 
( then I stopped upgrading as I was using it very well as a production system ) 
( I restarted at generic 19 when I thought things had settled down again - after reading the threads saying that the Nvidia Graphics seemed to be ok )......

I have used both sets of drivers on two separate systems I have installed on my hard drives one from the Nvidia site and one from the repositories ..... both are giving me very similar results ..... neither being 100% satisfactory.

I will not try to track down the problem as that seems pointless - as things are still moving on with graphics at the moment  ........ and I need a totally clean build to let you know how it works from a fresh install.

So ...... I am now downloading the [Daily Build  ]("http://cdimage.ubuntu.com/daily-live/current/")is this the one everyone seems to be running at present with fully working systems ?

I will create a clean partition and do a fresh install sometime later tonight.
and if that still doesn't work - I will ask for advice on how to go about tracking down what the problem may be, if there still is one.

---

### Post by cariboo on 2010-09-07
I'm running the daily build from about 10 days ago, updated a couple of times a day currently running :

> Linux chilanko-maverick 2.6.35-20-generic #29-Ubuntu SMP Fri Sep 3 14:55:28 UTC 2010 x86_64 GNU/Linux

---

### Post by 23meg on 2010-09-07
If everything is working great, it either happens that you aren't interested in the stuff that isn't working so great, or aren't pushing things hard enough.

Anyway, is this thread supposed to serve any purpose at this point? It seems like it's set to become a pile of random positive or negative observations, the latter of which are better posted to separate appropriately titled threads for better readability and more efficient debugging / bug reporting.

---

### Post by 23dornot23d on 2010-09-07
Its a useful thread for quickly discussing a few issues - before committing to writing a full blown thread on any item ..... I think its useful .... as long as we post the most relevant issues after having a quick chat about the general status of things .....

I have a feeling that dealing with just the individual items ...... we may just loose focus on the overall effect of what is happening to the full system ......

It needs one thread at least ...... 

[B]At least we can ask those who have their systems running well - how they managed to do it ....... ( which is very useful )
[/B] 
____________________________________________________________________________________________________

Also when you start to get a really good set of responses here ...... you will get a good feel for the overall way the Distro is heading  - Status ......

Just keep this one thread - for a general discussion about how well its going overall.

---

### Post by Cenotaph on 2010-09-07
maverick is probably the worst experience with any ubuntu i had while Beta. Still getting lots of issues, including the computer freezing completely for apparently no reason. im a bit worried, i must confess.

---

### Post by go7Ul1ai on 2010-09-07
Works fine for me, no problems :)

---

### Post by exploder on 2010-09-07
> maverick is probably the worst experience with any ubuntu i had while Beta. Still getting lots of issues, including the computer freezing completely for apparently no reason. im a bit worried, i must confess.

I had problems with the system freezing with the open source nvidea drivers, installing the proprietary drivers cured the problem. Installing Startup Manager and adjusting the settings fixed Plymouth so it displays properly.

---

### Post by 23dornot23d on 2010-09-07
> **exploder said:**
> I had problems with the system freezing with the open source nvidea drivers, installing the proprietary drivers cured the problem. Installing Startup Manager and adjusting the settings fixed Plymouth so it displays properly.

What kernels are you all using ? ...... (uname -r)

If it works well give a little info on what graphics card and what system you use please.

---

### Post by exploder on 2010-09-07
2.6.35-20 generic x64

---

### Post by ktp on 2010-09-07
> **23meg said:**
> If everything is working great, it either happens that you aren't interested in the stuff that isn't working so great, or aren't pushing things hard enough.

I was thinking the same thing...there is no such thing as bug free code. =)

---

### Post by 23dornot23d on 2010-09-07
I just tried the latest Daily Build ....
It booted ok into a normal graphics mode ..... but
The Nvidia 256.53 graphics driver was not on the disk - so could not try it out .

It would not install to my hard drive and just hung there ..... on the first screen
after ticking to install the MP3 stuff ....... but leaving the updates check box - un-ticked.

No messages came back from it - so you are left wondering what is going on ..... 

I had to kill it ...... as it would not let me out ......

( gparted crashed too from the CD ..... does not fill me with faith - but most other things keyboard mouse wifi etc worked ok )

---

### Post by cariboo on 2010-09-07
> **23meg said:**
> If everything is working great, it either happens that you aren't interested in the stuff that isn't working so great, or aren't pushing things hard enough.

Anyway, is this thread supposed to serve any purpose at this point? It seems like it's set to become a pile of random positive or negative observations, the latter of which are better posted to separate appropriately titled threads for better readability and more efficient debugging / bug reporting.

All the bugs I've submitted so far are either repaired, or except for one, being worked on or in heavy discussion.

---

### Post by exploder on 2010-09-07
23dornot23d, I had the same problems with the installer that you did. I ran the install from the live session and the install worked as it normally does.

---

### Post by exploder on 2010-09-07
23dornot23d, I had the same problems with the installer that you did. I ran the install from the live session and the install worked as it normally does.

---

### Post by exploder on 2010-09-07
Well, I spoke too soon. Two days of no problems and today the system froze up again for no apparent reason. Nothing in the logs and I was not using Firefox this time.... Dang it.....

---

### Post by 23dornot23d on 2010-09-07
Ok I may have another try later on from within the live session - because I want to sort out the graphics problems I am having with this latest kernel generic-20.

Cheers for the info

---

### Post by dagrump on 2010-09-07
3dornot
you should try the alt cd if you are planning to install anyway. It isn't fancy, just functional. Live disk is great but the alt. disk "just works".
You should start a different thread or find a related thread for your 3d issues.

---

### Post by 23dornot23d on 2010-09-08
Cheers ..... I wish I had done this before .... whatever happened before when it locked is now giving me a fsync error on my Terra Usb hard drive ......
Just running testdisk on it .... to make sure the structure is ok ..... had to re-write the structure to let the hard drive work ok again
was ages trying to find it and I am sure thats what was making gparted crash out .... as it is ok now .....
Synaptic is locking up ....... now though ...... oh ...... not a good night ........
I just sorted the disk out and tried again from the desktop ..... the exact same thing - it just hangs ,,,,, this is the worst 
installer I have ever come across ..... not sure now to wait ..... to try to exit ...... what it used to do is ask some basic 
questions before it does anything .....
What this did was to run the external drive up and jump back and forth between that and the main drive.

Now it sits there with the exact same screen as I started with ..... no drives going and no way to escape out of it .... 

This is barmy !!!!!   somehow I knew this was not going to be a good night ,,,, 
so is there any advice .... any key presses to safely get out of this ...... or is it the power button ?

Powered it down. ( why is there no information - or is there a way of seeing what is going on here )



Alt CD it is then if I can get the drive back .... after a shutdown again .......

Downloading the Alt CD now to see if it works ok .

---

### Post by 23dornot23d on 2010-09-08
I have an apology to make here ..... after doing a bootchart ...... my systen showed a EXE running at
start up ...... seems that a Windows virus had got onto my machine.

That was what caused the boot disk to not work properly too ..... it now works fine ..... and is the best I have used .

The system is quick and resposive and the boot was 39 secs for me which is good too ........

Just like to thank tje developers and wish them the best of luck for getting this out on the 10th of the 10th

Great work .... [IMG]http://www.liveinternet.ru/images/newsmiles/appl.gif[/IMG]

---

### Post by rburkartjo on 2010-09-12
tons of updates and no new problems that is a good sign.

---

### Post by zenarcher on 2010-09-12
I've been using Kubuntu 10.10 (64 bit) since Alpha 1.  I have to say, while there have been a few minor issues here and there (mainly resolved), this is the first Kubuntu version I've tested which has been without a major borking which required a reinstall.  The few minor issues have been able to be resolved quite easily.  I'm looking forward to a very stable final release.

Cheers,
zenarcher

---

### Post by rburkartjo on 2010-09-22
lots of updates in last two weeks and still no problems

---

