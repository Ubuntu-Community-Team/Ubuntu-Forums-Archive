---
title: "Lollypop Crashes in Plasma"
date: 2020-02-05
forum: Multimedia Software
---

### Post by jbh54enwiler on 2020-02-05
I recently attempted to install the Lollypop music player on my Kubuntu 19.10 laptop and discovered that it crashes on boot when I launch it through the GUI or through the terminal.  I also attempted to install the flatpak version and the installation failed, with Discover returning the error "Aborted due to failure."  I am runnng Plasma 5.17.5.

When I tried to load the Discover version of Lollypop through the terminal, it returned this response for the standard and debug modes of the application:

[FONT=monospace]```
[COLOR=#54FF54]&#8203;**jbh@jbh-HP-EliteBook-2560p**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lollypop[/COLOR]
[INFO] 2020-02-05 17:56:06 LastFM::__init__(): [Errno 2] No such file or directory: '/ho
me/jbh/.local/share/lollypop/lastfm_queue.bin'
[INFO] 2020-02-05 17:56:06 LastFM::__init__(): [Errno 2] No such file or directory: '/ho
me/jbh/.local/share/lollypop/librefm_queue.bin'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/lollypop/helper_art.py", line 146, in _on_get_art
work_pixbuf
    pixbuf, scale_factor, None)
TypeError: Couldn't find foreign struct converter for 'cairo.Surface'
[COLOR=#54FF54]**jbh@jbh-HP-EliteBook-2560p**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lollypop -d[/COLOR]
[INFO] 2020-02-05 17:57:08 LastFM::__init__(): [Errno 2] No such file or directory: '/ho
me/jbh/.local/share/lollypop/lastfm_queue.bin'
[DEBUG] 2020-02-05 17:57:08 GOA not available
[DEBUG] 2020-02-05 17:57:08 LastFMNetwork.__init__(secret)
[DEBUG] 2020-02-05 17:57:08 PasswordsHelper::get(): Waiting Secret service
[INFO] 2020-02-05 17:57:08 LastFM::__init__(): [Errno 2] No such file or directory: '/ho
me/jbh/.local/share/lollypop/librefm_queue.bin'
[DEBUG] 2020-02-05 17:57:08 LibreFMNetwork.__init__()
[DEBUG] 2020-02-05 17:57:08 PasswordsHelper::get(): Waiting Secret service
[DEBUG] 2020-02-05 17:57:08 Container::__on_list_one_activated()
[DEBUG] 2020-02-05 17:57:08 LazyLoadingView::lazy_loading(): 0.06888890266418457
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/lollypop/helper_art.py", line 146, in _on_get_art
work_pixbuf
    pixbuf, scale_factor, None)
TypeError: Couldn't find foreign struct converter for 'cairo.Surface'

```
[FONT=arial]And yes, I understand that Lollypop was written for GNOME systems.  This is the first GNOME app I've had crash on me in KDE.[/FONT][/FONT]

---

### Post by jhmb666 on 2020-05-05
sudo apt-get install python3-gi-cairo 

Works for me!!!!

Source: [https://github.com/rbgirshick/py-faster-rcnn/issues/221](https://github.com/rbgirshick/py-faster-rcnn/issues/221)

---

