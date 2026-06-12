---
title: "Help me install VLC in Ubuntu 10.10"
date: 2010-12-02
forum: Multimedia Software
---

### Post by drtiendiep on 2010-12-02
I'am Vietnamese. I want to install VLC in Ubuntu. Help me! Thanks

---

### Post by wilee-nilee on 2010-12-02
In a ubuntu terminal.
```
sudo apt-get install vlc
```

Might need the universe repo opened.

---

### Post by drtiendiep on 2010-12-02
Can you show detail? I don't install it.

---

### Post by wilee-nilee on 2010-12-03
So here is the actual VLC page that probably gives a better description than I can but I have your thread subscribed so I will try to get you setup.
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

You have a apt source list to open and be very careful here as your edits will be saved, and save the edits to open it in the terminal run.

```
sudo gedit /etc/apt/sources.list
```
you will see this list and remove the # as I have then hit save, and close the list. Just adjust it exactly as mine is don't remove the double ##
[ATTACH]177246[/ATTACH] 

Then run in the terminal
```
sudo apt-get update
```

then

```
sudo apt-get install vlc
```

---

### Post by drtiendiep on 2010-12-03
> **wilee-nilee said:**
> So here is the actual VLC page that probably gives a better description than I can but I have your thread subscribed so I will try to get you setup.
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

You have a apt source list to open and be very careful here as your edits will be saved, and save the edits to open it in the terminal run.

```
sudo gedit /etc/apt/sources.list
```
you will see this list and remove the # as I have then hit save, and close the list. Just adjust it exactly as mine is don't remove the double ##
[ATTACH]177246[/ATTACH] 

Then run in the terminal
```
sudo apt-get update
```

then

```
sudo apt-get install vlc
```
Thanks! I was installed it.

---

### Post by wilee-nilee on 2010-12-03
Excellent, sorry for the delays getting back to you some traumatic events have happened in my life in the last 24 hrs or so.

---

