---
title: "remote login before welcome screen loads programs"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by w0296094 on 2010-02-17
Hello,

I have 2 computers with kubuntu 8.10 using vinagre for my remote desktop viewer and x11nc for my server and I am trying to connect remotely through the command line from one computer to login to the startup screen in the other computer. 
Is this possible, since it looks like my server does not start until after I log in to my desktop screen?

---

### Post by w0296094 on 2010-02-25
anyone have any ideas to do this?

---

### Post by Vishal Agarwal on 2010-02-25
Did not very clear abt the problem ?

---

### Post by w0296094 on 2010-02-26
ok let me clarify. usually, every time one goes to the gui for ubuntu, one has to log in before going to the gui(this is the same place were you change wether you want kde or kde4, it usually has a baby blue background).
once you have logged in all programs(including the x11vnc server ) load and you are able to use remote login with no problems.
However, before you have logged in, once you go past the black screen and the progress screen from ubuntu and you go to the log in screen before accessing the GUI(the log in screen were you choose if you want kde or kde4, and usually has a baby blue background)
         at this point, if i want to access this computer from another computer, i get an error message that says that port 5900 was not opened, or something along those lines.

In other words, i cannot access this computer remotely from another computer by conventional means(like when i usually do when i access the ubuntu gui after logging in).
How do i go about logging in to this computer remotely.

---

### Post by krunge on 2010-02-26
See the section named 'Continously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

If you have any trouble implementing that, feel free to ask here.

---

### Post by w0296094 on 2010-03-19
thx for the info. I found my Xsetup file, which is  a shell script. At this point, I am stuck and havent found a way to open it. This type of file is a little new to me

---

### Post by krunge on 2010-03-19
I see an /etc/kde4/kdm/Xsetup script on a debian machine of mine. Perhaps yours is located there too. It is very short and looks like this:
```

#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &

```
I suggest opening it with an ascii text editor as root (perhaps 'sudo gedit <filename>', or nano instead of gedit, etc. I assume you can run a text editor as root and edit files.) Then add a line like this at the bottom of it:
```

/usr/bin/x11vnc -o /var/log/x11vnc.log -forever -bg

```(this assumes you have installed the 'x11vnc' package.)

Then save the text file and restart kdm (or reboot.)  x11vnc should be running attached to the kdm login screen and allow VNC access.  x11vnc logging output is directed to /var/log/x11vnc.log; look at that file when troubleshooting connections.

If your Xsetup is different from the one I show above, be sure to put the x11vnc line before any 'exit' line.

If you want a password to be required for VNC connections, and it is not clear from the FAQ page I gave as a link, feel free to ask.

---

### Post by jrssystemsnet on 2010-03-20
> **krunge said:**
> See the section named 'Continously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

If you have any trouble implementing that, feel free to ask here.Woah!  You learn something every day.  Thanks Krunge, I had no idea this was even out there. :popcorn:

---

### Post by w0296094 on 2010-03-23
thanks krunge I was able to login completely after opening the file, and following the isntructions. Somehow, i couldnt open the file before, but then i could open it again.

---

