---
title: "login logout sound problem solved"
date: 2009-06-06
forum: Multimedia Software
---

### Post by empty_tank on 2009-06-06
i installed ubuntu jaunty UNR in  my eeepc 900ha and the only problems i had were system login and logout sounds not working.  After searching, the solutions that worked for me are:

1.  install gnome-session-canberra (this fixed my login sound problem)
2.  for logout sound problem, edit /etc/gdm/PostSession/Default

     - gksu gedit /etc/gdm/PostSession/Default
     - insert the following line before "exit 0"

/usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout"

---

### Post by L.J on 2009-06-06
Hey, I need some help with my logout sound, can you explain exactly what to do to fix it please as i am relatively new to linux. Sorry for my inexperience. Any help will be appreciated :D.

---

