---
title: "Howto: Get Virgin Mobile Broadband2Go usb dongle working"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by RabidWeezle on 2009-10-16
I picked one of these up a little more than a month ago, it's a prepaid EVDO wireless card that runs over the sprint network. Anyway, there was a method of making it work using usb_modeswitch, and getting annoyed with all the steps needed to get it working after each boot or hotplug of the device, I decided to write a frontend/installer for it called VMDialer that would make it much more simple. 

[IMG]http://i34.tinypic.com/vy8mmw.png[/IMG]

Basically this is what you need to do:

```

sudo apt-get install xterm python python-gtk gnome-ppp

```
Note on users who have installed usb_modeswitch already:
If you have already installed usb_modeswitch, you might aswell remove it, because this doesn't call it. (I found that the one in the repo doesn't work for this device, so I included the latest version that does work for it, it will sit in /usr/share/vmdialer and called from there with my app. If you are a 64 bit user, I also included the source you can compile it and stick it in /usr/share/vmdialer overwriting the 32bit one if needed.

If you have one or more of these, you can omit them from the line

now head over to my google code site for VMDialer: [http://code.google.com/p/vmdialer/downloads/list](http://code.google.com/p/vmdialer/downloads/list) and download the latest version (0.11 as of writing this).

extract it where you want, then in a terminal:

```

cd /path/to/where/you/extracted/the/folder
sudo ./install

It should be rather quick

Then simply run it with the vmdialer command

[code]vmdialer
```

you can do this with alt+f2 if you want, or make a launcher on the desktop, whatever you want.

This has been tested in kubuntu and ubuntu jaunty running kernel 2.6.28-15-generic

Hopefully in karmic this app won't be needed as the kernel will do it up right the first time, we will see :)

BTW, if these instructions weren't enough or you still have questions, please read README.1rst located in the program's archive. There's an faq in there and some other trivialities.

---

### Post by RabidWeezle on 2009-10-17
Updated since I figured out from sprawlgeek (the person who did the initial usb_modeswitch method that I coded into less steps) that it also works with the new verizon mobile USB760 modem aswell. So if it's a Novatel USB760, it will work with this method (unless a new kernel or something breaks compatibility or until perhaps karmic comes out and has a later kernel. We will see. Until then, this will work for your usb760 needs.

---

### Post by pointym5 on 2009-11-03
What exactly are the "right things" that the Karmic release is supposed to do with one of these devices?  I'm running Karmic, and when I plug it in nothing interesting happens at all.  It just looks like an empty mass storage device.

---

### Post by pointym5 on 2009-11-03
For what it's worth I tried the "vmdialer" tool. It fails immediately with an error in the console window I launch it from:
```
Detecting USB760
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
there was a problem initializing the pynotify module

```

I'm running it as root (Karmic, 32-bit).

[edit] durr running as non-root avoids the dbus security failure

seems to work - still don't know what (if anything) karmic's supposed to do for me automagically.

---

### Post by pdc on 2009-11-03
so you did the 

> udo apt-get install xterm python python-gtk gnome-ppp

and then installed his vmdialer?

I guess RabidWeezle did comment ...........

> This has been tested in **kubuntu and ubuntu jaunty** running kernel 2.6.28-15-generic

Hopefully in karmic this app won't be needed as the kernel will do it up right the first time, we will see

---

### Post by pointym5 on 2009-11-04
Well, there's no python-gtk anymore (it's python-gtk2) but other than that, yes that's what I did. The problem was that running as root one can't do what the software needs to do.

---

### Post by RabidWeezle on 2010-05-02
Good news virgin mobile users! This app is now not required at all thanks to the release of Lucid Lynx. The new network manager has added support for the usb760 over virgin mobile.

Basically, click the network button at the top next to the speaker icon, and look under mobile broadband. Make a new mobile broadband connection and click virgin mobile/helios, then it will be up and running with no more configuration. Cheers to the ubuntu network guys for getting this done right!

---

### Post by Weezie on 2010-05-11
I'm trying to get my Virgin Mobile BB2G USB 760 to work on Ubuntu Netbook Remix (Network Manager), on a Dell Mini 910.

I'm very new to Ubuntu, and not a programmer at all. So please give instructions that a toddler would understand.:P

