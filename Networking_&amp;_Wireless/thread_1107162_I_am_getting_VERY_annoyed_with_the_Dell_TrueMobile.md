---
title: "I am getting VERY annoyed with the Dell TrueMobile 1300 Mini-PCI card"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by trecool999 on 2009-03-26
Please, please, please don't tell me to look on Google, Yahoo, Ask etc. because I have, and every thread is outdated and doesn't work for me.

I am quite new at Ubuntu, I know how to write C, C++ and use Windows, but I can only seem to get the hang of using the GUI of Ubuntu, but that isn't very helpful.

I get the hang of running commands, but the one thing I am here for help for is using the Dell card (named in the title).
Now I've noticed that it is actually a Broadcom adapter, and that Broadcom don't release their driver sources.
I've also read about ndiswrapper, fwcutter and all these other supposedly wonderful things that I have no idea how to use.

Has anyone got any newbie, straight-forward instructions that have a 99% chance of working on Ubuntu Intrepid 8.10?

Please and thank you.

---

### Post by trecool999 on 2009-03-26
Bump... Thread is almost on the next page...

---

### Post by trecool999 on 2009-03-26
Why is my thread being completely ignored by everyone and being thrown violently to the bottom of the list?? :'(

---

### Post by stchman on 2009-03-26
> **trecool999 said:**
> Please, please, please don't tell me to look on Google, Yahoo, Ask etc. because I have, and every thread is outdated and doesn't work for me.

I am quite new at Ubuntu, I know how to write C, C++ and use Windows, but I can only seem to get the hang of using the GUI of Ubuntu, but that isn't very helpful.

I get the hang of running commands, but the one thing I am here for help for is using the Dell card (named in the title).
Now I've noticed that it is actually a Broadcom adapter, and that Broadcom don't release their driver sources.
I've also read about ndiswrapper, fwcutter and all these other supposedly wonderful things that I have no idea how to use.

Has anyone got any newbie, straight-forward instructions that have a 99% chance of working on Ubuntu Intrepid 8.10?

Please and thank you.

First thing first.  You will need to have a wired ethernet connection to install packages.


Here is what you need.
1.  Get the Windows drivers for that particular card.
2.  Install ndisgtk package (GUI front end for ndsiwrapper)
3.  System--->Administration--->Windows Wirelss (I believe)
4.  Install driver and navigate to the .inf of the Windows driver.

Your wireless should work.  I don't believe you need to reboot.

---

### Post by trecool999 on 2009-03-26
> **stchman said:**
> First thing first.  You will need to have a wired connection.


Here is what you need.
1.  Get the Windows drivers.
2.  Install ndisgtk package (GUI front end for ndsiwrapper)
3.  System--->Administration--->Windows Wirelss (I believe)
4.  Install driver and navigate to the .inf of the Windows driver.

Your wireless should work.  I don't believe you need to reboot.

Ok, due to my endless searching on Google, I already have the latest ndiswrapper and ndisgtk packages but I haven't got System -> Administration -> Windows Wireless.
I can still access ndisgtk though, if that is what it is, it is just in a different location.
The thing is, I've installed the driver, and the GNOME device manager (which I also had to strangely download) tells me it is a Wifi interface with an installed driver. It doesn't tell me if it is the right one though (I have two, both Broadcom, one USB).

So I'm stuck at that point, and I have no idea how to configure the connection :(.
Thank you for trying to help.

---

### Post by Elfy on 2009-03-26
It's not the best thing to bump your thread 3 times in as many hours - you don't give people chance to see it, we are all volunteering and if it's not seen by someone who knows the answer it will move down the pile.

People look for zero reply threads and bumping means that it won't get seen.

I've not used wireless myself but, the same card was got working in this thread - [http://ubuntuforums.org/showthread.php?t=1010150](http://ubuntuforums.org/showthread.php?t=1010150)



[http://ubuntuforums.org/showpost.php?p=5559815&postcount=1](http://ubuntuforums.org/showpost.php?p=5559815&postcount=1)

---

### Post by trecool999 on 2009-03-26
> **forestpixie said:**
> It's not the best thing to bump your thread 3 times in as many hours - you don't give people chance to see it, we are all volunteering and if it's not seen by someone who knows the answer it will move down the pile.

People look for zero reply threads and bumping means that it won't get seen.

I've not used wireless myself but, the same card was got working in this thread - [http://ubuntuforums.org/showthread.php?t=1010150](http://ubuntuforums.org/showthread.php?t=1010150)



[http://ubuntuforums.org/showpost.php?p=5559815&postcount=1](http://ubuntuforums.org/showpost.php?p=5559815&postcount=1)

That's funny. Most of the support forums just ignore any posts that are on the 2nd page or later lol. That's why I bumped.

Thanks for the link. I'll see if it helps.
I guess I'll have to hibernate XP and get back to you.

---

### Post by trecool999 on 2009-03-26
I have got some very weird stuff going on.
It came up with the error shown in the picture below, so I uninstalled the device manager, ndiswrapper, ndisgtk etc. and reinstalled them again.
Now, when I try to run it again I get the same error and when I do the iwconfig thing it doesn't even come up with "wlan0" anymore!
:'(

[http://img407.imageshack.us/gal.php?g=jesuschrist.png](http://img407.imageshack.us/gal.php?g=jesuschrist.png)

---

### Post by stchman on 2009-03-26
> **trecool999 said:**
> Ok, due to my endless searching on Google, I already have the latest ndiswrapper and ndisgtk packages but I haven't got System -> Administration -> Windows Wireless.
I can still access ndisgtk though, if that is what it is, it is just in a different location.
The thing is, I've installed the driver, and the GNOME device manager (which I also had to strangely download) tells me it is a Wifi interface with an installed driver. It doesn't tell me if it is the right one though (I have two, both Broadcom, one USB).

So I'm stuck at that point, and I have no idea how to configure the connection :(.
Thank you for trying to help.

Do you have the Windows drivers for that card?  If yes there should be a .inf file in the archive.

Use the ndisgtk package and point to that .inf file.  I have used this method on friend's laptops with a decent success rate.

---

### Post by trecool999 on 2009-03-26
> **stchman said:**
> Do you have the Windows drivers for that card?  If yes there should be a .inf file in the archive.

Use the ndisgtk package and point to that .inf file.  I have used this method on friend's laptops with a decent success rate.

[http://img407.imageshack.us/img407/4923/jesuschrist.png](http://img407.imageshack.us/img407/4923/jesuschrist.png)
I get this error when I do it through the terminal as well.

---

### Post by trecool999 on 2009-03-26
HOORAY!!!
I have got the wireless working!
Don't ask how, because I honestly don't know.

---

