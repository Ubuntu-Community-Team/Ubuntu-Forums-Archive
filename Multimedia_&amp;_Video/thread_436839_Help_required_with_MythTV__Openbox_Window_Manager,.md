---
title: "Help required with MythTV / Openbox Window Manager, Mythfilldatabase"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by woodbeez13 on 2007-05-08
Hi, I'm three-quarters through an analog MythTV Combined Frontend/Backend install using dial-up and apt-get offline.  It's all going well so far but I need some advice regarding the MythTV user and the Openbox WM.

I've got MythTV backend and frontend installed OK but I'm not sure that Xmltv is setup properly (couldn't find much Noob level guidance on Xmltv 8-[ )  I need to open a terminal, run PON to connect my dial-up and run Mythfilldatabase to see what the output is.

I can do this from my normal Ubuntu user in Openbox but presumeably it needs to be done as the MythTV user and I don't know how to do this as the MythTV auto logs in and I can't see how to get back to the Openbox desktop when logged in as MythTV.

I've been using the Ubuntu Community Docs for this project on 7.04 Feisty.

Thanks in advance.

---

### Post by jimp180 on 2007-05-08
you should be able to just hit the escape key until you see the message "ARE YOU SURE YOU WANT TO QUIT MYTHTV" or something close to that, and arrow down to "yes" then you be logged out and at this point you have to be quick because you only have a few seconds to enter your user name before it logs mythtv user back in. once you log in with regular user you can right click on desktop and select "Terminal" if you run a mythtv command like mythfilldatabase it will tell you that you need to be a mythtv user to do this and ask if you would like to be one then you just click 'yes and after a couple screens you are able to log back in but now your user is in the mythtv group so the changes you make will work in mythtv.
hope this helps, it worked like this for me anyway.

---

### Post by woodbeez13 on 2007-05-08
Many thanks for this Jimp.  I followed your advice and began to learn about mythfilldatabase and xmltv (an arcane subject and soon to be the subject of another post).

Thanks again.    :)

---

