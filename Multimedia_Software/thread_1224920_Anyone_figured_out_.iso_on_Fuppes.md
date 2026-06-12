---
title: "Anyone figured out .iso on Fuppes?"
date: 2009-07-27
forum: Multimedia Software
---

### Post by R.Bucky on 2009-07-27
Has anyone figured out how to play iso's using fuppes? I have an Ubuntu Server 8.04 install. I know that FreeNAS has support... 

Anyone figure this out?

---

### Post by Shhnap on 2010-01-28
Hi, I know that this answer has been a long time in coming but that is because playing iso files is not something you want to do on any media server and therefore no one will know how to do it because no one would have. But I am not shutting you down, just let me explain how to solve your problem. :)

A .iso file is a CD Image file, and this time it is not the kind of image that you look at or set as your wallpaper. Here 'image' means 'perfect copy of other data'. Therefore the .iso file contains data that you may want to play but it is not in any format (yet) that Fuppes can play.

What you want to do is burn that .iso file to a CD (maybe using 'brasero') and then extract the media you want off the CD (maybe using 'dvd-rip' if it is a dvd). Then when you have video files of the cd like .avi or sound files like .mp3 then fuppes can stream them to and media device you like.

And that is all there is to it. :) If you need more help please feel free to ask.

BTW: So that your question get's answered in less than six months next time have a read of this: [http://www.catb.org/%7Eesr/faqs/smart-questions.html#goal](http://www.catb.org/%7Eesr/faqs/smart-questions.html#goal) It's really good advice that page and I found it very useful. You should read it all if you have the time.

---

### Post by glamajamma on 2011-03-14
For anyone else stumbling across this thread like I did, please DO NOT burn ISOs to get the data off of them.  You can easily mount them and get the data off:

sudo mount -o loop /location/of/iso/file/foo.iso /location/to/mount

We don't need more CDs in our landfills.

---

