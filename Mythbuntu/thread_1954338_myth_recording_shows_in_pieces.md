---
title: "myth recording shows in pieces"
date: 2012-04-07
forum: Mythbuntu
---

### Post by sqeelurgle on 2012-04-07
My myth box has started recording shows in pieces, which is very annoying.  The pieces seem to go anywhere from about 2 minutes up to 45 or so.  What seems to have started this is that my network connection has always been poor.  It cuts out every few minutes.  Last night I wanted to watch an internet stream on the TV, so I installed WICD instead of the default network manager.  Brilliant! for the first time this computer has reliable wireless.  Problem is that ever since the recordings have been done in pieces.  Now, the obvious solution (which I will do if necessary) is to uninstall WICD and go back to network manager.  If there is anyway that I can keep reliable wireless and still have recordings in one piece though that would be better.  Does anybody have any ideas to try, or suggestions as to where to start looking for the problem?  Running on Mythbuntu 10.04

Thanks

---

### Post by nickrout on 2012-04-07
Likely that wicd taking your network up and down is interfering with the backend running (the backend is dependent on the network).


Wireless is pretty hopeless for a backend, wire it and get rid of wicd.

---

### Post by sqeelurgle on 2012-04-08
Where my system is located, I think I would have to run a cable down 2 walls and down a stairwell.  Not so good aesthetically.  I doubt my wife would approve.  I could get it wired through the walls by an electrician, but the cost would prevent that.  WIreless it is.

---

### Post by nickrout on 2012-04-08
You could try powerline networking.

Or you could sort out why your wireless is dodgy, it shouldn't be.

---

### Post by sqeelurgle on 2012-04-08
From what I can work out, wireless dropping out regularly seems to be a common issue using network manager.  I am not sure if it is an issue just with my wireless chipset, or more common than that.  I suspect more common than just my chipset from what I have seen.  Anyway WICD manages the wireless perfectly (I watched a 1 hour live stream on the net the other night without it dropping out at all) but then I get the problems with recordings being done in pieces.  BTW, I should have mentioned that this is a BE and FE one the one machine.

---

### Post by uncle hammy on 2012-04-08
You seem to have glossed right over the excellent suggestion from Nick.  What about power line networking?  [http://www.newegg.com/Product/Product.aspx?Item=N82E16833181127](http://www.newegg.com/Product/Product.aspx?Item=N82E16833181127)

The other option is are you able to move your networking gear (modem, router, etc) to the location of your BE and then use wireless in the other areas of your house?

Running a BE (whether it's a BE/FE or just a BE) over wireless is not ideal, regardless of how stable your wireless is.

---

### Post by nickrout on 2012-04-08
Of course it may be nothing whatever to do with networking. Try looking in your backend logs. That is what they are for.

---

### Post by sqeelurgle on 2012-04-08
I removed WICD, and went back to network manager.  That fixed the mythtv recording problem, but the network is problematic again.  I will look in the backend logs though - just in case there's something that gives me a clue.  I was hoping to get away without spending any money to fix this issue, but the powerline network would be a convenient solution with not too much expense if it comes to it.  I am also going to try using a USB wifi adapter in place of the current PCI card in case that does something for me.

---

### Post by sqeelurgle on 2012-04-09
Hm, replacing WICD seems to have kept decent wireless as well as fixing the recording issue.  I guess that WICD must overwrite something when it installs, that doesn't get overwritten again when network manager installs.  Anyway, happy so far.

---

### Post by nickrout on 2012-04-09
> **sqeelurgle said:**
>   I guess that WICD must overwrite something when it installs, that doesn't get overwritten again when network manager installs.  

I doubt that, but the beauty of open source is that you can work that out for yourself :)

---

