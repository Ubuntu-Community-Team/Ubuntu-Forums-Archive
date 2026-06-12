---
title: "Audacity not recording, Ardour GTK not initializing JACK"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by dolphinsonar on 2006-12-09
Ardour can not connect to Jack:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=20804&stc=1&d=1165721680%5C[/IMG]


and Audacity shuts down everytime I click the record button.  Anyone have any ideas?

---

### Post by le_vainqueur on 2006-12-18
I'm having this problem as well

---

### Post by BRAXS69 on 2007-09-08
you need to install "jackd" ~ server plus to make things easier on getting things running you need to install "qjackctl" ~ this will provide a configuration interface for jackd....

```
sudo apt-get jackd qjackctl
```

thin you need to go "applications >> Sound and Video >> Jack Control" and make sure you dont have anything that is using your sound card at the moment when you click "start" on the control. 

now that all thats done you can run "Ardour" or anything else that utilizes jack....

---

