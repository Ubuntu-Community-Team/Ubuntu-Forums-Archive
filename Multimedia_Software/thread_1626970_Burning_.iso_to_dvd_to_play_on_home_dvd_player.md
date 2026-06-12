---
title: "Burning .iso to dvd to play on home dvd player?"
date: 2010-11-20
forum: Multimedia Software
---

### Post by bloodshot13 on 2010-11-20
I'm not much of a techie but I've been working on trying to make a dvd of home movies from an .avi format. I was able to play these .avi movies in vlc player fine.I've used devede to make files to .iso image. Then I use k3b(does it matter if running in gnome?) to try and burn the movies to dvd and I get these error messages. I am new to this so I'm sure it's something I'm missing. It's showing I only have 3.2gigs used space but maybe because some of the files are larger than 2gigs it won't burn? Are there some images in the files that I'm not aware of?I moved 3 .avi files(movies) to devede and it took a while to make these into an .iso file(format?). Then I moved the whole .iso image to video ts in k3b, and these are my results... Any help is much appreciated:D

---

### Post by bloodshot13 on 2010-11-20
By the way in screenshot k3berror2, the files on the top aren't the files I placed in video ts. The file I placed in video ts was solely an .iso image.

---

### Post by SeijiSensei on 2010-11-20
Did you try simply burning the ISO image that was created by Devede?  In K3b, try Tools > Burn Image, then point to the .iso file.

---

### Post by lisati on 2010-11-20
> **SeijiSensei said:**
> Did you try simply burning the ISO image that was created by Devede?  In K3b, try Tools > Burn Image, then point to the .iso file.

+1. An alternative is to right-click on the ISO file name, and select "Write to disk"


