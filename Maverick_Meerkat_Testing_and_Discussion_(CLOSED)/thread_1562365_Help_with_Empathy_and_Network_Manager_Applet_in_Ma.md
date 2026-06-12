---
title: "Help with Empathy and Network Manager Applet in Maverick Meerkat"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by drkages on 2010-08-27
Every time I try to connect to a wireless network the network manager applet crashes but no feedback is given.

I started the network manager from the terminal and it gives a segmentation fault error (core dumped).

Similarly when i try to add a new account to empathy it crashes without feedback, when using the terminal "empathy-account"

I get 
"Floating point exception (core dumped)"


Any ideas whether a bug report has been filed or how I could find out more about the error and possible helps

thanks

---

### Post by drkages on 2010-08-27
update:

when i run the applet in root using:

"sudo nm-applet" it works.

However i saw a new message

> 
(nm-applet:1507): WARNING **: _nm_object_get_property: Error getting 'Strength' for /org/freedesktop/NetworkManager/AccessPoint/2: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


any suggestions

thanks

---

### Post by cariboo on 2010-08-27
Have you tried removing network-manager-gnome and all the associated programs, then reinstalling?

---

### Post by drkages on 2010-08-28
No I haven't tried that as yet, because I was not certain if the problem was with that particular application.

The trend seems to be common with a lot of other applications. When used as a normal user they crash without warning usually due to a segmentation error of some kind. However when I run in sudo on the terminal it works.

I have noticed it in the following applications so far:
1. Empathy
2. QTCreator
3. Firefox 4
4. network manager applet
5. rhythmbox

(practically all applications seem unusually unstable, I usually use the development build but never had so much wide spread problems before)

Could you direct me to where I could get the core dumps to see if I could find any similarities apart from the errors

thanks

---

### Post by cariboo on 2010-08-28
It sounds like  you may have a  borked install. you can check in ~/.xsession-errors to see if there is anything relevant.

---

