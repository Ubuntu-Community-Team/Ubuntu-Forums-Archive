---
title: "Apache as proxy for BBC iplayer"
date: 2011-04-17
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-04-17
hey folkes;

so I spend a fair bit of time out of the uk and am really frustrated when i cannot get access to the bbc iplayer website abroad.  I would like to use my myth box to get access to the iplayer when im out of the UK and figured this should be achievable if i run my myth as a proxy.  

I dont want to break mythweb as i use it lots and could not live without it but do really want iplayer access.

Can someone help?

Thanks

---

### Post by Joe of loath on 2011-04-17
It would probably be easier to find a UK web proxy to watch through. Check out some free proxy lists online, see what you can find.

---

### Post by geekyhawkes on 2011-04-22
Thanks, but to be honest i would really like to use my own server as a proxy.  Keeps my options open then for any other uk sights i cannot access when out of the country.  Is there a guide anywhere, or someone that could help pleasE?  I have looked on the apache site but kind of goes straight in on level 11!

Thanks

---

### Post by Joe of loath on 2011-04-22
Best thing to do would be SSH tunnelling. Start an SSH server on your machine and port forward it properly (making sure your passwords are good, or you use key based authentication).

Then, when you're away you can simply run ssh -D 8080 user@hostname:port and set your browser's proxy to localhost:8080, and it should work fine :D

---

