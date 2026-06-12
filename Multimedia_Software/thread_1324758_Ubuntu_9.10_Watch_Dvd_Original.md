---
title: "Ubuntu 9.10 Watch Dvd Original"
date: 2009-11-12
forum: Multimedia Software
---

### Post by aloha.am on 2009-11-12
hello

i dont know how to watch movies in my new Ubuntu 9.10 ,

please tell me how to active, see, please.....

i whait yours answers

---

### Post by HappyFeet on 2009-11-12
Copy and paste the following into a terminal and hit enter.
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
Then
```
sudo apt-get install libdvdcss2
```

---

### Post by lschwarcz on 2010-01-27
> **HappyFeet said:**
> Copy and paste the following into a terminal and hit enter.
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
Then
```
sudo apt-get install libdvdcss2
```

I tried this and when I put a regular commercial DVD in the drive I get the error: No URI handler implemented for "dvd"

Is there some extra step I need to perform?

Thanks!
Larry.

---

### Post by ETbluez on 2010-01-27
> **lschwarcz said:**
> I tried this and when I put a regular commercial DVD in the drive I get the error: No URI handler implemented for "dvd"

Is there some extra step I need to perform?

Thanks!
Larry.
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Karmic#DVD_Playback_Capability)

---

### Post by sBoss on 2010-02-13
Hmm...that's odd.  When I cut and paste the list of commands into the terminal it worked right away.  You didn't have some other synaptic tool open did you?

---

