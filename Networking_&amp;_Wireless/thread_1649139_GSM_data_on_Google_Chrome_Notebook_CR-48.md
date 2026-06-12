---
title: "GSM data on Google Chrome Notebook CR-48"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by msnuser111 on 2010-12-19
I have one of the Google Chrome Notebooks aka the CR-48,I installed ubuntu and most of the hardware works fine,but the one thing that is bugging me is that I can't get the built in Qualcomm Gobi 2000 to work. I am trying to use the gsm part of it,and it shows up during boot and in lsusb,but it will not show up in the connection list in the top panel. It does show up with the CDMA connection on first bootup,but never again after that. I have tried installing the firmware [according to this guide]("http://ubuntuforums.org/showthread.php?t=1456735&highlight=gobi+2000") but it doesnt make anything change.

lsusb gives me this:
```
Bus 001 Device 002: ID 1410:a014 Novatel Wireless 

```I looked through the log viewer and the only thing I could find containing gobi was daemon.log which is attached.

I am running ubuntu desktop 32bit 10.10,fully updated.

---

### Post by msnuser111 on 2010-12-19
I got verizon working but still no gsm.

---

### Post by tgalati4 on 2010-12-20
It's quite possible that the gsm connection was not made in hardware.  The youtube videos discussed the dual-radio feature to allow international use, but the CR48 is a demonstration machine and US/Verizon only.  So it's possible that it has the gsm radio, but it might not be connected.

Also, did you insert a valid SIM card?  GSM requires a SIM card for activation.

---

### Post by msnuser111 on 2010-12-20
> **tgalati4 said:**
> It's quite possible that the gsm connection was not made in hardware.  The youtube videos discussed the dual-radio feature to allow international use, but the CR48 is a demonstration machine and US/Verizon only.  So it's possible that it has the gsm radio, but it might not be connected.

Also, did you insert a valid SIM card?  GSM requires a SIM card for activation.
Yes,my T-Mobile sim is in the slot under the battery. I would assume that the gsm hardware exists based on the fact that they put in a sim slot in the first place. (and yes,I do know what happens when I assume things.)

---

### Post by tgalati4 on 2010-12-20
Take it apart and see if it is really hooked up.  Have you ever seen a cable TV box with ports on the back that don't do anything?

Or, less risky approach, send an email to the chromeos developers working the wireless stuff.  Someone should know if the GSM will work with the current batch of CR48's.  Maybe you have to wait for CR49?

---

### Post by msnuser111 on 2010-12-20
> **tgalati4 said:**
> Take it apart and see if it is really hooked up.  Have you ever seen a cable TV box with ports on the back that don't do anything?

