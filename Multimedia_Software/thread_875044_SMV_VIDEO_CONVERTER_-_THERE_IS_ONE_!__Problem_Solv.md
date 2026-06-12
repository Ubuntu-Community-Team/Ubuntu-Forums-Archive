---
title: "SMV VIDEO CONVERTER - THERE IS ONE !  Problem Solved."
date: 2008-07-30
forum: Multimedia Software
---

### Post by lubeck on 2008-07-30
HI:
SOLVED for my Philips SA3245 Player and like others.  I note others have raved about this as well for their Philips players. 
(Faster and more flexible than WIN equivalent that came with unit.)
It is called "smv_encode".  For LINUX.

Available at [http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/](http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/) 
Works perfectly for Hardy 8.04.1 and there is a .deb installer at the site for auto loading. Wonderful.

Syntax at command line, or if you wish to 'Create Launcher,' is: smv_gui  
which pops up the simple, elegant gui version.
1. After start, Select file to convert - it will be clear how.
2. Select file location and name to save as (recommend a .smv suffix.)
3. I selected 220x176 for size, and 0 (zero) rotation.  With different players, you might need to adjust rotation or size.  
4. I left all other setting the same.
5. Press CONVERT.

Converts extremely fast...
As you know, then you just drag and drop to your player.
(Note: If I play back on Desktop, just hear sound in Movie Player.  Video perfect on device though.)

Hope it works for you.  Outstanding in my view.
g

---

### Post by VendettaVirtuoso on 2008-08-10
This sounds awesome, but it won't work for me because I run the 64-bit version of Hardy.

Is there any way someone can make a 64-bit deb for this? I've been looking for a real smv converter all day, and I've come up short every time.

---

### Post by sceaduwe on 2008-08-16
I also run the 64-bit version of Hardy. I installed the program from source. The picture quality was great, and the sound quality was ok, but the video was out of sync! I tried other videos and the same thing happened. I tried forcing the i386 package, but the same thing happened. If someone knows how to fix this please help!

P.S. My MP3 player is an SA30XX

---

### Post by Amanda HazLaPaz on 2008-10-23
I just followed these instructions for the .smv converter (after already having installed the .deb package installer per another Ubuntuer's suggestion a few weeks ago) and the solution was PERFECT for what I needed.

Now a little fine tuning to learn what size/rate/etc works best.  Will have to get used to opening from the command line, though.

Thank you very much!!  My son just received a Phillips 4G GoGear birthday present and is quite happy with how tech-smart his old ma is. Heck, it's not me, it's YOU guys.

---

### Post by TheFounder on 2009-11-27
Seriously if someone could compile and post the 64 bit version that would be helpful

---

### Post by DouglasCaixeta on 2009-12-04
> **lubeck said:**
> 
3. I selected 220x176 for size, and 0 (zero) rotation.  With different players, you might need to adjust rotation or size.  


I don't have this option. I can only select 96x128 and 127x159.

Then when I put on the mp4 is really small, use half of the screen. I use Ubuntu 9.04. What can be the problem?

---

### Post by t4thfavor on 2009-12-26
Looking into compiling it under x64, I have an email off to the former maintainer. Hopefully I get a response so I can maybe get access to the missing peices, and compile a package for x64 users.

---

### Post by j0bro on 2010-01-05
Hi guys,

Found out how to compile the sources for amd64, so here it is; compiled on Ubuntu Karmic 9.10 amd64. Unzip the attachment (debs were not allowed to attach).

After you install it, three commands are available:
[FONT="Courier New"]smv_decode
smv_encode
smv_gui[/FONT]

The latter brings up a handy GNOME gui program; for the Philips GoGear Ariaz 16GB, the settings I used were:
[FONT="Courier New"]geometry: 220x176
framerate: 11
tile factor: 11
rotation: 0 degrees
image quality: 84[/FONT]

Have fun!

---

### Post by achyuthan1991 on 2010-02-16
I do not get the option of screen size 176 x 220. I get only 96 x 128. I use Ubuntu 9.10 32 bit version.
If someone could compile it for the 32 bit version and post it, it would be really helpful.

Thank you in advance..

---

### Post by achyuthan1991 on 2010-02-16
I did find one at the link [http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/]("http://www.cs.bgu.ac.il/%7Eyurac/interests/smv-encode/")
But it offers a maximum size of 127 x 96 only.
Can someone edit it so that it also offers the size 220 x 159..
also the audio is slightly lagging behind the video...
Can someone please edit it and post it?

Thanks in advance

---

### Post by DouglasCaixeta on 2010-02-16
> **achyuthan1991 said:**
> I did find one at the link [http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/]("http://www.cs.bgu.ac.il/%7Eyurac/interests/smv-encode/")
But it offers a maximum size of 127 x 96 only.
Can someone edit it so that it also offers the size 220 x 159..
also the audio is slightly lagging behind the video...
Can someone please edit it and post it?

Thanks in advance

I try to type the resolution I want and it works. Just type whatever combination you want, dont rely on the available options.

---

### Post by achyuthan1991 on 2010-02-16
Thanks a lot Douglas :D
It helped a lot...
The ubuntu converter is loads better than the windows converter and is much faster...
Thanks a lot once more...:D

---

### Post by achyuthan1991 on 2010-02-24
hi this converter does work for some videos.
I know this will sound strange but y
I actually converted some videos and viewed them...
but when i later tried to convert a video using the same converter, the player responded "file format not supported"
Can anyone please tell me what the problem is?

---

### Post by Fastjack77 on 2010-04-27
This is working! The 64-bit version is working great.

---

### Post by mrgeez on 2010-05-12
Any1 managed 2 solve out of sync problems? Mine is Philips Gogear Ariaz, tried to use j0bro's settings. Converting on xp needs supercomputing, or days, the output is synced though. My OS is an x86_64 ArchLinux. What presets do you use to avoid picture lag?

---

### Post by kevinanchi on 2010-07-07
Thanks for the post, I'll check the link and will update you if its not getting done

---

### Post by alex12321 on 2010-08-07
Could someone of you send me the 32bit installer for the SMV-Converter, please?!
I tried this link "[http://www.cs.bgu.ac.il/~yurac/interests/smv-encode/]("http://www.cs.bgu.ac.il/%7Eyurac/interests/smv-encode/")" but each time I got the error-message: 504 Gateway time-out!

---

### Post by alex12321 on 2010-08-09
Don't know what went wrong yesterday!
Today the link worked well!

---

### Post by Jeffbuntu on 2012-10-31
Seems this is pretty old - but it was the first thread that came up.  Is there a new link to this one?  I tried but keep getting a 404 error.  Trying to get files onto a go-gear as well.

TIA 

Jeff

---

### Post by howefield on 2012-10-31
Old thread back to sleep.

---

