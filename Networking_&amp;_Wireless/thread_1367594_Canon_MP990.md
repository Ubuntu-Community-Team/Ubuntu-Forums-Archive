---
title: "Canon MP990"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Kaysea01 on 2009-12-29
OK folks...this is my first post to the Ubuntu community, because I am stumped.

I have been unable to connect to my shiny new Canon MP990 wireless printer on my linux machine (Ubuntu 8.04,) and I can't figure out what I'm doing wrong.  I'm using the Printer Configuration program, and I'm not sure where to go from there.  I tried to locate this wireless printer via the Internet Printing Protocol and the Other connections.

When I use the "Other" connection, I'm able to put in the network address for the printer, but my printer doesn't come up on the list of supported printers.  Are there any additional drivers I can locate via Synaptic or the "APT Get" command that will let me connect to this printer?

Thanks to all

Marco

---

### Post by gazzatav on 2009-12-29
Hi, have you checked your router to make sure there is a connection?  You should be able to get the ip address from there.  My old Epson printer connects wirelessly through a network box and that just has this in the url section 'socket://192.168.0.4:9100'.  I just went to new printer->network->internet printing protocol and typed in the ip address there.  (Without the 'socket://' and port number ':9100')

What software has the printer come with? - I just went to the Canon site and looked for drivers for this and they don't list any for Linux.  (I'm interested in this mfp myself)

---

### Post by blur xc on 2009-12-29
I have an mp980.  Simple fix?  Buy an hp.

Complicated fix that is unreliable- First, install all the canon software on a windows machine (at least w/ the mp980), w/ the usb cable connected, as this is the only way to get the printer on the network.  They purchase turbo print for approx $40usd (IIRC), and find the printer and print happily.  Scanning won't work over the network though.  You'll have to scan to a usb stick and transfer the files to the pc that way.  I often have to remove the printer and do the add new pritner setup again to make ti work.  If you change your wireless network, you'll need ot uninstall all the canon software on the windows pc, and reinstall it all to make it connect ot the new wireless network.  It's idiotic and horribly frustrating.  Half of the time, my wife emails me what she wants printed and I print it here at work (on an hp, but windows, but still, hp printers), and take it home.  That's less of a hassle.

