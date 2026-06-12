---
title: "Help setting up D-Link DWL-520 E1 adapter"
date: 2006-02-20
forum: Networking &amp; Wireless
---

### Post by armeck on 2006-02-20
[https://wiki.ubuntu.com/WifiDocs/Device/DWL-520vE1](https://wiki.ubuntu.com/WifiDocs/Device/DWL-520vE1)

So I have this network adapter and would love to follow the instructions, but how can I do this without being able to connect to the internet?  I am unsure where to go to download the files directly.

Any help would be greatly appreciated!

---

### Post by armeck on 2006-02-21
Maybe my problem wasn't clear?  I just need to know how to obtain the files listed in the How To without being able to apt-get (since I can't get on the internet).

Can anyone help me here?

---

### Post by Lambert on 2006-02-21
Go to this site and search for the packages you need.

[http://packages.ubuntu.com/breezy/]("http://packages.ubuntu.com/breezy/")

Download, and then through what ever method you chose, copy them to your hard drive. 

Then move to the folder you saved the files and you can install with dpkg.

Quick example.

If you copied package xyz.deb to your Desktop you would first move to the Desktop folder

```
cd /home/name/Desktop
``` 
Then to install you run this command.

```
sudo dpkg -i xyz.deb
```

If I need to clarify or expand this, just say so :)

---

### Post by armeck on 2006-02-21
Thanks, I'll give it a whirl!

---

