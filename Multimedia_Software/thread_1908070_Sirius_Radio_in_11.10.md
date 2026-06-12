---
title: "Sirius Radio in 11.10"
date: 2012-01-12
forum: Multimedia Software
---

### Post by teejay17 on 2012-01-12
I can't get Sirius Radio online to work at all in 11.10 on 3 different machines, 2 are 32 bit and one is 64. 
When I was running 11.04 and before, listening to Sirius radio was not a problem. 
Anyone know why this may be so? More importantly, does anyone know how to solve this problem. 
Thanks in advance.

---

### Post by wolfen69 on 2012-01-12
Hmmmm, works for me. Sounds like you just need some codecs. I added the medibuntu repos:
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs gecko-mediaplayer
```
restart firefox.

---

### Post by teejay17 on 2012-01-14
> **wolfen69 said:**
> Hmmmm, works for me. Sounds like you just need some codecs. I added the medibuntu repos:
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then
```
sudo apt-get install non-free-codecs gecko-mediaplayer
```restart firefox.
I did both commands and restarted Firefox and it was a no go. I then restarted my machine and it was still a no-go. Hmmm...
I have the "restricted" package already installed, and of course the gecko media player and its multitude of codecs, as well as the codecs posted above. 
I also have Adblock disabled & pop-ups allowed for the Sirius site. 
Is there anything else? I don't remember it being difficult like this in 11.04 and prior. Gnome Mplayer would just open and start streaming.

---

### Post by wolfen69 on 2012-01-14
I don't know what else you can do. I've had sirius radio streaming in 11.10 on 4 different computers no problem.

Are you running the latest flash?

---

### Post by teejay17 on 2012-01-15
> **wolfen69 said:**
> I don't know what else you can do. I've had sirius radio streaming in 11.10 on 4 different computers no problem.

Are you running the latest flash?

I believe so. 11.10.1

---

### Post by teejay17 on 2012-01-16
Edit: I should also add that it is the Mplayer streamer that isn't opening, or being prompted to open, in Firefox. I even installed the Plugin Toggler extension to make sure that I have Mplayer checked off, and still no go.

---

### Post by wolfen69 on 2012-01-16
I never had a media player pop open and run to listen to sirius. It just ran from the built in media player on the webpage.

---

### Post by teejay17 on 2012-01-16
> **wolfen69 said:**
> I never had a media player pop open and run to listen to sirius. It just ran from the built in media player on the webpage.
I've never had that. It's always been Mplayer that opens for me, and streams Windows Media format. And with Mplayer uninstalled, streaming on the site itself has never worked for me on any version of Ubuntu.

---

