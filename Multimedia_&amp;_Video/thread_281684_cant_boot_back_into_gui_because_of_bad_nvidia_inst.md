---
title: "cant boot back into gui because of bad nvidia install"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by DraeLee on 2006-10-21
hello i am new to linux and i tried to follow a guide to install the nvidia drivers and when i do i get the input not supported so i went to a guide to try and convert back to vesa well when i did i only got half way because the instructions  told to change the nvidia drivers back to vesa but didnt say how.  The instructions were not for someone new to linux so therefore i had to stop and i couldnt find an answer.  so unfortunately i ended up rebooting my machine thinking i fixed the problem. welllll i didnt.  I cant load into the gui.  so i would appreciate any help in trying to fix this otherwise im gonna have to reinstall ubuntu again

---

### Post by tronica on 2006-10-21
when your at the prompt type

> sudo dpkg-reconfigure xserver-xorg

and just follow that and then when your done with that type

> startx

thats not a fix but will get you back into gnome.

---

### Post by DraeLee on 2006-10-21
i tried to do that but it said i need to be in root?

dont know if i said it but as of right now im in safe mode on the disc so i will have to reboot and try this soon as i know how to get into root

---

### Post by tronica on 2006-10-21
sorry

did you have sudo in front of the command

---

### Post by DraeLee on 2006-10-21
lol u know what i just looked at what i had wrote down then and you know what i didnt.  i wrote it exactly how i saw it ok ok .  So now when i type this what do i do.  cause after u answer im gonna give it a go.  oh also ty for your help i appreciate it

---

### Post by tronica on 2006-10-21
when you use that command just use the default every thing, and when it ask you something like simple or advandced just hit simple. and thats it. then when it dumps you at the prompt just type startx

---

### Post by DraeLee on 2006-10-21
well sir i just did what u ask and i do belive i defaulted everything and when i did startx it looked like it worked and then it went right back to the cli prompt i restared the pc totally and still nothing im at a loss

---

### Post by tronica on 2006-10-21
what video card do have

---

### Post by DraeLee on 2006-10-21
nvidia 5200 128mb  geforce

---

### Post by tronica on 2006-10-21
i have that same card and never had any probs. the only other thing i would do is to reinstall ubuntu. i hate to have you do that, maybe someone with in a hour will have a new idea. if you have another computer i suggest you look at this guide, its for new linux users, and its easy.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

i think i would reinstall ubuntu and use that guide.

---

### Post by DraeLee on 2006-10-21
ok i figured i might have to what i will do is this i will reinstall and i will take a look at the guide after I install if you have the same card and this instruction worked for you then i will trust that and make it work if i have a question can i holla back at you

---

### Post by tronica on 2006-10-21
that site is to get new users up and running on everything you can think of. just PM if you have any questions.

---

### Post by DraeLee on 2006-10-21
will do and thanx for all your help ill let u know if im successful

---

