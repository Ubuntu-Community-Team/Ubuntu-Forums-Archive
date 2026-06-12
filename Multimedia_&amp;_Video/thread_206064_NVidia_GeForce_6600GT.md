---
title: "NVidia GeForce 6600GT"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by dannythomas13 on 2006-06-29
Ok, from reading through a few posts a few people seem to be having problems with this card...as i am myself. Does anyone know what can be done to get the NVidia X Server working and how to get the most out of this card as i tried a tutorial in my book saying to use "sudo nvidia-glx-config enable" but after the restart, like so many it seems...we get errors ad nothing works.
can anyone help as i would like to know how to get this set up so i can try out a nice 3d game...if i can find one, just trigger at the minute
thanks to everyone who replies for your time
Daniel =)

---

### Post by princemackenzie on 2006-06-29
[QUOTE=dannythomas13]Ok, from reading through a few posts a few people seem to be having problems with this card...as i am myself. Does anyone know what can be done to get the NVidia X Server working and how to get the most out of this card as i tried a tutorial in my book saying to use "sudo nvidia-glx-config enable" but after the restart, like so many it seems...we get errors ad nothing works.
can anyone help as i would like to know how to get this set up so i can try out a nice 3d game...if i can find one, just trigger at the minute
thanks to everyone who replies for your time
Daniel =)[/QUOTE]

I have this card and it is operating fine for me.  Have you followed the guide [here]("http://www.ubuntuforums.org/showthread.php?t=139264")?  What kind of errors do you get?  What do you mean by "nothing works"?

Please respond so we can help you!

---

### Post by tonyr on 2006-06-29
Read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by tseliot on 2006-06-30
[QUOTE=dannythomas13]Ok, from reading through a few posts a few people seem to be having problems with this card...as i am myself. Does anyone know what can be done to get the NVidia X Server working and how to get the most out of this card as i tried a tutorial in my book saying to use "sudo nvidia-glx-config enable" but after the restart, like so many it seems...we get errors ad nothing works.[/QUOTE]
"sudo nvidia-glx-config enable" is broken. Use the following command instead:
```
sudo nvidia-xconfig
```

---

### Post by gibbylinks on 2006-06-30
Hi

Is your card a genuine Nforce 6600GT. I ask because my card is INNO3D 6600GT and I had to flash the card BIOS to a different make before I got it to work with the Nvidia drivers. 

I struggled with this for ages before trying it. I couldn't believe it would work, but it did. I'm not at home just now so I can't post the exact details.

If this applies to you PLEASE make sure you know what your doing BEFORE you flash your card.

---

