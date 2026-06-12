---
title: "Connecting a wireless/wifi printer to ubuntu 12.04"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by CJR2011 on 2012-12-01
Okay so here are the issues: 
1.) I have no to limited experience with ubuntu and have used windows up until playing with ubuntu about a year ago 
2.)I do not know how to find my printer's ip
3.) I do not know how to find my printer's LAN settings
4.)I don't understand configuring networks or any of the technical procedures in attempting to do so.

*I say "playing" with ubuntu beacause I do understand some of the basic procedures of the operating system but I'm hoping to illicit a "hand-held" response in how to go about connecting to my wireless printer: A Canon-MP560-series

So I have spent several hours trying to connect my printer. I get as far as the "Host" input prompt and then I'm lost. When connecting a wifi printer what is the "Host" it is searching for and how do I go about locating my printer's "Host"

*The printer is connected to windows on my laptop and I'm assuming this will be the easiest route to finding the required information.

So please any help at all that deconstructs what it is I'm searching for and how I go about locating it would be extremely helpful. I would prefer not to clog the thread with un-useful information that I or other extremely novice users won't be able to understand. I am a noob and I have no technical skills, so I appologize in advance for any frustration that befalls you because of your dialogue with me. Thank you for the help.

---

### Post by pdc on 2012-12-01
I am interested in printers but only have experience with usb cables!

have a look at a couple of these videos:

see if any help you move forward ..

[http://www.youtube.com/watch?v=XifwwfPMtW8](http://www.youtube.com/watch?v=XifwwfPMtW8)

[http://www.youtube.com/watch?v=YekdBoF7vlY](http://www.youtube.com/watch?v=YekdBoF7vlY)

I would suggest you install the Canon drivers for the MP560 series before attempting the configure; if you have not already done so;

the driver comes in as [COLOR="SeaGreen"]cnijfilter-mp560series-3.20-1-i386-deb.tar.gz
[/COLOR]

you get it from here 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html)

..if you select archive manager if you download it; extract the package to your desktop; click on the [COLOR="Magenta"]install.sh[/COLOR] and it will install..

if you subscribe to a thread, you can follow it more easily; top-right: thread tools..................

....this driver is for 32bit...........64bit may need a symbolic link...
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html)

---

### Post by ahallubuntu on 2012-12-01
My Canon has a numeric keypad, so connecting it to my wireless network was super easy: just choose the network from the printer itself and type in the passcode right there.  It appears your Canon has some way to do the same from the printer.  That's really the first part: getting it on your network.  Have you done that?  Can you print to it wirelessly from Windows?

If it is on your network, the second part is detecting it in Ubuntu.  Have you tried simply asking Ubuntu to search for your printer?  If it is on your network, then it should at least find it (give it a minute of searching).

There are ways to find out the printer's IP address (assuming it is on your network), but to do that, I'd need more info on your home router (make/model).  Generally it involves logging into your router from a web browser, typically from the local IP address [http://192.168.1.1](http://192.168.1.1) or [http://10.0.0.1](http://10.0.0.1) or something like that.  (Varies by make/model of router.)

Anyway, once it is on the network and detected by Ubuntu, then you have to find a driver for it.

For some reason, Canon's Europe site seems to have the best Linux support.  I found Ubuntu drivers there for my Canon - was lucky.  There may be some sort of drivers for yours too:

[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

Debian drivers MAY work but may not be simple to get going.  (Ubuntu is based on Debian.)  You can try simply downloading them and trying to install, but you may need to read "README" files and decipher them.

It's also possible that, in Ubuntu 12.04 LTS, once the printer is on the network and detected that Ubuntu will will already have a driver for your printer.  Tell us if you've gotten to "on network and detected" yet.  If not, where is your stumbling block?  As said above, just getting it on your network should not even require a computer.

---

### Post by CJR2011 on 2012-12-01
Thank you both for replying so quickly and effectively. You have gotten me farther than anyone else's posts I've seen around the forums.

For the update:

I have found and "connected"(tentatively speaking because one way doesn't appear to be working) in two different ways.

The original way that is working, but extremely slow when it comes to printing. Slower than would be expected from my experience through windows's connection. I used something called samba(I think I installed this sometime ago, so I don't recall what it is exactly): essentially what I think is happening is I am using the computer that is connected to the printer via USB cable as the "host" and then it is connecting through this connection to the printer, thus causing the slow speed at which it prints.

I have connected by means of what is labeled "WORKGROUP" on my network which appears to be all the devices connected to my network and adding in the printer's work group location and "identifier"(I don't know what the proper term is, it is a series of integers and letters I put this in the [port/] (there should be a colon before the "port" in that, but it renders a smiley face if I put one) portion of the example provided by the "printing" program/application?). It appeared to be working (installed drivers and such) until I actually tried to print something.  Then the "printer state" read as such: "Idle - Unable to connect to CIFS host after tried (3 times)"

After watching the videos I see where I might have an issue. My printer is not connected via an ethernet cable, but solely through "wifi" and a usb cable to another computer in my home.

One thing that occurs differently with my case and the videos's cases is when I click the "network printer" drop down no devices show up. I tried waiting awhile and still no luck. Secondly when I click "find network printer" it asks for a "host" on the right which is confusing because idk what the "host" is in my case.

*also I'm unsure if i have a router or modem and I have no idea what the difference between the two is or if they even perform the same functions. It was the one provided by AT&T.

I hope I have addressed everything your two replies have brought up. BTW you two are great and I really appreciate the support. Thank you for the help.

---

### Post by CJR2011 on 2012-12-01
A few things I left out:

The printer is connected via a "wireless LAN" network or at least thats what it tells me.

The driver install (that pdc posted) appeared to be successful and it added what appears to be the correct printer to the printing-local host window, but when I try to print test, it goes from Idle > Processing... > Idle again. I don't know what this means because it doesn't register that it has failed to connect. This appears to be a fast and easy way about installing the driver and the printer to ubuntu, but I'm not sure what i messed up.

---

### Post by CJR2011 on 2012-12-01
> **pdc said:**
> if you subscribe to a thread, you can follow it more easily; top-right: thread tools..................

This was extremely helpful (: thank you lol.

Now is there a way to quote only part of what you said without having to delete the rest haha?

Uhoh... is that considered spamming my own thread?

---

### Post by boogerama on 2012-12-01
I checked [openprinting.org]("http://www.openprinting.org/printers") but didn't find your printer listed.  It does show an MP490 & 480 but they're listed as a "paperweight".  

Some wireless printers just wont work with Linux.  I had an Dell v305w (I think it's made by Lexmark) and I couldn't get that thing to print either.  It was also listed as a paperweight in OpenPrinters.org

---

### Post by CJR2011 on 2012-12-01
But I can get it to print it's just extremely slow and I have found the drivers (more accurately pdc has found the drivers) for it and it does appear to be installed and working (to an extent). 

Would this be enough proof of "compatibility" to delve further into making it run at the printer's full capacity?

---

### Post by boogerama on 2012-12-01
You're right, since it is printing there may be a work around to get it printing faster.  I just have no idea what it would be :)

---

### Post by CJR2011 on 2012-12-01
Story of my life lol. Thank you for the website I'll add it to my repertoire of references.

---

