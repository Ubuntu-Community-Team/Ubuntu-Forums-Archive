---
title: "Can't Start fuppes, sqlite database plugin error :("
date: 2009-08-22
forum: Multimedia Software
---

### Post by beterhans on 2009-08-22
HI I've compiled the fuppes by myself with no error
verion 0.640
and made it into a deb pkg with checkinstall

I installed it by dpkg -i

when i tried to run it
got the following error


==================================================
:confused::confused:

[email]hans@Galaxy:~/.fuppes[/email]$ fuppes
            FUPPES - 0.640
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

failed to initialize sqlite database plugin?

so do I need to install other sqlite database?

---

### Post by gneville on 2009-10-18
Hi,

I get the same problem.

Any solutions?

Cheers

---

### Post by gneville on 2009-10-22
I managed to get this to work.

For some reason I have to specify where the plugins are:

/usr/bin/fuppes --plugin-dir /usr/lib/fuppes/

---

### Post by emoguitarist06 on 2010-01-25
> **gneville said:**
> I managed to get this to work.

For some reason I have to specify where the plugins are:

/usr/bin/fuppes --plugin-dir /usr/lib/fuppes/

I don't have that directory in my /usr/lib/

---

### Post by Shhnap on 2010-01-26
Um, for now can I recommend not using checkinstall to install the fuppes package. Please use 'sudo make install' instead and leave it at that. It means that you will not have to use '--plugin-dir'. And it does not matter in the end because a fuppes package will be coming soon enough. If you want to see what I mean just click here: [http://massaioli.homelinux.com/wordpress/2010/01/19/working-on-a-debianized-fuppes/](http://massaioli.homelinux.com/wordpress/2010/01/19/working-on-a-debianized-fuppes/)

There are some more posts about fuppes on that blog too if you want to check out a little bit of current development.

---

### Post by adenewton on 2010-02-26
> **gneville said:**
> I managed to get this to work.

For some reason I have to specify where the plugins are:

/usr/bin/fuppes --plugin-dir /usr/lib/fuppes/

I'm having the same problem.

I installed fuppes via the getdeb site sas i had major problems compiling it. Now I get this problem,

I ran it as 
/usr/bin/fuppes --plugin-dir /usr/lib/fuppes/

which did launch it, however if i then go to the web browser to view the setup it says page cannot be displayed and when i look in the terminal the app has closed.

any ideas? here is the output from my terminal:

ade@ade-ubuntu:~$ /usr/bin/fuppes
            FUPPES - 0.662
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

failed to initialize sqlite database plugin.
ade@ade-ubuntu:~$ /usr/bin/fuppes --plugin-dir /usr/lib/fuppes/
            FUPPES - 0.662
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

error load symbol 'fuppes_encoder_set_audio_settings'
webinterface: [http://192.168.1.67:5001](http://192.168.1.67:5001)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

Segmentation fault

---

