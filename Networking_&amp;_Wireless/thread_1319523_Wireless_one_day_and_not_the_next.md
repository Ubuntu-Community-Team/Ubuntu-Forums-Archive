---
title: "Wireless one day and not the next?"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Draclvr on 2009-11-08
Finally have time to play with Linux and downloaded Ubuntu 9.10.  Set up my wireless, connected to the internet and was having a great time figuring things out.  Powered down for the night and when I booted up the next morning, no internet.  It "sees" my SSID, but keeps asking for my WEP key - time after time after time - with no results (I think I know the 128-bit WEP key by heart).  I deleted all instances of a wireless connection and started from scratch several times.  No luck.

For other reasons, I have regretted the Linksys WMP 110 wireless PCI adapter I put into this build I did last spring for my other hard drives, but it seems curious that it would work just fine and then 10 hours later stop working.

I'll keep searching the forums for an answer, but hoped someone might have a direction to point me to...

---

### Post by Draclvr on 2009-11-09
Help!  Nothing I've found on the forums works!

---

### Post by rpras on 2009-11-09
> **Draclvr said:**
> Help!  Nothing I've found on the forums works!

If you can stand typing into the terminal, try the instructions here: [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html).  This set of instructions finally got me going.

Good luck.

---

### Post by Draclvr on 2009-11-09
Thanks so much rpras.  I checked out your link and hopefully, it will get me going.  Now that I have time, I'd really like to get to know this OS...

---

### Post by Draclvr on 2009-11-10
Well, that didn't work either.  When using the terminal for the WEP connection key, I got an error at the sudo iwconfig (name of my interface) "essid" command.  The error state insufficient arguments (or something like that - it was late last night).  After that error, nothing worked any further and I finally gave up in frustration.

Maybe if I get away from it for a day, I'll dive back in.  This is starting to not be worth the trouble.

---

### Post by rpras on 2009-11-14
> **Draclvr said:**
> Well, that didn't work either.  When using the terminal for the WEP connection key, I got an error at the sudo iwconfig (name of my interface) "essid" command.  The error state insufficient arguments (or something like that - it was late last night).  After that error, nothing worked any further and I finally gave up in frustration.

Maybe if I get away from it for a day, I'll dive back in.  This is starting to not be worth the trouble.

Don't give up.  It will work.  You have to be very careful with the typing though.  Since you would need to type the commands multiple times, one way to avoid errors and resulting frustration is to create a script.  Just save the commands in a text file -- name it what you like -- and carry out a 'chmod 700 <filename>' on it.  After that you'll just need to run that file -- './<filename>'.

But I know what you mean -- I needed to 'get away' from the problem quite a few times.  #-o

---