You'll be happier w/ an hp.  I'm shopping around right now- I think this is the one I might end up with- [http://www.newegg.com/Product/Product.aspx?Item=N82E16828115455&cm_re=officejet_6500-_-28-115-455-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16828115455&cm_re=officejet_6500-_-28-115-455-_-Product)

It doesn't need to be connected to a computer to set up network connections.  Just select your wireless netwrok ssid, and inter your encryption key and you are all set.

BM

---

### Post by Kaysea01 on 2009-12-29
@ Blur xc

Normally, I would have bought an HP (In fact, this is my first non-HP printer I've bought in the past 15 years.) In this case, HP didn't have the combination of features I was looking for (wireless, high-resolution scanner, manual printer feed)

@ gazzatav

I tried your suggestion, and I'm still running into the driver issue.  The MP990 isn't on the list of Canon printers. 

To all --

Do you think any of the older Canon drivers would work for the MP 990?

---

### Post by TaxAlien on 2009-12-30
The solution is apparently to use turboprint which is a commercial printer driver on linux.

I've just had a go and it printed a test page...

So much for the great idea to avoid an HP product. Just like you I had enough of HP. Seems I had enough of Canon in just a day!

---

### Post by blur xc on 2009-12-30
> **TaxAlien said:**
> The solution is apparently to use turboprint which is a commercial printer driver on linux.

I've just had a go and it printed a test page...

So much for the great idea to avoid an HP product. Just like you I had enough of HP. Seems I had enough of Canon in just a day!

The grass looks greener on the other side of the fence, until you get there...

BM

---

### Post by blur xc on 2009-12-30
> **TaxAlien said:**
> The solution is apparently to use turboprint which is a commercial printer driver on linux.

I've just had a go and it printed a test page...

So much for the great idea to avoid an HP product. Just like you I had enough of HP. Seems I had enough of Canon in just a day!

Just about every Linux distro comes w/ open source hp drivers already installed.  All you do is plug in the printer and print (according to what I've read).  I'm sure there are other makes that are supported as well.  According  to my research, hp is the best supported line of printers in Linux.

BM

---

### Post by Kaysea01 on 2009-12-30
To all --

Thanks for the suggestions...I guess I'll have to go out and get the commercial drivers if I want this particular printer to work with my linux machine...bummer.

@ blur xc:  I have to agree with you about the HP drivers.  Not only are the HP printers the best supported in linux, but also in windows.  I have a 12 year old LaserJet 5P that's still running strong, and I'm sure that my old LaserJet 2P+ is probably running fine for someone in this town, too.  I'm just bummed the linux box is going to be the only computer in this home's network that won't be able to print to the color printer.  

I'm not too heartbroken about it as long as the rest of the family can print to it from their windows machines.  I'd catch real grief if that wasn't the case :)

Best regards,

Marco

---

### Post by blur xc on 2009-12-30
> **Kaysea01 said:**
> I'm not too heartbroken about it as long as the rest of the family can print to it from their windows machines.  I'd catch real grief if that wasn't the case :)

I've been in trouble a bit on that one...  I made our main family pc (centrally located in the house) run primarily on Ubuntu.  We got the Canon printer about a month or two before I built the new pc, which was before I knew what a pain it would be to print to.  So yeah, I've gotten a lot of grief...  I convinced my wife we needed to spent the $$ on turbo print, and now the printer is still horribly unreliable, and I'm pushing to spend another $100 - $150 for an hp printer.  So yeah, the wife's not happy.  She thinks everything regarding the computers should just work and not cost any extra money to use...

BM

---

### Post by x001 on 2010-03-30
I wondering if the MP860 drivers would work?
[http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp]("http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp")

I was also thinking of buying this printer but I guess I will go with an HP for now.

---

### Post by pdc on 2010-03-31
I find the Canon Asia site is a good source to look for linux drivers 

[http://support-sg.canon-asia.com/](http://support-sg.canon-asia.com/)

I can't see that the MF800 or MF900 series are supported;

turboprint make excellent drivers for a wide variety of printers with linux

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990)

you can download a free version, and pay a small sum for the fully working version; we bought turboprint several years ago and it has driven an ip5000 very well

---

### Post by blur xc on 2010-03-31
> **pdc said:**
> I find the Canon Asia site is a good source to look for linux drivers 

[http://support-sg.canon-asia.com/](http://support-sg.canon-asia.com/)

I can't see that the MF800 or MF900 series are supported;

turboprint make excellent drivers for a wide variety of printers with linux

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990)

you can download a free version, and pay a small sum for the fully working version; we bought turboprint several years ago and it has driven an ip5000 very well

I also bought turbo print, but it's not going to make the canon printer any better of a printer.

If your are running yours wired- maybe you'll be ok.  Ours was wireless, and it would drop off of our network from time to time, and as I stated in my earlier post, the only way to get it back on was to uninstall all the canon software from a windows computer, plug it in w/ the usb cable, and reinstall all the software and drivers again.  If I went a few weeks w/o printing, I'd have to spend a good 1/2 hr or more farting around with it to make it work again.  That, and in my observations- the mp980 has a voracious apatite for ink.  Not economical!

the HP 6500 wireless, to date, has had one issue of appearing offline on my desktop computer (laptops and netbook work fine still).  I verified that it was still on our wifi through the lcd on the printer, even reconnected it for good measure (takes a minute or two) with the wifi wizard.  I ended up having to remove it from the ubuntu printers dialog and re-add it, only took a few minutes to do, and it was working again.  And so far it seems to be better on ink consumption than the Canon.

BM

---

### Post by JazzyTech on 2010-09-11
> **pdc said:**
> I find the Canon Asia site is a good source to look for linux drivers 

[http://support-sg.canon-asia.com/](http://support-sg.canon-asia.com/)

I can't see that the MF800 or MF900 series are supported;

turboprint make excellent drivers for a wide variety of printers with linux

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP990)

you can download a free version, and pay a small sum for the fully working version; we bought turboprint several years ago and it has driven an ip5000 very well

I agree; TurboPrint is your easiest option right now. You can try it for a month before you buy.  Great piece of software imo! Took me some time but I've got my MP 990 working quite well as a printer connected wireless to my LAN. 

 SANE, on the other hand was harder to get going due to the backend.  I had to get the latest "git master" and compiled myself.  Everything works pretty good except for the "Transparency Unit" setting in Xsane. I cannot scan beyond 300 DPI.  600 DPI gives me a blank black picture, 1200 DPI produces a blank white picture.  The scan head "grinds" as if trying to find zero position not knowing it is already there when scanning beyond 1200 DPI.
  Can anyone direct me as to where I should start looking to fix this?  I'm feverishly hoping there is a config file somewhere that I can tinker with :)
I'm running ubuntu 10.04LTS, Xsane 0.996.

---

### Post by eljopc on 2011-01-02
IMHO

We want to use Linux open source because we do not want to get pushed in a box by Microsoft or Apple. Now we want to choose a good printer and we get pushed back to one label a lousy HP? 

Linux, thats sad.

And people, PLEASE, if someone asks how to do something in Linux they do not ask what you use and what works for you, they only want help on the asked question.

Sorry I get sometimes frustrated.

---

### Post by nakednorman on 2011-01-23
I tried 9.10 some while ago but it kept trashing my 'fake raid' (RAID 10).  It saw them (and wrote to them) as 4 sepatate disks, in spite of the fact that Ubuntu had a 5th disk all to itself.  When it wouldn't print to my Canon MP990 either, I gave up.

12 months on, I was just about to try 10.10 to see if things had improved on the fake raid front - but my excellent Canon MP990 is still going strong so there seems no point in trying an alternative to Windows if I have to replace good peripherals with 'compatible' items.

I'll look in again next year.

Regards.

---

