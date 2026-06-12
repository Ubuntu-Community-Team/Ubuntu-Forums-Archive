---
title: "no audio"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Almonte on 2008-04-10
A friend dual booted my acer laptop with Windows Vista and Ubuntu 7.10. When I play a music CD under Vista it works fine, but under ubuntu I get no audio. Please advice.

---

### Post by Metaljaz on 2008-04-11
In the terminal window type:
sudo lshw -C sound

This should tell you what audio card has been detected. Post the results.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by deadgobby on 2008-04-11
Please open up the terminal and type this command in and post the reply
aplay --list-devices 

Gobby

---

