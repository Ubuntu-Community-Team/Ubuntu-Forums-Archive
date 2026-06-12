---
title: "Problem Changing Default Programs for Media"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by spock959955 on 2006-10-18
I seem to be experiencing a great deal of trouble changing the the programs that different file types open with by default. For example, MP3s open with totem by default; I wish to change this to Amarok. 

I fully realize that the way it is supposed to work is 
left click on a file -> "properties" -> "open with" tab -> click the radio button of the program you wish it to open with

The problem I run into is that it will not allow me to select any of the radio buttons of alternate programs; they are not greyed-out, they just don't fill in when I click them. The rest of the line *is* highlighted, but the radio button itself does not become selected. And yes, I am clicking *directly on* the radio button itself. This happens when I'm logged in as root as well, so I don't think it's a permissions thing.

This problem is rather infuriating, and I would greatly appreciate any help anyone can give. Thanks!

---

### Post by spock959955 on 2006-10-18
hmmm...well, I made a little bit of progress. I found that if I run ```
gksudo nautilus
``` then it will actually allow me to select the radio buttons. The problem is, changing the setting in root does not carry over to my usual account. It will now open MP3 files in Amarok when I'm opening them as root, but will still open them in Totem when I'm opening them in my regular account, and it still does not allow me to change the association through my regular account. Suggestions?

---

### Post by Kateikyoushi on 2006-10-18
That's interesting what are your rights over those media files ?

---

### Post by spock959955 on 2006-10-24
Upon closer inspection, this does appear to be some sort of a permissions issue, although I'm not sure what's causing it. My account is an administrator account, so I should have the proper permissions/privleges to do anything (Under "Users and Groups", all of my user priveleges under the "user priveleges" tab are checked). I'm sure this is all somehow related to another problem I'm having; Alacarte Menu Editor will not actually let me edit my menu. I select all the changes I wish to make, but once I close the program, none of the changes I told it to make take effect. The strange thing is, I found that if I create a new user account and try to change these things in the new account (menu, file associations), it works just fine. It seems to be just my account that's having this problem

---

### Post by spock959955 on 2006-12-03
Well, some new progress has been made. I found a round-about way of changing the default programs assigned to open the different media types: by

```
sudo gedit /usr/share/applications/defaults.list
```

and editing / adding file associations where neccesary. Although this works, it is somewhat inconvenient. I changed ownership of this file to myself, and chmod-ed it to 777, but I still cannot change the default programs through the regular method (described in my first post). 

Perhapse the discovery of this method of working around the problem can help others in determining why I cannot change the file associations through the regular method. Or, at the very least, it can help others who are experiencing this same problem. Best of luck!

---

### Post by spock959955 on 2006-12-28
Another update:

Recently, I completely formatted my "/" partition (I gave "/" and "/home" their own partitions), and then did a fresh install Edgy (previously, I had been using dapper).. Oddly enough, I'm STILL experiencing the same problems. Not quite sure what this means..........

---

### Post by stebrepar on 2007-01-31
I'm having the same frustration (with totem's being set for pretty much all media, but its failing to handle many .wmv files). In another thread I came across the Firefox "MediaPlayerConnectivity" extension, which in a first try just now seems to be an acceptable workaround for the time being.
See [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
-- 
Stephen

---

