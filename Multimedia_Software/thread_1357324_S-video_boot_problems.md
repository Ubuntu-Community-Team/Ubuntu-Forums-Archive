---
title: "S-video boot problems"
date: 2009-12-17
forum: Multimedia Software
---

### Post by can2002 on 2009-12-17
[FONT="Verdana"]Hi all,

I've been trying to set-up a media PC over the last few days - the idea is that it will connect into a CRT set via S-video and run Mythtv.  The PC has a Radeon X300 video card and I'm building/testing it connected to a Dell monitor with both DVI and S-video connections).  Also, I'm using the 32 bit Karmic desktop version.

Thanks to various other posts I've been able to get the S-video port working using xrandr and I'm at a stage where (with entries in /etc/rc.local & ~/.gnomerc) the machine will automatically switch to S-video and I see my desktop.  I thought I'd hit gold, but as soon as I remove the DVI cable the PC fails to boot successfully.  With the DVI cable disconnected (leaving just an S-video connection), BIOS completes and I then see my Grub menu (I wonder if this in itself is a symptom as it seems to automatically go through Grub with the DVI connected); however if I manually select the 2.6.31-16-generic entry, the screen goes black and the box hangs (no hdd noises, to response to Alt-SysRq, etc.).  To add to this, if I disconnect S-video too, it seems to boot fully (e.g. I can ping the PC from another host).

I'm guessing some part of the graphical boot sequence is causing my problem and I'm hoping that adding a grub boot option will help - I just wondered if anyone else has experienced something similar??

Thanks in advance for any help!

Chris[/FONT]

---

### Post by can2002 on 2009-12-17
Hi,

By chance this evening I discovered that if I leave the machine for long enough, it does actually boot up, it just takes ages to do so.

I've timed a couple of boots and from issuing a reboot command to the completion of init is taking 11 minutes.  In essence I now have a system that behaves as I wanted - it just takes way too long...

Looking in kern.log, there is a slightly odd symptom showing the machine apparently trying to resume from disk:

[FONT="Courier New"]
Dec 17 23:20:05 myth-frontroom kernel: [    6.801863] sd 4:0:0:0: Attached scsi generic sg2 type 0
Dec 17 23:20:05 myth-frontroom kernel: [    6.802052] sd 4:0:0:1: Attached scsi generic sg3 type 0
Dec 17 23:20:05 myth-frontroom kernel: [    6.802242] sd 4:0:0:2: Attached scsi generic sg4 type 0
Dec 17 23:20:05 myth-frontroom kernel: [    6.802424] sd 4:0:0:3: Attached scsi generic sg5 type 0
Dec 17 23:20:05 myth-frontroom kernel: [    6.813197] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Dec 17 23:20:05 myth-frontroom kernel: [    6.839943] sd 4:0:0:3: [sde] Attached SCSI removable disk
Dec 17 23:20:05 myth-frontroom kernel: [    6.851823] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Dec 17 23:20:05 myth-frontroom kernel: [    6.852575] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Dec 17 23:20:05 myth-frontroom kernel: [   12.900519] generic-usb 0003:0547:7000.0004: timeout initializing reports
Dec 17 23:20:05 myth-frontroom kernel: [   12.900678] generic-usb 0003:0547:7000.0004: hiddev97,hidraw3: USB HID v1.10 Device [HID 0
547:7000] on usb-0000:00:1d.7-4.4/input0
Dec 17 23:20:05 myth-frontroom kernel: [   22.908596] generic-usb 0003:0547:7000.0005: timeout initializing reports
Dec 17 23:20:05 myth-frontroom kernel: [   22.908718] input: HID 0547:7000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.4/1-4.4:
1.1/input/input7
Dec 17 23:20:05 myth-frontroom kernel: [   22.908894] generic-usb 0003:0547:7000.0005: input,hidraw4: USB HID v1.10 Device [HID 0547
:7000] on usb-0000:00:1d.7-4.4/input1
Dec 17 23:20:05 myth-frontroom kernel: [   32.920590] generic-usb 0003:0547:7000.0006: timeout initializing reports
Dec 17 23:20:05 myth-frontroom kernel: [   32.920715] input: HID 0547:7000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.4/1-4.4:
1.2/input/input8
Dec 17 23:20:05 myth-frontroom kernel: [   32.920884] generic-usb 0003:0547:7000.0006: input,hidraw5: USB HID v1.10 Device [HID 0547
:7000] on usb-0000:00:1d.7-4.4/input2
Dec 17 23:20:05 myth-frontroom kernel: [  514.595731] PM: Starting manual resume from disk
Dec 17 23:20:05 myth-frontroom kernel: [  514.595737] PM: Resume from partition 8:5
Dec 17 23:20:05 myth-frontroom kernel: [  514.595739] PM: Checking hibernation image.
Dec 17 23:20:05 myth-frontroom kernel: [  514.595917] PM: Resume from disk failed.
Dec 17 23:20:05 myth-frontroom kernel: [  514.615810] EXT4-fs (sda1): barriers enabled
Dec 17 23:20:05 myth-frontroom kernel: [  514.635304] kjournald2 starting: pid 395, dev sda1:8, commit interval 5 seconds
Dec 17 23:20:05 myth-frontroom kernel: [  514.635319] EXT4-fs (sda1): delayed allocation enabled
Dec 17 23:20:05 myth-frontroom kernel: [  514.635324] EXT4-fs: file extents enabled
Dec 17 23:20:05 myth-frontroom kernel: [  514.645817] EXT4-fs: mballoc enabled
Dec 17 23:20:05 myth-frontroom kernel: [  514.645836] EXT4-fs (sda1): mounted filesystem with ordered data mode
Dec 17 23:20:05 myth-frontroom kernel: [  515.287987] type=1505 audit(1261091995.878:2): operation="profile_load" pid=418 name=/usr/
share/gdm/guest-session/Xsession
[/FONT]

