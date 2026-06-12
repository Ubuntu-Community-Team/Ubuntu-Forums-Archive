---
title: "No tv on mythtv"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by fkrogh on 2008-04-06
I'm losing the war with mythtv. In desperation I've upgraded to the Hardy beta,
so of course some of my problems may be there.  What I have:

1. Hauppauge WinTV-PVR-500 PCI card with remote. lspci shows among
other things (I don't know if Pericom is significant, but given the
ordering it seems likely.)

01:06.0 PCI bridge: Pericom Semiconductor Unknown device 8140
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

lsusb shows (in addition to the mouse)

Bus 001 Device 003: ID 1784:0001  

which I believe means the the remote IR device is seen.

2. The motherboard is a Biostar TF7050-M2 with Nvidia graphics on
board which I am using.  The processor is a dual core amd64, but
running in 32 bit mode.  I have the tv out S-video from the on board
graphics connected to my tv, but no signal ever seems to get to the
TV set.

What I've "achieved"

3. Configuration seems to see channels when it is doing the scan.

4. I have managed to get the back end started.  Evidently I had to add
"append = noapic nosmp" into /boot/grub/menu.1st in order to get this far.

5. When running irw it never sees anything from the remote.  If I do
sudo /etc/init.d/lirc stop, and then sudo lircd /dev/lircd
/dev/lirc0 then the command doesn't seem to complete, but pushing
any button on the remote gives me a new prompt which at least implies
that part of the remote is working.

What is not working.

6. If I use the Watch TV option from running the mythtv front end,
the screen just goes blank briefly and then displays the menu again.

I've been through a lot of forums, and some have been helpful (see 4
above) none seems to get me far enough to actually see a tv
program. I'm not a newbie in the sense that I've been a heavy computer
user since 1959 (coding in hex to start, but mostly in Fortran with a
bit of C thrown in), and have been running Gentoo for about 4 years
and Redhat for perhaps 6 years prior to that.  Clearly I'm missing
something significant here.

Any suggestions that might help illuminate anything would be much
appreciated.  Thanks and apologies for being so verbose,
Fred

P.S. Perhaps some Hardy weirdness.  As a result of one suggestion, I
added my typical user to the users group by editing /etc/group.
That didn't seem to work quite right, and so I tried going through
the system administration business.  In that case it doesn't get
around to asking for a password, and does not allow for any changes
to be made in anything, except make changes to my name.  After doing
that it asks for the password, allows the name change, but doesn't
allow any other changes.  I'll file a bug report if anyone else is seeing the same problem.

---

### Post by blcvegas on 2008-04-07
It sounds like you're using S-video for your input.  Is that the only input to you Hauppauge card?  If you want to scan for channels, you need an analog CATV signal input to your card or an external off-air antenna.

What video sources do you have setup in the backend?

I wouldn't try to setup the remote until you get everything else going.

---

### Post by Scorpuk on 2008-04-08
Not in any particular order. :-)

5. 

Something I noticed was this:

> sudo lircd /dev/lircd /dev/lirc0 


For mine I type

```
sudo lircd -d /dev/lirc0
```


-d tells lircd to use the device in the command line, in my case /dev/lirc0.


2.

TV out.

How is this connected to your TV set? 

As in does your TV have an S-Video connector or have you converted this to scart / rca phono?

Also if you have converted it does the AV channel you have connected it support S-Video.

For mine I used an S-Video to scart adaptor, but still needed to select AV2S on the TV.

One last thing. When you boot up the computer with the TV connected and powered up does anything appear on the TV? ie motherboard splash screen...


I'll look at the rest later. lunch break over :(

---

### Post by Chuckels550 on 2008-04-08
Why not re-install just using the Mythbuntu iso install?  See [www.mythbuntu.org](www.mythbuntu.org).  I couldn't get MythTV to work using Gutsy Gibbon, either.

---

### Post by fkrogh on 2008-04-12
My apologies for not replying sooner.  I was expected mail if replies were posted.  An update to my preferences should have fixed that.

Thanks for the responses.  I don't know why I didn't to it sooner, but looking in mythbackend.log showed the problem.  When I installed Ubuntu for some reason /dev/sdb1 was installed with a vfat file system.  And I just didn't change it.  That file system did not allow writing to it.  After formatting this with an xfs file system, and changing permissions, I now get TV, unfortunately all I get is static and if I switch the TV to look at the S-Video input, it reports that there is no signal..
(I'm just getting started on trying to figure out what might be the problem here..)

In response to previous postings.

My card is connected with Coax from the cable company.  The input is set to tuner as none of the other choices seemed to apply.

From the PC to the TV I'm using S-video for the video connection.  The TV has an S-Video in and the the motherboard provides for an S-video out.

Concerning the remote control, still no luck using irw.   htop shows for lircd

/usr/sbin/lircd --driver=devinput --device=/dev/lirc0 --output=/dev/lircd --listen

/usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd1 --connect=localhost 8765  --pidfile=/var/run/lircd1.pid

I'm not really clear on why there are two of these, but the first seem necessary and killing the second did not help.

Following advice given, I'm going to go back to working the tv part.  Once again, any suggestions welcome, and I will get to them a little faster.  Thanks,
Fred

---

### Post by fkrogh on 2008-04-12
After some time and a reboot, I now get a tv picture with no other changes.  Now if I only had sound and could change channels, I'd feel like maybe this could be useful.

---

