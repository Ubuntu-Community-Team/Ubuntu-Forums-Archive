---
title: "How do you save movies on harddisc?"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Rohbart on 2008-07-09
Hello,
can someone tell me how I can save movies on the harddisc? I know there is some copy protection but I think theres a way to deal with it. I just don't know how:(

---

### Post by jerome1232 on 2008-07-09
Using K9copy

[https://help.ubuntu.com/community/K9Copy]("https://help.ubuntu.com/community/K9Copy")

there's also a link in there the tells you how to deal with the encryption, kcopy works perfectly for me i just rip them as a .iso, if i burn them to disc they work in dvd players as well.

---

### Post by Rohbart on 2008-07-09
thanks a lot I'll test it

---

### Post by jerome1232 on 2008-07-09
apparently it didn't have the link I thought it did sorry about that
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") the part about libdvdcss2 is what you are interseted in

---

### Post by Rohbart on 2008-07-09
thanks again.
How long does it normally take to save a dvd?
The programm is now running for over an hour and has just copied 15%.
I installed the library using the synaptic package manager and not as described in your second link, is this the cause for the lame progress?
I will let it run till tomorrow, go to bed and check it out when I'm awake (its past 2 AM here in Germany). But please answer anyway.

---

### Post by rzrgenesys187 on 2008-07-09
I run DVDFab Decrypter in wine and it can decrypt a movie easily in around 20~30 minutes for a full disc

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

---

### Post by jerome1232 on 2008-07-09
it depends on your CPU and DVD-Rom speed really what are they?, Usually it extracts the files from the DVD, then records it to an iso, it does take a long time, mostly for the extraction part, I think it 30 minutes or so, I'll do a test 'cuz I usually just go do something else while it's going. This is on a Athlon 64 3700+, x86_64 architecture, a Sony it was 12x or 16x don't remember.


edit: Actually I just started ripping accepted, I know this dvd is encrypted, I'm about 4 minutes in and at 15% so you are getting really slow speeds, might want to uninstall the libdvdcss with --purge and try installing it the second way, that's how I installed it. btw do you rip the entire dvd? I only rip the titleset that contains the main movie

edit: Yeah ripping the main titleset took a mere 15 minutes

---

### Post by Rohbart on 2008-07-10
I just know that my cpu runs at 2666 ghz but I think it should be enough.
I have an Iso now, what is the next step I have to do to get full film?

I have deletedt libdvdss and tried to reinstall it as it is described in the link. But the terminal says: "no such file or directory"

---

### Post by jerome1232 on 2008-07-10
The iso is the full film, you can open it with totem to play on computer, or burn it to dvd and pop it in a dvd player. :)

---

### Post by Rohbart on 2008-07-10
thanks.
And what can I do to save it faster the next time?

---

### Post by jerome1232 on 2008-07-10
Did you add the medibuntu repository and get libdvdcss2 installed?
When you play a dvd from the drive does it work just fine (no jumpiness?)

the steps should be to get libdvdcss2 reinstalled
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install libdvdcss2 build-essential debhelper fakeroot

sudo /usr/share/doc/libdvdread3/install-css.sh

```

and you should have it built and installed

it could be your dvd-rom doesn't have DMA enabled? take a look at this but make sure you figure out what device your dvd-rom is and change the steps accordingly (mine is /dev/hda)
[https://help.ubuntu.com/community/DMA]("https://help.ubuntu.com/community/DMA")

hope that helps

---

### Post by Rohbart on 2008-07-10
> **rzrgenesys187 said:**
> I run DVDFab Decrypter in wine and it can decrypt a movie easily in around 20~30 minutes for a full disc

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

can xou tell me what you've done in addition to installing it?

---

