---
title: "Problem with blank screen at login..."
date: 2009-04-30
forum: Multimedia Software
---

### Post by Humanv013 on 2009-04-30
I recently installed the 64-bit version of Ubuntu 9.04 and have been having tremendous issues with installing the Nvidia drivers.  I've made some progress but it's still not working right and I'm at a complete loss as to where to go from here.

Here's my problem. Perhaps someone can point me in the right direction:

•I freshly install Ubuntu 9.04

•I then run the update management thing.

•Then I decide to try another go at using Ubuntu's "jockey" thing to download and install the nvidia 180 drivers.

•As I've tried this method many times before without success, I decide to try a suggestion I found in these forums to add a BusID and some other lines in xorg.conf to specify various options and whatnot.

•The result of doing this brings me to my current dilemma.  My system seems to boot up normal without any problem, except that once it gets to where it would show the login screen, goes blank. But the odd thing is, is that I can still hear the bongo sound that plays by default... plus if I type in my user name and password like normal it will play the default login music as if everything is normal... but it isn't.  I still can't see a thing on my screen.  

I AM able to Ctrl+Alt+F1 to the text command line and Ctrl+Alt+F7 back to what is supposed to be the GUI like normal, but like I said it displays nothing.

Perhaps someone out there has some suggestions for me or perhaps can point me in the right direction. I would really appreciate it.  If you need more info, I'll do the best I can to provide it and work with you, but I should warn you, I'm fairly new to Ubuntu and Linux so you'll have to bear with me.

---

### Post by instinct46 on 2009-04-30
dunno if this will help but, press CTRL + ALT + F2

then login and type this into the shell:

*sudo apt-get install update*

and then:

*sudo apt-get install upgrade*

may just be an old version of certain drivers conflicting, hope this helps.

---

### Post by Humanv013 on 2009-04-30
Thanks for the response, instinct46. 
I wasn't sure that that would help either, but I figure it couldn't hurt to try. But when I use those commands it doesn't return anything.  For both of them it says:

E: Couldn't find package update  <--(or upgrade in the case of the other command)


Also I came across another thread that seemed to have a very similar problem that I do ([http://www.neowin.net/forum/index.php?showtopic=609706](http://www.neowin.net/forum/index.php?showtopic=609706)).  I went ahead and tried doing what what had been suggested (Ctrl+Alt+[+/-]) but nothing changed from that either.

For your information this is my setup:

Asus M2N-SLI Deluxe Motherboard (Nvidia nForce 570 SLI chipset)
AMD Athlon 64 X2 2.2GHz processor
4 GB RAM
two Nvidia GeForce 8600 GT graphics cards

Not sure what other system info people might need to know but there's the basics.

---

### Post by KnowBS on 2009-07-29
Did you ever get the problem solved? LMK.

---

### Post by rustypipe on 2009-07-29
I have the same problem of black screen with pointer after a successful login.

Using option in lower left corner, I opted for "failsafe Gnome" session, and received the following error message:

"There is a problem with the configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

Any light on this message, and does it help us solve the black screen issue?

Thanks

---

### Post by igorzwx on 2009-07-29
Do you think your problem is unique?
[http://www.google.com/search?q=ubuntu%20%2Fusr%2Flib%2Flibconf2-4%2Fgconf-sanity-check-2%20exited%20with%20status%20256&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=ubuntu%20%2Fusr%2Flib%2Flibconf2-4%2Fgconf-sanity-check-2%20exited%20with%20status%20256&ie=UTF-8&oe=UTF-8)

---

### Post by KnowBS on 2009-07-29
I'm sorry I don't understand your link? I've seen tons of people with this problem or ones similar to it, but I've tried all the suggestions I've found and nothing has worked.

---

### Post by igorzwx on 2009-07-29
I seems that it is not solved yet.

---

