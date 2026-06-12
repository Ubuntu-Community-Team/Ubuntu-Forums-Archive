---
title: "Can't boot"
date: 2009-11-23
forum: Mythbuntu
---

### Post by tominated on 2009-11-23
Hi,
I just installed mythbuntu 9.10 on a friends pc (erased xubuntu 9.10 that I installed previously) and got through the install fine and set up myth-backend, but when I boot, it always comes up with the terminal's login screen and is really flickery. The keyboard is also very erratic (will not type everything that i input - i checked with multiple keyboards too). I can't login, because I can't type the password without it stuffing up. I selected the automatically log in checkbox when I set it up, too. I really need this box running. Is there anything I can do?

P.S. Bit of a linux newb, but i know my way around the terminal

---

### Post by blazemore on 2009-11-23
That sounds more like a hardware issue.
When you say it's "flickery" do you mean the display is flickery?
Have you tried with a different display?

---

### Post by kja999 on 2009-11-23
> **tominated said:**
> Hi,
I just installed mythbuntu 9.10 on a friends pc (erased xubuntu 9.10 that I installed previously) and got through the install fine and set up myth-backend, but when I boot, it always comes up with the terminal's login screen and is really flickery. The keyboard is also very erratic (will not type everything that i input - i checked with multiple keyboards too). I can't login, because I can't type the password without it stuffing up. I selected the automatically log in checkbox when I set it up, too. I really need this box running. Is there anything I can do?

P.S. Bit of a linux newb, but i know my way around the terminal

Is the flickering fast for a few minutes and then stops completely ?
Sounds like X can't find a valid screen to use and is dropping you back to console.
Log in (at console) and have a look through the Xorg log (/var/log/Xorg.0.log)
The end should show you the error (assuming any of this is correct ;)  )

---

### Post by jjuzwik on 2009-11-23
I have the SAME exact problem.  Fresh install of 9.10, hardware all works fine during the install...  It also works fine on the old 8.10 i was running.



> **tominated said:**
> Hi,
I just installed mythbuntu 9.10 on a friends pc (erased xubuntu 9.10 that I installed previously) and got through the install fine and set up myth-backend, but when I boot, it always comes up with the terminal's login screen and is really flickery. The keyboard is also very erratic (will not type everything that i input - i checked with multiple keyboards too). I can't login, because I can't type the password without it stuffing up. I selected the automatically log in checkbox when I set it up, too. I really need this box running. Is there anything I can do?

P.S. Bit of a linux newb, but i know my way around the terminal

---

### Post by jjuzwik on 2009-11-23
Assuming you have an nvidia video card...

See my post [HERE]("http://ubuntuforums.org/showthread.php?p=8372990#post8372990") on how to fix it.  

Its easy, if you have another pc nearby that can ssh into the hurting box;)

---

### Post by tominated on 2009-11-23
Figured it out! It seems it is a common problem with installing the nvidia drivers at setup, so I used the open source drivers, then once set up, I installed the nvidia ones! 
Thanks for your help anyway!

---

