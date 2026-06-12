---
title: "How to make Amarok my default music player on gnome?"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Prisma on 2007-06-03
Does anybody knows how make Amarok my default music player on gnome? i am not talking about file association, i am talking about fooling gnome to think Amarok is its default music player.

See, the problem is that I deleted Rhythmbox. Now when i hit the media key on my keyboard to call for my default music player gnome looks for that useless piece of *@$$&*! .... :p ..... looks for Rhythmbox instead of Amarok even though Amarok is the only music player install on Ubuntu. Why you cant chose your default music player in your preferred applications is something that escapes all reason. Also my media keys for play and pause dont work anymore even though i have set them up again. Would someone please explain how can you fix this?

Thanks

---

### Post by Prisma on 2007-06-03
This is the error message i am getting. Any thoughts about how to fix this? :D

---

### Post by Prisma on 2007-06-03
how can I replace the command rhythmbox with the command amarok? where is this information stored in ubuntu? where i can edit it?

---

### Post by Julolidine on 2007-06-03
OK, this is really hack-ish but it will work.   As far as I can find, chosing a new media player in the application preferences is not yet implemented, but is coming soon.  

```
sudo ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

You should definitely have rhthymbox not installed in this case, because this procedure will completely bork the rhythmbox launcher, and any time you try to call it, amarok will come up.  

To make sure /usr/bin/amarok is the path of amarok 
type
which amarok 

in the terminal.   If it comes up differently change the link path.

---

### Post by Prisma on 2007-06-03
Thank you for that tip i will try it.  :popcorn:

---

### Post by Monosabio on 2008-03-15
Just go to System -> Preferred Applications -> Multimedia 
Then chose Custom Player option and type amarok in Command field.

Then if you want to control Amarok with your multimedia keyboard keys, you will have to install a Script called Gnome Multimedia Keys. For this go to Tools -> Script Manager -> Get More Scripts and install it by selecting it from the list.

---

