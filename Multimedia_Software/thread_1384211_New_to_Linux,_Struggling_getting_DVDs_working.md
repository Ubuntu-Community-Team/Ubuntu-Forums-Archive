---
title: "New to Linux, Struggling getting DVDs working?"
date: 2010-01-18
forum: Multimedia Software
---

### Post by DMRider_10 on 2010-01-18
Hi, this is my first post so go easy!

Id consider myself an advanced PC/windows user, but have recently installed Ubuntu 9.10 on my laptop due to Vista being toss.

Its all working nicely, and im getting my head round installing things using the terminal etc. BUT ive come unstuck trying to get DVDs working. 

Ive started by following the multimedia sticky at the top of this page, I get through the first two stages ok and do:

[B]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[/B]and


[B]wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
[/B]
Without errors[B].

[/B]Then when I come to the** Installation **section and try:

[B]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar


[/B]I get the error: [B]

E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]Which is not on the list of errors given in the guide?

Please can anyone help me out as so far my Ubuntu experience has been a pleasant one and I dont want it to go sour now!

Thanks

---

### Post by 73ckn797 on 2010-01-18
Did you look here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the instructions?

You should only need to follow the "**Adding the Medibuntu Repositories**" section using terminal, 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then "[SIZE=2][B]Playing Encrypted DVDs"
[/B][/SIZE]```
sudo apt-get install libdvdcss2
```Then (choose the one for either 32 bit or 64 bit Uuntu):

```
sudo apt-get install w32codecs
```Works everytime!

---

### Post by DMRider_10 on 2010-01-18
I fall at the first hurdle.

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


Gives me

**E: Sub-process /usr/bin/dpkg returned an error code (1)**


??????

---

### Post by SlugSlug on 2010-01-18
try 

sudo apt-get -f install


and start again

---

### Post by DMRider_10 on 2010-01-18
Running:


sudo apt-get -f install

Brings up the same error?

---

### Post by lyall on 2010-01-18
are you running 32 or 64 bit OS

if you are using the 64 bit OS install the 64 bit apps for the 
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

please check which you are using.


good luck and have fun learning

---

### Post by DMRider_10 on 2010-01-18
**CPU**Intel Pentium Dual-Core T2370 (1.73GHz) [B]
BIOS[/B]Phoenix BIOS.  Press F2 to enter [B]
Chipset[/B]SiS M672MX 
**Memory**2GB DDR2 PC2-5300 (1 Memory Slot.  Max 2GB)
**Hard Drive**120GB Western Digital WD1200BEVS-22UST0-(S1) SATA [B]
CD Drive[/B]DVD±RW [B]
Screen[/B]15.4" Widescreen TFT (1280x800)
**Video Card**SIS Mirage3 integrated graphics (256MB shared) [B]
Sound Card[/B]Realtek High Definition Audio [B]
Modem[/B]Not installed * [B]
Network Card[/B]SiS191 Ethernet Controller
LiteOn WN6301L Wireless LAN ** 
**Ports**4x USB 2.0
1x Headphone
1x Microphone
1x 4-in-1 Card Reader (supports SD, MMC, MS, MS-Pro cards)
1x Kensington Lock
1x LAN
1x VGA




Thats the lappy spec which im 99% sure makes it a 32 bit?

---

### Post by alejaaandro on 2010-01-18
from [http://processorfinder.intel.com/details.aspx?sSpec=SLA4J](http://processorfinder.intel.com/details.aspx?sSpec=SLA4J)

Supported Features:
Dual Core
Enhanced Intel Speedstep® Technology
**Intel® EM64T 1**
Execute Disable Bit 2

are you sure it's 32 bit? i think EM64T is intels' name for 64 bit

---

### Post by DMRider_10 on 2010-01-18
Ah maybe so then?

So how can I get myself to square one then so I can start afresh?

---

### Post by alejaaandro on 2010-01-18
run 
> uname -m

this tells you on what platform your kernel thinks it's running..
if you actually have a 64bit processor, i don't THINK (please somebody correct if wrong) you can "upgrade" to a 64bit ubuntu. You must reinstall the correct version..
But there might still be a fix for you problem even without installing 64bit ubuntu, though i can't help you with that..

---

### Post by DMRider_10 on 2010-01-18
i686?

---

### Post by Yellow Pasque on 2010-01-18
Ok, you're running 32-bit. There's no issue there. Try to get a more specific error message. Look at the end of /var/log/dpkg.log

---

### Post by DMRider_10 on 2010-01-18
Do you mean type:

/var/log/dpkg.log

Into the terminal? 

I get command not found if I do?

---

### Post by alejaaandro on 2010-01-18
nope..
/var/log/dpkg.log is a file.. he means you should look for some info in that file that might help you figure out what you problem is..
in linux, almost everything that happens (either you do it or it's done automatically by the system) is logged to some file.. this way you can find out what happens and troubleshoot if something goes wrong or doesn't work..

if you wanna use the terminal write 
> cat /var/log/dpkg.log


if you prefer a gui, use any text editor (gedit is the default in gnome) to open that file and see if you can find something regarding your problem

---

### Post by DMRider_10 on 2010-01-20
I dont want to piss anyone off by pasting this, so if I shouldnt be doing it, please someone let me know. Looking at the log though, I dont have a clue what Im looking for. As I say, up to now this is the first problem ive come across, and the fault finding procedure is so different to windows that IM struggling! If someone wouldnt mind taking a look..........

---

### Post by Yellow Pasque on 2010-01-20
Your post is unreadable. Edit it and clear it out. Try attaching the log as a text file...

---

### Post by DMRider_10 on 2010-01-20
Sorry. To me it just comes up as it does in terminal?

---

### Post by DMRider_10 on 2010-01-20
[ATTACH]144233[/ATTACH]

Hope that works?

---

### Post by DMRider_10 on 2010-01-20
OK I dont seem to be able to install anything?! I just tried to install VLC and also a mini golf game, all from the software store and both failed? Get to like 50% and then an error box comes up saying packed couldnt be added/removed etc??? Related?

---

### Post by epicoder on 2010-01-20
[I]Deleted by sh228
[/I]

---

### Post by DMRider_10 on 2010-01-20
Ok problem solved. 

I reinstalled 9.10, did the process described on the first page of this thread, and totem STILL was giving me the No URI error. 

BUT, I dont know what was I had corrupted before, but now I could install packages. Installed VLC player and now DVDs work a treat!

Thanks for the help!

---

### Post by SlugSlug on 2010-01-20
wonder if it was your hard drives free space

you can always check that with 

```
df -h
```

---

### Post by DMRider_10 on 2010-01-20
You mean as in not enough free space?

It was a fresh 9.10 install with nothing else loaded onto the (120bg) HDD, so I doubt it! lol

Now I have a problem if I try to adjust the volume using FN+F5 or F6 (up or down) using the keyboard? The volume slider goes all whacky and is stuck on the screen?

---

### Post by SlugSlug on 2010-01-20
> **DMRider_10 said:**
> You mean as in not enough free space?

It was a fresh 9.10 install with nothing else loaded onto the (120bg) HDD, so I doubt it! lol


The auto partition option druing install has been known to allocate a small /

---

