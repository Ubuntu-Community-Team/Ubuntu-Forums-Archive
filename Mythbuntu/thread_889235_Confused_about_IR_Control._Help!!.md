---
title: "Confused about IR Control. Help!!"
date: 2008-08-13
forum: Mythbuntu
---

### Post by Zipster90 on 2008-08-13
I've just installed mythbuntu on an old machine and I'm able to watch tv with a pretty good picture. However, I have to control my Dish Network 311 receiver with the Dish remote since the PVR-250 card I bought from eBay didn't include the IR reciever. (Had a remote, but no reciever! :lolflag:) 

What I would like to know is if I need to buy both an IR blaster and receiver in order to have the PVR-250 remote control change the channel on the dish box as well as interface with MythTV. I'm also wondering if anyone else has a similar successful setup to this and how they did it. Any help is much appreciated.

All of the features of MythTV look so sweet...but I can't use 'em!:)

---

### Post by nasha on 2008-08-14
You will need an IR-blaster to have the setup you specified. Unfortunately i have no experience with blasters, so i cant offer any help.
Below is a forum search for IR blaster, you'll definately find some helpful information in there.
Good luck!

[HTML]http://ubuntuforums.org/search.php?searchid=46298655[/HTML]

---

### Post by LarryJ2 on 2008-08-14
Even though I had the IR Receiver plugin adapter and the associated remote for my KWorld 110 ATSC card,  I never was able to get it to work with mythbuntu.  

I finally purchased a streamzap remote.  It comes with a USB IR Receiver that sets near my mythbox.  This is supported directly by mythbuntu in the MCC. (Myth Control Center).  This worked right away.  I tweaked the lirccd.conf file so that the volume up / volume down buttons repeat and the red button brings up the "d" or delete menu.

I also purchased a serial blaster that attaches to the serial port on my mythbuntu box. Its supposed to change the channels on my dish receiver. It  works from the command line (terminal window) not otherwise.  Four days and counting!  

Others have had good luck with the MCE USB blaster/remote which I think I noticed was supported in the MCC

---

### Post by rubrboots on 2008-08-14
A homebrew serial irblaster is very cheap or easy to make yourself. My backend is running knoppmyth and the irblaster works perfectly with that. However, I have not yet been able to get a blaster working with Mythbuntu 8.04.1. Hopefully a solution exists.

---

### Post by LarryJ2 on 2008-08-15
Boots:

Have you checked to see if the /usr/local/bin  channel change script is being called?  I concluded the reason my blaster wasn't working is that Mythbuntu was not calling this script.  From the command line (terminal) the  dot sh (bash) and  dot pl (perl) versions work fine after I changed the irsend  line.

Larry

---

