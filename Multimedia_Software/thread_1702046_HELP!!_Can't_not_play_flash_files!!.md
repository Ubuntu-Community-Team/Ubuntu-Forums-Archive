---
title: "HELP!! Can't not play flash files!!"
date: 2011-03-07
forum: Multimedia Software
---

### Post by Br1987 on 2011-03-07
Hi, I just recently installed Ubuntu 10.04 on my computer it's a Pentium 4, 2,26 GHz, 1 GB RAM, and 2 40 GB HDD... I ran update manager and installed all the updates. I installed all the Ubuntu restricted extras and I can play all the formats but .flv; there's sound but the all I can see are lines and static... I ran the tests and see if my video card was properly working and all seemed OK. Also every time I play a youtube video or from another site that uses flash the computer totally crashes!!... I installed Chromium and see if the problem had to do with Firefox but chromium also totally crashes.. after rebooting I tried playing another Internet video, but all I could get was a blank screen with sound...

Another issue I had was that right after the installation I could not set the screen resolution higher than 800x600, but i solved the problem (thanks to the forums :)) editing the xorg.config file and the problem got solved... I don't know if the problem with the flash and the screen resolution are related =X

Could somebody help me??!! T_T

---

### Post by wishihadtime on 2011-03-07
Hey Everyone,
First Timer here, which reminds me, anyone like Elliott Smith? Anyway, I just want to add to this problem. Let me know if I'm not doing this correctly. I think that this month marks a year since I've been unable to play internet flash (youtube, etc) videos on my 2003 Presario laptop with Ubuntu 8.0.4 and Firefox 3.6.13. It's either March or May, but it's one of the M months. I spent WAY too time reading and trying to mess with figuring out what to do to see about getting it to work before I came by a short article that said that Adobe admitted that there is a problem with their latest flash player version 10.anything for Linux, and they don't know when they'll get it fixed. When they used 9 or earlier, it always worked okay. I read everything on the planet and tried many things to see if I could reinstall an older version again, but no luck. Simply put, it just doesn't work with 10. I also came by one link that said that it was an older flash player but it installed something called Elf which I can't get rid of and it's annoying the hell out of me. I know how to use the Synaptec Package Manager, but am not too techy other that that. I must admit that though I've tried, I don't have time to learn much because I'm trying to fix over 15 years of life's collisions that have piled up on me, which may take 15 more years, but so far it's working, now that I work part time. If anyone would like to help, I'd even trade what I do know, like fixing something on your house or your old car, or I could pay it forward, and hope that my appreciation is okay enough. 
Thanks much. rbarnes1972 at att dot net

---

### Post by Leisko on 2011-03-07
> **Br1987 said:**
> 
Also every time I play a youtube video or from another site that uses  flash the computer totally crashes!!... I installed Chromium and see if  the problem had to do with Firefox but chromium also totally crashes..  after rebooting I tried playing another Internet video, but all I could  get was a blank screen with sound...

