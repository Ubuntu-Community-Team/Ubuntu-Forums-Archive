---
title: "Anybody using cdrecord to copy audio cds?"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by andrew.46 on 2007-10-03
Hi,

 I have been using cdrecord to burn data cds and data dvds quite successfully and was keen to try copying audio cds as well. But I will admit to finding the instructions in the man pages more than a little baffling. Not much on the Internet either.

 Has anybody managed to successfully use cdrecord for this purpose? All is not lost for me I use Gnomebaker instead, but I suspect Gnomebaker uses cdrecord anyway ....

                       Andrew

---

### Post by andrew.46 on 2007-10-04
Hi,

 Surely it can't be this simple:

```
$ cdparanoia -B
$ cdrecord -v speed=4 dev=scsiaddress -audio -pad *.wav
```

 Hmmm..... time to produce some coasters :-)

             Andrew

---

