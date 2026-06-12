---
title: "how to add driver to printer driver list"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by kiridude on 2009-03-31
Hi, I am trying to connect wirelessly to my Canon IR 3300 printer. The drivers for this model exist for Linux and I download and installed them from Canon. When I enter the printer config wizard, it sees the printer, gets the IP correct, then offers a long list of drivers available. 

The strange thing here is that it does not offer the driver for my printer - even though it exists on the Canon website and I've even downloaded it!

Instead, it offers to use a driver for another model of printer from Canon.

Can someone help me to get the printer config to see the correct driver pls?

Thanks

---

### Post by chili555 on 2009-03-31
Is the driver that Canon provided a *.PPD* file? Do you not have the option to provide your own .ppd as you install the printer as attached?

---

### Post by kiridude on 2009-04-01
thanks for your reply chili - you're the only one :)

There is a ppd folder in the package that has ppd files for hundreds of printers...BUT...not one for the IR3300 - which is what the whole package was supposed to be for!

I find it strange that the driver package for the IR3300 does not have any reference to that model in it, but a reference to every other Canon printer ever made. ](*,)

I wrote an email to Canon requesting some help, or maybe you have some ideas.

Thanks

---

### Post by chili555 on 2009-04-01
You might check here: [http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_3300](http://openprinting.org/show_printer.cgi?recnum=Canon-imageRunner_3300)

I am a bit amused because it says the printer works 'partially' and the little chart knocks it down for graphics and photo. Since it appears this might be a monochrome laser printer, you would expect that the photo performance would be poor!

It says the *pxlmono* .ppd file is the recommended driver. I suggest downloading it and trying it.

PS - Oh, my!!! I just looked this monster up. That's quite a printer/scanner/etc. there!

---

### Post by kiridude on 2009-04-01
You're the best =D> it works now!

Cant believe Canon cant get their own drivers right, not to mention the slowest customer service in the world! I will not be purchasing again from them.

I now have a new small problem: since I am in Europe, the printers print A4, but when I installed Ubuntu, I set US (dumb move) - therefore paper format is set to Letter.

I have:
- edited the text of the ppd file
- changed the LC_PAPER variable
- changed the /etc/papersize
- changed default printer config to A4
- changed Open Office language setting to english GB
- even set it manually to A4 before each print

and STILL the machine sends it in letter format which blocks the printer.

This is not so tragic as I can manually change to A4 on the printer, but I must do this every time manually and the printer is on another floor !

Any ideas?

---

### Post by chili555 on 2009-04-01
I'm kinda feeling around in the dark here. I never had to try this, so I reserve the right to be wrong a few times! 

First, did you restart *cups* after you made those changes?```
sudo /etc/init.d/cups restart
```I might also try:```
sudo paperconfig -p a4
```And then restart *cups.*I will keep looking. Please let me know.

---

### Post by kiridude on 2009-04-01
I appreciate your help, especially since you're the only one in these forums willing to take a shot.

I had already restarted my computer, but restarted cups anyway, but to no avail.

And the paperconfig did not change anything.

I have seen other threads where similar issues have been solved by settings I have already changed. I am beginning to think that I may have to do a system re-install...

---

### Post by zyclop on 2009-04-04
we are using the CANON IR 3300 in a travel agency as the network printer. I suggest you check the paper format settings on the panel in the left lower corner of the printer face.
go to the system settings and check for conflicting entries.
consult the manual to check.
if your IP works there should be no reason for the printer to lock up because of format differences.
maybe you want to try switching paper drawers.
Best Regards

---

### Post by robbie60 on 2011-06-04
I have downloaded Ubuntu 10.04 to my netbook and I am loving it until I came to set up my Canon Pixma MP600. In Windows you can download the necessary file fairly seamlessly but how do I do in Unbuntu?
Any help greatly appreciated.

---

### Post by chili555 on 2011-06-04
This is not Windows-simple, but neither is it, as my drinking buddy says, rocket surgery. We'll be glad to help if you get stuck.

[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

FYI, Ubuntu is a Debian-like system.

---

