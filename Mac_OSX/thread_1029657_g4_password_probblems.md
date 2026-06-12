---
title: "g4 password probblems"
date: 2009-01-03
forum: Mac OSX
---

### Post by ChanServ on 2009-01-03
Hello fellow forumer's,

I have recently obtained an old imac g4 from a garage sale.  700Mhz and 125 MB's for a nice amount of 0$ :D

Anyway, It dident exactly come with a reinstall disk so, I figured I'd half to make do with creating a new user and working on the existing install. But the problem still lies that I do not know the root password on it. ;_;  Looking on the previous users leftovers, the password hint is listed as the plural form of a female dog (edited by me for the forums purposes :P).  The rest of said users files had been deleted, except for their web browsers history. Which showed me (among other things) that this computer hadn't been used in years, so it's not like I could just go back and ask for the password (they also moved, so that doesn't help).  

/Anyway/...  that brings me to my question, What can I do to guess/decrypt/unlock the password? I understand that there is some legality issues involved, but I'm sure that it is better than stealing OS9, as I assume that leopard will not run on this. 

Thank you,
-ChanServ

(note to mods, if you feel that this thread oversteps the forums boundaries, then I apologize, and you may delete it.)

---

### Post by NoSmokingBandit on 2009-01-03
If its running OsX (idk anything about OS9), open a terminal and type this:
rm /var/db/.applesetupdone

You might need to sudo that, idk. What happens is that when osx is done with all of its fancy "welcome to osx, lets set up an account" stuff it makes this little file. When you boot it up it looks for that file, if it exists it will assume you already have an account, if it doesnt exist it assumes you have never booted this os before and lets you create an Admin account right away. From there you can delete the other accounts (or look at their files :P )

---

### Post by MikeTheC on 2009-01-03
FYI:

The iMac in question will "normally" run a maximum of Mac OS X 10.4.x. Those iMacs take PC-133 RAM, and I believe the 700 should take 1GB max. However, they use a combination of 1 stick of desktop PC-133 and 1 stick of notebook PC-133.

[This page on xlr8YourMac.com](http://www.xlr8yourmac.com/systems/imac_g4/imacg4_takeapart.html) gives the complete take-apart process for that unit, which you will need should you want to not just fully upgrade to max RAM, but change out the HDD or optical drive.

Please use caution in taking the computer itself apart. Amongst other things, the G4 heatsink/fan assembly is mounted to the top of the case, and improper removal or re-assembly can potentially do damage. Also, be mindful of all internal cabling going up the boom to the LCD.

Good luck!

FWIW, you can also obtain Ubuntu PPC for it, but I really wouldn't recommend it because support for Apple's semi-custom hardware compromise the F/OSS community's ability to fully support it. (But I have tried it and it will work.)

AFWIW, when you take off just the bottom panel, you will have immediate access to the Airport socket (basically a customized PC-MCIA card) and you may still be able to get either an Apple or 3rd party compatible equivalent for it, should you want to have wireless capabilities. I would recommend you stick with the Apple Airport because it will be far better supported than what you generally find with 3rd party wireless products for Mac OS X or Mac OS 9.

---

