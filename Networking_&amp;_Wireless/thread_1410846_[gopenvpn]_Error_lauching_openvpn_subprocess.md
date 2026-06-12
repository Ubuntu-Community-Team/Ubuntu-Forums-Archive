---
title: "[gopenvpn] Error lauching openvpn subprocess"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by solarize on 2010-02-19
I would like to use openvpn through the gopenvpn app. So I followed the instructions given in:

[http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/](http://tranceparance.wordpress.com/2009/02/28/gopenvpn-installation-instructions-for-ubuntu-linux-810/)

Everything went fine and the app seems to be running fine. But when I want to connect by loading a vpn config file I get the an error window with the following text:

error launching openvpn subprocess


When I use openvpn from the command line with the same vpn config file everything works fine. Anybody any suggestions what causes this error? I'm using ubuntu 9.10.

Many thanks.

---

### Post by alonc on 2010-02-21
had the same problem.
solved it by using this guide:
[http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

you can skip Part 2 section 2-7 the SVN version contains the code changes

part 3  section 3 is the key to fix this problem don't skip this!

using this guide every thing is almost working  perfect …

the only problem that I have is that when I checked the Remember Password option the gopenvpn crashes...

as workaround I changed the openvpn config file (.ovpn).
I changed the line
auth-user-pass
to
auth-user-pass pass.txt
and created a text file pass.txt that contains two lines the first is the user name and the second is the password.

Not the best solution security wise but it's working without asking me the user and password every time

Alon

---

### Post by solarize on 2010-02-21
many thanks.

---

