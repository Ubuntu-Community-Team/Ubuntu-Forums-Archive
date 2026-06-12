---
title: "TV Goes Black"
date: 2007-12-10
forum: Mythbuntu
---

### Post by extasy on 2007-12-10
Hello!

I just finnished my installation of MythTV 7.10, everything has been working so far.

My tv card was not autodetected out of the box as some here has clamed I have a   a Hauppauge Nova-T-500 model 289 SL-289-V2.0-UK and I followed these excelent instructions ([http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")). It all have been working and I have scaned for chanels and it has found the chanels in my system. When I then try to watch TV I can se the name of the chanel but it's all black. No sound no nothing.

Anyone can help me?

---

### Post by uopjohnson on 2007-12-11
First things first.  Are you sure your cable is in and working?  Have you tested with another TV?

---

### Post by extasy on 2007-12-11
> **uopjohnson said:**
> First things first.  Are you sure your cable is in and working?  Have you tested with another TV?
Yes, I have a dilog topbox (dvb-t) that I use with my TV I used the same coaxial cabel that goes in to that box and put it in directly to my tv card, so there is no problem with the signal, and I find the chanels doing a search in mythtv, the svideo connection to the computer oviously works cause I can se the picture in mythtv when I'm searching and I have also tried to look at a divX and it works fine.

---

### Post by extasy on 2007-12-13
Not anyone who can point me into right direction?

---

### Post by uopjohnson on 2007-12-13
Sorry, I went googling for info on your card and then got tired.  What you need to do is test the card outside of mythtv by capturing video at the terminal.  The process for this with my card is 
```
cat /dev/video0 > test.mpg
```
and then open test.mpg in another player (mplayer, vlc, xine) I believe that in order to test your card you have to tune it to a working channel first, which I don't know how to do.  I'm sure the info is out there though. Or you may just want to try the above command.

---

### Post by tohc1 on 2007-12-14
I used to use knoppmyth and rememebered that this was a common problem (but not one I've ever had) have a look at...

[http://www.knoppmythwiki.org/index.php?page=BlackScreenWatchingTV](http://www.knoppmythwiki.org/index.php?page=BlackScreenWatchingTV) 

To see if anything helps.

I also have a nova-t 500 I take it you've enabled the onboard amplifier? 

Also are you using over the air listings or xmltv? I've found that TV does strange things after a fresh install that seem to be linked to there being no program data and the over the air grabber slowing things down. So try using xmltv and filling the database - (mythfilldatabase).
I now use xmltv (radiotimes uk) to get data and enable update listings over the air to get schedule changes.

Also testing the card outside myth would be a good idea - but then if you can scan the channels it's probably ok. I think you'll need to use a program to test it like tvtime, as you'll need to get a single channel from the multiplex.

Hopefully something there will work.

---

### Post by extasy on 2007-12-14
Thanks for all help!

Yesterday night I just got so sick and tired of it so I made a new clean install of the system did the guide again and then set it up again, and this time I got the tv functioning!

Now I saw that in the guide it said that some integrated motherboards can have problems with the priority and guess what, I seem to have this problem :( a P4 3ghz and it still don't run perfectly just watching.

It said that one could set the PCI Latency and one could use lspci -v to find the id of the card, well I got a hauppauge wintv nova-t 500 witch identifies itself as a usb card. But how do I know witch card is the right one for the tv card? I got some sis and some via usb devices, how do I know witch one is for the tv card and witch is for the system?

---

