---
title: "Linux driver for ATI Radeon 9200 video card"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2007-12-08
Am I correct that even though a "Linux driver is shown for the ATI Radeon 9200 video card" on the ATI technologies website (please see attached screenshot), that the driver that this ATI screen takes you to will NOT support the 9200 or at least not on Ubuntu Gutsy ???

And if that is the case then why the *$@)$$(@$, don't they take that off of there so people are not confused by it, unless it is that it will work on other Linux O/Ss but just not Ubuntu Gutsy ???

Thanks.

---

### Post by atlfalcons866 on 2007-12-08
hi
try using envy. envy will automatically install the driver

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by wpshooter on 2007-12-09
> **atlfalcons866 said:**
> hi
try using envy. envy will automatically install the driver

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

NO IT WON'T, I tried it.

ENVY used to work with this card but when I try it now, I get a terminal message which says that this driver is not compatible with your O/S.

Thanks.

---

### Post by acoustibop on 2007-12-09
Because if you select a card that the current 7.11 driver doesn't support, it will take you to the page for the 8.28.8 driver, which is the last fglrx driver that will support your card, wpshooter.

---

### Post by wpshooter on 2007-12-10
> **acoustibop said:**
> Because if you select a card that the current 7.11 driver doesn't support, it will take you to the page for the 8.28.8 driver, which is the last fglrx driver that will support your card, wpshooter.

I really don't understand what you are talking about.  Can you expound upon this ?

When I downloaded ENVY and then installed the packages for it and then choose to run ENVY from the menu listing where it is installed, I simply get an error message in the terminal saying that my O/S, (i.e. Ubuntu/Gutsy) is NOT supported.

I don't see anything that directs me to any other source for the proper driver for my ATI Radeon 9200 video card.

Thanks.

---

### Post by acoustibop on 2007-12-10
I answered your original question, wpshooter:
> **wpshooter said:**
> Am I correct that even though a "Linux driver is shown for the ATI Radeon 9200 video card" on the ATI technologies website (please see attached screenshot), that the driver that this ATI screen takes you to will NOT support the 9200 or at least not on Ubuntu Gutsy ???
If yo select a card on the ATI page that the current 7.11 driver doesn't support, such as your Radeon 9200, then you won't be directed to the download page for the 7.11 driver.  You'll be directed to the download page for the 8.28.8 driver, which is the last fglrx driver that supports cards such as yours.

I don't know how to explain it more clearly than that.  I can only suggest you go to the ATI driver download page, select Linux x86, then Radeon, then ATI Radeon 9200 series, and click GO.  Since you don't appear to understand what I said, I can only assume you haven't tried it.

---

### Post by wpshooter on 2007-12-10
> **acoustibop said:**
> I answered your original question, wpshooter:

If yo select a card on the ATI page that the current 7.11 driver doesn't support, such as your Radeon 9200, then you won't be directed to the download page for the 7.11 driver.  You'll be directed to the download page for the 8.28.8 driver, which is the last fglrx driver that supports cards such as yours.

I don't know how to explain it more clearly than that.  I can only suggest you go to the ATI driver download page, select Linux x86, then Radeon, then ATI Radeon 9200 series, and click GO.  Since you don't appear to understand what I said, I can only assume you haven't tried it.

Sorry.  The vain of my post had switched to ENVY from the original question about the ATI website.

But yes, I had chosen Linux/Radeon/9200 at their (ATI's site) and when I download what they show for that card and then try to run it per the instructions on their website, it will NOT run.

Thanks.

---

### Post by acoustibop on 2007-12-10
There have been reports of the ATI installer successfully installing the 7.11 driver, wpshooter, but AFAIK it's not considered a good method of installing fglrx drivers.  I'm not sure how you would go about installing the 8.28.8 driver, as it's contemporary with Dapper.

However, it's possible that if you try the Restricted Drivers Manager, it may offer you the 8.28.8 driver - or at least, if it offers to install a driver for you, that should be the 8.28.8 driver.

And the bottom line is, if you want an fglrx driver for your card, the 8.28.8 driver is the one.  No later drivers support your card.

---

### Post by wpshooter on 2007-12-10
> **acoustibop said:**
> There have been reports of the ATI installer successfully installing the 7.11 driver, wpshooter, but AFAIK it's not considered a good method of installing fglrx drivers.  I'm not sure how you would go about installing the 8.28.8 driver, as it's contemporary with Dapper.

However, it's possible that if you try the Restricted Drivers Manager, it may offer you the 8.28.8 driver - or at least, if it offers to install a driver for you, that should be the 8.28.8 driver.

And the bottom line is, if you want an fglrx driver for your card, the 8.28.8 driver is the one.  No later drivers support your card.

Thanks.

I have tried the restricted drivers manager function but it say that there are NO restricted drivers available/needed for my hardware.

I have tried installing the fglrx drivers thru synaptic BUT the machine definately did not like this because after changing the driver from ati to fglrx in the xorg.conf file, the machine would only load X in a very low resolution mode upon reboot and I could find no way in the configuration process that was offered to get it to run at the resolution that my card and monitor are capable of running.

I have e-mailed the writer of the ENVY program.  Maybe he can tell me why his program will not seem to work with this card and Gutsy.

Thanks, again.

---

