---
title: "Flash - Not Working properly"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-04-10
I just wanted to check if this is an issue or not in NATTY ...... for any other users

FLASH screens in FIREFOX 4 .......... 

They are breaking up with white squares everywhere ....... covering what you need to see.
or is this just because new flash drivers will need to be released for NATTY .........

I tried the same application in [COLOR=Red]UNITY - CLASSIC - KDE - GNOME-SHELL
[/COLOR]
The same thing is happening ....... in each ......


If anybody should want to check the application out .......... go into FACEBOOK ..... Lexolous ....... 

its a scrabble game - 

but it shows the effect quite well ........

__________________________________________________

ABSOLUTELY no problems if I go back to MAVERICK - there are no problems at all.

---

### Post by teachop on 2011-04-10
I am seeing a lot of artifacts - blocky churning artifacts, in the 64 bit beta flash.  I was using 32 bit prior, so I don't know if the problem is Natty or is the Adobe 64 bit beta.  It mostly works, but is a mess sometimes!

---

### Post by VinDSL on 2011-04-10
I just played it in Chromium (accidently).  Oops!

Then, I played it with Fx 4.

No problems with either browser!

BTW, I'm running the **Flash-Aid 2.0.6** add-on in Fx.

This, alone, may fix your Flash problem(s)...  ;)

---

### Post by 23dornot23d on 2011-04-10
I also use 64 bit Natty and 64 bit Maverick with the latest adobe beta flash driver .....

This effect is only happening in NATTY though ....

[IMG]http://img291.imageshack.us/img291/1566/problempk.jpg[/IMG]


Cheers VinDSL ...
BTW, I'm running the **Flash-Aid 2.0.6** add-on in Fx.

I will look this up ...... thankyou for trying it out too ..... ;)

_________________________________________________________________

Update ..... just tried theFlash-Aid 2.0.6 [Addon ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")still the same ...... are you running 64 bit too

---

### Post by dino99 on 2011-04-10
all fine on i386: either flash or gnash work well

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by 23dornot23d on 2011-04-10
Cheers ..... for that ..... my reason for using 64 bit was that is meant to be better and faster with rendering in Blender etc .....

I was just giving the information in case its a 64 bit problem only ....

Not a case of trying to be better than 32 bit ...... as I run both ......

But glad to know its working fine on 32 bit .....  ty ;)

---

### Post by VinDSL on 2011-04-10
> **23dornot23d said:**
> Cheers VinDSL ...

I will look this up ...... thankyou for trying it out too ..... ;)

Update ..... just tried this [Addon ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")still the same ...... are you running 64 bit too?
No, I'm running 32-bit -- actually, because of Flash problems (many years ago in SuSe).  LoL!  :D

Here's how it looks on my 32-bit Natty install...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-10-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-apr-2011.png")[/INDENT]


Nice n' clean!  ;)

---

### Post by 23dornot23d on 2011-04-10
Perfect ..... cheers VinDSL ..... :)

I run both 32 bit and 64 bit Maverick but I am pretty sure this does not occur in them ......
as I play scrabble quite a lot ..... and never had to worry before about running 64 bit or 32 bit.
will double check though ...... as it would be silly not to know for certain .....

**[COLOR=Red]Update :- Double checked and it works 100 % in both 32 bit and 64 bit Maverick ......[/COLOR]**

I may have to install the 32 bit Natty .... alongside this one for the time being  ......... ty

---

### Post by 23dornot23d on 2011-04-10
Just to update this ..... Flash is a problem in 64 bit NATTY only ......

have installed 32 bit just now and it is ok

---

### Post by VanR on 2011-04-10
Had that problem in Firefox and installed flash-aid plugin and it fixed it. Running AMD 64-bit Natty.

---

### Post by CaptainMark on 2011-04-10
i have exactly this same problem and flashaid hasnt helped

---

### Post by 23dornot23d on 2011-04-11
Cheers for the replies and trying it out ......

