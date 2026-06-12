---
title: "iPhone 3G works, iPhone 4 doesn't.."
date: 2011-01-14
forum: Multimedia Software
---

### Post by helios16v on 2011-01-14
My iPhone 3G works great with ubuntu, it deleted my playlists a few times but after I updated from 4.0.2 to 4.1 it hasn't done this again. However my iPhone 4 with 4.2.1 will not even connect to the computer, an icon wont even display and I get this error message every time it's plugged in. I just jailbroke my iPhone 4 in hope that this would make it work as I read somewhere that only jailbroken iPhones work on ubuntu and I can confirm this is not true as it still wont work.

This is the error message I reveive every time I plug my iPhone 4 into my laptop, I need to bring both phones around with me because my music is all still on my 3G lol.

[IMG]http://i426.photobucket.com/albums/pp349/helios16v/god%20dammit/Screenshot-UntitledWindow.png[/IMG]

I'm thinking of formatting, Installing Windows 7, and dual booting ubuntu on it just so I can sync my music onto my iPhone 4

**EDIT:**
I'm going to update my iPhone 4 to 4.3 Beta as I'm signed up for the DEV program and Jailbreak it to see if it's just a problem with firmware 4.2

---

### Post by Dammy on 2011-02-17
[http://ubuntuforums.org/archive/index.php/t-1628529.html](http://ubuntuforums.org/archive/index.php/t-1628529.html)

check this out for a fix

it worked for me on 32GB iPhone 4 on 4.2.1.



This is what the fix is essentially.

Open Terminal and run :

sudo add-apt-repository ppa:pmcenery/ppa

then:

sudo apt-get update

and

sudo apt-get upgrade
  
If that still hasn't worked, install libimobiledevice-utils by typing:

sudo apt-get install libimobiledevice-utils

Still hasn't worked? Run this:

idevicepair unpair
idevicepair pair
idevicepair validate

Good luck! :)

---