Edit: have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by bloodshot13 on 2010-11-21
Well I successfully burned the .iso to dvd with k3b:p. Tried playing the dvd in my home RCA dvd player and.........................................................................no dice:(. Says "The dvd is incompatible". This is an older dvd player so maybe that's why? Are .iso only compatible on newer dvd players? I did run the dvd in my computer through vlc player and was successful watching the dvd! Thanks for your help! So glad I've got a hard copy of these movies as the video camera that took them is no long with us(as it's dead). Thanks again! I don't know if I should mark this post as "solved" because of the dvd player issue?

---

### Post by coffeecat on 2010-11-21
> **bloodshot13 said:**
>  Says "The dvd is incompatible". This is an older dvd player so maybe that's why? Are .iso only compatible on newer dvd players? 

No. An ISO file is simply an image of a filesystem. Once it is burnt to the DVD, you have a usable DVD with all the folders and files. A more likely explanation is that older DVD players can only read the older DVD-R discs and you are probably using a DVD+R disc. Or +RW.

DVD-R - [http://en.wikipedia.org/wiki/DVD-R](http://en.wikipedia.org/wiki/DVD-R)

DVD+R - [http://en.wikipedia.org/wiki/DVD%2BR](http://en.wikipedia.org/wiki/DVD%2BR)


What type of discs were you using?

---

### Post by bloodshot13 on 2010-11-21
I'm using DVD-R(memorex). A friend of mine burned some dvds for me last year and he said he burned them as .iso and they worked in the same dvd player, so I'm not sure why this won't work. Not really sure why there is dvd-r and dvd+r they seem to be about the same from what I'm reading. I could understand if one was far superior to the other but that doesn't seem to be the case.

---

### Post by Chronon on 2010-11-21
Maybe it's a region issue?

---

### Post by coffeecat on 2010-11-22
> **Chronon said:**
> Maybe it's a region issue?

That's an interesting thought, but it won't be a region issue if the OP is using devede to make a DVD iso from a home movie AVI. However....

@bloodshot13, when using devede was it set to PAL or NTSC? My devede defaults to PAL but you'll need NTSC and if you've created a PAL DVD it's possible that an older DVD player isn't dual standard. Perhaps yours is NTSC only and puts out the incompatible message when confronted with a PAL DVD.

---

### Post by bloodshot13 on 2010-11-23
It is set to NTSC. Mine too, was set to PAL(default), but I made sure it was set to NTSC.

---

### Post by ron999 on 2010-11-23
Hi
Have you tried making a simple DVD with just one video and no menu?

---

### Post by Chronon on 2010-11-23
> **coffeecat said:**
> That's an interesting thought, but it won't be a region issue if the OP is using devede to make a DVD iso from a home movie AVI. However....


Ah, good point.  I forgot that the source was user-created AVIs.

---

### Post by bloodshot13 on 2010-11-25
> **ron999 said:**
> Hi
Have you tried making a simple DVD with just one video and no menu?

What exactly do you mean? You mean turn one of my .avi vids to .iso and burn w/o devede(just right click and "burn to disk") and maybe it will play straight to the video in the dvd player. Will making a video w/o menu work better? Just asking as I'm not sure. I haven't tried this but if you think it will work I will try. Just don't want to waste alot of dvd's.

---

### Post by ron999 on 2010-11-25
> **bloodshot13 said:**
> What exactly do you mean? You mean turn one of my .avi vids to .iso and burn w/o devede

Yes, create an iso from one avi file and burn it with K3b.

This method works OK for me:-

#1 Convert the file to MPEG-2.
```
ffmpeg -i **[COLOR="Red"]filename.avi[/COLOR]** -target ntsc-dvd foo.mpg
```
(Creates a file named **foo.mpg**)

#2 Build the file structure.
```
dvdauthor -o DVD/ -t foo.mpg && dvdauthor -o DVD/ -T
```
(Creates a folder named **DVD**)

#3 Make an iso.
```
mkisofs -dvd-video -v -o DVD.iso DVD
```
(Creates a file named **DVD.iso**)
_**EDIT**_
If the **mkisofs** command doesn't work, use **genisoimage** instead, like this:-
```
genisoimage -dvd-video -v -o DVD.iso DVD
```

Then burn the DVD.iso file to disc using K3b.

PS Use your own [COLOR="Red"]filename[/COLOR] in step #1 (obviously:D)
PPS With K3b use _**Tools > Burn Image...**_

---

### Post by bloodshot13 on 2010-11-26
Tried step #1 and this my result. The file is there, so I'm not sure why it says no file or directory.

---

### Post by ron999 on 2010-11-26
Hi
If those files aren't in the home directory, if they're in a separate folder such as 'Videos', you will need to use the full path. 
Something like this:-
```
ffmpeg -i [COLOR="Red"]/home/russel/Videos/homevid3.avi[/COLOR] -target ntsc-dvd foo.mpg
```

---

### Post by bloodshot13 on 2010-11-27
I'm finally found the magic folder to do item one and this is what is happening. Are there suppose to be errors(forgive me I'm not sure what I'm looking at)

---

### Post by ron999 on 2010-11-27
> **bloodshot13 said:**
>  Are there suppose to be errors

No, not really.:o

But the bitrate of your homevid3 file is very high (29801 Kb/s).
Maybe the ffmpeg program is struggling to keep up.

I suggest you let it run, then test your new foo.mpg file by playing some of it with VLC or another media player to see if it looks OK.

---

### Post by bloodshot13 on 2010-11-27
k

---

### Post by bloodshot13 on 2010-11-27
it's o.k.. Kinda grainy and there's like real quick computer noise(about the best I can describe it) every once in a while. Last about a second. I guess I'll go on to the next step.

---

### Post by bloodshot13 on 2010-12-04
well I try and build the file structure and get Warning: unknown mpeg2 aspect ratio 1. Then it shows ERR: Error writing data. I've tried taking a screenshot of the this widow but it just hangs up. I've had some problems w/ ubuntu login. I kept getting install warning, Power management may not be installed correctly contact administrator. I've researched this and am finally able to use my computer again(normally). This error is something to do with the hdd  being full and I'm wondering if this maybe why I can't take a screenshot and save it to desktop. I know this is a completely different problem and I will probably make a new thread with this and other issues I'm having.

---

### Post by bloodshot13 on 2010-12-04
> **bloodshot13 said:**
> Well I successfully burned the .iso to dvd with k3b:p. Tried playing the dvd in my home RCA dvd player and.........................................................................no dice:(. Says &quot;The dvd is incompatible&quot;. This is an older dvd player so maybe that's why? Are .iso only compatible on newer dvd players? I did run the dvd in my computer through vlc player and was successful watching the dvd! Thanks for your help! So glad I've got a hard copy of these movies as the video camera that took them is no long with us(as it's dead). Thanks again! I don't know if I should mark this post as &quot;solved&quot; because of the dvd player issue?

 Well I recently got a different dvd player that showed compatible w/ dvd+r dvd+rw/dvd-r/dvd-rw and the original .iso image I made played in this player :). I guess I can mark this thread as solved, even though the other way to make a dvd isn't working. whatcha think?

---

