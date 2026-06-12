---
title: "Radeon HD 4850 XT with Dell XPS 430 video problems"
date: 2009-06-14
forum: Multimedia Software
---

### Post by sanumala on 2009-06-14
Hi 

I have Dell XPS 430 with 8GB DDR3 RAM, 2 750GB HDD's, Intel Core 2 Q9550 2.83 Ghz 1333fsb quad core and some other stuff like blu-ray 19-1 video card reader ect..

When I got this xps desktop I immediately disabled RAID 0 and installed vista ultimate on one HDD and lastweek installed Ubuntu 9.04 on other 750GB hdd by creating manual partitions like 20GB swap 20GB / and remaining 650 GB /home 

Every thing works fine except Graphics. Lot of video tearing while playing avi, mkv or any other video formats. Tried default ubuntu suggested video drivers and tried ATI's 9.5 drivers also but same video tearing.


I have attached hardware configuration of system. 

Before Ubuntu I used to use centos 5.X series and everything is fine. The only extra thing i did in ubuntu is enabling desktop effects. But irrespective of enabling or disabling desktop effects   video tearing is there.

Can any body suggest the step by step procedure to fix this problem.

I have two toher boxes one is HP 8100n and other is HP m8457c with nvidia graphics cards. They are really cool.

I read lot of articles about ati-ubuntu seems like both are not in sync.

Please Help guys.

Note: I am not new to ubuntu but for forums :) I am a silent reader of forums and this is my first post.

---

### Post by danbyrne on 2009-06-15
Hi
 
I am having exactly the same issue, on the same GFX hardware (Radeon HD4850) with both 'restricted drivers' driver and the ATI.com binary.
 
When moving windows sometimes you can see the shearing with or without desktop effects. It's more prominent in movies, especially fullscreen (which used to freeze the system entirely)
 
It's supposed to be replacing windows 7 as an MCE and a basic webserver but without multimedia I can't be booted into Ubuntu for more than 20% of the time.

---

### Post by sanumala on 2009-06-15
Yeah Exactly 

When I open any avi file in totem or vlc it is ok in 100% screen but when i enable full screen system freezes and it will not allow to login into console also.

The Same Graphics Card is working great i mean really great with Cent OS 5.3 / RHEL 5.3 x86_64 bit.

---

### Post by danbyrne on 2009-06-15
> **sanumala said:**
> Yeah Exactly 

When I open any avi file in totem or vlc it is ok in 100% screen but when i enable full screen system freezes and it will not allow to login into console also.

The Same Graphics Card is working great i mean really great with Cent OS 5.3 / RHEL 5.3 x86_64 bit.

Hmm so it's compatible with other distros... I thought it might be compiz fusion so I disabled that, but it made no difference. I might try a different kernel version and see if that changes anything - I read that playing about with different kernels/drivers sometimes (randomly) did the trick.

Do you know which kernel version you were using?

Also *bump* - this is fairly standard hardware, any ubuntu community supporters got a clue whats going on here? Pretty annoying not being able to use a mainstream GFX card!

Cheers
Dan

---

### Post by sanumala on 2009-06-15
If I remember correctly I have used the default x86_64 bit kernel provided by cenOS 5.3 which is kernel-2.6.18.

Centos has better support in 5.3 for compiz but i never enabled compiz desktop effects in that.

Give a try with kernel-2.6.18 and please let know it works or not.

one week back i reformatted my HDD and installed ubuntu i will try centos once again from my end and see how it goes :p

Any way looking for the expert answers from ubuntu team to solve our question. 

I like my radeon HD 4850 very much in windows vista its like charm.

---

### Post by sanumala on 2009-06-15
Found around 250 threads reg. ati radeon in ubuntu forums and hardly no solution yet...

Seems like Ubuntu :( ATI Radeon

[http://ubuntuforums.org/search.php?searchid=60593446](http://ubuntuforums.org/search.php?searchid=60593446)

---

### Post by sanumala on 2009-06-16
Can anybody help. I am trying and trying but did not get a solution.

---

### Post by sanumala on 2009-06-18
Please help. Yesterday I have tried new 9.6 ATI drivers and systems freezes.
 
Again I restored old xconfig using aticonfig --initial -f

---

### Post by danbyrne on 2009-06-23
> **sanumala said:**
> Please help. Yesterday I have tried new 9.6 ATI drivers and systems freezes.
 
Again I restored old xconfig using aticonfig --initial -f

Hi there,
Just to let you know I'm still experimenting with this, haven't found a solution for it yet.
Is there any way to submit an official bug report for this, so that hopefully the ubuntu developers will look into it?

---

### Post by sanumala on 2009-06-23
> **danbyrne said:**
> Hi there,
Just to let you know I'm still experimenting with this, haven't found a solution for it yet.
Is there any way to submit an official bug report for this, so that hopefully the ubuntu developers will look into it?
 
I have tried different ways but no use. Planning to swith to nvidia and borught Geforce 9800 gt. today after work i will install the new graphics card and let you know how my experience is...
 
Even I dont know how to submit official bug report to ATI..

---

### Post by sanumala on 2009-06-23
Updated my graphics card to EVGA Geforce 9800 Gt 1GB and my video streaming rocks...

see thread [http://ubuntuforums.org/showthread.php?t=1194392](http://ubuntuforums.org/showthread.php?t=1194392)

---

### Post by danbyrne on 2009-06-25
> **sanumala said:**
> Updated my graphics card to EVGA Geforce 9800 Gt 1GB and my video streaming rocks...

see thread [http://ubuntuforums.org/showthread.php?t=1194392](http://ubuntuforums.org/showthread.php?t=1194392)

Nice,
Good to hear you've got it working.

I think I'm going to have to use Ubuntu only as a streaming server and not play anything through the TV/ATI card, gah. Kinda wish I'd stuck with my 7900!

---

