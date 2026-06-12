---
title: "need to be root to set dvd booktype???"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by toastydave1 on 2007-11-28
Hi there have been many posts on this, I thought I would try a different approach.

I have a dvd writer on which I would like to change the booktype when burning +r dvds to dvdrom

I can do this from the comand line with dvd+rw tools, but I need to use the sudo command to get the program to see my drives.

i need to type in the terminal

sudo dvd+rw-booktype -dvd-rom -unit+r /dev/hdc

I would like to set the booktype from within K3B

in the program, you can set command line arguments, so it looks like this may be possible.

However from within the program you cannot run a dvd+rw tools as root and so I can only enter for a command line argument

dvd+rw-booktype -dvd-rom -unit+r /dev/hdc

and as I said without the sudo it does not work...

any ideas on how I can the program dvd+rw-booktype to run as root without requiring the password every time it runs?

Thanks

---

### Post by bobpaul on 2008-05-14
I know I'm a few months late, but...

You could: 
a) setuid root for dvd+rw-booktype (causes any invocation by any user to execute dvd+rw-booktype with root priviledges)
b) use visudo and modify your sudoers file to allow password less execution of dvd+rw-booktype. With this route, you could even specify the entire command line you wish to allow. Once you have that working, simply add sudo to your commandline in k3b

---

