---
title: "Tvtuner"
date: 2012-12-09
forum: Multimedia Software
---

### Post by msk61 on 2012-12-09
Hi, My tvtuner card Winfast Dvt2000ds plus, is not reconized in Ubuntu 12.04.
In mythtv setup, When I select DVB DVT capture card (v3.x), my card should show up on the next line, but there is nothing there.
It also dosn't show up in TvTime or MeTv.
The card works fine in Windows8.
Thanks Shane.

---

### Post by sparx66 on 2012-12-11
Total Ubuntu noob, looked like fun to build a HTPC with Mythbuntu so why not. Followed the whirlpool buildlist to make it. Umbuntu runs great but I can't see the DTV2000DS Plus card. Any suggestions?:popcorn:

---

### Post by sparx66 on 2012-12-15
Hi there, did you find anything out?
I've found the card details using 
lsusb -v 

Can't see any details on the net as to how to fix it other that to write your own driver or ask some else to do it. 

I'm going load winxp to check that the card works. 
probably stay with that if theres no fix on the forums.
A bit disappointed.

---

### Post by haqking on 2012-12-15
[http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS#Making_it_work_in_Ubuntu](http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS#Making_it_work_in_Ubuntu)

---

### Post by sparx66 on 2012-12-15
Hi there,
Thanks for that. I had found it before but the model is bit different anyway it's worth a try.

I've loaded the .zip file on the desk top.
And run both files.

still a problem- see below.

thanks 
Phil

---

### Post by chadk5utc on 2012-12-15
sudo chmod +x install.sh
sudo ./install.sh

---

### Post by BicyclerBoy on 2012-12-15
The OP & sparx66 probably just need the firmware package..
Try that before making a mess of v4l etc..

sudo apt-get install linux-firmware-nonfree

then reboot (easiest for noobs) & then spool thru the output of: 
dmesg
for signs of life..

---

### Post by sparx66 on 2012-12-15
Hey thanks for all the help.
Managed to load ruby-gnome2.

But when I run ./tvconfig it can't find some of the files.

as per:

phil@phil-desktop:~/Desktop/tvconfig-master$ ./tvconfig
	Running Leadtek script
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
fatal: destination path 'v4l-utils' already exists and is not an empty directory.
sh: 1: autoreconf: not found
sh: 1: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
cp: cannot stat `ir-keytable': No such file or directory
cp: omitting directory `rc_keymaps'
phil@phil-desktop:~/Desktop/tvconfig-master$ 

I checked and the directory /dev/dvd doesn't exist.

Also ran sudo apt-get install linux-firmware-nonfree.

restarted etc.

Learning lots but no tuner card yet.

any suggestions?

Phil

---

### Post by BicyclerBoy on 2012-12-15
Good idea to search thru' logs about dvb & firmware etc.

Note that most of that LInuxTV.org page is old & relates to kernels from 10.04 etc..The v4l-dvb in later releases should just work.

dmesg | grep -i dvb
dmesg | grep -i af90
dmesg | greb -i leadtek

---

### Post by sparx66 on 2012-12-15
Thanks again

So one problem seems to be that directory

/dev/dvb 

never gets created or of course populated.

I've got:

/usr/share/dvb/dvb-t/

but without /dev/dvb there's no:
/dev/dvb/adapter0/frontend0
or
/dev/dvb/adapter0/demux0

I've just done a full reinstall of mythbuntu 12.04 from the ISO DVD but no DVB devices appear.

Any suggestions?

---

### Post by sparx66 on 2012-12-16
Ok so did some more reading.
Looks like the change from DTV2000Ds to DTV2000DS Plus is a big change, they use completely different drivers.
ref ([http://www.leadtek.com/eng/support/download.aspx#id=driver](http://www.leadtek.com/eng/support/download.aspx#id=driver))

So without a driver I'm toast.
(and I have confirmed that the /dev/dvb/ directory won't be created if there's no recognized card.)

So I'll try to swap the card with the supplier with a different model.


Phil
QLD, Australia.

---

### Post by sparx66 on 2012-12-16
Ok so did some more reading.
Looks like the change from DTV2000Ds to DTV2000DS Plus is a big change, they use completely different drivers.
ref ([http://www.leadtek.com/eng/support/d...aspx#id=driver](http://www.leadtek.com/eng/support/d...aspx#id=driver))

So without a driver I'm toast.
(and I have confirmed that the /dev/dvb/ directory won't be created if there's no recognized card.)

So I'll try to swap the card with the supplier with a different model.


Phil
QLD, Australia.

---

### Post by BicyclerBoy on 2012-12-16
Just because Leadtek uses different windows drivers for each model does not mean the h/w is that different.
They might be adding some other functionality & do not want to "enable" old h/w & thereby reduce sales etc.

You can't draw any conclusions from the existence of /dev/dvb folders.
If you do want to find the root cause you need to run the cmds I posted previous.

Almost none of the very few vendor supplied dvb-tunercard drivers work well or can be built against any kernel version.

---

### Post by sparx66 on 2012-12-17
Yep there's nothing in dmesg about the DVB stuff that I can find. 

I've decided to buy a Sony PS3 Play Tv which I am told "just works".

We'll see.

---