Again, any tips would be appreciated!

Chris

---

### Post by Relient_One on 2010-01-02
I'm actually having the exact same issue, VGA = 30second boot, S-Video = 11-12min boot.
 
Bump for suggestion
 
my only idea (and I'm new so bear with me.) is to add into the startup script for mythbuntu to force detect Svideo and enable display to it.
 
I've been looking around for several days and IRC sadly hasn't come to my rescue yet. POST if you find resolution please.

---

### Post by can2002 on 2010-01-02
My apologies - I found a solution in the end and forgot to post!

I changed boot defaults in /etc/default/grub file as follows:

[FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT=""[/FONT]

I've been running the PC connected to my TV only now for a couple of weeks without any problems.  I guess I could put the quiet option back, but I'm happy enough to see the verbose boot messages and so haven't bothered.  Remember to run 'update-grub' after making the change.

Chris

---

### Post by Plankman on 2010-01-08
Hey

Could you possibly post the instruction you used to get S-Video working on boot? I'm struggling a bit with mine. I'm setting up a Mythbuntu box connected to the tv with S-Video. At the moment, everytime I reboot I have to hook up my monitor, enable S-video and then disconnect the monitor.

Thanks :-)

---

### Post by can2002 on 2010-01-08
There are two aspects to this - the first is the slow boot and second being the auto-detection of X settings.

As mentioned in the last post, changing /etc/default/grub fixes the first.

To address the second, I manually placed the following in /etc/X11/xorg.conf:

[INDENT][FONT="Courier New"]
Section "Device"
        Identifier      "radeon"
        Driver          "radeon"
	Busid		"PCI:01:00:00"
	Option		"TVDACLoadDetect" "TRUE"
	Option		"TVStandard" "pal"
	Option		"ForceTVOut" "true"
	Option		"Monitor-S-video"	"TV"
EndSection

Section "Screen"
        Identifier      "TV"
        Device          "radeon"
        Monitor         "TV"
	SubSection "Display"
		Depth	24
		Modes   "800x600"
	EndSubSection
EndSection

Section "Monitor"
        Identifier      "TV"
	Option		"PreferredMode"	"800x600"
        HorizSync       30-70
        VertRefresh     50-75
EndSection[/FONT][/INDENT]

I pieced the above together from various other posts - I'm not saying it's 100% correct but it worked for me.

Cheers,
Chris

---

### Post by mdrake36 on 2010-01-11
this Thread helped me.:D I took for granted that my drivers were correct; since I saw an image on from s-video on boot. This was wrong as my system defaulted to strictly vga drivers and generic hardware drivers in gnome.
 
Once I udated my Nvidia drivers to an old but capable set of drivers; then after alittle tweaking at the menu in the preferences drop down; created was an 
X-config boot file as discribed above. 
I preemptive removed the "quiet splash" from the grub so I can't say wether I neccesarilly need too but now my Video functions work like a charm.
 
I did need to access the root but I am not qualified to recommend any legitimate way to do this; but its all out there. The X-config file requires root privileges to be saved and backed up.
 
Good lookin' out.

---

### Post by ebro173 on 2010-01-29
I just blew up a borrowed Tv.  

I would caution against doing what I just did. I wasn't being too thoughtful I guess or maybe now I wouldn't have a blown up Tv and a glitchy computer.

I was using an Acer Extensa laptop AMD64 ATI Radeon X1250 and Ubuntu 8.04 LTS.  The laptop is (was) dual boot with Windows Vista.

I wanted to stream video from the laptop to the Tv using an S-video cable booted into Ubuntu.  I was able to do this without any fooling around when booted into Windows.  But I would prefer to not use Windows so...

Here's what I did / what I think happened.

First I did some research on the forum and found this and other posts.

Then I made some changes to my xorg.conf file.  Specifically, I added these four lines:

Option "TVDACLoadDetect" "TRUE"
Option "TVStandard" "pal"
Option "ForceTVOut" "true"
Option "Monitor-S-video" "TV"

I put this into the section for the video device which had previously looked like this:

Section "Device"
        Identifier      "Configured Video Device"
    Driver        "fglrx"
EndSection

I put in the four additional lines below the existing line for the fglrx driver.  This much I know I did.  After that I'm not so sure.

I don't remember if I restarted the laptop or not.  I know I had both the laptop and the Tv on. I know the s-video cable was already plugged into the back of the Tv.  I know that next I plugged the s-video cable into the laptop.  I know that I then saw and heard some flashing static and popping.  Then there was electrical smoke and the smell of burning electronics.  My laptop screen went black.

I've now spent a few hours trying to get the laptop back in working order.  The files on the partitions that Ubuntu can access are all apparently still in tact.

I used the Ubuntu recovery mode from the grub menu and ran the tool for automatically fixing the xorg.conf file (is it xfix?).  Now things in Ubuntu look a little different, but happily I still have a functioning computer.  On the other hand, Windows is fried.  I can't boot into it.  The Windows recovery/Startup repair function doesn't work.

---

### Post by ebro173 on 2010-01-29
I've been trying to notice any other damage that the pyrotechnics may have done to the laptop.  It seems that the screen has been affected.  When the mouse pointer is moved all the way to the right edge of the screen it sort of flickers and gets grainy.  Still trying to get the Windows Vista install to boot up.

---

### Post by ebro173 on 2010-01-30
Also, every once in a while, there will be little flickering pixels across the whole screen.

---

### Post by ebro173 on 2010-02-18
I guess I fried the video card of the laptop.  Now, more often than not, the computer is basically unusable because the whole screen flickers, fades and just sort of acts crazy.  All the files on the computer are fine. I'll have to start moving all of them off that computer.  I can't figure out what to do to fix it.  I tried to take the laptop apart and got most of the way there. Then I decided to put it back together without really doing anything.  I had wanted to pull out the video card and try to install a new one.  Well, I think it is an integrated video card so that wouldn't have worked anyway.  I guess the fact that the video card is ruined (I think) means I can't hook the computer up to an external monitor and keep using it...

I have tried rebuilding my xorg.conf using the new open source ATI driver.  That worked fine at first but the flickering etc problems just keep recurring.  Usually, if I let the xfix utility run then it will work a bit better for a while and then it will act up again.

Eh...

---

### Post by drewsus on 2010-05-17
does it work with windows?

---

### Post by ebro173 on 2010-05-18
No. The windows side of that computer was a total bust after this event.  Ubuntu worked for a little while and then the screen flickering got worse and worse so as to render the computer unreliable for regular laptop usage.  I still have it.  It could be used as a server.  But I haven't set it up for that yet.  As it is I can use it by "ssh -X" when it is on and connected to my network.  I started some other threads about trying to get windows working again etc.  No luck.  I got another computer.

---