Or, less risky approach, send an email to the chromeos developers working the wireless stuff.  Someone should know if the GSM will work with the current batch of CR48's.  Maybe you have to wait for CR49?
not sure how I would tell once inside,this is the card: [http://www.engadget.com/photos/google-cr-48-laptop-torn-down/#3665054](http://www.engadget.com/photos/google-cr-48-laptop-torn-down/#3665054)

---

### Post by donciclon on 2010-12-20
Did all your hardware work right after you finished loading ubuntu up in the cr-48? After following the instructions to the T on the developer's site i was able to get it up and running but i had no wlan or audio. anyone know what gives?

---

### Post by msnuser111 on 2010-12-20
> **donciclon said:**
> Did all your hardware work right after you finished loading ubuntu up in the cr-48? After following the instructions to the T on the developer's site i was able to get it up and running but i had no wlan or audio. anyone know what gives?

yeah,both of those work,the only things I cant get working are gsm data,2 finger scrolling (or any scrolling for that matter,its recognized as a mouse not a touchpad),and the keyboard shortcuts.  Wine has some weird graphics glitches that I havent seen on other computers,but I'm not sure if thats the computer or intel's crappy graphics

---

### Post by ssvss on 2010-12-20
> **msnuser111 said:**
> I got verizon working but still no gsm.

Hi, Can you please tell how you got Verizon to work ?
Should I install any driver for it ?

---

### Post by msnuser111 on 2010-12-21
> **ssvss said:**
> Hi, Can you please tell how you got Verizon to work ?
Should I install any driver for it ?

Basically I just kept switching the kernel priority to switch between chrome os and ubuntu,and it started showing up,it usually shows up like 1 in 3 boots. 

[[more development on the issue]]
whatever the problem is,its not the card,its ubuntu. I tried my tmobile usb card and its doing exactly the same thing as the verizon part of the built in modem. I click on the network name,it tries to connect for a few seconds then says mobile broadband disconnected. The same card with the same configuration works on my desktop running a normal install of ubuntu 32bit,could it be that the cr-48 uses the chrome os kernel? vpn doesnt work either if that helps.

---

### Post by msnuser111 on 2010-12-21
> **msnuser111 said:**
> Basically I just kept switching the kernel priority to switch between chrome os and ubuntu,and it started showing up,it usually shows up like 1 in 3 boots. 

[[more development on the issue]]
whatever the problem is,its not the card,its ubuntu. I tried my tmobile usb card and its doing exactly the same thing as the verizon part of the built in modem. I click on the network name,it tries to connect for a few seconds then says mobile broadband disconnected. The same card with the same configuration works on my desktop running a normal install of ubuntu 32bit,could it be that the cr-48 uses the chrome os kernel? vpn doesnt work either if that helps.

the usb adapter I am using is a Huawei UMG181.

---

### Post by unforgiven512 on 2010-12-24
It seems to me as if the issue is USB devices under Ubuntu in general -- I had some issues getting Ubuntu to recognize other USB devices of mine as well. To get it to recognize my USB-Serial adapter, I had to unplug and replug it 5 times.

I think it may have something to do with us using the Chrome OS kernel, rather than a "real" kernel.

---

### Post by msnuser111 on 2010-12-24
> **unforgiven512 said:**
> It seems to me as if the issue is USB devices under Ubuntu in general -- I had some issues getting Ubuntu to recognize other USB devices of mine as well. To get it to recognize my USB-Serial adapter, I had to unplug and replug it 5 times.

I think it may have something to do with us using the Chrome OS kernel, rather than a "real" kernel.

On mine,the card.is recognized as soon as I plug it in,it just wont complete a connection to tmobile,it stops at authentication.

---

### Post by msnuser111 on 2011-01-01
> **msnuser111 said:**
> On mine,the card.is recognized as soon as I plug it in,it just wont complete a connection to tmobile,it stops at authentication.

I've been doing a lot of stuff with android over the last few days,and I was thinking about this while I was doing it,I think I figured out what the problem here is. VPN doesn't work,GSM over usb doesn't work,and the CDMA modem doesn't work,all stop at authentication. Could it be possible that its because the kernel doesn't have a TUN module built in? that seems to be what the problem is to me at least,anyone else have any ideas?

---

### Post by msnuser111 on 2011-01-11
I've been playing around with the new pc bios,and a normal ubuntu 64bit install,and it handles the usb stick properly now,I can connect without issues,Does anyone have any ideas for how to get the internal card working,cdma or gsm (preferably gsm)? It shows up as a novatel device,but I can't get the firmware to load. I tried gobi loader using the firware from chrome os,but it won't work.

---

### Post by defconoii on 2011-04-17
here is how to get 3G working on the CR-48 w/natty & maverick:
[http://cr48.wikispaces.com/Use+3G+Wireless+in+Ubuntu](http://cr48.wikispaces.com/Use+3G+Wireless+in+Ubuntu)
Now that this is working, maybe we can file a bug in launchpad with the supplied firmware and compiled modules to include in future ubuntu releases :)

---

### Post by jpthompson23 on 2012-01-17
Has anyone figured out how to do this?  I have an AT&T SIM card that I put in the slot.  I have the Verizon connection working, but I only get 100 MB/month.  I'd like to use my AT&T data plan.  BTW I am running Natty.

Apparently with crosh there is a utility that lets you change your carrier.  However, seeing as I'm not running Chrome OS, I can't use crosh.  So what else can I do?

---

