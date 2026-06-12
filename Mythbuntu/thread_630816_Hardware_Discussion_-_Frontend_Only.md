---
title: "Hardware Discussion - Frontend Only"
date: 2007-12-03
forum: Mythbuntu
---

### Post by Glenhawk on 2007-12-03
Hello all,
My old PC was a P4 2.66GHz with 2GB of DDR (not DDRII) and a 256MB Nvidia AGP card. Because my new PC is 64-bit architecture with DDRII and PCIE all my old bits were set aside to be used for a MythTV box.

My AGP card did not have composite out (for our crap TV) so I had to go back to my old 64MB Nvidia. The system worked ok, I could watch HD without lag (after a few seconds) but I thought I was at the limit of it's capabilities. The picture was a little blurry and I would occasionally get a skip or unsynchronised audio and video so I thought that I would try running the backend on my new PC to free-up my frontend PC.
(I later found out that the blurry picture could be fixed by de-interlacing and perhaps the split system was unnecessary)

I became committed to the split system when I found a tiny PC box that is ideal for our TV cabinet... but it could not contain a HDD because it was designed for MiniAXT not MicroAXT (anyone else ever wondered why they used mini for a board smaller than micro?).
So, the system:
[LIST]
P4 2.66GHz[/LIST]
[LIST]
[*]2GB RAM
[/LIST]
[LIST]
[*]64MB Nvidia
[/LIST]
[LIST]
[*]8GB CF card for OS
[/LIST]

From what I have seen so far works great as a mythbuntu front end; it is quiet, compact and serves all the video I throw at it as long as I don't install any more overheads (I tried installing GNOME desktop and I got processor lag).

Now my questions are about the VGA card. I am using a 64MB VGA card and all seems to work ok. Would that be because the rest of my system is overspec? What impact does a VGA card have on a frontend? 
I was planning to put my 256MB card in when we get a new TV (with VGA or DVI) but now it won't fit in the box because it is a full height card. When the new TV comes I will immediately use either the VGA on the 64MB card or the onboard Intel VGA. What sort of improvements would I be likely to see if I find a half height 256MB card? At this stage the easiest half height card to get my hands on is an ATI card, should I do that?

I am happy to say if it ain't broke don't fix it but while it looks ok on the small CRT, maybe it won't look good on the big LCD? Maybe it won't be able to handle big enough resolution?

I see recommendations for hardware for client/server installs of MythTV but what about just for the client?

---

### Post by ubnewbie2 on 2007-12-03
I am running a 128MB Nvidia card (geforce 7) and I have been wondering what the effects of more or less memory will be.   You say yours works with 64MB, so what does mythtv really need?  Would I benefit by getting a 256MB card?

---

### Post by newlinux on 2007-12-04
What resolution are you trying to run now and what resolution will you try to run when you get your new TV? If you are going to get a new card, I strongly recommend against an ATI card. You have a likely have more success with a nvidia card. 

It's hard to say what myth needs. It depends on the monitor (some monitors/TVs are more difficult to get looking right than others), processor, and your resolution requirements. before purchasing a new card you should try out your current card. I have a P4 2.6 with an MX440 (64MB) that does a great job with my HD content (mostly 720p).

---

### Post by Glenhawk on 2007-12-05
Yeah, I agree about the ATI card but I might have to visit a swap meet with my full height NVidia and see if I can trade it for a half height if I want to use my cool little case still.
The reason I mentioned ATI is because I probably have an ATI available to me if I wanted it.

I am not sure what RES the box is running at now because I did a fresh advanced install to clear my overhead and during it I specified composite out. The first time it booted it defaulted to the TV and it is hard to read the menu text.

I recently setup VNC and although I haven't checked the resolution yet I would say it is probably 1024x768 based on how much of the screen VNCVIEWER takes up.

I am planning to get a TrueHD TV (1080p) so I guess it will depend on how hard the 64MB card can drive it. BTW from memory I also have the MX440 but it could be a MX420 (it's pretty old)

---

### Post by ubnewbie2 on 2007-12-05
nVidia cards like my Geforce 7 128MB are really cheap, I only paid about $30, and it is working quite well at 1024x768.  I need to get around to raising that res a bit, now that 1080i stuff is being transmitted free-to-air more regularly.

---

