---
title: "DVD's STILL won't play!!"
date: 2011-06-06
forum: Multimedia Software
---

### Post by ablot on 2011-06-06
Hi,
I am simply trying to watch a shop bought DVD ... but no go. I have followed the ubuntu support info on restricted DVD playing ... it appears that I have all that is required to play a DVD ... I have tried Movie Player, Kaffiene, SMPlayer but they all seem to say the same thing - that they cannot read/find the source. Anyone have any ideas please?

---

### Post by SeijiSensei on 2011-06-06
Did you run "sudo /usr/share/doc/libdvdread4/install-css.sh"?

---

### Post by ablot on 2011-06-06
I tried to but for some weird reason ubuntu would not accept my administrator password at the terminal!

---

### Post by SeijiSensei on 2011-06-07
Ubuntu doesn't have a root (administrative) password by default.  The account created during installation has root privileges via sudo.  If you're the owner of that account, you should use your own password when prompted by sudo.

---

### Post by ablot on 2011-06-07
Sorry if I sound a bit thick here but I believe I only have two passwords ... 1. the one I use each time ubuntu starts up - this is what I believe is called the user password - in other words it only allows me access to the ubuntu where I can use things like open office, gimp, email stuff, and other software). This does not allow me to delete/change/download software. 2. the one I use to access ubunutu software center so that I can delete/change/download a program ... I understand this to be the administrator password. If that is the incorrect title then I am sorry for the confusion - however, this is the password I believe to be the one I use in the terminal. I have tried the user password in the terminal (just in case) but I was promptly told that not only was it the incorrect password - but I would be reported for typing in such a thing!! ... so I won't try that one again. So, your response is a bit puzzling. Are you saying that I a third password?

---

### Post by whatthefunk on 2011-06-07
> **ablot said:**
> Sorry if I sound a bit thick here but I believe I only have two passwords ... 1. the one I use each time ubuntu starts up - this is what I believe is called the user password - in other words it only allows me access to the ubuntu where I can use things like open office, gimp, email stuff, and other software). This does not allow me to delete/change/download software. 2. the one I use to access ubunutu software center so that I can delete/change/download a program ... I understand this to be the administrator password. If that is the incorrect title then I am sorry for the confusion - however, this is the password I believe to be the one I use in the terminal. I have tried the user password in the terminal (just in case) but I was promptly told that not only was it the incorrect password - but I would be reported for typing in such a thing!! ... so I won't try that one again. So, your response is a bit puzzling. Are you saying that I a third password?

If its your home pc, then you dont have to worry about being "reported" for using a wrong password.  All that that means is that your attempt at gaining access to system files was logged.  I assume that it is your home computer so the only person who would see that log is you.  Hopefully you go easy on yourself.  If you were at work or something, then you might get in trouble.

---

### Post by ablot on 2011-06-07
.Yes -its my home computer. So why is the terminal not recognizing my password ... which it does quite happily if I want to do anything in ubuntu software center? ... And I know the password is the correct one for making any changes on the computer.

---

### Post by SeijiSensei on 2011-06-07
When you run a command with sudo, you need to *use the same password you use to log in*.

---

### Post by ablot on 2011-06-07
Please bear with me here SeijiSensei ... you are saying that I must use the same password as the one I used when I started up my computer ... which in this case was my username's password. Well, when I try that password in the terminal I am told that my username is not in the sudors file. So how do I add my username to the sudors file?

---

### Post by ablot on 2011-06-07
... OK sussed it! I had to swith to my admin screen - add my username to sudors file - then go back to username terminal and voila it loaded libdvdread4 ... and now I can watch Pirates of the Caribean (again!) till my hearts content ... and as for all those 80's porn films ...!!! YIPPEE - seriously, thanks folks!

---

### Post by Dlambert on 2011-06-07
VLC is the best.

---

### Post by Dlambert on 2011-06-07
Also mark thread as solved.

---

