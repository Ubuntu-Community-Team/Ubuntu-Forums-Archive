---
title: "Movie Player Not playing dvd's"
date: 2010-09-17
forum: Multimedia Software
---

### Post by Joe_Ib on 2010-09-17
I am using ubuntu 10.04 and the default movie play that is automatically there is not reading dvds.  

It says:
"Totem connot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart totem to be able to play this media."


I did a little (not a lot) of looking and have tried one thing so far and have tried:

 ```
sudo apt-get install libdvdread4
```
Followed by
 ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```and to no effect

Any suggestions and help would be greatly appreciated.

---

### Post by davidmohammed on 2010-09-17
does installing all the restricted extras codecs work?


sudo apt-get install ubuntu-restricted-extras

---

### Post by Joe_Ib on 2010-09-17
Ill give it a shot seems as though its going to take 8 mins or so before I will know if it works or not.

---

### Post by lukeiamyourfather on 2010-09-17
I'd try another media player like VLC. Also see this if you haven't already.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Joe_Ib on 2010-09-17
> **davidmohammed said:**
> does installing all the restricted extras codecs work?


sudo apt-get install ubuntu-restricted-extras



Worked thank you very much

---

