---
title: "New to ubuntu and can't get soft modem to connct"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by lonewolf454 on 2008-12-22
I have a Gateway MT3707 with a softmodem on the soundcard.  I have tried for last several months to get it to connect, but no luck setting up.  I have attached ModemData.

---

### Post by ieee488 on 2008-12-23
I don't believe that you will be able to get that softmodem to work.

It is very similar to situation with my IBM Thinkpad 600E which has a DSP chip does both sound and modem duties.

If you really need dialup, your best bet is to buy a PCMCIA modem. I bought a couple of used ones from eBay that works in Linux.

---

### Post by jimmy the saint on 2008-12-23
You can get a zoom hardware serial modem new for ~60 bucks.  That would work without really having to configure anything except your connection.

---

### Post by ieee488 on 2008-12-23
I researched more and found that that model laptop has a ExpressCard slot and not a PCMCIA slot.

So, if you are going to need dial-up modem, you'll need to buy a USB modem that works with Linux or by an Express card modem (if they exist). You can also try an external serial modem but I'm not sure that laptop has a serial/COM port.

---

### Post by jimmy the saint on 2008-12-23
Oh man, I am kind of silly for missing that!  most laptops don't have serial ports so a serial modem probably wouldn't work.  Sorry about that!

---

### Post by ieee488 on 2008-12-23
It depends on how old the laptop is.
The newer ones don't have either serial or parallel port.

I was able to get the ACP modem on my Thinkpad600E to work in Red Hat 8 by muddling around. IBM had some files to help out. Recently someone tried to get it to work in PuppyLinux 4, but it was no go.

The long and short of it is that "modems" from DSP chips will have very hard time of it in Linux without help from the vendor.

---

### Post by _duncan_ on 2008-12-24
Take a look at [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1016821") thread. Apparently there are some USB hardware modems that work quite well with linux. The 2nd post (by ModelM) may interest you.

If these models are unavailable to you, your best bet will be to use a USB-to-serial converter in conjunction with an external hardware modem. The serial modem part should be easy as most will work with linux. However I've seen posts here claiming not all USB-serial converters will work.

---

### Post by lonewolf454 on 2008-12-24
I have been hard at it and have actually been able to make it dial isp.. I dont know if init string is screwy or what, the isp peoplepc accepts password and id but then disconnects.  So I will try for a little longer.  BTW It didnt come with any serial ports, parallel, etc.  Only 3 usb and a VGA d shell, guess I got what I paid for for 500 bucks.  Modem works fine under Vista, like that matters.

Thanks for suggestions thus far, if someone can help me get it to stay connected or recommend for init string, please reply.  Also, if I power down/power back up I again have to load modules sudo modprobe agrmodem,etc and sudo ln -s /dev/ttyAGS3, etc. or else it wont find when I wvdial.  Is there a way to save this?

---

### Post by Bartender on 2008-12-26
First thing to do is dump PeoplePC.  Since they insist on using proprietary software to connect, PPC should not work at all in Linux.  I've read one or two posts from people who claimed to have gotten connected, but I'm skeptical.
So, drop PPC and go with frys.com or copper.net or any other ISP that works with Linux.  If you call them and ask, they may say they don't "support" Linux, but that only means they don't want to deal with your questions.  It doesn't mean that a Linux PC can't dial in and connect.
Then get a USR 5637 USB modem.

---

### Post by ieee488 on 2008-12-26
AT&T Worldnet works with dial-up in Linux too, before I switched to Verizon DSL.

You'll probably have same problems with dial-up with Netzero too since they have a custom dialer. I tried dialing in on their free account, but it disconnected me immediately.

---

### Post by lonewolf454 on 2009-01-04
In contrast and to the defense of PeoplePC (they need it and there is undoubtably better ISP's) I have set up an internet connection working ok on another computer with an Intel 536EP soft modem.  So it does lead one to believe it is a driver/config problem and notsomuch a problem on the ISP's end. Thanks for suggestions.  We have AT&T for local phone service here and they won't even offer DSL.  I would never buy dialup from them and have cut my phone service with them to bare bones. AT&T are money grubbers whose time appears to be passing them by as they sit back and watch, arrogantly.

BTW - I did away with the PPC dialer software within the first month.  Dialing in without it is not a problem, internet connections are just like any other, only much slower (20kbps)(536EP) and not working (HDA modem)...

---

