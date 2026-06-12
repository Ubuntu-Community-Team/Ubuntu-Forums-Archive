---
title: "Ubuntu not detecting sound device"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by Shazda on 2006-02-07
I have an old 98 compaq presario 5240, I recently installed linux on this old machine but I cannot get the sound to work (onboard) When I go to volume control it says, "Error: No volume control elements and/or devices found" So im guessing its not able to detect it. If you could help them that would be great, thanks.

---

### Post by FarEast on 2006-02-07
Hi Shazda,

Your sound chip seems to be on ISA bus.  Do the following to know which
chip it is.

$ sudo apt-get install isapnptools
$ pnpdump > isabus.txt
$ gedit isabus.txt

Find information regarding the sound chip and paste it;) .

---

### Post by Shazda on 2006-02-07
This is what i get:

brandon@ubuntu:~$ $ sudo apt-get install isapnptools
bash: $: command not found
brandon@ubuntu:~$ $ pnpdump > isabus.txt
bash: $: command not found
brandon@ubuntu:~$ $ gedit isabus.txt
bash: $: command not found
brandon@ubuntu:~$

---

### Post by FarEast on 2006-02-08
Oh...
You do not need to type '$'.

---

### Post by wncben on 2006-02-08
hey there
 Try running the comands but do not add the extra $ ie:

sudo apt-get install isapnptools

etc.  

I am a newbie too, and made the same mistake.

Keep on keepin on, the more you play with the command line the easier it gets.  Despite the issues I've encountered so far, this is still easier than installong winblows.:p 

~Ol' Ben

---

