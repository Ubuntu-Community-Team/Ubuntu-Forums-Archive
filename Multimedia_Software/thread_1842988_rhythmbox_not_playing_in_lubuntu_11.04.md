---
title: "rhythmbox not playing in lubuntu 11.04"
date: 2011-09-12
forum: Multimedia Software
---

### Post by mabtifro2 on 2011-09-12
music works fine in audacious which i would use if it had a library, but it doesnt, so i downloaded rhythmbox and the songs load up fine in the library, but they dont work when i try to play them, they just either freeze the player, or shoe a red icon next to the track...

does this problem has a fix??

---

### Post by mabtifro2 on 2011-09-13
its an eeepc 900 by the way

---

### Post by mabtifro2 on 2011-09-15
anyone?

---

### Post by mabtifro2 on 2011-09-21
someone answer my question dammit!!! that, or suggest a new music player with a navigable library like rhythmbox

---

### Post by BicyclerBoy on 2011-09-21
You don't help your cause by not including useful info..
And endless sentences joined by commas are hard to digest.
 
I think rhythmbox uses gstreamer backend..

The default ubuntu gstreamer packages is missing all the non-free stuff.
You could get/install the gstreamer good, bad & the ugly packages.
They are available via synaptic package manager etc.

[http://en.wikipedia.org/wiki/GStreamer](http://en.wikipedia.org/wiki/GStreamer)

What are the file types ? AAC?

Normally rhythmbox prompts the user to download any required mp3 codecs.

I prefer clementine.

---

### Post by amjjawad on 2011-09-21
> **mabizeid said:**
> someone answer my question dammit!!! that, or suggest a new music player with a navigable library like rhythmbox

With such attitude, people will NOT jump to help, myself included. However, since I spent few seconds reading this thread, I don't mind to spend a little more to write this.

Please, use [www.googlubuntu.com](www.googlubuntu.com) or [www.google.com](www.google.com) and I'm sure you'll find the solution if there is no one answering your thread.

Good luck!

---

### Post by garvinrick4 on 2011-09-21
> someone answer my question dammit!!! that, or suggest a new music player with a navigable library like rhythmbox
Wow relax a bit, you must be a youngster, a spoiled one at that.
Open Ubuntu Software center and install the gstreamer that I have installed. (check mark)
We have a code of conduct in these Forums so chill or you will get asked to not come back.
Enjoy your Ubuntu, young man. Click on thumbnail.

---

### Post by garvinrick4 on 2011-09-21
If any of you new users do not know what codec's you need, what java, flashplayer and such. In post installation:
```
sudo apt-get install ubuntu-restricted-extras
``` will give you it all.

When it asks to install fonts from microsoft use tab key arrows and enter to navigate.
Here it is in Ubuntu software Center.

---

### Post by mabtifro2 on 2011-09-21
mp3, ogg, m4a... nothing works, i just downloaded clementine, doesnt work either, included screenshot, apparently citrus is hard to digest too

---

### Post by mabtifro2 on 2011-09-21
> **garvinrick4 said:**
> Wow relax a bit, you must be a youngster, a spoiled one at that.
Open Ubuntu Software center and install the gstreamer that I have installed. (check mark)
We have a code of conduct in these Forums so chill or you will get asked to not come back.
Enjoy your Ubuntu, young man. Click on thumbnail.

come on guys i was kidding, what fool really makes demands like that on a forum and expects someone to help... but then again after one week with no response, a little attitude generated some useful tips! :p

ill try your suggestions and let you guys know, thanks!!!

---

### Post by BicyclerBoy on 2011-09-21
Nothing like lemon juice rubbed in the wounds but NZ sweet navel orange is the best.
It was drawn by Monet so it was actually a lemon..

That looks like it is trying to download album art etc..
It does not look like a music playback error.

Clementine is gstreamer based so you still need the good bad & the ugly set..

Have you been messing around under-the-hood with pulse audio & alsa ?

ogg & wav work out of the box if I'm remembering correctly.

---

### Post by mabtifro2 on 2011-09-26
i tried all your suggestions right after your posts and nothing worked but it was late here where i am so i went over everything again more carefully and still cant figure out why its not working. it cant be a codec problem. i installed all the codecs and im sure neither ogg or wav are working. its a playback issue for sure. gnome player and audacious play everything, but rhythmbox and clementine choke. attached is the error symbol i get when i try to play in rhythmbox (a wav file btw). any other ideas?

---

### Post by mabtifro2 on 2011-09-26
ok new issue: i just realized after installing all the codecs it never asked me to install microsoft fonts. i dont have a software center, but when i opened up synaptic it gave me an error and told me to manually install:

sudo dpkg --configure -a

so i did and went back to synaptic and this time it worked normally right, then i go to close it and it has an application in the install queue and it turns out to be ms fonts and so i click apply all changes and it begins to install but it just freezes here. i rebooted and tried again and same deal. i even had to run that above command to get synaptic to open. so im lost. thanks.

the attachment is a screen shot of where it freezes

---

### Post by BicyclerBoy on 2011-09-27
Try..
aptitude -f update

Have you added any extras ppa/repositories ?
Have you removed ppa/repos without removing the packages first ?

---

### Post by mabtifro2 on 2011-10-15
man my system really got screwed up trying to fix this problem, so many problems till i downloaded lubuntu 11.10 and upgraded from flash drive, now EVERYTHIGN works perfect!!!!!!!!!!!!!!!! yaaaa boooyyyyyyyyy!!!

---

### Post by amjjawad on 2011-10-15
> **mabizeid said:**
> man my system really got screwed up trying to fix this problem, so many problems till i downloaded lubuntu 11.10 and upgraded from flash drive, now EVERYTHIGN works perfect!!!!!!!!!!!!!!!! yaaaa boooyyyyyyyyy!!!

HOOOHAAA© :D

Lubuntu ROCKS!

Well done and I'm so glad to know that. Yet again, another happy Lubuntu User :D

---

### Post by mabtifro2 on 2011-10-16
yea man thanks for your help. i first tried lxde on my beloved 900 about 2 years ago i think, i think i had it dual gnome/lxde but i let my uncle borrow it and he put windows on it :mad:

ive tried so many light weight distros in the past, i really wanted to settle down finally and then i discovered lubuntu, im totally into it. now i just gotta figure out how to get the horizontal two finger scroll work and ill be set!

[IMG]http://www.productwiki.com/upload/images/asus_eee_pc_900.jpg[/IMG]

I LOVE MY 900!!!!!!!!!!!!!!!!

---

### Post by amjjawad on 2011-10-16
I'm SO glad to know you are all into Lubuntu now :D
And you are welcome, I've done nothing much :)

If I'm not mistaken, I've seen that somewhere on LXDE Forum. Why not search there? I'm talking about the scroll issue :)

I'm about to leave soon so I'm sorry for not posting the direct link for you!

---

### Post by mabtifro2 on 2011-10-17
ill check it out in about a week when im back at home, im traveling right now.

---

### Post by amjjawad on 2011-10-17
> **mabizeid said:**
> ill check it out in about a week when im back at home, im traveling right now.

Ok, good luck and have a safe trip.
Just keep us posted and if I'll find that, I'll post it here for you :)

---

