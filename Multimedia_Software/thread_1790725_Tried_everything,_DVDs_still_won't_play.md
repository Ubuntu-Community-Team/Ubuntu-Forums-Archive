---
title: "Tried everything, DVDs still won't play"
date: 2011-06-25
forum: Multimedia Software
---

### Post by tcamdg on 2011-06-25
I've tried every different method of installing/reinstalling DVD support (libdvdcss2, etc.), and DVDs still won't play. The only thing I haven't tried is reinstalling Ubuntu 11.04 from scratch, because that's really not a viable option for me.

How can I get DVDs to play???

Please help.

---

### Post by ahears on 2011-06-25
Did you remember to run "sudo /usr/share/doc/libdvdread4/install-css.sh" script after installing the ubuntu-restricted-extras package?

---

### Post by tcamdg on 2011-06-25
> **ahears said:**
> Did you remember to run "sudo /usr/share/doc/libdvdread4/install-css.sh" script after installing the ubuntu-restricted-extras package?
Yes.

---

### Post by ahears on 2011-06-25
Sounds lika a Codec problem. 32 bit and 64 bit respectively.


wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb) && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb


I am assuming that the DVD player works but you cannot play DVD movie content due to a Codec Decryption problem, meaning that your hardware is ok right?

---

### Post by eddier on 2011-06-25
Can you confirm the Hardware is ok. i.e the DVD player.

I ask because a friend was having problems not being able to read DVD,s. CD's were ok!

Tried his player in my PC with the same result. The player is only 2 years old.

Put a new DVD player in to his PC and Bingo!

eddie

---

### Post by ahears on 2011-06-27
> **ahears said:**
> Sounds lika a Codec problem. 32 bit and 64 bit respectively.


wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb) && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb


I am assuming that the DVD player works but you cannot play DVD movie content due to a Codec Decryption problem, meaning that your hardware is ok right?


I hope this closes your problem, please mark this thread as SOLVED. Thank you.

---

### Post by tcamdg on 2011-06-30
> **ahears said:**
> I hope this closes your problem, please mark this thread as SOLVED. Thank you.

Strange...

I had previously installed those same exact codecs (amd64), and it didn't work then.

But now it works.

Sorry I didn't get back to this thread earlier.

Thanks!

---

### Post by ahears on 2011-06-30
Anytime! :)

---