If you have an open source Ati driver, flash sites "crash" your system. Here is some info: [http://ubuntuforums.org/showthread.php?t=1699550](http://ubuntuforums.org/showthread.php?t=1699550) e.g 
> Had the freeze problem in U10.4.

Installed the proprietary driver in 'Hardware Drivers'. 

Youtube Works now.

So, I think you should try the propietary driver. Go System -> Administration -> Hardware Drivers

---

### Post by Br1987 on 2011-03-07
Thx for the reply but I'm not using a ATI video card... I'm using a SiS (Silicone Integrated Systems) 300/305/630/540/730 32 Mb video card...

---

### Post by Br1987 on 2011-03-07
No proprietary drivers listed when checking on Hardware Drives

---

### Post by Br1987 on 2011-03-10
I reinstalled Ubuntu 10.04 run update manager, installed all the restricted extras, enabled medibuntu, etc, etc... but I can not play youtube videos nor flash files in the internet... I tried Minitube with no result, and tried also totem's youtube plugin but it can not play videos either... 
I have .flv files in my pc and can play them with no problem at all... the only problem seems to be with flash videos on the internet...  I also installed Chromuim but same result... 
Can somebody shed soe=me light on this??? Is is true wha ***wishihadtime ***says??
 
>  
I think that this month marks a year since I've been unable to play internet flash (youtube, etc) videos on my 2003 Presario laptop with Ubuntu 8.0.4 and Firefox 3.6.13. It's either March or May, but it's one of the M months. I spent WAY too time reading and trying to mess with figuring out what to do to see about getting it to work before I came by a short article that said that Adobe admitted that there is a problem with their latest flash player version 10.anything for Linux, and they don't know when they'll get it fixed. When they used 9 or earlier, it always worked okay. 


---

### Post by no2498 on 2011-03-10
look in your package manager for flash
uninstall what the system put in only
not a complete removal just uninstall
go to adobe site install flash player
now reinstall 
sudo apt-get install ubuntu-restricted-extras

---

### Post by Br1987 on 2011-03-10
Tried already... same result...  =(

---

### Post by no2498 on 2011-03-11
you by any chance have win ff installed
it loads some codes that may help you

---

### Post by Br1987 on 2011-03-11
I can convert videos with no problem at all!! but the problem remains the same =(

---

### Post by no2498 on 2011-03-11
ok try installing the grease monkey plugin for fire fox
just remembered i had to do it on my other computer
to get flash to work

---

### Post by Br1987 on 2011-03-11
:O Greasy Monkey... never heard of that... can you tell me please what does it do??
Sorry... there are a  lot of stuff I don't know =)

---

### Post by Br1987 on 2011-03-12
I figured out what to do with Greasemonkey (I think so) and Installed a script that claims to watch youtube videos without using flash!!... but no result... all i got when loading a youtube video is a white screen (where the video is supposed to be) and sound...

---

### Post by Br1987 on 2011-03-12
Ok I think this is an important update... I just tried to watch another youtube video and the interface had changed (I guess this is greasemonkey doing) there is a player but no video loads... when I press play it says that I don't have the right or the permission to open that file... =(
anyone??

---

### Post by runeh76 on 2011-03-12
Hi

Are u using 32or64bit Ubuntu?

Try flash-aid to Firefox:
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/")

---

### Post by Br1987 on 2011-03-12
about the new player I have is this one: Totem Browser Plugin 2.30.2 Browser Plugin using GStreamer 0.10.28
but as I said no result =(
I'm trying flash aid!! let's see what happens T_T

---

### Post by Br1987 on 2011-03-12
................... this is what I get T_T

[IMG]https://td2gug.blu.livefilestore.com/y1pRFqFTGFJ7X-7F3ITLXXloEJaDVVNZSuLhve9i7Q8N9R4SqnIC09ulaOeA6s-01SAxYAGWe92-5agYHEYMr7PYtvn4fNnpAjv/Screenshot.png?psid=1[/IMG]

---

### Post by Br1987 on 2011-03-12
sorry about the huge picture... I should have posted a link better =P

---

### Post by runeh76 on 2011-03-12
Ur picture doesnt show up..its login.srf

---

### Post by no2498 on 2011-03-13
Br1987  you need to set the permission's for video

put this in google

permissions for video linux ubuntu


hope it helps you

---

### Post by Br1987 on 2011-03-13
get a lot of results in Google searching for "video permissions" but anything to do with my problem... what's that anything about the video permission?? could you please be more specific??

---

### Post by Br1987 on 2011-03-14
> **Br1987 said:**
> about the new player I have is this one: Totem Browser Plugin 2.30.2 Browser Plugin using GStreamer 0.10.28

When I open youtube now and try to play a video using the greasemonkey script that doesn't use flash for playing youtube videos I get this

[B]An error occurred
Could not open location; you might not have permission to open the file.[/B]

---

### Post by Br1987 on 2011-03-21
Well... after several attempts to solve my problem, I could not solve it =( the only thing I can do to watch internet videos is downloading them in the lowest resolution (to make it quick) and watch them, If I like them I download them again in higher resolution... =P
Anyone can shed some light on my problem?? or I'll have to do what I've been doing so far??

---

### Post by wishihadtime on 2011-03-23
Hi All,
I haven't checked in for a big while, but I found the short article that mentions something about Adobe and the flash player problem. Sorry that I didn't include this before. I wonder what you all think about it. However, I see now that it is remarking about Windows, so I need a better opinion about it, but it sounds similar to my problem. I wonder if I made anyone needlessly worry; if so, then I'm sorry. However, it mentions this phrase which is plastered all over my computer - "The Adobe flash plugin has crashed". I've messed with all of the simple appearing solutions too many times and have become too tired of dealing with it anymore so I don't even try to look for a solution anymore though I still certainly wish that it could be fixed. I also can't look at some news articles, etc. I wish that I had time to learn more complicated  procedures like the terminal, etc. I think that I may try to get a Ubuntu installer disk and see what happens after reinstalling the OS. Does that sound too radical to anyone? Anyway, here's the link to that - [http://dummy-essentials.blogspot.com/2010/07/adobe-flash-plugin-has-crashed.html](http://dummy-essentials.blogspot.com/2010/07/adobe-flash-plugin-has-crashed.html)
Lastly, my About Firefox window says Firefox v. 3.6.15 and Mozilla Firefox for Ubuntu canonical - 1.0, if that helps.
Thanks much

---

### Post by Br1987 on 2011-03-26
SOLUTION AT LAST!!... Firefox just upgrade automatically and now I can see youtube videos with no problem =)
But when I try to go full screen everything goes black and white and stripes and etc, etc...

---

### Post by drdos2006 on 2011-03-26
Goto Firefox -> Tools. 
Goto Plug-ins, search for Flash-aid by lovinglinux.

Get the Flash-aid plugin and allow it to run.

regards

---

