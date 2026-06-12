---
title: "Jack and VLC/firefox"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by 00l0 on 2007-06-29
hello,
i finally managed to make my firewire audio interface working together with freebob and jack, tunning this command:
$jackd -d freebob

the first question is, how could i make it run everytime i start my computer? i want my interface to be my only audio device used...

my second question is about VLC, id like vlc to send audio signal out to jackd so i can hear my movie's sound through my interface, also with flash player(mozilla plugin) but i cant find the right place to set it up.

thank you :]

---

### Post by 00l0 on 2007-06-30
anyone?any ideas?  [:

---

### Post by linkx on 2007-07-01
I am in the same situation. I know it's possible to have JACK start at system start. I know that VLC can be set to use JACK by default. I would also like to know the best way to do these things. 

I'm not sure that Flash Player will output to JACK. This is devastating to my setup because I have to boot into a different operating system just to hear Flash audio through the speakers.

Let's get firewire audio devices better integrated into the Ubuntu desktop! HELP!

---

### Post by 00l0 on 2007-07-03
yeh Please! anyone? Firewire is one tough aspect as for compatibility in GNU/linux, at least for newbies....
c'mon all those experts out there   : D

---

### Post by fackamato on 2007-07-04
I haven''t been able to make VLC work with jack (directly, or via alsa) either. I know that it is possible to make a config file for the mplayer-mozilla-plugin similar to ~/.mplayer/config where you can set a lot of options.. I'll google a bit...

After one minute of googling, I came up with this: [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

```
mplayerplug-in configuration

The mplayerplug-in.conf file can change the behavior of the plugin. Here are the options.
The config file can be located in 3 places: 
$HOME/.mplayer/mplayerplug-in.conf
$HOME/.mozilla/mplayerplug-in.conf
/etc/mplayerplug-in.conf

These files are checked for existance and opened and the options are read. The options in the last read file supersedes the options set in the previous file. The read order of the files is: 
/etc/mplayerplug-in.conf
$HOME/.mozilla/mplayerplug-in.conf
$HOME/.mplayer/mplayerplug-in.conf
When you use the Configuration Dialog it sets the options in the last file so that the user settings override the system settings. 

Example:
prefer-aspect=1
ao=arts
There is an example config file in the source code package.
```

I have not tried it myself though, but will do now. ;)

**edit:** WOAH! Viewing a video on googlevideo (I know it doesn't use mplayer plugin I just wanted to test it) launches approx. 120 clients in the message window of qjackctl, and I don't even get sound.Strange. Will now try the plugin...Hm, the plugin doesn't seem to work in Opera, I'll investigate.

---

### Post by 00l0 on 2007-07-05
thank you thackamato, that's something
i'll see if there's a similar configuration file for the vlc-mozilla plugin though i'm using the firefox extension named MediaPlayerConnectivity to manage which multimedia files go with what player. I'll see if i can find something.


Btw, i found out that editing my /etc/rc.local file i can start my system with jackd activated(freebob)

the editing consists in adding this to the file:

$ jackd -d freebob &

The system starts with freebob activated(my Focusrite Saffire Firewire Interface show lights green, which mean that is ready to process aduio in-out), however, i can't here any audio files through xmms's jackd-plugin, not until i kill the jack server and relaunch it again with the exact same parameters.

ANy suggestions?


thank you!

---

### Post by fackamato on 2007-07-05
> **00l0 said:**
> thank you thackamato, that's something
i'll see if there's a similar configuration file for the vlc-mozilla plugin though i'm using the firefox extension named MediaPlayerConnectivity to manage which multimedia files go with what player. I'll see if i can find something.


Btw, i found out that editing my /etc/rc.local file i can start my system with jackd activated(freebob)

the editing consists in adding this to the file:

$ jackd -d freebob &

The system starts with freebob activated(my Focusrite Saffire Firewire Interface show lights green, which mean that is ready to process aduio in-out), however, i can't here any audio files through xmms's jackd-plugin, not until i kill the jack server and relaunch it again with the exact same parameters.

ANy suggestions?


thank you!

I guess that since it's from rc.d, jackd is started as root (thus you get no permission to use it). Perhaps in rc.local try

```
su username -c "jackd -d freebob &"
```

---

### Post by 00l0 on 2007-07-05
> **fackamato said:**
> I guess that since it's from rc.d, jackd is started as root (thus you get no permission to use it). Perhaps in rc.local try

```
su username -c "jackd -d freebob &"
```

hey fackamato,
thank you very much, that worked like a charm!
tho i don't really understand some of the parameters for the commands; what's the "-c" for? and what exactly is the meaning of the "&", i read somewhere it's something about not stopping the boot process,..is that true?

thank you very much again  ;D

---

### Post by fackamato on 2007-07-05
> **00l0 said:**
> hey fackamato,
thank you very much, that worked like a charm!
tho i don't really understand some of the parameters for the commands; what's the "-c" for? and what exactly is the meaning of the "&", i read somewhere it's something about not stopping the boot process,..is that true?

thank you very much again  ;D

Np.

-c is used to tell the su program to execute the line within the quotes and then exit. The & is used to put the program in the background so it doesn't halt the boot process (since Ubuntu doesn't use a parallel boot process yet..., like Archlinux ;)). Not all programs need & though, as a a matter of fact I don't think jackd needs it because it's a a daemon, and probably will daemonize itself when launched (haven't tried so I can't say for certain). :)

Glad you got it working. I would do the same, but then the other users on the computer wouldn't be able to use JACK. I wonder if there's a way to "su -c" a program but instead of user, running it with group priviligies... Or does it just work?

Can you use JACK with other users on your system with this kind of setup?

---

### Post by 00l0 on 2007-07-06
i'm sorry i don't know, i'm the only user...
maybe i can try creating some user group, tho i'll have to delete it later, let me know if you want so  ;D

---

### Post by fackamato on 2007-07-06
> **00l0 said:**
> i'm sorry i don't know, i'm the only user...
maybe i can try creating some user group, tho i'll have to delete it later, let me know if you want so  ;D

It would be cool if you tried ;)

---

### Post by 00l0 on 2007-07-09
hey fackamato,
i finally managed to do it!
I asked in the videolan forums and one of the site admins linked me to his blogsite where i found instructions on how to build VLC subversion with jack compatibility...i had success to it can't be very very hard... : D

well this is the blogsite:
[http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704](http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704)

just there's on thing missing(at least for me) during installation and that's the jacklib:
#sudo apt-get install libjack-dev

that's all, btw if you manage to build a .deb package please contact me i'd like to have it so i don't have to compile it again, i tried to do so with "checkinstall" but had an error.

good luck!   ;]

---

### Post by linkx on 2008-04-27
Have you had any luck getting sound from your Saffire? I am now running Hardy 8.04 final with my Focusrite Saffire LE and I am hoping to make watching videos and listening to music smoother. Posting tips would be appreciated; I will do the same!

---

