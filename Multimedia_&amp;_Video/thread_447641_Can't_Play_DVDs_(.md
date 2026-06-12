---
title: "Can't Play DVDs :("
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by Corey on 2007-05-18
I simply cannot get a DVD to play for the life of me. I've installed the libcss packaged. but totem, vlc, mplayer and xine all fail me. When I try to play a DVD in vlc nothing happens. the Play DVD disc option in totem is always grayed out. When I put a disk in, an icon shows up on my desktop, but it says the disc is empty and there is no option to play it. I've tried multiple DVDs but no luck. Please help! I spent 3 days setting up twinview and xinerama etc so that I could play dvds on my tv in my bedroom and now this! lol.

---

### Post by ntetreau on 2007-05-18
This is a very strange problem you have.  Perhaps you could elaborate on the hardware you use?  What else doesn't work with your drive?  Can you read CDs fine?  Read/write CDs?  I mean is it a problem you have only with DVDs?  How about trying to start VLC from a terminal and looking at the output while trying to play a DVD?

---

### Post by Kobalt on 2007-05-18
When you write > I've installed the libcss 
Do you mean you installed the libdvdcss2 package ? From where ?
Are you trying to read regular dvds or are these home made dvds ? Pal/Ntsc ? etc...

---

### Post by rggavubt on 2007-05-18
You didn't say what version of Ubuntu you are on??  I'm having the same problem since I upgraded to Feisty.  I could play DVD's in Dapper.  My DVD and CD sections are also grayed out??  I posted my own thread and so far no answers.  I went to places/computer and tried to mount my DVD-ROM with a movie in it and it will not mount.  I think it is some problem with my /etc/fstab file but I can't correct it.  I issued a bug #114816 but so far no replies??

---

### Post by stchman on 2007-05-18
> **Corey said:**
> I simply cannot get a DVD to play for the life of me. I've installed the libcss packaged. but totem, vlc, mplayer and xine all fail me. When I try to play a DVD in vlc nothing happens. the Play DVD disc option in totem is always grayed out. When I put a disk in, an icon shows up on my desktop, but it says the disc is empty and there is no option to play it. I've tried multiple DVDs but no luck. Please help! I spent 3 days setting up twinview and xinerama etc so that I could play dvds on my tv in my bedroom and now this! lol.

Follow the procedure laid out on my website for playing encrypted DVDs.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This works for both Edgy and Feisty.  It installs the medibuntu codecs and the CSS decryption for watching Hollywood DVDs.

---

### Post by Corey on 2007-05-24
Sorry for the delay. Was outta town babysitting my parents dogs. 

I'm running Feisty.

These are regular DVDs not burnt ones, and I've tried a number of them.

I did mean libdvdcss2. (my bad, typin' in a hurry) I got it from medibuntu repos which were mentioned in the multimedia howto.

The hardware shouldn't be the issue. It is a plextor DVD burner. It has no problem with audio or data CDs and in fact burnt and read the very DVD i used to install ubuntu.

Still not workin' 

](*,)

---

### Post by stchman on 2007-05-24
Did it work?

---

### Post by Bablefish on 2007-05-24
I can't play them either and I am talking about one that was made by one of thosevideo cameras that burn directly to a DVD. But I do know the command line Corey is talking about I found it in the Help section right in Ubuntu itself

sudo /user/share/doc/libdvdread3.install-css.sh

---

### Post by Virgilius on 2007-05-25
I tried what was recommended here on mine (Edgy) and it worked like a dream! and plus it was a simple thing to do :) Thanks heaps :)

---

### Post by treacle boy on 2007-06-01
Stchman, That's a brilliant site, Cheers!
Linux 1: Windows a big fat 0!

---

### Post by stchman on 2007-06-11
> **treacle boy said:**
> Stchman, That's a brilliant site, Cheers!
Linux 1: Windows a big fat 0!

Thanks, I like to help others get their Ubuntu up and running well.

---

### Post by Tim.Baron on 2007-11-29
Alright Mr stchman, 

I have to say thank you! I actually just registered on this website so I could post a reply and say thanks (that and it will come in handy in the future lol). Anyways I have tried at least three different online tutorials and spend at least an hour or two trying to get dvds working, I finally gave up on it. Well I stumbled accross your tutorial and thought what the heck, why not... and ta-da it works like a charm! Anyways, I've got Ubuntu 7.10 Gutsy, and dvds are working great after your tutorial, thanks again! 

-Tim Baron

---

### Post by indoe on 2008-02-04
> **stchman said:**
> Thanks, I like to help others get their Ubuntu up and running well.
Another thanks from another person you helped out.

---

### Post by eli_d on 2008-02-04
and another...  the person that just bumped the thread with their thanks, saved me from extreme frustration!  following your tutorial worked great on my thinkpad t30 in gibbon.  

previously, my dvd's were working fine with vlc and the libdvd package from synaptic... but after swapping the internal hard drive with a new one & updating some software, i kept getting errors like :

 ```
Buffer I/O error on device sr0, logical block 443
```

,when trying to play dvds.

i read through tons of threads, reinstalled all of the dvd libraries & nothing worked.  the dvds would mount and be readable in nautilus, but they couldn't be played!  the medibuntu decrypter libdvd package solved this.

thanks!

---

