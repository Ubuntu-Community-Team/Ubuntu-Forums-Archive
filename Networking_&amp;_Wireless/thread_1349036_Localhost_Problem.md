---
title: "Localhost Problem"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Norami on 2009-12-07
I'm having an issue with my laptop. Every time I try to use Firefox, it gives me this error.

[IMG]http://i23.photobucket.com/albums/b397/Norami/Screenshot.png[/IMG]

My computer will ping any site or server, and Empathy and Skype connect with no problem. Does anyone know what's going on here? It was fine last night. The only thing that has changed is my RAM. I upgraded it, but I doubt that has anything to do with this.

Also, this is what ifconfig tells me about the eth0 connection:

[IMG]http://i23.photobucket.com/albums/b397/Norami/terminal2.png[/IMG]

---

### Post by mchecca on 2009-12-07
It seems as if you are using a squid proxy that is not configured properly. Go to Edit>Preferences>Advanced>Network and click settings under connection. If you are using a proxy make sure it is properly configured. Its not, make sure you select "no proxy"

---

### Post by Norami on 2009-12-07
I've tried No Proxy, Auto-detect proxy, and Use system proxy. None of them get me anywhere, though. Still the same error.

---

### Post by mchecca on 2009-12-07
Do you have squid installed? If you do, try removing it and deleting the config files

---

### Post by Norami on 2009-12-07
I don't have squid installed.

---

### Post by mchecca on 2009-12-07
Then I guess you can try reinstalling firefox and see where that gets you. Deleting your "/.mozilla" folder might work also, but you'll have to backup your bookmarks and reinstall any extensions.

---

### Post by Norami on 2009-12-08
re-installed Firefox, and that seemed to work. Thanks for the help!

---

