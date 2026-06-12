---
title: "Wireless Password"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by jbsmith on 2009-10-31
Ok I am new to linux but not wireless.  I have searched all over the forums and google to determine why I have to enter my WiFi password each time I reboot to no avail.  I am running 9.10 and my WiFi password is not the same as my user password.

Is this by design and/or is there a way to have it automatically log into the WiFi network?

I have found many posts from back in 2007, '08 etc but none that talk about 9.10.


Thanks in advance

---

### Post by Turtle.net on 2009-10-31
Right click on nm-applet (top right of your screen, the thingy that gives you the state of your conection) then Edit Connections
Go to Wireless, Select your connection name, Edit...
Select the tab "Wireless Security"
Then make sure that your password is entered, that the "connect automatically" option is selected.
For more convenience (in case you create new users on your PC) select the option "Available to all users"
Should do the trick :)

---

### Post by jbsmith on 2009-10-31
Thanks, Just tired that (both the connect automatically and enable for other users was checked).  Did a restart and as soon as it boots up I get the message that 'Network Manager' trying to access keyring but its locked.'  Once I enter the password I am good to go.

Is there something I am doing wrong - do both my passwords need to be the same (I don't enter a password to boot up) it auto logs me in.

---

### Post by Turtle.net on 2009-10-31
Ok now I get it.
You should read this [thread]("http://ubuntuforums.org/showthread.php?t=1138099").

---

