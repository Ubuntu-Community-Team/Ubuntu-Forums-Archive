---
title: "Novatel / Verizon MiFi 2200 personal hotspot"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by Roger E Critchlow Jr on 2009-05-27
I've been using the MiFi with Ubuntu for over a week, from Seattle to Santa Fe on a road trip, and it's been great.  Particularly nice when you pull into a hotel that claims to have network access but can't explain why it doesn't actually work.   And it worked while driving down the road, too, well enough that I needed to discourage video viewing.

The device is a black rectangle smaller and thinner than an iPhone with a power switch, micro USB connector, status LED, a battery compartment, and a sticker identifying the network SSID and password.  It comes with battery, micro USB cable, AC wall wart to micro USB charger, and a cloth slip case.

To perform the initial activation of the MiFi or to download updates, it needs to be run from Windows or MacOS and connected via USB to install the VZAccess Manager application, drivers, twiddle the device state, and activate it on the Verizon network.  You also need to run in this mode to receive text messages, eg containing passwords for your myverizon accout.  When connected via USB it works as a USB CDMA modem and as a cdrom drive that provides the Windows or MacOS software and documentation.

After activation, when running on battery or off the AC power supply, the MiFi boots as a wireless access point, automatically connects to Verizon, and routes up to 5 connected devices to the internet.  No problems with this mode, we had a Windows machine, an Ubuntu machine, and a T-Mobile G1 all connected through the MiFi from a weigh station north of Brewster, Washington.  There is a web server running on the box which can be accessed wirelessly to check status and configure the usual access point / router options.

The puzzle comes when you connect as a USB device to Ubuntu.  It identifies as a cdrom drive with ID:[INDENT]Bus 006 Device 005: ID 1410:5041 Novatel Wireless 
[/INDENT]At this point, I thought to google the problem and found a Verizon forum post with the magic answer to my puzzle.  If you eject the VZAccess Manager volume which mounts as device 1410:5041, then it comes back and connects as a wireless modem / cdrom with ID:[INDENT]Bus 006 Device 007: ID 1410:6000 Novatel Wireless 
[/INDENT]The network manager picks it up as "Auto Mobile Broadband (CDMA) connection" and you can make a 3G connection by simply selecting it from the network manager menu.  

Which is what I did, this post started over my wired broadband and finished over wireless broadband.

It would be nice if the MiFi could be tricked into operating as a wireless access point while charging over a USB connection.  It would be nice to get access to the text message capability while connected from Ubuntu.  It would be nice to find a way to access the GPS which is reportedly onboard the Novatel.  And it would be nice if the web server provided the same capabilities as the VZAccess Manager application does under Windows.

But on the whole, there's little to complain about.  Now that I've discovered how to make a connection to the CDMA modem under Ubuntu, me, my laptop, my MiFi, and my micro USB cable are ready to roll.

The price for the MiFi from Verizon on a month-to-month non-contract basis has jumped from $270 on May 17 to $400 yesterday.  The prices with contract have also jumped.  There should be comparable devices available from Sprint and for GSM networks real soon, but I'd expect intense competition for components and manufacturing capability over the near term.

-- rec --

---

### Post by microtaint on 2009-05-28
I have also been using the Novatel Wireless MiFi on my ubuntu dell mini 9. I was wondering if anyone has had any luck running VZAccess Manager via wine.. for some reason I cant get it to install. Some how I came across a version of VZAccess Manager for linux , and got it install. For some reason the software hangs in the initializing mode. Works great with the WiFi and there is an admin area that gives you lots of information. 

Currently I'm in a mountainous area and trying to get my evdo signal, im stuck in 1x :(. Im currently using a Wilson amplifier and seems to be helping. without it i would not  have any service.

I activated my unit with osx. using vzaccess manager.
very cool product.

---

