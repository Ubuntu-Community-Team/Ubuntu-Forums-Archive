---
title: "picasa not working"
date: 2009-07-23
forum: Multimedia Software
---

### Post by Sakthi srinivas on 2009-07-23
i have installed picasa 3 for linux in my Ubuntu 8.04.
But when i tried to download an album from mail , it shows an error as "Firefox doesn't know how to open this address, because the protocol (picasa) isn't associated with any program.
i need help on this.. can any one help me pls

---

### Post by igorzwx on 2009-07-23
there should be something like "save the link target as", perhaps

---

### Post by oguillaume on 2011-07-25
I solved the following problem:
[INDENT]because the protocol (picasa) isn't associated with any program[/INDENT]
by changing the path to Picasa in Firefox.

In your Firefox address bar, type
```
about:config
```

In the Filter: field, type
```
network.protocol-handler.app.picasa
```

The value for this property is probably 
```
/usr/bin/picasa
```
which did not work for me although /usr/bin/picasa link exists:

Proof:
```
ls -l `which picasa`
lrwxrwxrwx 1 root root 33 2011-07-25 10:16 /usr/bin/picasa -> /opt/google/picasa/3.0/bin/picasa
```

Right-click on the value for the property entry and change it to
```
/opt/google/picasa/3.0/bin/picasa
```

Then when you click Download Album on a Picasa Web Album on a webpage, it will start Picasa and show a small dialog where you can confirm to start downloading all the pictures.

---

