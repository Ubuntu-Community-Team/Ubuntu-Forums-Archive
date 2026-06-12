---
title: "[Howto] Restore your previous xorg.conf file"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by Derek Djons on 2006-09-15
A few days ago I installed Cedega on my portable with Ubuntu Linux installed on it. After installation I customized the application options / preferences and ran the test utility. The test revealed that my 3D Acceleration wasn’t working. I found that a crucial part to have working so I started fixing it.

After a while I made a mistake and my (already highly customized) xorg.conf got re-written by all kinds of default settings. Since the xserver uses the file in order to start-up correctly you can imagine that my xserver crashed.

In Ubuntu Linux the xorg.conf file makes a backup of it’s current state before it accepts getting edited or rewritten. This does not apply when you edit xorg.conf yourself though (editing with Vi or Gedit). So I got an backup waiting to be restored, with all my setting related to resolution, drivers, AIXGL/Compiz and so on. I’ll use my own example in order to explain how you can restore the previous xorg.conf file.

After I rebooted Ubuntu Linux started up correctly until it came across xserver section. There the xserver crashed and I was presented with a terminal screen which kindly asked for my username.

I logged in with my normal account and entered:

    ```
djons@tosh-empire:/$ cd /
```

This command brings you to the root of your system. If you enter:

    ```
djons@tosh-empire:/$ dir
```

You will see you are at the beginning point of the system.We need to proceed towards the xorg.conf location. Hit the following path in order to get there:

    ```
djons@tosh-empire:/$ cd /etc/X11
```

Note that X11 is with a capital X. All Linux distributions, UNIX variations and thus also Mac OS X feature this.

When you are in the X11 directory you will see a file structure similar to this:

    ```
djons@tosh-empire:/etc/X11$ dir
    app-defaults gdm xorg.conf Xsession.d
    applnk rgb.txt xorg.conf~ Xsession.options
    config susewm xorg.conf.20060807011320 Xwrapper.config
    cursors X Xresources
    default-display-manager xinit xserver
    fonts xkb Xsession
```

You should pinpoint two files, they are the files with which we are going work:

    ```
xorg.conf
xorg.conf.?????????????
```

The question marks represents year, month, day and some more info. But the date is the most important since you can easily pick the most current back-upped version of xorg.conf before things went sour. So now it’s time to replace our corrupt xorg.conf with a previous working version.

First of all we have to delete the current corrupted xorg file. To make this happen do the following terminal work:

    ```
djons@tosh-empire:/etc/X11$ sudo rm xorg.conf
```

Now we have to rename the back-upped version in order to get our installation working with icons and mouse. Do the following terminal work:

    ```
djons@tosh-empire:/etc/X11$ sudo mv xorg.conf.????????????? xorg.conf
```

We’re done. The only thing you have to do is restart your machine and wait till it’s done booting up the installation. In order to get your machine rebooting hit the on/off switch once or use the following command:

    ```
djons@tosh-empire:/etc/X11$ sudo shutdown -r now
```

---

### Post by ssbaby on 2007-04-27
thank you so much for this - just saved me from having to reinstall again (i've been playing with getting Fiesty and my graphics card to play nicely, but corrupted my xorg.conf file)

---

### Post by disturbedite on 2007-04-27
i was gonna say, you should back up your xorg.conf before editing it.  then edit away, save and restart the xserver.  if you can't get to graphical login, restore it from command line like this:
sudo mv /path/to/xorg.conf.back  /etc/X11/xorg.conf

---

### Post by cubebomb on 2007-05-13
dam it just sucks you have to remember ALL of these commands, im gonna have to write all this **** down, and hopefully i can fix my ****, dont feel like restoring.

---

### Post by aniketnp on 2007-05-25
Thanks!

I learned something new and solved my problem.

---

### Post by kerunt on 2007-05-28
Thanks for the guide, just saved my butt!

---

### Post by ben55 on 2007-08-08
:KS

Thanks for the guide. Saved me from having to restore for the 8th time today.

---

### Post by NZJLY on 2007-08-17
Thanks :) :guitar:

---

### Post by dorkdork777 on 2007-08-29
TYVM! Fixed my mouse and resolution problems that started when I messed with the xorg.conf. Great work! :)

---

### Post by goofeyfoot on 2007-09-16
Just wanted to compliment you on this very concise explanation.  Usually, newbies like myself can't understand half the jargon on these forums.  Good writing and well-organized.

I also have a question.

I fried my file making changes just like you did.  Obviously, Ubuntu wouldn't boot.  But what was even more bizarre is that when I went back to the grub menu I found out that my windows xp operating system (which was on a completely separate drive) also got toasted.

Man, I don't mind messing with Ubuntu on a dual boot system but I didn't think that doing that would also cook a completely separate system.

I guess the question is how can you keep your Ubuntu hacking and mucking about from frying your Windows installation too?

Thanks again,

Michael

---

### Post by sideofzen on 2007-09-20
Thank you! This was a lifesaver. Definitely being tagged. No doubt I'll be needing it in the future.

---

### Post by Gaztech on 2007-10-28
Mate, thank you soooooo much, after being an idiot and putting a dodgy command in my xorg.conf file this saved me a  restore, THANK YOU!!!

---

### Post by drmaxmad on 2007-12-16
thanks mate......it really helped me a lot.:guitar:

---

