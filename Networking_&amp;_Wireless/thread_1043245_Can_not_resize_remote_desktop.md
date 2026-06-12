---
title: "Can not resize remote desktop"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by alextz on 2009-01-18
Greetings to the amazing ubuntu community. I'm very new to Ubuntu (installed it only yesterday) and would like some help with an issue I'm facing. I just made a shortcut on my panel for opening rdesktop (it connects to a Win2k pc that I use at work) but for some reason I can not resize the window. It appears on a 800x600 (or similar low res) window and does not even have the little button with the square for me to make it full screen. What can I do to make it bigger?

---

### Post by sarath_it on 2009-01-18
There are some options in display tab that you can change to get resolution you desire. Before connecting!

---

### Post by alextz on 2009-01-18
thanks for the quick reply! Unfortunately, I'm not sure which display tab you're referring to. The way I run it is via a shortcut which has the command 'rdesktop server.name.goeshere'. The only solution that I found was adding the line -f after the command in order to make it full screen. However, I'm not sure how to go back to non-full screen mode if I do it that way.

---

### Post by sarath_it on 2009-01-18
I dont know about shortcut thingy.. sorry, but if you goto menu>internet>terminal services client, Thats how I connect to rdp windows, you get a place to enter info and then customize the connection. the first tab take info about the other terminal, the display tab lets you configure   the resolution.

If you have a shortcut, you better paste it here. (remove personal info)

---

### Post by meUser on 2009-06-29
> **alextz said:**
> thanks for the quick reply! Unfortunately, I'm not sure which display tab you're referring to. The way I run it is via a shortcut which has the command 'rdesktop server.name.goeshere'. The only solution that I found was adding the line -f after the command in order to make it full screen. However, I'm not sure how to go back to non-full screen mode if I do it that way.

Hey, so the "-g" option may be what you're looking for, it may be used to define the geometry of the window WRT a percentage of your current window i.e.  "-g 90%".

---

### Post by computer13137 on 2009-06-29
In Terminal Services client on Ubuntu, you get out of full screen by pressing Control+Alt+Enter.

-Kirk

---

### Post by alextz on 2009-06-29
I'd like to thank everyone for their replies. meUser's suggestion did the trick for me. The command is now "rdesktop ****.******.** -f -g 70%" and it works perfectly. 

Problem solved.

---

### Post by rainofkayos on 2009-07-30
this may help you

-g 'geometry'
-f 'full'

i usually use a line like so: 

'rdesktop -g 1024x860 -u <username> -p '<password>' host.domain
 
or as mentioned previously you can use a percentage of your desktop with the -g switch

rdesktop -f 1024x768

This will work in statically setting the resolution how you want, Im not aware of any switch that makes the desktop resizable, as well AFAIK you exit full screen mode by leaving that rdp session (logging of rdp|shutting down host from rdp). These parameters are set in the call to rdp so rdp knows how to draw the window. 

Best
Rain

---

### Post by psarkar on 2013-04-26
try   [FONT=arial] [/FONT][FONT=arial]rdesktop -f IP_address:port
[/FONT][FONT=arial]
or 

 rdesktop -g1200x700 IP 

from your terminal 

BR
PSARKAR[/FONT]

---

### Post by wildmanne39 on 2013-04-26
Thread closed. Please do not post in old threads.

---

