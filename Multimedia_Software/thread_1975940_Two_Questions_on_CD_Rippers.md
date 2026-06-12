---
title: "Two Questions on CD Rippers"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Ifaistos on 2012-05-08
Hello everyone :-)

I am trying to rid CD's with the two rippers that come preinstalled with Ubuntu.  Namely Ripper X and Asunder CD Ripper.

I like Asunder CD Ripper, because it supports my language, and can create folder name and filenames in my language.  The problem is that it can't rip in mp3.

When I try to select mp3 compression I get the following error : 

'lame' was not found in your path. Asunder requires it to create MP3 files. All MP3 functionality is disabled.

Is there a way to fix this?  Please bare in mind that I have installed "restricted extras".

On the other hand Ripper X does not support my language, but can rip in mp3 format.
Does anyone know if there is a way for Ripper X to support other languages i.e. create folders and filenames in another language?

Thank you all :-)

---

### Post by shantiq on 2012-05-08
first run


```
lame
``` in your terminal to make sure it is there [but should be if you have restricted]:KS

---

### Post by Ifaistos on 2012-05-08
hm...

Thanks for your suggestion.
Strangely it was not installed.
I installed it with
sudo apt-get install lame

and now Asunder works!!

Is lame supposed to be installed when you install restricted-extras or not?

Thanks

---

### Post by shantiq on 2012-05-08
funny.    i thought it was too.....:KS

---