### Post by jimholt3 on 2009-05-30
Thanks for the info!  I was able to get Network Manager to see the device, but not able to get it to use the connection.  There was a username/password screen which I wasn't sure what to put there.  Also, it seems to want to use PPP, and I don't know if the settings for that are correct.

Also, my system which is Jaunty AMD64 did see the device first as a CDROM, but I had to actually mount it as root using the device /dev/sr1.  I am not sure why I couldn't mount/eject from the file manager.  When I ejected (as root via 'eject /dev/sr1') then it did reconnect as a modem.

I find the device to work well, but am currently trying to figure out why it doesn't seem to recharge the battery easily.  It is like you have to plug in the charger and device in some order.

---

### Post by microtaint on 2009-05-31
Is the network manager the same thing as system>admin>network?  how do i make the network manager see my device?

---

### Post by jimholt3 on 2009-06-01
System>Admin>Network Tools?  This is not Network Manager.  Network Manager is software which controls access to the network via the devices installed on your machine.  It generally has a little icon in the message area of the gnome panel which looks like two old terminals.

---

### Post by akraut on 2009-06-02
I've found the easiest way to charge the MiFi from your laptop, while still using the wireless functions...  Unfortunately, it requires some extra equipment.  ThinkGeek has a little USB dongle that will allow you to power a USB device, without the data lines getting in the way. [http://www.thinkgeek.com/gadgets/travelpower/b43f/](http://www.thinkgeek.com/gadgets/travelpower/b43f/)  It's about $8, but is effective.

---

### Post by Kevin- on 2009-09-14
Hi Roger , 

May I know how do you "eject" and re-mount the device ? 
All I see with my mifi device plugged in are the autorun, helper.exe and setup_vmc_lite.exe ,  I eject the device , nothing else comes up . d 
Do I need to do anything else to redetect the device and to mount it again ? 
Am stuck and needed to use this device as a dongle rather than a wifi connect..... 

Thanks in advance! 
Cheers.
Kevin

---

### Post by cbruce8 on 2009-10-12
Kevin, here is working sequence of events on a Dell E6400 running Jaunty:
1- attach MiFi using USB cable
2- When volume icon appears - eject 
3- When icon appears again, click network manager and select broadband

Hope that helps
-charlie

---

### Post by cbruce8 on 2009-10-12
Roger - from your post you are having no problems reattaching wirlessly to your MiFi from your Ubuntu box, correct?

---

### Post by topgun98 on 2009-12-15
Does anyone know how to prevent the MiFi -- and just the MiFi -- from automounting?

I tried the following line in fstab, but I get an error about permissions.  It does prevent it from automounting, but it also prevents the Mobile Broadband option from showing up in my system tray/notification area.

/dev/sr1       /media/VZA      iso9660 noauto,ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0      0

I would really love to be able to just plug this thing in and connect without having to eject the volume first.

Any ideas?

---

### Post by edulacomadreja on 2009-12-25
Hey **Roger**:

> It would be nice if the MiFi could be tricked into operating as a wireless access point while charging over a USB connection.

Well, you need tu cut the white and green wires (the data wires, red and black are the power wires) on the USB cable so there will be nothing but power running from the PC to the MIFI

Check this, it works!!!:

[http://www.youtube.com/watch?v=apnT_n-KD9I]("http://www.youtube.com/watch?v=apnT_n-KD9I")

---

### Post by B-Witty on 2009-12-29
Dang, it always recognizes as a CD Drive, but I have to do some kind of magic to get it recognize as USB drive (which works sometimes).  But it never recognizes as a way to connect.

----

Does it automatically connect after it is recognized as VZAccess thing (like a flash drive) because mine does not.

---

### Post by Rev. Pee Kitty on 2010-01-01
I just bought one and am having a similar problem. I'm using Kunbuntu 9.10 (2-6-31) and I've had no problems using the Mifi 2200 on my Windows box, both as WWAN and WiFi.
 
But when I plug it into my Linux box, it recognizes it immediately as both a CD-ROM and a Mobile Broadband. At least, I *think* it recognizes it as a mobile broadband - my network icon changes from a globe to a cell phone and it notifies me that the device was recognized.
 
But there's no connect option. If I hover over the network, it shows "Not Connected", and if I click on it to bring up my Network Manager, it doesn't show any available connections.
 
I just recently switched from Slackware over to Kunbuntu, so I'm not that good at diagnosing this - I'm not even sure how to bring up a list of every device, which might help me figure this out. Does anyone have any advice? Has anyone gotten a Mifi working under Kunbuntu?
 
Thanks,
PK

---

### Post by B-Witty on 2010-01-09
Hokay, I've researched this a bit. I know that if you have Windows installed and have it running (wired) on Windows and then restart to Ubuntu (or prolly should work for Kubuntu)
then the device is recognized properly and you will connect.

I'm just unsure how to make it work correctly wihtout having to do that. But I'm sorta researching around so lemme know anything...

---

### Post by pdc on 2010-01-10
this device seems like many;

comes loaded with windows software;
linux sees it as a CD-ROM device;
you need to "flip" it so linux sees it as a modem;

when you plug it in, an icon should appear on your desktop;
RIGHT-CLICK on the icon; and near the bottom of this menu you will see EJECT: select EJECT

the icon should disappear;

previously, folks described this device as auto-configuring;

you may need to configure:

try:

RIGHT-CLICK on network manager; the icon on the top tray of Ubuntu to the right; the connections icon;

select EDIT CONNECTIONS;

select ADD:

select country, network; accept;

now LEFT-CLICK on network manager; is your connection there?

press to click: any joy?

---

### Post by drew3739 on 2010-02-18
What if nothing comes up on my desktop?

I plug in the Mifi and nothing happens. I do however have Device Manager running and I can see the device recognized as a CDROM. If I hit properties I see novatel wireless. But there is no "eject" option in device manager.

Why is nothing poping up on my desktop?

---

### Post by CBMCO on 2010-02-24
You can always open up a terminal window and type "eject". That works for me.

---

### Post by lippsmasta on 2010-07-15
In order to charge the mifi while still usb plugged in check [this]("http://hawketechtalk.com/Members/hawke/mifi-2200-charging-via-usb-while-still-running-in-wifi-access-point-mode") out.

Basic steps: 


Login to Admin Page ([http://192.168.1.1](http://192.168.1.1))
Click on Advanced > Config File.

Click on "Download File" button and download to your system.

Change (with vi or nano or whatever)
<routeroverusb>0</routeroverusb>
to 
<routeroverusb>1</routeroverusb>
 
Upload the file on the same page.

Last Step, Important, after file upload it will soft reset for a sec then it needs a power cycle.

Now power over usb while connected to wireless will work!

---

### Post by eclectus on 2010-12-22
> **lippsmasta said:**
> 
Change (with vi or nano or whatever)
<routeroverusb>0</routeroverusb>
to 
<routeroverusb>1</routeroverusb>
 
Upload the file on the same page.

I don't see that option in my config file.  What version is specified in your config file?  Mine is 0.19P.

---

### Post by grikdog on 2011-01-30
I am completely baffled by the Verizon MiFi card.  I'm using Ubuntu 10.10, and it seems to work ok, BUT...

I had to VZW Access Manager on my daughter's Macbook, in order to authorize the MiFi with Verizon.  (They claim they did this at the store, but I suspect they didn't know what they were doing.)

With that done, my two Linux boxen sort of do and don't work right.  What am I doing wrong?

Did I need to Create New Wireless Network?  Or should I have just allowed discovery to find the Verizon gadget and simply logged on to it?

Since I seem to have done both (without truly knowing what this corner of Linux is really like), is that the reason my WiFi connects and then immediately disconnects.  If I then reconnect, the wifi net comes up.

Baffled.  Thanks for any help or insight on this.
d

---

