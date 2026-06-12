---
title: "Zotac ION HD-ID11 all working in HD"
date: 2010-11-08
forum: Mythbuntu
---

### Post by byronmyth on 2010-11-08
Hi Guys.
 
In case anyone is looking for a new frontend PC, I can highly recommend this little machine:
 
[http://www.zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100083&lang=en](http://www.zotac.com/index.php?option=com_wrapper&view=wrapper&Itemid=100083&lang=en)
 
It boots quickly, displays smooth HD tv using the highest VDPau setting, is almost silent and is SO small!
 
There are few foibles with setup, let me know if anyone else takes the plunge and has any issues.

---

### Post by mymythtv on 2010-11-08
got one myself, and it's ok so far - installed mythbuntu on SD card :-)

A few things - it's not totally silent ( I know - not loud, but ).
Have some problems - not sure if it's the ath9k driver ( testing wireless at the moment ) or the "old" 2.6.32 kernel problem ( still running 2.6.31 on my main fe/be ), causing "jerky" picture ( not HD - only SD )
There should also be external antenna - have a weak signal on the built in :-(

But - agree, it's a good fe :-)

---

### Post by ZedThou on 2010-11-09
> **byronmyth said:**
> 
It boots quickly, displays smooth HD tv using the highest VDPau setting, is almost silent and is SO small!
 
There are few foibles with setup, let me know if anyone else takes the plunge and has any issues.

You're running Advanced 2x deinterlacing? I've never been able to do that on my ION frontend, even overclocked.

---

### Post by byronmyth on 2010-11-11
*You're running Advanced 2x deinterlacing? I've never been able to do that on my ION frontend, even overclocked.* 
 
Yes no problem at all, and I wouldn't want to overclock.
 
*A few things - it's not totally silent *
 
Are you running the latest BIOS, I think they tweaked the fan settings in a later BIOS. Mine only makes a noise for a couple of seconds when first switching on, even the second one with a HD is almost silent?
 
*There should also be external antenna - have a weak signal on the built in* 
 
The Wireless support is hopeless IMHO, if you are managing to stream anything smoothly using wireless you are doing better than I ever did. I hard wired all my MythTv machines over a year ago as I got fed up with the dropouts. It's actually irritating that the wireless can't be switched off in the BIOS, instead I get the OS to do that at boot up time.

---

### Post by bance on 2010-11-11
Would you care to share your play back settings?

I'm sure they'd be of use to lots of people:P

TIA Steve,

---

### Post by AlexWerz on 2010-12-03
Hi!

I have bought the Zotac ID-11 to works as a frontend for mythtv. I have isntalled MythBuntu 10.10 and having problems with audio over HDMI. If I use VLC player it works perfect but in MythTV it does not. I have tried all the available soundcards in the general setup. None does work as audio over HDMI. Any hints for me?

Beside that I am getting a very blurred picture of the OSD. It jitters a bit. Has this something to do with anti aliasing? Where can I switch that on?

Thanks for your help,
Alex

---

### Post by nickrout on 2010-12-03
In general media streaming and wireless is a waste of time. Some people sometimes have luck, but then the start the microwave, or the neighbours start their wireless router on the same channel, or other untraceable things happen and it all goes to pieces.

Run a wire!

---

### Post by byronmyth on 2010-12-06
Assuming that you already have HDMI showing up in Alsamixer, I had to do the following to get sound in Myth via HDMI:
 
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT]       [/FONT][FONT=Calibri][SIZE=3]In audio settings under audio output device enter: [COLOR=red]ALSA: plughw:1,7[/COLOR] this will direct sound via HDMI.[/SIZE][/FONT]

---

### Post by nickrout on 2010-12-06
> **byronmyth said:**
> Assuming that you already have HDMI showing up in Alsamixer, I had to do the following to get sound in Myth via HDMI:
 
[FONT=Calibri][FONT=Calibri][SIZE=3]1.[/SIZE][/FONT]       [/FONT][FONT=Calibri][SIZE=3]In audio settings under audio output device enter: [COLOR=red]ALSA: plughw:1,7[/COLOR] this will direct sound via HDMI.[/SIZE][/FONT]

Is this 0.23 or 0.24? In 0.24 you should get rid of all asound.conf files and use the "scan for audio device" button.

---

### Post by byronmyth on 2010-12-07
>  
Is this 0.23 or 0.24? In 0.24 you should get rid of all asound.conf files and use the "scan for audio device" button. 

 
0.24. To be honest I've had so many problems over the last couple of weeks due to upgrading to 0.24 10.10 that when the HDMI sound continued to work I didn't do anything else. Even now I'm finding stuff "glitchy", I wish I hadn't bothered, 0.23 was working well for me.

---