Same even after I added the [Flash-aid plugin]("http://ubuntuforums.org/showpost.php?p=10660148&postcount=4") for Firefox ..... it still does the same thing ,,,,,

The screen break up happens in 64 Bit and it does it in all of my set-up's UNITY - Gnome-shell and Classic .

---

### Post by tik on 2011-04-11
Purge your current flash-plugin installation completely, add this ppa:

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

and reinstall the nonfree-plugin from the ppa. This fixed the flickering for me on 64bit Natty.

---

### Post by CaptainMark on 2011-04-11
@ VinDSL

i like your conky setup but i gave conky a go a while back and couldnt get my head round it, i was a total noob, know any good conky tutorials for beginners i think i could manage it now,

---

### Post by krazyd on 2011-04-15
> **dino99 said:**
> all fine on i386: either flash or gnash work well

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

That's terrible advice.

64-bit is faster in almost any workload. In some cases twice over as fast. If your CPU supports it, you should use 64-bit.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

The bug is here:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/748764](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/748764)

You can also download the 64-bit version of flash player here:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

Put the 'libflashplayer.so' file in ~/.mozilla/plugins/ and it will override the 32-bit flash player plugin. This fixed the problem for me.

---

### Post by dino99 on 2011-04-15
> **krazyd said:**
> That's terrible advice.

64-bit is faster in almost any workload. In some cases twice over as fast. If your CPU supports it, you should use 64-bit.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)



dont loose your mind with phoromix marketing :(

---

### Post by conualfy on 2011-04-20
Actually it's not only on Ubuntu 11.4, I use 10.10 and I have this bug, but I can't remember the exact time it appeared.

```
cat /proc/version
Linux version 2.6.35-28-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011
```

I did not have it a few days ago, but I tested different configurations: installed a new kernel (buggy: I  it could not install my bluetooth mouse), then uninstalled it; installed LibreOffice (it seems to work better than the standard 10.10 OpenOffice); I "upgraded" the Firefox 4 directory with a localized version by overwriting the files; it might be because of this :D

It's a 64bit Toshiba Satellite laptop, so I'm not eager to "downgrade" to 32bit, I would like to take advantage of the 64bits of the processor.

---

### Post by conualfy on 2011-04-20
Fixed the flash bug (64bits machine): I copied libflashplayer.so ([http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)) to all firefox plugins directories I found (as I don't know which one is "primary", I use them all, there is enough space on the disk)

sudo cp libflashplayer.so /usr/lib/firefox/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-4.0/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/


Tested with the same website 5 minutes ago I had the white squares on the video and it works ok.

---

### Post by 23dornot23d on 2011-04-22
> **tik said:**
> Purge your current flash-plugin installation completely, add this ppa:

[https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")

and reinstall the nonfree-plugin from the ppa. This fixed the flickering for me on 64bit Natty.


Sorry been using 32 bit for a long time - 

Just came back to this and this did solve it ...... and nothing else worked for me ..... flash aid ( nope )

Thanks for all the replies though .......

But the PPA was good ..... now it is flicker free .... and no white blocks ......

ty :D tik

---

### Post by VinDSL on 2011-04-23
> **23dornot23d said:**
> [...] nothing else worked for me ..... flash aid ( nope ) [...]
Sorry for being rudimentary, but...

Did you try the "Expert Mode" in Flash-Aid?

The method that has worked best for me is:

[LIST]
[*]Open Flash-Aid
[*]Go into "Expert Mode"
[*]Tab to "Installation Options" -> Choose "Version and Source: Google, from Chrome" 
[*]Tab to "Script Preview" -> Choose "Refresh" -> Then "Execute"
[*]Close the terminal when it's done
[*]Tab to "Flash-Aid Preferences"
[*]Uncheck "Check for flash updates"
[*]Close Flash-Aid
[*]Close & Re-open Firefox
[/LIST]

The Google version of Flash is significantly smoother, on my machine, than the Adobe versions.  ;)

---

