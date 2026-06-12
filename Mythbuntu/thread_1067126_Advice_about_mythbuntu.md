---
title: "Advice about mythbuntu"
date: 2009-02-11
forum: Mythbuntu
---

### Post by csbright on 2009-02-11
Hello People. 

Okay here goes, 

I hope someone will take the time to read this post and give me a little advice. I work in the Audio/Video industry and have been collecting music and movies for years. A couple of years after several frustrating thefts of music from my store. I decided to start making ISO's of all the music I still had and of everything I purchased in the future. As well as I got this lame brain idea of also storing all my DVDs in the same format. An ISO. This keeps everything intact on the DVD does not compress it and only takes up crap loads of storage space on my hard drive. As the cost of hard drives had dove I have stored more and more of my movies in an ISO form. I use a virtual drive to load the movie and watch them on my computer or output them to my TV. But never have been able to find a program that would allow me to create a searchable database in any of the normal media players, like you might with a folder filled with MP3's. 

At some point someone had suggested I look closely at mythbuntu because they thought it would be able to do everything I would like it to. I see that it can also be a PVR as well as access to my netflix account etc etc. 

So my basic question before I start digging deep into unbuntu and mythbuntu. The question I have is this. 

Lets say I have 3 1TB drives all filled with ISO's of DVD's. Will I actually be able to have mythbuntu go out and try to find the art work etc for the ISO's and be able to browse or search them like a might a Music library?  

My machine I will be running both the backend and frontend on at the moment is a 
MSI DKA790GX Platnium 
2gig of Corsair memory 
AMD Dual Core Kuma 7550 

Much thanks in advance for your time 

CsBright

---

### Post by nickrout on 2009-02-11
> **csbright said:**
> Hello People. 

Okay here goes, 

I hope someone will take the time to read this post and give me a little advice. I work in the Audio/Video industry and have been collecting music and movies for years. A couple of years after several frustrating thefts of music from my store. I decided to start making ISO's of all the music I still had and of everything I purchased in the future. As well as I got this lame brain idea of also storing all my DVDs in the same format. An ISO. This keeps everything intact on the DVD does not compress it and only takes up crap loads of storage space on my hard drive. As the cost of hard drives had dove I have stored more and more of my movies in an ISO form. I use a virtual drive to load the movie and watch them on my computer or output them to my TV. But never have been able to find a program that would allow me to create a searchable database in any of the normal media players, like you might with a folder filled with MP3's. 

At some point someone had suggested I look closely at mythbuntu because they thought it would be able to do everything I would like it to. I see that it can also be a PVR as well as access to my netflix account etc etc. 

So my basic question before I start digging deep into unbuntu and mythbuntu. The question I have is this. 

Lets say I have 3 1TB drives all filled with ISO's of DVD's. Will I actually be able to have mythbuntu go out and try to find the art work etc for the ISO's and be able to browse or search them like a might a Music library?  



yes, but it will do so from the file names, so they need to be sensibly named, not some random collection of characters.

(you can also manually enter the IMDB number if it is not found by searching on the filename, but for your number of movies it would be tedious).

---

### Post by newlinux on 2009-02-11
IF you are just interested in the movie and music features and not the PVR, I recommend you look into XBMC
[http://xbmc.org/](http://xbmc.org/)

---

### Post by freak42 on 2009-02-12
> ... But never have been able to find a program that would allow me to create a searchable database in any of the normal media players, like you might with a folder filled with MP3's.

You likely won't be able to do that. MP3s (and some other media file types) carry meta information about the data it contains (so in the mp3 file is a header that carries all the information like title,artist, song,album,year....)

.iso is just a disk image format not a multimedia format it does not contain any meta information at all, so there is no way that your computer can find out information about it's contents easily.

---

### Post by csbright on 2009-02-12
Alright so which is it.... it will with some work on my part like naming the movie correctly or adding in the IMDB #.. or just simply will not. I would like this for all of its functionality. Also the PVR function. Although wth the amount of content you canget directly off the sites themselves. the pvr is the last issue to tackle. If my shows are avaiable via the net instead of cable. well then pvr is not the issue. But I now have two people saying it is possible if I am willing to spend the time and learning curve to do it. and One no it is not possible. 

I would assume this means it is more possible then not with a little work am I right ? 

I do not mind getting my hands dirty. so digging is screwing with code in the console may be my downfall. But that is why I always will have a MCE as a back up if I give up.

thanks much 
Chris

---

### Post by nickrout on 2009-02-12
you don't need to do any work at the console.

in video manager you select a movie hit "i" (on your remote) and select "search" from the popup menu. It finds the movie on imdb based on the filename and loads the metadata. If it finds more than one match (as it did for me on "The Day The Earth Stood Still" just yesterday) it will let you choose the correct one. If it doesn't find it (rare movie, filename error, etc) then you can manually enter the imdb number, which you find using your web browser on another computer.

There are scripts to do this in bulk, ie you run the script and it goes through your entire movie collection and gets metadata for what it can find automatically. That will require the console, but equally its not difficult.

There are other alternative grabbers that use other movie sites, or which are more geared to TV episodes.

If I were you my plan would be to go through your collection and get the filenames right **first** and then let the imdb bulk grabber loose on them. You'll probably get 90% of them right straight up.

---

### Post by nickrout on 2009-02-12
> **freak42 said:**
> You likely won't be able to do that. MP3s (and some other media file types) carry meta information about the data it contains (so in the mp3 file is a header that carries all the information like title,artist, song,album,year....)

.iso is just a disk image format not a multimedia format it does not contain any meta information at all, so there is no way that your computer can find out information about it's contents easily.

While technically you are right about the built in metadata, myth offers easy ways to import the metadata, see my other posts in this thread.

---

