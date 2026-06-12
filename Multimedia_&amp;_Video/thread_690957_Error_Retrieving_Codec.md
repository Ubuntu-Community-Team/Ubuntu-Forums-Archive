---
title: "Error Retrieving Codec"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Speedy162005 on 2008-02-08
So a little background on my issue. I installed the Firefox 3 beta. I didn't like it, so I went back to Firefox 2, which took a lot of work and what not, but I finally got it up and running somehow.

Anyways, I went to Totem to try and get the codec for my DVD to work, however, when I tried to get it, I received the following message:

Could not launch URL "http://www.gnome.org/projects/totem/#codecs": Failed to execute child process "/usr/lib/firefox-3.0/firefox-3.0" (No such file or directory)

Fine, so I created that directory and tried to do a redirect, which I think I did wrong, and now I receive this error message:

Could not launch URL "http://www.gnome.org/projects/totem/#codecs": Failed to execute child process "/usr/lib/firefox-3.0/firefox-3.0" (Permission denied)


Anyways, I know my copy of firefox is located at 

/usr/lib/firefox

I am pretty sure that all Totem is trying to do is launch Firefox, but it is going to the wrong directory. How do I make This work?

---

### Post by HappyFeet on 2008-02-08
not sure why totem is doing that, but here is how to get dvd codecs.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
```

---

