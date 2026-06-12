---
title: "Installing Hauppauge HVR-1600. Need help"
date: 2009-06-20
forum: Multimedia Software
---

### Post by RGPerson on 2009-06-20
Well, it's been awhile since I really tried to *work* in Linux. Mostly just watched TV and checked e-mails. So, anyway, we bought a Hauppauge HVR-1600 tv tuner card. It says there is Linux support.

Took awhile to figure out the whole driver install.  (Gotta admit, Windows makes that so much easier.)

I downloaded the driver from linuxtv.org

I used the commands from [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

(Starting with downloading the latest driver.  We don't have Mythtv up and working yet, so I skipped that part.)

I did these commands

 cd v4l-dvb 
 make 
 sudo make install
 sudo make unload
 sudo modprobe cx18

Seemed to go fine there.  Then I followed the next instruction:

> Tip: Type in the next line. If the output matches, this section can probably be skipped. 

dmesg | grep "cx18.*loaded"
[   23.555603] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.227119] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   25.651060] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

I typed it in, but nothing came back, so I went on to the next session and didn't skip it.

wget [http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz)
tar -xzvf cx18-firmware.tar.gz
sudo cp cx18-firmware/*.fw /lib/firmware

It seemed to do what it wanted.

 sudo shutdown -r now


I did that. The computer shut down.  When it booted back up, we can't see a darn thing.  It's not black.  It's just not usable.  The mouse pointer looks like an odd square. I can't see if the logon box is up.  Can't do anything with it.  We rebooted it and now it is just black.

Please help. If we can do something to login with a command line instead of the GUI, that might be the best way.  I will need detailed command line help though, I'm a PC girl trying to work with Linux here.

Thank you,

Gabrielle

---

### Post by x22 on 2009-06-21
> when it booted back up, we can't see a darn thing

do you mean, no GUI in the end, or do you mean no
"loading linux..." long wait...ACPI...  lots of
different text on the screen, in the first place?

if the latter, can't help; but if no GUI suggest using
a bootable floppy/CD ("tomsrtbt," "system rescue") to
boot, then if yr root directory "/" is on hda2,

"mount /dev/hda2 /mnt"

"chroot /mnt"

"which gdm"--/sbin/gdm, or /usr/sbin/gdm...

"mv /sbin/gdm /sbin/g_old_dm"

reboot

disabling the auto-GUI login "gdm" should leave you
with the command line

---

### Post by RGPerson on 2009-06-21
> **x22 said:**
> > when it booted back up, we can't see a darn thing

do you mean, no GUI in the end, or do you mean no
"loading linux..." long wait...ACPI...  lots of
different text on the screen, in the first place?

if the latter, can't help; but if no GUI suggest using
a bootable floppy/CD ("tomsrtbt," "system rescue") to
boot, then if yr root directory "/" is on hda2,

"mount /dev/hda2 /mnt"

"chroot /mnt"

"which gdm"--/sbin/gdm, or /usr/sbin/gdm...

"mv /sbin/gdm /sbin/g_old_dm"

reboot

disabling the auto-GUI login "gdm" should leave you
with the command line

Well, there was something on the screen. A very distorted GUI, I'd say.  We rebooted and still can't see anything really. It's mostly black. If I move the mouse, I see a disorted white banner at the top, repeating the word Dell.  That's the only word I can make out. It is a Dell computer.

And sorry, I really couldn't understand the rest. I don't have a bootable floppy or CD of linux at the moment.  And honestly, I can't say where my root directory is.  We have only one hard drive in there, if that helps.  I can see the GRUB menu and edit a line if need be.  I was able to VNC to the computer before we rebooted.  Got a blank screen but thought maybe I could use SSH (with Windows? How? I don't know that either), but now I can't VNC so that's out too.

If we reinstall Ubuntu, I'm afraid we'll be back at square one with all the stuff we fixed before and now can't remember how we did. Is there a better distro (we have 8.04)? But could we keep our e-mail and our calender items? Data, in other words?

PS. We have an ATI video card. I've seen there are problems with Nvidia cards and the HVR1600 but that shouldn't be our case as we don't have NVidia.

Gabrielle
Frustrated at this point and practically helpless in the world of Linux.

---

### Post by RGPerson on 2009-06-21
Please can someone help us. We are dead in the water here. 

We can't get into ubuntu at all at this time.  

Gabrielle

Update: We are still fairly dead, but I did find that pressing ctrl+alt+F1 got me to the command line.  I could see a bunch of stuff starting and then finally got a log in.  I logged in.  Now what?  Is there any hope of fixing this?

---

### Post by xc3RnbFO8P on 2009-06-21
What is your computer spec.?
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600")
> General Tips
As a general rule, HDTV is very resource intensive. The HVR-1600 is no exception. A video card supporting OpenGL and/or XvMC is strongly recommended. Minimum CPU feature set should probably start at a dual-core or a very late model single-core.

---

### Post by RGPerson on 2009-06-21
> **Ringi said:**
> What is your computer spec.?
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600")

Honestly, I don't remember everything but we bought a computer specifically to be powerful enough to do stuff like this.  It is a dual core and we upgraded to 4GB of memory and we got an ATI Radeon 4550 video card.  Should be plenty powerful.

I believe it's a Dell Inspiron 530n

Gabrielle

---

### Post by xc3RnbFO8P on 2009-06-21
It could be a bad install of Ubuntu, reading your post.

---

### Post by RGPerson on 2009-06-21
> **Ringi said:**
> It could be a bad install of Ubuntu, reading your post.

We had some problems earlier on but it was working.  I can see that there are 2 Mythubuntu's we can boot into as well, but then we can't get to some of our files in the Ubuntu 8.04 we have (the one we have installed our video card drivers in and updated, and now cannot see).

BTW: I did a dmesg | grep cx18.  I have to type up what I saw on the screen.  The left hand margin seems to be off the screen.

31.882137] cx18: Start initialization, version 1.2.0
31.882170] cx18-0: Initializing card 0
31.882171] cx18-0: Autodected Hauppauge card
31-887909] cx18-0: Unreasonably low latency timer, setting to 64 (from 2)
31.888011] cx18-0: cx23418 revision 01010000
32.108801] cx18-0: Autodected Hauppage HVR-1600
32.108803] cx18-0: Simultaneous Digital and Analog TV capture supported 
32.370915] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
32.454586] cs5345 0-004c: chip found  @ 0x98 (cx18 i2c driver #0-0)
32.586585] cx18-0: Registered device video0 for encoder MPEG (64x32kB)
32.586588] DVB: registering new adapter (cx18)
32.679680] cx18-0: DVB Frontend registered
32.379681] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
32.379697] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
32.679710] cx18-0: Registered device vbi0 for encoder VBI (20 x 21984 bytes)
32.679724] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
32.679726] cx18-0: Initialized card: Hauppage HVR-1600
32.679741] cx18: End Initialization
40.782353] cx18-0: loaded v41-cx23418-cpu.fw firmware (185332 bytes)
40.604832] cx18-0: loaded v41-cx23418-apu.fw firmware V00120000 (141200 bytes)
40.611016] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
41.443282] cx18-0 843: loaded v4l-cs23418-dig.fw firmware (16382 bytes)
41.462533] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

As much as I understand (which isn't a lot) that the driver loaded.  But somehow our GUI went bad.  Could it have messed up the video driver for our ATI Radeon 4550?

Gabrielle

---

### Post by xc3RnbFO8P on 2009-06-21
> We had some problems earlier on but it was working. I can see that there are 2 Mythubuntu's we can boot into as well, but then we can't get to some of our files in the Ubuntu 8.04 we have (the one we have installed our video card drivers in and updated, and now cannot see).
Looks bad to me,
make a fresh install
Jaunty 32 bit
use the restricted graphic driver from
System> Administration> Hardware Drivers

---

### Post by RGPerson on 2009-06-21
> **Ringi said:**
> Looks bad to me,
make a fresh install
Jaunty 32 bit
use the restricted graphic driver from
System> Administration> Hardware Drivers


Will it overwrite my documents and stuff in my Home directory?  My firefox bookmarks?  

Gabrielle

---

### Post by xc3RnbFO8P on 2009-06-21
> Will it overwrite my documents and stuff in my Home directory? My firefox bookmarks? 
Yes it will,
**you have to backup your Home folder**,
in the /home/.mozilla/**firefox** folder is all your bookmarks, settings and password in firefox.
You can replace this folder in the new install (just rename the new firefox folder first, firefoxxx or something)

---

### Post by RGPerson on 2009-06-21
> **Ringi said:**
> Yes it will,
**you have to backup your Home folder**,
in the /home/.mozilla/**firefox** folder is all your bookmarks, settings and password in firefox.
You can replace this folder in the new install (just rename the new firefox folder first, firefoxxx or something)


Okay, I can do that now. Because we made a slight progress.

We got an old monitor out of the closet and hooked it up.  Low and behold, we have GUI.  We have low resolution 800x600 or 640x480 but at least it's something.  So I can at least back up my stuff.  But how's this:  Did the install of the HVR-1600 mess up my ATI video card so that we can't use our 32" HD LCD TV to be the monitor anymore?  (It can do terminal, just not GUI.)

Gabrielle

---

### Post by xc3RnbFO8P on 2009-06-21
Restart the computer choose  Recovery Mode and run **xfix**

---

### Post by RGPerson on 2009-06-21
> **Ringi said:**
> Restart the computer choose  Recovery Mode and run **xfix**

I'd love to but it hangs when I try to run it in recovery mode.  Doesn't even get to a log in.

:(

Gabrielle

---

### Post by RGPerson on 2009-06-21
Lo and Behold: We have GUI!  It's not great but it's there.

We can't get a higher resolution than 1024x768 and it means we can't see the edges (No menu bar at the top, no taskbar at the bottom. They're there. I can see them in VNC.  We just can't see them on our TV.

So I really do feel it was the video drivers that got screwed up.

If I look at Administration| Hardware Drivers, it says no proprietary drivers are in use. I'm pretty sure the ATI one was proprietary.

If I look under Device Manager (Applications |  System Tools), I see PCI Bridge
  Video Controller
     DVB Device listed 4 times and Hauppauge HVR-1600 listed 4 times.
Further down  I see another PCI Bridge with
  VGA Controller (shown as Vendor: ATI Technologies, but there's nothing to expand there.  Under it is
  Audio Device
    HDA ATI HDMI Sound Card

Should I try reinstalling the drivers for the ATI?

Gabrielle

---

### Post by RGPerson on 2009-06-22
And once again, we have a black screen. I can probably get it to show with the old monitor but I think it's time to cut our losses.  Okay, today I'm going to research installing the Radeon and I'm going to research installing the HVR1600 and have them all down on paper, step by step.

But first, which distro should I go with?  We do want to use Myth TV at some point. Should we try one of the mythubuntu's?  We have a couple installed already.  Or should we go up to 8.10 or 9.04?  Or should we stick with 8.04?

I want to get this done right this time around.

Gabrielle

---

### Post by RGPerson on 2009-06-22
Well, it was the ATI driver.  Gave it one last shot. Tried to open the Catalyst console but it said no drivers were there.  So I downloaded the latest driver and attempted to install it.  Had to get creative as we were stuck in low res with the old monitor and some of the buttons were out of reach. But finally got it and on the big screen as well!  Now we're in the max resolution for the TV.

So now it's time to go back to the Hauppage.  I may have gotten the driver loaded. If so, we need to see about the software side of things.

Gabrielle

---

### Post by dano1 on 2009-06-23
got the 1600 working with myth 9.04 no problem. Didn't need the ivtv drivers(beleieve theyre loaded with the kernel) lemme know if i can help.

Using mythbuntu 9.04, not installing myth over ubuntu.

---

