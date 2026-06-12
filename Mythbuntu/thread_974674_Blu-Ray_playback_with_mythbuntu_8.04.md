---
title: "Blu-Ray playback with mythbuntu 8.04"
date: 2008-11-07
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-11-07
is this possible? ive been doing a bit of reading but it seems i cant get a straight answer. i have mythbuntu 8.04 and im enjoying every minute of it. it works great as a "video jukebox" for my ripped DVD's (all 900 GB of them lol). but now that ive moved up to a 42" plasma i want to start to move to HD content. i dont have a Blu-Ray player, so i was thinking of getting a blu-ray drive so that i could just play them back. 

from what ive been seeing, playing them back directly from the disc wont work yet. however using the dd command one is able to make an .iso file out of the entire disc. GREAT! id rather have it on my HDD anyway so that its easier to access from my couch (its too much work getting up and swapping discs ;) )

now my question is, will mythtv be able to play back this .iso like my other dvd .iso's? obviously it will be a higher bitrate and a much larger file. and i stream over a network to my frontends, will i run into issues here? i have gigabit ethernet (router is gigabit as well).

what about HDCP? will i run into issues there too? or will the .iso no longer have HDCP limitations? i use a DVI-HDMI cable to transfer video to my tv from my frontend. video card in the frontend is a 7200GS, which as far as i know is not HDCP compliant. does linux even support HDCP even if your hardware does?

how about sound? ive read that they use some different sound formats on the BD discs. will i run into issues there? 

i know ill have to update udf to 2.5, but other than that, what am i facing? 

any help is much appreciated. thanks.

edit: i got blu-ray ripped, but having issues with playback. more detailed questions below!

---

### Post by gsrcrxsi on 2008-11-08
bump. anyone?

---

### Post by solitaire on 2008-11-08
Blu-Ray encryption is a different beast entirely from DVD. to play a Blu-ray disc the player creates a virtual system which then decrypts the movie and sends it to the player. if you dd the drive all you'll get is the encrypted system which holds the movie. you then need to decrypt it to get access to that movie.

Check out [www.doom9.org](www.doom9.org) for more info and a better explination on blu-ray playing

---

### Post by gsrcrxsi on 2008-11-08
could you be more specific in the link? i cant find anything about blu-ray on that site. only DVD. 

and what do you mean about the encryption? care to explain what i need to do to get the movie into a sigle playable file?

---

### Post by solitaire on 2008-11-08
check this thread:

[http://forum.doom9.org/showthread.php?t=123111&highlight=linux](http://forum.doom9.org/showthread.php?t=123111&highlight=linux)

---

### Post by solitaire on 2008-11-08
opps double post! :D
[]("http://forum.doom9.org/showthread.php?t=123111&highlight=linux")

---

### Post by newlinux on 2008-11-08
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

and

[http://forum.doom9.org/showthread.php?t=140571](http://forum.doom9.org/showthread.php?t=140571)

Might help.

---

### Post by gsrcrxsi on 2008-12-11
bringing this back up for some developments.

ive upgraded my hardware.
Backend:
q6600 @ 3.6GHz
4GB DDR3 1066 ram
8800GT vid card
LG blu-ray drive
1x640GB WD
2x1TB WD 
watercooled

Frontend:
e5200 @ 2.5GHz
2GB DDR2 800 ram
7200GS vid card
1x40GB WD
air cooled

now that ive aquired a BD drive to rip blu-rays. i started out with "The Dark Knight". ripped it with AnyDVD HD via virtual machine (since anydvd doesnt run in linux or wine). the rip was perfect and i used TsRemux to repackage the ripped .m2ts file into a .m2ts file with only the audio and video streams i want (best picture and sound). so here i am left a 30GB .m2ts file. this can be easily played with MPlayer and both audio and video work fine. testing it out on my backend has flawless playback, which is expected since its pretty powerful. 

now the issue im having is with playback on my frontend. with the default commands from Myth, i can play the file via Mplayer. it plays but its very juttery and its maxing out a single core at 100%. i took some tips from this page: [http://www.mythtv.org/wiki/index.php/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/index.php/High_Definition_Disk_Formats)

and im using this command in myth to play the movie:
```
mplayer -fs -zoom -quiet -vo xv -fps 24000/1001 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -framedrop
```

this improved it, but video still lags a bit. sound is perfect though. fast moving scenes or wide angle scenes seem to slow down considerably. and the multithreading didnt seem to help, its still maxing out a single core at 100% while the other is about 10%. 

does anyone have any recommendations on what i should do from here? from what ive read before, my hardware should be able to handle this playback. i have a feeling if i can get it to use more of the second core that that will help out a lot. ive also installed the latest nvidia drivers for this machine (177.82), but that didnt help. would a more powerful videocard help? do the nvidia drivers even offer hardware accelleration if i were to upgrade to a card that is capable of that? 

any help would be greatly appreciated.

---

### Post by august495 on 2008-12-11
Are you trying to stream the file? Maybe a network bandwidth issue?

---

### Post by gsrcrxsi on 2008-12-11
yes i am streaming it but bandwidth is not the issue. its gigabit ethernet from the server to the machine. even the router has gigabit ports.

im considering CoreAVC

---

### Post by gsrcrxsi on 2008-12-12
anyon have experience with coreAVC and myth? i hear good things but it seems kind of cumbersome looking at the install how to. 

nvidia is on the verge having support for HW decoding of h264, VC-1, etc. the drivers are still in beta (180.06). but i wuld have to upgrade vid card too, whic isnt reall what i want to do at this point. 

to me it seems like my computer should be able to handle it. looking at the backend when is running, only uses ~10% of each core and seems to do fairly well with multithreading, but my frontend doesnt seem to be multithreading at all with a single core maxed out.

---

### Post by Caps18 on 2008-12-12
Have you tried Xine or VLC for the frontend?  I had a similar problem with mplayer that went away when I switched it to Xine.

---

### Post by gsrcrxsi on 2008-12-12
i was under the impression that mplayer was the only player that could play .m2ts files (blu-ray rip). is this not true?

---