I have the Network Manager saying the Mobile Broadband is connected, but when I go to Chrome, Firefox, Skype, etc., no pages load. The circle on the browser just spins and spins. :( 
I have no clue what to do or what settings to change. I have the following in the Virgin Mobile/Helio setup:
number: #777
username: blank
password: blank

(I've tried putting my virgin # and pin in - this didn't work, I tried Internet/Internet - this didn't work either)

For PPP - all connection types checked (I tried un-checking CHAP - this didn't work)

For IPv4 - Automatic PPP

Help - what do I need to do to get this working? It connects but doesn't work???? (arrrrgggggh):confused:

---

### Post by alexfish on 2010-05-11
Hi Weezie

 Assuming you think the connection is working with Network Manager ,
 with the Network Manager can you post the details of the connection information by right clicking on the applet , then post all the details , below is a typical screen shot , although your details may differ

regards

alexfish

---

### Post by Weezie on 2010-05-11
SOLVED: Thanks alexfish. My son solved my brain-wracking problem within 10 minutes. Too bad he was in school all day, or it would have been solved earlier. 

Anyway, it was the IPv4 setting. He changed it to the 2nd setting of "Automatic Addresses Only". Viola. Pages started loading. It was something that simple.

Appreciate your offer to help. :KS

---

### Post by alexfish on 2010-05-11
hi Weezie

good news

also

good to know the younger generation have something to offer

regards

alexfish

---

### Post by Andrew Olney on 2010-06-13
One thing not mentioned is that usb-modeswitch is still required.

sudo apt-get usb-modeswitch

is required for the 760 to be recognized as a modem rather than a cd drive.

---

### Post by axman1971 on 2010-07-12
Hello all.. I followed Weezie's method and it still doesn't work... a connection show's as active, but no web page comes up at all...any help would be very much appreciated...
Thanks again

---

### Post by sieve on 2010-07-12
> **RabidWeezle said:**
> Good news virgin mobile users! This app is now not required at all thanks to the release of Lucid Lynx. The new network manager has added support for the usb760 over virgin mobile.

Basically, click the network button at the top next to the speaker icon, and look under mobile broadband. Make a new mobile broadband connection and click virgin mobile/helios, then it will be up and running with no more configuration. Cheers to the ubuntu network guys for getting this done right!

This is true.
Was never able to get Broadband2Go working quite right on 9.09 and had given up on it for a while. Based on what RabidWeezle posted, I gave it another try last night on a 10.04 system and it worked easily and perfectly. :D

---

### Post by axman1971 on 2010-07-12
Did you have to tweek anything at all? the sprint usb worked right out the box... I've since deleted that one and tried to put in the virgin USB and nothing...EDIT****
I got it working, looks like I missed 1 crucial step, You HAVE TO activate it through a windows laptop/desktop first.

m

---

### Post by sieve on 2010-11-12
> **axman1971 said:**
>  You HAVE TO activate it through a windows laptop/desktop first.

That's what I did, although I don't know if that's still the case or if you could do it through WINE.

---

### Post by akeem_da_dream on 2010-12-06
> **Andrew Olney said:**
> One thing not mentioned is that usb-modeswitch is still required.

sudo apt-get usb-modeswitch

is required for the 760 to be recognized as a modem rather than a cd drive.

i got "invalid operation usb-modeswitch" is there an alternate command?

---

### Post by pdc on 2010-12-07
sometimes it is helpful to spell out a bit more of what is happening:

assumption: you have ubuntu 10.10 installed?

and you have a virgin mobile broadband dongle you want to use?

and if you plug it in; and wait a bit; and left-click on the network manager icon; (leftmost of those at top right) ...... that there is no option to configure new mobile broadband connection?

I say all this because 10.10 is picking up most modems automatically;

so you may not need usb_modeswitch;

if you really want it, best get the latest debian package from the debian repositories, as the ubuntu one is a few behind

debian repository [http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

assuming you have 32bit ubuntu, you would select the i386 version and also install the data package too

---

### Post by akeem_da_dream on 2011-05-07
well months later i attempt this and read this thread more carefully. I'm connected. thanks!

---

### Post by pdc on 2011-05-07
well done;

enjoy

---

