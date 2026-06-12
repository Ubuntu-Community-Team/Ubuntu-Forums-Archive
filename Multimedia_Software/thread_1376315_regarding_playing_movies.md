---
title: "regarding playing movies"
date: 2010-01-09
forum: Multimedia Software
---

### Post by renjumace on 2010-01-09
i have recently installed ubuntu in my dell inspiron 1525 laptop. i have difficulty playing movies in ubuntu. i have the default movie player but it is not able to play the movie. it asks for plugins to play it. an example of a plugin is here, MPEG-4 AAC decoder,
H.264 decoder. please advise me how to install these plugins and how to get alternative video and audio players.. cheers to all.

---

### Post by HappyFeet on 2010-01-09
Copy and paste into terminal
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs libdvdcss2
```

---

### Post by renjumace on 2010-01-09
will it also solve the problem of no startup music.. normally a sort of music comes after we have provided the entries in the login screen...

---

### Post by renjumace on 2010-01-11
actually the login sound came after doing this.. but will i have to install something extra for the other sounds...

---

