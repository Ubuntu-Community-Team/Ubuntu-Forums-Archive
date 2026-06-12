---
title: "UK noobie cannot set up MythTV - urgent help please."
date: 2011-06-20
forum: Mythbuntu
---

### Post by elsmandino on 2011-06-20
Hi there,

I am trying to set up Mythbuntu (both frontend and backend on the same computer). Specs are as follows:

*Athlon II X2 240e
*Asus M4A785TD-M Evo
*Antec NSK2480 - with the 380w PSU
*4GB Corsair Ram
*1.5TB AV-GP Hard Drive (Recording), 2TB F4 Sasmung (Storage), Samsung F7 Laptop Drive 500GB(Time Shifting and OS)
*Hauppauge HVR-2200
*Haupauge Nova-HD S2

I have installed the programme but am having no luck at all in setting up the tuner cards or getting EPG information. The two above cards are a dual Freeview Card and a single Freesat card - are these both definitely supported?

Are there any absolute beginner guides to help me our or could someone perhaps give me a really basic walkthrough to getting things up and running? I have used quite a few Media Centres in the past (MCE, Medaportal, GBPVR) but I am having absolutely no luck with this one - really frustrating as I wanted to try and get away from Windows.

Any help would be really appreciated.

Thanks

---

### Post by ktmom on 2011-06-20
Which mythbuntu version are you installing?  I am certain the HVR-2200 will work although a quick search found this [thread]("http://ubuntuforums.org/showthread.php?t=1537727&highlight=Hauppauge+HVR-2200").  The 2250 is it's brother and what I use.  Under mythbuntu 10.04 upgraded to mythtv .24 fixes I didn't have to install any drivers for my 2250.

The mythbuntu wiki has an [installation guide]("http://www.mythbuntu.org/wiki/installation-guide"), have you seen this?

Beyond those comments, could you be specific as to what happens when you do what.  It's easier to figure out what to try next if we know what you've already tried.

---

### Post by elsmandino on 2011-06-21
Hi there - thanks for your reply.  This is driving me mad.

I am using the 32-bit of mythbuntu 11.04.

When I go to the Capture Card Setup, I get to the heading DVB DTV capture card (v3.x), the Frontend ID says Contexant CX24116/CX24118 Subtype: DVB-S2 (my Freesat Card).

I can add this card apparently without problem as /dev/dvb/adapter0/frontend0.

I then go back to add my two Freeview cards I go back to the (v3.x) heading and it has "dev/dvb/adaptero/frontend0--Warning: already in use.

I assume this means that I need to assign a new name for the next card but I have no idea how.

Hopefully this makes some sense and thanks again.

---

### Post by Maheriano on 2011-06-21
Be careful you're adding the right chip in the card. Some cards have ATSC, NTSC and QTSC (or whatever that is called) and I'm pretty sure you have to add each one individually. So if you add ATSC and are scanning for a NTSC feed, it won't work.

---

### Post by nickrout on 2011-06-22
> **elsmandino said:**
> Hi there - thanks for your reply.  This is driving me mad.

I am using the 32-bit of mythbuntu 11.04.

When I go to the Capture Card Setup, I get to the heading DVB DTV capture card (v3.x), the Frontend ID says Contexant CX24116/CX24118 Subtype: DVB-S2 (my Freesat Card).

I can add this card apparently without problem as /dev/dvb/adapter0/frontend0.

I then go back to add my two Freeview cards I go back to the (v3.x) heading and it has "dev/dvb/adaptero/frontend0--Warning: already in use.

I assume this means that I need to assign a new name for the next card but I have no idea how.

Hopefully this makes some sense and thanks again.

change adaptor0 to adaptor1. Use the right arrow key in that field to change it.

---

### Post by elsmandino on 2011-06-22
I think I see the problem - on the Capture Card Setup page, when I go to DVB DTV Capture Card (v3.x), there should be a box underneath saying DVB Card Number.  I don't have this and I think this probably means that the HVR-2200 isn't in fact being recognised by my computer.

I would be really grateful for a walkthrough on how to install the drivers for this card (remember - I am an absolute beginner to Linux at the moment).

Thanks

---

### Post by bance on 2011-06-22
A search for your card in the box (Top right of this page )

Yielded [this]("http://ubuntuforums.org/showthread.php?t=1537727&highlight=Hauppauge+HVR-2200"), 30 secs! (0.023 Secs)

HTH Steve

---

### Post by elsmandino on 2011-06-22
Hi there - the thanks very much for that.  The problem is following these instructions:



[B][SIZE="1"]I figured it out. I needed to install the latest drivers, like so:
Upgrading drivers

$ hg clone [http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)


$ make menuconfig
$ perl -p -i -e 's/FIREDTV=m/FIREDTV=n/' v4l/.config
$ edit as needed but should have all enabled that is needed

$ sudo make CONFIG_DVB_FIREDTV:=n || return
$ sudo make install
$ sudo reboot


Upgrading firmware to the files in:


Download new firmware from

[http://www.steventoth.net/linux/hvr2...wares/4038864/](http://www.steventoth.net/linux/hvr2...wares/4038864/)


Now copy that into the kernel firmware dir.

sudo cp *fw /lib/firmware/`uname -r`[/SIZE]
[/B]



I am totally unfamiliar with Ubuntu, thus have no idea what I should be doing - at a guess:

Would I open the terminal and literally type the following:


[B][SIZE="1"]$ hg clone [http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)


$ make menuconfig
$ perl -p -i -e 's/FIREDTV=m/FIREDTV=n/' v4l/.config
$ edit as needed but should have all enabled that is needed

$ sudo make CONFIG_DVB_FIREDTV:=n || return
$ sudo make install
$ sudo reboot
[/SIZE]
[/B]
After the machine has rebooted, do I then just typ, in a new terminal:


**[SIZE="1"]sudo cp *fw /lib/firmware/`uname -r`[/SIZE]?**



Sorry if this is really basic textbook stuff.

Thanks again.

---

### Post by PhilWig on 2011-06-22
I use a Hauppauge T500 in the UK so cannot really help with your specific query but will make two comments:

1.  I found Garry Parker's pages very helpful - google 'Garry Parker Mythtv'. He is UK based and has advice on both DVB-T and satellite. 

2.  The T500 needs microcode to be loaded onto the card and I fully expect your card is the same.  I find that code is only re-loaded after a cold boot - ie power off, pull the mains plug for a few seconds or turn power off on the PSU then re-power.    I need to do this for such changes as turning on the T500 internal amplifier or (strangely) a switch from VGA to HDMI.  You will certainly need to do it after driver changes.

Best wishes.
Phil

---

### Post by bance on 2011-06-22
Maybe first, open a terminal, and type (copy and paste..... saves typo's..... just remember the $ is a prompt so don't copy that.):-

```
lspci -vv
```Read through the output and see if your card is recognised, if it is there, then try:-

```
dmesg|grep 'firmware'
```This might give you a clue as to whether you have the firmware or if there is problems loading it.

If your card is recognised, you can probably skip the first part of the solution, and just get the firmware if you need it.

If not you will have to follow the entire solution....

First install mercurial... from synaptic or:-

```
apt-get install mercurial libncurses5-dev
```Then change directories:-

```
cd saa7164-stable
```Then begin the solution

Also after this line ( $ perl -p -i -e 's/FIREDTV=m/FIREDTV=n/' v4l/.config*.*) Where it says "edit as needed" escape or tab through to the finish... it should tell you which is correct!

Then continue with the rest of the solution.

---

