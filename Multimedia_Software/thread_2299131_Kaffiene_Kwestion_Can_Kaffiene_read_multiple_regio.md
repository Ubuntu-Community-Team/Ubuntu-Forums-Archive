---
title: "Kaffiene Kwestion: Can Kaffiene read multiple region codes"
date: 2015-10-15
forum: Multimedia Software
---

### Post by heroquestelf on 2015-10-15
I have an anime series that I would LOVE to watch that is available in the UK, but not in the US. They are sold on region 2 DVDs. I read an article saying that Kaffiene would allow you to take a laptop with a region 1 DVDRom and view any DVD from any region. Does anyone know whether or not this is true?

For the record, I'm running a Toshiba Satellite P305 with Trusty Tahr 14.04 LTS.

---

### Post by mc4man on 2015-10-16
Generally speaking region codes are not enforced in linux. However a common laptop dvd drive model does so at the drive level. Most MATSHITA laptop dvd drives will only allow access to css encrypted dvds when there is a region match.
Nothing to be done about that except get a different drive.
```
sudo lshw -c disk
```
look for vendor: in *-cdrom section

---

### Post by Bucky Ball on 2015-10-16
As mentioned above, this is about the optical drive, not the OS. The DVD players for the television are commonly region restricted but never had the problem on a regular laptop/computer optical disk drive.

---

### Post by heroquestelf on 2015-10-24
My DVD Rom is an Optiarc. 

Let me ask a different question then. I was told that a good option would be to get an external DVD rom/reader from a supplier in the UK, but I'm a little worried about getting burned on that end as well. As far as I can tell, I can't find any region codes on any of the external roms... at least, not online. Do the DVD Roms get their region assignment from the machine they get hooked up to? CAn anyone advise?

---

### Post by mc4man on 2015-10-25
> **heroquestelf said:**
> My DVD Rom is an Optiarc. 

Let me ask a different question then. I was told that a good option would be to get an external DVD rom/reader from a supplier in the UK, but I'm a little worried about getting burned on that end as well. As far as I can tell, I can't find any region codes on any of the external roms... at least, not online. Do the DVD Roms get their region assignment from the machine they get hooked up to? CAn anyone advise?

Your current laptop dvd drive should work just fine with any region's dvd.

There is no reason to get an external drive unless you just want one. In that case keep in mind that dvd drives come without any region set, so no reason to buy one from overseas.

There are some minor reasons to set your drive to a region if it hasn't been already done. In your case that would be region 1. If the laptop had ever played a commercial dvd in Windows thru a licensed player than that would have  occurred without you really knowing..

---

### Post by heroquestelf on 2015-10-25
If it has, how do I find out, and is there any way to reset the region code?

---

### Post by mc4man on 2015-10-25
> **heroquestelf said:**
> If it has, how do I find out, and is there any way to reset the region code?

Well as mentioned no need to "reset" the region code if already set. 
To ck. anyway - 
```
sudo apt-get install regionset
```
After installed - 
Place _any optical media disk in drive_, wait for drive to settle & close any popup.

Then in a terminal - (assumes drive is /dev/sr0, if regionset fails then try /dev/sr1
```
regionset /dev/sr0
```

Ex. here - 
> ~$ regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: [COLOR="#0000CD"]SET[/COLOR]
vendor resets available: 4
user controlled changes resets available: [COLOR="#FF0000"]4[/COLOR]
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n



Note that region 1 is set & I have 4 resets until drive locks forever at final set.
So I answer n (no) & that's that...

---

### Post by heroquestelf on 2015-10-25
coooooool.
 [IMG]http://ih0.redbubble.net/image.9959761.6180/fc,550x550,white.jpg[/IMG]

And for the record, my readout was exactly the same as yours. Okay, good. Awesomesauce. You guys rule.

I just wanted to drop everyone an update to again say thank you. My wonderful region 2 DVD's just came in, and while they won't play on anything else in the house, they will play on my wonderful Ubuntu machine. 

WOOT.

[IMG]https://shutteredbutterfly.files.wordpress.com/2013/01/power_up_linux.jpg?w=503[/IMG]

---

### Post by Bucky Ball on 2015-11-05
Glad to see your jubilation! When you've come back to earth, please see the first link in my signature and mark thread as solved. Thanks and enjoy the DVDs and Ubuntu. :)

---

### Post by sammiev on 2015-11-05
> **Bucky Ball said:**
> When you've come back to earth, please see the first link in my signature and mark thread as solved.

:lolflag:

---

