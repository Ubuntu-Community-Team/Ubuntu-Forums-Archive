---
title: "no top or bottom bar in ubuntu 11.04"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by computerboy on 2011-02-28
I just installed ubuntu 11.04 and there is no top or bottom bar, any suggestions?

---

### Post by howefield on 2011-02-28
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by Kirboosy on 2011-02-28
[COLOR=Red]Welcome to the Forums! :D[/COLOR]

Can you right click on the desktop area and hit "Add Panel"? 


I've not tried Natty yet so I'm just blindly shooting....Also since I'm assuming (if I'm wrong forgive me) you are new to Ubuntu I would recommend 10.10. 11.04 isn't ready for primetime just yet. ;)

---

### Post by andrewthomas on 2011-02-28
> **computerboy said:**
> I just installed ubuntu 11.04 and there is no top or bottom bar, any suggestions?
When you log in, at the gdm screen, after you select your username, switch the session from ubuntu desktop to ubuntu classic and you will have a gnome-panel session instead of a unity session.

---

### Post by jennybrew on 2011-02-28
> **computerboy said:**
> I just installed ubuntu 11.04 and there is no top or bottom bar, any suggestions?

Ive had this several times including tonight after the latest updates. In addition I seem to have picked up a bad case of disappearing window borders.
A reboot cured it tonight but I intend doing a fresh install again at the weekend from the latest build (then)

---

### Post by dubmartian on 2011-02-28
ctrl+alt+t to bring up terminal and type:
gnome-panel --replace
you'll lose the panels again if you close the terminal you typed that into.

restarting the xserver to make 'em stay may work too:
ctrl+alt+F1, login and type:
sudo service gdm stop
sudo service gdm start

edit: oh, and if you are using unity, the above code will add panels on top of unity's panel but will act funny.

---

### Post by fflopes on 2011-02-28
I have the same issue for Unity.  I log in and there are no panels, even though the notice of connecting to the wireless and ubuntu one are shown.  It has been over a week now I cannot run Unity.  The classic wm works fine though.  I have an ATI HD3200 board.  Important to say that ctrl+alt+t doesn't bring anything.

---

### Post by dubmartian on 2011-02-28
your right, i now remember i couldnt get the terminal with ctrl+alt+t. i dont think i could right click the desktop or create a launcher so i right clicked a random file, folder, etc, chose "open with other app" and typed gnome-terminal in the "use a custom command" box.

---

