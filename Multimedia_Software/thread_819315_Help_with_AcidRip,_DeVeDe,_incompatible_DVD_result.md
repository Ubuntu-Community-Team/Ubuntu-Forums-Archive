---
title: "Help with AcidRip, DeVeDe, incompatible DVD result"
date: 2008-06-05
forum: Multimedia Software
---

### Post by reiki on 2008-06-05
Using Ubuntu Hardy.
And I'm new at this DVD rip/author thing but I've burned plenty of DVDs and CDs.
This is all legal content. Nothing copyright or protected or anything.

I have a DVD project mostly complete. 
I copied 4 DVDs to iso (using gnomebaker) and then burned them to DVD. Those work fine.

The last DVD I have to make involves getting one full performance off of a DVD that is made from a transferred VCR tape. Yeah, I know... this part was already done... I have a recorded and working DVD of that transferred tape. 

When I say, "working", I mean the DVD plays fine in standard DVD players that you would find in someone's A/V rack.

So I used AcidRip to get chapter 19 off one DVD, and then to rip the entire "movie" off of another DVD. I ripped them to .avi files.

Then I opened DeVeDe and it opens with "Title 1" which I edited appropriately. I added the full lenth .avi file and all the while I am making sure that NTSC is selected and not PAL/SECAM. I created another title, and then added the second .avi file.

I am basically leaving everything at the default setting in DeVeDe except I am making sure it's on NTSC instead of PAL. I then went into the menu options, being sure again that NTSC is selected and otherwise accepted the defaults. (First project like this.... don't need fancy.... just need it working). Menu looks acceptable. 

Now I tell DeVeDe to create an .iso. Takes a while, but finishes successfully. I get an iso file. 

Burn that to DVD using GnomeBaker, insert into DVD player (not computer... the one at the TV) and I get a message that it is unsupported.

Examining the disc I see the expected TS_Audio and TS_Video folders and files.  

Now I know I can create an iso from a DVD using gnomebaker and get a usable result because I've done it. I can burn that iso to a DVD and get a usable result. (I've already done exactly that many, many times)

So I have to assume that there is something wrong with my procedure for ripping (an incorrect setting in AcidRip) OR my procedure for putting the DVD together (using DeVeDe)

Should I be AcidRipp'ing these to mpeg instead? And using something other than DeVeDe to put the disc together (like DVD Styler or something?)


Where am I screwing this up?

Thanks

---

### Post by aeiah on 2008-06-05
you shouldnt be converting them to avi. this is counter-intuitive since you're then converting them back to mpeg (dvd) format. you should rip them with no compression or change in format from mpeg for the best results. this however, may or may not solve your problem, since devede is designed to handle avi files i assume

instead of acid rip, you might want to consider xdvdshrink, or perhaps k9copy, as this will easily allow you to rip without compressing and it should just be a matter of stitching the parts together in devede

---

### Post by reiki on 2008-06-06
Thank you. I'm learning.
I switched to tovid for creating the DVD structure. Todisc makes a fine menu for what I'm trying to do. However I STILL ran into problems after using makedvd to burn the DVD. My player still said it was "unsupported". It would play in VLC, but not on any other player in the house. I have a Sony DVD changer and a Panasonic recorder set up in my A/V system and my wife and kids all have DVD burners in their computers. Nobody could play the DVD but me (on the computer where it was created)

As I said, I'm using Hardy. I had a hard time believing that ALL of the DVD players in my house had a problem so I rebooted to Gutsy. 
I did not repeat the entire process. I simply used makedvd to burn the DVD from the files that had already been created by todisc in Hardy.
It worked! It made a DVD that all players in my house can read.
I checked the version of growisofs in Gutsy and it seems to be the same version as being used in Hardy (7.0.1) and genisofs seems to be the same version as well.
Were they PREPARED differently from Gutsy package to Hardy package? I don't know. I'm not even sure that's EXACTLY where the problem lies. What I *DO* know is that Hardy can't make the DVDs compatible with all players and in Gutsy, I can (using the same commands as in Hardy)

This leads me to believe that SOMETHING in Hardy is broken and I don't have enough in-depth technical knowledge about how it all works together to know exactly what files to be looking at or how to troubleshoot it any farther than I have.

Is it possible that teh default settings being passed to growisofs and/or genisofs are different in Hardy than they are in Gutsy? I don't know where to look for those defaults.

---

