---
title: "serving media files over internet"
date: 2010-01-19
forum: Multimedia Software
---

### Post by boandmichele on 2010-01-19
this might not be the correct section, but here it goes.  

i've been using ubuntu for almost 3 years, and consider myself a somewhat advanced user, but i cannot find a good solution for this.  

i want to serve files over the internet, specifically to family members.  i did this in windows many years ago, they could just [http://myipaddress](http://myipaddress) and see whatever shares were on there.  

i can install apache now, but i cannot figure out how to serve a specific folder via http.  i'd rather use nginx, so i installed it but can't figure that out either.  any ideas?  i am not so good at the networking :p

---

### Post by szemy on 2010-01-19
I just mount the folder into /var/www with the --bind option.
Than I use dyndns so that I don't have to figure out my ever changing ip address. 
Dont forget to at least rename index.html, so that apach will serve the contents of the folder.

---

### Post by boandmichele on 2010-01-19
> **szemy said:**
> I just mount the folder into /var/www with the --bind option.
Than I use dyndns so that I don't have to figure out my ever changing ip address. 
Dont forget to at least rename index.html, so that apach will serve the contents of the folder.

okay the dyndns is easy, i can handle that.  

is --bind something like a dynamic link?  i don't know how to do that, but it seems like a good solution.  

and renaming index.html... i have no idea.  i remember setting up an .htaccess in windows, but thats been a few years.  thanks for the response :)

---

### Post by szemy on 2010-01-21
Since Linux 2.4.0 it is possible to remount part of the file hierarchy somewhere else. The call is
                     mount --bind olddir newdir
              or shortoption
                     mount -B olddir newdir

according to man mount.

so if you want to share /home/video you just issue 
sudo mount --bind /home/video /var/www/

than you rename index.html in /var/www since normally apache pushes this file first. if it doesn't exist, it will list the contents of /var/www

hope this helps

---

