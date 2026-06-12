---
title: "skype mood mesage = song curently playing on rhythmbox"
date: 2008-06-19
forum: Multimedia Software
---

### Post by Kazimieras on 2008-06-19
Hello,
I have googled a lot on this, but the only thing I´ve found was "skype-plugin" here:
[http://code.google.com/p/skype-plugin/](http://code.google.com/p/skype-plugin/)
as you see, no downloads are currently available.
Has anyone managed to find any other plug-ins to do this?

---

### Post by torbi on 2008-07-08
Hi there!

I got Skype to display the current song by doing the following:

1. Open a terminal and create folder by entering in the following command:

   mkdir -p $HOME/.gnome2/rhythmbox/plugins/skype-plugin

2. Go to [http://skype-plugin.googlecode.com/svn/trunk/src/]("http://skype-plugin.googlecode.com/svn/trunk/src/") and download all the files into /.gnome2/rhythmbox/plugins/skype-plugin located in your home directory. 

To do this you can go to PLACES > HOME FOLDER, and hit CONTROL+H to see all the hidden files (usually hidden files have a "." prefix), navigate to .gnome2/rhythmbox/plugins/skype-plugin and copy/download them into there.

3. Restart Rhythmbox and turn on the plugin via EDIT > PLUGINS. Allow Rhythmbox to access Skype (Skype should prompt you) and you should see song information displayed.

Let me know if these instructions were useful to you.

Torbi

---

### Post by gubaidullin on 2008-10-02
Works like a charm!
You can place *skype-plugin* folder in  */usr/lib/rhythmbox/plugins/* also making plugin available for all rhythmbox/skype users.

---

### Post by Kazimieras on 2009-04-09
Works for me too. Thanks ;)

---

### Post by iiPing on 2009-08-10
here is another one i wrote:
[http://github.com/iiPing/Rhythmbox-Skype-Mood-Notifier/tree/master](http://github.com/iiPing/Rhythmbox-Skype-Mood-Notifier/tree/master)

and a clone from google projects

[http://code.google.com/p/rbskypemoodnotify/](http://code.google.com/p/rbskypemoodnotify/)

the version 0.01 works on hardy and the newest I did works on jaunty version 0.25

---

### Post by tas-92 on 2010-12-03
hey i can't open the link. it asks for some username and password.

? me email address -> [email]tassilosch@hotmail.com[/email]

Thanks in advance! tass

---

### Post by hellblazer on 2011-04-20
awesome that was easier than falling form a chair :D

---

### Post by made_of_spoons on 2011-06-02
I can't make a new folder in that rhythmbox 'plugins' folder. Nor can I put anything there. Why is that? It says I have no permisson.

---

### Post by /bee/ on 2011-06-02
Are you attempting to do so as root?

---

### Post by olligobber on 2011-07-18
> **torbi said:**
> Hi there!

I got Skype to display the current song by doing the following:

1. Open a terminal and create folder by entering in the following command:

   mkdir -p $HOME/.gnome2/rhythmbox/plugins/skype-plugin

2. Go to [http://skype-plugin.googlecode.com/svn/trunk/src/]("http://skype-plugin.googlecode.com/svn/trunk/src/") and download all the files into /.gnome2/rhythmbox/plugins/skype-plugin located in your home directory. 

To do this you can go to PLACES > HOME FOLDER, and hit CONTROL+H to see all the hidden files (usually hidden files have a "." prefix), navigate to .gnome2/rhythmbox/plugins/skype-plugin and copy/download them into there.

3. Restart Rhythmbox and turn on the plugin via EDIT > PLUGINS. Allow Rhythmbox to access Skype (Skype should prompt you) and you should see song information displayed.

Let me know if these instructions were useful to you.

Torbi

I can't open [http://skype-plugin.googlecode.com/svn/trunk/src/]("http://skype-plugin.googlecode.com/svn/trunk/src/"), it asks for a username and password...

---

### Post by Tornikee on 2011-11-01
Any plugins that work w/ Banshee?

---

