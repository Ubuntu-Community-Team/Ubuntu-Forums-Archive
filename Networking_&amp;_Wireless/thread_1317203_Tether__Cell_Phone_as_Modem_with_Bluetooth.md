---
title: "Tether / Cell Phone as Modem with Bluetooth"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by undoIT on 2009-11-06
I have successfully tethered my Samsung M610 cell phone (Sprint) with the USB data cable for use as modem. Couldn't have been easier! Much better than either Windows or OS X!

However, I can't figure out how to get the phone tethered through bluetooth. It seems like it should be simple after reading this:

> GNOME 2.28 offers a number of new features as well as stability and general improvements. For those that use Bluetooth enabled devices, you’ll love the new GNOME Bluetooth management tool. GNOME Bluetooth supports hundreds of Bluetooth devices, including mice, keyboards and headsets. This also includes PulseAudio integration for headsets and headphones. Also included with GNOME Bluetooth is the ability to access the internet through your Bluetooth enabled mobile phone. No more tethering! This is exciting news!

[http://ubuntu-tutorials.com/2009/10/27/whats-new-in-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/27/whats-new-in-ubuntu-9-10-karmic-koala/)

I don't see any options in Gnome Bluetooth or Network manager for connecting to the phone for use as a modem through bluetooth. Am I missing something?

---

### Post by undoIT on 2009-11-07
Okay, I figured this out. If somebody else is trying to get this working, hopefully this will be helpful.

First, I had to install blueman:

```
sudo apt-get install blueman
```

To open blueman, I went to System > Preferences > Bluetooth Manager. Then the applet for blueman appeared in the top right corner of system tray (not sure if it would've automatically appeared there after reboot, because it does appear there now every time I reboot).

To get connected, I open Blueman. Since I already established a connection with the default bluetooth manager, my phone is listed there. I right click it, Serial Ports > Dial Up Service. Then the phone is connected for use as modem.

For the final step, I go to Network Manager and connect to the phone. (I think the network connection for the phone is already listed there because I set it up earlier when tethering via USB).

Seems like there is one extra unneccessary step to establish a connection, but hey, I'm sitting in bed with my cell phone on the coffee table, tethered with bluetooth and connected with high-speed internet :cool:

It would be awesome to see this integrated with the default bluetooth manager as seamlessly as the USB tethering option. Linux just keeps getting better and better :guitar:

---

### Post by fyrmedic on 2009-11-12
Worked great for me. 

I had been using the CLI to do it via pppd and a bunch of scripts that I cobbled together. That worked great through 8.10, 9.04 and was sporadic on 9.10. But today I tried the Blueman approach and it works GREAT!!!!

Gotta love that LINUX!!!!!!

Oh yeah, I am using a Trendnet bluetooth dongle, connecting to a Verizon Blackberry Storm v1, and I think the dialup is just to #777.

Good luck,

Brad

---

### Post by isleshocky77 on 2009-11-17
undoIT,
Could you post the instructions you used for usb?

fyrmedic,
Could you use the scripts your using for Verizon? I'm sitting here banging my head against the wall. I've tried every example connect script for ppp and I keep getting "Connect Script Failed".  Any more information would be much appreciated.

Thanks to both.

---

### Post by undoIT on 2009-11-17
> **isleshocky77 said:**
> undoIT,
Could you post the instructions you used for usb?


Hi Stephen. Tethering with USB was very simple. I just plug the cell phone into the USB port, left-click NetworkManager Applet in top right of taskbar. There is an option for "New Mobile Broadband (CDMA) Connection...". I click that and follow the prompts and it is done.

---

### Post by fyrmedic on 2009-11-19
Stephan


Regarding my old scripts- I could not use them reliably. It seemed that they only worked when they wanted to. That wasn't very often and definitely not when I wanted them to. 

Today I brought the Acer AspireOne with me. It was recently upgraded with a clean install of 9.10 netbook remix. The first thing I did when I did the install was to install "blueman". Today when I got the chance I plugged in the bluetooth adaptor and used blueman to associate with with my Verizon BB Storm. I then right clicked on the entry shown in blueman for my phone and selected "serial ports-dialup service". That ran me through a quick little install wizard and I was done and able to select "Verizon connection" under "Mobile Broadband" in Networkmanager.

I am by no means a pro at tutorials but those are basically the steps that I used to get my internet connection established on my phone via bluetooth.  I hope that it helps you in some way.

Good Luck

---

### Post by mahiyar on 2010-02-23
Thanks UndoIt. This really helped. I guess internet through bluetooth is slow, looking for a similar set up through USB. The best part is, this worked in Ubuntu but not in Windows, not unless I install the bloated PC-Suite. Ubuntu is great, people who go out to help and offer solutions (like you) is what make Ubuntu a greater experience.

---

### Post by undoIT on 2010-03-26
One more thing to add. If you get this error:

> Connection Failed: Port already in use

or you are having a problem reconnecting after the bluetooth connection has been disconnected you can run this command in terminal:

```
sudo /etc/init.d/bluetooth restart
```

You may have to run it twice, I do. After you have done so, you'll be able to open blueman again to reconnect the phone as modem without having to reboot the computer.

---

### Post by readycarpenter on 2010-03-26
also if you use sprint, and you have a palm pre, it runs webos which is based on the linux kernel, there is a great app that lets you tether your 3g or 4g network via wireless, turning your pre into a wireless router, and no extra charges from sprint for "phone as a modem" just use your unlimited data plan that comes with your pre plan. costs less and you can use your pre to tether via usb, wireless, or bluetooth!

[http://forum.mytether.net/]("http://forum.mytether.net/")

---

