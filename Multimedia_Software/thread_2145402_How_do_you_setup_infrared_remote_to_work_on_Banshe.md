---
title: "How do you setup infrared remote to work on Banshee?"
date: 2013-05-15
forum: Multimedia Software
---

### Post by JJ Avila on 2013-05-15
How do you get an Infrared Remote to work on Banshee?


I have already installed lirc. (sudo-apt-get install lirc). It is working perfectly with XBMC Frodo 12.


In Banshee, I have went under Edit > Preferences > Extensions and put a check mark in Infrared Remote Control.


I am using Ubuntu 12.04 (64 bit) with GNOME Shell 3.4 and using Banshee 2.6.1.


I am still unable to use my infrared remote on Banshee.


Any help is greatly appreciated.

---

### Post by JJ Avila on 2013-05-16
Ok, I found a solution.

gksudo gedit ~/.lircrc

and paste the following:
begin
        prog=banshee
        remote=mceusb
        button=KEY_PLAY
        config=play
end
 
begin
        prog=banshee
        remote=mceusb
        button=KEY_PAUSE
        config=pause
end
 
begin
        prog=banshee
        remote=mceusb
        button=KEY_STOP
        config=stop
end
 
begin
        prog=banshee
        remote=mceusb
        button=KEY_AGAIN
        config=previous
end
 
begin
        prog=banshee
        remote=mceusb
        button=KEY_NEXT
        config=next
end

Also, the following links were useful:
[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)
[https://github.com/willprice/dotfiles/blob/master/lirc/banshee](https://github.com/willprice/dotfiles/blob/master/lirc/banshee)

Hope this information is useful to other users.

---

