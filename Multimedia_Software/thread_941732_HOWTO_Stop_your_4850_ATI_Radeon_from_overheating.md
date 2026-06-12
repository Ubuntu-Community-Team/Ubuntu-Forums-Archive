---
title: "HOWTO: Stop your 4850 ATI Radeon from overheating"
date: 2008-10-08
forum: Multimedia Software
---

### Post by porchrat on 2008-10-08
Greetings netizens of Ubuntuforums.

I don't know if any of you realise this, but the early release HD4850 Radeon cards from ATI have a firmware issue that prevents the fan from coming on when the card builds up heat.  As a result a lot of people are running their machines with 4850 cards idling at around 80 degrees celcius.  This is quite dangerous and could damage your graphics card, and perhaps other components as well.

I have created this HOWTO to help inform people of the problem and to offer a workaround that, while a little inconvenient, will at least protect the card until ATI can sort this out.  Note that this problem seems not to effect cards other than the 4850, however it never hurts to check these things, so by all means follow this guide if you would like as it will work for any of the newer ATI cards.

Firstly I first learnt about this issue from this thread:
[http://ubuntuforums.org/showthread.php?t=861718]("http://ubuntuforums.org/showthread.php?t=861718")

Please feel free to read it.

The first thing that you need to do is install the latest version of the ATI catalyst driver.  You need the latest driver (or at least any catalyst driver version 8.7 or above) as it is the only driver that contains the temperature checking and fan setting commands required to ensure the safety of your 4850.  The guide that I found the most informative and the most helpful is this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Please follow the instructions under: "Method 2: Manual Method (installing Catalyst 8.8 or 8.9)".  You will have the drivers installed and running in no time at all.

Now that the drivers are installed lets check the temperature of the card.  We do this using this command:

```
aticonfig --adapter=0 --od-gettemperature
```

If your card is experiencing this heating problem it should be a high temperature (mine was around 75 and within a minute or so had the temperature had risen to 81 degrees celcius).  If your card is cool (normally around the high 30's) then don't worry, your card is functioning properly.

If your card is running hot then you need to set the fan speed manually to cool the card.  To do this use this command:

```
aticonfig --pplib-cmd "set fanspeed 0 65"
```

Replace the "65" with whatever number is ideal for your 4850.  The speed you require will depend on the temperature of the room, how much ventilation your PC gets etc.  The higher the number the faster your card's fan will spin.

Note that this command cannot be incorporated into the /etc/init.d/ directory and then linked to the rc.d system.  It also cannot be appended to the /etc/rc.local file either.  To my knowledge there is no way to make this command run at startup.  Therefore you will need to execute the command to start the fan everytime you boot the system.

I would recommend you create a script file and place it on your Desktop so that you remember it.

If anyone has any firther queries please don't hesitate to ask, hopefully there is a solution out there that I am currently unaware of.

Take care
porchrat

---

### Post by porchrat on 2008-10-23
OK I have been introduced to a much better fix for this problem from an insightful ubuntu user (nitrousoxide82).

The problem was that this script can't execute unless X is running.

Basically the fix is this simple:

Take the script I mentioned in the previous post and move it into /etc/X11/Xsession.d/ using this command:

```
sudo mv /path/to/the/script /etc/X11/Xsession.d/
```

Then just to be safe make sure you change ownership to root, and set permissions to match that of the rest of the files in that directory:

```
sudo chown root:root script_name
sudo chmod 644 script_name
```

Also you may want to remove the .sh extension as it isn't needed here.

Hopefully this helps.

Regards
Porchrat

---

