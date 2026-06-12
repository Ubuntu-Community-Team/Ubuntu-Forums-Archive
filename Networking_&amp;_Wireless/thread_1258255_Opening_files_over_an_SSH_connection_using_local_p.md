---
title: "Opening files over an SSH connection using local programs"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Shekibobo on 2009-09-04
I just started using a ssh connection to access my account on my school's Linux servers.  It works great, and I'm learning a bunch, but I'm wondering a few things.

Is it possible to open a file over the ssh connection using programs native to my local machine?  For instance, I want to open the file index.php on the server in gedit on my computer, but would preferably do this without having to use VNCViewer (which works fine, but is incredibly slow).  Every time I try to open a file using gedit over ssh, I get the error:
```
(gedit:23996): Gtk-WARNING **: cannot open display: 

```

which I assume means the terminal is trying to open gedit on the remote server, and can't do it because we're only connecting through the terminal.

Is it possible to open this file using my own computer to edit the file remotely?

Or am I just missing the point of ssh entirely?

---

### Post by falconindy on 2009-09-04
SSH isn't really meant to behave that way. You do, however, have a few options (ranked in order of my personal preference):

1) Use a command line editor, such as VI, Emacs or nano/pico
2) Copy the file off the host using SCP and then send it back
3) If your only intent is to edit files on a remote box, employ FTP instead

---

### Post by OmarAvelar on 2009-09-04
If the server supports** X11 forwarding**, you could run the ssh command with the **-X** switch and have the program display the window on your working machine (but it would be in fact be using the server's programs).

Try it, if X11 redirection is enabled and you run gedit as you mentioned earlier, it would show up in your display without that warning. :D

---

### Post by bear24rw on 2009-09-04
```
$ ssh -X user@server gedit file.txt
```

---

### Post by darincb77 on 2010-05-27
To open using gedit installed on the machine you are sshing on, use

```
ssh -X name@something.something
```

As said before, the -X allows X windows to pop up, so if the computer you ssh onto has gedit installed, you can use gedit.

However, my personal favorite method of using your local programs is a combination of sftp (to mount a directory you would normally ssh into) and nautilus-open-terminal, a small installation that will let you right-click an open a local or remote terminal from any directory in nautilus):

1) Install nautilus-open-terminal from synaptic
2) In nautilus, add an sftp to where you want to go, like 
```
sftp://NAME@something.something/favorite/directory/location
```
3) Drag your sftp folder to the "places" menu on the left hand side of Nautilus for convenient reuse
4) When you want to "ssh" (really an sftp now) using your local programs, open nautilus and double-click on your desired sftp destination. Now in whatever directory you want through nautilus, you can right click and in the menu that pops up, click on "Open in Local Terminal"

Now you have a mounted sftp file system that you can navigate like it is your own, using your local programs. Alternatively, you can just navigate this through nautilus. 

-d

---

