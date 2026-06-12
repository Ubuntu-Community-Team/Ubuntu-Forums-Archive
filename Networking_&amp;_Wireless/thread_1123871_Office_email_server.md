---
title: "Office email server"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by dndrich on 2009-04-12
Ubuntupals:

Curious as to how I can do this:

Presently in my office I have a Windows computer running a program called Merak Mail.  This is a really extensive email server program that has pop, imap, and built in web mail.  I use it on the office lan to have intraoffice email only.  Some folks log in from their computers using a web interface, while others can log in using a pop client like outlook or thunderbird.  Now, I managed to configure the thing by some miracle since I don't understand the complex nature of email servers, but it works just perfectly.  The mail appears to be kept on my computer in folders by user, and I have about 30 users throughout the office.  The gui administration is really nice.  It lets me set up policies for the users, such as the amount of disk space they get.  I am interested in trying to set something up that is similar using ubuntu.  I gotta believe that can be done with programs like courier and squirrel mail, but I could really use some kind of how to in order to set it up.  I want to be able to add users using a gui, and have a nice webmail interface as well as pop capability.  The thing doesn't need ssl or any other significant security, as it is strictly within the office lan.  Any ideas, O brilliant ubuntupals?

---

### Post by hyper_ch on 2009-04-12
a common combo for a mailserver setup is to use

postfix & courier-imap/courier-pop3.

I usually follow Falko's perfect howto setup over at [http://www.howtoforge.com](http://www.howtoforge.com) for setting up the mailserver.

There is a wui admin tool for postfix but manual handling is very simple also (at least with postfix/courier). You really might want to consider trying this first by hand then then use a wui admin tool.

As for webmail I use on one server squirelmail also. It's not as "pretty" as other webmails but it just works. On one server I did setup Horde so that also group calendar, todo list etc. can be run on that server (I don't want to use Google Tools for that as there is als confidential data). However setting up Horde takes a little while.

You might also want to look at Citadel - it should have webmail and also groupware stuff.

There's another one that is also often recommended... it will just install everything on its own. I didn't like it because it takes away control from me and from what I'm doing. I forgot the name right now.

---

### Post by kevdog on 2009-04-13
Wow I used to use Merak mail along time ago.  Thanks for a trip down memory lane.  

Ive heard the Citadel is very nice, but I haven't tried it.

---

### Post by nandemonai on 2009-04-13
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Also a good document on setting up all sorts of servers, including email.

---

### Post by dipeshmehta on 2009-04-13
> **hyper_ch said:**
> 
I usually follow Falko's perfect howto setup over at [http://www.howtoforge.com](http://www.howtoforge.com) for setting up the mailserver.

I also agree with hyper_ch.  Falko's guide is pretty good. It covers everything you want as well as it is given step-by-step.

---

