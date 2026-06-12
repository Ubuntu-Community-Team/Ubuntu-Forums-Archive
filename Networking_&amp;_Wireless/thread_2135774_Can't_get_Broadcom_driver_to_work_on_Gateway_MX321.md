---
title: "Can't get Broadcom driver to work on Gateway MX3215"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by MontoyaF1 on 2013-04-15
I just installed Kubuntu 12.04 and can't get the Broadcom driver to work (I'm assuming the instructions would be the same as Ubuntu, but if not I can post this question in another forum).  While resolving this, I'm logging in each time by typing b43.blacklist=yes at the GRUB screen, then I use a NetGear air card to connect to the Internet.

So far I have tried this:

> In **Kubuntu**, go to **System -> Additional Drivers** in the Applications menu or press ALT + F2 and type jockey-kde.
  After the Additional Drivers windows opens, select the one that says **Broadcom STA Wireless Drivers** and click on the button below that says Install.



It downloads everything, then at some point it just hangs during installation and I had to shut down my laptop.

Next I followed the offline instructions found [here]("http://linuxforums.org.uk/index.php?topic=5842.msg81040#msg81040"), so I did the following:

> 
From Kubuntu installation disc, I grabbed a copy of ** b43-fwcutter **from pool > main > b >

Downloaded these 2 files (again, I do have Internet through my air card):
[http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)
and
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)


Ran this command:

tar -xjvf broadcom-wl-5.10.56.27.3_mipsel.tar.bz2

I then copied wl_prebuilt.o file to the same folder that my b43-fwcutter tool was sitting in and typed this:
> 
sudo b43-fwcutter -w /lib/firmware wl_prebuilt.o
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo chmod 755 /lib/firmware/b43
sudo chmod 755 /lib/firmware/b43legacy
sudo modprobe -r b43
sudo modprobe b43


Everything seemed to work except the last "modprobe" command.  At this point, the terminal doesn't return to a $ prompt, but rather just sits there, unresponsive, and if I hit <ENTER> it will go down a line each time, and that is about it.

After the "modprobe" failed, I also tried:

> 
sudo modprobe -r b43
sudo modprobe b43legacy

It just sits there too without returning to the $ prompt.  Closing the terminal and rebooting shows that there is no driver installed--wireless still doesn't work.  I also tried the modprobe command with the NetGear air card removed just in case that was somehow interfering (yeah, I'm a noob).

 What the heck?  Why is it that every method I use ends in failure?

---

### Post by spring117 on 2013-04-15
Here's how I solved the BCM4321 issue on my system.

Start a terminal session, run

```
sudo apt-get install bcmwl-kernel-source
```

Exit the terminal, shutdown your computer. After the restart, I had fully working wireless adapter on my 13.04.

Hope it works in your case, too!

---

### Post by MontoyaF1 on 2013-04-19
> **spring117 said:**
> Here's how I solved the BCM4321 issue on my system.

Start a terminal session, run

```
sudo apt-get install bcmwl-kernel-source
```

Exit the terminal, shutdown your computer. After the restart, I had fully working wireless adapter on my 13.04.

Hope it works in your case, too!

That doesn't work either, I get this:

