---
title: "ATI Radeon video card"
date: 2013-01-31
forum: Multimedia Software
---

### Post by gordie69 on 2013-01-31
I'm trying to this ati card but it says something about the var/log/jockey.log and won't activate my card driver

---

### Post by Mark Phelps on 2013-02-01
Then ... you need to read through the text in that log to see what error messages it is writing.  We can't just GUESS at what the problem might be!

---

### Post by gordie69 on 2013-02-01
I'm just not sure where to go and read this text it gave me everytime I go to install this card. 

Sorry guys

---

### Post by Yellow Pasque on 2013-02-01
What is the output of:
```
sudo apt-get install fglrx
```

> I'm just not sure where to go and read this text
```
gedit /var/log/jockey.log
```

---

