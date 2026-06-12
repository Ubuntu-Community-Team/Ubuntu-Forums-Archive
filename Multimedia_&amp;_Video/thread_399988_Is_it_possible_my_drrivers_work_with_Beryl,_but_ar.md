---
title: "Is it possible my drrivers work with Beryl, but are not interfacing with games"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by Hortinstein on 2007-04-03
Hi, I have tried a few 3d games on my desktop after I installed the ATI 8.34.8  drivers....I know that they are not the newest, but everygame i try...Secondlife Alpha client, and Nexuiz run at horrible speeds.  Its really strange because it makes no difference what my  window manager is (either beryl or just Gnome) and when I tried it with beryl running the game didnt affect beryl's benchmarks at all.....thats why I thik that the games might not be working with it

should i try a non-xgl session?

EDIT: My specs are below...I know the card is integrated, but neither game has any really high requirements

---

### Post by thechanklybore on 2007-04-03
Yes do nonXgl - otherwise things will be working in software render mode as XGL doesn't allow DRI for OpenGL programs other than the X-Server.

nonXgl will make things peachy.

---

### Post by Hortinstein on 2007-04-03
so dont try to run gales in an xgl setting?  Ok good to know that...but I have seen people running world of warcraft and beryl at the same time...can i run beryl in a non xgl setting?

What is the real advantage of XGL

---