[HR][/HR]> Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 182 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up bcm43xx-fwcutter (1:005-2) ...
--2013-04-19 12:16:13--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
Resolving boredklink.googlepages.com (boredklink.googlepages.com)... 74.125.130.132, 2607:f8b0:4002:c05::84
Connecting to boredklink.googlepages.com (boredklink.googlepages.com)|74.125.130.132|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://sites.google.com/site/boredklink/wl_apsta.o](http://sites.google.com/site/boredklink/wl_apsta.o) [following]
--2013-04-19 12:16:13--  [http://sites.google.com/site/boredklink/wl_apsta.o](http://sites.google.com/site/boredklink/wl_apsta.o)
Resolving sites.google.com (sites.google.com)... 74.125.130.138, 74.125.130.139, 74.125.130.101, ...
Connecting to sites.google.com (sites.google.com)|74.125.130.138|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://sites.google.com/site/boredklink/wl_apsta.o](https://sites.google.com/site/boredklink/wl_apsta.o) [following]
--2013-04-19 12:16:13--  [https://sites.google.com/site/boredklink/wl_apsta.o](https://sites.google.com/site/boredklink/wl_apsta.o)
Connecting to sites.google.com (sites.google.com)|74.125.130.138|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-04-19 12:16:14 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 8
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by MontoyaF1 on 2013-04-21
Anybody else have another idea?

---

### Post by squakie on 2013-04-21
It's been several years now, but I believe that was a laptop I had once.  In those days I had to use ndiswrapper, ndisgtk and the bcmwl5 sys and inf files.  I would normally stay away from ndiswrapper when ever possible now, but this may be a case where it will just make your experience with Ubuntu better, instead of fighting the wireless.  I used to go by userid gcos7, and I believe it was under that id that I had created a how-to for Ubuntu on the mx3215.  While it is for an older version of Ubuntu, the concepts still apply.  I have been able to locate that how-to, so I'll ask a mod if they can find it and then I'll post the link back here for you.  Again, in this case, I really would go with ndiswrapper, ndisgtk and the windows xp driver files (.sys and .inf) - I believe that how-to had a link for getting those.

---

### Post by squakie on 2013-04-21
Here's the link (under a different id):  [http://ubuntuforums.org/showthread.php?t=507505&highlight=ubuntu+pn+gateway+mx3215](http://ubuntuforums.org/showthread.php?t=507505&highlight=ubuntu+pn+gateway+mx3215)

---

### Post by Hadaka on 2013-04-21
Hi, you are loading the sta driver which is also
refered to as a "wl" driver, then you are modprobe-ing
b43..which in a conflicting driver to the wl. let's take a look
at which driver you really need.
please open a terminal ...ctrl/alt/t  then COPY and paste
the following...
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
cat /etc/modules
```
paste the results...thanks.

---

### Post by MontoyaF1 on 2013-04-23
Thanks for everyone's reply so far.  Here are the results I get when I enter those four lines:

> 
**driethme@driethmeMX3215:~$ lspci -nn | egrep '0200|0280'**
00:0e.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
**driethme@driethmeMX3215:~$ lsmod**
Module                  Size  Used by
via                    45249  1 
drm                   197692  2 via
snd_via82xx            37639  1 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      27448  1 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
bnep                   17830  2 
rfcomm                 38139  0 
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
bluetooth             158438  8 bnep,rfcomm
wl                   3032511  1 
snd_pcm                80845  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12937  0 
cfg80211              178679  4 wl,ath5k,ath,mac80211
snd                    62064  9 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core              15040  1 tifm_7xx1
soundcore              14635  1 snd
psmouse                72846  0 
pcmcia                 39791  0 
parport_pc             32114  0 
lib80211               14040  1 wl
serio_raw              13027  0 
i2c_viapro             12969  0 
ppdev                  12849  0 
yenta_socket           27465  0 
snd_page_alloc         14108  3 snd_via82xx,snd_via82xx_modem,snd_pcm
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32325  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
via_rhine              27413  0 
sdhci_pci              18324  0 
pata_via               13428  2 
sdhci                  28241  1 sdhci_pci
video                  19068  0 
**driethme@driethmeMX3215:~$ rfkill list all**
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
**driethme@driethmeMX3215:~$ cat /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
driethme@driethmeMX3215:~$ 


---

### Post by Kopkins on 2013-04-23
According to [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) you should use the b43 module. (you have a BCM4318 based on the output of the commands from your last post.)

Here are [instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29-1") from the Ubuntu documentation, there are easy to follow steps to get your wireless up and running. 

You'll probably want to add 'b43' to your /etc/modules file. That way it's ready to go each time you boot. 

Good luck,

Kopkins

---

### Post by Hadaka on 2013-04-24
Hi, sorry i am so late getting back to you...
from a wired connection
please do..
```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43

```
*Edit:do you not have a wired connection?
        if you do NOT,we "may" have to use a
        different method.
thanks

---

### Post by Kopkins on 2013-04-24
> **Hadaka said:**
> Hi, sorry i am so late getting back to you...
from a wired connection
please do..
```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43

```
*Edit:do you not have a wired connection?
        if you do NOT,we "may" have to use a
        different method.
thanks

He has an external wireless Netgear thing.

---

### Post by Hadaka on 2013-04-24
Hi, Let's do this the easy way.
since you have no "hardwire" and only the air card.
we can load it with no internet connection...*After
you click the b-43 zip file and drop it on your Desktop.
Instrutions.
grab the zip file..place on Desktop
click on network icon and uncheck Enable Wireless.
(this will stop your air card)
at this point you will have no internet access...which
is what we want.
then please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then at the Desktop zip file...*right click and chose..extract here.
then..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
lastly..once again click the wireless network icon...and *check Enable wireless.
you should now have the internal wireless card working with NO aircard.[ATTACH=CONFIG]241713[/ATTACH]

---

### Post by MontoyaF1 on 2013-04-24
> **Hadaka said:**
> Hi, Let's do this the easy way.
since you have no "hardwire" and only the air card.
we can load it with no internet connection...*After
you click the b-43 zip file and drop it on your Desktop.
Instrutions.
grab the zip file..place on Desktop
click on network icon and uncheck Enable Wireless.
(this will stop your air card)
at this point you will have no internet access...which
is what we want.
then please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then at the Desktop zip file...*right click and chose..extract here.
then..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
lastly..once again click the wireless network icon...and *check Enable wireless.
you should now have the internal wireless card working with NO aircard.[ATTACH=CONFIG]241713[/ATTACH]

Thanks for the quick response.  Okay, here is what I did.  I downloaded the b43.zip file as you directed, and then extracted it to my desktop.  

I disconnected my Internet (I even removed the air card), then typed this:

> driethme@driethmeMX3215:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for driethme: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 192 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bcm43xx-fwcutter (1:005-2) ...
--2013-04-24 15:11:33--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
Resolving boredklink.googlepages.com (boredklink.googlepages.com)... failed: Name or service not known.
wget: unable to resolve host address `boredklink.googlepages.com'
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

I created the directory using the command you gave (actually, it was already there, so I blew it away and started from scratch):

> sudo mkdir /lib/firmware/b43

I then changed directories to be in the /b43 folder on my destop and then typed:
> sudo cp * /lib/firmware/b43


All the files should be there, but just to prove it, here is what it looks like:

> 
driethme@driethmeMX3215:~$ cd /lib/firmware/b43
driethme@driethmeMX3215:/lib/firmware/b43$ ls
a0g0bsinitvals5.fw   a0g1initvals13.fw    b0g0initvals5.fw    lp0initvals15.fw    ucode14.fw
a0g0bsinitvals9.fw   a0g1initvals5.fw     b0g0initvals9.fw    n0absinitvals11.fw  ucode15.fw
a0g0initvals5.fw     a0g1initvals9.fw     lp0bsinitvals13.fw  n0bsinitvals11.fw   ucode5.fw
a0g0initvals9.fw     b0g0bsinitvals13.fw  lp0bsinitvals14.fw  n0initvals11.fw     ucode9.fw
a0g1bsinitvals13.fw  b0g0bsinitvals5.fw   lp0bsinitvals15.fw  pcm5.fw
a0g1bsinitvals5.fw   b0g0bsinitvals9.fw   lp0initvals13.fw    ucode11.fw
a0g1bsinitvals9.fw   b0g0initvals13.fw    lp0initvals14.fw    ucode13.fw
driethme@driethmeMX3215:/lib/firmware/b43$ 


I then typed this:

> 
driethme@driethmeMX3215:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
driethme@driethmeMX3215:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': Device or resource busy

What did I do wrong?  Does it have anything to do with the earlier error of "dpkg: error processing bcm43xx-fwcutter (--configure):"??? I get that error at the end of anything I try to do in Kubuntu.  Thanks for everyone's help!

---

### Post by Hadaka on 2013-04-24
Hi, i have no idea where this is comming from
wget: unable to resolve host address `boredklink.googlepages.com'
I can only guess you went to one or more "help" files on the internet
and attempted to load a fix. If you are not running dual boot with windows
it would probably take less time to just reload 12.04 as you have this
pretty well tangeled up and it would take much longer to figure out
just exactly what is hosed.
While loading the updates and upgrades via wireless is not always
a good idea,you are pretty much stuck doing that with your aircard.
so i would reload 12.04 and NOT load any wireless drivers, but do the
updates and upgrades. then load the b43 from the zip file and all should
be well. after you reload the os do.
```
sudo apt-get update
sudo apt-get upgrade
```
remove the aircard and load the b43 per above instructions.

---

### Post by MontoyaF1 on 2013-04-26
Thanks.  I'll try that this weekend.

---

### Post by MontoyaF1 on 2013-04-28
OK.  I'm back.  I reinstalled Kubuntu 12.04, leaving the button unchecked for loading 3rd party software, I logged back in, at the Grub screen I put b43.blacklist=yes in order to allow my desktop to load.

I took my copy of b43.zip that I had on a thumb drive, put it in Documents/b43, extracted it, disabled my wi-fi (aircard) then did the following:

> driethme@driethme:~$ **sudo apt-get remove --purge bcmwl-kernel-source**[sudo] password for driethme: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
driethme@driethme:~$ 


driethme@driethme:~$ **sudo cp Documents/b43/b43/* /lib/firmware/b43**
[sudo] password for driethme: 
driethme@driethme:~$ **cd /lib/firmware/b43**
driethme@driethme:/lib/firmware/b43$ **ls**
a0g0bsinitvals5.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw     n0bsinitvals11.fw   ucode9.fw
driethme@driethme:/lib/firmware/b43$ **sudo rmmod -f b43**
ERROR: Removing 'b43': No such file or directory
driethme@driethme:/lib/firmware/b43$** sudo rmmod -f ssb**
driethme@driethme:/lib/firmware/b43$ **sudo modprobe b43**
FATAL: Error inserting b43 (/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
driethme@driethme:/lib/firmware/b43$ 

I tried re-enabling my wi-fi with the aircard ejected, but it didn't work.

---

### Post by Hadaka on 2013-04-28
Hi, ok you are in better shape than you were,
remove the b43 from the blacklist and try to
load the driver again. You may also have to
temp. insert the aircard to do ...
```
sudo apt-get upgrade
sudo apt-get update
```
prior to loading the zip files so that the ucodes
will load correctly.

---

### Post by MontoyaF1 on 2013-04-30
Actually, I booted up last night without blacklisting b43, and wireless began working immediately.  Thank you so much!

Now my only issue is that the sound doesn't work.  When I had Ubuntu I had to go into AlsaMixer to uncheck some radio button for the speaker in order to get it to work each time, but I don't see anything like that in Kubuntu.

---

### Post by Kopkins on 2013-04-30
Try in terminal ```
alsamixer
``` from there you should be able to adjust volume levels and unmute channels.

---

### Post by Hadaka on 2013-04-30
Hi, glad you got it working, hopefully you did
```
sudo apt-get upgrade
sudo apt-get update
```
Im not a lubuntu user so i have nothing to input
on your sound problem. I would suggest you mark
this thread SOLVED as it was posted for a wireless
problem and then start a new thread in  the beginner
section for sound problems.
glad to hear you are up and running.

---

### Post by MontoyaF1 on 2013-04-30
> **Hadaka said:**
> Hi, glad you got it working, hopefully you did
```
sudo apt-get upgrade
sudo apt-get update
```
Im not a lubuntu user so i have nothing to input
on your sound problem. I would suggest you mark
this thread SOLVED as it was posted for a wireless
problem and then start a new thread in  the beginner
section for sound problems.
glad to hear you are up and running.

I would flag it as SOLVED if I could find a button somewhere on the page to do that.  Maybe I need to start another thread with that question.:P

Thanks again everybody that contributed!!!

---

### Post by Hadaka on 2013-04-30
Hi, to mark it solved..sign back in, click your thread
click advance edit, ,then where it says  "Kubuntu"
hit the down arrow and choose..SOLVED.
thanks.

---

### Post by MontoyaF1 on 2013-05-01
Thanks again for your help.  While logged in, there is no "Advance Edit" to click on.  When I look in "Thread Tools," it only gives me three options, none of which are to mark it as solved:

[LIST]
[*] 				[h=6]Thread Tools[/h]
[LIST]
[*][Show Printable Version]("http://ubuntuforums.org/printthread.php?t=2135774&pp=10&page=3")
[*][Email this Page&#8230;]("http://ubuntuforums.org/sendmessage.php?do=sendtofriend&t=2135774")
[*] 						 							[Subscribe to this Thread&#8230;]("http://ubuntuforums.org/subscription.php?do=addsubscription&t=2135774")
[/LIST]
 			
[/LIST]

---

### Post by Hadaka on 2013-05-01
try this
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[http://ubuntuforums.org/showthread.php?t=2141082&p=12628674#post12628674](http://ubuntuforums.org/showthread.php?t=2141082&p=12628674#post12628674)

---

### Post by MontoyaF1 on 2013-05-02
Sorry.  When I follow those instructions I don't have a Prefix field in which to choose "SOLVED."  I only have a free form field for the reason for the editing (and yes, I'm doing this from the first post, not my subsequent replies).

I'm starting to think that Unbuntuforums.org is intentionally made difficult to use in order to weed out those novices that might try Ubuntu.

---

### Post by Hadaka on 2013-05-02
Hi, It's just because you have not done this before,
you are about to become an expert at marking a thread
SOLVED.
click the first red link in post #24
it has pictures and everything ;)
then..follow the yellow brick road.
the [prefix] field you refered to currently
has [Kubuntu] in it. because when you started this thread
you actully chose it...sooo...that is the PREFIX field.
click the down arrow on that and ...viola! you will see
SOLVED.

easy huh?
This is all about getting your mind to purge any bad windows
habits and think logically for linux....:p
good luck...

---

### Post by MontoyaF1 on 2013-05-07
Dude, I swear that I didn't have that field before, but I found it now.
:)

Thanks again for all of your help.

---

