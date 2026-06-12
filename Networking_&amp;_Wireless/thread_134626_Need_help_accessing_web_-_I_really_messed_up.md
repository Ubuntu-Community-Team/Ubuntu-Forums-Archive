---
title: "Need help accessing web - I really messed up"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by harnadem on 2006-02-22
Someone please help me!  I have been trying to properly configure dansguardian and tinyproxy on my breezy machine to allow a networked Win98 machine to access the internet.  Somewhere I made a mistake and have lost web browser access to the internet (I can still access my email, and can ping all networked computers back and forth).

What I did was follow the procedures outlined in [http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html").  I still couldn't access the internet, and looked for help.  I came across this posting by supermike: [http://www.nuxified.org/forums/viewtopic.php?t=132]("http://www.nuxified.org/forums/viewtopic.php?t=132").  I followed the steps in his post.  This is where I believe I got into trouble.  I decided to remove tinyproxy (which I did :cry: ) and install squid (which I couldn't :-? )!  Basically, I can no longer access the internet to run or update apt-get or to surf the web.  I can, however, download my email.

I have no idea how to fix this, and really, really need help!  Thanks!

---

### Post by spd106 on 2006-02-22
Have you checked the internet proxy settings?
System -> Preferences -> Network Proxy
and 
the connection settings in firefox
Edit -> Preferences -> Connection settings

---

### Post by harnadem on 2006-02-24
SPD106 - thanks for the help.  I checked my browser settings, and changed it from a proxy listening to 8080 to a direct internet access (which I have).  I then tried to check the internet proxy settings (System -> Preferences -> Network Proxy) and saw that it was also set to listen to port 8080.  I tried to change this, but kept getting the following error:
[I][COLOR="Blue"]
"Gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change.  Some of the settings you have selected may not take effect, or may not be restored next time you use the application"[/COLOR][/I]     

Clicking on the Details button, the following was displayed:

*[COLOR="Blue"]"detail: Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for '/system/http-proxy/use_http_proxy' set in a read-only source at the front of your configuration path"[/COLOR]*

I am basically lost in trying to figure out how to go about fixing this to allow web access.  If I boot into the system using the 'Recovery Mode' then I can StartX and have web access.  However, as a normal user, booting into the standard kernel, I cannot.

---

### Post by harnadem on 2006-02-24
I am really hoping that someone can help me.  I am basically dead in the water unless I can regain my web access; and, I am desperately trying to avoid having to re-install and lose my saved information.

---

### Post by harnadem on 2006-02-25
Without any suggestions on how to proceed - I went ahead and reinstalled breezy.  Now I can access the internet - and just have to see if I can remember all the rest of my previous settings.

---

