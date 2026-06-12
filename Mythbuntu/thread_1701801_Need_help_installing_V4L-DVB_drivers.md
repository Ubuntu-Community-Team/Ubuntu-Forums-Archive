---
title: "Need help installing V4L-DVB drivers"
date: 2011-03-06
forum: Mythbuntu
---

### Post by mookie60 on 2011-03-06
I recently installed mythbuntu 10.04.   I have 2 tuners, Haup 1600 and pchdtv 5500.   The 5500 seems to record fine, but the 1600 is quite glitchy.   

I read the mythtv.org page for the 1600,  If I understand it correctly, I need to install new drivers using the instructions on:    [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Under the "manually intensive approach" on this page, the 3rd instruction says "make tar DIR=<some dir with media -git tree>" .   It's not clear to me what this means.   Could someone tell what directory I should use here?

Thanks

---

### Post by mookie60 on 2011-03-13
bump

---

### Post by ian dobson on 2011-03-14
Hi,

why just use the basic method:-

git clone git://linuxtv.org/media_build.git
cd media_build 
./build.sh

Regards
Ian Dobson

---

### Post by mookie60 on 2011-03-21
Ian,

I would have preferred to use the "basic" method, but the webpage  

[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

says that this method, when used with Ubuntu, causes a "fatal compilation error".  It goes on to say that the more "manually intensive" approach is best.  And even then (if I'm reading it correctly), it still requires a manual edit of the v4l/.config file before "proceeding to build the modules".  I'm guessing "build" is effectively the same thing as "make".

I don't know if the "fatal compilation error" is a big deal or not, but I've reinstalled this system a couple times already, and I'm really trying to avoid doing that again.

Thanks for any clarification on this install which you can provide.

---

### Post by PatrickD-52761 on 2011-03-25
> **mookie60 said:**
> Ian,

I would have preferred to use the "basic" method, but the webpage  

[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

says that this method, when used with Ubuntu, causes a "fatal compilation error".  It goes on to say that the more "manually intensive" approach is best.  And even then (if I'm reading it correctly), it still requires a manual edit of the v4l/.config file before "proceeding to build the modules".  I'm guessing "build" is effectively the same thing as "make".

I don't know if the "fatal compilation error" is a big deal or not, but I've reinstalled this system a couple times already, and I'm really trying to avoid doing that again.

Thanks for any clarification on this install which you can provide.

I'm in the same position as you (in that my HVR-1600 doesn't work correctly in Mythbuntu 10.10).  The "compilation errors" are because the kernel doesn't properly recognize some of the cards that the "make" will try to create drivers for.  That's why they say you need to change line about firedtv from "m" to "n" (so it won't try to build a driver for that card).

I haven't tried the steps from the site either, because when I tried compiling earlier (using the method from mythtv's wiki), it failed to detect my cards afterwards (and I had to do a complete reinstall).

As for your original question, I think if you view the build.sh file, you'll see the line "make tar" and "make untar" in it.  You should be able to copy those lines and paste them into the terminal (most likely you'll have to write them out and type them in though).

Finally, you may be able to use the basic approach (with a slight modification first).  Assuming (since I haven't downloaded the git tree yet) that the v4l.config file is already present in the directory, you could edit it prior to running the ./build.sh line in the "basic commands".  If it's not already present, then you have to do the manual build.

I'll reboot into my mythtv box after I post this, and play around with it for a while. If I get things working, I'll reply with my steps (or at least whether you can edit the file immediately or not, and what the line for "make tar" shows in my build.sh file).

Also, if you're receiving an error message in dmesg (or on bootup) about not having enough vmalloc memory, what you need to do is edit the command in GRUB, and add vmalloc=192M or vmalloc=256M to it (right before the "quiet splash" phrase). You can edit GRUB's configuration, or just manually add it when you reboot.  I'd try 192M first, and move up to 256M if you need to.

Have a great day:)
Patrick.

---

### Post by mookie60 on 2011-03-25
Patrick,

Thank you sooo much.   I had all but given up.   Thankfully I also have a pchdtv 5500 whick makes solid digital recordings, so I just lowered the priority on the 1600.  The 1600 dvb does work, but lots of little hiccups.  

I'll follow your suggestions for the driver install, but I won't get around to it for a few days.  

I never needed to increase the vmalloc setting when I only had the 1600, but when I added the 5500 I have needed to change it.  It's set at 256 right now, but I should try 192 to see if I can get away with something lower.

Sorry to hear your 1600 isn't working with 10.10.  I recently redid my system, going from 9.04 to 10.04.   I debated for a while between 10.04 and 10.10, and only chose 10.04 because of the long term support - I guess got lucky.

Thank you again for the details you provided.  I let you know how it goes.

---

### Post by mookie60 on 2011-04-13
Patrick,

I've finally gotten around to employing your suggestions.

After I performed the first step, "git clone git://linuxtv.org/media_build.git "

The lines you referred to, I think, in the build.sh file are:

  run make -C linux/ download
  run make -C linux/ untar
  run make

I'm not real sure what to do with this, as it's not in the "make tar" format you described.   

I also looked for the "v4l.config" (and v4l/.config), but couldn't find it.  So I guess it's not generated till a subsequent step, like  "make tar DIR=*"?   So I'm still unsure what to replace "*" with.

I know this isn't suppose to be so difficult, but apparently it's not idiot proof.

Thanks
John

---

### Post by PatrickD-52761 on 2011-04-14
> **mookie60 said:**
> Patrick,

I've finally gotten around to employing your suggestions.

After I performed the first step, "git clone git://linuxtv.org/media_build.git "

The lines you referred to, I think, in the build.sh file are:

  run make -C linux/ download
  run make -C linux/ untar
  run make

I'm not real sure what to do with this, as it's not in the "make tar" format you described.   

I also looked for the "v4l.config" (and v4l/.config), but couldn't find it.  So I guess it's not generated till a subsequent step, like  "make tar DIR=*"?   So I'm still unsure what to replace "*" with.

I know this isn't suppose to be so difficult, but apparently it's not idiot proof.

Thanks
John

Hi John,

I went into their IRC Channel and asked about your question.  And I directed them to this thread (so hopefully one of the people will come and help you out also).  One comment returned was this:

BTW, the last three patches here need to be used to get analog to work for the latest HVR-1600's : [http://git.linuxtv.org/awalls/media_tree.git?a=shortlog;h=refs/heads/cx18_39](http://git.linuxtv.org/awalls/media_tree.git?a=shortlog;h=refs/heads/cx18_39)

So, it sounds like you'll need an extra bit of help.  As for my issue, the drivers were fine. I ended up having to configure some things inside of mythfrontend to get everything up and running.

Have a great weekend, and sorry I couldn't be more help. :)
Patrick.

---

### Post by andyzx6r on 2011-05-09
Does anyone have an answer for this yet?

I have been trying to install V4L for about a week now and I am close to tearing my hair out!

Surely it can't be impossible to install V4l on natty?

This is my first post, so please be understanding if I'm doing something wrong

Andy

---

### Post by PatrickD-52761 on 2011-05-09
> **andyzx6r said:**
> Does anyone have an answer for this yet?

I have been trying to install V4L for about a week now and I am close to tearing my hair out!

Surely it can't be impossible to install V4l on natty?

This is my first post, so please be understanding if I'm doing something wrong

Andy

Hi Andy,

When you do a dmesg and look for any cx18 entries, do you get anything at all?  Also lspci -v should show something.  If the cards are recognized in those places, then you could try this instead:  When you set the cards up, don't set them up as v4l analog cards. Set them up as "MPEG-2 encoder card (PVR-x50, PVR-500)" (Natty or earlier).  I'd have to dig into my mythbackend on Maverick to see what they're listed as.

Hope this helps, and sorry if I didn't. I ended up setting mine up with this configuration, and they work.

Have a great day:)
Patrick.

---

### Post by andyzx6r on 2011-05-09
> **PatrickD-52761 said:**
> Hi Andy,

When you do a dmesg and look for any cx18 entries, do you get anything at all?  Also lspci -v should show something.  If the cards are recognized in those places, then you could try this instead:  When you set the cards up, don't set them up as v4l analog cards. Set them up as "MPEG-2 encoder card (PVR-x50, PVR-500)" (Natty or earlier).  I'd have to dig into my mythbackend on Maverick to see what they're listed as.

Hope this helps, and sorry if I didn't. I ended up setting mine up with this configuration, and they work.

Have a great day:)
Patrick.

Patrick,

No, nothing for dmesg or lspci. Actually, I got so desperate that I installed Win7 on the machine to see if it would recognise the card, but it didn't show up there either so I have come to the conclusion that the card is dead.

I have, however, just bought a cheap [SIZE=1]wintv-hvr-1200[/SIZE] from ebay, so I expect the nightmare to start again in a few days when I try to get that working.  

I don't suppose anyone has an answer to the original query - can you install v4l on natty? And if so, how?  

It seems like quite a big deal to me if it isn't possible. I have two computers, a laptop and a media pc, both running Ubuntu because that's the only flavour of linux I've tried, and it's been such a steep learning curve that I can't face starting another flavour, but I really need to get the DVB working, otherwise the media pc is pointless.

Thanks for responding.

Andy

---

### Post by PatrickD-52761 on 2011-05-10
My understanding is that they built the v4l drivers into the kernel on Natty.  So you don't need to install anything, as it should already be present.  I could be wrong though.

Sorry to hear about your card.

Have a great day, and good luck with the new card. :)
Patrick.

---

### Post by andyzx6r on 2011-05-13
I got my new card, plugged it in and it worked! All it needed was a driver install and I was away. 

Thanks for the support - I had no idea that the v4l drivers were included in the latest build, this simplified life immeasurably.

---

