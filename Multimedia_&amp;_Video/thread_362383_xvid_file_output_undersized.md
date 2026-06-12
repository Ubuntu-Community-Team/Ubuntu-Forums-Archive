---
title: "xvid file output undersized"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by 1917oct on 2007-02-15
I'm running a 386 based dapper on a p4 1.8g

I have been tinkering for days now trying to make mencoder (through acidrip) output an xvid.avi with the correct file size (or at least close to it) indicated in acidrip.  Consistantly, the file size is undersized.  An encode indicated to be 900mb will be nearly haf that size (between 500 and 650mb.)

I have re-installed mencoder, reinstalled mplayer, edited xvid config, and still no dice. 
I re-installed acidrip, and that fixed the cropping bug. But still I get undersize encodes. 

It's all dapper repository installs, no cvs, (i'm a supern00b.)

Anyone have any suggestions?

---

### Post by disturbedite on 2007-02-15
instead of using quantizer use "two pass final size".  i wish i could give you the command but i can't seem to remember it for "two pass final size" cuz i never use it.  i'd google it if you don't know it.

---

### Post by 1917oct on 2007-02-15
I took a look around google, and haven't really found the second pass final size option... 
But I did find a lot of other useful things :| 

I'll take a more thorough look tonight, because it sounds exactly like what I'm looking for.

---

### Post by disturbedite on 2007-02-16
i'd try [doom9]("http://www.doom9.org/") and its forum.  its a great place for all things multimedia when it comes to software. and other stuff too.

---

### Post by 1917oct on 2007-02-16
Yes, actually i'm familiar with the doom9 forums, as I am a windows user trying to move to linux.  I've gone there many times for for agknot help.. it I can't solve this problem soon, I may post there... 

thank you for the advice though

---

### Post by protorox on 2008-04-19
I had the same exact problem...

It's a bug in AcidRip!

I finally found a solution...

1) Load the DVD as usual
2)** DON'T SPECIFY THE FILE SIZE USING A KEYBOARD INPUT - INSTEAD USE THE ARROWS!**
3) After you've reached the desired filesize, go to the "Video" tab and click the "Lock" checkbox next to the bitrate textbox.
4) Finally, review all your settings and click "Start".

I hope this helps!

---

