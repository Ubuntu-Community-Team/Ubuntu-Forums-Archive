---
title: "Receiving a troublesome error trying to install plug-ins"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by PurpleZoe on 2007-08-12
Greetings:)

I am a very new noob. I installed Ubuntu on Friday (after a 6 hour call with Microsoft's game of passing the tech support buck...).  I am now done with the nonsense of Microsoft and am really excited about Linux.
Only thing is Feisty Fawn has made it very difficult for me to install libdvdcss.
I'd like to be able to watch divx videos and play and rip my dvd's but can't currently due to understandable licensing restrictions.
I googled for a solution that matched my OS release, and found a review that advised how to install it and followed his suggestions.

His review is here; [http://www.reviewlinux.com/index.php?m=show&id=6034](http://www.reviewlinux.com/index.php?m=show&id=6034)

I found his instructions fairly easy to follow from the point where he offered instructions from a guide (2 lines). I entered them. All seemed to be installing fine but a screen with a Java agreement popped up and nothing I did seemed to helped me agree by keying yes or pressing enter, etc. I couldn't find any instructions in help either.

I closed out of it hoping it would still install seeing as I could find no options offered for my agreement input.

When I went back into terminal to add command lines for win32 from the same review in the 'Play Dvd' section, I get an error now reading: dpkg was interrupted, you must manually run 'dpkg --configure -a'  to correct the problem.

When I ran: dpkg --configure -a

It brought up screen asking for a superuser. I attempted to type in my password. This did not work. I then attempted to type in my username, thinking it needed that before the password. No dice.

Any suggestions?

Gracious Thanks
-Zoe

:guitar:

---

### Post by aysiu on 2007-08-12
```
sudo dpkg --configure -a
``` is the command you're looking for.

By the way, those instructions are totally convoluted. You could have installed *libdvdvcss2* and *w32codecs* with three commands pasted into the terminal: ```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get update && sudo apt-get install w32codecs libdvdcss2
```

---

### Post by PurpleZoe on 2007-08-12
Interesting.

I typed in the three command lines and was given the prompt to type in my password.
I did so and this came up:

[COLOR="Yellow"]wget: Invalid --execute command 'y.gpg'[/COLOR]

Do I need to uninstall something?

Apologies if I'm missing the obvious.
I think I'll need to get a copy of 'Linux for Dummies' at some point soon.

:guitar:

---

### Post by aysiu on 2007-08-12
Don't retype. Copy and paste.

---

### Post by PurpleZoe on 2007-08-13
Grazi. It did take the command.
:guitar:

I had no idea I could cut and paste. All this time... I've been typing.

Unfortunately it still won't play dvds or divx video. Am I missing something? I installed wine recently with no problem. I may try to run Windows apps with wine or crossover in the future, but would rather not deal with windows at all if I possibly can. I like Ubuntu.
I would like to play dvd's and divx: vids though.


Thankyou for your time with this.

---

### Post by PurpleZoe on 2007-08-14
Does anyone know of another solution for playing divx and dvd's in Ubuntu?
I managed to install libdvdcss and it still isn't playing...

Grazi.:guitar:

---

### Post by PurpleZoe on 2007-08-15
So I figured out how to get some dvd's to play in gzine. All don't play though, even with libdvdcss2 installed.

I have mplayer as well, but  newer dvd's and divx are still not recognized.
[U]
Here's what the bugfix report reads at 
[https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/112055:](https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/112055:)[/U]

[B]Bug description 

Firefox does not recognize that the mplayer plugin provides divx support in a standard installation of ubuntu feisty. Using about:config in firefox does not show the divx plugin even though divx support is provided in

/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt

moving these two files to /usr/lib/firefox/plugins/ solves the problem.

this bug is replicated by others as noted in [http://ubuntuforums.org/showthread.php?t=396569](http://ubuntuforums.org/showthread.php?t=396569)[/B]


What command do I use in terminal to get the plugins moved to the new folder this bugfix advises will solve the problem?

Thanks to all for the assistance.
I love Ubuntu but I hope the next version will have the glitchiness of installing outside software ironed out. Playing retail dvd's (and .divx files online) at the least is a normal thing that customer's seek to do. Imo everything is damn near perfect and I am more content than I ever was with Windows, but I really want to avoid having to install the Codeweaver's window app plug-in/software. 

^_^

---

